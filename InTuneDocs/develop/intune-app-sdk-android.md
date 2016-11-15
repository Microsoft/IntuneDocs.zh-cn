---
title: "Microsoft Intune App SDK for Android 开发人员指南 | Microsoft Intune"
description: 
keywords: SDK
author: Msmbaldwin
manager: jeffgilb
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: edbc701effb3817c2f9a160f05e7b5bc8ad0070e
ms.openlocfilehash: ee3a668a5415d14eb82e64e6bb16d9621bb13b57


---


# <a name="microsoft-intune-app-sdk-for-android-developer-guide"></a>Microsoft Intune App SDK for Android 开发人员指南

> [!NOTE]
> 你可能希望首先阅读 [Intune App SDK 概述](intune-app-sdk.md)，该文档涵盖 SDK 的当前功能并介绍了如何在每个受支持的平台上准备集成。 

用于 Android 的 Microsoft Intune App SDK 支持将 Intune 移动应用管理 (MAM) 集成到 Android 应用中。 启用了 MAM 的应用程序是指与 Intune App SDK 集成的应用程序，允许 IT 管理员在通过 Intune 主动管理移动应用时在该应用上部署策略。

# <a name="whats-in-the-sdk"></a>SDK 包含的内容 

Intune App SDK for Android 是没有外部依赖项的标准 Android 库。 该 SDK 由以下内容组成：  

* **Microsoft.Intune.MAM.SDK.jar**：启用 MAM 以及启用与 Intune 公司门户应用的互操作性所需的接口。 应用必须指定它作为 Android 库引用。

* **Microsoft.Intune.MAM.SDK.Support.v4.jar**：在利用 Android v4 支持库的应用中启用 MAM 所需的接口。  需要此支持的应用必须直接引用该 jar 文件。 

* **Microsoft.Intune.MAM.SDK.Support.v7.jar**：在利用 Android v7 支持库的应用中启用 MAM 所需的接口。 需要此支持的应用必须直接引用该 jar 文件。

* **资源目录**：SDK 所依赖的资源（如字符串）。 

* **Microsoft.Intune.MAM.SDK.aar**：SDK 组件（Support.V4 和 Support.V7 jar 除外）。 如果生成系统支持 AAR 文件，则此文件可以用于替代各个组件。

* **AndroidManifest.xml**：其他入口点和库要求。 

* **THIRDPARTYNOTICES.TXT**：一个归属声明，用于确认将在应用中编译的第三方和/或 OSS 代码。 

# <a name="requirements"></a>要求 

Intune App SDK 是已编译的 Android 项目。 因此，应用用于其最低或目标 API 版本的 Android 版本在很大程度上是不可知的。 此 SDK 支持 Android API 14 (Android 4.0+) 到 Android API 24。 

对于 MAM 策略的启用，用于 Android 的 Intune App SDK 依赖于设备上是否存在[公司门户](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)应用。 对于没有设备注册的 MAM，不会**要求**用户使用公司门户注册设备。


# <a name="how-the-intune-app-sdk-works"></a>Intune App SDK 的使用方式 

##<a name="entry-points"></a>入口点

Intune App SDK 需要更改应用的源代码才能启用 Intune 应用管理策略。 此操作可通过将 Android 基类替换为等效的 Intune 基类（其名称具有前缀 **MAM**）来完成。 SDK 类介于 Android 基类与应用自己的该类派生版本之间。  以一个活动为例，你最终会得到类似于下面这样的继承层次结构：Activity > MAMActivity > AppSpecificActivity。

例如，**AppSpecificActivity** 与其父级（例如，调用 `super.onCreate()`）交互时，**MAMActivity** 就是超级类。 

