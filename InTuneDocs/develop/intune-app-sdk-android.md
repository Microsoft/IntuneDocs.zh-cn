---
# required metadata

title: Microsoft Intune App SDK for Android 开发人员指南 | Microsoft Intune
description:
keywords:
author: Msmbaldwin
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune App SDK for Android 开发人员指南

> [!NOTE] 建议首先阅读 [Intune App SDK 概述](intune-app-sdk.md)，该文档涵盖 SDK 的当前功能并介绍了如何在每个受支持的平台上准备集成。 

# 该 SDK 包含的内容 

Intune App SDK for Android 是没有外部依赖项的标准 Android 库。 
该 SDK 由以下内容组成:  

* **`Microsoft.Intune MAM.SDK.jar`**：在应用中启用 MAM，以及启用与 Microsoft Intune 公司门户应用的互操作性所需的接口。 应用必须指定它作为 Android 库引用。

*  **`Microsoft.Intune.MAM.SDK.Support.v4.jar`**：在利用 android v4 支持库的应用中启用 MAM 所需的接口。  需要此支持的应用必须直接引用该 jar 文件。 

* **`Microsoft.Intune.MAM.SDK.Support.v7.jar`**：在利用 android v7 支持库的应用中启用 MAM 所需的接口。   需要此支持的应用必须直接引用该 jar 文件

* **资源目录**：SDK 所依赖的资源（如字符串）。 

* **`Microsoft.Intune.MAM.SDK.aar`**：SDK 组件（Support.V4 和 Support.V7 jar 除外）。 如果生成系统支持 AAR 文件，则此文件可以用于替代各个组件。

* **`AndroidManifest.xml`**：其他入口点和库要求。 

* **`THIRDPARTYNOTICES.TXT`**：一个归属声明，用于确认将编译到应用中的第三方和/或 OSS 代码。 

# 惠? 

Intune App SDK 是已编译的 Android 项目。 因此，应用用于其最低或目标 API 版本的 Android 版本在很大程度上是不可知的。 SDK 支持 Android API 14 (Android 4.0+) 到 Android 24。 

# Intune App SDK 的使用方式 

Intune App SDK 需要更改应用的源代码以启用应用管理策略。 这通过将 android 基类替换为等效的托管类（在文档使用前缀 `MAM`。 SDK 类介于 Android 基类与应用自己的该类派生版本之间。  以一个活动为例，你最终会得到类似于下面这样的继承层次结构： `Activity ->MAMActivity->AppSpecificActivity`。

当 `AppSpecificActivity` 要与其父级（例如 `super.onCreate())` 交互）时，`MAMActivity` 是超类（尽管处于继承层次结构中并替换了几个方法）。 Android 应用具有单一模式，可以通过其上下文对象访问整个系统。  另一方面，结合了 Intune App SDK 的应用具有双模式，因为应用会继续通过上下文对象访问系统，但是根据所使用的基本活动，上下文对象将由 Android 提供，或者以智能方式在系统的受限视图与 Android 提供的上下文之间进行多路复用。

对于 MAM 策略的启用，Intune App SDK for Android 依赖于设备上是否存在公司门户应用。 当公司门户应用不存在时，已启用 MAM 应用的行为不会更改，会如同任何其他移动应用一样进行操作。 当公司门户已安装并且具有用户策略时，SDK 入口点会以异步方式初始化。 仅当 Android 最初创建进程时才需要初始化。 在初始化过程中，会建立与公司门户应用的连接并下载应用限制策略。  

# 如何与 Intune App SDK 集成
 
如前所述，该 SDK 需要更改应用的源代码以启用应用管理策略。 下面是在应用中启用 MAM 所需的步骤： 

## 将类、方法和活动替换为 MAM 等效项（必需） 

