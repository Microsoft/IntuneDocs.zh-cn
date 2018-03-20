---
title: "iOS 应用保护策略设置"
titlesuffix: Microsoft Intune
description: "本主题介绍适用于 iOS 设备的应用保护策略设置。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0f8b08f2-504c-4b38-bea2-b8a4ef0526b8
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fcdcc7c91791713ef784fbcebd23aa4b96c732dc
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2018
---
#  <a name="ios-app-protection-policy-settings"></a>iOS 应用保护策略设置
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

可在 Azure 门户的“添加策略” > “设置”边栏选项卡中为应用保护策略[配置](app-protection-policies.md)本主题所述的策略设置。

有两种类别的策略设置：数据重定位设置和访问设置。 在本主题中，术语***策略托管应用***指使用应用保护策略配置的应用。

##  <a name="data-relocation-settings"></a>数据重定位设置

| Setting | 如何使用 | 默认值 |
|------|------|------|
| **阻止 iTunes 和 iCloud 备份** | 选择“是”，阻止此应用将工作或学校的数据备份到 iTunes 和 iCloud。 选择“否”允许此应用程序将工作或学校的数据备份到 iTunes 和 iCloud。| 是 |
| **允许应用向其他应用传送数据** | 指定哪些应用可从此应用接收数据： <ul><li> **策略托管应用**：仅允许传输到其他策略托管应用。</li> <li>**所有应用**：允许传输到任何应用。 </li> <li>**无**：不允许将数据传输到任何应用，包括其他策略托管应用。</li></ul> 此外，如果将此选项设置为“策略托管应用”或“无”，则将阻止允许 Spotlight Search 在应用内搜索数据的 iOS 9 功能。 <br><br> 默认情况下，Intune 允许向一些豁免应用和服务传输数据。 此外，如果需要允许将数据传输到不支持 Intune APP 的应用，则可以创建自己的豁免项目。 有关详细信息，请参阅[数据传输豁免](#data-transfer-exemptions)。 | 所有应用 |
| **允许应用从其他应用接收数据** | 指定哪些应用可将数据传输到此应用： <ul><li>**策略托管应用**：仅允许从其他策略托管应用传输。</li><li>**所有应用**：允许从任何应用传输数据。</li><li>**无**：不允许从任何应用传输数据，包括其他策略托管应用。</li></ul> Intune 可能会允许从一些豁免应用和服务传输数据。 有关应用和服务的完整列表，请参阅[数据传输豁免](#data-transfer-exemptions)。 非注册 iOS 设备上已启用多标识 MAM 的 应用忽略此策略，并允许所有传入数据。 | 所有应用 |
| **阻止“另存为”** | 选择“是”，在此应用中禁用“另存为”选项。 如果你希望允许使用“另存为”，请选择“否”。 | 否 |
| **限制剪切、复制和粘贴到其他应用程序** | 指定剪切、复制和粘贴操作何时可用于此应用。 选择： <ul><li>**阻止**：不允许在此应用和任何其他应用间进行剪切、复制和粘贴操作。</li><li>**策略托管应用**：允许在此应用和其他策略托管应用间进行剪切、复制和粘贴操作。</li><li>**带粘贴的策略托管应用**：允许在此应用和其他策略托管应用间进行剪切或复制。 允许将任何应用中的数据粘贴到此应用。</li><li>**任何应用**：不限制从此应用和对此应用进行剪切、复制和粘贴。 | 任何应用 |
|**限制显示在 Managed Browser 内的 Web 内容** | 选择“是”，强制在 Managed Browser 应用中打开应用中的 Web 链接。 <br><br> 对于未在 Intune 中注册的设备，策略托管应用中的 Web 链接将仅可在 Managed Browser 应用中打开。 <br><br> 如果正使用 Intune 管理设备，请参阅[使用 Microsoft Intune 的托管浏览器策略管理 Internet 访问](app-configuration-managed-browser.md)。 | 否 |
| **加密应用数据** | 对于策略托管应用，使用 iOS 提供的设备级别的加密方案对数据进行静态加密。 需要 PIN 时，根据应用保护策略中的设置对数据进行加密。 <br><br> 转到[此处](https://support.apple.com/HT202739)官方 Apple 文档，查看哪些 iOS 加密模块由 FIPS 140-2 认证或挂起 FIPS 140-2 证书。 <br><br> 指定何时加密应用中工作或学校数据。 选择： <ul><li>**锁定设备时**：锁定设备时，加密与此策略关联的所有应用数据。</li><li>**锁定设备并具有打开的文件时**：锁定设备时，对与此策略相关联的所有应用数据进行加密，当前已在应用中打开的文件中的数据除外。</li><li>**设备重启后**：设备重启后，对与此策略相关联的所有应用数据进行加密，直到首次解锁设备。</li><li>**使用设备设置**：基于设备上的默认设置对应用数据进行加密。 </li></ul> 启用此设置时，用户可能需要设置并使用 PIN 才能访问其设备。  如果没有设备 PIN 且需要加密，则不启动应用，并将通过“公司要求先启用设备 PIN 才能访问此应用”消息提示用户设置 PIN。  | 当设备锁定 |
| **禁用联系人同步** | 选择“是”，阻止应用将数据保存到设备上的本机“联系人”应用。 如果选择“否”，应用可将数据保存到设备上的本机“联系人”应用。 <br><br>执行选择性擦除从应用删除工作或学校数据时，将删除从应用直接同步到本机“联系人”应用的联系人。 无法擦除从本机通讯簿同步到另一个外部源中的任何联系人。 目前仅适用于 Microsoft Outlook 应用。 | 否 |
| **禁用打印** | 选择“是”，阻止应用打印工作或学校数据。 | 否 |
| **选择可保存公司数据的存储服务** | 用户可以保存到所选的服务（OneDrive for Business、SharePoint 和本地存储）中。 将阻止所有其他服务。 | 未选择任何项 |

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
| **需要 PIN 才能进行访问** | 选择“是”，需要 PIN 才可使用此应用。 用户首次在工作或学校环境中运行应用时，将提示其设置此 PIN。 无论在联机或脱机情况下工作，PIN 始终有效。 默认值 = **是**。<br><br> 为 PIN 强度配置以下设置： <ul><li>**选择类型**：在访问应用了应用保护策略的应用之前，为数值或密码类型 PIN 设置要求。 数值要求只涉及数字，而密码可采用至少 1 个字母或至少 1 个特殊字符进行定义。 <br><br> **注意：**配置密码类型要求应用具有 Intune SDK 版本 7.1.12 或更高版本。 数值类型没有任何 Intune SDK 版本限制。 允许的特殊字符包括 iOS 英语键盘上的特殊字符和符号。 默认值 = 数值。</li><br><li>**PIN 重置前的尝试次数**：指定用户重置其 PIN 码前必须成功完成输入的尝试次数。 此策略设置格式支持正整数。 默认值 = **5**。</li><li> **允许简单 PIN**：选择“是”，允许用户使用简单的 PIN 序列，如 1234、1111、abcd 或 aaaa。 选择“否”，阻止用户使用简单的序列。 <br><br>**注意**：在 iOS 上，如果配置了密码类型 PIN，且允许简单 PIN 设置为“是”，则需要至少 1 个字母或至少 1 个特殊字符。 如果配置了密码类型 PIN，且允许简单 PIN 设置为“否”，则需要至少 1 个数字，1 个字母和至少 1 个特殊字符。  默认值 = **是**。 </li><br><li> **PIN 长度**：指定 PIN 序列必须包含的最小位数。 默认值 = **4**。 </li><li> **允许指纹而非 PIN (iOS 8.0+)**：选择“是”，允许用户使用 [Touch ID](https://support.apple.com/HT201371) 而非 PIN 进行应用访问。 默认值 = **是**。</li><li> **允许使用面部识别替代 PIN (iOS 11+)**：选择“是”，允许用户使用 [Face ID](https://support.apple.com/HT208109) 而非 PIN 使用应用。 默认值 = **是**。 用户使用其工作帐户访问应用时，系统会提示提供面部标识。</li><li> **管理设备 PIN 时禁用应用 PIN**：在已注册设备上检测到设备锁后选择“是”禁用应用 PIN。 <br><br> **注意**：要求应用具有 Intune SDK 版本 7.0.1 或更高版本。 默认值 = 否</li></ul> 在 iOS 设备上，可让用户使用 [Touch ID](https://support.apple.com/HT201371) 或 [Face ID](https://support.apple.com/HT208109) 而非 PIN 来证明其身份。 Intune 使用 [LocalAuthentication](https://developer.apple.com/documentation/localauthentication/) API 对使用 Touch ID 和 Face ID 的用户进行身份验证。 若要了解有关 Touch ID 和 Face ID 的详细信息，请参阅 [iOS 安全指南](https://www.apple.com/business/docs/iOS_Security_Guide.pdf)。 用户尝试通过其工作或学校帐户使用此应用时，系统会提示他们提供其指纹标识或面部标识，而不是输入 PIN。 启用此设置时，如果使用工作或学校帐户，应用切换器的预览图像将模糊显示。 </li></ul><!-- <br><br>You can require a PIN expiration for targeted iOS apps. You can configure the PIN requirement and expiration date in days through the Azure portal. When required, a user will be required to set and use a new PIN before getting access to an iOS app. Only iOS apps that have app protection enabled with the Intune App SDK will support this feature.-->| 需要 PIN 才能进行访问：是 <br><br> 选择类型：数值 <br><br> PIN 重置尝试次数：5 <br><br> 允许使用简单 PIN：是 <br><br> PIN 长度：4 <br><br> 允许使用指纹：是 <br><br> 允许面部识别：是 <br><br> 禁用应用 Pin：否 |
| **访问需要公司凭据** | 选择“是”，要求用户使用其工作或学校帐户（而不是输入 PIN）登录进行应用访问。 如果将其设置为“是”，则此设置将替代 PIN 或 Touch ID 的要求。  | 否 |
| **阻止在已越狱或取得 root 权限的设备上运行托管应用** |  选择“是”，阻止在已越狱或取得 root 权限的设备上运行此应用。 用户仍能够将此应用用于个人任务，但必须使用其他设备访问此应用中的工作或学校数据。 | 是 |
| **在一定时间后重新检查访问要求（分钟）** | 配置下列设置： <ul><li>**超时**：指重新检查访问要求（在前面的策略中定义）之前的分钟数。 例如，如果管理员在策略中启用 PIN，并阻止取得 root 权限的设备，则用户打开 Intune 托管的应用时，必须输入 PIN，且必须在未取得 root 权限的设备上使用应用。 使用此设置时，用户在 30 分钟（默认值）内无需在任何 Intune 托管应用上再次输入 PIN 或执行 root 检测检查。  <br><br>**注意：**在 iOS 上，同一发布者的所有 Intune 托管应用均共享此 PIN。 应用离开设备主屏幕后，就会重置特定 PIN 的 PIN 计时器。 在此设置定义的超时期限内，用户无需在共享 PIN 的任何 Intune 托管应用上输入该 PIN。 此策略设置格式支持正整数。<br></li><br><li>**脱机宽限期**：指 MAM 应用可脱机运行的分钟数，需在重新检查应用访问要求之前指定该时间（以分钟为单位）。 默认值 = **720** 分钟（12 小时）。 此时间段到期后，应用将要求用户对 AAD 进行身份验证，以便应用可以继续运行。 此策略设置格式支持正整数。<br></li></ul>| 超时：30 <br><br> 脱机：720 |
| **擦除应用数据前的脱机时间间隔(天)** | 经过数天（由管理员定义）的脱机运行后，应用会要求用户连接到网络并重新进行身份验证。 如果用户身份验证成功，则可继续访问其数据，且将重置脱机时间间隔。  如果用户未能通过身份验证，则应用会对用户帐户和数据执行选择性擦除。  请参阅[如何仅擦除 Intune 托管应用中的企业数据](https://docs.microsoft.com/intune/apps-selective-wipe)，详细了解选择性擦除所删除的数据。 此策略设置格式支持正整数。 <br> | 90 天 |
| **要求最低 iOS 操作系统版本** | 选择“是”将要求要使用此应用需具备的最低 iOS 操作系统版本。 如果设备上的 iOS 版本不符合此要求，将阻止用户访问。 <br><br> **注意**：要求应用具有 Intune SDK 版本 7.0.1 或更高版本。 | 否 |
| **要求最低 iOS 操作系统版本(仅警告)** | 选择“是”将要求要使用此应用需具备的最低 iOS 操作系统版本。 如果设备上的 iOS 版本不符合此要求，用户将看到一个通知。 可忽略此通知。 <br><br> **注意**：要求应用具有 Intune SDK 版本 7.0.1 或更高版本。 | 否 |
| **要求最低应用版本** | 选择“是”将要求要使用此应用需具备的最低应用版本。 如果设备上的应用版本不符合此要求，将阻止用户访问。<br><br>由于应用的版本方案之间通常不同，因此，要创建一个针对一个应用的最低应用版本策略（例如“Outlook 版本策略”。 <br><br> 此策略设置格式支持 major.minor、major.minor.build 或 major.minor.build.revision。 <br><br> **注意**：要求应用具有 Intune SDK 版本 7.0.1 或更高版本。 | 否 | 
| **要求最低应用版本(仅警告)** | 选择“是”将建议要使用此应用需具备的最低应用版本。 如果设备上的应用版本不符合此要求，用户将会看到一个通知。 可忽略此通知。<br><br>由于应用的版本方案之间通常不同，因此，要创建一个针对一个应用的最低应用版本策略（例如“Outlook 版本策略”。 <br><br> 此策略设置格式支持 major.minor、major.minor.build 或 major.minor.build.revision。 <br><br> **注意**：要求应用具有 Intune SDK 版本 7.0.1 或更高版本。 | 否 | 
| **要求最低 Intune 应用保护策略 SDK 版本** | 选择“是”将要求要使用的应用上的最低 Intune 应用保护策略 SDK 版本。 如果应用的 Intune 应用保护策略 SDK 版本不符合此要求，将阻止用户访问。 <br> <br> 若要详细了解 Intune 应用保护策略 SDK，请参阅 [Intune App SDK 概述](app-sdk.md) <br><br> 此策略设置格式支持 major.minor、major.minor.build 或 major.minor.build.revision。 <br><br> **注意**：要求应用具有 Intune SDK 版本 7.0.1 或更高版本。 | 否 |

> [!NOTE]
> 若要深入了解在“访问权限”部分配置给同一组应用和用户的多个 Intune 应用保护设置如何在 iOS 上运行，请参阅 [Intune MAM 常见问题](https://docs.microsoft.com/en-us/intune/mam-faq#app-experience-on-ios)。

##  <a name="add-ins-for-outlook-app"></a>Outlook 应用的加载项

Outlook 最近为 Outlook for iOS 引入了加载项，让你可将热门应用集成到电子邮件客户端中。 Outlook 的加载项可在 Web、Windows、Mac 和 Outlook for iOS 上使用。 由于加载项是通过 Microsoft Exchange 管理的，所以用户能够在 Outlook 和非托管加载项应用程序之间共享数据和邮件，除非用户的 Exchange 关闭了加载项。

如果要阻止最终用户访问和安装 Outlook 加载项（这会影响所有 Outlook 客户端），请确保在 Exchange 管理中心中对角色进行以下更改：

- 若要防止用户安装 Office 应用商店加载项，请从中删除“我的应用商店”角色。
- 若要防止用户侧向加载加载项，请从中删除“我的自定义应用”角色。
- 若要防止用户安装所有加载项，请从中删除“我的自定义应用”和“我的应用商店”角色。

这些说明适用于跨 Web、Windows、Mac 和移动版 Outlook 的 Office 365、Exchange 2016、Exchange 2013。

- 详细了解 [Outlook 的加载项](https://technet.microsoft.com/library/jj943753(v=exchg.150).aspx)。
- 详细了解[如何指定可安装和管理 Outlook 应用的加载项的管理员和用户](https://technet.microsoft.com/library/jj943754(v=exchg.150).aspx)。
