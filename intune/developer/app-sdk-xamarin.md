---
title: Microsoft Intune App SDK Xamarin Bindings
description: 借助 Intune App SDK Xamarin Bindings，可在使用 Xamarin 生成的 iOS 和 Android 应用中启用 Intune 应用保护策略。
keywords: sdk、Xamarin、intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/28/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 183cc5ed233de4a3285cf5cfd3290aead9c1de72
ms.sourcegitcommit: 9ee2401a2f01373a962749b0728c22385dbcba6d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181902"
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Microsoft Intune App SDK Xamarin Bindings

> [!NOTE]
> 你可能希望首先阅读 [ Intune App SDK 入门指南](app-sdk-get-started.md)一文，其中介绍了如何为每个受支持的平台上的集成做准备。

## <a name="overview"></a>概述
借助 [Intune App SDK Xamarin Bindings](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)，可在使用 Xamarin 生成的 iOS 和 Android 应用中启用 [Intune 应用保护策略](../apps/app-protection-policy.md)。 该绑定使开发人员可以轻松将 Intune 应用保护功能内置到基于 Xamarin 的应用中。

通过 Microsoft Intune App SDK Xamarin Bindings，可将 Intune 应用保护策略（也称为 APP 或 MAM 策略）合并到使用 Xamarin 开发的应用中。 启用了 MAM 的应用程序是指与 Intune App SDK 集成的应用程序。 在 Intune 主动管理移动应用时，IT 管理员可将应用保护策略部署到该应用。

## <a name="whats-supported"></a>支持的功能

### <a name="developer-machines"></a>开发人员计算机
* Windows（Visual Studio 版本 15.7+）
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

Intune SDK 依赖于 [Active Directory 身份验证库 (ADAL)](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) 实现它的[身份验证](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/)和条件启动方案，这需要使用 [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/) 配置应用。 