* Android 基类必须替换为其 MAM 等效项。 为此，请查找下表中列出的类的所有实例，并将它们替换为 Intune App SDK 等效项。  

    | Android 类 | Intune App SDK 替换项 |
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
    | android.app.PendingIntent | MAMPendingIntent |
    | android.app.Service | MAMService |
    | android.app.TabActivity | MAMTabActivity |
    | android.app.TaskStackBuilder | MAMTaskStackBuilder |
    | android.app.backup.BackupAgent | MAMBackupAgent |
    | android.app.backup.BackupAgentHelper | MAMBackupAgentHelper |
    | android.app.backup.FileBackupHelper | MAMFileBackupHelper |
    | android.app.backup.SharePreferencesBackupHelper | MAMSharedPreferencesBackupHelper |
    | android.content.BroadcastReceiver | MAMBroadcastReceiver |
    | android.content.ContentProvider | MAMContentProvider |
    | android.os.Binder | MAMBinder* |
    | android.provider.DocumentsProvider | MAMDocumentsProvider |
    | android.preference.PreferenceActivity | MAMPreferenceActivity |

    *仅当未从 AIDL 接口生成 Binder 时，才需要将 Binder 替换为 MAMBinder。

    **Microsoft.Intune.MAM.SDK.Support.v4.jar**：

    | Android 类 Intune MAM | SDK 替换项 |
    |--|--|
    | android.support.v4.app.DialogFragment | MAMDialogFragment
    | android.support.v4.app.FragmentActivity | MAMFragmentActivity
    | android.support.v4.app.Fragment | MAMFragment
    | android.support.v4.app.TaskStackBuilder | MAMTaskStackBuilder
    | android.support.v4.content.FileProvider | MAMFileProvider
    
    **Microsoft.Intune.MAM.SDK.Support.v7.jar**：

    |Android 类 | Intune MAM SDK 替换项 |
    |--|--|
    |android.support.v7.app.ActionBarActivity | MAMActionBarActivity |


* 使用已由其 MAM 等效项所替代的 android 入口点时，必须使用入口点生命周期的备用版本（类 `MAMApplication`除外）。

    例如，从 `MAMActivity`派生（而不是替代 `onCreate` 并调用 `super.onCreate`）时，活动必须替代 `onMAMCreate` 并调用`uper.onMAMCreate`。 这可以在特定情况下限制活动启动（及其他）。 

# 启用需要应用参与的功能 

SDK 无法单独实现某些策略。 为了使应用可以控制这些功能的行为，我们公开了几个 API，可以在下面包含的 `AppPolicy` 接口中找到它们。  

    /**
     * External facing app policies.
     */
    public interface AppPolicy {
        /**
         * Restrict where an app can save personal data.
         * 
         * @return True if the app is allowed to save to personal data stores;
         *         false otherwise.
         */
        boolean getIsSaveToPersonalAllowed();
    
        /**
         * Check if policy prohibits saving to a content provider location.
         * 
         * @param location
         *            a content URI to check
         * @return True if location is not a content URI or if policy does not 
         *         prohibit saving to the content location.
         */
        boolean getIsSaveToLocationAllowed(android.net.Uri location); 
    
        /**
         * Whether the SDK PIN prompt is enlightened for the app.
         * 
         * @return True if the PIN is enabled. False otherwise.
         */
        boolean getIsPinRequired();
        /**
         * Whether the Intune Managed Browser is required to open web links.
         *
         * @return True if the Managed Browser is required, false otherwise
         */
        boolean getIsManagedBrowserRequired();
    }

## 对应用保存行为启用 IT 管理员控制

许多应用可实现允许最终用户在本地保存文件或保存到其他服务的功能。 Intune App SDK 允许 IT 管理员通过应用他们认为适合于组织的策略限制来防止数据泄漏。  管理员可以控制的策略之一是最终用户是否可以保存到个人数据存储。 这包括保存到本地位置、SD 卡或备份服务。 启用该功能需要应用参与。 如果应用允许直接从应用保存到个人或云位置，则必须实现此功能以确保 IT 管理员可以控制是否允许保存到某个位置。 以下 API 使应用可以了解按照当前管理策略，是否允许保存到个人存储。 应用随后可以强制执行策略，因为它知道最终用户可以通过应用来使用个人数据存储。  

