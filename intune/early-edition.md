---
title: "早期版本"
description: 
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 01/18/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 12f4a09fe10ec792abe8183369a21f53c23f5d1a
ms.sourcegitcommit: 53d272defd2ec061dfdfdae3668d1b676c8aa7c6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2018
---
# <a name="the-early-edition-for-microsoft-intune---january-2018"></a>Microsoft Intune 早知道 - 2018 年 1 月

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

### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546---"></a>可以更轻松地解决适用于 Windows 10 的“公司门户”应用的符合性问题 <!--676546 -->

使用 Windows 设备的最终用户将可以点击“公司门户”应用中的不符合原因。 在可能的情况下，此操作会使用户直接转到“设置”应用中的适当位置，以修复问题。

### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625---"></a>新增了 Apple 批量注册所需的用户身份验证选项 <!-- 747625 -->
对于以下注册方法，Intune 将支持使用“公司门户”应用验证设备：

- Apple 设备注册计划
- Apple School Manager
- Apple Configurator 注册

使用“公司门户”选项时，可以强制执行 Azure Active Directory 多重身份验证，而不会屏蔽这些注册方法。

使用“公司门户”选项时，Intune 会跳过 iOS 设置助理中用于用户关联注册的用户身份验证。 也就是说，设备最初注册为无用户设备，因此不会接收用户组的配置或策略， 只会接收设备组的配置和策略。 不过，Intune 会在设备上自动安装“公司门户”应用。 首个启动并登录“公司门户”应用的用户将与 Intune 中的设备相关联。 此时，用户将会接收用户组的配置和策略。 只有重新注册，才能更改用户关联。

### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Intune 支持多个 Apple DEP/Apple School Manager 帐户 <!-- 747685 -->
Intune 将支持最多通过 100 个不同的 Apple 设备注册计划 (DEP) 或 Apple School Manager 帐户注册设备。 可以单独管理注册配置文件和设备的每个已上传令牌。 可以根据已上传的 DEP/ School Manager 令牌自动分配不同的注册配置文件。 如果上传了多个 School Manager 令牌，一次只能与 Microsoft 学校数据同步共享一个令牌。

迁移后，通过 Graph 管理 Apple DEP 或 ASM 的 beta 版本 Graph API 和已发布脚本将不再有效。 新的 beta 版本 Graph API 正在进行开发，将在迁移后发布。

### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eeready---"></a>使用“访问工作或学校帐户”设置选择设备类别 <!-- 1058963 eeready -->
如果已启用[设备组映射](https://docs.microsoft.com/en-us/intune/device-group-mapping)，Windows 10 用户将会在通过“设置” > “帐户” > “访问工作或学校帐户”中的“连接”按钮注册后或在开箱即用体验期间，看到选择设备类别的提示。

### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>将符合性策略定目标到设备组中的设备 <!--1307012 -->

将可以把符合性策略定目标到用户组中的用户。 将可以把符合性策略定目标到设备组中的设备。

### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>根据组添加和排除应用分配 <!-- 1406920 -->

在应用分配期间以及在选择分配类型后，将可以选择要添加和排除的组。

### <a name="remote-erase-command-support----1438084---"></a>远程“清除”命令支持 <!-- 1438084 -->

管理员将可以远程发出清除命令。

> [!IMPORTANT]
> 由于清除命令无法撤消，因此应谨慎使用。

清除命令不仅会从设备中删除所有数据（包括操作系统）， 还会从 Intune 管理范围中删除设备。 不过，并不会向用户发出警告，而是在命令发出后立即执行清除操作。

将可以配置 6 位恢复 PIN。 此 PIN 可用于解锁已清除的设备，此时将开始重新安装操作系统。 开始清除后，PIN 便会显示在 Intune 中设备概述边栏选项卡上的状态栏中。 只要清除正在进行中，PIN 就会一直显示。 清除完成后，设备便会从 Intune 管理范围中完全消失。 请务必记录恢复 PIN。这样一来，无论是谁恢复设备，都可以使用它。

### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Windows 搜索结果中的 Windows 信息保护 (WIP) 加密数据 <!-- 1469193 -->

借助 Windows 信息保护 (WIP) 策略中的新设置，可以控制是否在 Windows 搜索结果中添加 WIP 加密数据。

### <a name="website-learning-mode----1631908---"></a>网站学习模式 <!-- 1631908 -->

Intune 将引入 Windows 信息保护 (WIP) 学习模式扩展。 除了查看已启用 WIP 的应用的相关信息外，还将可以查看与网站共享工作数据的设备的摘要。 通过此信息，可以确定应将哪些网站添加到组和用户 WIP 策略中。

### <a name="updates-to-compliance-emails---1637547---"></a>更新了符合性电子邮件 <!--1637547 -->

如果发送电子邮件来报告不符合设备，其中将包括不符合设备的详细信息。 下面的文章将进行更新以体现这一点：[自动执行解决不符合问题所需的操作](#actions-for-noncompliance)。

### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>适用于 Intune 的条件访问策略只能通过 Azure 门户访问 <!-- 1737088 1634311 -->
我们将简化条件访问的配置和管理位置。 将在 [Azure 门户](https://portal.azure.com)中依次通过“Azure Active Directory” > “条件访问”配置和管理条件访问策略。 为方便操作，还将能够在 Azure 门户中依次通过“Intune” > “条件访问”，从 Intune 访问此边栏选项卡。

###  <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>已到期令牌和即将到期令牌的警报 <!-- 1639263 -->
概述页将显示已到期令牌和即将到期令牌的警报。 单击一个令牌的警报后，将转到令牌的详细信息页。  如果单击多个令牌的警报，将转到所有令牌及其状态的列表。 管理员应在到期日期之前续订令牌。

### <a name="remote-printing-over-a-secure-network----1709994----"></a>通过安全网络远程打印 <!-- 1709994  -->
使用 PrinterOn 的无线移动打印解决方案，用户将可以随时随地通过安全网络进行远程打印。 PrinterOn 将集成适用于 iOS 和 Android 的 Intune APP SDK。 将可以通过管理控制台中的 Intune“应用保护策略”边栏选项卡，将应用保护策略定目标到此应用。 最终用户将能够通过 Play 商店或 iTunes 下载“PrinterOn for Microsoft”应用，以便在 Intune 生态系统内使用。

### <a name="approve-the-company-portal-app-for-android-for-work---1797090---"></a>审核适用于 Android for Work 的“公司门户”应用 <!--1797090 -->
如果组织使用 Android for Work，将需要手动审核适用于 Android 的“公司门户”应用，以便它能够继续从托管的 Google Play 商店接收自动更新。

### <a name="faceid-on-ios-devices----1807377---"></a>iOS 设备上的 FaceID<!-- 1807377 -->
Intune 应用保护策略现在支持用于在 iOS 设备上控制 FaceID 的设置。 此设置适用于支持 FaceID 功能的设备（目前仅限 iPhone X）。 此设置与当前支持的 TouchID 控件相互独立。 组织可以选择是否信任 FaceID 作为有效的 PIN 提示，以将其作为 TouchID 控件的替代方式。

### <a name="microsoft-graph-api-for-intune---general-availability-----1833289---"></a>适用于 Intune 的 Microsoft Graph API - 正式版本 <!-- 1833289 -->
借助 Microsoft Graph 中的 Intune API，将可以编程方式访问数据和方法，从而自动执行 Intune 服务的管理操作。  通过这些 API 的正式版本，客户、合作伙伴和开发人员将能够利用这些 API 与内部或商业解决方案集成，这些解决方案需要或与 Intune 支持或其他通过 Microsoft Graph 提供的 Microsoft 服务支持相关。

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>应用保护策略<!-- 679615 -->
Intune 应用保护策略将提供创建默认全局策略的功能，以便快速对整个租户中所有用户启用保护。

### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>撤销 iOS 批量采购计划应用<!-- 820863 -->
对于具有一个或多个 iOS 批量采购计划 (VPP) 应用的给定设备，你将能够撤销相关的基于设备的应用许可证。 撤销应用许可证将不会从设备中卸载相关的 VPP 应用。 若要卸载 VPP 应用，必须将分配操作更改为“卸载”。 有关详细信息，请参阅[如何使用 Microsoft Intune 管理通过批量采购计划购买的 iOS 应用](vpp-apps-ios.md)。

### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>撤销 iOS 批量采购计划令牌的许可证<!-- 820870 -->
你将能够撤销给定 VPP 令牌的所有 iOS 批量采购计划 (VPP) 应用的许可证。

### <a name="new-ios-device-action------1244701---"></a>新的 iOS 设备操作<!-- 1244701 -->
你可以关闭 iOS 10.3 监督的设备。 此操作会立即关闭设备，而不会向最终用户发出警告。 当你在“设备”工作负载中选择设备时，可以在设备属性中找到“关闭（仅监督）”操作。


### <a name="intune-now-provides-the-account-move-operation-----1573558-1579830---"></a>Intune 现在提供帐户移动操作<!-- 1573558, 1579830 -->
“帐户移动”将租户从一个 Azure 扩展单元 (ASU) 迁移到另一个。 “帐户移动”可用于两种由客户启动的情景，当你调用请求它的 Intune 支持团队时，也可以是 Microsoft 驱动的情景，其中 Microsoft 需要对后端服务进行调整。 在“帐户移动”期间，租户进入只读模式 (ROM)。 在 ROM 期间，注册、重命名设备、更新符合性状态等服务操作将失败。




<!-- the following are present prior to 1712 -->
### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>使用内置应用类型将 Office 365 移动应用分配到 iOS 和 Android 设备<!-- 1332318 -->
借助内置应用类型，可更轻松地创建 Office 365 应用并将其分配到管理的 iOS 和 Android 设备。 这些应用包括 Word、Excel、PowerPoint 和 OneDrive 等 Office 365 应用。 可将特定应用分配到应用类型并编辑应用信息配置。


### <a name="assignment-conflict-resolution-has-changed-for-ios-store-apps----1480316---"></a>iOS 应用商店应用的分配冲突解决方法已发生更改 <!-- 1480316 -->
最终用户可能发现 iOS 应用商店应用可用性已发生更改。 目前，如果某个应用被分配到两个组并且在“必需和可用”和“不适用”之间存在冲突，则该应用会被解析为“必需和可用”。 更改后，遇到此冲突的应用会被解析为“不适用”。

对于某个应用被分配到多个组（具有不同应用意向）的情况，这项更改有助于避免混淆。

如果希望在 11 月服务发布前，在信息工作者门户和公司门户中使用应用，你有两个选择：

1. 删除组的“不适用”分配。
2. 创建一个新组，该组不包括已分配“必需和可用”意向的成员，然后将该组分配为“不适用”。

有关详细信息，请参阅[如何使用 Microsoft Intune 将应用分配到组](apps-deploy.md)。

> [!Note]
> 发布后，无法在 Intune 经典控制台中查看或修改移动设备管理 (MDM) 应用分配。 但是，可使用 Azure 控制台或 Intune 图形 API 分配应用。

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731---"></a>独立于 Android 设备管理 Android for Work 设备 <!-- 1490731 -->
Intune 支持独立于 Android 平台管理 Android for Work 设备的注册。 这些设置位于“设备注册” > “注册限制” > “设备类型限制”下。 （这些设置之前位于“设备注册” > “Android for Work 注册” > “Android for Work 注册设置”下。）

默认情况下，Android for Work 设备的设置与 Android 设备的设置相同。 但是，更改 Android for Work 设置后则不再相同。
 
如果阻止个人 Android for Work 注册，那么仅公司 Android 设备可注册为 Android for Work。

使用新设置时，请考虑下列各项：

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>如果之前从未载入 Android for Work 注册
默认设备类型限制将阻止新的 Android for Work 平台。 载入该功能后，可允许设备注册 Android for Work。 为此，请更改默认值或新建一个设备类型限制，取代默认设备类型限制。

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>如果已载入 Android for Work 注册
如果之前已载入，那么情况取决于所选设置：

| Setting | 默认设备类型限制中的 Android for Work 状态 | 注意 |
| --- | --- | --- |
| **将所有设备作为 Android 管理** | 已阻止 | 所有 Android 设备均不注册 Android for Work。 |
| 将受支持设备作为 Android for Work 管理 | ，然后用户才能访问 | 所有支持 Android for Work 的 Android 设备均须注册 Android for Work。 |
| **仅为这些组中的用户将受支持设备作为 Android for Work 管理** | 已阻止 | 创建单独的设备类型限制策略替代默认值。 此策略将之前选择的组定义为允许 Android for Work 注册。 允许所选组中的用户继续注册 Android for Work 设备。 所有其他用户则不能注册 Android for Work。 |

所有情况下都将保留预期规则。 对你来说，无需任何操作即可维护环境中的 Android for Work 全局或按组允许。

这些更改随 11 月更新一起推出，但可能需要一些时间才能在你的帐户上执行。 当帐户可使用这些更改时，你会在 Office 365 门户中收到确认通知。


### <a name="configure-an-ios-app-pin----1586774---"></a>配置 iOS 应用 PIN <!-- 1586774 -->
很快，便能要求目标 iOS 应用使用 PIN。 几天后，还可通过 Azure 门户配置 PIN 需求和到期日期。 需要时，用户必须设置并使用新的 PIN 才有权访问 iOS 应用。 只有使用 Intune App SDK 启用应用保护的 iOS 应用才支持此功能。

### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866--"></a>iOS 版公司门户应用的用户体验更新<!--1412866-->

我们将向 iOS 版公司门户应用发布用户体验主要更新。 此更新具有经过完全重新设计的视觉效果，包括现代化的外观和经提升的可用性和可访问性感受。 iOS 公司门户当前的所有功能都将保留。

我们将通过 Apple TestFlight 计划推出更新版 iOS 公司门户应用的预发布版本，用户可以使用并提供反馈。 若想参与 TestFlight，请在 https://aka.ms/intune_ios_cp_testflight 注册。 

![新 iOS 公司门户应用的预告图像](./media/ios-cp-app-redesign-1801-teaser.png)


<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory 网站可能需要 Intune Managed Browser 应用，并且支持 Managed Browser（公共预览版）的单一登录<!-- 710595 -->   
利用 Azure Active Directory (Azure AD)，可在移动设备上将对网站的访问限于 Intune Managed Browser 应用。 在 Managed Browser 中，网站数据可保持安全并且独立于最终用户的个人数据。 此外，Managed Browser 支持受 Azure AD 保护的站点的单一登录功能。 通过登录 Managed Browser，或在设备上将 Managed Browser 与由 Intune 管理的其他应用配合使用，用户无需输入凭据，Managed Browser 即可访问受 Azure AD 保护的公司站点。 此功能适用于 Outlook Web Access (OWA) 和 SharePoint Online 等站点，以及通过 Azure 应用代理访问的 Intranet 资源等其他公司站点。


<!-- the following are present prior to 1710 -->



### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>支持 Windows 10 版本升级策略 <!-- 903672(archived), 1119689 -->  
可以创建 Windows 10 版本升级策略，将 Windows 10 设备升级到 Windows 10 教育版、Windows 10 教育版 N、Windows 10 专业版、Windows 10 专业版 N、Windows 10 专业教育版和 Windows 10 专业教育版 N。有关 Windows 10 版本升级的详细信息，请参阅[如何配置 Windows 10 版本升级](edition-upgrade-configure-windows-10.md)。




<!-- the following are present prior to 1709 -->


### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Intune 应用保护和 Citrix MDX 开发工具 <!-- 709185 -->
可以同时使用 Citrix XenMobile MDX 和 Microsoft Intune 来管理设备和应用。 通过使用此方法，可在使用 Citrix mVPN 技术的同时通过 Intune 应用保护策略管理应用。

能够查找包含适用于iOS 和 Android 的 App Wrapping Tool 和 Intune App SDK 的代码存储库，同时还能集成 Citrix MDX mVPN 技术。




<!-- the following are present prior to 1711 -->


### <a name="redirecting-macos-users-to-our-new-company-portal-app---1380728--"></a>将 macOS 用户重定向到新公司门户应用<!--1380728-->   
当最终用户登录公司门户网站注册其 macOS 设备时，系统会将其定向到下载 macOS 版新公司门户应用的页面，以便完成此过程。 使用 OS X El Capitan 10.11 或更高版本的 macOS 设备会出现这种情况。 



<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>iOS 和 Android 的 Intune Managed Browser 支持<!-- 1374196 -->
自 2017 年 10 月起，Android 版 Intune Managed Browser 应用将仅支持运行 Android 4.4 及更高版本的设备。 iOS 上的 Intune Managed Browser 应用将仅支持运行 iOS 9.0 及更高版本的设备。 早期版本的 Android 和 iOS 将能够继续使用 Managed Browser，但不能安装新版本的应用，并且可能无法访问所有应用功能。 建议将这些设备更新为受支持的操作系统版本。


### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>改进了用户达到允许注册的最大设备数时提示的错误消息 <!-- 1270370 -->
使用 Android 设备的最终用户将不再看到通用错误消息，而将看到下面可操作的友好错误消息：“注册设备数已达到 IT 管理员允许的数量上限。请删除已注册的设备，或者向 IT 管理员寻求帮助。”




## <a name="notices"></a>通知

此时没有任何活动通知。




### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。
