---
title: "Microsoft Intune App SDK Cordova 插件 | Microsoft Intune"
description: 
keywords: "sdk、Cordova、intune"
author: oydang
manager: angrobe
ms.author: oydang
ms.date: 11/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb940cb9-d43f-45ca-b065-ac0adc61dc6f
ms.reviewer: karthikaraman
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: af7df3fcf50c3508d495522341bb287c638f40a3
ms.openlocfilehash: 2af369cc44c710789ab65eb25f10602882772019


---
# ﻿<a name="microsoft-intune-app-sdk-cordova-plugin"></a>Microsoft Intune App SDK Cordova 插件

> [!NOTE]
> 你可能希望首先阅读 [ Intune App SDK 入门指南](intune-app-sdk-get-started.md)一文，其中介绍了如何为每个受支持的平台上的集成做准备。


## <a name="overview"></a>概述

[Intune App SDK Cordova 插件](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)允许在使用 Cordova 生成的 iOS 和 Android 应用中启用 [Intune 移动应用管理功能](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)。 该插件允许开发人员将 Intune 应用和数据保护功能集成到基于 Cordova 的应用中。

你会发现你可以在不改变应用行为的情况下启用 SDK 功能。 将该插件内置到 iOS 或 Android 移动应用后，IT 管理员将能够通过 Microsoft Intune 移动应用程序管理 (MAM) 部署策略，以便支持各种数据保护功能。 我们已生成插件，以便在 Cordova 生成过程中自动执行大部分步骤。 因此，你将能够快速启用应用以进行管理。 若要开始，请根据目标平台按照以下步骤操作。




## <a name="whats-supported"></a>支持的功能

### <a name="developer-machines"></a>开发人员计算机
* Windows
* Mac OS


### <a name="mobile-app-platforms"></a>移动应用平台
* Android 4.0+
* iOS

### <a name="intune-mobile-application-management-scenarios"></a>Intune 移动应用程序管理方案

* 注册了 Intune MDM 的设备
* 注册了第三方 EMM 的设备
* 非托管设备（未向任何 MDM 注册）

使用 Intune App SDK Cordova 插件生成的 Cordova 应用现在可以在注册了 Intune 移动设备管理 (MDM) 的设备和未注册的设备上接收 Intune 移动应用程序管理 (MAM) 策略。



## <a name="prerequisites"></a>先决条件

### <a name="technical-prerequisites"></a>技术先决条件

* **[仅限 Android]** 必须始终在设备上安装最新的 Microsoft Intune 公司门户应用。


