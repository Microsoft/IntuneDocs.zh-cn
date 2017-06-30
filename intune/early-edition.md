---
title: "早期版本"
description: 
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 06/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 6b098720df2897bc814c94bb1245cffd36439014
ms.contentlocale: zh-cn
ms.lasthandoff: 06/08/2017


---

# <a name="the-early-edition-for-microsoft-intune---june-2017"></a>Microsoft Intune 的早期版本 - 2017 年 6 月

早期版本提供了一份即将发布的 Microsoft Intune 版本中将出现的功能列表。 此信息的提供条件极为严格，并在不断变化。 请不要与公司外部共享此信息。 此处列出的某些功能有无法按期发布的风险并可能推迟到以后的版本。 正在以试验模式（外部测试）测试其他功能，以确保它们可立即供客户使用。 如果有任何问题或顾虑，请与 Microsoft 产品组联系人联系。 

本页将定期更新。 返回查看其他更新。 

> [!Note]
>下面的更改依据 Intune 开发。 有关新的混合功能的详细信息，请查看[混合新增功能页](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。


## <a name="whats-coming-to-intune-on-the-azure-portal"></a>Azure 门户上的 Intune 的新增功能

### <a name="new-app-configuration-settings-for-the-intune-managed-browser-----682951----"></a>Intune 托管浏览器的新应用配置设置 <!--- 682951 --->

我们将针对 Intune 托管浏览器应用添加更多配置。 你将能够使用应用配置策略为浏览器配置默认主页和书签。 

### <a name="restrict-android-device-enrollment-restriction-by-os-version----747620---"></a>按 OS 版本限制 Android 设备注册 <!-- 747620 -->

Intune 将支持按操作系统版本号限制 Android 注册。 在“设备类型限制”下，IT 管理员将能够设置平台配置，以限制最低和最高操作系统值之间的注册。 操作系统版本必须指定为 Major.Minor.Build.Rev，其中 Minor、Build and Rev 为可选。

>[!NOTE]
>这不是一项安全功能，因为已遭攻击的设备会误报其操作系统版本信息。 这是对于非恶意用户的最大努力障碍。

### <a name="android-for-work-support-for-lookout----1087312---"></a>Lookout 的 Android for Work 支持<!-- 1087312 -->

在使用 Lookout for Work 应用时，Lookout 的 Intune 连接器将支持 Android for Work 设备。 你将能够在容器内部或外部部署 Lookout 应用。

### <a name="support-for-offline-apps-from-the-windows-store-for-business-----777044----"></a>支持来自适用于企业的 Windows 应用商店的脱机应用<!--- 777044 --->

你从适用于企业的 Windows 应用商店购买的脱机应用现在将同步至 Intune 门户。 然后，你将能够将这些应用部署到设备组或用户组。 脱机应用由 Intune 安装，而不是由应用商店安装。

### <a name="new-settings-for-windows-10-device-restriction-profile-----978527--978550-978569-978575-1050031-1058611-1124583----"></a>Windows 10 设备限制配置文件的新设置 <!--- 978527,  978550, 978569, 978575, 1050031, 1058611, 1124583 --->

将为 Windows 10 设备限制配置文件提供以下设置：

- Windows Defender
- 手机网络和连接性
- 锁定屏幕体验
- 隐私
- 搜索
- 报告和遥测
- Windows 聚焦
- Edge 浏览器

### <a name="support-for-shared-ipads-with-the-ios-classroom-app----1044681-854689---"></a>支持与 iOS Classroom 应用共享 iPad<!-- 1044681, 854689 -->

我们将扩展对管理 iOS Classroom 应用的支持，以便为使用托管 Apple ID 登录共享 iPad 的学生提供支持。

### <a name="office-365-proplus-app-available-for-windows-10-devices---1121362--"></a>适用于 Windows 10 设备的 Office 365 ProPlus 应用 <!--1121362-->

我们将添加可以让你轻松地将 Office 365 ProPlus 应用分配到 Windows 10 设备的新 Office 365 ProPlus 应用类型。 此外，如果你拥有 Microsoft Project 和 Microsoft Visio 的许可证，你还可以安装它们。 所需的应用将被捆绑在一起，并且将显示为 Intune 控制台的应用列表中的一个应用。

### <a name="tag-corporate-owned-devices-with-serial-number----1215070---"></a>用序列号标记公司拥有的设备 <!-- 1215070 -->

Intune 将支持上传 iOS、macOS 和 Android 序列号作为公司拥有的设备的标识符。 此时，你将不能使用序列号来阻止个人设备进行注册，因为在注册过程未验证序列号。 在不久的将来将推出按序列号阻止个人设备。

### <a name="scom-management-pack-for-exchange-connector----885457---"></a>适用于 Exchange 连接器的 SCOM 管理包 <!-- 885457 -->

将会提供适用于 Exchange 连接器的 System Center Operations Manager (SCOM) 管理包帮助你分析 Exchange 连接器日志。 这将在你需要进行问题故障排除时为你提供监控 Intune 的多种方式。

### <a name="new-role-based-administration-access-for-intune-admins----1099990---"></a>面向 Intune 管理员的全新基于角色的管理访问权限 <!-- 1099990 -->

将添加新的条件性访问管理员角色，以查看、创建、修改和删除 Azure AD 条件性访问策略。 以前，只有全局管理员和安全管理员具有此权限。 可以为 Intune 管理员授予此角色权限，以便他们有权访问条件性访问策略。

### <a name="app-based-conditional-access-for-microsoft-teams----1257019---"></a>面向 Microsoft 团队的基于应用的条件性访问权限 <!-- 1257019 -->

对于适用于 Exchange 和 SharePoint Online 的基于应用的条件性访问策略，适用于 iOS 和 Android 的 Microsoft Teams 应用将属于已批准应用。 你将能够利用基于应用的条件性访问通过 Azure 门户中的“Intune 应用保护”边栏选项卡为所有租户配置应用。

## <a name="whats-coming-to-intune-apps"></a>Intune 应用的新增功能

### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Samsung KNOX 启动 PIN 改进通知 <!--1087143-->

最终用户需要在 Samsung KNOX 设备上设置启动 PIN 以符合加密时，最终用户点击向他们显示的通知后，此通知会将其转到“设置”应用中的确切位置。  以前，该通知会将最终用户转到密码更改屏幕。

### <a name="promoting-the-most-current-version-of-the-company-portal-for-android---1098661--"></a>提示安装面向 Android 的公司门户的最新版本 <!--1098661-->

当应用的“通知”屏幕中已发布面向 Android 的公司门户应用的新推荐版本时，最终用户将看到应用内通知。 该通知将告诉用户某个“公司门户更新可用”。 点击此通知将打开一个网页，并显示可以从其中下载更新版本的可用应用商店列表。 

### <a name="improvements-to-app-syncing-with-windows-10-creators-update----676505---"></a>与 Windows 10 创意者更新的应用同步改进 <!-- 676505 -->

面向 Windows 10 的公司门户将自动启动与 Windows 10 创意者更新 (1704) 的设备应用安装请求同步。 这将减少“正在挂起同步”状态下的应用安装停止问题。 此外，用户将可以从该应用内部手动启动同步。 

面向 Windows 10 的公司门户还将公开一个刷新按钮，用户可以通过它在必要时刷新应用中的内容。 

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Windows 10 公司门户新的引导式体验<!-- 1058938 -->

适用于 Windows 10 的公司门户应用将为尚未被标识或注册的设备提供引导式的 Intune 演练体验。 新体验提供了循序渐进的说明，引导用户完成 AAD 注册（条件性访问功能所需）和 MDM 注册（设备管理功能所需）。 引导式体验可从公司门户主页获取。 如果用户未完成注册和登记，可以继续使用应用，但能够体验的功能将很有限。

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>改进了所有平台上跨公司门户应用的登录体验<!--User Story 1132123-->

我们宣布将在接下来的几个月内推出一项更新，该更新将提升适用于 Android、iOS 和 Windows 的 Intune 公司门户应用的登录体验。 当 Azure AD 进行此更改时，新的用户体验将自动在公司门户应用的所有平台上显现。 此外，用户可以使用生成的一次性验证码从其他设备立即登录到公司门户。 当用户需要在没有凭据的情况下登录时，这尤为有用。

可以在“应用 UI 中的新增功能”[](whats-new-app-ui.md)页看到使用凭据进行登录的以前的登录体验和新登录体验，以及从其他设备进行登录的新登录体验的屏幕快照。


## <a name="notices"></a>通知

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 将要求更新应用传输安全<!--748318-->

自 2017 年春季开始，Apple 宣布他们将强制对应用程序传输安全 (ATS) 实施特定要求。 使用 ATS 对所有通过 HTTPS 的应用通信实施更严格的安全措施。 此更改会影响使用 iOS 公司门户应用的 Intune 客户。 请查看 [Intune 支持博客](https://aka.ms/compportalats)，了解更多详细信息。

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接访问 Apple 注册方案<!--951869-->

对于在 2017 年 1 月之后创建的 Intune 帐户，Intune 支持在 Azure 预览门户中使用注册设备工作负荷直接访问 Apple 注册方案。 以前，仅能通过经典 Intune 门户中的链接访问 Apple 注册预览版。 2017 年 1 月之前创建的 Intune 帐户需要进行一次性迁移，然后才能使用 Azure 中的这些功能。 迁移的计划目前尚未公布，但详细信息将尽快发布。 强烈建议创建一个试用帐户，在现有帐户无法访问预览版时测试新体验。

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>做好应对更改的计划：Intune 将更改 Intune 合作伙伴门户体验<!-- 1050016 -->

自 2017 年 5 月中旬起，我们将从 manage.microsoft.com 中删除 Intune 合作伙伴页面（从服务更新入手）。  

如果你是合作伙伴管理员，将无法再代表客户在 Intune 合作伙伴页面中查看内容和执行操作，而是需要在 Microsoft 的其他两个合作伙伴门户之一进行登录。

使用 [Microsoft 合作伙伴中心](https://partnercenter.microsoft.com/)和 [Microsoft Office 365 合作伙伴管理中心](https://portal.office.com/)，可以登录所管理的客户帐户。 作为合作伙伴，未来请使用其中一个网站管理客户。

### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。

