---
title: "使用 App Wrapping Tool 包装 Android 应用 | Microsoft Intune"
description: "使用本文中提供的信息，了解不更改应用本身代码即可包装 Android 应用的方法。 准备应用以便应用移动应用管理策略。"
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: oldang
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b25c7d7063ce586bb1cd960534f3e2ed57f6aec4
ms.openlocfilehash: 7c61ad6a3122793ddd66547b7040f978705b540c


---

# <a name="prepare-android-apps-for-mobile-application-management-with-the-intune-app-wrapping-tool"></a>使用 Intune 应用包装工具为移动应用程序管理准备 Android 应用

通过限制应用的功能，而不更改应用自身的代码，使用适用于 Android 的 Microsoft Intune 应用包装工具，更改内部 Android 应用的行为。

该工具是一个 Windows 命令行应用程序，它在 PowerShell 中运行并在 Android 应用周围创建“包装器”。 包装应用后，可通过在 Intune 中配置[移动应用程序管理策略](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)来更改应用的功能。


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

- Android 要求对所有应用包 (.apk) 进行签名。 使用 Java keytool 生成对已包装输出应用进行签名所需的凭据。 例如，以下命令使用 Java 可执行文件 keytool.exe 生成应用包装工具可用于对已包装输出应用进行签名的密钥。

    ```
    keytool.exe -genkeypair -v -keystore mykeystorefile -alias mykeyalias -keyalg RSA -keysize 2048 -validity 50000
    ```
    此示例通过使用 RSA 算法生成密钥对（2,048 位公钥和相关私钥）。 然后将公钥包装成存储为单元素证书链的 X.509 v3 自签名证书。 此证书链和私钥被存储在一个名为“mykeystorefile”的新密钥存储条目中，由别名“mykeyalias”标识。 该密钥存储条目的有效期为 50,000 天。

    该命令将提示为密钥存储和密钥提供密码。 使用安全的密码，但需要记住密码，因为运行应用包装工具时会用到该密码。

    有关详细的文档，请在 Oracle 文档网站上了解更多关于 Java [密钥工具](http://docs.oracle.com/javase/6/docs/technotes/tools/windows/keytool.html) 和 Java [密钥存储](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html)的信息。

## <a name="install-the-app-wrapping-tool"></a>安装应用包装工具

1.  从 [GitHub 存储库](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android)将 Intune App Wrapping Tool for Android 的安装文件 InstallAWT.exe 下载到 Windows 计算机。 打开该安装文件。

2.  接受许可协议，然后完成安装。

注意将工具安装到的文件夹。 默认位置为：C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool。

## <a name="run-the-app-wrapping-tool"></a>运行应用包装工具

1.  在安装了应用包装工具的 Windows 计算机上，在管理员模式下打开 PowerShell 窗口。

2.  从安装该工具的文件夹导入应用包装工具 PowerShell 模块：

    ```
    Import-Module .\IntuneAppWrappingTool.psm1
    ```

3.  通过使用 **invoke-AppWrappingTool** 命令运行该工具，它使用以下语法：
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
|**-SigAlg**&lt;SecureString&gt;| （可选）用于签名的签名算法的名称。 该算法必须与私钥兼容。|示例：SHA256withRSA、SHA1withRSA、MD5withRSA|
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

## <a name="security-considerations-for-running-the-app-wrapping-tool"></a>运行应用包装工具的安全注意事项
防止潜在的欺骗、信息泄露和特权提升攻击：

-   确保输入业务线 (LOB) 应用程序、输出应用程序和 Java 密钥存储位于运行应用包装工具的同一台 Windows 计算机上。

-   将输出应用程序导入到运行该工具的同一台计算机上的 Intune 控制台。 有关 Java keytool 的详细信息，请参阅 [keytool](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html)。

-   如果输出应用程序和工具位于通用命名约定 (UNC) 路径，并且未在同一台计算机上运行工具和输入文件，则使用 [Internet 协议安全性 (IPsec)](http://en.wikipedia.org/wiki/IPsec) 或 [服务器消息块 (SMB) 签名](https://support.microsoft.com/en-us/kb/887429)将环境设置为安全。

-   确保应用程序来源可信。

-   确保包含已包装应用的输出目录的安全。 考虑为输出使用用户级目录。

### <a name="see-also"></a>另请参阅
- [决定如何使用 Microsoft Intune 为移动应用程序管理准备应用](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)

- [使用 SDK 启用针对移动应用程序管理的应用](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Nov16_HO1-->


