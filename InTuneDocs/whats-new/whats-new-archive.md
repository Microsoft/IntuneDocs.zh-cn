---
title: "新增功能存档 | Microsoft Intune"
description: "存档的 Microsoft Intune 新增功能公告"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/11/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: aa8fe81b6a9f6b11bba9c15ede36d9df9cd2e0da
ms.openlocfilehash: 72a2f8026d1a67a3a49111daa9a7b8380b0cb088


---
# <a name="whats-new---archive"></a>新增功能 - 存档

此页是 [Microsoft Intune 中新增功能中最新声明的存档](whats-new-in-microsoft-intune.md)。

## <a name="october-2016"></a>2016 年 10 月

### <a name="conditional-access-for-mobile-application-management"></a>用于移动应用程序管理的条件访问
你将能够限制对 Exchange Online 的访问，以便访问只能来自支持 Intune 移动应用程序管理策略的应用（如 Outlook）。 [这一新功能](/intune/deploy-use/allow-policy-managed-apps-access-to-o365)与 Intune 移动应用管理 (MAM) 策略实现完美配对，因为你可以阻止对内置邮件客户端或其他未配置 Intune MAM 策略的应用的访问。 这可确保用户使用可通过 Intune MAM 进行保护的应用访问组织数据。 你可以通过 Azure 门户开始使用 Intune 移动应用管理。 在“设置”边栏选项卡中查找新的“条件访问”分区。

### <a name="conditional-access-for-windows-pcs"></a>Windows 电脑的条件访问
现在可通过 Intune 管理控制台创建条件访问策略，阻止 Windows 电脑访问 [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) 和 [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)。 还可以创建条件访问策略，阻止访问 Office 桌面和通用应用程序。

### <a name="android-for-work-support"></a>Android for Work 支持

> [!IMPORTANT]

> 虽然可通过“必需”操作部署 Android for Work 应用，但如果已将 Intune 组迁移至新的 Azure AD 组体验，则只可以将应用部署为“可用”。

目前 Intune 是 Android for Work (AfW) 计划的一部分。 从本月起到接下来的几个月，我们将提供对 AfW 功能的支持。 请注意，AfW 的可用应用部署利用新的分组和目标设定体验。 新预配的 Intune 服务帐户在 AfW 对它们可用后就可使用此功能。

<!--Existing Intune customers can use this feature in production once their tenant has been migrated. Existing customers are welcome to create a trial Intune account to plan for and test this feature until their tenant has been migrated. Any questions on grouping and targeting timelines, please contact our [migration team](mailto:intunegrps@microsoft.com).-->

[阅读 Microsoft 关于针对 Android for Work 的 Intune 支持公告](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/12/microsoft-intune-support-for-android-for-work/)。

以下 Intune 主题是新主题或使用 Android for Work 信息进行了更新：

