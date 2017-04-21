---
title: "Microsoft Intune App SDK Cordova 插件 | Microsoft Docs"
description: 
keywords: "sdk、Cordova、intune"
author: oydang
manager: angrobe
ms.author: oydang
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb940cb9-d43f-45ca-b065-ac0adc61dc6f
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: df54ac3a62b5ef21e8a32f3a282dd5299974a1b0
ms.openlocfilehash: 40c369bb0ff18bda30b221c461f75799e601c67c
ms.lasthandoff: 04/12/2017


---
# <a name="microsoft-intune-app-sdk-cordova-plugin"></a>Microsoft Intune App SDK Cordova 插件

> [!NOTE]
> 你可能希望首先阅读 [ Intune App SDK 入门指南](intune-app-sdk-get-started.md)一文，其中介绍了如何为每个受支持的平台上的集成做准备。

## <a name="overview"></a>概述

[Intune App SDK Cordova 插件](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)允许在使用 Cordova 生成的 iOS 和 Android 应用中启用 [Intune 移动应用保护策略](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)。 该插件允许开发人员将 Intune 应用和数据保护功能集成到基于 Cordova 的应用中。

你会发现你可以在不改变应用行为的情况下启用 SDK 功能。 一旦将插件内置到 iOS 或 Android 应用中，Microsoft Intune 管理员就能够部署 Intune 应用保护策略，该策略由各种数据保护功能组成。 插件已生成，将自动执行 Cordova 生成过程中的大部分步骤。 因此，你能够快速启用应用以进行 Intune 应用保护。 若要开始，请根据目标平台按照以下步骤操作。

## <a name="supported-platforms"></a>支持的平台

* 该插件适用于 Windows、Mac 和 Linux 操作系统
* 该插件适用于 `minSdkVersion` >= 14 且 `targetSdkVersion` <= 24 的 Android 应用
* 该插件适用于面向 iOS 9.0 及更高版本的 iOS 应用。

## <a name="intune-mobile-application-management-scenarios"></a>Intune 移动应用程序管理方案

* 注册了 Intune MDM 的设备
* 注册了第三方 EMM 的设备
* 非托管设备（未向任何 MDM 注册）

使用 Intune App SDK Cordova 插件生成的 Cordova 应用现在可以在已注册和未注册 Intune 移动设备管理 (MDM) 的设备上接收 Intune 应用保护策略。

## <a name="prerequisites"></a>先决条件

### <a name="android"></a>Android

* 必须始终在设备上安装最新的 Microsoft Intune 公司门户应用。
* Java 7 必须至少位于使用插件时将执行 Cordova 生成的路径上。

### <a name="ios"></a>iOS

* 必须在设备上安装最新的 Microsoft Intune 公司门户应用以使用 MDM 功能。 没有设备注册功能的 Intune 应用保护策略则*不*需要。

### <a name="both-platforms"></a>两个平台

