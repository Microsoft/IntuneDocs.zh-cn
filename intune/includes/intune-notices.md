---
title: 包含文件
description: 包含文件
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 0aa78ec17aba5deb0c914c3698676219f203b856
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73415085"
---
本文中的通知提供了重要信息，可以帮助你为未来的 Intune 更改和功能做好准备。

### <a name="plan-for-change-the-server-side-logging-for-siri-commands-setting-will-be-removed-from-the-intune-console----5468501--"></a>更改计划：“Siri 命令的服务器端日志记录”设置将从 Intune 控制台中删除 <!-- 5468501-->

我们计划通过 Intune 服务的 11 月更新从 Intune 控制台中删除“Siri 命令的服务器端日志记录”设置。 此更改与已删除该设置的 Apple 保持一致。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
当 11 月更新或 1911 于 11 月中旬推出时，你会看到此设置已从 Intune 控制台中的 iOS 配置文件的“设备限制”菜单（内置应用）中删除。 它可能出现在策略和目标设备的管理配置文件中，但该设置对设备没有影响。 我们不会对功能造成很大的影响，因为它当前不能在设备上运行，即使你在管理配置文件中看到了它也是如此。

可以选择以下两个路径之一：
- 如果要从策略中删除此设置，则可以转到具有此设置的配置文件，进行次要编辑并保存策略。 此策略将在后端重新计算，并且将从策略中删除此设置。
- 如果选择不执行此操作，则最终用户将在其设备的管理配置文件中看到此设置，但该设置没有任何影响。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我能够针对此更改做什么准备？
你可以根据上述部分执行操作或将策略保留原样。 当此更改推出时，我们将更新“新增功能”页和文档。

### <a name="end-of-support-for-legacy-pc-management"></a>停止支持旧版 PC 管理

将于 2020 年 10 月 15 日停止支持旧版 PC 管理。 请将设备升级到 Windows 10，并将它们重新注册为 MDM 设备，以便继续由 Intune 托管它们。

