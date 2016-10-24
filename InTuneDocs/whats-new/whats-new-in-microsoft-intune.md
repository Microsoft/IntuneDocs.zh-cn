---
title: "新增功能 | Microsoft Intune"
description: "了解 Microsoft Intune 的当月新增功能和过去版本"
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 10/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 503719953031bf5079b2bf5bc84a0497d708f79a
ms.openlocfilehash: 730809e0841a248b90f5fe157f2c6338bfd32b2d


---
# Microsoft Intune 新增功能 -- 2016 年 10 月
了解此版本 Microsoft Intune 中的新增功能。 你还可以发现需要计划的即将发生的更改，以及有关过去版本的信息。

所有这些功能最终将支持混合客户部署（带 Intune 的 Configuration Manager）。 有关新的混合功能的详细信息，请查看[混合新增功能页](https://technet.microsoft.com/library/mt718155.aspx)。
<!---@Barry, the above blurb stays in each version, but make sure Tyler signs off each time. Also, remember to set the ms.date in the metadata to the sprint release. --->

## 新增功能

### 用于移动应用程序管理的条件访问
你将能够限制对 Exchange Online 的访问，以便访问只能来自支持 Intune 移动应用程序管理策略的应用（如 Outlook）。 [这一新功能](/intune/deploy-use/allow-policy-managed-apps-access-to-o365)与 Intune 移动应用管理 (MAM) 策略实现完美配对，因为你可以阻止对内置邮件客户端或其他未配置 Intune MAM 策略的应用的访问。 这可确保用户使用可通过 Intune MAM 进行保护的应用访问组织数据。 你可以通过 Azure 门户开始使用 Intune 移动应用管理。 在“设置”边栏选项卡中查找新的“条件访问”分区。

### Windows 电脑的条件访问
现在可通过 Intune 管理控制台创建条件访问策略，阻止 Windows 电脑访问 [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) 和 [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)。 还可以创建条件访问策略，阻止访问 Office 桌面和通用应用程序。

### Android for Work 支持
目前 Intune 是 Android for Work 计划的一部分。 从本月起，我们将开始推出对 Android for Work 中 Intune 功能的支持。
[阅读 Microsoft 关于针对 Android for Work 的 Intune 支持公告](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/12/microsoft-intune-support-for-android-for-work/)。

以下 Intune 主题是新主题或使用 Android for Work 信息进行了更新：

对于 IT 专业人员：
- [设置 Android for Work](/intune/deploy-use/set-up-android-for-work)
<!--- [Nathan Bigman's resource access topics]()-->
- [使用 Intune 限制对 Exchange Online 和新版 Exchange Online Dedicated 的电子邮件访问](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
- [使用 Intune 限制对 Exchange 内部部署和旧版 Exchange Online Dedicated 的电子邮件访问](/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
- [Android for Work 合规性策略设置](/intune/deploy-use/afw-compliance-policy-settings-in-microsoft-intune)
- [如何部署 Android for Work 应用](/intune/deploy-use/android-for-work-apps)
- [使用移动应用配置策略配置 Android for Work 应用](/intune/deploy-use/afw-app-configuration-policy)
- [Android for Work 策略设置](/intune/deploy-use/android-for-work-policy-settings-in-microsoft-intune)

对于最终用户：
- [创建工作配置文件时会发生的情况](/intune/enduser/what-happens-when-you-create-a-work-profile-android)
- [创建工作配置文件并在 Intune 中注册设备](/intune/enduser/create-a-work-profile-and-enroll-your-device-in-intune-android)

### 集成 Lookout 以保护 iOS 设备
在 10 月，Microsoft 将与 Lookout 的移动威胁防护解决方案集成，以通过检测设备上的恶意软件、危险应用等来保护 iOS 移动设备。 Lookout 的解决方案有助于确定威胁级别，可对该功能进行配置。 可以在 Intune 中创建合规性策略规则，以根据 Lookout 的风险评估来确定设备合规性。 使用条件访问策略，你可以基于设备合规性状态允许或阻止访问公司资源。

将提示不合规 iOS 设备的最终用户进行注册，并要求其在设备上安装 Lookout for Work 应用，激活该应用并修正 Lookout for Work 应用程序中报告的威胁，以便获得对公司数据的访问权限。 了解如何[配置并部署 Lookout for Work 应用](/intune/deploy-use/configure-and-deploy-lookout-for-work-apps)。
<!--TFS 1319493-->

<!--### New Microsoft Intune Company Portal available for Windows 10 devices
Microsoft is releasing a new [Microsoft Intune Company Portal for Windows 10 devices](https://go.microsoft.com/fwlink/?linkid=830663). This app, which leverages the new Windows 10 Universal format, will provide the user with an updated user experience within the app and identical experiences across all Windows 10 devices, PC and Mobile alike, while still enabling all the same functionality that they are using today.

The new app will also allow users to leverage additional platform features like single sign-on (SSO) and certificate-based authentication on Windows 10 devices. The app will be made available as an upgrade to the existing Windows 8.1 Company Portal and Windows Phone 8.1 Company Portal installs from the Windows Store.-->

### Intune App Wrapping Tool for Android
可以利用 Intune App Wrapping Tool，使应用能够使用 Intune 移动应用程序管理 (MAM) 策略。 现在可支持 MAM 策略，且无需设备注册。

### 从使用 MAM 策略管理的应用中管理打印
现可阻止打印来自使用了 MAM 策略的应用中的公司数据。 可在 [Azure 门户](/Intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)中使用此设置，且 [iOS](/Intune/deploy-use/ios-mam-policy-settings) 和 [Android](/Intune/deploy-use/android-mam-policy-settings) 设备均支持此设置。
<!--TFS 1014328-->

## 通知

### Android Samsung KNOX 与 Intune 的兼容性
Samsung Galaxy Ace 手机的某些型号无法作为 Samsung KNOX 设备通过 Intune 进行管理。 当你使用 Intune 注册这些设备时，它们将被视为标准 Android 设备来进行管理。

受影响的型号包括：

* SM-G313HU
* SM-G313HY
* SM-G313M
* SM-G313MY
* SM-G313U

你和最终用户无需采取进一步的操作。 有关详细信息，请访问 [Samsung KNOX](https://www.samsungknox.com) 网站。

### 用于 Windows 8 的公司门户应用已停用；对 Windows Phone 8 和 Windows RT 平台的支持已终止
从 2016 年 10 月开始，Microsoft Intune 将终止对 Windows 8 公司门户的支持。 另外，Microsoft Intune 还将终止对 Windows Phone 8 和 Windows RT 平台的支持。 因此，将无法注册或更新任何 Windows Phone 8 或 Windows RT 设备。

可以继续管理已注册的 Windows Phone 8、Windows RT 和 Windows 8 设备。 将 Windows Phone 8 和 Windows 8 设备更新到 Windows 8.1 和 Windows Phone 8.1，并使用相应的 Windows 8.1 和 Windows Phone 8.1 公司门户应用在不中断的情况下继续向这些设备分发应用。

从 2016 年 11 月开始，我们将终止对 Windows Phone 8 公司门户的支持。
<!--TFS 1255391-->

## 即将推出

### 用于 Windows 10 设备的新 Microsoft Intune 公司门户
Microsoft 正在发布适用于 Windows 10 设备的新 Microsoft Intune 公司门户。 此应用利用了新 Windows 10 Universal 格式，将在应用内为用户提供更新的用户体验，且跨所有 Windows 10 设备（PC 和移动设备等）提供相同的体验，同时还将保持现有的一切功能。

新应用还允许用户们在 Windows 10 设备上利用传统平台功能，例如单一登录 (SSO) 和基于证书的身份验证。 此应用将作为对现有 Windows 8.1 公司门户和 Windows Phone 8.1 公司门户（安装自 Windows 应用商店）的升级而提供。 有关详细信息，请转到 [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp)。
<!--TFS 1016502-->

### 另请参阅
* [Microsoft Intune 博客](http://go.microsoft.com/fwlink/?LinkID=273882)
* [云平台路线图](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [早期 Intune 发行版本](previous-intune-releases.md)



<!--HONumber=Oct16_HO3-->


