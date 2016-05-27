---
# required metadata

title: 使用应用包装工具准备管理 iOS 应用 | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 99ab0369-5115-4dc8-83ea-db7239b0de97

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用 Intune 应用包装工具为移动应用程序管理准备 iOS 应用
使用**适用于 iOS 的 Microsoft Intune 应用包装工具**修改内部 iOS 应用的行为，方法是限制应用的功能，而无需更改应用自身的代码。

该工具是在应用周围创建“包装程序”的 Mac OS 命令行应用程序。 处理应用后，可以使用你配置的[移动应用程序管理策略](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)来更改应用的功能。

若要下载该工具，请参阅[适用于 iOS 的 Microsoft Intune 应用包装工具](http://www.microsoft.com/en-us/download/details.aspx?id=45218)

## 步骤 1：满足使用应用包装工具的先决条件

|要求|更多信息|
|---------------|--------------------------------|
|支持的操作系统和工具集|你必须在运行 OS X 10.8.5 或更高版本的 Mac 计算机上运行应用包装工具，计算机还要安装 XCode 工具集 5 或更高版本。|
|签名证书和预配配置文件|你必须有 Apple 签名证书和预配配置文件。 请参阅 [Apple 开发人员文档](https://developer.apple.com/)|
|使用应用包装工具处理应用|应用必须由你公司或独立软件供应商 (ISV) 开发并签名。 你无法使用该工具处理 Apple Store 中的应用。 应用必须针对 iOS 7.0 或更高版本编写。 应用还必须是地址无关可执行文件 (PIE) 格式。 有关 PIE 格式的更多信息，请参阅 Apple 开发人员文档。 最后，应用的扩展名必须是 **.app** 或 **.ipa** 格式。|
|包装工具无法处理的应用|加密应用、未签名应用和带有扩展文件属性的应用。|
|使用 Azure Active Directory 库 (ADAL) 的应用|如果你的应用使用 ADAL，则应用结合的 ADAL 版本必须高于或等于 1.0.2，且开发人员必须授予其应用访问 Intune 移动应用程序管理资源的权限。<br /><br />有关如何使用 ADAL 的详细信息，请参阅本文中的[有关使用 Azure Active Directory 库的应用的信息](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md#information-for-apps-that-use-the-azure-active-directory-library)。|
|设置应用权利|在包装应用之前，必须设置权利，以便为应用提供除平常所授权限和功能以外的其他权限和功能。 有关说明，请参阅[设置应用权利](#setting-app-entitlements)。|

## 步骤 2：安装应用包装工具

1.  从 [Microsoft 下载中心](https://www.microsoft.com/download/details.aspx?id=45218)“适用于 iOS 的 Microsoft Intune 应用包装工具”页上，将应用包装工具的安装文件下载到 Mac 计算机。

2.  在 Mac 计算机上，双击安装文件 **Microsoft Intune App Wrapping Tool for iOS.dmg**

3.  选择“同意”以接受最终用户许可协议 (EULA)。 安装程序已安装并显示在 Mac 计算机上。

4.  打开安装程序，将显示的文件复制到 Mac 计算机上的新文件夹中。 现在，你可以断开已装载的安装程序驱动器。

    你现已运行应用包装工具。

## 步骤 3：运行应用包装工具

1.  在 Mac 计算机上，打开终端窗口并导航到你保存文件的文件夹。 由于可执行程序在包内，你必须运行以下命令：
```
    ./IntuneMAMPackager.app/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -a <client ID of input app> -r <reply URI of input app> -v true
```
    > [!NOTE]
    > Some parameters are optional as shown in the table below.

    **Example:** The following example command runs the app wrapping tool on an app named **MyApp.ipa**. A provisioning profile and SHA-1 hash are specified. The processed app is created and stored in the **/users/myadmin/Documents** on the Mac computer.

    ```
    /users/myadmin/Downloads/IntuneMAMPackager.app/Contents/MacOS/IntuneMAMPackager -i /users/myadmin/Downloads/MyApp.ipa -o /users/myadmin/Documents/MyApp_Wrapped.ipa -p /users/myadmin/Downloads/My_Provisioning_Profile_.mobileprovision -c 12A3BC45D67EF8901A2B3CDEF4ABC5D6E7890FAB –a 20e1cd0d-268e-4308-9583-02ae97dd353e –r https://contoso/ -v true
    ```
    You can use the following command line properties with the app wrapping tool:

|属性|更多信息|
  |------------|--------------------|
  |**-h**|显示应用包装工具可用的命令行属性。|
  |**-i**|指定输入应用的路径和文件名。|
  |**-o**|指定保存处理后的应用的路径。|
  |**-p**|指定 iOS 应用的配置文件的路径。|
  |**-c**|指定签名证书的 SHA1 哈希。|
  |**-a**|输入应用的客户端 ID（GUID 格式），如果应用使用 Azure Active Directory 库（可选）。|
  |**-r**|输入文件的重定向 URI，如果应用使用 Azure Active Directory 库（可选）。|
  |**-v**|将详细消息输出到控制台（可选）。|

2. 处理完成后，将显示消息 **“应用程序已包装成功”** 。

    如果出错，请参阅[错误消息](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md#error-messages)以寻求帮助。

3.  包装的应用已保存在你之前指定的输出文件夹内。 你现在可以将应用上载到 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 并关联一份移动应用程序管理策略。

    > [!IMPORTANT]
    > 你必须将应用上载为新应用。 你无法更新未包装版本的旧应用。

    现在，可以将应用部署到 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 组，并且该应用现将在使用所指定的应用限制的设备上运行。

## 错误消息和日志文件
使用以下信息可排查应用包装工具出现的问题。

### 错误消息
如果应用包装工具失败，将显示以下错误消息之一：

|错误消息|更多信息|
|-----------------|--------------------|
|你必须指定有效的 iOS 配置文件。|配置文件可能无效。 检查以确保你有正确的设备权限，以及针对开发或分发的正确配置文件。 配置文件可能已过期。|
|指定有效的输入应用程序名称。|确保你指定的输入应用程序名称正确。|
|指定输出应用程序的有效路径。|确保你指定的输出应用程序路径存在且正确。|
|指定有效的输入配置文件。|确保你提供了有效的配置文件名称和扩展名。 你的配置文件可能没有授权，或你可能没有包括 **–p** 命令行选项。|
|未找到你指定的输入应用程序。 指定有效的输入应用程序名称和路径。|确保你的输入应用路径有效且存在。 确保输入应用在指定的位置。|
|未找到你指定的输入配置文件。 指定有效的输入配置文件。|确保输入配置文件的路径有效，并且你指定的文件存在。|
|未找到你指定的输出应用程序文件夹。 指定输出应用程序的有效路径。|确保你指定的输出路径有效且存在。|
|输出应用没有 .ipa 扩展名。|应用包装工具仅接受扩展名为 **“.app”** 和 **“.ipa”** 的应用。 确保你的输出文件的扩展名有效。|
|指定了无效的签名证书。 指定有效的 Apple 签名证书。|确保你从 Apple 开发人员门户下载了正确的签名证书。 配置证书也可能已过期。 如果你的 Apple 证书和配置文件可以正确地在 Xcode 内为应用签名，则他们对应用包装工具是有效的。|
|你指定的输入应用程序无效。 指定有效的应用程序。|确保你有编译为的“.app”或“.ipa”的有效 iOS 应用程序。|
|你指定的输入应用程序已加密。 指定有效的未加密应用程序。|应用包装工具不支持加密的应用。 指定未加密的应用。|
|你指定的输入应用程序不是地址无关可执行文件 (PIE) 格式。 指定有效的 PIE 格式应用程序。|地址无关可执行文件 (PIE) 应用运行时可以加载在随机内存地址，这对安全性有益。 有关详细信息，请参阅你的 Apple 开发人员文档。|
|你指定的输入应用已包装。 指定有效的未包装应用程序。|你无法处理本工具已经处理过的应用。 如果你想要再次处理应用，请使用原版应用运行本工具。|
|你指定的输入应用程序未签名。 指定已签名的有效应用程序。|应用包装工具需要已签名的应用。 咨询开发人员文档以了解如何对已包装的应用签名。|
|你指定的输入应用程序必须为 .ipa 或 .app 格式。|应用包装工具仅接受 .app 或 .ipa 扩展名。 确保你的输入文件的扩展名有效，并且编译为的“.app”或“.ipa”文件。|
|你指定的输入应用已包装，并且为最新的策略模板版本。|应用包装工具将不会用最新的策略模板版本重新包装现有的已包装的应用。|
|所给的 Azure Active Directory 客户端 ID 不是格式正确的 GUID。 请指定有效的客户端 ID。|使用客户端 ID 参数时，确保你提供了有效的 GUID 格式客户端 ID。|
|所给的 Azure Active Directory 回复 URI 不是格式正确的 URI。 请指定有效的回复 URI。|使用回复 URI 命令行属性时，请确保你提供了有效的回复 URI。|
|警告：你没有指定 SHA1 证书哈希。 确保你的已包装应用程序在部署前已签名。|确保你指定了有效的 SHA 哈希（使用 **“–c”** 命令行属性）。|

### 应用包装工具的日志文件
使用应用包装工具包装的应用生成写入 iOS 客户端设备控制台的日志。 此信息在你对应用程序存在疑问且如果该问题与应用包装工具有关并需要进行诊断的情况下有用。 若要检索此信息，请使用以下步骤：

1.  通过运行应用，再现该问题。

2.  通过按照 Apple 的[调试已部署的 iOS 应用](https://developer.apple.com/library/ios/qa/qa1747/_index.html)说明操作，收集控制台输出

3.  通过各控制台输入以下脚本，筛选应用限制输出的已保持的日志：

    ```
    grep “IntuneAppRestrictions” <text file containing console output> > <required filtered log file name>
    ```
    你可以将筛选后的日志提交给 Microsoft。

    > 在日志文件中，“内部版本”代表 Xcode 的内部版本。

    包装的应用也将向用户提供在应用损坏后直接通过电子邮件从设备发送日志的选项。 用户可以将日志发送给你进行检查，并在需要时转发给 Microsoft。

## 有关使用 Azure Active Directory 库的应用的信息
该部分的信息仅适用于使用 Azure Active Directory 库 (ADAL) 的应用。 如果不确定你的应用是否使用此库，请联系应用的开发人员。

应用结合的 ADAL 的版本必须高于或等于 1.0.2。

对于使用 ADAL 的应用，则必须满足下列要求：

-   应用结合的 ADAL 的版本必须高于或等于 1.0.2

-   开发人员必须授予其应用访问 Intune 移动应用程序管理资源的权限，如[对使用 ADAL 的应用所需执行的步骤](#steps-to-follow-for-apps-that-use-adal)中所述

### 所需获取的标识符的概述
使用 ADAL 的应用必须通过 Azure 管理门户注册，以获得其应用的两个唯一标识符：

|标识符|更多信息|默认值|
|--------------|--------------------|-----------------|
|**客户端 ID**|在应用注册至 Azure Active Directory 后，会为每个应用生成唯一 GUID 标识符。<br /><br />如果知道应用的特定客户端 ID，则可以指定此值。 否则，将使用默认值。|6c7e8096-f593-4d72-807f-a5f86dcc9c77|
|**重定向 URI**|开发人员可以在将他们的应用注册到 Azure Active Directory 时提供 URI 值，以确保身份验证令牌明确地返回到该端点。<br /><br />提供重定向 URI 是应用包装工具的一项可选参数。 如果未指定，则会使用默认 URI。|urn:ietf:wg:oauth:2。0:oob|


### 对使用 ADAL 的应用所需执行的步骤

1.  查看[所需获取的标识符的概述](#overview-of-identifiers-you-need-to-get)以确定需要获取的值。

2.  通过执行以下操作，在 Azure Active Directory 中配置对移动应用程序管理的访问：

    1. 在 Azure 管理门户登录现有的 Azure Active Directory 帐户。

    2.  单击 Azure Active Directory 中的 **“现有 LOB 应用程序注册”** 。

    3.  在“配置”部分，选择“配置对其他应用程序中的 Web API 的访问权限”

    4.  在“对其他应用程序的权限”部分，从第一个下拉列表中选择“Intune 移动应用程序管理”

        现在可以在应用包装工具中使用应用的客户端 ID。 你可以在 Azure Active Directory 管理门户中找到应用的客户端 ID，如[所需获取的标识符的概述](#overview-of-identifiers-you-need-to-get)部分中所述。

3.  将 **Client-ID**（使用属性 **–a**）和 **Redirect-URI** 值用作应用包装工具中的命令行属性。 如果没有这些值，则使用默认值。 你必须同时指定这两个值，否则最终用户将无法成功地对已处理的应用进行身份验证。

### 证书、预配配置文件和身份验证要求

|要求|详细信息|
|---------------|-----------|
|预配配置文件|**将配置文件包括在内之前，确保它有效** - 处理 iOS 应用时，应用包装工具不会检查配置文件是否已过期。 如果指定了过期的配置文件，应用包装工具将包括过期的配置文件，并且在将应用安装到 iOS 设备之前，你将无法知道存在问题。|
|Certificate|**指定证书前，确保证书有效** - 处理 iOS 应用时，该工具不会检查证书是否已过期。 如果提供了过期证书的哈希，工具将对应用进行处理并签名，但是应用将无法安装在设备上。<br /><br />**确保用于给封装的应用程序签名的证书在配置文件中有匹配的配置文件** - 该工具不会验证配置文件是否有对应的用于给包装的应用程序签名的证书。|
|身份验证|设备必须设置 PIN 以使加密起作用。 在你部署了已包装应用程序的设备上，点击设备上的状态栏将要求用户用 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 重新进行身份验证。 已包装应用程序中的默认策略是“重新启动时进行身份验证”。 iOS 在退出应用然后重新启动时会处理任何外部通知（例如电话呼叫）。<br /><br />对于已包装的应用，将缓存第一个登录同一发布者的任何已包装的应用的用户。 此点之后，仅缓存允许访问该应用的用户。 要重置用户，设备必须取消注册然后再重新注册。|

### 有关 ADAL 的故障排除和技术说明

-   如果没有找到 ADAL 资源，工具将包括 ADAL 动态库。 工具将在根文件夹中搜索名为 **“ADALiOS.bundle”** 的 ADAL 库。

-   该工具不会在应用内搜索 ADAL 二进制文件（如果有）。 如果应用链接至过时的版本，在启用了身份验证策略后，则可能在登录过程中出现运行时错误。

-   [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 将 AAD 令牌提取至 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] MAM 资源 ID，用于进行身份验证。 但是，它不用于任何会进而验证其有效性的调用中。 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 仅读取已登录用户的 UPN 来确定应用的访问权限。 AAD 令牌不用于任何未来的服务调用。

-   由于身份验证令牌存储在同一 Keychain 内，则所以自同一发布者的应用共享身份验证令牌。 如果你想要隔离特定应用程序，则必须对该应用使用不同的签名证书和配置文件。

-   如果提供了你的客户端应用程序的客户端 ID 和重定向 URI，则可以避免两次登录提示。 该客户端 ID 需要注册以访问在 AAD 仪表板中发布的 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] MAM 资源 ID。 如果不这样做，将导致应用运行时登录失败。

## 设置应用权利
在包装应用之前，可以授予**权利**，以便为应用提供其他权限和功能，使其能够执行比一般情况下更多的操作。  **权利文件**在代码签名过程中用于指定应用内的特殊权限（例如，对共享密钥链的访问权限）。 在应用开发过程中，会在 Xcode 内启用称为**功能**的特定应用服务。 启用后，功能即反映在权利文件中。 有关权利和功能的详细信息，请参阅 iOS 开发人员库中的[添加功能](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html)。 有关支持的功能的完整列表，请参阅[支持的功能](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SupportedCapabilities/SupportedCapabilities.html)

### 适用于 iOS 的应用包装工具支持的功能

|功能|描述|推荐指南|
|--------------|---------------|------------------------|
|应用组|使用应用组可让多个应用访问共享容器，并支持应用之间的其他进程间通信。<br /><br />若要启用应用组，请打开“功能”窗格，并单击“应用组”部分中的“开”开关。 你可以添加应用组，也可以选择现有应用组。|使用应用组时，请使用反向 DNS 表示法：<br /><br />*group.com.companyName.AppGroup*|
|后台模式|启用后台模式后，iOS 应用可以在后台继续运行。||
|数据保护|数据保护可提高 iOS 应用存储在磁盘上的文件的安全级别。 数据保护使用特定设备提供的内置加密硬件，将文件以加密格式存储在磁盘上。 你的应用需预配为使用数据保护。||
|应用内购买|应用内购买直接将应用商店嵌入你的应用中，允许你连接到应用商店并且安全地处理用户付款。 你可以使用应用内购买收取有关增强功能或应用可用的其他内容的付款。||
|密钥链共享|启用密钥链共享后，你的应用可以与你的团队开发的其他应用共享密钥链中的密码。|使用密钥链共享时，请使用反向 DNS 表示法：<br /><br />*com.companyName.KeychainGroup*|
|个人 VPN|启用个人 VPN 后，你的应用可以使用网络扩展框架来创建和控制自定义系统 VPN 配置。||
|推送通知|Apple Push Notification 服务 (APNs) 允许不在前台运行的应用通知用户，它有关于该用户的信息。|若要使推送通知正常工作，需使用应用特定的预配配置文件。<br /><br />按照 [Apple 开发人员文档](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html)中的步骤操作|
|无线附件配置|启用无线附件配置可向项目添加外部附件框架，并允许应用配置 MFi Wi-Fi 附件。||

### 权利启用步骤

1.  启用应用中的功能：

    1.  在 Xcode 中，导航到应用的目标，并单击“功能”窗格。

    2.  打开相应的功能。 有关每项功能以及如何确定正确值的详细信息，请参阅 iOS 开发人员库中的[添加功能](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html)。

    3.  记下在此过程中创建的任何 ID。

    4.  生成要包装的应用并对其签名。

2.  启用预配配置文件中的权利：

    1.  登录到 Apple 开发人员会员中心。

    2.  为应用创建预配配置文件。 有关说明，请参阅[如何获取适用于 iOS 的 Intune 应用包装工具的先决条件](http://blogs.technet.com/b/microsoftintune/archive/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios.aspx)

    3.  在预配配置文件中，启用与应用中相同的权利。 你需要提供在应用开发过程中指定的相同 ID。

    4.  完成预配配置文件向导并下载你的文件。

3.  确保已经满足所有先决条件，然后对应用进行包装。

### 排查与权利相关的常见错误
如果适用于 iOS 的应用包装工具显示权利错误，请尝试下列故障排除步骤。

|问题|原因|解决方法|
|---------|---------|--------------|
|无法分析从输入应用程序生成的权利。|应用包装工具无法读取从应用提取的权利文件。 权利文件的格式可能不正确。|检查应用的权利文件。 为此，请按照下面详述的说明操作。 检查权利文件时，请检查所有格式不正确的语法。 该文件应为 XML 格式。|
|预配配置文件中缺少权利（已列出缺少的权利）。 使用具有这些权利的预配配置文件对应用重新封装。|预配配置文件中启用的权利与应用中启用的功能不匹配。 与特定功能（即，应用组、密钥链访问等等）相关联的 ID 也存在这种不匹配。|通常情况下，你可以创建一个新的预配配置文件，在其中启用与应用相同的功能。 如果配置文件和应用之间的 ID 不匹配，应用包装工具将更换 ID（如果能）。 如果新建配置文件后仍然收到此错误，可以尝试使用 **–e** 参数从应用中删除权利（请参阅下面的“使用 –e 参数从应用中删除权利”部分）。|

### 查找已签名应用的现有权利
若要查看已签名应用和预配配置文件的现有权利，请执行以下操作：

1.  找到 .ipa 文件并将其扩展名更改为 .zip。

2.  展开该 .zip 文件。 这将生成一个包含 .app 包的 Payload 文件夹。

3.  使用 codesign 工具检查 .app 包上的权利，如下所示：

    ```
    $ codesign -d --entitlements :- "Payload/YourApp.app"
    ```
    其中 `YourApp.app` 是 .app 包的实际名称。

4.  使用安全工具检查应用的嵌入式预配配置文件的权利：

    ```
    $ security -D -i "Payload/YourApp.app/embedded.mobileprovision"
    ```
    其中 `YourApp.app` 是 .app 包的实际名称。

### 使用 – e 参数从应用中删除权利
此命令将删除不在权利文件中的应用中的任何已启用功能。 如果删除应用正在使用的功能，它会中断你的应用。 如果拥有一个默认具有所有功能的供应商生产应用是一个你可能会删除丢失功能的情况示例。

```
./IntuneMAMPackager.app/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -e
```

## 应用包装工具的安全和隐私
在你使用应用包装工具时，使用以下安全和隐私的最佳做法。

-   你指定的签名证书、配置证书和业务线应用必须在同一台你用于运行应用包装工具的 Mac 计算机上。 如果文件在 UNC 路径上，确保这些文件可以从 Mac 计算机上访问。 路径必须受到 IPsec 和 SMB 签名的保护。

    导入到 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 控制台中的包装的应用程序应位于你在其上运行该工具的同一计算机上。 如果文件在 UNC 路径上，确保它可以在运行 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 控制台的计算机上访问。 路径必须受到 IPsec 和 SMB 签名的保护。

-   从 Microsoft 下载中心站点下载应用包装工具的环境必须受到 IPsec 和 SMB 签名的保护。

-   你处理的应用必须来自值得信任的来源，以保护不受攻击。

-   确保你在应用包装工具中指定的输出文件夹是安全的，尤其当它是远程文件夹时。

-   包含文件上载对话框的 iOS 应用可以允许用户规避应用于应用的剪切、复制和粘贴限制。 例如，用户可能使用文件上载对话框来上载应用数据的屏幕截图。

-   如果用户在自己设备上从包装应用监视文档文件夹，他们可能看到一个名为 **“.msftintuneapplauncher”**的文件夹。 如果更改了该文件夹或将其删除，则可能影响受限制应用的正确运行。

### 另请参阅
- [决定如何使用 Microsoft Intune 为移动应用程序管理准备应用](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)</br>
- [使用 Microsoft Intune 策略管理设备上的设置和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)</br>
- [使用 SDK 启用针对移动应用程序管理的应用](use-the-sdk-to-enable-apps-for-mobile-application-management.md)


<!--HONumber=May16_HO2-->


