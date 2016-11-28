---
title: "Microsoft Intune App SDK 入门 | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.author: oydang
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ca4623db80d711f3543b6d688fb1bb1ef228c62c
ms.openlocfilehash: 2a65ae79a0bba21d555dbed9f1bc40e01452f08c


---

# <a name="get-started-with-the-microsoft-intune-app-sdk"></a>Microsoft Intune App SDK 入门

本指南将帮助你通过 Microsoft Intune 快速启用移动应用进行移动应用程序管理 (MAM)。 先去了解 [Intune App SDK 概述](intune-app-sdk.md)中介绍的 Intune App SDK 优点可能会很有帮助。

本指南介绍了使用 Microsoft Intune 在应用中启用 MAM 的主要步骤。 Intune App SDK 支持跨平台的类似方案，且旨在跨平台为 IT 管理员创造一致的体验。 但是由于平台限制，某些功能的支持存在细微差异。

## <a name="register-your-store-app-with-microsoft"></a>向 Microsoft 注册应用商店应用

**如果应用是公司内部应用，不会在公共应用商店中提供**：

则*不需要*注册应用。 对于内部业务线应用，IT 管理员将对应用进行内部部署。 Intune 将检测使用 SDK 构建的应用，并允许 IT 管理员向其应用 MAM 策略设置。 你可以跳到[使用 SDK 对 MAM 启用 iOS 或 Android 移动应用](#enable-your-ios-or-android-mobile-app-for-mam-with-the-sdk)部分。

**如果应用将被发布到公共应用商店（例如Apple App Store 或 Google Play）**：

则*必须*首先向 Microsoft Intune 注册应用并同意注册条款。 然后，IT 管理员可将 Intune MAM 策略设置应用到启用的应用，该应用将被列为 Intune 应用合作伙伴。 除非已完成注册并已由 Microsoft Intune 团队确认，否则 Intune 管理员不能向应用深层链接应用 MAM 策略。 Microsoft 还会将你的应用添加到其 [Microsoft Intune 合作伙伴页](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps)。 在该页面中，将显示应用的图标，表明它支持 Microsoft Intune MAM 策略。

若要开始注册过程，请填写 [Microsoft Intune 应用合作伙伴调查表](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR6oOVGFZ3pxJmwSN1N_eXwJUQUc5Mkw2UVU0VzI5WkhQOEYyMENWNDBWRS4u)。

我们将使用调查表答复中列出的电子邮件地址来联系你并继续注册过程。 此外，如果我们有任何问题，我们会使用你的注册电子邮件地址与你联系。

> [!NOTE]
> 在调查表中以及通过与 Microsoft Intune 团队的电子邮件通信收集到的所有信息都会遵循 [Microsoft 隐私声明](https://www.microsoft.com/en-us/privacystatement/default.aspx)。

**注册过程中会出现的情况**：

1. 提交调查表后，我们会通过你的注册电子邮件地址联系你，以确认成功接收或请求提供其他信息以完成注册。
2. 接收到所有必要信息后，我们将发送 Microsoft Intune 应用合作伙伴协议供你签名。 此协议描述了你的公司在成为 Microsoft Intune 应用合作伙伴之前必须接受的条款。
3. 向 Microsoft Intune 服务成功注册应用后以及在 [Microsoft Intune 合作伙伴](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps)站点上推荐你的应用时会予以通知。
4. 最后，会将你的应用的深层链接添加到下个月的 Intune 服务更新中。 例如，如果注册信息在七月完成，则会在八月中旬支持深层链接。

如果应用的深层链接在将来发生更改，则需要重新注册应用。 此外，如果使用新版本的 Intune App SDK 更新应用，请告知我们。



## <a name="download-the-sdk-files"></a>下载 SDK 文件

用于本机 iOS 和 Android 的 Intune App SDK 都托管于 Microsoft GitHub 帐户。 下面的公共存储库具有适用于 iOS 和 Android 的 SDK 文件，分别为：

* [用于 iOS 的 Intune 应用 SDK](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)
* [用于 Android 的 Intune 应用 SDK](https://github.com/msintuneappsdk/ms-intune-app-sdk-android)

如果应用是 Xamarin 或 Cordova 应用，请使用以下开发人员工具：

* [Intune App SDK Xamarin 组件](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)
* [Intune App SDK Cordova 插件](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)

注册可用于从存储库中分叉和拉取的 GitHub 帐户是一个好办法。 GitHub 可让开发人员与我们的产品团队进行沟通、开展问题并快速接收回复、查看发行说明并向 Microsoft 提供反馈。 有关 GitHub 帐户和存储库的问题，请联系 msintuneappsdk@microsoft.com。





## <a name="enable-your-ios-or-android-mobile-app-for-mam-with-the-sdk"></a>使用 SDK 对 MAM 启用 iOS 或 Android 移动应用

若要将 Intune App SDK 集成到本机 iOS 应用，需查看以下文档：

* **[Intune App SDK for iOS 开发人员指南](intune-app-sdk-ios.md)**：本文档将指导你逐步完成使用 Intune App SDK 启用移动 iOS 应用的过程。


若要将 Intune App SDK 集成到本机 Android 应用，需查看以下文档：

* **[Intune App SDK for Android 开发人员指南](intune-app-sdk-android.md)**：本文档将指导你逐步完成使用 Intune App SDK 启用移动 Android 应用的过程。

若要使用 Intune App SDK Cordova 插件生成 Cordova 应用，需查看以下文档：

* **[Intune App SDK Cordova 插件指南](intune-app-sdk-cordova)**：本文档可帮助你使用适用于 Intune 移动应用程序管理的 Cordova 来生成 iOS 和 Android 应用。

若要使用 Intune App SDK Xamarin 组件生成 Xamarin 应用，需查看以下文档：

* **[Intune App SDK Xamarin 组件指南](intune-app-sdk-xamarin)**：本文档可帮助你使用适用于 Intune 移动应用程序管理的 Cordova 来生成 iOS 和 Android 应用。




## <a name="configure-telemetry-for-your-app"></a>配置应用遥测

Microsoft Intune 收集应用的使用情况统计数据。

* **Intune App SDK for iOS**：默认情况下，SDK 会记录有关使用事件的 SDK 遥测数据。 会将此数据发送到 Microsoft Intune。

    * 如果选择不从应用将 SDK 遥测数据发送到 Microsoft Intune，则必须通过在 IntuneMAMSettings 字典中将属性 `MAMTelemetryDisabled` 设置为“YES”，来禁用遥测数据传输。

* **Intune App SDK for Android**：不通过 SDK 记录遥测数据。

## <a name="test-your-mam-enabled-app-with-microsoft-intune"></a>使用 Microsoft Intune 测试启用了 MAM 的应用

完成将 iOS 或 Android 应用与 Intune App SDK 集成的必需步骤后，需要确保所有应用管理策略都已针对用户和 IT 管理员启用并正常工作。 若要测试已集成的应用，则需查看以下文档：

<!--TODO-->

* **使用 Microsoft Intune 测试启用了 MAM 的应用**：本文档将指导你逐步了解如何使用 Microsoft Intun 测试启用了 MAM 的 iOS 或 Android 应用。 可在 SDK 的 GitHub 存储库中找到此文档。

* **Microsoft Intune 帐户**：若要使用 Microsoft Intune 测试启用了 MAM 的应用，你将需要 Microsoft Intune 帐户。
    * 如果你是为 Intune MAM 启用 iOS 或 Android 应用商店应用的 ISV，则在使用 Microsoft Intune 完成注册（如注册步骤中所述）后，会收到促销代码。 促销代码允许你注册具有 1 年延期使用的 Microsoft Intune 试用。
    * 如果你正在开发一套不会发送到应用商店的业务应用，则你应能够通过你的组织访问 Microsoft Intune。 你还可以在 [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0) 中注册为期 1 个月的免费试用。



<!--HONumber=Nov16_HO3-->