* 需要 0.8.0+ 版本的[适用于 Cordova 的 Azure Active Directory 身份验证库 (ADAL) 插件](https://github.com/AzureAD/azure-activedirectory-library-for-cordova)。

> [!NOTE]
> 根据[此处](https://issues.apache.org/jira/browse/CB-6227?jql=text%20~%20%22plugin%20dependency%22)记录的 Apache Cordova bug，已经具有插件依赖关系的应用不会自动将插件升级到所请求的版本。



## <a name="quick-start"></a>快速入门

1. 更新 ADAL 版本：

  ```shell
  cordova plugin remove cordova-plugin-ms-adal
  cordova plugin add cordova-plugin-ms-adal@0.8.x
  ```

2. 添加 Intune App SDK for Cordova 插件：

  ```shell
  cordova plugin add cordova-plugin-ms-intune-mam
  ```

## <a name="build-the-plugin-into-your-ios-app"></a>将插件内置到 iOS 应用

需要针对应用完成一些步骤才能启用 Intune 应用保护策略。 为了方便起见，这些步骤将作为预生成挂钩在 Cordova 生成过程中自动执行。 因此，自动步骤将会修改与项目配置关联的 `*.pbxproj`、`*-Info.plist` 和 `*.entitlements` 文件。 如果项目中未包含授权文件，插件将自动创建一个。

此设置仅支持单个目标，并且如果有多个目标则将在找到的第一个目标上执行配置。 如果该进程失败，请检查：

1. 应用的 Xcode 项目是 `[name].xcodeproj`，其中 `[name]` 是在 `config.xml` 中定义的值
2. 项目使用[标准 Cordova 应用目录结构](https://cordova.apache.org/docs/en/latest/reference/cordova-cli/index.html#directory-structure)。

## <a name="build-the-plugin-into-your-android-app"></a>将插件内置到 Android 应用

1. 使用最新的 Cordova 工具导入此插件。 该插件将作为 `after_compile` 步骤自动调用。

2. 在生成过程结束时，该插件将创建一个启用了 Intune 的生成 apk 版本 (Android API 14+)。 生成输出将包含 `[Project]-intunewrapped-[Build_Configuration].apk`（例如 `helloWorld-intunewrapped-debug.apk`）。

> [!NOTE]
> 插件仅支持 Gradle 生成。

由于[此处](https://issues.apache.org/jira/browse/CB-9434)的 Cordova bug 字段，导致在 `cordova run` 上忽略某些 Cordova 挂钩，若要从命令行运行已包装的应用，必须执行以下操作：

```shell
$ cordova build
$ cordova run --nobuild
```

## <a name="sign-your-android-app"></a>对 Android 应用签名

该插件会自动识别你在以下位置提供给 Cordova 的签名信息：

* platforms/android/debug-signing.properties
* platforms/android/release-signing.properties
* res/native/android/ant.properties

有关预期格式的详细信息，请参阅 [ Cordova Gradle 签名信息](https://cordova.apache.org/docs/en/latest/guide/platforms/android/#using-gradle)。

目前不支持在 `build.json` 中或任意位置（通过参数向 Cordova 版本提供）提供签名信息的功能。

## <a name="debugging-from-visual-studio"></a>通过 Visual Studio 进行调试

第一次启动应用后，会看到一个对话框，告知你该应用是通过 Intune 管理的。 点击“不再显示”，然后再次从 VS 中单击“调试/运行”按钮以点击断点。

## <a name="known-limitations"></a>已知限制

### <a name="android"></a>Android

* MultiDex 支持不完整。
* 应用必须具有 `minSdkVersion` 14 和 `targetSdkVersion` 24 或更低版本。 目前不支持面向 API 25 的应用
* 不能对已使用 V2 签名方案签名的应用重新签名。 当该插件包装 V2 签名的应用时，包装的输出 .apk 是未签名的。
*
  * 你可以通过将以下内容添加到 `build-extras.gradle` 文件，禁用 Cordova 的默认 V2 签名：

  ```gradle
  android {
      signingConfigs {
          release {
              v2SigningEnabled false
          }
          debug {
              v2SigningEnabled false
          }
      }
      buildTypes {
          release {
              signingConfig signingConfigs.release
          }
          debug {
              signingConfig signingConfigs.debug
          }
      }
  }
  ```

### <a name="ios"></a>iOS

* 每当修改 **Info.plist** 文件的 **CFBundleDocumentTypes** 节点下的 UTI 列表时，必须在相同 plist 文件的所导入 UTI 部分中清除 Intune UTI（**UTImportedTypeDeclarations** 节点），然后才能再次生成。 所有 Intune UTI 将以前缀 `com.microsoft.intune.mam` 开头。

* 如果要从 Cordova 项目中删除 Cordova 插件的 Intune App SDK，还必须删除 iOS 平台并重新添加它，以便撤消 .xcodeproj 和 .plist 文件中的一些 Intune 配置。

