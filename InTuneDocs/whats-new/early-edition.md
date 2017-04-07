---
title: "早期版本 | Microsoft Docs"
description: 
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 1ba0dab35e0da6cfe744314a4935221a206fcea7
ms.openlocfilehash: 3b355d43d4be05535f256d88a8648c2e67035882
ms.lasthandoff: 03/13/2017


---


# <a name="the-early-edition-for-microsoft-intune---march-2017"></a>Microsoft Intune 的早期版本 - 2017 年 3 月

**早期版本**提供了一份即将发布的 Microsoft Intune 版本中将出现的功能的列表。 此信息在非常有限的情况下依据保密协议 (NDA) 提供，并不断变化。 此处列出的某些功能有无法按期发布的风险并可能推迟到以后的版本。 正在以试验模式（外部测试）测试其他功能，以确保它们可立即供客户使用。 如果有任何问题或顾虑，请联系 Intune/PM 好友。

本页将定期更新。 返回查看其他更新。

> [!Note]
> 下面的更改依据 Intune 开发。 所有这些功能最终将支持混合客户部署（带 Intune 的 Configuration Manager）。 有关新的混合功能的详细信息，请查看[混合新增功能页](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。

## <a name="new-capabilities"></a>新功能

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Android 适用的公司门户应用的最新用户体验<!--621622-->

适用于 Android 的公司门户应用将更新其用户界面，提供更现代的外观和感受以及更好的用户体验。 值得注意的更新包括：

- 颜色：公司门户选项卡标头将按 IT 定义的品牌进行着色。
- 应用：“应用”选项卡上将更新“特色应用”和“所有应用”按钮。
- 搜索：“应用”选项卡上的“搜索”按钮现在是浮动的操作按钮。
- 导航应用：“所有应用”视图以选项卡形式呈现出“特色”、“所有”和“分类”，便于导航。
- 支持：更新“我的设备”和“联系 IT”选项卡以提高可读性。

有关这些更改的更多详细信息，可访问 [应用用户界面更新页面](whats-new-in-intune-app-ui.md]。

### <a name="signing-script-for-windows-10-company-portal---941642--"></a>对 Windows 10 公司门户的脚本进行签名<!--941642-->

对于需要下载和旁加载 Windows 10 Company Portal 应用的客户，现在可以使用脚本简化并精简组织的应用签名过程。   要下载脚本及其使用说明，请参阅 TechNet 库中的 [Windows 10 公司门户的 Microsoft Intune 签名脚本](https://aka.ms/win10cpscript)。 有关此公告的详细信息，请参阅 Intune 支持团队博客上的[更新 Windows 10 公司门户应用](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/)。 

## <a name="notices"></a>通知

### <a name="improved-support-for-android-users-based-in-china---720444--"></a>改进了对身处中国的 Android 用户的支持<!--720444-->

由于中国地区没有 Google Play 商店，Android 设备必须从中国的市场获取应用。 公司门户将支持此工作流，方法是将中国的 Android 用户重定向为从本地应用商店下载公司门户和 Outlook 应用。 对于移动设备管理和移动应用程序管理，此举将改善启用条件性访问策略时的用户体验。 下列中文应用商店中提供适用于 Android 的公司门户和 Outlook 应用：

- [百度](https://go.microsoft.com/fwlink/?linkid=836946)
- [小米](https://go.microsoft.com/fwlink/?linkid=836947)
- [腾讯](https://go.microsoft.com/fwlink/?linkid=836949)
- [华为](https://go.microsoft.com/fwlink/?linkid=836948)
- [豌豆荚](https://go.microsoft.com/fwlink/?linkid=836950)

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 将要求更新应用传输安全<!--748318-->

自 2017 年春季开始，Apple 宣布他们将强制对应用程序传输安全 (ATS) 实施特定要求。 使用 ATS 对所有通过 HTTPS 的应用通信实施更严格的安全措施。 此更改会影响使用 iOS 公司门户应用的 Intune 客户。 请查看 [Intune 支持博客](https://aka.ms/compportalats)，了解更多详细信息。

## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Azure 上新的 Intune 管理体验公开预览版<!--736542-->

在 2017 年初，我们会将完整管理体验迁移到 Azure 上，以便能够在可使用图形 API 进行扩展的新式服务平台上对核心 EMS 工作流进行强大且集成的管理。

新的试用租户将于本月开始在 Azure 门户中看到新管理体验的公开预览版。 在预览状态下，将以迭代方式交付现有 Intune 控制台的功能和奇偶校验。

Azure 门户中的管理体验将使用已公布的新分组和定向功能；当现有租户迁移到新的分组体验时，也会将你迁移，以预览租户上的新管理体验。 在此期间，如果想要在租户迁移之前测试或查看任何新功能，请注册新的 Intune 试用帐户或查阅[新文档](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune)。

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>非托管设备可访问已分配的应用<!--664691-->

公司门户网站上的设计更改之一是，iOS 和 Android 用户能够在其非托管设备上安装分配到的“可用且无需注册”设备。 用户可使用其 Intune 凭据登录到公司门户网站，并查看分配到的应用列表。 “可用且无需注册”应用的应用包可通过公司门户网站进行下载。 需要注册才能安装的应用不受此更改影响，如果用户想安装这类应用，则会提示用户注册其设备。

### <a name="improvements-to-device-actions-report---677150--"></a>改进设备操作报告<!--677150-->

改进了设备操作报告，进而改善了性能。 此外，现可按状态筛选报告。 例如，可筛选报告以仅显示“已完成”的设备操作。

### <a name="actions-for-non-compliance---730266--"></a>针对不合规的操作<!--730266-->

“针对不合规的操作”是合规性策略的新功能，允许在不合规的设备上执行操作。 可指定单个或多个操作，并指定这些操作必然会发生的时间段。 例如，可在设备变为不合规后，立即通过电子邮件通知该不合规设备的用户，或可在 3 天宽限期后，通过条件性访问阻止不合规设备访问公司资源。

### <a name="custom-app-categories---748805--"></a>自定义应用类别<!--748805-->

现可以为添加到 Intune 的应用创建、编辑和分配类别。 目前，只能以英文指定类别。
请参阅[如何将应用添加到 Intune](/intune-azure/manage-apps/add-apps)。

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>将 LOB 应用分配给未注册设备的用户<!--748823-->

现在，无论用户的设备是否已注册 Intune，都可以从应用商店向用户分配业务线应用。 如果用户设备未注册 Intune，他们必须转到公司门户网站（而非公司门户应用）安装它。

### <a name="new-compliance-reports---846671--"></a>新符合性报告<!--846671-->

现可通过符合性报告了解设备在公司中的符合性状态，以便快速解决用户遇到的与符合性相关的问题。 可查看以下相关信息

- 设备的总体符合性状态
- 单个设置的符合性状态
- 单个策略的符合性状态

还可使用这些报告向下钻取各个设备，查看影响该设备的特定设置和策略。

### <a name="additional-windows-10-upgrade-paths---903672--"></a>Windows 10 其他升级途径<!--903672-->

现可创建版本升级策略，将设备升级到以下的其他 Windows 10 版本：

- Windows 10 专业版
- Windows 10 专业版 N
- Windows 10 专业教育版
- Windows 10 专业教育版 N


### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接访问 Apple 注册方案<!--951869-->

对于在 2017 年 1 月之后创建的 Intune 帐户，Intune 支持在 Azure 预览门户中使用注册设备工作负荷直接访问 Apple 注册方案。 以前，仅能通过经典 Intune 门户中的链接访问 Apple 注册预览版。 2017 年 1 月之前创建的 Intune 帐户需要进行一次性迁移，然后才能使用 Azure 中的这些功能。 迁移的计划目前尚未公布，但详细信息将尽快发布。 强烈建议创建一个试用帐户，在现有帐户无法访问预览版时测试新体验。

### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new-in-microsoft-intune.md)。

