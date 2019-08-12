---
title: Microsoft Intune 经典门户中的新增功能存档
description: 存档的 Microsoft Intune 新增功能公告
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/08/2017
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: d414295966580e0dd91ce2b94757509fd13bdfbe
ms.sourcegitcommit: e6edfbfd63dd7c2500ce1123205aa2af9a7e8e2e
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2019
ms.locfileid: "68783138"
---
# <a name="whats-new-in-the-intune-classic-portal---previous-months"></a>Intune 经典门户中的新增功能 - 前几个月

[!INCLUDE [classic-portal](./includes/classic-portal.md)]

此页列出了之前在[“新增功能”页](whats-new.md)中列出的适用于 Intune 经典门户的新功能和通告。

## <a name="april-2017"></a>2017 年 4 月

### <a name="new-capabilities"></a>新功能

#### <a name="myapps-available-for-managed-browser---822308-822303--"></a>MyApps 可用于 Managed Browser <!--822308, 822303-->

Microsoft MyApps 现在在托管浏览器中具有更好的支持。 面向管理的托管浏览器用户将直接转到 MyApps 服务，他们可在此处访问管理员预配的 SaaS 应用。 面向 Intune 管理的用户将能够继续从内置托管浏览器书签访问 MyApps。

#### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431-971473--"></a>Managed Browser 和公司门户的新图标 <!--918433, 918431, 971473-->

托管浏览器正在接收 Android 和 iOS 版本应用的更新图标。 新图标将包含更新的 Intune 徽章，使其与企业移动性 + 安全性 (EM+S) 中的其他应用更加一致。 你可以在 [Intune 应用 UI 页面中的新增内容](whats-new-app-ui.md)上查看 Managed Browser 的新图标。

公司门户还正在接收 Android、iOS 和 Windows 版本应用的更新图标，以提高与 EM + S 中其他应用的一致性。 这些图标将在 4 月至 5 月下旬在所有平台中逐步发布。

#### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Android 公司门户中的登录进度指示器 <!--953374-->

用户启动或恢复应用时，Android 公司门户应用的更新会显示进度指示器。 允许用户访问应用前，指示器将经历以下新状态：开始是“正在连接...”，然后是“正在登录...”，接下来是“正在查看安全要求...”。 可以在 [Intune 应用 UI 页面中的新增内容](whats-new-app-ui.md)上查看适用于 Android 的公司门户应用的新屏幕。

#### <a name="block-apps-from-accessing-sharepoint-online----679339---"></a>阻止应用访问 SharePoint Online <!-- 679339 -->

现在可以创建基于应用的条件访问策略，用于阻止未应用应用保护策略的应用访问 [SharePoint Online](app-based-conditional-access-intune-create.md)。 在基于应用的条件访问方案中，可以使用 Azure 门户，指定要向其授予对 SharePoint Online 访问权限的应用。

#### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>从适用于 iOS 的企业门户到 Outlook for iOS 的单一登录支持 <!--834012-->
如果用户在同一设备上使用同一帐户登录到适用于 iOS 的公司门户应用，则不再需要登录 Outlook 应用。 用户启动 Outlook 应用时，他们将能够选择自己的帐户并自动登录。 我们也正在致力于为其他 Microsoft 应用添加此功能。

#### <a name="improved-status-messaging-in-the-company-portal-app-for-ios---744866--"></a>改进了适用于 iOS 的公司门户应用的状态消息传送 <!--744866-->
现在将在适用于 iOS 的公司门户应用中显示更具体的新错误消息，以提供有关设备状态的更多可访问信息。 这些错误情况以前包含在标题为“公司门户暂时不可用”的常规错误消息中。 此外，如果用户在没有 Internet 连接的情况下在 iOS 上启动公司门户，他们现在将在主页上看到显示“无Internet 连接”的持续状态栏。

#### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>改进了适用于 Windows 10 的公司门户应用的应用安装状态 <!--676495-->

Windows 10 公司门户应用中开始的应用安装包括如下改进：
- 为 MSI 包提供更快的安装进度报告
- 为运行 Windows 10 周年更新和更高版本的设备上的现代应用提供更快的安装进度报告
- 为运行 Windows 10 周年更新和更高版本的设备上的现代应用安装提供了新的进度栏

你可以在 [Intune 应用 UI 页面中的新增功能](whats-new-app-ui.md)上看到新的进度栏。

