---
title: "使用 Intune 配置和管理 PKCS 证书"
titleSuffix: Intune on Azure
description: "使用 Intune 创建和分配 PKCS 证书。"
keywords: 
author: MicrosoftGuyJFlo
ms.author: joflore
manager: angrobe
ms.date: 12/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a51d260718e0d0c3984966fab69e202b854c1847
ms.sourcegitcommit: b2467a653ffd36c2248a30b69cb88e3dc7cca2ed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2017
---
# <a name="configure-and-manage-pkcs-certificates-with-intune"></a>使用 Intune 配置和管理 PKCS 证书

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="requirements"></a>要求

若要在 Intune 中使用 PKCS 证书，必须具有以下基础结构：

* 配置了现有 Active Directory 域服务 (AD DS) 域。
 
  如果需要了解有关如何安装和配置 AD DS 的详细信息，请参阅文章 [AD DS 设计和规划](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning)。

* 配置了现有企业证书颁发机构 (CA)。

  如果需要了解有关如何安装和配置 Active Directory 证书服务 (AD CS) 的详细信息，请参阅文章 [Active Directory 证书服务分步指南](https://technet.microsoft.com/library/cc772393)。

  > [!WARNING]
  > Intune 要求在企业证书颁发机构 (CA) 而非独立 CA 中运行 AD CS。

* 已连接到企业 CA 的客户端。
* 从企业 CA 导出的根证书的副本。
* 从 Intune 门户下载了 Microsoft Intune 证书连接器 (NDESConnectorSetup.exe)。
* 可用于托管 Microsoft Intune 证书连接器 (NDESConnectorSetup.exe) 的 Windows Server。

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>从企业 CA 中导出根证书

需要每个设备上有根证书或中间 CA 证书，以对 VPN、WiFi 和其他资源进行身份验证。 以下步骤介绍如何从企业 CA 中获取所需的证书。

1. 使用具有管理权限的帐户登录到企业 CA。
2. 以管理员身份打开命令提示符。
3. 将根 CA 证书导出到可以稍后对其进行访问的位置。

   例如：

4.  向导完成后，关闭向导前，单击“启动证书连接器 UI” 。

   `certutil -ca.cert certnew.cer`

   有关详细信息，请参阅[用于管理证书的 Certutil 任务](https://technet.microsoft.com/library/cc772898.aspx#BKMK_ret_sign)。

## <a name="configure-certificate-templates-on-the-certification-authority"></a>配置证书颁发机构上的证书模板

1. 使用具有管理权限的帐户登录到企业 CA。
2. 打开“证书颁发机构”控制台。
3. 右键单击“证书模板”，然后选择“管理”。
4. 找到“用户”证书模板，右键单击该模板，然后选择“复制模板”。 随即出现“新模板属性”窗口。
5. 在“兼容性”选项卡上
   * 将“证书颁发机构”设置为“Windows Server 2008 R2”
   * 将“证书接收人”设置为“Windows 7 / Server 2008 R2”
6. 在“常规”选项卡上  ：
   * 将“模板显示名称”设置为对你有意义的名称。

   > [!WARNING]
   > 默认情况下，“模板名称”与“模板显示名称”相同，不包含空格。 请记下模板名称，供以后使用。

7. 在“请求处理”选项卡上，选择“允许导出私钥”框。
8. 在“加密”选项卡上，确认将“最小密钥大小”设置为 2048。
9. 在“使用者名称”选项卡上，选中单选按钮“在请求中提供”。
10. 在“扩展”选项卡上，确认在“应用程序策略”下看到加密文件系统、安全电子邮件和客户端身份验证。
    
      > [!IMPORTANT]
      > 对于 iOS 和 macOS 证书模板，在“扩展”选项卡上，编辑“密钥用法”，并确保未选择“数字签名为原件的证明”。

11. 在“安全”选项卡上，为安装 Microsoft Intune 证书连接器所在的服务器添加计算机帐户。
    * 允许该帐户具有读取和注册权限。
12. 单击“应用”，然后单击“确认”以保存证书模板。
13. 关闭“证书模板控制台” 。
14. 在“证书颁发机构”控制台中，右键单击“证书模板”、“新建”、“要颁发的证书模板”。
    * 选择在前面的步骤中创建的模板，然后单击“确定”。
15. 为了让服务器代表已注册 Intune 的设备和用户管理证书，请执行以下步骤：

    a. 右键单击“证书颁发机构”，选择“属性”。

    b. 在“安全”选项卡上，为运行 Microsoft Intune 证书连接器所在的服务器添加计算机帐户。
      * 向计算机帐户授予“发布和管理证书”以及“请求证书”允许权限。
16. 注销企业 CA。

## <a name="download-install-and-configure-the-microsoft-intune-certificate-connector"></a>下载、安装和配置 Microsoft Intune 证书连接器

![ConnectorDownload][ConnectorDownload]

1. 在 Azure 门户中，选择“更多服务” > “监视 + 管理” > “Intune”。
2. 在“Intune”边栏选项卡上，选择“设备配置”。 
3. 在“设备配置”边栏选项卡上，选择“证书颁发机构”。 
4. 单击“添加”，并选择“下载连接器文件”。 将下载的文件保存到可以从服务器上进行访问的位置，将在该服务器上安装该应用程序。 
5.  登录到将要安装 Microsoft Intune 证书连接器的服务器。
6.  运行安装程序并接受默认位置。 它将连接器安装到 C:\Program Files\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe。
    1. 在“安装程序选项”页上选择“PFX 分发”，然后单击“下一步”。
    2. 单击“安装”并等待安装完成。
    3. 在完成页上，选中标记为“启动 Intune 连接器”的框，然后单击“完成”。
7.  现在将出现 NDES 连接器窗口，显示“注册”选项卡。要启用对 Intune 的连接，请单击“登录”并提供具有管理权限的帐户。
8.  在“高级”选项卡上，可以保持单选按钮“使用此计算机的系统帐户（默认）”的选中状态。
9.  单击“应用”，然后单击“关闭”。
10. 现在将返回到 Azure 门户。 几分钟后，在“Intune” > “设备配置” > “证书颁发机构”中，应该能够在“连接状态”下看到绿色的复选标记和“活动”一词。 这一确认可以让你知道你的连接器服务器可以与 Intune 通信。


## <a name="create-a-device-configuration-profile"></a>创建设备配置配置文件

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 导航到“Intune”、“设备配置”、“配置文件”，然后单击“创建配置文件”。

   ![NavigateIntune][NavigateIntune]

3. 请填充以下信息：
   * 配置文件的名称
   * （可选）设置描述
   * 将配置文件部署到的平台
   * 将配置文件类型设置为“受信任的证书”
4. 导航到“设置”并提供以前导出的 .cer 文件根 CA 证书。

   > [!NOTE]
   > 你可能有或没有为证书选择“目标存储区”的选项，具体取决于在步骤 3 中所选的平台。

   ![ProfileSettings][ProfileSettings]

5. 单击“确认”，然后单击“创建”以保存你的配置文件。
6. 若要将新的配置文件分配给一个或多个设备，请参阅[如何分配 Microsoft Intune 设备配置文件](device-profile-assign.md)。

## <a name="create-a-pkcs-certificate-profile"></a>创建 PKCS 证书配置文件

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 导航到“Intune”、“设备配置”、“配置文件”，然后单击“创建配置文件”。
3. 请填充以下信息：
   * 配置文件的名称
   * （可选）设置描述
   * 将配置文件部署到的平台
   * 将配置文件类型设置为“PKCS 证书”
4. 导航到“设置”并提供以下信息：
   * 续订阈值 (%) - 建议为 20%。
   * 证书有效期 - 如未更改证书模板，则此选项应设置为一年。
   * 证书颁发机构 - 此选项是企业 CA 的内部完全限定的域名 (FQDN)。
   * 证书颁发机构名称 - 此选项是企业 CA 的名称，可能与以前的项目不同。
   * 证书模板名称 - 此选项是前面创建的模板名称。 请记住，默认情况下，“模板名称”与“模板显示名称”相同，不包含空格。
   * 使用者名称格式 - 将此选项设置为公用名（除非另有要求）。
   * 使用者可选名称 - 将此选项设置为用户主体名称 (UPN)（除非另有要求）。
   * 扩展密钥用法 - 只要在上一部分“配置证书颁发机构上的证书模板”中使用了步骤 10 中的默认设置，就可以从选择框中添加以下预定义的值：
      * **任何用途**
      * **客户端身份验证**
      * **安全电子邮件**
   * **根证书** - （针对 Android 配置文件）此选项是上一部分[从企业 CA 导出根证书](#export-the-root-certificate-from-the-enterprise-ca)下的步骤 3 中导出的 .cer 文件。

5. 单击“确认”，然后单击“创建”以保存你的配置文件。
6. 若要将新的配置文件分配给一个或多个设备，请参阅文章[如何分配 Microsoft Intune 设备配置文件](device-profile-assign.md)。


[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "导航到 Azure 门户中的 Intune 并为受信任的证书创建新的配置文件"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "创建配置文件并上载受信任的证书"
[ConnectorDownload]: ./media/certificates-download-connector.png "从 Azure 门户下载证书连接器"  
