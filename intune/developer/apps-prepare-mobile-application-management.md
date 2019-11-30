---
title: 让应用可供使用 Microsoft Intune 进行移动应用管理
description: 本主题中的信息可帮助决定何时应该使用应用包装工具和应用 SDK 来启用自定义业务线应用，以使用移动应用管理策略。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 29e22121-8268-48b5-a671-f940a6be1d24
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 901eaafb24cda185540ffc4b1a56484042af74c1
ms.sourcegitcommit: 23e9c48348a6eba494d072a2665b7481e5b5c84e
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74547688"
---
# <a name="prepare-line-of-business-apps-for-app-protection-policies"></a>准备业务线应用以使用应用保护策略

可以使用 Intune 应用包装工具或 Intune App SDK 来支持应用使用应用保护策略。 通过此信息了解这两种方式以及何时使用这两种方式。

## <a name="intune-app-wrapping-tool"></a>Intune 应用包装工具

App Wrapping Tool 主要用于内部  业务线 (LOB) 应用。 此工具是一个命令行应用程序。它可以在应用周围创建包装器，之后包装器将允许 Intune 应用保护策略管理该应用。 在保护独立软件供应商 (ISV) 提供的应用时，请务必说明 ISV 是否仍然支持包装的应用。

使用此工具不需要源代码，但需要签名凭据。 有关签名凭据的详细信息，请参阅 [Intune 博客](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/)。 有关应用包装工具文档的信息，请参阅 [Android 应用包装工具](app-wrapper-prepare-android.md)和 [iOS 应用包装工具](app-wrapper-prepare-ios.md)。

应用包装工具**不**支持 Apple App Store 或 Google Play 商店中的应用。 也不支持某些需要开发人员集成的功能（请参阅以下功能对照表）。

有关未在 Intune 中注册的设备上的应用保护策略应用包装工具的详细信息，请参阅[保护未在 Microsoft Intune 中注册的设备上的业务线应用及数据](../apps/apps-add.md)。

### <a name="reasons-to-use-the-app-wrapping-tool"></a>使用应用包装工具的原因

* 应用未内置数据保护功能
* 应用非常简单
* 应用是在内部部署的
* 无权访问应用的源代码。
* 未开发应用
* 应用包含最少的用户身份验证体验

### <a name="supported-app-development-platforms"></a>受支持的应用开发平台

|**应用包装工具** | **Xamarin** |**Cordova** |
|------|----|----|
|**iOS** |是|是|
|**Android**|不支持 - 使用 [Intune App SDK Xamarin 绑定](app-sdk-xamarin.md)。|是|

## <a name="intune-app-sdk"></a>Intune App SDK

App SDK 主要面向在 Apple App Store 或 Google Play 商店中安装了应用并想使用 Intune 管理应用的客户。 但是，任何应用都可以利用集成 SDK 的优势，即使是业务线应用。

若要了解有关 SDK 的详细信息，请参阅[概述](app-sdk.md)。 若要开始使用 SDK，请参阅 [Microsoft Intune App SDK 入门](app-sdk-get-started.md)。

### <a name="reasons-to-use-the-sdk"></a>使用 SDK 的原因

* 应用未内置数据保护功能
* 应用复杂且包含许多体验
* 应用部署在 Google Play 商店或 Apple App Store 等公共应用商店中
* 自己是应用开发者，拥有使用 SDK 的技术背景
* 应用具有其他 SDK 集成
* 应用频繁更新

### <a name="supported-app-development-platforms"></a>受支持的应用开发平台

|**Intune App SDK** |**Xamarin** |**Cordova**
|------|----|----|
|**iOS**|支持 - 使用 [Intune App SDK Xamarin Bindings](app-sdk-xamarin.md)。|否|
|**Android**| 支持 - 使用 [Intune App SDK Xamarin Bindings](app-sdk-xamarin.md)。|否|

### <a name="not-using-an-app-development-platform-listed-above"></a>不使用上面列出的应用开发平台？

Intune SDK 开发团队主动测试和维护对使用原生 Android、iOS（Obj-C、Swift）、Xamarin、Xamarin.Forms 和 Cordova 平台生成的应用的支持。 虽然某些客户已成功将 Intune SDK 与 React Native 和 NativeScript 等其他平台集成，但我们不会使用受支持平台之外的任何方式为应用开发人员提供明确的指导或插件。 

## <a name="feature-comparison"></a>功能比较

此表列出了可用于 App SDK 和应用包装工具的设置。

|功能|App SDK|应用包装工具|
|-----------|---------------------|-----------|
|限制显示在企业托管浏览器内的 Web 内容|X|X|
|阻止 Android、iTunes 或 iCloud 备份|X|X|
|允许应用向其他应用传送数据|X|X|
|允许应用从其他应用接收数据|X|X|
|限制使用其他应用剪切、复制和粘贴|X|X|
|指定可能会从托管应用中剪切或复制的字符数|X|X|
|访问需要简单 PIN|X|X|
|指定重置 PIN 前的尝试次数|X|X|
|允许使用指纹而不是 PIN|X|X|
|允许面部识别而非 PIN（仅限 iOS）|X|X|
|访问需要公司凭据|X|X|
|设置 PIN 过期|X|X|
|阻止在已越狱或取得 root 权限的设备上运行托管应用|X|X|
|加密应用数据|X|X|
|在指定分钟数后重新检查访问要求|X|X|
|指定离线宽限期|X|X|
|阻止屏幕捕捉（仅限于 Android 设备）|X|X|
|支持未进行设备注册的 MAM|X|X|
|完全擦除应用数据|X|X|
|多标识方案中的工作和学校数据的选择性擦除 <br><br>**注意：** 对于 iOS 设备，删除管理配置文件时，也会删除该应用。|X||
|防止“另存为”|X||
|目标应用程序配置（或通过 "MAM 通道" 的应用配置）|X||
|支持多身份标识|X||
|可自定义样式 |X|||
|按需应用与 Citrix mVPN 的 VPN 连接|X|X| 
|禁用联系人同步|X|X|
|禁用打印|X|X|
|要求最低应用版本|X|X|
|要求最低操作系统版本|X|X|
|要求最低 Android 安全修补程序版本（仅限 Android）|X|X|
|要求最低 Intune SDK for iOS（仅限 iOS）|X|X|
|SafetyNet 设备证明（仅限 Android）|X|X|
|对应用进行威胁扫描（仅限 Android）|X|X|

## <a name="next-steps"></a>后续步骤

要详细了解应用保护策略和 Intune，请参阅以下主题：

- [Android 应用包装工具](app-wrapper-prepare-android.md)<br>
- [iOS 应用包装工具](app-wrapper-prepare-ios.md)<br>
- [使用 SDK 启用针对移动应用程序管理的应用](app-sdk.md)
