---
title: "早期版本 | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 10/05/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a5c4b0f15456a9f24c95954d669a17c63f96a459
ms.openlocfilehash: 273016d4fe114bbe60e9cebc06e89584c8f91f0b


---

# Microsoft Intune 中即将推出的功能 - 10 月
**早期版本**提供了一份即将发布的 Microsoft Intune 版本中将出现的功能的列表。 此信息在非常有限的情况下依据保密协议 (NDA) 提供，并不断变化。 此处列出的某些功能有无法按期发布的风险并可能推迟到以后的版本。 正在以试验模式（外部测试）测试其他功能，以确保它们可立即供客户使用。 如果有任何问题或顾虑，请联系 Intune/PM 好友。

本页将定期更新。 回来查看即将推出的更新。

下面的更改依据 Intune 开发。 所有这些功能最终将支持混合客户部署（带 Intune 的 Configuration Manager）。 有关新的混合功能的详细信息，请查看[混合新增功能页](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx)。

### 从使用 MAM 策略管理的应用中管理打印
现可阻止打印来自使用了 MAM 策略的应用中的公司数据。 可在 [Azure 门户](..deployuse/create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)中使用此设置，且 [iOS](..deployuse/ios-mam-policy-settings) 和 [Android](..deployuse/android-mam-policy-settings) 设备均支持此设置。
<!--TFS 1014328-->

### 用于 Windows 10 设备的新 Microsoft Intune 公司门户
Microsoft 正在发布适用于 Windows 10 设备的新 Microsoft Intune 公司门户。 此应用利用了新 Windows 10 Universal 格式，将在应用内为用户提供更新的用户体验，且跨所有 Windows 10 设备（PC 和移动设备等）提供相同的体验，同时还将保持现有的一切功能。

新应用还允许用户们在 Windows 10 设备上利用传统平台功能，例如单一登录 (SSO) 和基于证书的身份验证。 此应用将作为对现有 Windows 8.1 公司门户和 Windows Phone 8.1 公司门户（安装自 Windows 应用商店）的升级而提供。
<!--TFS 1016502-->

### Android for Work 支持

