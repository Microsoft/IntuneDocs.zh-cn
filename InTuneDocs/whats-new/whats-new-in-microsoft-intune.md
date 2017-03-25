---
title: "新增功能 | Microsoft Docs"
description: "了解 Microsoft Intune 当月新增的功能和过去的版本"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 03/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b6c245d60c661c04b4c4d29c9bdcdd752254d978
ms.openlocfilehash: 2a602b351cf7f345bd56f20394943ea25f2d2060
ms.lasthandoff: 03/15/2017


---
# <a name="whats-new-in-microsoft-intune---march-2017"></a>Microsoft Intune 中的新增功能 - 2017 年 3 月
了解此版本 Microsoft Intune 中的新增功能。 你还可以发现需要计划的即将发生的更改，以及有关过去版本的信息。

> [!Note]
> 所有这些功能最终将支持混合客户部署（带 Intune 的 Configuration Manager）。 有关新的混合功能的详细信息，请查看[混合新增功能页](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。

## <a name="new-capabilities"></a>新功能

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Android 适用的公司门户应用的最新用户体验<!--621622-->

适用于 Android 的公司门户应用将更新其用户界面，提供更现代的外观和感受以及更好的用户体验。 值得注意的更新包括：

- 颜色：公司门户选项卡标头将按 IT 定义的品牌进行着色。
- 应用：“应用”选项卡上将更新“特色应用”和“所有应用”按钮。
- 搜索：“应用”选项卡上的“搜索”按钮现在是浮动的操作按钮。
- 导航应用：“所有应用”视图以选项卡形式呈现出“特色”、“所有”和“分类”，便于导航。
- 支持：更新“我的设备”和“联系 IT”选项卡以提高可读性。

有关这些更改的详细信息，请参阅 [Intune 最终用户应用的 UI 更新](whats-new-in-intune-app-ui.md)。

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>非托管设备可访问已分配的应用<!--664691-->

公司门户网站上的设计更改之一是，iOS 和 Android 用户能够在其非托管设备上安装分配到的“可用且无需注册”设备。 用户可使用其 Intune 凭据登录到公司门户网站，并查看分配到的应用列表。 “可用且无需注册”应用的应用包可通过公司门户网站进行下载。 需要注册才能安装的应用不受此更改影响，如果用户想安装这类应用，则会提示用户注册其设备。

### <a name="signing-script-for-windows-10-company-portal---941642--"></a>对 Windows 10 公司门户的脚本进行签名<!--941642-->

如果你需要下载和旁加载 Windows 10 公司门户应用，现在可以使用脚本简化并精简组织的应用签名过程。   要下载脚本及其使用说明，请参阅 TechNet 库中的 [Windows 10 公司门户的 Microsoft Intune 签名脚本](https://aka.ms/win10cpscript)。 有关此公告的详细信息，请参阅 Intune 支持团队博客上的[更新 Windows 10 公司门户应用](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/)。


## <a name="notices"></a>通知

### <a name="improved-support-for-android-users-based-in-china---720444--"></a>改进了对身处中国的 Android 用户的支持<!--720444-->

由于中国地区没有 Google Play 商店，Android 设备必须从中国的市场获取应用。 公司门户将支持此工作流，方法是将中国的 Android 用户重定向为从本地应用商店下载公司门户和 Outlook 应用。 对于移动设备管理和移动应用程序管理，此举将改善启用条件性访问策略时的用户体验。 下列中文应用商店中提供适用于 Android 的公司门户和 Outlook 应用：

- [百度](https://go.microsoft.com/fwlink/?linkid=836946)
- [小米](https://go.microsoft.com/fwlink/?linkid=836947)
- [腾讯](https://go.microsoft.com/fwlink/?linkid=836949)
- [华为](https://go.microsoft.com/fwlink/?linkid=836948)
- [豌豆荚](https://go.microsoft.com/fwlink/?linkid=836950)

### <a name="best-practice-make-sure-your-company-portal-apps-are-up-to-date---879465--"></a>最佳做法：确保你的公司门户应用处于最新状态<!--879465-->

2016 年 12 月，我们发布了一个更新，在一组用户注册 iOS、Android、Windows 8.1 + 或 Windows Phone 8.1 + 设备时强制进行多重身份验证 (MFA)。 如果没有适用于 Android (v5.0.3419.0+) 和 iOS (v2.1.17+) 的公司门户应用的某些基线版本，此功能将无法正常运行。

通过将新函数添加到控制台和所有受支持平台上的公司门户应用，Microsoft 不断改进 Intune。 因此，Microsoft 仅发布针对我们在当前版本公司门户应用中所发现问题的修补程序。 因此建议使用最新版本的公司门户应用以获取最佳用户体验。

>[!Tip]
> 让用户设置其设备以在相应的应用商店中自动更新应用。 如果你使 Android 公司门户应用在网络共享上可用，可以从 [Microsoft 下载中心](https://www.microsoft.com/download/details.aspx?id=49140)下载最新版本。

### <a name="microsoft-teams-is-now-enabled-for-mam-on-ios-and-android"></a>现已在 iOS 和 Android 上为 MAM 启用 Microsoft Teams

Microsoft 已宣布发布 Microsoft Teams 的通用版本。 适用于 iOS 和 Android 的更新的 Microsoft Teams 应用现已具备 Intune 移动应用管理 (MAM) 功能，让你的团队可以自由地跨设备工作，同时确保对话和公司数据始终受到保护。 有关详细信息，请参阅企业移动性和安全性博客上的 [Microsoft Teams 公告](https://blogs.technet.microsoft.com/enterprisemobility/2017/03/14/microsoft-teams-is-now-generally-available-and-mam-enabled-on-ios-and-android/)。


## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Azure 上的 Intune 管理体验公开预览版的新增功能<!--736542-->

在 2017 年初，我们会将完整管理体验迁移到 Azure 上，以便能够在可使用图形 API 进行扩展的新式服务平台上对核心 EMS 工作流进行强大且集成的管理。

新的试用租户将于本月开始在 Azure 门户中看到新管理体验的公开预览版。 在预览状态下，将以迭代方式交付现有 Intune 控制台的功能和奇偶校验。

Azure 门户中的管理体验将使用已公布的新分组和定向功能；当现有租户迁移到新的分组体验时，也会将你迁移，以预览租户上的新管理体验。 在此期间，如果想要在租户迁移之前测试或查看任何新功能，请注册新的 Intune 试用帐户或查阅[新文档](https://docs.microsoft.com/intune-azure/introduction/whats-new)。

> [!Note]
> 对于 Azure 门户预览版，我们将在本月推出更新。 但是，鉴于 Intune 服务的推出方式，所做的更改可能无法立即使用。  在新门户功能可用之前，必须按顺序更新服务的多个组件。 在本月晚些时候推出时可查找 Azure 门户预览版中的更改。 有关更改的完整列表，请参阅 [Microsoft Intune 预览版中的新增功能](/intune-azure/introduction/whats-new)。

## <a name="whats-coming"></a>即将推出

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 将要求更新应用传输安全<!--748318-->

自 2017 年春季开始，Apple 宣布他们将强制对应用程序传输安全 (ATS) 实施特定要求。 使用 ATS 对所有通过 HTTPS 的应用通信实施更严格的安全措施。 此更改会影响使用 iOS 公司门户应用的 Intune 客户。 请查看 [Intune 支持博客](https://aka.ms/compportalats)，了解更多详细信息。

### <a name="see-also"></a>另请参阅
* [Microsoft Intune 博客](http://go.microsoft.com/fwlink/?LinkID=273882)
* [云平台路线图](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Azure 预览版的新增功能](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [What's new in the Company Portal UI](https://docs.microsoft.com/intune/whats-new/whats-new-in-company-portal-ui)（公司门户 UI 新增功能）
* [新增功能存档](whats-new-archive.md)

