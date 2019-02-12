---
title: 在 Microsoft Intune 中使用私钥证书和公钥证书 - Azure | Micrososft Docs
description: 向 Microsoft Intune 添加或创建公钥加密标准 (PKCS) 证书，所需步骤如下：导出根证书、配置证书模板、下载和安装 Microsoft Intune 证书连接器 (NDES)、创建设备配置文件，并在 Azure 和证书颁发机构中创建 PKCS 证书配置文件。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5c2c649df23a84d8836a68fd0456da6ce8dda2c0
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55837269"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>在 Intune 中配置和使用 PKCS 证书

证书用于进行身份验证并保证用户安全访问公司资源（例如 VPN 或 WiFi 网络）。 许多组织中都使用采用私钥和公钥密钥对的证书（也称为 PKCS 证书）。 Microsoft Intune 包括内置的设置来使用 PKCS 证书对组织资源进行访问和身份验证。 使用 Intune 中的设备配置配置文件将这些设置推送（或部署）到设备。

本文列出了使用 PKCS 证书的要求，介绍如何导出 PKCS 证书，以及如何将证书添加到 Intune 设备配置文件。

## <a name="requirements"></a>要求

要在 Intune 中使用 PKCS 证书，必须具有以下基础结构：

- **Active Directory 域**：此部分中列出的所有服务器都必须加入 Active Directory 域。

  若要深入了解如何安装和配置 AD DS，请参阅 [AD DS 设计和规划](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning)。

