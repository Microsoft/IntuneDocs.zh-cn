---
title: "新增功能 | Microsoft Docs"
description: "了解 Microsoft Intune 当月新增的功能和过去的版本"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 2e6452a066aa7eaeb295a3b531d83dc3b632bcf5
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---
# <a name="whats-new-in-microsoft-intune---april-2017"></a>Microsoft Intune 中的新增功能 - 2017 年 4 月
了解此版本 Microsoft Intune 中的新增功能。 你还可以发现需要计划的即将发生的更改，以及有关过去版本的信息。

> [!Note]
> 所有这些功能最终将支持混合客户部署（带 Intune 的 Configuration Manager）。 有关新的混合功能的详细信息，请查看[混合新增功能页](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。

## <a name="new-capabilities"></a>新功能

### <a name="myapps-available-for-managed-browser---822308-822303--"></a>MyApps 可用于托管浏览器 <!--822308, 822303-->

Microsoft MyApps 现在在托管浏览器中具有更好的支持。 面向管理的托管浏览器用户将直接转到 MyApps 服务，他们可在此处访问管理员预配的 SaaS 应用。 面向 Intune 管理的用户将能够继续从内置托管浏览器书签访问 MyApps。

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431-971473--"></a>托管浏览器和公司门户的新图标 <!--918433, 918431, 971473-->

托管浏览器正在接收 Android 和 iOS 版本应用的更新图标。 新图标将包含更新的 Intune 徽章，使其与企业移动性 + 安全性 (EM+S) 中的其他应用更加一致。 你可以在 [Intune 应用 UI 页面中的新增内容](whats-new-in-intune-app-ui.md)上查看 Managed Browser 的新图标。

公司门户还正在接收 Android、iOS 和 Windows 版本应用的更新图标，以提高与 EM + S 中其他应用的一致性。 这些图标将在 4 月至 5 月下旬在所有平台中逐步发布。

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Android 公司门户中的登录进度指示器 <!--953374-->

用户启动或恢复应用时，Android 公司门户应用的更新会显示进度指示器。 该指示器将依次显示新的状态，从“正在连接...”开始，然后“正在登录...”，最后“正在检查安全性要求...”，完成后即允许用户访问该应用。 可以在 [Intune 应用 UI 页面中的新增内容](whats-new-in-intune-app-ui.md)上查看适用于 Android 的公司门户应用的新屏幕。

### <a name="block-apps-from-accessing-sharepoint-online----679339---"></a>阻止应用访问 SharePoint Online<!-- 679339 -->

现在可以创建基于应用的条件访问策略以阻止应用（没有对这些应用适用的应用保护策略）访问 [SharePoint Online](/intune-classic/deploy-use/mam-ca-for-sharepoint-online)。 在基于应用程序的条件访问方案中，可以使用 Azure 门户指定想要有权访问 SharePoint Online 的应用。

### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>从适用于 iOS 的企业门户到 Outlook for iOS 的单一登录支持 <!--834012-->
如果用户在同一设备上使用同一帐户登录到适用于 iOS 的公司门户应用，则不再需要登录 Outlook 应用。 用户启动 Outlook 应用时，他们将能够选择自己的帐户并自动登录。 我们也正在致力于为其他 Microsoft 应用添加此功能。

### <a name="improved-status-messaging-in-the-company-portal-app-for-ios---744866--"></a>改进了适用于 iOS 的公司门户应用的状态消息传送 <!--744866-->
现在将在适用于 iOS 的公司门户应用中显示更具体的新错误消息，以提供有关设备状态的更多可访问信息。 这些错误情况以前包含在标题为“公司门户暂时不可用”的常规错误消息中。 此外，如果用户在没有 Internet 连接的情况下在 iOS 上启动公司门户，他们现在将在主页上看到显示“无Internet 连接”的持续状态栏。

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>改进 Windows 10 公司门户应用的应用安装状态 <!--676495-->

Windows 10 公司门户应用中开始的应用安装包括如下改进：
-    为 MSI 包提供更快的安装进度报告
-    为运行 Windows 10 周年更新和更高版本的设备上的现代应用提供更快的安装进度报告
-    为运行 Windows 10 周年更新和更高版本的设备上的现代应用安装提供了新的进度栏

你可以在 [Intune 应用 UI 页面中的新增功能](whats-new-in-intune-app-ui.md)上看到新的进度栏。

### <a name="bulk-enroll-windows-10-devices----747607---"></a>批量注册 Windows 10 设备 <!-- 747607 -->

现在可通过 Windows 配置设计器将大量运行 Windows 10 Creators 更新的设备联接到 Azure Active Directory 和 Intune。若要对 Azure AD 租户启用批量 MDM 注册 /intune-classic/deploy-use/bulk-enroll-windows)，请使用 Windows 配置设计器创建一个将设备加入 Azure AD 租户的配置包，然后将此包应用到需要进行批量注册和管理的公司所拥有设备。 将程序包应用到设备后，设备将加入 Azure AD 并注册 Intune，以供 Azure AD 用户登录。  Azure AD 用户是这些设备上的标准用户并接收分配的策略和必需的应用。 目前不支持自助服务和公司门户方案。

## <a name="notices"></a>通知

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接访问 Apple 注册方案<!--951869-->

对于在 2017 年 1 月之后创建的 Intune 帐户，Intune 支持在 Azure 预览门户中使用注册设备工作负荷直接访问 Apple 注册方案。 以前，仅能通过经典 Intune 门户中的链接访问 Apple 注册预览版。 2017 年 1 月之前创建的 Intune 帐户需要进行一次性迁移，然后才能使用 Azure 中的这些功能。 迁移的计划目前尚未公布，但详细信息将尽快发布。 强烈建议创建一个试用帐户，在现有帐户无法访问预览版时测试新体验。

