---
title: "早期版本 | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f287a0ad082fa20a2e84abbf8f5585117aae6f57
ms.openlocfilehash: e604b8809bd444d9069d449a6c691a8444296623


---

# <a name="the-early-edition-for-microsoft-intune---december"></a>Microsoft Intune 的早期版本 - 12 月

**早期版本**提供了一份即将发布的 Microsoft Intune 版本中将出现的功能的列表。 此信息在非常有限的情况下依据保密协议 (NDA) 提供，并不断变化。 此处列出的某些功能有无法按期发布的风险并可能推迟到以后的版本。 正在以试验模式（外部测试）测试其他功能，以确保它们可立即供客户使用。 如果有任何问题或顾虑，请联系 Intune/PM 好友。

本页将定期更新。 返回查看其他更新。

下面的更改依据 Intune 开发。 所有这些功能最终将支持混合客户部署（带 Intune 的 Configuration Manager）。 有关新的混合功能的详细信息，请查看[混合新增功能页](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx)。

<!--736542-->
## <a name="public-preview-of-the-new-intune-admin-experience-on-azure"></a>Azure 上新的 Intune 管理体验公开预览版

在 2017 年初，我们会将完整管理体验迁移到 Azure 上，以便能够在可使用图形 API 进行扩展的新式服务平台上对核心 EMS 工作流进行强大且集成的管理。

新的试用租户将于本月开始在 Azure 门户中看到新管理体验的公开预览版。 在预览状态下，将以迭代方式交付现有 Intune 控制台的功能和奇偶校验。

Azure 门户中的管理体验将使用已公布的新分组和定向功能；当现有租户迁移到新的分组体验时，也会将你迁移，以预览租户上的新管理体验。 在此期间，如果想要在租户迁移之前测试或查看任何新功能，请注册新的 Intune 试用帐户或查阅新文档。

如果对租户迁移的时间表有任何疑问，请通过 [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com) 联系我们的迁移团队。

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Azure 门户公开预览版中的电信费用管理集成<!--747605-->
现在，我们将开始在 Azure 门户中预览与第三方电信费用管理 (TEM) 服务的集成。 可以使用 Intune 强制实施对国内和漫游数据使用的限制。 我们将使用 [Saaswedo](http://www.saaswedo.com) 开始这些集成。

## <a name="new-capabilities"></a>新功能

### <a name="multi-factor-authentication-across-all-platforms---747590--"></a>跨所有平台的多重身份验证 <!--747590-->
现在，可以通过在 Azure Active Directory 中的 Microsoft Intune 注册应用程序上配置 MFA，在所选用户组从 Azure 管理门户注册 iOS、Android、Windows 8.1+ 或 Windows Phone 8.1+ 设备时，对其强制执行多重身份验证 (MFA) 。

### <a name="conditional-access-for-mam-with-sharepoint-online---vso-679339--"></a>MAM 与 SharePoint Online 的条件访问 <!--VSO 679339-->
可以阻止不受 Intune 移动应用管理 (MAM) 策略支持的应用访问 SharePoint Online。  可以在 Azure 门户中开始使用 Intune 移动应用管理。 在“设置”边栏选项卡中查找“条件访问”部分，其中包含针对 SharePoint Online 的选项。 此功能将独立于服务版本的其余部分进行发布。

## <a name="notices"></a>通知

### <a name="multi-factor-authentication-on-enrollment-moving-to-the-azure-portal---vso-750545--"></a>注册移动到 Azure 门户时的多重身份验证 <!--VSO 750545-->
以前，管理员会转到 Intune 控制台或 Configuration Manager（1610 之前的版本）控制台，以设置 MFA 用于 Intune 注册。 通过此更新的功能，现在可使用 Intune凭据登录 [Microsoft Azure 门户](https://manage.windowsazure.com)，并通过 Azure AD 配置 MFA 设置。 在[此处](https://aka.ms/mfa_ad)了解详细信息。

### <a name="company-portal-app-for-android-now-available-in-china---vso-658093--"></a>Android 版公司门户应用现已在中国推出  <!--VSO 658093-->
我们将发布 Android 版公司门户应用，以供中国地区下载。 由于中国地区没有 Google Play 商店，Android 设备必须从中国的应用市场获取应用。 Android 版公司门户应用可通过 360、腾讯、小米、豌豆荚和华为进行下载。 

Android 版公司门户应用使用 Google Play Services 与 Microsoft Intune 服务进行通信。 由于 Google Play Services 尚未在中国推出，因此执行以下任何任务最高可能需要 8 个小时才能完成。 

|Intune 管理控制台| Android 适用的 Intune 公司门户应用 |Intune 公司门户网站|   
|---|---|---|
|完全擦除| 移除远程设备| 移除设备（本地和远程）|
|“选择性擦除”| 重置设备| 重置设备|
|新的或更新的应用部署| 安装可用的业务线应用| 设备密码重置|
|远程锁定|||
|密码重置|||

## <a name="deprecations"></a>弃用功能

### <a name="removal-of-exchange-online-mobile-inbox-policies---770687--"></a>删除 Exchange Online 移动版收件箱策略 <!--770687-->
从 12 月开始，管理员将无法再在 Intune 控制台中查看或配置 Exchange Online (EAS) 移动版邮箱策略。 此更改将在 12 月和 1 月向所有 Intune 租户推出。 所有现有策略将保持配置状态；若要配置新策略，请使用 Exchange 命令行管理程序。 可在[此处](https://technet.microsoft.com/en-us/library/bb123783%28v=exchg.150%29.aspx)找到详细信息。

### <a name="intune-av-player-image-viewer-and-pdf-viewer-apps-are-no-longer-supported-on-android---747553--"></a>Android 不再支持 Intune AV 播放器、图像查看器和 PDF 查看器应用 <!--747553-->
从 2016 年 12 月中旬起，用户将无法继续使用 Intune AV 播放器、图像查看器和 PDF 查看器应用。 这些应用已替换为 Azure 信息保护应用。 可在[此处](https://docs.microsoft.com/information-protection/rms-client/mobile-app-faq)查找有关 Azure 信息保护应用的详细信息。

### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new-in-microsoft-intune.md)。



<!--HONumber=Nov16_HO4-->


