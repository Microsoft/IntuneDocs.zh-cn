---
title: "使用远程擦除来帮助保护数据"
description: "Intune 提供选择性擦除和完全擦除功能，以删除敏感公司数据和删除对许多公司资源的访问权限。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8519e411-3d48-44eb-9b41-3e4fd6a93112
ms.reviewer: lancecra
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9d03f3936d608b9d526724eccbbdadbe030b53b8
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="help-protect-your-data-with-full-or-selective-wipe-using-microsoft-intune"></a>使用 Microsoft Intune 的完全擦除或选择性擦除保护数据

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

可以从不再需要的、已重新调整用途的或已丢失的 Intune 托管设备中擦除应用和数据。 若要执行此操作，Intune 将提供选择性擦除和完全擦除功能。 对于在 Intune 中注册的私人所有设备，用户还可从 Intune 公司门户应用中发出远程设备擦除命令。

  > [!NOTE]
  > 本主题仅涉及擦除通过 Intune 移动设备管理功能管理的设备。 还可使用 [Azure 门户](https://portal.azure.com)[从应用中擦除公司数据](wipe-managed-company-app-data-with-microsoft-intune.md)。 还可以[停用使用 Intune 客户端软件管理的计算机](retire-a-windows-pc-with-microsoft-intune.md)。

## <a name="full-wipe"></a>完全擦除

“完全擦除”将设备还原为其出厂默认设置，同时删除所有公司和用户数据和设置。 设备从 Intune 删除。 完全擦除可用于将设备授予新用户前或在设备丢失或被盗的情况下，对设备进行重置。  **请谨慎选择完全擦除。无法恢复设备上的数据**。


> [!Warning]
> 如果对 RAM 小于 4 GB 的 Windows 10 RTM 设备（早于 Windows 10 版本 1511 的设备）进行了擦除，则可能会变得无法访问。 若要访问已无响应的 Windows 10 设备，可以通过 USB 驱动器启动设备。

### <a name="remotely-wipe-a-device-from-the-intune-administrator-console"></a>从 Intune 管理员控制台远程擦除设备

1.  选择要擦除的设备。 你可以按用户或设备进行查找。

    -   **按用户：**

        1.  在 [Intune 管理员控制台](https://manage.microsoft.com/)中，依次选择**组**&gt;**所有用户**。

        2.  选择要擦除其移动设备的用户的名称。 选择**查看属性**。

        3.  在用户的“属性”页，选择“设备”，然后选择要擦除的移动设备的名称。 若要选择多个设备，请按住 Ctrl 并单击相应设备。

    -   **按设备：**

        1.  在 [Intune 管理员控制台](https://manage.microsoft.com/)中，依次选择**组**&gt;**所有移动设备**。

         ![启动停用或擦除操作](../media/dev-sa-wipe.png)

        2.  选择“设备”，然后选择要擦除的移动设备的名称。 若要选择多个设备，请按住 Ctrl 并单击相应设备。

2.  选择**停用/擦除**。

3.  此时将出现一条确认消息，询问你是否要停用该设备。

    -   若要执行仅删除公司应用和数据的“选择性擦除”，请选择“是”。

    -   若要执行将擦除所有应用和数据并将设备返回到出厂默认设置的“完全擦除”，请选择“在停用之前擦除设备”。 此操作适用于除 Windows 8.1 外的所有平台。 “无法恢复通过完全擦除删除的数据”。

如果设备已打开并连接，擦除命令会在 15 分钟内跨所有设备类型进行传播。

#### <a name="to-delete-devices-in-the-azure-active-directory-portal"></a>在 Azure Active Directory 门户中删除设备

1.  浏览到 [http://aka.ms/accessaad](http://aka.ms/accessaad) 或从 [https://portal.office.com](https://portal.office.com) 选择**管理**&gt; **Azure AD**。

2.  单击页面左侧的链接，使用组织 ID 登录。

3.  创建 Azure 订阅（如果没有）。 如果有付费帐户，应该不会要求提供信用卡或付款（请选择**注册免费的 Azure Active Directory**订阅链接）。

4.  选择“Active Directory”，然后选择你的组织。

5.  选择“用户”  选项卡。

6.  选择要删除其设备的用户。

7.  选择**设备**。

8.  根据需要删除设备，例如那些不再使用的设备或者定义不准确的设备。


## <a name="selective-wipe"></a>“选择性擦除”

**选择性擦除**将删除公司数据，包括设备中的移动应用管理 (MAM) 数据(适用的)、设置和电子邮件配置文件。 选择性擦除会将用户的个人数据保留在设备上。 设备从 Intune 删除。 下表描述了将删除什么数据，以及在选择性擦除之后对设备上保留的数据的影响。 （这些表按平台进行组织。）

**iOS**

|数据类型|iOS|
|-------------|-------|
|Intune 安装的公司应用和关联数据|卸载应用。 删除公司应用数据。<br /><br />来自使用移动应用程序管理的 Microsoft 应用程序的应用程序数据被删除。 应用程序不会删除。|
|设置|不再强制实施通过 Intune 策略设置的配置，用户可以更改设置。|
|Wi-Fi 和 VPN 配置文件设置|删除。|
|证书配置文件设置|已删除并吊销证书。|
|管理代理|删除管理配置文件。|
|Email|已删除通过 Intune 设置的电子邮件配置文件并删除设备上缓存的电子邮件。 如果在本地托管 Microsoft Exchange，则不会删除电子邮件配置文件和缓存的电子邮件。|
|Outlook|已删除适用于 iOS 的 Microsoft Outlook 应用接收到的电子邮件。</br>例外：如果在本地托管 Exchange，则不会删除电子邮件。|
|Azure Active Directory (AAD) 脱离|已删除 AAD 记录。|
|联系人 | 将删除从应用直接同步到本机通讯簿的联系人。  无法擦除从本机通讯簿同步到另一个外部源中的任何联系人。 <br /> <br />目前仅支持 Outlook 应用。

**Android**

|数据类型|Android|Android Samsung KNOX 标准版|
|-------------|-----------|------------------------|
|Web 链接|删除。|删除。|
|非托管的 Google Play 应用|保留已安装的应用和数据。|保留已安装的应用和数据。|
|非托管的业务线应用|保留已安装的应用和数据。|已卸载应用并由此删除了应用的本地数据。 未删除应用外的数据（例如 SD 卡上的数据）。|
|托管的 Google Play 应用|删除应用数据。 不删除应用。 应用（例如 SD 卡）外由 MAM 加密保护的数据仍然进行加密处理且不可用，但不删除。|删除应用数据。 不删除应用。 应用（例如 SD 卡）外由 MAM 加密保护的数据仍然进行加密处理，但不删除。|
|托管的业务线应用|删除应用数据。 不删除应用。 应用（例如 SD 卡）外由 MAM 加密保护的数据仍然进行加密处理且不可用，但不删除。|删除应用数据。 不删除应用。 应用（例如 SD 卡）外由 MAM 加密保护的数据仍然进行加密处理且不可用，但不删除。|
|设置|不再强制实施通过 Intune 策略设置的配置，用户可以更改设置。|不再强制实施通过 Intune 策略设置的配置，用户可以更改设置。|
|Wi-Fi 和 VPN 配置文件设置|删除。|删除。|
|证书配置文件设置|已吊销证书，但未删除。|已删除并吊销证书。|
|管理代理|撤销设备管理员权限。|撤销设备管理员权限。|
|Email|N/A。 查看 Outlook 项。|已删除通过 Intune 设置的电子邮件配置文件并删除设备上缓存的电子邮件。|
|Outlook|仅当 Outlook 由 MAM 策略保护时，才会删除 Android 版 Microsoft Outlook 应用接收的电子邮件。 否则取消注册时不会擦除 Outlook。</br>例外：如果在本地托管 Exchange，则不会删除电子邮件。|仅当 Outlook 由 MAM 策略保护时，才会删除 Android 版 Microsoft Outlook 应用接收的电子邮件。 否则取消注册时不会擦除 Outlook。</br>例外：如果在本地托管 Exchange，则不会删除电子邮件。|
|Azure Active Directory (AAD) 脱离|已删除 AAD 记录。|已删除 AAD 记录。|
|联系人 | 将删除从应用直接同步到本机通讯簿的联系人。  无法擦除从本机通讯簿同步到另一个外部源中的任何联系人。 <br /> <br />目前仅支持 Outlook 应用。|将删除从应用直接同步到本机通讯簿的联系人。  无法擦除从本机通讯簿同步到另一个外部源中的任何联系人。 <br /> <br />目前仅支持 Outlook 应用。

**Android for Work**

在 Android for Work 设备上执行选择性擦除将删除该设备上工作配置文件中的所有数据、应用和设置。 这将从 Intune 管理中停用设备。 Android for Work 不支持完全擦除。

**Windows**

|数据类型|Windows 8.1 (MDM) 和 Windows RT 8.1|Windows RT|Windows Phone 8 和 Windows Phone 8.1|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Intune 安装的公司应用和关联数据|通过 EFS 保护的文件的密钥将被吊销，用户将无法打开文件。|不会删除公司应用。|卸载最初通过公司门户安装的应用。 删除公司应用数据。|将卸载应用并删除旁加载密钥。|
|设置|不再强制实施通过 Intune 策略设置的配置，用户可以更改设置。|不再强制实施通过 Intune 策略设置的配置，用户可以更改设置。|不再强制实施通过 Intune 策略设置的配置，用户可以更改设置。|不再强制实施通过 Intune 策略设置的配置，用户可以更改设置。|
|Wi-Fi 和 VPN 配置文件设置|删除。|删除。|不支持。|删除。|
|证书配置文件设置|已删除并吊销证书。|已删除并吊销证书。|不支持。|已删除并吊销证书。|
|Email|删除启用了 EFS 的电子邮件，包括 Windows 电子邮件的邮件应用以及附件。|不支持。|已删除通过 Intune 设置的电子邮件配置文件并删除设备上缓存的电子邮件。|删除启用了 EFS 的电子邮件，包括 Windows 电子邮件的邮件应用以及附件。 删除由 Intune 预配的邮件帐户。</br>**例外**：如果在本地托管 Microsoft Exchange，则不会删除电子邮件帐户。|
|Azure Active Directory (AAD) 脱离|否。|否。|已删除 AAD 记录。|不适用。 Windows 10 不支持对已加入 Azure Active Directory 的设备使用选择性擦除。|

## <a name="wipe-encryption-file-system-efs-enabled-content"></a>擦除启用了加密文件系统 (EFS) 的内容
Windows 8.1 和 Windows RT 8.1 支持选择性擦除 EFS 加密内容。 以下几点适用于启用 EFS 的内容的选择性擦除：

-   仅选择性擦除使用同一 Internet 域作为 Intune 帐户通过 EFS 保护的应用和数据。 有关详细信息，请参阅[设备数据管理的 Windows 选择性擦除](http://technet.microsoft.com/library/dn486874.aspx)。

-   如果对与 EFS 关联的域进行了任何更改，则更改可能要花费长达 48 小时，之后才能对使用新域的应用和数据进行选择性擦除。

-   将擦除向 Intune 注册的每个域。

EFS 选择性擦除当前支持下列数据和应用：

-   Windows 相关邮件应用程序

-   工作文件夹

-   使用 EFS 加密的文件和文件夹。 有关详细信息，请参阅[加密文件系统的最佳方案](http://support.microsoft.com/kb/223316)。

-   如果你的组织维护其在 Active Directory 中的标识，它必须使用目录同步工具 (DirSync) 同步信息到 EFS 选择性擦除的 AAD 才能正常工作。  有关目录同步的详细信息，请参阅 Azure Active Directory 文档中的[目录同步方案](http://technet.microsoft.com/library/dn441212.aspx)。

## <a name="monitor-retire-wipe-and-delete-actions"></a>监视器停用、擦除和删除操作
获取已停用、擦除或删除的设备的报告：

1.  在 [Intune 管理员控制台](https://manage.microsoft.com/)中，依次选择**报表**&gt;**设备历史记录报表**。

2.  为报表提供开始和结束日期，然后选择“查看报表”。

此报表还会显示执行该操作的人员。

### <a name="see-also"></a>另请参阅
[停用设备](retire-devices-from-microsoft-intune-management.md)

[Windows Selective Wipe for Device Data Management](http://technet.microsoft.com/library/dn486874.aspx)（设备数据管理的 Windows 选择性擦除）
