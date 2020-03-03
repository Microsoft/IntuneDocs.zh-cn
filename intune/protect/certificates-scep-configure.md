---
title: 配置基础结构以支持在 Microsoft Intune 中使用 SCEP 证书配置文件 - Azure | Microsoft Docs
description: 要在 Microsoft Intune 中使用 SCEP，请配置本地 AD 域、创建证书颁发机构、设置 NDES 服务器，并安装 Intune 证书连接器。
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
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c454ae6184f4d2a7c3c31f3c61d2cf4331ac187c
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514092"
---
# <a name="configure-infrastructure-to-support-scep-with-intune"></a>配置基础结构以支持在 Intune 中使用 SCEP

Intune 支持使用简单证书注册协议 (SCEP) 来[验证体验与应用和公司资源的连接](certificates-configure.md)。 SCEP 使用证书颁发机构 (CA) 证书来保护证书签名请求 (CSR) 的消息交换。 当基础结构支持 SCEP 时，可以使用 Intune SCEP 证书  配置文件（Intune 中的一种设备配置文件）将证书部署到设备。 使用 Active Directory 证书服务证书颁发机构时，需要 Microsoft Intune 证书连接器才可在 Intune 中使用 SCEP 证书配置文件。 使用[第三方证书颁发机构](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration)时，不需要该连接器。 

本文中的信息可帮助配置基础结构，以便在使用 Active Directory 证书服务时支持 SCEP。 在配置基出结构后，可以在 Intune 中[创建和部署 SCEP 证书配置文件](certificates-profile-scep.md)。

> [!TIP]
> Intune 还支持使用[公钥加密标准 12 号证书](certficates-pfx-configure.md)。

## <a name="prerequisites-for-using-scep-for-certificates"></a>使用 SCEP 证书的先决条件

