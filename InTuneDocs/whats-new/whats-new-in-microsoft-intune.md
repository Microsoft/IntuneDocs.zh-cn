---
title: "新增功能 | Microsoft Docs"
description: "了解 Microsoft Intune 当月和往期版本中的新增功能"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 04/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: 0dc3fd3b4cc355bc95677ca648efdee07d1066b2
ms.contentlocale: zh-cn
ms.lasthandoff: 04/24/2017


---
# <a name="whats-new-in-microsoft-intune---april-2017"></a>Microsoft Intune 中的新增功能 - 2017 年 4 月
了解此版本 Microsoft Intune 中的新增功能。 还可以了解需要提前计划的即将发生的更改，以及往期版本的相关信息。

> [!Note]
> 混合客户部署（含 Intune 的 Configuration Manager）最终将会支持所有这些功能。 若要详细了解新增的混合功能，请参阅[混合版本中的新增功能](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)页。

## <a name="new-capabilities"></a>新功能

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>改进了适用于所有平台的公司门户应用的登录体验 <!--User Story 1132123-->

我们一直在不断改进适用于 Android、iOS 和 Windows 的 Intune 公司门户应用的登录体验。 在 Azure AD 执行此更改后，适用于所有平台的公司门户应用的用户体验都会自动焕然一新。 此外，用户现在还可以使用生成的一次性代码从其他设备登录公司门户。 当用户需要在不使用凭据的情况下登录时，此功能就特别有用。

有关旧登录体验、使用凭据时的新登录体验以及从其他设备登录时的新登录体验的屏幕截图，请参阅[应用 UI 中的新增功能](whats-new-in-intune-app-ui.md)页面。

### <a name="myapps-available-for-managed-browser---822308-822303--"></a>适用于 Managed Browser 的 MyApps <!--822308, 822303-->

现在 Microsoft MyApps 改进了 Managed Browser 内部的支持。 不作为管理目标的 Managed Browser 用户将直接转至 MyApps 服务，这些用户可以在其中访问管理员预配的 SaaS 应用。 作为 Intune 管理目标的用户将可以继续从内置 Managed Browser 书签访问 MyApps。

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431-971473--"></a>Managed Browser 和公司门户的新图标 <!--918433, 918431, 971473-->

Managed Browser 将获得该应用的 Android 和 iOS 版的更新图标。 新图标将包含更新的 Intune 徽章，使其与企业移动性 + 安全性 (EM+S) 中的其他应用更为一致。 可以在 [Intune 应用 UI 页中的新增功能](whats-new-in-intune-app-ui.md)中查看 Managed Browser 的新图标。

公司门户还将获得该应用的 Android、iOS 和 Windows 版的更新图标，以改进与 EM+S 中的其他应用的一致性。 这些图标将于四月至五月底逐步在平台上发布。

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Android 公司门户中的登录进度指示器 <!--953374-->

用户启动或重启应用时，Android 公司门户应用的更新程序将显示登录进度指示器。 允许用户访问应用前，指示器将经历以下新状态：开始是“正在连接...”，然后是“正在登录...”，接下来是“正在查看安全要求...”。 可以在 [Intune 应用 UI 页中的新增功能](whats-new-in-intune-app-ui.md)中查看适用于 Android 的公司门户应用的新屏幕。

### <a name="block-apps-from-accessing-sharepoint-online----679339---"></a>阻止应用访问 SharePoint Online <!-- 679339 -->

现在可以创建基于应用的条件访问策略来阻止未向其实施应用保护策略的应用访问 [SharePoint Online](/InTune/deploy-use/mam-ca-for-sharepoint-online)。 在基于应用的条件访问方案中，可以指定想要让其具备使用 Azure 门户访问 SharePoint Online 的权限的应用。

### <a name="bulk-enroll-windows-10-devices----747607---"></a>批量注册 Windows 10 设备 <!-- 747607 -->

现在，可以使用 Windows 配置设计器 (WCD)，将运行 Windows 10 创意者更新的大量设备加入 Azure Active Directory 和 Intune。 若要为 Azure AD 租户启用[批量 MDM 注册](/intune/deploy-use/bulk-enroll-windows)，请创建一个预配包，以使用 Windows 配置设计器将设备加入 Azure AD 租户，然后将预配包应用到要批量注册并管理的企业拥有的设备。 将预配包应用到设备后，它们便会加入 Azure AD、注册使用 Intune，然后即可供 Azure AD 用户登录。  Azure AD 用户是这些设备上的标准用户，可接收分配的策略和所需的应用。 暂不支持执行自助式操作和使用公司门户。

## <a name="notices"></a>通知

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接访问 Apple 注册方案 <!--951869-->

