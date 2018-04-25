---
title: Microsoft Intune App SDK Xamarin Bindings
description: 借助 Intune App SDK Xamarin Bindings，可在使用 Xamarin 生成的 iOS 和 Android 应用中启用 Intune 应用保护策略。
keywords: sdk、Xamarin、intune
author: Erikre
manager: dougeby
ms.author: erikre
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9f9cc117925f59c9fb7c55d0ff10aedf09d26f93
ms.sourcegitcommit: b727b6bd6f138c5def7ac7bf1658068db30a0ec3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/06/2018
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Microsoft Intune App SDK Xamarin Bindings

> [!NOTE]
> 你可能希望首先阅读 [ Intune App SDK 入门指南](app-sdk-get-started.md)一文，其中介绍了如何为每个受支持的平台上的集成做准备。

## <a name="overview"></a>概述
借助 [Intune App SDK Xamarin Bindings](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)，可在使用 Xamarin 生成的 iOS 和 Android 应用中启用 [Intune 应用保护策略](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)。 该绑定使开发人员可以轻松将 Intune 应用保护功能内置到基于 Xamarin 的应用中。

通过 Microsoft Intune App SDK Xamarin Bindings，可将 Intune 应用保护策略（也称为 APP 或 MAM 策略）合并到使用 Xamarin 开发的应用中。 启用了 MAM 的应用程序是指与 Intune App SDK 集成的应用程序。 在 Intune 主动管理移动应用时，IT 管理员可将应用保护策略部署到该应用。

## <a name="whats-supported"></a>支持的功能

### <a name="developer-machines"></a>开发人员计算机
* Windows
* macOS


### <a name="mobile-app-platforms"></a>移动应用平台
* Android
* iOS


### <a name="intune-mobile-application-management-scenarios"></a>Intune 移动应用程序管理方案

* Intune APP-WE（无需设备注册）
* 注册了 Intune MDM 的设备
* 注册了第三方 EMM 的设备

使用 Intune App SDK Xamarin Bindings 生成的 Xamarin 应用现在可以在已注册和未注册 Intune 移动设备管理 (MDM) 的设备上接收 Intune 应用保护策略。

## <a name="prerequisites"></a>必备条件

查看[许可条款](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20Xamarin%20Component.pdf)。 打印并保留一份许可条款，以留作记录。 下载和使用 Intune App SDK Xamarin Bindings 即表示你同意这些许可条款。 如果不接受这些条款，请不要使用此软件。

## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>在 iOS 移动应用中启用 Intune 应用保护策略
1. 向 Xamarin.iOS 项目添加 [Microsoft.Intune.MAM.Xamarin.iOS NuGet 包](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS)。
2.  按照将 Intune App SDK 集成到 iOS 移动应用的常规必需步骤操作。 可以从 [Intune App SDK for iOS 开发人员指南](app-sdk-ios.md#build-the-sdk-into-your-mobile-app)中集成说明的第 3 步开始操作。 可跳过运行 IntuneMAMConfigurator 一节中的最后一步，因为此工具包含在 Microsoft.Intune.MAM.Xamarin.iOS 包中，并将在生成时自动运行。
    **重要说明**：在 Visual Studio 中为应用启用密钥链共享与在 Xcode 中略有不同。 打开应用的“权利”plist 文件，并确保已启用“启用密钥链”选项，且已在相应部分中添加了相应的密钥链共享组。 然后，对于所有相应的配置/平台组合，请确保已在项目的“iOS 捆绑包签名”选项的“自定义权利”字段中指定了“权利”plist 文件。
3.  添加绑定且正确配置应用后，应用即可开始使用 Intune SDK 的 API。 为此，必须添加以下命名空间：

      ```csharp
      using Microsoft.Intune.MAM;
      ```
4. 若要开始接收应用保护策略，必须在 Intune MAM 服务中注册应用。 如果应用已使用 Azure Active Directory Authentication Library (ADAL) 验证用户，应用应在成功验证用户后，向 IntuneMAMEnrollmentManager 的 registerAndEnrollAccount 方法提供用户的 UPN：
      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```
      **重要说明**：请务必使用应用中的设置替代 Intune App SDK 的默认 ADAL 设置。 可以通过应用 Info.plist 中的 IntuneMAMSettings 字典执行此操作，如 [Intune App SDK for iOS 开发人员指南](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk)中所述。也可以使用 IntuneMAMPolicyManager 实例的 AAD 替代属性。 对于 ADAL 设置是静态的应用，建议使用 Info.plist 方法；对于在运行时确定这些值的应用，建议使用替代属性。 
      
      如果应用不使用 ADAL，且希望使用 Intune SDK 处理身份验证，应用应调用 IntuneMAMEnrollmentManager 的 loginAndEnrollAccount 方法：
      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```

## <a name="enabling-app-protection-policies-in-your-android-mobile-app"></a>在 Android 移动应用中启用应用保护策略
向 Xamarin.Android 项目添加 [Microsoft.Intune.MAM.Xamarin.Android NuGet 包](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android)。

若是 Xamarin.Android 应用，需仔细阅读[用于 Android 的 Intune App SDK 开发人员指南](app-sdk-android.md)并按文章内容进行操作，包括根据该指南中的[表](app-sdk-android.md#replace-classes-methods-and-activities-with-their-mam-equivalent)将类、方法和活动替换为其 MAM 等效项。 

> [!NOTE]
> 如果应用没有定义 `android.app.Application` 类，则需要创建一个，并确保继承自 `MAMApplication`。

> [!NOTE]
> 尝试在[用于 Android 的 Intune App SDK 开发人员指南](app-sdk-android.md)中查找 `Microsoft.Intune.MAM.Xamarin.Android` Bindings 的等效 API 或根据该指南转换代码片段时，请注意 Xamarin 的绑定生成器会对 Android API 进行以下重要修改：
> * 会将所有标识符转换为 Pascale 事例 (com.microsoft.foo -> Com.Microsoft.Foo)
> * 会将所有的 get/set 操作转换为属性操作（例如 Foo.getBar() -> Foo.Bar，Foo.setBar("zap") -> Foo.Bar = "zap"）
> * 所有接口的名称都加上了字符“I”(FooInterface -> IFooInterface)

对于使用 Xamarin.Forms 或其他 UI 框架的应用，我们提供了名为 `Microsoft.Intune.MAM.Remapper` 的工具。 该工具将为你完成类替换。 若要使用该工具，请执行下列操作：

1.  向项目添加 [Microsoft.Intune.MAM.Remapper.Tasks](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) NuGet 包。

2.  将 Nuget 包随附的 `remapping-config.json` 文件的生成操作设置为 RemappingConfigFile。 所包含的 `remapping-config.json` 仅适用于 Xamarin.Forms。 对于其他 UI 框架，请参阅 Remapper NuGet 包中所包含的自述文件。

3.  在 MAMApplication 的 OnMAMCreate 函数中添加对 Xamarin.Forms.Forms.Init(Context, Bundle) 的调用，这样借助 Intune 管理，该应用程序即可在后台启动。

4.  执行[用于 Android 的 Intune App SDK 开发人员指南](app-sdk-android.md)中适用于应用的其他步骤。

> [!NOTE]
> 更新 Microsoft.Intune.MAM.Remapper.Tasks 包时，remapping-config.json 的生成操作有时可能会重置，从而导致生成操作失败。

## <a name="next-steps"></a>后续步骤

你已完成将应用设置为使用 Intune 管理的基本步骤。 现在可以按照上述针对每个平台的集成指南中的步骤进行操作。

如果你的组织已经是 Intune 的客户，请与 Microsoft 支持代表合作打开支持票证并在 [Github 问题页](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues)上创建一个问题，我们会尽快为你提供帮助。 