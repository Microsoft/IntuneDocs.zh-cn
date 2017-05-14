---
title: "用于 iOS 的 Microsoft Intune App SDK 开发人员指南 | Microsoft Docs"
description: "用于 iOS 的 Microsoft Intune App SDK 支持将 Intune 应用保护策略（以移动应用管理 (MAM) 的形式）集成到 iOS 应用中。"
keywords: 
author: mtillman
manager: angrobe
ms.author: mtillman
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df54ac3a62b5ef21e8a32f3a282dd5299974a1b0
ms.openlocfilehash: 1d2cb0d4b9442262c562e559a675f5a4a28ee572
ms.contentlocale: zh-cn
ms.lasthandoff: 05/03/2017


---

# <a name="microsoft-intune-app-sdk-for-ios-developer-guide"></a>用于 iOS 的 Microsoft Intune App SDK 开发人员指南

> [!NOTE]
> 建议首先阅读 [Intune App SDK 入门指南](intune-app-sdk-get-started.md)一文，该文章介绍了如何在每个受支持的平台准备集成。

用于 iOS 的 Microsoft Intune App SDK 支持将 Intune 应用保护策略（也称为 APP 或 MAM 策略）集成到本机 iOS 应用中。 启用了 MAM 的应用程序是指与 Intune App SDK 集成的应用程序。 Intune 主动管理移动应用时，IT 管理员可将应用保护策略部署到该应用。

## <a name="prerequisites"></a>先决条件

* 需要运行 OS X 10.8.5 或更高版本并安装了 Xcode 8 或更高版本的 Mac OS 计算机。

* 应用必须适用于 iOS 9 或更高版本。

* 查看[用于 iOS 的 Intune App SDK 许可条款](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20for%20iOS%20.pdf)。 打印并保留一份许可条款副本，留作记录。 下载和使用用于 iOS 的 Intune App SDK 即表示你同意这些许可条款。  如果不接受这些条款，请不要使用此软件。

* 在 [GitHub](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios) 上下载用于 iOS 的 Intune App SDK 的文件。

## <a name="whats-in-the-sdk"></a>SDK 包含什么

用于 iOS 的 Intune App SDK 包括一个静态库、资源文件、API 标头、一个调试设置 .plist 文件和一个配置器工具。 移动应用可能只包含资源文件，并以静态方式链接到库，以便实施大多数策略。 高级的 Intune MAM 功能是通过 API 来实现的。

本指南介绍了以下用于 iOS 的 Intune App SDK 组件的用法：

* libIntuneMAM.a：Intune App SDK 静态库。 如果应用不使用扩展，请将此库链接到项目，为 Intune 移动应用管理启用应用。

* IntuneMAM.framework：Intune App SDK 框架。 将此框架链接到项目，为 Intune 移动应用管理启用应用。 如果应用使用扩展，则使用框架而不是静态库，使项目不会创建多个静态库副本。

* IntuneMAMResources.bundle：一个资源包，包含 SDK 所依赖的资源。

* 标头：用于公开 Intune App SDK API。 如果你使用 API，则需要包括包含该 API 的标头文件。 以下标头文件包括启用 Intune App SDK 的功能所需的 API 函数调用：

    * IntuneMAMAsyncResult.h
    * IntuneMAMDataProtectionInfo.h
    * IntuneMAMDataProtectionManager.h
    * IntuneMAMFileProtectionInfo.h
    * IntuneMAMFileProtectionManager.h
    * IntuneMAMPolicyDelegate.h
    * IntuneMAMLogger.h


## <a name="how-the-intune-app-sdk-works"></a>Intune App SDK 的使用方式

Intune App SDK for iOS 的目标是在最大程度上减少代码更改的情况下将管理功能添加到 iOS 应用中。 代码更改越少，面市时间就越短，同时不影响移动应用程序的一致性和稳定性。


## <a name="build-the-sdk-into-your-mobile-app"></a>将 SDK 构建到移动应用中

若要启用 Intune App SDK，请执行以下步骤：

