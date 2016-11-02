---
title: "Microsoft Intune App SDK for iOS 开发人员指南 | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6b998728b3db60d10cadbcd34b5412fa76cb586f
ms.openlocfilehash: ddc47ef5846bf448cf0de1e57b527e8ec4c562cc


---

# Microsoft Intune App SDK for iOS 开发人员指南

> [!NOTE]
> 你可能希望首先阅读 [ Intune App SDK 入门指南 ](intune-app-sdk-get-started.md)，该文档介绍了如何为每个受支持的平台上的集成做准备。* 

Microsoft Intune App SDK for iOS 支持将 Intune 移动应用管理 (MAM) 集成到 iOS 应用中。 启用了 MAM 的应用程序是指与 Intune App SDK 集成的应用程序，允许 IT 管理员在通过 Intune 主动管理移动应用时在该应用上部署策略。


# SDK 包含什么 

Intune App SDK for iOS 包括一个静态库、资源文件、API 标头、一个调试设置 plist 和一个配置器工具。 移动应用可能只包含资源文件，并且静态链接到库，以便实施大多数策略。 高级的 Intune MAM 功能是通过 API 来实现的。

本指南将介绍如何使用以下 Intune App SDK for iOS 组件：

* **libIntuneMAM.a**：Intune App SDK 静态库。 如果应用不使用扩展，请将此库链接到项目，为 Intune 移动应用程序管理启用应用。 有关说明可以在“使用 Intune App SDK 生成应用”一节中找到。

* **IntuneMAM.framework**：Intune App SDK 框架。 将此框架链接到项目，为 Intune 移动应用程序管理启用应用。 如果应用使用扩展，则使用框架而不是静态库，使项目不会创建静态库的多个副本。

* **IntuneMAMResources.bundle**：一个资源包，包含 SDK 所依赖的资源。 

* **标头**：用于公开 Intune App SDK API。 如果你使用 API，则需要包括包含该 API 的标头文件。 以下标头文件包括启用 Intune App SDK 的功能所需的 API 函数调用。 
    
    * IntuneMAMAsyncResult.h
    * IntuneMAMDataProtectionInfo.h
    * IntuneMAMDataProtectionManager.h
    * IntuneMAMFileProtectionInfo.h
    * IntuneMAMFileProtectionManager.h
    * IntuneMAMPolicyDelegate.h
    * IntuneMAMLogger.h 


# Intune App SDK 的使用方式

Intune App SDK for iOS 的目标是在最大程度上减少代码更改的情况下将管理功能添加到 iOS 应用中。 代码更改更少，面市时间更短，但依然能保证移动应用程序的一致性和稳定性。 

需要将应用程序链接到静态库，并必须包含资源包。 MAMDebugSettings.plist 文件是可选的，可以包含在此工具包中，以便模拟要应用到应用的 MAM 策略，而无需通过 Microsoft Intune 部署此应用。 此外，在调试版本中，通过 iTunes 文件共享将文件传输到应用的 Documents 目录下，可以应用 MAMDebugSettings.plist 文件中的策略。

# 将 SDK 构建到移动应用中 

完成以下步骤来启用 Intune App SDK：

1. **选项 1**：通过执行以下操作链接到 `libIntuneMAM.a` 库：

    将 `libIntuneMAM.a` 库拖放到项目目标的“链接的框架和库”列表中。
    ![Intune App SDK iOS - 链接的框架和库](../media/intune-app-sdk-ios-linked-frameworks-and-libraries.png) 

    **注意**：如果计划将应用发布到应用商店，请使用 `libIntuneMAM.a` 的发行版，而不是调试版。 发行版将在 "release" 文件夹中。 调试版包含详细的输出，这些输出有助于对 Intune App SDK 的问题进行故障排除。
    
    **选项 2**：将 `IntuneMAM.framework` 链接到你的项目。 将 `IntuneMAM.framework` 拖放到项目目标的“链接的框架和库”列表中。
    
    **注意**：如果使用框架，则必须在将应用提交到应用商店之前，从通用框架中手动删除模拟器体系结构。 请参阅“将应用提交到应用商店”一节。

2. 请向项目中添加以下 iOS 框架：
    * MessageUI.framework
    * Security.framework
    * MobileCoreServices.framework
    * SystemConfiguration.framework
    * libsqlite3.dylib
    * libc + +.dylib
    * ImageIO.framework
    * LocalAuthentication.framework
    * AudioToolbox.framework

    **注意**：如果此应用针对的是 iOS 7，请将 `LocalAuthentication.framework` 的“Status”特性设置为“Optional”。 如果未设置“Status”，则无法在 iOS 7 上启动此应用。

    **注意**：Xcode 7 已将 `.dylib` 扩展名切换为 `.tbd`。

3. 将 `IntuneMAMResources.bundle` 资源包添加到项目，方法是在“生成阶段”将此资源包拖放到“复制资源包”下面。
![Intune App SDK iOS - 复制资源包](../media/intune-app-sdk-ios-copy-bundle-resources.png)
 