在继续操作之前，请确保[已创建受信任的证书配置文件](certificates-configure.md#export-the-trusted-root-ca-certificate)并将其部署到将使用 SCEP 证书配置文件的设备  。 SCEP 证书配置文件直接引用用于通过受信任的根 CA 证书来预配设备的受信任证书配置文件。

### <a name="servers-and-server-roles"></a>服务器和服务器角色

以下本地基础结构必须在已加入 Active Directory 域的服务器上运行，Web 应用程序代理服务器除外。

- 证书颁发机构  - 使用在 Windows Server 2008 R2 企业版 Service Pack 1 或更高版本上运行的 Microsoft Active Directory 证书服务企业证书颁发机构 (CA)。 所用 Windows Server 版本必须仍受 Microsoft 支持。 不支持独立 CA。 有关详细信息，请参阅[安装证书颁发机构](https://technet.microsoft.com/library/jj125375.aspx)。 如果 CA 运行的是 Windows Server 2008 R2 SP1，则必须[安装修补程序 KB2483564](https://support.microsoft.com/kb/2483564/)。

- NDES 服务器角色  - 必须在 Windows Server 2012 R2 或更高版本上配置网络设备注册服务 (NDES) 服务器角色。 本文的后面部分介绍了如何[安装 NDES](#set-up-ndes)。

  - 托管 NDES 的服务器必须已加入域，并与企业 CA 位于相同的林中。
  - 不可使用在托管企业 CA 的服务器上安装的 NDES。
  - 可以将 Microsoft Intune 证书连接器安装在托管 NDES 的同一服务器上。

  要详细了解 NDES，请参阅 Windows Server 文档[网络设备注册服务指南](https://technet.microsoft.com/library/hh831498.aspx)以及 [Using a Policy Module with the Network Device Enrollment Service（将策略模块与网络设备注册服务配合使用）](https://technet.microsoft.com/library/dn473016.aspx)。

- Microsoft Intune 证书连接器  - 需要 Microsoft Intune 证书连接器才可在 Intune 中使用 SCEP 证书配置文件。 本文介绍了如何[安装此连接器](#install-the-intune-certificate-connector)。

  该连接器支持美国联邦信息处理标准 (FIPS) 模式。 FIPS 不是必需的，但启用它时可颁发和吊销证书。
  - 该连接器必须与 NDES 服务器角色在同一服务器上运行，且该服务器运行 Windows Server 2012 R2 或更高版本。
  - 该连接器需要 .NET 4.5 Framework，而 Windows Server 2012 R2 中自动包含 .NET 4.5 Framework。
  - 必须在托管 NDES 和 Microsoft Intune 证书连接器的服务器上[禁用](https://technet.microsoft.com/library/cc775800(v=WS.10).aspx) Internet Explorer 增强型安全配置。

以下本地基础结构是可选的：

要允许 Internet 上的设备获取证书，需要将 NDES URL 发布到企业网络外部。 可以使用 Azure AD 应用程序代理、Web 应用程序代理服务器或其他反向代理。

- Azure AD 应用程序代理  （可选）- 可以使用 Azure AD 应用程序代理（而不是专用的 Web 应用程序代理 (WAP) 服务器）向 Internet 发布 NDES URL。 这允许面向 Intranet 和面向 Internet 的设备获取证书。 有关详细信息，请参阅[如何提供对本地应用程序的安全远程访问](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy)。

- Web 应用程序代理服务器  （可选）- 使用运行 Windows Server 2012 R2 或更高版本的服务器作为 Web 应用程序代理 (WAP) 服务器来将 NDES URL 发布到 Internet。  这允许面向 Intranet 和面向 Internet 的设备获取证书。

  承载 WAP 的服务器[必须安装此更新](https://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx)以支持网络设备注册服务所使用的长 URL。 该更新包括在 [2014 年 12 月的更新汇总中](https://support.microsoft.com/kb/3013769)，或单独更新自 [KB3011135](https://support.microsoft.com/kb/3011135)。

  WAP 服务器必须具有与发布到外部客户端的名称匹配的 SSL 证书，并且信任托管 NDES 服务的计算机上使用的 SSL 证书。 这些证书使 WAP 服务器可以终止来自客户端的 SSL 连接，并创建与 NDES 服务的新 SSL 连接。

  有关详细信息，请参阅[规划 WAP 证书](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383650(v=ws.11)#plan-certificates)和[有关 WAP 服务器的常规信息](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn584113(v=ws.11))。

### <a name="accounts"></a>帐户

- NDES 服务帐户  - 在设置 NDES 前，确定要用作 NDES 服务帐户的域用户帐户。 可以在配置 NDES 之前，在配置发证 CA 上的模板时指定该帐户。

  此帐户必须对托管 NDES 的服务器拥有以下权限：

  - 本地登录 
  - 作为服务登录 
  - 作为批处理作业登录 

  有关详细信息，请参阅[创建充当 NDES 服务帐户的域用户帐户](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831498(v=ws.11)#to-create-a-domain-user-account-to-act-as-the-ndes-service-account)。

- 对托管 NDES 服务的计算机的访问权限  - 需要一个有权限在安装 NDES 的服务器上安装和配置 Windows 服务器角色的域用户帐户。

- 对证书颁发机构的访问权限  - 需要一个有权管理证书颁发机构的与用户帐户。

### <a name="network-requirements"></a>网络要求

建议通过反向代理（例如，[Azure AD 应用程序代理、Web 访问代理](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/)或第三方代理）发布 NDES 服务器。 如果不使用反向代理，则允许端口 443 上的 TCP 流量从 Internet 上的所有主机和 IP 地址传输到 NDES 服务。

允许 NDES 服务和环境中任何支持基础结构之间进行通信所需的所有端口和协议。 例如，托管 NDES 服务的计算机需要与 CA、DNS 服务器、域控制器以及环境中可能的其他服务或服务器（例如 Configuration Manager）进行通信。

### <a name="certificates-and-templates"></a>证书和模板

使用 SCEP 时，使用了以下证书和模板。

|对象    |详细信息    |
|----------|-----------|
|**SCEP 证书模板**         |将在发证 CA 上配置的模板，用于完成设备 SCEP 请求。 |
|**客户端身份验证证书** |从发证 CA 或公共 CA 请求。<br /> 此证书安装在托管 NDES 服务的计算机上，供 Intune 证书连接器使用。<br /> 如果证书已在用于颁发证书的 CA 模板上设置客户端和服务器身份验证密钥用法（增强型密钥使用）    ， 则可将相同的证书用于服务器和客户端身份验证。 |
|**服务器身份验证证书** |发证 CA 或公共 CA 请求 Web 服务器证书。<br /> 在托管 NDES 的计算机上的 IIS 中安装并绑定此 SSL 证书。<br />如果证书已在用于颁发证书的 CA 模板上设置客户端和服务器身份验证密钥用法（增强型密钥使用）    ， 则可将相同的证书用于服务器和客户端身份验证。 |
|**受信任的根 CA 证书**       |要使用 SCEP 证书配置文件，设备必须信任受信任的根证书颁发机构 (CA)。 在 Intune 中使用受信任的证书配置文件为用户和设备预配受信任的根 CA 证书  。 <br/><br/> -  在每个操作系统平台上使用一个受信任的根 CA 证书，并将该证书与创建的每个受信任的根证书配置文件关联。 <br /><br /> -  可以在需要时使用其它受信任的根 CA 证书。 例如，可以使用其他证书来信任为 Wi-Fi 访问点的服务器身份验证证书签名的 CA。 为发证 CA 创建其他受信任的根 CA 证书。  对于在 Intune 中创建的 SCEP 证书配置文件，请确保在其中为发证 CA 指定受信任的根 CA 配置文件。<br/><br/> 有关受信任证书配置文件的信息，请参阅“在 Intune 中使用证书进行身份验证”中的[导出受信任的 CA 证书](certificates-configure.md#export-the-trusted-root-ca-certificate)和[创建受信任的证书配置文件](certificates-configure.md#create-trusted-certificate-profiles)  。 |

## <a name="configure-the-certification-authority"></a>配置证书颁发机构

在以下各节介绍了如何：

- 为 NDES 配置和发布所需模板
- 设置吊销证书的所需权限。

完成以下各节需要具备 Windows Server 2012 R2 或更高版本和 Active Directory 证书服务 (AD CS) 方面的知识。

### <a name="access-your-issuing-ca"></a>访问发证 CA

1. 使用有权管理 CA 的域帐户登录发证 CA。

2. 打开证书颁发机构 Microsoft 管理控制台 (MMC)。 运行“certsrv.msc”，或在服务器管理器中单击“工具”，然后单击“证书颁发机构”     。

3. 选择“证书模板”节点，单击“操作” > “管理”    。

### <a name="create-the-scep-certificate-template"></a>创建 SCEP 证书模板

1. 创建 v2 证书模板（具有 Windows 2003 兼容性），用作 SCEP 证书模板。 你可以：

   - 使用“证书模板”管理单元创建新的自定义模板  。
   - 复制现有模板（如用户模板）然后更新，将其用作 NDES 模板。

2. 在模板的指定选项卡上配置以下设置：

   - 常规  ：

     - 取消选中“在 Active Directory 中发布证书”  。
     - 指定一个友好的“模板显示名称”，以便稍后识别此模板  。

   - **使用者名称**：

     - 选择“在请求中提供”  。 由适用于 NDES 的 Intune 策略模块强制实施安全措施。

       ![模板，“使用者名称”选项卡](./media/certificates-scep-configure/scep-ndes-subject-name.jpg)

   - **扩展**：

     - 确保“应用程序策略描述”包括“客户端身份验证”   。

       > [!IMPORTANT]
       > 只添加所需的应用程序策略即可。 与你的安全管理员确认你的选择。

     - 对于 iOS/iPadOS 和 macOS 证书模板，请编辑“密钥用法”并确保未选择“数字签名为原件的证明”   。

     ![模板，“扩展”选项卡](./media/certificates-scep-configure/scep-ndes-extensions.jpg)  

   - **安全性**：

     - 添加 NDES 服务帐户  。 此帐户需要具有此模板的读取  和注册  权限。

     - 为将创建 SCEP 配置文件的 Intune 管理员添加其他帐户。 这些帐户需要模板的读取权限，以便使这些管理员能够在创建 SCEP 配置文件时浏览此模板  。

     ![模板，“安全”选项卡](./media/certificates-scep-configure/scep-ndes-security.jpg)

   - 请求处理  ：

     下图是一个示例。 你的配置可能有所不同。  

     ![模板，“请求处理”选项卡](./media/certificates-scep-configure/scep-ndes-request-handling.png)

   - 颁发要求  ：

     下图是一个示例。 你的配置可能有所不同。

     ![模板，“颁发要求”选项卡](./media/certificates-scep-configure/scep-ndes-issuance-reqs.jpg)

3. 保存证书模板。

### <a name="create-the-client-certificate-template"></a>创建客户端证书模板

Intune 证书连接器要求某个证书的“客户端身份验证”增强型密钥用法和使用者名称与安装连接器的计算机的 FQDN 相同  。 需要添加具有以下属性的模板：

- “扩展” > “应用程序策略”必须包含“客户端身份验证”   
- “使用者名称” > “在请求中提供”   。

如果已有包含这些属性的模板，则可以重复使用它，否则可以通过复制现有模板或创建自定义模板来创建新模板。

### <a name="create-the-server-certificate-template"></a>创建服务器证书模板

托管设备和 NDES 服务器上的 IIS 之间的通信使用 HTTPS，这需要使用证书。 可以使用 Web 服务器证书模板来颁发此证书  。 或者，如果想要使用专用模板，则需要以下属性：

- “扩展” > “应用程序策略”必须包含“服务器身份验证”   
- “使用者名称” > “在请求中提供”   。

> [!NOTE]
> 如果证书同时满足客户端和服务器证书模板的要求，则可以对 IIS 和 Intune 证书连接器使用单个证书。

### <a name="grant-permissions-for-certificate-revocation"></a>授予吊销证书的权限

为了使 Intune 能够吊销不再需要的证书，必须授予证书颁发机构权限。

在 Intune 证书连接器上，可以使用 NDES 服务器系统帐户或特定帐户（如 NDES 服务帐户）   。

1. 在“证书颁发机构”控制台中，右键单击 CA 名称，然后单击“属性”  。

2. 在“安全”  选项卡中，单击“添加”  。

3. 授予“颁发和管理证书”权限  ：

   - 如果选择使用 NDES 服务器系统帐户，请提供针对 NDES 服务器的权限  。
   - 如果选择使用 NDES 服务帐户，则改为提供针对该帐户权限  。

### <a name="modify-the-validity-period-of-the-certificate-template"></a>修改证书模板的有效期

可选择修改证书模板的有效期。  

[创建 SCEP 证书模板](#create-the-scep-certificate-template)后，可以编辑模板，在“常规”选项卡上查看“有效期”   。

默认情况下，Intune 使用模板中配置的值。 但是，可以将 CA 配置为允许申请者输入其他值，并且可在 Intune 控制台中设置该值。

> [!IMPORTANT]
> 对于 iOS/iPadOS 和 macOS，请始终使用模板中设置的值。

#### <a name="to-configure-a-value-that-can-be-set-from-within-the-intune-console"></a>配置可在 Intune 控制台中设置的值

1. 请在 CA 上运行以下命令：

   -**certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**
   -**net stop certsvc**
   -**net start certsvc**

2. 在发证 CA 上，使用证书颁发机构管理单元发布证书模板。 选择“证书模板”节点，选择“操作” > “新建” > “要颁发的证书模板”，然后选择在前面一节中创建的模板     。

3. 通过查看“证书模板”  文件夹中已发布的模板来对该模板进行验证。

## <a name="set-up-ndes"></a>设置 NDES

以下过程可帮助配置用于 Intune 的网络设备注册服务 (NDES)。 有关 NDES 的详细信息，请参阅[网络设备注册服务指南](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831498(v%3dws.11))。

### <a name="install-the-ndes-service"></a>安装 NDES 服务

1. 在将要通过 NDES 服务的服务器上，以“企业管理员”身份登录，并使用[添加角色和功能向导](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831809(v=ws.11))安装 NDES  ：

   1. 在向导中，选择“Active Directory 证书服务”  以获得对 AD CS 角色服务的访问权限。 选择“网络设备注册服务”  ，取消选中“证书颁发机构”  ，然后完成向导。

      > [!TIP]
      > 在“安装进度”  处，不要选择“关闭”  。 而是选择“配置目标服务器上的 Active Directory 证书服务”的链接  。 “AD CS 配置”向导随即打开，它可用于本文中的下一个过程：“配置 NDES 服务”   。 打开“AD CS 配置”后，你可以关闭“添加角色和功能”向导。

   2. 将 NDES 添加到服务器后，向导也会安装 IIS。 确认 IIS 具有以下配置：

      - “Web 服务器” > “安全性” > “请求筛选”   
      - “Web 服务器” > “应用程序开发” > “ASP.NET 3.5”   

        安装 ASP.NET 3.5 会安装 .NET Framework 3.5。 安装 .NET Framework 3.5 时，安装核心“.NET Framework 3.5”  功能和“HTTP 激活”  。

      - “Web 服务器” > “应用程序开发” > “ASP.NET 4.5”   

        安装 ASP.NET 4.5 会安装 .NET Framework 4.5。 安装 .NET Framework 4.5 时，安装核心“.NET Framework 4.5”功能、“ASP.NET 4.5”和“WCF 服务” > “HTTP 激活”功能     。

      - “管理工具” > “IIS 6 管理兼容性” > “IIS 6 元数据库兼容性”   
      - “管理工具” > “IIS 6 管理兼容性” > “IIS 6 WMI 兼容性”   
      - 在服务器上，将 NDES 服务帐户添加为本地“IIS_IUSR”组成员  。

2. 在托管 NDES 服务的计算机中，在提升的命令提示符处运行以下命令。 以下命令可设置 NDES 服务帐户的 SPN：

   `setspn -s http/<DNS name of the computer that hosts the NDES service> <Domain name>\<NDES Service account name>`

   例如，如果托管 NDES 服务的计算机名为 Server01  ，域为 Contoso.com  ，并且服务帐户为 NDESService  ，则使用：

   `setspn –s http/Server01.contoso.com contoso\NDESService`  

### <a name="configure-the-ndes-service"></a>配置 NDES 服务

1. 在托管 NDES 服务的计算机中，打开“AD CS 配置”向导，然后进行以下更新  ：

   > [!TIP]
   > 如果从上一个过程继续，并单击了“在目标服务器上配置 Active Directory 证书服务”链接，则此向导应已打开  。 或者，打开“服务器管理器”访问“Active Directory 证书服务”的后期部署配置。

   - 在“角色服务”中，选择“网络设备注册服务”   。
   - 在“NDES 的服务帐户”中，指定 NDES 服务帐户  。
   - 在“NDES 的 CA”中，单击“选择”，然后选择在其中配置证书模板的发证 CA   。
   - 在“为 NDES 加密”页面，设置符合公司要求的秘钥长度  。
   - 在“确认”页面，选择“配置”，完成向导   。

2. 完成向导后，在托管 NDES 服务的计算机中更新以下注册表项：

   `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\`

   要更新此密钥，请标识证书模板的“目的”（位于“请求处理”选项卡上）   。 然后，通过将现有数据替换为在[创建证书模板](#create-the-scep-certificate-template)时指定的证书模板名称（不是模板的显示名称），更新对应的注册表项。

   下表将证书模板目的映射至注册表中的值：

   |证书模板目的（位于“请求处理”选项卡上）|待编辑的注册表值|在 Intune 管理控制台中显示的 SCEP 配置文件的值|
   |------------------------|-------------------------|---|
   |签名               |SignatureTemplate        |数字签名 |
   |加密              |EncryptionTemplate       |密钥加密  |
   |签名和加密|GeneralPurposeTemplate   |密钥加密 <br/> 数字签名 |

   例如，如果证书模板的目的为“加密”  ，然后将“EncryptionTemplate”  值编辑为你的证书模板的名称。

3. 配置 IIS 请求筛选，在 IIS 中添加对 NDES 服务收到的长 URL（查询）的支持。

   1. 在 IIS 管理器中，选择“默认网站” > “请求筛选” > “编辑功能设置”，打开“编辑请求筛选设置”页面     。

   2. 配置下列设置：

      - 最大 URL 长度(字节) = 65534 
      - 最大查询字符串(字节) = 65534 

   3. 选择“确定”，保存此配置并关闭 IIS 管理器  。

   4. 查看以下注册表项并确认其具有指示的值，以验证此配置：

      `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters`

      以下值设置为 DWORD 值：

      - 名称：MaxFieldLength  ，十进制值为 65534 
      - 名称：MaxRequestBytes  ，十进制值为 65534 

4. 重启托管 NDES服务的服务器。 请勿使用 iisreset  ；iireset 未完成所需更改。

5. 浏览到 http://Server_FQDN/certsrv/mscep/mscep.dll   。 应看到与下图类似的 NDES 页面：

   ![测试 NDES](./media/certificates-scep-configure/scep-ndes-url.png)

   如果 Web 地址返回“503 服务不可用”  ，请查看计算机事件查看器。 当应用程序池因缺少 [NDES 服务帐户权限](#accounts)而停止时，通常会出现此错误。
  
### <a name="install-and-bind-certificates-on-the-server-that-hosts-ndes"></a>在托管 NDES 服务的服务器上安装和绑定证书

> [!TIP]
> 在以下过程中，如果某个服务器配置为同时满足服务器和客户端身份验证的要求，则可以使用单个证书进行“服务器身份验证”和“客户端身份验证”   。 以下过程的步骤 1 和步骤 3 中描述了用于每种身份验证的条件。

1. 从内部 CA 或公共 CA 请求“服务器身份验证”  证书，然后在服务器上安装该证书。

   如果服务器对单个网络地址使用外部和内部名称，则服务器身份验证证书必须具有：

   - “使用者名称”  （包括外部公共服务器名称）。
   - “使用者可选名称”  （包括内部服务器名称）。

2. 在 IIS 中绑定服务器身份验证证书：

   1. 安装服务器身份验证证书后，打开“IIS 管理器”，然后选择“默认网站”   。 在“操作”窗格中，选择“绑定”   。

   1. 选择“添加”，将“类型”设置为“https”并确认端口为“443”     。
   
   1. 为“SSL 证书”  指定服务器身份验证证书。

3. 在你的 NDES 服务器上，请求并安装来自你的内部 CA 或公用证书颁发机构的“客户端身份验证”  证书。

   客户端身份验证证书必须具备以下属性：

   - **增强型密钥使用**：此值必须包括“客户端身份验证”  。
   - **使用者名称**：此值必须与安装证书的服务器（NDES 服务器）的 DNS 名称相同。

4. 托管 NDES 服务的服务器现已支持 Intune 证书连接器。

## <a name="install-the-intune-certificate-connector"></a>安装 Intune 证书连接器

Microsoft Intune 证书连接器安装在运行 NDES 服务的服务器上。 不支持在证书颁发机构 (CA) 所在的同一服务器上使用 NDES 或 Intune 证书连接器。

### <a name="to-install-the-certificate-connector"></a>安装证书连接器

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 选择“租户管理”   > “连接器和令牌”   > “证书连接器”   > “添加”  。

3. 下载并保存 SCEP 文件的连接器。 将该文件保存到可从要安装连接器的服务器访问的位置。

   ![ConnectorDownload](./media/certificates-scep-configure/download-certificates-connector.png)

4. 下载完成后，请转到托管网络设备注册服务 (NDES) 角色的服务器。 然后：

   1. 确认已安装 .NET 4.5 Framework，因为它是 Intune 证书连接器的必需项。 Windows Server 2012 R2 和更高版本中自动包含 .NET 4.5 Framework。

   2. 运行安装程序 (NDESConnectorSetup.exe)  。 安装程序还会安装 NDES 和 IIS 证书注册点 (CRP) Web 服务的策略模块。 CRP Web 服务 CertificateRegistrationSvc 作为 IIS 中的应用程序运行  。

      如果为独立 Intune 安装 NDES，则 CRP 服务会自动随证书连接器一起安装。

5. 提示输入证书连接器的客户端证书时，选取“选择”  ，然后选择在前文[在托管 NDES 的服务器上安装和绑定证书](#install-and-bind-certificates-on-the-server-that-hosts-ndes)过程的步骤 3 中，在 NDES 服务器上安装的“客户端身份验证”  证书。

   选择客户端身份验证证书后，会返回到“Microsoft Intune 证书连接器的客户端证书”  处。 尽管不会显示所选证书，但可以选择“下一步”查看该证书的属性  。 然后依次选择“下一步”和“安装”   。

> [!NOTE]
> 在启动 Intune 证书连接器之前，必须对 GCC High 租户进行以下更改。
> 
> 编辑下面列出的两个配置文件，这将更新 GCC High 环境的服务终结点。 请注意，这些更新会将 URI 的后缀 .com  更改为 .us  后缀。 总共有 3 个 URI 更新，NDESConnectorUI.exe.config 配置文件中有 2 个更新，NDESConnector.exe.config 文件中有 1 个更新。
> 
> - 文件名：<install_Path>\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe.config
> 
>   示例：(%programfiles%\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe.config)
>   ```
>    <appSettings>
>        <add key="SignInURL" value="https://portal.manage.microsoft.us/Home/ClientLogon"/>
>        <add key="LocationServiceEndpoint" value="RestUserAuthLocationService/RestUserAuthLocationService/ServiceAddresses"/>
>        <add key="AccountPortalURL" value="https://manage.microsoft.us"/>
>    </appSettings>
>   ```
> 
> - 文件名：<install_Path>\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config
>
>   示例：(%programfiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config)
>    ```
>    <appSettings>
>        <add key="BaseServiceAddress" value="https://manage.microsoft.us/" />
>    ```
>
> 如果未完成这些编辑，则 GCC High 租户将收到以下错误消息：“访问被拒绝” “你无权查看此页”

6. 在向导完成后，先单击“启动证书连接器 UI，然后再关闭向导”  。

   如果在启动证书连接器 UI 前关闭了向导，你可以通过运行以下命令重新打开它：

   *<install_Path>\NDESConnectorUI\NDESConnectorUI.exe*

7. 在“证书连接器”  UI 中：

   1. 选择“登录”，输入你的 Intune 服务管理员凭据或具有全局管理权限的租户管理员的凭据  。

   2. 必须为所用帐户分配有效的 Intune 许可证。

   3. 登录后，Intune 证书连接器从 Intune 下载证书。 此证书用于连接器和 Intune 之间的身份验证。 如果所用帐户没有 Intune 许可证，则连接器（NDESConnectorUI.exe）无法从 Intune 获取证书。  

      如果组织使用代理服务器并且 NDES 服务器需要代理才能访问 Internet，请选择“使用代理服务器”  。 然后输入用于连接的代理服务器名称、端口和帐户凭据。

   4. 选择“高级”选项卡，然后输入在证书颁发机构上拥有“颁发和管理证书”权限的帐户的凭据   。 单击“应用”以应用更改  。  

    5. 你现在可以关闭证书连接器 UI。

8. 打开命令提示符，输入“services.msc”，然后按 Enter   。 右键单击  “Intune 连接器服务” >   “重启”。

要验证服务是否正在运行，请打开浏览器并输入以下 URL。 应返回 403 错误  ：`https://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll`

> [!NOTE]
> Intune 证书连接器支持 TLS 1.2。 如果托管连接器的服务器支持 TLS 1.2，则使用 TLS 1.2。 如果服务器不支持 TLS 1.2，则使用 TLS 1.1。 目前，TLS 1.1 用于设备和服务器之间的身份验证。

## <a name="next-steps"></a>后续步骤

[创建 SCEP 证书配置文件](certificates-profile-scep.md)  
[Troubleshoot issues for the Intune certificate connector（排查 Intune 证书连接器问题）](troubleshoot-certificate-connector-events.md)
