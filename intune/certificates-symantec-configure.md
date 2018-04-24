---
title: 使用 Microsoft Intune 颁发 Symantec PKCS 证书
titlesuffix: ''
description: 安装和配置 Intune 证书连接器，以便从 Symantec PKI Manager Web 服务向 Intune 管理的设备颁发 PKCS 证书。
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ff642c7d8d836979fadebc799e2e7373cd299f4e
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="set-up-intune-certificate-connector-for-symantec-pki-manager-web-service"></a>为 Symantec PKI Manager Web 服务设置 Intune 证书连接器

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文介绍如何安装和配置 Intune 证书连接器，以便从 Symantec PKI Manager Web 服务向 Intune 管理的设备颁发 PKCS 证书。

Symantec PKI Manager Web 服务在本文中称为 Symantec CA。 如果你已配置 Intune 证书连接器，以从 Microsoft 证书颁发机构 (CA) 颁发 PKCS 证书和 SCEP 证书，则可以使用相同的连接器来从 Symantec CA 配置和颁发 PKCS 证书。 在这种情况下，Intune 证书连接器可以颁发以下证书：

* 来自 Microsoft CA 的 PKCS 证书
* 来自 Microsoft CA 的 SCEP 证书
* 来自 Symantec CA 的 PKCS 证书

如果你想要将 Intune 证书连接器用于 Microsoft CA 和 Symantec CA，则必须先完成 Microsoft CA 的 Intune 证书连接器配置，然后执行以下步骤将其配置用于 Symantec CA。  有关配置 Microsoft CA 的 Intune 证书连接器的详细信息，请参阅[如何在 Microsoft Intune 中配置证书](certificates-configure.md)。

## <a name="prepare-to-install-intune-certificate-connector"></a>准备安装 Intune 证书连接器

如果你已为现有 Microsoft CA 使用 Intune 证书连接器，并且想要添加 Symantec CA 支持，则跳过此步骤，并从 Intune 管理门户安装最新的 Intune 证书连接器之后继续剩余步骤。 仅当你希望独立为 Symantec CA 使用 Intune 证书连接器时，才需要执行此步骤。

1. 从以下列表中选择一个 Windows 操作系统版本，并将其安装在计算机上：
   * Windows Server 2012 R2 Datacenter
   * Windows Server 2012 R2 Standard
   * Windows Server 2016 Datacenter
   * Windows Server 2016 标准版

2. 创建具有管理权限的用户，并使用它来完成以下步骤。

3. 更新以获取最新 Windows 更新并进行安装（如果存在）。

   > [!IMPORTANT]
   > 安装 Windows 更新之后，重新启动计算机。

4. 安装 .NET Framework 3.5：

    a. 打开“控制面板” > “程序和功能” > “启用或关闭 Windows 功能”

    b. 选择“.NET Framework 3.5”并安装。

## <a name="install-the-symantec-registration-authorization-certificate"></a>安装 Symantec 注册授权证书

使用以下步骤从 Symantec CA 获取注册授权 (RA) 证书。 必须在 Symantec CA 具有有效订阅才能获取 RA 证书。

1. 将以下代码片段保存到名为 certreq.ini 的文件，并根据需要进行更新（例如：CN 格式的使用者名称）。

   ```
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
   ```

2. 打开提升的命令提示符并使用以下命令生成 CSR 内容：

   `Certreq.exe -new certreq.ini request.csr`

3. 在记事本中打开 request.csr 文件，并复制以下格式的 CSR 内容：

    ```
    -----BEGIN NEW CERTIFICATE REQUEST-----
    MIID8TCCAtkCAQAwbTEMMAoGA1UEBhMDVVNBMQswCQYDVQQIDAJXQTEQMA4GA1UE
    …
    …
    fzpeAWo=
    -----END NEW CERTIFICATE REQUEST-----
    ```

