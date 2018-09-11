---
title: iOS 应用保护策略设置
titlesuffix: Microsoft Intune
description: 本主题介绍适用于 iOS 设备的应用保护策略设置。
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 08/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0f8b08f2-504c-4b38-bea2-b8a4ef0526b8
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4eaf1cc4258873f325edf3f51c7fa725bd54db26
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2018
ms.locfileid: "43313810"
---
#  <a name="ios-app-protection-policy-settings"></a>iOS 应用保护策略设置
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

可在 Azure 门户的“添加策略” > “设置”边栏选项卡中为应用保护策略[配置](app-protection-policies.md)本主题所述的策略设置。

有两种类别的策略设置：数据重定位设置和访问设置。 在本主题中，术语***策略托管应用***指使用应用保护策略配置的应用。

##  <a name="data-relocation-settings"></a>数据重定位设置

| Setting | 如何使用 | 默认值 |
|------|------|------|
| **阻止 iTunes 和 iCloud 备份** | 选择“是”，阻止此应用将工作或学校的数据备份到 iTunes 和 iCloud。 选择“否”允许此应用程序将工作或学校的数据备份到 iTunes 和 iCloud。| 是 |
| **允许应用向其他应用传送数据** | 指定哪些应用可从此应用接收数据： <ul><li> **策略托管应用**：仅允许传输到其他策略托管应用。</li> <li>**所有应用**：允许传输到任何应用。 </li> <li>**无**：不允许将数据传输到任何应用，包括其他策略托管应用。</li></ul>如果将此设置设置为“策略托管应用”，则可以配置“筛选“打开方式/共享”对话框以便仅显示策略托管应用?”设置。 选择“是”：对于使用 iOS 上的文件/文档的应用，仅在 Apple 的“打开方式/共享”对话框中显示托管应用。 选择“否”：在 Apple 的“打开方式/共享”对话框中显示设备上可用于打开文件/文档的所有应用。 发送到非托管应用的托管数据仍然处于加密状态。 <br><br>**注意：** 若要配置“打开方式/共享”对话框的筛选，充当文件/文档源的应用和可打开此文件/文档的应用均需具有适用于 iOS 8.1.1 版本或更高版本的 Intune SDK。 默认值为“否”。 <br><br> 此外，如果将该设置设置为“策略托管应用”或“无”，则将阻止允许 Spotlight Search 在应用内搜索数据的 iOS 9 功能。 <p><p>此策略也会影响 Web 内容的行为。 如果此策略设置为“阻止”，则用户将无法打开任何浏览器（包括 Managed Browser）的 http 链接。 此外，如果此策略设置为“仅限托管的策略”，则只能在 Managed Browser 中打开 http 链接。 <p> 默认情况下，Intune 允许向一些豁免应用和服务传输数据。 此外，如果需要允许将数据传输到不支持 Intune APP 的应用，则可以创建自己的豁免项目。 有关详细信息，请参阅[数据传输豁免](#data-transfer-exemptions)。 | 所有应用 |
| **允许应用从其他应用接收数据** | 指定哪些应用可将数据传输到此应用： <ul><li>**策略托管应用**：仅允许从其他策略托管应用传输。</li><li>**所有应用**：允许从任何应用传输数据。</li><li>**无**：不允许从任何应用传输数据，包括其他策略托管应用。</li></ul> Intune 可能会允许从一些豁免应用和服务传输数据。 有关应用和服务的完整列表，请参阅[数据传输豁免](#data-transfer-exemptions)。 非注册 iOS 设备上已启用多标识 MAM 的 应用忽略此策略，并允许所有传入数据。 | 所有应用 |
| **阻止“另存为”** | 选择“是”，在此应用中禁用“另存为”选项。 如果你希望允许使用“另存为”，请选择“否”。 <p><br>**选择可保存公司数据的存储服务** <br>用户可以保存到所选的服务（OneDrive for Busines、SharePoint 和本地存储）中。 将阻止所有其他服务。</p> | 否 <br><br> 未选择任何项 |
| **限制剪切、复制和粘贴到其他应用程序** | 指定剪切、复制和粘贴操作何时可用于此应用。 选择： <ul><li>**阻止**：不允许在此应用和任何其他应用间进行剪切、复制和粘贴操作。</li><li>**策略托管应用**：允许在此应用和其他策略托管应用间进行剪切、复制和粘贴操作。</li><li>**带粘贴的策略托管应用**：允许在此应用和其他策略托管应用间进行剪切或复制。 允许将任何应用中的数据粘贴到此应用。</li><li>**任何应用**：不限制从此应用和对此应用进行剪切、复制和粘贴。 | 任何应用 |
|**限制显示在 Managed Browser 内的 Web 内容** | 选择“是”，强制在 Managed Browser 应用中打开应用中的 Web 链接。 <br><br> 对于未在 Intune 中注册的设备，策略托管应用中的 Web 链接将仅可在 Managed Browser 应用中打开。 <br><br> 如果正使用 Intune 管理设备，请参阅[使用 Microsoft Intune 的托管浏览器策略管理 Internet 访问](app-configuration-managed-browser.md)。 <br><br> 移动设备（iOS 和 Android）的 Microsoft Edge 浏览器支持 Intune 应用保护策略。 在 Edge 浏览器应用程序中使用其企业 Azure AD 帐户登录的用户将受 Intune 保护。 Microsoft Edge 浏览器集成了 MAM SDK 并支持其除阻止以外的所有数据保护策略：<ul><li>另存为：Microsoft Edge 浏览器不允许用户向云存储提供商（如 OneDrive）添加直接的应用内连接，并且不允许用户将文件下载到本地文件系统。</li><li>联系人同步：Microsoft Edge 浏览器不会保存到本地联系人列表。</li></ul>Microsoft Edge 浏览器将利用 Intune 策略的自动注册。 这意味着当设备上的另一个 Microsoft 应用程序由 Intune 策略管理时，Microsoft Edge 浏览器将自动检查是否存在面向 Edge 应用的策略。 Intune 策略的自动注册由 MAM SDK 处理，因此不需要应用参与。 | 否 |
| **加密应用数据** | 对于策略托管应用，使用 iOS 提供的设备级别的加密方案对数据进行静态加密。 需要 PIN 时，根据应用保护策略中的设置对数据进行加密。 <br><br> 转到[此处](https://support.apple.com/HT202739)官方 Apple 文档，查看哪些 iOS 加密模块由 FIPS 140-2 认证或挂起 FIPS 140-2 证书。 <br><br> 指定何时加密应用中工作或学校数据。 选择： <ul><li>**是**：锁定设备时，加密与此策略关联的所有应用数据，这些数据将受到 Intune 中的应用层加密保护。 启用此设置时，用户可能需要设置并使用 PIN 才能访问其设备。  如果没有设备 PIN 且需要加密，则不启动应用，并将通过“公司要求先启用设备 PIN 才能访问此应用”消息提示用户设置 PIN。</li><li>**否**：Intune 不会强制执行加密。 | 是|
| **禁用联系人同步** | 选择“是”，阻止应用将数据保存到设备上的本机“联系人”应用。 如果选择“否”，应用可将数据保存到设备上的本机“联系人”应用。 <br><br>执行选择性擦除从应用删除工作或学校数据时，将删除从应用直接同步到本机“联系人”应用的联系人。 无法擦除从本机通讯簿同步到另一个外部源中的任何联系人。 目前仅适用于 Microsoft Outlook 应用。 | 否 |
| **禁用打印** | 选择“是”，阻止应用打印工作或学校数据。 | 否 |
| **阻止第三方键盘** | 选择“是”：阻止在托管应用程序中使用第三方键盘。 <br><br>启用此设置后，用户将收到一次性消息，说明禁止使用第三方键盘。 用户首次需要使用键盘与组织数据进行交互时，将会出现此消息。 使用托管应用程序时，只能使用标准的 iOS 键盘，所有其他键盘选项都将禁用。 此设置不影响在非托管应用程序中使用第三方键盘。 | 否 |

> [!NOTE]
> 无数据重定位设置控制 iOS 设备上由 Apple 托管的打开方式功能。 要使用管理 Apple 打开方式，请参阅[使用 Microsoft Intune 管理 iOS 应用之间的数据传输](data-transfer-between-apps-manage-ios.md)。

## <a name="data-transfer-exemptions"></a>数据传输豁免

有一些豁免应用和平台服务，Intune 应用保护策略可能会允许在某些情况下向其或从其传输数据。 此列表可能会更改以反映有利于安全工作效率的服务和应用。

| 应用/服务名称 | 描述 |
| ---- | --- |
|<code>tel; telprompt</code> | 本机电话应用 |
| <code>skype</code> | Skype |
| <code>app-settings</code> | 设备设置 |
| <code>itms; itmss; itms-apps; itms-appss; itms-services</code> | App Store |
| <code>calshow</code> | 本机日历 |


## <a name="access-settings"></a>访问设置

| Setting | 如何使用 | 默认值 |
|------|------|------|
| **需要 PIN 才能进行访问** | 选择“是”，需要 PIN 才可使用此应用。 用户首次在工作或学校环境中运行应用时，将提示其设置此 PIN。 无论在联机或脱机情况下工作，PIN 始终有效。 默认值 = **是**。<br><br> 为 PIN 强度配置以下设置： <ul><li>**选择类型**：在访问应用了应用保护策略的应用之前，为数值或密码类型 PIN 设置要求。 数值要求只涉及数字，而密码可采用至少 1 个字母或至少 1 个特殊字符进行定义。 <br><br> **注意：** 配置密码类型要求应用具有 Intune SDK 版本 7.1.12 或更高版本。 数值类型没有任何 Intune SDK 版本限制。 允许的特殊字符包括 iOS 英语键盘上的特殊字符和符号。 默认值 = 数值。<br><br></li><li>**PIN 重置前的尝试次数**：指定用户重置其 PIN 码前必须成功完成输入的尝试次数。 此策略设置格式支持正整数。 默认值 = **5**。<br><br></li><li> **允许简单 PIN**：选择“是”，允许用户使用简单的 PIN 序列，如 1234、1111、abcd 或 aaaa。 选择“否”，阻止用户使用简单的序列。 <br><br>注意：如果配置了密码类型 PIN，且允许简单 PIN 设置为“是”，则用户在其 PIN 中需要至少 1 个字母或至少 1 个特殊字符。 如果配置了密码类型 PIN，且允许简单 PIN 设置为“否”，则用户在其 PIN 中需要至少 1 个数字和 1 个字母以及至少 1 个特殊字符。 默认值 = **是**。 <br><br></li><li>**PIN 长度**：指定 PIN 序列必须包含的最小位数。<br><br>注意：在某些 iOS 设备上，当配置了长度大于 6 的 PIN 时，用户将在 UI 上看到文本输入字段，但仍需输入“选择类型”设置确定的 PIN 类型。 默认值 = **4**。 <br><br></li><li> **允许指纹而非 PIN (iOS 8.0+)**：选择“是”，允许用户使用 [Touch ID](https://support.apple.com/HT201371) 而非 PIN 进行应用访问。 默认值 = **是**。<br><br></li><li> **允许使用面部识别替代 PIN (iOS 11+)**：选择“是”，允许用户使用 [Face ID](https://support.apple.com/HT208109) 而非 PIN 使用应用。 <br><br>**注意：** 配置面部识别要求应用具有 Intune SDK 版本 7.1.19 或更高版本。 默认值 = **是**。 用户使用其工作帐户访问应用时，系统会提示提供面部标识。<br><br></li><li> **托管设备 PIN 后禁用应用 PIN**：选择“是”，如果在已配置公司门户的已注册设备上检测到设备锁，则禁用应用 PIN。<br><br> **注意**：要求应用具有 Intune SDK 版本 7.0.1 或更高版本。 默认值 = **否**。</li></ul> 在 iOS 设备上，可让用户使用 [Touch ID](https://support.apple.com/HT201371) 或 [Face ID](https://support.apple.com/HT208109) 而非 PIN 来证明其身份。 Intune 使用 [LocalAuthentication](https://developer.apple.com/documentation/localauthentication/) API 对使用 Touch ID 和 Face ID 的用户进行身份验证。 若要了解有关 Touch ID 和 Face ID 的详细信息，请参阅 [iOS 安全指南](https://www.apple.com/business/docs/iOS_Security_Guide.pdf)。 用户尝试通过其工作或学校帐户使用此应用时，系统会提示他们提供其指纹标识或面部标识，而不是输入 PIN。 启用此设置时，如果使用工作或学校帐户，应用切换器的预览图像将模糊显示。 </li></ul><!-- <br><br>You can require a PIN expiration for targeted iOS apps. You can configure the PIN requirement and expiration date in days through the Azure portal. When required, a user will be required to set and use a new PIN before getting access to an iOS app. Only iOS apps that have app protection enabled with the Intune App SDK will support this feature.-->| 需要 PIN 才能进行访问：是 <br><br> 选择类型：数值 <br><br> PIN 重置尝试次数：5 <br><br> 允许使用简单 PIN：是 <br><br> PIN 长度：4 <br><br> 允许使用指纹：是 <br><br> 允许面部识别：是 <br><br> 禁用应用 PIN：否 |
| **访问需要公司凭据** | 选择“是”，要求用户使用其工作或学校帐户（而不是输入 PIN）登录进行应用访问。 如果将此设置为“是”，并且 PIN 或生物识别提示已打开，则会显示公司凭据以及 PIN 或生物识别提示。 | 否 |
| **阻止在已越狱或取得 root 权限的设备上运行托管应用** |  选择“是”，阻止在已越狱或取得 root 权限的设备上运行此应用。 用户仍能够将此应用用于个人任务，但必须使用其他设备访问此应用中的工作或学校数据。 | 是 |
| **在一定时间后重新检查访问要求（分钟）** | 配置下列设置： <ul><li>**超时**：指重新检查访问要求（在前面的策略中定义）之前的分钟数。 例如，如果管理员在策略中启用 PIN，并阻止取得 root 权限的设备，则用户打开 Intune 托管的应用时，必须输入 PIN，且必须在未取得 root 权限的设备上使用应用。 使用此设置时，用户在 30 分钟（默认值）内无需在任何 Intune 托管应用上再次输入 PIN 或执行 root 检测检查。  <br><br>**注意：** 在 iOS 上，同一发布者的所有 Intune 托管应用均共享此 PIN。 应用离开设备主屏幕后，就会重置特定 PIN 的 PIN 计时器。 在此设置定义的超时期限内，用户无需在共享 PIN 的任何 Intune 托管应用上输入该 PIN。 此策略设置格式支持正整数。<br><br></li><li>脱机宽限期：指 MAM 应用可以脱机运行的分钟数。 指定重新检查应用访问要求之前的时间（以分钟为单位）。 默认值 = **720** 分钟（12 小时）。 此宽限期过期后，应用将阻止对工作或学校数据的访问，直到网络访问可用为止。 此策略设置格式支持正整数。</li></ul>| 超时：30 <br><br> 脱机：720 |
| **擦除应用数据前的脱机时间间隔(天)** | 经过数天（由管理员定义）的脱机运行后，应用会要求用户连接到网络并重新进行身份验证。 如果用户身份验证成功，则可继续访问其数据，且将重置脱机时间间隔。  如果用户未能通过身份验证，则应用会对用户帐户和数据执行选择性擦除。  请参阅[如何仅擦除 Intune 托管应用中的企业数据](https://docs.microsoft.com/intune/apps-selective-wipe)，详细了解选择性擦除所删除的数据。 此策略设置格式支持正整数。 <br> | 90 天 |
| **要求最低 iOS 操作系统版本** | 选择“是”将要求要使用此应用需具备的最低 iOS 操作系统版本。 如果设备上的 iOS 版本不符合此要求，将阻止用户访问。 <br><br> **注意**：要求应用具有 Intune SDK 版本 7.0.1 或更高版本。 | 否 |
| **要求最低 iOS 操作系统版本(仅警告)** | 选择“是”将要求要使用此应用需具备的最低 iOS 操作系统版本。 如果设备上的 iOS 版本不符合此要求，用户将看到一个通知。 可忽略此通知。 <br><br> **注意**：要求应用具有 Intune SDK 版本 7.0.1 或更高版本。 | 否 |
| **要求最低应用版本** | 选择“是”将要求要使用此应用需具备的最低应用版本。 如果设备上的应用版本不符合此要求，将阻止用户访问。<br><br>由于应用的版本方案之间通常不同，因此，要创建一个针对一个应用的最低应用版本策略（例如“Outlook 版本策略”。 <br><br> 此策略设置格式支持 major.minor、major.minor.build 或 major.minor.build.revision。 <br><br> **注意**：要求应用具有 Intune SDK 版本 7.0.1 或更高版本。 | 否 | 
| **要求最低应用版本(仅警告)** | 选择“是”将建议要使用此应用需具备的最低应用版本。 如果设备上的应用版本不符合此要求，用户将会看到一个通知。 可忽略此通知。<br><br>由于应用的版本方案之间通常不同，因此，要创建一个针对一个应用的最低应用版本策略（例如“Outlook 版本策略”。 <br><br> 此策略设置格式支持 major.minor、major.minor.build 或 major.minor.build.revision。 <br><br> **注意**：要求应用具有 Intune SDK 版本 7.0.1 或更高版本。 | 否 | 
| **要求最低 Intune 应用保护策略 SDK 版本** | 选择“是”将要求要使用的应用上的最低 Intune 应用保护策略 SDK 版本。 如果应用的 Intune 应用保护策略 SDK 版本不符合此要求，将阻止用户访问。 <br> <br> 若要详细了解 Intune 应用保护策略 SDK，请参阅 [Intune App SDK 概述](app-sdk.md) <br><br> 此策略设置格式支持 major.minor、major.minor.build 或 major.minor.build.revision。 <br><br> **注意**：要求应用具有 Intune SDK 版本 7.0.1 或更高版本。 | 否 |

> [!NOTE]
> 要详细了解在“访问权限”部分配置给同一组应用和用户的多个 Intune 应用保护设置如何在 iOS 上运行，请参阅 [Intune MAM 常见问题](https://docs.microsoft.com/en-us/intune/mam-faq#app-experience-on-ios)和[在 Intune 中使用应用保护策略访问操作选择性地擦除数据](app-protection-policies-access-actions.md)。

##  <a name="add-ins-for-outlook-app"></a>Outlook 应用的加载项

Outlook 最近为 Outlook for iOS 引入了加载项，让你可将热门应用集成到电子邮件客户端中。 Outlook 的加载项可在 Web、Windows、Mac 和 Outlook for iOS 上使用。 Intune SDK 和 Intune 应用保护策略不包括对管理 Outlook 加载项的支持，但可使用其他方法来限制其使用。 由于加载项是通过 Microsoft Exchange 管理的，所以用户能够在 Outlook 和非托管加载项应用程序之间共享数据和邮件，除非用户的 Exchange 关闭了加载项。

如果要阻止最终用户访问和安装 Outlook 加载项（这会影响所有 Outlook 客户端），请确保在 Exchange 管理中心中对角色进行以下更改：

- 若要防止用户安装 Office 应用商店加载项，请从中删除“我的市场”角色。
- 若要防止用户侧向加载加载项，请从中删除“我的自定义应用”角色。
- 若要防止用户安装所有加载项，请从中删除“我的自定义应用”和“我的市场”角色。

这些说明适用于跨 Web、Windows、Mac 和移动版 Outlook 的 Office 365、Exchange 2016、Exchange 2013。

- 详细了解 [Outlook 的加载项](https://technet.microsoft.com/library/jj943753(v=exchg.150).aspx)。
- 详细了解[如何指定可安装和管理 Outlook 应用的加载项的管理员和用户](https://technet.microsoft.com/library/jj943754(v=exchg.150).aspx)。

##  <a name="linkedin-account-connections-for-microsoft-apps"></a>Microsoft 应用的 LinkedIn 帐户连接

LinkedIn 帐户连接允许用户在某些 Microsoft 应用中查看公开的 LinkedIn 档案信息。 默认情况下，用户可选择连接其 LinkedIn 和 Microsoft 工作或学校帐户，以查看其他 LinkedIn 档案信息。 

> [!NOTE]
> 美国政府客户以及在澳大利亚、加拿大、中国、法国、德国、印度、韩国、英国、日本和南非托管 Exchange Online 邮箱的组织目前无法使用 LinkedIn 集成功能。

Intune SDK 和 Intune 应用保护策略不包括对管理 LinkedIn 帐户连接的支持，但可使用其他方法来对其进行管理。 可为整个组织禁用 LinkedIn 帐户连接，也可为组织中的所选用户组启用 LinkedIn 帐户连接。 这些设置会影响所有平台（Web、移动和桌面）上 Office 365 应用之间的 LinkedIn 连接。 你可以：

- 在 Azure 门户中启用或禁用租户的 LinkedIn 帐户连接。 
- 使用组策略为组织的 Office 2016 应用启用或禁用 LinkedIn 帐户连接。

如果为租户启用了 LinkedIn 集成，则当组织中的用户连接其 LinkedIn 和 Microsoft 工作或学校帐户时，他们有两种选项： 

- 他们可授权在两个帐户之间共享数据。 这意味着，他们允许其 LinkedIn 帐户与其 Microsoft 工作或学校帐户彼此共享数据。 与 LinkedIn 共享的数据退出联机服务。 
- 他们仅允许从 LinkedIn 帐户向 Microsoft 工作和学校帐户共享数据

如果用户同意在帐户之间共享数据，与 Office 加载项一样，LinkedIn 集成使用现有的 Microsoft Graph API。 LinkedIn 集成仅使用 Office 加载项可用的 API 子集，并支持各种排除项。


|Microsoft Graph 权限  |描述  |
|---------|---------|
|[人员](https://developer.microsoft.com/en-us/graph/docs/concepts/permissions_reference#people-permissions)的读取权限     |允许该应用读取与已登录用户相关的评分列表。 该列表可包括本地联系人、社交网络或组织目录中的联系人以及最近通信（如电子邮件和 Skype）中的联系人。         |
|[日历](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdeveloper.microsoft.com%2Fen-us%2Fgraph%2Fdocs%2Fconcepts%2Fpermissions_reference%23calendars-permissions&data=04%7C01%7CCem.Aykan%40microsoft.com%7C59705402acc347cdf0d908d5b1d82d53%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636610464378331622%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwifQ%3D%3D%7C-1&sdata=fABkrlIxqggnB%2Bc%2BR%2BbFpuenhSg7OHfBhWcbv3ahmAU%3D&reserved=0)的读取权限     |允许该应用读取用户日历中的事件。 包括已登录用户日历中的会议、其时间、地点和与会者。         |
|[用户配置文件](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdeveloper.microsoft.com%2Fen-us%2Fgraph%2Fdocs%2Fconcepts%2Fpermissions_reference%23user-permissions&data=04%7C01%7CCem.Aykan%40microsoft.com%7C59705402acc347cdf0d908d5b1d82d53%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636610464378341626%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwifQ%3D%3D%7C-1&sdata=RcnVIpntjyR4TXafOYTV0SffZuZWpshQQWY0e2VkkXg%3D&reserved=0)的读取权限     |允许用户登录到应用，并允许应用读取已登录用户的个人资料。 它还允许应用读取已登录用户的基本公司信息。         |
|Subscriptions     |此作用域不可用且尚未使用。 它包括用户组织向 Microsoft 应用和服务（如 Office 365）提供的订阅。         |
|见解     |此作用域不可用且尚未使用。 它包括基于 Microsoft 服务的使用与已登录用户帐户相关的权益。         |

### <a name="learn-more"></a>了解详细信息

- 了解 [Microsoft 应用中的 LinkedIn 信息和功能](https://go.microsoft.com/fwlink/?linkid=850740)。
- 在 [Office 365 产品指南页](https://products.office.com/en-US/business/office-365-roadmap?filters=%26freeformsearch=linkedin#abc)了解 LinkedIn 帐户连接版本。 
- 了解[配置 LinkedIn 帐户连接](https://docs.microsoft.com/en-us/azure/active-directory/linkedin-integration)。
- 有关用户的 LinkedIn 和 Microsoft 工作或学校帐户之间共享的数据的详细信息，请参阅[工作或学校的 Microsoft 应用程序中的 LinkedIn](https://www.linkedin.com/help/linkedin/answer/84077)。