如果应用程序已配置为使用 ADAL 或 MSAL，并且拥有其自己的自定义客户端 ID 用于使用 Azure Active Directory 进行身份验证，请务必按以下步骤操作，将 Xamarin 应用权限授予 Intune 移动应用程序管理 (MAM) 服务。 请使用 [Intune SDK 入门指南](app-sdk-get-started.md)的[向 Intune 应用保护服务提供应用访问权限](app-sdk-get-started.md#give-your-app-access-to-the-intune-app-protection-service-optional)一节中的说明。

## <a name="security-considerations"></a>安全注意事项

防止潜在的欺骗、信息泄露和特权提升攻击：

* 确保在安全的工作站上进行 Xamarin 应用开发。
* 确保绑定来自有效的 Microsoft 源：
  * [MS Intune App SDK NuGet 配置文件](https://www.nuget.org/profiles/msintuneappsdk)
  * [Intune App SDK Xamarin GitHub 存储库](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)
* 为项目配置 NuGet 配置以信任已签名且未修改的 NuGet 包。
有关详细信息，请参阅[安装已签名的包](https://docs.microsoft.com/nuget/consume-packages/installing-signed-packages)。
* 保护包含 Xamarin 应用的输出目录。 考虑为输出使用用户级目录。


## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>在 iOS 移动应用中启用 Intune 应用保护策略
1. 向 Xamarin.iOS 项目添加 [Microsoft.Intune.MAM.Xamarin.iOS NuGet 包](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS)。
2. 按照将 Intune App SDK 集成到 iOS 移动应用的常规必需步骤操作。 可以从 [Intune App SDK for iOS 开发人员指南](app-sdk-ios.md#build-the-sdk-into-your-mobile-app)中集成说明的第 3 步开始操作。 可跳过运行 IntuneMAMConfigurator 一节中的最后一步，因为此工具包含在 Microsoft.Intune.MAM.Xamarin.iOS 包中，并将在生成时自动运行。
    **重要提示**：在 Visual Studio 中为应用启用密钥链共享与在 Xcode 中略有不同。 打开应用的“权利”plist 文件，并确保已启用“启用密钥链”选项，且已在相应部分中添加了相应的密钥链共享组。 然后，对于所有相应的配置/平台组合，请确保已在项目的“iOS 捆绑包签名”选项的“自定义权利”字段中指定了“权利”plist 文件。
3. 添加绑定且正确配置应用后，应用即可开始使用 Intune SDK 的 API。 为此，必须添加以下命名空间：

      ```csharp
      using Microsoft.Intune.MAM;
      ```

4. 若要开始接收应用保护策略，必须在 Intune MAM 服务中注册应用。 如果应用不使用 [Azure Active Directory 身份验证库](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) (ADAL) 或 [Microsoft 身份验证库](https://www.nuget.org/packages/Microsoft.Identity.Client) (MSAL) 对用户进行身份验证，且希望由 Intune SDK 处理身份验证，应用应将用户的 UPN 提供给 IntuneMAMEnrollmentManager 的 LoginAndEnrollAccount 方法：

      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```

      如果用户的 UPN 在调用时未知，则应用可能会传入 null。 在这种情况下，系统将提示用户输入他们的电子邮件地址和密码。
      
      如果应用已使用 ADAL 或 MSAL 对用户进行身份验证，则可以在应用和 Intune SDK 之间配置单一登录 (SSO) 体验。 首先，需要将 Intune SDK 使用的默认 AAD 设置替代为应用的这些设置。 可通过应用 Info.plist 中的 IntuneMAMSettings 字典执行此操作，如 [Intune App SDK for iOS 开发人员指南](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk)中所述。也可通过 IntuneMAMSettings 类的 AAD 替代属性在代码中执行此操作。 对于 ADAL 设置是静态的应用，建议使用 Info.plist 方法；对于在运行时确定这些值的应用，建议使用替代属性。 配置所有 SSO 设置后，应用应在成功通过身份验证后向 IntuneMAMEnrollmentManager 的 RegisterAndEnrollAccount 方法提供用户的 UPN：

      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```

      应用可以通过在 IntuneMAMEnrollmentDelegate 的子类中实现 EnrollmentRequestWithStatus 方法并将 IntuneMAMEnrollmentManager 的 Delegate 属性设置为该类的实例来确定尝试注册的结果。 

      成功注册后，应用可以通过查询以下属性来确定已注册帐户的 UPN（如果以前未知）： 

      ```csharp
       string enrolledAccount = IntuneMAMEnrollmentManager.Instance.EnrolledAccount;
      ```      
### <a name="sample-applications"></a>示例应用程序
[GitHub](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) 上提供了强调 Xamarin.iOS 应用中 MAM 功能的示例应用程序。

> [!NOTE] 
> 没有适用于 iOS/iPadOS 的重映射器。 集成到 Xamarin.Forms 应用应与集成到常规 Xamarin.iOS 项目的操作相同。 

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>在 Android 移动应用中启用 Intune 应用保护策略
1. 向 Xamarin.Android 项目添加 [Microsoft.Intune.MAM.Xamarin.Android NuGet 包](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android)。
    1. 对于 Xamarin.Forms 应用，还要将 [Microsoft.Intune.MAM.Remapper.Tasks NuGet 包](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks)添加到 Xamarin.Android 项目中。 
2. 按照[将 Intune App SDK 集成](app-sdk-android.md)到 Android 移动应用中所需的一般步骤进行操作，同时参阅此文档以获取更多详细信息。

### <a name="xamarinandroid-integration"></a>Xamarin.Android 集成

有关集成 Intune App SDK 的完整概述，请参阅[面向 Android 开发人员的 Microsoft Intune App SDK for Android 指南](app-sdk-android.md)。 阅读本指南并将 Intune App SDK 与 Xamarin 应用集成时，下面几部分着重介绍用 Java 开发的本机 Android 应用和用 C# 开发的 Xamarin 应用的实现之间的差异。 这些部分应视为补充部分，不能因此不阅读完整指南。

#### <a name="remapper"></a>重映射器
从 1.4428.1 版本开始，可将 `Microsoft.Intune.MAM.Remapper` 包作为[生成工具](app-sdk-android.md#build-tooling)添加到 Xamarin Android 应用程序，以执行 MAM 类、方法和系统服务替换。 如果包括重映射器，则在生成应用程序时，将自动执行重命名方法和 MAM 应用程序部分的 MAM 等效替换部分。

若要通过重映射器从 MAM 通知中排除类，可以在项目 `.csproj` 文件中添加以下属性。

```xml
  <PropertyGroup>
    <ExcludeClasses>Semicolon separated list of relative class paths to exclude from MAM-ification</ExcludeClasses>
  </PropertyGroup>
```

> [!NOTE]
> 重映射器当前禁止在 Xamarin Android 应用中进行调试。 建议使用手动集成来调试应用程序。

#### <a name="renamed-methods"></a>[重命名的方法](app-sdk-android.md#renamed-methods)
在许多情况下，Android 类中提供的方法已在 MAM 替换类中标记为最终方法。 在此情况下，MAM 替换类会提供应替代的具有类似名称的方法（使用“`MAM`”作为后缀）。 例如，从 `MAMActivity` 派生（而不是替代 `OnCreate()` 并调用 `base.OnCreate()`）时，`Activity` 必须替代 `OnMAMCreate()` 并调用 `base.OnMAMCreate()`。

#### <a name="mam-application"></a>[MAM 应用程序](app-sdk-android.md#mamapplication)
应用必须定义 `Android.App.Application` 类。 如果手动集成 MAM，则它必须继承自 `MAMApplication`。 确保你的子类用 `[Application]` 属性正确修饰并替代 `(IntPtr, JniHandleOwnership)` 构造函数。

```csharp
    [Application]
    class TaskrApp : MAMApplication
    {
    public TaskrApp(IntPtr handle, JniHandleOwnership transfer)
        : base(handle, transfer) { }
```

> [!NOTE]
> 在“调试”模式下部署时，MAM Xamarin 绑定的问题可能导致应用程序故障。 变通方法是必须将 `Debuggable=false` 属性添加到 `Application` 类，并且如果手动设置，则必须从清单中删除 `android:debuggable="true"` 标记。

#### <a name="enable-features-that-require-app-participation"></a>[启用需要应用参与的功能](app-sdk-android.md#enable-features-that-require-app-participation)
例如：确定应用是否需要 PIN

```csharp
MAMPolicyManager.GetPolicy(currentActivity).IsPinRequired;
```

例如：确定主要 Intune 用户

```csharp
IMAMUserInfo info = MAMComponents.Get<IMAMUserInfo>();
return info?.PrimaryUser;
```

例如：确定是否允许保存到设备或云存储

```csharp
MAMPolicyManager.GetPolicy(currentActivity).GetIsSaveToLocationAllowed(SaveLocation service, String username);
```

#### <a name="register-for-notifications-from-the-sdk"></a>[注册来自 SDK 的通知](app-sdk-android.md#register-for-notifications-from-the-sdk)
应用必须通过创建 `MAMNotificationReceiver` 并向 `MAMNotificationReceiverRegistry` 注册，来注册来自 SDK 的通知。 此操作可通过在 `App.OnMAMCreate` 中提供接收方以及所需通知类型来实现，如以下示例所示：

```csharp
public override void OnMAMCreate()
{
    // Register the notification receivers
    IMAMNotificationReceiverRegistry registry = MAMComponents.Get<IMAMNotificationReceiverRegistry>();
    foreach (MAMNotificationType notification in MAMNotificationType.Values())
    {
        registry.RegisterReceiver(new ToastNotificationReceiver(this), notification);
    }
    ...
```

#### <a name="mam-enrollment-manager"></a>[MAM 注册管理器](app-sdk-android.md#mamenrollmentmanager)

```csharp
IMAMEnrollmentManager mgr = MAMComponents.Get<IMAMEnrollmentManager>();
```

### <a name="xamarinforms-integration"></a>Xamarin.Forms 集成

对于 `Xamarin.Forms` 应用程序，`Microsoft.Intune.MAM.Remapper` 包将 `MAM` 类注入常用 `Xamarin.Forms` 类的类层次结构中，从而自动执行 MAM 类替换。 

> [!NOTE]
> 除上面详述的 Xamarin.Android 集成外，还必须完成 Xamarin.Forms 集成。 重映射器的行为与 Xamarin.Forms 应用的行为有所不同，因此仍必须执行手动 MAM 替换。

将重映射器添加到项目后，需要执行 MAM 等效替换。 如果将对 `OnCreate` 和 `OnResume` 的替代分别替换为 MAM 等效的 `OnMAMCreate` 和 `OnMAMResume`，则 `FormsAppCompatActivity` 和 `FormsApplicationActivity` 可以继续在应用程序中使用。

```csharp
    public class MainActivity : global::Xamarin.Forms.Platform.Android.FormsAppCompatActivity
    {
        protected override void OnMAMCreate(Bundle savedInstanceState)
        {
            base.OnMAMCreate(savedInstanceState);
            global::Xamarin.Forms.Forms.Init(this, savedInstanceState);
            LoadApplication(new App());
        }
```

如果未进行替换，则在进行替换之前可能会遇到以下编译错误：
* [编译器错误 CS0239](https://docs.microsoft.com/dotnet/csharp/misc/cs0239)。 此错误常见于此窗体 ``'MainActivity.OnCreate(Bundle)': cannot override inherited member 'MAMAppCompatActivityBase.OnCreate(Bundle)' because it is sealed``。
这是预期结果，因为当重映射器修改 Xamarin 类的继承时，将 `sealed` 某些函数，并添加新的 MAM 变量来替代。
* [编译器错误 CS0507](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0507)：此错误常见于此窗体 ``'MyActivity.OnRequestPermissionsResult()' cannot change access modifiers when overriding 'public' inherited member ...``。 当重映射器更改一些 Xamarin 类的继承时，某些成员函数将更改为 `public`。 如果替代任何这些函数，则还需要将这些替代的访问修饰符更改为 `public`。

> [!NOTE]
> 重映射器重写了 Visual Studio 用于 IntelliSense 自动完成的依赖项。 因此，在为 IntelliSense 添加重映射器时，可能需要重载并重新生成项目，以正确识别更改。

#### <a name="troubleshooting"></a>疑难解答
* 如果启动时在应用程序中遇到白屏，则可能需要强制在主线程上执行导航调用。
* 由于 MvvmCross 和 Intune MAM 类之间的冲突，Intune SDK Xamarin 绑定不支持使用跨平台框架（例如 MvvmCross）的应用。 尽管有些客户在将其应用改为无格式 Xamarin.Forms 后可能成功集成，但我们不为使用 MvvmCross 的应用开发人员提供明确的指导或插件。

### <a name="company-portal-app"></a>公司门户应用
Intune SDK Xamarin 绑定依赖于设备上存在[公司门户](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) Android 应用以启用应用保护策略。 公司门户从 Intune 服务中检索应用保护策略。 应用初始化时，它会加载策略和代码以强制从公司门户实施该策略。 用户无需登录。

> [!NOTE]
> 如果 Android  设备上未安装公司门户应用，Intune 托管应用的行为与不支持 Intune 应用保护策略的普通应用相同。

对于无需设备注册的应用保护， _**不会**_ 要求用户使用公司门户应用注册设备。

### <a name="sample-applications"></a>示例应用程序
[GitHub](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps) 上提供了强调 Xamarin.Android 和 Xamarin.Forms 应用中 MAM 功能的示例应用程序。

## <a name="support"></a>支持
如果你的组织已经是 Intune 客户，请与 Microsoft 支持代表合作，以开立支持票证，并在 [GitHub 问题页](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues)上创建问题。 我们将尽快提供帮助。 
