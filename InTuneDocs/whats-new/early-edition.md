---
title: "早期版本 | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 12/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 18d47678b0fbdbd98502f2d3b469b202b567b2e7
ms.openlocfilehash: 3c7edc236878232c6f4c0ae993733c967946e765


---

# <a name="the-early-edition-for-microsoft-intune---january"></a>Microsoft Intune 的早期版本 - 1 月

**早期版本**提供了一份即将发布的 Microsoft Intune 版本中将出现的功能的列表。 此信息在非常有限的情况下依据保密协议 (NDA) 提供，并不断变化。 此处列出的某些功能有无法按期发布的风险并可能推迟到以后的版本。 正在以试验模式（外部测试）测试其他功能，以确保它们可立即供客户使用。 如果有任何问题或顾虑，请联系 Intune/PM 好友。

本页将定期更新。 返回查看其他更新。

> [!Note]
> 下面的更改依据 Intune 开发。 所有这些功能最终将支持混合客户部署（带 Intune 的 Configuration Manager）。 有关新的混合功能的详细信息，请查看[混合新增功能页](https://docs.microsoft.com/en-us/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。

## <a name="new-capabilities"></a>新功能

### <a name="actions-for-non-compliance---730266--"></a>针对不合规的操作<!--730266-->
“针对不合规的操作”是合规性策略的新功能，允许在不合规的设备上执行操作。 可指定单个或多个操作，并指定这些操作必然会发生的时间段。 例如，可在设备变为不合规后，立即通过电子邮件通知该不合规设备的用户，或可在 3 天宽限期后，通过条件性访问阻止不合规设备访问公司资源。

### <a name="in-console-reports-for-mam-without-enrollment---677961--"></a>无需注册的 MAM 控制台内报表<!--677961-->
已为已注册设备和未注册设备添加了新的应用保护报表。 详细了解如何[使用 Intune 监视移动应用管理策略](https://docs.microsoft.com/en-us/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune)。

### <a name="conditional-access-for-mam-with-sharepoint-online---679339--"></a>MAM 与 SharePoint Online 的条件访问 <!--679339-->
可以阻止不受 Intune 移动应用管理 (MAM) 策略支持的应用访问 SharePoint Online。  可以在 Azure 门户中开始使用 Intune 移动应用管理。 在“设置”边栏选项卡中查找“条件访问”部分，其中包含针对 SharePoint Online 的选项。 此功能将独立于服务版本的其余部分进行发布。 <!--Find out more about this new feature [here](https://docs.microsoft.com/intune/deploy-use/mam-ca-for-sharepoint-online).-->

### <a name="android-711-support---694397--"></a>Android 7.1.1 支持<!--694397-->
Intune 现在完全支持并可管理 Android 7.1.1。

## <a name="notices"></a>通知

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>默认通过 Windows 设置管理 Windows 桌面设备<!--663050-->
用于注册 Windows 10 桌面版的默认行为发生了变化。 新的注册将遵循典型 MDM 代理注册流程，而非通过电脑代理进行。

公司门户网站将为 Windows 10 桌面用户提供注册说明，指导他们完成将 Windows 10 桌面计算机添加为移动设备的过程。 这不会影响当前已注册的电脑，[如果愿意](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune)，组织仍可使用电脑代理来管理 Windows 10 桌面。

### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>iOS 版公司门户链接在应用内打开<!--665954-->
iOS 版公司门户应用内的链接（包括文档和应用链接）将通过 Safari 的应用内视图直接在公司门户应用中打开。 此更新将与 1 月的服务更新分开提供。

### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>改进对选择性擦除的移动应用管理支持<!--581242-->
如果由于“擦除应用数据前的脱机时间间隔”策略导致自动删除了工作或学校数据，则将为最终用户提供有关如何重新获得这些数据的访问权限的其他指导。<!--, or the removal of the Intune Company Portal on Android.-->

### <a name="new-documentation-for-app-protection-policies---583398--"></a>新的应用保护策略文档<!--583398-->
针对想要使用 Intune 应用包装工具或 Intune App SDK 在 iOS 和 Android 应用中启用应用保护策略（称为 MAM 策略）的管理员和应用开发人员，我们更新了相关文档。

已更新以下文章：

* [决定如何使用 Microsoft Intune 为移动应用程序管理准备应用](https://docs.microsoft.com/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)
* [使用 Intune 应用包装工具为移动应用程序管理准备 iOS 应用](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)
* [Microsoft Intune App SDK 入门](https://docs.microsoft.com/intune/develop/intune-app-sdk-get-started)
* [Intune App SDK for iOS 开发人员指南](https://docs.microsoft.com/intune/develop/intune-app-sdk-ios)

以下文章是对文档库新增的内容：

* [Intune App SDK Cordova 插件](https://docs.microsoft.com/intune/develop/intune-app-sdk-cordova)
* [Intune App SDK Xamarin 组件](https://docs.microsoft.com/intune/develop/intune-app-sdk-xamarin)

### <a name="progress-bar-when-launching-the-company-portal-on-ios---665978--"></a>在 iOS 上启动公司门户时的进度栏<!--665978-->
IOS 版公司门户在启动屏幕上引入了一个进度栏，为用户提供所发生的加载进程的信息。 进度栏将逐步推出，以替代旋转图标。 这意味着某些用户将看到新的进度栏，而其他用户会继续看到旋转图标。

## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Azure 上新的 Intune 管理体验公开预览版<!--736542-->

在 2017 年初，我们会将完整管理体验迁移到 Azure 上，以便能够在可使用图形 API 进行扩展的新式服务平台上对核心 EMS 工作流进行强大且集成的管理。

新的试用租户将于本月开始在 Azure 门户中看到新管理体验的公开预览版。 在预览状态下，将以迭代方式交付现有 Intune 控制台的功能和奇偶校验。

Azure 门户中的管理体验将使用已公布的新分组和定向功能；当现有租户迁移到新的分组体验时，也会将你迁移，以预览租户上的新管理体验。 在此期间，如果想要在租户迁移之前测试或查看任何新功能，请注册新的 Intune 试用帐户或查阅[新文档](https://docs.microsoft.com/en-us/intune-azure/introduction/what-is-microsoft-intune)。

如果对租户迁移的时间表有任何疑问，请通过 [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com) 联系我们的迁移团队。

### <a name="january-2017"></a>2017 年 1 月

#### <a name="custom-app-categories---748805--"></a>自定义应用类别<!--748805-->
现可以为添加到 Intune 的应用创建、编辑和分配类别。 目前，只能以英文指定类别。

#### <a name="assign-line-of-business-apps-whether-or-not-devices-are-enrolled---748803--"></a>分配业务线应用（无论设备是否注册）<!--748803-->
现在，无论用户的设备是否已注册 Intune，都可以从应用商店向用户分配业务线和应用。 如果用户设备未注册 Intune，他们必须转到公司门户网站（而非公司门户应用）安装它。

### <a name="december-2016"></a>2016 年 12 月

#### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Azure 门户公开预览版中的电信费用管理集成<!--747605-->
现在，我们将开始在 Azure 门户中预览与第三方电信费用管理 (TEM) 服务的集成。 可以使用 Intune 强制实施对国内和漫游数据使用的限制。 我们将使用 [Saaswedo](http://www.saaswedo.com) 开始这些集成。 若要在试用租户中启用此功能，请[联系 Microsoft 支持](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)。

### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new-in-microsoft-intune.md)。



<!--HONumber=Dec16_HO4-->