4. 登录到 Symantec CA 并从任务导航到“获取 RA 证书”。

   a. 从步骤 3 开始在指定文本框中提供 CSR 内容。

   b. 在指定文本框中提供证书友好名称。

   c. 单击“继续” 。

      将显示 RA 证书的可下载链接。

   d. 将 RA 证书下载到本地计算机。

5. 将 RA 证书导入到 Windows 证书存储中：

    a. 打开 MMC 控制台。

    b. 单击“文件” > “添加或删除管理单元” > “证书”> 然后单击“添加”。

    c. 选择“计算机帐户”，然后单击“下一步”。

    d. 选择“本地计算机”，然后单击“完成”。

    e. 在“添加或删除管理单元”窗口上单击“确定”。展开“证书(本地计算机)” > “个人” > “证书”。

    f. 右键单击“证书”节点，然后选择“所有任务” > “导入”。

    g. 选择从 Symantec CA 下载 RA 证书的位置，然后单击“下一步”。

    h. 选择“个人证书存储”，然后单击“下一步”。

    i. 单击“完成” 。 这会将 RA 证书及其私钥导入本地计算机个人存储。  

6. 导出和导入私钥证书：

    a. 展开“证书(本地计算机)” > “个人” > “证书”。

    b. 选择在上一步中已导入的证书。

    c. 右键单击证书并选择“所有任务” > “导出”。

    d. 单击“下一步”并键入密码。

    e. 选择要导出到的位置，然后单击“完成”。

    f. 按照步骤 5 中的相同过程，将私钥证书导入本地计算机个人存储中。

7. 复制 RA 证书指纹（不含任何空格）。  下面是一个示例指纹：

   ```
   RA Cert Thumbprint: “EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5”
   ```


   > [!NOTE]
   > 如果从 Symantec CA 获取 RA 证书存在任何问题，请联系 Symantec 客户支持部门。

## <a name="install-intune-certificate-connector"></a>安装 Intune 证书连接器

如果你已对现有 Microsoft CA 使用最新的 Intune 证书连接器，并想要添加 Symantec CA 支持，则跳过此步骤。 否则，从 Intune 管理门户下载最新的 Intune 证书连接器，然后按照以下说明操作。

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 在“Intune”窗格上，选择“设备配置”。
4. 在“设备配置”窗格上，选择“证书颁发机构”。
5. 单击“添加”并选择“下载连接器文件”。 将下载的文件保存到可以从服务器上进行访问的位置，将在该服务器上安装该应用程序。 
3. 使用提升的权限运行 NDESConnectorSetup.exe。

    a. 在“安装选项”屏幕上，选择“PFX 分发”如以下屏幕截图所示。  使用默认选择完成剩余设置。

   > [!IMPORTANT]
   > 如果你想要配置 Intune 证书连接器，以便从 Microsoft CA 和 Symantec CA 颁发证书，请选择“SCEP 和 PFX 配置文件分发”。 使用默认选择完成剩余设置。

   ![InstallConnector][InstallConnector]
 
## <a name="configure-intune-certificate-connector"></a>配置 Intune 证书连接器

默认情况下，Intune 证书连接器安装在 `%ProgramFiles%\Microsoft Intune`。

1. 在记事本中打开 %ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config 文件。

    a. 使用上一节中复制的证书指纹值更新 RACertThumbprint 密钥值。  以下是一个示例：

   ```
   <add key="RACertThumbprint"
   value="EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5"/>
   ```

    b. 保存并关闭该文件。

2. 打开 services.msc。

    a. 选择“Intune 连接器服务”。

    b. 停止此服务，然后再次启动。

    c. 关闭“服务”窗口。

## <a name="setup-the-intune-administrator-account"></a>设置 Intune 管理员帐户

如果你已对现有 Microsoft CA 使用 Intune 证书连接器，并想要添加 Symantec CA 支持，则跳过此步骤，继续执行剩余步骤。 

1. 从 ` %ProgramFiles%\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe ` 启动 NDES 连接器用户界面

    a. 单击“注册”选项卡，然后单击“登录”。

    b. 在指定文本框中提供你的 Intune 租户管理员凭据。

    c. 单击“登录”。  它将显示包含“已成功注册”消息的确认对话框如以下屏幕截图所示。
