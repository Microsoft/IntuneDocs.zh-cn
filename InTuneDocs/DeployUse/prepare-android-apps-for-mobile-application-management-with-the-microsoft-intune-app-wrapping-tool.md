---
# required metadata

title: 使用应用包装工具准备管理 Android 应用 | Microsoft Intune | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用 Intune 应用包装工具为移动应用程序管理准备 Android 应用
使用**适用于 Android 的 Microsoft Intune 应用包装工具**修改内部 Android 应用的行为，让你配置应用的功能而无需修改应用自身的代码。

该工具是一个 Windows 命令行应用程序，它在 PowerShell 中运行并在应用周围创建“包装器”。 处理应用后，可以使用你配置的[移动应用程序管理策略](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)来更改应用的功能。

如果你的应用正在使用 Azure Active Directory 身份验证库 (ADAL)，则在包装你的应用之前，必须完成[如何包装使用 Azure Active Directory 库的应用](#how-to-wrap-apps-that-use-the-azure-active-directory-library)中的步骤。 如果不确定你的应用是否使用此库，请联系应用的开发人员。

在运行工具前查看[运行应用包装工具的安全注意事项](#security-considerations-for-running-the-app-wrapping-tool)。 若要下载该工具，请参阅[适用于 Android 的 Microsoft Intune 应用包装工具](https://www.microsoft.com/download/details.aspx?id=47267)

## 步骤 1：满足使用应用包装工具的先决条件

-   必须在运行 Windows 7 或更高版本的 Windows 计算机上运行应用包装工具。

-   输入应用必须是有效的 Android 应用程序包且具有扩展名为 **.apk** 的文件，同时：

    -   不能加密

    -   必须尚未被应用包装工具包装

    -   必须是针对 Android 4.0 或更高版本编写的

-   应用必须由公司开发，或为公司开发。 无法使用此工具处理从 Google Play 商店中下载的应用。

-   若要运行应用包装工具，必须安装最新版 [Java Runtime Environment](http://java.com/download/)，然后确保已在 Windows 环境变量中将 Java 路径变量设置为 **C:\ProgramData\Oracle\Java\javapath**。 有关更多帮助，请参阅 [Java 文档](http://java.com/download/help/)

    > [!NOTE]
    > 在某些情况下，32 位版本的 Java 可能会导致内存问题。 我们建议你改为安装 64 位版本。

## 步骤 2：安装应用包装工具

1.  将应用包装工具的安装文件从 Microsoft 下载中心下载到 Windows 计算机，并打开该安装文件。

2.  接受许可协议，然后完成安装。

注意将工具安装到的文件夹。 默认位置为：**C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool**

## 步骤 3：运行应用包装工具

1.  在安装应用包装工具的 Windows 计算机上打开 PowerShell 窗口。

2.  从安装该工具的文件夹导入应用包装工具 PowerShell 模块：

    ```
    Import-Module .\IntuneAppWrappingTool.psm1
    ```

3.  同时使用 **invoke-AppWrappingTool** 命令及以下参数来运行该工具。 标记为“可选”的参数适用于使用 Azure Active Directory 库 (ADAL) 的应用。 有关详细信息，请参阅[如何包装使用 Azure Active Directory 库的应用](#how-to-wrap-apps-that-use-the-azure-active-directory-library)

|参数|更多信息|示例|
|-------------|--------------------|---------|
|**-InputPath**&lt;String&gt;|源 Android 应用 (.apk) 的路径。| |
|**-OutputPath**&lt;String&gt;|到“输出”Android 应用的路径。 如果这是与 InputPath 相同的目录路径，则打包将失败。| |
|**-KeyStorePath**&lt;String&gt;|到包含用于签名的公钥/私钥对的密钥库文件的路径。| |
|**-KeyStorePassword**&lt;SecureString&gt;|用于解密密钥库的密码。| |
|**-KeyAlias**&lt;String&gt;|要用于进行签名的密钥的名称。| |
|**-KeyPassword**&lt;SecureString&gt;|用于解密私钥的密码，该私钥将用于签名。| |
|**-SigAlg**&lt;SecureString&gt;|用于签名的签名算法的名称。 该算法必须与私钥兼容。|示例：SHA256withRSA、SHA1withRSA、MD5withRSA|
|**-ClientID**&lt;GUID&gt;|输入应用的 Azure Active Directory 客户端 ID（可选）。| |
|**-AuthorityURI**&lt;Uri&gt;|输入应用的 Azure Active Directory 颁发机构 URI（可选）。| |
|**-SkipBroker**&lt;Boolean&gt;|指示输入应用程序是否支持设备级中转单一登录（可选）。 |**True** - 输入应用程序不支持设备级中转单一登录。 使用 NonBrokerRedirectURI 参数。 **False** - 输入应用程序支持设备级中转单一登录|
|**-NonBrokerRedirectURI**&lt;URI&gt;|如果 SkipBroker 为 True，则使用 Azure Active Directory 重定向 URI（可选）。|  |


CommonParameters

- （可选 - 支持常见的 PowerShell 参数，如 verbose、debug 等）

- 有关常见参数的列表，请参阅 [Microsoft 脚本中心](https://technet.microsoft.com/library/hh847884.aspx)

    ```
    Help Invoke-AppWrappingTool
    ```
- 若要查看工具的帮助，输入命令：

**要了解有关 Azure Active Directory (AAD) 集成的详细信息，请参阅[如何包装使用 Azure Active Directory 库的应用](#how-to-wrap-apps-that-use-the-azure-active-directory-library)**


    Import-Module "C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool\IntuneAppWrappingTool.psm1"
    Invoke-AppWrappingTool –InputPath <input-app.apk> -OutputPath <output-app.apk> -KeyStorePath <path-to-signing.keystore> -KeyAlias <signing-key-name> -ClientID <xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx> -AuthorityURI <http://AzureActiveDirectory.Authority.URL> -SkipBroker<$True|$False> -NonBrokerRedirectURI <urn:xxx:xx:xxxx:xx:xxx>

例如：

然后将提示你输入 **KeyStorePassword** 和 **KeyPassword**

## 将在指定的输出路径中生成并保存包装的应用和日志文件。
运行应用包装工具的安全注意事项

-   防止潜在的欺骗、信息泄露和特权提升攻击：

-   确保输入业务线应用程序、输出应用程序和 Java KeyStore 位于运行应用包装工具的同一台计算机上。

-   将输出应用程序导入到运行该工具的同一台计算机上的 Intune 控制台。

-   如果输出应用程序和工具位于通用命名约定 (UNC) 路径，并且未在同一台计算机上运行工具和输入文件，则使用 [Internet 协议安全性 (IPsec)](http://en.wikipedia.org/wiki/IPsec) 或[服务器消息块 (SMB) 签名](https://support.microsoft.com/en-us/kb/887429)将环境配置为安全

-   确保应用程序来自可靠来源，尤其是使用 Azure Active Directory (AAD) 时，这可能会使应用程序能够在运行时期间访问 AAD 令牌。 确保包含已包装应用的输出目录的安全。

## 考虑为输出使用用户级目录。
如何包装使用 Azure Active Directory 库的应用

### 如果你的应用正在使用 Azure Active Directory 身份验证库 (ADAL)，则在包装你的应用程序之前，必须完成这些步骤。
步骤1：确保已满足 ADAL 的要求

-   对于使用 ADAL 的应用，则必须满足下列要求：

-   应用结合的 ADAL 的版本必须高于或等于 1.0.2。

### 开发人员必须授予其应用访问 Intune 移动应用程序管理资源的权限，如[步骤3：在 AAD 中配置对移动应用程序管理的访问权限](#step-3-configure-access-to-mobile-app-management-in-aad)中所述
步骤 2：查看注册应用时需要获取的标识符 在下一步骤中，你将使用 Azure 管理门户来注册你的应用（该应用通过 Azure Active Directory (AAD) 使用 ADAL）以获取下表中列出的唯一标识符。

|然后，在集成 ADAL 与该应用时将标识符提供给开发人员。|标识符|更多信息|
|--------------|--------------------|-----------------|
|**默认值**|客户端 ID<br /><br />在应用注册到 AAD 后，为该应用生成的唯一 GUID 标识符。 如果已知应用的客户端 ID，则指定该值。|否则，请使用默认值。|
|**6c7e8096-f593-4d72-807f-a5f86dcc9c77**|颁发机构 URI<br /><br />AAD 对象的颁发机构统一资源标识符 (URI) 值（例如，用户和组）。 AuthorityURI 参数对应用包装工具为可选。||
|**如果不使用此参数，则将使用默认 URI。**|SkipBroker<br /><br />指示是否将把公司门户用作代理的值。<br /><br />**True** – 公司门户将不用于 ADAL 身份验证。 **False** – 公司门户将用于 ADAL 身份验证。||
|**公司门户出于单一登录目的使用已注册用户。**|非代理重定向 URI|ADAL 不使用代理应用（Intune 公司门户）时将使用的登录 URI。|
|**urn:ietf:wg:oauth:2。0:oob**|资源 ID||

### 指向应用的 AAD 资源的指针。
步骤 3：在 AAD 中配置对移动应用管理的访问权限

1.  在你可以在应用包装工具中使用应用的 AAD 注册值之前，应用开发人员必须通过执行以下步骤授予该应用对 Intune 移动应用程序管理资源的访问权限：

2.  在 Azure 管理门户中登录到现有 AAD 帐户。

3.  选择“现有 LOB 应用程序注册”

4.  在“配置”部分，选择“配置对其他应用程序中的 Web API 的访问权限”

在“对其他应用程序的权限”部分，从第一个下拉列表中选择“Intune 移动应用程序管理” 你现在可以在应用包装工具中使用该应用的客户端 ID。

### 你可以在 Azure Active Directory 管理门户中找到客户端 ID，如[步骤 2：查看注册应用时需要获取的标识符](#step-2-review-the-identifiers-you-need-to-get-when-you-register-the-app)中所述
步骤 4：在应用包装工具中使用 AAD 标识符值 使用你从注册过程获取的标识符值，在应用包装工具中输入该值作为命令行属性。 必须指定表中的所有值，以便最终用户可对应用成功进行身份验证。

|如果不指定值，则使用默认值。|标识符|
|--------------|-------------|
|参数|客户端 ID|
|ClientID|颁发机构 URI|
|颁发机构 URI|SkipBroker|
|SkipBroker|非代理重定向 URI|
|NonBrokerRedirectURI|资源 ID|
ResourceID

-   包装应用时请记住以下几点： 应用包装工具不会在应用内搜索 ADAL 二进制文件（如果有）。

-   如果应用链接至二进制文件的过时版本，在启用了身份验证策略后，则可能在登录过程中出现运行时错误。 若要验证身份验证是否成功， [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 提取与 MAM 资源 ID 关联的 AAD 令牌。 但是，此令牌不用于任何会进而验证其有效性的调用中。

-   仅读取已登录用户的用户主体名称 (UPN) 来确定应用的访问权限。 AAD 令牌不用于任何未来的服务调用。

-   由于身份验证令牌存储在同一密钥链内，因此来自同一发布者的应用将共享身份验证令牌。 若要隔离特定应用，则对该应用使用不同的签名证书、设置配置文件密钥库和密钥别名。 如果提供了你的客户端应用程序的客户端 ID 和颁发机构 URI，则可以避免两次登录提示。


### 你需要注册该客户端 ID 以使其能够访问在 AAD 仪表板中发布的 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] MAM 资源 ID。
- [如果不注册该客户端 ID，则应用运行时用户登录失败。](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)

- [另请参阅](use-the-sdk-to-enable-apps-for-mobile-application-management.md)


<!--HONumber=May16_HO2-->


