---
title: "新增功能 | Microsoft Intune"
description: "了解 Microsoft Intune 的当月新增功能和过去版本"
keywords: 
author: Lindavr
manager: angrobe
ms.date: 08/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d51ab5d486e7e23d2527f9cb95f105e7916cdb27
ms.openlocfilehash: 138d362618c9859a55988b7a2ada85e44b0e95c5


---

# Microsoft Intune 新增功能
了解此版本 Microsoft Intune 中的新增功能。 你还可以发现需要计划的即将发生的更改，以及有关过去版本的信息。

所有这些功能最终将支持混合客户部署（带 Intune 的 Configuration Manager）。 有关新的混合功能的详细信息，请查看[混合新增功能页](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx)。
<!---@Barry, the above blurb stays in each version, but make sure Tyler signs off each time. Also, remember to set the ms.date in the metadata to the sprint release. --->

## 2016 年 8 月
## 应用管理
<!---@Barry, I created the buckets of App management, Device management, etc but am not tied to them. Just wanted to break up and organize the feature list. If you're going to take over the Company Portal section, please talk to Stacie about how she's been organizing it. --->

### iOS 9.3 隐藏和显示的应用
对于运行 iOS 9.3 或更高版本的设备，你可将 iOS 常规配置策略中的隐藏和显示的应用列表用于：
- 指定对用户隐藏的应用列表。 用户无法查看，或启动这些应用。
- 指定用户可以查看和启动的应用列表。 无法查看或启动其他应用。

你可以指定的应用包括已部署的应用，以及内置的 iOS 应用，如“信息”和“备忘录”。 有关详细信息，请参阅 [Microsoft Intune 中的 iOS 策略设置]( https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune)
<!---TFS 1279009 checked--->
### Samsung KNOX 设备允许和阻止的应用策略
你现在可以配置适用于 Samsung KNOX 设备的自定义策略，该策略允许你创建以下项之一：
- 阻止在设备上运行的应用的列表。 即使安装了阻止列表中定义的应用，该应用也不能在设备上激活。
- 允许设备用户从 Google Play 商店中安装的应用的列表。 其他应用不能从应用商店安装。

仅运行 Samsung KNOX 的设备可以使用这些设置。
有关详细信息，请参阅[使用自定义策略允许和阻止适用于 Samsung KNOX 设备的应用]( custom-policy-to-allow-and-block-samsung-knox-apps.md)。
<!---TFS 1311629 checked --->
### 与移动应用程序管理 (MAM) 兼容的新应用
无论设备是否注册，适用于 [iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) 和 [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) 的 Yammer 应用现在与 [Intune 移动应用程序管理 (MAM) 策略](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)兼容。

有关 MAM 兼容应用的完整列表，请参阅 [Microsoft Intune 应用程序合作伙伴](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners)站点。
<!--- TFS 1252335 & 1252336 checked--->


<!--- I started putting TFS numbers in the What's Coming topic and found it helpful when updating the What's New. Up to you if you want to continue. --->

### Intune 查看器应用
随着新的 RMS 共享应用的发布，我们将从 2016 年 8 月起删除以下 Intune 查看器应用：
- Intune AV 查看器
- Intune PDF 查看器
- Google Play 中适用于 Android 的 Intune 图像查看器

建议使用[适用于 Android 的 Rights Management 应用（RMS 共享）](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app)而不是使用 Intune 查看器应用，前者只需部署一个应用而不是三个单独的应用便可安全地查看 Android 设备上的公司文件。 如果不再支持 Intune 查看器应用，则将其从 Google 应用商店中删除并且不可供将来使用。

## 设备管理
### Android 7.0 支持
Intune 为移动设备即将推出的 Android 7.0 操作系统提供“day 0”支持。
<!---TFS 1262053--->
### Google 删除了 Android 7.0 设备上的远程密码重置功能
Google 正在删除 Android 7.0 设备的 IT 管理员和最终用户远程重置密码功能。 以前，IT 管理员可以远程重置用户的密码，而且最终用户可以从公司门户网站重置其密码。



## 公司门户更新
### 公司门户网站
- **从公司门户到 Microsoft 的反馈链接** <br/>
公司门户网站使最终用户能够点击位于页面底部的新的“反馈”链接，以便向 Microsoft 发送有关他们对站点的体验的反馈。 收集的匿名信息反馈将帮助 Microsoft 改进用户的公司门户网站体验。
<!--- TFS 1313657 checked--->

### iOS
- **最低 iOS 托管浏览器版本已更新为 8.0**<br/>
已更新用于 iOS 的 Microsoft Intune Managed Browser 应用以支持运行 iOS 8.0 或更高版本的设备。 虽然 iOS 7.1 设备仍可使用现有的 Managed Browser 应用，但最好鼓励你的用户更新为 iOS 8.0 或更高版本，以访问和充分利用新的 Managed Browser 功能。  
<!---TFS 1313253 checked--->