* 需要 0.8.0+ 版本的[适用于 Cordova 的 Azure Active Directory 身份验证库 (ADAL) 插件](https://github.com/AzureAD/azure-activedirectory-library-for-cordova)。
  * **重要提示：**由于[此处](https://issues.apache.org/jira/browse/CB-6227?jql=text%20~%20%22plugin%20dependency%22)归档的 Apache Cordova bug，已具有插件依赖关系的应用不会自动将插件升级到所请求的版本。


### <a name="before-you-install-and-use-microsoft-intune-app-sdk-cordova-plugin-you-must"></a>在安装和使用 Microsoft Intune App SDK Cordova 插件之前，**必须**：

* 查看 [Intune App SDK Cordova 插件许可条款](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam/blob/master/Intune_App_SDK_Cordova_plugin_RTM_license.pdf)。

* 打印并保留一份许可条款，以留作记录。 下载和使用 Intune App SDK Cordova 插件即表示同意这些许可条款。  如果不接受这些条款，请不要使用此软件。


## <a name="quick-start"></a>快速入门

1. 更新 ADAL 版本：

    ```
    cordova plugin remove cordova-plugin-ms-adal
    cordova plugin add cordova-plugin-ms-adal@0.8.x
    ```

2. 添加 Intune App SDK for Cordova 插件：

    ```
    cordova plugin add cordova-plugin-ms-intune-mam
    ```

## <a name="how-to-build-the-plugin-into-your-ios-app"></a>如何将插件内置到 iOS 应用

需要完成一些步骤，以使应用启用 Intune MAM。 为了方便起见，这些步骤将作为预生成挂钩在 Cordova 生成过程中自动执行。 因此，自动步骤将会修改与项目配置关联的 `*.pbxproj`、`*-Info.plist` 和 `*.entitlements` 文件。 如果项目中未包含授权文件，插件将自动创建一个。

此设置仅支持单个目标，并且如果有多个目标则将在找到的第一个目标上执行配置。 如果该进程失败，请检查：

1. 应用的 Xcode 项目是 `[name].xcodeproj`，其中 `[name]` 是在 `config.xml` 中定义的值
2. 项目使用[标准 Cordova 应用目录结构](https://cordova.apache.org/docs/en/latest/reference/cordova-cli/index.html#directory-structure)。

## <a name="how-to-build-the-plugin-into-your-android-app"></a>如何将插件内置到 Android 应用

1. 使用最新的 Cordova 工具导入此插件。 该插件将作为 `after_compile` 步骤自动调用。

2. 该插件将在生成过程结束时创建一个启用了 MAM 的版本的生成 apk (Android API 14+)。 生成输出将包含 `[Project]-intunewrapped-[Build_Configuration].apk`（例如 `helloWorld-intunewrapped-debug.apk`）。

插件仅支持 Gradle 生成。

由于[此处](https://issues.apache.org/jira/browse/CB-9434)的 Cordova bug 字段，导致在 `cordova run` 上忽略某些 Cordova 挂钩，若要从命令行运行已包装的应用，必须执行以下操作：

```
$ cordova build
$ cordova run --nobuild
```


### <a name="signing-your-android-app"></a>对 Android 应用签名
若要将签名信息添加到已包装的 apk，请像通常那样修改 `build.json` 以添加签名信息。 例如：
```json
{
  "android": {
    "release": {
      "keystore": "your.keystore",
      "storePassword": "yourpassword",
      "alias": "youralias",
      "password" : "yourpassword",
      "keystoreType": ""
    }
  }
}
```

### <a name="build-for-android-test-only"></a>生成仅适用于 Android 测试

1. 将 `android:testOnly="true"` 添加到 `AndroidManifest.xml` 文件的应用程序节点。


2. **Cordova 6.x.x：**在 `[PROJECT_ROOT]/platforms/android/cordova/lib/Adb.js` 中，更改行 60

    ```javascript
    var args = ['-s', target, 'install'];
    ```
    设置为
    ```javascript
    var args = ['-s', target, 'install', '-t'];
    ```

这样做的效果是使用“-t”标志运行 `adb install`，因为无法在没有它的情况下安装 `testOnly` 应用。

### <a name="debugging-from-visual-studio"></a>通过 Visual Studio 进行调试
第一次启动应用后，会看到一个对话框，告知你该应用是通过 Intune 管理的。 点击“不再显示”，然后再次从 VS 中单击“调试/运行”按钮以点击断点。

## <a name="known-limitations"></a>已知限制
### <a name="android"></a>Android
* MultiDex 支持不完整。
* 应用必须面向 Android 4.0 (Android API 14) 或更高版本。

### <a name="ios"></a>iOS
* 每当修改 **Info.plist** 文件的 **CFBundleDocumentTypes** 节点下的 UTI 列表时，必须在相同 plist 文件的所导入 UTI 部分中清除 Intune UTI（**UTImportedTypeDeclarations** 节点），然后才能再次生成。 所有 Intune UTI 将以前缀 `com.microsoft.intune.mam` 开头。

* 如果要从 Cordova 项目中删除 Intune 插件，还必须删除 iOS 平台并重新添加它，以撤消 .xcodeproj 和 .plist 文件中的某些 Intune 配置。



<!--HONumber=Nov16_HO4-->