4. 将 `-force_load {PATH_TO_LIB}/libIntuneMAM.a` 添加到以下任一项，并将 `{PATH_TO_LIB}` 替换为 Intune App SDK 的位置：
    * 项目的 `OTHER_LDFLAGS` 生成配置设置 
    * UI 的“其他链接器标志”<br>

    **注意**：要查找 `PATH_TO_LIB`，请选择文件 `libIntuneMAM.a`，并从“文件”菜单中选择“获取信息”。 复制并粘贴“信息”窗口中“常规”部分的“位置”信息（路径）。

5. 如果移动应用的 Info.plist 文件中定义了主要 Nib 或 Storyboard，请删除 Main Storyboard 或 Main Nib 文件字段。 使用以下键名称（如果适用）在名称为 IntuneMAMSettings 的新字典下方添加之前删除的 Storyboard 或 Nib 的值：
    * MainStoryboardFile
    * MainStoryboardFile~ipad
    * MainNibFile
    * MainNibFile ~ ipad
    
   **注意**：如果移动应用的 Info.plist 文件中未定义主要 Nib 或 Storyboard，那么这些设置为**非必需**字段。 

    **注意**：你可以使用原始格式查看 Info.plist 文件（目的是查看键名称），方法是右键单击文档正文的任意位置，然后将查看类型更改为“显示原始键/值”。

6. 通过单击每个项目目标的“功能”并启用“Keychain 共享”开关，来启用 Keychain 共享（如果尚未启用）。 需要启用 Keychain 共享才能继续执行下一步。

    **注意**：你的配置文件需要支持新的 keychain 共享值。 keychain 访问组应支持通配符。 你可以通过以下方法进行验证：在文本编辑器中打开 .mobileprovision 文件，搜索“keychain-access-groups”，确保其中包含通配符，例如： 
    ```
    <key>keychain-access-groups</key>
    <array>
    <string>YOURBUNDLESEEDID.*</string>
    </array>
    ```
7. 启用 keychain 共享后，请按照以下步骤创建将在其中存储 Intune App SDK 数据的单独的访问组。 你可以使用 UI 或授权文件创建 keychain 访问组：

    使用 UI 创建 keychain 访问组： 
    
    * 如果你的移动应用没有定义任何 keychain 访问组，则将此应用的程序包 ID 添加为第一个组。
    * 添加共享的 keychain 组 `com.microsoft.intune.mam`。 Intune App SDK 使用此访问组来存储数据。  
    * 将 `com.microsoft.adalcache` 添加到现有的访问组。 

    ![Intune App SDK iOS - keychain 共享](../media/intune-app-sdk-ios-keychain-sharing.png) 

    如果你使用授权文件来创建 keychain 访问组，而不是常规的 UI，那么你需要在授权文件的 keychain 访问组前面添加 `$(AppIdentifierPrefix)` 。 例如：  
    * `$(AppIdentifierPrefix)com.microsoft.intune.mam` 
    * `$(AppIdentifierPrefix)com.microsoft.adalcache`

    **注意**：授权文件是移动应用独有的 XML 文件，用于指定 iOS 应用中的特殊权限和功能。

8. 如果应用在其 Info.plist 文件中定义了 URL 方案，则为每个 URL 方案添加另一个具有 `-intunemam` 后缀的方案。

9. 对于为 iOS 9+ 开发的移动应用，需要在应用的 Info.plist 文件的 `LSApplicationQueriesSchemes` 数组中包括应用传递到 `UIApplication canOpenURL` 的每个协议。 此外，对于每个列出的协议，需要添加新的协议，并对新协议附加 `-intunemam`。 你还必须在此数组中包括 `http-intunemam`、 `https-intunemam`和 `ms-outlook-intunemam` 。 

10. 如果应用在其授权中定义了应用组，则将这些组作为字符串数组添加到 `AppGroupIdentitifiers` 键下面的 IntuneMAMSettings 字典中。

