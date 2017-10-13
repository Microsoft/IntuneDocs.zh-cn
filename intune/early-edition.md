---
title: "早期版本"
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 09/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f2e11a7fbe226932206f6946ef0603307e76c69c
ms.sourcegitcommit: 4184db38d1a9a223e680bcb4c9b732f7069bf510
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2017
---
# <a name="the-early-edition-for-microsoft-intune---september-2017"></a>Microsoft Intune 明日新闻 - 2017 年 9 月

早期版本提供了一份即将发布的 Microsoft Intune 版本中将出现的功能列表。 此信息的提供具有条件限制，并且会不断变化。 请不要与公司外部共享此信息。 此处列出的某些功能有无法按期发布的风险并可能推迟到以后的版本。 正在以试验模式（外部测试）测试其他功能，以确保它们可立即供客户使用。 如果有任何问题或顾虑，请与 Microsoft 产品组联系人联系。

本页将定期更新。 返回查看其他更新。

> [!Note]
>下面的更改依据 Intune 开发。 有关新的混合功能的详细信息，请查看[混合新增功能页](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。

<!--

## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
   
-->

  

## <a name="intune-in-the-azure-portal"></a>Azure 门户中的 Intune


### <a name="google-play-protect-support-on-android----908720----"></a>Android 上的 Google Play Protect 支持 <!-- 908720  -->  
随着 Android Oreo 的发布，Google 引入了一系列名为 Google Play Protect 的安全功能，以便用户和组织可以运行安全的应用和 Android 映像。 Intune 将支持 Google Play Protect 功能，包括 SafetyNet 远程认证。  管理员可以设置符合性策略要求，要求配置和正常运行 Google Play Protect。 “SafetyNet 设备认证”设置要求设备连接到 Google 服务，以验证设备是否正常运行且未遭到入侵。 管理员还可以对 Android for Work 设置配置文件设置，以要求 Google Play 服务对已安装的应用进行验证。  如果设备不符合 Google Play Protect 要求，条件访问可能会禁止用户访问公司资源。 

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time-----1333292---"></a>禁止 Android 设备用户更改设备日期和时间 <!-- 1333292 -->
将可以使用 [Android 自定义设备策略](custom-settings-android.md)，禁止 Android 设备用户更改设备日期和时间。
为此，请将 URI ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange 设置为 TRUE，配置 Android 自定义策略，再将策略分配给相应组。

### <a name="view-app-protection-policy-assignments-for-troubleshooting-----1475003---"></a>查看应用保护策略分配以进行故障排除 <!--  1475003 -->
在即将发布的这一版本中，“应用保护策略”选项将添加到“疑难解答”边栏选项卡上的“分配”下拉列表中。 现在可以选择应用保护策略，查看分配给选定用户的应用保护策略。

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>创建特定区域 Apple App Store 专属的 iOS 应用 <!-- 1281692 -->
将可以在创建 Apple App Store 管理的应用期间，指定国家/地区区域设置。

> [!NOTE]  
> 目前，只能创建美国应用商店专属的 Apple App Store 管理的应用。

### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>选择 Apple 国家/地区应用商店以同步 VPP 应用 <!-- 1332311 -->  
将可以在上传 VPP 令牌时，配置 Volume Purchase Program (VPP) 国家/地区应用商店。 Intune 将同步指定 VPP 国家/地区应用商店中所有区域设置对应的 VPP 应用。

> [!NOTE]  
> 目前，Intune 只会同步 VPP 国家/地区应用商店中，区域设置与创建 Intune 租户所用的 Intune 区域设置一致的 VPP 应用。

###  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>更新 iOS VPP 用户和设备许可的应用 <!-- 1305564 -->  
将可以把 iOS VPP 令牌配置为，更新针对此令牌通过 Intune 服务购买的所有应用。 Intune 将在应用商店内检测 VPP 应用更新，并在设备进行检测时自动将这些更新推送到设备中。

### <a name="ios-11-support----1428975---"></a>iOS 11 支持 <!-- 1428975 -->
Intune 将支持 Apple 发布的 iOS 11。

### <a name="new-settings-for-windows-10-team-device-restriction-profile------1308838----"></a>Windows 10 协同版设备限制配置文件的新设置 <!--- 1308838  -->
在此版本中，我们将添加 Windows 10 协同版设备限制配置文件的许多新设置，以帮助用户控制 Surface Hub 设备。
有关此配置文件的详细信息，请参阅 [Windows 10 协同版设备限制设置](device-restrictions-windows-10-teams.md)。

### <a name="support-for-windows-10-edition-upgrade-policy------903672-1119689---"></a>支持 Windows 10 版本升级策略 <!-- 903672, 1119689 -->  
将可以创建 Windows 10 版本升级策略，以将 Windows 10 设备升级到 Windows 10 教育版、Windows 10 教育版 N、Windows 10 专业版、Windows 10 专业版 N、Windows 10 专业教育版和 Windows 10 专业教育版 N。有关 Windows 10 版本升级的详细信息，请参阅[如何配置 Windows 10 版本升级](edition-upgrade-configure-windows-10.md)。

### <a name="review-policy-compliance-for-windows-10-update-rings----1352223---"></a>检查 Windows 10 更新通道的策略符合性 <!-- 1352223 -->  
将可以在“软件更新” > “每个更新通道部署状态”中检查 Windows 10 更新通道的策略报告。 策略报告包括已配置的更新通道的部署状态。 

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>Windows 10 公司门户应用被添加到 Windows 信息保护允许策略 <!-- 677129 -->  
Windows 10 公司门户应用将更新为支持 Windows 信息保护 (WIP)。 此类应用将可以被添加到 WIP 允许策略。 此更改生效后，便无需再将应用添加到“豁免”列表。 

### <a name="remote-support-for-windows-and-windows-mobile-devices-----1070473---"></a>Windows 和 Windows Mobile 设备的远程支持 <!-- 1070473 -->    
Intune 将可以使用 [TeamViewer](https://www.teamviewer.com) 软件（单独购买），为运行 Windows 和 Windows Mobile 设备的用户提供远程协助。

### <a name="scan-devices-with-windows-defender----1280988--1280990-----"></a>使用 Windows Defender 扫描设备 <!-- 1280988  1280990   -->
将可以在受管理 Windows 10 设备上，使用 Windows Defender 防病毒运行“快速扫描”、“完全扫描”和“更新签名”。 在设备的“概览”边栏选项卡上，选择要在设备上运行的操作。 在命令发送到设备之前，系统会提示用户确认操作。 

**快速扫描**：快速扫描可扫描恶意软件注册启动的位置，如注册表项和已知的 Windows 启动文件夹。 快速扫描平均需要五分钟才能完成。 “始终开启实时保护”设置可在用户打开、关闭文件、转到文件夹时扫描文件。与此设置配合使用，快速扫描可有助于保护系统或内核免遭潜在恶意软件威胁。 扫描完成时，用户可以在设备上查看扫描结果。 

**完全扫描**：完全扫描非常适合受恶意软件威胁的设备，以确定是否需要更彻底地清理任何停用组件，并且十分适用于运行按需扫描。 完全扫描可能需要一小时才能完成。 扫描完成时，用户可以在设备上查看扫描结果。 

**更新签名**：更新签名命令可更新 Windows Defender 防病毒恶意软件定义和签名。 这有助于确保 Windows Defender 防病毒可以有效地检测恶意软件。 此功能仅适用于挂起设备 Internet 连接的 Windows 10 设备。 

### <a name="bitlocker-device-configuration----1397398---"></a>BitLocker 设备配置 <!-- 1397398 -->  
在“Windows 加密”>“基本设置”中，将可以使用新的“针对其他磁盘加密的警告”设置，从而禁止对用户设备上可能使用的其他磁盘加密显示[警告提示](https://docs.microsoft.com/en-us/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption)。  警告提示要求先征得最终用户同意，然后才能在设备上设置 BitLocker，并且会在最终用户确认之前禁止设置 BitLocker。  这一新设置可以禁用最终用户警告。

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>适用于 Windows 8.1 和 Windows Phone 8.1 的公司门户将进入持续性模式 <!--1428681-->
自 2017 年 10 月起，适用于 Windows 8.1 和 Windows Phone 8.1 的公司门户应用将进入持续性模式。 也就是说，这些平台将继续支持应用和现有方案（如注册和符合性）。 将仍可以通过现有发布通道（如 Microsoft 应用商店）下载这些应用。 

一旦进入持续性模式，这些应用就只会收到关键安全更新程序。 对于这些应用，将不会发布其他任何更新或功能。 若要使用新功能，建议将设备更新到 Windows 10 或 Windows 10 移动版。 

###  <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>在 Android for Work 中，禁止在工作配置文件与个人配置文件之间进行复制粘贴 <!-- 1098994 -->   
在此版本中，将可以配置 Android for Work 工作配置文件，以禁止在工作应用与个人应用之间进行复制粘贴。 可以转到 Android for Work 平台的“设备限制”配置文件，在“工作配置文件设置”中找到这一新设置。

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Android 公司门户应用与工作配置文件配合使用时的新行为 <!---1485783--->
使用工作配置文件注册 Android for Work 设备时，在设备上执行管理任务的正是工作配置文件中的公司门户应用。 除非在个人配置文件中使用已启用 MAM 的应用，否则 Android 公司门户应用不再提供任何服务。 为了改善工作配置文件体验，Intune 将在成功使用工作配置文件注册后自动隐藏个人公司门户应用。

随时都可以在 [Play Store 中搜索公司门户](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)并点击“启用”，从而在个人配置文件中启用 Android 公司门户应用。

### <a name="intune-mam--outlook-for-android-add-ins-----1450688---"></a>Intune MAM 与 Android 版 Outlook 加载项 <!-- 1450688 -->
Office 团队将在几周内发布 Android 版 Outlook 加载项。 此加载项功能集已包含在 Windows、iOS、Web 和 Mac 版 Outlook 中。 由于加载项是通过 Exchange 管理，因此用户能够跨 Outlook 和非管理加载项应用复制和共享数据和邮件，除非 Exchange 管理员禁止访问加载项。 

若要管理用户对加载项的访问权限，请与 Exchange 管理员合作，共同确保 MAM 数据保护策略应用于加载项。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
如果 Exchange 策略已设置为禁止旁加载或安装加载项，后续不会进行读取。 MAM 策略将按预期应用。 不过，如果已设置 MAM 策略以限制在 Android 版 Outlook 中执行剪切、复制和粘贴操作，但未在 Exchange 中设置加载项策略，大家应知道，默认情况下，用户将可以在 Outlook 中安装加载项。 这些加载项可以访问邮件正文、主题和其他邮件属性。 可以让 Exchange 管理员删除“我的市场应用”和“我的自定义应用”角色，从而禁止最终用户安装加载项。 有关详细信息，请参阅下面共享的其他信息链接。

请注意，Exchange 中的设置更改仅适用于 Windows、iOS、Web、Mac 和移动版 Outlook。 

#### <a name="what-do-i-need-to-do"></a>我需要做什么？
请立即查看 Exchange 策略。 通知 IT 和支持人员。 与我们的支持团队联系，告知需要解决的任何特定问题或疑虑。 

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>用户设备关联实体集合被添加到 Intune 数据仓库数据模型 <!-- 1187917 -->
将可以使用能关联用户与设备实体集合的用户设备关联信息，生成报表和数据可视化效果。 可通过从“数据仓库 Intune”页检索到的 Power BI 文件 (PBIX)、通过 OData 终结点或通过开发自定义客户端，访问数据模型。


<!-- the following are present prior to 1709 -->

### <a name="actions-for-non-compliance----730266--"></a>针对不合规的操作<!--730266-->     
“针对不合规的操作”是合规性策略的新功能，允许在不合规的设备上执行操作。 可指定单个或多个操作，并指定这些操作必然会发生的时间段。 例如，可在设备变为不合规后，立即通过电子邮件通知该不合规设备的用户，或可在 3 天宽限期后，通过条件性访问阻止不合规设备访问公司资源。

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>列出使用较旧 iOS 版本的 iOS 设备的新报表   <!-- 1352223 -->
可在“软件更新”工作区中获取“过期 iOS 设备”报表。 在报表中，可以查看已应用 iOS 更新策略且具有可用更新的受监督 iOS 设备的列表。 可以查看每个设备的状态，了解该设备未自动更新的原因。 

### <a name="new-settings-for-windows-10-device-restriction-profile"></a>Windows 10 设备限制配置文件的新设置
<!--- 978575, 1308849, -->
我们将向 Windows Defender SmartScreen 类别中的 Windows 10 设备限制配置文件中添加新设置。

有关 Windows 10 设备限制配置文件的详细信息，请参阅 [Windows 10 和更高版本的设备限制设置]( device-restrictions-windows-10.md)。

### <a name="android-for-work-support-for-lookout----1087312---"></a>Lookout 的 Android for Work 支持<!-- 1087312 -->   
在使用 Lookout for Work 应用时，Lookout 的 Intune 连接器将支持 Android for Work 设备。 可以在容器内部或外部部署 Lookout 应用。

### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Intune 应用保护和 Citrix MDX 开发工具 <!-- 709185 -->
可以同时使用 Citrix XenMobile MDX 和 Microsoft Intune 来管理设备和应用。 通过使用此方法，可在使用 Citrix mVPN 技术的同时通过 Intune 应用保护策略管理应用。

能够查找包含适用于iOS 和 Android 的 App Wrapping Tool 和 Intune App SDK 的代码存储库，同时还能集成 Citrix MDX mVPN 技术。

### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium - 新移动威胁防御合作伙伴<!-- 954681 -->
能够根据 Zimperium 给出的风险评估，使用条件访问控制移动设备对公司资源的访问，Zimperium 是与 Microsoft Intune 集成的移动威胁防御解决方案。

#### <a name="how-integration-with-intune-works"></a>与 Intune 的集成是如何发挥作用的？
基于从运行 Zimperium 的设备收集的遥测评估风险。 可以基于通过 Intune 设备符合性策略启动的 Zimperium 风险评估配置 EMS 条件访问策略，从而根据检测到的威胁允许或阻止不符合要求的设备访问公司资源。

### <a name="new-azure-ad-conditional-access-policy-ui-link-from-intune-----1016201---"></a>Intune 中的新 Azure AD 条件访问策略用户界面链接 <!-- 1016201 -->
IT 管理员可以通过 Azure AD 工作负荷中的新条件访问策略设置基于应用的条件性策略。 位于 Azure Intune 应用保护部分的基于应用的条件访问策略只是暂时保持现状，未来将逐步强制实施。 Intune 工作负荷与 Azure AD 中的新条件访问策略用户界面存在便捷的链接。

### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>本地 Exchange 连接器高可用性支持 <!-- 676614 -->   
能够拥有用于本地 Exchange 连接器的多个客户端访问服务器 (CAS) 角色。 例如，如果主 CAS 失败，Exchange 连接器会收到一个用于回退到其他 CAS 的查询。 此功能可确保服务不中断。

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>适用于 Exchange 连接器的 System Center Operations Manager 管理包<!-- 885457 -->   
将会提供适用于 Exchange 连接器的 System Center Operations Manager 管理包帮助你分析 Exchange 连接器日志。 此管理包将在需要进行问题故障排除时为你提供监控 Intune 的多种方式。

### <a name="end-of-support-for-ios-80----1164477---"></a>停止对 iOS 8.0 的支持<!---1164477--->
适用于 iOS 的托管应用和公司门户应用需要使用 iOS 9.0 和更高版本才能访问公司资源。 今年 9 月之前不更新的设备将不再能够访问公司门户应用或这些应用。  

### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>停止对 Android 4.3 及更低版本的支持 <!---1171127, 1326920 --->
Android 托管的应用和公司门户应用需要使用 Android 4.4 和更高版本访问公司资源。 在 10 月初之前还未更新的设备将不再能够访问公司门户应用或这些应用。 截至 12 月，所有已注册的设备将在 12 月强制停用，从而导致无法访问公司资源。 如果使用应用保护策略而不使用 MDM，应用将不会收到更新，并且随着时间推移其体验质量将会降低。

### <a name="platform-support-reminder-windows-phone-81-mainstream-support-will-end-july-11-2017----1327781---"></a>平台支持提醒：Windows Phone 8.1 主流支持将于 2017 年 7 月 11 日结束 <!-- 1327781 -->  
2017 年 7 月 11 日，Windows Phone 8.1 平台的主流支持将迎来结束。 Windows 8.1 电脑支持不受影响。

不会对任何由 Intune 服务管理的 Windows Phone 8.1 设备产生即时影响。 注册的设备将继续工作，并且所有策略、配置和应用都将继续按预期方式工作。 请注意，对于 Intune 服务中的 Windows Phone 8.1 平台以及 Windows Phone 8.1 公司门户应用，不推出任何功能改进。

建议尽早将符合条件的 Windows Phone 8.1 设备升级到 Windows 10 移动版。 





## <a name="intune-apps"></a>Intune 应用

### <a name="search-improvements-to-the-company-portal-website---1331697--"></a>公司门户网站的搜索改进<!--1331697-->
我们正在改进应用搜索功能，首先从[公司门户网站](https://portal.manage.microsoft.com)开始。 除“名称”和“说明”字段外，现在还可按应用类别执行搜索。 结果默认按相关性呈降序排列。 

由于适用于 iOS 的公司门户应用中也包含公司门户网站，因此 iOS 用户也将收到此更改。 适用于 Android 和 Windows 的公司门户应用将在未来几个月中收到类似更新。 

我们仍在努力优化跟踪相关性的方式，因此请使用公司门户网站底部的“反馈”链接向我们反馈当前的运行状况。

### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>刷新操作被添加到 Windows 10 公司门户应用 <!--1132468-->
Windows 10 公司门户应用将支持用户通过请求刷新或在桌面设备上按 F5，刷新应用中的数据。


### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>现在可以在没有注册提示的情况下，安装可注册或不可注册的应用。 <!-- 1334712 -->
在 Android 公司门户应用中，可以在没有注册提示的情况下，安装可注册或不可注册的公司应用。

### <a name="ios-company-portal-display-large-icons----1454593---"></a>iOS 公司门户显示大图标 <!-- 1454593 -->
我们正在修复 iOS 公司门户应用磁贴中显示的图标存在的已知问题。 如果上传 120x120 像素或更大的应用图标，它们现在会显示在 [公司门户网站] (https://portal.manage.microsoft.com) 中，且 iOS 公司门户应用页会占据整个应用磁贴。

### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android------1396349---"></a>Android 公司门户应用的表述更容易理解 <!---1396349--->    
为了让最终用户能够更轻松地注册，Android 公司门户应用的注册流程已使用新文本进行了简化。 


<!-- the following are present prior to 1709 -->


### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>iOS 和 Android 的 Intune Managed Browser 支持<!---1374196--->
自 2017 年 10 月起，Android 版 Intune Managed Browser 应用将仅支持运行 Android 4.4 及更高版本的设备。 iOS 上的 Intune Managed Browser 应用将仅支持运行 iOS 9.0 及更高版本的设备。 早期版本的 Android 和 iOS 将能够继续使用 Managed Browser，但不能安装新版本的应用，并且可能无法访问所有应用功能。 建议将这些设备更新为受支持的操作系统版本。

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>允许最终用户无需进行注册便可访问适用于 Android 的公司门户应用 <!---1169910--->  
最终用户很快将无需注册其设备就能访问 Android 公司门户应用。 使用应用保护策略的组织中的最终用户在打开公司门户应用时将不再收到指示其注册设备的提示。 最终用户也将能够从公司门户安装应用而无需注册其设备。 

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>改进了用户达到允许注册的最大设备数时提示的错误消息 <!-- 1270370 -->
最终用户将不再看到普通错误消息，而将看到一条友好且可操作的错误消息：“注册设备数已达到 IT 管理员允许的最大数量。请删除已注册的设备，或者向 IT 管理员寻求帮助。”

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>通知最终用户可查看哪些 iOS 设备信息 <!--739894-->
我们将在 iOS 公司门户应用的“设备详细信息”屏幕上添加“所有权类型”。 这样，用户便可直接在 Intune 最终用户文档的此页中发现详细隐私信息。用户还将能在“关于”屏幕中找到此信息。

### <a name="apps-details-pages-display-new-information-for-android-devices---1287476--"></a>应用详细信息页显示 Android 设备的新信息 <!--1287476-->
Android 公司门户应用的应用详细信息页将显示 IT 管理员为该应用定义的应用类别。

### <a name="intune-mobile-application-management-mam-dialog-boxes-now-have-a-modern-interface----1199015---"></a>“Intune 移动应用管理”(MAM) 对话框现在具有现代界面 <!-- 1199015 -->
经过更新，“Intune 移动应用管理”(MAM) 对话框现已具有现代外观和体验。 对话框功能与以前相同。

在现代 Android 设备上， Intune 现在显示的错误或通知对话框也将呈现出更新的外观和体验。



## <a name="notices"></a>通知
### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 将要求更新应用传输安全<!--748318-->   
自 2017 年春季开始，Apple 宣布他们将强制对应用程序传输安全 (ATS) 实施特定要求。 使用 ATS 对所有通过 HTTPS 的应用通信实施更严格的安全措施。 此更改会影响使用 iOS 公司门户应用的 Intune 客户。 请查看 [Intune 支持博客](https://aka.ms/compportalats)，了解更多详细信息。

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>做好应对更改的计划：Intune 将更改 Intune 合作伙伴门户体验<!-- 1050016 -->
自 2017 年 5 月中旬起，我们将从 manage.microsoft.com 中删除 Intune 合作伙伴页面（从服务更新入手）。  

如果你是合作伙伴管理员，将无法再代表客户在 Intune 合作伙伴页面中查看内容和执行操作，而是需要在 Microsoft 的其他两个合作伙伴门户之一进行登录。

使用 [Microsoft 合作伙伴中心](https://partnercenter.microsoft.com/)和 [Microsoft Office 365 合作伙伴管理中心](https://portal.office.com/)，可以登录所管理的客户帐户。 作为合作伙伴，未来请使用其中一个网站管理客户。



### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。
