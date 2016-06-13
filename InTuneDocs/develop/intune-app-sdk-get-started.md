---
# required metadata

title: Microsoft Intune App SDK 入门 | Microsoft Intune
description:
keywords:
author: Msmbaldwin
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune App SDK 入门

本入门指南可帮助你快速通过 Microsoft Intune 使用移动应用程序管理的移动应用。 先去了解 [Intune App SDK 概述](intune-app-sdk.md)中枚举的 Intune App SDK 优点，这一点可能很有用。

本指南会指导完成使用 Microsoft Intune 在应用中启用移动应用管理所需的主要步骤。 Intune App SDK 支持跨平台的类似方案，且旨在跨平台为 IT 管理员创造一致的体验。 但是由于平台限制，某些功能的支持存在细微差异。

# 入门

## 注册 Microsoft Connect

Intune App SDK 当前可通过 Microsoft Connect 进行访问，但需要注册。 若要注册，请使用公司电子邮件注册 [Microsoft 帐户](https://connect.microsoft.com/ConfigurationManagervnext/InvitationUse.aspx?ProgramID=8967&InvitationID=8967-YJYJ-8G6X)。

你的注册会处于待定状态，直到 Intune 团队审查你的请求。 典型响应时间在 2 - 3 个工作日内。 批准之后，你会收到电子邮件通知，其中包含用于下载适用于你的平台的 Intune App SDK 以及所有相关指南的链接。 你还可以在 MSDN 站点上访问这些指南。

## 向 Microsoft Intune 注册应用商店应用

**如果启用的应用是公司内部应用，不会在 Apple 或 Google 应用商店中提供**：无需注册应用。 对于此类内部应用，IT 管理员会将它们直接加载到 Microsoft Intune 控制台以进行部署，Intune 会检测到应用已使用 SDK 进行了生成，并会向 IT 管理员显示对其应用 MAM 策略的选项。 你可以跳到题为[使用 SDK 对 MAM 启用 iOS 或 Android 移动应用](#enable-your-ios-or-android-mobile-app-for-mam-with-the-sdk)的部分。

**如果你是开发将通过 Apple 或 Google 应用商店向客户提供的应用的 ISV**：必须先向 Microsoft Intune 注册应用并同意注册条款。 可以在此时提供应用的深层链接。 此后 IT 管理员可以将 Intune MAM 策略应用于该应用。 除非已完成注册并已由 Microsoft Intune 团队确认，否则不会向应用深层链接提供在管理控制台中应用 MAM 策略的选项。 Microsoft 还维护 Microsoft Intune 合作伙伴网站，应用将在其中进行注册，以便客户知道它支持 Microsoft Intune MAM 策略。

若要开始注册过程，请**查看并签署 **[Microsoft Intune 合作伙伴协议](https://connect.microsoft.com/ConfigurationManagervnext/Survey/Survey.aspx?SurveyID=17806)。 此协议描述了公司在成为 Microsoft Intune 应用合作伙伴之前必须接受的条款。 你需要先登录，然后才能查看此文档。 可以在 Intune App SDK Microsoft Connect 站点中的调查选项卡下或此处找到该协议。 我们还会要求你提供应用的名称、你公司的名称以及指向你的应用的 Google 或 iTunes 应用商店深层链接。

![Microsoft Connect](../media/microsoft-connect.png)

我们会使用你的注册电子邮件地址来确认并完成注册过程的接收。 此外，如果我们有任何问题，我们会使用你的注册电子邮件地址联系你。

**注册过程中会出现的情况**：提交了表单之后，Microsoft 会通过你的注册电子邮件地址联系你，以确认成功接收或请求提供其他信息以完成注册。 向 Microsoft Intune 成功注册你的应用后以及在 Microsoft Intune 合作伙伴站点上推荐你的应用时，也会联系你。 确认收到信息之后，你的应用深层链接将包含在下一月度 Intune 服务更新中。 例如，如果注册信息在七月完成，则会在八月中旬支持应用深层链接。 如果应用商店应用深层链接在将来发生更改，则需要重新注册应用。 如果使用新版本的 Intune App SDK 更新应用，也请告知我们。

**注意**：在以上表单中以及通过与 Intune 团队的电子邮件通信收集的所有信息都遵循 [Microsoft 隐私声明](https://www.microsoft.com/en-us/privacystatement/default.aspx)。

## 使用 SDK 对 MAM 启用 iOS 或 Android 移动应用

要启用 iOS 移动应用，你将需要以下各项：

1. **[Intune App SDK for iOS 开发人员指南](intune-app-sdk-ios.md)**：本文档将指导你逐步完成使用 Intune App SDK 启用移动 iOS 应用的过程。 可以在作为 Intune App SDK 包的一部分下载的文档文件夹中找到此文档。
2. **Intune App SDK for iOS**：作为从 Microsoft Intune 下载的 Intune App SDK 包的一部分，你会发现一个签名文件夹“Intune App SDK for iOS”。 此文件夹包含所有 Intune App SDK for iOS 内容。

要使用 Intune App SDK 启用 android 移动应用，你将需要以下各项：

1. **[Intune App SDK for Android 开发人员指南](intune-app-sdk-android.md)**：本文档将指导你逐步完成使用 Intune App SDK 启用移动 Android 应用的过程。 可以在作为 Intune App SDK 包的一部分下载的文档文件夹中找到此文档。
2. **Intune App SDK for Android**：作为从 Microsoft Intune 下载的 Intune App SDK 包的一部分，你会发现一个签名文件夹“Intune App SDK for Android”。 此文件夹包含所有 Intune App SDK for android 内容。

## 关闭应用的遥测

**Intune App SDK for iOS**：默认情况下，SDK 会记录有关使用事件的 SDK 遥测数据。 会将此数据发送到 Microsoft Intune。

如果你选择不从应用程序将 SDK 遥测数据发送到 Microsoft Intune，则必须通过在 **IntuneMAMSettings** 中将属性 `MAMTelemetryDisabled` 设置为“YES”，来 `IntuneMAMSettings`。

**Intune App SDK for Android**：不通过 SDK 记录 SDK 遥测数据。

## 使用 Microsoft Intune 测试启用了 MAM 的应用

一旦完成了启用（集成 Intune App SDK）iOS 或 Android Intune App SDK 所必须的步骤，你将需要确保所有应用管理策略都已针对最终用户和 IT 管理员启用并正常工作。 要测试已启用的应用，你将需要以下各项：

1. **使用 Microsoft Intune 测试启用了 MAM 的应用**：本文档将指导你逐步了解如何使用 Microsoft Intun 测试启用了 MAM 的 iOS 或 android 应用。 可以在作为 Intune App SDK 包的一部分下载的文档文件夹中找到此文档。
2. **Microsoft Intune 帐户**：要使用 Microsoft Intune 测试启用了 MAM 的应用，你将需要 Microsoft Intune 帐户。 如果你是针对 MAM 启用 iOS 或 android 应用商店应用的 ISV，则在向 Microsoft Intune 完成注册（如注册步骤中所述）之后，你会收到促销代码。 促销代码允许你注册具有 1 年延期使用的 Microsoft Intune 试用。 如果你正在开发一套不会发送到应用商店的业务应用，则你应能够通过你的组织访问 Microsoft Intune。 你还可以向 [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0) 注册为期 1 个月的免费试用。



<!--HONumber=May16_HO2-->