要确定是否强制执行策略，应用可以进行以下调用： 

    MAMComponents.get(AppPolicy.class).getIsSaveToPersonalAllowed();

**注意**：MAMComponents.get(AppPolicy.class) 会始终返回非 null 应用策略（即使设备或应用不受管理）。 

## 允许应用检测是否需要 PIN 策略
 
 在其他一些策略中，应用可能希望禁用其部分功能，以便不重复 Intune App SDK 中的功能。 例如，如果应用具有其自己的 PIN 用户体验，则在 SDK 配置为要求最终用户输入 PIN 时，它可能希望禁用该体验。 

要确定 PIN 策略是否配置为定期需要 PIN 输入，则应用可以进行以下调用： 

    MAMComponents.get(AppPolicy.class).getIsPinRequired();

## 注册来自 SDK 的通知  

Intune App SDK 允许应用控制特定策略（如远程擦除策略）由 IT 管理员使用时的行为。 为此，需要通过创建 `MAMNotificationReceiver` 类并向 `MAMNotificationReceiverRegistry`。 这通过在  `App.onCreate`中提供接收方以及接收方要接收的通知类型来实现，如下面的示例所示：
 
    @Override
      public void onCreate() {
            super.onCreate();
    MAMComponents.get(MAMNotificationReceiverRegistry.class).registerReceiver(
    new ToastNotificationReceiver(), MAMNotificationType.WIPE_USER_DATA);
    }

`MAMNotificationReceiver` 只接收通知。 某些通知由 SDK 直接处理，而其他通知需要应用参与。 应用必须从通知返回 true 或 false。 它必须始终返回 true，除非它由于通知失败而尝试执行某种操作。 此失败可能会报告给 Intune 服务，例如应用指示它未能擦除用户数据时。 可在 `MAMNotificationReceiver.onReceive`中安全地进行阻止；其回调不会在 UI 线程上运行。 