#### <a name="bulk-enroll-windows-10-devices----747607---"></a>批量注册 Windows 10 设备 <!-- 747607 -->

现在可以使用 Windows 配置设计器 (WCD) 将运行 Windows 10 创意者更新的大量设备加入到 Azure Active Directory 和 Intune。 若要启用 Azure AD 租户的[批量 MDM 注册](windows-bulk-enroll.md)，请使用 Windows 配置设计器创建将设备加入你的 Azure AD 租户的预配程序包，并将程序包应用到你想要批量注册和管理的公司所有的设备。 将预配包应用到设备后，它们便会加入 Azure AD、注册使用 Intune，然后即可供 Azure AD 用户登录。  Azure AD 用户是这些设备上的标准用户，可接收分配的策略和所需的应用。 目前不支持自助服务和公司门户方案。

### <a name="whats-new-in-the-public-preview-of-intune-in-the-azure-portal--736542--"></a>Azure 门户中 Intune（公共预览版）的新增功能<!--736542-->

在 2017 年初，我们会将完整管理体验迁移到 Azure 上，以便能够在可使用图形 API 进行扩展的新式服务平台上对核心 EMS 工作流进行强大且集成的管理。

新的试用租户将于本月开始在 Azure 门户中看到新管理体验的公开预览版。 在预览状态下，将以迭代方式交付现有 Intune 控制台的功能和奇偶校验。

对于 Azure 门户中的管理体验，将使用已宣布的新分组和定位功能；将现有租户迁移为采用新的分组体验时，也会迁移为在租户上预览新管理体验。 在此期间，如果想要在租户迁移之前测试或查看任何新功能，请注册新的 Intune 试用帐户或查阅[新文档](whats-new.md)。

在[此处](whats-new.md)可找到 Azure 中 Intune 预览版的新增功能。

### <a name="notices"></a>通知

#### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接访问 Apple 注册方案 <!--951869-->

对于在 2017 年 1 月之后创建的 Intune 帐户，Intune 支持在 Azure 预览门户中使用注册设备工作负荷直接访问 Apple 注册方案。 以前，只能通过 Azure 门户中的链接访问 Apple 注册预览版。 2017 年 1 月之前创建的 Intune 帐户需要进行一次性迁移，然后才能使用 Azure 中的这些功能。 虽然迁移时间表尚未宣布，但会尽快发布详细信息。 强烈建议创建一个试用帐户，在现有帐户无法访问预览版时测试新体验。

#### <a name="whats-coming-for-appx-in-intune-in-the-azure-portal----1000270---"></a>Azure 门户中 Intune 的 Appx 新增功能 <!-- 1000270 -->

在迁移到 Azure 门户中 Intune 期间，我们做出了三项 appx 更改：

1. 在 Intune 控制台中添加新 appx 应用类型，这些类型只能部署到已进行 MDM 注册的设备。
2. 重用现有的 appx 应用类型，以仅面向通过 Intune PC 代理托管的 PC。
3. 通过迁移将所有现有的 appxs 转换为 MDM appx。

##### <a name="how-does-this-affect-me"></a>这对我有何影响？

这不会影响通过 Intune PC 代理管理的设备中的任何现有部署。 但是，迁移后将无法将这些已迁移的 appx 部署到由先前未面向的 Intune PC 代理托管的任何新设备。

##### <a name="what-action-do-i-need-to-take"></a>我需要执行什么操作

