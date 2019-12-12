---
title: 在 Microsoft Intune 中使用私钥证书和公钥证书 - Azure | Microsoft Docs
description: 使用 Microsoft Intune 的公钥加密标准 (PKCS) 证书。 其中包括使用根证书和证书模板、安装 Intune 证书连接器 (NDES) 和 PKCS 证书的设备配置文件。
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
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3db085e6e88f8f57eb0276afa77290df8574568f
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "73801711"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>在 Intune 中配置和使用 PKCS 证书

Intune 支持使用私钥和公钥对 (PKCS) 证书。 本文有助于帮助配置所需的本地证书连接器等基础结构，导出 PKCS 证书，然后将证书添加到 Intune 设备配置配置文件。

Microsoft Intune 包括内置的设置来使用 PKCS 证书对组织资源进行访问和身份验证。 证书用于进行身份验证并保证用户安全访问公司资源（例如 VPN 或 WiFi 网络）。 使用 Intune 中的设备配置配置文件，将这些设置部署到设备。

有关使用导入的 PKCS 证书的信息，请参阅[导入的 PFX 证书](certificates-imported-pfx-configure.md)。


## <a name="requirements"></a>要求

要在 Intune 中使用 PKCS 证书，必须具有以下基础结构：

- **Active Directory 域**：  
  此部分中列出的所有服务器都必须加入 Active Directory 域。

  有关安装和配置 Active Directory 域服务 (AD DS) 的详细信息，请参阅 [AD DS 设计和规划](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning)。

