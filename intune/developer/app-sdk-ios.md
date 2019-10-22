---
title: 用于 iOS 的 Microsoft Intune App SDK 开发人员指南
description: 通过 Microsoft Intune App SDK for iOS，可将 Intune 应用保护策略（也称为 APP 或 MAM 策略）合并到本机 iOS 应用中。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/17/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 93b48fd5f6482669da923e4c15dcb09c7d328197
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503454"
---
# <a name="microsoft-intune-app-sdk-for-ios-developer-guide"></a>用于 iOS 的 Microsoft Intune App SDK 开发人员指南

> [!NOTE]
> 建议阅读 [Intune App SDK 入门指南](app-sdk-get-started.md)一文，该文章介绍了如何在每个受支持的平台准备集成。

通过 Microsoft Intune App SDK for iOS，可将 Intune 应用保护策略（也称为 APP 或 MAM 策略）合并到本机 iOS 应用中。 启用了 MAM 的应用程序是指与 Intune App SDK 集成的应用程序。 在 Intune 主动管理移动应用时，IT 管理员可将应用保护策略部署到该应用。

## <a name="prerequisites"></a>必备条件

* 需要运行 OS X 10.8.5 或更高版本的 Mac OS 计算机，还需安装 Xcode 9 或更高版本。

* 应用必须适用于 iOS 11 或更高版本。

* 查看 [Intune App SDK for iOS 许可条款](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20for%20iOS.pdf)。 打印并保留一份许可条款副本，留作记录。 下载和使用用于 iOS 的 Intune App SDK 即表示你同意这些许可条款。  如果不接受这些条款，请不要使用此软件。

* 在 [GitHub](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios) 上下载用于 iOS 的 Intune App SDK 的文件。

## <a name="whats-in-the-sdk-repository"></a>SDK 存储库中的内容

以下文件与不包含 Swift 代码或使用10.2 之前的 Xcode 版本编译的应用/扩展相关：

* **IntuneMAM.framework**：Intune App SDK 框架。 建议将此框架链接到应用/扩展，以启用 Intune 客户端应用程序管理。 但是，某些开发人员可能更倾向于静态库的性能优势。 参阅以下内容。

* **libIntuneMAM.a**：Intune App SDK 静态库。 开发人员可以选择链接静态库而不是框架。 由于在生成时静态库直接嵌入到应用/扩展二进制文件中，因此使用静态库有一些启动时性能优势。 但将其集成到你的应用程序是一个更复杂的过程。 如果你的应用程序包含任何扩展，则将静态库链接到应用程序和扩展会导致应用程序捆绑包大小较大，因为静态库将嵌入到每个应用/扩展二进制文件中。 使用 framework 时，应用和扩展可以共享同一 Intune SDK 二进制文件，从而使应用大小更小。

* **IntuneMAMResources.bundle**：一个资源包，包含 SDK 所依赖的资源。 资源捆绑仅适用于集成静态库（Libintunemam.a）的应用。

以下文件与包含 Swift 代码的应用/扩展相关，并通过 Xcode 10.2 + 编译：

* **IntuneMAMSwift**： INTUNE App SDK Swift 框架。 此框架包含应用将调用的 Api 的所有标头。 将此框架链接到应用/扩展，以启用 Intune 客户端应用程序管理。

* **IntuneMAMSwiftStub**： INTUNE App SDK Swift 存根 framework。 这是必须链接的应用/扩展所需的 IntuneMAMSwift 的依赖项。


以下文件与所有 apps/docs.ms 相关：

* **IntuneMAMConfigurator**：一种工具，用于配置应用程序或扩展的信息。 Info.plist 具有 Intune 管理的最低要求更改。 根据你的应用或扩展的功能，你可能需要对 info.plist 进行其他手动更改。

* **标头**：用于公开公共 Intune App SDK API。 这些标头包含在 IntuneMAM/IntuneMAMSwift 框架中，因此使用任一框架的开发人员无需手动将标头添加到项目。 选择链接到静态库（Libintunemam.a）的开发人员需要在其项目中手动包含这些标头。

以下头文件包含 Intune App SDK 面向开发人员发布的 API、数据类型和协议：

-  IntuneMAMAppConfig.h
-  IntuneMAMAppConfigManager.h
-  IntuneMAMDataProtectionInfo.h
-  IntuneMAMDataProtectionManager.h
-  IntuneMAMDefs.h
-  IntuneMAMDiagnosticConsole.h
-  IntuneMAMEnrollmentDelegate.h
-  IntuneMAMEnrollmentManager.h
-  IntuneMAMEnrollmentStatus.h
-  IntuneMAMFileProtectionInfo.h
-  IntuneMAMFileProtectionManager.h
-  IntuneMAMLogger.h
-  IntuneMAMPolicy.h
-  IntuneMAMPolicyDelegate.h
-  IntuneMAMPolicyManager.h
-  IntuneMAMVersionInfo.h

开发人员只需导入 IntuneMAM.h 即可获取上述所有标头的内容


## <a name="how-the-intune-app-sdk-works"></a>Intune App SDK 的使用方式

Intune App SDK for iOS 的目标是在最大程度上减少代码更改的情况下将管理功能添加到 iOS 应用中。 代码更改越少，面市时间就越短，但不影响移动应用程序的一致性和稳定性。


## <a name="build-the-sdk-into-your-mobile-app"></a>将 SDK 构建到移动应用中

若要启用 Intune App SDK，请执行以下步骤：

