---
title: 用于 Android 的 Microsoft Intune App SDK 开发人员指南
description: 用于 Android 的 Microsoft Intune App SDK 支持将 Intune 移动应用管理 (MAM) 集成到 Android 应用中。
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/14/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: c8c5be1d7a02c2c8329afe05dcdce22f48c49d05
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503491"
---
# <a name="microsoft-intune-app-sdk-for-android-developer-guide"></a>用于 Android 的 Microsoft Intune App SDK 开发人员指南

> [!NOTE]
> 建议先阅读 [Intune App SDK 概述](app-sdk.md)，该文档涵盖 SDK 的当前功能并介绍了如何在每个受支持的平台上准备集成。

通过 Microsoft Intune App SDK for Android，可将 Intune 应用保护策略（也称为 **APP** 或 MAM 策略）合并到本机 Android 应用中。 Intune 托管的应用程序是指与 Intune App SDK 集成的应用程序。 当 Intune 主动托管应用时，Intune 管理员可将应用保护策略轻松部署到该应用。


## <a name="whats-in-the-sdk"></a>SDK 包含的内容

Intune App SDK 包括下列文件：

* **Microsoft.Intune.MAM.SDK.aar**：SDK 组件（支持库 JAR 文件除外）。
* **Microsoft.Intune.MAM.SDK.Support.v4.jar**：在使用 Android v4 支持库的应用中启用 MAM 所需的类。
* **Microsoft.Intune.MAM.SDK.Support.v7.jar**：在使用 Android v7 支持库的应用中启用 MAM 所需的类。
* **Microsoft.Intune.MAM.SDK.Support.v17.jar**：在使用 Android v17 支持库的应用中启用 MAM 所需的类。 
* **Microsoft.Intune.MAM.SDK.Support.Text.jar**：在使用包 `android.support.text` 中 Android 支持库类的应用中启用 MAM 所需的类。
* **Microsoft.Intune.MAM.SDK.DownlevelStubs.aar**：此 AAR 包含 Android 系统类的存根，它们仅存在于较新的设备上，由 `MAMActivity` 中的方法引用。 较新的设备将忽略这些存根类。 仅当应用对从 `MAMActivity` 派生的类执行反射时，此 AAR 才是必需的，而大多数应用无需包含它。 AAR 包含用于排除其所有类的 ProGuard 规则。
* **com.microsoft.intune.mam.build.jar**：[帮助集成 SDK](#build-tooling) 的一个 Gradle 插件。
* **CHANGELOG.txt**：提供每个 SDK 版本中所做的更改记录。
* **THIRDPARTYNOTICES.TXT**：一个归属声明，用于确认将在应用中编译的第三方和/或 OSS 代码。

## <a name="requirements"></a>要求

### <a name="android-versions"></a>Android 版本
此 SDK 支持 Android API 19 (Android 4.4+) 到 Android API 28 (Android 9.0)。

### <a name="company-portal-app"></a>公司门户应用
对于应用保护策略的启用，用于 Android 的 Intune App SDK 依赖于设备上是否存在[公司门户](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)应用。 公司门户从 Intune 服务中检索应用保护策略。 应用初始化时，它会加载策略和代码以强制从公司门户实施该策略。

> [!NOTE]
> 如果设备上未安装公司门户应用，则 Intune 托管的应用的行为与不支持 Intune 应用保护策略的普通应用相同。

对于无需设备注册的应用保护， _**不会**_ 要求用户使用公司门户应用注册设备。

## <a name="sdk-integration"></a>SDK 集成

### <a name="sample-app"></a>示例应用
要通过示例了解如何与 Intune App SDK 适当集成，请参阅 [GitHub](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App)。 本示例使用 [Gradle 生成插件](#gradle-build-plugin)。

### <a name="referencing-intune-app-libraries"></a>引用 Intune 应用库

Intune App SDK 是没有外部依赖项的标准 Android 库。 Microsoft.Intune.MAM.SDK.aar 既包含启用应用保护策略所需的接口，同时也包含与 Microsoft Intune 公司门户应用进行互操作所必需的代码  。

Microsoft.Intune.MAM.SDK.aar 必须指定为 Android 库引用  。 要执行此操作，请在 Android Studio 中打开应用项目，然后转到“文件”>“新建”>“新模块”  ，选择“导入 .JAR/.AAR 包”  。 选择我们的 Android 存档包 Microsoft.Intune.MAM.SDK.aar 为 .AAR 创建模块。 右键单击包含应用代码的一个或多个模块，然后转到“模块设置” > “依赖项选项卡” > “+ 图标” > “模块依赖项”，选择刚创建的 MAM SDK AAR 模块，然后选择“确定”      。 这将确保生成项目时一起编译模块和 MAM SDK。

此外，Microsoft.Intune.MAM.SDK.Support.XXX.jar 库还包含相应 `android.support.XXX` 库的 Intune 变体  。 它们并没有内置在 Microsoft.Intune.MAM.SDK.aar 中，以防应用不需要依赖支持库。

#### <a name="proguard"></a>ProGuard

如果 [ProGuard](http://proguard.sourceforge.net/)（或任何其他收缩/混淆机制）用作一个生成步骤，SDK 则具有必须包含的其他配置规则。 当生成中包含 .AAR 时，我们的规则会自动集成到 proguard 步骤中，并保留必要的类文件。

Azure Active Directory 身份验证库 (ADAL) 可能有其自己的 ProGuard 限制。 如果应用集成 ADAL，则必须遵循 ADAL 文档中的这些限制。

### <a name="policy-enforcement"></a>策略强制
Intune App SDK 是一个 Android 库，使应用能够支持和参与 Intune 策略的强制执行。 

大多数策略都是半自动强制执行的，但某些策略需要[来自应用的显式参与才能强制执行](#enable-features-that-require-app-participation)。
无论你是要执行源集成，还是使用生成工具进行集成，都需要为提供要求显式参与的策略的代码。

对于自动强制执行的策略，需要应用将从多个 Android 基类的继承替换为从 MAM 等效项的继承，并同样地将对某些 Android 系统服务类的调用替换为对 MAM 等效项的调用。 [下面](#class-and-method-replacements)详细介绍了所需的具体替换内容，可以使用源集成手动执行，也可以通过生成工具自动执行。

### <a name="build-tooling"></a>生成工具
此 SDK 提供了可以自动执行 MAM 等效项替换的生成工具（用于 Gradle 生成的一个插件和用于非 Gradle 生成的一个命令行工具）。 这些工具将转换由 Java 编译生成的类文件，并且不会修改原始源代码。

工具仅执行[直接替换](#class-and-method-replacements)。 它们不执行任何更复杂的 SDK 集成，例如[另存为策略](#enable-features-that-require-app-participation)、[多个标识](#multi-identity-optional)、[App-WE 注册](#app-protection-policy-without-device-enrollment)、[AndroidManifest 修改](#manifest-replacements)或 [ADAL 配置](#configure-azure-active-directory-authentication-library-adal)，因此在应用完全启用 Intune 之前必须完成这些集成。 请仔细查看本文档的其余部分以了解与应用相关的集成点。

> [!NOTE]
> 可以针对已通过手动替换执行了部分或完整的 MAM SDK 源集成的项目运行工具。 你的项目必须仍将 MAM SDK 列为依赖项。

### <a name="gradle-build-plugin"></a>Gradle 生成插件
如果应用不使用 gradle 进行生成，请跳转至[与命令行工具集成](#command-line-build-tool)。 

应用 SDK 插件作为 SDK 的一部分 GradlePlugin/com.microsoft.intune.mam.build.jar 分发  。 若要使 Gradle 能够找到插件，必须将其添加到 buildscript classpath 中。 插件依赖于也必须被添加的 [Javassist](https://jboss-javassist.github.io/javassist/)。 若要将这些添加到 classpath 中，请将以下内容添加到根 `build.gradle`

```groovy
buildscript {
    repositories {
        jcenter()
    }
    dependencies {
        classpath "org.javassist:javassist:3.22.0-GA"
        classpath files("$PATH_TO_MAM_SDK/GradlePlugin/com.microsoft.intune.mam.build.jar")
    }
}
```

然后，在 APK 项目的 `build.gradle` 文件中，只需将插件应用为
```groovy
apply plugin: 'com.microsoft.intune.mam'
```

默认情况下，此插件将仅在 `project` 依赖项上执行操作  。
测试编译不会受到影响。 可以提供配置以列出
*  要排除的项目
*  [要包括的外部依赖项](#usage-of-includeexternallibraries) 
*  要从处理中排除的特定类
*  要从处理中排除的变体。 这些可能是指一个完整的变体名称或一种口味。 例如
     * 如果应用具有 {`savory`, `sweet`} 和 {`vanilla`, `chocolate`} 口味的生成类型 `debug` 和 `release`，则可以指定
     * `savory` 以排除具有咸辣口味的所有变体，或指定 `savoryVanillaRelease` 以仅排除此变体。

#### <a name="example-partial-buildgradle"></a>部分 build.gradle 示例

```groovy

apply plugin: 'com.microsoft.intune.mam'

dependencies {
    implementation project(':product:FooLib')
    implementation project(':product:foo-project')
    implementation fileTree(dir: "libs", include: ["bar.jar"])
    implementation fileTree(dir: "libs", include: ["zap.jar"])
    implementation "com.contoso.foo:zap-artifact:1.0.0"
    implementation "com.microsoft.bar:baz:1.0.0"
    implementation "com.microsoft.qux:foo:2.0"

    // Include the MAM SDK
    implementation files("$PATH_TO_MAM_SDK/Microsoft.Intune.MAM.SDK.aar")
}
intunemam {
    excludeProjects = [':product:FooLib']
    includeExternalLibraries = ['bar.jar', "com.contoso.foo:zap-artifact", "com.microsoft.*", "!com.microsoft.qux*"]
    excludeClasses = ['com.contoso.SplashActivity']
    excludeVariants=['savory']
}
```

这将产生以下影响：
* 不重写 `:product:FooLib`，因为它包含在 `excludeProjects` 中
* 重写 `:product:foo-project`，但 `com.contoso.SplashActivity` 除外，因为它位于 `excludeClasses` 中，因此会被跳过
* 重写 `bar.jar`，因为它包含在 `includeExternalLibraries` 中
* 不重写 `zap.jar`，因为它不是一个项目且不包含在 `includeExternalLibraries` 中 
* 重写 `com.contoso.foo:zap-artifact:1.0.0`，因为它包含在 `includeExternalLibraries` 中
* 重写 `com.microsoft.bar:baz:1.0.0`，因为它通过通配符 (`com.microsoft.*`) 包含在 `includeExternalLibraries` 中。
* 即使 `com.microsoft.qux:foo:2.0` 与前一项匹配相同的通配符，也不重写它，因为已通过取反模式将其明确排除在外。

#### <a name="usage-of-includeexternallibraries"></a>includeExternalLibraries 的使用

由于插件默认仅在项目依赖项（通常由 `project()` 函数提供）上执行操作，因此，如果需要 MAM 根据以下说明的标准对由 `fileTree(...)` 指定的或从 maven 或其他包源（例如“`com.contoso.bar:baz:1.2.0`”）获取的任何依赖项进行处理，则必须将这些依赖项提供给 `includeExternalLibraries` 属性。 支持使用通配符 ("*")。 以 `!` 开头的项是取反运算，可用于排除否则将通过通配符包含在内的库。

使用项目表示法指定外部依赖项时，建议省略 `includeExternalLibraries` 值中的版本组件。 如果确定要包括此版本，它必须是一个精准版本。 不支持动态版本规范（例如 `1.+`）。

用于确定是否需要在 `includeExternalLibraries` 中包含库的一般规则基于两个问题：
1. 库中是否包含有 MAM 等效项适用的类？ 示例：`Activity`、`Fragment`、`ContentProvider` 和 `Service` 等。
2. 如果是，应用是否会使用这些类？

如果对这两个问题都回答“是”，则必须将该库包含在 `includeExternalLibraries` 中。 

| 方案 | 是否应包括？ |
|--|--|
| 在应用中包括 PDF 查看器库，并且当用户尝试查看 PDF 时在应用程序中使用查看器 `Activity` | 是 |
| 在应用中包括一个 HTTP 库以增强 Web 性能 | 否 |
| 包括如 React Native（包含从 `Activity`、`Application` 和 `Fragment` 派生的类）的一个库，并且在应用中使用或进一步派生这些类 | 是 |
| 包括如 React Native（包含从 `Activity`、`Application` 以及 `Fragment` 派生的类）的一个库，但仅使用静态帮助程序或实用程序类 | 否 |
| 包括一个库（此库包含从 `TextView` 派生的视图类），并且在应用中使用或进一步派生这些类 | 是 |

#### <a name="reporting"></a>报表
生成插件可生成其所作更改的 HTML 报表。 要请求生成此报表，请在 `intunemam` 配置块中指定 `report = true`。 如果已生成，则报表将写入生成目录中的 `outputs/logs`。

```groovy
intunemam {
    report = true
}
```

#### <a name="verification"></a>验证
生成插件可以运行其他验证来查找处理类中的可能错误。 若要请求此项，请在 `intunemam` 配置块中指定 `verify = true`。 请注意，这可能会增加插件任务所花费的时间。

```groovy
intunemam {
    verify = true
}
```

#### <a name="incremental-builds"></a>增量生成
若要启用对增量构建的支持，请在 `intunemam` 配置块中指定 `incremental = true`。  这是一个试验性功能，旨在通过仅处理已更改的输入文件，提高生成性能。  默认配置为 `false`。

```groovy
intunemam {
    incremental = true
}
```

#### <a name="dependencies"></a>依赖关系

gradle 插件在 [Javassist](https://jboss-javassist.github.io/javassist/) 上具有一个依赖项，它必须可用于 Gradle 的依赖项解析（如上所述）。 运行插件时，Javassist 仅会在生成时被使用。 应用中将不会添加任何 Javassist 代码。

> [!NOTE] 
> 必须使用版本 3.0 或更新版本的 Android Gradle 插件以及 Gradle 4.1 或更新版本。

### <a name="command-line-build-tool"></a>命令行生成工具
如果生成使用 Gradle，请跳转至[下一节](#class-and-method-replacements)。

SDK 放置的 `BuildTool` 文件夹中提供了命令行生成工具。 它执行与上述的 Gradle 插件相同的功能，但可以被集成到自定义或非 Gradle 生成系统中。 由于它更为通用，调用更加复杂，因此在可能的情况下，应使用 Gradle 插件。

#### <a name="using-the-command-line-tool"></a>使用命令行工具

可以通过使用位于 `BuildTool\bin` 目录中所提供的帮助程序脚本来调用命令行工具。

此工具需要以下参数。

| 参数 | 描述 |
| -- | -- |
| `--input` | 要修改的一个用分号分隔的 jar 文件列表和类文件目录。 这应包括打算重写的所有 jar/目录。 |
| `--output` | 用于存储修改后的类的一个用分号分隔的 jar 文件列表和目录。 每个输入条目应有一个输出条目，并且它们应按顺序列出。 |
| `--classpath` | 生成类路径。 这可能包含 jar 和类目录。 |
| `--excludeClasses`| 一个用分号分隔的列表，其中包含不应重写的类的名称。 |

除了 `--excludeClasses` 是可选的，所有参数都是必需的。

> [!NOTE]
> 在类似 Unix 的系统上，分号是一个命令分隔符。 要避免 shell 拆分命令，请务必通过 '\' 对每个分号进行转义，或者将整个参数用引号引起来。

#### <a name="example-command-line-tool-invocation"></a>命令行工具调用示例

``` batch
> BuildTool\bin\BuildTool.bat --input build\product-foo-project;libs\bar.jar --output mam-build\product-foo-project;mam-build\libs\bar.jar --classpath build\zap.jar;libs\Microsoft.Intune.MAM.SDK\classes.jar;%ANDROID_SDK_ROOT%\platforms\android-27\android.jar --excludeClasses com.contoso.SplashActivity
```

这将产生以下影响：

* `product-foo-project` 目录重写为 `mam-build\product-foo-project`
* `bar.jar` 重写为 `mam-build\libs\bar.jar`
* 不重写 `zap.jar`，因为它仅列在 `--classpath` 中 
* `com.contoso.SplashActivity` 类即使在 `--input` 中也不会被重写 

> [!NOTE] 
> 生成工具目前不支持 aar 文件。 如果生成系统在处理 aar 文件时尚未提取 `classes.jar`，你则需要在调用生成工具之前执行此操作。


## <a name="class-and-method-replacements"></a>类和方法替换

必须将 Android 基类替换为其相应的 MAM 等效项才能启用 Intune 管理。 SDK 类介于 Android 基类与应用自己的该类派生版本之间。 例如，应用活动最终会得到类似下面这样的继承层次结构：`Activity` > `MAMActivity` >
`AppSpecificActivity`。 MAM 层筛选对系统操作的调用，以便无缝地向应用提供世界的托管视图。

除了基类外，应用可能在不派生情况下使用的一些类（例如 `MediaPlayer`）也有所需的 MAM 等效项，并且[还必须替换某些方法调用](#wrapped-system-services)。 具体详细信息如下所示。

> [!NOTE] 
> 如果你的应用程序与 SDK[生成工具](#build-tooling)集成，将自动执行以下类和方法替换。

| Android 基类 | Intune App SDK 替换项 |
|--|--|
| android.app.Activity | MAMActivity |
| android.app.ActivityGroup | MAMActivityGroup |
| android.app.AliasActivity | MAMAliasActivity |
| android.app.Application | MAMApplication |
| android.app.Dialog | MAMDialog |
| android.app.AlertDialog.Builder | MAMAlertDialogBuilder |
| android.app.DialogFragment | MAMDialogFragment |
| android.app.ExpandableListActivity | MAMExpandableListActivity |
| android.app.Fragment | MAMFragment |
| android.app.IntentService | MAMIntentService |
| android.app.LauncherActivity | MAMLauncherActivity |
| android.app.ListActivity | MAMListActivity |
| android.app.ListFragment | MAMListFragment |
| android.app.NativeActivity | MAMNativeActivity |
| android.app.PendingIntent | MAMPendingIntent（请参阅[挂起意向](#pendingintent)） |
| android.app.Service | MAMService |
| android.app.TabActivity | MAMTabActivity |
| android.app.TaskStackBuilder | MAMTaskStackBuilder |
| android.app.backup.BackupAgent | MAMBackupAgent |
| android.app.backup.BackupAgentHelper | MAMBackupAgentHelper |
| android.app.backup.FileBackupHelper | MAMFileBackupHelper |
| android.app.backup.SharePreferencesBackupHelper | MAMSharedPreferencesBackupHelper |
| android.content.BroadcastReceiver | MAMBroadcastReceiver |
| android.content.ContentProvider | MAMContentProvider |
| android.os.Binder | MAMBinder（仅当 Binder 不是从 Android 接口定义语言 (AIDL) 接口生成时才需要） |
| android.media.MediaPlayer | MAMMediaPlayer |
| android.media.MediaMetadataRetriever | MAMMediaMetadataRetriever |
| android.provider.DocumentsProvider | MAMDocumentsProvider |
| android.preference.PreferenceActivity | MAMPreferenceActivity |
| android.support.multidex.MultiDexApplication | MAMMultiDexApplication |
| android.widget.TextView | MAMTextView |
| android.widget.AutoCompleteTextView | MAMAutoCompleteTextView |
| android.widget.CheckedTextView | MAMCheckedTextView |
| android.widget.EditText | MAMEditText |
| android.inputmethodservice.ExtractEditText | MAMExtractEditText |
| android.widget.MultiAutoCompleteTextView | MAMMultiAutoCompleteTextView |

> [!NOTE]
> 即使应用程序无需派生自己的 `Application` 类，[请参阅以下 `MAMApplication`](#mamapplication)

### <a name="microsoftintunemamsdksupportv4jar"></a>Microsoft.Intune.MAM.SDK.Support.v4.jar：

| Android 类 | Intune App SDK 替换项 |
|--|--|
| android.support.v4.app.DialogFragment | MAMDialogFragment
| android.support.v4.app.FragmentActivity | MAMFragmentActivity
| android.support.v4.app.Fragment | MAMFragment
| android.support.v4.app.JobIntentService | MAMJobIntentService
| android.support.v4.app.TaskStackBuilder | MAMTaskStackBuilder
| android.support.v4.content.FileProvider | MAMFileProvider
| android.support.v4.content.WakefulBroadcastReceiver | MAMWakefulBroadcastReceiver

### <a name="microsoftintunemamsdksupportv7jar"></a>Microsoft.Intune.MAM.SDK.Support.v7.jar：

|Android 类 | Intune App SDK 替换项 |
|--|--|
| android.support.v7.app.AlertDialog.Builder | MAMAlertDialogBuilder |
| android.support.v7.app.AppCompatActivity | MAMAppCompatActivity |
| android.support.v7.widget.AppCompatAutoCompleteTextView | MAMAppCompatAutoCompleteTextView |
| android.support.v7.widget.AppCompatCheckedTextView | MAMAppCompatCheckedTextView |
| android.support.v7.widget.AppCompatEditText | MAMAppCompatEditText |
| android.support.v7.widget.AppCompatMultiAutoCompleteTextView | MAMAppCompatMultiAutoCompleteTextView |
| android.support.v7.widget.AppCompatTextView | MAMAppCompatTextView |

### <a name="microsoftintunemamsdksupportv17jar"></a>Microsoft.Intune.MAM.SDK.Support.v17.jar:
|Android 类 | Intune App SDK 替换项 |
|--|--|
| android.support.v17.leanback.widget.SearchEditText | MAMSearchEditText |

### <a name="microsoftintunemamsdksupporttextjar"></a>Microsoft.Intune.MAM.SDK.Support.Text.jar:
|Android 类 | Intune App SDK 替换项 |
|--|--|
| android.support.text.emoji.widget.EmojiAppCompatEditText | MAMEmojiAppCompatEditText |
| android.support.text.emoji.widget.EmojiAppCompatTextView | MAMEmojiAppCompatTextView |
| android.support.text.emoji.widget.EmojiEditText | MAMEmojiEditText |
| android.support.text.emoji.widget.EmojiTextView | MAMEmojiTextView |

### <a name="renamed-methods"></a>重命名的方法
在许多情况下，Android 类中提供的方法已在 MAM 替换类中标记为最终方法。 在此情况下，MAM 替换类会提供应替代的具有类似名称的方法（通常使用“`MAM`”作为后缀）。 例如，从 `MAMActivity` 派生（而不是替代 `onCreate()` 并调用 `super.onCreate()`）时，`Activity` 必须替代 `onMAMCreate()` 并调用 `super.onMAMCreate()`。 Java 编译器应强制执行最终限制，以防止意外替代原始方法（而不是 MAM 等效项）。

### <a name="mamapplication"></a>MAMApplication
如果应用创建了 `android.app.Application` 的子类，则必须改为创建 `com.microsoft.intune.mam.client.app.MAMApplication` 的子类  。 如果应用不含 `android.app.Application` 子类，则必须将 `"com.microsoft.intune.mam.client.app.MAMApplication"` 设置为 AndroidManifest.xml 的 `<application>` 标记中的 `"android:name"` 属性  。

### <a name="pendingintent"></a>PendingIntent
必须使用 `MAMPendingIntent.get*` 方法，而不是 `PendingIntent.get*`。 此后，可正常使用得到的 `PendingIntent`。

### <a name="wrapped-system-services"></a>包装的系统服务
对于某些系统服务类，有必要在 MAM 包装类上调用静态方法，而不是直接在服务实例上调用所需的方法。 例如，对 `getSystemService(ClipboardManager.class).getPrimaryClip()` 的调用必须变成对 `MAMClipboardManager.getPrimaryClip(getSystemService(ClipboardManager.class)` 的调用。 不建议手动进行这些替换。 相反，让 BuildPlugin 来执行。

| Android 类 | Intune App SDK 替换项 |
|--|--|
| android.content.ClipboardManager | MAMClipboard |
| android.content.ContentProviderClient | MAMContentProviderClientManagement |
| android.content.ContentResolver | MAMContentResolverManagement |
| android.content.pm.PackageManager | MAMPackageManagement |
| android.app.DownloadManager | MAMDownloadManagement |
| android.print.PrintManager | MAMPrintManagement |
| android.support.v4.print.PrintHelper | MAMPrintHelperManagement |
| android.view.View | MAMViewManagement |
| android.view.DragEvent | MAMDragEventManagement |
| NotificationManager | MAMNotificationManagement |
| android. 支持 NotificationManagerCompat | MAMNotificationCompatManagement |

某些类会包装其大部分方法（如 `ClipboardManager`、`ContentProviderClient`、`ContentResolver` 和 `PackageManager`），而其他类只包装一个或两个方法（如 `DownloadManager`、`PrintManager`、`PrintHelper`、`View``DragEvent`、`NotificationManager` 和 `NotificationManagerCompat`）。 如果不使用 BuildPlugin，请查阅 MAM 等效类公开的 API 来获取确切的方法。

### <a name="manifest-replacements"></a>清单替换
可能需要在清单以及 Java 代码中执行上述一些类替换。 特别说明：
* `android.support.v4.content.FileProvider` 的清单引用必须替换为 `com.microsoft.intune.mam.client.support.v4.content.MAMFileProvider`。

## <a name="androidx-libraries"></a>AndroidX 库
借助 Android P，Google 宣布了一组名为 AndroidX 的新支持库（已重命名），版本 28 是现有 android.support 库的最后一个主要版本。

与 android 支持库不同，我们不提供 AndroidX 库的 MAM 变体。 相反，应将 AndroidX 视为任何其他外部库，并应配置为由生成插件/工具重写。 对于 Gradle 生成，可以通过在插件配置的 `includeExternalLibraries` 字段中包括 `androidx.*` 来完成此操作。命令行工具的调用必须显式列出所有 jar 文件。

### <a name="pre-androidx-architecture-components"></a>AndroidX 的体系结构组件
许多 Android 体系结构组件（包括空间、ViewModel 和 WorkManager）都是针对 AndroidX 重新打包的。 如果你的应用程序使用这些库的预 AndroidX 变体，请确保通过在插件配置的 `includeExternalLibraries` 字段中包含 `android.arch.*` 来应用重写。或者，将库更新为其 AndroidX 等效项。

## <a name="sdk-permissions"></a>SDK 权限

Intune App SDK 需要具有三个 [Android 系统权限](https://developer.android.com/guide/topics/security/permissions.html)才能在应用上进行集成：

* `android.permission.GET_ACCOUNTS`（如有必要，可在运行时请求）

* `android.permission.MANAGE_ACCOUNTS`

* `android.permission.USE_CREDENTIALS`

Azure Active Directory 身份验证库 ([ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/)) 需要这些权限以执行代理身份验证。 如果未对应用授予这些权限或权限被用户废除，则将禁用需要代理（公司门户应用）的身份验证流。

## <a name="logging"></a>Logging

应尽早初始化日志记录，以从记录的数据中获取最大价值。 `Application.onMAMCreate()` 通常是初始化日志记录的最佳位置。

若要在应用中接收 MAM 日志，请创建 [Java 处理程序](https://docs.oracle.com/javase/7/docs/api/java/util/logging/Handler.html)并将其添加到 `MAMLogHandlerWrapper`。 这将在应用处理程序上为每个日志消息调用 `publish()`。

```java
/**
 * Global log handler that enables fine grained PII filtering within MAM logs.  
 *
 * To start using this you should build your own log handler and add it via
 * MAMComponents.get(MAMLogHandlerWrapper.class).addHandler(myHandler, false);  
 *
 * You may also remove the handler entirely via
 * MAMComponents.get(MAMLogHandlerWrapper.class).removeHandler(myHandler);
 */
public interface MAMLogHandlerWrapper {
    /**
     * Add a handler, PII can be toggled.
     *
     * @param handler handler to add.
     * @param wantsPII if PII is desired in the logs.    
     */
    void addHandler(final Handler handler, final boolean wantsPII);

    /**
     * Remove a handler.
     *
     * @param handler handler to remove.
     */
    void removeHandler(final Handler handler);
}
```

## <a name="enable-features-that-require-app-participation"></a>启用需要应用参与的功能

SDK 无法单独实现某些应用保护策略。 通过使用下面的 `AppPolicy` 接口中包含的多个 API，该应用可控制其行为以实现这些功能。 若要检索 `AppPolicy` 实例，请使用 `MAMPolicyManager.getPolicy`。

```java
/**
 * External facing application policies.
 */
public interface AppPolicy {

/**
 * Restrict where an app can save personal data.
  * This function is now deprecated. Use getIsSaveToLocationAllowed(SaveLocation, String) instead
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
 *           the username/email associated with the cloud service being saved to. Use null if a mapping between
 *           the AAD username and the cloud service username does not exist or the username is not known.
 * @return true if the location can be saved to by the identity, false if otherwise.
 */
boolean getIsSaveToLocationAllowed(SaveLocation service, String username);

/**
 * Checks whether any activities which could handle the given intent are allowed by policy. Returns false only if all
 * activities which could otherwise handle the intent are blocked. If there are no activities which could handle the intent
 * regardless of policy, returns true. If some activities are allowed and others blocked, returns true. Note that it is not
 * necessary to use this method for policy enforcement. If your app attempts to launch an intent for which there are no
 * allowed activities, MAM will display a dialog explaining the situation to the user.
 *
 * @param intent
 *         intent to check
 *
 * @return whether any activities which could handle this intent are allowed.
*/
boolean areIntentActivitiesAllowed(Intent intent);

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
 * Check if policy allows taking screenshots.
 *
 * @return True if screenshots will be blocked, false otherwise
 */
boolean getIsScreenCaptureAllowed();

/**
 * Check if policy allows Contact sync to local contact list.
 *
 * @return True if Contact sync is allowed to save to local contact list; false otherwise.
 */
boolean getIsContactSyncAllowed();

/**
 * Get the notification restriction. If {@link NotificationRestriction#BLOCKED BLOCKED}, the app must not show any notifications
 * for the user associated with this policy. If {@link NotificationRestriction#BLOCK_ORG_DATA BLOCK_ORG_DATA}, the app must show
 * a modified notification that does not contain organization data. If {@link NotificationRestriction#UNRESTRICTED
 * UNRESTRICTED}, all notifications are allowed.
 *
 * @return The notification restriction.
 */
NotificationRestriction getNotificationRestriction();

/**
 * This method is intended for diagnostic/telemetry purposes only. It can be used to discover whether file encryption is in use.
 * File encryption is transparent to the app and the app should not need to make any business logic decisions based on this.
 * @return True if file encryption is in use.
 */
boolean diagnosticIsFileEncryptionInUse();

/**
 * Return the policy in string format to the app.
 *  
 * @return The string representing the policy.
 */
String toString();

}
```

> [!NOTE]
> `MAMPolicyManager.getPolicy` 会始终返回非 null 应用策略（即使设备或应用不在 Intune 管理策略下，也是如此）。

### <a name="example-determine-if-pin-is-required-for-the-app"></a>示例：确定应用是否需要 PIN

如果应用有其自己的 PIN 用户体验，则当 IT 管理员将 SDK 配置为提示输入应用 PIN 时，你可能要将其禁用。 若要确定 IT 管理员是否已为当前最终用户对此应用部署应用 PIN 策略，请调用以下方法：

```java

MAMPolicyManager.getPolicy(currentActivity).getIsPinRequired();
```

### <a name="example-determine-the-primary-intune-user"></a>示例：确定主要 Intune 用户

除了 AppPolicy 中公开的 API，`MAMUserInfo` 接口内定义的 `getPrimaryUser()` API 还公开了用户主体名称 (**UPN**)。 若要获取 UPN，请调用以下项：

```java
MAMComponents.get(MAMUserInfo.class).getPrimaryUser();
```

MAMUserInfo 接口的完整定义如下：

```java
/**
 * External facing user information.
 *
 */
public interface MAMUserInfo {
       /**
        * Get the primary user name.
        *
        * @return the primary user name or null if neither the device nor app is enrolled.
        */
       String getPrimaryUser();
}
```

### <a name="example-determine-if-saving-to-device-or-cloud-storage-is-permitted"></a>示例：确定是否允许保存到设备或云存储

许多应用都可实现允许最终用户在本地保存文件或保存到云存储服务的功能。 使用 Intune App SDK，IT 管理员可通过应用他们认为适合于组织的策略限制来防止数据泄漏。  例如，IT 可以控制最终用户是否可以保存到“个人”非托管数据存储。 这包括保存到本地位置、SD 卡或第三方备份服务。

**启用该功能需要应用参与。** 如果应用允许直接从应用保存到个人或云位置，则必须实现此功能以确保 IT 管理员可以控制是否允许保存到某个位置。 以下 API 使应用可以了解按照当前 Intune 管理员的策略，是否允许保存到个人存储。 应用随后可以强制执行策略，因为它知道最终用户可以通过应用来使用个人数据存储。  

若要确定是否强制执行策略，可进行以下调用：

```java
MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(
SaveLocation service, String username);
```

`service` 参数必须是以下 `SaveLocation` 值之一：


- `SaveLocation.ONEDRIVE_FOR_BUSINESS`
- `SaveLocation.SHAREPOINT`
- `SaveLocation.LOCAL`
- `SaveLocation.OTHER`

`username` 应该是与要保存的云服务关联的 UPN/用户名/电子邮件（并非一定要与拥有保存的文档的用户相同）  。 如果 AAD UPN 与云服务用户名之间的映射不存在或用户名未知，请使用 NULL。 `SaveLocation.LOCAL` 不是云服务，因此应始终与 `null` 用户名参数一起使用。

之前确定用户策略是否允许用户将数据保存到不同位置的方法是同一个 **AppPolicy** 类中的 `getIsSaveToPersonalAllowed()`。 现在**不推荐使用**也不应使用此功能，以下调用等效于 `getIsSaveToPersonalAllowed()`：

```java
MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(SaveLocation.LOCAL, null);
```

>[!NOTE]
> 如果 **SaveLocations** 枚举中未列出要考虑的位置，则使用 `SaveLocation.OTHER`。

### <a name="example-determine-if-notifications-with-organization-data-need-to-be-restricted"></a>示例：确定是否需要限制包含组织数据的通知

如果你的应用程序显示通知，你必须在显示通知之前，检查与通知关联的用户的通知限制策略。 若要确定是否强制执行策略，可进行以下调用。

```java
NotificationRestriction notificationRestriction =
    MAMPolicyManager.getPolicyForIdentity(notificationIdentity).getNotificationRestriction();
```

如果 `BLOCKED` 限制，应用不能为与此策略关联的用户显示任何通知。 如果 `BLOCK_ORG_DATA`，则应用必须显示不包含组织数据的已修改通知。 如果 `UNRESTRICTED`，则允许所有通知。

如果未调用 `getNotificationRestriction`，MAM SDK 将尽力为单标识应用自动限制通知。 如果启用了自动拦截，并设置了 `BLOCK_ORG_DATA`，则不会显示通知。 若要进行更精细的控制，请检查 `getNotificationRestriction` 的值并相应地修改应用通知。

## <a name="register-for-notifications-from-the-sdk"></a>注册来自 SDK 的通知

### <a name="overview"></a>概述
当 IT 管理员部署特定策略（如选择性擦除策略）时，Intune App SDK 允许应用控制相应行为。 IT 管理员部署此类策略时，Intune 服务会向 SDK 下发通知。

应用必须通过创建 `MAMNotificationReceiver` 并向 `MAMNotificationReceiverRegistry` 注册，来注册来自 SDK 的通知。 此操作可通过在 `App.onCreate` 中提供接收方以及所需通知类型来实现，如以下示例所示：

```java
@Override
public void onCreate() {
  super.onCreate();
  MAMComponents.get(MAMNotificationReceiverRegistry.class)
    .registerReceiver(
      new ToastNotificationReceiver(),
      MAMNotificationType.WIPE_USER_DATA);
  }
```

### <a name="mamnotificationreceiver"></a>MAMNotificationReceiver

`MAMNotificationReceiver` 接口仅接收来自 Intune 服务的通知。 某些通知由 SDK 直接处理，而其他通知需要应用参与。 应用**必须**从通知返回 true 或 false。 它必须始终返回 true，除非它由于通知失败而尝试执行某种操作。

* 这种失败可能会被报告到 Intune 服务。 需报告的情形示例：应用在 IT 管理员启动擦除后无法擦除用户数据。

>[!NOTE]
> 可在 `MAMNotificationReceiver.onReceive` 中放心阻止，因为其回调未在 UI 线程上运行。

在 SDK 中定义的 `MAMNotificationReceiver` 接口如下所示：

```java
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
```

### <a name="types-of-notifications"></a>通知类型

以下通知会发送到应用，其中一些可能需要应用参与：

* **WIPE_USER_DATA**：此通知在 `MAMUserNotification` 类中进行发送。 收到此通知后，应用*必须*删除与托管标识相关的所有数据（从 `MAMUserNotification.getUserIdentity()`）。 出现这种情况的原因可能有多种，包括应用调用 `unregisterAccountForMAM` 时、IT 管理员启动擦除时或未满足管理员要求的条件性访问策略。 如果你的应用程序未注册此通知，则将执行默认的擦除行为。 默认行为将删除单个标识应用的所有文件，或删除使用多标识应用的托管标识标记的所有文件的所有文件。 此通知永远不会发送到 UI 线程。

* **WIPE_USER_AUXILIARY_DATA**：如果应用希望 Intune App SDK 执行默认选择性擦除行为，但是在擦除进行时仍想删除一些辅助数据，则应用可以注册此通知。 此通知不适用于单标识应用，它将仅发送到多标识应用。 此通知永远不会发送到 UI 线程。

* **REFRESH_POLICY**：此通知在 `MAMUserNotification` 中进行发送。 收到此通知后，应用缓存的所有 Intune 策略决策都必须失效且必须更新。 如果应用未存储任何策略假设，则无需注册此通知。 不保证会将此通知发送到哪个线程。

* **REFRESH_APP_CONFIG**：此通知在 `MAMUserNotification` 中进行发送。 收到此通知后，所有缓存的应用程序配置数据必须失效且必须更新。 不保证会将此通知发送到哪个线程。

* **MANAGEMENT_REMOVED**：此通知在 `MAMUserNotification` 中进行发送，并通知应用它将变为不受托管。 一旦不受托管，它将无法进行以下操作：读取加密文件、读取通过 MAMDataProtectionManager 加密的数据、与加密剪贴板进行交互，或以其他方式参与托管应用生态系统。 在下面查看更多详细信息。 此通知永远不会发送到 UI 线程。

* **MAM_ENROLLMENT_RESULT**：此通知在 `MAMEnrollmentNotification` 中进行发送，目的是通知应用 APP-WE 注册尝试已完成，并提供该尝试的状态。 不保证会将此通知发送到哪个线程。

* **COMPLIANCE_STATUS**：此通知在 `MAMComplianceNotification` 中发送，目的是就符合性修正尝试的结果通知应用。 不保证会将此通知发送到哪个线程。

> [!NOTE]
> 应用不能同时注册 `WIPE_USER_DATA` 和 `WIPE_USER_AUXILIARY_DATA` 通知。

### <a name="management_removed"></a>MANAGEMENT_REMOVED

`MANAGEMENT_REMOVED` 通知表示前一名策略托管用户将不再由 Intune MAM 策略托管。 这不需要擦除用户数据或注销用户（如果必须进行擦除，系统将发送 `WIPE_USER_DATA` 通知）。 许多应用可能根本不需要处理此通知，不过使用 `MAMDataProtectionManager` 的应用应[特别留意此通知](#data-protection)。

MAM 调用应用的 `MANAGEMENT_REMOVED` 接收器时，以下情况为 true：
* MAM 已解密属于该应用的先前加密文件（但未解密受保护的数据缓冲区）。 不解密 SD 卡上公共位置中不直属于应用的文件（例如，Documents 或 Download 文件夹）。
* 不加密由接收器方法（或接收器启动后运行的任何其他代码）创建的新文件或受保护的数据缓冲区。
* 应用仍可访问加密密钥，因此解密数据缓冲区等操作将会成功。

应用的接收器返回后，将无法再访问加密密钥。

## <a name="configure-azure-active-directory-authentication-library-adal"></a>配置 Azure Active Directory Authentication Library (ADAL)

首先，请阅读 [GitHub 上的 ADAL 存储库](https://github.com/AzureAD/azure-activedirectory-library-for-android)中的 ADAL 集成指南。

SDK 依赖于 [ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) 实现其[身份验证](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/)和条件启动方案，这要求应用通过 [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/) 进行配置。 配置值通过 AndroidManifest 元数据传递给 SDK。

要配置应用并启用适当的身份验证，请将以下内容添加到 AndroidManifest.xml 中的应用节点。 其中某些配置在一般情况下，仅当应用使用 ADAL 进行身份验证时才需要；在这种情况下，需要应用用于向 AAD 注册自己的特定值。 这样做是为了确保系统不会由于 AAD 识别到两个单独的注册值（一个来自应用，一个来自 SDK）而两次提示最终用户进行身份验证。

```xml
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
```

### <a name="adal-metadata"></a>ADAL 元数据

* 颁发机构是当前使用的 AAD 机构  。 如果此值不存在，则使用 AAD 公共环境。
    > [!NOTE]
    > 如果应用程序具有主权云感知功能，请不要设置此字段。

* ClientID 是要使用的 AAD ClientID（也称为应用程序 ID）  。 如果将其注册到 Azure AD，则应使用自己的应用的 ClientID，如果不集成 ADAL，则利用[默认注册](#default-enrollment-optional)。

* **NonBrokerRedirectURI** 是在无代理情况下使用的 AAD 重定向 URI。 如果未指定，则使用默认值 `urn:ietf:wg:oauth:2.0:oob`。 此默认设置适用于大多数应用。

  * NonBrokerRedirectURI 仅在 SkipBroker 为“true”时使用。

* SkipBroker 用于替代默认的 ADAL SSO 参与行为  。 只应为指定 ClientID 且不支持中转身份验证/设备范围 SSO 的应用指定 SkipBroker  。 在此情况下，应将其设置为“true”。 大多数应用不得设置 SkipBroker 参数。

  * 必须在清单中指定 ClientID，才能指定 SkipBroker 值  。

  * 指定 ClientID 时，默认值为“false”。

  * SkipBroker为“true”时，将使用 NonBrokerRedirectURI。 未集成 ADAL（因此没有 ClientID）的应用也将默认为“true”。

### <a name="common-adal-configurations"></a>常用 ADAL 配置

以下是使用 ADAL 配置应用的常见方法。 找到应用的配置，并确保 ADAL 元数据参数（如上所述）设置为所需的值。 在所有情况下，如果需要，可以为非默认环境指定颁发机构。 如果未指定，则将使用公共生产 AAD 权限。

#### <a name="1-app-does-not-integrate-adal"></a>1.应用未集成 ADAL
清单中不得出现 ADAL 元数据  。

#### <a name="2-app-integrates-adal"></a>2.应用集成了 ADAL

|所需的 ADAL 参数| 值 |
|--|--|
| ClientID | 应用的 ClientID（注册应用时由 Azure AD 生成） |

如有必要，可指定颁发机构。

必须使用 Azure AD 注册应用，并授予应用访问应用保护策略服务的权限：
* 有关使用 Azure AD 注册应用程序的信息，请参阅[此处](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)。
* 确保执行向应用保护策略 (APP) 服务提供 Android 应用权限的步骤。 使用“向 Intune 应用保护服务提供应用访问权限（可选）”下的 [Intune SDK 入门指南](https://docs.microsoft.com/intune/app-sdk-get-started#next-steps-after-integration)中的说明。 

另请参阅以下[条件访问](#conditional-access)的要求。


#### <a name="3-app-integrates-adal-but-does-not-support-brokered-authenticationdevice-wide-sso"></a>3.应用集成了 ADAL，但不支持代理身份验证/设备级 SSO

|所需的 ADAL 参数| 值 |
|--|--|
| ClientID | 应用的 ClientID（注册应用时由 Azure AD 生成） |
| SkipBroker | **True** |

如有必要，可以指定颁发机构和 NonBrokerRedirectURI。

### <a name="conditional-access"></a>条件性访问
条件访问 (CA) 是 Azure Active Directory [功能](https://docs.microsoft.com/azure/active-directory/develop/active-directory-conditional-access-developer)，可用于控制对 AAD 资源的访问。 [Intune 管理员可定义仅允许从由 Intune 托管的设备或应用中访问资源的 CA 规则](https://docs.microsoft.com/intune/conditional-access)。 为确保应用能在适当的时候访问资源，必须按照以下步骤操作。 如果应用未获取任何 AAD 访问令牌，或仅访问不受 CA 保护的资源，则可跳过这些步骤。

1. 按照 [ADAL 集成指南](https://github.com/AzureAD/azure-activedirectory-library-for-android#how-to-use-this-library)进行操作。 
   有关代理的使用情况，请特别参阅步骤 11。
2. [使用 Azure Active Directory 注册应用程序](https://docs.microsoft.com/azure/active-directory/active-directory-app-registration)。 
   可在上面的 ADAL 集成指南中找到重定向 URI。
3. 根据上述第 2 项中的[常用 ADAL 配置](#common-adal-configurations)设置清单元数据参数。
4. 通过从 [Azure 门户](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExchangeConnectorMenu/aad/connectorType/2)启用[基于设备的 CA](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use) 测试所有内容已正确配置并确认以下内容
    - 登录到应用会提示安装和注册 Intune 公司门户
    - 注册后，成功登录到应用。
5. 在你的应用发布 Intune APP SDK 集成后，请立即联系 msintuneappsdk@microsoft.com，将它添加到核准应用列表中，以实现[基于应用的条件访问](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use#app-based-conditional-access)
6. 将应用添加到已批准列表后，通过[配置基于应用的 CA](https://docs.microsoft.com/intune/app-based-conditional-access-intune-create) 进行验证，并确保成功登录到应用。

## <a name="app-protection-policy-without-device-enrollment"></a>无需设备注册的应用保护策略

### <a name="overview"></a>概述
无需设备注册的 Intune 应用保护策略，也称为 APP-WE 或 MAM-WE，允许 Intune 管理应用而无需设备注册 Intune MDM。 需要或无需设备注册的 APP-WE。 公司门户仍需要安装在设备上，但用户不需要登录公司门户并注册设备。

> [!NOTE]
> 在无需设备注册的情况下，所有应用都需要支持应用保护策略。

### <a name="workflow"></a>工作流

当应用创建新的用户帐户时，它应注册该帐户以通过 Intune App SDK 进行管理。 SDK 将处理关于在 APP-WE 服务中注册应用的详细信息；如有必要，若注册失败，它将以适当的时间间隔重试注册。

此外，应用还可以查询 App SDK 以了解已注册用户的状态，从而确定是否应阻止用户访问企业内容。 可以注册多个帐户进行管理，但目前，一次只能在 APP-WE 服务中主动注册一个帐户。 这意味着每次应用上只有一个帐户可以接收应用保护策略。

应用需要提供一个回调，以代表 SDK 从 Azure Active Directory Authentication Library (ADAL) 获取适当的访问令牌。 假定应用已使用 ADAL 进行用户身份验证，并获取它自己的访问令牌。

当应用彻底删除一个帐户时，它应取消注册该帐户，以表明该应用不应再将策略应用于此用户。 如果用户已在 MAM 服务中注册，将注销用户并擦除应用。

### <a name="overview-of-app-requirements"></a>应用要求概述

若要实现 APP-WE 集成，应用必须在 MAM SDK 中注册用户帐户：

1. 应用_必须_实现和注册 `MAMServiceAuthenticationCallback` 接口的实例。 应尽早在应用的生命周期中注册回调实例（通常采用应用程序类的 `onMAMCreate()` 方法）。

2. 当创建一个用户帐户且该用户成功使用 ADAL 登录时，则该应用_必须_调用 `registerAccountForMAM()`。

3. 在删除用户帐户后，应用应调用 `unregisterAccountForMAM()` 以从 Intune 管理中删除该帐户。

    > [!NOTE]
    > 如果用户暂时注销该应用，该应用不需要调用 `unregisterAccountForMAM()`。 调用可能会启动擦除以彻底删除用户的企业数据。


### <a name="mamenrollmentmanager"></a>MAMEnrollmentManager
可以在 `MAMEnrollmentManager` 接口中找到所有必要的身份验证和注册 API。 对 `MAMEnrollmentManager` 的引用可以按以下方式获得：

```java
MAMEnrollmentManager mgr = MAMComponents.get(MAMEnrollmentManager.class);

// make use of mgr
```

返回的 `MAMEnrollmentManager` 实例保证不能为空。 API 方法分为两类：**身份验证**和**帐户注册**。

```java
package com.microsoft.intune.mam.policy;

public interface MAMEnrollmentManager {
    public enum Result {
        AUTHORIZATION_NEEDED,
        NOT_LICENSED,
        ENROLLMENT_SUCCEEDED,
        ENROLLMENT_FAILED,
        WRONG_USER,
        MDM_ENROLLED,
        UNENROLLMENT_SUCCEEDED,
        UNENROLLMENT_FAILED,
        PENDING,
        COMPANY_PORTAL_REQUIRED;
    }

    //Authentication methods
    interface MAMServiceAuthenticationCallback {
        String acquireToken(String upn, String aadId, String resourceId);
    }
    void registerAuthenticationCallback(MAMServiceAuthenticationCallback callback);
    void updateToken(String upn, String aadId, String resourceId, String token);

    //Registration methods
    void registerAccountForMAM(String upn, String aadId, String tenantId);
    void registerAccountForMAM(String upn, String aadId, String tenantId, String authority);
    void unregisterAccountForMAM(String upn);
    Result getRegisteredAccountStatus(String upn);
}
```

### <a name="account-authentication"></a>帐户身份验证
本部分介绍 `MAMEnrollmentManager` 中的身份验证 API 方法以及如何使用这些方法。

```java
interface MAMServiceAuthenticationCallback {
        String acquireToken(String upn, String aadId, String resourceId);
}
void registerAuthenticationCallback(MAMServiceAuthenticationCallback callback);
void updateToken(String upn, String aadId, String resourceId, String token);
```

1. 应用必须实现 `MAMServiceAuthenticationCallback` 接口以允许 SDK 为给定用户和资源 ID 请求 ADAL 令牌。 必须通过调用其 `registerAuthenticationCallback()` 方法将回调实例提供给 `MAMEnrollmentManager`。 应用生命周期中可能在较早便需要令牌，以用于注册重试或应用保护策略刷新签入，因此注册回调的理想位置是在应用 `MAMApplication` 子类的 `onMAMCreate()` 方法中。

2. `acquireToken()` 方法应获取给定用户的请求资源 ID 的访问令牌。 如果无法获取请求的令牌，则会返回 null。

    > [!NOTE]
    > 请确保应用使用传递给 `acquireToken()` 的 `resourceId` 和 `aadId` 参数，以便获取正确的令牌。

    ```java
    class MAMAuthCallback implements MAMServiceAuthenticationCallback {
        public String acquireToken(String upn, String aadId, String resourceId) {
            return mAuthContext.acquireTokenSilentSync(resourceId, ClientID, aadId).getAccessToken();
        }
    }
    ```

3. 如果 SDK 调用 `acquireToken()` 时应用无法提供令牌--例如，如果无提示的身份验证失败，并且刚好不方便显示 UI--应用可在稍后通过调用 `updateToken()` 方法提供令牌。 之前调用 `acquireToken()` 时请求的 UPN、AAD ID 和资源 ID 必须连同最后获得的令牌一起传递给 `updateToken()`。 在从所提供的回调返回 null 之后，应用应尽快调用此方法。

    > [!NOTE]
    > SDK 将定期调用 `acquireToken()` 以获取令牌，因此调用 `updateToken()` 并非严格要求。 但是，强烈建议进行调用，因为它可以帮助及时完成注册和应用保护策略签入。


### <a name="account-registration"></a>帐户注册
本部分介绍 `MAMEnrollmentManager` 中的账户注册 API 方法以及如何试用这些方法。

```java
void registerAccountForMAM(String upn, String aadId, String tenantId);
void registerAccountForMAM(String upn, String aadId, String tenantId, String authority);
void unregisterAccountForMAM(String upn);
Result getRegisteredAccountStatus(String upn);
```

1. 若要注册帐户进行管理，应用应调用 `registerAccountForMAM()`。 用户帐户通过 UPN 及其 AAD 用户 ID 进行标识。 此外，还需要租户 ID 以将注册数据与用户的 AAD 租户相关联。 还可提供用户权限以允许针对特定主权云进行注册，有关详细信息，请参阅[主权云注册](#sovereign-cloud-registration)。  SDK 可能会尝试在 MAM 服务中为给定用户注册应用，如果注册失败，它将定期重试注册，直到取消注册该帐户。 重试周期通常为 12-24 小时。 SDK 通过通知异步提供注册尝试的状态。

2. 由于必须进行 AAD 身份验证，因此注册用户帐户的最佳时机是在用户登录应用并成功使用 ADAL 进行身份验证之后。用户的 AAD ID 和租户 ID 作为 [`AuthenticationResult`](https://github.com/AzureAD/azure-activedirectory-library-for-android) 对象的一部分从 ADAL 身份验证调用返回。
    * 租户 ID 来自 `AuthenticationResult.getTenantID()` 方法。
    * 在来自 `AuthenticationResult.getUserInfo()` 的 `UserInfo` 类型子对象中找到了用户的相关信息，而 AAD 用户 ID 正是通过调用 `UserInfo.getUserId()` 从该对象中检索而得 。

3. 若要从 Intune 管理中取消注册帐户，应用应调用 `unregisterAccountForMAM()`。 如果该帐户已成功注册并托管，SDK 将取消注册该帐户并擦除其数据。 将会停止定期注册重试。 SDK 经通知异步提供取消注册请求的状态。

### <a name="sovereign-cloud-registration"></a>主权云注册
[主权云感知](https://www.microsoft.com/trustcenter/cloudservices/nationalcloud)的应用程序必须将 `authority` 提供给 `registerAccountForMAM()`  。  这可通过在 ADAL 的 [1.14.0+](https://github.com/AzureAD/azure-activedirectory-library-for-android/releases/tag/v1.14.0) acquireToken extraQueryParameters 中提供 `instance_aware=true`，然后对 AuthenticationCallback AuthenticationResult 调用 `getAuthority()` 来实现。

```java
mAuthContext.acquireToken(this, RESOURCE_ID, CLIENT_ID, REDIRECT_URI, PromptBehavior.FORCE_PROMPT, "instance_aware=true",
        new AuthenticationCallback<AuthenticationResult>() {
            @Override
            public void onError(final Exception exc) {
                // authentication failed
            }

            @Override
            public void onSuccess(final AuthenticationResult result) {
                mAuthority = result.getAuthority();
                // handle other parts of the result
            }
        });
```

> [!NOTE]
> 不要在 AndroidManifest.xml 中设置 `com.microsoft.intune.mam.aad.Authority` 元数据项。

> [!NOTE]
> 确保在 `MAMServiceAuthenticationCallback::acquireToken()` 方法中正确设置了颁发机构。

#### <a name="currently-supported-sovereign-clouds"></a>当前支持的主权云

1. Azure 美国政府云

### <a name="important-implementation-notes"></a>重要实现说明

#### <a name="authentication"></a>身份验证
* 当应用调用 `registerAccountForMAM()` 时，不久后它可能会通过另一个线程在其 `MAMServiceAuthenticationCallback` 接口上收到回调。 理想情况下，应用会在注册帐户之前从 ADAL 获取自己的令牌，以更快获取所请求的令牌。 如果应用从回叫返回有效令牌，注册将继续进行，并且该应用将会通过通知获取最终结果。

* 如果应用未返回有效的 AAD 令牌，则注册尝试的最终结果将是 `AUTHENTICATION_NEEDED`。 如果应用通过通知收到此结果，则强烈建议通过获取先前从 `acquireToken()` 请求的用户和资源的令牌并调用 `updateToken()` 方法再次启动注册过程来加快注册过程。

* 还将调用应用的已注册 `MAMServiceAuthenticationCallback` 来获取令牌，以定期进行应用保护策略刷新签入。如果应用在请求时不能提供令牌，它将不会收到通知，但它应尝试获取令牌并在下次方便的时候调用 `updateToken()`，以加快签入过程。 如果未提供令牌，则仍将在尝试下一次签入时调用回调。

* 支持主权云需要提供颁发机构。

#### <a name="registration"></a>注册
* 为方便起见，注册方法为幂等；例如，`registerAccountForMAM()` 将仅在尚未注册帐户时注册该帐户并尝试注册应用，`unregisterAccountForMAM()` 将仅在目前已注册帐户时取消注册该帐户。 后续调用没有操作，因此，多次调用这些方法不会产生任何危害。 此外，并不保证对这些方法的调用和结果通知之间是一一对应的：即如果为某个已注册的标识调用 `registerAccountForMAM()`，可能不会再次为该标识发送通知。 可能发送的通知并未与对这些方法的任何调用对应，因为 SDK 可能定期在后台尝试注册，并且从 Intune 服务接收的擦除请求可能触发取消注册。

* 可以为任意数量的不同标识调用注册方法，但当前只有一个用户帐户可以成功注册。 如果同时或近乎同时注册了获得 Intune 许可并应用了应用保护策略的多个用户帐户，不保证哪个帐户将会注册成功。

* 最后，你可以查询 `MAMEnrollmentManager` 以查看是否已注册特定帐户并使用 `getRegisteredAccountStatus()` 方法获取其当前状态。 如果未注册所提供的帐户，此方法将返回 **null**。 如果注册了该帐户，则此方法将以 `MAMEnrollmentManager.Result` 枚举的其中一个成员返回帐户的状态。

### <a name="result-and-status-codes"></a>结果和状态代码
首次注册一个帐户时，它最初为 `PENDING` 状态，表示初始 MAM 服务注册尝试未完成。 注册尝试完成后，将使用下表中的结果代码之一发送通知。 此外，`getRegisteredAccountStatus()` 方法将返回该帐户的状态，以便应用始终可以确定是否阻止了该用户对企业内容的访问。 如果注册尝试失败，该帐户的状态可能会随 SDK 在后台重试注册而不断变化。

|结果代码 | 说明 |
| -- | -- |
| `AUTHORIZATION_NEEDED` | 此结果表示应用的已注册 `MAMServiceAuthenticationCallback` 实例未提供令牌或提供的令牌无效。  如有可能，应用应获取有效的令牌并调用 `updateToken()`。 |
| `NOT_LICENSED` | 用户未获得 Intune 许可，或尝试联系 Intune MAM 服务失败。  应用应继续处于不受托管的（普通）状态下，用户不会被阻止。  将定期重试注册，以防用户将来获得许可。 |
| `ENROLLMENT_SUCCEEDED` | 注册尝试成功，或者用户已注册。  在成功注册的情况下，将在此通知之前发送策略刷新通知。  应允许对企业数据进行访问。 |
| `ENROLLMENT_FAILED` | 注册尝试失败。  设备日志中提供了进一步的详细信息。  在此状态下，不应允许应用访问企业数据，因为先前已确定用户已获得 Intune 许可。|
| `WRONG_USER` | 每个设备只能有一个用户能够在 MAM 服务中注册应用。 此结果表明，为其传递此结果的用户（第二个用户）针对 MAM 策略，但其他用户已注册。 由于无法为第二个用户强制使用 MAM 策略，你的应用不得允许访问此用户的数据（可能是从你的应用中删除该用户），除非此用户在以后注册成功。 由于提供此 `WRONG_USER` 结果，MAM 会提示选择删除现有帐户。 如果用户在赞成中进行了应答，则稍后可能会短时间注册第二个用户。 只要第二个用户保持注册，MAM 就会定期重试注册。 |
| `UNENROLLMENT_SUCCEEDED` | 取消注册已成功。|
| `UNENROLLMENT_FAILED` | 取消注册请求失败。  设备日志中提供了进一步的详细信息。 通常情况下，只要应用传递了有效（不能为 null 也不为空） UPN，就不会发生这种情况。 应用无法直接、可靠地进行修正。 如果在取消注册有效 UPN 时接收到此值，请将其作为 bug 报告给 Intune MAM 团队。|
| `PENDING` | 用户的初始注册尝试正在进行中。  在获知注册结果之前应用可以阻止对企业数据的访问，但并不要求这样做。 |
| `COMPANY_PORTAL_REQUIRED` | 用户获得了 Intune 许可，但在设备上安装公司门户应用之前不能注册该应用。 Intune APP SDK 将尝试阻止给定用户对应用的访问，并指引他们安装公司门户应用（请参见以下详细信息）。 |


### <a name="company-portal-requirement-prompt-override-optional"></a>公司门户要求提示重写（可选）
如果收到 `COMPANY_PORTAL_REQUIRED` 结果，SDK 将阻止使用其标识已请求进行注册的活动。 相反，SDK 将让这些活动显示下载公司门户的提示。 如果要防止你的应用中出现该行为，活动可能会实施 `MAMActivity.onMAMCompanyPortalRequired`。

在 SDK 显示其默认阻止 UI 之前将调用此方法。 如果应用更改了活动标识，或者取消注册尝试进行注册的用户，SDK 将不会阻止活动。 在此情况下，由该应用负责避免泄露企业数据。 只有多标识应用（稍后讨论）才能够更改活动标识。

如果不显式继承 `MAMActivity`（因为生成工具将进行该更改），但仍需处理此通知，可以改为实现 `MAMActivityBlockingListener`。

### <a name="notifications"></a>通知
如果应用注册类型为 MAM_ENROLLMENT_RESULT 的通知，则系统会发送 `MAMEnrollmentNotification` 来通知应用注册请求已完成  。 将通过 `MAMNotificationReceiver` 接口接收 `MAMEnrollmentNotification`，如[注册来自 SDK 的通知](#register-for-notifications-from-the-sdk)部分所述。

```java
public interface MAMEnrollmentNotification extends MAMUserNotification {
    MAMEnrollmentManager.Result getEnrollmentResult();
}
```

`getEnrollmentResult()` 方法将返回注册请求的结果。  由于 `MAMEnrollmentNotification` 扩展了 `MAMUserNotification`，因此还会提供尝试进行注册的用户的标识。 应用必须实现 `MAMNotificationReceiver` 接口来接收这些通知，详见[注册来自 SDK 的通知](#register-for-notifications-from-the-sdk)部分。

在收到注册通知时，已注册用户帐户的状态可能会发生更改，但在所有情况下不会更改（例如，如果在生成 `WRONG_USER` 等更详尽的结果后收到了 `AUTHORIZATION_NEEDED` 通知，那么更详尽的结果将保持为该帐户的状态）。  帐户成功注册后，状态将保持为 `ENROLLMENT_SUCCEEDED`，直到帐户取消注册或被擦除为止。

## <a name="app-ca-with-policy-assurance"></a>具有策略保证的 APP CA

### <a name="overview"></a>概述
借助具有策略保证的 APP CA（条件访问），在具有 Intune 应用保护策略的应用程序上有条件地访问资源。  AAD 通过要求 APP 必须先注册和管理应用，然后才能授予其令牌以访问具有策略保证保护资源的 APP CA，来强制执行此操作。  应用需要使用 ADAL 中转站来获取令牌，而且设置要与上述[条件访问](#conditional-access)中所述的设置相同。

### <a name="adal-changes"></a>ADAL 更改
ADAL 库有一个新的错误代码，它用于通知应用无法获取令牌是因不符合 APP 管理而导致的。  如果应用收到此错误代码，则需要调用 SDK，尝试通过注册应用和应用策略来修正符合性。 通过使用 ADAL `AuthenticationCallback` 的 `onError()` 方法，系统将收到异常且将出现错误代码 `ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED`。  在这种情况下，异常可转换为 `IntuneAppProtectionPolicyRequiredException`，从中可提取其他参数用于修正符合性（请参阅以下代码示例）。 修正成功后，应用可通过 ADAL 重新尝试获取令牌。

> [!NOTE]
> 要使用这个新的错误代码以及对带策略保证的 APP CA 的其他支持，需具备 ADAL 库 1.15.0 版（或更高版本）。

### <a name="mamcompliancemanager"></a>MAMComplianceManager
从 ADAL 收到需要策略的错误时，将使用 `MAMComplianceManager` 接口。  它包含 `remediateCompliance()` 方法，须调用该方法来尝试使应用处于符合状态。 对 `MAMComplianceManager` 的引用可以按以下方式获得：

```java
MAMComplianceManager mgr = MAMComponents.get(MAMComplianceManager.class);

// make use of mgr
```

返回的 `MAMComplianceManager` 实例保证不能为空。

```java
package com.microsoft.intune.mam.policy;

public interface MAMComplianceManager {
    void remediateCompliance(String upn, String aadId, String tenantId, String authority, boolean showUX);
}
```

调用`remediateCompliance()` 方法来尝试将应用置于管理之下，从而满足 AAD 授予所请求令牌的条件。  前 4 个参数可从 ADAL `AuthenticationCallback.onError()` 方法接收的异常中提取（请参阅以下代码示例）。  最后一个参数是布尔值，它控制了在符合性尝试期间是否显示 UX。  这是一个简单的阻止进程样式界面，用作在此操作期间无需显示自定义 UX 的应用的默认设置。  它将仅在符合性修正过程中进行阻止且不显示最终结果。  应用应注册通知接收器以处理符合性修正尝试的结果（成功或失败），详见下文。

`remediateCompliance()` 方法可在符合性建立期间执行 MAM 注册。  如果应用已为注册通知注册了通知接收器，则它可能会收到注册通知。  应用注册的 `MAMServiceAuthenticationCallback` 将调用其 `acquireToken()` 方法来获取 MAM 注册的令牌。 在应用获得自己的令牌之前将调用 `acquireToken()`，因此应用在成功获取令牌后执行的任何簿记或帐户创建任务都可能尚未完成。  回叫必须能够在此情况下获取令牌。  如果无法从 `acquireToken()` 返回令牌，则符合性修正尝试将失败。  如果稍后使用所请求资源的有效令牌来调用 `updateToken()`，则将立即使用给定的令牌重新尝试修正符合性。

> [!NOTE]
> 仍可在 `acquireToken()` 中无提示地获取令牌，因为在收到 `ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED` 错误之前，系统已指导用户安装中转站和注册设备。  这导致中转站在其缓存中具有有效的刷新令牌，允许无提示地成功获取所请求的令牌。

下列示例展示了在 `AuthenticationCallback.onError()` 方法中接收需要策略的错误并调用 `MAMComplianceManager` 来处理该错误。

```java
public void onError(@Nullable Exception exc) {
    if (exc instanceof AuthenticationException && 
        ((AuthenticationException) exc).getCode() == ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED) {

        final IntuneAppProtectionPolicyRequiredException policyRequiredException = 
            (IntuneAppProtectionPolicyRequiredException) ex;

        final String upn = policyRequiredException.getAccountUpn();
        final String aadId = policyRequiredException.getAccountUserId();
        final String tenantId = policyRequiredException.getTenantId();
        final String authority = policyRequiredException.getAuthorityURL();

        MAMComplianceManager complianceManager = MAMComponents.get(MAMComplianceManager.class);
        complianceManager.remediateCompliance(upn, aadId, tenantId, authority, showUX);
    }
}
```

### <a name="status-notifications"></a>状态通知
如果应用注册类型为 COMPLIANCE_STATUS 的通知，则系统会发送 `MAMComplianceNotification`，就符合性修正尝试的最终状态通知应用  。 将通过 `MAMNotificationReceiver` 接口接收 `MAMComplianceNotification`，如[注册来自 SDK 的通知](#register-for-notifications-from-the-sdk)部分所述。

```java
public interface MAMComplianceNotification extends MAMUserNotification {
    MAMCAComplianceStatus getComplianceStatus();
    String getComplianceErrorTitle();
    String getComplianceErrorMessage();
}
```

`getComplianceStatus()` 方法将符合性修正尝试的结果作为 `MAMCAComplianceStatus` 枚举中的值返回。

|状态代码 | 说明 |
| -- | -- |
| 未知 | 状态未知。 这可能表示意外的失败原因。 其他信息可在公司门户日志中找到。 |
| COMPLIANT | 符合性修正成功，应用现已符合策略。 应重新尝试获取 ADAL 令牌。 |
| NOT_COMPLIANT | 符合性修正尝试失败。  应用不符合条件，且只能在错误条件得到纠正之后才能尝试重新获取 ADAL 令牌。  使用 MAMComplianceNotification 发送其他错误信息。 |
| SERVICE_FAILURE | 尝试从 Intune 服务中检索符合性数据时出现故障。 其他信息可在公司门户日志中找到。 |
| NETWORK_FAILURE | 连接 Intune 服务时出错。 应用应在网络连接恢复时再次尝试获取其令牌。 |
| CLIENT_ERROR | 由于与客户端相关的某个原因，符合性修正尝试失败。  例如，原因可能是没有令牌或用户错误。 使用 MAMComplianceNotification 发送其他错误信息。 |
| PENDING | 符合性修正尝试失败，因为超过时间限制时尚未从服务收到状态响应。 应用应稍后再次尝试其令牌获取。 |
| COMPANY_PORTAL_REQUIRED | 必须在设备上安装公司门户，才能成功修正符合性。  如果设备上已安装公司门户，则需要重启应用。  在这种情况下，系统将显示一个对话框，要求用户重启应用。 |

如果符合性状态是 `MAMCAComplianceStatus.COMPLIANT`，则应用应重启其原始令牌获取操作（适用于自己的资源）。 如果符合性修正尝试失败，`getComplianceErrorTitle()` 和 `getComplianceErrorMessage()` 方法将返回应用可在最终用户选中时显示的本地化的字符串。  大多数错误情况都无法由应用修正，因此通常最好是使帐户创建或登录失败，并允许用户稍后再试。  如果故障仍然存在，则可借助 MAM 日志来确定原因。  最终用户可以使用[此处](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android "通过电子邮件将日志发送给公司支持人员")的说明提交日志。

由于 `MAMComplianceNotification` 扩展了 `MAMUserNotification`，因此还会提供尝试进行修正的用户的标识。

下面的示例展示了使用匿名类注册接收器来实现 MAMNotificationReceiver 接口：

```java
final MAMNotificationReceiverRegistry notificationRegistry = MAMComponents.get(MAMNotificationReceiverRegistry.class);
// create a receiver
final MAMNotificationReceiver receiver = new MAMNotificationReceiver() {
    public boolean onReceive(MAMNotification notification) {
        if (notification.getType() == MAMNotificationType.COMPLIANCE_STATUS) {
            MAMComplianceNotification complianceNotification = (MAMComplianceNotification) notification;
            
            // take appropriate action based on complianceNotification.getComplianceStatus()
            
            // unregister this receiver if no longer needed
            notificationRegistry.unregisterReceiver(this, MAMNotificationType.COMPLIANCE_STATUS);
        }
        return true;
    }
};
// register the receiver
notificationRegistry.registerReceiver(receiver, MAMNotificationType.COMPLIANCE_STATUS);
```

> [!NOTE]
> 通知接收器必须先注册才能调用 `remediateCompliance()`，避免可能导致通知缺失的争用条件。

### <a name="implementation-notes"></a>实现说明
> [!NOTE]
> **重要更改！**  <br>
> 应用的 `MAMServiceAuthenticationCallback.acquireToken()` 方法应将新的 `forceRefresh` 标志的*值*传递给 `acquireTokenSilentSync()`。
> 以前，我们建议传递*true*以解决在从 broker 刷新令牌时遇到的问题，但发现在某些情况下，如果此标志为*true*，可能会阻止在某些情况下获取令牌。
```java
AuthenticationResult result = acquireTokenSilentSync(resourceId, clientId, userId, /* forceRefresh */ false);
```

> [!NOTE]
> 如果要在修正尝试期间显示自定义的阻止 UX，则应将 showUX 参数的 false 状态传递给 `remediateCompliance()`  。 必须确保在调用 `remediateCompliance()` 之前先显示 UX 并注册通知侦听器。  这将防止在 `remediateCompliance()` 迅速失败的情况下，出现导致通知缺失的争用条件。  例如，Activity 子类的 `onCreate()` 或 `onMAMCreate()` 方法是注册通知侦听器再调用 `remediateCompliance()` 的理想之选。  `remediateCompliance()` 的参数可作为额外意向传递给 UX。  收到符合性状态通知后，可显示结果，也可仅完成活动。

> [!NOTE]
> `remediateCompliance()` 将注册帐户并尝试注册。  获取主令牌后，无需调用 `registerAccountForMAM()`，但即使调用也没有任何不利影响。 另一方面，如果应用无法获取其令牌且希望删除用户帐户，则必须调用 `unregisterAccountForMAM()` 来删除帐户并防止后台重试注册。

## <a name="protecting-backup-data"></a>保护备份数据
自 Android Marshmallow (API 23) 开始，Android 有两种方法可供应用来备份其数据。 用户可以在其应用中使用这两种选项，但需要不同的步骤，以确保正确实现 Intune 数据保护。 可查看下表，以了解有关正确数据保护行为所需的对应操作。  有关备份方法的详细信息，可参阅 [Android API 指南](https://developer.android.com/guide/topics/data/backup.html)。

### <a name="auto-backup-for-apps"></a>应用的自动备份
Android 开始在 Android Marshmallow 设备上向应用的 Google Drive 提供[自动完整备份](https://developer.android.com/guide/topics/data/autobackup.html)（不考虑应用的目标 API）。 在 AndroidManifest.xml 中，如果将 `android:allowBackup` 显式设置为 **false**，则 Android 永远都不会将你的应用排入队列且“企业”数据将保留在应用中。 在这种情况下，无需执行进一步操作。

但是，即使未在清单文件中指定 `android:allowBackup`默认情况下也会将 `android:allowBackup` 属性设置为 true。 这意味着所有应用数据都会自动备份到用户的 Google Drive 帐户，这种默认行为会带来**数据泄露风险**。 因此 SDK 要求进行下面概括的更改以确保使用数据保护。  如果希望应用在 Android Marshmallow 设备上运行，请务必遵循以下指南以正确保护客户数据。  

Intune 可让用户使用 Android 中所有可用的[自动备份功能](https://developer.android.com/guide/topics/data/autobackup.html)（包括定义 XML 中的自定义规则），但必须遵循以下步骤保护数据：

1. 如果应用**不**使用它自己的自定义 BackupAgent，则使用默认的 MAMBackupAgent 以允许执行符合 Intune 策略的自动完整备份。 将以下项放入应用清单：

    ```xml
    android:fullBackupOnly="true"
    android:backupAgent="com.microsoft.intune.mam.client.app.backup.MAMDefaultBackupAgent"
    ```
    
2. **[可选]** 如果实现可选的自定义 BackupAgent，则需要确保使用 MAMBackupAgent 或 MAMBackupAgentHelper。 请参阅以下部分。 考虑切换为使用 Intune 的 MAMDefaultFullBackupAgent  （如步骤 1 中所述），它在 Android M 及更高版本上提供轻松备份。

3. 确定应用应接收的完整备份类型（未筛选、已筛选或无）时，你将需要将属性 `android:fullBackupContent` 设置为 true、false 或应用中的 XML 资源。

4. 然后， _**必须**_ 将所有置于 `android:fullBackupContent` 的内容复制到清单中名为 `com.microsoft.intune.mam.FullBackupContent` 的元数据标记。

    **示例 1**：如果你希望应用在无需排除的情况下进行完整备份，请同时将 `android:fullBackupContent` 属性和 `com.microsoft.intune.mam.FullBackupContent` 元数据标记设置为 **true**：

    ```xml
    android:fullBackupContent="true"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />  
    ```

    **示例 2**：如果你希望应用使用其自定义 BackupAgent 并选择退出符合 Intune 策略的完整自动备份，则必须将属性和元数据标记同时设置为 **false**：

    ```xml
    android:fullBackupContent="false"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="false" />  
    ```

    示例 3  ：如果希望应用根据 XML 文件中定义的自定义规则具有完整备份，将属性和元数据标记设置为相同的 XML 资源：

    ```xml
    android:fullBackupContent="@xml/my_scheme"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />  
    ```

### <a name="keyvalue-backup"></a>键/值备份
[键/值备份](https://developer.android.com/guide/topics/data/keyvaluebackup.html)选项可供所有 API 8+ 使用，并可将应用数据上载到 [Android 备份服务](https://developer.android.com/google/backup/index.html)。 应用每个用户的数据量限制为 5 MB。 如果你使用键/值备份，则必须使用 **BackupAgentHelper** 或 **BackupAgent**。

### <a name="backupagenthelper"></a>BackupAgentHelper
在本机 Android 功能和 Intune MAM 集成两个方面，BackupAgentHelper 的实现都比 BackupAgent 简单得多。 BackupAgentHelper 允许开发人员分别将整个文件和共享首选项注册到 **FileBackupHelper** 和 **SharedPreferencesBackupHelper**，它们随后会在创建时添加到 BackupAgentHelper。 请按照以下步骤将 Intune MAM BackupAgentHelper 和 Intune MAM 配合使用：

1. 若要将多身份备份与 BackupAgentHelper 一同使用，请按照有关[扩展 BackupAgentHelper](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgentHelper) 的 Android 指南进行操作。

2. 让类扩展 BackupAgentHelper、FileBackupHelper 和 SharedPreferencesBackupHelper 的 MAM 等效项。

|Android 类 | MAM 等效项 |
|--|--|
|BackupAgentHelper |MAMBackupAgentHelper |
|FileBackupHelper | MAMFileBackupHelper
|SharedPreferencesBackupHelper| MAMSharedPreferencesBackupHelper|

遵循以下准则将会成功完成多身份备份和还原。

### <a name="backupagent"></a>BackupAgent

BackupAgent 使你可以更明确要备份哪些数据。 因为主要由开发人员负责实现，所以确保从 Intune 进行适当数据保护需要更多步骤。 由于大部分工作由你（即开发人员）来完成，因此会稍微更多地涉及 Intune 集成。

**集成 MAM：**

1. 仔细阅读[键/值备份](https://developer.android.com/guide/topics/data/keyvaluebackup.html)的 Android 指南，尤其是[扩展 BackupAgent](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent)，以确保 BackupAgent 实现遵循 Android 指导原则。

2. 让类扩展 `MAMBackupAgent`。

**多身份备份：**

1. 在开始备份之前，检查计划备份的文件或数据缓冲区确实**允许 IT 管理员在多身份方案中进行备份**。 我们在 `MAMFileProtectionManager` 和 `MAMDataProtectionManager` 中提供了 `isBackupAllowed` 函数以确定这一点。 如果不允许备份文件或数据缓冲区，则你不应继续将其包括在备份中。

2. 在备份过程中的某个时候，如果要备份在步骤 1 中检查的文件的标识，则必须使用计划从中提取数据的文件调用 `backupMAMFileIdentity(BackupDataOutput data, File … files)`。 这会自动为你创建新的备份实体并将它们写入 `BackupDataOutput` 。 这些实体会在还原时自动进行使用。

**多身份还原：**

数据备份指南指定使用常规算法来还原应用数据，并在[扩展 BackupAgent](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent) 部分提供了一个代码示例。 要成功完成多身份还原，必须遵循此代码示例中提供的一般结构，特别要注意以下信息：

1. 必须使用 `while(data.readNextHeader())` 循环浏览备份实体。 在以上代码中，`data` 是 MAMBackupDataInput 的本地变量名称，在还原时传递给你的应用  。

2. 如果 `data.getKey()` 与 `onBackup` 中编写的密钥不匹配，则必须调用 `data.skipEntityData()`。 如果不执行此步骤，还原可能不会成功。 在以上代码中，`data` 是 MAMBackupDataInput 的本地变量名称，在还原时传递给你的应用  。

3. 在 `while(data.readNextHeader())` 构造中使用备份实体时避免返回，因为我们自动编写的实体将会丢失。 在以上代码中，`data` 是 MAMBackupDataInput 的本地变量名称，在还原时传递给你的应用  。

## <a name="multi-identity-optional"></a>多标识（可选）

### <a name="overview"></a>概述
默认情况下，Intune App SDK 会将策略作为一个整体应用到该应用。 多标识是一种可选的 Intune 应用保护功能，可以启用该功能以允许策略应用到单标识级别。 这需要比其他应用保护功能还要多得多的应用参与。

> [!NOTE]
> 缺少正确的应用参与可能会导致数据泄漏和其他安全问题。

用户注册设备或应用后，SDK 会注册此标识并将其作为主要 Intune 托管标识。 应用中的其他用户会被视为具有不受限策略设置的非托管标识。

> [!NOTE]
> 目前，每台设备仅支持一个 Intune 托管标识。

标识被定义为字符串。 标识**不区分大小写**，而且向 SDK 请求标识可能会返回在设置标识时最初使用的相同大小写情况。

应用必须  在其打算更改现用身份时通知 SDK。 在某些情况下，SDK 也会在需要标识更改时通知应用。 然而，在大多数情况下，MAM 不知道 UI 中正在显示的数据或在给定的时间内在线程上使用的数据，并且要依赖应用设置正确的标识以避免数据泄漏。 在随后各部分中，将会调用需要应用操作的一些特定方案。

### <a name="enabling-multi-identity"></a>启用多身份标识
默认情况下，所有应用都会被视为单一标识的应用。 通过替换 AndroidManifest.xml 清单中的以下元数据，可将应用声明为多标识感知。

```xml
  <meta-data
    android:name="com.microsoft.intune.mam.MAMMultiIdentity"
    android:value="true" />
```

### <a name="setting-the-identity"></a>设置标识
开发人员可在以下级别上按降序优先级设置应用用户的标识：

  1. 线程级别
  2. `Context`（通常为 `Activity`）级别
  3. 进程级别

在线程级别上设置的标识可取代在 `Context` 级别（在其上设置的标识可取代在进程级别上设置的标识）上设置的标识。 在 `Context` 中设置的标识仅在合适的相关方案中使用。 例如，文件 IO 操作就不具有相关联的 `Context`。 最常见的情况是，应用将在 `Activity` 上设置 `Context` 标识。 除非 `Activity` 标识设置为相同标识，否则应用不得显示托管标识的数据  。 通常情况下，仅当在所有线程上一次只能有一名用户使用应用时，进程级标识才有用。 许多应用可能不需要使用它。

如果应用使用 `Application` 上下文来获取系统服务，请确保已设置线程或进程标识，或者已在应用的 `Application` 上下文中设置了 UI 标识。

要在使用 `setUIPolicyIdentity` 或 `switchMAMIdentity` 更新 UI 标识时处理特殊情况，这两种方法都可传递一组 `IdentitySwitchOption` 值。

* `IGNORE_INTENT`：如果请求应忽略与当前活动关联的意向的标识开关，则请使用此项。
  例如：

  1. 你的应用从包含托管文档的托管标识中接收意向并显示该文档。
  2. 用户切换到其个人标识，因此你应用请求了一个 UI 标识开关。 在个人标识中，你的应用不再显示该文档，因此在请求标识开关时，你使用了 `IGNORE_INTENT`。

  如果未设置，SDK 将假定应用中仍在使用最新的意向。 这将导致新标识的接收策略将意向视为传入数据并使用其标识。

>[!NOTE]
> 由于 `CLIPBOARD_SERVICE` 用于 UI 操作，因此 SDK 使用前台活动的 UI 标识执行 `ClipboardManager` 操作。
> `MAMPolicyManager` 上的以下方法可用于设置标识和检索以前设置的标识值。

```java
public static void setUIPolicyIdentity(final Context context, final String identity, final MAMSetUIIdentityCallback mamSetUIIdentityCallback, final EnumSet<IdentitySwitchOption> options);

  public static String getUIPolicyIdentity(final Context context);

  public static MAMIdentitySwitchResult setProcessIdentity(final String identity);

  public static String getProcessIdentity();

  public static MAMIdentitySwitchResult setCurrentThreadIdentity(final String identity);

  public static String getCurrentThreadIdentity();

/**
   * Get the current app policy. This does NOT take the UI (Context) identity into account.
   * If the current operation has any context (e.g. an Activity) associated with it, use the overload below.
   */
  public static AppPolicy getPolicy();

  /**
  * Get the current app policy. This DOES take the UI (Context) identity into account.
   * If the current operation has any context (e.g. an Activity) associated with it, use this function.
   */
  public static AppPolicy getPolicy(final Context context);


  public static AppPolicy getPolicyForIdentity(final String identity);

  public static boolean getIsIdentityManaged(final String identity);
  ```

>[!NOTE]
> 可通过将标识设置为 null 清除应用的标识。
>
> 空字符串可用作永无应用保护策略的标识。

#### <a name="results"></a>结果
所有这些用于设置标识的方法都可通过 `MAMIdentitySwitchResult` 返回结果值。 可返回的值有四个：

| 返回值 | 方案 |
|--            |--        |
| `SUCCEEDED`    | 标识更改成功。 |
| `NOT_ALLOWED`  | 不允许更改标识。 在当前线程上已设置另一标识时尝试设置 UI (`Context`) 标识，会出现此问题。 |
| `CANCELLED`    | 用户取消了标识更改，通常是在出现 PIN 或身份验证提示时按了“后退”按钮。 |
| `FAILED`       | 标识更改失败，原因不明。|

在显示或使用公司数据之前，应用应确保标识切换成功。 目前，对于启用多标识的应用，进程和线程标识切换将始终成功，但是我们保留添加故障条件的权利。 如果 UI 标识与线程标识相冲突，或者如果用户取消条件启动要求（例如，按下 PIN 屏幕上的后退按钮），则 UI 标识切换会因参数无效而失败。 活动上失败的 UI 标识开关的默认行为是完成活动（请参阅下面 `onSwitchMAMIdentityComplete`）。

如果通过 `setUIPolicyIdentity` 设置 `Context` 标识，会以异步方式报告结果。 如果 `Context` 是一个 `Activity`，则 SDK 不会知道标识更改是否成功，直到执行条件启动，而此操作可能需要用户输入 PIN 或公司凭据。 应用可以实现 `MAMSetUIIdentityCallback` 来接收此结果，也可以为回调对象传递 null。 请注意，如果调用 `setUIPolicyIdentity`，而以前对*同一上下文*中的 `setUIPolicyIdentity` 的结果尚未传递，则新的回调将取代旧的回调，并且原始回调将永远不会收到结果。

```java
    public interface MAMSetUIIdentityCallback {
        void notifyIdentityResult(MAMIdentitySwitchResult identitySwitchResult);
  }
```

还可通过 `MAMActivity` 中的方法（而不是调用 `MAMPolicyManager.setUIPolicyIdentity`）直接设置活动的标识。 使用以下方法来执行此操作：

```java
     public final void switchMAMIdentity(final String newIdentity, final EnumSet<IdentitySwitchOption> options);
```

如果你希望应用收到尝试更改该活动标识结果的通知，还可以重写 `MAMActivity` 中的方法。

``` java
    public void onSwitchMAMIdentityComplete(final MAMIdentitySwitchResult result);
```

如果不替代 `onSwitchMAMIdentityComplete`（或调用 `super` 方法），则活动上失败的标识开关将导致活动完成。 如果替代该方法，则必须注意在标识开关失败后不会显示公司数据。

>[!NOTE]
> 切换标识可能需要重新创建该活动。 在这种情况下，`onSwitchMAMIdentityComplete` 回调将被直接传送到活动的新实例。


### <a name="implicit-identity-changes"></a>隐式标识更改
应用除可设置标识外，还可基于从另一 Intune 托管的应用（具有应用保护策略）进入的数据更改线程或上下文的标识。

#### <a name="examples"></a>示例
1. 如果活动从由另一 MAM 应用发送的 `Intent` 启动，则活动的标识将在发送 `Intent` 时基于另一应用的有效标识进行设置。

2. 使用服务，将设置线程的标识，方法与 `onStart` 或 `onBind` 调用期间进行的操作类似。 在从 `onBind` 返回的 `Binder` 中进行调用也将暂时设置线程标识。

3. 在 `ContentProvider` 中进行调用同样会对其持续时间设置线程标识。


    此外，用户与活动的交互可能导致隐式标识切换。

    **示例：** 用户在 `Resume` 期间取消授权提示将导致隐式切换到空标识。

    应用有机会识别这些更改，在必要的情况下，可以禁止这些更改。 `MAMService` 和 `MAMContentProvider` 公开子类可能会重写的以下方法：

    ```java
    public void onMAMIdentitySwitchRequired(final String identity,
      final AppIdentitySwitchResultCallback callback);
    ```

    在 `MAMActivity` 类中，此方法中还会存在其他参数：

    ```java
    public void onMAMIdentitySwitchRequired(final String identity,
      final AppIdentitySwitchReason reason,
      final AppIdentitySwitchResultCallback callback);
    ```

    * `AppIdentitySwitchReason` 可以捕获隐式切换的源，且可接受值 `CREATE`、`RESUME_CANCELLED` 和 `NEW_INTENT`。  因活动继续而导致显示 PIN、身份验证或其他相容 UI 以及当用户尝试取消该 UI（通常通过使用“后退”按钮）时，将使用 `RESUME_CANCELLED` 原因。


    * `AppIdentitySwitchResultCallback` 如下所示：

      ```java
      public interface AppIdentitySwitchResultCallback {
          /**
            * @param result
            *            whether the identity switch can proceed.
            */
          void reportIdentitySwitchResult(AppIdentitySwitchResult result);
        }
        ```

      其中 ```AppIdentitySwitchResult``` 是 `SUCCESS` 或 `FAILURE`。

对于所有隐式标识更改（通过由 `MAMService.onMAMBind` 返回的 Binder 完成的更改除外），都会调用 `onMAMIdentitySwitchRequired` 方法。 `onMAMIdentitySwitchRequired` 的默认实现将立即调用：

* 当由 `RESUME_CANCELLED` 造成时，请调用 `reportIdentitySwitchResult(FAILURE)`。

* 所有其他情况均为 `reportIdentitySwitchResult(SUCCESS)`。

  大多数应用都无需使用其他方法来阻止或延迟标识切换，但是如果应用需要执行此操作，则必须考虑以下几点：

  * 如果阻止标识切换，其结果与 `Receive` 共享设置禁止数据流入的结果相同。

  * 如果服务在主线程上运行，则**必须**同步调用 `reportIdentitySwitchResult` 或挂起 UI 线程。

  * 若要创建 `Activity`，将在 `onMAMCreate` 之前调用 `onMAMIdentitySwitchRequired`  。 如果应用必须显示 UI 来确定是否允许切换标识，则必须使用*另一*活动显示该 UI。

  * 在 `Activity` 中，请求切换到空标识且其原因为 `RESUME_CANCELLED` 时，则该应用必须修改已恢复的活动来显示与该标识切换相一致的数据  。  如果无法做到这一点，则该应用应拒绝切换，且将会再次要求用户遵循恢复标识的策略（例如，在应用 PIN 输入屏幕上显示）。

    > [!NOTE]
    > 多身份标识应用将始终接收来自托管和非托管应用的传入数据。 应用将负责用托管的方式来处理托管标识的数据。

  如果请求的标识受托管（使用 `MAMPolicyManager.getIsIdentityManaged` 进行检查），但此应用无法使用该帐户（例如，因为必须首先在应用中设置帐户，如电子邮件帐户），则应拒绝标识切换。

#### <a name="build-plugin--tool-considerations"></a>生成插件/工具注意事项
如果不显式继承 `MAMActivity`、`MAMService` 或 `MAMContentProvider`（因为允许生成工具进行该更改），但仍需处理标识切换，则可以改为实现 `MAMActivityIdentityRequirementListener`（对于 `Activity`）或 `MAMIdentityRequirementListener`（对于 `Service` 或 `ContentProviders`）。
可以通过调用以下静态方法访问 `MAMActivity.onMAMIdentitySwitchRequired` 的默认行为：`MAMActivity.defaultOnMAMIdentitySwitchRequired(activity, identity,
reason, callback)`。

同样，如果需要覆盖 `MAMActivity.onSwitchMAMIdentityComplete`，则可以实现 `MAMActivityIdentitySwitchListener`，而无需显式继承 `MAMActivity`。

### <a name="preserving-identity-in-async-operations"></a>保留异步操作中的标识
UI 线程上的操作通常将后台任务分派给另一线程。 多标识应用需要确保这些后台任务以适当标识进行操作，这种标识通常与分派它们的活动使用的标识相同。 MAM SDK 提供 `MAMAsyncTask` 和 `MAMIdentityExecutors`以便于帮助保留标识。
如果异步操作可将公司数据写入文件或者可与其他应用通信，则必须使用它们。

#### <a name="mamasynctask"></a>MAMAsyncTask
若要使用 `MAMAsyncTask`，仅需从它而不是 `AsyncTask` 中继承，并分别用 `doInBackgroundMAM` 和 `onPreExecuteMAM` 替代 `doInBackground` 和 `onPreExecute`。 `MAMAsyncTask` 构造函数采用了活动上下文。 例如：

```java
  AsyncTask<Object, Object, Object> task = new MAMAsyncTask<Object, Object, Object>(thisActivity) {

    @Override
    protected Object doInBackgroundMAM(final Object[] params) {
        // Do operations.
    }

    @Override
    protected void onPreExecuteMAM() {
        // Do setup.
    };
}
```

### <a name="mamidentityexecutors"></a>MAMIdentityExecutors
`MAMIdentityExecutors` 允许使用 `wrapExecutor` 和 `wrapExecutorService` 方法将现有 `Executor` 或 `ExecutorService` 实例包装为保留标识的 `Executor`/`ExecutorService`。 例如

```java
  Executor wrappedExecutor = MAMIdentityExecutors.wrapExecutor(originalExecutor, activity);
  ExecutorService wrappedService = MAMIdentityExecutors.wrapExecutorService(originalExecutorService, activity);
```

### <a name="file-protection"></a>文件保护
基于线程和进程标识，每个文件在创建时都具有与之关联的标识。 此标识可用于文件加密和选择性擦除。 但只有文件的标识经托管且具有要求加密的策略时才会进行加密。 SDK 的默认选择性功能擦除将仅擦除与擦除请求的托管标识相关联的文件。 应用可使用 `MAMFileProtectionManager` 类查询或更改文件的标识。

```java
public final class MAMFileProtectionManager {

   /**
    * Protect a file or directory. This will synchronously trigger whatever protection is required for the file, and will tag the
    * file for future protection changes. If an identity is set on a directory, it is set recursively on all files and
    * subdirectories. New files or directories will inherit their parent directory's identity. If MAM is operating in offline mode,
    * this method will silently do nothing.
    *
    * @param identity
    *       Identity to set.
    * @param file
    *       File to protect.
    *
    * @throws IOException
    *       If the file cannot be protected.
    */
   public static void protect(final File file, final String identity) throws IOException;

   /**
     * Protect a file obtained from a content provider. This is intended to be used for
     * sdcard (whether internal or removable) files accessed through the Storage Access Framework.
     * It may also be used with descriptors referring to private files owned by this app.
     * It is not intended to be used for files owned by other apps and such usage will fail. If
     * creating a new file via a content provider exposed by another MAM-integrated app, the new
     * file identity will automatically be set correctly if the ContentResolver in use was
     * obtained via a Context with an identity or if the thread identity is set.
     *
     * This will synchronously trigger whatever protection is required for the file, and will tag
     * the file for future protection changes. If an identity is set on a directory, it is set
     * recursively on all files and subdirectories. If MAM is operating in offline mode, this
     * method will silently do nothing.
     *
     * @param identity
     *            Identity to set.
     * @param file
     *            File to protect.
     *
     * @throws IOException
     *             If the file cannot be protected.
     */
    public static void protect(final ParcelFileDescriptor file, final String identity) throws IOException;

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

   /**
    * Get the protection info on a file.
    *
    * @param file
    *            File or directory to get information on.
    * @return File protection info, or null if there is no protection info.
    * @throws IOException
    *             If the file cannot be read or opened.
    */
    public static MAMFileProtectionInfo getProtectionInfo(final ParcelFileDescriptor file) throws IOException;

}

public interface MAMFileProtectionInfo {
    String getIdentity();
}
 ```

#### <a name="app-responsibility"></a>应用责任
MAM 无法自动推断出要在 `Activity` 中读取的文件和在其中显示的数据之间的关系。 应用必须  在显示公司数据之前适当地设置 UI 标识。 这包括从文件中读取的数据。 如果一个文件来自应用外部（来自 `ContentProvider` 或从公开可写的位置读取），则应用必须  在显示从文件中读取的信息之前尝试确定文件标识（使用 `MAMFileProtectionManager.getProtectionInfo`）。 如果 `getProtectionInfo` 报告非 NULL、非空的标识，则必须将 UI 标识  设置为匹配此标识（使用 `MAMActivity.switchMAMIdentity` 或 `MAMPolicyManager.setUIPolicyIdentity`）。 如果标识切换失败，则不得  显示来自该文件的数据。

示例流如下所示：
* 用户选择要在应用中打开的文档。
  * 在打开流期间，在从磁盘读取数据之前，应用确认应该用于显示内容的标识：

    ```java
    MAMFileProtectionInfo info = MAMFileProtectionManager.getProtectionInfo(docPath)
    if (info != null)
        MAMPolicyManager.setUIPolicyIdentity(activity, info.getIdentity(), callback, EnumSet.noneOf<IdentitySwitchOption.class>)
    ```

  * 应用会一直等待，直到将结果报告给回叫。
  * 如果报告的结果是一个故障，则应用不显示文档。
* 应用将打开并呈现该文件。
  
#### <a name="single-identity-to-multi-identity-transition"></a>单一标识转换到多标识
如果之前通过单标识 Intune 集成发布的应用稍后集成了多标识，则之前安装的应用进行转换（不向用户显示且没有关联的 UX）。 应用无需明确执行任何操作即可处理这一转换  。 在转换之前创建的所有文件都将继续被视为“托管”（因此，如果已启用加密策略，则它们将保持加密状态）。 如果需要，可对 `MAMFileProtectionManager.protect` 的升级和使用进行检测，以标记具有空标识的特定文件或目录（如果它们已加密，则此操作将去除加密）。

#### <a name="offline-scenarios"></a>脱机方案
文件标识标记可识别脱机模式。 应考虑以下几点：

* 如果未安装公司门户，则无法将文件标记为标识。

* 如果已安装公司门户，但应用不具有 Intune MAM 策略，则无法可靠地将文件标记为标识。

* 文件标识标记可用时，所有之前创建的文件都将被视为专用/不受托管（属于空字符串标识），除非应用先前已作为单身份标识托管应用，在这种情况下，该应用被视为归属于已注册用户。

### <a name="directory-protection"></a>目录保护
可能会使用用于保护文件的同一个 `protect` 方法来保护目录。 目录保护以递归方式应用于所有文件和目录中包含的子目录，以及在目录中创建的新文件。 因为目录保护以递归方式应用，所以对于大型目录，`protect` 调用可能需要一些时间才能完成。 为此，对包含大量文件的目录应用保护的应用可能希望在后台线程上以异步方式运行 `protect`。

### <a name="data-protection"></a>数据保护
无法将文件标记为属于多身份标识。 对于必须存储属于同一文件中不同用户的数据的应用，可使用由 `MAMDataProtectionManager` 提供的功能手动执行此操作。 这可让应用加密数据并将其绑定到特定用户。 经过加密的数据适合存储到文件中的磁盘。 可查询与标识关联的数据，并且随后可解密此数据。

使用 `MAMDataProtectionManager` 的应用应实现 `MANAGEMENT_REMOVED` 通知的接收器。 此通知完成后，如果在缓冲区受保护时启用了文件加密，则通过此类保护的缓冲区将不再可读。 在此通知期间，应用可通过对所有缓冲区调用 `MAMDataProtectionManager.unprotect` 来修正这一情况。 如果想要保留标识信息，也可以在此通知期间安全调用保护--加密保证会在此通知期间禁用。

```java

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

### <a name="content-providers"></a>内容提供程序
如果应用通过 `ContentProvider` 提供的是企业数据而不是 `ParcelFileDescriptor`，应用必须调用 `MAMContentProvider` 中的 `isProvideContentAllowed(String)` 方法，针对内容传递所有者标识的 UPN（用户主体名称）。 如果此函数返回 false，则此内容不得返回到调用方  。 通过内容提供程序返回的文件描述符将自动基于文件标识进行处理。

如果没有显式继承 `MAMContentProvider`，而是允许生成工具进行此项更改，则可调用同一方法的静态版本：`MAMContentProvider.isProvideContentAllowed(provider,
contentIdentity)`。

### <a name="selective-wipe"></a>选择性擦除
如果多标识应用注册了 `WIPE_USER_DATA` 通知，则应用有责任删除要擦除的用户的所有数据，包括已标识为属于该用户的所有文件。 如果应用从文件中删除用户数据，但希望在文件中保留其他数据，则必须将文件的标识（通过 `MAMFileProtectionManager.protect`）更改为个人用户或空标识  。 如果当前使用加密策略，则不会解密正在擦除的用户的任何剩余文件，并且擦除后将无法访问这些应用。

注册 `WIPE_USER_DATA` 的应用无法享有 SDK 默认的选择性擦除行为的好处。 对于多身份标识感知应用，这种丢失可能更为重要，因为 MAM 默认的选择性擦除将仅擦除其标识被擦除锁定的文件。 如果多身份标识感知应用希望完成 MAM 默认选择性擦除 _**并**_ 希望针对擦除执行其自己的操作，则应注册 `WIPE_USER_AUXILIARY_DATA` 通知。 此通知将在执行 MAM 默认选择性擦除前一秒由 SDK 发出。 应用不能同时注册 `WIPE_USER_DATA` 和 `WIPE_USER_AUXILIARY_DATA`。

默认的选择性擦除将正常关闭应用，这会完成活动并终止应用进程。 如果应用替代了默认的选择性擦除，则可能需要考虑手动关闭应用以防止用户在擦除后访问内存中的数据。

## <a name="enabling-mam-targeted-configuration-for-your-android-applications-optional"></a>为 Android 应用程序启用面向 MAM 的配置（可选）
可在 Intune 控制台中为 [MAM-WE](https://docs.microsoft.com/intune/app-configuration-policies-managed-app) 和 [Android Enterprise](https://docs.microsoft.com/intune/app-configuration-policies-use-android) 配置应用程序专属的键值对。
这些键值对根本不会被 Intune 解释，而是被传递给应用。 想要接收这种配置的应用程序可以使用 `MAMAppConfigManager` 和 `MAMAppConfig` 类进行这些操作。 如果多个策略针对同一个应用，则可能会有多个冲突的值可用于同一个键。

> [!NOTE] 
> 通过 MAM 进行传递的配置设置-我们无法在 `offline` （未安装公司门户时） delievered。  在这种情况下，通过 `MAMUserNotification` 在空标识上传递的只有 Android Enterprise AppRestrictions。

### <a name="get-the-app-config-for-a-user"></a>获取用户的应用程序配置
可以按如下所示检索应用配置：
```java
MAMAppConfigManager configManager = MAMComponents.get(MAMAppConfigManager.class);
String identity = "user@contoso.com"
MAMAppConfig appConfig = configManager.getAppConfig(identity);
```

如果没有 MAM 注册的用户，但你的应用仍想要检索 Android 企业配置（不是特定用户），则可以传递 null 或空字符串。

### <a name="conflicts"></a>冲突
在 MAM 应用配置中设置的值将覆盖 Android Enterprise config 中具有相同密钥集的值。 

如果管理员为同一密钥配置了冲突的值（例如，将具有相同密钥的不同应用配置集定位到包含同一用户的多个组），Intune 将无法自动解决此冲突，并将所有值适用于你的应用程序。 

应用可以从 `MAMAppConfig` 对象请求给定键的所有值：
```java
List<Boolean> getAllBooleansForKey(String key)
List<Long> getAllIntegersForKey(final String key)
List<Double> getAllDoublesForKey(final String key)
List<String> getAllStringsForKey(final String key)
```

或请求选择一个值：
```java
Boolean getBooleanForKey(String key, BooleanQueryType queryType)
Long getIntegerForKey(String key, NumberQueryType queryType)
Double getDoubleForKey(String key, NumberQueryType queryType)
String getStringForKey(String key, StringQueryType queryType)

enum BooleanQueryType {
    /**
     * In case of conflict, arbitrarily picks one. This is not guaranteed to return the same value every time.
     */
    Any,
    /**
     * In case of conflict, returns true if any of the values are true.
     */
    Or,
    /**
     * In case of conflict, returns false if any of the values are false.
     */
    And
}

enum NumberQueryType {
    /**
     * In case of conflict, arbitrarily picks one. This is not guaranteed to return the same value every time.
     */
    Any,
    /**
     * In case of conflict, returns the minimum Integer.
     */
    Min,
    /**
     * In case of conflict, returns the maximum Integer.
     */
    Max
}

enum StringQueryType {
    /**
     * In case of conflict, arbitrarily picks one. This is not guaranteed to return the same value every time.
     */
    Any,
    /**
     * In case of conflict, returns the first result ordered alphabetically.
     */
    Min,

    /**
     * In case of conflict, returns the last result ordered alphabetically.
     */
    Max
}
```

您的应用程序还可以请求原始数据作为键值对集的列表。

```java
List<Map<String, String>> getFullData()
```

### <a name="full-example"></a>完整示例
```java
MAMAppConfigManager configManager = MAMComponents.get(MAMAppConfigManager.class);
String identity = "user@contoso.com"
MAMAppConfig appConfig = configManager.getAppConfig(identity);
String fooValue = null;
if (appConfig.hasConflict("foo")) {
    List<String> values = appConfig.getAllStringsForKey("foo");
    fooValue = chooseBestValue(values);
} else {
    valueToUse = appConfig.getStringForKey("foo", MAMAppConfig.StringQueryType.Any);
}
Long barValue = appConfig.getIntegerForKey("bar", MAMAppConfig.NumberQueryType.Min);
```

### <a name="notification"></a>通知
应用配置会添加一个新的通知类型：
* **REFRESH_APP_CONFIG**：此通知在 `MAMUserNotification` 中发送，并通知应用新的应用配置数据可用。

### <a name="further-reading"></a>深入阅读
关于如何在 Android 中创建面向 MAM 的应用配置策略的详细信息，请参阅[如何使用适用于 Android 的 Microsoft Intune 应用配置策略](https://docs.microsoft.com/intune/app-configuration-policies-managed-app)。

应用配置还可以使用图形 API 进行配置。 有关信息，请参阅针对[MAM 的配置的图形 API 文档](https://docs.microsoft.com/graph/api/resources/intune-mam-targetedmanagedappconfiguration)。

## <a name="style-customization-optional"></a>样式自定义（可选）
可以直观地自定义由 MAM SDK 生成的视图，以更匹配在其中集成它的应用。 可以自定义主次视图、背景色以及应用徽标的大小。 此样式自定义项为可选，如果未配置任何自定义样式，将使用默认值。

### <a name="how-to-customize"></a>如何自定义
若要将样式更改应用到 Intune MAM 视图，必须首先创建一个样式来替代 XML 文件。 此文件应位于应用的“/ res/xml”目录，你可以按照自己的喜好对它进行命名。 下面是此文件应遵循的格式示例。

```xml
<?xml version="1.0" encoding="utf-8"?>
<styleOverrides>
    <item
        name="foreground_color"
        resource="@color/red"/>
    <item
        name="accent_color"
        resource="@color/blue"/>
    <item
        name="background_color"
        resource="@color/green"/>
    <item
        name="logo_image"
        resource="@drawable/app_logo"/>
</styleOverrides>
```

你必须重用应用中已存在的资源。 例如，必须在 colors.xml 文件中定义绿色并在此处引用它。 不能使用十六进制颜色代码“#0000ff”。 应用徽标的最大大小为 110 dip (dp)。 可以使用较小的徽标图像，但遵循最大大小会产生最佳外观。 如果超过 110 dip 限制，图像将缩小并可能会模糊。

以下是允许的样式属性、其控制的 UI 元素、其 XML 属性项名称和每个属性所需资源类型的完整列表。

|样式属性 | 受影响的 UI 元素 | 属性项名称 | 所需资源类型 |
| -- | -- | -- | -- |
| 背景色 | PIN 屏幕背景色 <Br>PIN 框填充色 | background_color | 颜色 |
| 前景色 | 前景文本颜色 <br> 处于默认状态的 PIN 边框 <br> 用户输入 PIN 时 PIN 框中的字符（包括经过模糊处理的字符）| foreground_color | 颜色|
| 着色 | 突出显示时的 PIN 边框 <br> 超链接 |accent_color | 颜色 |
| 应用徽标 | Intune 应用 PIN 屏幕上显示的大图标 | logo_image | 可绘制 |

## <a name="default-enrollment-optional"></a>默认注册（可选）
以下指南面向：需要在应用启动时出现用户提示以自动注册 APP-WE 服务（本节中称为“默认注册”）；需要 Intune 应用保护策略以仅允许受 Intune 保护的用户使用你的集成了 SDK 的 Android LOB 应用  。 指南中还说明如何为集成了 SDK 的 Android LOB 应用启用 SSO。 可由非  Intune 用户使用的应用商店应用不支持此操作。

> [!NOTE] 
> “默认注册”提供一个为设备上的应用从 APP-WE 服务获取策略的简便方法  。

> [!NOTE] 
> “默认注册”可感知到主权云  。

可通过下列步骤启用默认注册：

1. 如果应用集成了 ADAL 或者你需要启用 SSO，则请按照[通用 ADAL 配置](#common-adal-configurations) #2 [配置 ADAL](#configure-azure-active-directory-authentication-library-adal)。 如果不需要，则可跳过此步骤。
   
2. 通过将以下值放入清单来启用默认注册：
   ```xml 
   <meta-data android:name="com.microsoft.intune.mam.DefaultMAMServiceEnrollment" android:value="true" />
   ```
   > [!NOTE] 
   > 这必须是应用中唯一的 MAM-WE 集成。 如果有任何其他调用 MAMEnrollmentManager API 的尝试，则将发生冲突。

3. 通过将以下值放入清单来启用所需的 MAM 策略：
   ```xml 
   <meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />
   ```
   > [!NOTE] 
   > 这将强制用户在设备上下载公司门户，并且需要完成默认注册流程才能使用。

## <a name="limitations"></a>限制

### <a name="policy-enforcement-limitations"></a>策略强制实施限制

* **使用内容解析程序**：“传输或接收”Intune 策略可能会阻止或部分阻止使用内容解析程序访问其他应用中的内容提供程序。 这将导致 `ContentResolver` 方法返回 null 或引发失败值（例如 `openOutputStream` 在受阻时会引发 `FileNotFoundException`）。 应用可以通过进行以下调用，来确定是否策略已导致（或策略会导致）通过内容解析程序写入数据失败：

    ```java
    MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(contentURI);
    ```

    或如果没有关联活动：

    ```java
    MAMPolicyManager.getPolicy().getIsSaveToLocationAllowed(contentURI);
    ```

    在第二种情况下，多标识应用必须注意适当地设置线程标识（或将显式标识传递给 `getPolicy` 调用）。

### <a name="exported-services"></a>导出的服务
Intune App SDK 中包括的 AndroidManifest.xml 文件包含 **MAMNotificationReceiverService**，它必须是导出的服务才能允许公司门户将通知发送到托管应用。 服务会检查调用方以确保仅允许公司门户发送通知。

### <a name="reflection-limitations"></a>反射限制
某些 MAM 基类（例如 `MAMActivity`、`MAMDocumentsProvider`）包含使用仅在特定 API 级别之上的参数或返回类型的方法（基于原始 Android 基类）。 出于此原因，使用反射来枚举应用组件的所有方法并非始终都是可能的。 此限制并不仅限于 MAM，如果应用本身从 Android 的基类中实现了这些方法，那么同一限制也适用。

### <a name="robolectric"></a>Robolectric
不支持在 Robolectric 下测试 MAM SDK 行为。 在 Robolectric 下运行 MAM SDK 存在已知的问题，因为 Robolectric 下的行为无法准确地模仿真实设备或仿真器上的行为。

如果需要在 Robolectric 下测试应用程序，推荐的变通方法是将应用程序类逻辑移动到帮助程序，并使用未从 MAMApplication 继承的应用程序类生成单元测试 apk。

## <a name="expectations-of-the-sdk-consumer"></a>SDK 使用者的期望
Intune SDK 会维护 Android API 提供的协定，但可能会由于策略实施而更频繁地触发失败条件。 这些 Android 最佳做法可减少发生失败的可能性：

* 可能返回 null 的 Android SDK 函数现在为 null 的可能性会更高。  要最大程度减小问题，请确保在正确的位置进行 null 检查。

* 可以进行检查的功能必须通过其 MAM 替换 API 进行检查。

* 派生的任何函数都必须调用到其超类版本。

* 避免以不明确的方式使用任何 API。 例如，使用 `Activity.startActivityForResult` 而不检查 requestCode 会导致奇怪的行为。

## <a name="telemetry"></a>遥测技术

Intune App SDK for Android 不会控制应用中的数据集合。 公司门户应用程序会默认记录系统生成的数据。 会将此数据发送到 Microsoft Intune。 根据 Microsoft 策略，我们不会收集任何个人数据。

> [!NOTE]
> 如果最终用户选择不发送此数据，则必须在“公司门户”应用的“设置”下关闭遥测。 有关详细信息，请参阅[关闭 Microsoft 使用情况数据收集](https://docs.microsoft.com/intune-user-help/turn-off-microsoft-usage-data-collection-android)。 

## <a name="recommended-android-best-practices"></a>建议使用的 Android 最佳做法

* 所有库项目都应尽可能共享同一个 android:package。 这不会偶尔在运行时失败；它仅仅是生成时间问题。 Intune App SDK 的较新版本将删除某些冗余。

* 使用最新的 Android SDK 生成工具。

* 删除所有不必要和未使用的库（例如 android.support.v4）

## <a name="testing"></a>测试
请参阅[测试指南](app-sdk-android-testing-guide.md)。
