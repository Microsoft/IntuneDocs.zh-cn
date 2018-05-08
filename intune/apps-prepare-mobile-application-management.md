---
title: 准备业务线应用以使用应用保护策略
titlesuffix: Microsoft Intune
description: 借助应用包装工具和应用 SDK，自定义业务线应用可使用 Microsoft Intune 中的应用保护策略。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 29e22121-8268-48b5-a671-f940a6be1d24
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5ae3b19cfe57c48ac262a376c778d7d593456991
ms.sourcegitcommit: 0f1a5d6e577915d2d748d681840ca04a0a2604dd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="prepare-line-of-business-apps-for-app-protection-policies"></a>准备业务线应用以使用应用保护策略

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

可以使用 Intune 应用包装工具或 Intune App SDK 来支持应用使用应用保护策略。 通过此信息了解这两种方式以及何时使用这两种方式。

## <a name="intune-app-wrapping-tool"></a>Intune 应用包装工具
应用包装工具主要用于内部业务线 (LOB) 应用。 此工具是一个命令行应用程序。它可以在应用周围创建包装器，之后包装器将允许 Intune 应用保护策略管理该应用。

使用此工具不需要源代码，但需要签名凭据。 有关签名凭据的详细信息，请参阅 [Intune 博客](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/)。 有关应用包装工具文档的信息，请参阅 [Android 应用包装工具](app-wrapper-prepare-android.md) 和 [iOS 应用包装工具](app-wrapper-prepare-ios.md)。

应用包装工具**不**支持 Apple App Store 或 Google Play 商店中的应用。 也不支持某些需要开发人员集成的功能（请参阅以下功能对照表）。


有关未在 Intune 中注册的设备上的应用保护策略应用包装工具的详细信息，请参阅[保护未在 Microsoft Intune 中注册的设备上的业务线应用及数据](/intune-classic/deploy-use/protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune)。

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
|**Outlook Web Access (OWA)**| 提供预览 |是|

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
|**Outlook Web Access (OWA)**| 支持 - 使用 [Intune App SDK Xamarin Bindings](app-sdk-xamarin.md)。|否|

## <a name="feature-comparison"></a>功能比较
此表列出了可用于 App SDK 和应用包装工具的设置。

> [!NOTE]
> 应用包装工具可以与独立 Intune 或带 Configuration Manager 的 Intune 结合使用。

|                                                         功能                                                          | App SDK | 应用包装工具 |
|--------------------------------------------------------------------------------------------------------------------------|---------|-------------------|
|                              限制显示在企业托管浏览器内的 Web 内容                              |    X    |         X         |
|                                        阻止 Android、iTunes 或 iCloud 备份                                        |    X    |         X         |
|                                         允许应用向其他应用传送数据                                         |    X    |         X         |
|                                        允许应用从其他应用接收数据                                         |    X    |         X         |
|                                      限制使用其他应用剪切、复制和粘贴                                       |    X    |         X         |
|                                              访问需要简单 PIN                                               |    X    |         X         |
|                                         使用 Intune PIN 替换内置应用 PIN                                         |    X    |                   |
|                                     指定重置 PIN 前的尝试次数                                      |    X    |         X         |
|                                             允许使用指纹而不是 PIN                                             |    X    |         X         |
|                                         访问需要公司凭据                                         |    X    |         X         |
|                             阻止在已越狱或取得 root 权限的设备上运行托管应用                              |    X    |         X         |
|                                                     加密应用数据                                                     |    X    |         X         |
|                           在指定分钟数后重新检查访问要求                            |    X    |         X         |
|                                             指定离线宽限期                                             |    X    |         X         |
|                                           阻止屏幕捕捉（仅限于 Android 设备）                                            |    X    |         X         |
|                                        支持未进行设备注册的 MAM                                         |    X    |         X         |
|                                                        完全擦除                                                         |    X    |         X         |
| 选择性擦除 <br></br><strong>注意：</strong>对于 iOS 设备，删除管理配置文件时，也会删除该应用。 |    X    |                   |
|                                                    防止“另存为”                                                     |    X    |                   |
|                                            目标应用程序配置                                            |    X    |                   |
|                                                支持多身份标识                                                |    X    |                   |
|                                                    可自定义样式                                                    |    X    |                   |

## <a name="next-steps"></a>后续步骤

要详细了解应用保护策略和 Intune，请参阅以下主题：

  -  [Android 应用包装工具](app-wrapper-prepare-android.md)</br>
  - [iOS 应用包装工具](app-wrapper-prepare-ios.md)</br>
  - [使用 SDK 启用针对移动应用程序管理的应用](/intune-classic/deploy-use/use-the-sdk-to-enable-apps-for-mobile-application-management)
