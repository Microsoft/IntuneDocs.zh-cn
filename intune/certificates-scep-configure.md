---
title: 在 Microsoft Intune 中使用 SCEP 证书 - Azure | Microsoft Docs
description: 要在 Microsoft Intune 中使用 SCEP 证书，请配置本地 AD 域，创建证书颁发机构，设置 NDES 服务器，并安装 Intune 证书连接器。 然后创建 SCEP 证书配置文件并将此配置文件分配到组。 另请参阅不同的事件 ID 及其说明，以及 Intune 连接器服务的诊断代码。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/05/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6f1cdacf4b4d26e9db9b4090805f697927a399c5
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61510003"
---
# <a name="configure-and-use-scep-certificates-with-intune"></a>在 Intune 中配置和使用 SCEP 证书

本文说明如何配置基础结构，然后使用 Intune 创建和分配简单证书注册协议 (SCEP) 证书配置文件。

## <a name="configure-on-premises-infrastructure"></a>配置本地基础结构

- **Active Directory 域**：本部分列出的所有服务器（Web 应用程序代理服务器除外）必须加入你的 Active Directory 域。

- **证书颁发机构** (CA)：必须是在 Windows Server 2008 R2 企业版或更高版本上运行的 Microsoft 企业证书颁发机构 (CA)。 不支持独立 CA。 有关详细信息，请参阅[安装证书颁发机构](http://technet.microsoft.com/library/jj125375.aspx)。
    如 CA 运行的是 Windows Server 2008 R2，则必须[安装修补程序 KB2483564](http://support.microsoft.com/kb/2483564/)。

- **NDES 服务器**：在 Windows Server 2012 R2 或更高版本上，设置网络设备注册服务 (NDES) 服务器角色。 Intune 不支持在同时运行企业 CA 的服务器上使用 NDES。 有关如何配置 Windows Server 2012 R2 以托管 NDES 的说明，请参阅[网络设备注册服务指南](http://technet.microsoft.com/library/hh831498.aspx)。
必须将 NDES 服务器加入与企业 CA 相同的林中的域。 有关在单独的林、独立的网络或内部的域中部署 NDES 服务器的详细信息，可查阅[结合使用策略模块和网络设备注册服务](https://technet.microsoft.com/library/dn473016.aspx)。

- **Microsoft Intune 证书连接器**：在 Intune 门户中，转到“设备配置” > “证书连接器” > “添加”，然后按照“为 SCEP 安装连接器的步骤”操作。 使用门户中的下载链接开始下载证书连接器安装程序 NDESConnectorSetup.exe。  将在具有 NDES 角色的服务器上运行此安装程序。  

此 NDES 证书连接器还支持美国联邦信息处理标准 (FIPS) 模式。 FIPS 不是必需的，但启用 FIPS 时可颁发和吊销证书。

- **Web 应用程序代理服务器**（可选）：将运行 Windows Server 2012 R2 或更高版本的服务器用作 Web 应用程序代理 (WAP) 服务器。 该配置：
  - 允许设备使用 Internet 连接接收证书。
  - 是设备通过 Internet 连接接收和续订证书时的安全建议。
  
- **Azure AD 应用程序代理**（可选）：可以使用 Azure AD 应用程序代理（而不是专用的 Web 应用程序代理 (WAP) 服务器）向 Internet 发布 NDES 服务器。 有关详细信息，请参阅[如何提供对本地应用程序的安全远程访问](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy)。

#### <a name="additional"></a>Additional

- 承载 WAP 的服务器[必须安装此更新](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx)以支持网络设备注册服务所使用的长 URL。 该更新包括在 [2014 年 12 月的更新汇总中](http://support.microsoft.com/kb/3013769)，或单独更新自 [KB3011135](http://support.microsoft.com/kb/3011135)。
- WAP 服务器必须具有与将要向外部客户端发布的名称相匹配的 SSL 证书，并且信任 NDES 服务器上使用的 SSL 证书。 这些证书使 WAP 服务器可以终止来自客户端的 SSL 连接，并创建至 NDES 服务器的新 SSL 连接。

有关详细信息，请参阅[规划 WAP 证书](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383650(v=ws.11)#plan-certificates)和[有关 WAP 服务器的常规信息](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn584113(v=ws.11))。

### <a name="network-requirements"></a>网络要求

如果不使用反向代理（例如 WAP 或 Azure AD 应用代理），则允许端口 443 上的 TCP 流量从 Internet 上的所有主机/IP 地址传输到 NDES 服务器。

允许 NDES 服务器和任何支持基础结构之间所需的所有端口和协议。 例如，NDES 服务器需要与 CA、DNS 服务器、Configuration Manager 服务器、域控制器以及环境中可能的其他服务进行通信。

强烈建议通过反向代理（例如，[Azure AD 应用程序代理](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/)、[Web 访问代理](https://technet.microsoft.com/library/dn584107.aspx)或第三方代理）发布 NDES 服务器。

### <a name="certificates-and-templates"></a>证书和模板  

|对象|详细信息|
|----------|-----------|
|**证书模板**|在发证 CA 上配置此模板。|
|**客户端身份验证证书**|发证 CA 或公共 CA 请求；在 NDES 服务器上安装证书。|
|**服务器身份验证证书**|发证 CA 或公共 CA 请求；在 NDES 服务器上的 IIS 中安装并绑定该 SSL 证书。 如果证书具有客户端和服务器身份验证密钥使用集（增强型密钥使用），则可以使用相同的证书。|
|**受信任的根 CA 证书**|将此证书从根 CA 或信任根 CA 的任何设备中导出为“.cer”文件。 然后，使用受信任的 CA 证书配置文件将其分配给用户、设备或同时向两者分配。<br /><b>注意：<b />分配 SCEP 证书配置文件时，请务必将 SCEP 证书配置文件中引用的受信任的根证书配置文件分配到同一用户或设备组。<br /><br />你可以在每个操作系统平台上使用一个受信任的根 CA 证书，并将其与你创建的每个受信任的根证书配置文件相关联。<br /><br />你可以在需要时使用其它受信任的根 CA 证书。 例如，你可以这样做来信任为 Wi-Fi 访问点的服务器身份验证证书签名的 CA。|

### <a name="accounts"></a>帐户

|名称|详细信息|
|--------|-----------|
|**NDES 服务帐户**|输入用作 NDES 服务帐户的域用户帐户。 |

## <a name="configure-your-infrastructure"></a>配置你的基础结构
配置证书配置文件前，请完成以下步骤。 必须具备 Windows Server 2012 R2 或更高版本和 Active Directory 证书服务 (ADCS) 方面的知识，才能执行下面这些步骤：

#### <a name="step-1---create-an-ndes-service-account"></a>步骤 1 - 创建 NDES 服务帐户

创建用作 NDES 服务帐户的域用户帐户。 安装和配置 NDES 之前，在配置发证 CA 上的模板时输入该帐户。 确保用户具有默认权限，即“本地登录”、“作为服务登录”和“作为批处理作业登录”的权限。 某些组织已采用强化策略禁用这些权限。

#### <a name="step-2---configure-certificate-templates-on-the-certification-authority"></a>步骤 2 - 配置证书颁发机构上的证书模板
在此步骤中，你将：

- 配置 NDES 证书模板
- 发布 NDES 证书模板

##### <a name="configure-the-certification-authority"></a>配置证书颁发机构

1. 以企业管理员身份登录。

2. 在发证 CA 上，使用“证书模板”管理单元创建新的自定义模板。 或者，复制现有模板，然后更新现有模板（如用户模板）以与 NDES 配合使用。

   >[!NOTE]
   > NDES 证书模板必须基于 v2 证书模板（具有 Windows 2003 兼容性）。

   模板必须进行以下配置：

   - 通常情况下：
   
       - 确认未选中“在 Active Directory 中发布证书”属性。
       - 为模板输入友好的“模板显示名称”。

   - 在“使用者名称”处，选择“在请求中提供”。 （由适用于 NDES 的 Intune 策略模块强制实施安全措施）。

   - 在“扩展”选项卡上，确认“应用程序策略描述”包括“客户端身份验证”。

     > [!IMPORTANT]
     > 对于 iOS 和 macOS 证书模板，在“扩展”选项卡上编辑“密钥用法”，并确认未选择“数字签名为原件的证明”。

   - 在“安全性”选项卡上，添加 NDES 服务帐户，并授予它“注册”模板的权限。 将创建 SCEP 配置文件的 Intune 管理员需要“读取”权限，以便在创建 SCEP 配置文件时可以浏览到该模板。

     > [!NOTE]
     > 若要吊销证书，NDES 服务帐户需要针对证书配置文件所用的每个证书模板具有“颁发和管理证书”权限。

3. 在模板的“常规”选项卡上查看“有效期”。 默认情况下，Intune 使用模板中配置的值。 但是，可以将 CA 配置为允许申请者输入其他值，随后便能够在 Intune 管理员控制台中设置此值。 如果你想要一直使用模板中的值，跳过该步骤的其余部分即可。

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
   选择“证书模板”节点，单击“操作” > “新建” > “要颁发的证书模板”，然后选择你在步骤 2 中创建的模板。

3. 通过查看“证书模板”文件夹下已发布的模板来对它进行验证。

#### <a name="step-3---configure-prerequisites-on-the-ndes-server"></a>步骤 3 - 在 NDES 服务器上配置必备组件
在此步骤中，你将：

- 将 NDES 添加到 Windows Server 并配置 IIS 以支持 NDES
- 将 NDES 服务帐户添加到 IIS_IUSR 组
- 设置 NDES 服务帐户的服务主体名称 (SPN)

1. 在承载 NDES 的服务器上安装 NDES 时，以“企业管理员”身份登录，然后使用[添加角色和功能向导](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831809(v=ws.11))：

   1. 在向导中，选择“Active Directory 证书服务”以获得对 AD CS 角色服务的访问权限。 选择“网络设备注册服务”，取消选择“证书颁发机构”，然后完成向导。

      > [!TIP]
      > 在“安装进度”处，不要勾选“关闭”。 而是选择“配置目标服务器上的 Active Directory 证书服务”的链接。 “AD CS 配置”向导将会打开，此配置将用于下一步骤。 打开“AD CS 配置”后，你可以关闭“添加角色和功能”向导。

   2. 将 NDES 添加到服务器后，向导也会安装 IIS。 确认 IIS 具有以下配置：

       - “Web 服务器” > “安全性” > “请求筛选”

       - “Web 服务器” > “应用程序开发” > “ASP.NET 3.5” 

            安装 ASP.NET 3.5 会安装 .NET Framework 3.5。 安装 .NET Framework 3.5 时，安装核心“.NET Framework 3.5”功能和“HTTP 激活”。

       - “Web 服务器” > “应用程序开发” > “ASP.NET 4.5” 

            安装 ASP.NET 4.5 会安装 .NET Framework 4.5。 安装 .NET Framework 4.5 时，安装核心“.NET Framework 4.5”功能、“ASP.NET 4.5”和“WCF 服务” > “HTTP 激活”功能。

       - “管理工具” > “IIS 6 管理兼容性” > “IIS 6 元数据库兼容性”

       - “管理工具” > “IIS 6 管理兼容性” > “IIS 6 WMI 兼容性”

       - 在服务器上，将 NDES 服务帐户添加为本地“IIS_IUSR”组成员。

2. 在提升的命令指示符处，运行以下命令以设置 NDES 服务帐户的 SPN：

    `setspn -s http/<DNS name of NDES Server> <Domain name>\<NDES Service account name>`

    例如，如果 NDES 服务器名为 Server01，你的域为 Contoso.com，并且服务帐户为 NDESService，则使用：

    `setspn –s http/Server01.contoso.com contoso\NDESService`

#### <a name="step-4---configure-ndes-for-use-with-intune"></a>步骤 4 - 配置 NDES 以与 Intune 一起使用
在此步骤中，你将：

- 配置 NDES 以与发证 CA 一起使用
- 在 IIS 绑定服务器身份验证 (SSL) 证书
- 在 IIS 中配置请求筛选

1. 在 NDES 服务器上，打开“AD CS 配置”向导，然后进行以下更新：

    > [!TIP]
    > 如果在上一步骤中单击了该链接，则此向导已经打开。 或者，打开“服务器管理器”访问“Active Directory 证书服务”的后期部署配置。

   - 在“角色服务”页面，选择“网络设备注册服务”
   - 在“NDES 的服务帐户”页面，输入 NDES 服务帐户
   - 在“NDES 的 CA”页面，单击“选择”，然后选择在其中配置证书模板的发证 CA
   - 在“为 NDES 加密”页面，设置符合公司要求的秘钥长度。
   - 在“确认”页面，选择“配置”，完成向导。

2. 完成向导后，在 NDES 服务器上更新以下注册表项：

    `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\`

    要更新此密钥，请标识证书模板的“目的”（位于“请求处理”选项卡上）。 然后，通过将现有数据替换为在“步骤 2”中指定的证书模板的名称（不是模板的显示名称），更新对应的注册表项。 下表将证书模板目的映射至注册表中的值：

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

5. 重新启动服务器。 请勿使用 iisreset；它不会完成这些更改。
6. 浏览到 `http://*FQDN*/certsrv/mscep/mscep.dll`。 应看到与下图类似的 NDES 页面：

    ![测试 NDES](./media/SCEP_NDES_URL.png)

    如果你收到“503 服务不可用”的信息，请查看事件查看器。 可能是因 NDES 用户缺少权限导致应用程序池停止。 步骤 1 中描述了这些权限。

##### <a name="install-and-bind-certificates-on-the-ndes-server"></a>在 NDES 服务器上安装和绑定证书

1. 在你的 NDES 服务器上，请求并安装来自你的内部 CA 或公共 CA 的“服务器身份验证”证书。 随后绑定 IIS 中的 SSL 证书。

    > [!TIP]
    > 绑定 IIS 中的 SSL 证书后，安装客户端身份验证证书。 该证书可以由 NDES 服务器信任的任何 CA 颁发。 如果证书具有客户端和服务器身份验证密钥使用集（增强型密钥使用），则可以使用相同的证书。 查看以下步骤以获得有关这些身份验证证书的信息。

   1. 获取服务器身份验证证书后，打开“IIS 管理器”，然后选择“默认网站”。 在“操作”窗格中，选择“绑定”。

   2. 选择“添加”，将“类型”设置为“https”并确认端口为“443”。 独立 Intune 仅支持端口 443。

   3. 为“SSL 证书”输入服务器身份验证证书。

      > [!NOTE]
      > 如果 NDES 服务器对单个网络地址使用外部和内部名称，则服务器身份验证证书必须具有：
      > - **使用者名称**（包括外部公共服务器名称）
      > - **使用者可选名称**（包括内部服务器名称）

2. 在你的 NDES 服务器上，请求并安装来自你的内部 CA 或公用证书颁发机构的“客户端身份验证”证书。 如果证书具有这两个功能，则可以与服务器身份验证证书相同。

    客户端身份验证证书必须具备以下属性：

    - **增强型密钥使用**：此值必须包括客户端身份验证

    - **使用者名称**：此值必须与安装证书的服务器（NDES 服务器）的 DNS 名称相同

##### <a name="configure-iis-request-filtering"></a>配置 IIS 请求筛选

1. 在 NDES 服务器上打开“IIS 管理器”，在“连接”窗格中选择“默认网站”，然后打开“请求筛选”。

2. 选择“编辑功能设置”，然后设置值：

    - **查询字符串(字节)** = **65534**
    - **最大 URL 长度(字节)** = **65534**

3. 查看以下注册表：

    `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters`

    确认以下值都设置为 DWORD 值：

    - 名称：MaxFieldLength，十进制值为 65534
    - 名称：MaxRequestBytes，十进制值为 65534

4. 重新启动 NDES 服务器。 服务器现已支持证书连接器。

#### <a name="step-5---enable-install-and-configure-the-intune-certificate-connector"></a>步骤 5 - 启用、安装和配置 Intune 证书连接器
在此步骤中，你将：

- 在 Intune 中启用对 NDES 的支持。
- 在承载环境中的网络设备注册服务 (NDES) 角色的服务器上下载、安装和配置证书连接器。 为提高组织中 NDES 实现的缩放性，可安装多个 NDES 服务器，并让每个 NDES 服务器都具有一个 Microsoft Intune 证书连接器。

##### <a name="download-install-and-configure-the-certificate-connector"></a>下载、安装和配置证书连接器

> [!IMPORTANT] 
> Microsoft Intune 证书连接器必须安装在单独的 Windows Server 上。 它不能安装在证书颁发机构 (CA) 上。 它还必须安装在与网络设备注册服务 (NDES) 角色相同的服务器上。

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
2. 选择“设备配置” > “认证连接器” > “添加”。
3. 下载并保存 SCEP 文件的连接器。 将该文件保存到可从要安装连接器的服务器访问的位置。

   ![ConnectorDownload](./media/certificates-scep-configure/download-certificates-connector.png)


4. 下载完成后，请转到托管网络设备注册服务 (NDES) 的服务器。 然后：

    1. 确保已安装 .NET 4.5 Framework，因为它是 NDES 证书连接器的必需项。 Windows Server 2012 R2 和更高版本中自动包含 .NET 4.5 Framework。
    2. 运行安装程序 (NDESConnectorSetup.exe)。 该安装程序也会安装 NDES 和 CRP Web Service 的策略模块。 CRP Web 服务 CertificateRegistrationSvc 作为 IIS 中的应用程序运行。

    > [!NOTE]
    > 如果为独立 Intune 安装 NDES，则 CRP 服务会自动随证书连接器一起安装。 如果将 Intune 与 Configuration Manager 配合使用，请以单独的站点系统角色安装证书注册点。

5. 提示输入证书连接器的客户端证书时，选取“选择”，然后选择步骤 4 中在你的 NDES 服务器上安装的“客户端身份验证”证书。

    选择客户端身份验证证书后，你将返回到“Microsoft Intune 证书连接器的客户端证书” 处。 尽管所选证书不会显示，但可以单击“下一步”查看该证书的属性。 然后依次选择“下一步”和“安装”。

    > [!IMPORTANT]
    > [必须在托管 Intune 证书连接器的 NDES 服务器](https://technet.microsoft.com/library/cc775800(v=WS.10).aspx)上禁用 Internet Explorer 增强型安全配置。

6. 在向导完成后，先单击“启动证书连接器 UI，然后再关闭向导”。

    > [!TIP]
    > 如果在启动证书连接器 UI 前关闭了向导，你可以通过运行以下命令重新打开它：
    >
    > <install_Path>\NDESConnectorUI\NDESConnectorUI.exe

7. 在“证书连接器” UI 中：

    选择“登录”，输入你的 Intune 服务管理员凭据或具有全局管理权限的租户管理员的凭据。 登录后，Intune 证书连接器将从 Intune 下载证书。 此证书用于连接器和 Intune 之间的身份验证。

    > [!IMPORTANT]
    > 必须为用户帐户分配有效的 Intune 许可证。 如果用户帐户没有有效的 Intune 许可证，NDESConnectorUI.exe 将失败。

    如果组织使用代理服务器并且 NDES 服务器需要代理才能访问 Internet，请选择“使用代理服务器”。 然后输入用于连接的代理服务器名称、端口和帐户凭据。

    选择“高级”选项卡，然后输入在证书颁发机构上拥有“颁发和管理证书”权限的帐户的凭据。 单击“应用”以应用更改。

    你现在可以关闭证书连接器 UI。

8. 打开命令提示符，输入“services.msc”，然后按 Enter。 右键单击“Intune 连接器服务” > “重启”。

要验证服务是否正在运行，请打开浏览器并输入以下 URL。 应返回 403 错误：

`http://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll`

> [!NOTE]
> NDES 证书连接器中包含 TLS 1.2 支持。 因此，如果已安装 NDES 证书连接器的服务器支持 TLS 1.2，则使用 TLS 1.2。 如果服务器不支持 TLS 1.2，则使用 TLS 1.1。 目前，TLS 1.1 用于设备和服务器之间的身份验证。

## <a name="create-a-scep-certificate-profile"></a>创建 SCEP 证书配置文件

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
2. 选择“设备配置” > “配置文件” > “创建配置文件”。
3. 为 SCEP 证书配置文件输入“名称”和“说明”。
4. 从“平台”下拉列表中，为此 SCEP 证书选择设备平台。 目前，可以为设备限制设置选择以下平台之一：
   - **Outlook Web Access (OWA)**
   - **Android Enterprise**
   - **iOS**
   - **macOS**
   - **Windows Phone 8.1**
   - **Windows 8.1 及更高版本**
   - **Windows 10 及更高版本**
5. 从“配置文件”类型下拉列表中，选择“SCEP 证书”。
6. 输入以下设置：

   - **证书类型**：为用户证书选择“用户”。 “用户”证书类型可包含证书主题和 SAN 中的用户和设备属性。  对于无用户设备（如展台）等方案或 Windows 设备，请选择“设备”，将证书放在本地计算机证书存储中。 “设备”证书只能在证书主题和 SAN 中包含设备属性。  “设备”证书可用于以下平台：  
     - Android Enterprise - 工作配置文件
     - iOS
     - macOS
     - Windows 8.1 及更高版本
     - Windows 10 及更高版本


   - **使用者名称格式**：选择 Intune 如何自动创建证书请求中的使用者名称。 如果选择“用户”证书类型或“设备”证书类型，选项将发生更改。 

        **“用户”证书类型**  

        可以在使用者名称中包括用户的电子邮件地址。 选择：

        - 未配置
        - 公用名称
        - 包含电子邮件地址的公用名称
        - 作为电子邮件地址的公用名称
        - IMEI（国际移动设备标识）
        - **序列号**
        - **自定义**：选中此选项时，也会显示“自定义”文本框。 使用此字段输入一个自定义使用者名称格式，包括变量。 自定义格式支持两种变量：公用名 (CN) 和电子邮件 (E)。 可将“公用名(CN)”设置为以下任何变量：

            - **CN={{UserName}}**：用户的用户主体名称，例如 janedoe@contoso.com
            - **CN={{AAD_Device_ID}}**：在 Azure Active Directory (AD) 中注册设备时分配的 ID。 此 ID 通常用于向 Azure AD 进行身份验证。
            - **CN={{SERIALNUMBER}}**：制造商通常用于标识设备的唯一序列号 (SN)
            - **CN={{IMEINumber}}**：用于标识移动电话的国际移动设备标识 (IMEI)
            - **CN={{OnPrem_Distinguished_Name}}**：用逗号分隔的一系列相对可分辨名称，如 `CN=Jane Doe,OU=UserAccounts,DC=corp,DC=contoso,DC=com`

                要使用 `{{OnPrem_Distinguished_Name}}` 变量，请务必使用 [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) 将 `onpremisesdistingishedname` 用户属性同步到 Azure AD。

            - **CN={{onPremisesSamAccountName}}**：管理员可以使用 Azure AD 连接到名为 `onPremisesSamAccountName` 的属性，将 Active Directory 中的 samAccountName 属性同步到 Azure AD。 Intune 可以将该变量替换为 SCEP 证书主题中的证书颁发请求的一部分。  samAccountName 属性是用于从早期版本的 Windows（Windows 2000 之前）支持客户端和服务器的用户登录名。 用户登录名称格式为：`DomainName\testUser` 或仅 `testUser`。

                要使用 `{{onPremisesSamAccountName}}` 变量，请务必使用 [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) 将 `onPremisesSamAccountName` 用户属性同步到 Azure AD。

            通过使用这些变量的一个或多个与静态字符串的组合，可以创建一个自定义使用者名称格式，例如：  

            CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US

            本示例创建了使用者名称格式，其中除了使用 CN 和 E 变量外，还使用了组织单元、组织、位置、省/直辖市/自治区和国家/地区值的字符串。 [CertStrToName 函数](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx)介绍此函数及其支持的字符串。

        **“设备”证书类型**  

        使用“设备”证书类型时，还可以对值使用以下设备证书变量：  

        ```
        "{{AAD_Device_ID}}",
        "{{Device_Serial}}",
        "{{Device_IMEI}}",
        "{{SerialNumber}}",
        "{{IMEINumber}}",
        "{{AzureADDeviceId}}",
        "{{WiFiMacAddress}}",
        "{{IMEI}}",
        "{{DeviceName}}",
        "{{FullyQualifiedDomainName}}",
        "{{MEID}}",
        ```

        可以在自定义值文本框中使用静态文本添加这些变量。 例如，可以将公用名添加为 `CN = {{DeviceName}}text`。

        > [!IMPORTANT]
        >  - 在使用者的静态文本中，未括住变量的大括号 { } 将解析为错误。 
        >  - 使用设备证书变量时，将变量括在大括号 { } 内。
        >  - `{{FullyQualifiedDomainName}}` 仅适用于 Windows 和已加入域的设备。 
        >  -  在使用者或 SAN 中为设备证书使用设备属性（例如 IMEI、序列号和完全限定的域名）时，请注意这些属性可能被有权访问设备的人员仿造。
        >  - 如果不支持指定的设备变量，则不会在设备上安装配置文件。 例如，如果在分配给不具有 IMEI 号码的设备的 SCEP 配置文件的使用者名称中使用了 {{IMEI}}，配置文件安装将失败。 


   - **使用者备用名称**：输入 Intune 如何自动创建证书请求中使用者可选名称 (SAN) 的值。 如果选择“用户”证书类型或“设备”证书类型，选项将发生更改。 

        **“用户”证书类型**  

        以下属性可用：

        - 电子邮件地址
        - 用户主体名称 (UPN)

            例如，如果选择用户证书类型，则可以在使用者可选名称中包括用户主体名称 (UPN)。 如果使用客户端证书向“网络策略服务器”进行身份验证，则要将使用者可选名称设置为 UPN。 

        **“设备”证书类型**  

        可自定义的一个表格格式文本框。 以下属性可用：

        - DNS

        凭借“设备”证书类型，可以对值使用以下设备证书变量：  

        ```
        "{{AAD_Device_ID}}",
        "{{Device_Serial}}",
        "{{Device_IMEI}}",
        "{{SerialNumber}}",
        "{{IMEINumber}}",
        "{{AzureADDeviceId}}",
        "{{WiFiMacAddress}}",
        "{{IMEI}}",
        "{{DeviceName}}",
        "{{FullyQualifiedDomainName}}",
        "{{MEID}}",
        ```

        可以在自定义值文本框中使用静态文本添加这些变量。 例如，可以将 DNS 属性添加为 `DNS name = {{AzureADDeviceId}}.domain.com`。

        > [!IMPORTANT]
        >  - 在 SAN 的静态文本中，使用大括号{ }、竖杠符号 | 和分号 ; 将不起作用。 
        >  - 使用设备证书变量时，将变量括在大括号 { } 内。
        >  - `{{FullyQualifiedDomainName}}` 仅适用于 Windows 和已加入域的设备。 
        >  -  在使用者或 SAN 中为设备证书使用设备属性（例如 IMEI、序列号和完全限定的域名）时，请注意这些属性可能被有权访问设备的人员仿造。
        >  - 如果不支持指定的设备变量，则不会在设备上安装配置文件。 例如，如果在分配给不具有 IMEI 号码的设备的 SCEP 配置文件的使用者可选名称中使用了 {{IMEI}}，配置文件安装将失败。  

   - **证书有效期**：如果对颁发 CA 运行了允许自定义有效期的 `certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE` 命令，则可以输入证书过期之前的剩余时间量。<br>可以在证书模板中输入低于（但不能高于）有效期的值。 例如，如果证书模板中的证书有效期为 2 年，则输入值可以为 1 年，但不能为 5 年。 该值还必须小于发证 CA 证书的剩余有效期。 
   - 密钥存储提供程序 (KSP)（Windows Phone 8.1、Windows 8.1、Windows 10）：输入存储证书密钥的位置。 可以选择下列值之一：
     - 注册到受信任的平台模块(TPM) KSP (若有); 否则，注册到软件 KSP
     - 注册到受信任的平台模块(TPM) KSP，否则失败
     - 注册到 Passport，否则失败(Windows 10 及更高版本)
     - **注册到软件 KSP**

   - **密钥用法**：输入证书的密钥用法选项。 选项包括：
     - **密钥加密**：仅在密钥已加密时才允许密钥交换
     - **数字签名**：仅当数字签名有助于保护密钥时才允许密钥交换
   - **密钥大小（位）**：选择密钥中包含的位数
   - **哈希算法**（Android、Windows Phone 8.1、Windows 8.1、Windows 10）：选择要与此证书一起使用的可用哈希算法类型之一。 选择连接设备支持的最高级别安全性。
   - **根证书**：选择之前配置并分配到用户和/或设备的根 CA 证书配置文件。 此 CA 证书必须是将颁发在此证书配置文件中配置的证书的 CA 的根证书。 请务必将此受信任的根证书配置文件分配到 SCEP 证书配置文件中分配的同一个组。
   - **扩展密钥用法**：为证书的预期目的添加值。 大多数情况下，证书需要“客户端身份验证”以便用户或设备能够向服务器进行验证。 但，你可以根据需要添加任何其他密钥用法。
   - **注册设置**
     - **续订阈值 (%)**：输入设备请求证书续订之前剩余的证书有效期限的百分比。
     - **SCEP 服务器 URL**：为通过 SCEP 颁发证书的 NDES 服务器输入 1 个或多个 URL。 例如，输入类似于 `https://ndes.contoso.com/certsrv/mscep/mscep.dll` 的内容。
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

有关如何分配配置文件的信息，请参阅[分配设备配置文件](device-profile-assign.md)。

## <a name="intune-connector-setup-verification-and-troubleshooting"></a>Intune 连接器设置验证和故障排除

若要解决问题并验证 Intune 连接器设置，请参阅[证书颁发机构脚本示例](https://aka.ms/intuneconnectorverificationscript)

## <a name="intune-connector-events-and-diagnostic-codes"></a>Intune 连接器事件和诊断代码

从版本 6.1806.x.x 开始，Intune 连接器服务会在“事件查看器”（“应用程序和服务日志” > “Microsoft Intune 连接器”）中记录事件。 使用这些事件可帮助解决 Intune 连接器配置中的潜在问题。 这些事件记录操作的成功和失败，并且还包含带有消息的诊断代码，以帮助 IT 管理员进行故障排除。

### <a name="event-ids-and-descriptions"></a>事件 ID 和说明

> [!NOTE]
> 有关每个事件的相关诊断代码的详细信息，请使用“诊断代码”表（在本文中）。

| 事件 ID      | 事件名称    | 事件说明 | 相关诊断代码 |
| ------------- | ------------- | -------------     | -------------            |
| 10010 | StartedConnectorService  | 连接器服务已启动 | 0x00000000, 0x0FFFFFFF |
| 10020 | StoppedConnectorService  | 连接器服务已停止 | 0x00000000, 0x0FFFFFFF |
| 10100 | CertificateRenewal_Success  | 连接器注册证书已成功更新 | 0x00000000, 0x0FFFFFFF |
| 10102 | CertificateRenewal_Failure  | 连接器注册证书更新失败。 重新安装连接器。 | 0x00000000, 0x00000405, 0x0FFFFFFF |
| 10302 | RetrieveCertificate_Error  | 未能从注册表中检索到连接器注册证书。 查看事件详细信息，获取与此事件相关的证书指纹。 | 0x00000000, 0x00000404, 0x0FFFFFFF |
| 10301 | RetrieveCertificate_Warning  | 查看事件详细信息中的诊断信息。 | 0x00000000, 0x00000403, 0x0FFFFFFF |
| 20100 | PkcsCertIssue_Success  | 已成功颁发 PKCS 证书。 查看事件详细信息，获取与此事件相关的设备 ID、用户 ID、CA 名称、证书模板名称和证书指纹。 | 0x00000000, 0x0FFFFFFF |
| 20102 | PkcsCertIssue_Failure  | 未能颁发 PKCS 证书。 查看事件详细信息，获取与此事件相关的设备 ID、用户 ID、CA 名称、证书模板名称和证书指纹。 | 0x00000000, 0x00000400, 0x00000401, 0x0FFFFFFF |
| 20200 | RevokeCert_Success  | 已成功撤销证书。 查看事件详细信息，获取与此事件相关的设备 ID、用户 ID、CA 名称和证书序列号。 | 0x00000000, 0x0FFFFFFF |
| 20202 | RevokeCert_Failure | 未能撤销证书。 查看事件详细信息，获取与此事件相关的设备 ID、用户 ID、CA 名称和证书序列号。 有关其他信息，请参阅 NDES SVC 日志。   | 0x00000000, 0x00000402, 0x0FFFFFFF |
| 20300 | Upload_Success | 已成功下载证书的请求或撤销数据。 查看事件详细信息，获取上传详细信息。 | 0x00000000, 0x0FFFFFFF |
| 20302 | Upload_Failure | 未能下载证书的请求或撤销数据。 查看“事件详细信息”>“上传状态”以确定故障点。| 0x00000000, 0x0FFFFFFF |
| 20400 | Download_Success | 已成功下载签署证书、下载客户端证书或撤销证书的请求。 查看事件详细信息，获取下载详细信息。  | 0x00000000, 0x0FFFFFFF |
| 20402 | Download_Failure | 未能下载签署证书、下载客户端证书或撤销证书的请求。 查看事件详细信息，获取下载详细信息。 | 0x00000000, 0x0FFFFFFF |
| 20500 | CRPVerifyMetric_Success  | 证书注册点已成功验证客户端质询 | 0x00000000, 0x0FFFFFFF |
| 20501 | CRPVerifyMetric_Warning  | 证书注册点已完成并拒绝了请求。 有关详细信息，请参阅诊断代码和消息。 | 0x00000000, 0x00000411, 0x0FFFFFFF |
| 20502 | CRPVerifyMetric_Failure  | 证书注册点未能验证客户端质询。 有关详细信息，请参阅诊断代码和消息。 有关与该质询相对应的设备 ID，请查看事件消息详细信息。 | 0x00000000, 0x00000408, 0x00000409, 0x00000410, 0x0FFFFFFF |
| 20600 | CRPNotifyMetric_Success  | 证书注册点已成功完成通知过程并已将证书发送到客户端设备。 | 0x00000000, 0x0FFFFFFF |
| 20602 | CRPNotifyMetric_Failure  | 证书注册点未能完成通知过程。 查看事件消息的详细信息，获取有关请求的信息。 验证 NDES 服务器和 CA 之间的连接。 | 0x00000000, 0x0FFFFFFF |

### <a name="diagnostic-codes"></a>诊断代码

| 诊断代码 | 诊断名称 | 诊断消息 |
| -------------   | -------------   | -------------      |
| 0x00000000 | 成功  | 成功 |
| 0x00000400 | PKCS_Issue_CA_Unavailable  | 证书颁发机构无效或无法访问。 验证证书颁发机构是否可用，以及服务器是否可以与之通信。 |
| 0x00000401 | Symantec_ClientAuthCertNotFound  | 在本地证书存储中找不到 Symantec 客户端身份验证证书。 请参阅文章[安装 Symantec 注册授权证书](https://docs.microsoft.com/intune/certificates-symantec-configure#install-the-symantec-registration-authorization-certificate)以获取详细信息。  |
| 0x00000402 | RevokeCert_AccessDenied  | 指定的帐户无权从 CA 撤销证书。 请参阅事件消息详情中的“CA 名称”字段以确定颁发 CA。  |
| 0x00000403 | CertThumbprint_NotFound  | 找不到与输入相匹配的证书。 注册证书连接器并重试。 |
| 0x00000404 | Certificate_NotFound  | 找不到与提供的输入相匹配的证书。 重新注册证书连接器并重试。 |
| 0x00000405 | Certificate_Expired  | 证书已过期。 重新注册证书连接器以更新证书，然后重试。 |
| 0x00000408 | CRPSCEPCert_NotFound  | 找不到 CRP 加密证书。 验证是否正确安装 NDES 和 Intune 连接器。 |
| 0x00000409 | CRPSCEPSigningCert_NotFound  | 无法检索签名证书。 验证 Intune 连接器服务配置是否正确，以及 Intune 连接器服务是否正在运行。 此外，验证证书下载事件是否成功。 |
| 0x00000410 | CRPSCEPDeserialize_Failed  | 未能反序列化 SCEP 质询请求。 验证是否正确安装 NDES 和 Intune 连接器。 |
| 0x00000411 | CRPSCEPChallenge_Expired  | 由于证书质询已过期，因此请求已被拒绝。 客户端设备可以在从管理服务器获取新的质询后重试。 |
| 0x0FFFFFFFF | Unknown_Error  | 我们无法完成你的请求，因为发生了服务器端错误。 请稍后重试。 |

## <a name="next-steps"></a>后续步骤

- [使用 PKCS 证书](certficates-pfx-configure.md)，或[从 Symantec PKI 管理器 Web 服务颁发 PKCS 证书](certificates-symantec-configure.md)
- [添加第三方 CA 以通过 Intune 使用 SCEP](certificate-authority-add-scep-overview.md)
- 有关其他帮助，请使用[在 Microsoft Intune 中对 SCEP 证书配置文件部署进行故障排除](https://support.microsoft.com/help/4457481/troubleshooting-scep-certificate-profile-deployment-in-intune)指南。
