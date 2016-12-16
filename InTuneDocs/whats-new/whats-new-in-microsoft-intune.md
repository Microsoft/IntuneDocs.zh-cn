---
title: "新增功能 | Microsoft Intune"
description: "了解 Microsoft Intune 的当月新增功能和过去版本"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 12/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9fd309a10d9eb020795c5ce46df124b13dc1a006
ms.openlocfilehash: d117c929fbde4dd0a39503b8da695aa9c9ea91ad


---
# <a name="whats-new-in-microsoft-intune---december-2016"></a>Microsoft Intune 新增功能 — 2016 年 12 月
了解此版本 Microsoft Intune 中的新增功能。 你还可以发现需要计划的即将发生的更改，以及有关过去版本的信息。

> [!Note]
> 所有这些功能最终将支持混合客户部署（带 Intune 的 Configuration Manager）。 有关新的混合功能的详细信息，请查看[混合新增功能页](https://docs.microsoft.com/en-us/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。

## <a name="public-preview-of-the-new-intune-admin-experience-on-azure--736542--"></a>Azure 上新的 Intune 管理体验公开预览版<!--736542-->
在 2017 年初，我们会将完整管理体验迁移到 Azure 上，以便能够在可使用图形 API 进行扩展的新式服务平台上对核心 EMS 工作流进行强大且集成的管理。 在正式发布此面向所有 Intune 租户的门户之前，我们高兴地宣布将在本月晚些时候向所选租户推出此新的管理体验的预览版。

Azure 门户中的管理体验将使用已公布的新分组和定向功能；当现有租户迁移到新的分组体验时，也会将你迁移，以预览租户上的新管理体验。 同时，在[新文档](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune)中查找应用商店提供的用于 Azure 门户中的 Microsoft Intune 的应用的更多信息。

如果对租户迁移的时间表有任何疑问，请通过 [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com) 联系我们的迁移团队。

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Azure 门户公开预览版中的电信费用管理集成<!--747605-->
现在，我们将开始在 Azure 门户中预览与第三方电信费用管理 (TEM) 服务的集成。 可以使用 Intune 强制实施对国内和漫游数据使用的限制。 我们将使用 [Saaswedo](http://www.saaswedo.com) 开始这些集成。

## <a name="new-capabilities"></a>新功能

### <a name="multi-factor-authentication-across-all-platforms---747590--"></a>跨所有平台的多重身份验证 <!--747590-->
现在，可以通过在 Azure Active Directory 中的 Microsoft Intune 注册应用程序上配置 MFA，在所选用户组从 Azure 管理门户注册 iOS、Android、Windows 8.1+ 或 Windows Phone 8.1+ 设备时，对其强制执行多重身份验证 (MFA) 。

<!--VSO 679339, awaiting chrisgre for go-live--><!--### Conditional access for MAM with SharePoint Online
可以阻止不受 Intune 移动应用管理 (MAM) 策略支持的应用访问 SharePoint Online。  可以在 Azure 门户中开始使用 Intune 移动应用管理。 在“设置”边栏选项卡中查找“条件访问”部分，其中包含针对 SharePoint Online 的选项。 此功能将独立于服务版本的其余部分进行发布。 在[此处](https://docs.microsoft.com/intune/deploy-use/mam-ca-for-sharepoint-online)了解更多有关此新功能的信息。-->

### <a name="ability-to-restrict-mobile-device-enrollment--747596--"></a>限制移动设备注册的功能<!--747596-->
Intune 新增了注册限制，可控制允许注册的移动设备平台。 Intune 将移动设备平台分为 iOS、macOS，Android、Windows 和 Windows Mobile。
* 限制移动设备注册不会限制电脑客户端注册。
* 阻止个人自有设备的注册有一个附加选项，该选项仅适用于 iOS。

Intune 将所有新设备都标记为个人所有，除非 IT 管理员将设备标记为公司所有，如[本文](https://docs.microsoft.com/en-us/intune/deploy-use/manage-corporate-owned-devices)所述。


## <a name="notices"></a>通知

### <a name="multi-factor-authentication-on-enrollment-moving-to-the-azure-portal---vso-750545--"></a>注册移动到 Azure 门户时的多重身份验证 <!--VSO 750545-->
以前，管理员会进入 Intune 控制台或 Configuration Manager（2016 年 10 月之前的版本）控制台，以设置 MFA 用于 Intune 注册。 通过此更新的功能，现在可使用 Intune凭据登录 [Microsoft Azure 门户](https://manage.windowsazure.com)，并通过 Azure AD 配置 MFA 设置。 在[此处](https://aka.ms/mfa_ad)了解详细信息。

### <a name="company-portal-app-for-android-now-available-in-china---vso-658093--"></a>Android 版公司门户应用现已在中国推出  <!--VSO 658093-->
我们将发布 Android 版公司门户应用，以供中国地区下载。 由于中国地区没有 Google Play 商店，Android 设备必须从中国的应用市场获取应用。 可在以下应用商店下载用于 Android 的公司门户应用：
* [百度](https://go.microsoft.com/fwlink/?linkid=836946)
* [华为](https://go.microsoft.com/fwlink/?linkid=836948)
* [腾讯](https://go.microsoft.com/fwlink/?linkid=836949)
* [豌豆荚](https://go.microsoft.com/fwlink/?linkid=836950)
* [小米](https://go.microsoft.com/fwlink/?linkid=836947)

Android 版公司门户应用使用 Google Play Services 与 Microsoft Intune 服务进行通信。 由于 Google Play Services 尚未在中国推出，因此执行以下任何任务最高可能需要 8 个小时才能完成。 

|Intune 管理控制台| Android 适用的 Intune 公司门户应用 |Intune 公司门户网站|   
|---|---|---|
|完全擦除| 移除远程设备| 移除设备（本地和远程）|
|“选择性擦除”| 重置设备| 重置设备|
|新的或更新的应用部署| 安装可用的业务线应用| 设备密码重置|
|远程锁定|||
|密码重置|||

## <a name="deprecations"></a>弃用功能

### <a name="firefox-to-no-longer-support-silverlight--vso-tba--"></a>Firefox 不再支持 Silverlight<!--VSO TBA-->
Mozilla 将在 52 版 [Firefox 浏览器](https://www.mozilla.org/firefox)中移除对 Silverlight 的支持，此更新于 2017 年 3 月生效。 因此，无法使用高于 51 版的 Firefox 登录现有 Intune 控制台。 我们建议使用 Internet Explorer 10 或 11，或者 [52 版之前的 Firefox](https://ftp.mozilla.org/pub/firefox/releases/) 访问管理控制台。 Intune 向 Azure 门户的过渡允许其支持多种[新式浏览器](https://docs.microsoft.com/en-us/azure/azure-preview-portal-supported-browsers-devices)，而无需依赖于 Silverlight。

### <a name="removal-of-exchange-online-mobile-inbox-policies---770687--"></a>删除 Exchange Online 移动版收件箱策略 <!--770687-->
从 12 月开始，管理员将无法再在 Intune 控制台中查看或配置 Exchange Online (EAS) 移动版邮箱策略。 此更改将在 12 月和 1 月向所有 Intune 租户推出。 所有现有策略将保持配置状态；若要配置新策略，请使用 Exchange 命令行管理程序。 可在[此处](https://technet.microsoft.com/en-us/library/bb123783%28v=exchg.150%29.aspx)找到详细信息。

### <a name="intune-av-player-image-viewer-and-pdf-viewer-apps-are-no-longer-supported-on-android---747553--"></a>Android 不再支持 Intune AV 播放器、图像查看器和 PDF 查看器应用 <!--747553-->
从 2016 年 12 月中旬起，用户将无法继续使用 Intune AV 播放器、图像查看器和 PDF 查看器应用。 这些应用已替换为 Azure 信息保护应用。 可在[此处](https://docs.microsoft.com/information-protection/rms-client/mobile-app-faq)查找有关 Azure 信息保护应用的详细信息。

### <a name="see-also"></a>另请参阅
* [Microsoft Intune 博客](http://go.microsoft.com/fwlink/?LinkID=273882)
* [云平台路线图](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [早期 Intune 发行版本](whats-new-archive.md)



<!--HONumber=Dec16_HO2-->


