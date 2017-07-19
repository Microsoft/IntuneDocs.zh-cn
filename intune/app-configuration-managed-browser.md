---
title: "使用 Managed Browser 应用管理 Web 访问"
titleSuffix: Intune on Azure
description: "部署 Managed Browser 应用程序，以限制 Web 浏览和到其他应用的 Web 数据传输。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1feca24f-9212-4d5d-afa9-7c171c5e8525
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e85306934b68f64bad8c223ac117190607db8473
ms.sourcegitcommit: fd5b7aa26446d2fa92c21638cb29371e43fe169f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2017
---
# <a name="manage-internet-access-using-managed-browser-policies-with-microsoft-intune"></a>使用 Microsoft Intune 的 Managed Browser 策略管理 Internet 访问

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Managed Browser 是一款 Web 浏览应用，可以从公共应用商店中下载它以供组织使用。 通过 Intune 配置时，Managed Browser 可以：
- 用于通过 MyApps 服务进行单一登录来访问公司网站和 SaaS 应用，并保护 Web 数据。
- 使用一系列 URL 和域进行预配置，以限制用户可在公司中导航到的网站。
- 使用主页和指定的书签进行预配置。

由于此应用已与 Intune SDK 集成，因此也可以向其应用应用保护策略，包括：
- 控制剪切、复制和粘贴操作的使用
- 防止发生屏幕捕获
- 确保指向用户所选内容的链接仅在其他托管应用中打开。

有关详细信息，请参阅[什么是应用保护策略？](/intune/app-protection-policy)

可以将这些设置应用于已注册的 Intune 设备及已注册其他设备管理产品的设备，还可应用于未进行托管的设备。

如果用户从应用商店中安装了 Managed Browser，并且 Intune 未托管它，则可将其用作基本的 Web 浏览器，其支持通过 Microsoft MyApps 网站进行单一登录。 用户将被直接转到 MyApps 网站，在其中用户可以看到其预配的所有 SaaS 应用程序。
Intune 未托管 Managed Browser 期间，无法访问由 Intune 托管的其他应用程序中的数据。 

Managed Browser 不支持安全套接字层版本 3 (SSLv3) 加密协议。

可以针对以下设备类型创建 Managed Browser 策略：

-   运行 Android 4 和更高版本的设备

-   运行 iOS 8.0 及更高版本的设备

Intune Managed Browser 支持从 [Microsoft Intune 应用程序合作伙伴](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx)打开 Web 内容。

## <a name="create-a-managed-browser-app-configuration"></a>创建 Managed Browser 应用配置

1.  登录到 Azure 门户中。
2.  选择“更多服务” > “监视 + 管理” > “Intune”。
3.  在管理列表中的“移动应用”边栏选项卡上，选择“应用配置策略”。
4.  在“应用配置策略”边栏选项卡上，选择“添加”。
5.  在“添加应用配置”边栏选项卡上，输入应用配置设置的“名称”和可选“描述”。
6.  对于“设备注册”类型，请选择“未注册 Intune”。
7.  选择“选择所需应用”，然后在“目标应用”边栏选项卡上，选择适用于 iOS 或适用于 Android（或适用于两者）的“Managed Browser”。
8.  选择“确定”，返回“添加应用配置”边栏选项卡。
9.  选择“配置设置”。 在“配置”边栏选项卡上，定义键值对来为 Managed Browser 提供配置。 请参阅本主题的后续部分，了解可以定义的不同键值对。
10. 完成后，选择“确定”。
11. 在“添加应用配置”边栏选项卡上，选择“创建”。
12. 创建新配置后，其显示在“应用配置”边栏选项卡上。

>[!IMPORTANT]
>目前，Managed Browser 依赖于自动注册。 对于要应用的应用配置，设备上的其他应用程序必须已由 Intune 应用保护策略托管。

## <a name="assign-the-configuration-settings-you-created"></a>分配已创建的配置设置

将这些设置分配到 Azure AD 用户组。 如果用户安装了 Managed Browser 应用，则应用将按指定的设置进行管理。

1. 在 Intune 移动应用程序管理仪表板的“设置”边栏选项卡上，选择“应用配置”。
2. 在应用配置列表中，选择一个想要分配的配置。
3. 在下一个边栏选项卡上，选择“用户组”。
4. 在“用户组”边栏选项卡上，选择想要将应用配置分配到的 Azure AD 组，然后选择“确定”。


## <a name="how-to-configure-application-proxy-settings-for-the-managed-browser"></a>如何为 Managed Browser 配置应用程序代理设置