2. 关闭 NDES 连接器用户界面。

![ConfigureConnector][ConfigureConnector]
 
## <a name="create-a-trusted-certificate-profile"></a>创建受信任的证书配置文件

为 Intune 受管理设备部署的 PKCS 证书必须使用受信任的根证书进行链接。 这需要你使用从 Symantec CA 获取的根证书创建 Intune 受信任的证书配置文件。

1. 从 Symantec CA 中获取受信任的根证书：

    a. 登录到 Symantec CA 管理门户。

    b. 从任务单击“管理 CA”：

    c. 从 CA 列表中选择相应的 CA。

    d. 单击“下载根证书”来下载受信任的根证书。

2. 在 Intune 管理门户中创建受信任的证书配置文件：

    a. 使用 Intune 租户管理员凭据登录到 [Azure 门户](https://portal.azure.com)，然后搜索 Intune 资源。

    b. 通过访问“Microsoft Intune” > “设备配置” > “配置文件” > “创建配置文件”，创建受信任的证书配置文件。

    c. 在“名称”和“说明”字段提供所需的信息，然后选择目标平台。 

    d. 从“配置文件类型”类型下拉列表中选择“受信任的证书”。

    e. 上载在上一步中从 Symantec CA 获得的受信任的根证书。

    f. 完成剩余的配置文件创建步骤。 

    g. 单击“分配”然后选择适当的组。  至少一个用户或设备必须成为已分配组的一部分。

## <a name="get-the-certificate-profile-oid"></a>获取证书配置文件 OID

证书配置文件 OID 与 Symantec CA 中的证书配置文件模板相关联。  若要在 Intune 管理门户中创建 PKCS 证书配置文件，则证书模板名称必须以证书配置文件 OID 的形式提供，该 OID 与 Symantec CA 中的证书模板相关联。

1. 登录到 Symantec CA 管理门户。
2. 单击“管理证书配置文件”。
3. 选择要使用的证书配置文件。
4. 复制证书配置文件 OID。 这类似于以下示例：

   ```
   Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109 
   ```

   > [!NOTE]
   > 如果获取证书配置文件 OID 时出现任何问题，请联系 Symantec 客户支持部门。

## <a name="create-a-pkcs-certificate-profile"></a>创建 PKCS 证书配置文件

1. 使用 Intune 租户管理员凭据登录到 [Azure 门户](https://portal.azure.com)，然后搜索 Intune 资源。
2. 通过访问“Microsoft Intune” > “设备配置”>“配置文件” > “创建配置文件”，创建 PKCS 证书配置文件。

    a. 在“名称”和“说明”字段提供所需的信息，然后选择目标平台。

    b. 从“配置文件类型”下拉列表中选择“PKCS 证书配置文件”。  

    c. 完成其余步骤来创建配置文件。

   ![ConfigureProfile][ConfigureProfile]

   > [!IMPORTANT]
   > PKCS 证书配置文件的以下参数必须使用下表中的指定值配置（如屏幕截图所示），以便从 Symantec CA 通过 Intune 证书连接器颁发 PKCS 证书。 

    |PKCS 证书参数 | 值 | 描述 |
    | --- | --- | --- |
    | 证书颁发机构 | pki-ws.symauth.com | 此值必须是不带结尾斜杠的 Symantec CA 基本服务 FQDN。  如果不确定这是否为 Symantec CA 订阅的正确基本服务 FQDN，请联系 Symantec 客户支持部门。 <br><br> 如果此 FQDN 不正确，则 Intune 证书连接器不会从 Symantec CA 颁发 PKCS 证书。| 
    | 证书颁发机构名称 | Symantec | 此值必须是字符串 Symantec。 <br><br> 如果对此值进行任何更改，则 Intune 证书连接器将不会从 Symantec CA 颁发 PKCS 证书。|
    | 证书模板名称 | 来自 Symantec CA 的证书配置文件 OID。 <br><br> 示例：`2.16.840.1.113733.1.16.1.2.3.1.1.61904612`| 该值必须是上一节从 Symantec CA 证书配置文件模板中获取的证书配置文件 OID。 <br><br> 如果 Intune 证书连接器在 Symantec CA 中找不到与此证书配置文件 OID 关联的证书模板，则它不会从 Symantec CA 颁发 PKCS 证书。|

   > [!NOTE]
   > Windows 平台的 PKCS 证书配置文件不需要与受信任的证书配置文件相关联。 但是非 Windows 平台配置文件（如 Android）则必须关联。

3. 单击“分配”然后选择适当的组。  至少一个用户或设备必须成为已分配组的一部分。
 
完成前面的步骤之后，Intune 证书连接器将从 Symantec CA 向所分配组中的 Intune 管理设备颁发 PKCS 证书。 这些证书将在 Intune 管理设备上的当前用户证书存储的个人存储中可用。

### <a name="pkcs-certificate-profile-supported-attributes"></a>PKCS 证书配置文件支持的属性

|属性 | Intune 支持的格式 | Symantec 云 CA 支持的格式 | 结果 |
| --- | --- | --- | --- |
| 使用者名称 |Intune 仅支持以下三种格式的使用者名称： <br><br> 1.公用名 <br> 2.包含电子邮件地址的公用名称 <br> 3.作为电子邮件地址的公用名称 <br><br> 以下是一个示例： <br><br> `CN = IWUser0 <br><br> E = IWUser0@samplendes.onmicrosoft.com` | Symantec CA 支持其他属性。  如果要选择其他属性，则必须在 Symantec 证书配置文件模板中使用固定值来定义它们。| 我们使用公用名或来自 PKCS 证书请求的电子邮件。 <br><br> Intune 证书配置文件和 Symantec 证书配置文件模板之间的任何属性选择不匹配都会导致无法从 Symantec CA 颁发证书。|
| SAN | Intune 仅支持以下 SAN 字段值： <br><br> AltNameTypeEmail <br><br> AltNameTypeUpn <br><br> AltNameTypeOtherName（编码值） | Symantec 云 CA 也支持这些参数。 如果要选择其他属性，则必须在 Symantec 证书配置文件模板中使用固定值来定义它们。 <br><br> AltNameTypeEmail：如果在 SAN 中未找到此类型，则使用 AltNameTypeUpn 的值。  如果在 SAN 中也未找到 AltNameTypeUpn，则使用“使用者名称”的值（如果其是电子邮件格式）。  如果仍未找到，Intune 证书连接器将无法颁发证书。 <br><br> 示例：`RFC822 Name=IWUser0@ndesvenkatb.onmicrosoft.com`  <br><br> AltNameTypeUpn：如果在 SAN 中找不到此类型，则使用 AltNameTypeEmail 的值。 如果在 SAN 中也找不到 AltNameTypeEmail，则使用“使用者名称”的值（如果其是电子邮件格式）。  如果仍未找到，Intune 证书连接器将无法颁发证书。  <br><br> 示例：`Other Name: Principal Name=IWUser0@ndesvenkatb.onmicrosoft.com` <br><br> AltNameTypeOtherName：如果在 SAN 中找不到此类型，Intune 证书连接器将无法颁发证书。 <br><br> 示例：`Other Name: DS Object Guid=04 12 b8 ba 65 41 f2 d4 07 41 a9 f7 47 08 f3 e4 28 5c ef 2c` <br><br>  重要注意事项：对于此字段，Symantec CA 仅支持编码格式的值（十六进制值）。 因此，对于此字段中的任何值，Intune 证书连接器在提交证书请求之前会将其转换为 Base 64 编码。 Intune 证书连接器不会验证此值是否已编码。 | 无 |

## <a name="troubleshooting"></a>疑难解答

Intune 证书连接器服务日志位于 NDES 连接器计算机上的 `%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\Logs\Logs` 中。 打开 [SvcTraceViewer](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) 中的日志，然后搜索异常或错误消息。

| 问题/错误消息 | 解决步骤 |
| --- | --- |
| 无法使用 NDES 连接器 UI 上的 Intune 租户管理员帐户登录 | Intune 管理门户中未启用本地证书连接器时，可能会发生这种情况。 要解决此问题，请执行以下步骤： <br><br> 从 Silver Light UI： <br> 1.登录到 [Intune 管理门户](https://admin.manage.microsoft.com) <br> 2.单击“管理” <br> 3.选择“移动设备管理”>“证书连接器” <br> 4.单击“配置本地证书连接器”。 <br> 5.选择“启用证书连接器”复选框。 <br> 6.单击“确定” 。 <br><br>或 <br><br> 从 Azure 门户 UI： <br> 1.登录到 [Azure 门户](https://portal.azure.com) <br> 2.转到 Microsoft Intune <br> 3.选择“设备配置” > “证书颁发机构” <br> 4.单击“启用”。 <br><br> 在从 Silver Light UI 或 Azure 门户完成前述步骤之后，尝试使用相同的 Intune 租户管理员帐户登录 NDES 连接器 UI。 |
| 找不到 NDES 连接器证书。 <br><br> System.ArgumentNullException: 值不能为 null。 | 如果 Intune 租户管理员帐户从未登录到 NDES 连接器 UI，则 Intune 证书连接器会显示此错误。 <br><br> 如果此错误仍然存在，请重新启动 Intune 服务连接器。 <br><br> 1.打开 services.msc <br> 2.选择“Intune 连接器服务”。 <br> 3.单击右键并选择“重新启动”。|
| NDES 连接器 - IssuePfx - 常规异常： <br> System.NullReferenceException: 对象引用未设置为某个对象的实例。 | 此错误是暂时的。 重新启动 Intune 服务连接器。 <br><br> 1.打开 services.msc <br> 2.选择“Intune 连接器服务”。 <br> 3.单击右键并选择“重新启动”。 |
| Symantec 提供程序 - 无法获取 Symantec 策略，“操作已超时” | Intune 证书连接器在与 Symantec CA 通信时收到“操作已超时”错误。 如果此错误继续出现，请增加连接超时值并重试。 <br><br> 要增加连接超时值： <br> 1.转到 NDES 连接器计算机。 <br>2.在记事本中打开 `%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config` 文件。 <br> 3.增加以下参数的超时值： <br><br> `CloudCAConnTimeoutInMilliseconds` <br><br> 4.重新启动 Intune 连接器服务。 <br><br> 如果问题仍然存在，请联系 Symantec 客户支持部门。 |
| Symantec 提供程序 - 无法获取客户端证书 | Intune 证书连接器从“本地计算机 - 个人证书存储”中检索不到资源授权证书。 要解决此问题，请确保将资源授权证书连同其私钥一起安装在“本地计算机-个人证书存储”中。 <br><br> 注意：资源授权证书必须从 Symantec CA 获取。 有关详细信息，请联系 Symantec 客户支持部门。 | 
| Symantec 提供程序 - 无法获取 Symantec 策略，“请求已中止: 未能创建 SSL/TLS 安全通道”。 | 在以下情况下会发生此错误： <br><br> 1.Intune 证书连接器服务没有足够的权限从“本地计算机-个人证书存储”中读取资源授权证书及其私钥。 要解决此问题，请检查在 services.msc 中运行上下文帐户的连接器服务。 该连接器服务必须在 NT AUTHORITY\SYSTEM 上下文下运行。 <br><br> 2.Intune 管理门户中的 PKCS 证书配置文件在配置时可能使用了无效的 Symantec CA 基本服务 FQDN。 FQDN 类似于 `pki-ws.symauth.com`。 要解决此问题，请咨询 Symantec 客户支持部门，以确定该 URL 是否适合你的订阅。 <br><br> 3.Intune 证书连接器无法使用资源授权证书对 Symantec CA 进行身份验证，因为它无法检索证书私钥。 要解决此问题，请确保将资源授权证书连同其私钥一起安装在“本地计算机-个人证书存储”中。 <br><br> 如果问题仍然存在，请联系 Symantec 客户支持部门。 |
| Symantec 提供程序 - 无法获取 Symantec 策略，“不理解请求元素。” | Intune 证书连接器无法获取 Symantec 证书配置文件模板，因为客户端配置文件 OID 与 Intune 证书配置文件不匹配。 在其他情况下，Intune 证书连接器无法找到与 Symantec CA 中给定客户端配置文件 OID 关联的证书配置文件模板。 <br><br> 要解决此问题，请确保从 Symantec CA 的 Symantec 证书模板获取正确的客户端配置文件 OID。 然后更新 Intune 管理门户中的 PKCS 证书配置文件。 <br><br> 获取来自 Symantec CA 的客户端配置文件 OID： <br> 1.登录到 Symantec CA 管理门户。 <br> 2.单击“管理证书配置文件” <br> 3.选择要使用的证书配置文件。 <br> 4.获取证书配置文件 OID。 这类似于以下示例： <br> `Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109` <br><br> 使用正确的证书配置文件 OID 更新 PKCS 证书配置文件： <br>1.登录到 Intune 管理门户 <br> 2.转到 PKCS 证书配置文件并单击“编辑”。 <br> 3.在“证书模板名称”字段中更新证书配置文件 OID。 <br> 4.保存 PKCS 证书配置文件。 |
| Symantec 提供程序 - 策略验证失败。 <br><br> 属性不属于 Symantec 支持的证书模板属性列表 | 当 Symantec 证书配置文件模板和 Intune 证书配置文件之间存在差异时，Symantec CA 将显示此消息。 SubjectName 或 SubjectAltName 中的属性不匹配时，可能会发生此问题。 <br><br> 要解决此问题，请确保在 Symantec 证书配置文件模板中为 SubjectName 和 SubjectAltName 选择 Intune 支持的属性。 有关详细信息，请参阅“证书参数”一节中的 Intune 支持的属性。 |
| 某些用户设备不接收来自 Symantec CA 的 PKCS 证书。 | 当用户 UPN 包含特殊字符（如下划线）时会发生此问题（示例：`global_admin@intune.onmicrosoft.com`）。 <br><br> Symantec CA 不支持 mail_firstname 和 mail_lastname 中的特殊字符。 <br><br> 请执行以下步骤来帮助解决此问题： <br><br> 1. 登录到 Symantec CA 管理门户。 <br> 2.转到“管理证书配置文件”。 <br> 3. 单击用于 Intune 的证书配置文件。 <br> 4.单击自定义选项链接。 <br> 5. 单击“高级选项”按钮。 <br> 6.在证书字段 – 使用者 DN 下，添加公用名 (CN) 字段并删除现有公用名 (CN) 字段。 添加和删除操作必须一起执行。 <br> 7.  单击“保存”。 <br><br> 通过上述更改，Symantec 证书配置文件会请求“CN=<upn>”而不是 mail_firstname 和 mail_lastname。 |
| 用户从设备手动删除已部署的证书。 | Intune 将在下一步的签入或策略实施过程中重新部署相同的证书。 在这种情况下，NDES 连接器不会收到 PKCS 证书请求。 |

## <a name="next-steps"></a>后续步骤

- 使用本文中提供的信息以及[什么是 Microsoft Intune 设备配置文件？](device-profiles.md)中的信息来管理组织的设备及设备上的证书。

[InstallConnector]:  ./media/certificates-symantec-connector-install.png "安装 Intune 证书连接器并选择 PFX 分发"
[ConfigureConnector]: ./media/certificates-symantec-configure-connector-configure.png "配置 Intune 证书连接器"
[ConfigureProfile]: ./media/certificates-symantec-pkcs-example.png "在 Azure 门户中创建 PKCS 证书配置文件"