典型 Android 应用具有单一模式，可以通过其[上下文](https://developer.android.com/reference/android/content/Context.html)对象访问系统。  另一方面，已包含 Intune App SDK 的应用则具有双模式。 这些应用继续通过上下文对象访问系统，但是根据所使用的基本活动，上下文对象将由 Android 提供，或者以智能方式在系统的受限视图与 Android 提供的上下文之间进行多路复用。

使用已由其 MAM 等效项所替代的 Android [入口点](https://developer.android.com/guide/components/fundamentals.html)时，必须使用入口点生命周期的 MAM 版本（类 **MAMApplication** 除外）。

例如，从 **MAMActivity** 派生（而不是替代 `onCreate` 并调用 `super.onCreate`）时，活动必须替代 `onMAMCreate` 并调用 `super.onMAMCreate`。 这可以使 Intune 在特定情况下限制活动启动（及其他）。 


##<a name="sdk-permissions"></a>SDK 权限

Intune App SDK 需要具有三个 [Android 系统权限](https://developer.android.com/guide/topics/security/permissions.html)才能在应用上进行集成：

* `android.permission.GET_ACCOUNTS` [需要时可在运行时请求]
* `android.permission.MANAGE_ACCOUNTS`
* `android.permission.USE_CREDENTIALS`

Azure Active Directory 身份验证库 ([ADAL](https://azure.microsoft.com/en-us/documentation/articles/active-directory-authentication-libraries/)) 需要这些权限以执行代理身份验证。 如果未对应用授予这些权限或权限被用户废除，则将禁用需要代理（公司门户应用）的身份验证流。


##<a name="company-portal"></a>Company Portal

为什么需要公司门户应用？ 如果设备上安装了公司门户，当从 Intune 服务检索到用户的应用程序限制策略时，将以异步方式初始化 SDK 入口点。 仅当 Android 最初创建进程时才需要初始化。 在初始化过程中，会建立与公司门户应用的连接并从应用检索策略。  

> [!NOTE]
> 如果设备上没有安装公司门户应用，则已启用 Intune 应用的行为不会更改，且会与常规应用行为一样。


# <a name="how-to-integrate-with-the-intune-app-sdk"></a>如何与 Intune App SDK 集成
 
如前所述，该 SDK 需要更改应用的源代码才能启用应用管理策略。 下面是在应用中启用 MAM 所需的步骤： 

## <a name="replace-classes-methods-and-activities-with-their-mam-equivalent-required"></a>将类、方法和活动替换为其 MAM 等效项（必需） 

Android 基类必须替换为其相应的 MAM 等效项。 为此，请查找下表中列出的类的所有实例，并将它们替换为 Intune App SDK 等效项。 

| Android 基类 | Intune App SDK 替换项 |
|--|--|
| android.app.Activity | MAMActivity |
| android.app.ActivityGroup | MAMActivityGroup |
| android.app.AliasActivity | MAMAliasActivity |
| android.app.Application | MAMApplication |
| android.app.DialogFragment | MAMDialogFragment |
| android.app.ExpandableListActivity | MAMExpandableListActivity |
| android.app.Fragment | MAMFragment |
| android.app.IntentService | MAMIntentService |
| android.app.LauncherActivity | MAMLauncherActivity |
| android.app.ListActivity | MAMListActivity |
| android.app.NativeActivity | MAMNativeActivity |
| android.app.PendingIntent | **MAMPendingIntent** * |
| android.app.Service | MAMService |
| android.app.TabActivity | MAMTabActivity |
| android.app.TaskStackBuilder | MAMTaskStackBuilder |
| android.app.backup.BackupAgent | MAMBackupAgent |
| android.app.backup.BackupAgentHelper | MAMBackupAgentHelper |
| android.app.backup.FileBackupHelper | MAMFileBackupHelper |
| android.app.backup.SharePreferencesBackupHelper | MAMSharedPreferencesBackupHelper |
| android.content.BroadcastReceiver | MAMBroadcastReceiver |
| android.content.ContentProvider | MAMContentProvider |
| android.os.Binder | **MAMBinder**（仅当 Binder 不是从 Android 接口定义语言 (AIDL) 接口生成时才需要） |
| android.provider.DocumentsProvider | MAMDocumentsProvider |
| android.preference.PreferenceActivity | MAMPreferenceActivity |


**Microsoft.Intune.MAM.SDK.Support.v4.jar**：

| Android 类 Intune MAM | Intune App SDK 替换项 |
|--|--|
| android.support.v4.app.DialogFragment | MAMDialogFragment
| android.support.v4.app.FragmentActivity | MAMFragmentActivity
| android.support.v4.app.Fragment | MAMFragment
| android.support.v4.app.TaskStackBuilder | MAMTaskStackBuilder
| android.support.v4.content.FileProvider | MAMFileProvider
    
**Microsoft.Intune.MAM.SDK.Support.v7.jar**：

|Android 类 | Intune App SDK 替换项 |
|--|--|
|android.support.v7.app.ActionBarActivity | MAMActionBarActivity |

>[!NOTE]
>请记住 - 使用已由其 MAM 等效项所替代的 Android [入口点](https://developer.android.com/guide/components/fundamentals.html)时，必须使用入口点生命周期的 MAM 版本（类 **MAMApplication** 除外）。
>
>例如，从 **MAMActivity** 派生（而不是替代 `onCreate` 并调用 `super.onCreate`）时，活动必须替代 `onMAMCreate` 并调用 `super.onMAMCreate`。 这可以使 Intune 在特定情况下限制活动启动（及其他）。 

### <a name="pendingintents-and-renamed-methods"></a>PendingIntents 和重命名的方法 

从一个 MAM 入口点派生之后，可以按通常方法使用上下文，安全启动活动（使用其 **PackageManager**）等等。  

**PendingIntents** 是此规则的例外情况。 调用这种类时，需要更改类名。 例如，必须使用 `MAMPendingIntents.get*` 方法，而不是 `PendingIntent.get*`。 此后，可照常使用所生成的 **PendingIntents**。

在某些情况下，Android 类中提供的方法已在 MAM 替换类中标记为最终方法。 在此情况下，MAM 替换类会提供应改为替代的具有类似名称的方法（通常使用“MAM”作为后缀）。 例如，应替代 `ContentProvider.query`，而不是替代 `MAMContentProvider.queryMAM`。 Java 编译器应强制执行最终限制，以防止意外替代原始方法（而不是 MAM 等效项）。 

##<a name="enable-features-that-require-app-participation"></a>启用需要应用参与的功能 

SDK 无法单独实现某些策略。 该应用可以使用下面 **AppPolicy** 接口中包含的多个 API 控制其行为以实现这些功能。  

```
/**
 * External facing application policies.
 */
public interface AppPolicy {

/**
 * Restrict where an app can save personal data.
 * <strong>This function is now deprecated. Please use {@link #getIsSaveToLocationAllowed(SaveLocation, String)} instead</strong>
 * @return True if the app is allowed to save to personal data stores; false otherwise.
 */
@Deprecated
boolean getIsSaveToPersonalAllowed();

/**
 * Check if policy prohibits saving to a content provider location.
 * 
 * @param location
 *            a content URI to check
 * @return True if location is not a content URI or if policy does not prohibit saving to the content location.
 */
boolean getIsSaveToLocationAllowed(Uri location);

/**
 * Determines if the SaveLocation passed in can be saved to by the username associated with the cloud service.
 *
 * @param service
 *           see {@link SaveLocation}.
 * @param username
 *           the username/email associated with the cloud service being saved to. Use null if a mapping between the AAD username and the cloud service username does not exist or the username is not known.
 * @return true if the location can be saved to by the identity, false if otherwise.
 */
boolean getIsSaveToLocationAllowed(SaveLocation service, String username);

/**
 * Whether the SDK PIN prompt is enabled for the app.
 * 
 * @return True if the PIN is enabled. False otherwise.
 */
boolean getIsPinRequired();

/**
 * Whether the Intune Managed Browser is required to open web links.
 * @return True if the Managed Browser is required, false otherwise
 */
boolean getIsManagedBrowserRequired();

/**
 * Check if policy allows Contact sync to local contact list.
 * 
 * @return True if Contact sync is allowed to save to local contact list; false otherwise.
 */
boolean getIsContactSyncAllowed();

/**
 * Return the policy in string format to the app.
 *  
 * @return The string representing the policy.
 */
String toString();


}

```

## <a name="enable-it-control-over-app-saving-behavior"></a>对应用保存行为启用 IT 控制

许多应用都可实现允许最终用户在本地保存文件或保存到云存储服务的功能。 使用 Intune App SDK，IT 管理员可通过应用他们认为适合于组织的策略限制来防止数据泄漏。  例如，IT 可以控制最终用户是否可以保存到“个人”非托管数据存储。 这包括保存到本地位置、SD 卡或第三方备份服务。 

**启用该功能需要应用参与。** 如果应用允许直接从应用保存到个人或云位置，则必须实现此功能以确保 IT 管理员可以控制是否允许保存到某个位置。 以下 API 使应用可以了解按照当前 Intune 管理员的策略，是否允许保存到个人存储。 应用随后可以强制执行策略，因为它知道最终用户可以通过应用来使用个人数据存储。  

要确定是否强制执行策略，应用可以进行以下调用： 

```
MAMComponents.get(AppPolicy.class).getIsSaveToPersonalAllowed();
```

**注意**：`MAMComponents.get(AppPolicy.class)` 会始终返回非 null 应用策略（即使设备或应用不在 Intune 管理策略下，也是如此）。 

## <a name="allow-app-to-detect-if-pin-policy-is-required"></a>允许应用检测是否需要 PIN 策略
 
对于某些 Intune 应用限制，用户可能希望其应用禁用部分功能，以便不重复 Intune App SDK 中的功能。 例如，如果应用具有其自己的 PIN 用户体验，则在 SDK 配置为要求最终用户输入 PIN 时，该应用可能需要禁用该功能。 

要确定 PIN 策略是否配置为启动时需要应用 PIN，应用可以进行以下调用： 

```
MAMComponents.get(AppPolicy.class).getIsPinRequired();
```

## <a name="registering-for-notifications-from-the-sdk"></a>注册来自 SDK 的通知  

当 IT 管理员部署特定策略（如选择性擦除策略）时，Intune App SDK 允许应用控制相应行为。 IT 管理员部署此类策略时，Intune 服务会向 SDK 下发通知。

但应用需要通过创建 **MAMNotificationReceiver** 类并将其向 **MAMNotificationReceiverRegistry** 注册，来注册来自 SDK 的通知。 此操作可通过在 `App.onCreate` 中提供接收方以及所需通知类型来实现，如以下示例所示：

``` 
@Override
public void onCreate() {
    super.onCreate();
    MAMComponents.get(MAMNotificationReceiverRegistry.class)
.registerReceiver(
                new ToastNotificationReceiver(),
MAMNotificationType.WIPE_USER_DATA);
    }
```

**MAMNotificationReceiver** 只从 Intune 服务接收通知。 某些通知由 SDK 直接处理，而其他通知需要应用参与。 

应用**必须**从通知返回 true 或 false。 

它必须始终返回 true，除非它由于通知失败而尝试执行某种操作。 

* 这种失败可能会被报告到 Intune 服务。 需报告的情形示例：应用在 IT 管理员启动擦除后无法擦除用户数据。 

可在 `MAMNotificationReceiver.onReceive` 中放心阻止，因为其回调未在 UI 线程上运行。 

下面显示了 SDK 中定义的 **MAMNotificationReceiver** 接口： 

```
/**
 * The SDK is signaling that a WG event has occurred. 
 * 
 */
public interface MAMNotificationReceiver {

    /**
     * A notification was received.
     * 
     * @param notification
     *            The notification that was received.
     * @return The receiver should return true if it handled the
     *   notification without error (or if it decided to ignore the
     *   notification). If the receiver tried to take some action in 
     *   response to the notification but failed to complete that
     *   action it should return false.
     */
    boolean onReceive(MAMNotification notification);
}

```

##<a name="types-of-notifications"></a>通知类型
以下通知会发送到应用，其中一些可能需要应用参与： 

* **`WIPE_USER_DATA`**：此通知在 **MAMUserNotification** 类中进行发送。 收到此通知后，应用应删除与随 **MAMUserNotification** 传递的“企业”标识关联的所有数据。 此通知当前在 Intune 服务取消注册过程中进行发送。 用户的主名称通常在注册过程中进行指定。 如果注册了此通知，则应用必须确保所有用户数据都已删除。 如果你未注册它，则会执行默认选择性擦除行为。

* **`WIPE_USER_AUXILIARY_DATA`**：如果应用希望 Intune App SDK 执行默认选择性擦除行为，但是在擦除进行时仍想删除一些辅助数据，则应用可以注册此通知。  

* **`REFRESH_POLICY`**：此通知在 **MAMUserNotification** 中进行发送。 收到此通知后，必须先使所有缓存的 Intune 策略失效，然后再更新这些策略。 这通常由 SDK 处理；但是如果以任何持久方式使用策略，则应由应用处理。 



## <a name="protecting-backup-data"></a>保护备份数据 

自 Android Marshmallow (API 23) 开始，Android 有两种方法可供应用来备份其数据。 用户可以在其应用中使用这两种选项，但需要不同的步骤，以确保正确实现 Intune 数据保护。 可查看下表，以了解有关正确数据保护行为所需的对应操作。  有关备份方法的详细信息，可参阅 [Android API 指南](http://developer.android.com/guide/topics/data/backup.html)。 

### <a name="auto-backup-for-apps"></a>应用的自动备份

Android 开始在 Android Marshmallow 设备上向应用提供[自动完整备份](https://developer.android.com/guide/topics/data/autobackup.html)（不考虑应用的目标 API）。 在 AndroidManifest.xml 中，如果将 `android:allowBackup` 显式设置为 **false**，则 Android 永远都不会将你的应用排入队列且“企业”数据将保留在应用中。 在这种情况下，无需执行进一步操作。

但是，即使未在清单文件中指定 `android:allowBackup`默认情况下也会将 `android:allowBackup` 属性设置为 true。 这意味着所有应用数据都会自动备份到用户的 Google Drive 帐户，这种默认行为会带来**数据泄露风险**。 因此 SDK 要求进行下面概括的更改以确保使用数据保护。  如果希望应用在 Android Marshmallow 设备上运行，请务必遵循以下指南以正确保护客户数据。  

*  如果尚未使用 **MAMBackupAgent** 或 **MAMBackupAgentHelper** 写入备份代理以备份应用，则必须考虑和控制自动备份上传应用数据的方式。 Intune 可让用户使用 Android 中所有可用的[自动备份功能](https://developer.android.com/guide/topics/data/autobackup.html)（包括定义 XML 中的自定义规则），但必须遵循以下步骤保护数据：

    1. 使用默认的 MAMBackupAgent，以允许执行符合 Intune 策略的自动完整备份。 将 `android:backupAgent="com.microsoft.intune.mam.client.app.backup.MAMDefaultBackupAgent"` 置于应用清单中。 
    2. 确定应用应接收的完整备份类型（未筛选、已筛选或无）时，需要将属性 `android:fullBackupContent` 设置为 true、false 或应用中的 XML 资源。 请将放入 `android:fullBackupContent` 的所有内容置于名为 `com.microsoft.intune.mam.FullBackupContent` 的元数据标记

    **示例**：如果希望应用根据 XML 文件中的自定义规则具有完整备份，请提供清单中 `com.microsoft.intune.mam.FullBackupContent` 元数据标记下的资源，如下所示： 
    ```
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />  
    ```



### <a name="keyvalue-backup"></a>键/值备份

此选项对所有 API 可用，并使用 `BackupAgent` 和 `BackupAgentHelper`。 

#### <a name="using-backupagenthelper"></a>使用 BackupAgentHelper

`BackupAgentHelper` 的实现都比 `BackupAgent` 简单得多。 `BackupAgentHelper` 允许开发人员分别将整个文件和共享首选项注册到 `FileBackupHelper` 或 `SharedPreferencesBackupHelper`，它们随后会在创建时添加到 `BackupAgentHelper` 。 

#### <a name="using-backupagent"></a>使用 BackupAgent

`BackupAgent` 使你可以更明确地表示进行备份的数据。 但是，此选项意味着你无法利用 Android 备份框架。  因为主要由你负责实现，所以确保从 MAM 进行适当数据保护需要更多步骤。 由于大部分工作由你（即开发人员）来完成，因此会稍微更多地涉及 MAM 集成。 

##### <a name="app-does-not-have-a-backup-agent"></a>应用没有备份代理
  
这些是 `android:allowBackup =true`：

###### <a name="full-back-up-according-to-a-configuration-file"></a>根据配置文件进行的完整备份： 

在清单中的 `com.microsoft.intune.mam.FullBackupContent` 元数据标记下提供资源。 例如：    `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />`

在 `<application>` 标记中添加以下属性： `android:fullBackupContent="@xml/my_scheme"`，其中 `my_scheme` 是应用中的 XML 资源。 

###### <a name="full-back-dup-without-exclusions"></a>完整备份（不带扩展） 

在清单中提供标记，如 `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />` 
 
在 `<application>` 标记中添加以下属性：`android:fullBackupContent="true"`。

##### <a name="app-has-a-backup-agent"></a>应用具有备份代理

遵循上面概括的 `BackupAgent` 和 `BackupAgentHelper` 部分中的建议 

考虑切换为使用我们的 `MAMDefaultFullBackupAgent`，它在 Android M 上提供轻松备份。 

#### <a name="before-your-backup"></a>在备份之前

开始备份之前，必须检查是否确实允许备份你计划备份的文件或数据缓冲区。 我们在 `isBackupAllowed` 和 `MAMFileProtectionManager` 和 `MAMDataProtectionManager` 函数用于确定这一点。 如果不允许备份文件或数据缓冲区，则你不应尝试继续在备份中利用它。

在备份过程中的某个时候，如果你希望备份在步骤 1 中检查的文件的标识，则必须调用 `backupMAMFileIdentity(BackupDataOutput data, File … files)`（使用你计划从中提取数据的文件）。 这会自动为你创建新的备份实体并将它们写入 `BackupDataOutput` 。 这些实体会在还原时自动进行使用。 

### <a name="configure-azure-directory-authentication-library-adal"></a>配置 Azure 目录身份验证库 (ADAL)  

SDK 依赖于 ADAL 实现其身份验证和条件启动方案，这要求应用进行一定量的 Azure Active Directory 配置。 配置值通过 `AndroidManifest` 元数据传递给 SDK。 要配置应用并启用适当的身份验证，请将以下内容添加到 `AndroidManifest`。 其中某些配置在一般情况下，仅当应用使用 ADAL 进行身份验证时才需要；在这种情况下，需要应用用于向 AAD 注册自己的特定值。 这样做是为了确保系统不会由于 AAD 识别到两个单独的注册值（一个来自应用，一个来自 SDK）而两次提示最终用户进行身份验证。 

        <meta-data
            android:name="com.microsoft.intune.mam.aad.Authority"
            android:value="https://AAD authority/" />
        <meta-data
            android:name="com.microsoft.intune.mam.aad.ClientID"
            android:value="your-client-ID-GUID" />
        <meta-data
            android:name="com.microsoft.intune.mam.aad.NonBrokerRedirectURI"
            android:value="your-redirect-URI" />
        <meta-data
            android:name="com.microsoft.intune.mam.aad.SkipBroker"
            android:value="[true | false]" />

GUID 不应具有前导或尾随大括号。

#### <a name="common-adal-configurations"></a>常用 ADAL 配置 

以下是上文说明的值的常用配置。 

##### <a name="app-does-not-integrate-adal"></a>应用未集成 ADAL

* 颁发机构必须设置为在其中配置了 AAD 帐户的所需环境。

* SkipBroker 必须设置为 true。

##### <a name="app-integrates-adal"></a>应用集成了 ADAL

* 颁发机构必须设置为在其中配置了 AAD 帐户的所需环境。

* 客户端 ID 必须设置为应用的客户端 ID。

* `NonBrokerRedirectURI` 应设置为应用的有效重定向 URI。
    * Or `urn:ietf:wg:oauth:2.0:oob` 必须配置为有效 AAD 重定向 URI。

* SkipBroker 必须设置为 false（或不存在）

* AAD 必须配置为接受代理重定向 URI。

##### <a name="app-integrates-adal-but-does-not-support-the-aad-authenticator-app"></a>应用集成了 ADAL，但不支持 AAD 验证器应用。

* 颁发机构必须设置为在其中配置了 AAD 帐户的所需环境。

* 客户端 ID 必须设置为应用的客户端 ID。

* `NonBrokerRedirectURI` 必须设置为应用的有效重定向 URI。

    * Or `urn:ietf:wg:oauth:2.0:oob` 应配置为有效 AAD 重定向 URI。

### <a name="how-to-enable-logging-in-the-sdk"></a>如何在 SDK 中启用日志记录 

日志记录通过 `java.util.logging` 框架进行。 要接收日志，请按照 [Java 技术指南](http://docs.oracle.com/javase/6/docs/technotes/guides/logging/overview.html)。 根据应用， `App.onCreate` 通常是启动日志记录的最佳位置。 请注意，日志消息按类名进行键控（这可能比较模糊）。

##<a name="multiidentity"></a>多身份标识
###<a name="overview"></a>概述
默认情况下，Intune App SDK 会将策略作为一个整体应用到该应用。 多身份标识是一种 MAM 功能，可以启用该功能以允许策略应用到单身份标识级别上。  这需要比其他 MAM 功能还要多得多的应用参与。 应用需要在打算更改活动标识时通知应用 SDK，SDK 也会在需要更改标识时通知应用。 目前，仅支持一个托管标识。 用户注册设备或应用后，SDK 会使用此标识并将其作为主要托管标识。 应用中的其他用户会被视为具有不受限策略设置的非托管标识。 

注意，标识被简单地定义为字符串。 标识不区分大小写，而且向 SDK 请求标识可能会返回在设置标识时最初使用的相同大小写情况。

###<a name="enabling-multiidentity"></a>启用多身份标识
默认情况下，所有应用都会被视为单一标识的应用。 通过替换 Android 清单中的以下元数据，应用可以将其自身声明为多身份标识感知。

```
<meta-data
            android:name="com.microsoft.intune.mam.MAMMultiIdentity"
            android:value="true" />
```
###<a name="setting-the-identity"></a>设置标识

开发人员可在以下级别上设置应用的标识： 
1. 进程级别， 
2. 上下文（通常为活动）级别 
3. 线程级别 

在线程级别上设置的标识可取代在上下文级别上设置的标识，而在上下文级别上设置的标识可取代在进程级别上设置的标识。 仅在合适的时候才使用在上下文上设置的标识。 例如，文件 IO 操作就不具有相关联的上下文。 MAMPolicyManager 上的以下方法可用于设置标识和检索以前设置的标识值。

```
public static void setUIPolicyIdentity(final Context context, final String identity, final MAMSetUIIdentityCallback mamSetUIIdentityCallback);

public static String getUIPolicyIdentity(final Context context);

public static MAMIdentitySwitchResult setProcessIdentity(final String identity);

public static String getProcessIdentity();

public static MAMIdentitySwitchResult setCurrentThreadIdentity(final String identity);

public static String getCurrentThreadIdentity();

/**
 * Get the currently applicable app policy. Same as MAMComponents.get(AppPolicy.class). This method does
    not take the context identity into account.
 */
public static AppPolicy getPolicy();

/**
 * Get the currently applicable app policy, taking the context
 * identity into account.
 */
public static AppPolicy getPolicy(final Context context);


public static AppPolicy getPolicyForIdentity(final String identity);

public static boolean getIsIdentityManaged(final String identity);

```
还可通过将标识设置为 NULL 清除应用的标识。 空字符串可用作永无限制的标识。 所有这些用于设置标识的方法都可通过 ``` MAMIdentitySwitchResult``` 返回结果值。 可返回的值有四个：

1.**SUCCEEDED**：标识更改成功 2.**NOT_ALLOWED**：不允许更改标识。 如果尝试切换到与该注册用户属于同一公司的另一企业用户，将出现此问题。 在当前线程上已设置另一标识时尝试设置 UI（上下文）标识，也将出现此问题。
3.**CANCELLED**：用户取消了标识更改，通常是在出现 PIN/Auth 提示时按了“后退”按钮。
4.**FAILED**：标识更改失败，原因不明。

对于设置上下文标识，会以异步方式报告结果。 如果上下文是一个活动，则不会知道标识更改是否成功，直到执行条件启动，此操作可能需要用户输入 PIN 或其完整的公司凭据。 应用应实现 ```MAMSetUIIdentityCallback``` 以接收此结果，尽管它可以为此参数传递 null。

```
public interface MAMSetUIIdentityCallback {
    void notifyIdentityResult(MAMIdentitySwitchResult identitySwitchResult); 
}
```

还可通过 MAMActivity 上的方法（而不是调用 ``` MAMPolicyManager.setUIPolicyIdentity```）直接设置活动的标识。 可使用以下方法执行此操作：

 ```public final void switchMAMIdentity(final String newIdentity);```

应用还可替代 MAMActivity 上的方法来接收尝试更改该活动标识的通知 

```public void onSwitchMAMIdentityComplete(final MAMIdentitySwitchResult result);```

**注意：**切换标识可能需要重新创建该活动。 在这种情况下，```onSwitchMAMIdentityComplete``` 回调将被直接传送到活动的新实例。

###<a name="implicit-identity-changes"></a>隐式标识更改

应用除可设置标识外，还可基于从另一启用了 MAM 的应用进入的数据更改线程或上下文的标识。 例如，如果活动从由另一 MAM 应用发送的 Intent 启动，则活动的标识将在发送 Intent 时基于另一应用的有效标识进行设置。
对于服务，将设置线程的标识，方法与对 onStart 或 onBind 调用的持续时间进行的操作类似。 在从 onBind 返回的 Binder 中进行调用也将暂时设置线程标识。
在 ```ContentProvider``` 中进行调用同样会对其持续时间设置线程标识。
此外，用户与活动的交互可能导致隐式标识切换。
例如，用户在 ```Resume``` 期间取消授权提示将导致隐式切换到空标识。
应用有机会识别这些更改，在某些情况下，可以禁止这些更改（如需要）。 ```MAMService``` 和 ```MAMContentProvider``` 可以公开以下方法，其中子类可以重写：

```
public void onMAMIdentitySwitchRequired(final String identity,
    final AppIdentitySwitchResultCallback callback);
```
如果是 ```MAMActivity``` ，此方法中还会存在其他参数： 
```
public void onMAMIdentitySwitchRequired(final String identity, 
    final AppIdentitySwitchReason reason,
    final AppIdentitySwitchResultCallback callback);
```
```AppIdentitySwitchReason``` 可以捕获隐式切换的源，且可接受值 ```CREATE```、```RESUME_CANCELLED``` 和 ```NEW_INTENT```。  因活动继续而导致显示 PIN、身份验证或其他相容 UI 以及当用户尝试取消该 UI（通常通过使用“后退”按钮）时，将使用 ```RESUME_CANCELLED``` 原因。
```AppIdentitySwitchResultCallback``` 如下所示：
```
public interface AppIdentitySwitchResultCallback {
    /**
     * @param result
     *            whether the identity switch can proceed.
     */
    void reportIdentitySwitchResult(AppIdentitySwitchResult result);
}
```
其中 ```AppIdentitySwitchResult``` 是 ```SUCCESS``` 或 ```FAILURE```。 

对于所有隐式标识更改（通过由 ```MAMService.onMAMBind``` 返回的 Binder 完成的更改除外），都会调用 ```onMAMIdentitySwitchRequired``` 方法。 此外，原因为 ```RESUME_CANCELLED``` 和 ```reportIdentitySwitchResult(SUCCESS)``` 时，```onMAMIdentitySwitchRequired``` 的默认实现会立即调用 ```reportIdentitySwitchResult(FAILURE)```。 

大多数应用都无需使用其他方法来阻止或延迟标识切换，但是如果应用需要执行此操作，则必须考虑以下几点：*如果标识切换被阻止，其结果与 ```Receive``` 共享设置禁止数据进入的结果一样。*如果服务在主线程上运行，则**必须**同步调用 ```reportIdentitySwitchResult``` 或挂起 UI 线程。 
*对于 ```Activity``` 创建，将在 ```onMAMCreate``` 之前调用 ```onMAMIdentitySwitchRequired```。如果应用必须显示 UI 来确定是否允许切换标识，则必须使用另一活动显示该 UI。*在活动中，要求切换到空标识且其原因相当于 ```RESUME_CANCELLED``` 时，则该应用必须修改已恢复的活动来显示与该标识切换相一致的数据。  如果无法做到这一点，则该应用应拒绝切换，且将会再次要求用户遵循恢复标识的策略（例如，在 PIN 输入屏幕上显示）。 

**注意：**多身份标识应用将始终接收来自托管和非托管应用的传入数据。 应用将负责用托管的方式来处理托管标识的数据。 如果请求的标识由 ```(MAMPolicyManager.getIsIdentityManaged)``` 管理，但此应用无法使用该帐户（例如，因为必须首先在应用中设置帐户，如电子邮件帐户），则应拒绝标识切换。

##<a name="file-protection"></a>文件保护
每个文件基于线程和进程标识在创建时都具有与之关联的标识。 此标识可用于文件加密和选择性擦除。 但只有文件的标识具有要求加密的策略时才会进行加密。 SDK 的默认选择性擦除将仅擦除与擦除请求的标识相关联的文件。 应用可使用 ```MAMFileProtectionManager``` 查询或更改文件的标识
```
public final class MAMFileProtectionManager {

    /**
     * Protect a file. This will synchronously trigger whatever protection is required for the file, and will tag the file for
     * future protection changes.
     * 
     * @param identity
     *            Identity to set.
     * @param file
     *            File to protect.
     * @throws IOException
     *             If the file cannot be changed.
     */
    public static void protect(final File file, final String identity) throws IOException;

    /**
     * Get the protection info on a file.
     * 
     * @param file
     *            File or directory to get information on.
     * @return File protection info, or null if there is no protection info.
     * @throws IOException
     *             If the file cannot be read or opened.
     */
    public static MAMFileProtectionInfo getProtectionInfo(final File file) throws IOException;
}

public interface MAMFileProtectionInfo {
String getIdentity();
}
```

**注意：**文件标识标记可识别脱机模式。 应考虑以下几点。
* 如果未安装公司门户，则无法将文件标记为标识。 
* 如果已安装公司门户，但应用不具有策略，则无法可靠地将文件标记为标识。
* 文件标识标记可用时，所有之前创建的文件都将被视为专用（属于空字符串标识），除非应用先前已作为单身份标识托管应用，在这种情况下，该应用被视为归属于已注册用户。

###<a name="data-protection"></a>数据保护
无法将文件标记为属于多身份标识。 对于必须存储属于同一文件中不同用户的数据的应用，可使用由 ```MAMDataProtectionManager``` 提供的功能手动执行此操作。 这可让应用加密数据并将其绑定到特定用户。 经过加密的数据适合存储到文件中的磁盘。 可查询与标识相关联的数据，并且可随后解密此数据。 

```
public final class MAMDataProtectionManager {
    /**
     * Protect a stream. This will return a stream containing the protected 
 * input.
     * 
     * @param identity
     *            Identity to set.
     * @param input
     *            Input data to protect, read sequentially. This function 
 *            will change the position of the stream but may not have
     *            read the entire stream by the time it returns. The 
 *            returned stream will wrap this one. Calls to read on the
     *            returned stream may cause further reads on the original 
 *            input stream. Callers should not expect to read directly
     *            from the input stream after passing it to this method. 
 *            Calling close on the returned stream will close this one.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be protected
     */
    public static InputStream protect(final InputStream input, final String identity);

    /**
     * Protect a byte array. This will return protected bytes.
     * 
     * @param identity
     *            Identity to set.
     * @param input
     *            Input data to protect.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be protected
     */
    public static byte[] protect(final byte[] input, final String identity) throws IOException;

    /**
     * Unprotect a stream. This will return a stream containing the 
 * unprotected input.
     * 
     * @param input
     *            Input data to protect, read sequentially.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be unprotected
     */
    public static InputStream unprotect(final InputStream input) throws IOException;

    /**
     * Unprotect a byte array. This will return unprotected bytes.
     * 
     * @param input
     *            Input data to protect.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be unprotected
     */
    public static byte[] unprotect(final byte[] input) throws IOException;

    /**
     * Get the protection info on a stream.
     * 
     * @param input
     *            Input stream to get information on. Either this input 
 *            stream must have been returned by a previous call to 
     *            protect OR input.markSupported() must return true. 
 *            Otherwise it will be impossible to get protection info 
 *            without advancing the stream position. The stream must be 
 *            positioned at the beginning of the protected data.
     * @return Data protection info, or null if there is no protection 
 *            info.
     * @throws IOException
     *             If the input cannot be read.
     */
    public static MAMDataProtectionInfo getProtectionInfo(final InputStream input) throws IOException;

    /**
     * Get the protection info on a stream.
     * 
     * @param input
     *            Input bytes to get information on. These must be bytes 
 *            returned by a previous call to protect() or a copy of 
 *            such bytes.
     * @return Data protection info, or null if there is no protection 
 *            info.
     * @throws IOException
     *             If the input cannot be read.
     */
    public static MAMDataProtectionInfo getProtectionInfo(final byte[] input) throws IOException;
}
```
##<a name="content-providers"></a>内容提供程序
如果应用通过 ```ContentProvider``` 而不是 ```ParcelFileDescriptor``` 提供潜在公司数据，则该应用必须调用 ```MAMContentProvider``` 方法 ```isProvideContentAllowed(String)```，为所有者 ```UPN``` 传递内容。 如果此函数返回 false，则此内容可能不会返回到调用方。 通过内容提供程序返回的文件描述符将自动基于文件标识进行处理。

##<a name="selective-wipe"></a>选择性擦除
如果应用注册 ```WIPE_USER_DATA``` 通知，则它无法享有 SDK 默认的选择性擦除行为的好处。 对于多身份标识应用，这一点可能更为重要，因为 MAM 默认的选择性擦除将仅擦除与要擦除的标识匹配的文件。 如果构建的是多身份标识应用，则可注册 ```WIPE_USER_AUXILIARY_DATA```，以便你利用 SDK 默认擦除行为的优势。 此通知将在执行 SDK 默认选择性擦除的前一秒发出。 请注意，应用不能同时注册 ```WIPE_USER_DATA``` 和 ```WIPE_USER_AUXILIARY_DATA```。

## <a name="known-platform-limitations"></a>已知平台限制 

### <a name="file-size-limitations"></a>文件大小限制 

在 Android 上，对于在没有 ProGuard 的情况下运行的大型基本代码，Dalvik 可执行文件格式的限制可能会成为问题。 具体而言，可能会出现以下限制： 

* 对字段的 65K 限制。

* 对方法的 65K 限制。

包括许多项目时，每个 android:package 都会获得 R 的副本，这会随着库的添加时而显著增加字段数。 以下建议可能有助于减轻此限制：
 
* 所有库项目都应尽可能共享同一个 android:package。 这不会偶尔在字段中失败，因为它仅仅是生成时间问题。   此外，较新版本的 Android SDK 会预处理 DEX 文件以删除某些冗余。 这甚至可更进一步地减少与字段之间的距离。

* 使用提供的最新 Android SDK 生成工具。

* 删除所有不必要和未使用的库（例如 `android.support.v4`）

### <a name="policy-enforcement-limitations"></a>策略强制实施限制

**屏幕捕获**：SDK 无法在已完成 Activity.onCreate 的活动中强制执行新的屏幕捕获设置值。 这可能会产生一段时间，在这段时间内，应用配置为禁用屏幕截图，但仍可以拍摄屏幕截图。

**使用内容解析程序*：传输或接收策略可能会阻止或部分阻止使用内容解析程序访问其他应用中的内容提供程序。 这将导致 ContentResolver 方法返回 null 或引发失败值（例如 `openOutputStream` 在受阻时会引发 `FileNotFoundException` ）。 应用可以通过进行以下调用，来确定是否策略已导致（或策略会导致）通过内容解析程序写入数据失败：

    MAMComponents.get(AppPolicy.class).getIsSaveToLocationAllowed(contentURI)

**导出的服务**：Intune App SDK 中包括的 `AndroidManifest.xml` 文件包含 `MAMNotificationReceiverService`，它必须是导出的服务才能允许公司门户将通知发送到已启用应用。 服务会检查调用方以确保仅允许公司门户发送通知。 

## <a name="recommended-android-best-practices"></a>建议使用的 Android 最佳做法 

Intune SDK 会维护 Android API 提供的协定，但可能会由于策略实施而更频繁地触发失败条件。 这些 Android 最佳做法可减少发生失败的可能性： 

* 可能返回 null 的 Android SDK 函数现在为 null 的可能性会更高。  要最大程度减小问题，请确保在正确的位置进行 null 检查。

* 可以进行检查的功能必须通过其 SDK API 进行检查。

* 派生的任何函数都必须调用到其超类版本。

* 避免以不明确的方式使用任何 API。 例如，不检查 requestCode 的 `Activity.startActivityForResult/onActivityResult` 会导致奇怪的行为。






<!--HONumber=Oct16_HO5-->