下面显示了 SDK 中定义的 MAMNotificationReceiver 接口： 

    /**
     * The SDK is signaling that a MAM event has occurred. 
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

以下通知会发送到应用，其中一些可能需要应用参与： 

* **`WIPE_USER_DATA`通知**：此通知在 `MAMUserNotification` 类中进行发送。 收到此通知时，应用应删除与随 `MAMUserNotification`。 此通知当前在 Intune 服务取消注册过程中进行发送。 用户的主名称通常在注册过程中进行指定。 如果注册了此通知，则应用必须确保所有用户数据都已删除。 如果你未注册它，则会执行默认选择性擦除行为。 

* **`WIPE_USER_AUXILIARY_DATA` 通知**：如果应用希望 Intune App SDK 执行默认擦除，但是在擦除进行时仍想删除一些辅助数据，则应用可以注册此通知。  

* **`REFRESH_POLICY` 通知**：此通知在 MAMNotification 中进行发送，而不包含任何其他信息。 收到此通知时，任何缓存的策略都必须被视为不再失效，因此应检查策略内容。 这通常由 SDK 处理，但是如果以任何持久方式使用策略，则应由应用处理。 

## 挂起意向和方法 

从一个 MAM 入口点派生之后，可以按通常方法使用上下文，以便启动活动（使用其 `PackageManager`）等等。  `PendingIntents` 是此规则的例外情况。 调用这种类时，需要更改类名。 例如，必须使用 `MAMPendingIntents.get*`，而不是使用 `PendingIntent.get*`。 

在某些情况下，Android 类中提供的方法已在 MAM 替换类中标记为最终方法。 在此情况下，MAM 替换类会提供应改为替代的具有类似名称的方法（通常使用“MAM”作为后缀）。 例如，应替代 `ContentProvider.query`，而不是替代 `MAMContentProvider.queryMAM`。 Java 编译器应强制执行最终限制，以防止意外替代原始方法（而不是 MAM 等效项）。 

# 保护备份数据 

自 Android Marshmallow (API 23) 开始，Android 现在有两种方法可供应用来备份其数据。 这些选项可在应用中使用，需要不同步骤来确保正确应用 MAM 数据保护。 你可以查看下表以了解有关正确数据保护行为所需的对应操作的快速概览。  还可以在 [Android 开发人员数据备份指南](http://developer.android.com/guide/topics/data/backup.html.)。 

## 自动完整备份

在 Android M 中，当在 Android M 设备上运行时，Android 开始向应用提供自动完整备份（不考虑目标 API）。 只要 `android:allowBackup` 属性不是 false，应用便会收到其应用的完整、未筛选备份。 这会带来数据泄漏风险，因此 SDK 要求进行下表中概括的更改以确保应用数据保护。  需遵循下面概括的准则以正确保护客户数据，这十分重要。  如果设置 `android:allowBackup=false` ，则操作系统绝不会将应用排队以进行备份，并且你没有针对 MAM 的进一步操作，因为没有备份
 
 ## “键/值”备份

此选项对所有 API 可用，并使用 `BackupAgent` 和 `BackupAgentHelper`。 

### 使用 BackupAgentHelper

`BackupAgentHelper` 在本机 Android 功能和 MAM 集成这两个方面，比 `BackupAgent` 的实现要简单得多。 `BackupAgentHelper` 允许开发人员分别将整个文件和共享首选项注册到 `FileBackupHelper` 或 `SharedPreferencesBackupHelper`，它们随后会在创建时添加到 `BackupAgentHelper`。 

### 使用 BackupAgent

`BackupAgent` 使你可以更明确地表示进行备份的数据。 但是，此选项意味着你无法利用 Android 备份框架。  因为主要由你负责实现，所以确保从 MAM 进行适当数据保护需要更多步骤。 由于大部分工作由你（即开发人员）来完成，因此会稍微更多地涉及 MAM 集成。 

#### 应用没有备份代理
  
这些是 `Android:allowbBackup =true`：

##### 根据配置文件进行的完整备份： 

在清单中的 `com.microsoft.intune.mam.FullBackupContent` 元数据标记下提供资源。 例如：
    `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />`

在 `<application>` 标记中添加以下属性： `android:fullBackupContent="@xml/my_scheme"`，其中 `my_scheme` 是应用中的 XML 资源。 

##### 完整备份（不带扩展） 

在清单中提供标记，如 `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />` 
 
在 `<application>` 标记中添加以下属性：`android:fullBackupContent="true"`。

#### 应用具有备份代理

遵循上面概括的 `BackupAgent` 和 `BackupAgentHelper` 部分中的建议 

考虑切换为使用我们的 `MAMDefaultFullBackupAgent`，它在 Android M 上提供轻松备份。 

### 在备份之前

开始备份之前，必须检查是否确实允许备份你计划备份的文件或数据缓冲区。 我们在 `isBackupAllowed` 和 `MAMFileProtectionManager` 和 `MAMDataProtectionManager` 函数用于确定这一点。 如果不允许备份文件或数据缓冲区，则你不应尝试继续在备份中利用它。

在备份过程中的某个时候，如果你希望备份在步骤 1 中检查的文件的标识，则必须调用 `backupMAMFileIdentity(BackupDataOutput data, File … files)`（使用你计划从中提取数据的文件）。 这会自动为你创建新的备份实体并将它们写入 `BackupDataOutput` 。 这些实体会在还原时自动进行使用。 

## 配置 Azure 目录身份验证库 (ADAL)  

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

### 常用 ADAL 配置 

以下是上文说明的值的常用配置。 

#### 应用未集成 ADAL

* 颁发机构必须设置为在其中配置了 AAD 帐户的所需环境。

* SkipBroker 必须设置为 true。

#### 应用集成了 ADAL

* 颁发机构必须设置为在其中配置了 AAD 帐户的所需环境。

* 客户端 ID 必须设置为应用的客户端 ID。

* `NonBrokerRedirectURI` 应设置为应用的有效重定向 URI。
    * Or `urn:ietf:wg:oauth:2.0:oob` 必须配置为有效 AAD 重定向 URI。

* SkipBroker 必须设置为 false（或不存在）

* AAD 必须配置为接受代理重定向 URI。

#### 应用集成了 ADAL，但不支持 AAD 验证器应用。

* 颁发机构必须设置为在其中配置了 AAD 帐户的所需环境。

* 客户端 ID 必须设置为应用的客户端 ID。

* `NonBrokerRedirectURI` 必须设置为应用的有效重定向 URI。

    * Or `urn:ietf:wg:oauth:2.0:oob` 应配置为有效 AAD 重定向 URI。

## 如何在 SDK 中启用日志记录 

日志记录通过 `java.util.logging` 框架进行。 要接收日志，请按照 [Java 技术指南](http://docs.oracle.com/javase/6/docs/technotes/guides/logging/overview.html)。 根据应用， `App.onCreate` 通常是启动日志记录的最佳位置。 请注意，日志消息按类名进行键控（这可能比较模糊）。

# 已知平台限制 

## 文件大小限制 

在 Android 上，对于在没有 ProGuard 的情况下运行的大型基本代码，Dalvik 可执行文件格式的限制可能会成为问题。 具体而言，可能会出现以下限制： 

* 对字段的 65K 限制。

* 对方法的 65K 限制。

包括许多项目时，每个 android:package 都会获得 R 的副本，这会随着库的添加时而显著增加字段数。 以下建议可能有助于减轻此限制：
 
* 所有库项目都应尽可能共享同一个 android:package。 这不会偶尔在字段中失败，因为它仅仅是生成时间问题。   此外，较新版本的 Android SDK 会预处理 DEX 文件以删除某些冗余。 这甚至可更进一步地减少与字段之间的距离。

* 使用提供的最新 Android SDK 生成工具。

* 删除所有不必要和未使用的库（例如 `android.support.v4`）

## 策略强制实施限制

**屏幕捕获**：SDK 无法在已完成 Activity.onCreate 的活动中强制执行新的屏幕捕获设置值。 这可能会产生一段时间，在这段时间内，应用配置为禁用屏幕截图，但仍可以拍摄屏幕截图。

**使用内容解析程序*：传输或接收策略可能会阻止或部分阻止使用内容解析程序访问其他应用中的内容提供程序。 这将导致 ContentResolver 方法返回 null 或引发失败值（例如 `openOutputStream` 在受阻时会引发 `FileNotFoundException` ）。 应用可以通过进行以下调用，来确定是否策略已导致（或策略会导致）通过内容解析程序写入数据失败：

    MAMComponents.get(AppPolicy.class).getIsSaveToLocationAllowed(contentURI)

**导出的服务**：Intune App SDK 中包括的 `AndroidManifest.xml` 文件包含 `MAMNotificationReceiverService`，它必须是导出的服务才能允许公司门户将通知发送到已启用应用。 服务会检查调用方以确保仅允许公司门户发送通知。 

# 建议使用的 Android 最佳做法 

Intune SDK 会维护 Android API 提供的协定，但可能会由于策略实施而更频繁地触发失败条件。 这些 Android 最佳做法可减少发生失败的可能性： 

* 可能返回 null 的 Android SDK 函数现在为 null 的可能性会更高。  要最大程度减小问题，请确保在正确的位置进行 null 检查。

* 可以进行检查的功能必须通过其 SDK API 进行检查。

* 派生的任何函数都必须调用到其超类版本。

* 避免以不明确的方式使用任何 API。 例如，不检查 requestCode 的 `Activity.startActivityForResult/onActivityResult` 会导致奇怪的行为。


<!--HONumber=May16_HO2-->