1. 选项 1（推荐）：将 `IntuneMAM.framework` 链接到项目。 将 `IntuneMAM.framework` 拖动到项目目标的“链接的框架和库”列表中。

    > [!NOTE]
    > 如果使用框架，必须在将应用提交到 App Store 之前，从通用框架中手动删除模拟器体系结构。 有关详细信息，请参阅[将应用提交到 App Store](#Submit-your-app-to-the-App-Store)。

2. 选项 2：链接到 `libIntuneMAM.a` 库。 将 `libIntuneMAM.a` 库拖动到项目目标的“链接的框架和库”列表中。

    ![Intune App SDK iOS：链接的框架和库](../media/intune-app-sdk-ios-linked-frameworks-and-libraries.png)

    > [!NOTE]
    > 如果计划将应用发布到 App Store，请使用 `libIntuneMAM.a` 的发行版，而不是调试版。 发行版位于“release”文件夹中。 调试版包含有助于排除 Intune App SDK 问题的详细输出。

    将 `-force_load {PATH_TO_LIB}/libIntuneMAM.a` 添加到以下任一项，并将 `{PATH_TO_LIB}` 替换为 Intune App SDK 的位置：
      * 项目的 `OTHER_LDFLAGS` 生成配置设置
      * UI 的“其他链接器标志”

        > [!NOTE]
        > 若要查找 `PATH_TO_LIB`，请选择文件 `libIntuneMAM.a`，并从“文件”菜单中选择“获取信息”。 复制并粘贴“信息”窗口中“常规”部分的“位置”信息（路径）。

3. 将以下 iOS 框架添加到项目：
    * MessageUI.framework
    * Security.framework
    * MobileCoreServices.framework
    * SystemConfiguration.framework
    * libsqlite3.tbd
    * libc++.tbd
    * ImageIO.framework
    * LocalAuthentication.framework
    * AudioToolbox.framework


4. 将 `IntuneMAMResources.bundle` 资源包添加到项目，方法是在“生成阶段”将此资源包拖动到“复制资源包”下方。

    ![Intune App SDK iOS：复制包资源](../media/intune-app-sdk-ios-copy-bundle-resources.png)

5. 如果移动应用的 Info.plist 文件中定义了主要 Nib 或 Storyboard 文件，请剪切“Main Storyboard”或“Main Nib”字段。 在 Info.plist 中，使用以下键名称（若适用）在名为 IntuneMAMSettings  的新字典下方粘贴这些字段及其对应值：
    * MainStoryboardFile
    * MainStoryboardFile~ipad
    * MainNibFile
    * MainNibFile ~ ipad
    > [!NOTE]
  > 如果移动应用的 Info.plist 文件中未定义主要 Nib 或 Storyboard 文件，则不需要这些设置。

    可使用原始格式查看 Info.plist 文件（目的是查看键名称），方法是右键单击文档正文的任意位置，然后将查看类型更改为“显示原始键/值”。

6. 选择每个项目目标的“功能”并启用“密钥链共享”开关，启用密钥链共享（如果尚未启用）。 需要启用密钥链共享才能继续执行下一步。

  > [!NOTE]
    > 预配的配置文件需要支持新的密钥链共享值。 keychain 访问组应支持通配符。 可通过以下方法进行验证：在文本编辑器中打开 .mobileprovision 文件，搜索“keychain-access-groups”，确保其中包含通配符。 例如：
    ```xml
    <key>keychain-access-groups</key>
    <array>
    <string>YOURBUNDLESEEDID.*</string>
    </array>
    ```

7. 启用密钥链共享后，请按照以下步骤创建单独的访问组，以便 Intune App SDK 可在其中存储数据。 可使用 UI 或使用授权文件创建密钥链访问组。 如果使用 UI 创建密钥链访问组，请务必按照以下步骤操作：

    1. 如果移动应用未定义任何密钥链访问组，请将此应用的程序包 ID 添加为第一个组。

    2. 将共享密钥链组 `com.microsoft.intune.mam` 添加到现有访问组。 Intune App SDK 使用此访问组来存储数据。

    3. 将 `com.microsoft.adalcache` 添加到现有访问组。

        4. 将 `com.microsoft.workplacejoin` 添加到现有访问组。
            ![Intune App SDK iOS：密钥链共享](../media/intune-app-sdk-ios-keychain-sharing.png)

      5. 如果使用授权文件创建密钥链访问组，请在授权文件的密钥链访问组前面添加 `$(AppIdentifierPrefix)`。 例如：

            * `$(AppIdentifierPrefix)com.microsoft.intune.mam`
            * `$(AppIdentifierPrefix)com.microsoft.adalcache`

    > [!NOTE]
    > 授权文件是一个 XML 文件，它对于移动应用程序是唯一的。 用于在 iOS 应用中指定特殊权限和功能。

7. 如果应用的 Info.plist 文件中定义了 URL 方案，请为每个 URL 方案添加另一个具有 `-intunemam` 后缀的方案。

8. 对于 iOS 9+ 上开发的移动应用，需要在应用的 Info.plist 文件的 `LSApplicationQueriesSchemes` 数组中包括应用传递到 `UIApplication canOpenURL` 的每个协议。 此外，对于每个列出的协议，添加新的协议，并对新协议追加 `-intunemam`。 还必须在此数组中包括 `http-intunemam`、`https-intunemam` 和 `ms-outlook-intunemam`。

9. 如果应用在其授权中定义了应用组，则将这些组作为字符串数组添加到 `AppGroupIdentifiers` 键下面的 IntuneMAMSettings 字典中。



## <a name="configure-azure-active-directory-authentication-library-adal"></a>配置 Azure Active Directory Authentication Library (ADAL)

Intune App SDK 使用 [Azure Active Directory Authentication Library](https://github.com/AzureAD/azure-activedirectory-library-for-objc) 进行身份验证和条件启动。 它还依赖 ADAL 向 MAM 服务注册用户标识，用于不含设备注册方案的管理。

通常，ADAL 要求应用注册 Azure Active Directory (AAD) 并获得唯一的 ID（客户端 ID）和其他标识符，以保护授予该应用的令牌。 除非另有规定，否则连接 Azure AD 时，Intune App SDK 使用默认的注册值。  

如果应用已使用 ADAL 对用户进行身份验证，则该应用必须使用其现有的注册值，并替代 Intune App SDK 默认值。 这可确保不会提示两次让用户进行身份验证（一次由 Intune App SDK，一次由应用）。

### <a name="recommendations"></a>建议

建议应用链接到其主分支上的[最新版 ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-objc/releases)。 Intune App SDK 目前使用 ADAL 的代理分支，以支持需要条件访问的应用。 （因此，这些应用依赖于 Microsoft Authenticator 应用。）但 SDK 仍与 ADAL 的主分支兼容。 使用适合应用的分支。

### <a name="link-to-adal-binaries"></a>链接到 ADAL 二进制文件

请按照以下步骤将应用链接到 ADAL 二进制文件：

1. 从 GitHub 下载[适用于 Objective-C 的 Azure Active Directory Authentication Library (ADAL)](https://github.com/AzureAD/azure-activedirectory-library-for-objc)，然后遵循有关如何使用 Git 子模块或 CocoaPods 下载 ADAL 的[说明](https://github.com/AzureAD/azure-activedirectory-library-for-objc/blob/master/README.md)执行操作。

2. 在项目中包括 `ADALiOSBundle.bundle` 资源包，方法是在“生成阶段”将此资源包拖动到“复制资源包”下方。

3. 将 `-force_load {PATH_TO_LIB}/libADALiOS.a` 添加到项目的 `OTHER_LDFLAGS` 生成配置设置或 UI 的“其他链接器标志”中。 应将 `PATH_TO_LIB` 替换为 ADAL 二进制文件位置。



### <a name="share-the-adal-token-cache-with-other-apps-signed-with-the-same-provisioning-profile"></a>与其他使用相同预配配置文件签名的应用共享 ADAL 令牌缓存？**

如果要在使用相同预配配置文件签名的应用之间共享 ADAL 令牌，请按照以下说明执行操作：

1. 如果应用未定义任何密钥链访问组，请将此应用的程序包 ID 添加为第一个组。

2. 在密钥链权利中添加 `com.microsoft.adalcache` 和 `com.microsoft.workplacejoin` 访问组，启用 ADAL 单一登录 (SSO)。

3. 如果要显式设置 ADAL 共享缓存密钥链组，请务必将其设置为 `<app_id_prefix>.com.microsoft.adalcache`。 除非替代 ADAL，否则它将完成此设置。 如果希望指定一个自定义密钥链组来替代 `com.microsoft.adalcache`，请在“IntuneMAMSettings”下的 Info.plist 文件中使用键 `ADALCacheKeychainGroupOverride` 进行指定。

### <a name="configure-adal-settings-for-the-intune-app-sdk"></a>配置 Intune App SDK 的 ADAL 设置

如果应用已使用 ADAL 进行身份验证并拥有自己的 ADAL 设置，则可强制 Intune App SDK 在对 Azure Active Directory 进行身份验证时使用相同的设置。 这可确保应用不会两次提示用户进行身份验证。 请参阅 [Intune App SDK 的配置设置](#configure-settings-for-the-intune-app-sdk)，了解有关填充以下设置的信息：  

* ADALClientId
* ADALAuthority
* ADALRedirectUri
* ADALRedirectScheme
* ADALCacheKeychainGroupOverride

如果应用已使用 ADAL，则需要以下配置：

1. 在项目的 Info.plist 文件的 IntuneMAMSettings 字典（键名称为 `ADALClientId`）下，指定要用于 ADAL 调用的客户端 ID。

2. 另外，在键名称为 `ADALAuthority` 的 IntuneMAMSettings 字典下指定 Azure AD 颁发机构。

3. 同时，在键名称为 `ADALRedirectUri` 的 IntuneMAMSettings 字典下指定要用于 ADAL 调用的重定向 URI。 可能还需根据应用的重定向 URI 格式指定 `ADALRedirectScheme`。


此外，可使用运行时特定于租户的 URL 替代 Azure AD 颁发机构 URL。 为此，只需在 `IntuneMAMPolicyManager` 实例上设置 `aadAuthorityUriOverride` 属性。

> [!NOTE]
> 对于[无需设备注册的应用](#App-protection-policy-without-device-enrollment)，必须设置 AAD 颁发机构 URL，以便 SDK 可以重复使用应用提取的 ADAL 刷新令牌。

SDK 会继续使用此颁发机构 URL 进行策略刷新和任何后续注册请求，除非该值被清除或更改。  因此，请务必在托管用户注销此应用后清除该值，并在新托管用户登录时重置该值。

### <a name="if-your-app-does-not-use-adal"></a>应用不使用 ADAL 的情况

如果应用不使用 ADAL，Intune App SDK 会为 ADAL 参数提供默认值，并处理针对 Azure AD 的身份验证。 无需为上面列出的 ADAL 设置指定任何值。

## <a name="app-protection-policy-without-device-enrollment"></a>无需设备注册的应用保护策略

### <a name="overview"></a>概述
无需设备注册的 Intune 应用保护策略，也称为 APP-WE 或 MAM-WE，允许 Intune 管理应用而无需设备注册 Intune 移动设备管理 (MDM)。 若要支持这一新功能，应用必须注册用户帐户以便进行管理。 若要使用新 API，请执行以下步骤：

1. 使用 Intune App SDK 的最新版本，无论设备是否注册，该版本都支持应用管理。

2. 将 IntuneMAMEnrollment.h 添加到任何要调用 API 的文件。

### <a name="register-user-accounts"></a>注册用户帐户

如果应用代表指定的用户帐户向 APP-WE 服务注册，则该应用可从 Intune 服务接收应用保护策略。 应用负责向 SDK 注册任何新登录的用户。 新用户帐户经身份验证后，应用应调用 Headers/IntuneMAMEnrollment.h 中的 `registerAndEnrollAccount` 方法：

```objc
/**


 *  This method will add the account to the list of registered accounts.
 *  An enrollment request will immediately be started.
 *  @param identity The UPN of the account to be registered with the SDK
 */

(void)registerAndEnrollAccount:(NSString *)identity;

```
通过调用 `registerAndEnrollAccount` 方法，SDK 会注册用户帐户并尝试代表此帐户注册应用。 如果注册由于任何原因失败，SDK 会在 24 小时后自动重试注册。 出于调试目的，应用可通过委托接收有关任何注册请求结果的通知。

调用此 API 后，应用可继续正常工作。 如果注册成功，SDK 会通知用户需要重启应用。 此时，用户可立即重启应用。

### <a name="deregister-user-accounts"></a>取消注册用户帐户

应用应先从 SDK 取消注册用户，然后再注销该用户。 这可确保：

1. 不再对用户的帐户进行注册重试。

2. 删除应用保护策略。

3. 如果应用启动选择性擦除（可选），则会删除任何公司数据。

注销用户之前，应用应调用 `Headers/IntuneMAMEnrollment.h` 中的以下 API：

```objc
/*
 *  This method will remove the provided account from the list of
 *  registered accounts.  Once removed, if the account has enrolled
 *  the application, the account will be un-enrolled.
 *  @note In the case where an un-enroll is required, this method will block
 *  until the Intune MAM AAD token is acquired, then return.  This method must be called before  
 *  the user is removed from the application (so that required AAD tokens are not purged
 *  before this method is called).
 *  @param identity The UPN of the account to be removed.
 *  @param doWipe   If YES, a selective wipe if the account is un-enrolled
 */

(void)deRegisterAndUnenrollAccount:(NSString *)identity withWipe:(BOOL)doWipe;
```

删除用户帐户的 Azure AD 令牌之前，必须调用此方法。 SDK 需要用户帐户的 AAD 令牌才能代表用户向 APP-WE 服务发出特定请求。

如果应用要自行删除用户的公司数据，则可将 `doWipe` 标志设置为 false。 否则，应用可让 SDK 启动选择性擦除。 这会导致调用应用的选择性擦除委托。

```objc
[[IntuneMAMEnrollmentManager instance] deRegisterAndUnenrollAccount:@”user@foo.com” withWipe:YES];
```

### <a name="apps-that-do-not-use-adal"></a>不使用 ADAL 的应用

未使用 ADAL 注册用户的应用仍可从 Intune 服务接收应用保护策略，方法是调用 API 使 SDK 处理该身份验证。 应用尚未使用 Azure AD 对用户进行身份验证，但仍需要检索应用保护策略以帮助保护数据时，应使用此方法。 例如，正在使用另一个身份验证服务进行应用注册时，或应用完全不支持注册时。 为此，应用程序应调用 Headers/IntuneMAMEnrollment.h 中的 `loginAndEnrollAccount` 方法：

```objc
/**
 *  Creates an enrollment request which is started immediately.
 *  If no token can be retrieved for the identity, the user will be prompted
 *  to enter their credentials, after which enrollment will be retried.
 *  @param identity The UPN of the account to be logged in and enrolled.
 */
 (void)loginAndEnrollAccount: (NSString *)identity;

```

通过调用此方法，如果找不到任何现有令牌，SDK 会提示用户输入凭据。 随后，SDK 将尝试代表提供的用户帐户向 APP-WE 服务注册应用。 可使用作为标识的“nil”调用此方法。 在此情况下，SDK 会使用设备上现有的管理用户进行注册，或在找不到任何现有用户时提示用户输入用户名。

如果注册失败，应用应考虑在之后某一时间再次调用此 API，具体取决于失败的详细信息。 应用可通过委托接收有关任何注册请求结果的[通知](#Status-result-and-debug-notifications)。

调用此 API 后，应用可继续正常工作。 如果注册成功，SDK 会通知用户需要重启应用。

## <a name="status-result-and-debug-notifications"></a>状态、结果和调试通知

应用可接收有关向 Intune MAM 服务发出的以下请求的状态、结果和调试通知：

 - 注册请求
 - 策略更新请求
 - 取消注册请求

通过 `Headers/IntuneMAMEnrollmentDelegate.h` 中的委托方法显示通知：

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

- 与请求关联的帐户的标识
- 指示请求结果的状态代码
- 带有状态代码说明的错误字符串
- 一个 `NSError` 对象

此对象连同可返回的特定状态代码在 `IntuneMAMEnrollmentStatus.h` 中进行定义。


### <a name="sample-code"></a>代码示例

以下是委托方法的示例实现：

```objc
- (void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus *)status
{
    NSLog(@"enrollment result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}


- (void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus *)status
{
    NSLog(@"policy check-in result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus *)status
{
    NSLog(@"un-enroll result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

```

## <a name="app-restart"></a>应用重启

应用首次接收应用保护策略时必须重启才能应用所需挂钩。 为了通知应用需要重启，SDK 在 Headers/IntuneMAMPolicyDelegate.h 中提供了委托方法。

```objc
 - (BOOL) restartApplication
```
此方法的返回值会告诉 SDK 应用程序是否必须处理所需的重启：   

 - 如果返回 true，则应用程序必须处理重启。   

 - 如果返回 false，则 SDK 会在此方法返回后重启应用程序。 SDK 会立即显示一个对话框，告知用户重启应用程序。

## <a name="customize-your-apps-behavior"></a>自定义应用行为

可调用 Intune App SDK 的几个 API 获取有关部署到应用的 Intune 应用保护策略的信息。 可使用此数据自定义应用行为。 大多数应用保护策略设置都由 SDK（而不是应用程序）自动强制执行。 应用应实现的唯一设置是“另存为”控件。

### <a name="get-app-protection-policy"></a>获取应用保护策略

#### <a name="intunemampolicymanagerh"></a>IntuneMAMPolicyManager.h
IntuneMAMPolicyManager 类可公开部署到应用程序的 Intune 应用保护策略。 尤其是，它可公开可用于[启用多身份标识](#-enable-multi-identity-optional)的 API。

#### <a name="intunemampolicyh"></a>IntuneMAMPolicy.h
IntuneMAMPolicy 类可公开部署到应用程序的 Intune 应用保护策略。 此类中公开的大多数策略设置都由 SDK 强制执行，但可根据策略设置的强制执行方式自定义应用行为。

此类可公开实现“另存为”控件所需的一些 API（详见下一部分）。

### <a name="implement-save-as-controls"></a>实现“另存为”控件

通过 Intune，IT 管理员可选择托管应用保存数据的存储位置。 应用可使用在 IntuneMAMPolicy.h 中定义的 isSaveToAllowedForLocation，针对允许的存储位置查询 Intune App SDK。

将托管数据保存到云存储或本地位置前，应用必须使用 isSaveToAllowedForLocation API 进行检查，了解 IT 管理员是否允许数据保存在此处。

使用 isSaveToAllowedForLocation API 时，应用必须传入用于存储位置的 UPN（如可用）。

#### <a name="supported-save-locations"></a>支持的保存位置

isSaveToAllowedForLocation API 提供常量来检查 IT 管理员是否允许将数据保存到 IntuneMAMPolicy.h 中定义的以下位置：

* IntuneMAMSaveLocationOther
* IntuneMAMSaveLocationOneDriveForBusiness
* IntuneMAMSaveLocationSharePoint
* IntuneMAMSaveLocationLocalDrive

应用应使用 isSaveToAllowedForLocation API 中的常量来检查是否可将数据保存到“托管”（如 OneDrive for Business）或“个人”位置。 此外，应用无法确定是“托管”还是“个人”位置时，应使用该 API。

`IntuneMAMSaveLocationOther` 常量代表已知为“个人”的位置。

如果应用将数据保存到本地设备上的任何位置，应使用 `IntuneMAMSaveLocationLocalDrive` 常量。

## <a name="configure-settings-for-the-intune-app-sdk"></a>配置 Intune App SDK 设置

可使用应用程序的 Info.plist 文件中的 IntuneMAMSettings 字典设置和配置 Intune App SDK。 如果 Info.plist 文件中未显示 IntuneMAMSettings 字典，则应在应用的 Info.plist 中创建字段名称为“IntuneMAMSettings”的字典。

在 IntuneMAMSettings 字典下，可添加配置设置的键/值行来配置 SDK。 下表列出了所有支持的设置。

其中的一些设置可能已在前面各部分中提及，一些设置则不适用于所有应用。

设置  | 类型  | 定义 | 是否必需？
--       |  --   |   --       |  --
ADALClientId  | 字符串  | 应用的 Azure AD 客户端标识符。 | 应用使用 ADAL 时必需。 |
ADALAuthority | 字符串 | 应用使用的 Azure AD 颁发机构。 应使用自己的环境，其中已配置 AAD 帐户。 | 应用使用 ADAL 时必需。 如果此值不存在，则使用 Intune 默认值。|
ADALRedirectUri  | 字符串  | 应用的 Azure AD 重定向 URI。 | 如果应用使用 ADAL，则需要 ADALRedirectUri 或 ADALRedirectScheme。  |
ADALRedirectScheme  | 字符串  | 应用的 Azure AD 重定向方案。 如果应用程序的重定向 URI 为 `scheme://bundle_id` 格式，则它可用于代替 ADALRedirectUri。 | 如果应用使用 ADAL，则需要 ADALRedirectUri 或 ADALRedirectScheme。 |
ADALLogOverrideDisabled | 布尔值  | 指定 SDK 是否会将所有 ADAL 日志（包括应用的现有 ADAL 调用）路由到其自己的日志文件。 默认值为 NO。 如果应用要设置其自己的 ADAL 日志回调，则设置为“是”。 | 可选。 |
ADALCacheKeychainGroupOverride | 字符串  | 指定要用于 ADAL 缓存而不是“com.microsoft.adalcache”的密钥链组。 请注意，这并不包含应用 ID 前缀。 这将作为运行时所提供字符串的前缀。 | 可选。 |
AppGroupIdentifiers | 字符串数组  | 应用的授权 com.apple.security.application 组部分的应用组数组。 | 如果应用使用应用组，则需要此设置。 |
ContainingAppBundleId | 字符串 | 指定扩展的包含应用程序的程序包 ID。 | iOS 扩展需要此设置。 |
DebugSettingsEnabled| 布尔值 | 如果设置为“是”，则可应用“设置”包中的测试策略。 启用此设置时，不应提供应用程序。 | 可选。 |
MainNibFile<br>MainNibFile ~ ipad  | 字符串  | 此设置应包含应用程序的主要 nib 文件名。  | 如果应用程序在 Info.plist 中定义了 MainNibFile，则需要此设置。 |
MainStoryboardFile<br>MainStoryboardFile~ipad  | 字符串  | 此设置应包含应用程序的主要 storyboard 文件名。 | 如果应用程序在 info.plist 中定义了 UIMainStoryboardFile，则需要此设置。 |
MAMPolicyRequired| 布尔值| 指定应用没有 Intune 应用保护策略时，是否要阻止应用启动。 默认值为 NO。 <br><br> 请注意：MAMPolicyRequired 设置为“是”时，无法将应用提交到 App Store。 | 可选。 |
MAMPolicyWarnAbsent | 布尔值| 指定应用没有 Intune 应用保护策略时，是否在启动期间警告用户。 请注意：此设置设为“是”时，无法将应用提交到商店。 | 可选。 |
MultiIdentity | 布尔值| 指定应用是否识别多身份标识。 | 可选。 |
SplashIconFile <br>SplashIconFile~ipad | 字符串  | 指定 Intune 初始屏幕（启动）图标文件。 | 可选。 |
SplashDuration | 数字 | 应用程序启动时显示 Intune 启动屏幕的最小时间（以秒为单位）。 默认值为 1.5。 | 可选。 |
BackgroundColor| 字符串| 指定启动屏幕和 PIN 屏幕的背景色。 接受 #XXXXXX 格式的十六进制 RGB 字符串，其中 X 的范围可以为 0-9 或 A-F。 可忽略井号。   | 可选。 默认为浅灰色。 |
ForegroundColor| 字符串| 指定启动屏幕和 PIN 屏幕的前景色，如文本颜色。 接受 #XXXXXX 格式的十六进制 RGB 字符串，其中 X 的范围可以为 0-9 或 A-F。 可忽略井号。  | 可选。 默认为黑色。 |
AccentColor | 字符串| 指定 PIN 屏幕的主题色，例如按钮文本颜色和框高亮颜色。 接受 #XXXXXX 格式的十六进制 RGB 字符串，其中 X 的范围可以为 0-9 或 A-F。 可忽略井号。| 可选。 默认为系统蓝色。 |
MAMTelemetryDisabled| 布尔值| 指定 SDK 是否会将任何遥测数据发送到其后端。| 可选。 |

> [!NOTE]
> 如果会将应用发布到 App Store，根据 App Store 标准，必须将 `MAMPolicyRequired` 设置为“否”。

## <a name="telemetry"></a>遥测技术

默认情况下，用于 iOS 的 Intune App SDK 会记录以下使用事件的遥测数据。 会将此数据发送到 Microsoft Intune。

* 应用启动：用于帮助 Microsoft Intune 按照管理类型（含 MDM 的 MAM、不含 MDM 注册的 MAM 等）了解已启用 MAM 的应用使用情况。

* 注册调用：用于帮助 Microsoft Intune 了解客户端启动的注册调用的成功率和其他性能指标。

> [!NOTE]
> 如果选择不将 Intune App SDK 遥测数据从移动应用程序发送到 Microsoft Intune，则必须禁用 Intune App SDK 遥测数据捕获功能。 在 IntuneMAMSettings 字典中将属性 `MAMTelemetryDisabled` 设置为“是”。

## <a name="enable-multi-identity-optional"></a>启用多身份标识（可选）

默认情况下，SDK 会将策略作为一个整体应用到该应用。 多身份标识是一项 MAM 功能，启用后可在每个标识级别上应用策略。 这需要比其他 MAM 功能还要多的应用参与。

应用必须在其意图更改现用身份时通知应用 SDK。 SDK 也会在需要标识更改时通知应用。 目前，仅支持一个托管标识。 用户注册设备或应用后，SDK 会使用此标识并将其视为主要托管标识。 应用中的其他用户会被视为具有不受限策略设置的非托管标识。

请注意，标识简单地定义为字符串。 标识不区分大小写。 向 SDK 请求标识可能不会返回设置标识时最初使用的相同大小写。

### <a name="identity-overview"></a>标识概述

标识就是帐户的用户名（例如 user@contoso.com）。 开发人员可在以下级别上设置应用的标识：

* 进程标识：设置进程级标识，并且主要用于单一标识应用程序。 此标识会影响所有任务、文件和 UI。

* UI 标识：确定应用于主线程上 UI 任务的策略，例如剪切/复制/粘贴、PIN、身份验证和数据共享。 UI 标识不会影响文件任务，如加密和备份。

* 线程标识：影响应用于当前线程的策略。 此标识会影响所有任务、文件和 UI。

不论用户是否为托管，应用都会负责设置合适的标识。

在任何时候，每个线程都具有用于 UI 任务和文件任务的有效标识。 这是确定应应用哪些策略（如有）的标识。 如果此标识为“无标识”或用户不是托管的，则不会应用任何策略。 下图显示如何确定有效的标识。

  ![Intune App SDK iOS：链接的框架和库](../media/intune-app-sdk/ios-thread-identities.png)

### <a name="thread-queues"></a>线程队列

应用通常将异步和同步任务调度到线程队列。 SDK 截获 Grand Central Dispatch (GCD) 调用，并将当前线程标识与调度任务相关联。 完成任务时，SDK 会临时将线程标识更改为与任务关联的标识，再完成任务，然后还原原始线程标识。


由于 `NSOperationQueue` 基于 GCD 之上，`NSOperations` 会在任务被添加到 `NSOperationQueue` 的同时运行线程标识。 `NSOperations` 或直接通过 GCD 调度的函数还可在当前线程标识运行时对其进行更改。 此标识会替代继承自调度线程的标识。

### <a name="file-owner"></a>文件所有者

SDK 跟踪本地文件所有者的标识，并相应地应用策略。 文件所有者是在创建文件时或在截断模式下打开文件时建立的。 所有者被设置为执行任务的线程的有效文件任务标识。

应用也可使用 `IntuneMAMFilePolicyManager` 显式设置文件所有者标识。 应用可使用 `IntuneMAMFilePolicyManager` 在显示该文件内容之前检索文件所有者和设置 UI 标识。

### <a name="shared-data"></a>共享数据

如果应用创建包含同时来自托管和非托管用户的数据的文件，则应用负责加密托管用户的数据。 可通过使用 `IntuneMAMDataProtectionManager` 中的 `protect` 和 `unprotect` API 加密数据。

`protect` 方法接受的标识可以是托管用户，也可以是非托管用户。 如果为托管用户，则会对数据加密。 如果为非托管用户，则会将编码有标识的标头添加到数据中，而不会对数据加密。 可使用 `protectionInfo` 方法检索数据的所有者。

### <a name="share-extensions"></a>共享扩展

如果应用包含共享扩展，则可使用 `IntuneMAMDataProtectionManager` 中的 `protectionInfoForItemProvider` 方法检索要共享项的所有者。 如果共享项为文件，则 SDK 会处理设置文件所有者。 如果共享项为数据，则应用负责设置文件所有者（如果此数据永久保存到一个文件中），并负责在 UI 中显示此数据之前调用 `setUIPolicyIdentity` API。

### <a name="turning-on-multi-identity"></a>启用多身份标识

默认情况下，应用被视为单一标识。 SDK 将进程标识设置为已注册的用户。 若要启用多身份标识支持，需要将名为 `MultiIdentity` 且值为“是”的布尔设置添加到应用的 Info.plist 文件中的 IntuneMAMSettings 字典。

> [!NOTE]
> 启用多身份标识后，进程标识、UI 标识和线程标识设置为 nil。 应用负责对其进行适当设置。

### <a name="switching-identities"></a>切换标识

* 应用启动标识切换：

    在启动时，多身份标识应用被视为在未知的非托管帐户下运行。 条件启动 UI 不会运行，且不会在该应用上强制执行任何策略。 应用负责在标识需要更改时通知 SDK。 通常，当应用要显示特定用户帐户的数据时会发出通知。

    例如，用户尝试打开文档、邮箱或笔记本中的标签页时。 应用需在实际打开文件、邮箱或标签页之前通知 SDK。 可通过 `IntuneMAMPolicyManager` 中的 `setUIPolicyIdentity` 实现。 不论用户是否为托管都应调用此 API。 如果用户为托管用户，则 SDK 会执行条件启动检查，例如破解检测、PIN 和身份验证。

    标识切换的结果会通过完成处理程序异步返回到应用。 应用应推迟打开文档、邮箱或标签页，直到返回成功结果代码。 如果标识切换失败，应用应取消任务。

* SDK 启动标识切换：

    有时，SDK 需要求应用切换到特定标识。 多身份标识应用必须实现 `IntuneMAMPolicyDelegate` 中的 `identitySwitchRequired` 方法来处理此请求。

    调用此方法时，如果应用能够处理切换到特定标识的请求，则应将 `IntuneMAMAddIdentityResultSuccess` 传递到完成处理程序。 如果无法处理切换标识，应用应将 `IntuneMAMAddIdentityResultFailed` 传递到完成处理程序。

    应用无需调用 `setUIPolicyIdentity` 来响应此调用。 如果 SDK 需要应用切换到非托管用户帐户，则空字符串将传递到 `identitySwitchRequired` 调用。

* 选择性擦除：

    应用为选择性擦除时，SDK 会调用 `IntuneMAMPolicyDelegate` 中的 `wipeDataForAccount` 方法。 应用负责删除指定用户的帐户以及与其关联的任何数据。 如果应用从 `wipeDataForAccount` 调用返回 FALSE，则 SDK 能够删除用户拥有的全部文件。

    请注意，需从后台线程调用此方法。 除非已删除用户的所有数据，否则应用不会返回任何值（文件除外，应用会返回 FALSE）。

## <a name="test-app-protection-policy-settings-in-xcode"></a>测试 Xcode 中的应用保护策略设置

在手动测试生产中的启用 Intune 的应用之前，可在 Xcode 中使用 Settings.bundle 文件。 这样，无需连接 Intune 即可设置应用保护策略进行测试。

### <a name="enable-policy-testing"></a>启用策略测试

请按照以下步骤启用 Xcode 中的策略测试：

1. 请务必在调试版本中执行。 右键单击项目中的顶层文件夹，添加 Settings.bundle 文件。 从菜单中选择“添加” > “新建文件”。 在“资源”下选择“设置包”模板。

2.  将以下块复制到用于调试版本的 Settings.bundle/Root.plist 文件中：
    ```xml
    <key>PreferenceSpecifiers</key>
    <array>
        <dict>
            <key>Type</key>
            <string>PSChildPaneSpecifier</string>
            <key>Title</key>
            <string>MDM Debug Settings</string>
            <key>Key</key>
            <string>MAMDebugSettings</string>
            <key>File</key>
            <string>MAMDebugSettings</string>
        </dict>
    </array>
    ```

3. 在应用的 Info.plist 的 IntuneMAMSettings 字典中，添加一个名为“DebugSettingsEnabled”的布尔值。 将 DebugSettingsEnabled 的值设置为“是”。



### <a name="app-protection-policy-settings"></a>应用保护策略设置

下表介绍了使用 MAMDebugSettings.plist 进行测试的应用保护策略设置。 若要打开设置，请将其添加到 MAMDebugSettings.plist 中。

| 策略设置名称 | 描述 | 可能的值 |
| -- | -- | -- |
| AccessRecheckOfflineTimeout | 启用身份验证后，Intune 阻止应用启动或恢复之前应用处于脱机状态的时长（以分钟为单位）。 | 任何大于 0 的整数 |
|    AccessRecheckOnlineTimeout | 启动或恢复时（前提条件是启用了身份验证或 PIN 以供访问），系统提示用户输入 PIN 或进行身份验证之前应用可运行的时长（以分钟为单位）。 | 任何大于 0 的整数 |
| AppSharingFromLevel | 指定此应用可接受哪些应用的数据。 | 0 = |
## <a name="ios-best-practices"></a>iOS 最佳做法

以下是针对 iOS 进行开发时建议采用的最佳做法：

* iOS 文件系统区分大小写。 确保文件名大小写正确，如 `libIntuneMAM.a` 和 `IntuneMAMResources.bundle`。

* 如果 Xcode 查找 `libIntuneMAM.a` 时遇到问题，可通过将此库的路径添加到链接器搜索路径来解决此问题。

## <a name="faqs"></a>常见问题


是否所有 API 都可通过本机 Swift 或 Objective-C 和 Swift 互操作性进行寻址？

Intune App SDK API 仅可采用 Objective-C 且不支持本机 Swift。 Objective-C 必须与 Swift 具有互操作性。


应用程序的所有用户是否都需要向 APP-WE 服务注册？

否。 实际上，只有工作或学校帐户需要向 Intune App SDK 注册。 应用负责确定使用的帐户是否为工作或学校帐户。   

已登录到应用程序的用户呢？他们是否需要注册？

应用程序负责在用户成功通过身份验证后注册用户。 此外，应用程序还负责注册任何在应用程序具备 MDM Less MAM 功能之前便已存在的现有帐户。   

为此，应用程序应使用 `registeredAccounts:` 方法。 此方法会返回 NSDictionary，其中包含所有已注册 Intune MAM 服务的帐户。 如果应用程序中没有任何现有帐户存在于列表中，则应用程序应通过 `registerAndEnrollAccount:` 注册这些帐户。

SDK 多长时间重试一次注册？

SDK 会在上次注册失败后每隔 24 小时自动重试。 SDK 这样做是为了确保：即使用户的组织在用户登录应用程序后启用了 MAM，用户也能成功注册并接收策略。

SDK 会在检测到用户已成功注册该应用程序后停止重试。 这是因为只有 1 位用户可以在特定时间注册应用程序。 如果用户未注册，则同样将在 24 小时间隔后再次开始重试。

为何用户需要取消注册？

SDK 将在后台定期执行以下操作：

 - 如果应用程序尚未注册，SDK 会每隔 24 小时尝试注册所有已注册的帐户。
 - 如果应用程序已注册，SDK 会每 8 小时检查一次应用保护策略更新。

取消注册用户会通知 SDK - 用户不再使用该应用程序，并且 SDK 可以停止该用户帐户的任何周期事件。 必要时，这还会触发应用取消注册和选择性擦除。

是否应在取消注册方法中将 doWipe 标志设置为 true？

应在用户注销应用程序之前调用此方法。  如果将用户数据作为注销的一部分从应用程序中删除，则可将 `doWipe` 设置为 false。 但是，如果应用程序未删除用户的数据，则 `doWipe` 应设置为 true，以便 SDK 可删除数据。

是否有其他可以取消注册应用程序的方法？

是，IT 管理员可向应用程序发送选择性擦除命令。 这将取消注册用户，并擦除用户的数据。 SDK 自动处理此方案，并通过取消注册委托方法发送通知。



## <a name="submit-your-app-to-the-app-store"></a>将应用提交到 App Store

Intune App SDK 的静态库和框架版本都是通用的二进制文件。 这意味着它们包含适用于所有设备和模拟器体系结构的代码。 如果应用含有模拟器代码，Apple 会拒绝将其提交到 App Store。 针对仅设备生成的静态库编译时，链接器会自动删除模拟器代码。 请按照以下步骤操作，确保将应用上传到 App Store 之前删除所有模拟器代码。

1. 请确保 `IntuneMAM.framework` 位于桌面上。

2. 运行以下命令：

    ```bash
    lipo ~/Desktop/IntuneMAM.framework/IntuneMAM -remove i386 -remove x86_64 -output ~/Desktop/IntuneMAM.device_only
    ```

    ```bash
    cp ~/Desktop/IntuneMAM.device_only ~/Desktop/IntuneMAM.framework/IntuneMAM
    ```
    第一个命令用于从框架的 DYLIB 文件中删除模拟器体系结构。 第二个命令用于将仅设备 DYLIB 文件复制回框架目录。

