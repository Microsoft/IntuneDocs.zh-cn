---
title: "新增功能 | Microsoft Intune"
description: "了解 Microsoft Intune 的当月新增功能和过去版本"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8e88c14ad77d8fe1b4c0fe2e7676d126e6288146
ms.openlocfilehash: bcd77b751c2059131558e1cbfeebd4d3f71086e5


---
# <a name="whats-new-in-microsoft-intune---november-2016"></a>Microsoft Intune 新增功能 - 2016 年 11 月
了解此版本 Microsoft Intune 中的新增功能。 你还可以发现需要计划的即将发生的更改，以及有关过去版本的信息。

所有这些功能最终将支持混合客户部署（带 Intune 的 Configuration Manager）。 有关新的混合功能的详细信息，请查看[混合新增功能页](https://technet.microsoft.com/library/mt718155.aspx)。
<!---@Barry, the above blurb stays in each version, but make sure Tyler signs off each time. Also, remember to set the ms.date in the metadata to the sprint release. --->

## <a name="new-capabilities"></a>新功能

<!--### View App States for All Platforms in Real Time
App installation status is now shown in real-time in the console. When you previously deployed an app, you had to wait for a targeted device to report back before the app install status was displayed in the Intune console.

### Streamline iOS App Management for your End Users
Intune can now automatically take over management of the previously installed app and no end user action is required.

Previously, if the end user of an enrolled iOS device installed an app from the App Store before you deployed that same app with a deployment action of __Available__, then the end user had to:

1. Open the __Company Portal__.
2. Select the app.
3. Tap __Install__ to enable Intune to take over management of the app.-->

<!--### New Microsoft Intune Company Portal App for Windows 10 Devices
Microsoft is releasing a new Intune Company Portal for Windows 10 devices. This app, which leverages the new Windows 10 Universal format, will provide the user with an updated user experience within the app and identical experiences across all Windows 10 devices, PC and Mobile alike - while still enabling all the same functionality that they are using today.

The new app will also allow users to leverage additional platform features like single sign-on and certificate-based authentication on Windows 10 devices. The app will be made available as an upgrade to the existing Windows 8.1 Company Portal and Windows Phone 8.1 Company Portal installs from the Windows Store. It will also be available for sideloading.-->

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



<!--HONumber=Nov16_HO3-->