- **证书颁发机构**：  
   企业证书颁发机构 (CA)。

  有关安装和配置 Active Directory 证书服务 (AD CS) 的信息，请参阅 [Active Directory 证书服务分步指南](https://technet.microsoft.com/library/cc772393)。

  > [!WARNING]  
  > Intune 要求在企业证书颁发机构 (CA) 而非独立 CA 中运行 AD CS。

- **客户端**：  
  连接到企业 CA。

- **根证书**：  
  从企业 CA 导出的根证书的副本。

- Microsoft Intune 证书连接器  （亦称为“NDES 证书连接器”）  ：  
  在 Intune 门户中，转到“设备配置” > “证书连接器” > “添加”，然后按照“为 PKCS #12 安装连接器的步骤”操作     。 使用门户中的下载链接开始下载证书连接器安装程序 NDESConnectorSetup.exe  。  

  Intune 支持每个租户最多拥有 100 个此连接器实例。 连接器的每个实例都必须位于单独的 Windows 服务器上。 可以将此连接器的实例与 Microsoft Intune PFX 证书连接器的实例安装在同一服务器上。 使用多个连接器时，连接器基础结构支持高可用性和负载均衡，因为所有可用连接器实例都可以处理 PKCS 证书请求。 

  连接器处理用于身份验证或 S/MIME 电子邮件签名的 PKCS 证书请求。

  Microsoft Intune 证书连接器还支持美国联邦信息处理标准 (FIPS) 模式。 FIPS 不是必需的，但启用 FIPS 时可颁发和吊销证书。

- **Microsoft Intune 的 PFX 证书连接器**：  
  如果计划使用 S/MIME 电子邮件加密，请使用 Intune 门户下载支持 PFX 证书导入的 PFX 证书连接器  。  转到“设备配置” > “证书连接器” > “添加”，然后按照“为导入的 PFX 证书安装连接器的步骤”操作     。 使用门户中的下载链接开始下载安装程序 PfxCertificateConnectorBootstrapper.exe  。 

  每个 Intune 租户都支持此连接器的一个实例。 可以将此连接器的实例与 Microsoft Intune 证书连接器的实例安装在同一服务器上。

  该连接器处理导入 Intune 中的 PFX 文件的请求，以便为特定用户进行 S/MIME 电子邮件加密。  

  新版本可用时，此连接器可自动更新。 要使用更新功能，必须：
  - 在服务器上安装 Microsoft Intune 的 PFX 证书连接器。  
  - 要自动接收重要更新，请确保防火墙已打开，以便连接器从端口 443 访问 autoupdate.msappproxy.net   。   

  若要详细了解 Intune 和连接器可以访问的网络终结点，请参阅 [Microsoft Intune 网络终结点](../fundamentals/intune-endpoints.md)。

- **Windows Server**：  
  使用 Windows Server 托管以下内容：

  - Microsoft Intune 证书连接器 - 用于身份验证和 S/MIME 电子邮件签名方案
  - Microsoft Intune 的 PFX 证书连接器 - 用于 S/MIME 电子邮件加密方案。

  Intune 支持在 Microsoft Intune 证书连接器所在的服务器上安装 PFX 证书连接器   。
  
## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>从企业 CA 中导出根证书

要使用 VPN、WiFi 或其他资源对设备进行身份验证，设备需要根证书或中间 CA 证书。 以下步骤介绍如何从企业 CA 中获取所需的证书。

**使用命令行**：  
1. 使用管理员帐户登录根证书颁发机构服务器。
 
2. 转到“开始” > “运行”，然后输入“Cmd”以打开命令提示符    。 
    
3. 指定“certutil -ca.cert ca_name.cer”  ，以将根证书导出为“ca_name.cer”  文件。



## <a name="configure-certificate-templates-on-the-ca"></a>在 CA 上配置证书模板

1. 使用具有管理权限的帐户登录到企业 CA。
2. 打开“证书颁发机构”  控制台，右键单击“证书模板”  ，然后选择“管理”  。
3. 找到“用户”证书模板，右键单击该模板，然后选择“复制模板”以打开“新建模板的属性面板”    。

    > [!NOTE]
    > 对于 S/MIME 电子邮件签名和加密方案，许多管理员使用单独的证书进行签名和加密。 如果使用 Microsoft Active Directory 证书服务，则针对 S/MIME 电子邮件签名证书可使用“仅 Exchange 签名”模板，针对 S/MIME 加密证书可使用“Exchange 用户”模板   。  如果使用第三方证书颁发机构，建议查看其指南，设置签名和加密模板。

4. 在“兼容性”  选项卡上：

    - 将“证书颁发机构”  设置为“Windows Server 2008 R2” 
    - 将“证书接收人”  设置为“Windows 7 / Server 2008 R2” 

5. 在“通用”选项卡上，将“模板显示名称”设置为对你有意义的名称   。

    > [!WARNING]
    > 默认情况下，“模板名称”  与“模板显示名称”  相同，不包含空格  。 请记下模板名称，供以后使用。

6. 在“请求处理”中，选择“允许导出私钥”   。
7. 在“加密”  处，确认将“最小密钥大小”  设置为 2048。
8. 在“使用者名称”处，选择“在请求中提供”   。
9. 在“扩展”  处，确认在“应用程序策略”  下显示有加密文件系统、安全电子邮件和客户端身份验证。

    > [!IMPORTANT]
    > 对于 iOS 证书模板，转到“扩展”  选项卡，更新“密钥用法”  ，并确保未选择“数字签名为原件的证明”  。

10. 在“安全”  选项中，为安装 Microsoft Intune 证书连接器的服务器添加计算机帐户。 允许该帐户具有读取  和注册  权限。
11. 选择“应用”   > “确认”  以保存证书模板。 关闭“证书模板控制台”  。
12. 在“证书颁发机构”  控制台中，右键单击“证书模板”   > “新建”   > “要颁发的证书模板”  。 选择在先前步骤中创建的模板。 选择“确定”  。
13. 为了让服务器管理已注册设备和用户的证书，请使用以下步骤：

    1. 右键单击“证书颁发机构”，选择“属性”  。
    2. 在“安全”选项卡上，添加运行连接器（Microsoft Intune 证书连接器和 Microsoft Intune 的 PFX 证书连接器）的服务器的计算机帐户   。 
    3. 向计算机帐户授予“发布和管理证书”  以及“请求证书”  允许权限。

14. 注销企业 CA。

## <a name="download-install-and-configure-the-microsoft-intune-certificate-connector"></a>下载、安装和配置 Microsoft Intune 证书连接器

> [!IMPORTANT]  
> Microsoft Intune 证书连接器不能安装在颁发的证书颁发机构 (CA) 上，而必须安装在单独的 Windows 服务器上。  

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 选择“租户管理”   > “连接器和令牌”   > “证书连接器”   > “+ 添加”  。

3. 针对 PKCS #12 的连接器单击“下载证书连接器软件”  并将文件保存到可从服务器上进行访问的位置，将在该服务器上安装连接器。

   ![Microsoft Intune 证书连接器下载](./media/certficates-pfx-configure/download-ndes-connector.png)
 
4. 下载完成后，登录服务器。 然后：

    1. 确保已安装 .NET 4.5 Framework 或更高版本，因为它是 NDES 证书连接器的必需项。 Windows Server 2012 R2 和更高版本中自动包含 .NET 4.5 Framework。
    2. 运行安装程序 (NDESConnectorSetup.exe) 并接受默认位置。 连接器将安装到 `\Program Files\Microsoft Intune\NDESConnectorUI`。 在安装程序选项中，选择“PFX 分发”  。 继续并完成安装。
    3. 默认情况下，连接器服务在本地系统帐户下运行。 如果需要通过代理访问 Internet，请确认本地服务帐户可以访问服务器上的代理设置。

5. 此时，Microsoft Intune 证书连接器打开“注册”  选项卡。要启用到 Intune 的连接，请“登录”并输入具有全局管理权限的帐户  。
6. 在“高级”  选项卡上，建议让“使用此计算机的系统帐户(默认)”  保持选中状态。
7. 应用   > 关闭 
8. 返回到 Intune 门户（“Intune” > “设备配置” > “认证连接器”）    。 片刻之后，将显示绿色复选标记，且“连接状态”显示“可用”   。 连接器服务器现可与 Intune 通信。
9. 如果网络环境中有 Web 代理，则可能需要其他配置才能使连接器正常运行。 有关详细信息，请参阅 Azure Active Directory 文档中的[使用现有本地代理服务器](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers)。

> [!NOTE]  
> Microsoft Intune 证书连接器支持 TLS 1.2。 如果在托管连接器的服务器上安装了 TLS 1.2，则连接器使用 TLS 1.2。 否则，使用 TLS 1.1。 目前，TLS 1.1 用于设备和服务器之间的身份验证。

## <a name="create-a-trusted-certificate-profile"></a>创建受信任的证书配置文件

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 选择“设备”   > “配置文件”   > “创建配置文件”  。

   ![导航到 Intune 并为受信任的证书创建新的配置文件](./media/certficates-pfx-configure/certificates-pfx-configure-profile-new.png)

3. 输入以下属性：

    - 配置文件的名称 
    - （可选）设置描述
    - 将配置文件部署到的平台 
    - 将配置文件类型  设置为“受信任的证书” 

4. 选择“设置”  并指定之前导出的 .cer 文件根 CA 证书。

   > [!NOTE]
   > 能否为证书选择“目标存储区”取决于步骤 2 中所选的平台   。

   ![创建配置文件并上传受信任的证书](./media/certficates-pfx-configure/certificates-pfx-configure-profile-fill.png)

5. 选择“确定”   > “创建”  以保存配置文件。

6. 若要将新配置文件分配给一个或多个设备，请参阅[分配 Microsoft Intune 设备配置文件](../configuration/device-profile-assign.md)。

## <a name="create-a-pkcs-certificate-profile"></a>创建 PKCS 证书配置文件

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 选择并转到“设备”   > “配置文件”   > “创建配置文件”  。

3. 输入以下属性：

    - 配置文件的名称 
    - （可选）设置描述
    - 将配置文件部署到的平台 
    - 将“配置文件类型”设置为“PKCS 证书”  

4. 选择“设置”  ，并配置适用于所选平台的属性：
   
   |设置     | 平台     | 详细信息   |
   |------------|------------|------------|
   |续订阈值 (%)         |全部         |建议设为 20%  | 
   |证书有效期   |全部         |如果没有更改证书模板，则此选项可能设置为一年。 |
   |密钥存储提供程序 (KSP)    |Windows 10  | 对于 Windows，请选择在设备上存储密钥的位置。 |
   |证书颁发机构       |全部         |显示企业 CA 的内部完全限定的域名 (FQDN)。  |
   |证书颁发机构名称  |全部         |列出企业 CA 的名称，例如“Contoso 证书颁发机构”。 |
   |证书类型              |macOS       |选择一个类型： <br> **-** **用户**证书可在证书使用者和 SAN 中同时包含用户和设备属性。 <br><br>**-** **设备**证书只能在证书使用者和 SAN 中包含设备属性。 设备适用于无用户设备（例如网亭或其他共享设备）的情况。  <br><br> 此选择影响使用者名称格式。 |
   |**使用者名称格式**          |全部         |对于大多数平台，除非另有要求，否则请将此选项设置为“公用名”  。<br><br>对于 macOS，使用者名称格式由证书类型决定。 请参阅本文后面的 [macOS 的使用者名称格式](#subject-name-format-for-macos)。 |
   |**使用者可选名称**     |全部         |除非另有要求，否则将此选项设置为“用户主体名称 (UPN)”  。 |
   |**扩展密钥用法**           |**-** Android 设备管理员 <br>**-** Android Enterprise（*设备所有者* *工作配置文件*） <br> **-** Windows 10 |证书通常需要“客户端身份验证”，以便用户或设备能够对服务器进行身份验证  。 |
   |**允许所有应用访问私钥** |macOS  |请将其设置为“启用”，以使为关联的 Mac 设备配置的应用可以访问 PKCS 证书私钥  。 <br><br> 有关此设置的详细信息，请参阅 Apple 开发人员文档中[配置文件参考](https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf)中的 AllowAllAppsAccess 证书有效负载部分  。 |
   |**根证书**             |**-** Android 设备管理员 <br> **-** Android Enterprise（*设备所有者* *工作配置文件*） |选择以前分配的根 CA 证书配置文件。 |

5. 选择“确定”   > “创建”  以保存配置文件。

6. 若要将新配置文件分配给一个或多个设备，请参阅[分配 Microsoft Intune 设备配置文件](../configuration/device-profile-assign.md)。

   > [!NOTE]
   > 在应用了 Android Enterprise 配置文件的设备上，使用 PKCS 证书配置文件安装的证书在设备上不可见。 若要确认证书部署是否成功，请检查 Intune 控制台中配置文件的状态。

### <a name="subject-name-format-for-macos"></a>macOS 的使用者名称格式

创建 macOS PKCS 证书配置文件时，使用者名称格式的选项取决于所选的证书类型，即“用户”或“设备”   。  

> [!NOTE]  
> 当生成的证书签名请求 (CSR) 中的使用者名称包含以下字符之一作为转义字符（后跟反斜杠 \\）时，使用 PKCS 获取证书存在[与 SCEP 相同的](certificates-profile-scep.md#avoid-certificate-signing-requests-with-escaped-special-characters)已知问题：
> - \+
> - ;
> - 、
> - =

- **“用户”证书类型**  
  使用者名称格式的格式选项包括两个变量  ：公用名 (CN)  和电子邮件 (E)  。 可将“公用名(CN)”设置为以下任何变量  ：

  - **CN={{UserName}}** ：用户的用户主体名称，例如 janedoe@contoso.com。
  - **CN={{AAD_Device_ID}}** ：在 Azure Active Directory (AD) 中注册设备时分配的 ID。 此 ID 通常用于向 Azure AD 进行身份验证。
  - **CN={{SERIALNUMBER}}** ：制造商通常用于标识设备的唯一序列号 (SN)。
  - **CN={{IMEINumber}}** ：用于标识移动电话的国际移动设备标识 (IMEI)。
  - **CN={{OnPrem_Distinguished_Name}}** ：用逗号分隔的一系列相对可分辨名称，如 CN=Jane Doe、OU=UserAccounts、DC=corp、DC=contoso、DC=com  。

    要使用 {{OnPrem_Distinguished_Name}} 变量，请确保使用 [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) 将onpremisesdistinguishedname 用户属性与 Azure AD 同步   。

  - **CN={{onPremisesSamAccountName}}** ：管理员可以使用 Azure AD 连接到名为 onPremisesSamAccountName 的属性，将 Active Directory 中的 samAccountName 属性同步到 Azure AD  。 Intune 可以将该变量替换为证书使用者中的证书颁发请求的一部分。 samAccountName 属性是指用户登录名，该名称用于支持早期版本的 Windows（Windows 2000 之前）中的客户端和服务器。 用户登录名的格式为：DomainName\testUser，或仅 testUser   。

    要使用 {{onPremisesSamAccountName}} 变量，请确保使用 [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) 将 onPremisesSamAccountName 用户属性与 Azure AD 同步   。

  通过使用这些变量的一个或多个与静态字符串的组合，可以创建一个自定义使用者名称格式，例如：  
  - CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US 
  
  该示例包含使用者名称格式，其中除了不仅使用了 CN 和 E 变量，还使用了组织单元、组织、位置、省/直辖市/自治区和国家/地区值的字符串。 [CertStrToName 函数](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx)介绍此函数及其支持的字符串。

- **“设备”证书类型**  
  “使用者名称格式”的格式选项包括以下变量： 
  - **{{AAD_Device_ID}}**
  - **{{Device_Serial}}**
  - **{{Device_IMEI}}**
  - **{{SerialNumber}}**
  - **{{IMEINumber}}**
  - **{{AzureADDeviceId}}**
  - **{{WiFiMacAddress}}**
  - **{{IMEI}}**
  - **{{DeviceName}}**
  - **{{FullyQualifiedDomainName}}** （仅适用于 Windows 和加入域的设备） 
  - **{{MEID}}**

  可在文本框中指定这些变量，后跟变量的文本。 例如，可以将名为 Device1 的设备的公用名添加为 CN={{DeviceName}}Device1   。

  > [!IMPORTANT]  
  > - 指定变量时，请将变量名称括在大括号 {} 中（如示例中所示），以避免出现错误。  
  > - 在设备证书的使用者或 SAN 中使用的设备属性（例如 IMEI、SerialNumber 和 FullyQualifiedDomainName）可能被有权访问设备的人员仿造      。
  > - 设备必须支持在证书配置文件中为该配置文件指定的所有变量，才能在该设备上安装。  例如，如果在 SCEP 配置文件的使用者名称中使用 {{IMEI}} 并将其分配给没有 IMEI 号码的设备，则配置文件安装将失败  。  
 


## <a name="whats-new-for-connectors"></a>连接器的新增功能

我们将定期发布这两个证书连接器的更新。 更新连接器时，你可以在此处阅读有关更改的信息。

Microsoft Intune 的 PFX 证书连接器[支持自动更新](#requirements)，而 Intune 证书连接器则需要手动更新   。

### <a name="may-17-2019"></a>2019 年 5 月 17 日

- **Microsoft Intune 的 PFX 证书连接器 - 版本 6.1905.0.404**  
  此版本中的更改：  
  - 修复了以下问题：因现有 PFX 证书持续重新处理而导致连接器停止处理新请求。 

### <a name="may-6-2019"></a>2019 年 5 月 6 日

- **Microsoft Intune 的 PFX 证书连接器 - 版本 6.1905.0.402**  
  此版本中的更改：  
  - 连接器的轮询间隔从 5 分钟降到了 30 秒。
 
### <a name="april-2-2019"></a>2019 年 4 月 2日

- **Intune 证书连接器 - 版本 6.1904.1.0**  
  此版本中的更改：  
  - 解决了使用全局管理员帐户登录连接器后连接器可能无法注册到 Intune 的问题。  
  - 包括证书吊销的可靠性修补程序。  
  - 包括性能修补程序，以提高处理 PKCS 证书请求的速度。  

- **Microsoft Intune 的 PFX 证书连接器 - 版本 6.1904.0.401**
  > [!NOTE]  
  > 此版本的 PFX 连接器的自动更新直到 2019 年 4 月 11 日才可用。  

  此版本中的更改：  
  - 解决了使用全局管理员帐户登录连接器后连接器可能无法注册到 Intune 的问题。  


## <a name="next-steps"></a>后续步骤

配置文件已创建，但它尚未起到任何作用。 下一步，[分配配置文件](../configuration/device-profile-assign.md)并[监视其状态](../configuration/device-profile-monitor.md)。

[使用 SCEP 证书](certificates-scep-configure.md)，或[从 Symantec PKI 管理器 Web 服务颁发 PKCS 证书](certificates-digicert-configure.md)。