目前 Intune 是 [Android for Work 计划](https://enterprise.google.com/android/partners/)的一部分。 从本月起，我们将开始推出对 Android for Work 中 Intune 功能的支持。

[阅读 Microsoft 关于针对 Android for Work 的 Intune 支持公告](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/12/microsoft-intune-support-for-android-for-work/)。

<!---This month, some newly provisioned Intune tenants will start seeing the Android for Work features. We will announce later when existing tenants will begin to see this feature.--->
<!--TFS 1043303-->

### Android Samsung KNOX 与 Intune 的兼容性

Samsung Galaxy Ace 手机的某些型号无法作为 Samsung KNOX 设备通过 Intune 进行管理。 当你使用 Intune 注册这些设备时，它们将被视为标准 Android 设备来进行管理。
受影响的型号包括：

* SM-G313HU
* SM-G313HY
* SM-G313M
* SM-G313MY
* SM-G313U

你和最终用户无需采取进一步的操作。
有关详细信息，请访问 [Samsung KNOX](https://www.samsungknox.com) 网站。

<!--TFS 1173566 iX blurb provided by Barry; requires PM signoff

### Multi-factor authentication for Android and iOS enrollment

In addition to Windows 8.1 and later, administrators can now enable multi-factor authentication for Android and iOS devices in the Microsoft Intune Enrollment application. -->    

### 用于 Windows 8 的公司门户应用已停用；对 Windows Phone 8 和 Windows RT 平台的支持已终止
从 2016 年 10 月开始，Microsoft Intune 将终止对 Windows 8 公司门户的支持。 另外，Microsoft Intune 还将终止对 Windows Phone 8 和 Windows RT 平台的支持。 因此，将无法注册或更新任何 Windows Phone 8 或 Windows RT 设备。

可以继续管理已注册的 Windows Phone 8、Windows RT 和 Windows 8 设备。 将 Windows Phone 8 和 Windows 8 设备更新到 Windows 8.1 和 Windows Phone 8.1，并使用相应的 Windows 8.1 和 Windows Phone 8.1 公司门户应用在不中断的情况下继续向这些设备分发应用。

从 2016 年 11 月开始，我们将终止对 Windows Phone 8 公司门户的支持。
<!--TFS 1255391-->

### 用于移动应用程序管理的条件访问
现可创建条件访问策略来阻止未托管的移动应用程序访问 [Exchange Online](..deployuse/restrict-access-to-exchange-online-with-microsoft-intune.md) 和 [SharePoint Online](..deployuse/restrict-access-to-sharepoint-online-with-microsoft-intune.md)。 可以阻止那些未通过 Intune App SDK 启用 MAM 的内置电子邮件客户端和应用。  要实现此目的，可以创建条件访问策略，并指定允许其利用 Azure 门户访问 Exchange Online 和 SharePoint Online 的应用程序。
<!--TFS 1317673-->

<!--TFS 1318014; awaiting approval in notes as to whether to proceed

### "Default" policy is deprecated

To minimize unintentionally assigned profiles, Intune is removing support for the "default" Corporate Device Enrollment profile for Apple Device Enrollment Program (DEP) device serial numbers in the new Azure console. Serial numbers synchronized from an Apple DEP account will initially have no Corporate Device Enrollment profile assigned.  A profile must be assigned manually after synchronization. This change will apply to the new console only. Until the existing Admin console is retired, no change will take place.
-->

<!--TFS 1318023; awaiting approval in notes as to whether to proceed

### Deprecation of row-by-row iOS Details review for iOS device CSV uploads

In order to streamline uploading IMEI numbers for Corporate devices and Apple serial numbers for Configurator enrollment, Intune is removing the row by row review of hardware identifiers already found in the system. This review allows the IT Pro to accept associated Details from the CSV to overwrite the existing details for a hardware identifier already in the system. The review will be replaced by a single option to automatically overwrite Details for all hardware identifiers or ignore new details for existing identifiers. This change will apply to the new console only. Until the existing Admin console is retired, no change will take place.
-->

### 集成 Lookout 以保护 iOS 设备
在 10 月，Microsoft 将与 Lookout 的移动威胁防护解决方案集成，以通过检测设备上的恶意软件、危险应用等来保护 iOS 移动设备。 Lookout 的解决方案有助于确定威胁级别，可对该功能进行配置。 可以在 Intune 中创建合规性策略规则，以根据 Lookout 的风险评估来确定设备合规性。 使用条件访问策略，你可以基于设备合规性状态允许或阻止访问公司资源。

将提示不合规 iOS 设备的最终用户进行注册，并要求其在设备上安装 Lookout for Work 应用，激活该应用并修正 Lookout for Work 应用程序中报告的威胁，以便获得对公司数据的访问权限。
<!--TFS 1319493-->

### 适用于 Android 的 Intune App SDK 和 App Wrapping Tool
可以利用 Intune App Wrapping Tool 或 Intune App SDK，使应用程序能够使用 Intune 移动应用程序管理 (MAM) 策略。 App Wrapping Tool 和 SDK 的最新更新将包括：

* 对 Android N 的支持
* 对 MAM 策略的支持，且无需设备注册
* 对基于 Xamarin 的 Android 应用的支持

可在 Android App Wrapping Tool 的公开预览版中测试 MAM（无需设备注册）和 Xamarin 支持：[https://github.com/msintuneappsdk/intune-app-wrapper-android-preview](https://github.com/msintuneappsdk/intune-app-wrapper-android-preview)
<!--TFS 1319511; please create new TFS entry for WN text associated with this TFS item-->

<!--TFS 1319613; no iX review on PM text blurb

### Private preview customers using MAM Conditional Access will have their policies reset

Due to changes in the policy structure for Conditional Access for Mobile App Management, any existing policies that were set by customers through the private preview will be removed. Customers will need to set new policies once the change is made. The timing will coincide with the October service update.
-->

### 另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new-in-microsoft-intune.md)。



<!--HONumber=Oct16_HO1-->


