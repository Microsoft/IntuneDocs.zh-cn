---
title: "Microsoft Intune App SDK Xamarin 组件"
description: 
keywords: "sdk、Xamarin、intune"
author: erikre
manager: angrobe
ms.author: erikre
ms.date: 11/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ae53ced489542ba7e675e547740f1858d761c7ab
ms.sourcegitcommit: 833b1921ced35be140f0107d0b4205ecacd2753b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2018
---
# <a name="microsoft-intune-app-sdk-xamarin-component"></a>Microsoft Intune App SDK Xamarin 组件

> [!NOTE]
> 你可能希望首先阅读 [ Intune App SDK 入门指南](app-sdk-get-started.md)一文，其中介绍了如何为每个受支持的平台上的集成做准备。



## <a name="overview"></a>概述
[Intune App SDK Xamarin 组件](https://components.xamarin.com/view/microsoft.intune.mam)允许在使用 Xamarin 生成的 iOS 和 Android 应用中启用 [Intune 应用保护策略](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)。 该组件使开发人员可以轻松将 Intune 应用保护功能内置到基于 Xamarin 的应用中。

> [!NOTE]
> 对用于 Xamarin 的 Intune SDK 的支持当前仅作为预览功能提供。 

通过 Microsoft Intune App SDK Xamarin 组件，可将 Intune 应用保护策略（也称为 APP 或 MAM 策略）合并到使用 Xamarin 开发的应用中。 启用了 MAM 的应用程序是指与 Intune App SDK 集成的应用程序。 在 Intune 主动管理移动应用时，IT 管理员可将应用保护策略部署到该应用。

## <a name="whats-supported"></a>支持的功能

### <a name="developer-machines"></a>开发人员计算机
* macOS


### <a name="mobile-app-platforms"></a>移动应用平台
* Android
* iOS


### <a name="intune-mobile-application-management-scenarios"></a>Intune 移动应用程序管理方案

* 注册了 Intune MDM 的设备
* 注册了第三方 EMM 的设备
* 非托管设备（未向任何 MDM 注册）

使用 Intune App SDK Xamarin 组件生成的 Xamarin 应用现在可以在已注册和未注册 Intune 移动设备管理 (MDM) 的设备上接收 Intune 应用保护策略。

## <a name="prerequisites"></a>必备条件

* **[仅限 Android]** 必须在设备上安装最新的 Microsoft Intune 公司门户应用。

## <a name="get-started"></a>入门

1.  从[此处](https://components.xamarin.com/submit/xpkg)下载 **Xamarin component.exe** 并将其解压缩。

2. 阅读 Microsoft Intune MAM Xamarin 组件的[许可条款](https://components.xamarin.com/license/microsoft.intune.mam)。

3.  从 [GitHub](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) 或 [Xamarin](https://components.xamarin.com/license/microsoft.intune.mam) 下载 Intune App SDK Xamarin 组件文件夹并从中提取。 在 步骤 1 和 3 中下载的这两个文件应处于相同的目录级别。

4.  在命令行中以管理员身份运行 `Xamarin.Component.exe install <.xam> file`。

5.  在 Visual Studio 中，右键单击以前创建的 Xamarin 项目中的“组件”。

6.  选择“编辑组件”并添加以本地方式下载到计算机上的 Intune App SDK 组件。



## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>在 iOS 移动应用中启用 Intune 应用保护策略
1.  按照将 Intune App SDK 集成到 iOS 移动应用的常规必需步骤操作。 可以从 [Intune App SDK for iOS 开发人员指南](app-sdk-ios.md#build-the-sdk-into-your-mobile-app)中集成说明的第 3 步开始操作。
    **重要说明**：在 Visual Studio 中为应用启用密钥链共享与在 Xcode 中略有不同。 打开应用的“权利”plist 文件，并确保已启用“启用密钥链”选项，且已在相应部分中添加了相应的密钥链共享组。 然后，对于所有相应的配置/平台组合，请确保已在项目的“iOS 捆绑包签名”选项的“自定义权利”字段中指定了“权利”plist 文件。
2.  添加组件且正确配置应用后，应用即可开始使用 Intune SDK 的 API。 为此，必须添加以下命名空间：
      ```csharp
      using Microsoft.Intune.MAM;
      ```
3.    若要开始接收应用保护策略，必须在 Intune MAM 服务中注册应用。 如果应用已使用 Azure Active Directory Authentication Library (ADAL) 验证用户，应用应在成功验证用户后，向 IntuneMAMEnrollmentManager 的 registerAndEnrollAccount 方法提供用户的 UPN：
      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```
      **重要说明**：请务必使用应用中的设置替代 Intune App SDK 的默认 ADAL 设置。 可以通过应用 Info.plist 中的 IntuneMAMSettings 字典执行此操作，如 [Intune App SDK for iOS 开发人员指南](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk)中所述。也可以使用 IntuneMAMPolicyManager 实例的 AAD 替代属性。 对于 ADAL 设置是静态的应用，建议使用 Info.plist 方法；对于在运行时确定这些值的应用，建议使用替代属性。 
      
      如果应用不使用 ADAL，且希望使用 Intune SDK 处理身份验证，应用应调用 IntuneMAMEnrollmentManager 的 loginAndEnrollAccount 方法：
      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```

## <a name="enabling-app-protection-policies-in-your-android-mobile-app"></a>在 Android 移动应用中启用应用保护策略
对于不使用 UI 框架的基于 Xamarin 的 Android 应用，需要阅读并遵循 [Intune App SDK for Android 开发人员指南](app-sdk-android.md)。 对于基于 Xamarin 的 Android 应用，需要根据本指南所包含的[表](app-sdk-android.md#replace-classes-methods-and-activities-with-their-mam-equivalent)将类、方法和活动替换为其 MAM 等效项。 如果应用没有定义 `android.app.Application` 类，则需要创建一个，并确保继承自 `MAMApplication`。

对于 Xamarin 窗体和其他 UI 框架，我们提供了名为 `MAM.Remapper` 的工具。 该工具将为你完成类替换。 但是，你需要执行以下步骤：

1.  将引用添加到 `Microsoft.Intune.MAM.Remapper.Tasks` NuGet 包版本 0.1.0.0 或更高版本。

2.  将以下行添加到 Android csproj：
  ```xml
  <Import
  Project="$(NugetPack)\\Microsoft.Intune.MAM.Remapper.Tasks.0.1.X.X\\build\\MonoAndroid10\\Microsoft.Intune.MAM.Remapper.targets" />
  ```

3.  将所添加 `remapping-config.json` 文件的生成操作设置为 **RemappingConfigFile**。 所包含的 `remapping-config.json` 仅适用于 Xamarin.Forms。 对于其他 UI 框架，请参阅 Remapper NuGet 包中所包含的自述文件。

## <a name="next-steps"></a>后续步骤

你已完成将组件内置到应用中的基本步骤。 现在可以按照 Xamarin Android 示例应用中的所述步骤进行操作。 我们提供了两个示例，一个用于 Xamarin.Forms，另一个用于 Android。
