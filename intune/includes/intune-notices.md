---
title: 包含文件
description: 包含文件
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/19/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 7373ca24c1ae1f439096d9bedcb8e81979c95586
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74829079"
---
本文中的通知提供了重要信息，可以帮助你为未来的 Intune 更改和功能做好准备。

### <a name="updated-support-statement-for-adobe-acrobat-reader-for-intune-mobile-app--5746776--"></a>针对“Adobe Acrobat Reader for Intune”移动应用的更新支持声明<!--5746776-->
我们在 8 月底的 MC188653 上得知，Adobe Acrobat Reader for Intune 移动应用将于 2019 年 12 月 1 日到期，且 Adobe 计划在其主要的 Acrobat Reader 应用中支持 Intune 应用保护策略。 自那以后，我们收到客户反馈，我们需要提供更多的时间来继续允许 IT 管理员瞄准目标，并让最终用户开始使用 Adobe Acrobat Reader for Intune。 鉴于 Adobe Acrobat Reader for Intune 在最终用户设备上的高使用率及其在企业场景中的重要性，我们希望确保任何体验都能满足组织的应用保护需求。 

虽然由于 Acrobat Reader 移动应用支持应用保护策略并且已经集成了 Intune SDK，我们仍然建议在策略中面向一般的 Acrobat Reader 移动应用，但 Adobe Acrobat Reader for Intune 应用将继续得到支持至 2020 年 3 月 31 日。 

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
你收到此消息是因为我们的报告表明，贵组织中的一个或多个策略针对的是 Adobe Acrobat Reader for Intune 应用程序，并且/或者你可能已经收到了我们以前的 EOL 通信。 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
让最终用户和技术支持人员得知晓此更改。 可以使用[公司门户的支持信息功能](../apps/company-portal-app.md#support-information)来建立与 Intune 相关的问题通道。

#### <a name="additional-information"></a>其他信息
https://helpx.adobe.com/acrobat/kb/intune-app-end-of-life.html


### <a name="end-support-for-windows-phone-81--3544909--"></a>结束对 Windows Phone 8.1 的支持<!--3544909-->
Microsoft 对 Windows Phone 8.1 的主流支持于 2017 年 7 月结束，延期支持于 2019 年 6 月结束。 自 2017 年 10 月以来，针对 Windows Phone 8.1 的公司门户应用一直处于支持模式。 Microsoft Intune 将于 2020 年 2 月 20 日结束对 Windows Phone 8.1 的支持。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
2020 年 2 月 20 日之后，这些设备将不再收到任何安全更新，并且你将无法注册任何新设备。 现有的 Windows Phone 8.1 设备将保持注册状态（策略、应用和报告），但请注意，在此日期之后，将不再支持对现有注册设备的任何故障排除，因为许多组件（如第三方证书）已结束对该平台的支持。 Intune 将停止与 Intune 和 Windows Phone 8.1 的兼容性测试。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
你可以查看 Intune 报告，了解可能受影响的设备或用户。 转到“设备”>“所有设备”并按 OS 进行筛选。 你可以添加附加列，帮助确定你的组织中哪些人员的设备正在运行 Windows Phone 8.1。 要求你的最终用户将设备升级到受支持操作系统版本。

### <a name="update-your-intune-outlook-app-protection-policies-app--2576686--"></a>更新 Intune Outlook 应用保护策略 (APP)<!--2576686-->
如果在消息中心收到 MC195618，则可能需要采取措施。 正如 Microsoft 365 路线图功能 ID 56325 和 56326 中所分享的，Intune 和适用于 iOS 和 Android 的 Outlook 正在推出支持在邮件通知和日历提醒中限制敏感数据的功能。 由于这些改进，适用于 iOS 和 Android 的 Outlook 将删除对你当前用于管理通知的多个数据保护应用配置键的支持。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
尽管新功能尚未发布，但在发布时，以下应用配置键在适用于 iOS 和 Android 的 Outlook 中将不再工作：
- com.microsoft.outlook.Mail.NotificationsEnabled
- com.microsoft.outlook.Mail.NotificationsEnabled.UserChangeAllowed
- com.microsoft.outlook.Calendar.NotificationsEnabled
- com.microsoft.outlook.Calendar.NotificationsEnabled.UserChangeAllowed

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
建议将 Intune 应用保护策略数据保护设置“组织数据通知”设置为“阻止组织数据”，以便为此新功能做好准备。 从 2019 年 12 月 16 日开始，适用于 iOS 和 Android 的 Outlook 将服从“组织数据通知”数据保护设置，不再支持上述键。 配置此新设置将确保在不再支持上述配置键时敏感数据不会泄露。 此外，当数据保护设置“组织数据通知”设置为“阻止组织数据”且具有附加应用配置设置“日历通知”时，则 Outlook 会提供更多的粒度。 应用保护策略设置和此应用配置设置相组合可限制邮件通知中的敏感信息，同时在日历通知中公开敏感信息，使用户可以通过快速扫视通知或通知中心访问其会议。

#### <a name="additional-information"></a>其他信息
有关应用设置和 Outlook 设置的详细信息，请参阅：
- [Android 应用保护策略设置](../apps/app-protection-policy-settings-android.md)
- [iOS 应用保护策略设置](../apps/app-protection-policy-settings-ios.md)
- [部署 Outlook for iOS 和 Outlook for Android 应用配置设置](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)


### <a name="intune-plan-for-change-windows-10-version-1703-company-portal-moving-out-of-support--5026679--"></a>Intune 更改计划：Windows 10 版本 1703 公司门户即将停止支持<!--5026679-->
Windows 10 版本 1703（也称为 Windows 10 RS2）已于 2019 年 10 月 8 日停止提供针对企业版和教育版的服务。 自 2019 年 12 月 26 日开始，Intune 将终止对 RS2/RS1 的相应公司门户应用的支持。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
接下来，尽管我们会在 2019 年 12 月 26 日之前继续支持此版本的公司门户应用，但你将不会在特定版本的公司门户应用中看到新功能，包括根据需要向公司门户应用提供任何安全更新。 但是，由于 Windows 10 版本 1703 在停止提供服务后将不会收到任何安全更新，因此，我们强烈建议将 Windows 设备更新为最新的 Windows 版本，并确保使用的是最新的公司门户应用，以便继续获取新功能和其他功能。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
所要采取的步骤将取决于你配置环境的方式。 但一般情况下，应确定具有较旧操作系统版本的设备和/或设备上的公司门户，然后进行更新。 若要设置 Windows 10 更新通道，请登录到 Intune -> 软件更新 – Windows 10 更新通道。 公司门户的最新版本是版本 10.3.5601.0。 请指导用户从 Microsoft Store 获取该版本，以与最新版本保持同步。 此外，你还可以通过[适用于企业的 Microsoft Store](https://docs.microsoft.com/intune/windows-store-for-business) 使用 Intune 在 Windows 设备上安装最新版本。

#### <a name="additional-information"></a>其他信息
[使用 Microsoft Intune 手动添加 Windows 10 公司门户应用](https://docs.microsoft.com/intune/store-apps-company-portal-app)


### <a name="take-action-use-microsoft-edge-for-your-protected-intune-browser-experience--5728447--"></a>执行操作：使用 Microsoft Edge 获取受保护的 Intune 浏览器体验<!--5728447-->
正如我们在过去一年中一直分享的那样，Microsoft Edge 移动版支持与 Managed Browser 相同的一组管理功能，同时提供了更好的最终用户体验。 为了让 Microsoft Edge 提供强大的体验，我们将停用 Intune Managed Browser。 自 2020 年 1 月 27 日开始，Intune 将不再支持 Intune Managed Browser。  

#### <a name="how-does-this-affect-me"></a>这对我有何影响？ 
自 2020 年 2 月 1 日开始，Google Play 商店或 iOS 应用商店中将不再提供 Intune Managed Browser。 届时，虽然新用户将无法下载 Intune Managed Browser 应用，但你仍可以将新的应用保护策略定向到 Intune Managed Browser。 此外，在 iOS 上，向下推送到已注册 MDM 设备的新 Web 剪辑将在 Microsoft Edge 中打开，而不是在 Intune Managed Browser 中打开。  

2020 年 3 月 31 日，Intune Managed Browser 将从 Azure 控制台中删除。 这意味着你将无法再为 Intune Managed Browser 创建新策略。 现有的 Intune Managed Browser 策略不会受到影响。 Intune Managed Browser 将在控制台中显示为无图标的 LOB 应用程序，但现有策略将仍显示为应用的定向策略。 届时，我们还会在“应用程序保护策略”的“数据保护”部分中删除将 Web 内容重定向到 Intune Managed Browser 的选项。  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？ 
若要确保从 Intune Managed Browser 平稳过渡到 Microsoft Edge，我们建议你主动执行以下步骤： 

1. 使用应用保护策略（也称为 MAM）和应用配置设置，将 Microsoft Edge 定向到 iOS 和 Android。 将这些现有策略定向到 Microsoft Edge，即可对 Microsoft Edge 重复使用 Intune Managed Browser 策略。  
2. 确保环境中所有受 MAM 保护的应用都将应用保护策略设置“限制与其他应用的 Web 内容传输”设置为“策略托管浏览器”。 
3. 通过将托管应用配置设置“com.microsoft.intune.useEdge”设置为 true 来定位所有受 MAM 保护的应用。 从下个月的 1911 版本开始，只需配置“限制与其他应用的 Web 内容传输”设置，以在应用保护策略的“数据保护”部分中选中“Microsoft Edge”，即可完成步骤 2 和步骤 3。 

即将支持 iOS 和 Android 上的 Web 剪辑。 发布此支持后，你需要重定向预先存在的 Web 剪辑，以确保它们在 Microsoft Edge 中而不是在 Managed Browser 中打开。 

#### <a name="additional-information"></a>其他信息
如需了解更多信息，请访问有关[将 Microsoft Edge 与应用保护策略结合使用](../apps/manage-microsoft-edge.md)的文档，或查看我们的[支持博客文章](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Use-Microsoft-Edge-for-your-Protected-Intune-Browser-Experience/ba-p/1004269)。

### <a name="plan-for-change-updated-experience-when-enrolling-android-enterprise-dedicated-devices-in-intune--5198878--"></a>更改计划：在 Intune 中注册 Android Enterprise 专用设备时更新了体验<!--5198878-->
对于 Intune 11 月版或 1911 版，我们将添加对 SCEP 设备证书部署到 Android Enterprise 专用设备的支持，以便启用对 Wi-Fi 配置文件的基于证书的访问。 此更改还涉及在注册 Android Enterprise 专用设备时对流的一些次要更改。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
如果在你的环境中管理 Android Enterprise 专用设备，你会开始看到一些更改将于 11 月推出。

- 对于新的 Android Enterprise 专用设备注册：最终用户会在注册过程中在设备上看到一组不同的步骤。 注册仍将以当前的方式开始（使用 QR、NFC、零接触或设备标识符），但在 11 月服务发布后，必须执行应用安装步骤。
- 对于注册为专用设备的现有 Android 设备：Intune 将开始于 11 月初在设备上自动安装 Microsoft Intune 应用。 用户无需采取任何操作。 应用将在设备上自动下载并安装。 

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我能够针对此更改做什么准备？
你应该计划更新最终用户指南，并使支持人员知道此更改。 单击“其他信息”以了解更多详细信息和屏幕截图。 开始推出此更改时，我们将更新新增功能页面。

#### <a name="additional-information"></a>其他信息
[https://aka.ms/Dedicated_devices_enrollment](https://aka.ms/Dedicated_devices_enrollment)

### <a name="end-of-support-for-legacy-pc-management"></a>停止支持旧版 PC 管理

将于 2020 年 10 月 15 日停止支持旧版 PC 管理。 请将设备升级到 Windows 10，并将它们重新注册为“移动设备管理”(MDM) 设备，以便继续由 Intune 托管它们。

[了解详细信息](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator"></a>减少对 Android 设备管理员的支持 
Android 设备管理员（有时称为“旧版”Android 管理，随 Android 2.2 发布）是一种管理 Android 设备的方法。 不过，[Android Enterprise](../enrollment/connect-intune-android-enterprise.md)（随 Android 5.0 发布）现在提供改进的管理功能。 为了实现更现代化、更丰富、更安全的设备管理，Google 正在减少新 Android 版本中对设备管理员的支持。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
由于 Google 的这些变化，Intune 用户将受到以下几个方面的影响：  
- Intune 将只能在 2020 年第二季度之前为运行 Android 10 及更高版本的设备管理员管理的 Android 设备提供完全支持。 在此之后运行 Android 10 或更高版本的设备管理员管理的设备将无法再进行完全管理。 特别是，受影响的设备将不会收到新的密码要求。
    - Samsung Knox 设备在此期间不受影响，因为通过 Intune 与 Knox 平台的集成提供了扩展支持。 这使你有更多时间来规划过渡弃用设备管理员管理。    
- 设备管理员管理的仍在低于 Android 10 的 Android 版本上运行的 Android 设备将不会受到影响，可以继续完全由设备管理员进行管理。    
- 对于运行 Android 10 及更高版本的所有设备，Google 限制了设备管理员管理代理（如公司门户）访问设备标识符信息的能力。 在设备更新到 Android 10 或更高版本后，此限制将影响以下 Intune 功能：  
    - VPN 的网络访问控制将不再有效。   
    - 使用 IMEI 或序列号将设备识别为公司拥有的设备将不会自动将设备标记为公司拥有的设备。  
    - 在 Intune 中，IMEI 和序列号将不再对 IT 管理员可见。 
        > [!NOTE]
        > 这只会影响 Android 10 及更高版本上设备管理员管理的设备，并且不会影响作为 Android Enterprise 管理的设备。 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
为避免在即将到来的 2020 年第三季度出现功能降低的情况，建议采取如下操作：
- 不要将新设备加入设备管理员管理中。
- 如果希望设备接收到 Android 10 的更新，请将其从设备管理员管理迁移到 Android Enterprise 管理和/或应用保护策略。

#### <a name="additional-information"></a>其他信息
- [从设备管理员迁移到 Android Enterprise 的 Google 指南](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [弃用设备管理员 API 计划的 Google 文档](https://developers.google.com/android/work/device-admin-deprecation)

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


