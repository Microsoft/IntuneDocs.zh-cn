---
title: "新增功能 | Microsoft Intune"
description: "了解 Microsoft Intune 的当月新增功能和过去版本"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8ef3b7e4eec5a520c93fb3f70c8e5b6ee7d2c3aa
ms.openlocfilehash: e0b0c7eb3ddc07f05fc0c2e4caa6726ed052c9d8


---
# <a name="whats-new-in-microsoft-intune---november-2016"></a>Microsoft Intune 新增功能 - 2016 年 11 月
了解此版本 Microsoft Intune 中的新增功能。 你还可以发现需要计划的即将发生的更改，以及有关过去版本的信息。

> [!Note]
> 所有这些功能最终将支持混合客户部署（带 Intune 的 Configuration Manager）。 有关新的混合功能的详细信息，请查看[混合新增功能页](https://docs.microsoft.com/en-us/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。

## <a name="new-capabilities"></a>新功能

<!--### View App States for All Platforms in Real Time
App installation status is now shown in real-time in the console. When you previously deployed an app, you had to wait for a targeted device to report back before the app install status was displayed in the Intune console.

### Streamline iOS App Management for your End Users
Intune can now automatically take over management of the previously installed app and no end user action is required.

Previously, if the end user of an enrolled iOS device installed an app from the App Store before you deployed that same app with a deployment action of __Available__, then the end user had to:

1. Open the __Company Portal__.
2. Select the app.
3. Tap __Install__ to enable Intune to take over management of the app.-->

__适用于 Windows 10 设备的新 Microsoft Intune 公司门户__ Microsoft 将发布[适用于 Windows 10 设备的新 Microsoft Intune 公司门户](https://www.microsoft.com/store/apps/9wzdncrfj3pz)。 此应用利用了新 Windows 10 Universal 格式，将在应用内为用户提供更新的用户体验，且跨所有 Windows 10 设备（PC 和移动设备等）提供相同的体验，同时还将保持现有的一切功能。

新应用还允许用户们在 Windows 10 设备上利用传统平台功能，例如单一登录 (SSO) 和基于证书的身份验证。 此应用将作为对现有 Windows 8.1 公司门户和 Windows Phone 8.1 公司门户（安装自 Windows 应用商店）的升级而提供。 有关详细信息，请转到 [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp)。

<!--### Support for Windows Store for Business Apps Being Deployed as Available
You can now deploy apps you synchronized from the Windows Store for Business (WSfB) with a deployment action of __Available__ or __Required__. After syncing WSfB apps into Intune, administrators will be able to target those apps as available installs to groups of users. End users will see the deployed WSfB apps as available for install in the Universal Company Portal, where they can choose whether they would like to acquire the apps.

### Conditional Access for MAM with SharePoint Online

You can block apps that are not supported by Intune mobile app management (MAM) policies from accessing SharePoint online.  You can get started in Intune mobile app management via the Azure portal. Look for the  Conditional Access section in the “Settings” blade which now includes the option for SharePoint online.-->

> [!IMPORTANT]

> __Intune 和 Android for Work 更新__

> 虽然可通过“必需”操作部署 Android for Work 应用，但如果已将 Intune 组迁移至新的 Azure AD 组体验，则只可以将应用部署为“可用”。

### <a name="intune-app-sdk-for-cordova-plugin-now-supports-mam-without-enrollment"></a>Intune App SDK for Cordova 插件现在无需注册便可支持 MAM
应用开发人员现在可以使用 Intune App SDK for Cordova 插件启用 MAM 功能，而无需在适用于 Android 和 iOS 的基于 Cordova 的应用中注册设备。 可在[此处](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)找到 Intune App SDK for Cordova 插件。

### <a name="intune-app-sdk-xamarin-component-now-supports-mam-without-enrollment"></a>Intune App SDK Xamarin 组件现在无需注册便可支持 MAM
应用开发人员现在可以使用 Intune App SDK Xamarin 组件启用 MAM 功能，而无需在适用于 Android 和 iOS 的基于 Xamarin 的应用中注册设备。 可在[此处](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)找到 Intune App SDK Xamarin 组件。

## <a name="notices"></a>通知

### <a name="symantec-signing-certificate-no-longer-requires-signed-windows-phone-8-company-portal-for-upload"></a>上传 Symantec 签名证书不再需要已签名的 Windows Phone 8 公司门户
上传 Symantec 签名证书将不再需要已签名的 Windows Phone 8 公司门户应用。 可以独立上传该证书。

## <a name="deprecations"></a>弃用功能

### <a name="support-for-the-windows-phone-8-company-portal"></a>对 Windows Phone 8 公司门户的支持
现在将弃用对 Windows Phone 8 公司门户的支持。 2016 年 10 月弃用了对 Windows Phone 8 和 WinRT 平台的支持。 2016 年 10 月弃用了对 Windows 8 公司门户的支持。


### <a name="see-also"></a>另请参阅
* [Microsoft Intune 博客](http://go.microsoft.com/fwlink/?LinkID=273882)
* [云平台路线图](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [早期 Intune 发行版本](whats-new-archive.md)



<!--HONumber=Dec16_HO1-->


