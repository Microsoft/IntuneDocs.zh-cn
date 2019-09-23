---
title: 包含文件
description: 包含文件
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 041f37e56e85b0ac26a4dd7a9dbbdb49bc0ebd9e
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2019
ms.locfileid: "71166328"
---
本文中的通知提供了重要信息，可以帮助你为未来的 Intune 更改和功能做好准备。 


### <a name="decreasing-support-for-android-device-administrator"></a>减少对 Android 设备管理员的支持 
Android 设备管理员（有时称为“旧版”Android 管理，随 Android 2.2 发布）是一种管理 Android 设备的方法。 不过，[Android Enterprise](../connect-intune-android-enterprise.md)（随 Android 5.0 发布）现在提供改进的管理功能。 为了实现更现代化、更丰富、更安全的设备管理，Google 正在减少新 Android 版本中对设备管理员的支持。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
由于 Google 的这些变化，Intune 用户将受到以下几个方面的影响： 
- Intune 将只能在 2020 年夏季之前为运行 Android 10 和更高版本（也称为 Android Q）的设备管理员管理的 Android 设备提供支持。 此日期是预计发布 Android 下一个主要版本的时间。  
- 在 2020 年夏季以后运行 Android 10 或更高版本的设备管理员管理的设备将无法再进行完全管理。    
- 设备管理员管理的仍在低于 Android 10 的 Android 版本上运行 Android 设备将不会受到影响，可以继续由设备管理员进行完全管理。  
- 对于所有 Android 10 及更高版本的设备，Google 限制了设备管理员管理代理（如公司门户）访问设备标识符信息的能力。 在设备更新到 Android 10 或更高版本后，这将影响以下 Intune 功能： 
    - VPN 的网络访问控制将不再有效。  
    - 使用 IMEI 或序列号将设备识别为公司拥有的设备将不会自动将设备标记为公司拥有的设备。 
    - 在 Intune 中，IMEI 和序列号将不再对 IT 管理员可见。 
        > [!Note]
        > 这只会影响 Android 10 及更高版本上设备管理员管理的设备，并且不会影响作为 Android Enterprise 管理的设备。 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
为避免在即将到来的 2020 年夏季出现功能降低的情况，建议采取如下操作：
- 不要将新设备加入设备管理员管理中。
- 如果希望设备接收到 Android 10 的更新，请将其从设备管理员管理迁移到 Android Enterprise 管理和/或应用保护策略。