[了解详细信息](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator"></a>减少对 Android 设备管理员的支持 
Android 设备管理员（有时称为“旧版”Android 管理，随 Android 2.2 发布）是一种管理 Android 设备的方法。 不过，[Android Enterprise](../enrollment/connect-intune-android-enterprise.md)（随 Android 5.0 发布）现在提供改进的管理功能。 为了实现更现代化、更丰富、更安全的设备管理，Google 正在减少新 Android 版本中对设备管理员的支持。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
由于 Google 的这些变化，Intune 用户将受到以下几个方面的影响：  
- Intune 将只能在 2020 年夏季之前为运行 Android 10 和更高版本（也称为 Android Q）的设备管理员管理的 Android 设备提供支持。 此日期是预计发布 Android 下一个主要版本的时间。   
- 在 2020 年夏季以后运行 Android 10 或更高版本的设备管理员管理的设备将无法再进行完全管理。       
- 设备管理员管理的仍在低于 Android 10 的 Android 版本上运行 Android 设备将不会受到影响，可以继续由设备管理员进行完全管理。    
- 对于运行 Android 10 及更高版本的所有设备，Google 限制了设备管理员管理代理（如公司门户）访问设备标识符信息的能力。 在设备更新到 Android 10 或更高版本后，这将影响以下 Intune 功能：  
    - VPN 的网络访问控制将不再有效。   
    - 使用 IMEI 或序列号将设备识别为公司拥有的设备将不会自动将设备标记为公司拥有的设备。  
    - 在 Intune 中，IMEI 和序列号将不再对 IT 管理员可见。 
        > [!NOTE]
        > 这只会影响 Android 10 及更高版本上设备管理员管理的设备，并且不会影响作为 Android Enterprise 管理的设备。 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
为避免在即将到来的 2020 年夏季出现功能缩减的情况，建议采取如下操作：
- 不要将新设备加入设备管理员管理中。
- 如果希望设备接收到 Android 10 的更新，请将其从设备管理员管理迁移到 Android Enterprise 管理和/或应用保护策略。

#### <a name="additional-information"></a>其他信息
- [从设备管理员迁移到 Android Enterprise 的 Google 指南](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [弃用设备管理员 API 计划的 Google 文档](https://developers.google.com/android/work/device-admin-deprecation)

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>将 Android 公司门户应用更新到最新版本 <!--4536963-->
Intune 定期发布 Android 公司门户应用的更新。 在 2018 年 11 月，我们发布了一次公司门户更新，其中包括后端开关，以便为 Google 从现有通知平台更改为 Google 的 Firebase 云消息传递 (FCM) 做好准备。 随着 Google 停用其现有通知平台并迁移到 FCM，最终用户需要将他们的公司门户应用至少更新到 2018 年 11 月版本，以便继续与 Google Play 商店通信。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
我们的遥测显示，你的设备的公司门户版本低于 5.0.4269.0。 如果未安装该版本或更高版本的公司门户应用，那么，由 IT 专业人员发起的设备操作（如擦除、重置密码）、可用和所需的应用安装以及证书注册可能无法按预期方式工作。 如果设备是在 Intune 中注册的 MDM，可以通过依次进入“客户端应用”、“发现的应用”查看公司门户版本和用户。 选择早期版本的公司门户应用，可以查看哪些最终用户的设备尚未更新公司门户应用。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
要求尚未更新的 Android 设备的最终用户通过 Google Play 更新公司门户应用。 如果某个用户未自动更新公司门户应用，请通知支持人员。 有关 Google FCM 平台和更改的更多信息，请参阅“其他信息”  中的链接。

#### <a name="additional-information"></a>其他信息
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-full-screen-experience-coming-to-intune---4593669--"></a>Intune 即将推出新的全屏幕体验 <!--4593669-->
我们将在 Azure 门户中向 Intune 推出更新的创建和编辑 UI 体验。 此新体验将使用压缩在一个边栏选项卡中的向导样式格式简化现有工作流。 此更新将消除“边栏选项卡扩展”或需要向下钻取到深度边栏选项卡体验的任何创建和编辑流。 创建工作流也将更新为包含分配（应用分配除外）。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
接下来的几个月里，将同时在 portal.azure.com 和 devicemanagement.microsoft.com 推出 Intune 全屏幕体验。 此 UI 更新不会影响现有策略和配置文件的功能，但你将看到一个稍经修改的工作流。 例如，创建新策略时，你将能够将某些分配设置为此流的一部分，而不是在创建策略后执行此操作。 有关控制台中新体验的屏幕截图，请参阅其他信息中的博客文章
** 。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我能够针对此更改做什么准备？
不需要执行任何操作，但可以考虑在必要时更新 IT 专业人员指南。 当在 Azure 门户上向 Intune 中的各种边栏选项卡推出此体验时，我们将更新文档。

#### <a name="additional-information"></a>其他信息 
https://aka.ms/intune_fullscreen

### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-an-upcoming-release---4911065---"></a>更改计划：适用于 Android 的 Intune App SDK 和应用保护策略将在即将发布的版本中支持 Android 5.0 及更高版本 <!--4911065 -->
Intune 将在即将发布的版本中支持 Android 5.x (Lollipop) 及更高版本。 使用最新的 Intune App SDK 更新所有包装好的应用，并更新设备。

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

### <a name="intune-plan-for-change-nearing-end-of-support-for-windows-7---3042987---"></a>Intune 更改计划：即将停止支持 Windows 7<!-- 3042987 -->
如我们在 2018 年 9 月发布的 MC148476 和在 2019 年 3 月再次发布的 MC176794 所述，将于 2020 年 1 月 14 日结束对 Windows 7 的延长支持。 到那时，Intune 将停止对运行 Windows 7 的设备的支持，因此我们可以将投资集中在支持较新的技术和提供出色的最终用户体验上。 在该日期后，有助于保护你的 Windows 7 PC 的技术协助和自动更新将不能再通过 Intune 获得。 Microsoft 强烈建议你在 2020 年 1 月之前迁移到 Windows 10，以避免所需服务或支持不再可用的情况。 有关 Windows 支持生命周期的详细信息，请参阅[此处](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
你收到此消息是因为你当前正在使用旧版 Intune PC 软件代理来管理 Windows 7 PC。 由于 Windows 7 延长支持结束之前的剩余时间已不到一年，我们强烈建议你的组织尽快开始升级到 Windows 10。  

PC 管理功能直接内置于 Windows 10 操作系统中，你不再需要安装客户端代理，例如适用于 Windows 7 的 Intune 软件客户端。 从 Windows 8.1 开始，Microsoft 使用移动设备管理 (MDM) 体系结构来预配、配置、更新和管理 Windows PC。 设置 Intune 后，可以通过 MDM 通道[将 Windows 10 PC 注册到 Intune](..\windows-enroll.md)，从而简化 Windows 注册。 建议使用此“无代理”MDM 管理解决方案来管理 Windows 10 PC。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
我们鼓励你的组织立即考虑此操作计划：

- 在 2020 年 1 月 14 日之前计划并将 Windows 7 队伍升级到 Windows 10。
- 浏览 [Windows 10 部署支持](https://docs.microsoft.com/windows/deployment/)，详细了解如何将现有的一系列 Windows 7 PC 升级到 Windows 10。
- 查看帮助实现 Microsoft 应用程序兼容性保证的 FastTrack 所提供的[桌面应用保证](https://www.microsoft.com/fasttrack/microsoft-365/desktop-app-assure?rtc=1)。
- 将现有的旧版 Intune 软件客户端托管设备转换为 Microsoft 推荐的解决方案，以便使用 MDM 管理来管理 Windows 10。 在 Azure 门户中使用 Intune 的 MDM 管理注册所有新的 Windows 10 PC。

有关详细信息，请参阅[此处的博客文章](https://aka.ms/Windows7_Intune)。