可将 Intune Managed Browser 和 [Azure AD 应用程序代理]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started)配合使用，以支持 iOS 和 Android 设备用户实现以下方案：

- 用户下载并登录到 Microsoft Outlook 应用。  将自动应用 Intune 应用保护策略。 它们对保存的数据进行加密，并阻止用户将公司文件传输到设备上的非托管应用或位置。 当用户接下来点击 Outlook 中 intranet 站点的链接时，可以指定在 Managed Browser 应用中而不是在另一个浏览器中打开链接。
Managed Browser 识别出这个 intranet 站点已通过应用程序代理向用户公开。 将通过应用程序代理对用户进行自动路由，以便在进入 intranet 站点前进行任何适用的多重身份验证和条件性访问。 之前在用户处于远程访问状态时，可能找不到该站点，现在用户可正常访问该网站且 Outlook 中的链接也按预期工作。  

- 远程用户打开 Managed Browser 应用程序，并使用内部 URL 导航到 intranet 站点。 Managed Browser 识别出这个 intranet 站点已通过应用程序代理向用户公开。 将通过应用程序代理对用户进行自动路由，以便在进入 intranet 站点前进行任何适用的多重身份验证和条件性访问。
之前在用户处于远程访问状态时，可能找不到该站点，现在用户可正常访问。  

### <a name="before-you-start"></a>开始之前

- 确保通过 Azure AD 应用程序代理发布内部应用程序。
- 要配置应用程序代理和发布应用程序，请参阅[设置文档]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started#how-to-get-started)。 
- 必须使用 Managed Browser 应用的最低版本 1.2.0。
- Managed Browser 应用的用户具有分配给该应用的 [Intune 应用保护策略]( app-protection-policy.md)。
- 用户只能看到针对分配给自己的应用程序代理应用的自动重定向操作。

#### <a name="step-1-enable-automatic-redirection-to-the-managed-browser-from-outlook"></a>步骤 1：从 Outlook 启用指向 Managed Browser 的自动重定向
Outlook 必须配置可启用**将 Web 内容限制为仅在 Managed Browser 中显示**这一设置的应用保护策略。

#### <a name="step-2-assign-an-app-configuration-policy-assigned-for-the-managed-browser"></a>步骤 2：为 Managed Browser 分配一个应用配置策略。
此过程将 Managed Browser 应用配置为使用应用代理重定向。 使用创建 Managed Browser 应用配置的过程提供以下键值对：

|||
|-|-|
|Key|值|
|**com.microsoft.intune.mam.managedbrowser.AppProxyRedirection**|**true**|


## <a name="how-to-configure-the-homepage-for-the-managed-browser"></a>如何配置 Managed Browser 的主页

使用此设置可配置用户启动 Managed Browser 或创建新选项卡时看到的主页。 使用创建 Managed Browser 应用配置的过程提供以下键值对：

|||
|-|-|
|Key|值|
|**com.microsoft.intune.mam.managedbrowser.homepage**|指定有效 URL。 将阻止错误的 URL，这是一项安全措施。<br>示例：**https://www.bing.com**|


## <a name="how-to-configure-bookmarks-for-the-managed-browser"></a>如何配置 Managed Browser 的书签

使用此设置可配置一组可供 Managed Browser 用户使用的书签。

- 用户无法删除或修改这些书签
- 这些书签显示在列表顶部。 用户创建的任何书签显示在这些书签下方。

使用创建 Managed Browser 应用配置的过程提供以下键值对：

|||
|-|-|
|Key|值|
|**com.microsoft.intune.mam.managedbrowser.bookmarks**|此配置的值是一个书签列表。 每个书签都由书签标题和书签 URL 组成。 用字符 **&#124;** 分隔标题和 URL。<br><br>示例：**Microsoft Bing&#124;https://www.bing.com**<br><br>若要配置多个书签，可使用双字符 **&#124;&#124;** 分隔每对书签<br><br>示例：**Bing&#124;https://www.bing.com&#124;&#124;Contoso&#124;https://www.contoso.com**|

## <a name="how-to-specify-allowed-and-blocked-urls-for-the-managed-browser"></a>如何为 Managed Browser 指定允许和阻止的 URL

使用创建 Managed Browser 应用配置的过程提供以下键值对：

