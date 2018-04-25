---
title: 在 Microsoft Intune 中使用 SCEP 证书 - Azure | Microsoft Docs
description: 要在 Microsoft Intune 中使用 SCEP 证书，请配置本地 AD 域，创建证书颁发机构，设置 NDES 服务器，并安装 Intune 证书连接器。 然后创建 SCEP 证书配置文件并将此配置文件分配到组。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: kmyrup
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dabf8d67b4d0bd7252f306d6b21949cf501eca8d
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="configure-and-use-scep-certificates-with-intune"></a>在 Intune 中配置和使用 SCEP 证书

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文说明如何配置基础结构，然后使用 Intune 创建和分配简单证书注册协议 (SCEP) 证书配置文件。

## <a name="configure-on-premises-infrastructure"></a>配置本地基础结构

- **Active Directory 域**：此部分中列出的所有服务器（Web 应用程序代理服务器除外）都必须加入 Active Directory 域。

- **证书颁发机构** (CA)：在 Windows Server 2008 R2 企业版或更高版本上运行的企业证书颁发机构 (CA)。 不支持独立 CA。 有关详细信息，请参阅[安装证书颁发机构](http://technet.microsoft.com/library/jj125375.aspx)。
    如 CA 运行的是 Windows Server 2008 R2，则必须[安装修补程序 KB2483564](http://support.microsoft.com/kb/2483564/)。

- **NDES 服务器**：在运行 Windows Server 2012 R2 或更高版本的服务器上，必须设置网络设备注册服务 (NDES)。 如果在服务器上运行了企业 CA，则同时在该服务器上运行的 Intune 将不支持使用 NDES。 有关如何配置 Windows Server 2012 R2 以托管网络设备注册服务的说明，请参阅[网络设备注册服务指南](http://technet.microsoft.com/library/hh831498.aspx)。
NDES 服务器必须以域加入到托管 CA 的域，且不能与 CA 位于同一服务器上。 有关在单独的林、独立的网络或内部的域中部署 NDES 服务器的详细信息，可查阅[结合使用策略模块和网络设备注册服务](https://technet.microsoft.com/library/dn473016.aspx)。

- **Microsoft Intune 证书连接器**：使用 Azure 门户下载“证书连接器”安装程序 (ndesconnectorssetup.exe)。 然后可以在你想在其上安装证书连接器的承载了网络设备注册服务 (NDES) 角色的服务器上运行 ndesconnectorssetup.exe。 
- **Web 应用程序代理服务器**（可选）：使用运行 Windows Server 2012 R2 或更高版本的服务器作为 Web 应用程序代理 (WAP) 服务器。 该配置：
  -  允许设备使用 Internet 连接接收证书。
  -  是设备通过 Internet 连接接收和续订证书时的安全建议。

> [!NOTE]
> - 承载 WAP 的服务器[必须安装此更新](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx)以支持网络设备注册服务所使用的长 URL。 该更新包括在 [2014 年 12 月的更新汇总中](http://support.microsoft.com/kb/3013769)，或单独更新自 [KB3011135](http://support.microsoft.com/kb/3011135)。
> - WAP 服务器必须具有与将要向外部客户端发布的名称相匹配的 SSL 证书，并且信任 NDES 服务器上使用的 SSL 证书。 这些证书使 WAP 服务器可以终止来自客户端的 SSL 连接，并创建至 NDES 服务器的新 SSL 连接。
> 
>   有关 WAP 证书的信息，请参阅[规划证书](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383650(v=ws.11)#plan-certificates)。
> 
>   有关 WAP 服务器的一般信息，请参阅[使用 Web 应用程序代理](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn584113(v=ws.11))。

### <a name="network-requirements"></a>网络要求

从 Internet 到外围网络，从所有主机或 Internet 上的 IP 地址到 NDES 服务器，都支持 443 端口。

从外围网络到受信任网络，支持域对已加入域的 NDES 服务器进行访问所需的所有端口和协议。 NDES 服务器需要证书服务器、DNS 服务器、Configuration Manager 服务器和域控制器的访问权限。

建议通过代理（例如，[Azure AD 应用程序代理](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/)、[Web Access 代理](https://technet.microsoft.com/library/dn584107.aspx)或第三方代理）发布 NDES 服务器。

### <a name="certificates-and-templates"></a>证书和模板

|对象|详细信息|
|----------|-----------|
|**证书模板**|在发证 CA 上配置此模板。|
|**客户端身份验证证书**|发证 CA 或公共 CA 请求；在 NDES 服务器上安装证书。|
|**服务器身份验证证书**|发证 CA 或公共 CA 请求；在 NDES 服务器上的 IIS 中安装并绑定该 SSL 证书。|
|**受信任的根 CA 证书**|可以从根 CA 或信任该根 CA 的任何设备中将该证书导出为 .cer 文件，并通过使用可信 CA 证书配置文件将其分配到设备。<br /><br />你可以在每个操作系统平台上使用一个受信任的根 CA 证书，并将其与你创建的每个受信任的根证书配置文件相关联。<br /><br />你可以在需要时使用其它受信任的根 CA 证书。 例如，你可以这样做来信任为 Wi-Fi 访问点的服务器身份验证证书签名的 CA。|

### <a name="accounts"></a>帐户

|名称|详细信息|
|--------|-----------|
|**NDES 服务帐户**|输入用作 NDES 服务帐户的域用户帐户。|

## <a name="configure-your-infrastructure"></a>配置你的基础结构
配置证书配置文件前，请完成以下任务。 完成这些任务需要 Windows Server 2012 R2 和 Active Directory 证书服务 (ADCS) 方面的知识：

**步骤 1**：创建 NDES 服务帐户

**步骤 2**：配置证书颁发机构上的证书模板

**步骤 3**：在 NDES 服务器上配置必备组件

**步骤 4**：配置 NDES 以与 Intune 一起使用

**步骤 5**：启用、安装和配置 Intune 证书连接器

#### <a name="step-1---create-an-ndes-service-account"></a>步骤 1 - 创建 NDES 服务帐户

创建用作 NDES 服务帐户的域用户帐户。 安装和配置 NDES 之前，在配置发证 CA 上的模板时输入该帐户。 确保用户具有默认权限，即“本地登录”、“作为服务登录”和“作为批处理作业登录”的权限。 某些组织已采用强化策略禁用这些权限。

#### <a name="step-2---configure-certificate-templates-on-the-certification-authority"></a>步骤 2 - 配置证书颁发机构上的证书模板
在此任务中完成以下操作：

- 配置 NDES 证书模板
- 发布 NDES 证书模板

##### <a name="configure-the-certification-authority"></a>配置证书颁发机构

1. 以企业管理员身份登录。

2. 在发证 CA 上，使用“证书模板”管理单元创建新的自定义模板。 或者，复制现有模板，然后更新现有模板（如用户模板）以与 NDES 配合使用。

   >[!NOTE]
   > NDES 证书模板必须基于 v2 证书模板（具有 Windows 2003 兼容性）。

   模板必须进行以下配置：

   - 为模板输入友好的“模板显示名称”。

   - 在“使用者名称”处，选择“在请求中提供”。 （由适用于 NDES 的 Intune 策略模块强制实施安全措施）。

   - 在“扩展”选项卡上，确认“应用程序策略描述”包括“客户端身份验证”。

     > [!IMPORTANT]
     > 对于 iOS 和 macOS 证书模板，在“扩展”选项卡上编辑“密钥用法”，并确认未选择“数字签名为原件的证明”。

   - 在“安全性”选项卡上，添加 NDES 服务帐户，并授予它“注册”模板的权限。 将创建 SCEP 配置文件的 Intune 管理员需要“读取”权限，以便在创建 SCEP 配置文件时可以浏览到该模板。

     > [!NOTE]
     > 若要吊销证书，NDES 服务帐户需要针对证书配置文件所用的每个证书模板具有“颁发和管理证书”权限。

3. 在模板的“常规”选项卡上查看“有效期”。 默认情况下，Intune 使用模板中配置的值。 但是，可以视需要将 CA 配置为允许申请者输入其他值，随后便能够在 Intune 管理员控制台中设置此值。 如果你想要一直使用模板中的值，跳过该步骤的其余部分即可。

   > [!IMPORTANT]
   > iOS 和 macOS 始终使用模板中设置的值，无论你设置的其他配置如何。

示例模板配置：

![模板，“请求处理”选项卡](./media/scep_ndes_request_handling.png)

![模板，“使用者名称”选项卡](./media/scep_ndes_subject_name.jpg)

![模板，“安全”选项卡](./media/scep_ndes_security.jpg)

![模板，“扩展”选项卡](./media/scep_ndes_extensions.jpg)

![模板，“颁发要求”选项卡](./media/scep_ndes_issuance_reqs.jpg)

> [!IMPORTANT]
> 对于应用程序策略，只添加所需的应用程序策略即可。 与你的安全管理员确认你的选择。

配置 CA 以允许申请者输入有效期：

1. 请在 CA 上运行以下命令：
   - **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**
   - **net stop certsvc**
   - **net start certsvc**

2. 在发证 CA 上，使用证书颁发机构管理单元发布证书模板。
   选择“证书模板”节点，单击“操作” > “新建” > “要颁发的证书模板”，然后选择在步骤 2 中创建的模板。

3. 通过查看“证书模板”文件夹下已发布的模板来对它进行验证。

#### <a name="step-3---configure-prerequisites-on-the-ndes-server"></a>步骤 3 - 在 NDES 服务器上配置必备组件
在此任务中完成以下操作：

- 将 NDES 添加到 Windows Server 并配置 IIS 以支持 NDES
- 将 NDES 服务帐户添加到 IIS_IUSR 组
- 为 NDES 服务帐户设置 SPN

1. 在承载 NDES 的服务器上安装 NDES 时，以“企业管理员”身份登录，然后使用[添加角色和功能向导](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831809(v=ws.11))：

   1. 在向导中，选择“Active Directory 证书服务”以获得对 AD CS 角色服务的访问权限。 选择“网络设备注册服务”，取消选择“证书颁发机构”，然后完成向导。

      > [!TIP]
      > 在“安装进度”处，不要勾选“关闭”。 而是选择“配置目标服务器上的 Active Directory 证书服务”的链接。 “AD CS 配置”向导将会打开，此配置将用于下一个任务。 打开“AD CS 配置”后，你可以关闭“添加角色和功能”向导。

   2. 将 NDES 添加到服务器后，向导也会安装 IIS。 确保 IIS 具有以下配置：

   3. “Web 服务器” > “安全性” > “请求筛选”

   4. “Web 服务器” > “应用程序开发” > “ASP.NET 3.5”。 安装 ASP.NET 3.5 会安装 .NET Framework 3.5。 安装 .NET Framework 3.5 时，安装核心“.NET Framework 3.5”功能和“HTTP 激活”。

   5. “Web 服务器” > “应用程序开发” > “ASP.NET 4.5”。 安装 ASP.NET 4.5 会安装 .NET Framework 4.5。 安装 .NET Framework 4.5 时，安装核心“.NET Framework 4.5”功能、“ASP.NET 4.5”和“WCF 服务” > “HTTP 激活”功能。

   6. “管理工具” > “IIS 6 管理兼容性” > “IIS 6 元数据库兼容性”

   7. “管理工具” > “IIS 6 管理兼容性” > “IIS 6 WMI 兼容性”

   8. 在服务器上，将 NDES 服务帐户添加为“IIS_IUSR”组成员。

2. 在提升的命令指示符处，运行以下命令以设置 NDES 服务帐户的 SPN：

    `setspn -s http/<DNS name of NDES Server> <Domain name>\<NDES Service account name>`

    例如，如果 NDES 服务器名为 Server01，你的域为 Contoso.com，并且服务帐户为 NDESService，则使用：

    `setspn –s http/Server01.contoso.com contoso\NDESService`

#### <a name="step-4---configure-ndes-for-use-with-intune"></a>步骤 4 - 配置 NDES 以与 Intune 一起使用
在此任务中完成以下操作：

- 配置 NDES 以与发证 CA 一起使用
- 在 IIS 绑定服务器身份验证 (SSL) 证书
- 在 IIS 中配置请求筛选

1. 在 NDES 服务器上，打开“AD CS 配置”向导，然后进行以下更新：

    > [!TIP]
    > 如果你在上一任务中单击了该链接，则此向导已经打开。 或者，打开“服务器管理器”访问“Active Directory 证书服务”的后期部署配置。

   - 在“角色服务”页面，选择“网络设备注册服务”
   - 在“NDES 的服务帐户”页面，输入 NDES 服务帐户
   - 在“NDES 的 CA”页面，单击“选择”，然后选择在其中配置证书模板的发证 CA
   - 在“为 NDES 加密”页面，设置符合公司要求的秘钥长度。
   - 在“确认”页面，选择“配置”，完成向导。

2. 完成向导后，在 NDES 服务器上更新以下注册表项：

    `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\`

    要更新此密钥，请标识证书模板的“目的”（位于“请求处理”选项卡上）。 然后，通过将现有数据替换为在“任务 1”中指定的证书模板的名称（不是模板的显示名称），更新对应的注册表项。 下表将证书模板目的映射至注册表中的值：

    |证书模板目的（位于“请求处理”选项卡上）|待编辑的注册表值|在 Intune 管理控制台中显示的 SCEP 配置文件的值|
    |---|---|---|
    |签名|SignatureTemplate|数字签名|
    |加密|EncryptionTemplate|密钥加密|
    |签名和加密|GeneralPurposeTemplate|密钥加密<br/>数字签名|

    例如，如果证书模板的目的为“加密”，然后将“EncryptionTemplate”值编辑为你的证书模板的名称。

3. NDES 服务器收到长 URL（查询），要求添加两个注册表项：


   |                        位置                        |      值      | 类型  |      数据       |
   |--------------------------------------------------------|-----------------|-------|-----------------|
   | HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters | MaxFieldLength  | DWORD | 65534（十进制） |
   | HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters | MaxRequestBytes | DWORD | 65534（十进制） |


4. 在 IIS 管理器中，选择“默认网站” > “请求筛选” > “编辑功能设置”。 将“URL 最大长度”和“最大查询字符串”更改为“65534”，如下所示：

    ![IIS 的最大 URL 长度和最大查询长度](./media/SCEP_IIS_max_URL.png)

5. 重新启动服务器。 在服务器上运行 iisreset 不足以完成这些更改。
6. 浏览到 `http://*FQDN*/certsrv/mscep/mscep.dll`。 应看到与下图类似的 NDES 页面：

    ![测试 NDES](./media/SCEP_NDES_URL.png)

    如果你收到“503 服务不可用”的信息，请查看事件查看器。 可能是因 NDES 用户缺少权限导致应用程序池停止。 任务 1 中描述了这些权限。

##### <a name="install-and-bind-certificates-on-the-ndes-server"></a>在 NDES 服务器上安装和绑定证书

1. 在你的 NDES 服务器上，请求并安装来自你的内部 CA 或公共 CA 的“服务器身份验证”证书。 随后绑定 IIS 中的 SSL 证书。

    > [!TIP]
    > 绑定 IIS 中的 SSL 证书后，安装客户端身份验证证书。 该证书可以由 NDES 服务器信任的任何 CA 颁发。 尽管这不是最佳做法，但可以对服务器和客户端身份验证使用相同的证书，只要证书具备两个增强型密钥使用 (EKU) 即可。 查看以下步骤以获得有关这些身份验证证书的信息。

   1. 获取服务器身份验证证书后，打开“IIS 管理器”，然后选择“默认网站”。 在“操作”窗格中，选择“绑定”。

   2. 选择“添加”，将“类型”设置为“https”并确认端口为“443”。 独立 Intune 仅支持端口 443。

   3. 为“SSL 证书”输入服务器身份验证证书。

      > [!NOTE]
      > 如果 NDES 服务器对单个网络地址使用外部和内部名称，则服务器身份验证证书必须具有：
      > - **使用者名称**（包括外部公共服务器名称）
      > - **使用者可选名称**（包括内部服务器名称）

2. 在你的 NDES 服务器上，请求并安装来自你的内部 CA 或公用证书颁发机构的“客户端身份验证”证书。 该证书可以与服务器身份验证的证书相同，如果证书具有这两个功能。

    客户端身份验证证书必须具备以下属性：

    - **增强型密钥使用**：此值必须包括“客户端身份验证”

    - **使用者名称**：此值必须与安装证书的服务器（NDES 服务器）的 DNS 名称相同

##### <a name="configure-iis-request-filtering"></a>配置 IIS 请求筛选

1. 在 NDES 服务器上打开“IIS 管理器”，在“连接”窗格中选择“默认网站”，然后打开“请求筛选”。

2. 选择“编辑功能设置”，然后设置值：

    - **查询字符串(字节)** = **65534**
    - **最大 URL 长度(字节)** = **65534**

3. 查看以下注册表：

    `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters`

    确认以下值都设置为 DWORD 值：

    - 名称：“MaxFieldLength” ，十进制值为 65534
    - 名称：“MaxRequestBytes” ，十进制值为 65534

4. 重新启动 NDES 服务器。 服务器现已支持证书连接器。

#### <a name="step-5---enable-install-and-configure-the-intune-certificate-connector"></a>步骤 5 - 启用、安装和配置 Intune 证书连接器
在此任务中完成以下操作：

- 在 Intune 中启用对 NDES 的支持。
- 在承载环境中的网络设备注册服务 (NDES) 角色的服务器上下载、安装和配置证书连接器。 为提高组织中 NDES 实现的缩放性，可安装多个 NDES 服务器，并让每个 NDES 服务器都具有一个 Microsoft Intune 证书连接器。

##### <a name="download-install-and-configure-the-certificate-connector"></a>下载、安装和配置证书连接器
![ConnectorDownload](./media/certificates-download-connector.png)

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 选择“设备配置”，然后选择“证书颁发机构”。
4. 选择“添加”和“下载连接器文件”。 将下载的文件保存到可以从服务器上进行访问的位置，将在该服务器上安装该应用程序。
5. 下载完成后，在承载网络设备注册服务 (NDES) 角色的服务器上运行下载的安装程序 (ndesconnectorssetup.exe)。 该安装程序也会安装 NDES 和 CRP Web Service 的策略模块。 （CRP Web 服务 CertificateRegistrationSvc 运行为 IIS 中的应用程序）

    > [!NOTE]
    > 如果为独立 Intune 安装 NDES，则 CRP 服务会自动随证书连接器一起安装。 如果将 Intune 与 Configuration Manager 配合使用，请以单独的站点系统角色安装证书注册点。

6. 提示输入证书连接器的客户端证书时，选取“选择”，然后选择任务 3 中在你的 NDES 服务器上安装的“客户端身份验证”证书。

    选择客户端身份验证证书后，你将返回到“Microsoft Intune 证书连接器的客户端证书” 处。 尽管所选证书不会显示，但可以单击“下一步”查看该证书的属性。 然后依次选择“下一步”和“安装”。

7. 在向导完成后，先单击“启动证书连接器 UI，然后再关闭向导”。

    > [!TIP]
    > 如果在启动证书连接器 UI 前关闭了向导，你可以通过运行以下命令重新打开它：
    >
    > <install_Path>\NDESConnectorUI\NDESConnectorUI.exe

8. 在“证书连接器” UI 中：

    选择“登录”，输入你的 Intune 服务管理员凭据或具有全局管理权限的租户管理员的凭据。

    > [!IMPORTANT]
    > 必须为用户帐户分配有效的 Intune 许可证。 如果用户帐户没有有效的 Intune 许可证，NDESConnectorUI.exe 将失败。

    如果组织使用代理服务器并且 NDES 服务器需要代理才能访问 Internet，请选择“使用代理服务器”，然后输入用于连接的代理服务器名称、端口和帐户凭据。

    选择“高级”选项卡，然后输入在证书颁发机构上拥有“颁发和管理证书”权限的帐户的凭据。 单击“应用”以应用更改。

    你现在可以关闭证书连接器 UI。

9. 打开命令提示符，输入“services.msc”，然后按 Enter。 右键单击“Intune 连接器服务”，选择“重启”。

要验证服务是否正在运行，请打开浏览器并输入以下 URL。 应返回 403 错误：

`http://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll`

## <a name="create-a-scep-certificate-profile"></a>创建 SCEP 证书配置文件

1. 在 Azure 门户中，打开 Microsoft Intune。
2. 依次选择“设备配置”、“配置文件”和“创建配置文件”。
3. 为 SCEP 证书配置文件输入“名称”和“说明”。
4. 从“平台”下拉列表中，为此 SCEP 证书选择设备平台。 目前，可以为设备限制设置选择以下平台之一：
   - **Outlook Web Access (OWA)**
   - **iOS**
   - **macOS**
   - **Windows Phone 8.1**
   - **Windows 8.1 及更高版本**
   - **Windows 10 及更高版本**
5. 从“配置文件”类型下拉列表中，选择“SCEP 证书”。
6. 在“SCEP 证书”窗格上，配置下列设置：

   - **证书有效期**：如果对发证 CA 运行允许自定义有效期的 `certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE` 命令，则可以输入证书过期之前的剩余时间量。<br>可以在证书模板中输入低于（但不能高于）有效期的值。 例如，如果证书模板中的证书有效期为 2 年，则输入值可以为 1 年，但不能为 5 年。 该值还必须小于发证 CA 证书的剩余有效期。 
   - **密钥存储提供程序 (KSP)** (Windows Phone 8.1、Windows 8.1、Windows 10)：输入存储证书密钥的位置。 可以选择下列值之一：
     - 注册到受信任的平台模块(TPM) KSP (若有); 否则，注册到软件 KSP
     - 注册到受信任的平台模块(TPM) KSP，否则失败
     - 注册到 Passport，否则失败(Windows 10 及更高版本)
     - **注册到软件 KSP**

   - **使用者名称格式**：从列表中，选择 Intune 在证书请求中自动创建使用者名称的方法。 如果证书用于用户，还可包含使用者名称中的用户电子邮件地址。 选择：
     - 未配置
     - 公用名称
     - 包含电子邮件地址的公用名称
     - 作为电子邮件地址的公用名称
     - IMEI（国际移动设备标识）
     - **序列号**
     - **自定义**：选择此选项后，将会显示另一个下拉字段。 使用此字段输入自定义使用者名称格式。 自定义格式支持两个变量：“公用名(CN)”和“电子邮件(E)”。 可将“公用名(CN)”设置为以下任何变量：
       - **CN={{UserName}}**：用户的用户主体名称，如 janedoe@contoso.com
       - **CN={{AAD_Device_ID}}**：在 Azure Active Directory (AD) 中注册设备时分配的 ID。 此 ID 通常用于向 Azure AD 进行身份验证。
       - **CN={{SERIALNUMBER}}**：制造商通常用于标识设备的唯一序列号 (SN)
       - **CN={{IMEINumber}}**：用于标识移动电话的国际移动设备标识 (IMEI)
       - **CN={{OnPrem_Distinguished_Name}}**：用逗号分隔的一系列相对可分辨名称，如 `CN=Jane Doe,OU=UserAccounts,DC=corp,DC=contoso,DC=com`

       > [!TIP]
       > 要使用 `{{OnPrem_Distinguished_Name}}` 变量，请务必使用 [Azure Active Directory (AD) 连接](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)将 `onpremisesdistingishedname` 用户属性同步到 Azure AD。

       通过将一个或多个以上变量与静态字符串组合使用，可以创建自定义使用者名称格式，例如：CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US。 <br/> 本示例创建了使用者名称格式，其中除了使用 CN 和 E 变量外，还使用了组织单元、组织、位置、省/直辖市/自治区和国家/地区值的字符串。 [CertStrToName 函数](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx)介绍此函数及其支持的字符串。




- **使用者可选名称**：输入 Intune 在证书请求中自动创建使用者可选名称 (SAN) 的值的方法。 例如，如果选择用户证书类型，则可以在使用者可选名称中包括用户主体名称 (UPN)。 如果客户端证书用于向网络策略服务器进行验证，则必须将使用者可选名称设置为 UPN。
- **密钥用法**：输入证书的密钥用法选项。 选项包括：
  - **密钥加密**：仅在密钥加密时允许密钥交换
  - **数字签名**：仅在数字签名帮助保护密钥时允许密钥交换
- **密钥大小（位数）**：选择密钥中包含的位数
- **哈希算法** (Android、Windows Phone 8.1、Windows 8.1、Windows 10)：选择要与此证书一起使用的可用哈希算法类型之一。 选择连接设备支持的最高级别安全性。
- **根证书**：选择之前配置并分配到用户或设备的根 CA 证书配置文件。 此 CA 证书必须是将颁发在此证书配置文件中配置的证书的 CA 的根证书。
- **扩展密钥用法**：选择“添加”为证书的预期目的添加值。 大多数情况下，证书需要“客户端身份验证”以便用户或设备能够向服务器进行验证。 但，你可以根据需要添加任何其他密钥用法。
- **注册设置**
  - **续订阈值(%)**：输入设备请求证书续订之前剩余的证书有效期限的百分比。
  - **SCEP 服务器 URL**：为通过 SCEP 颁发证书的 NDES 服务器输入 1 个或多个 URL。
  - 选择“确定”，然后选择“创建”来创建配置文件。

配置文件随即创建并显示在“配置文件列表”窗格中。

## <a name="assign-the-certificate-profile"></a>分配证书配置文件

将证书配置文件分配给组之前，请注意以下几点：

- 将证书配置文件分配给组时，将在设备上安装受信任的 CA 证书配置文件的证书文件。 设备使用 SCEP 证书配置文件来创建设备需要的证书。
- 仅在运行创建配置文件时使用的平台的设备上安装证书配置文件。
- 可以向用户集合或设备集合分配证书配置文件。
- 若要在注册设备后向设备快速发布证书，请将证书配置文件分配给用户组（而不是设备组）。 如果分配到设备组，则需要在设备接收策略前进行完整的设备注册。
- 尽管单独分配每个配置文件，但仍需分配受信任的根 CA 和 SCEP 或 PKCS 配置文件。 否则，SCEP 或 PKCS 证书策略将失败。

    > [!NOTE]
    > 对于 iOS，如果部署了使用相同证书配置文件的多个资源配置文件，则管理配置文件中应会显示该证书的多个副本。
    
有关如何分配配置文件的信息，请参阅[如何分配设备配置文件](device-profile-assign.md)。