对于 IT 专业人员：
- [设置 Android for Work](/intune/deploy-use/set-up-android-for-work)
<!--- [Nathan Bigman's resource access topics]()-->
- [使用 Intune 限制对 Exchange Online 和新版 Exchange Online Dedicated 的电子邮件访问](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
- [使用 Intune 限制对 Exchange 内部部署和旧版 Exchange Online Dedicated 的电子邮件访问](/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
- [Android for Work 合规性策略设置](/intune/deploy-use/afw-compliance-policy-settings-in-microsoft-intune)
- [如何部署 Android for Work 应用](/intune/deploy-use/android-for-work-apps)
- [使用移动应用配置策略配置 Android for Work 应用](/intune/deploy-use/afw-app-configuration-policy)
- [Android for Work 策略设置](/intune/deploy-use/android-for-work-policy-settings-in-microsoft-intune)

对于最终用户：
- [创建工作配置文件时会发生的情况](/intune/enduser/what-happens-when-you-create-a-work-profile-android)
- [创建工作配置文件并在 Intune 中注册设备](/intune/enduser/create-a-work-profile-and-enroll-your-device-in-intune-android)

### <a name="lookout-integration-to-protect-ios-devices"></a>集成 Lookout 以保护 iOS 设备
在 10 月，Microsoft 将与 Lookout 的移动威胁防护解决方案集成，以通过检测设备上的恶意软件、危险应用等来保护 iOS 移动设备。 Lookout 的解决方案有助于确定威胁级别，可对该功能进行配置。 可以在 Intune 中创建合规性策略规则，以根据 Lookout 的风险评估来确定设备合规性。 使用条件访问策略，你可以基于设备合规性状态允许或阻止访问公司资源。

将提示不合规 iOS 设备的最终用户进行注册，并要求其在设备上安装 Lookout for Work 应用，激活该应用并修正 Lookout for Work 应用程序中报告的威胁，以便获得对公司数据的访问权限。 了解如何[配置并部署 Lookout for Work 应用](/intune/deploy-use/configure-and-deploy-lookout-for-work-apps)。
<!--TFS 1319493-->

<!--### New Microsoft Intune Company Portal available for Windows 10 devices
Microsoft is releasing a new [Microsoft Intune Company Portal for Windows 10 devices](https://go.microsoft.com/fwlink/?linkid=830663). This app, which leverages the new Windows 10 Universal format, will provide the user with an updated user experience within the app and identical experiences across all Windows 10 devices, PC and Mobile alike, while still enabling all the same functionality that they are using today.

The new app will also allow users to leverage additional platform features like single sign-on (SSO) and certificate-based authentication on Windows 10 devices. The app will be made available as an upgrade to the existing Windows 8.1 Company Portal and Windows Phone 8.1 Company Portal installs from the Windows Store.-->

### <a name="intune-app-wrapping-tool-for-android"></a>Intune App Wrapping Tool for Android
可以利用 Intune App Wrapping Tool，使应用能够使用 Intune 移动应用程序管理 (MAM) 策略。 现在可支持 MAM 策略，且无需设备注册。

### <a name="manage-printing-from-apps-managed-using-mam-policies"></a>从使用 MAM 策略管理的应用中管理打印
现可阻止打印来自使用了 MAM 策略的应用中的公司数据。 可在 [Azure 门户](/Intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)中使用此设置，且 [iOS](/Intune/deploy-use/ios-mam-policy-settings) 和 [Android](/Intune/deploy-use/android-mam-policy-settings) 设备均支持此设置。
<!--TFS 1014328-->

### <a name="support-for-fingerprints-on-android-devices"></a>Android 设备上支持使用指纹
Android 移动应用管理 (MAM) 策略现在允许用户使用指纹（而不是键入 PIN）访问应用。 在此查看此设置和其他[适用于 Android 的移动应用管理策略设置](/Intune/deploy-use/android-mam-policy-settings)。

### <a name="notices"></a>通知

__Android Samsung KNOX 与 Intune 的兼容性__ Samsung Galaxy Ace 手机的某些型号无法作为 Samsung KNOX 设备通过 Intune 进行管理。 当你使用 Intune 注册这些设备时，它们将被视为标准 Android 设备来进行管理。

受影响的型号包括：

* SM-G313HU
* SM-G313HY
* SM-G313M
* SM-G313MY
* SM-G313U

你和最终用户无需采取进一步的操作。 有关详细信息，请访问 [Samsung KNOX](https://www.samsungknox.com) 网站。

__适用于 Windows 8 的公司门户应用已弃用；将终止对 Windows Phone 8 和 Windows RT 平台的支持__ 从 2016 年 10 月开始，Microsoft Intune 将终止对 Windows 8 公司门户的支持。 另外，Microsoft Intune 还将终止对 Windows Phone 8 和 Windows RT 平台的支持。 因此，将无法注册或更新任何 Windows Phone 8 或 Windows RT 设备。

可以继续管理已注册的 Windows Phone 8、Windows RT 和 Windows 8 设备。 将 Windows Phone 8 和 Windows 8 设备更新到 Windows 8.1 和 Windows Phone 8.1，并使用相应的 Windows 8.1 和 Windows Phone 8.1 公司门户应用在不中断的情况下继续向这些设备分发应用。

从 2016 年 11 月开始，我们将终止对 Windows Phone 8 公司门户的支持。
<!--TFS 1255391-->

### <a name="whats-coming"></a>即将推出

__可用于 Windows 10 设备的新 Microsoft Intune 公司门户__ Microsoft 将发布适用于 Windows 10 设备的新 Microsoft Intune 公司门户。 此应用利用了新 Windows 10 Universal 格式，将在应用内为用户提供更新的用户体验，且跨所有 Windows 10 设备（PC 和移动设备等）提供相同的体验，同时还将保持现有的一切功能。

新应用还允许用户们在 Windows 10 设备上利用传统平台功能，例如单一登录 (SSO) 和基于证书的身份验证。 此应用将作为对现有 Windows 8.1 公司门户和 Windows Phone 8.1 公司门户（安装自 Windows 应用商店）的升级而提供。 有关详细信息，请转到 [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp)。
<!--TFS 1016502-->

## <a name="september-2016"></a>2016 年 9 月
### <a name="new-features-announcements-and-information"></a>新增功能、公告和信息
* [Windows 条件访问](#windows-conditional-access)
* [iOS 10 支持](#ios-10-support)
* [支持 MAM，且无需进行设备注册（针对 Android 和 iOS）](#app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios)
* [Intune 组将于 9 月过渡到 Azure Active Directory](#intune-groups-begin-transitioning-to-azure-active-directory-in-september)
* [集成 Lookout 以保护 Android 设备](#lookout-integration-to-protect-android-devices)
* [Android、iOS 和 Windows 公司门户更新](#company-portal-updates)
* [Intune 术语表](#intune-glossary)
* [即将推出](#whats-coming)

### <a name="windows-conditional-access"></a>Windows 条件访问
现在可通过 Intune 管理控制台创建条件访问策略，阻止 Windows 电脑访问 Exchange Online 和 SharePoint Oline。 还可以创建条件访问策略，阻止访问 Office 桌面和通用应用程序。

### <a name="ios-10-support"></a>iOS 10 支持
现有的 Intune MDM 和 MAM 方案与 iOS 10 兼容。 有关提示，请参阅 [Intune Support Team Blog](https://blogs.technet.microsoft.com/intunesupport/2016/09/13/support-tip-intune-support-for-ios-10/)（Intune 支持团队博客）。

### <a name="app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios"></a>App Wrapping Tool 支持 MAM，且无需进行设备注册（针对 Android 和 iOS）
Intune App Wrapping Tool 是一种命令行工具，用于在适用于 iOS 和 Android 的业务线 (LOB) 应用上启用 Intune MAM。 借助该工具，能够以最简单的方法将 Intune MAM SDK 整合到应用中，以便应用可执行通过 Intune 部署的 MAM 策略。 使用 MAM 策略，可以：

1. 加密应用数据。
2. 要求信息工作者在启动应用时输入 PIN。
3. 允许应用仅将数据传输到其他托管应用。
4. 防止应用将数据备份到 Android、iTunes 和 iCloud。
5. 仅允许剪切、复制和粘贴到其他托管应用，以及剪切、复制和粘贴自其他托管应用。

已更新的 Intune App Wrapping Tool 的公共预览版现支持 MAM，且无需在 Android 和 iOS 上对内部 LOB 应用进行设备注册。 这意味着最终用户不需要让其设备注册 Intune，便可使用启用了 MAM 的 LOB 应用。

任何人都可以测试该公共预览版软件，并参阅帮助文档，该文档位于 msintuneappsdk 的 GitHub：

<p style="margin-left: 40px">http://www.github.com/msintuneappsdk/intune-app-wrapper-ios-preview

<p style="margin-left: 40px">http://www.github.com/msintuneappsdk/intune-app-wrapper-android-preview

安装和使用适用于 Android 和 iOS 预发行版的 Microsoft Intune 应用包装之前，必须：

* 查看适用于 Android 和 iOS 预发行版的 Microsoft Intune App Wrapping Tool 的 Microsoft 许可条款
* 打印并保留一份许可条款，以留作记录。 下载和使用适用于 Android 预发行版的 Microsoft Intune App Wrapping Tool 表示你同意这些许可条款。 如果不接受这些条款，请不要使用此软件。
<!---TFS 1235607--->

### <a name="intune-groups-begin-transitioning-to-azure-active-directory-in-september"></a>Intune 组将于 9 月过渡到 Azure Active Directory
某些新的 Intune 帐户将使用 Azure Active Directory 安全组，而不是 Intune 用户组。 你将知道自己使用的是安全组，因为 Intune 门户组页上会有一个定向到 Azure 管理门户的链接。

### <a name="lookout-integration-to-protect-android-devices"></a>集成 Lookout 以保护 Android 设备
Microsoft 将与 Lookout 的移动威胁防护解决方案集成，以通过检测设备上的恶意软件、危险应用等来保护 Android 移动设备。 Lookout 的解决方案有助于确定威胁级别，可对该功能进行配置。 可以在 Intune 中创建合规性策略规则，以根据 Lookout 的风险评估来确定设备合规性。 使用条件访问策略，你可以基于设备合规性状态允许或阻止访问公司资源。

将提示非合规性设备的最终用户进行注册，并要求其在 Android 设备上安装 Lookout for Work 应用程序，激活该应用并修正 Lookout for Work 应用程序中报告的威胁，以便获得访问权限。 若要了解详细信息，请参阅[根据设备、网络和应用程序风险限制访问权限](restrict-access-based-on-device-network-app-risk.md)。


### <a name="company-portal-updates"></a>公司门户更新

__Android__

<p style="margin-left: 40px">**向 Android 公司门户添加“通知”**<br/>
<p style="margin-left: 40px">已将新的“通知”图标添加到 Android 公司门户的主页上。 点击此图标将访问“通知”页，该页将向你的最终用户显示在公司门户应用中需要注意的所有项，例如，设备非合规性、注册更新和注册激活。 iOS 公司门户应用已经有此通知体验。 拥有此新的“通知”页意味着，只要设备已注册，每次启动或恢复公司门户时，你将不会看到“公司访问设置”页。 如果你创建自己的最终用户指南，可能需要更新你的文档来反映此更改。 在[此处](https://aka.ms/androidcpupdate)查看更新的屏幕截图。  

__iOS__
<p style="margin-left: 40px">**iOS 公司门户应用的支持更改**<br/>
<p style="margin-left: 40px">现要求适用于 iOS 的 Microsoft Intune 公司门户应用的所有用户都使用最新版本。 新用户只能下载最新版本，而当前用户必须更新到最新版本。 最新版本需要 iOS 8.0 或更高版本，因此运行较旧的 iOS 版本的设备将无法使用公司门户或者进行注册，直到将其设备更新为 iOS 8.0 或更高版本，并且将公司门户应用更新到最新版本。 运行 iOS 8.0 以下版本的已注册设备将继续受管理，并将列在 Intune 管理员控制台中。
<!---TFS 1283165--->

<p style="margin-left: 40px">**iOS 最终用户如何获取应用方面的改进**<br/>
<p style="margin-left: 40px">在 iOS 的公司门户应用的应用磁贴中已进行了以下更改，从一个位置（公司门户网站中）即可将用户指向其所有应用的不同视图。 Apple 限制禁止业务线和托管应用商店应用列于公司门户应用中，并要求用户访问不同视图来查找自己所有的应用。

<p style="margin-left: 40px">“公司应用”磁贴之前指向公司门户网站“全部”选项卡中的所有应用的列表，此行为将继续以同种方式运作。 磁贴名称已更改为“全部应用”。

<p style="margin-left: 40px">“其他应用”磁贴之前指向公司门户应用内部的一个视图，其中列出了 Apple 允许公司门户应用显示的所有应用。 磁贴名称已更改为“特别推荐的应用”，点击该磁贴会将用户转到公司门户网站的“特别推荐”选项卡。

<p style="margin-left: 40px">“类别”磁贴之前指向公司门户应用内部的一个视图，其中列出了应用类别。 磁贴名称未改变，但它现指向公司门户网站的“类别”选项卡。 你可以在[此处](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186)查看更新的屏幕截图。
  <!---TFS 1317133--->

<p style="margin-left: 40px">**如果 IT 专业人员为应用设置该要求，则会提示安装 iOS 托管浏览器应用**<br/>
<p style="margin-left: 40px">如果你已经将 Web Clip 配置为仅在托管的浏览器中打开，且托管浏览器未在设备上安装，则设备上的公司门户应用将提示用户安装托管浏览器后才能安装 Web Clip。
  <!---TFS 1228570--->

__Windows__
<p style="margin-left: 40px">**添加到 Windows Phone 8.1 公司门户应用的反馈按钮**<br/>
<p style="margin-left: 40px">Windows Phone 8.1 公司门户应用让最终用户能够通过使用新的“发送反馈”按钮发送有关应用的反馈。 要找到该按钮，用户需点击公司门户应用屏幕右下方的的“三个点”菜单，然后点击“发送反馈”。 收集的匿名信息反馈将帮助 Microsoft 改进用户的公司门户应用体验。
<!---TFS 1317806--->

### <a name="intune-glossarybr"></a>Intune 术语表</br>
我们在库中添加了一个新的[术语表主题](https://docs.microsoft.com/intune/understand-explore/intune-glossary)，帮助你了解 Intune 产品中使用的一些术语。

## <a name="august-2016"></a>2016 年 8 月
### <a name="app-management"></a>应用管理
<!---@Barry, I created the buckets of App management, Device management, etc but am not tied to them. Just wanted to break up and organize the feature list. If you're going to take over the Company Portal section, please talk to Stacie about how she's been organizing it. --->

__iOS 9.3 隐藏和显示的应用__ 对于运行 iOS 9.3 或更高版本的设备，可将 iOS 常规配置策略中隐藏和显示的应用列表用于：
- 指定对用户隐藏的应用列表。 用户无法查看，或启动这些应用。
- 指定用户可以查看和启动的应用列表。 无法查看或启动其他应用。

你可以指定的应用包括已部署的应用，以及内置的 iOS 应用，如“信息”和“备忘录”。 有关详细信息，请参阅 [Microsoft Intune 中的 iOS 策略设置]( https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune)
<!---TFS 1279009 checked--->
__Samsung KNOX 设备允许和阻止的应用策略__ 现在可以配置适用于 Samsung KNOX 设备的自定义策略，使你能够创建以下项之一：
- 阻止在设备上运行的应用的列表。 即使安装了阻止列表中定义的应用，该应用也不能在设备上激活。
- 允许设备用户从 Google Play 商店中安装的应用的列表。 其他应用不能从应用商店安装。

仅运行 Samsung KNOX 的设备可以使用这些设置。
有关详细信息，请参阅[使用自定义策略允许和阻止适用于 Samsung KNOX 设备的应用]( custom-policy-to-allow-and-block-samsung-knox-apps.md)。
<!---TFS 1311629 checked --->
__与移动应用程序管理 (MAM) 策略兼容的新应用__ 无论是否已注册设备，适用于 [iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) 和 [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) 的 Yammer 应用现在都与 [Intune 移动应用程序管理 (MAM) 策略](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)兼容。

有关 MAM 兼容应用的完整列表，请参阅 [Microsoft Intune 应用程序合作伙伴](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners)站点。
<!--- TFS 1252335 & 1252336 checked--->


<!--- I started putting TFS numbers in the What's Coming topic and found it helpful when updating the What's New. Up to you if you want to continue. --->

__Intune 查看器应用__ 随着新的 RMS 共享应用的发布，我们将从 2016 年 8 月起删除以下 Intune 查看器应用：
- Intune AV 查看器
- Intune PDF 查看器
- Google Play 中适用于 Android 的 Intune 图像查看器

建议使用[适用于 Android 的 Rights Management 应用（RMS 共享）](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app)而不是使用 Intune 查看器应用，前者只需部署一个应用而不是三个单独的应用便可安全地查看 Android 设备上的公司文件。 如果不再支持 Intune 查看器应用，则将其从 Google 应用商店中删除并且不可供将来使用。

### <a name="device-management"></a>设备管理
__Android 7.0 支持__ Intune 为移动设备即将推出的 Android 7.0 操作系统提供“day 0”支持。
<!---TFS 1262053--->
### <a name="google-removal-of-remote-passcode-reset-capability-on-android-70-devices"></a>Google 删除了 Android 7.0 设备上的远程密码重置功能
Google 正在删除 Android 7.0 设备的 IT 管理员和最终用户远程重置密码功能。 以前，IT 管理员可以远程重置用户的密码，而且最终用户可以从公司门户网站重置其密码。



### <a name="company-portal-updates"></a>公司门户更新
__公司门户网站__
- **从公司门户到 Microsoft 的反馈链接** <br/>
公司门户网站使最终用户能够点击位于页面底部的新的“反馈”链接，以便向 Microsoft 发送有关他们对站点的体验的反馈。 收集的匿名信息反馈将帮助 Microsoft 改进用户的公司门户网站体验。
<!--- TFS 1313657 checked--->

__iOS__
- **最低 iOS 托管浏览器版本已更新为 8.0**<br/>
已更新用于 iOS 的 Microsoft Intune Managed Browser 应用以支持运行 iOS 8.0 或更高版本的设备。 虽然 iOS 7.1 设备仍可使用现有的 Managed Browser 应用，但最好鼓励你的用户更新为 iOS 8.0 或更高版本，以访问和充分利用新的 Managed Browser 功能。  
<!---TFS 1313253 checked--->

### <a name="whats-coming"></a>即将推出
__Intune 组将于 2016 年 9 月过渡到 Azure Active Directory 组__ Intune 正在创建将 Azure Active Directory (AAD) 安全组用作 Intune 中的用户和设备组的新组管理体验。 **当我们介绍新的基于 Azure 的 Intune 管理门户时**，这些组将用于所有组管理、策略部署和配置文件部署。

此新体验将会使你无需在服务之间重复组，**允许你访问某些新的 Azure Active Directory Premium (AADP) 组功能**，并提供使用 PowerShell 和图表的可扩展性。 这还将跨企业移动性管理统一组管理体验。

若要启用移动到安全组，**当前管理控制台**中的体验将进行一些修改。 **这些更改和 AAD 安全组的使用情况将记录在 Intune 文档中**。

Intune 的新客户将看到**当前租户执行操作之前的一些安全组更改**。

除了组管理中的更改，**还将弃用以下功能**：
- 在创建新组的过程中排除成员或组
- “**未分组的用户**”和“**未分组的设备**”组
- 服务管理员角色中的“**管理组**”
- 对通知规则的基于组的自定义警报
- 利用报表中的组进行透视
<!--- TFS 1295329--->

__向 Android 公司门户添加“通知”__ 我们将于 9 月发布 Android 公司门户的更新，会在主页上引入一个新的“通知”图标。 点击此图标将访问“**通知**”页，该页将向你的最终用户显示在公司门户应用中需要注意的所有项，例如，设备非合规性、注册更新和注册激活。 如果还使用 iOS 公司门户应用，你将已看到通知体验。 通过引入“**通知**”页，只要设备已经注册，每次启动或恢复 Android 公司门户时，你将不会看到“**公司访问设置**”页。 我们听说你们中的许多人都已创建最终用户指南，而且非常感谢你们在指南/屏幕快照可能需要更新时提前通知我们。 请更新你的文档，以反映体验中即将发生的更改。 在此查找更新的屏幕快照：https://aka.ms/androidcpupdate。  

### <a name="service-deprecation"></a>服务弃用
<!---@Barry, we started listing service deprecations earlier this summer. --->
- **iOS 公司门户应用的支持更改**<br/>
在 9 月，要求适用于 iOS 的 Microsoft Intune 公司门户应用的所有用户都使用最新版本。 新用户将只能够下载最新版本，而当前用户必须更新到最新版本。 最新版本需要 iOS 8.0 或更高版本，因此运行较旧的 iOS 版本的设备将无法使用公司门户或者进行注册，直到将其设备更新为 iOS 8.0 或更高版本，并且将公司门户应用更新到最新版本。 运行 iOS 8.0 以下版本的已注册设备将继续受管理，并将列在 Intune 管理员控制台中。  

- **最低 iOS 托管浏览器版本已更新为 8.0**<br/>
Intune 将于 8 月发布适用于 iOS 的更新的 Microsoft Intune 托管浏览器应用，该应用将仅支持运行 iOS 8.0 或更高版本的设备。 iOS 7.1 设备仍将能够使用现有的托管浏览器应用，请鼓励你的用户更新为 iOS 8.0 或更高版本，以访问和充分利用新的托管浏览器功能。  
<!---TFS 1313253--->

- **适用于 Windows 8 和 Windows Phone 8 的公司门户应用将从 2016 年 9 月起弃用** <br/>
从 2016 年 9 月开始，Microsoft Intune 将结束为适用于 Windows Phone 8 和 Windows 8 平台的 Microsoft Intune 公司门户应用提供支持。 将设备更新到 Windows 8.1 和 Windows Phone 8.1，并使用相应的 Windows 8.1 和 Windows Phone 8.1 公司门户应用继续向这些设备分发应用。
<!---TFS 1255391--->

<!--- - **Custom Group Targeting of Notification Rules Removal.**<br/>
Intune notification rules define who an email alert will be sent to from Intune. Currently, you can configure notification rules to send emails to all users of devices in an Intune device group that you created. From around June 1st 2016 moving forward, targeting user-created groups will no longer be supported.

    Today, to target a notification rule to a group you created from the Microsoft Intune administration console, you would take the following steps:

    In the **Admin** workspace, click **Notification Rules** > **Create New Rule**

    In step two of the Create Notification Rule Wizard, select the device groups which the rule will target. This step, “select device groups”, is being removed from the Intune Console.

    The preliminary timeline for this change is as follows:
    - In August, 2016, new tenants will not see step two of the Create Notification Rule Wizard. Exiting tenants are unaffected.
    - Around September, 2016, some existing tenants will not see the “select device groups” in the wizard.
    - Around November, 2016, we expect that all tenants will not see the “select device groups” in the wizard.

--->

## <a name="july-2016"></a>2016 年 7 月
### <a name="app-management"></a>应用管理

__改善应用预配配置文件更新体验__ Apple iOS 业务线移动应用附带预配配置文件和证书签名的代码。 当应用在 iOS 设备上运行时，iOS 会确认 iOS 应用的完整性，并强制实施由预配配置文件定义的策略。

用于签署应用的企业签名证书通常持续 3 年。 但是，预配配置文件将在 1 年后过期。 利用此更新，Intune 会为你提供一些工具，用于主动地将新预配配置文件策略部署到安装了即将到期的应用而证书仍有效的设备。 有关详细信息，请参阅[使用 iOS 移动预配配置文件策略以保持你的业务线应用最新](/intune/deploy-use/ios-mobile-app-provisioning-profiles)。
<!--- TFS 1280247--->

__用于 Intune 应用的 SDK Xamarin 已推出__ Intune App SDK Xamarin 组件允许在使用 Xamarin 生成的移动 iOS 和 Android 应用中启用 Intune 移动应用管理功能。 你可以在 [Xamarin 应用商店](https://components.xamarin.com/view/Microsoft.Intune.MAM)中或在 [Microsoft Intune Github 页面](https://github.com/msintuneappsdk)上找到该组件。
<!--- TFS 1061478 --->

### <a name="device-management"></a>设备管理
__提高了设备注册限制__ Intune 将每个用户的最大可配置设备注册限制从 5 提高到了 15。
<!---TFS 1289896 --->

__运行 Intune 客户端软件的 Windows 电脑的 TeamViewer 集成__
运行 Intune 客户端的 Windows 电脑的 [TeamViewer](https://www.teamviewer.com) 集成能够实现与 Windows 电脑建立远程协助会话，从而帮助支持最终用户支持部门。 这包括 Windows 7、Windows 8、Windows 8.1 和 Windows 10。 有关详细信息，请参阅[使用 Microsoft Intune 计算机客户端的常见 Windows 电脑管理任务](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client)。
<!---TFS 1284856--->

### <a name="company-portal-updates"></a>公司门户更新

__公司门户网站__
- **改善了注册 Windows 设备时的最终用户体验**<br/>
使用条件访问时，Windows 8.1、Windows 10 桌面版和 Windows 10 移动版的注册步骤已在公司门户网站中阐明。 用户现在将看到单独的“设备注册”和“工作区加入”步骤，从而在他们遇到工作区加入 (WPJ) 失败时更易于看到设备的状态以及完成此过程。 执行单独的步骤还可以简化 IT 管理员排除故障的过程。 以前，当最终用户尝试注册并且 WPJ 除外的所有注册步骤都成功时，已注册的设备将不出现在用户要标识的设备列表中，因而使用户感到困惑。

__Android__
- **Android 公司门户应用**<br/>
如果 Android 最终用户看到一条错误消息，指出其设备缺少所需的证书，用户可以点击“如何解决此问题”按钮以获取安装缺少的证书的[步骤](/intune/enduser/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator)。 如果用户完成这些步骤，但看到另一条“缺少证书”的错误消息，系统会要求用户联系其 IT 管理员，并提供此[链接](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues)，其中包含 IT 管理员可以用于解决证书问题的步骤。

- **限制旁加载的应用安装到注册的设备**<br/>
Android 设备不能再通过公司门户网站安装应用程序，除非使用适用于 Android 的 Intune 公司门户应用已在 Intune 中注册设备。
<!---TFS 1299082--->

__iOS__
- **对 iOS 公司门户应用中设备注册管理器帐户的更改**<br/>
若要提高性能和可扩展性，Intune 不再在 iOS 公司门户应用的“**我的设备**”窗格中显示所有设备注册管理器 (DEM) 设备。 仅显示运行该应用的本地设备，且仅限该设备通过公司门户应用注册的情况下。

DEM 用户可能会在本地设备上执行操作，但只能从 Intune 管理员控制台远程管理其他已注册设备。 此外，Intune 将不支持通过 Apple 设备注册计划或 Apple 配置器工具使用 DEM 帐户。 这两种注册方法已支持共享的 iOS 设备的无用户注册。

当共享设备的无用户注册不可用时，仅使用 DEM 帐户。 有关详细信息，请参阅[使用 Microsoft Intune 中的“设备注册管理器”注册企业自有设备](https://docs.microsoft.com/en-us/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)。
<!---TFS 1233681--->

### <a name="change-of-names-for-windows-features"></a>对 Windows 功能名称的更改
- [Microsoft Passport for Windows](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune) 现在称为 **Windows Hello 企业版**。
- [企业数据保护](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune)现在称为 **Windows 信息保护**。

## <a name="june-2016"></a>2016 年 6 月
### <a name="intune-service-health"></a>Intune 服务运行状况
Intune 服务运行状态信息已随同其他 Microsoft 服务一起移到一个中心位置。 现在，你可在服务运行状态下的 Office 365 管理门户中找到此信息。 有关详细信息，请参阅[此博客文章](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/)。

### <a name="app-management"></a>应用管理
- **增强的 Windows 10 企业数据策略配置体验。** 我们围绕创建应用规则、指定网络边界定义和其他企业数据保护设置增强了 Windows 10 企业数据保护策略配置体验。 若要了解详细信息，请参阅 [Create an enterprise data protection (EDP) policy using Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune)（使用 Microsoft Intune 创建企业数据保护 (EDP) 策略）。


### <a name="device-management"></a>设备管理
- **Windows Defender 策略设置，可以避免可能不需要的应用。** 名为“**可能不需要的应用程序检测**”的新 Windows Defender 设置已被添加到 Windows 10 桌面版和移动版的常规配置。 你可以使用此设置以防止已注册的 Windows 台式计算机运行被 Windows Defender 分类为可能不需要的软件。 你可以防止这些应用程序运行，或使用审核模式在安装了不需要的应用程序时进行报告。 有关详细信息，请参阅 [Microsoft Intune 中的 Windows 10 策略设置](https://docs.microsoft.com/en-us/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune)。
<!---TFS 1244478--->

### <a name="conditional-access"></a>条件性访问
- **Intune 的 Cisco ISE 网络访问控制策略。**  使用 Cisco 标识服务引擎 (ISE) 2.1 并使用 Microsoft Intune 的客户可以在 ISE 中设置网络访问控制策略。

    此策略下，需要使用 WiFi 或 VPN 连接到网络的设备必须在符合以下条件后才被允许访问：

    * 必须由 Intune 进行管理
    * 必须符合任何已部署的 Intune 合规性策略

 非合规设备的最终用户将被提示注册和修正任何合规性问题以获取访问权限。
- **浏览器的条件性访问。** 可以为 [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) 和 [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune) 设置条件访问策略，以便仅允许通过托管且合规的 iOS 和 Android 设备上受支持的 Web 浏览器对其进行访问。 尝试通过 iOS 和 Android 设备登录到 Outlook Web Access (OWA) 和 SharePoint 站点的最终用户，系统将提示通过 Intune 注册其设备以及在完成登录前解决任何非合规性问题。
<!---TFS 1175844--->

- **Dynamics CRM Online 支持条件性访问。** 可以为 [Dynamics CRM Online](/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune) 设置条件访问策略，以便仅允许托管且合规的 iOS 和 Android 设备对其进行访问。 系统将提示尝试登录到 iOS 和 Android 设备上的 Dynamics CRM 移动应用的最终用户注册 Intune 并在登录完成前修正任何非合规性问题。
<!---TFS1295358--->

### <a name="intune-company-portal-updates"></a>Intune 公司门户更新

__Android 公司门户应用__

- 当 IT 管理员应用了新的“要求设备不允许安装来自未知源的应用 (Android 4.0 +)”策略时，Android 4.0 或更高版本设备的最终用户将看到消息“必须禁用来自未知来源的安装”。 用户将需要转到“设置” > “安全”，然后关闭“未知源”。 通过合规性消息中的链接，用户可获取有关该消息和为什么需要禁用该设置的详细[信息](/Intune/EndUser/you-are-asked-to-turn-off-unknown-sources-android)。

- 当 IT 管理员应用了新的“要求设备已启用扫描应用的安全威胁 (Android 4.0 +)”策略时，Android 4.0 或更高版本设备的最终用户将看到消息“扫描设备的安全威胁”。 用户将需要转到“设置” > “Google” > “安全”，然后打开“扫描设备的安全威胁”。 通过合规性消息中的链接，用户可获取有关该消息和为什么需要启用该设置的详细[信息](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android)。

- 当 IT 管理员应用了新的“要求禁用 USB 调试 (Android 4.2 +)”策略时，Android 4.2 或更高版本设备的最终用户将看到消息“必须禁用 USB 调试”。 用户将需要转到“设置” > “开发人员”选项，然后关闭“USB 调试”。 通过合规性消息中的链接，用户可获取有关该消息和为什么需要禁用该设置的详细[信息](/Intune/EndUser/you-are-asked-to-turn-off-usb-debugging-android)。

- 当 IT 管理员应用新的“最低 Android 安全修补程序级别 (Android 6.0+)”策略时，Android 6.0 或更高版本设备用户会看到消息“此设备不符合最低 Android 安全修补程序级别”。 用户将需要安装所需的安全修补程序。 通过合规性消息中的链接，用户可获取有关如何安装所需安全修补程序并查看当前已安装的安全修补程序的[信息](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android)。

__iOS 公司门户应用__

- 当最终用户安装业务线应用时，现在它们将看到改进的应用安装体验。 如果应用安装要花很长时间，用户可以手动同步设备以强制继续同步过程。 若要查看最终用户说明，请参阅[手动同步 iOS 设备](/Intune/EndUser/sync-your-device-manually-ios)。

- 适用于 iOS 的 Microsoft Intune 公司门户应用已更新，可支持 iOS 8.0 和更高版本。 此更新意味着，仅当设备正在运行 iOS 8.0 或更高版本时，最终用户才可在 Intune 中安装公司门户应用并注册新设备。 如果用户已注册运行不受支持的 iOS 版本的设备，则这些用户可以继续使用其设备上的公司门户应用。


## <a name="may-2016"></a>2016 年 5 月
所有这些功能也受混合部署 (Configuration Manager with Intune) 支持。 有关新的混合功能的详细信息，请查看[混合新增功能](https://technet.microsoft.com/en-us/library/mt718155.aspx)页。

### <a name="documentation"></a>文档
欢迎使用 [docs.microsoft.com](https://docs.microsoft.com/en-us/intune) 预览版本！
这是一个全新的新式内容平台，旨在使作为我们客户的你能更容易地理解和使用 Intune。
若要了解所有新增功能，请参阅 [Introducing docs.microsoft.com](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/)（docs.microsoft.com 简介）

### <a name="intune-service-health"></a>Intune 服务运行状况
Intune 服务运行状态信息已随同其他 Microsoft 服务一起移到一个中心位置。 现在你可在**服务运行状态**下的 [Office 365 管理门户](https://portal.office.com/Admin/Default.aspx)中找到此信息。
有关详细信息，请参阅[此博客文章](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/)。


### <a name="app-management"></a>应用管理
- **MAM SDK：支持 PIN 长度配置。** 你将能够指定类似于设备 PIN 的 MAM 应用的 PIN 的长度。 这将要求最终用户符合你设置的新限制。 他们将看到一个稍经修改的 PIN 屏幕来解释较长输入。 有关详细信息，请参阅[适用于 Android 的 MAM 策略设置](/intune/deploy-use/android-mam-policy-settings)和[适用于 iOS 的 MAM 策略设置](/intune/deploy-use/ios-mam-policy-settings)。

- **Skype for Business iOS 版和 Android 版。** 你现在可以通过 [MAM 以 Skype for Business 为目标，而不需要注册策略](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)。 用户登录后，将应用 MAM 策略。

- **可通过 MAM 策略管理的新应用。** 适用于 Android 的 Microsoft Word、Excel 和 PowerPoint 应用现在可与未向 Intune 注册的设备上的 MAM 策略相关联。 有关支持的应用的完整列表，请转到 [Microsoft Intune application partners](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)（Microsoft Intune 应用程序合作伙伴）页上的 Microsoft Intune mobile application gallery（Microsoft Intune 移动应用程序库）。


### <a name="company-portal-updates"></a>公司门户更新

#### <a name="android-company-portal-app"></a>Android 公司门户应用
- **最终用户 toast 通知**：当最终用户从公司门户注册设备或删除设备时，现在他们将会看到来自 Andoid 公司门户应用的 toast 通知。

- **对 Android 公司门户应用中设备注册管理器帐户的更改。** 若要提高性能和可扩展性，Intune 不再在 Android 公司门户应用的“我的设备”窗格中显示所有设备注册管理器 (DEM) 设备。 仅显示运行该应用的本地设备，且仅限该设备通过公司门户应用注册的情况下。 DEM 用户可能会在本地设备上执行操作，但只能从 Intune 管理员控制台远程管理其他已注册设备。

#### <a name="company-portal-website"></a>公司门户网站
- **公司门户网站：设备标识横幅将向最终用户提供详细信息。** 最终用户现在能够更轻松地标识他们在使用公司门户网站时所选的设备。 如果选择了错误的设备，他们将能够通过点击主页标题栏中的**点击此处**链接选择正确的设备。

### <a name="service-deprecation"></a>服务弃用
- **Intune 查看器应用。** 随着新的 RMS 共享应用的发布，我们将从 2016 年 8 月起删除以下 Intune 查看器应用：
    - Intune AV 查看器
    - Intune PDF 查看器
    - Google Play 中适用于 Android 的 Intune 图像查看器

  建议使用适用于 Android 的 Rights Management 应用（RMS 共享）而不是使用 Intune 查看器应用，前者只需部署一个应用而不是三个单独的应用便可安全地查看 Android 设备上的公司文件。 了解有关 RMS 共享应用（具有指向文档的链接）的详细信息。

- **通知规则删除的自定义组目标。**
Intune 通知规则定义将从 Intune 向其发送电子邮件警报的人员。 当前，你可将通知规则配置为向你创建的 Intune 设备组中的设备所有用户发送电子邮件。 约从 2016 年 6 月 1 日起，已不再支持目标用户创建组。

    当前，若要为从 Microsoft Intune 管理控制台创建的组指定通知规则，应采用以下步骤：

    在**管理员**工作区，单击**通知规则**  >  **创建新规则**

    在创建通知规则向导的步骤二中，选择此规则所针对的设备组。 将从 Intune 控制台中删除“选择设备组”这一步骤。

    此更改的初步时间线如下：
    - 2016 年 6 月，新租户将看不到创建通知规则向导的步骤二。 正在退出的租户不受影响。
    - 2016 年 8 月左右，某些正在退出的租户将看不到向导中的“选择设备组”。
    - 2016 年 10 月左右，我们期望所有租户将不会看到向导中的“选择设备组”。


- **iOS 公司门户应用的支持更改**。 未来数月中，Microsoft Intune 公司门户应用 iOS 版将会更新，更新后仅支持运行 iOS 8.0 或更高版本的设备。 用户将无法注册运行 iOS 8.0 以下版本的新设备。 已注册的运行 iOS 8.0 以下版本的设备将继续受管理，且在有限时间内，能够继续使用公司门户应用。 但是，只有 iOS 8.0 或更高版本的设备才能访问最新版本的公司门户应用。 我们鼓励你通知用户更新到 iOS 8.0 或更高版本以充分利用 Intune 的新功能。  


## <a name="april-2016"></a>2016 年 4 月
所有这些功能也支持混合客户（与 Intune 集成的 Configuration Manager）。

### <a name="app-management"></a>应用管理
- **MAM 用户合规性。**
现在，你可以查看 Azure Active Directory (AAD) 租户中的任何用户的应用程序管理策略的[状态](/intune/deploy-use/monitor-mobile-app-management-policies-with-Microsoft-Intune)。 这包括：
   - 设备
   - 在设备上的应用

   状态值：

   **已签入**：指示该策略已部署到用户，以及应用已用在工作环境中且已成功接收到该策略。

    **未签入**：指示策略已部署到用户，但应用从那时起尚未在工作环境中使用。


- **防止 Outlook 联系人同步的 MAM 控件 (Android)。**
适用于[移动应用程序管理](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)而无需注册设备的新设置。 此设置可以防止应用程序将联系人同步到 Android 设备的本机通讯簿。 启用此设置后，目标应用程序将不能再将联系人保存到本机通讯簿。 禁用此设置后，目标应用程序将能够将联系人保存到本机通讯簿。 [远程擦除设备或应用](/intune/deploy-use/wipe-managed-company-app-data-with-Microsoft-Intune)后，将删除已保存到本机通讯簿的所有联系人。 最初，Android 设备上的 Outlook 应用程序支持此新设置。

### <a name="device-management"></a>设备管理
- **公司拥有的设备的电话号码标识。** 例如，当运行移动设备清单报表时，现在使用其完整的电话号码标识归类为“企业”的手机。 BYOD 电话号码将继续使用 **** 屏蔽，仅显示最后 4 位数字。


### <a name="company-portal-updates"></a>公司门户更新
**Android 公司门户应用**未在 Intune 注册其设备和未安装正确证书的用户将不能登录到 Android 公司门户应用，并且会看到以下消息：“无法登录，因为设备缺少必需的证书”。 该消息包含“如何解决此问题”的链接，用户可以点击以查看关于安装证书的说明。 若要查看最终用户解决此问题的步骤，请参阅[设备缺少必需的证书](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing)。

**iOS 公司门户应用**已添加“下拉刷新”操作支持以刷新主页上的内容，其中包括列出的应用、设备以及 IT 联络信息。 “下列刷新”操作不会检查合规性或策略信息，这可以通过选择当前设备的磁贴，然后点击“同步”按钮来实现。

**Windows 10 移动版和 Windows Phone 8.1 公司门户应用**当最终用户安装业务线应用时，他们现在将了解到改进后的应用安装体验。 如果应用安装要花很长时间，用户可以手动同步设备以强制继续同步过程。 若要查看最终用户说明，请参阅[手动同步设备以加速应用安装](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually)。

**公司门户网站**当 Windows 10 移动版和 Windows Phone 8.1 用户正在安装业务线应用时，现在他们将看到以下新状态，向他们提供有关安装状态的详细信息：

* **等待设备进行同步** – 用户已点击“安装”，并且设备现在尝试与 Intune 基础结构进行同步。 必须先同步，然后才能完成安装。 “正在等待设备进行同步”消息也是一个链接，用户可以点击以查看[说明](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually)，了解如果同步过程需要很长时间或已停止，如何手动将设备与 Intune 同步。
* **正在下载** – 正在处理用户的下载请求，且设备正在下载并安装应用。

添加这些状态之前，如果应用安装需要很长时间，用户将感到困惑，因为他们只能看到“正在安装”状态，而这可能会在屏幕上保持数个小时。 添加新的状态意味着，现在用户可以点击“正在等待设备进行同步”链接，并按照说明进行操作以强制继续同步过程，而不是呼叫支持部门。



### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new-in-microsoft-intune.md)。



<!--HONumber=Nov16_HO3-->