迁移后，如果要进行新的 PC 部署，则需要将 appx 作为电脑 appx 再次上传。 若要了解详细信息，请参阅 Intune 支持团队博客上的 [Azure 门户中 Intune 的 Appx 更改](https://aka.ms/appxchange)。  

#### <a name="administration-roles-being-replaced-in-azure-portal"></a>在 Azure 门户中被替换的管理角色

在 Intune 经典门户 (Silverlight) 中使用的现有移动应用程序管理 (MAM) 管理角色（参与者、所有者和只读）被替换为 Intune Azure 门户中一套完整的基于角色的新的管理控制方法 (RBAC)。 在迁移到 Azure 门户后，需要将管理员重新分配到这些新的管理角色。 有关 RBAC 和新角色的详细信息，请参阅 [Microsoft Intune 基于角色的访问控制](role-based-access-control.md)。

### <a name="whats-coming"></a>即将推出

#### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>改进了所有平台上跨公司门户应用的登录体验 <!--User Story 1132123-->

我们宣布将在接下来的几个月内推出一项更新，用以提升适用于 Android、iOS 和 Windows 的 Intune 公司门户应用的登录体验。 当 Azure AD 进行此更改时，新的用户体验将自动在公司门户应用的所有平台上显现。 此外，用户可以使用生成的一次性验证码从其他设备立即登录到公司门户。 当用户需要在没有凭据的情况下登录时，这尤为有用。

可以在[“应用 UI 中的新增功能”](whats-new-app-ui.md)页看到使用凭据进行登录以前的登录体验和新登录体验，以及从其他设备进行登录的新登录体验的屏幕快照。

#### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>做好应对更改的计划：Intune 将更改 Intune 合作伙伴门户体验 <!-- 1050016 -->

自 2017 年 5 月中旬起，我们将从 manage.microsoft.com 中删除 Intune 合作伙伴页面（从服务更新入手）。  

如果你是合作伙伴管理员，将无法再代表客户在 Intune 合作伙伴页面中查看内容和执行操作，而是需要在 Microsoft 的其他两个合作伙伴门户之一进行登录。

使用 [Microsoft 合作伙伴中心](https://partnercenter.microsoft.com/)和 [Microsoft 365 管理中心](https://admin.microsoft.com/)，可以登录所管理的客户帐户。 作为合作伙伴，未来请使用其中一个网站管理客户。


#### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 将要求更新应用程序传输安全性 <!--748318-->

Apple 宣布他们将强制对应用程序传输安全 (ATS) 实施特定要求。 使用 ATS 对所有通过 HTTPS 的应用通信实施更严格的安全措施。 此更改会影响使用 iOS 公司门户应用的 Intune 客户。

我们通过强制实施新的 ATS 要求的 Apple TestFlight 计划提供了适用于 iOS 的公司门户应用的可用版本。 如果你想要试用以测试你的 ATS 符合性，请发送电子邮件至 <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a>，并提供你的名字、姓氏、电子邮件地址和公司名称。 请查看 [Intune 支持博客](https://aka.ms/compportalats)，了解更多详细信息。

## <a name="march-2017"></a>2017 年 3 月

### <a name="new-capabilities"></a>新功能

#### <a name="support-for-skycure"></a>对 Skycure 的支持

现在可以使用条件访问（基于Skycure 执行的风险评估）控制移动设备对企业资源的访问。Skycure 是与 Microsoft Intune 集成的移动威胁防御解决方案。 基于从运行 Skycure 的设备收集的遥测评估风险，包括：

- 物理防御
- 网络防御
- 应用程序防御
- 漏洞防御

可根据通过 Intune 设备合规性策略启用的 Symantec Endpoint Protection Mobile (Skycure) 风险评估，配置 EMS 条件访问策略。 根据检测到的威胁，可使用这些策略允许或阻止不符合设备访问企业资源。 有关详细信息，请参阅 [Symantec Endpoint Protection Mobile 连接器](skycure-mobile-threat-defense-connector.md)。

#### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>适用于 Android 的公司门户应用的最新用户体验 <!--621622-->

适用于 Android 的公司门户应用将更新其用户界面，提供更现代的外观和感受以及更好的用户体验。 值得注意的更新包括：

- 颜色：公司门户选项卡标头将按 IT 定义的品牌进行着色。
- 应用：“应用”  选项卡上将更新“特色应用”  和“所有应用”  按钮。
- 搜索：“应用”  选项卡上的“搜索”  按钮现在是浮动的操作按钮。
- 导航应用：“所有应用”  视图以选项卡形式呈现出“特色”  、“所有”  和“分类”  ，便于导航。
- 支持：更新“我的设备”  和“联系 IT”  选项卡以提高可读性。

有关这些更改的详细信息，请参阅 [Intune 最终用户应用的 UI 更新](whats-new-app-ui.md)。

#### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>非受管理设备可访问已分配的应用 <!--664691-->

公司门户网站上的设计更改之一是，iOS 和 Android 用户能够在其非托管设备上安装分配到的“可用且无需注册”设备。 用户可使用其 Intune 凭据登录到公司门户网站，并查看分配到的应用列表。 “可用且无需注册”应用的应用包可通过公司门户网站进行下载。 需要注册才能安装的应用不受此更改影响，如果用户想安装这类应用，则会提示用户注册其设备。

#### <a name="signing-script-for-windows-10-company-portal---941642--"></a>对 Windows 10 公司门户的脚本进行签名 <!--941642-->

如果你需要下载和旁加载 Windows 10 公司门户应用，现在可以使用脚本简化并精简组织的应用签名过程。   要下载脚本及其使用说明，请参阅 TechNet 库中的 [Windows 10 公司门户的 Microsoft Intune 签名脚本](https://aka.ms/win10cpscript)。 有关此公告的详细信息，请参阅 Intune 支持团队博客上的[更新 Windows 10 公司门户应用](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/)。


### <a name="notices"></a>通知

#### <a name="support-for-ios-103"></a>对 iOS 10.3 的支持

IOS 10.3 发行版于 2017 年 3 月 27 面向 iOS 用户推出。 所有现有的 Intune MDM 和 MAM 方案与最新版本的 Apple 操作系统兼容。 在用户将设备和应用升级到 iOS 10.3 时，预计当前可用于管理 iOS 设备的所有现有 Intune 功能都将继续工作。

目前没有任何要共享的已知问题。 如果你遇到有关 iOS 10.3 的任何问题，请随时联系 [Intune 支持团队](get-support.md)。

#### <a name="improved-support-for-android-users-based-in-china---720444--"></a>改进了对身处中国的 Android 用户的支持 <!--720444-->

由于中国地区没有 Google Play 商店，Android 设备必须从中国的市场获取应用。 公司门户将支持此工作流，方法是将中国的 Android 用户重定向为从本地应用商店下载公司门户和 Outlook 应用。 对于移动设备管理和移动应用程序管理，此举将改善启用条件性访问策略时的用户体验。 下列中文应用商店中提供适用于 Android 的公司门户和 Outlook 应用：

- [百度](https://go.microsoft.com/fwlink/?linkid=836946)
- [小米](http://en.miui.com/thread-469541-1-1.html)
- [腾讯](https://go.microsoft.com/fwlink/?linkid=836949)
- [华为](https://go.microsoft.com/fwlink/?linkid=836948)
- [豌豆荚](https://go.microsoft.com/fwlink/?linkid=836950)

#### <a name="best-practice-make-sure-your-company-portal-apps-are-up-to-date---879465--"></a>最佳做法：确保公司门户应用处于最新状态 <!--879465-->

2016 年 12 月，我们发布了一个更新，在一组用户注册 iOS、Android、Windows 8.1 + 或 Windows Phone 8.1 + 设备时强制进行多重身份验证 (MFA)。 如果没有适用于 Android (v5.0.3419.0+) 和 iOS (v2.1.17+) 的公司门户应用的某些基线版本，此功能将无法正常运行。

通过将新函数添加到控制台和所有受支持平台上的公司门户应用，Microsoft 不断改进 Intune。 因此，Microsoft 仅发布针对我们在当前版本公司门户应用中所发现问题的修补程序。 因此建议使用最新版本的公司门户应用以获取最佳用户体验。

>[!Tip]
> 让用户设置其设备以在相应的应用商店中自动更新应用。 如果你使 Android 公司门户应用在网络共享上可用，可以从 [Microsoft 下载中心](https://www.microsoft.com/download/details.aspx?id=49140)下载最新版本。

#### <a name="microsoft-teams-is-now-enabled-for-mam-on-ios-and-android"></a>现已在 iOS 和 Android 上为 MAM 启用 Microsoft Teams

Microsoft 已宣布发布 Microsoft Teams 的通用版本。 适用于 iOS 和 Android 的更新的 Microsoft Teams 应用现已具备 Intune 移动应用管理 (MAM) 功能，让你的团队可以自由地跨设备工作，同时确保对话和公司数据始终受到保护。 有关详细信息，请参阅企业移动性和安全性博客上的 [Microsoft Teams 公告](https://blogs.technet.microsoft.com/enterprisemobility/2017/03/14/microsoft-teams-is-now-generally-available-and-mam-enabled-on-ios-and-android/)。


## <a name="february-2017"></a>2017 年 2 月

### <a name="new-capabilities"></a>新功能

### <a name="modernizing-the-company-portal-website---753980--"></a>公司门户网站现代化 <!--753980-->
公司门户网站将支持面向不具有托管设备的用户的应用。 此网站将使用新的撞色配色方案、动态图和“汉堡菜单” ![（汉堡菜单的小图，该图片现已添加到公司门户网站左上角，](./media/CP_hamburger_menu.png)。

### <a name="notices"></a>通知

#### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>iOS 设备的组迁移将不需要对组或策略进行任何更新 <!--898837-->
对于所有由公司设备注册配置文件预分配的 Intune 设备组，在迁移到 Azure Active Directory 设备组期间，都将根据公司设备注册配置文件的名称在 AAD 中创建相应的动态设备组。 这样可以确保设备在注册时自动进行分组，并接收与原始 Intune 组相同的策略和应用。

租户进入分组和设定目标的迁移阶段时，Intune 将自动创建一个动态 AAD 组，该组与公司设备注册配置文件面向的 Intune 组相对应。 Intune 管理员删除目标 Intune 组时，相应的动态 AAD 组不会被删除。 组成员和动态查询将被清除，但该组本身将继续保留，直到 IT 管理员通过 AAD 门户将其删除。

同样，如果 IT 管理员更改了公司设备注册配置文件面向的 Intune 组，Intune 将创建新的动态组来反映新的配置文件分配，但不会删除为旧分配创建的动态组。

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>默认通过 Windows 设置管理 Windows 桌面设备 <!--663050-->
用于注册 Windows 10 桌面版的默认行为发生了变化。 新的注册将遵循典型 MDM 代理注册流程，而非通过电脑代理进行。 公司门户网站将为 Windows 10 桌面用户提供注册说明，指导他们完成将 Windows 10 桌面计算机添加为移动设备的过程。 这不会影响当前已注册的电脑，[如果愿意](manage-windows-pcs-with-microsoft-intune.md)，组织仍可使用电脑代理来管理 Windows 10 桌面。

#### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>改进对选择性擦除的移动应用管理支持 <!--581242-->
如果由于“擦除应用数据前的脱机时间间隔”策略导致自动删除了工作或学校数据，则将为最终用户提供有关如何重新获得这些数据的访问权限的其他指导。<!--, or the removal of the Intune Company Portal on Android.-->

#### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>适用于 iOS 的公司门户链接在应用内打开 <!--665954-->
iOS 版公司门户应用内的链接（包括文档和应用链接）将通过 Safari 的应用内视图直接在公司门户应用中打开。 此更新将与 1 月的服务更新分开提供。

#### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Windows 设备的新 MDM 服务器地址 <!--893007-->
Windows 和 Windows Phone 用户如果输入 __manage.microsoft.com__ 作为 MDM 服务器地址（出现提示时），尝试注册设备时将失败。 MDM 服务器地址已从 __manage.microsoft.com__ 更改为 __enrollment.manage.microsoft.com__ 。 通知用户在注册 Windows 和/或 Windows Phone 时，如果出现提示，请使用 __enrollment.manage.microsoft.com__ 作为 MDM 服务器地址。 无需更改 CNAME 设置。 有关此更改的详细信息，请访问[aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange)。

#### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>适用于 Android 的公司门户应用的最新用户体验 <!--621622-->
从 3 月开始，Android 适用的公司门户应用将按照[材料设计指南](https://material.io/guidelines/material-design/introduction.html)来打造更具现代感的外观。 改进的用户体验包括：

* __颜色__ ：可以根据自定义调色板对选项卡标头着色。
* __界面__ ：“应用”选项卡上已更新了“特色应用”和“所有应用”按钮。“搜索”按钮现在是浮动的操作按钮。
* __导航__ ：“所有应用”以选项卡形式呈现出“特色”、“所有”和“分类”视图，便于导航。
* __服务__ ：“我的设备”和“联系 IT”选项卡提高了可读性。

可在 [UI 更新页](whats-new-app-ui.md)上查看最初和最后的图像。

### <a name="associate-multiple-management-tools-with-the-microsoft-store-for-business---926135--"></a>将多个管理工具与适用于企业的 Microsoft Store 关联 <!--926135-->
使用多个管理工具部署适用于企业的 Microsoft 应用商店时，以前只能将一个管理工具与适用于企业的 Microsoft 应用商店关联。 现在可以将多个管理工具与应用商店相关联，例如 Intune 和 Configuration Manager。 有关详细信息，请参阅[使用 Microsoft Intune 管理从适用于企业的 Microsoft 应用商店中购买的应用](windows-store-for-business.md)。

## <a name="whats-new-in-the-public-preview-of-intune-in-the-azure-portal---736542--"></a>Azure 门户中 Intune（公共预览版）的新增功能 <!--736542-->

在 2017 年初，我们会将完整管理体验迁移到 Azure 上，以便能够在可使用图形 API 进行扩展的新式服务平台上对核心 EMS 工作流进行强大且集成的管理。

新的试用租户将于本月开始在 Azure 门户中看到新管理体验的公开预览版。 在预览状态下，将以迭代方式交付现有 Intune 控制台的功能和奇偶校验。

对于 Azure 门户中的管理体验，将使用已宣布的新分组和定位功能；将现有租户迁移为采用新的分组体验时，也会迁移为在租户上预览新管理体验。 在此期间，如果想要在租户迁移之前测试或查看任何新功能，请注册新的 Intune 试用帐户或查阅[新文档](whats-new.md)。

在[此处](whats-new.md)可找到 Azure 中 Intune 预览版的新增功能。

## <a name="january-2017"></a>2017 年 1 月

### <a name="new-capabilities"></a>新功能

#### <a name="in-console-reports-for-mam-without-enrollment---677961--"></a>无需注册的 MAM 控制台内报表 <!--677961-->
已为已注册设备和未注册设备添加了新的应用保护报表。 详细了解如何[使用 Intune 监视移动应用管理策略](app-protection-policies-monitor.md)。

#### <a name="android-711-support---694397--"></a>Android 7.1.1 支持 <!--694397-->
Intune 现在完全支持并可管理 Android 7.1.1。

#### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them---unknown--"></a>解决 iOS 设备处于非活动状态，或管理控制台不能与其通信的问题 <!--unknown-->
如果用户的设备失去与 Intune 的联系，可向其提供新的故障排除步骤，帮助他们重新获得公司资源的访问权限。 请参阅[设备处于非活动状态，或管理控制台不能与其通信](troubleshoot-device-enrollment-in-intune.md#devices-are-inactive-or-the-admin-console-cant-communicate-with-them)。

### <a name="notices"></a>通知

#### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>默认通过 Windows 设置管理 Windows 桌面设备 <!--663050-->
用于注册 Windows 10 桌面版的默认行为发生了变化。 新的注册将遵循典型 MDM 代理注册流程，而非通过电脑代理进行。

公司门户网站将为 Windows 10 桌面用户提供注册说明，指导他们完成将 Windows 10 桌面计算机添加为移动设备的过程。 这不会影响当前已注册的电脑，[如果愿意](manage-windows-pcs-with-microsoft-intune.md)，组织仍可使用电脑代理来管理 Windows 10 桌面。

#### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>改进对选择性擦除的移动应用管理支持 <!--581242-->
如果由于“擦除应用数据前的脱机时间间隔”策略导致自动删除了工作或学校数据，则将为最终用户提供有关如何重新获得这些数据的访问权限的其他指导。<!--, or the removal of the Intune Company Portal on Android.-->

#### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>适用于 iOS 的公司门户链接在应用内打开 <!--665954-->
iOS 版公司门户应用内的链接（包括文档和应用链接）将通过 Safari 的应用内视图直接在公司门户应用中打开。 此更新将与 1 月的服务更新分开提供。

#### <a name="modernizing-the-company-portal-website---753980--"></a>公司门户网站现代化 <!--753980-->
从 2 月开始，公司门户网站将支持针对不具有托管设备的用户的应用。 此网站将使用新的撞色配色方案、动态图和“汉堡菜单” ![公司门户网站汉堡菜单](./media/CP_hamburger_menu.png)。

#### <a name="new-documentation-for-app-protection-policies---583398--"></a>新的应用保护策略文档 <!--583398-->
针对想要使用 Intune 应用包装工具或 Intune App SDK 在 iOS 和 Android 应用中启用应用保护策略（称为 MAM 策略）的管理员和应用开发人员，我们更新了相关文档。

已更新以下文章：

* [决定如何使用 Microsoft Intune 为移动应用程序管理准备应用](apps-prepare-mobile-application-management.md)
* [使用 Intune 应用包装工具为移动应用程序管理准备 iOS 应用](app-wrapper-prepare-ios.md)
* [Microsoft Intune App SDK 入门](app-sdk-get-started.md)
* [Intune App SDK for iOS 开发人员指南](app-sdk-ios.md)

以下文章是对文档库新增的内容：

* [Intune App SDK Cordova 插件](app-sdk-cordova.md)
* [Intune App SDK Xamarin 组件](app-sdk-xamarin.md)

#### <a name="progress-bar-when-launching-the-company-portal-on-ios---665978--"></a>在 iOS 上启动公司门户时的进度栏 <!--665978-->
IOS 版公司门户在启动屏幕上引入了一个进度栏，为用户提供所发生的加载进程的信息。 进度栏将逐步推出，以替代旋转图标。 这意味着某些用户将看到新的进度栏，而其他用户会继续看到旋转图标。

## <a name="december-2016"></a>2016 年 12 月

### <a name="public-preview-of-intune-in-the-azure-portal--736542--"></a>Azure 门户中 Intune（公共预览版）<!--736542-->
在 2017 年初，我们会将完整管理体验迁移到 Azure 上，以便能够在可使用图形 API 进行扩展的新式服务平台上对核心 EMS 工作流进行强大且集成的管理。 在正式发布此面向所有 Intune 租户的门户之前，我们高兴地宣布将在本月晚些时候向所选租户推出此新的管理体验的预览版。

Azure 门户中的管理体验将使用已公布的新分组和定向功能；当现有租户迁移到新的分组体验时，也会将你迁移，以预览租户上的新管理体验。 同时，在[新文档](/intune/what-is-intune)中查找应用商店提供的用于 Azure 门户中的 Microsoft Intune 的应用的更多信息。

__Azure 门户（公开预览版）中的电信费用管理集成__ <!--747605-->
现在，我们将开始在 Azure 门户中预览与第三方电信费用管理 (TEM) 服务的集成。 可以使用 Intune 强制实施对国内和漫游数据使用的限制。 我们将使用 [Saaswedo](http://www.saaswedo.com/) 开始这些集成。 若要在试用租户中启用此功能，请[联系 Microsoft 支持](get-support.md)。

### <a name="new-capabilities"></a>新功能

__跨所有平台的多重身份验证__ <!--747590-->
现在，可以通过在 Azure Active Directory 中的 Microsoft Intune 注册应用程序上配置 MFA，在所选用户组从 Azure 管理门户注册 iOS、Android、Windows 8.1+ 或 Windows Phone 8.1+ 设备时，对其强制执行多重身份验证 (MFA) 。

__限制移动设备注册的功能__ <!--747596-->
Intune 新增了注册限制，可控制允许注册的移动设备平台。 Intune 将移动设备平台分为 iOS、macOS，Android、Windows 和 Windows Mobile。
* 限制移动设备注册不会限制电脑客户端注册。
* 阻止个人自有设备的注册有一个附加选项，该选项仅适用于 iOS。

Intune 将所有新设备都标记为个人所有，除非 IT 管理员将设备标记为公司所有，如[本文](device-enrollment.md)所述。

### <a name="notices"></a>通知

__注册移动到 Azure 门户时的多重身份验证__ <!--VSO 750545-->
以前，管理员会进入 Intune 控制台或 Configuration Manager（2016 年 10 月之前的版本）控制台，以设置 MFA 用于 Intune 注册。 通过此更新的功能，现在可使用 Intune凭据登录 [Microsoft Azure 门户](https://manage.windowsazure.com)，并通过 Azure AD 配置 MFA 设置。 在[此处](https://aka.ms/mfa_ad)了解详细信息。

__适用于 Android 的公司门户应用现已在中国推出__  <!--VSO 658093-->
我们将发布 Android 版公司门户应用，以供中国地区下载。 由于中国地区没有 Google Play 商店，Android 设备必须从中国的应用市场获取应用。 可在以下应用商店下载用于 Android 的公司门户应用：
* [百度](https://go.microsoft.com/fwlink/?linkid=836946)
* [华为](https://go.microsoft.com/fwlink/?linkid=836948)
* [腾讯](https://go.microsoft.com/fwlink/?linkid=836949)
* [豌豆荚](https://go.microsoft.com/fwlink/?linkid=836950)
* [小米](http://en.miui.com/thread-469541-1-1.html)

Android 版公司门户应用使用 Google Play Services 与 Microsoft Intune 服务进行通信。 由于 Google Play Services 尚未在中国推出，因此执行以下任何任务最高可能需要 8 个小时才能完成。 

|Intune 管理控制台| Android 适用的 Intune 公司门户应用 |Intune 公司门户网站|   
|---|---|---|
|完全擦除| 移除远程设备| 移除设备（本地和远程）|
|选择性擦除| 重置设备| 重置设备|
|新的或更新的应用部署| 安装可用的业务线应用| 设备密码重置|
|远程锁定|||
|密码重置|||

### <a name="deprecations"></a>弃用功能

__Firefox 不再支持 Silverlight__ <!--VSO TBA-->
Mozilla 将在 52 版 [Firefox 浏览器](https://www.mozilla.org/firefox)中移除对 Silverlight 的支持，此更新于 2017 年 3 月生效。 因此，无法使用高于 51 版的 Firefox 登录现有 Intune 控制台。 我们建议使用 Internet Explorer 10 或 11，或者 [52 版之前的 Firefox](https://ftp.mozilla.org/pub/firefox/releases/) 访问管理控制台。 Intune 向 Azure 门户的过渡允许其支持多种[新式浏览器](/azure/azure-preview-portal-supported-browsers-devices)，而无需依赖于 Silverlight。

__删除 Exchange Online 移动版收件箱策略__ <!--770687-->
从 12 月开始，管理员将无法再在 Intune 控制台中查看或配置 Exchange Online (EAS) 移动版邮箱策略。 此更改将在 12 月和 1 月向所有 Intune 租户推出。 所有现有策略将保持配置状态；若要配置新策略，请使用 Exchange 命令行管理程序。 可在[此处](https://technet.microsoft.com/library/bb123783%28v=exchg.150%29.aspx)找到详细信息。

__Android 不再支持 Intune AV 播放器、图像查看器和 PDF 查看器应用__ <!--747553-->
从 2016 年 12 月中旬起，用户将无法继续使用 Intune AV 播放器、图像查看器和 PDF 查看器应用。 这些应用已替换为 Azure 信息保护应用。 可在[此处](/information-protection/rms-client/mobile-app-faq)查找有关 Azure 信息保护应用的详细信息。

## <a name="november-2016"></a>2016 年 11 月

### <a name="new-capabilities"></a>新功能

__适用于 Windows 10 设备的新 Microsoft Intune 公司门户__ Microsoft 将发布[适用于 Windows 10 设备的新 Microsoft Intune 公司门户](https://www.microsoft.com/store/apps/9wzdncrfj3pz)。 此应用利用了新 Windows 10 Universal 格式，将在应用内为用户提供更新的用户体验，且跨所有 Windows 10 设备（PC 和移动设备等）提供相同的体验，同时还将保持现有的一切功能。

新应用还允许用户们在 Windows 10 设备上利用传统平台功能，例如单一登录 (SSO) 和基于证书的身份验证。 此应用将作为对现有 Windows 8.1 公司门户和 Windows Phone 8.1 公司门户（安装自 Microsoft 应用商店）的升级而提供。 有关详细信息，请转到 [aka.ms/intunecp_universalapp](https://aka.ms/intunecp_universalapp)。

> [!IMPORTANT]
> __Intune 和 Android for Work 上的更新__ 虽然可通过“必需”  操作部署 Android for Work 应用，但如果已将 Intune 组迁移至新的 Azure AD 组体验，则只可以将应用部署为“可用”  。

__Intune App SDK for Cordova 插件现在支持 MAM（无需注册设备）__ 应用开发人员现在可以使用 Intune App SDK for Cordova 插件启用 MAM 功能，且无需在适用于 Android 和 iOS 的基于 Cordova 的应用中注册设备。 可在[此处](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)找到 Intune App SDK for Cordova 插件。

__Intune App SDK Xamarin 组件现在支持 MAM（无需注册设备）__ 应用开发人员现在可以使用 Intune App SDK Xamarin 组件启用 MAM 功能，且无需在适用于 Android 和 iOS 的基于 Xamarin 的应用中注册设备。 可在[此处](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)找到 Intune App SDK Xamarin 组件。

### <a name="notices"></a>通知

__上传 Symantec 签名证书不再需要已签名的 Windows Phone 8 公司门户__ 上传 Symantec 签名证书不再需要已签名的 Windows Phone 8 公司门户应用。 可以独立上传该证书。

### <a name="deprecations"></a>弃用功能

__对 Windows Phone 8 公司门户的支持__ 将取消对 Windows Phone 8 公司门户的支持。 2016 年 10 月弃用了对 Windows Phone 8 和 WinRT 平台的支持。 2016 年 10 月弃用了对 Windows 8 公司门户的支持。


## <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。
