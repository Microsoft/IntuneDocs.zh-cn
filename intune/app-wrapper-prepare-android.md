---
title: 使用 Intune 应用包装工具包装 Android 应用
description: 了解不更改应用本身代码即可包装 Android 应用的方法。 准备应用以便应用移动应用管理策略。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 32ce1a71911c7a902f2790fef584ab1c3b86a293
ms.sourcegitcommit: 6ff5df63a2fff291d7ac5fed9c51417fe808650d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52167444"
---
# <a name="prepare-android-apps-for-app-protection-policies-with-the-intune-app-wrapping-tool"></a>使用 Intune 应用包装工具准备 Android 应用以便使用应用保护策略

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

通过限制应用的功能，而不更改应用自身的代码，使用适用于 Android 的 Microsoft Intune 应用包装工具，更改内部 Android 应用的行为。

该工具是一个 Windows 命令行应用程序，它在 PowerShell 中运行并在 Android 应用周围创建“包装器”。 包装应用后，可通过在 Intune 中配置[移动应用程序管理策略](/intune-classic/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console)来更改应用的功能。


在运行工具前查看[运行应用包装工具的安全注意事项](#security-considerations-for-running-the-app-wrapping-tool)。 若要下载该工具，请转到 GitHub 上的[适用于 Android 的 Microsoft Intune 应用包装工具](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android)。

## <a name="fulfill-the-prerequisites-for-using-the-app-wrapping-tool"></a>满足使用应用包装工具的先决条件

-   必须在运行 Windows 7 或更高版本的 Windows 计算机上运行应用包装工具。

-   输入应用必须是有效的 Android 应用程序包，且文件扩展名为 .apk，同时：

    -   不能对其进行加密。
    -   必须尚未被 Intune 应用包装工具包装。
    -   必须是针对 Android 4.0 或更高版本编写的。

-   应用必须由你的公司开发，或为你的公司开发。 无法将此工具用在从 Google Play 商店中下载的应用。

-   若要运行应用包装工具，必须安装最新版 [Java 运行时环境](http://java.com/download/)，然后确保已在 Windows 环境变量中将 Java 路径变量设置为 C:\ProgramData\Oracle\Java\javapath。 有关更多帮助，请参阅 [Java 文档](http://java.com/download/help/)。

    > [!NOTE]
    > 在某些情况下，32 位版本的 Java 可能会导致内存问题。 最好安装 64 位版本。

- Android 要求对所有应用包 (.apk) 进行签名。 有关重复使用现有证书和证书签名的综合指南，请参阅[重复使用签名证书和包装应用](https://docs.microsoft.com/intune/app-wrapper-prepare-android#reusing-signing-certificates-and-wrapping-apps)。 Java 可执行文件 keytool.exe 可用于生成对已包装的输出应用进行签名所需的新凭据。 必须保证设置的所有密码的安全性，但需要记住密码，因为运行应用包装工具时需要使用。

> [!NOTE]
> Intune App Wrapping Tool 不支持用于应用签名的 Google 的 v2 和即将推出 v3 签名方案。 使用 Intune App Wrapping Tool 包装 .apk 文件后，建议使用 [Google 提供的 Apksigner 工具]( https://developer.android.com/studio/command-line/apksigner)。 这将确保一旦应用安装到最终用户设备上，它就可以通过 Android 标准正确启动。 

- （可选）在输入应用中启用 Multidex。 有时由于在包装过程中添加的 Intune MAM SDK 类，应用可能会达到 Dalvik 可执行文件 (DEX) 大小限制。 DEX 文件是 Android 应用的编译部分。 在此方案中，最佳做法是在该应用自身中启用 Multidex。 在某些组织中，这需要与编译应用的相关人员（即应用生成团队）合作。 

## <a name="install-the-app-wrapping-tool"></a>安装应用包装工具

1.  从 [GitHub 存储库](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android)将 Intune App Wrapping Tool for Android 的安装文件 InstallAWT.exe 下载到 Windows 计算机。 打开该安装文件。

2.  接受许可协议，然后完成安装。

注意将工具安装到的文件夹。 默认位置为：C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool。

## <a name="run-the-app-wrapping-tool"></a>运行应用包装工具

1. 在安装了应用包装工具的 Windows 计算机上，打开 PowerShell 窗口。

2. 从安装该工具的文件夹导入应用包装工具 PowerShell 模块：

   ```
   Import-Module .\IntuneAppWrappingTool.psm1
   ```

3. 通过使用 **invoke-AppWrappingTool** 命令运行该工具，它使用以下语法：
   ```
   Invoke-AppWrappingTool [-InputPath] <String> [-OutputPath] <String> -KeyStorePath <String> -KeyStorePassword <SecureString>
   -KeyAlias <String> -KeyPassword <SecureString> [-SigAlg <String>] [<CommonParameters>]
   ```

   下表详细说明了 **Invoke-appwrappingtool** 命令的属性：

|属性|信息|示例|
|-------------|--------------------|---------|
|**-InputPath**&lt;String&gt;|源 Android 应用 (.apk) 的路径。| |
 |**-OutputPath**&lt;String&gt;|指向输出 Android 应用的路径。 如果这是与 InputPath 相同的目录路径，则打包将失败。| |
|**-KeyStorePath**&lt;String&gt;|包含用于签名的公钥/私钥对的密钥库文件的路径。|默认情况下，密钥存储文件存储在“C:\Program Files (x86)\Java\jreX.X.X_XX\bin”中。 |
|**-KeyStorePassword**&lt;SecureString&gt;|用于解密密钥库的密码。 Android 要求对所有的应用程序包 (.apk) 签名。 使用 Java keytool 生成 KeyStorePassword。 在此处了解更多有关 Java [密钥存储](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html)的信息。| |
|**-KeyAlias**&lt;String&gt;|要用于进行签名的密钥的名称。| |
|**-KeyPassword**&lt;SecureString&gt;|用于解密私钥的密码，该私钥将用于签名。| |
|**-SigAlg**&lt;SecureString&gt;| （可选）用于签名的签名算法的名称。 该算法必须与私钥兼容。|示例：SHA256withRSA、SHA1withRSA|
| **&lt;CommonParameters&gt;** | （可选）该命令支持常见的 PowerShell 参数，如 verbose 和 debug。 |


- 有关常见参数的列表，请参阅 [Microsoft 脚本中心](https://technet.microsoft.com/library/hh847884.aspx)。

- 若要查看该工具的详细使用情况信息，请输入命令：

    ```
    Help Invoke-AppWrappingTool
    ```

**示例：**

导入 PowerShell 模块。
```
Import-Module "C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool\IntuneAppWrappingTool.psm1"
```
在本机应用 HelloWorld.apk 上运行应用包装工具。
```
invoke-AppWrappingTool -InputPath .\app\HelloWorld.apk -OutputPath .\app_wrapped\HelloWorld_wrapped.apk -KeyStorePath "C:\Program Files (x86)\Java\jre1.8.0_91\bin\mykeystorefile" -keyAlias mykeyalias -SigAlg SHA1withRSA -Verbose
```

然后将提示输入 **KeyStorePassword** 和 **KeyPassword**。 输入用于创建密钥存储文件的凭据。

包装的应用和日志文件将在指定的输出路径中生成并保存。

## <a name="how-often-should-i-rewrap-my-android-application-with-the-intune-app-wrapping-tool"></a>我应该多久使用一次 Intune 应用包装工具来重新包装 Android 应用程序？
需要重新包装应用程序的主要方案如下：
* 应用程序本身已发布新的版本。 该应用的以前版本已包装且已上传到 Intune 控制台。
* Intune App Wrapping Tool for Android 已发布新的版本，该版本提供了重要的 bug 修补程序或新的特定 Intune 应用程序保护策略功能。 GitHub 存储库每 6-8 周会发布一次 [Microsoft Intune App Wrapping Tool for Android](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android) 的新版本。

重新包装的一些最佳做法包括： 
* 维护在生成过程中使用的签名证书，请参阅[重复使用签名证书和包装应用](https://docs.microsoft.com/intune/app-wrapper-prepare-android#reusing-signing-certificates-and-wrapping-apps)

## <a name="reusing-signing-certificates-and-wrapping-apps"></a>重复使用签名证书和包装应用
Android 要求所有应用都必须由有效证书进行签名才能安装在 Android 设备上。

包装的应用可以作为包装过程的一部分进行签名，也可以使用现有的签名工具包装后进行签名（包装前应用中的任何签名信息都会被丢弃）。 如果可能，应在包装期间使用已在生成过程中使用的签名信息。 在某些组织中，这需要与拥有密钥存储信息的相关人员（即应用生成团队）合作。 

如果无法使用以前的签名证书，或之前未部署应用，则可以按照 [Android 开发人员指南](https://developer.android.com/studio/publish/app-signing.html#signing-manually)中的说明创建新的签名证书。

如果以前使用不同的签名证书部署过应用，那么升级后便无法将应用上传到 Intune。 如果应用使用与生成应用所用的证书不同的证书签名，则将中断应用升级方案。 因此，应该维护任何新的签名证书以进行应用升级。 

## <a name="security-considerations-for-running-the-app-wrapping-tool"></a>运行应用包装工具的安全注意事项
防止潜在的欺骗、信息泄露和特权提升攻击：

-   确保输入业务线 (LOB) 应用程序、输出应用程序和 Java 密钥存储位于运行应用包装工具的同一台 Windows 计算机上。

-   在运行此工具的同一台计算机上，将输出应用导入 Intune。 有关 Java keytool 的详细信息，请参阅 [keytool](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html)。

-   如果输出应用程序和工具位于通用命名约定 (UNC) 路径，并且未在同一台计算机上运行工具和输入文件，则使用 [Internet 协议安全性 (IPsec)](http://wikipedia.org/wiki/IPsec) 或 [服务器消息块 (SMB) 签名](https://support.microsoft.com/kb/887429)将环境设置为安全。

-   确保应用程序来源可信。

-   确保包含已包装应用的输出目录的安全。 考虑为输出使用用户级目录。

## <a name="requiring-user-login-prompt-for-an-automatic-app-we-service-enrollment-requiring-intune-app-protection-policies-in-order-to-use-your-wrapped-android-lob-app-and-enabling-adal-sso-optional"></a>需要用户登录提示以自动注册 APP-WE 服务，需要 Intune 应用保护策略以使用已包装的 Android LOB 应用，以及启用 ADAL SSO（可选）

以下指南面向：需要在应用启动时出现用户提示以自动注册 APP-WE 服务（本节中称为“默认注册”）；需要 Intune 应用保护策略以仅允许受 Intune 保护的用户使用你的已包装的 Android LOB 应用。 指南中还说明如何为已包装的 Android LOB 应用启用 SSO。 

> [!NOTE] 
> “默认注册”提供一个为设备上的应用从 APP-WE 服务获取策略的简便方法。

### <a name="general-requirements"></a>一般要求
* Intune SDK 团队需要应用的应用程序 ID。 可按此方式找到此内容：在 [Azure 门户](https://portal.azure.com/)中的“所有应用程序”下，找到“应用程序 ID”列。 建议通过电子邮件 msintuneappsdk@microsoft.com 联系 Intune SDK 团队。
     
### <a name="working-with-the-intune-sdk"></a>使用 Intune SDK
以下说明专门面向最终用户设备上要求使用 Intune 应用保护策略的所有 Android 和 Xamarin 应用。

1. 使用 [Intune SDK for Android 指南](https://docs.microsoft.com/intune/app-sdk-android#configure-azure-active-directory-authentication-library-adal)中定义的步骤配置 ADAL。

> [!NOTE]
> 与应用关联的“客户端 ID”一词与 Azure 门户中与应用关联的“应用程序 ID”一词的含义相同。 
> * 启用 SSO 需要“通用 ADAL 配置”#2。

2. 通过将以下值放入清单来启用默认注册：```xml <meta-data android:name="com.microsoft.intune.mam.DefaultMAMServiceEnrollment" android:value="true" />```
   > [!NOTE] 
   > 这必须是应用中唯一的 MAM-WE 集成。 如果有任何其他调用 MAMEnrollmentManager API 的尝试，则可能发生冲突。

3. 通过将以下值放入清单来启用所需的 MAM 策略：```xml <meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />```
   > [!NOTE] 
   > 这将强制用户在设备上下载公司门户，并且需要完成默认注册流程才能使用。

### <a name="see-also"></a>另请参阅
- [决定如何使用 Microsoft Intune 为移动应用程序管理准备应用](apps-prepare-mobile-application-management.md)

- [Microsoft Intune App SDK for Android 开发人员指南](app-sdk-android.md)
