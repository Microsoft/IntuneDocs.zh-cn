---
title: 在 Microsoft Intune 中使用导入的 PFX 证书 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中使用导入的公钥加密标准 (PKCS) 证书，包括导入证书、配置证书模板、安装 Intune 导入的 PFX 证书连接器，以及创建导入的 PKCS 证书配置文件。
keywords: ''
author: ralms
ms.author: brenduns
manager: dougeby
ms.date: 09/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f68ee794ce1fce2fbdbae8898c412309906b3f5c
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2019
ms.locfileid: "71167072"
---
# <a name="configure-and-use-imported-pkcs-certificates-with-intune"></a>在 Intune 中配置和使用导入的 PKCS 证书

Microsoft Intune 支持使用导入的公钥对 (PKCS) 证书，这些证书通常用于带有电子邮件配置文件的 S/MIME 加密。 Intune 中的某些电子邮件配置文件支持启用 S/MIME 的选项，你可以在其中定义 S/MIME 签名证书和 S/MIME 加密证书。

S/MIME 加密很有挑战性，因为电子邮件是使用特定证书进行加密的。 你必须拥有对你阅读电子邮件的设备上的电子邮件加密的证书私钥，才可以对电子邮件进行解密。 加密证书会定期续订，这意味着你可能需要在所有设备上拥有加密历史记录，才能确保能够阅读较早的电子邮件。  由于需要跨设备使用相同的证书，因此无法使用 [SCEP](certificates-scep-configure.md) 或 [PKCS](certficates-pfx-configure.md) 证书配置文件来实现此目的，因为这些证书传送机制针对每个设备提供独特的证书。 

有关将 S/MIME 与 Intune 配合使用的详细信息，请参阅[使用 S/MIME 对电子邮件进行加密](certificates-s-mime-encryption-sign.md)。

## <a name="requirements"></a>要求

要在 Intune 中使用导入的 PKCS 证书，必须具有以下基础结构：

- **Microsoft Intune 的 PFX 证书连接器**：  
  每个 Intune 租户都支持此连接器的一个实例。 可以将此连接器的实例与 Microsoft Intune 证书连接器的实例安装在同一服务器上。

  该连接器处理导入 Intune 中的 PFX 文件的请求，以便为特定用户进行 S/MIME 电子邮件加密。  

  新版本可用时，此连接器可自动更新。 要使用更新功能，必须确保防火墙已打开，以便连接器从端口 443 访问 autoupdate.msappproxy.net   。  

  有关连接器访问的所有网络终结点的详细信息，请参阅 [Intune 网络配置要求和带宽](network-bandwidth-use.md)。


- **Windows Server**：  
  你可以使用 Windows Server 托管 Microsoft Intune 的 PFX 证书连接器。  该连接器用于处理导入到 Intune 的证书的请求。

  Intune 支持在 Microsoft Intune 的 PFX 证书连接器所在的服务器上安装 Microsoft Intune 证书连接器   。

  要支持该连接器，服务器必须运行 .NET 4.6 Framework 或更高版本。 如果开始安装连接器时尚未安装 .NET 4.6 Framework，连接器安装过程会自动安装它。

- **Visual Studio 2015 或更高版本**（可选）：可以使用 Visual Studio 生成带有 cmdlet 的帮助程序 PowerShell 模块，以便将 PFX 证书导入 Microsoft Intune。 要获取帮助程序 PowerShell cmdlet，请参阅 [GitHub 中的 PFXImport PowerShell Project](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell)。

## <a name="how-it-works"></a>工作原理

当使用 Intune 将导入的 PFX 证书  部署到用户时，除了设备外，还有两个组件在运行： 

- **Intune 服务**：以加密状态存储 PFX 证书，并处理将证书部署到用户设备的操作。  在使用硬件安全模块 (HSM) 或 Windows 加密系统上传证书之前，对保护证书私钥的密码进行了加密，以确保 Intune 在任何时候都无法访问该私钥。
- **Microsoft Intune 的 PFX 证书连接器**：当设备请求导入 Intune 的 PFX 证书时，加密的密码、证书和设备的公钥将发送到连接器。  连接器使用本地私钥对密码进行解密，然后在将证书发送回 Intune 之前，使用设备密钥重新对密码（以及使用 iOS 时的所有 plist 配置文件）加密。  然后，Intune 将证书传递到设备，设备能够用设备的私钥对证书解密并进行安装。

## <a name="download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune"></a>下载、安装和配置 Microsoft Intune 的 PFX 证书连接器

1. 在 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 门户中，选择“设备配置”   > “认证连接器”   > “添加” 

   ![下载 Microsoft Intune 的 PFX 证书连接器](media/certificates-imported-pfx-configure/download-imported-pfxconnector.png)

