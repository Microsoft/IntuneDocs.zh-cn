---
title: 使用 Microsoft Intune 颁发 DigiCert PKCS 证书
titleSuffix: Microsoft Intune
description: 安装和配置 Intune 证书连接器，以便从 DigiCert PKI 平台向 Intune 管理的设备颁发 PKCS 证书。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ca76ffe0c8fa42f1c2cf24fcdefd287140231220
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "73801620"
---
# <a name="set-up-intune-certificate-connector-for-digicert-pki-platform"></a>设置 DigiCert PKI 平台的 Intune 证书连接器

使用 Intune 证书连接器，以便从 DigiCert PKI 平台向 Intune 管理的设备颁发 PKCS 证书。 可以将连接器仅用于 DigiCert 证书颁发机构 (CA)，也可以将连接器同时用于 DigiCert CA 和 Microsoft CA。

> [!TIP]
> DigiCert 已获取 Symantec 的网站安全和相关的 PKI 解决方案业务。 有关此更改的详细信息，请参阅 [Symantec 技术支持](https://support.symantec.com/en_US/article.INFO4722.html)一文。

如果已使用 Intune 证书连接器通过 PKCS 或 System Center Endpoint Protection 从 Microsoft CA 颁发证书，则可以使用相同的连接器从 DigiCert CA 配置和颁发 PKCS 证书。 完成配置以支持 DigiCert CA 后，Intune 证书连接器可以颁发以下证书：

* 来自 Microsoft CA 的 PKCS 证书
* 来自 DigiCert CA 的 PKCS 证书
* 来自 Microsoft CA 的 Endpoint Protection 证书

如果未安装连接器，但计划将其用于 Microsoft CA 和 DigiCert CA，请先完成 Microsoft CA 的连接器配置。 然后，返回到本文，将其配置为同时支持 DigiCert。 有关证书配置文件和连接器的详细信息，请参阅[在 Microsoft Intune 中为设备配置证书配置文件](certificates-configure.md)。  

如果将连接器仅用于 DigiCert CA，则可以使用本文中的说明来安装和配置连接器。

## <a name="prerequisites"></a>必备条件

- **DigiCert CA 的活动订阅**：需要订阅才能从 DigiCert CA 获取注册机构 (RA) 证书。

## <a name="install-the-digicert-ra-certificate"></a>安装 DigiCert RA 证书

1. 将以下代码片段保存到名为 certreq.ini  的文件中，并根据需要进行更新（例如：CN 格式的使用者名称）  。

        [Version] 
        Signature="$Windows NT$" 
        
        [NewRequest] 
        ;Change to your,country code, company name and common name 
        Subject = "Subject Name in CN format"
        
        KeySpec = 1 
        KeyLength = 2048 
        Exportable = TRUE 
        MachineKeySet = TRUE 
        SMIME = False 
        PrivateKeyArchive = FALSE 
        UserProtected = FALSE 
        UseExistingKeySet = FALSE 
        ProviderName = "Microsoft RSA SChannel Cryptographic Provider" 
        ProviderType = 12 
        RequestType = PKCS10 
        KeyUsage = 0xa0 
        
        [EnhancedKeyUsageExtension] 
        OID=1.3.6.1.5.5.7.3.2 ; Client Authentication  // Uncomment if you need a mutual TLS authentication
        
        ;----------------------------------------------- 

2. 打开提升的命令提示符并使用以下命令生成证书签名请求 (CSR)：

   `Certreq.exe -new certreq.ini request.csr`

3. 在记事本中打开 request.csr 文件，并复制以下格式的 CSR 内容：

        -----BEGIN NEW CERTIFICATE REQUEST-----
        MIID8TCCAtkCAQAwbTEMMAoGA1UEBhMDVVNBMQswCQYDVQQIDAJXQTEQMA4GA1UE
        …
        …
        fzpeAWo=
        -----END NEW CERTIFICATE REQUEST-----


4. 登录到 DigiCert CA，并浏览到任务中的“获取 RA 证书”  。

   a. 从步骤 3 开始在文本框中提供 CSR 内容。

   b. 提供证书的友好名称。

   c. 选择“继续”  。

   d. 使用提供的链接将 RA 证书下载到本地计算机。

5. 将 RA 证书导入到 Windows 证书存储中：

   a. 打开 MMC 控制台。

   b. 选择“文件”   > “添加或删除管理单元”   > “证书”   > “添加”  。

   c. 选择“计算机帐户”   > “下一步”  。

   d. 选择“本地计算机”   > “完成”  。

   e. 在“添加或删除管理单元”窗口中选择“确定”   。 展开“证书(本地计算机)”   > “个人”   > “证书”  。

   f. 右键单击“证书”  节点，然后选择“所有任务”   > “导入”  。

   g. 选择从 DigiCert CA 下载 RA 证书的位置，然后选择“下一步”  。

   h. 选择“个人证书存储”   > “下一步”  。

   i. 选择“完成”以将 RA 证书及其私钥导入本地计算机个人存储   。

6. 导出和导入私钥证书：

   a. 展开“证书(本地计算机)”   > “个人”   > “证书”  。

   b. 选择在上一步中已导入的证书。

   c. 右键单击证书并选择“所有任务”   > “导出”  。

   d. 选择“下一步”，然后输入密码。 

   e. 选择要导出到的位置，然后选择“完成”  。

   f. 使用步骤 5 中的过程，将私钥证书导入本地计算机个人存储中  。

   g. 记录 RA 证书指纹副本（不含任何空格）。 下面是一个指纹示例：

        RA Cert Thumbprint: “EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5”

    > [!NOTE]
    > 若要获取从 DigiCert CA 获取 RA 证书的帮助，请联系 [DigiCert 客户支持部门](mailto:enterprise-pkisupport@digicert.com)。

## <a name="prepare-to-install-intune-certificate-connector"></a>准备安装 Intune 证书连接器

> [!TIP]
> 本文适用于将 Intune 证书连接器仅用于一个 DigiCert CA 的情况。 如果将 Intune 证书连接器用于一个 Microsoft CA 并想要添加 DigiCert CA 支持，请直接跳到[将连接器配置为支持 DigiCert](#configure-the-connector-to-support-digicert)。

1. 从以下列表中选择一个 Windows 操作系统版本，并将其安装在计算机上：
   * Windows Server 2012 R2 Datacenter
   * Windows Server 2012 R2 Standard
   * Windows Server 2016 Datacenter
   * Windows Server 2016 标准版

2. 创建具有管理权限的用户，并使用它来完成以下步骤。

3. 检查最新 Windows 更新并进行安装（如果存在）。 安装 Windows 更新之后，重新启动计算机。

4. 安装 .NET Framework 3.5：

   a. 打开“控制面板”   > “程序和功能”   > “启用或关闭 Windows 功能”  。

   b. 选择“.NET Framework 3.5”  并安装。

## <a name="install-intune-certificate-connector-for-use-with-digicert"></a>安装 Intune 证书连接器以与 DigiCert 配合使用

> [!TIP]
> 如果将 Intune 证书连接器用于一个 Microsoft CA 并想要添加 DigiCert CA 支持，请直接跳到[将连接器配置为支持 DigiCert](#configure-the-connector-to-support-digicert)。

从 Intune 管理门户下载最新的 Intune 证书连接器版本，然后按照以下说明操作。

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 选择“租户管理”   > “连接器和令牌”   > “证书连接器”   > “+ 添加”  。

3. 针对 PKCS #12 的连接器单击“下载证书连接器软件”  并将文件保存到可从服务器上进行访问的位置，将在该服务器上安装连接器。

   ![下载连接器软件](./media/certificates-digicert-configure/connector-download.png)

4. 在要安装连接器的服务器上，使用提升的权限运行 NDESConnectorSetup.exe  。

5. 在“安装选项”页上，选择“PFX 分发”   。

   ![选择 PFX 分发](./media/certificates-digicert-configure/digicert-ca-connector-install.png)

   > [!IMPORTANT]
   > 如果使用 Intune 证书连接器从 Microsoft CA 和 DigiCert CA 颁发证书，请选择“SCEP 和 PFX 配置文件分发”  。

6. 使用默认选择完成连接器设置。

## <a name="configure-the-connector-to-support-digicert"></a>将连接器配置为支持 DigiCert

默认情况下，Intune 证书连接器安装在 %ProgramFiles%\Microsoft Intune\NDESConnectorSvc  中。

1. 在 NDESConnectorSvc  文件夹中，在记事本中打开 NDESConnector.exe.config  文件。

   a. 使用上一节中复制的证书指纹值更新 `RACertThumbprint` 密钥值。 例如：

        <add key="RACertThumbprint"
        value="EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5"/>

   b. 保存并关闭该文件。

2. 打开“services.msc”  ：

   a. 选择“Intune 连接器服务”  。

   b. 停止此服务，然后再次启动。

   c. 关闭服务的窗口。

## <a name="set-up-the-intune-administrator-account"></a>设置 Intune 管理员帐户  

> [!TIP]
> 如果将 Intune 证书连接器用于 Microsoft CA 并想要添加 DigiCert CA 支持，请直接跳到[创建受信任的证书配置文件](#create-a-trusted-certificate-profile)。
 
1. 从 %ProgramFiles%\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe  中打开 NDES 连接器用户界面。

2. 在“注册”选项卡上，选择“登录”   。

3. 提供你的 Intune 租户管理员凭据。

4. 选择“登录”，然后选择“确定”以确认注册成功   。 然后可以关闭 NDES 连接器用户界面。

   ![包含“已成功注册”消息的 NDES 连接器界面](./media/certificates-digicert-configure/certificates-digicert-configure-connector-configure.png)

## <a name="create-a-trusted-certificate-profile"></a>创建受信任的证书配置文件

为 Intune 托管设备部署的 PKCS 证书必须使用受信任的根证书进行链接。 若要建立此链接，请使用来自 DigiCert CA 的根证书创建 Intune 受信任的证书配置文件。

1. 从 DigiCert CA 中获取受信任的根证书：

   a. 登录到 DigiCert CA 管理门户。

   b. 从“任务”中选择“管理 CA”   。

   c. 从列表中选择相应的 CA。

   d. 选择“下载根证书”来下载受信任的根证书  。

2. 在 Intune 门户中创建受信任的证书配置文件：

   a. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

   b. 选择“设备”   > “配置文件”   > “创建配置文件”  。

   c. 输入以下属性：

      - 配置文件的名称 
      - （可选）设置“描述” 
      - 将配置文件部署到的平台 
      - 将配置文件类型  设置为“受信任的证书” 

   d. 选择“设置”  ，然后浏览到受信任的根 CA 证书 .cer 文件（为与此证书配置文件一起使用而导出的文件），然后选择“确定”  。

   e. 从以下位置选择受信任证书的**目标存储区**（仅适用于 Windows 8.1 和 Windows 10 设备）：
      - **计算机证书存储区 - 根**
      - **计算机证书存储区 - 中间**
      - **用户证书存储区 - 中间**

   f. 完成后，选择“确定”，返回“创建配置文件”窗格，然后选择“创建”    。  

  该配置文件将出现在“设备配置 - 配置文件”窗格中的配置文件列表中，其中配置文件类型为“受信任的证书”   。  请确保将此配置文件分配给将接收证书的设备。 若要向组分配此配置文件，请参阅[分配设备配置文件](../configuration/device-profile-assign.md)。


## <a name="get-the-certificate-profile-oid"></a>获取证书配置文件 OID  

证书配置文件 OID 与 DigiCert CA 中的证书配置文件模板相关联。 若要在 Intune 中创建 PKCS 证书配置文件，则证书模板名称必须采用证书配置文件 OID 的形式，该 OID 与 DigiCert CA 中的证书模板相关联。

1. 登录到 DigiCert CA 管理门户。
2. 选择“管理证书配置文件”  。
3. 选择要使用的证书配置文件。
4. 复制证书配置文件 OID。 这类似于以下示例：

       Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109 

> [!NOTE]
> 如果需要帮助来获取证书配置文件 OID，请联系 [DigiCert 客户支持部门](mailto:enterprise-pkisupport@digicert.com)。

## <a name="create-a-pkcs-certificate-profile"></a>创建 PKCS 证书配置文件

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 选择“设备”   > “配置文件”   > “创建配置文件”  。

3. 输入以下属性：

   - 配置文件的名称 
   - （可选）设置“描述” 
   - 将配置文件部署到的平台 
   - 将“配置文件类型”设置为“PKCS 证书”  

4. 在“PKCS 证书”  窗格中，使用下表中的值配置参数。 需要这些值才能通过 Intune 证书连接器从 DigiCert CA 颁发 PKCS 证书。

   |PKCS 证书参数 | 值 | 描述 |
   | --- | --- | --- |
   | 证书颁发机构 | pki-ws.symauth.com | 此值必须是不带结尾斜杠的 DigiCert CA 基本服务 FQDN。 如果不确定这是否为 DigiCert CA 订阅的正确基本服务 FQDN，请联系 DigiCert 客户支持部门。 <br><br>*如果从 Symantec 更改为 DigiCert，则此 URL 保持不变*。 <br><br> 如果此 FQDN 不正确，则 Intune 证书连接器不会从 DigiCert CA 颁发 PKCS 证书。| 
   | 证书颁发机构名称 | Symantec | 此值必须是字符串 Symantec  。 <br><br> 如果对此值进行任何更改，则 Intune 证书连接器将不会从 DigiCert CA 颁发 PKCS 证书。|
   | 证书模板名称 | 来自 DigiCert CA 的证书配置文件 OID。 例如：**2.16.840.1.113733.1.16.1.2.3.1.1.61904612**| 该值必须是[上一节](#get-the-certificate-profile-oid)从 DigiCert CA 证书配置文件模板中获取的证书配置文件 OID。 <br><br> 如果 Intune 证书连接器在 DigiCert CA 中找不到与此证书配置文件 OID 关联的证书模板，则它不会从 DigiCert CA 颁发 PKCS 证书。|

   ![CA 和证书模板的选择](./media/certificates-digicert-configure/certificates-digicert-pkcs-example.png)

   > [!NOTE]
   > Windows 平台的 PKCS 证书配置文件不需要与受信任的证书配置文件相关联。 但是非 Windows 平台配置文件（如 Android）则必须关联。

5. 完成配置文件的配置以满足你的业务需求，然后选择“创建”  以保存配置文件。

6. 在新配置文件的“概述”  页上，选择“分配”  ，并配置将接收此配置文件的相应组。 至少一个用户或设备必须成为已分配组的一部分。
 
完成前面的步骤之后，Intune 证书连接器将从 DigiCert CA 向所分配组中的 Intune 管理设备颁发 PKCS 证书。 这些证书将在 Intune 管理设备上的当前用户证书存储的个人存储中可用   。

### <a name="supported-attributes-for-the-pkcs-certificate-profile"></a>PKCS 证书配置文件支持的属性

|属性 | Intune 支持的格式 | DigiCert 云 CA 支持的格式 | result |
| --- | --- | --- | --- |
| 使用者名称 |Intune 仅支持以下三种格式的使用者名称： <br><br> 1.公用名 <br> 2.包含电子邮件地址的公用名 <br> 3.作为电子邮件地址的公用名 <br><br> 例如： <br><br> `CN = IWUser0 <br><br> E = IWUser0@samplendes.onmicrosoft.com` | DigiCert CA 支持更多属性。  如果要选择更多属性，则必须在 DigiCert 证书配置文件模板中使用固定值来定义它们。| 我们使用公用名或来自 PKCS 证书请求的电子邮件。 <br><br> Intune 证书配置文件和 DigiCert 证书配置文件模板之间的任何属性选择不匹配都会导致无法从 DigiCert CA 颁发证书。|
| SAN | Intune 仅支持以下 SAN 字段值： <br><br> **AltNameTypeEmail** <br> **AltNameTypeUpn** <br> **AltNameTypeOtherName**（编码值） | DigiCert 云 CA 也支持这些参数。 如果要选择更多属性，则必须在 DigiCert 证书配置文件模板中使用固定值来定义它们。 <br><br> **AltNameTypeEmail**：如果在 SAN 中找不到此类型，Intune 证书连接器将使用 AltNameTypeUpn  的值。  如果在 SAN 中也未找到 AltNameTypeUpn  ，Intune 证书连接器将使用“使用者名称”的值（如果其是电子邮件格式）。  如果仍未找到此类型，Intune 证书连接器将无法颁发证书。 <br><br> 示例： `RFC822 Name=IWUser0@ndesvenkatb.onmicrosoft.com`  <br><br> **AltNameTypeUpn**：如果在 SAN 中找不到此类型，Intune 证书连接器将使用 AltNameTypeEmail  的值。 如果在 SAN 中也未找到 AltNameTypeEmail  ，Intune 证书连接器将使用“使用者名称”的值（如果其是电子邮件格式）。 如果仍未找到此类型，Intune 证书连接器将无法颁发证书。  <br><br> 示例： `Other Name: Principal Name=IWUser0@ndesvenkatb.onmicrosoft.com` <br><br> **AltNameTypeOtherName**：如果在 SAN 中找不到此类型，Intune 证书连接器将无法颁发证书。 <br><br> 示例： `Other Name: DS Object Guid=04 12 b8 ba 65 41 f2 d4 07 41 a9 f7 47 08 f3 e4 28 5c ef 2c` <br><br>  对于此字段，DigiCert CA 仅支持编码格式的值（十六进制值）。 对于此字段中的任何值，Intune 证书连接器在提交证书请求之前会将其转换为 base64 编码。 Intune 证书连接器不会验证此值是否已编码。  | 无 |

## <a name="troubleshooting"></a>疑难解答

Intune 证书连接器服务日志在 NDES 连接器计算机上的 %ProgramFiles%\Microsoft Intune\NDESConnectorSvc\Logs\Logs  中可用。 打开 [SvcTraceViewer](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) 中的日志，然后搜索异常或错误消息。

| 问题/错误消息 | 解决步骤 |
| --- | --- |
| 无法使用 Intune 租户管理员帐户登录到 NDES 连接器 UI。 | Microsoft 终结点管理器管理中心未启用本地证书连接器时，可能会发生这种情况。 解决此问题： <br><br> 1.登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。 <br> 2.选择“租户管理”   > “连接器和令牌”   > “证书连接器”  。 <br> 3.找到证书连接器并确保它已启用。 <br><br> 完成前述步骤之后，尝试使用相同的 Intune 租户管理员帐户登录到 NDES 连接器 UI。 |
| 找不到 NDES 连接器证书。 <br><br> System.ArgumentNullException:值不能为 null。 | 如果 Intune 租户管理员帐户从未登录到 NDES 连接器 UI，则 Intune 证书连接器会显示此错误。 <br><br> 如果此错误仍然存在，请重新启动 Intune 服务连接器。 <br><br> 1.打开“services.msc”  。 <br> 2.选择“Intune 连接器服务”  。 <br> 3.单击右键并选择“重新启动”  。|
| NDES 连接器 - IssuePfx - 常规异常： <br> System.NullReferenceException：对象引用未设置为某个对象的实例。 | 此错误是暂时的。 重新启动 Intune 服务连接器。 <br><br> 1.打开“services.msc”  。 <br> 2.选择“Intune 连接器服务”  。 <br> 3.单击右键并选择“重新启动”  。 |
| DigiCert 提供程序 - 无法获取 DigiCert 策略。 <br><br>“操作已超时。” | Intune 证书连接器在与 DigiCert CA 通信时收到“操作已超时”错误。 如果此错误继续出现，请增加连接超时值并重试。 <br><br> 若要增加连接超时值，请执行以下操作： <br> 1.转到 NDES 连接器计算机。 <br>2.在记事本中打开 %ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config  文件。 <br> 3.增加以下参数的超时值： <br><br> `CloudCAConnTimeoutInMilliseconds` <br><br> 4.重新启动 Intune 证书连接器服务。 <br><br> 如果问题仍然存在，请联系 DigiCert 客户支持部门。 |
| DigiCert 提供程序 - 无法获取客户端证书。 | Intune 证书连接器从“本地计算机 - 个人证书存储”中检索不到资源授权证书。 若要解决此问题，请将资源授权证书连同其私钥一起安装在“本地计算机-个人证书存储”中。 <br><br> 资源授权证书必须从 DigiCert CA 获取。 有关详细信息，请联系 DigiCert 客户支持部门。 | 
| DigiCert 提供程序 - 无法获取 DigiCert 策略。 <br><br>“请求已中止：无法创建 SSL/TLS 安全通道。" | 在以下情况下会发生此错误： <br><br> 1.Intune 证书连接器服务无权从“本地计算机-个人证书存储”中读取资源授权证书及其私钥。 若要解决此问题，请检查在 services.msc 中运行上下文帐户的连接器服务。 该连接器服务必须在 NT AUTHORITY\SYSTEM 上下文下运行。 <br><br> 2.Intune 管理门户中的 PKCS 证书配置文件在配置时可能使用了无效的 DigiCert CA 基本服务 FQDN。 FQDN 类似于 pki-ws.symauth.com  。 若要解决此问题，请咨询 DigiCert 客户支持部门，以确定该 URL 是否适合你的订阅。 <br><br> 3.Intune 证书连接器无法通过资源授权证书对 DigiCert CA 进行身份验证，因为它无法检索证书私钥。 若要解决此问题，请将资源授权证书连同其私钥一起安装在“本地计算机-个人证书存储”中。 <br><br> 如果问题仍然存在，请联系 DigiCert 客户支持部门。 |
| DigiCert 提供程序 - 无法获取 DigiCert 策略。 <br><br>“无法理解请求元素。” | Intune 证书连接器无法获取 DigiCert 证书配置文件模板，因为客户端配置文件 OID 与 Intune 证书配置文件不匹配。 在其他情况下，Intune 证书连接器无法找到与 DigiCert CA 中客户端配置文件 OID 关联的证书配置文件模板。 <br><br> 若要解决此问题，请从 DigiCert CA 的 DigiCert 证书模板获取正确的客户端配置文件 OID。 然后更新 Intune 管理门户中的 PKCS 证书配置文件。 <br><br> 从 DigiCert CA 中获取证书配置文件 OID： <br> 1.登录到 DigiCert CA 管理门户。 <br> 2.选择“管理证书配置文件”  。 <br> 3.选择要使用的证书配置文件。 <br> 4.获取证书配置文件 OID。 这类似于以下示例： <br> `Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109` <br><br> 使用正确的证书配置文件 OID 更新 PKCS 证书配置文件： <br>1.登录到 Intune 管理门户。 <br> 2.转到 PKCS 证书配置文件并选择“编辑”  。 <br> 3.在证书模板名称对应的字段中更新证书配置文件 OID。 <br> 4.保存 PKCS 证书配置文件。 |
| DigiCert 提供程序 - 策略验证失败。 <br><br> 属性不属于 DigiCert 支持的证书模板属性列表。 | 当 DigiCert 证书配置文件模板和 Intune 证书配置文件之间存在差异时，DigiCert CA 将显示此消息。 SubjectName 或 SubjectAltName 中的属性不匹配时，可能会发生此问题   。 <br><br> 若要解决此问题，请在 DigiCert 证书配置文件模板中为 SubjectName 和 SubjectAltName 选择 Intune 支持的属性   。 有关详细信息，请参阅“证书参数”一节中的 Intune 支持的属性  。 |
| 某些用户设备不接收来自 DigiCert CA 的 PKCS 证书。 | 当用户 UPN 包含特殊字符（如下划线）时会发生此问题（示例：`global_admin@intune.onmicrosoft.com`）。 <br><br> DigiCert CA 不支持 mail_firstname 和 mail_lastname 中的特殊字符   。 <br><br> 请执行以下步骤来帮助解决此问题： <br><br> 1.登录到 DigiCert CA 管理门户。 <br> 2.转到“管理证书配置文件”  。 <br> 3.选择用于 Intune 的证书配置文件。 <br> 4.选择“自定义选项”  链接。 <br> 5.选择“高级选项”  按钮。 <br> 6.在“证书字段 – 使用者 DN”下，添加“公用名 (CN)”字段并删除现有“公用名 (CN)”字段    。 添加和删除操作必须一起执行。 <br> 7.选择“保存”  。 <br><br> 通过上述更改，DigiCert 证书配置文件会请求“CN=<upn>”而不是 mail_firstname 和 mail_lastname    。 |
| 用户从设备手动删除已部署的证书。 | Intune 将在下一步的签入或策略实施过程中重新部署相同的证书。 在这种情况下，NDES 连接器不会收到 PKCS 证书请求。 |

## <a name="next-steps"></a>后续步骤

使用本文中的信息以及[什么是 Microsoft Intune 设备配置文件？](../configuration/device-profiles.md)中的信息来管理组织的设备及设备上的证书。