## 即将推出
### Intune 组将于 2016 年 9 月初过渡到 Azure Active Directory 组
Intune 正在创建将 Azure Active Directory (AAD) 安全组用作 Intune 中的用户和设备组的新组管理体验。 **当我们介绍新的基于 Azure 的 Intune 管理门户时**，这些组将用于所有组管理、策略部署和配置文件部署。

此新体验将会使你无需在服务之间重复组，**允许你访问某些新的 Azure Active Directory Premium (AADP) 组功能**，并提供使用 PowerShell 和图表的可扩展性。 这还将跨企业移动性管理统一组管理体验。

若要启用移动到安全组，**当前管理控制台**中的体验将进行一些修改。 **这些更改和 AAD 安全组的使用情况将记录在 Intune 文档中**。

Intune 的新客户将看到**当前租户执行操作之前的一些安全组更改**。

除了组管理中的更改，**还将弃用以下功能**：
- 在创建新组的过程中排除成员或组
- “**未分组的用户**”和“**未分组的设备**”组
- 服务管理员角色中的“**管理组**”
- 对通知规则的基于组的自定义警报
- 利用报表中的组进行透视
<!--- TFS 1295329--->

### 向 Android 公司门户添加“通知”
我们即将于 9 月发布 Android 公司门户的更新，这将在主页上引入一个新的“通知”图标。 点击此图标将访问“**通知**”页，该页将向你的最终用户显示在公司门户应用中需要注意的所有项，例如，设备非合规性、注册更新和注册激活。 如果还使用 iOS 公司门户应用，你将已看到通知体验。 通过引入“**通知**”页，只要设备已经注册，每次启动或恢复 Android 公司门户时，你将不会看到“**公司访问设置**”页。 我们听说你们中的许多人都已创建最终用户指南，而且非常感谢你们在指南/屏幕快照可能需要更新时提前通知我们。 请更新你的文档，以反映体验中即将发生的更改。 在此查找更新的屏幕快照：https://aka.ms/androidcpupdate。  


### 云路线图
通过[云平台路线图](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)实时了解 Intune 即将推出的开发内容。

### 服务弃用
<!---@Barry, we started listing service deprecations earlier this summer. --->
- **iOS 公司门户应用的支持更改**<br/>
在 9 月，要求适用于 iOS 的 Microsoft Intune 公司门户应用的所有用户都使用最新版本。 新用户将只能够下载最新版本，而当前用户必须更新到最新版本。 最新版本需要 iOS 8.0 或更高版本，因此运行较旧的 iOS 版本的设备将无法使用公司门户或者进行注册，直到将其设备更新为 iOS 8.0 或更高版本，并且将公司门户应用更新到最新版本。 运行 iOS 8.0 以下版本的已注册设备将继续受管理，并将列在 Intune 管理员控制台中。  

- **最低 iOS 托管浏览器版本已更新为 8.0**<br/>
Intune 将于 8 月发布适用于 iOS 的更新的 Microsoft Intune 托管浏览器应用，该应用将仅支持运行 iOS 8.0 或更高版本的设备。 iOS 7.1 设备仍将能够使用现有的托管浏览器应用，请鼓励你的用户更新为 iOS 8.0 或更高版本，以访问和充分利用新的托管浏览器功能。  
<!---TFS 1313253--->

- **适用于 Windows 8 和 Windows Phone 8 的公司门户应用将从 2016 年 9 月起弃用** <br/>
从 2016 年 9 月开始，Microsoft Intune 将结束为适用于 Windows Phone 8 和 Windows 8 平台的 Microsoft Intune 公司门户应用提供支持。 将设备更新到 Windows 8.1 和 Windows Phone 8.1，并使用相应的 Windows 8.1 和 Windows Phone 8.1 公司门户应用继续向这些设备分发应用。
<!---TFS 1255391--->

<!--- - **Custom Group Targeting of Notification Rules Removal.**<br/>
Intune notification rules define who an email alert will be sent to from Intune. Currently, you can configure notification rules to send emails to all users of devices in an Intune device group that you created. From around June 1st 2016 moving forward, targeting user-created groups will no longer be supported.

    Today, to target a notification rule to a group you created from the Microsoft Intune administration console, you would take the following steps:

    In the **Admin** workspace, click **Notification Rules** > **Create New Rule**

    In step two of the Create Notification Rule Wizard, select the device groups which the rule will target. This step, “select device groups”, is being removed from the Intune Console.

    The preliminary timeline for this change is as follows:
    - In August, 2016, new tenants will not see step two of the Create Notification Rule Wizard. Exiting tenants are unaffected.
    - Around September, 2016, some existing tenants will not see the “select device groups” in the wizard.
    - Around November, 2016, we expect that all tenants will not see the “select device groups” in the wizard.

--->



## 早期 Intune 发行版本
如果想要查看在过去六个月内发布在 Intune 中的内容，它们已在[早期 Intune 发行版本](previous-intune-releases.md)文章中列出。

### 另请参阅
* [Microsoft Intune 博客](http://go.microsoft.com/fwlink/?LinkID=273882)
* [云平台路线图](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)



<!--HONumber=Aug16_HO3-->