2. 按照指导将 Microsoft Intune 的 PFX 证书连接器  下载到可从要安装连接器的服务器访问的位置。
3. 下载完成后，登录服务器并运行安装程序 (PfxCertificateConnectorBootstrapper.exe)。  
   - 如果你接受默认安装位置，连接器将安装到 `Program Files\Microsoft Intune\PFXCertificateConnector`。
   - 连接器服务在本地系统帐户下运行。 如果需要通过代理进行 Internet 访问，请确认本地服务帐户可以访问服务器上的代理设置。

4. 安装后，Microsoft Intune 的 PFX 证书连接器将打开“注册”选项卡  。 要启用到 Intune 的连接，请“登录”并输入具有 Azure 全局管理员或 Intune 管理员权限的帐户  。

   > [!WARNING]
   > 默认情况下，在 Windows Server 中，“IE 增强的安全配置”  设置为“启用”  导致登录 Office 365 出现问题。

5. 关闭窗口。
6. 在 Intune 门户中，返回到“设备配置”   > “认证连接器”  。 片刻之后，将显示绿色勾号且“连接状态”显示“可用”   。 连接器服务器现可与 Intune 通信。

## <a name="import-pfx-certificates-to-intune"></a>将 PFX 证书导入到 Intune

使用 [Microsoft Graph](https://docs.microsoft.com/graph) 将用户 PFX 证书导入到 Intune。 帮助程序 [GitHub 上的 PFXImport PowerShell Project](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell) 提供了用于轻松完成操作的 cmdlet。

如果希望通过使用 Graph 使用自己的自定义解决方案，请使用 [userPFXCertificate 资源类型](https://docs.microsoft.com/graph/api/resources/intune-raimportcerts-userpfxcertificate?view=graph-rest-beta)。

### <a name="build-pfximport-powershell-project-cmdlets"></a>生成“PFXImport PowerShell Project”cmdlet

要使用 PowerShell cmdlet，需使用 Visual Studio 自行生成项目。 此过程是直接的，虽然它可以在服务器上运行，但建议在工作站上运行。  

1. 转到 GitHub 上的 [Intune-Resource-Access](https://github.com/microsoft/Intune-Resource-Access) 存储库的根目录，然后使用 Git 将存储库下载或克隆到你的计算机。

   ![GitHub 下载按钮](media/certificates-imported-pfx-configure/github-download.png)

2. 转到 `.\Intune-Resource-Access-develop\src\PFXImportPowershell\` 并使用 Visual Studio 和 PFXImportPS.sln  文件打开项目。
3. 在顶部，从“调试”  更改为“发布”  。
4. 转到“生成”  ，选择“生成 PFXImportPS”  。 稍后 Visual Studio 左下部将显示“已成功生成”  消息。

   ![Visual Studio 生成选项](media/certificates-imported-pfx-configure/vs-build-release.png)

5. 生成过程在 `.\Intune-Resource-Access-develop\src\PFXImportPowershell\PFXImportPS\bin\Release` 处使用 PowerShell 模块创建一个新文件夹。

   在接下来的步骤中，你将使用此“发布”  。

### <a name="create-the-encryption-public-key"></a>创建加密公钥

将 PFX 证书及其私钥导入到 Intune。 使用本地存储的公钥对保护私钥的密码进行加密。 可以使用 Windows 加密、硬件安全模块或另一种加密方式生成并存储公钥/私钥对。  根据使用的加密类型，公钥/私钥对可以采用文件格式导出以进行备份。

PowerShell 模块提供了使用 Windows 加密创建密钥的方法。 你也可以使用其他工具创建密钥。  

#### <a name="to-create-the-encryption-key-using-windows-cryptography"></a>使用 Windows 加密创建加密密钥

1. 将 Visual Studio 创建的“发布”  文件夹复制到安装了 Microsoft Intune 的 PFX 证书连接器  的服务器。 此文件夹包含 PowerShell 模块。  
2. 在服务器上，以管理员身份打开 PowerShell  ，然后导航到包含 PowerShell 模块的“发布”  文件夹。
3. 要导入模块，需要运行 `Import-Module .\IntunePfxImport.psd1` 以导入模块。
4. 接下来，运行 `Add-IntuneKspKey "Microsoft Software Key Storage Provider" "PFXEncryptionKey"`

   > [!TIP]  
   > 当导入 PFX 证书时，必须再次选择你使用的提供程序。 你可以使用 **Microsoft 软件密钥存储提供程序**支持使用其他提供程序。 密钥名称也作为示例提供，你可以使用你选择的其他密钥名称。  

   如果打算从你的工作站导入证书，可以使用以下命令将此密钥导出到文件：`Export-IntunePublicKey -ProviderName "<ProviderName>" -KeyName "<KeyName>" -FilePath "<File path to write to>"`

   必须在承载 Microsoft Intune 的 PFX 证书连接器的服务器上导入私钥，以便可以成功处理导入的 PFX 证书。  

#### <a name="to-use-a-hardware-security-module-hsm"></a>使用硬件安全模块 (HSM)  

可以使用硬件安全模块 (HSM) 生成并存储公钥/私钥对。 有关详细信息，请参阅 HSM 提供商文档。

### <a name="import-pfx-certificates"></a>导入 PFX 证书 

以下过程使用 PowerShell cmdlet 作为示例来说明如何导入 PFX 证书。 你可以根据自己的需求选择不同的选项。

选项包括：  
- 预期目的（根据标记将证书分组在一起）：  
  - 未分配
  - smimeEncryption
  - smimeSigning


- 填充方案：  
  - pkcs1
  - oaepSha1
  - oaepSha256
  - oaepSha384
  - oaepSha512

选择与用于创建密钥的提供程序匹配的密钥存储提供程序。

#### <a name="to-import-the-pfx-certificate"></a>导入 PFX 证书  

1. 按照以下提供商文档，从任何证书颁发机构 (CA) 导出证书。  对于 Microsoft Active Directory 证书服务，可以使用[此示例脚本](https://gallery.technet.microsoft.com/Export-CMPfxCertificatesFro-d55f687b)。   
2. 在服务器上，以管理员身份打开 PowerShell  ，然后导航到包含 PowerShell 模块的“发布”  文件夹。
3. 要导入模块，请运行 `Import-Module .\IntunePfxImport.psd1`  
4. 要向 Intune Graph 进行身份验证，请运行 `$authResult = Get-IntuneAuthenticationToken -AdminUserName "<Admin-UPN>"`

   > [!NOTE]
   > 由于向 Graph 进行身份验证，因此你必须提供对 AppID 的权限。 如果是第一次使用此实用程序，则需要全局管理员  权限。 PowerShell cmdlet 使用 [PowerShell Intune 示例](https://github.com/microsoftgraph/powershell-intune-samples)中所用的相同 AppID。   
5. 通过运行 `$SecureFilePassword = ConvertTo-SecureString -String "<PFXPassword>" -AsPlainText -Force`，将每个要导入的 PFX 文件的密码转换为安全字符串。  
6. 要创建 UserPFXCertificate  对象，请运行 `$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "<FullPathPFXToCert>" $SecureFilePassword "<UserUPN>" "<ProviderName>" "<KeyName>" "<IntendedPurpose>" "<PaddingScheme>"`

   例如：`$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "C:\temp\userA.pfx" $SecureFilePassword "userA@contoso.com" "Microsoft Software Key Storage Provider" "PFXEncryptionKey" "smimeEncryption" "pkcs1"`

   > [!NOTE]  
   > 当从安装了连接器的服务器之外的其他系统中导入证书时，必须使用包含密钥文件路径的以下命令：`$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "<FullPathPFXToCert>" $SecureFilePassword "<UserUPN>" "<ProviderName>" "<KeyName>" "<IntendedPurpose>" "<PaddingScheme>" "<File path to public key file>"`

7. 通过运行 `Import-IntuneUserPfxCertificate -AuthenticationResult $authResult -CertificateList $userPFXObject`，将 UserPFXCertificate  对象导入到 Intune

8. 要验证证书是否已导入，请运行 `Get-IntuneUserPfxCertificate -AuthenticationResult $authResult -UsertList "<UserUPN>"`

有关其他可用命令的详细信息，请参阅 [GitHub 上 的 PFXImport PowerShell Project ](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell) 中的自述文件。

## <a name="create-a-pkcs-imported-certificate-profile"></a>创建 PKCS 导入的证书配置文件

将证书导入 Intune 后，创建“PKCS 导入的证书”配置文件，并将其分配给 Azure Active Directory 组  。

1. 在 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 门户中，转到“设备配置”   > “配置文件”   > “创建配置文件”  。
2. 输入以下属性：

   - 配置文件的名称 
   - （可选）设置描述
   - 将配置文件部署到的平台 
   - 将“配置文件类型”设置为“PKCS 导入的证书”  

3. 转到“设置”  ，输入以下属性：

   - **预期目的**：指定为此配置文件导入的证书的预期目的。 管理员可以导入具有不同预期目的（如身份验证、S/MIME 签名或 S/MIME 加密）的证书。 证书配置文件中选择的预期目的将证书配置文件与正确的导入证书相匹配。 “预期目的”是一种将导入的证书分组在一起的标记，并不保证使用该标记导入的证书能满足预期目的。  
   - **证书有效期**：除非证书模板中的有效期发生了更改，否则此选项默认为一年。  
   - **密钥存储提供程序 (KSP)** ：对于 Windows，请选择在设备上存储密钥的位置。  

4. 选择“确定”   > “创建”  以保存配置文件。
5. 若要将新配置文件分配给一个或多个设备，请参阅[分配 Microsoft Intune 设备配置文件](device-profile-assign.md)。



