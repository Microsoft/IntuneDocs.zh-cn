---
title: "针对移动应用管理准备应用 | Microsoft Intune"
description: "本主题中的信息可帮助你决定何时应该使用 App Wrapping Tool 和应用 SDK 来启用你的自定义业务线应用，以使用移动应用管理策略。"
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 29e22121-8268-48b5-a671-f940a6be1d24
ms.reviewer: oldang
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: df1b58d5ce94c985e71f3afbe228dba9438040dc
ms.openlocfilehash: d79c498fd775ee9b3d59761fec2fe6ebba116d6d


---

# 决定如何使用 Microsoft Intune 为移动应用程序管理准备应用
可以使用 Intune 应用包装工具或 Intune App SDK 启用应用以使用移动应用程序管理 (MAM) 策略。 通过此信息了解这两种方式以及何时使用这两种方式。

## Intune 应用包装工具
应用包装工具主要用于内部业务线 (LOB) 应用。 此工具是一个命令行应用程序。它可以在应用周围创建包装器，之后包装器将允许 Intune 移动应用程序管理策略管理该应用。 

使用此工具不需要源代码，但需要签名凭据。  有关签名凭据的详细信息，请参阅 [Intune 博客](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/)。 有关应用包装工具文档的信息，请参阅 [Android 应用包装工具](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) 和 [iOS 应用包装工具](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)。

应用包装工具**不**支持 Apple App Store 或 Google Play 商店中的应用，也不支持需要开发人员集成的某些功能（请参见以下功能对比表）。

如果已编写应用或者如果源代码不可用，则应该使用应用包装工具，而不是 SDK。

**有关未在 Intune 中注册的设备上的 MAM 应用包装工具的详细信息，请参阅[保护未在 Microsoft Intune 上注册的设备上的业务线应用及数据](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md)**。

### 受支持的应用开发平台

|**应用包装工具** | **Xamarin** |**Cordova** |
|------|----|----|
|**iOS** |是|是|
|**Android**| 否 |是|

## Intune App SDK
App SDK 主要面向在 Apple App Store 或 Google Play 商店中安装了应用并想使用 Intune 管理应用的客户。 但是，任何应用都可以利用集成 SDK 的优势，即使是业务线应用。

若要了解有关 SDK 的详细信息，请参阅[概述](/intune/develop/intune-app-sdk)。 若要开始使用 SDK，请参阅 [Microsoft Intune App SDK 入门](/intune/develop/intune-app-sdk-get-started)。

### 受支持的应用开发平台

|**Intune App SDK** |**Xamarin** |**Cordova**
|------|----|----|
|**iOS**|支持 - 使用 Intune App SDK Xamarin 组件|支持 - 使用 Intune App SDK Cordova 插件|
|**Android**| 支持 - 使用 Intune App SDK Xamarin 组件|支持 - 使用 Intune App SDK Cordova 插件|

## 功能比较
此表列出了可用于 App SDK 和应用包装工具的设置。

> [!NOTE]
> 应用包装工具可以与独立 Intune 或带 Configuration Manager 的 Intune 结合使用。

|功能|App SDK|应用包装工具|
|-----------|---------------------|-----------|
|限制显示在企业托管浏览器内的 Web 内容|X|X|
|阻止 Android、iTunes 或 iCloud 备份|X|X|
|允许应用向其他应用传送数据|X|X|
|允许应用从其他应用接收数据|X|X|
|限制剪切、复制和粘贴到其他应用程序|X|X|
|访问需要简单 PIN|X|X|
|使用 Intune PIN 替换内置应用 PIN|X||
|指定重置 PIN 前的尝试次数|X|X|
|需要指纹而不是 PIN（仅限 iOS设备）<br></br>**注意：**只在仅 MAM 环境下可用|X||
|访问需要公司凭据|X|X|
|阻止在已越狱或取得 root 权限的设备上运行托管应用|X|X|
|加密应用数据|X|X|
|在指定分钟数后重新检查访问要求|X|X|
|指定离线宽限期|X|X|
|阻止屏幕捕捉（仅限于 Android 设备）|X|X|
|完全擦除|X|X|
|选择性擦除 <br></br>**注意：**对于 iOS 设备，删除管理配置文件时，也会删除该应用。|X||
|防止“另存为” |X||
|支持多身份标识|X||
|支持未进行设备注册的 MAM|X|X|
### 另请参阅

[Android 应用包装工具](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[iOS 应用包装工具](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[使用 SDK 启用针对移动应用程序管理的应用](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Sep16_HO4-->