- **证书颁发机构** (CA)：企业证书颁发机构 (CA)

  若要深入了解如何安装和配置 Active Directory 证书服务 (AD CS)，请参阅 [Active Directory 证书服务分步指南](https://technet.microsoft.com/library/cc772393)。

  > [!WARNING]
  > Intune 要求在企业证书颁发机构 (CA) 而非独立 CA 中运行 AD CS。

- **客户端**：连接到企业 CA

- **根证书**：从企业 CA 导出的根证书的副本

- **Microsoft Intune 证书连接器**：使用 Azure 门户下载“证书连接器”安装程序 (NDESConnectorSetup.exe)。 

  连接器处理用于身份验证或 S/MIME 电子邮件签名的 PKCS 证书请求。

  NDES 证书连接器还支持美国联邦信息处理标准 (FIPS) 模式。 FIPS 不是必需的，但启用 FIPS 时可颁发和吊销证书。

- **Microsoft Intune 的 PFX 证书连接器**：如果计划使用 S/MIME 电子邮件加密，请使用 Azure 门户下载“Microsoft Intune 的 PFX 证书连接器”安装程序 (PfxCertificateConnectorBootstrapper.exe)。 该连接器处理导入 Intune 中的 PFX 文件的请求，以便为特定用户进行 S/MIME 电子邮件加密。

- **Windows Server**：托管以下内容：

  - 用于身份验证和 S/MIME 电子邮件签名方案的 Microsoft Intune 证书连接器 (NDESConnectorSetup.exe)
  - 用于 S/MIME 电子邮件加密方案的 Microsoft Intune 的 PFX 证书连接器 (PfxCertificateConnectorBootstrapper.exe)。

  可在同一服务器上运行这两种连接器（Microsoft Intune 证书连接器和 Microsoft Intune 的 PFX 证书连接器）。

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>从企业 CA 中导出根证书

要验证 VPN、WiFi 或其他资源，每台设备均需具备根证书或中间 CA 证书。 以下步骤介绍如何从企业 CA 中获取所需的证书。

1. 使用具有管理权限的帐户登录到企业 CA。
2. 以管理员身份打开命令提示符。
3. 将根 CA 证书 (.cer) 导出到稍后可访问的位置。
4. 向导完成后，关闭向导前，单击“启动证书连接器 UI” 。

   `certutil -ca.cert certnew.cer`

   有关详细信息，请参阅[用于管理证书的 Certutil 任务](https://technet.microsoft.com/library/cc772898.aspx#BKMK_ret_sign)。

## <a name="configure-certificate-templates-on-the-ca"></a>在 CA 上配置证书模板

1. 使用具有管理权限的帐户登录到企业 CA。
2. 打开“证书颁发机构”控制台，右键单击“证书模板”，然后选择“管理”。
3. 找到“用户”证书模板，右键单击该模板，然后选择“复制模板”。 随即打开“新模板的属性”。

    > [!NOTE]
    > 对于 S/MIME 电子邮件签名和加密方案，许多管理员使用单独的证书进行签名和加密。 如果使用 Microsoft Active Directory 证书服务，则针对 S/MIME 电子邮件签名证书可使用“仅 Exchange 签名”模板，针对 S/MIME 加密证书可使用“Exchange 用户”模板。  如果使用第三方证书颁发机构，建议查看其指南，设置签名和加密模板。

4. 在“兼容性”选项卡上：

    - 将“证书颁发机构”设置为“Windows Server 2008 R2”
    - 将“证书接收人”设置为“Windows 7 / Server 2008 R2”

5. 在“通用”选项卡上，将“模板显示名称”设置为对你有意义的名称。

    > [!WARNING]
    > 默认情况下，“模板名称”与“模板显示名称”相同，不包含空格。 请记下模板名称，供以后使用。

6. 在“请求处理”中，选择“允许导出私钥”。
7. 在“加密”处，确认将“最小密钥大小”设置为 2048。
8. 在“使用者名称”处，选择“在请求中提供”。
9. 在“扩展”处，确认在“应用程序策略”下显示有加密文件系统、安全电子邮件和客户端身份验证。

    > [!IMPORTANT]
    > 对于 iOS 证书模板，转到“扩展”选项卡，更新“密钥用法”，并确保未选择“数字签名为原件的证明”。

10. 在“安全”选项中，为安装 Microsoft Intune 证书连接器的服务器添加计算机帐户。 允许该帐户具有读取和注册权限。
11. 选择“应用” > “确认”以保存证书模板。 关闭“证书模板控制台” 。
12. 在“证书颁发机构”控制台中，右键单击“证书模板” > “新建” > “要颁发的证书模板”。 选择在先前步骤中创建的模板。 选择“确定”。
13. 为了让服务器管理已注册设备和用户的证书，请使用以下步骤：

    1. 右键单击“证书颁发机构”，选择“属性”。
    2. 在“安全”选项卡上，添加运行连接器（Microsoft Intune 证书连接器和 Microsoft Intune 的 PFX 证书连接器）的服务器的计算机帐户。 
    3. 向计算机帐户授予“发布和管理证书”以及“请求证书”允许权限。

14. 注销企业 CA。

## <a name="download-install-and-configure-the-certificate-connectors"></a>下载、安装和配置证书连接器

### <a name="microsoft-intune-certificate-connector"></a>Microsoft Intune 证书连接器

> [!IMPORTANT] 
> Microsoft Intune 证书连接器必须安装在单独的 Windows Server 上。 不能安装在证书颁发机构 (CA) 上。

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”> 筛选“Intune”> 选择“Intune”。
2. 选择“设备配置” > “证书颁发机构” > “添加”。
3. 下载并保存连接器文件。 将该文件保存到可从要安装连接器的服务器访问的位置。

    ![ConnectorDownload][ConnectorDownload]

4. 下载完成后，登录服务器。 然后：

    1. 确保已安装 .NET 4.5 Framework 或更高版本，因为它是 NDES 证书连接器的必需项。 Windows Server 2012 R2 和更高版本中自动包含 .NET 4.5 Framework。
    2. 运行安装程序 (NDESConnectorSetup.exe) 并接受默认位置。 连接器将安装到 `\Program Files\Microsoft Intune\NDESConnectorUI`。 在安装程序选项中，选择“PFX 分发”。 继续并完成安装。
    3. 默认情况下，连接器服务在本地系统帐户下运行。 如果需要通过代理访问 Internet，请确认本地服务帐户可以访问服务器上的代理设置。

5. NDES 连接器将打开“注册”选项卡。要启用到 Intune 的连接，请“登录”并输入具有全局管理权限的帐户。
6. 在“高级”选项卡上，建议让“使用此计算机的系统帐户(默认)”保持选中状态。
7. 应用 > 关闭
8. 返回到 Azure 门户（通过选择“Intune” > “设备配置” > “证书颁发机构”）。 片刻之后，将显示绿色复选标记，且“连接状态”显示“可用”。 连接器服务器现可与 Intune 通信。
9. 如果网络环境中有 Web 代理，则可能需要其他配置才能使连接器正常运行。 有关详细信息，请参阅 Azure Active Directory 文档中的[使用现有本地代理服务器](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers)。

> [!NOTE]
> Microsoft Intune 证书连接器中包含 TLS 1.2 支持。 因此，如果已安装 Microsoft Intune 证书连接器的服务器支持 TLS 1.2，则使用 TLS 1.2。 如果服务器不支持 TLS 1.2，则使用 TLS 1.1。 目前，TLS 1.1 用于设备和服务器之间的身份验证。

### <a name="pfx-certificate-connector-for-microsoft-intune"></a>Microsoft Intune 的 PFX 证书连接器

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
2. 选择“设备配置” > “证书颁发机构” > “添加”
3. 下载并保存 Microsoft Intune 的 PFX 证书连接器。 将该文件保存到可从要安装连接器的服务器访问的位置。
4. 下载完成后，登录服务器。 然后：

    1. 确保已安装 .NET 4.6 Framework 或更高版本，因为它是 Microsoft Intune 的 PFX 证书连接器的必需项。 如果未安装 .NET 4.6 Framework，安装程序会自动安装它。
    2. 运行安装程序 (PfxCertificateConnectorBootstrapper.exe)并接受默认位置。 连接器将安装到 `Program Files\Microsoft Intune\PFXCertificateConnector`。
    3. 连接器服务在本地系统帐户下运行。 如果需要通过代理进行 Internet 访问，请确认本地服务帐户可以访问服务器上的代理设置。

5. 安装后，Microsoft Intune 的 PFX 证书连接器将打开“注册”选项卡。 要启用到 Intune 的连接，请“登录”并输入具有 Azure 全局管理员或 Intune 管理员权限的帐户。
6. 关闭窗口。
7. 返回到 Azure 门户（通过选择“Intune” > “设备配置” > “证书颁发机构”）。 片刻之后，将显示绿色复选标记，且“连接状态”显示“可用”。 连接器服务器现可与 Intune 通信。

## <a name="create-a-trusted-certificate-profile"></a>创建受信任的证书配置文件

1. 在 [Azure 门户](https://portal.azure.com)，转到“Intune” > “设备配置” > “配置文件” > “创建配置文件”。

   ![NavigateIntune][NavigateIntune]

2. 输入以下属性：

    - 配置文件的名称
    - （可选）设置描述
    - 将配置文件部署到的平台
    - 将配置文件类型设置为“受信任的证书”

3. 转到“设置”并输入之前导出的 .cer 文件根 CA 证书。

   > [!NOTE]
   > 能否为证书选择“目标存储区”取决于步骤三中所选的平台。

   ![ProfileSettings][ProfileSettings]

4. 选择“确定” > “创建”以保存配置文件。
5. 若要将新配置文件分配给一个或多个设备，请参阅[分配 Microsoft Intune 设备配置文件](device-profile-assign.md)。

## <a name="create-a-pkcs-certificate-profile"></a>创建 PKCS 证书配置文件

1. 在 [Azure 门户](https://portal.azure.com)，转到“Intune” > “设备配置” > “配置文件” > “创建配置文件”。
2. 输入以下属性：

    - 配置文件的名称
    - （可选）设置描述
    - 将配置文件部署到的平台
    - 将“配置文件类型”设置为“PKCS 证书”

3. 转到“设置”，输入以下属性：

    - **续订阈值 (%)**：建议设为 20%。
    - **证书有效期**：如果没有更改证书模板，则此选项可能设置为一年。
    - **密钥存储提供程序 (KSP)**：对于 Windows，请选择在设备上存储密钥的位置。
    - **证书颁发机构**：显示企业 CA 的内部完全限定的域名 (FQDN)。
    - **证书颁发机构名称**：列出企业 CA 的名称，例如“Contoso 证书颁发机构”。
    - **证书模板名称**：之前创建的模板名称。 请记住，默认情况下，“模板名称”与“模板显示名称”相同，不包含空格。
    - **使用者名称格式**：除非另有要求，否则请将此选项设置为“公用名”。
    - **使用者备用名称**：除非另有要求，否则将此选项设置为“用户主体名称 (UPN)”。

4. 选择“确定” > “创建”以保存配置文件。
5. 若要将新配置文件分配给一个或多个设备，请参阅[分配 Microsoft Intune 设备配置文件](device-profile-assign.md)。

## <a name="create-a-pkcs-imported-certificate-profile"></a>创建 PKCS 导入的证书配置文件

可以将以前颁发给特定用户的证书从任何 CA 导入到 Intune。 导入的证书安装在用户注册的每个设备上。 S/MIME 电子邮件加密是将现有 PFX 证书导入 Intune 的最常见方案。 用户可能拥有许多证书来加密电子邮件。 这些证书的私钥必须存在于用户的所有设备上，以便它们可以解密以前加密的电子邮件。

若要将证书导入 Intune，可使用 [GitHub 上提供的 PowerShell cmdlet](https://github.com/Microsoft/Intune-Resource-Access)。

将证书导入 Intune 后，创建“PKCS 导入的证书”配置文件，并将其分配给 Azure Active Directory 组。

1. 在 [Azure 门户](https://portal.azure.com)，转到“Intune” > “设备配置” > “配置文件” > “创建配置文件”。
2. 输入以下属性：

    - 配置文件的名称
    - （可选）设置描述
    - 将配置文件部署到的平台
    - 将“配置文件类型”设置为“PKCS 导入的证书”

3. 转到“设置”，输入以下属性：

    - **预期目的**：为此配置文件导入的证书的预期目的。 管理员可能已导入具有不同预期目的的证书（如身份验证、S/MIME 签名或 S/MIME 加密）。 证书配置文件中选择的预期目的将证书配置文件与正确的导入证书相匹配。
    - **证书有效期**：如果没有更改证书模板，则此选项可能设置为一年。
    - **密钥存储提供程序 (KSP)**：对于 Windows，请选择在设备上存储密钥的位置。

4. 选择“确定” > “创建”以保存配置文件。
5. 若要将新配置文件分配给一个或多个设备，请参阅[分配 Microsoft Intune 设备配置文件](device-profile-assign.md)。

## <a name="next-steps"></a>后续步骤

配置文件已创建，但它尚未起到任何作用。 下一步，[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

[使用 SCEP 证书](certificates-scep-configure.md)，或[从 Symantec PKI 管理器 Web 服务颁发 PKCS 证书](certificates-symantec-configure.md)。

[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "导航到 Azure 门户中的 Intune 并为受信任的证书创建新的配置文件"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "创建配置文件并上载受信任的证书"
[ConnectorDownload]: ./media/certificates-download-connector.png "从 Azure 门户下载证书连接器"  