|||
|-|-|
|Key|值|
|选择：<br><br>- 指定允许的 URL（只允许这些 URL；不可访问其他网站）：**com.microsoft.intune.mam.managedbrowser.AllowListURLs**<br><br>- 指定阻止的 URL（可访问其他所有站点）： <br><br>**com.microsoft.intune.mam.managedbrowser.BlockListURLs**|键的对应值是 URL 列表。 将所有要允许或阻止的 URL 输入为单个值，以管道字符 **&#124;** 分隔。<br><br>例如：<br><br>-**URL1&#124;URL2&#124;URL3**<br>-**http://*.contoso.com/*&#124;https://*.bing.com/*&#124;https://expenses.contoso.com**|

>[!IMPORTANT]
>不要同时指定这两个键。 如果两个键同时针对同一个用户，则使用允许键，因为它是限制性最强的选项。
>此外，务必不要阻止重要的页面，例如你的公司网站。

### <a name="url-format-for-allowed-and-blocked-urls"></a>允许的 URL 和阻止的 URL 的格式
使用以下信息来了解有关指定允许和阻止列表中的 URL 时允许使用的格式和通配符：

-   可以根据以下允许模式列表中的规则使用通配符 (**&#42;**)：

-   在将 URL 输入列表时，确保对所有 URL 添加 **“http”** 或 **“https”** 作为前缀。

-   可以在地址中指定端口号。 如果未指定端口号，则使用以下值：

    -   对于 http，使用端口 80

    -   对于 https，使用端口 443

    不支持对端口号使用通配符。 例如，**http&colon;//www&period;contoso&period;com:*;** 和 **http&colon;//www&period;contoso&period;com: /*;** 不受支持。

-   使用下表了解指定 URL 时可以使用的允许模式：

|URL|详细信息|匹配|不匹配|
    |-------|---------------|-----------|------------------|
    |http://www.contoso.com|匹配单个页面|www.contoso.com|host.contoso.com<br /><br />www.contoso.com/images<br /><br />contoso.com/|
    |http://contoso.com|匹配单个页面|contoso.com/|host.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com|
    |http://www.contoso.com/&#42;|匹配以 www.contoso.com 开头的所有 URL|www.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com/videos/tvshows|host.contoso.com<br /><br />host.contoso.com/images|
    |http://&#42;.contoso.com/&#42;|匹配 contoso.com 下的所有子域|developer.contoso.com/resources<br /><br />news.contoso.com/images<br /><br />news.contoso.com/videos|contoso.host.com|
    |http://www.contoso.com/images|匹配单个文件夹|www.contoso.com/images|www.contoso.com/images/dogs|
    |http://www.contoso.com:80|匹配单个页面（使用端口号）|http://www.contoso.com:80|
    |https://www.contoso.com|匹配单个安全页面|https://www.contoso.com|http://www.contoso.com|
    |http://www.contoso.com/images/&#42;|匹配单个文件夹和所有子文件夹|www.contoso.com/images/dogs<br /><br />www.contoso.com/images/cats|www.contoso.com/videos|

-   以下是一些你不能指定的输入的示例：

    -   &#42;.com

    -   &#42;.contoso/&#42;

    -   www.contoso.com/&#42;images

    -   www.contoso.com/&#42;images&#42;pigs

    -   www.contoso.com/page&#42;

    -   IP 地址

    -   https://&#42;

    -   http://&#42;

    -   http://www.contoso.com:&#42;

    -   http://www.contoso.com: /&#42;

## <a name="security-and-privacy-for-the-managed-browser"></a>Managed Browser 的安全和隐私

-   在 iOS 设备上，如果用户访问的网站的证书已过期或不受信任，则无法打开该网站。

-   Managed Browser 不使用用户在设备上对内置浏览器进行的设置。 Managed Browser 无法访问这些设置。

-   如果配置与 Managed Browser 关联的一个应用保护策略中的选项**访问需要简单 PIN** 或**访问需要公司凭据**，且用户选择了身份验证页面上的帮助链接，那么无论是否已将这些用户添加到策略中的阻止列表中，他们都可以浏览任何 Internet 站点。

-   Managed Browser 仅能在直接访问站点时阻止访问。 使用中间服务（例如翻译服务）访问站点时，该策略则不会阻止访问。

-   在判断是否允许通过身份验证和访问 Intune 文档时，**&#42;.microsoft.com** 不在允许或阻止列表设置的约束范围之内。 始终允许。

### <a name="turn-off-usage-data"></a>关闭用法数据
Microsoft 会自动收集有关性能和 Managed Browser 使用情况的匿名数据，以改进 Microsoft 产品和服务。 用户可通过使用设备上的“使用情况数据”设置关闭数据收集。 不具有对此数据的收集的控制。


