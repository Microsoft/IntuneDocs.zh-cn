---
title: "Microsoft Intune App SDK Xamarin 组件"
description: 
keywords: "sdk、Xamarin、intune"
author: mtillman
manager: angrobe
ms.author: mtillman
ms.date: 11/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b900cb2c2c02ca96a771dbebd208872941079e38
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="microsoft-intune-app-sdk-xamarin-component"></a>Microsoft Intune App SDK Xamarin 组件

> [!NOTE]
> 你可能希望首先阅读 [ Intune App SDK 入门指南](app-sdk-get-started.md)一文，其中介绍了如何为每个受支持的平台上的集成做准备。



## <a name="overview"></a>概述
[Intune App SDK Xamarin 组件](https://components.xamarin.com/view/microsoft.intune.mam)允许在使用 Xamarin 生成的 iOS 和 Android 应用中启用 [Intune 应用保护策略](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)。 该组件使开发人员可以轻松将 Intune 应用保护功能内置到基于 Xamarin 的应用中。

你会发现你可以在不改变应用行为的情况下启用 SDK 功能。 将该组件内置到 iOS 或 Android 移动应用后，IT 管理员将能够通过 Microsoft Intune 移动应用程序管理 (MAM) 部署策略，以便支持各种数据保护功能。

## <a name="whats-supported"></a>支持的功能

### <a name="developer-machines"></a>开发人员计算机
* Windows


### <a name="mobile-app-platforms"></a>移动应用平台
* Android
* iOS


### <a name="intune-mobile-application-management-scenarios"></a>Intune 移动应用程序管理方案

* 注册了 Intune MDM 的设备
* 注册了第三方 EMM 的设备
* 非托管设备（未向任何 MDM 注册）

使用 Intune App SDK Xamarin 组件生成的 Xamarin 应用现在可以在注册了 Intune 移动设备管理 (MDM) 的设备和未注册的设备上接收 Intune 移动应用程序管理 (MAM) 策略。

## <a name="prerequisites"></a>先决条件

* **[仅限 Android]** 必须始终在设备上安装最新的 Microsoft Intune 公司门户应用。

## <a name="get-started"></a>入门

1.  从[此处](https://components.xamarin.com/submit/xpkg)下载 **Xamarin component.exe** 并将其解压缩。

2. 阅读 Microsoft Intune MAM Xamarin 组件的[许可条款](https://components.xamarin.com/license/microsoft.intune.mam)。

3.  从 [GitHub](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) 或 [Xamarin](https://components.xamarin.com/license/microsoft.intune.mam) 下载 Intune App SDK Xamarin 组件文件夹并从中提取。 在 步骤 1 和 3 中下载的这两个文件应处于相同的目录级别。

4.  在命令行中以管理员身份运行 `Xamarin.Component.exe install <.xam> file`。

5.  在 Visual Studio 中，右键单击以前创建的 Xamarin 项目中的**组件**。

6.  选择“编辑组件”并添加以本地方式下载到计算机上的 Intune App SDK 组件。



## <a name="enabling-intune-mam-in-your-ios-mobile-app"></a>在 iOS 移动应用中启用 Intune MAM
1.  为了初始化 Intune App SDK，需要调用 `AppDelegate.cs` 类中的任意一个 API。 例如：

      ```csharp
      public override bool FinishedLaunching (UIApplication application, NSDictionary launchOptions)
      {
            Console.WriteLine ("Is Managed: {0}", IntuneMAMPolicyManager.Instance.PrimaryUser != null);
            return true;
      }

      ```

2.  现在该组件已添加并初始化，便可以按照所需的常规步骤将 App SDK 内置到 iOS 移动应用中。 可在 [Intune App SDK for iOS 开发人员指南](app-sdk-ios.md)中找到用于启用本机 iOS 应用的完整文档。
3. **重要提示**：特定于基于 Xamarin 的 iOS 应用有几项修改。 例如，当启用密钥链组时，需要添加以下内容以包含组件中包括的 Xamarin 示例应用。 以下是“密钥链访问”组中需要的组的示例：

      ```xml
      <?xml version="1.0" encoding="UTF-8"?>
      <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
      <plist version="1.0">
            <dict>
                  <key>keychain-access-groups</key>
                  <array>
                        <string>$(AppIdentifierPrefix)com.xamarin.microsoftintunesample</string>
                        <string>$(AppIdentifierPrefix)com.xamarin.microsoftintunesample.intunemam</string>
                        <string>$(AppIdentifierPrefix)com.microsoft.intune.mam</string>
                        <string>$(AppIdentifierPrefix)com.microsoft.adalcache</string>
                  </array>
            </dict>
      </plist>
      ```

你已完成将组件内置到基于 Xamarin 的 iOS 应用所需的步骤。 如果使用 Xcode 生成项目，那么可以使用 `Intune App SDK Settings.bundle`。 这使你能够在生成项目以进行测试和调试时随时打开或关闭 Intune 策略设置。 若要利用此捆绑包，请按照 [Intune App SDK for iOS 开发人员指南](app-sdk-ios.md)中的步骤操作，并阅读[在 Xcode 中调试](app-sdk-ios.md#status-result-and-debug-notifications)部分。

## <a name="enabling-mam-in-your-android-mobile-app"></a>在 Android 移动应用中启用 MAM
对不使用 UI 框架的基于 Xamarin 的 Android 应用，你需要阅读并遵循 [Intune App SDK for Android 开发人员指南]。 对基于 Xamarin 的 Android 应用，需要根据本指南所包含的[表](app-sdk-android.md#replace-classes-methods-and-activities-with-their-mam-equivalent)将类、方法和活动替换为 MAM 等效项。 如果应用没有定义 `android.app.Application` 类，则需要创建一个，并确保继承自 `MAMApplication`。

对于 Xamarin 窗体和其他 UI 框架，我们提供了名为 `MAM.Remapper` 的工具。 该工具将为你完成类替换。 但是，你需要执行以下步骤：

1.  将引用添加到 ` Microsoft.Intune.MAM.Remapper.Tasks` nuget 包版本 0.1.0.0 或更高版本。

2.  将以下行添加到 Android csproj：
  ```xml
  <Import
  Project="$(NugetPack)\\Microsoft.Intune.MAM.Remapper.Tasks.0.1.X.X\\build\\MonoAndroid10\\Microsoft.Intune.MAM.Remapper.targets" />
  ```

3.  将所添加 `remapping-config.json` 文件的生成操作设置为 **RemappingConfigFile**。 所包含的 `remapping-config.json` 仅适用于 Xamarin.Forms。 对于其他 UI 框架，请参阅 Remapper nuget 包中所包含的自述文件。

## <a name="test-your-app"></a>测试应用程序

你已完成将组件内置到应用中的基本步骤。 现在可以按照 Xamarin Android 示例应用中的所述步骤进行操作。 我们提供了两个示例，一个用于 Xamarin.Forms，另一个用于 Android。