对于 2017 年 1 月之后创建的 Intune 帐户，Intune 允许在 Azure 预览门户中使用“注册设备”工作负载直接访问 Apple 注册方案。 以前，Apple 注册预览只能通过经典 Intune 门户中的链接进行访问。 在 2017 年 1 月之前创建的 Intune 帐户必须先进行一次性迁移，然后才能在 Azure 中使用这些功能。 虽然迁移时间表尚未宣布，但会尽快发布详细信息。 如果现有帐户无法访问注册预览，强烈建议创建试用帐户来测试新体验。

### <a name="whats-coming-for-appx-in-intune-on-azure----1000270---"></a>Azure 上的 Intune 中即将推出的 Appx 新功能 <!-- 1000270 -->

在迁移到 Azure 上的 Intune 期间，我们在执行三项 appx 更改：

1. 在经典 Intune 控制台中添加新的 appx 应用类型，这种类型只能部署到已注册 MDM 的设备。
2. 重新利用现有的 appx 应用类型，使其仅定位通过 Intune PC 代理管理的 PC。
3. 通过迁移将现有全部 appx 转换成 MDM appx。

#### <a name="how-does-this-affect-me"></a>这会对我产生哪些影响？

这不会影响通过 Intune PC 代理管理的设备中的任何现有部署。 不过，迁移后，将无法把已迁移的 appx 部署到任何通过 Intune PC 代理管理且以前未定位的新设备。

#### <a name="what-action-do-i-need-to-take"></a>我需要采取哪些措施

迁移后，如果要进行新的 PC 部署，则需要再次将 appx 重新上载为 PC appx。 若要了解详细信息，请参阅 Intune 支持团队博客上的 [Azure 上的 Intune 中推出的 Appx 更改](https://aka.ms/appxchange)。  


## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Azure 上 Intune 管理体验的公开预览版的新增功能 <!--736542-->

在 2017 年年初，我们将会把管理体验完全迁移到 Azure 上，以便能够在可使用 Graph API 进行扩展的新式服务平台上对核心 EMS 工作流进行强大的集成式管理。

从本月开始，新建的试用租户将可以在 Azure 门户中看到新管理体验的公开预览版。 在预览状态下，将以循环访问方式交付功能，以及与现有 Intune 控制台等同的体验。

对于 Azure 门户中的管理体验，将使用已宣布的新分组和定位功能；将现有租户迁移为采用新的分组体验时，也会迁移为在租户上预览新管理体验。 与此同时，如果要在租户迁移完成之前测试或查看任何新功能，请注册新的 Intune 试用帐户或参阅[新文档](/intune-azure/introduction/whats-new)。

> [!Note]
> 对于 Azure 门户预览版，我们即将推出本月的更新。 不过，鉴于 Intune 服务的推出方式，更改可能无法立即生效。  必须先依序更新服务的多个组件，然后才能使用新门户功能。 请查看本月晚些时候推出的 Azure 门户预览版更改。 有关更改的完整列表，请参阅 [Microsoft Intune 预览版中的新增功能](/intune-azure/introduction/whats-new)。

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Azure 门户将替换管理角色

Intune 经典门户 (Silverlight) 中使用的现有移动应用管理 (MAM) 管理角色（参与者、所有者和只读）将替换成 Intune Azure 门户中一整套新的基于角色的管理控制 (RBAC) 角色。 迁移到 Azure 门户后，便需要向管理员重新分配这些新的管理角色。 有关 RBAC 和新角色的详细信息，请参阅 [Microsoft Intune 基于角色的访问控制](/intune-azure/access-control/role-based-access-control)。


## <a name="whats-coming"></a>即将推出

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>做好应对更改的计划：Intune 将更改 Intune 合作伙伴门户体验<!-- 1050016 -->

自 2017 年 5 月中旬起，我们将从 manage.microsoft.com 中删除 Intune 合作伙伴页面（从服务更新入手）。  

如果你是合作伙伴管理员，将无法再代表客户在 Intune 合作伙伴页面中查看内容和执行操作，而是需要在 Microsoft 的其他两个合作伙伴门户之一进行登录。

使用 [Microsoft 合作伙伴中心](https://partnercenter.microsoft.com/)和 [Microsoft Office 365 合作伙伴管理中心](https://portal.office.com/)，可以登录所管理的客户帐户。 作为合作伙伴，未来请使用其中一个网站管理客户。 


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 要求针对应用传输安全进行更新 <!--748318-->

自 2017 年春季起，Apple 宣布将强制实施应用传输安全 (ATS) 特定要求。 ATS 用于对所有通过 HTTPS 的应用通信强制实施更严格的安全措施。 此更改会影响使用 iOS 公司门户应用的 Intune 客户。 请参阅 [Intune 支持博客](https://aka.ms/compportalats)，了解更多详情。

### <a name="see-also"></a>另请参阅
* [Microsoft Intune 博客](http://go.microsoft.com/fwlink/?LinkID=273882)
* [云平台路线图](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Azure 预览版中的新增功能](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [公司门户 UI 中的新增功能](https://docs.microsoft.com/intune/whats-new/whats-new-in-company-portal-ui)
* [新增功能存档](whats-new-archive.md)