### <a name="whats-coming-for-appx-in-intune-on-azure----1000270---"></a>Azure 上 Intune 的 Appx 的新增功能 <!-- 1000270 -->

在迁移到 Azure 上的 Intune 的过程中，我们做出了 3 个 appx 更改：

1. 在仅能部署到 MDM 注册的设备的经典 Intune 控制台中添加新的 appx 应用类型。
2. 重用现有的 appx 应用类型，以仅面向通过 Intune PC 代理托管的 PC。
3. 通过迁移将所有现有的 appxs 转换为 MDM appx。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？

这不会影响通过 Intune PC 代理管理的设备的任何现有部署。 但是，迁移后将无法将这些已迁移的 appx 部署到由先前未面向的 Intune PC 代理托管的任何新设备。

#### <a name="what-action-do-i-need-to-take"></a>我需要执行什么操作

迁移后，如果要进行新的 PC 部署，则需要将 appx 作为电脑 appx 再次上传。 若要了解详细信息，请参阅 [Intune 支持团队博客上的 ](https://aka.ms/appxchange)Azure 上 Intune 中的 Appx 更改。  

## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Azure 上的 Intune 管理体验公开预览版的新增功能<!--736542-->

在 2017 年初，我们会将完整管理体验迁移到 Azure 上，以便能够在可使用图形 API 进行扩展的新式服务平台上对核心 EMS 工作流进行强大且集成的管理。

新的试用租户将于本月开始在 Azure 门户中看到新管理体验的公开预览版。 在预览状态下，将以迭代方式交付现有 Intune 控制台的功能和奇偶校验。

Azure 门户中的管理体验将使用已公布的新分组和定向功能；当现有租户迁移到新的分组体验时，也会将你迁移，以预览租户上的新管理体验。 在此期间，如果想要在租户迁移之前测试或查看任何新功能，请注册新的 Intune 试用帐户或查阅[新文档](/intune/whats-new)。

> [!Note]
> 对于 Azure 门户预览版，我们将在本月推出更新。 但是，鉴于 Intune 服务的推出方式，所做的更改可能无法立即使用。  在新门户功能可用之前，必须按顺序更新服务的多个组件。 在本月晚些时候推出时可查找 Azure 门户预览版中的更改。 有关更改的完整列表，请参阅 [Microsoft Intune 预览版中的新增功能](/intune/whats-new)。

### <a name="administration-roles-being-replaced-in-azure-portal"></a>在 Azure 门户中被替换的管理角色

在 Intune 经典门户 (Silverlight) 中使用的现有移动应用程序管理 (MAM) 管理角色（参与者、所有者和只读）被替换为 Intune Azure 门户中一套完整的基于角色的新的管理控制方法 (RBAC)。 在迁移到 Azure 门户后，需要将管理员重新分配到这些新的管理角色。 有关 RBAC 和新角色的详细信息，请参阅 [Microsoft Intune 基于角色的访问控制](/intune/role-based-access-control)。

## <a name="whats-coming"></a>即将推出

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>改进了所有平台上跨公司门户应用的登录体验<!--User Story 1132123-->

我们宣布将在接下来的几个月内推出一项更新，该更新将提升适用于 Android、iOS 和 Windows 的 Intune 公司门户应用的登录体验。 当 Azure AD 进行此更改时，新的用户体验将自动在公司门户应用的所有平台上显现。 此外，用户可以使用生成的一次性验证码从其他设备立即登录到公司门户。 当用户需要在没有凭据的情况下登录时，这尤为有用。

可以在“应用 UI 中的新增功能”[](whats-new-in-intune-app-ui.md)页看到使用凭据进行登录的以前的登录体验和新登录体验，以及从其他设备进行登录的新登录体验的屏幕快照。

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>做好应对更改的计划：Intune 将更改 Intune 合作伙伴门户体验<!-- 1050016 -->

自 2017 年 5 月中旬起，我们将从 manage.microsoft.com 中删除 Intune 合作伙伴页面（从服务更新入手）。  

如果你是合作伙伴管理员，将无法再代表客户在 Intune 合作伙伴页面中查看内容和执行操作，而是需要在 Microsoft 的其他两个合作伙伴门户之一进行登录。

使用 [Microsoft 合作伙伴中心](https://partnercenter.microsoft.com/)和 [Microsoft Office 365 合作伙伴管理中心](https://portal.office.com/)，可以登录所管理的客户帐户。 作为合作伙伴，未来请使用其中一个网站管理客户。


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 将要求更新应用传输安全<!--748318-->

Apple 宣布他们将强制对应用程序传输安全 (ATS) 实施特定要求。 使用 ATS 对所有通过 HTTPS 的应用通信实施更严格的安全措施。 此更改会影响使用 iOS 公司门户应用的 Intune 客户。

我们通过强制实施新的 ATS 要求的 Apple TestFlight 计划提供了适用于 iOS 的公司门户应用的可用版本。 如果你想要试用以测试你的 ATS 符合性，请发送电子邮件至 <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a>，并提供你的名字、姓氏、电子邮件地址和公司名称。 请查看 [Intune 支持博客](https://aka.ms/compportalats)，了解更多详细信息。

### <a name="see-also"></a>另请参阅
* [Microsoft Intune 博客](http://go.microsoft.com/fwlink/?LinkID=273882)
* [云平台路线图](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Azure 预览版的新增功能](https://docs.microsoft.com/intune/whats-new)
* [What's new in the Company Portal UI](/intune-classic/whats-new/whats-new-in-company-portal-ui)（公司门户 UI 新增功能）
* [新增功能存档](whats-new-archive.md)