1. **选项 1-框架（推荐）** ：如果你使用的是 Xcode 10.2 +，而你的应用程序/扩展包含 Swift 代码，则将 `IntuneMAMSwift.framework` 和 `IntuneMAMSwiftStub.framework` 链接到你的目标：将 `IntuneMAMSwift.framework` 和 `IntuneMAMSwiftStub.framework` 拖到项目目标的 "**嵌入的二进制文件**" 列表。

    否则，将 `IntuneMAM.framework` 链接到目标：将 `IntuneMAM.framework` 拖到项目目标的 "**嵌入的二进制文件**" 列表。

   > [!NOTE]
   > 如果使用框架，必须在将应用提交到应用商店之前，从通用框架中手动删除模拟器体系结构。 有关详细信息，请参阅[向 App Store 提交应用](#submit-your-app-to-the-app-store)。

   **选项 2-静态库**：此选项仅适用于不包含 Swift 代码或使用 Xcode < 10.2 生成的应用/扩展。 链接到 `libIntuneMAM.a` 库。 将 `libIntuneMAM.a` 库拖动到项目目标的“链接的框架和库”  列表中。

    ![Intune App SDK iOS：链接的框架和库](./media/app-sdk-ios/intune-app-sdk-ios-linked-frameworks-and-libraries.png)

    将 `-force_load {PATH_TO_LIB}/libIntuneMAM.a` 添加到以下任一项，并将 `{PATH_TO_LIB}` 替换为 Intune App SDK 的位置：
   * 项目的 `OTHER_LDFLAGS` 内部版本配置设置。
   * Xcode UI 的“其他链接器标志”  。

     > [!NOTE]
     > 要查找 `PATH_TO_LIB`，请选择文件 `libIntuneMAM.a`，并从“文件”  菜单中选择“获取信息”  。 复制并粘贴“信息”  窗口中“常规”  部分的“位置”  信息（路径）。

     将 `IntuneMAMResources.bundle` 资源包添加到项目中，方法是在“构建阶段”  将此资源包拖放到“复制资源包”  下面。

     ![Intune App SDK iOS：复制资源包](./media/app-sdk-ios/intune-app-sdk-ios-copy-bundle-resources.png)
         
2. 将以下 iOS 框架添加到项目：  
-  MessageUI.framework  
-  Security.framework  
-  MobileCoreServices.framework  
-  SystemConfiguration.framework  
-  libsqlite3.tbd  
-  libc++.tbd  
-  ImageIO.framework  
-  LocalAuthentication.framework  
-  AudioToolbox.framework  
-  QuartzCore.framework  
-  WebKit.framework

3. 选择每个项目目标的“功能”  并启用“密钥链共享”  开关，启用密钥链共享（如果尚未启用）。 需要启用 Keychain 共享才能继续执行下一步。

   > [!NOTE]
   > 预配的配置文件需要支持新的 keychain 共享值。 keychain 访问组应支持通配符。 可通过以下方法进行验证：在文本编辑器中打开 .mobileprovision 文件，搜索 keychain-access-groups  ，确保其中包含通配符。 例如：
   >
   >  ```xml
   >  <key>keychain-access-groups</key>
   >  <array>
   >  <string>YOURBUNDLESEEDID.*</string>
   >  </array>
   >  ```

4. 启用 keychain 共享后，请按照以下步骤创建单独的访问组，以便 Intune App SDK 可在其中存储数据。 可以使用 UI 或使用授权文件创建 keychain 访问组。 如果你使用 UI 创建密钥链访问组，请务必按照以下步骤操作：

     a. 如果移动应用未定义任何 keychain 访问组，请将此应用的程序包 ID 添加为第一个组  。
    
    b. 将共享密钥链组 `com.microsoft.intune.mam` 添加到现有访问组中。 Intune App SDK 使用此访问组来存储数据。
    
    c. 将 `com.microsoft.adalcache` 添加到现有的访问组。
    
      ![Intune App SDK iOS：keychain 共享](./media/app-sdk-ios/intune-app-sdk-ios-keychain-sharing.png)
    
    d. 如果直接编辑权利文件，而不是使用上述 Xcode UI 创建密钥链访问组，则需要在密钥链访问组前加上 `$(AppIdentifierPrefix)`（Xcode 会自动处理此问题）。 例如：
    
      - `$(AppIdentifierPrefix)com.microsoft.intune.mam`
      - `$(AppIdentifierPrefix)com.microsoft.adalcache`
    
      > [!NOTE]
      > 授权文件是一个 XML 文件，它对于移动应用程序是唯一的。 它用于在 iOS 应用中指定特殊权限和功能。 如果应用以前没有权利文件，那么启用密钥链共享（第 3 步）应该已导致 Xcode 为应用生成一个权利文件。 请确保应用的程序包 ID 为列表中的首项。

5. 在应用的 Info.plist 文件的 `LSApplicationQueriesSchemes` 数组中添加应用传递到 `UIApplication canOpenURL` 的各个协议。 请务必先保存所做的更改，再继续执行下一步。

6. 如果应用已不再使用 FaceID，请务必使用默认消息配置 [NSFaceIDUsageDescription Info.plist 键](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/CocoaKeys.html#//apple_ref/doc/uid/TP40009251-SW75)。 这是必需的，这样 iOS 才能让用户知道应用计划如何使用 FaceID。 利用 Intune 应用保护策略设置，可使用 FaceID 获取应用访问权限（由 IT 管理员配置）。

7. 使用 [SDK 存储库](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)中的 IntuneMAMConfigurator 工具完成配置应用的 Info.plist。 该工具有以下三个参数：

   |属性|如何使用它|
   |---------------|--------------------------------|
   |- i |  `<Path to the input plist>` |
   |- e | `<Path to the entitlements file>` |
   |- o |  （可选）`<Path to the output plist>` |

如果未指定“-o”参数，将就地修改输入文件。 因为此工具是幂等类型，所以只要更改了应用的 Info.plist 或权利文件，就应该重新运行此工具。 还应在更新 Intune SDK 时下载并运行此工具的最新版本，以防最新版本中更改了 Info.plist 配置要求。

## <a name="configure-adalmsal"></a>配置 ADAL/MSAL

Intune App SDK 可以使用[Azure Active Directory 身份验证库](https://github.com/AzureAD/azure-activedirectory-library-for-objc)或[Microsoft 身份验证库](https://github.com/AzureAD/microsoft-authentication-library-for-objc)来实现其身份验证和条件启动方案。 它还依赖于 ADAL/MSAL 向 MAM 服务注册用户标识，用于不含设备注册方案的管理。

ADAL/MSAL 通常要求应用注册 Azure Active Directory (AAD)，并创建唯一的客户端 ID 和重定向 URI，以确保向应用授予的令牌的安全性。 如果应用已使用 ADAL 或 MSAL 对用户进行身份验证，应用必须使用它的现有注册值，并替代 Intune App SDK 默认值。 这可确保不会提示两次让用户进行身份验证（一次由 Intune App SDK，一次由应用）。

如果你的应用程序尚未使用 ADAL 或 MSAL，而你不需要访问任何 AAD 资源，则无需在 AAD 中设置客户端应用注册（如果选择集成 ADAL）。 如果决定集成 MSAL，则需要配置应用注册，并覆盖默认 Intune 客户端 ID 和重定向 URI。  

建议应用链接到[ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-objc/releases)或[MSAL](https://github.com/AzureAD/microsoft-authentication-library-for-objc/releases)的最新版本。

### <a name="link-to-adal-or-msal-binaries"></a>链接到 ADAL 或 MSAL 二进制文件

**选项 1-** 按照[以下步骤](https://github.com/AzureAD/azure-activedirectory-library-for-objc#download)将应用链接到 ADAL 二进制文件。

**选项 2-** 或者，您可以按照[这些说明](https://github.com/AzureAD/microsoft-authentication-library-for-objc#installation)将您的应用程序链接到 MSAL 二进制文件。

1. 如果应用未定义任何 keychain 访问组，请将此应用的程序包 ID 添加为第一个组。

2. 通过向密钥链访问组添加 `com.microsoft.adalcache`，启用 ADAL/MSAL 单一登录 (SSO)。

3. 如果正在显式设置 ADAL 共享缓存密钥链组，请确保将其设置为 `<appidprefix>.com.microsoft.adalcache`。 除非替代 ADAL，否则它将完成此设置。 如果希望指定一个自定义 keychain 组来替代 `com.microsoft.adalcache`，请在“IntuneMAMSettings”下的 Info.plist 文件中使用键 `ADALCacheKeychainGroupOverride` 进行指定。

### <a name="configure-adalmsal-settings-for-the-intune-app-sdk"></a>为 Intune App SDK 配置 ADAL/MSAL 设置

如果应用已使用 ADAL 或 MSAL 进行身份验证，并拥有自己的 Azure Active Directory 设置，你可以强制 Intune App SDK 在针对 AAD 进行身份验证期间使用相同的设置。 这样可确保应用不会两次提示用户进行身份验证。 请参阅 [Intune App SDK 的配置设置](#configure-settings-for-the-intune-app-sdk)，了解有关填充以下设置的信息：  

* ADALClientId
* ADALAuthority
* ADALRedirectUri
* ADALRedirectScheme
* ADALCacheKeychainGroupOverride

如果应用已使用 ADAL 或 MSAL，需要以下配置：

1. 在项目的 Info.plist 文件中，在键名称为 `ADALClientId` 的 **IntuneMAMSettings** 字典下指定要用于 ADAL 调用的客户端 ID。

2. 另外，在键名称为 `ADALAuthority` 的 **IntuneMAMSettings** 字典下指定 Azure AD 颁发机构。

3. 同时，在键名称为 `ADALRedirectUri` 的 **IntuneMAMSettings** 字典下指定要用于 ADAL 调用的重定向 URI。 也可以改为指定 `ADALRedirectScheme`（如果应用的重定向 URI 采用格式 `scheme://bundle_id` 的话）。

此外，应用还可以在运行时替代这些 Azure AD 设置。 为此，只需在 `IntuneMAMPolicyManager` 实例上设置 `aadAuthorityUriOverride`、`aadClientIdOverride` 和 `aadRedirectUriOverride` 属性。

4. 确保执行向应用保护策略 (APP) 服务提供 iOS 应用权限的步骤。 使用[向 Intune 应用保护服务提供应用访问权限(可选)](app-sdk-get-started.md#give-your-app-access-to-the-intune-app-protection-service-optional)下的 [Intune SDK 入门指南](app-sdk-get-started.md#next-steps-after-integration)中的说明。  

> [!NOTE]
> 对于不需要在运行时确定的所有静态设置，建议使用 Info.plist 方法。 分配给 `IntuneMAMPolicyManager` 属性的值优先于 Info.plist 中指定的任何相应值；即使在重启应用后，值也会暂留。 在用户遭取消注册或值被清除或更改前，SDK 会继续将它们用于策略签入。

### <a name="if-your-app-does-not-use-adal-or-msal"></a>如果应用不使用 ADAL 或 MSAL

如前文所述，Intune App SDK 可以使用[Azure Active Directory 身份验证库](https://github.com/AzureAD/azure-activedirectory-library-for-objc)或[Microsoft 身份验证库](https://github.com/AzureAD/microsoft-authentication-library-for-objc)来实现其身份验证和条件启动方案。 它还依赖于 ADAL/MSAL 向 MAM 服务注册用户标识，用于不含设备注册方案的管理。 如果**你的应用程序未将 ADAL 或 MSAL 用于其自己的身份验证机制**，则你可能需要配置自定义 AAD 设置，具体取决于你选择的集成身份验证库：   

ADAL - Intune App SDK 会为 ADAL 参数提供默认值，并处理针对 Azure AD 的身份验证。 开发人员无需为之前提到的 ADAL 设置指定任何值。 

MSAL-开发人员需要在 AAD 中创建应用注册，其中的自定义重定向 URI 采用[此处](https://github.com/AzureAD/microsoft-authentication-library-for-objc/wiki/Migrating-from-ADAL-Objective-C-to-MSAL-Objective-C#app-registration-migration)指定的格式。 开发人员应设置前面提到的 `ADALClientID` 和 `ADALRedirectUri` 设置，或 `IntuneMAMPolicyManager` 实例上的等效 `aadClientIdOverride` 和 `aadRedirectUriOverride` 属性。 开发人员还应确保他们按照上一部分中的步骤4，为其应用注册访问 Intune 应用保护服务。

### <a name="special-considerations-when-using-msal"></a>使用 MSAL 时的特殊注意事项 

1. **检查 Web 视图**-建议应用程序不要将 SFSafariViewController、SFAuthSession 或 ASWebAuthSession 用作应用程序启动的任何 MSAL 交互身份验证操作的 web 视图。 如果出于某种原因，应用必须将这些 webview 之一用于任何交互式 MSAL auth 操作，它还必须将 `SafariViewControllerBlockedOverride` 设置为在应用程序的 info.plist 中的 `IntuneMAMSettings` 字典下 `true`。 警告：这将关闭 Intune 的 SafariViewController 挂钩以启用身份验证会话。 当应用程序使用 SafariViewController 查看公司数据时，这会在应用程序中的其他地方冒数据泄漏，因此应用程序不应在任何这些 web 视图类型中显示公司数据。
2. 如果在这种情况下，必须**同时链接 adal 和 MSAL** -开发人员希望 Intune 更喜欢 MSAL over adal，则必须选择加入。 默认情况下，如果两个版本都在运行时链接，则 Intune 将更倾向于受支持的 MSAL 版本。 Intune 将仅在 Intune 第一次身份验证操作时首选受支持的 MSAL 版本，在 `NSUserDefaults` 中 `true` `IntuneMAMUseMSALOnNextLaunch`。 如果 `IntuneMAMUseMSALOnNextLaunch` `false` 或未设置，Intune 将回退为默认行为。 顾名思义，对 `IntuneMAMUseMSALOnNextLaunch` 所做的更改将在下一次启动时生效。


## <a name="configure-settings-for-the-intune-app-sdk"></a>配置 Intune App SDK 设置

可以使用应用程序的 Info.plist 文件中的 **IntuneMAMSettings** 字典设置和配置 Intune App SDK。 如果 Info.plist 文件中未显示 IntuneMAMSettings 字典，应进行创建。

在 IntuneMAMSettings 字典下，可以使用以下受支持设置来配置 Intune App SDK。

其中的一些设置可能已在前面各节中提及，一些设置则不适用于所有应用。

Setting  | 类型  | 定义 | 是否必需？
--       |  --   |   --       |  --
ADALClientId  | 字符串  | 应用的 Azure AD 客户端标识符。 | 对于使用 MSAL 的所有应用和访问非 Intune AAD 资源的任何 ADAL 应用都是必需的。 |
ADALAuthority | 字符串 | 应用使用的 Azure AD 颁发机构。 应使用已配置 AAD 帐户的你自己的环境。 | 如果应用使用 ADAL 或 MSAL 访问非 Intune AAD 资源，则是必需的。 如果此值不存在，则使用 Intune 默认值。|
ADALRedirectUri  | 字符串  | 应用的 Azure AD 重定向 URI。 | 对于所有使用 MSAL 的应用程序和访问非 Intune AAD 资源的任何 ADAL 应用，都需要 ADALRedirectUri 或 ADALRedirectScheme。  |
ADALRedirectScheme  | 字符串  | 应用的 Azure AD 重定向方案。 如果应用的重定向 URI 为 `scheme://bundle_id` 格式，则它可用于代替 ADALRedirectUri。 | 对于所有使用 MSAL 的应用程序和访问非 Intune AAD 资源的任何 ADAL 应用，都需要 ADALRedirectUri 或 ADALRedirectScheme。 |
ADALLogOverrideDisabled | 布尔值  | 指定 SDK 是否会将所有 ADAL/MSAL 日志（包括应用的 ADAL 调用（若有））路由到它自己的日志文件。 默认值为 NO。 如果应用将设置自己的 ADAL/MSAL 日志回叫，则设置为“YES”。 | 可选。 |
ADALCacheKeychainGroupOverride | 字符串  | 指定要用于 ADAL/MSAL 缓存（而不是“com.microsoft.adalcache”）的密钥链组。 注意，这并不包含应用 ID 前缀。 这将作为运行时所提供字符串的前缀。 | 可选。 |
AppGroupIdentifiers | 字符串数组  | 应用的授权 com.apple.security.application 组部分的应用组数组。 | 如果应用使用应用组，则需要此设置。 |
ContainingAppBundleId | 字符串 | 指定扩展的包含应用程序的程序包 ID。 | iOS 扩展需要此设置。 |
DebugSettingsEnabled| 布尔值 | 如果设置为“是”，则可以应用设置包中的测试策略。 应用程序*不*会因启用此设置而提供。 | 可选。 默认值为“否”。 |
AutoEnrollOnLaunch| 布尔值| 指定在检测到现有托管标识且应用尚未注册时，应用是否应尝试在启动时自动注册。 默认值为 NO。 <br><br> 注意：如果找不到任何托管标识，或 ADAL/MSAL 缓存中无任何有效标识令牌可用，那么注册尝试会静默失败，而不会提示输入凭据，除非应用也将 MAMPolicyRequired 设置为“YES”。 | 可选。 默认值为“否”。 |
MAMPolicyRequired| 布尔值| 如果应用没有 Intune 应用保护策略，指定是否要阻止应用启动。 默认值为 NO。 <br><br> 注意：MAMPolicyRequired 设置为 YES 时，无法将应用提交到应用商店。 MAMPolicyRequired 设置为 YES 时，AutoEnrollOnLaunch 也应设置为 YES。 | 可选。 默认值为“否”。 |
MAMPolicyWarnAbsent | 布尔值| 如果应用没有 Intune 应用保护策略，指定应用是否在启动期间警告用户。 <br><br> 注意：解除警报后，仍将允许用户在没有策略的情况下使用应用。 | 可选。 默认值为“否”。 |
MultiIdentity | 布尔值| 指定应用是否识别多身份标识。 | 可选。 默认值为“否”。 |
SafariViewControllerBlockedOverride | 布尔值| 禁用 Intune 的 SafariViewController 挂钩，通过 SFSafariViewController、SFAuthSession 或 ASWebAuthSession 启用 MSAL authentication。 | 可选。 默认值为“否”。 警告：如果使用不当，可能会导致数据泄漏。 仅在绝对必要时启用。 有关详细信息，请参阅[使用 MSAL 时的特殊注意事项](#special-considerations-when-using-msal)。  |
SplashIconFile~ipad <br>IntuneMAMSettings | 字符串  | 指定 Intune 初始屏幕（启动）图标文件。 | 可选。 |
SplashDuration | 数字 | 应用程序启动时显示 Intune 启动屏幕的最小时间（以秒为单位）。 默认值为 1.5。 | 可选。 |
BackgroundColor| 字符串| 指定 Intune SDK 的 UI 组件的背景色。 接受 #XXXXXX 格式的十六进制 RGB 字符串，其中 X 的范围可以为 0-9 或 A-F。 可忽略井号。   | 可选。 默认情况下，系统背景色可能因不同版本的 iOS 和 iOS 深色模式设置而异。 |
ForegroundColor| 字符串| 指定 Intune SDK 的 UI 组件的前景色，如文本颜色。 接受 #XXXXXX 格式的十六进制 RGB 字符串，其中 X 的范围可以为 0-9 或 A-F。 可忽略井号。  | 可选。 默认为系统标签颜色，在不同版本的 iOS 中以及根据 iOS 深色模式设置，这些颜色可能有所不同。 |
AccentColor | 字符串| 指定 Intune SDK 的 UI 组件的强调颜色，例如按钮文本颜色和固定框突出显示颜色。 接受 #XXXXXX 格式的十六进制 RGB 字符串，其中 X 的范围可以为 0-9 或 A-F。 可忽略井号。| 可选。 默认为系统蓝色。 |
SupportsDarkMode| 布尔值 | 指定在没有为 BackgroundColor/ForegroundColor/AccentColor 设置显式值的情况下，Intune SDK 的 UI 配色方案是否应观察系统暗色模式设置 | 可选。 默认为“是”。 |
MAMTelemetryDisabled| 布尔值| 指定 SDK 是否会将任何遥测数据发送到其后端。| 可选。 默认值为“否”。 |
MAMTelemetryUsePPE | 布尔值 | 指定 MAM SDK 是否将数据发送到 PPE 遥测后端。 使用 Intune 策略测试应用时使用该布尔值，以便测试遥测数据不会与客户数据相混淆。 | 可选。 默认值为“否”。 |
MaxFileProtectionLevel | 字符串 | 可选。 允许应用指定其可以支持的 `NSFileProtectionType` 最大值。 如果该级别高于应用程序可以支持的级别，则此值将替代服务发送的策略。 可能的值：`NSFileProtectionComplete`、`NSFileProtectionCompleteUnlessOpen`、`NSFileProtectionCompleteUntilFirstUserAuthentication`、`NSFileProtectionNone`。|
OpenInActionExtension | 布尔值 | 对于 Open in Action 扩展，设置为“是”。 有关详细信息，请参阅通过 UIActivityViewController 共享数据部分。 |
WebViewHandledURLSchemes | 字符串数组 | 指定应用的 WebView 处理的 URL 方案。 | 应用使用的 WebView 通过链接和/或 javascript 处理 URL 时需要。 |

## <a name="receive-app-protection-policy"></a>接收应用保护策略

### <a name="overview"></a>概述

要接收 Intune 应用保护策略，应用必须发起向 Intune MAM 服务注册的请求。 可以在 Intune 控制台中配置应用，这样无论是否有设备注册，都可以接收应用保护策略。 没有设备注册的应用保护策略亦称为“APP-WE”  或“MAM-WE”，这样应用就可以由 Intune 管理，而无需在 Intune 移动设备管理 (MDM) 中注册设备。 在这两种情况下，都必须向 Intune MAM 服务注册应用，才能接收策略。

> [!Important]
> 应用保护策略启用加密时，适用于 iOS 的 Intune App SDK 将使用 256 位加密密钥。 所有应用都需要拥有当前 SDK 版本以允许受保护的数据共享。

### <a name="apps-that-already-use-adal-or-msal"></a>已使用 ADAL 或 MSAL 的应用

如果已使用 ADAL 或 MSAL，应用应在用户已成功通过身份验证后对 `IntuneMAMEnrollmentManager` 实例调用 `registerAndEnrollAccount` 方法：

```objc
/*
 *  This method will add the account to the list of registered accounts.
 *  An enrollment request will immediately be started.
 *  @param identity The UPN of the account to be registered with the SDK
 */

(void)registerAndEnrollAccount:(NSString *)identity;
```

通过调用 `registerAndEnrollAccount` 方法，SDK 会注册用户帐户并尝试代表此帐户注册应用。 如果注册由于任何原因失败，SDK 会在 24 小时后自动重试注册。 出于调试目的，应用可通过委托接收有关任何注册请求的结果的[通知](#status-result-and-debug-notifications)。

在调用此 API 后，应用可继续正常工作。 如果注册成功，SDK 会通知用户需要重启应用。 此时，用户可立即重启应用。

```objc
[[IntuneMAMEnrollmentManager instance] registerAndEnrollAccount:@”user@foo.com”];
```

### <a name="apps-that-do-not-use-adal-or-msal"></a>不使用 ADAL 或 MSAL 的应用

如果不使用 ADAL 或 MSAL 来登录用户，应用仍可以从 Intune MAM 服务接收应用保护策略，具体方法是调用 API 让 SDK 处理相应身份验证。 当应用尚未使用 Azure AD 对用户进行身份验证，但仍需要检索应用保护策略以帮助保护数据时，应使用此方法。 例如，正在使用另一个身份验证服务进行应用登录时，或应用完全不支持登录时。 为此，应用可以对 `IntuneMAMEnrollmentManager` 实例调用 `loginAndEnrollAccount` 方法：

```objc
/**
 *  Creates an enrollment request which is started immediately.
 *  If no token can be retrieved for the identity, the user will be prompted
 *  to enter their credentials, after which enrollment will be retried.
 *  @param identity The UPN of the account to be logged in and enrolled.
 */
 (void)loginAndEnrollAccount: (NSString *)identity;
```

通过调用此方法，如果找不到任何现有令牌，SDK 会提示用户输入凭据。 随后，SDK 会尝试代表提供的用户帐户向 Intune MAM 服务注册应用。 可以使用作为标识的“nil”调用此方法。 在这种情况下，SDK 会使用设备上的现有托管用户进行注册（在 MDM 中），或在找不到任何现有用户时提示用户输入用户名。

如果注册失败，应用应考虑在之后某一时间再次调用此 API，取决于失败的详细信息。 应用可通过委托接收有关任何注册请求的结果的[通知](#status-result-and-debug-notifications)。

在调用此 API 后，应用可继续正常工作。 如果注册成功，SDK 会通知用户需要重启应用。

例如：

```objc
[[IntuneMAMEnrollmentManager instance] loginAndEnrollAccount:@”user@foo.com”];
```

### <a name="let-intune-handle-authentication-and-enrollment-at-launch"></a>启动时由 Intune 处理身份验证和注册

若要让 Intune SDK 在应用完成启动前使用 ADAL/MSAL 处理所有身份验证和注册，并且应用始终需要 APP 策略，则不必使用 `loginAndEnrollAccount` API。 只需在应用的 Info.plist 的 IntuneMAMSettings 字典中将以下两个设置设置为“是”即可。

Setting  | 类型  | 定义 |
--       |  --   |   --       |  
AutoEnrollOnLaunch| 布尔值| 指定在检测到现有托管标识且应用尚未注册时，应用是否应尝试在启动时自动注册。 默认值为 NO。 <br><br> 注意：如果找不到任何托管标识，或 ADAL/MSAL 缓存中无任何有效标识令牌可用，那么注册尝试会静默失败，而不会提示输入凭据，除非应用也将 MAMPolicyRequired 设置为“YES”。 |
MAMPolicyRequired| 布尔值| 如果应用没有 Intune 应用保护策略，指定是否要阻止应用启动。 默认值为 NO。 <br><br> 注意：MAMPolicyRequired 设置为“是”时，无法将应用提交到应用商店。 MAMPolicyRequired 设置为 YES 时，AutoEnrollOnLaunch 也应设置为 YES。 |

如果为应用选择此选项，则无需在注册后重启应用。

### <a name="deregister-user-accounts"></a>取消注册用户帐户

在用户注销应用之前，应用应从 SDK 取消注册用户。 这可确保：

1. 不再对用户的帐户进行注册重试。

2. 将会删除应用保护策略。

3. 如果应用启动选择性擦除（可选），则将删除所有相关数据。

在用户注销前，应用应对 `IntuneMAMEnrollmentManager` 实例调用以下方法：

```objc
/*
 *  This method will remove the provided account from the list of
 *  registered accounts.  Once removed, if the account has enrolled
 *  the application, the account will be un-enrolled.
 *  @note In the case where an un-enroll is required, this method will block
 *  until the Intune APP AAD token is acquired, then return.  This method must be called before  
 *  the user is removed from the application (so that required AAD tokens are not purged
 *  before this method is called).
 *  @param identity The UPN of the account to be removed.
 *  @param doWipe   If YES, a selective wipe if the account is un-enrolled
 */
(void)deRegisterAndUnenrollAccount:(NSString *)identity withWipe:(BOOL)doWipe;
```

在删除用户帐户的 Azure AD 令牌之前，必须调用此方法。 SDK 需要用户帐户的 AAD 令牌，才能代表用户向 Intune MAM 服务发出特定请求。

如果应用要自行删除用户的公司数据，则可将 `doWipe` 标志设置为 false。 否则，应用可让 SDK 启动选择性擦除。 这会导致调用应用的选择性擦除委托。

例如：

```objc
[[IntuneMAMEnrollmentManager instance] deRegisterAndUnenrollAccount:@”user@foo.com” withWipe:YES];
```

## <a name="status-result-and-debug-notifications"></a>状态、结果和调试通知

应用可接收有关以下向 Intune MAM 服务发出的请求的状态、结果和调试通知：

* 注册请求
* 策略更新请求
* 取消注册请求

将通过 `IntuneMAMEnrollmentDelegate.h` 中的委托方法显示通知：

```objc
/**
 *  Called when an enrollment request operation is completed.
 * @param status status object containing debug information
 */

(void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;

/**
 *  Called when a MAM policy request operation is completed.
 *  @param status status object containing debug information
 */
(void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;

/**
 *  Called when a un-enroll request operation is completed.
 *  @Note: when a user is un-enrolled, the user is also de-registered with the SDK
 *  @param status status object containing debug information
 */

(void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;
```

这些委托方法都会返回一个 `IntuneMAMEnrollmentStatus` 对象，其中包含以下信息：

* 与请求关联的帐户的标识
* 指示请求结果的状态代码
* 带有状态代码说明的错误字符串
* 一个 `NSError` 对象。 此对象连同可返回的特定状态代码在 `IntuneMAMEnrollmentStatus.h` 中进行定义。

### <a name="sample-code"></a>代码示例

以下是委托方法的示例实现：

```objc
- (void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"enrollment result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"policy check-in result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"un-enroll result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}
```

## <a name="application-restart"></a>应用程序重启

应用首次接收 MAM 策略时必须重启才能应用所需挂钩。 为了通知应用需要重启，SDK 在 `IntuneMAMPolicyDelegate.h` 中提供了委托方法。

```objc
 - (BOOL) restartApplication
```

此方法的返回值会告诉 SDK 应用程序是否必须处理所需的重启：

* 如果返回 true，则应用程序必须处理重启。

* 如果返回 false，则 SDK 会在此方法返回后重启应用程序。 SDK 会立即显示一个对话框，告知用户重启应用程序。

## <a name="customize-your-apps-behavior-with-apis"></a>使用 API 自定义应用行为

可调用 Intune App SDK 的几个 API 来获取有关部署到应用的 Intune APP 策略信息。 可以使用此数据自定义应用行为。 下表介绍了将使用的一些基本 Intune 类。

实例 | 描述
----- | -----------
IntuneMAMPolicyManager.h | IntuneMAMPolicyManager 类公开部署到应用程序的 Intune APP 策略。 值得注意的是，它公开对[启用多身份标识](app-sdk-ios.md#enable-multi-identity-optional)有用的 API。 |
IntuneMAMPolicy.h | IntuneMAMPolicy 类公开一些适用于该应用的 MAM 策略设置。 公开这些策略以便应用自定义其 UI。 大多数策略设置由 SDK 而不是应用实现。 “另存为”控件是应由应用实现的唯一设置。 此类公开了实现“另存为”所需的一些 API。 |
IntuneMAMFileProtectionManager.h | IntuneMAMFileProtectionManager 类公开 API，应用可使用这些 API 根据提供的标识显式保护文件和目录。 标识可由 Intune 托管或非托管，SDK 将应用相应的 MAM 策略。 可选择是否使用此类。 |
IntuneMAMDataProtectionManager.h | IntuneMAMDataProtectionManager 类公开 API，应用可以使用这些 API 来保护给定提供标识的数据缓冲区。 标识可由 Intune 托管或非托管，SDK 将相应地应用加密。 |

## <a name="implement-save-as-controls"></a>实现“另存为”控件

通过 Intune，IT 管理员可选择托管应用保存数据的存储位置。 应用可使用 `IntuneMAMPolicy.h` 中定义的 `isSaveToAllowedForLocation` API 在 Intune App SDK 中查询允许的存储位置。

应用将托管数据保存到云存储或本地位置前，必须使用 `isSaveToAllowedForLocation` API 进行检查，了解 IT 管理员是否允许将数据保存在此处。

使用 `isSaveToAllowedForLocation` API 时，应用必须传入用于存储位置的 UPN（如可用）。

### <a name="supported-save-locations"></a>支持的存储位置

`isSaveToAllowedForLocation` API 提供常量来检查 IT 管理员是否允许将数据保存到在 `IntuneMAMPolicy.h` 中定义的以下位置：

* IntuneMAMSaveLocationOther
* IntuneMAMSaveLocationOneDriveForBusiness
* IntuneMAMSaveLocationSharePoint
* IntuneMAMSaveLocationLocalDrive

应用应使用 `isSaveToAllowedForLocation` 中的常量来检查是否可将数据保存到“托管”位置（如 OneDrive for Business）或“个人”。 此外，应用无法确定是“托管”还是“个人”位置时，应使用 API。

`IntuneMAMSaveLocationOther` 常数代表已知为“个人”的位置。

如果应用将数据保存到本地设备上的任何位置，应使用 `IntuneMAMSaveLocationLocalDrive` 常数。

## <a name="share-data-via-uiactivityviewcontroller"></a>通过 UIActivityViewController 共享数据

从版本 8.0.2 开始，Intune App SDK 可以筛选 `UIActivityViewController` 操作，以便只有 Intune 托管的共享位置可供选择。 此行为将由应用程序数据传输策略控制。

### <a name="copy-to-actions"></a>“复制到”操作

通过 `UIActivityViewController` 和 `UIDocumentInteractionController` 共享文档时，iOS 会为每个支持打开该共享文档的应用程序显示“复制到”操作。 应用程序通过其 Info.plist 中的 `CFBundleDocumentTypes` 设置声明它们支持的文档类型。 如果策略禁止共享给非托管应用程序，则此类共享将不再可用。 作为替代，用户必须将非 UI Action 扩展添加到其应用程序并将其链接到 Intune App SDK。 Action 扩展只是存根。 SDK 将实现文件共享行为。 请遵循以下步骤进行配置：

1. 应用程序必须在其 Info.plist `CFBundleURLTypes` 下至少定义一个 schemeURL。

2. 应用程序和操作扩展必须共享至少一个应用组，并且该应用组必须列在应用和扩展 IntuneMAMSettings 字典下的 `AppGroupIdentifiers` 数组下。

3. 将操作扩展命名为“Open in”，后跟应用程序名称。 根据需要本地化 Info.plist。

4. 如 [Apple 开发者文档](https://developer.apple.com/ios/human-interface-guidelines/extensions/sharing-and-actions/)中所述提供扩展的模板图标。 或者，可以使用 IntuneMAMConfigurator 工具从应用程序 .app 目录生成这些图像。 若要执行此操作，请运行：

    ```bash
    IntuneMAMConfigurator -generateOpenInIcons /path/to/app.app -o /path/to/output/directory
    ```

5. 在扩展 Info.plist 中的 IntuneMAMSettings 下，添加一个名为 `OpenInActionExtension` 且值为“是”的布尔设置。

6. 配置 `NSExtensionActivationRule` 以支持单个文件以及应用程序的 `CFBundleDocumentTypes` 中以“`com.microsoft.intune.mam`”为前缀的所有类型。 例如，如果应用程序支持 public.text 和 public.image，则激活规则为：

    ```objc
    SUBQUERY (
        extensionItems,
        $extensionItem,
        SUBQUERY (
            $extensionItem.attachments,
            $attachment,
            ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.text” ||
            ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.image”).@count == 1
    ).@count == 1
    ```

### <a name="update-existing-share-and-action-extensions"></a>更新现有的 Share 和 Action 扩展

如果应用已包含 Share 或 Action 扩展，则必须修改它们的 `NSExtensionActivationRule` 以允许 Intune 类型。 对于扩展支持的每种类型，需添加以“`com.microsoft.intune.mam`”为前缀的附加类型。 例如，如果现有的激活规则是：  

```objc
SUBQUERY (
    extensionItems,
    $extensionItem,
    SUBQUERY (
        $extensionItem.attachments,
        $attachment,
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.data"
    ).@count > 0
).@count > 0
```

它应更改为：

```objc
SUBQUERY (
    extensionItems,
    $extensionItem,
    SUBQUERY (
        $extensionItem.attachments,
        $attachment,
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.data" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.data
    ).@count > 0
).@count > 0
```

> [!NOTE]
> 可以使用 IntuneMAMConfigurator 工具将 Intune 类型添加到激活规则。 如果现有的激活规则使用预定义的字符串常量（例如 NSExtensionActivationSupportsFileWithMaxCount、NSExtensionActivationSupportsText 等），谓词语法可能会变得相当复杂。 添加 Intune 类型时，IntuneMAMConfigurator 工具也可用于将激活规则从字符串常量转换为谓词字符串。

### <a name="what-the-ui-should-look-like"></a>UI 的外观

旧版 UI：

![共享数据 - iOS 旧的共享 UI](./media/app-sdk-ios/sharing-UI-old.png)

新版 UI：

![共享数据 - iOS 新的共享 UI](./media/app-sdk-ios/sharing-UI-new.png)

## <a name="enable-targeted-configuration-appmam-app-config-for-your-ios-applications"></a>为 iOS 应用程序启用目标配置（APP/MAM 应用配置）

面向 MAM 的配置（也称为 MAM 应用配置）允许应用通过 Intune SDK 接收配置数据。 应用所有者/开发人员须定义此数据的格式和变体并将其传达给 Intune 客户。

Intune 管理员可以通过 Intune Azure 门户和 Intune 图形 API 定位并部署配置数据。 自 Intune App SDK for iOS 7.0.1 版起，参与 MAM 目标配置的应用均可通过 MAM 服务获取 MAM 目标配置数据。 通过 MAM 服务直接将应用程序配置数据推送到应用，而非通过 MDM 渠道。 Intune App SDK 提供一个类，可用于访问从这些控制台检索的数据。 下列各项为必备项：

* 访问面向 MAM 的配置 UI 之前，需要向 Intune MAM 服务注册应用。 有关详细信息，请参阅[接收应用保护策略](#receive-app-protection-policy)。

* 将 `IntuneMAMAppConfigManager.h` 包括在应用的源文件中。

* 调用 `[[IntuneMAMAppConfigManager instance] appConfigForIdentity:]` 以获取应用配置对象。

* 对 `IntuneMAMAppConfig` 对象调用适当的选择器。 例如，如果应用程序密钥是一个字符串，则需要使用 `stringValueForKey` 或 `allStringsForKey`。 请参阅 `IntuneMAMAppConfig.h` 了解有关返回值和错误条件的详细说明。

有关图形 API 功能的详细信息，请参阅[图形 API 参考](https://developer.microsoft.com/graph/docs/concepts/overview)。

关于如何在 iOS 中创建面向 MAM 的应用配置策略的详细信息，请参阅[如何使用适用于 iOS 的 Microsoft Intune 应用配置策略](../apps/app-configuration-policies-use-ios.md)。

## <a name="telemetry"></a>遥测技术

默认情况下，用于 iOS 的 Intune App SDK 会收集以下事件类型的遥测：

* **应用启动事件**：用于帮助 Microsoft Intune 按照管理类型（含 MDM 的 MAM、不含 MDM 注册的 MAM 等）了解已启用 MAM 的应用的使用情况。

* **注册调用**：用于帮助 Microsoft Intune 了解客户端启动的注册调用的成功率和其他各种性能指标。

* **Intune 操作**：为了帮助诊断问题并确保 Intune 功能，我们会收集有关 Intune SDK 操作的信息。

> [!NOTE]
> 如果选择不将 Intune App SDK 遥测数据从移动应用程序发送到 Microsoft Intune，则必须禁用 Intune App SDK 遥测数据捕获功能。 在 IntuneMAMSettings 字典中将属性 `MAMTelemetryDisabled` 设置为“是”。

## <a name="enable-multi-identity-optional"></a>启用多身份标识（可选）

默认情况下，SDK 会将策略作为一个整体应用到该应用。 多身份标识是一项 MAM 功能，启用后可在每个标识级别上应用策略。 这需要比其他 MAM 功能还要多的应用参与。

应用必须在其意图更改现用身份时通知应用 SDK。 SDK 也会在需要标识更改时通知应用。 目前，仅支持一个托管标识。 用户注册设备或应用后，SDK 会使用此标识并将其视为主要托管标识。 应用中的其他用户会被视为具有不受限策略设置的非托管标识。

请注意，标识简单地定义为字符串。 标识不区分大小写。 向 SDK 请求标识可能不会返回在设置标识时最初使用的相同大小写情况。

### <a name="identity-overview"></a>标识概述

标识就是帐户的用户名（例如 user@contoso.com）。 开发人员可在以下级别上设置应用的标识：

* **进程标识**：设置进程级标识，并且主要用于单一标识应用程序。 此标识会影响所有任务、文件和 UI。

* **UI 标识**：确定应用于主线程上 UI 任务的策略，例如剪切/复制/粘贴、PIN、身份验证和数据共享。 UI 标识不会影响文件任务（如加密和备份）。

* **线程标识**：线程标识会影响应用于当前线程上的策略类型。 此标识会影响所有任务、文件和 UI。

不论用户是否为托管，应用都会负责设置合适的标识。

在任何时候，每个线程都具有用于 UI 任务和文件任务的有效标识。 此标识是用于确定应应用哪些策略（如有）的标识。 如果此标识为“无标识”或用户不是托管的，则不会应用任何策略。 下图显示如何确定有效的标识。

  ![Intune App SDK iOS：标识确定过程](./media/app-sdk-ios/ios-thread-identities.png)

### <a name="thread-queues"></a>线程队列

应用通常将异步和同步任务调度到线程队列。 SDK 截获 Grand Central Dispatch (GCD) 调用，并将当前线程标识与调度任务相关联。 完成任务时，SDK 会临时将线程标识更改为与任务相关联的标识，再完成任务，然后还原原始线程标识。


由于 `NSOperationQueue` 基于 GCD 之上，`NSOperations` 会在任务被添加到 `NSOperationQueue` 的同时运行线程标识。 `NSOperations` 或直接通过 GCD 调度的函数还可以在当前线程标识运行时对其进行更改。 此标识会替代继承自调度线程的标识。

### <a name="file-owner"></a>文件所有者

SDK 跟踪本地文件所有者的标识，并相应地应用策略。 文件所有者是在创建该文件时或在截断模式下打开文件时建立的。 所有者被设置为执行任务的线程的有效文件任务标识。

应用也可以使用 `IntuneMAMFilePolicyManager` 显式设置文件所有者标识。 应用可以使用 `IntuneMAMFilePolicyManager` 在显示该文件的内容之前检索文件所有者和设置 UI 标识。

### <a name="shared-data"></a>共享数据

如果应用创建包含同时来自托管和非托管用户的数据的文件，则应用负责加密托管用户的数据。 可以通过使用 `IntuneMAMDataProtectionManager` 中的 `protect` 和 `unprotect` API 加密数据。

`protect` 方法接受为托管或非托管用户的标识。 如果用户为托管用户，则会对数据进行加密。 如果用户为非托管用户，则会将一个编码有标识的标头添加到数据中，而不会对数据进行加密。 可以使用 `protectionInfo` 方法检索数据的所有者。

### <a name="share-extensions"></a>共享扩展

如果应用包含共享扩展，则可以使用 `IntuneMAMDataProtectionManager` 中的 `protectionInfoForItemProvider` 方法检索要共享项的所有者。 如果共享项为文件，则 SDK 会处理设置文件所有者。 如果共享项为数据，则应用负责设置文件所有者（如果此数据永久保存到一个文件中），并负责在 UI 中显示此数据之前调用 `setUIPolicyIdentity` API。

### <a name="turn-on-multi-identity"></a>打开多身份标识

默认情况下，应用被视为单一标识。 SDK 将进程标识设置为已注册的用户。 若要启用多身份标识支持，需要将名为 `MultiIdentity` 且值为“YES”的布尔设置添加到应用的 Info.plist 文件中的 IntuneMAMSettings 字典。

> [!NOTE]
> 启用多身份标识后，进程标识、UI 标识和线程标识将被设置为 nil。 应用负责适当地设置它们。

### <a name="switch-identities"></a>切换标识

* **应用启动标识切换**：

    在启动时，多身份标识应用被视为在未知的非托管帐户下运行。 条件启动 UI 不会运行，且不会在该应用上强制执行任何策略。 应用负责在标识需要更改时通知 SDK。 通常情况下，当应用要显示特定用户帐户的数据时会发出通知。

    例如，用户尝试打开文档、邮箱或笔记本中的标签页时。 应用需在实际打开文件、邮箱或标签页之前通知 SDK。 可通过 `IntuneMAMPolicyManager` 中的 `setUIPolicyIdentity` API 实现。 不论用户是否为托管都应调用此 API。 如果用户为托管用户，则 SDK 会执行条件启动检查（如破解检测、PIN 和身份验证）。

    标识切换的结果会通过完成处理程序异步返回到应用。 应用应推迟打开文档、邮箱或标签页，直到返回成功结果代码。 如果标识切换失败，应用应取消任务。

* SDK 启动标识切换  ：

    有时，SDK 需要要求应用切换到特定标识。 多身份标识应用必须实现 `IntuneMAMPolicyDelegate` 中的 `identitySwitchRequired` 方法来处理此请求。

    调用此方法时，如果应用能够处理切换到特定标识的请求，则应将 `IntuneMAMAddIdentityResultSuccess` 传递到完成处理程序中。 如果无法处理切换标识，应用应将 `IntuneMAMAddIdentityResultFailed` 传递到完成处理程序中。

    应用无需调用 `setUIPolicyIdentity` 来响应此调用。 如果 SDK 需要应用切换到非托管用户帐户，则空字符串将传递到 `identitySwitchRequired` 调用。

* **选择性擦除**：

    应用为选择性擦除时，SDK 会调用 `IntuneMAMPolicyDelegate` 中的 `wipeDataForAccount` 方法。 应用负责删除指定用户的帐户以及任何与其关联的数据。 如果应用从 `wipeDataForAccount` 调用返回 FALSE，则 SDK 将删除用户拥有的全部文件。

    注意，需从后台线程调用此方法。 除非已删除用户的所有数据，否则应用不会返回任何值（文件除外，应用会返回 FALSE）。

## <a name="ios-best-practices"></a>iOS 最佳做法

以下是针对 iOS 进行开发时建议采用的最佳做法：

* IOS 文件系统是区分大小写的。 确保文件名大小写正确，如 `libIntuneMAM.a` 和 `IntuneMAMResources.bundle`。

* 如果 Xcode 在查找 `libIntuneMAM.a` 时遇到问题，可以通过将此库的路径添加到链接器搜索路径来解决此问题。

## <a name="faqs"></a>常见问题解答

### <a name="are-all-of-the-apis-addressable-through-native-swift-or-the-objective-c-and-swift-interoperability"></a>是否所有 API 都可通过本机 Swift 或 Objective-C 和 Swift 互操作性进行寻址？

Intune App SDK API 仅可采用 Objective-C 且不支持**本机** Swift。 Objective-C 必须与 Swift 具有互操作性。

### <a name="do-all-users-of-my-application-need-to-be-registered-with-the-app-we-service"></a>应用程序的所有用户是否都需要注册 APP-WE 服务？

不能。 实际上，只有工作或学校帐户需要向 Intune App SDK 注册。 应用负责确定所使用的帐户是否为工作或学校账户。

### <a name="what-about-users-that-have-already-signed-in-to-the-application-do-they-need-to-be-enrolled"></a>已登录到应用程序的用户呢？ 他们是否需要注册？

应用程序负责在用户成功通过身份验证后注册用户。 此外，应用程序还负责注册任何现有帐户，这些帐户创建时可能应用程序中还没有 MDM 和 MAM 功能。

为此，应用程序应使用 `registeredAccounts:` 方法。 此方法会返回 NSDictionary，其中包含所有已注册到 Intune MAM 服务的帐户。 如果应用程序中没有任何现有帐户存在于列表中，则应用程序应注册，并通过 `registerAndEnrollAccount:` 注册这些帐户。

### <a name="how-often-does-the-sdk-retry-enrollments"></a>SDK 多长时间会重试注册？

SDK 会在上一次注册失败后每隔 24 小时自动重试。 SDK 这样做是为了确保：即使用户的组织在用户登录到应用程序后启用了 MAM，用户也能成功注册并接收策略。

SDK 会在检测到用户已成功注册该应用程序后停止重试。 这是因为只有 1 位用户可以在特定时间注册应用程序。 如果用户未注册，则将在同样 24 小时间隔后再次开始重试。

### <a name="why-does-the-user-need-to-be-deregistered"></a>为何用户需要取消注册？

SDK 将在后台定期执行以下操作：

* 如果应用程序尚未注册，SDK 会每隔 24 小时尝试注册所有已注册的帐户。
* 如果应用程序已注册，SDK 会每隔 8 小时检查 MAM 策略更新。

取消注册用户会通知 SDK 用户不再使用该应用程序，并且 SDK 可以停止该用户帐户的任何周期事件。 如有必要，这也会触发应用取消注册和选择性擦除。

### <a name="should-i-set-the-dowipe-flag-to-true-in-the-deregister-method"></a>是否应在取消注册方法中将 doWipe 标志设置为 true？

应在用户注销应用程序之前调用此方法。  如果作为注销的一部分，已从应用程序中删除用户的数据，则可将 `doWipe` 设置为 false。 但是，如果应用程序未删除用户的数据，则 `doWipe` 应设置为 true，以便 SDK 可以删除数据。

### <a name="are-there-any-other-ways-that-an-application-can-be-un-enrolled"></a>是否有其他可以取消注册应用程序的方法？

是，IT 管理员可以向应用程序发送选择性擦除命令。 这将取消注册并注销用户，并且将擦除用户的数据。 SDK 自动处理此方案，并将通过取消注册委托方法发送通知。

### <a name="is-there-a-sample-app-that-demonstrates-how-to-integrate-the-sdk"></a>是否提供演示如何集成 SDK 的示例应用？

可以！ 我们最近刚刚改进了开源示例应用[适用于 iOS 的 Wagr](https://github.com/Microsoft/Wagr-Sample-Intune-iOS-App)。 现在，Wagr 已使用 Intune App SDK 启用应用保护策略。

### <a name="how-can-i-troubleshoot-my-app"></a>如何对应用进行故障排除？

Intune SDK for iOS 9.0.3 + 支持在移动应用内添加诊断控制台，用于测试策略和记录错误。 `IntuneMAMDiagnosticConsole.h` 定义 `IntuneMAMDiagnosticConsole` 类接口，开发人员可以使用该接口显示 Intune 诊断控制台。 这样，最终用户或开发人员就可以在测试过程中收集和共享 Intune 日志，以帮助诊断他们可能遇到的任何问题。 此 API 对于集成程序是可选的。

## <a name="submit-your-app-to-the-app-store"></a>将应用提交到应用商店

Intune App SDK 的静态库和框架版本都是通用的二进制文件。 这意味着它们包含适用于所有设备和模拟器体系结构的代码。 如果应用含有模拟器代码，Apple 会拒绝将其提交到应用商店。 针对仅设备生成的静态库编译时，链接器会自动删除模拟器代码。 按照下面的步骤确保将应用上载到应用商店之前删除所有模拟器代码。

1. 请确保 `IntuneMAM.framework` 位于桌面上。

2. 运行以下命令：

    ```bash
    lipo ~/Desktop/IntuneMAM.framework/IntuneMAM -remove i386 -remove x86_64 -output ~/Desktop/IntuneMAM.device_only
    ```

    ```bash
    cp ~/Desktop/IntuneMAM.device_only ~/Desktop/IntuneMAM.framework/IntuneMAM
    ```

    第一个命令用于从框架的 DYLIB 文件中删除模拟器体系结构。 第二个命令用于将仅设备 DYLIB 复制回框架目录。
