---
title: "Microsoft Intune 中前几个月的新增功能"
titlesuffix: 
description: "查看 Intune 新增功能页中早期的公告"
keywords: 
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7ba6262c1126a421f2e2ca0e5085796c11df8d9a
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2018
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>Microsoft Intune 中前几个月的新增功能

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="october-2017"></a>2017 年 10 月

### <a name="ios-and-android-line-of-business-app-version-number-is-visible----1380712---"></a>iOS 和 Android 业务线应用版本号是可见的 <!-- 1380712 -->

现在，Intune 中的应用会显示 iOS 和 Android 业务线应用的版本号。 版本号会在 Azure 门户、应用列表和应用概述边栏选项卡中显示。 最终用户可在公司门户应用和 Web 门户中查看应用的版本号。

__完整版本号__ 完整版本号标识应用的特定版本。 该号码显示为“版本号(内部版本号)”。 例如：2.2(2.2.17560800)

完整版本号包含两个部分：

 - **版本**  
   版本号是应用的发行版号（可人工读取）。 最终用户使用版本号确定应用的不同发行版。

 - **内部版本号**  
    内部版本号是一个内部号码，可在应用检测中使用，并可用于以编程方式管理应用。 内部版本号是指应用的迭代，应用可引用代码中的更改。

要详细了解版本号以及如何开发业务线应用，请参阅 [Microsoft Intune App SDK 入门](app-sdk-get-started.md#line-of-business-app-version-numbers)。

### <a name="device-and-app-management-integration----677972---"></a>设备和应用管理集成<!-- 677972 -->   
由于 Intune 移动设备管理 (MDM) 和移动应用管理 (MAM) 均可通过 Azure 门户访问，因此 Intune 已开始集成有关应用程序和设备管理的 IT 管理员体验。 这些更改旨在简化设备和应用的管理体验。

有关 MDM 和 MAM 更改的详细信息，请参阅 [Intune 支持团队博客](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/)中的发布内容。

### <a name="new-enrollment-alerts-for-apple-devices----1471790---"></a>Apple 设备的新注册警报 <!-- 1471790 -->
注册的概述页将介绍一些有关 Apple 设备管理的警报，这些警报适用于 IT 管理员。 如果存在下列情况，“概述”页上就会显示警报：Apple MDM 推送消息称证书将过期或已过期；设备注册计划令牌将过期或已过期；设备注册计划中存在未分配的设备。

### <a name="support-token-replacement-for-app-configuration-without-device-enrollment----1080364---"></a>支持使用令牌替换应用配置（无需设备注册）<!-- 1080364 -->

对于未注册设备上的应用，可在应用配置期间使用令牌获取动态值。 有关详细信息，请参阅[为受管理应用添加应用配置策略（无需设备注册）](app-configuration-policies-managed-app.md)。

### <a name="updates-to-the-company-portal-app-for-windows-10---1299474--"></a>更新适用于 Windows 10 的公司门户应用<!--1299474-->
适用于 Windows 10 的公司门户应用的“设置”页面已更新，以使设置和预期的用户操作在所有设置中更加一致。 其更新也旨在匹配其他 Windows 应用的布局。 你可以在[应用 UI 中的新增功能](whats-new-app-ui.md)页找到更新之前/之后的图像。

### <a name="inform-end-users-what-device-information-can-be-seen-for-windows-10-devices---1337920--"></a>告知最终用户可以查看 Windows 10 设备的哪些设备信息 <!--1337920-->
我们已在适用于 Windows 10 的公司门户应用的“设备详细信息”屏幕上添加了“所有权类型”。 这样，用户便可直接在 Intune 最终用户文档的此页中发现详细隐私信息。用户还将在“关于”屏幕中找到此信息。

### <a name="feedback-prompts-for-the-company-portal-app-for-android---1165249--"></a>适用于 Android 的公司门户应用的反馈提示<!--1165249-->
适用于 Android 的公司门户应用现在可请求最终用户反馈。 将此反馈直接发送给 Microsoft，让最终用户有机会在公用 Google Play 商店中查看应用。 反馈不是必需的，很容易消除，所以用户可以继续使用该应用。

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>利用 Android 版公司门户应用帮助用户自助 <!-- 1573324, 1573150, 1558616, 1564878 -->

适用于 Android 的公司门户应用为最终用户添加了说明，帮助他们了解并自行解决（如果可能）新用例。
- 如果最终用户达到可允许添加的设备数量上限，将会引导他们转到 [Azure Active Directory 门户](https://account.activedirectory.windowsazure.com/r/#/profile)，以便删除设备。
- 为最终用户提供要遵守的步骤以帮助他们[修复 Samsung Knox 设备上的激活错误](https://go.microsoft.com/fwlink/?linkid=859718)或者[关闭节能模式](/intune-user-help/power-saving-mode-android)。 如果这些解决方案均无法解决问题，请查看[将日志提交给 Microsoft](/intune-user-help/send-logs-to-microsoft-android) 的相关说明。

### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>适用于 Android 设备的新“解决”操作<!-- 1583480 -->

Android 版公司门户应用在“更新设备设置”页中引入了“解决”操作。 选择此选项会将最终用户直接转至导致其设备不符合的设置。 Android 版公司门户应用当前为以下设置提供此操作：[设备密码](/intune-user-help/set-your-pin-or-password-android)、[USB 调试](/intune-user-help/you-need-to-turn-off-usb-debugging-android)和[未知源](/intune-user-help/you-need-to-turn-off-unknown-sources-android)。

### <a name="device-setup-progress-indicator-in-android-company-portal----1565657---"></a>适用于 Android 的公司门户中的设备设置进度指示器<!-- 1565657 -->
适用于 Android 的公司门户应用在用户注册设备时显示设备设置进度指示器。 该指示器将显示最新状态，从“设置设备...”，再“注册设备...”，接着“完成设备注册...”，然后“完成设备设置...”。

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>iOS 版公司门户上基于证书的身份验证支持<!--1029830-->
我们在 iOS 版公司门户应用中添加了对基于证书的身份验证 (CBA) 的支持。 使用 CBA 的用户可输入其用户名，然后点击“使用证书登录”链接。 Android 和 Windows 版公司门户应用中已实现了对 CBA 的支持。 有关详细信息，请参阅[登录公司门户应用](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal)页。

### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>现在可以在没有注册提示的情况下，安装可注册或不可注册的应用。 <!-- 1334712 -->

在 Android 公司门户应用中，现可在没有注册提示的情况下，安装通过/不通过注册而获取的公司应用。

### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune-----747617----"></a>Microsoft Intune 中的 Windows AutoPilot Deployment 计划支持<!-- 747617  -->
现在可将 Microsoft Intune 与 Windows AutoPilot Deployment 计划配合使用，授权用户在不劳烦 IT 的情况下设置其企业设备。 可以自定义全新体验 (OOBE)，引导用户将设备加入 Azure AD 并在 Intune 中注册。 在配合使用 Microsoft Intune 与 Windows AutoPilot 时，完全无需部署、维护和管理操作系统映像。 有关详细信息，请参阅 [Enroll Windows devices using Windows AutoPilot Deployment Program](https://docs.microsoft.com/intune/enrollment-autopilot)（使用 Windows AutoPilot Deployment 计划注册 Windows 设备）。

### <a name="quick-start-for-device-enrollment-----1425655---"></a>设备注册快速入门  <!-- 1425655 --> 
快速入门当前在设备注册中可用，此外还提供了用于管理平台和配置注册过程的参考表格。 对每个项目的简短说明和包含分步说明的文档链接提供了有用的文章，可帮助简化入门过程。

### <a name="device-categorization----1427491---"></a>设备分类 <!-- 1427491 -->
“设备”>“概述”边栏选项卡中的已注册设备平台图可以按平台（包括 Android、iOS、macOS、Windows 和 Windows Mobile）整理设备。  运行其他操作系统的设备将被分到“其他”组。  这包括由 Blackberry 和 NOKIA 等厂家生产的设备。  

要了解租户中的哪些设备会受到影响，请选择“管理”>“所有设备”，然后使用“筛选器”限制“操作系统”字段。

### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium - 新移动威胁防御合作伙伴<!-- 954681 -->  
可根据 Zimperium 进行的风险评估，使用条件访问控制移动设备对公司资源的访问，Zimperium 是与 Microsoft Intune 集成的移动威胁防御解决方案。

#### <a name="how-integration-with-intune-works"></a>与 Intune 集成的工作原理
基于从运行 Zimperium 的设备收集的遥测评估风险。 可以基于通过 Intune 设备符合性策略启动的 Zimperium 风险评估配置 EMS 条件访问策略，从而根据检测到的威胁允许或阻止不符合要求的设备访问公司资源。

### <a name="new-settings-for-windows-10-device-restriction-profile------978575-1308849---"></a>Windows 10 设备限制配置文件的新设置  <!--- 978575, 1308849, -->  
我们将向 Windows Defender SmartScreen 类别中的 Windows 10 设备限制配置文件中添加新设置。

有关 Windows 10 设备限制配置文件的详细信息，请参阅 [Windows 10 和更高版本的设备限制设置]( device-restrictions-windows-10.md)。

### <a name="remote-support-for-windows-and-windows-mobile-devices------1070473---"></a>Windows 和 Windows Mobile 设备的远程支持   <!-- 1070473 -->  
Intune 现在可以使用 [TeamViewer](https://www.teamviewer.com) 软件（单独购买），为运行 Windows 和 Windows Mobile 设备的用户提供远程协助。

### <a name="scan-devices-with-windows-defender----1280988--1280990-----"></a>使用 Windows Defender 扫描设备 <!-- 1280988  1280990   -->
现可在托管的 Windows 10 设备上，使用 Windows Defender 防病毒运行“快速扫描”、“完全扫描”和“更新签名”。 在设备的“概览”边栏选项卡上，选择要在设备上运行的操作。 在命令发送到设备之前，系统会提示用户确认操作。 

**快速扫描**：快速扫描可扫描恶意软件注册启动的位置，如注册表项和已知的 Windows 启动文件夹。 快速扫描平均需要五分钟才能完成。 “始终开启实时保护”设置可在用户打开、关闭文件、转到文件夹时扫描文件。与此设置配合使用，快速扫描可有助于保护系统或内核免遭潜在恶意软件威胁。 扫描完成时，用户可以在设备上查看扫描结果。 

**完全扫描**：完全扫描非常适合受恶意软件威胁的设备，以确定是否需要更彻底地清理任何停用组件，并且十分适用于运行按需扫描。 完全扫描可能需要一小时才能完成。 扫描完成时，用户可以在设备上查看扫描结果。 

**更新签名**：更新签名命令可更新 Windows Defender 防病毒恶意软件定义和签名。 这有助于确保 Windows Defender 防病毒可以有效地检测恶意软件。 此功能仅适用于挂起设备 Internet 连接的 Windows 10 设备。 

### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal-----1400455---"></a>已将“启用/禁用”按钮从 Intune Azure 门户的 Intune 证书颁发机构页中删除  <!-- 1400455 -->
 我们正在删除在 Intune 上设置证书连接器这一额外步骤。 当前，需要下载证书连接器，然后在 Intune 控制台中启用它。 但如果在 Intune 控制台中禁用它，该连接器仍将持续颁发证书。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
从 10 月开始，Azure 门户的证书颁发机构页中将不再显示“启用/禁用”按钮。 连接器功能保持不变。 证书仍将部署到在 Intune 中注册的设备。 可以继续下载并安装证书连接器。 若要停止颁发证书，当前需卸载证书连接器，而不是禁用它。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
如果目前已禁用证书连接器，则应该卸载它。

### <a name="new-settings-for-windows-10-team-device-restriction-profile-------1308838---"></a>Windows 10 协同版设备限制配置文件的新设置   <!--- 1308838 -->
在此版本中，我们向 Windows 10 协同版设备限制配置文件添加了许多新设置，以帮助用户控制 Surface Hub 设备。

有关此配置文件的详细信息，请参阅 [Windows 10 协同版设备限制设置](device-restrictions-windows-10-teams.md)。

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time-----1333292---"></a>禁止 Android 设备用户更改设备日期和时间 <!-- 1333292 -->
将可以使用 [Android 自定义设备策略](custom-settings-android.md)，禁止 Android 设备用户更改设备日期和时间。

为此，请将 URI ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange 设置为 TRUE，配置 Android 自定义策略，再将策略分配给相应组。

### <a name="bitlocker-device-configuration----1397398---"></a>BitLocker 设备配置 <!-- 1397398 -->
在“Windows 加密”>“基本设置”中，现可以使用新的“针对其他磁盘加密的警告”设置，从而禁止对用户设备上可能使用的其他磁盘加密显示[警告提示](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption)。  警告提示要求先征得最终用户同意，然后才能在设备上设置 BitLocker，并且会在最终用户确认之前禁止设置 BitLocker。  这一新设置可以禁用最终用户警告。


### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant----800882---"></a>适用于业务应用的 Volume Purchase Program 现在将同步到你的 Intune 租户 <!-- 800882 -->  
第三方开发人员可以私下将应用分发给适用于 iTunes Connect 中指定的业务成员的经授权 Volume Purchase Program。 这些面向业务成员的 VPP 可以登录 Volume Purchase Program App Store 并购买应用。

此版本中，最终用户购买的适用于业务应用的 VPP 将开始同步到其 Intune 租户中。

### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>选择 Apple 国家/地区应用商店以同步 VPP 应用 <!-- 1332311 -->  
将可以在上传 VPP 令牌时，配置 Volume Purchase Program (VPP) 国家/地区应用商店。 Intune 将同步指定 VPP 国家/地区应用商店中所有区域设置对应的 VPP 应用。

> [!NOTE]  
> 目前，Intune 只会同步 VPP 国家/地区应用商店中，区域设置与创建 Intune 租户所用的 Intune 区域设置一致的 VPP 应用。


### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>在 Android for Work 中，禁止在工作配置文件与个人配置文件之间进行复制粘贴 <!-- 1098994 -->
在此版本中，将可以配置 Android for Work 工作配置文件，以禁止在工作应用与个人应用之间进行复制粘贴。 可以转到 Android for Work 平台的“设备限制”配置文件，在“工作配置文件设置”中找到这一新设置。

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>创建特定区域 Apple App Store 专属的 iOS 应用 <!-- 1281692 -->
将可以在创建 Apple App Store 管理的应用期间，指定国家/地区区域设置。

> [!Note]  
> 目前，只能创建美国应用商店中具备的 Apple App Store 托管应用。

###  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>更新 iOS VPP 用户和设备许可的应用 <!-- 1305564 -->  
将可以把 iOS VPP 令牌配置为，更新针对此令牌通过 Intune 服务购买的所有应用。 Intune 将在应用商店内检测 VPP 应用更新，并在设备进行检测时自动将这些更新推送到设备中。

有关设置 VPP 令牌和启用自动更新的步骤，请参阅 [如何使用 Microsoft Intune 管理通过批量采购计划购买的 iOS 应用] (/intune/vpp-apps-ios)。


### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>用户设备关联实体集合被添加到 Intune 数据仓库数据模型 <!-- 1187917 -->
现在可使用用户设备关联信息（该信息将用户和设备实体集合相关联）生成报表和数据可视化效果。 可通过从“数据仓库 Intune”页检索到的 Power BI 文件 (PBIX)、通过 OData 终结点或通过开发自定义客户端，访问数据模型。

### <a name="review-policy-compliance-for-windows-10-update-rings----1067886---"></a>检查 Windows 10 更新通道的策略符合性 <!-- 1067886 -->
将可以在“软件更新”>“每个更新通道的部署状态”中检查 Windows 10 更新通道的策略报告。 策略报告包括已配置的更新通道的部署状态。 

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>列出使用较旧 iOS 版本的 iOS 设备的新报表   <!-- 1352223 -->
可在“软件更新”工作区中获取“过期 iOS 设备”报告。 在报表中，可以查看已应用 iOS 更新策略且具有可用更新的受监督 iOS 设备的列表。 可以查看每个设备的状态，了解该设备未自动更新的原因。 

### <a name="view-app-protection-policy-assignments-for-troubleshooting-----1475003---"></a>查看应用保护策略分配以进行故障排除 <!--  1475003 -->
在即将发布的这一版本中，“应用保护策略”选项将添加到“疑难解答”边栏选项卡上的“分配”下拉列表中。 现在可以选择应用保护策略，查看分配给选定用户的应用保护策略。



### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>对公司门户中的设备设置工作流的改进<!--1490692-->
我们改进了适用于 Android 的公司门户应用中的设备设置工作流。 语言更贴近你公司的用语习惯，在可能的情况下我们还对屏幕进行了合并。 可以在[应用 UI 的新增功能](whats-new-app-ui.md#week-of-october-2-2017)页中查看这些更改。

### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>改进了与请求访问 Android 设备上的联系人相关的指南<!--1484985-->

适用于 Android 的公司门户应用需要最终用户接受“联系人”权限。 如果最终用户拒绝授予此访问权限，现在他们将看到应用内通知，提醒他们授予此权限以实现条件访问。 

### <a name="secure-startup-remediation-for-android---1490712--"></a>面向 Android 的安全启动修正<!--1490712-->

使用 Android 设备的最终用户将能够点击公司门户应用中的不合规原因。 在可能的情况下，此操作会使用户直接转到“设置”应用中的适当位置，以修复问题。 

### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo---1475932--"></a>向最终用户额外发送有关 Android Oreo 公司门户应用的推送通知 <!--1475932-->

最终用户可以看到其他通知，其中指明了 Android Oreo 公司门户应用何时执行后台任务，如从 Intune 服务检索策略。 这进一步提高了透明度，可方便最终用户了解公司门户应用何时在其设备上执行管理任务。 这是 Android Oreo 公司门户应用的全部[公司门户 UI 优化](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune)中的一部分。 

Android Oreo 中启用的新 UI 元素有进一步的优化。  最终用户将看到附加通知，指示他们公司门户何时执行从 Intune 服务中检索策略等后台任务。  最终用户可以更加清楚地了解公司门户何时在设备上执行管理任务。

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Android 公司门户应用与工作配置文件配合使用时的新行为 <!-- 1485783 -->

使用工作配置文件注册 Android for Work 设备时，在设备上执行管理任务的正是工作配置文件中的公司门户应用。 

除非在个人配置文件中使用已启用 MAM 的应用，否则 Android 公司门户应用不再提供任何服务。 为了改善工作配置文件体验，Intune 将在成功使用工作配置文件注册后自动隐藏个人公司门户应用。

随时都可以在 [Play Store 中搜索公司门户](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)并点击“启用”，从而在个人配置文件中启用 Android 公司门户应用。

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>适用于 Windows 8.1 和 Windows Phone 8.1 的公司门户将进入持续性模式 <!--1428681-->

自 2017 年 10 月起，适用于 Windows 8.1 和 Windows Phone 8.1 的公司门户应用将进入持续性模式。 也就是说，这些平台将继续支持应用和现有方案（如注册和符合性）。 将仍可以通过现有发布通道（如 Microsoft 应用商店）下载这些应用。 

一旦进入持续性模式，这些应用仅可收到重要安全更新程序。 对于这些应用，将不会发布其他任何更新或功能。 若要使用新功能，建议将设备更新到 Windows 10 或 Windows 10 移动版。 


### <a name="block-unsupported-samsung-knox-device-enrollment-----1490695---"></a>阻止不受支持的 Samsung Knox 设备注册<!-- 1490695 -->

公司门户应用仅尝试注册受支持的 Samsung Knox 设备。 为了避免出现阻止 MDM 注册的 Knox 激活错误，仅在 [Samsung 发布的设备列表](https://www.samsungknox.com/knox-supported-devices/knox-workspace)中有相应设备时，才尝试执行设备注册。 Samsung 设备的一些型号支持 Knox，而另一些型号则不支持 Knox。 购买并部署前，请与设备经销商确认 Knox 兼容性。 有关已验证设备的完整列表，可以参阅 [Android 和 Samsung Knox Standard 策略设置](/intune/supported-devices-browsers.md#intune-supported-devices)。

### <a name="end-of-support-for-android-43-and-lower----1171126-1326920---"></a>停止对 Android 4.3 及更低版本的支持 <!-- 1171126, 1326920 -->
Android 托管的应用和公司门户应用需要使用 Android 4.4 和更高版本访问公司资源。 截至 12 月，所有注册的设备都将在 12 月内被强制停用，进而将无法再访问公司资源。 如果使用应用保护策略而不使用 MDM，应用将不会收到更新，并且随着时间推移其体验质量将会降低。

### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices---1165314--"></a>告知最终用户可在注册设备上查看哪些设备信息<!--1165314-->
我们将在所有公司门户应用的“设备详细信息”屏幕上添加“所有权类型”。 这样，用户便可直接在[公司可看到哪些信息？](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune)文章中发现详细隐私信息。 近期将在所有公司门户应用中推出此更新。 我们在 [9 月](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017)宣布了面向 iOS 的此项更新。

## <a name="september-2017"></a>2017 年 9 月

### <a name="intune-supports-ios-11---1428975--"></a>Intune 支持 iOS 11<!--1428975-->
Intune 支持 iOS 11。 此信息之前已在 [Intune 支持博客](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/)中发布。

### <a name="end-of-support-for-ios-80----1164477---"></a>停止对 iOS 8.0 的支持<!-- 1164477 -->
适用于 iOS 的托管应用和公司门户应用需要使用 iOS 9.0 和更高版本才能访问公司资源。 今年 9 月之前不更新的设备将不再能够访问公司门户应用或这些应用。 

### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>刷新操作被添加到 Windows 10 公司门户应用 <!--1132468-->
使用 Windows 10 版公司门户应用，用户可以通过下拉刷新或在桌面上按 F5 来刷新应用中的数据。

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>通知最终用户可查看哪些 iOS 设备信息 <!--739894-->

我们已在适用于 iOS 的公司门户应用的“设备详细信息”屏幕上添加“所有权类型”。 这样，用户可以直接从此页在 Intune 最终用户文档中找到隐私的相关详情。用户还将能在“关于”屏幕中找到此信息。

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>允许最终用户无需进行注册便可访问适用于 Android 的公司门户应用 <!---1169910--->

最终用户很快将无需注册其设备就能访问 Android 公司门户应用。 使用应用保护策略的组织中的最终用户在打开公司门户应用时将不再收到指示其注册设备的提示。 最终用户也将能够从公司门户安装应用而无需注册其设备。 


### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Android 公司门户应用的表述更容易理解 <!---1396349--->  

为了让最终用户能够更轻松地注册，Android 公司门户应用的注册流程已使用新文本进行了简化。 若有自定义注册文档，不妨进行更新，以反映新屏幕。 可以在 [Intune 最终用户应用的 UI 更新](whats-new-app-ui.md#week-of-september-11-2017)页面找到示例图片。

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>Windows 10 公司门户应用被添加到 Windows 信息保护允许策略 <!-- 677129 -->

Windows 10 公司门户应用已更新为支持 Windows 信息保护 (WIP)。 可以将应用添加到 WIP 允许策略。 此更改生效后，便无需再将应用添加到“豁免”列表。


## <a name="august-2017"></a>2017 年 8 月

### <a name="improvements-to-device-overview----1404453---"></a>设备概述改进<!-- 1404453 -->  
设备概述改进现在显示已注册设备，但不包含由 Exchange ActiveSync 管理的设备。 Exchange ActiveSync 设备没有与已注册设备相同的管理选项。 要在 Azure 门户的 Intune 中查看已注册设备数和各平台的已注册设备数，请转到“设备” > “概述”。

### <a name="improvements-to-device-inventory-collected-by-intune"></a>Intune 所收集设备清单的改进
<!-- 961134, 1104426, 1281327, 1333543 -->
此版本中，我们对由你管理的设备收集的清单信息做出了以下改进：
 
-   对于 Android 设备，现在可向设备清单添加一列，显示每个设备的最新修补程序级别。 将“安全修补程序级别”列添加到设备列表可查看此项。
-   筛选设备视图时，现在可按设备注册日期筛选设备。 例如，可仅显示于指定日期后注册的设备。
-   我们已对“上次签入日期”项所用的筛选器做出了一些改进。
-   在设备列表中，现在可显示公司拥有设备的电话号码。
此外，还可使用筛选器窗格按电话号码搜索设备。
 
有关设备清单的详细信息，请参阅[如何查看 Intune 设备清单](device-inventory.md)。

### <a name="conditional-access-support-for-macos-devices"></a>对 macOS 设备的条件访问支持 
<!-- 720172 -->
现在可设置一个条件访问策略，要求 Mac 设备注册 Intune 且符合其设备符合性策略。 例如，用户可以下载适用于 macOS 的 Intune 公司门户应用并向 Intune 注册其 Mac 设备。 Intune 会评估 Mac 设备是否符合 PIN、加密、OS 版本和系统完整性等要求。

- 深入了解[对 macOS 设备的条件访问支持](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)。

### <a name="company-portal-app-for-macos-is-in-public-preview----1484796---"></a>适用于 macOS 的公司门户应用当前为公共预览版<!---1484796--->
适用于 macOS 的公司门户应用目前作为企业移动性 + 安全性中条件访问公共预览版的一部分提供。 此版本支持 macOS 10.11 及更高版本。 在 [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal) 获取该应用。 


### <a name="new-device-restriction-settings-for-windows-10"></a>适用于 Windows 10 的 Intune 新设备限制设置    
<!--1063965, 1308850  -->
在此版本中，我们为 [Windows 10 设备限制配置文件](/intune/device-restrictions-windows-10)添加了新设置，类别如下：

-   Windows Defender SmartScreen
-   App Store

### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>更新至 Windows 10 终结点保护设备配置文件以应用 BitLocker 设置
<!--1459533 -->    
此版本中，我们已对 BitLocker 设置在 Windows 10 终结点保护设备配置文件中的作用方式做出如下改进：
 
在“Bitlocker OS 驱动器设置”下，对于“包含非兼容 TPM 芯片的 BitLocker”设置，选择“阻止”后，以前这会导致实际上允许 BitLocker 的问题。 我们已修复此问题，在选中“阻止”后会阻止 BitLocker。
在“Bitlocker OS 驱动器设置”下，对于“基于证书的数据恢复代理”设置，现在可显式阻止基于证书的数据恢复代理。 但是，默认情况下允许此代理。
在“BitLocker 固定数据驱动器设置”下，对于“数据恢复代理”设置，现在可显式阻止数据恢复代理。
有关详细信息，请参阅[适用于 Windows 10 及更高版本的 Endpoint Protection 设置](endpoint-protection-windows-10.md)。


### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Android 公司门户用户和应用保护策略用户的新登录体验 <!-- 621669 -->
最终用户现在可以使用 Android 公司门户应用浏览应用、管理设备和查看 IT 联系人信息，而无需注册其 Android 设备。 此外，如果最终用户已使用受 Intune 应用保护策略保护的应用，并启动了 Android 公司门户，最终用户不会再接收到注册设备的提示。

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Android 公司门户应用中用于切换电池优化的新设置 <!--1405990-->
适用于 Android 的公司门户应用的“设置”页添加了新设置，该设置可使用户轻松关闭公司门户和 Microsoft Authenticator 应用的电池优化。 设置中显示的应用名称将有所区别，具体取决于使用哪一应用管理工作帐户。 我们建议用户关闭电池优化，以提高用于同步电子邮件和数据的工作应用的性能。 

### <a name="multi-identity-support-for-onenote-for-ios---------1234281---"></a>对适用于 iOS 的 OneNote 的多身份支持<!-- 1234281 -->
最终用户现在可对适用于 iOS 的 Microsoft OneNote 使用不同的帐户（工作帐户和个人帐户）。 应用保护策略可应用于工作笔记本中的公司数据，而不会影响个人笔记本。 例如，可通过应用策略允许用户查找工作笔记本中的信息，但阻止用户将工作笔记本中的公司数据复制粘贴到个人笔记本。
 
- 详细了解支持 Intune 的[应用保护和多身份](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)的应用。

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>允许和阻止在 Samsung Knox Standard 设备上运行应用的新设置
<!-- 1305423 822899-->  
在此版本中，将添加新的[设备限制设置](device-restrictions-android.md)，以便用户能够指定以下应用列表：
 
- 允许用户安装的应用
- 已阻止用户运行的应用
- 设备上对用户隐藏的应用
 
可以通过 URL、包名称或从管理的应用列表中指定应用。

### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>Intune 中新 Azure AD 基于应用的条件访问策略用户界面链接
<!-- 1016201 -->
IT 管理员现可通过 Azure AD 工作负荷中的新条件访问策略 UI 设置基于应用的条件策略。 位于 Azure 门户中 Intune 应用保护部分的基于应用的条件访问策略只是暂时保持现状，未来将逐步强制实施。 此外，还有指向 Intune 工作负荷中新条件访问策略 UI 的便捷链接。

- 深入了解 [Azure AD 中基于应用的条件访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference)。



## <a name="july-2017"></a>2017 年 7 月

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version------1333256--1245463----"></a>按 OS 版本限制 Android 和 iOS 设备注册 <!--- 1333256,  1245463 --->
Intune 现在支持按操作系统版本号限制 iOS 和 Android 注册。 在“设备类型限制”下，IT 管理员现可设置平台配置，限制最低和最高操作系统值之间的注册。 Android 操作系统版本必须指定为 Major.Minor.Build.Rev，其中 Minor、Build 和 Rev 是可选的。 iOS 版本必须指定为 Major.Minor.Build，其中 Minor 和 Build 是可选的。 详细了解[设备注册限制](enrollment-restrictions-set.md)。

>[!NOTE]
>请勿通过 Apple 注册计划或 Apple Configurator 限制注册。

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment------1333272--1333275-1245709----"></a>限制 Android、iOS 和 macOS 设备的个人私有设备注册<!--- 1333272,  1333275, 1245709 --->
Intune 可通过将企业设备 IMEI 号码列入允许列表来限制个人设备注册。 Intune 现已使用设备序列号将此功能扩展到 iOS、Android 和 macOS。 通过将序列号上传到 Intune，可将设备预声明为企业所有的设备。 使用注册限制，可以阻止私人拥有的设备 (BYOD)，仅允许企业所有的设备进行注册。 详细了解[设备注册限制](enrollment-restrictions-set.md)。

若要导入序列号，请转至“设备注册” > “公司设备标识符”，单击“添加”，然后上传一个 CSV 文件（无标头，含两列，分别是序列号和详细信息，如 IMEI 号）。  若要限制私人拥有的设备，请转到“设备注册” > “注册限制”。 在“设备类型限制”下，选择“默认”，然后选择“平台配置”。 可以针对 iOS、Android 和 macOS“允许”或“阻止”私人拥有的设备。 


### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>用于强制设备与 Intune 同步的新设备操作 <!-- 711369 -->
在此版本中，我们添加了一个新的设备操作，可强制所选设备立即通过 Intune 签入。 当设备签入时，该设备会立即收到已分配给自己的任何挂起的操作或策略。  此操作可帮助立即验证和对已分配的策略进行故障排除，而无需等待下一个安排的签入。
有关详细信息，请参阅[同步设备](device-sync.md)

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>强制受监视的 iOS 设备自动安装可用的最新软件更新 <!-- 777100 -->
软件更新工作区推出了一项新策略，可在该工作区中强制受监视的 iOS 设备自动安装可用的最新软件更新。 有关详细信息，请参阅[配置 iOS 更新策略](/intune/software-updates-ios)

### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner-----954651-1172027---"></a>Check Point SandBlast Mobile - 新移动威胁防御伙伴<!-- 954651, 1172027 -->
可根据 Check Point SandBlast Mobile 给出的风险评估，使用条件访问控制移动设备对公司资源的访问，Check Point SandBlast Mobile 是与 Microsoft Intune 集成的移动威胁防御解决方案。

#### <a name="how-integration-with-intune-works"></a>与 Intune 的集成是如何发挥作用的？
基于从运行 Check Point SandBlast Mobile 的设备收集的遥测评估风险。 可基于通过 Intune 设备符合性策略启用的 Check Point SandBlast Mobile 风险评估配置 EMS 条件访问策略。 根据检测到的威胁，可允许或阻止不符合设备访问企业资源。


### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business----748101---"></a>将应用部署为在适用于企业的 Microsoft 应用商店中可用<!-- 748101 -->
通过此版本，管理员现可将适用于企业的 Microsoft 应用商店分配为可用。 设置为可用时，最终用户可安装来自公司门户应用或网站的应用，而无需重定向到 Microsoft 应用商店。

### <a name="ui-updates-to-the-company-portal-website---1313244-part-1--"></a>公司门户网站的用户界面更新 <!--1313244 part 1-->
我们对[公司门户网站](https://portal.manage.microsoft.com)的用户界面进行了几项更新，目的是增强最终用户体验。

- __对应用磁贴的改进__：应用图标现在显示时将具有基于图标主导颜色（如果可检测到）自动生成的背景色。 适用时，此背景会替代以前应用磁贴上显示的灰色边框。

    在即将发布的版本中，公司门户网站会尽可能显示大图标。 建议 IT 管理员使用像素大小不低于 120 x120 的高分辨率图标发布应用。 

- __导航更改__：导航栏项已移至左上角的汉堡菜单。 已删除“类别”页面。 用户现在可在浏览时按类别筛选内容。

- __对精选应用的更新__：我们在网站中添加了一个专用页面，用户可在其中浏览精选的应用，还可以对主页的“精选”部分做出一些用户界面调整。

### <a name="ibooks-support-for-the-company-portal-website---1231841--"></a>针对公司门户网站的 iBooks 支持<!--1231841-->
我们已向公司门户网站添加了一个专用页面，允许用户浏览和下载 iBooks。 


### <a name="additional-help-desk-troubleshooting-details------applies-to-1263399-1326964-1341642----"></a>有关支持人员故障排除的其他详细信息 <!---  Applies to 1263399, 1326964, 1341642 --->
Intune 更新了故障排除的显示内容，并添加了提供给管理人员和支持人员的信息。 现在用户可以看到一个“分配”表，表中按组成员身份汇总了针对用户的所有分配。 此列表包括：
- 移动应用
- 相容性策略
- 配置文件
 
此外，“设备”表格现包括“Azure AD 联接类型”和“Azure AD 符合性”列。 有关详细信息，请参阅[帮助用户解决问题](help-desk-operators.md)。



### <a name="intune-data-warehouse-public-preview"></a>Intune 数据仓库（公共预览版）
Intune 数据仓库每天对数据进行采样，提供租户的历史视图。 可使用 Power BI 文件 (PBIX) 访问数据，该文件是一个 OData 链接，可与许多分析工具兼容或与 REST API 交互。 有关详细信息，请参阅[使用 Intune 数据仓库](reports-nav-create-intune-reports.md)。


### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>适用于 Windows 10 公司门户应用的浅色和深色模式<!---676547--->
最终用户将能够为 Windows 10 公司门户应用自定义颜色模式。 用户能够在公司门户应用的“设置”部分进行更改。 更改将在用户重启应用后显示。 对于 Windows 10 版本 1607 及更高版本，应用模式将默认为系统设置。 对于 Windows 10 版本 1511 及更早版本，应用模式将默认为浅色模式。

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>让最终用户能够在 Windows 10 公司门户应用中标记其设备组<!---807046-->
最终用户现在能够选择其设备所属的组，方法是直接从 Windows 10 公司门户应用中标记该组。



## <a name="june-2017"></a>2017 年 6 月

### <a name="new-role-based-administration-access-for-intune-admins------1099990---"></a>面向 Intune 管理员的全新基于角色的管理访问权限   <!-- 1099990 -->  
将添加新的条件性访问管理员角色，以查看、创建、修改和删除 Azure AD 条件性访问策略。 以前，只有全局管理员和安全管理员具有此权限。 可以为 Intune 管理员授予此角色权限，以便他们有权访问条件性访问策略。


### <a name="tag-corporate-owned-devices-with-serial-number----1215070---"></a>用序列号标记公司拥有的设备 <!-- 1215070 -->  
Intune 现支持上传 iOS、macOS 和 Android 序列号作为公司设备的标识符。 此时，你将不能使用序列号来阻止个人设备进行注册，因为在注册过程中未验证序列号。 在不久的将来将推出按序列号阻止个人设备。


### <a name="new-remote-actions-for-ios-devices----854689---"></a>适用于 iOS 设备的新远程操作 <!-- 854689 -->
在此版本中，我们增加了两个适用于托管 Apple 课堂应用的共享 iPad 设备的新远程设备操作：

-   [注销当前用户](device-logout-user.md) - 注销所选 iOS 设备上的当前用户。
-   [删除用户](device-remove-user.md) - 从 iOS 设备上的本地缓存中删除所选用户。


### <a name="support-for-shared-ipads-with-the-ios-classroom-app----1044681---"></a>支持与 iOS Classroom 应用共享 iPad<!-- 1044681 -->
在此版本中，我们扩展了对管理 iOS Classroom 应用的支持，以便为使用托管 Apple ID 登录共享 iPad 的学生提供支持。


### <a name="changes-to-intune-built-in-apps----1332306---"></a>Intune 内置应用的更改 <!-- 1332306 -->
之前，Intune 包含了一些可供快速分配的内置应用。 根据你的反馈，我们已将此列表删除，你将不再看到内置应用。
但是，如果你已分配任何内置应用，则在应用列表中仍会看到这些应用。 你可以根据需要继续分配这些应用。
在后续版本中，我们计划提供一种方法，以便用户可以更轻松地在 Azure 门户中选择并分配内置应用。

### <a name="easier-installation-of-office-365-apps-----1121362----"></a>更简易的 Office 365 应用安装 <!--- 1121362 --->
通过使用新的 Office 365 专业增强版应用类型，可轻松将 Office 365 专业增强版 2016 应用分配到所管理的运行 Windows 10 最新版本的设备。 此外，如果拥有 Microsoft Project 和 Microsoft Visio 的许可证，还可以安装这两个应用。 所需的应用将被捆绑在一起，并且显示为 Intune 控制台的应用列表中的一个应用。
有关详细信息，请参阅[如何为 Windows 10 添加 Office 365 应用](apps-add-office365.md)。


### <a name="support-for-offline-apps-from-the-microsoft-store-for-business-----777044----"></a>支持适用于企业的 Microsoft 应用商店中的脱机应用<!--- 777044 --->
从适用于企业的 Microsoft 应用商店购买的离线应用现在将同步到 Azure 门户。 然后，便可以将这些应用部署到设备组或用户组。 脱机应用由 Intune 安装，而不是由应用商店安装。

### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps------1257019---"></a>Microsoft Teams 现在是已批准应用的基于应用的 CA 列表的一部分   <!-- 1257019 -->
对于适用于 Exchange 和 SharePoint Online 的基于应用的条件性访问策略，适用于 iOS 和 Android 的 Microsoft Teams 应用现属于已批准应用。 将能够利用基于应用的条件性访问通过 Azure 门户中的“Intune 应用保护”边栏选项卡为所有租户配置应用。

### <a name="managed-browser-and-app-proxy-integration----1287310---"></a>Managed Browser 和应用代理集成 <!-- 1287310 -->
Intune Managed Browser 现在可与 Azure AD 应用程序代理服务集成，以使用户甚至可在远程工作的时候访问内部网站。 浏览器用户只需像平时一样简单输入网站 URL，Managed Browser 便会通过应用代理 Web 网关路由请求。 有关详细信息，请参阅[使用 Managed Browser 策略管理 Internet 访问](app-configuration-managed-browser.md)。

### <a name="new-app-configuration-settings-for-the-intune-managed-browser----682951---"></a>Intune 托管浏览器的新应用配置设置 <!-- 682951 -->
在此版本中，我们为适用于 iOS 和 Android 的 Intune Managed Browser 应用添加了进一步配置。 现在你能够使用应用配置策略为浏览器配置默认主页和书签。
有关详细信息，请参阅[使用 Managed Browser 策略管理 Internet 访问](app-configuration-managed-browser.md)

### <a name="bitlocker-settings-for-windows-10-----951707---"></a>Windows 10 的 BitLocker 设置  <!-- 951707 -->
你现在可以使用新的 Intune 设备配置文件为 Windows 10 设备配置 BitLocker 设置。 例如，可以要求加密设备，还可以配置在打开 BitLocker 时应用的进一步设置。
有关详细信息，请参阅[适用于 Windows 10 及更高版本的 Endpoint Protection 设置](endpoint-protection-windows-10.md)。

### <a name="new-settings-for-windows-10-device-restriction-profile-----978527--978550-978569-1050031-1058611-----"></a>Windows 10 设备限制配置文件的新设置 <!--- 978527,  978550, 978569, 1050031, 1058611,  --->
在此版本中，我们为 Windows 10 设备限制配置文件添加了新设置，按照以下类别：

-  Windows Defender
-  手机网络和连接性
-  锁定屏幕体验
-  隐私
-  搜索
-  Windows 聚焦
-  Edge 浏览器

有关 Windows 10 设置的详细信息，请参阅 [Windows 10 及更高版本的设备限制设置](device-restrictions-windows-10.md)。


### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>适用于 Android 的公司门户应用现推出了全新的应用保护政策最终用户体验 <!--1305217-->
根据客户反馈，已修改适用于 Android 的公司门户应用，以便显示“访问公司内容”按钮。 其目的在于，使最终用户在仅需要访问支持应用保护策略（Intune 移动应用程序管理的一项功能）的应用时，无需完成不必要的注册过程。 可以在[应用 UI 的新增功能](whats-new-app-ui.md)页中查看这些更改。

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>新增可轻松删除公司门户的菜单操作 <!--1164569-->
根据用户反馈，适用于 Android 的公司门户应用新添加了一个菜单操作，可启动对设备中公司门户的删除。 此操作可从 Intune 管理中删除设备，这样用户就可以从设备中删除应用。 你可以在[应用 UI 中的新增功能](whats-new-app-ui.md)页和 [Android 最终用户文档](/intune-user-help/unenroll-your-device-from-intune-android)中查看这些更改。

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>与 Windows 10 创意者更新的应用同步改进 <!--676505-->
面向 Windows 10 的公司门户应用，现在将针对具有 Windows 10 创意者更新（版本 1703）的设备自动启动应用安装请求同步。 这将减少“正在挂起同步”状态下的应用安装停止问题。 此外，用户也能够从应用中手动启动同步。 可以在[应用 UI 的新增功能](whats-new-app-ui.md)页中查看这些更改。

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Windows 10 公司门户新的引导式体验<!---1058938--->
适用于 Windows 10 的公司门户应用将为尚未被标识或注册的设备提供引导式的 Intune 演练体验。 新体验提供了循序渐进的说明，引导用户完成 AAD 注册（条件性访问功能所需）和 MDM 注册（设备管理功能所需）。 引导式体验可从公司门户主页获取。 如果用户没有完成注册，仍可以继续使用应用，但可用功能受到限制。

此更新仅在运行 Windows 10 周年更新（内部版本 1607）或更高版本的设备上可见。 可以在[应用 UI 的新增功能](whats-new-app-ui.md)页中查看这些更改。


### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>Microsoft Intune 和条件性访问管理控制台正式发布
我们要宣布的是，新的 Azure 门户中 Intune 管理控制台和条件访问管理控制台正式发布。 通过 Azure 门户中 Intune，现在可以在一个位置上统一管理所有 Intune MAM 和 MDM 功能，并利用 Azure AD 分组和定位功能。 Azure 中的条件性访问可以跨 Azure AD 和 Intune 在一个统一的控制台中集成丰富的功能。 而且，从管理体验上来看，移动到 Azure 平台还可让你用上现代浏览器。

现在，Intune 在 Azure 门户 (portal.azure.com) 中显示，但不随附“预览”标签。

此时，现有客户无需进行任何操作，除非你已在消息中心收到过系列消息之一，请求你采取操作，以便我们迁移组。 你可能还收到过一则消息中心通知，通知你由于我方的 bug，迁移将花费更长时间。 我们正在继续努力工作，以迁移任何受影响的客户。

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>对适用于 iOS 的公司门户应用中应用磁贴的改进
我们更新了主页上的应用磁贴设计，以反映你为公司门户设置的品牌颜色。 有关详细信息，请参阅[应用 UI 中的新增功能](whats-new-app-ui.md)。

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>适用于 iOS 的公司门户应用现在可使用帐户选取器
当 iOS 设备用户登录公司门户时，如果他们使用其工作或学校帐户登录其他 Microsoft 应用，则会看到新的帐户选取器。 有关详细信息，请参阅[应用 UI 中的新增功能](whats-new-app-ui.md)。

## <a name="may-2017"></a>2017 年 5 月

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>更改 MDM 颁发机构，而无需取消注册托管设备 <!--1103950-->
你现在可以更改 MDM 颁发机构，而无需联系 Microsoft 支持部门，并且无需取消注册并重新注册现有的受管理设备。 在 Configuration Manager 控制台中，可以通过“设置”将 [MDM 颁发机构](/sccm/mdm/deploy-use/change-mdm-authority)从“Configuration Manager (混合)”更改为“Microsoft Intune (独立)”，反之亦然。


### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>改进了 Samsung Knox 启动 PIN 通知 <!--1087143-->
如果最终用户需要在 Samsung Knox 设备上设置启动 PIN 以符合加密要求，点击所看到的通知后将会转到“设置”应用中的确切位置。  以前，该通知会将最终用户转到密码更改屏幕。

### <a name="device-enrollment"></a>设备注册

#### <a name="apple-school-manager-asm-support-with-shared-ipad----748864-770395--"></a>共享 iPad 的 Apple School Manager (ASM) 支持<!-- 748864, 770395-->

Intune 现在支持使用 Apple School Manager (ASM) 来替换 Apple 设备注册计划，从而提供 iOS 设备开箱注册体验。 需要执行 ASM 载入才能将 Classroom 应用用于共享 iPad，并且需要执行此操作才会允许通过 Microsoft 学校数据同步 (SDS) 将数据从 ASM 同步到 Azure Active Directory。 有关详细信息，请参阅[通过 Apple School Manager 进行 iOS 设备注册](apple-school-manager-set-up-ios.md)。

> [!NOTE]
> 配置与课堂应用配合使用的共享 iPad 将需要在 Azure 中进行 iOS 教育版配置，这一功能尚未提供。  此功能将很快添加。

### <a name="device-management"></a>设备管理

#### <a name="provide-remote-assistance-to-android-devices-using-teamviewer----675418---"></a>使用 TeamViewer 为 Android 设备提供远程协助 <!-- 675418 -->

Intune 现在可使用 [TeamViewer](https://www.teamviewer.com) 软件（另行购买）为运行 Android 设备的用户提供远程协助。 有关详细信息，请参阅[向 Intune 托管的 Android 设备提供远程协助](device-profile-android-teamviewer.md)。

### <a name="app-management"></a>应用管理

#### <a name="new-app-protection-policies-conditions-for-mam----679864---"></a>MAM 的新应用保护策略条件 <!-- 679864 -->

你现在可以为没有注册用户的 MAM 设置强制执行以下策略的要求：

- 最低应用程序版本
- 最低操作系统版本
- 目标应用程序的最低 Intune APP SDK 版本（仅 iOS）

Android 和 iOS 上均提供此功能。 Intune 支持对 OS 平台版本、应用程序版本和 Intune APP SDK 的最低版本强制要求。 在 iOS 上，已集成 SDK 的应用程序还可在 SDK 级别设置最低版本强制要求。 如果上述三种不同级别中均未满足应用保护策略中的最低要求，用户将无法访问目标应用程序。 此时，用户可以删除其帐户（对于多重身份标识的应用程序）、关闭应用程序，或更新其 OS 或应用程序版本。

你还可以通过配置其他设置来提供建议进行 OS 或应用程序升级的非阻止型通知。 可以关闭此通知，并且应用程序可供正常使用。

有关详细信息，请参阅 [iOS 应用保护策略设置](app-protection-policy-settings-ios.md)和 [Android 应用保护策略设置](app-protection-policy-settings-android.md)。

#### <a name="configure-app-configurations-for-android-for-work----621621---"></a>配置适用于 Android for Work 的应用配置 <!-- 621621 -->
应用商店中的部分 Android 应用支持托管的配置选项，可让 IT 管理员控制应用在工作配置文件中的运行方式。 使用 Intune，现在可以查看应用支持的配置，并在 Azure 门户中使用配置设计器或 JSON 编辑器对它们进行配置。 有关详细信息，请参阅[使用针对 Android for Work 的应用配置](app-configuration-policies-use-android.md)。

#### <a name="new-app-configuration-capability-for-mam-without-enrollment----677969---"></a>针对没有注册的 MAM 的新应用注册功能 <!-- 677969 -->
你现在可以通过没有注册通道的 MAM 创建应用配置策略。 此功能相当于移动设备管理 (MDM) 应用配置中提供的应用配置策略。 有关使用没有注册的 MAM 的应用配置示例，请参阅[使用 Microsoft Intune 的 Managed Browser 策略管理 Internet 访问](app-configuration-managed-browser.md)。

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser----682960---"></a>为 Managed Browser 配置允许和阻止的 URL 列表 <!-- 682960 -->
你现在可以使用 Azure 门户中的应用配置设置为 Intune Managed Browser 配置允许和阻止的域和 URL 列表。 无论是在受管还是不受管的设备上使用它，都可以配置这些设置。 有关详细信息，请参阅[使用 Microsoft Intune 的 Managed Browser 策略管理 Internet 访问](app-configuration-managed-browser.md)。

#### <a name="app-protection-policy-helpdesk-view----1069473---"></a>应用保护策略支持人员视图 <!-- 1069473 -->
IT 支持人员用户现在可以在“疑难解答”边栏选项卡中查看用户许可证状态和已分配给用户的应用保护策略应用的状态。 有关详细信息，请参阅[疑难解答](./help-desk-operators.md)。

### <a name="device-configuration"></a>设备配置

#### <a name="control-website-visits-on-ios-devices----723832---"></a>控制 iOS 设备上的网站访问 <!-- 723832 -->
你现在可以使用以下两种方法之一控制 iOS 设备的用户可以访问的网站：

- 使用 Apple 内置的 Web 内容筛选器添加允许和阻止的 URL。

- 只允许 Safari 浏览器访问指定的网站。 将在 Safari 中为你指定的每个站点创建书签。

有关详细信息，请参阅[适用于 iOS 设备的 Web 内容筛选器设置](web-content-filter-settings-ios.md)。

#### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>预配置 Android for Work 应用的设备权限 <!-- 621614 -->
对于已部署到 Android for Work 设备工作配置文件的应用，你现在可以针对各个应用配置权限状态。  默认情况下，要求位置或设备摄像头访问权限等设备权限的 Android 应用将提示用户接受或拒绝权限。  例如，如果应用要使用设备的麦克风，则将提示最终用户授予该应用使用麦克风的权限。 通过此功能，可让你代表最终用户定义权限。  你可以将权限配置为 a) 无需通知用户即自动拒绝；b) 无需通知用户即自动批准，或 c) 提示用户接受或拒绝。 有关详细信息，请参阅 [Microsoft Intune 中的 Android for Work 设备限制设置](device-restrictions-android-for-work.md)。

#### <a name="define-app-specific-pin-for-android-for-work-devices----728976-1102534---"></a>为 Android for Work 设备定义特定于应用的 PIN <!-- 728976, 1102534 -->
具有作为 Android for Work 设备管理的工作配置文件的 Android 7.0 及更高版本的设备，可让管理员定义仅适用于工作配置文件中应用于各应用的密码策略。  选项包括：

- 定义仅设备范围的密码策略 - 这是用户解锁整个设备时必须使用的密码。
- 仅定义工作配置文件密码策略 - 只要打开工作配置文件中的任何应用，系统均会提示用户输入密码。
- 同时定义设备和工作配置文件策略 - IT 管理员可以选择同时以不同的长度定义设备密码策略和工作配置文件密码策略（例如，使用四位数的 PIN 来解锁设备，使用六位数的 PIN 来打开任意工作应用）。

有关详细信息，请参阅 [Microsoft Intune 中的 Android for Work 设备限制设置](device-restrictions-android-for-work.md)。

> [!NOTE]
> 此选项仅适用于 Android 7.0 及更高版本。  默认情况下，最终用户可以使用两个单独定义的 PIN，或者他们可以选择将两个已定义的 PIN 合并为二者中较强大的一个 PIN。

#### <a name="new-settings-for-windows-10-devices----978585---"></a>适用于 Windows 10 设备的新设置 <!-- 978585 -->
我们已添加新的 [Windows 设备限制设置](device-restrictions-windows-10.md)，可控制无线显示、设备发现、任务切换和 SIM 卡错误消息等功能。

#### <a name="updates-to-certificate-configuration----918991-and-823198---"></a>证书配置更新 <!-- 918991 and 823198 -->
创建 SCEP 证书配置文件时，对于“使用者名称格式”，可以使用适用于 iOS、 Android 和 Windows 设备的“自定义”选项。 在本次更新之前，“自定义”字段仅适用于 iOS 设备。 有关详细信息，请参阅[如何创建 SCEP 证书配置文件] (certificates-scep-configure.md#how-to-create-a-scep-certificate-profile)。

创建 PKCS 证书配置文件时，对于“使用者可选名称”，可以选择“自定义 Azure AD 属性”。 当选择“自定义 Azure AD 属性”时，将出现“部门”选项。 有关详细信息，请参阅[如何创建 PKCS 证书配置文件](certficates-pfx-configure.md#create-a-device-configuration-profile)。

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode----662059---"></a>配置多个当 Android 设备处于展台模式时可以运行的应用 <!-- 662059 -->
当 Android 设备处于展台模式时，你之前仅能配置一个允许运行的应用。 现在，你可以使用应用 ID、应用商店 URL，或通过选择一个已经管理的 Android 应用配置多个应用。 有关详细信息，请参阅[展台模式设置](device-restrictions-android.md#kiosk)。



## <a name="april-2017"></a>2017 年 4 月

### <a name="support-for-managing-the-apple-classroom-app"></a>支持管理 Apple Classroom 应用
现在可以在 iPad 设备上管理 iOS Classroom 应用。 使用正确的班级和学生数据设置教师 iPad 上的 Classroom 应用，然后配置已注册到某个班级的学生 iPad，方便使用此应用进行控制。
有关详细信息，请参阅[配置 iOS 教育设置](education-settings-configure-ios.md)。

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>支持 Android 应用的托管配置选项 <!-- 621621 -->
Play Store 中支持托管配置选项的 Android 应用现在可以由 Intune 进行配置。  通过此功能，IT 可查看应用支持的配置值列表，并提供优质的引导式 UI，以便配置这些值。

### <a name="new-android-policy-for-complex-pins----722069---"></a>复杂 PIN 的新 Android 策略 <!-- 722069 -->
现在可以在运行 Android 5.0 及更高版本的设备的 Android 设备配置文件中设置数字复杂度的必需[密码](device-restrictions-android.md#password)类型。  使用此设置可防止设备用户创建包含重复或连续数字（如 1111 或 1234）的 PIN。

### <a name="additional-support-for-android-for-work-devices"></a>对 Android for Work 设备的其他支持
- **管理密码及工作配置文件设置** <!-- 612808 -->

  通过新的 Android for Work 设备限制策略，现在可让你在管理的 Android for Work 设备上管理密码和工作配置文件设置。

- **允许在工作和个人配置文件之间共享数据** <!-- 1045102 -->

此 Android for Work 设备限制配置文件现在具有新的选项来帮助你配置工作和个人配置文件之间共享的数据。

- **限制工作和个人配置文件之间的复制和粘贴** <!-- 1046094 -->

  借助适用于 Android for Work 设备的新的自定义设备配置文件，现在可以限制是否允许在工作和个人应用之间进行复制和粘贴操作。

有关详细信息，请参阅 [Android for Work 的设备限制](device-restrictions-android-for-work.md)。

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>将 LOB 应用分配到 iOS 和 Android 设备 <!-- 1057568 -->
现在可以为用户或设备分配适用于 [iOS](lob-apps-ios.md)（.ipa 文件）和 [Android](lob-apps-android.md)（.apk 文件）的业务线 (LOB) 应用。


###  <a name="new-device-policies-for-ios----723774-723815-723826-723830---"></a>适用于 iOS 的新设备策略<!-- 723774, 723815, 723826, 723830 -->
- **主屏幕上的应用** - 控制用户在[其 iOS 设备的主屏幕](home-screen-settings-ios.md)上看到的应用。 此策略将更改主屏幕的布局，但不会部署任何应用。

- **与 AirPrint 设备的连接** - 控制 iOS 设备的最终用户可以连接到的 [AirPrint 设备](air-print-settings-ios-macos.md)（网络打印机）。

- **与 AirPlay 设备的连接** - 控制 iOS 设备的最终用户可以连接到的 [AirPlay 设备](airplay-settings-ios.md)（如 Apple TV）。

- **自定义锁屏界面消息** - 配置用户将在其 iOS 设备的锁屏界面上看到的自定义消息（替换默认的锁屏界面消息）。 有关详细信息，请参阅[激活 iOS 设备上的丢失模式](device-lost-mode.md)

### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>限制 iOS 应用的推送通知 <!-- 723767 -->
在 Intune 设备限制配置文件中，现在可以为 iOS 设备配置以下[通知设置](app-notification-settings-ios.md)：

- 完全打开或关闭指定应用的通知。
- 在通知中心中打开或关闭指定应用的通知。
- 指定警报类型：“无”、“横幅”或“提醒”。
- 指定是否允许此应用的徽章。
- 指定是否允许通知声音。

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>配置 iOS 应用以单一应用模式自主运行 <!-- 737837 -->
可以使用 Intune 设备配置文件配置 iOS 设备，以[自主单一应用模式](device-restrictions-ios.md#autonomous-single-app-mode-supervised-only)运行指定应用。 配置此模式并运行应用时，将锁定设备，因此该设备只能运行该应用。 举个例子，当你配置一个允许用户在设备上进行测试的应用时就是如此。 应用的操作完成或删除此策略时，设备将恢复正常状态。

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>为 iOS 设备上的电子邮件和 web 浏览配置受信任的域 <!-- 723765 -->
现在可以从 iOS 设备限制配置文件配置以下[域设置](device-restrictions-ios.md#domains)：

- **未标记的电子邮件域** - 用户发送或接收的电子邮件如果不匹配在此处指定的域，将标记为不受信任。

- **托管的 Web 域** - 从此处指定的 URL 下载的文档将被视为托管(仅限 Safari)。  

- **Safari 密码自动填充域** - 用户只能在 Safari 中保存与你在此处指定的模式相匹配的 URL 的密码。 若要使用此设置，设备必须处于监督模式，不配置为用于多个用户。 （iOS 9.3 及更高版本）


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>iOS 公司门户中可用的 VPP 应用 <!-- 748782 -->
现在可以将 iOS 批量购买的 (VPP) 应用作为**可用**安装分配给最终用户。 最终用户需要具有 Apple Store 帐户才能安装该应用。

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>同步 Apple VPP 应用商店的电子书 <!-- 800878 -->
现在可以将 Intune 与从 Apple 批量采购计划应用商店购买的书[同步](vpp-apps-ios.md)，并将其分配给用户。

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Samsung Knox Standard 设备的多用户管理 <!-- 971988 -->
现在，运行 Samsung Knox Standard 的设备支持使用 Intune 进行[多用户管理](android-enroll.md)。 这意味着最终用户可以使用其 Azure Active Directory 凭据登录和注销设备，并且无论是否正在使用，都会集中管理设备。  最终用户登录时，可以访问应用，还可以获得已应用于应用的任何策略。 用户注销时，会清除所有应用数据。

### <a name="additional-windows-device-restriction-settings----818566---"></a>其他 Windows 设备限制设置 <!-- 818566 -->
我们添加了对其他 [Windows 设备限制设置](device-restrictions-windows-10.md)的支持，如其他 Microsoft Edge 浏览器支持、设备锁屏界面自定义、开始菜单自定义、Windows 聚焦搜索集壁纸和代理设置。

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Windows 10 创意者更新的多用户支持 <!-- 822547 -->
我们为运行 Windows 10 创意者更新的设备和加入 Azure Active Directory 域的设备添加了对[多用户管理](windows-enroll.md)的支持。 这意味着不同的标准用户使用其 Azure AD 凭据登录设备时，他们将收到分配给其用户名的所有应用和策略。 用户当前无法将公司门户用于自助服务方案，如安装应用。

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Windows 10 电脑的 Fresh Start <!-- 1004830 -->
现在提供 Windows 10 电脑的全新 [Fresh Start 设备操作](device-fresh-start.md)。  发出此操作时，电脑上安装的任何应用都将被删除，而且电脑会自动更新到最新版本的 Windows。 这可用于删除新电脑通常附带的预先安装的 OEM 应用。 可以配置是否在发出此设备操作时保留用户数据。

### <a name="additional-windows-10-upgrade-paths----903672---"></a>Windows 10 其他升级途径<!-- 903672 -->
现可创建[版本升级策略](edition-upgrade-configure-windows-10.md)，将设备升级到以下的其他 Windows 10 版本：

- Windows 10 专业版
- Windows 10 专业版 N
- Windows 10 专业教育版
- Windows 10 专业教育版 N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>批量注册 Windows 10 设备 <!-- 747607 -->
现在可以使用 Windows 配置设计器 (WCD) 将运行 Windows 10 创意者更新的大量设备加入到 Azure Active Directory 和 Intune。 若要启用 Azure AD 租户的[批量 MDM 注册](windows-bulk-enroll.md)，请使用 Windows 配置设计器创建将设备加入你的 Azure AD 租户的预配程序包，并将程序包应用到你想要批量注册和管理的公司所有的设备。 将程序包应用到设备后，设备将加入 Azure AD 并在 Intune 中注册，以供 Azure AD 用户登录。  Azure AD 用户是这些设备上的标准用户并接收分配的策略和必需的应用。 目前不支持自助服务和公司门户方案。

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----581122-736644---"></a>PIN 和托管存储位置的新 MAM 设置 <!-- 581122, 736644 -->
现在这两个新的应用设置可用于帮助你处理移动应用程序管理 (MAM) 方案：

- **托管设备 PIN 时禁用应用 PIN** - 检测注册设备上是否存在设备 PIN，如果是，则忽略应用保护策略触发的应用 PIN。 此设置允许减少用户在注册设备上打开已启用 MAM 的应用程序时所看到的 PIN 提示次数。 此功能适用于 Android 和 iOS。

- **选择可将公司数据保存到其中的存储服务** - 允许你指定可将公司数据保存到哪些存储位置。 用户可以保存到所选存储位置服务，这意味着将阻止所有未列出的其他存储位置服务。

  支持的存储位置服务列表：

  - OneDrive
  - Business SharePoint Online
  - 本地存储

### <a name="help-desk-troubleshooting-portal----907448---"></a>支持人员疑难解答门户<!-- 907448 -->
新的[疑难解答门户](help-desk-operators.md)允许技术支持人员和 Intune 管理员查看用户及其设备，并执行任务以解决 Intune 技术问题。

## <a name="march-2017"></a>2017 年 3 月

### <a name="support-for-ios-lost-mode---431695--"></a>对 iOS 丢失模式的支持<!--431695-->
对于 iOS 9.3 和更高版本设备，Intune 增加了对**丢失模式**的支持。 现在可以锁定设备以防止所有使用并显示设备锁定屏幕的消息和联系人电话号码。

最终用户将无法解锁设备，直到管理员禁用丢失模式。 启用丢失模式后，可以使用“查找设备”操作在 Intune 控制台中的地图上显示该设备的地理位置。

此设备必须是处于监督模式下通过 EDP 注册的公司所有的 iOS 设备。

有关详细信息，请参阅[什么是 Microsoft Intune 设备管理](device-management.md)？

### <a name="improvements-to-device-actions-report---677150--"></a>改进设备操作报告<!--677150-->
改进了设备操作报告，进而改善了性能。 此外，现可按状态筛选报告。 例如，可筛选报告以仅显示“已完成”的设备操作。

### <a name="custom-app-categories---748805--"></a>自定义应用类别<!--748805-->
现可以为添加到 Intune 的应用创建、编辑和分配类别。 目前，只能以英文指定类别。
请参阅[如何将应用添加到 Intune](apps-add.md)。

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>将 LOB 应用分配给未注册设备的用户<!--748823-->
现在，无论用户的设备是否已注册 Intune，都可以设置应用商店到用户业务线应用程序。 如果用户设备未注册 Intune，他们必须转到公司门户网站（而非公司门户应用）安装它。

### <a name="new-compliance-reports---846671--"></a>新符合性报告<!--846671-->
现可通过符合性报告了解设备在公司中的符合性状态，以便快速解决用户遇到的与符合性相关的问题。 可查看以下相关信息

- 设备的总体符合性状态
- 单个设置的符合性状态
- 单个策略的符合性状态

还可使用这些报告深入了解各个设备，查看影响该设备的特定设置和策略。

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接访问 Apple 注册方案<!--951869-->
对于在 2017 年 1 月之后创建的 Intune 帐户，Intune 支持在 Azure 门户中使用注册设备工作负荷直接访问 Apple 注册方案。 以前，只能通过 Azure 门户中的链接访问 Apple 注册预览版。 2017 年 1 月之前创建的 Intune 帐户需要进行一次性迁移，然后才能使用 Azure 中的这些功能。 虽然迁移时间表尚未宣布，但会尽快发布详细信息。 强烈建议创建一个试用帐户，在现有帐户无法访问预览版时测试新体验。


## <a name="february-2017"></a>2017 年 2 月

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>限制移动设备注册的功能<!--747600, 795782-->
Intune 新增了注册限制，可控制允许注册的移动设备平台。 Intune 将移动设备平台分为 iOS、macOS，Android、Windows 和 Windows Mobile。

* 限制移动设备注册不会限制电脑客户端注册。  
* 阻止个人自有设备的注册有一个附加选项，该选项仅适用于 iOS 和 Android。

Intune 将所有新设备都标记为个人所有，除非 IT 管理员将设备标记为公司所有，如[本文](https://docs.microsoft.com/intune-classic/deploy-use/manage-corporate-owned-devices)所述。

### <a name="view-all-actions-on-managed-devices---677150--"></a>查看托管设备上的所有操作<!--677150-->
新添加的__设备操作__报表显示了在设备上执行远程操作（如出厂重置）的操作者，还额外显示了该操作的状态。 请参阅 [What is device management?](device-management.md)（什么是设备管理？）。

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>非托管设备可访问已分配的应用<!--664691-->
公司门户网站上的设计更改之一是，iOS 和 Android 用户能够在其非托管设备上安装分配到的“可用且无需注册”设备。 用户可使用其 Intune 凭据登录到公司门户网站，并查看分配到的应用列表。 “可用且无需注册”应用的应用包可通过公司门户网站进行下载。 需要注册才能安装的应用不受此更改影响，如果用户想安装这类应用，则会提示用户注册其设备。

### <a name="custom-app-categories---748805--"></a>自定义应用类别<!--748805-->
现可以为添加到 Intune 的应用创建、编辑和分配类别。 目前，只能以英文指定类别。
请参阅[如何将应用添加到 Intune](apps-add.md)。

### <a name="display-device-categories---814654--"></a>显示设备类别<!--814654-->
现在可以将设备类别作为设备列表中的一列进行查看。 并且还可以在设备属性边栏选项卡的属性部分编辑该类别。 请参阅[如何将应用添加到 Intune](apps-add.md)。

### <a name="configure-windows-update-for-business-settings---776716--"></a>配置 Windows Update for Business 设置<!--776716-->

Windows 即服务是为 Windows 10 提供更新的新方式。 从 Windows 10 开始，任何新的功能更新和质量更新都将包含所有此前更新的内容。 这意味着，只要安装了最新更新，你的 Windows 10 设备将完全保持最新状态。 与以前版本的 Windows 不同的是，现在必须安装完整的更新，而不是部分更新。

借助 Windows Update for Business 可以简化更新管理体验，不需要批准设备组的单个更新。 通过配置更新推出策略仍可以管理环境中的风险，并且 Windows 更新将确保在适当的时间安装更新。 Microsoft Intune 提供在设备上配置更新设置的功能，使你能够延迟更新安装。 Intune 不会存储更新，仅存储更新策略分配。 设备直接访问 Windows 更新以进行更新。使用 Intune 来配置和管理 **Windows 10 更新通道**。 更新通道包含一组设置，可配置何时以及如何安装 Windows 10 更新。 有关详细信息，请参阅[配置 Windows Update for Business 设置](windows-update-for-business-configure.md)。
