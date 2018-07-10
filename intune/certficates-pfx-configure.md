---
title: 在 Microsoft Intune 中使用 PKCS 证书 - Azure | Micrososft Docs
description: 向 Microsoft Intune 添加或创建公钥加密标准证书，所需步骤如下：导出根证书、配置证书模板、下载和安装 Microsoft Intune 证书连接器 (NDES)、创建设备配置文件，以及在 Azure 和证书颁发机构中创建 PKCS 证书配置文件。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3b3bfe76173eff76a3175952bef5c6e23ad5e429
ms.sourcegitcommit: afda8a0fc0f615e976b18ddddf81d56d7ae3566e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/20/2018
ms.locfileid: "36271535"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>在 Intune 中配置和使用 PKCS 证书

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

证书用于进行身份验证并保证用户安全访问公司资源（例如 VPN 或 WiFi 网络）。 本文介绍如何导出 PKCS 证书，然后将证书添加到 Intune 配置文件中。 

## <a name="requirements"></a>要求

要在 Intune 中使用 PKCS 证书，必须具有以下基础结构：

- **Active Directory 域**：此部分中列出的所有服务器都必须加入 Active Directory 域。

  若要深入了解如何安装和配置 AD DS，请参阅 [AD DS 设计和规划](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning)。

- **证书颁发机构** (CA)：企业证书颁发机构 (CA)

  若要深入了解如何安装和配置 Active Directory 证书服务 (AD CS)，请参阅 [Active Directory 证书服务分步指南](https://technet.microsoft.com/library/cc772393)。

  > [!WARNING]
  > Intune 要求在企业证书颁发机构 (CA) 而非独立 CA 中运行 AD CS。

- **客户端**：连接到企业 CA

- **根证书**：企业 CA 根证书的导出副本

- **Microsoft Intune 证书连接器**：使用 Azure 门户下载“证书连接器”安装程序 (NDESConnectorSetup.exe)。 

  NDES 证书连接器还支持美国联邦信息处理标准 (FIPS) 模式。 FIPS 不是必需的，但启用 FIPS 时可颁发和吊销证书。

- **Windows Server**：用于托管 Microsoft Intune 证书连接器 (NDESConnectorSetup.exe)

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>从企业 CA 中导出根证书

要验证 VPN、WiFi 和其他资源，每台设备均必须具备根证书或中间 CA 证书。 以下步骤介绍如何从企业 CA 中获取所需的证书。

1. 使用具有管理权限的帐户登录到企业 CA。
2. 以管理员身份打开命令提示符。
3. 将根 CA 证书 (.cer) 导出到稍后可访问的位置。

   例如：

4. 向导完成后，关闭向导前，单击“启动证书连接器 UI” 。

   `certutil -ca.cert certnew.cer`

   有关详细信息，请参阅[用于管理证书的 Certutil 任务](https://technet.microsoft.com/library/cc772898.aspx#BKMK_ret_sign)。

## <a name="configure-certificate-templates-on-the-certification-authority"></a>配置证书颁发机构上的证书模板

1. 使用具有管理权限的帐户登录到企业 CA。
2. 打开“证书颁发机构”控制台，右键单击“证书模板”，然后选择“管理”。
3. 找到“用户”证书模板，右键单击该模板，然后选择“复制模板”。 随即打开“新模板的属性”。
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
11. 选择“应用”，然后选择“确认”以保存证书模板。
12. 关闭“证书模板控制台” 。
13. 在“证书颁发机构”控制台中，右键单击“证书模板”、“新建”、“要颁发的证书模板”。 选择在先前步骤中创建的模板，然后选择“确定”。
14. 为了让服务器代表已注册 Intune 的设备和用户管理证书，请执行以下步骤：

    1. 右键单击“证书颁发机构”，选择“属性”。
    2. 在“安全”选项卡上，为运行 Microsoft Intune 证书连接器所在的服务器添加计算机帐户。 向计算机帐户授予“发布和管理证书”以及“请求证书”允许权限。

15. 注销企业 CA。

## <a name="download-install-and-configure-the-certificate-connector"></a>下载、安装和配置证书连接器

![ConnectorDownload][ConnectorDownload]

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 选择“设备配置”，然后选择“证书颁发机构”。
4. 选择“添加”和“下载连接器文件”。 将下载的文件保存到可以从服务器上进行访问的位置，将在该服务器上安装该应用程序。
5. 下载完成后，登录服务器。 然后：

    1. 确保已安装 .NET 4.5 Framework，因为它是 NDES 证书连接器的必需项。 Windows Server 2012 R2 和更高版本中自动包含 .NET 4.5 Framework。
    2. 运行安装程序 (NDESConnectorSetup.exe) 并接受默认位置。 连接器将安装到 `\Program Files\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe`。 在安装程序选项中，选择“PFX 分发”。 继续并完成安装。

6. NDES 连接器将打开“注册”选项卡。要启用到 Intune 的连接，请“登录”并输入具有全局管理权限的帐户。
7. 在“高级”选项卡上，让“使用此计算机的系统帐户(默认)”保持选中状态。
8. 单击“应用”，再单击“关闭”。
9. 返回到 Azure 门户（通过选择“Intune” > “设备配置” > “证书颁发机构”）。 片刻之后，将显示绿色勾号且“连接状态”显示“可用”。 连接器服务器现可与 Intune 通信。

> [!NOTE]
> NDES 证书连接器中包含 TLS 1.2 支持。 因此，如果已安装 NDES 证书连接器的服务器支持 TLS 1.2，则使用 TLS 1.2。 如果服务器不支持 TLS 1.2，则使用 TLS 1.1。 目前，TLS 1.1 用于设备和服务器之间的身份验证。

## <a name="create-a-device-configuration-profile"></a>创建设备配置配置文件

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 转到“Intune” > “设备配置” > “配置文件” > “创建配置文件”。

   ![NavigateIntune][NavigateIntune]

3. 输入以下属性：

  - 配置文件的名称
  - （可选）设置描述
  - 将配置文件部署到的平台
  - 将配置文件类型设置为“受信任的证书”

4. 转到“设置”并输入之前导出的 .cer 文件根 CA 证书。

   > [!NOTE]
   > 能否为证书选择“目标存储区”取决于步骤三中所选的平台。

   ![ProfileSettings][ProfileSettings]

5. 选择“确认”，然后选择“创建”以保存配置文件。
6. 若要将新配置文件分配给一个或多个设备，请参阅[分配 Microsoft Intune 设备配置文件](device-profile-assign.md)。

## <a name="create-a-pkcs-certificate-profile"></a>创建 PKCS 证书配置文件

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 转到“Intune” > “设备配置” > “配置文件” > “创建配置文件”。
3. 输入以下属性：

  - 配置文件的名称
  - （可选）设置描述
  - 将配置文件部署到的平台
  - 将配置文件类型设置为“PKCS 证书”

4. 转到“设置”，输入以下属性：

  - 续订阈值 (%) - 建议为 20%。
  - **证书有效期** - 如未更改证书模板，则此选项可能设置为一年。
  - **证书颁发机构** - 显示企业 CA 的内部完全限定的域名 (FQDN)。
  - **证书颁发机构名称** - 列出企业 CA 的名称（可能与之前的名称不同）。
  - **证书模板名称** - 之前创建的模板名称。 请记住，默认情况下，“模板名称”与“模板显示名称”相同，不包含空格。
  - 使用者名称格式 - 将此选项设置为公用名（除非另有要求）。
  - 使用者可选名称 - 将此选项设置为用户主体名称 (UPN)（除非另有要求）。
  - **扩展密钥用法** - 只要在本文中[配置证书颁发机构上的证书模板](#configure-certificate-templates-on-the-certification-authority)部分使用了步骤 10 中的默认设置，即可从选项中添加以下预定义值：
    - **任何用途**
    - **客户端身份验证**
    - **安全电子邮件**
  - **根证书** -（针对 Android 配置文件）列出在本文[从企业 CA 导出根证书](#export-the-root-certificate-from-the-enterprise-ca)部分的步骤 3 中导出的 .cer 文件。

5. 选择“确认”，然后选择“创建”以保存配置文件。
6. 若要将新配置文件分配给一个或多个设备，请参阅[分配 Microsoft Intune 设备配置文件](device-profile-assign.md)。

## <a name="next-steps"></a>后续步骤
[使用 SCEP 证书](certificates-scep-configure.md)，或[从 Symantec PKI 管理器 Web 服务颁发 PKCS 证书](certificates-symantec-configure.md)。

[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "导航到 Azure 门户中的 Intune 并为受信任的证书创建新的配置文件"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "创建配置文件并上载受信任的证书"
[ConnectorDownload]: ./media/certificates-download-connector.png "从 Azure 门户下载证书连接器"  