11. 将移动应用程序链接到 Azure 目录身份验证库 (ADAL)。 Objective C 的 ADAL 库[可在 Github 上获取](https://github.com/AzureAD/azure-activedirectory-library-for-objc)。

    **注意**：从 2015 年 6 月 19 日起针对 ADAL 代理分支代码测试了 Intune App SDK。 请确保与 ADAL 库的最新/正在使用的版本进行链接。

12. 在项目中包括 `ADALiOSBundle.bundle` 资源包，方法是在“生成阶段”将此资源包拖放到“复制资源包”下面。

13. 链接到此库时使用 `-force_load PATH_TO_ADAL_LIBRARY` 链接器选项。

    将 `-force_load {PATH_TO_LIB}/libADALiOS.a` 添加到项目的 `OTHER_LDFLAGS` 生成配置设置或 UI 的“其他链接器标志”。 `PATH_TO_LIB` 应替换为 ADAL 二进制文件位置。 

# 在应用中配置 Azure 目录身份验证库 (ADAL) 设置 

Intune App SDK 在其身份验证和条件启动时使用 ADAL。 它还依赖于 ADAL 以注册带有 MAM 服务的用户标识，用于不含设备注册方案的管理。 

通常情况下，ADAL 要求应用进行注册并获得唯一的 ID（称为 ClientID）和其他标识符，从而确保授予该应用的令牌的安全。 连接 Azure Active Directory 时，Intune App SDK 使用默认的注册值。  

如果应用在进行身份验证时使用了 ADAL，那么此应用必须使用其现有的注册值，并覆盖 Intune App SDK 的默认值，从而确保不会提示最终用户进行两次身份验证（一次是由 Intune App SDK 发起的身份验证，另一次是由此应用发起的身份验证）。 

##ADAL 常见问题解答

**应使用何种 ADAL 二进制文件？** 

Intune App SDK 目前使用 [ADAL on GitHub](https://github.com/AzureAD/azure-activedirectory-library-for-objc)（GitHub 上的 ADAL）的代理分支，以便支持需要条件访问的应用（即依赖于 Microsoft Authenticator 应用的应用）。 但是，SDK 仍与 ADAL 的主分支兼容。 请使用适合于你应用的分支。

**如何链接到 ADAL 二进制文件？**

将 `-force_load {PATH_TO_LIB}/libADALiOS.a` 添加到项目的 `OTHER_LDFLAGS` 生成配置设置或 UI 的“其他链接器标志”。 `PATH_TO_LIB` 应替换为 ADAL 二进制文件位置。 此外，请确保将 ADAL 包复制到你的应用。  

有关详细信息，请参阅 [ADAL on Github](https://github.com/AzureAD/azure-activedirectory-library-for-objc)（Github 上的 ADAL）中的说明。


**如何与其他签名有相同预配配置文件的应用共享 ADAL 缓存？**

如果应用没有定义任何 keychain 访问组，则将此应用的程序包 ID 添加为第一个组。
通过在 keychain 权利中添加 `com.microsoft.adalcache` 和 `com.microsoft.workplacejoin` 访问组来启用 ADAL SSO。 

如果正在显式设置 ADAL 共享缓存 keychain 组，请确保将其设置为 `<app_id_prefix>.com.microsoft.adalcache`。 除非替代 ADAL，否则它将完成此设置。 如果希望指定一个自定义 keychain 组来替代 `com.microsoft.adalcache`，请在“IntuneMAMSettings”下的 Info.plist 中使用键 `ADALCacheKeychainGroupOverride` 进行指定。

**如何强制 Intune App SDK 使用应用已在使用的 ADAL 设置？** 

如果应用已在使用 ADAL，请参阅下方 IntuneMAMSettings 中的小节了解有关填充以下设置的信息：  

* ADALClientId
* ADALRedirectUri
* ADALRedirectScheme
* ADALCacheKeychainGroupOverride

**如何在 AAD 生产环境和内部测试环境之间进行切换？**

`MAMPolicies.plist` 中的 `AadAuthorityURI` 设置可用于指定适用于 ADAL 调用的 AAD 环境。 当前已默认设置为使用 AAD 预生产环境 (PPE)，除非替代。
    
若要对 PPE 进行测试，可以使用编译时或运行时切换。 

对于 MAM 服务 URL 和 AAD 的编译时环境切换，请将 MAMEnvironment.plist 中的 `UsePPE` 布尔标志设置为 true（**注意**：不支持通过 Info.plist 执行此操作）。 

对于运行时环境切换，请将标准用户默认中的 `com.microsoft.intune.mam.useppe` 设置为“1”以使用 PPE。 这将替换现有的 `com.microsoft.intune.mam.AADAuthorityEnvironment` 设置。 

**如何使用运行时提供的租户特定的 URL 替代 AAD 颁发机构 URL？** 

在 IntuneMAMPolicyManager 实例上设置 `aadAuthorityUriOverride` 属性。

**注意**：在没有设备注册方案的 MAM 中需要此属性，以允许 SDK 重用应用提取的 ADAL 刷新令牌。

**注意：**SDK 会继续使用此颁发机构 URL 进行策略刷新和任何后续注册请求，除非该值被清除或更改。  因此，请务必在企业用户注销此应用后清除该值，并在新的企业用户重新登录时重置该值。


**如果应用自身使用 ADAL 进行身份验证，应该怎么办？**

如果应用已经使用 ADAL 进行身份验证，则必须执行下面的步骤。 如果应用不依赖于 ADAL，则应查阅有关如何使用 Intune 服务进行注册（如果应用不使用 ADAL）小节。

* 在项目的 Info.plist 中，在具有键名 `ADALClientId` 的 IntuneMAMSettings 字典下面指定要用于 ADAL 调用的 ClientID。 

* 在项目的 Info.plist 中，在具有键名 `ADALRedirectUri` 的 IntuneMAMSettings 字典下面指定要用于 ADAL 调用的重定向 URI。 你可能还需要根据应用的重定向 URI 的格式指定 `ADALRedirectScheme` 。



#使用 MAM 服务注册应用 

## 使用 API
Intune App SDK 现提供 iOS 应用从 Intune 接收 MAM 策略的功能，而无需使用 Intune 注册 MDM。 为支持这一新功能，SDK 提供的新 API 允许应用接收 MAM 策略。 若要使用新 API，请完成以下步骤：

1. 使用 Intune App SDK 的最新版本，无论含或不含设备注册，该版本都支持应用管理。 如果应用使用了不含此功能的旧版本 SDK，则需要更新 Intune MAM 库，以及带有来自最新 SDK 的标头的标头文件夹。

2. 将 IntuneMAMEnrollment.h 添加到任何要调用 API 的文件 

3. 若要对 PPE 进行测试，可以使用编译时或运行时切换。 

    对于 MAM 服务 URL 和 AAD 的编译时环境切换，请将 MAMEnvironment.plist 中的 `UsePPE` 布尔标志设置为 true（**注意**：不支持通过 Info.plist 执行此操作）。 

    对于运行时环境切换，请将标准用户默认中的 `com.microsoft.intune.mam.useppe` 设置为“1”以使用 PPE。 这将替换现有的 `com.microsoft.intune.mam.AADAuthorityEnvironment` 设置。 


##注册帐户 

如果应用代表指定的用户帐户进行注册，则该应用可从 Intune 服务接收 MAM 策略。  应用有责任使用 Intune App SDK 注册任何新登录的用户。  新用户帐户经身份验证后，应用应调用 Headers/IntuneMAMEnrollment.h 中找到的 `registerAndEnrollAccount` 方法： 

```
/** 


 *  This method will add the account to the list of registered accounts. 
 *  An enrollment request will immediately be started.
 *  @param identity The UPN of the account to be registered with the SDK 
 */ 

(void)registerAndEnrollAccount:(NSString *)identity; 

```
通过调用上面的方法，SDK 会注册用户帐户并尝试注册代表此帐户的应用。  如果注册由于任何原因失败，SDK 会在 24 小时后自动重试注册。  出于调试目的，应用可通过委托接收有关任何注册请求结果的通知（请参阅下方详细信息）。

调用此 API 后，应用程序可继续正常工作。  如果注册未成功，该 SDK 会通知用户重启应用。  此时，用户可立即重启应用。


##取消注册帐户 


用户注销应用之前，应用应从 SDK 取消注册用户。  这样做可确保： 

1. 不再对用户的帐户进行注册重试。 
2. 如果用户已成功注册应用程序，则会从 Intune MAM 服务中取消注册该用户和应用，并删除 MAM 策略。
3. 也可启动选择性擦除以确保已删除所有与工作或学校相关的数据。 

用户注销之前，应用应调用在 Headers/IntuneMAMEnrollment.h 中找到的以下 API： 

```
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

必须在删除用户帐户的 AAD 令牌之前调用此方法。  SDK 需要用户的应用令牌来为代表用户的 Intune MAM 服务发出指定请求。 

如果应用要删除其自身中用户的工作或学校相关数据，则可将 `doWipe` 标志设置为 false。  否则，应用可使 SDK 启动选择性擦除，从而调用应用的选择性擦除委托。 

```
[[IntuneMAMEnrollmentManager instance] deRegisterAndUnenrollAccount:@”user@foo.com” withWipe:YES]; 
```


##未登录注册 

未使用 Azure Active Directory 登录用户的应用仍可以通过调用以下 API 从 Intune 服务接收 MAM 策略，使 SDK 处理身份验证。 应用应在未使用 AAD 对用户进行身份验证但仍需检索 MAM 策略以保护应用中的数据时使用此方法 -- 例如：如果使用了其他身份验证服务进行应用登录，或如果应用不支持登录。 若要执行此操作，应用程序应调用 Headers/IntuneMAMEnrollment.h 中找到的 `loginAndEnrollAccount` 方法：

```
/** 
 *  Creates an enrollment request which is started immediately. 
 *  If no token can be retrieved for the identity, the user will be prompted 
 *  to enter their credentials, after which enrollment will be retried. 
 *  @param identity The UPN of the account to be logged in and enrolled. 
 */ 
 (void)loginAndEnrollAccount: (NSString *)identity; 

```
通过调用此方法，如果找不到任何现有令牌，则 SDK 会提示用户输入凭据，然后尝试注册代表此帐户的应用程序。 作为标识可将此方法称作“nil”，在此情况下 SDK 会使用设备上现有的 MAM 用户进行注册，或在找不到任何现有用户时提示用户。 

如果注册失败，应用应考虑在之后某一时间再次调用此 API，取决于失败的详细信息。 应用可通过委托接收有关任何注册请求结果的通知（请参阅详细信息）。 

调用此 API 后，应用可继续正常工作。  如果注册成功，SDK 会通知用户重启应用，如上文有关注册帐户小节中的图片所示。 

##调试信息 

应用可接收有关以下针对 Intune MAM 服务的请求的调试通知： 

 - 注册请求 
 - 策略更新请求 
 - 取消注册请求 

通过可在 Headers/IntuneMAMEnrollmentDelegate.h 中找到的委托方法显示通知： 

```
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

这些委托方法返回 ```IntuneMAMEnrollmentStatus``` 对象，其中包含以下信息： 

- 与请求关联的帐户的标识 
- 指示请求结果的状态代码 
- 带有状态代码说明的错误字符串 
- NSError 对象 

此对象连同可返回的特定状态代码在 Headers/IntuneMAMEnrollmentStatus.h 中进行定义。 

请注意，此信息用于调试目的，应用程序的业务逻辑不应基于这些通知。  其想法是，应用可将此信息发送给遥测服务用于调试或监视目的。 


##示例代码 

委托方法的示例实现如下： 

```
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


##应用重启 

应用首次接收到 MAM 策略时需要重启才能应用所需挂钩。  为了通知应用需要重启，SDK 在 Headers/IntuneMAMPolicyDelegate.h 中提供了委托方法。 
```
 - (BOOL) restartApplication 
```
此方法的返回值会告诉 SDK 应用程序是否处理所需的重启。   

 - 如果返回 true，则应用程序将负责处理重启。   
 - 如果返回 false，则 SDK 会在此方法返回后重启该应用程序。  SDK 会立即弹出一个对话框，告诉用户必须重启应用程序。 

#实施“另存为”控件

通过 Intune，IT 管理员可选择托管应用保存数据的存储位置。 应用可使用 **isSaveToAllowedForLocation** API 为允许的存储位置查询 Intune App SDK。

将托管数据保存到云存储或本地位置前，应用必须使用 **isSaveToAllowedForLocation** API 进行检查，以了解 IT 管理员是否允许数据保存在此处。

使用 **isSaveToAllowedForLocation** API 时，应用必须传入用于存储位置的 UPN（若可用）。

##支持的位置

**isSaveToAllowedForLocation** API 提供用于检查以下位置的常数：

* IntuneMAMSaveLocationOther 
* IntuneMAMSaveLocationOneDriveForBusiness 
* IntuneMAMSaveLocationSharePoint 
* IntuneMAMSaveLocationBox 
* IntuneMAMSaveLocationDropbox 
* IntuneMAMSaveLocationGoogleDrive 
* IntuneMAMSaveLocationLocalDrive 

应用应使用 **isSaveToAllowedForLocation** API 中的常数来检查数据是否可保存到被视为“已托管”的位置（例如 OneDrive for Business）或“个人”。 此外，无法确定位置为“已托管”或“个人”时，应使用 API。 

如果已知位置为“个人”，应用应使用 **IntuneMAMSaveLocationOther** 值。 

如果应用将数据保存到本地设备上的任何位置，应使用 **IntuneMAMSaveLocationLocalDrive** 常数。



# 配置 Intune App SDK 设置

应用的 Info.plist 文件中包含的 IntuneMAMSettings 字典用于配置 Intune App SDK。 下面列出了所有支持的设置： 

其中的一些设置可能已在前面各节中提及，一些设置则不适用于所有应用。 

Setting  | 类型  | 定义 | 是否必需？
--       |  --   |   --       |  --
ADALClientId  | 字符串  | 应用的 AAD 客户端标识符。 | 如果应用使用 ADAL 则需要。
ADALRedirectUri  | 字符串  | 应用的 AAD 重定向 URI。 | 如果应用使用 ADAL，则需要 ADALRedirectUri 或 ADALRedirectScheme。 
ADALRedirectScheme  | 字符串  | 应用的 AAD 重定向方案。 如果应用的重定向 URI 为 `scheme://bundle_id` 格式，则它可用于代替 ADALRedirectUri。 | 如果应用使用 ADAL，则需要 ADALRedirectUri 或 ADALRedirectScheme。 
ADALLogOverrideDisabled | 布尔值  | 指定 SDK 是否将所有 ADAL 日志（包括应用的 ADAL 调用，如果有）路由到它自己的日志文件。 默认值为 NO。 如果应用想要设置其自己的 ADAL 日志回调，则设置为 YES。 | 可选。
ADALCacheKeychainGroupOverride | 字符串  | 指定要用于 ADAL 缓存而不是“com.microsoft.adalcache”的 keychain 组。 注意，这并不包含应用 ID 前缀。 这将作为运行时提供的字符串的前缀。 | 可选。
AppGroupIdentifiers | 字符串数组  | 应用的授权 com.apple.security.application 组部分的应用组数组。 | 如果应用使用应用组，则需要此设置。
ContainingAppBundleId | 字符串 | 指定扩展的包含应用程序的程序包 ID。 | iOS 扩展需要此设置。
DebugSettingsEnabled| 布尔值 | 如果设置为“是”，则可以应用设置包中的测试策略。 应用程序**不**会因启用此设置而提供。 | 可选。
MainNibFile<br>MainNibFile ~ ipad  | 字符串  | 此设置应包含应用的主要 nib 文件名。  | 如果应用程序在其 Info.plist 中定义了 MainNibFile，则需要此设置。
MainStoryboardFile<br>MainStoryboardFile~ipad  | 字符串  | 此设置应包含应用的主要 storyboard 文件名。 | 如果应用程序在其 Info.plist 中定义了 UIMainStoryboardFile，则需要此设置
MAMPolicyRequired| 布尔值| 如果应用没有 Intune MAM 策略，指定是否要阻止应用启动。 默认值为“否”。 
MAMPolicyWarnAbsent | 布尔值| 如果应用没有 Intune MAM 策略，指定应用是否在启动时警告用户。 注意：此设置被设为“是”时，无法将应用提交到商店 | 可选。
MultiIdentity | 布尔值| 指定应用是否为多身份标识识别 | 可选。
SplashIconFile~ipad <br>IntuneMAMSettings | 字符串  | 指定 Intune 的初始屏幕图标文件。 有关更多信息，请参阅本文的“启动时的图像文件”一节。 | 可选。
SplashDuration | 数字 | 应用启动时显示 Intune 初始屏幕的最小时间（以秒为单位）。 默认值为 1.5。 | 可选。
BackgroundColor| 字符串| 指定初始屏幕和 PIN 屏幕的背景色。 接受“#XXXXXX”格式的十六进制 RGB 字符串，其中“X”的范围可以为 0-9 或 A-F。 可忽略井号。   | 也可选择默认的浅灰色。
ForegroundColor| 字符串| 指定初始屏幕和 PIN 屏幕的前景色，例如文本颜色。 接受“#XXXXXX”格式的十六进制 RGB 字符串，其中“X”的范围可以为 0-9 或 A-F。 可忽略井号。  | 也可选择默认的黑色。
AccentColor | 字符串| 指定 PIN 屏幕的主题色，例如按钮文本颜色和窗口高亮颜色。  接受“#XXXXXX”格式的十六进制 RGB 字符串，其中“X”的范围可以为 0-9 或 A-F。 可忽略井号。| 也可选择默认的系统蓝色。
MAMTelemetryDisabled| 布尔值| 指定 SDK 是否会将任何遥测数据发送回其后端| 可选。
MAMTelemetryUsePPE | 布尔值 | 指定 SDK 是否会将数据发送到其预生产环境 (PPE) 后端。 使用 Intune 策略测试应用时使用该布尔值，以便测试遥测数据不会与客户数据相混淆。 | 可选。

## 遥测技术 

默认情况下，Intune App SDK for iOS 记录使用事件的遥测数据，并将其发送到 Microsoft Intune。 将对以下使用事件记录数据： 

1. **应用启动事件**：用于帮助 Microsoft Intune 按照管理类型（含 MDM 的 MAM、不含 MDM 注册的 MAM，等）了解已启用 MAM 的应用的使用情况。

2. **EnrollApplication API 调用事件**：用于帮助 Microsoft Intune 了解客户端的 `enrollApplication` 调用的成功率和其他各种性能指标。

**注意**：如果选择不将 Intune App SDK 遥测数据从移动程序发送到 Microsoft Intune，则必须禁用 Intune App SDK 遥测数据捕获功能，方法是在 IntuneMAMSettings 字典中将属性 `MAMTelemetryDisabled` 设置为“是”。


## 将 SDK 构建到扩展中（可选） 

生成扩展时，请按照与生成移动应用相同的说明执行操作，如本文的“将 SDK 构建到移动应用中”一节所述。 此外，通过在具有包含应用程序的包 ID 的 IntuneMAMSettings 字典下面添加 `ContainingAppBundleId` 键，更新每个扩展的 Info.plist 文件。

## 将 SDK 构建到框架中（可选）

在应用了对 Intune App SDK 的最新更新后，如果移动应用包含嵌入的应用程序框架，则无需使用任何特定的链接器标志编译此移动应用。 

## 启动时的图像文件（可选）

当已启用 MAM 的应用由 Microsoft Intune 主动管理时，Intune App SDK 将在应用启动时显示启动屏幕，用于向用户表示此应用已被管理。 你可以选择添加要在“由你的公司管理”启动页面显示的图像文件。 针对图像使用以下准则：

* 在应用的 Info.plist 文件中，在具有键名 `SplashIconFile` 和 `SplashIconFile~ipad` 的 IntuneMAMSettings 字典下面添加文件名。 

* 图像大小和要求：

    * 对 iPhone 6s Plus 和 iPhone 6 Plus 使用 180 x 180，对其他 iPhone 型号使用 120x120，对 iPad 使用 152x152。 
    
    * 从文件名中删除 .png 扩展名。 
    
    * 链接到此库时使用 `@2x` 后缀，对 3 倍大小的版本使用 `@3x` 后缀。 如果图像大小不正确，则将对它们进行缩放，使其大小合适。 如果未指定 SplashIconFile 值，则 Intune App SDK 将选择应用的一个图标（对所有 Iphone 选择 60 x 60，对 iPad 选择 76 x 76）。

**注意**：此屏幕由启动触发，但可以由用户永久关闭。



#启用多身份标识（可选）

默认情况下，SDK 会将策略作为一个整体应用到该应用。 多身份标识是一种 MAM 功能，可以启用该功能以允许策略应用到单身份标识级别上。  这需要比其他 MAM 功能还要多的应用参与。 

应用需要在其意图更改现用身份时通知应用 SDK。 SDK 也会在需要标识更改时通知应用。 目前，仅支持一个托管标识。 用户注册设备或应用后，SDK 会使用此标识并将其作为主要托管标识。 应用中的其他用户会被视为具有不受限策略设置的非托管标识。 

注意，标识被简单地定义为字符串。 标识不区分大小写，而且向 SDK 请求标识可能会返回在设置标识时最初使用的相同大小写情况。


##了解标识 
  
标识只是帐户的用户名（例如 user@contoso.com）。 开发人员可以在以下不同级别上设置应用的标识： 

* **进程标识**：进程标识用于设置进程级标识，并且主要用于单一标识应用程序。 此标识会影响所有操作、文件和 UI。
* **UI 标识**：确定应用于主线程上 UI 操作中的策略类型，例如剪切/复制/粘贴、PIN、身份验证、数据共享等。UI 标识不会影响文件操作（如加密、备份等）。
* **线程标识**：线程标识会影响应用于当前线程上的策略类型。 此标识会影响所有操作、文件和 UI。

不论用户是否为托管，应用都会负责设置合适的标识。

在任何时候，每个线程都具有 UI 操作和文件操作的有效标识。 此标识用于确定应应用哪些策略（如有）。 如果此标识为“无标识”或用户不是托管的，则不会应用任何策略。 
 
 

##线程队列
 
应用通常将异步和同步任务调度到线程队列。 SDK 截获 Grand Central Dispatch (GCD) 调用，并将当前线程标识与调度任务相关联。 执行任务时，SDK 会临时将线程标识更改为与任务相关联的标识，再执行任务，然后还原原始线程标识。 由于 `NSOperationQueue` 基于 GCD 之上，`NSOperations` 会在其被添加到 `NSOperationQueue` 的同时运行线程标识。 `NSOperations` 或使用 GCD 直接调度的函数还可以在当前线程标识运行时对其进行更改。 此标识会替代继承自调度线程的标识。 

##文件所有者
 
SDK 跟踪本地文件所有者身份，并相应地应用策略。 文件所有者是在创建该文件时或在截断模式下打开文件时建立的。 所有者被设置为执行操作的线程的有效文件操作身份。 或者，应用可以显式使用 `IntuneMAMFilePolicyManager` 设置文件所有者身份。 应用可以使用 `IntuneMAMFilePolicyManager` 在显示该文件的内容之前检索文件所有者和设置 UI 标识。


##共享数据文件
 
如果应用创建包含同时来自托管和非托管用户的数据的文件，则应用需加密托管用户的数据。 可使用 `IntuneMAMDataProtectionManager` 的 `protect` 和 `unprotect` API 加密数据。 `protect` 方法可以接受托管或非托管用户的标识。 如果用户为托管用户，则会对数据进行加密。 如果用户为非托管用户，则会将一个编码有标识的标头添加到数据中，而不会对数据进行加密。  `protectionInfo` 方法可用于检索数据的所有者。

##共享扩展
 
如果应用包含共享扩展，则可以使用 `IntuneMAMDataProtectionManager` 中的 `protectionInfoForItemProvider` 方法检索要共享项的所有者。 如果共享项为文件，则 SDK 会处理设置文件所有者。 如果共享项为数据，且该数据被保存到文件，则应用会设置文件所有者，并会在在 UI 中显示此数据之前调用 `setUIPolicyIdentity` API（如下所述）。
 
##开启多身份
 
默认认为应用是单身份，SDK 将进程标志设置为已注册的用户。 若要启用多身份标识支持，必需将名为 `MultiIdentity`且值为“YES”的布尔量设置添加到应用的 Info.plist 文件中的 **IntuneMAMSettings** 字典。 

> [!NOTE]
> 启用多身份后，进程标识、UI 标识和线程标识将被设置为 nil。 应用有责任进行适当设置。

 
##切换标识
 
###应用启动标识切换
在启动时，多身份标识应用被视为在未知的非托管帐户下运行。 条件启动 UI 不会运行，且不会在该应用上强制执行任何策略。 应用负责在标识需要更改时通知 SDK。 通常情况下，当应用要为特定用户帐户显示数据时发出通知。

例如，用户尝试打开文档、邮箱或笔记本中的标签页时。 应用需在实际打开文件、邮箱或标签页之前通知 SDK。 可通过 `IntuneMAMPolicyManager` 中的 `setUIPolicyIdentity` API 实现。 不论用户是否为托管都应调用此 API。 如果用户为托管用户，则 SDK 会指向条件启动检查（如破解检测、PIN、身份验证等）。 标识切换的结果会通过完成处理程序异步返回到应用。 应用应推迟打开文档、邮箱、标签页等， 直到返回成功结果代码。 如果标识切换失败，应用应取消操作。 

###SDK 启动标识切换
有时，SDK 需要要求应用切换到特定标识。 多身份标识应用必须实现 `IntuneMAMPolicyDelegate` 中的 `identitySwitchRequired` 方法来处理此请求。 在调用时，如果应用能够处理切换到特定标识的请求，则应将 `IntuneMAMAddIdentityResultSuccess` 传递到完成处理程序中。 如果无法处理切换标识，应用应将 `IntuneMAMAddIdentityResultFailed` 传递到完成处理程序中。 应用无需调用 `setUIPolicyIdentity` 来响应此调用。 如果 SDK 需要应用切换到非托管用户帐户，则空字符串将传递到 `identitySwitchRequired` 调用。 
 
###“选择性擦除”
应用为选择性擦除时，SDK 会调用 `IntuneMAMPolicyDelegate` 中的 `wipeDataForAccount` 方法。 应用负责删除指定用户的帐户以及任何与其相关的数据。 如果应用从 `wipeDataForAccount` 调用返回“FALSE”，则 SDK 可删除用户拥有的全部文件。 注意，此方法从后台线程中进行调用，且应用不会返回“FALSE”，除非已删除用户的所有数据（如果应用返回“FALSE”，则文件异常）。

# 在 Xcode 中调试 Intune App SDK

在使用 Microsoft Intune 手动测试已启用 MAM 的应用之前，可以在 Xcode 中使用 **Settings.bundle** 文件。 这样，你无需连接到 Intune 就可以设置测试策略。 要启用此功能：

* 右键单击项目的最上层文件夹以添加 Settings.bundle 文件。 从菜单中选择“添加 -> 新建文件”。 在要添加的“资源”下面选择“设置包”模板。

* 仅在调试内部版本中，将 MAMDebugSettings.plist 复制到 Settings.bundle。

* 在 Root.plist（位于 Settings.bundle）中，添加首选项设置“Type”= 子窗格，且“FileName”= MAMDebugSettings。

* 在“设置”->“你的应用名称”中，打开“启用测试策略”。

* 启动应用（在 Xcode 内部或外部）。 

* 在“设置”->“你的应用名称”->“启用测试策略”中，打开一个策略，例如“PIN”。

* 启动应用（在 Xcode 内部或外部）。 确认 PIN 是否工作正常。

> [!NOTE]
> 现在你可以使用“设置”->“你的应用名称”->“启用测试策略”来启用和切换设置。

# 建议使用的 iOS 最佳做法

以下是针对 iOS 进行开发时建议采用的最佳做法：

IOS 文件系统是区分大小写的。 确保文件名的大小写正确，例如 `libIntuneMAM.a` 和 `IntuneMAMResources.bundle`。

如果 Xcode 在查找 `libIntuneMAM.a`时遇到问题，可以通过将此库的路径添加到链接器搜索路径来解决此问题。



##常见问题 

 **应用程序的所有用户是否都需要使用 MAM 服务注册？**

否。  实际上，只有工作或学校帐户需要向 Intune App SDK 注册。  应用负责确定所使用的帐户是否为工作或学校账户。   
 
**已登录到应用程序的用户呢？  他们是否需要注册？** 

应用程序负责在用户成功经过身份验证后为其注册的同时，也负责注册任何现有帐户，这些帐户可能在应用程序具有 MAM（无 MDM）功能之前已存在。   


若要执行此操作，应用程序应使用 `registeredAccounts:` 方法。  此方法返回包含所有已注册到 Intune MAM 服务的帐户的 NSDictionary。  如果应用程序中的没有任何现有帐户存在于列表中，则应用程序应注册，并通过 `registerAndEnrollAccount:` 注册这些帐户。 


 

**SDK 多长时间会重试注册？** 

SDK 会在上一次注册失败后每隔 24 小时自动重试。  SDK 这样做是为了确保：即使用户的组织在用户登录到应用程序后启用了 MAM，用户也能成功注册并接收策略。 

SDK 会在检测到用户已成功注册该应用程序后停止重试。  这是因为只有 1 位用户可以在任意给定时间内注册应用程序。 如果用户未注册，则将在同样 24 小时间隔后再次开始重试。 


 
**为何用户需要取消注册？** 

SDK 将在后台定期执行以下操作：

 - 如果应用程序尚未注册，SDK 会每隔 24 小时尝试注册所有已注册的帐户。 
 - 如果应用程序已注册，SDK 会每隔 8 小时检查 MAM 策略更新。 

通过取消注册用户，应用程序会通知 SDK 用户不再使用该应用程序，并可以暂停为该用户帐户执行上述周期事件。  如有必要，这也会触发应用程序取消注册和选择性擦除。 

**是否应在取消注册方法中将 doWipe 标志设置为 true？** 应在用户注销应用程序之前调用此方法。  作为注销的一部分，如果应用程序已删除用户的数据，则可将 `doWipe` 设置为 false。  但是，如果应用程序实际未删除用户的数据，则该标志应设置为 true，以便 SDK 可以手动删除数据本身。 

**是否有其他可以取消注册应用程序的方法？** 是，IT 管理员可以向该应用程序发送选择性擦除命令，撤销用户注册、取消用户注册，并擦除用户的数据。  SDK 自动处理此方案，并将通过取消注册委托方法发送通知。 

#将应用提交到应用商店
Intune App SDK 的静态库和框架构建均为通用二进制文件，这意味着它们含有用于所有设备和模拟器体系结构的代码。 如果应用含有模拟器代码，Apple 会拒绝将其提交到应用商店。 编译针对用于仅设备构建的静态库时，链接器会自动删除其中的模拟器代码。

如果应用使用 Intune App SDK 的**框架构建**，则必须在将应用提交到应用商店之前，从通用框架中手动删除模拟器体系结构。 下面的这些说明将帮助你完成操作：

1. 请确保 `IntuneMAM.framework` 位于桌面上。
2. 运行以下命令：
    
    ```
    lipo ~/Desktop/IntuneMAM.framework/IntuneMAM -remove i386 -remove x86_64 -output ~/Desktop/IntuneMAM.device_only
    ```
    第一个命令用于从框架的 dylib 中删除模拟器体系结构。
    ```
    cp ~/Desktop/IntuneMAM.device_only ~/Desktop/IntuneMAM.framework/IntuneMAM 
    ```
    第二个命令用于将仅设备 dylib 复制回框架目录。



<!--HONumber=Oct16_HO3-->