#### <a name="additional-information"></a>其他信息
- [从设备管理员迁移到 Android Enterprise 的 Google 指南](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [弃用设备管理员 API 计划的 Google 文档](https://developers.google.com/android/work/device-admin-deprecation)

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>将 Android 公司门户应用更新到最新版本 <!--4536963-->
Intune 定期发布 Android 公司门户应用的更新。 在 2018 年 11 月，我们发布了一次公司门户更新，其中包括后端开关，以便为 Google 从现有通知平台更改为 Google 的 Firebase 云消息传递 (FCM) 做好准备。 随着 Google 停用其现有通知平台并迁移到 FCM，最终用户需要将他们的公司门户应用至少更新到 2018 年 11 月版本，以便继续与 Google Play 商店通信。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
我们的遥测显示，你的设备的公司门户版本低于 5.0.4269.0。 如果未安装该版本或更高版本的公司门户应用，那么，由 IT 专业人员发起的设备操作（如擦除、重置密码）、可用和所需的应用安装以及证书注册可能无法按预期方式工作。 如果设备是在 Intune 中注册的 MDM，可以通过依次进入“客户端应用”、“发现的应用”查看公司门户版本和用户。 选择早期版本的公司门户，可以查看哪些最终用户的设备尚未更新公司门户。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
要求尚未更新的 Android 设备的最终用户通过 Google Play 更新公司门户。 如果某个用户未自动更新公司门户应用，请通知支持人员。 有关 Google FCM 平台和更改的更多信息，请参阅“其他信息”中的链接。

#### <a name="additional-information"></a>其他信息
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-fullscreen-experience-coming-to-intune---4593669--"></a>Intune 即将推出新的全屏幕体验 <!--4593669-->
我们将在 Azure 门户中向 Intune 推出更新的创建和编辑 UI 体验。 此新体验将使用压缩在一个边栏选项卡中的向导样式格式简化现有工作流。 此更新将消除“边栏选项卡扩展”或需要向下钻取到深度边栏选项卡体验的任何创建和编辑流。 创建工作流也将更新为包含分配（应用分配除外）。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
接下来的几个月里，将同时在 portal.azure.com 和 devicemanagement.microsoft.com 推出 Intune 全屏幕体验。 此 UI 更新不会影响现有策略和配置文件的功能，但你将看到一个稍经修改的工作流。 例如，创建新策略时，你将能够将某些分配设置为此流的一部分，而不是在创建策略后执行此操作。 有关控制台中新体验的屏幕截图，请参阅附加信息中的博客文章。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我能够针对此更改做什么准备？
不需要执行任何操作，但可以考虑在必要时更新 IT 专业人员指南。 当在 Azure 门户上向 Intune 中的各种边栏选项卡推出此体验时，我们将更新文档。

#### <a name="additional-information"></a>其他信息 
https://aka.ms/intune_fullscreen

### <a name="plan-for-change-intune-moving-to-support-ios-11-and-higher-in-september----4665324--"></a>更改计划：Intune 将于 9 月开始支持 iOS 11 及更高版本 <!-- 4665324-->
我们预计 Apple 将于 9 月发布 iOS 13。 Intune 注册、公司门户和 Managed Browser 将在 iOS 13 发布后不久开始支持 iOS 11 及更高版本。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
如果 iOS 11.0 及更高版本上支持 O365 移动应用，这可能不会对你造成任何影响。你可能已升级了 OS 或设备。 但如果你拥有下面列出的任何设备，或者决定要注册下面列出的任何设备，请注意，以下设备不支持 iOS 10 以上的 OS。 需将这些设备升级为支持 iOS 11 或更高版本的设备：

- iPhone 5
- iPhone 5c
- iPad（第 4 代）

如果使用应用程序保护策略 (APP)，则还可以设置“要求最低 iOS 操作系统(仅警告)”访问设置。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
检查 Intune 报告，查看可能受影响的设备或用户。 转到“设备”   > “所有设备”  ，并按“OS”进行筛选。 可以添加其他列，帮助确定组织中哪些人员拥有运行 iOS 10 的设备。 要求最终用户在 9 月前将其设备升级到支持的 OS 版本。

### <a name="plan-for-change-support-for-version-811-and-higher-of-intune-app-sdk-for-ios----3586942--"></a>更改计划：支持 Intune App SDK for iOS 的 8.1.1 版及更高版本 <!-- 3586942-->
从 2019 年 9 月起，Intune 将通过 Intune App SDK 8.1.1 及更高版本支持 iOS 应用。 不再支持使用低于 SDK 8.1.1 版本构建的应用。 此更改将随 Apple iOS 13 的发布（预计将于 9 月发布，并且已在 MC181399 中公布）而生效。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
借助 Intune App SDK 或 App Wrapping 集成，可通过数据加密保护公司数据免受未经批准的应用程序和用户的影响。 Intune 应用保护策略 (APP) 启用加密时，Intune App SDK for iOS 将默认使用 256 位加密密钥。 在此更改之后，在 SDK 8.1.1 之前的版本上使用 128 位加密密钥的任何 iOS 应用都不能再与集成了 SDK 8.1.1 或使用 256 位密钥的应用程序共享数据。 所有的 iOS 应用都需要 SDK 8.1.1 版本或更高版本，才能进行受保护的数据共享。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我能够针对此更改做什么准备？
检查 Microsoft、第三方和业务线 (LOB) 应用。 确保所有受 Intune APP 保护的应用程序都使用 SDK 版本 8.1.1 或更高版本。

- 对于 LOB 应用：可能需要重新发布与 SDK 8.1.1 版本或更高版本集成的应用。 建议使用最新的 SDK 版本。 要了解如何针对应用保护策略准备好 LOB 应用，请参阅[针对应用保护策略准备好业务线应用](../apps-prepare-mobile-application-management.md)。
- Microsoft/第三方应用：确保向用户部署这些应用的最新版本。

还应更新文档或开发人员指南（如适用），将此更改添加到其中，以支持 SDK。

#### <a name="additional-information"></a>其他信息
[准备业务线应用以使用应用保护策略](../apps-prepare-mobile-application-management.md)

### <a name="plan-for-change-new-windows-updates-settings-in-intune----4464404---"></a>更改计划：Intune 中的新 Windows 更新设置 <!-- 4464404 -->
从 Intune 服务的 8 月版本或 1908 开始，我们将添加新的“截止时间设置”，可以对此进行配置，而不是“允许用户重启(预定重启)”设置。 我们计划在 1909 或 9 月更新中的 UI 上禁用预定重启设置，然后在 10 月底之前将它们从控制台中完全删除。 

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
如果在环境中管理 Windows 10 设备： 
- 对于 8 月 Intune 更新或 1908，除了旧的预定重启设置，你还会在控制台中看到新的截止时间设置。
- 如果同时配置了这两个旧设置和新设置，则截止时间设置值将重写预定重启设置值。
- 截止时间设置将替换 1910 更新控制台中的“允许用户重新启动(预定重启)”选项。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我能够针对此更改做什么准备？
开始使用 1908 中的截止时间设置，方法是使用所需的值对其进行配置。 准备就绪后，可以将预定重启设置设为“未配置”，以便在 10 月从控制台中删除这些设置。

如果需要，请更新文档和任何自动化脚本。 

删除预定重启设置之前，我们会随时为你提供最新消息并将提醒发送到消息中心。

### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-october---4911065---"></a>更改计划：适用于 Android 的 Intune App SDK 和应用保护策略将于 10 月份支持 Android 5.0 和更高版本 <!--4911065 -->
Intune 将于 10 月份支持 Android 5.x (Lollipop) 及更高版本。 使用最新的 Intune App SDK 更新所有包装好的应用，并更新设备。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
如果没有使用或未计划使用适用于 Android 的 SDK 或应用，此更改不会影响你。 如果正在使用 Intune App SDK，请确保更新到最新版本，并将设备更新到 Android 5.x 和更高版本。 如果不更新，应用将不会收到更新，并且随着时间推移其体验质量将会降低。 

下面是运行 Android 版本 4.x 的 Intune 中注册的常用设备列表。 如果有其中一个设备，请执行相应的步骤，确保该设备将支持 Android 版本 5.0 或更高版本，或者将其替换为支持 Android 版本 5.0 或更高版本的设备。 这个列表并未包含所有可能需要评估的设备：
- Samsung SM-T561  
- Samsung SM-T365 
- Samsung GT-I9195 
- Samsung SM-G800F
- Samsung SM-G357FZ
- Motorola XT1080
- Samsung GT-I9305
- Samsung SM-T231

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
使用最新的 Intune App SDK 包装应用。 还可以设置“要求最低操作系统版本(仅警告)”条件启动设置来通知个人设备上的最终用户进行升级。
