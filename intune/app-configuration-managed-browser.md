---
title: "使用 Managed Browser 应用管理 Web 访问"
titleSuffix: Intune on Azure
description: "部署 Managed Browser 应用程序，以限制 Web 浏览和到其他应用的 Web 数据传输。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1feca24f-9212-4d5d-afa9-7c171c5e8525
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 7db72e25c8ba5846a50989b17d2c7adfb6f1c44e
ms.contentlocale: zh-cn
ms.lasthandoff: 06/08/2017


---

# <a name="manage-internet-access-using-managed-browser-policies-with-microsoft-intune"></a>使用 Microsoft Intune 的 Managed Browser 策略管理 Internet 访问

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Managed Browser 是一款可用 Web 浏览应用，可以从公共应用商店中下载它以供组织使用。 借助 Intune，可以通过 MyApps 服务进行单一登录来使用 Managed Browser 访问公司网站和 SaaS 应用，并保护 Web 数据。 此外，可以为 Managed Browser 预配置一个 URL 和域列表来限制用户可在公司上下文中导航到的网站。

由于此应用已与 Intune SDK 集成，因此也可以向其应用应用保护策略。 这些策略可能包括控制剪切、复制和粘贴的使用，阻止屏幕捕获，以及确保用户选择的内容链接仅在其他托管应用中打开。 有关详细信息，请参阅[什么是应用保护策略？](/intune/app-protection-policy)。
可以将这些设置应用于已注册 Intune 的设备及已注册其他设备管理产品的设备，还可应用于未进行托管的设备。

>[!IMPORTANT]
>Managed Browser 应用仅在设备上的其他应用已检索应用保护策略后检索和应用 Intune 应用保护策略。<br><br> 

如果用户从应用商店中安装了 Managed Browser，并且 Intune 未托管它，则可将其用作基本的 Web 浏览器，其支持通过 Microsoft MyApps 网站进行单一登录。 用户将被直接转到 MyApps 网站，在其中用户可以看到其预配的所有 SaaS 应用程序。
Intune 未托管 Managed Browser 期间，其无法访问由 Intune 托管的其他应用程序中的数据。 


可以针对以下设备类型创建 Managed Browser 策略：

-   运行 Android 4 和更高版本的设备

-   运行 iOS 8.0 及更高版本的设备

Intune Managed Browser 支持从 [Microsoft Intune 应用程序合作伙伴](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx)打开 Web 内容。

## <a name="create-a-managed-browser-app-configuration"></a>创建 Managed Browser 应用配置

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune 应用保护”。
3. 在 Intune 移动应用程序管理仪表板的“设置”边栏选项卡上，选择“应用配置”。
4. 在“应用配置”边栏选项卡上，选择“添加配置”。
5. 在“添加应用配置”边栏选项卡上，输入应用配置设置的“名称”和可选“描述”。
5. 选择“选择所需应用”，然后在“目标应用”边栏选项卡上，选择适用于 iOS 或适用于 Android（或适用于两者）的“Managed Browser”。
6. 选择“确定”，返回“添加应用配置”边栏选项卡。
7. 选择“定义配置”。 在“配置”边栏选项卡上，定义键值对来为 Managed Browser 提供配置。
请参阅本主题的后续部分，了解可以定义的不同键值对。
8. 完成后，请单击“确定”。
9. 在“添加应用配置”边栏选项卡上，选择“创建”。
10. 创建新配置后，其显示在“应用配置”边栏选项卡上。




## <a name="assign-the-configuration-settings-you-created"></a>分配已创建的配置设置

将这些设置分配到 Azure AD 用户组。 如果用户已安装 Managed Browser 应用，则你已指定的设置将管理此应用。

1. 在 Intune 移动应用程序管理仪表板的“设置”边栏选项卡上，选择“应用配置”。
2. 在应用配置列表中，选择一个想要分配的配置。
3. 在下一个边栏选项卡上，选择“用户组”。
4. 在“用户组”边栏选项卡上，选择想要将应用配置分配到的 Azure AD 组，然后选择“确定”。


## <a name="how-to-specify-allowed-and-blocked-urls-for-the-managed-browser"></a>如何为 Managed Browser 指定允许和阻止的 URL

使用创建 Managed Browser 应用配置的过程提供以下键值对：

### <a name="key"></a>Key

选择：

- 指定允许的 URL（仅允许这些 URL；不可访问任何其他网站）：**com.microsoft.intune.mam.managedbrowser.AllowListURLs**
- 指定阻止的 URL（可访问任何其他网站）：**com.microsoft.intune.mam.managedbrowser.BlockListURLs**

>[!IMPORTANT]
>不要同时指定这两个键。 如果两个键同时针对同一个用户，则将使用允许键，因为它是限制性最强的选项。
>此外，务必不要阻止重要的页面，例如你的公司网站。

### <a name="value"></a>值

键的对应值是 URL 列表。 将要允许或阻止的所有 URL 作为单个值输入，并用竖线 **|** 字符分隔。

例如： 

- **URL1|URL2|URL3**
- **http://*.contoso.com/*|https://*.bing.com/*|https://expenses.contoso.com**

请参阅本主题中的参考部分，查看更多可以使用的 URL 格式示例。


## <a name="security-and-privacy-for-the-managed-browser"></a>Managed Browser 的安全和隐私

-   在 iOS 设备上，如果用户访问的网站的证书已过期或不受信任，则无法打开该网站。

-   Managed Browser 不使用用户在设备上对内置浏览器进行的设置。 这是因为 Managed Browser 无权访问这些设置。

-   如果你在与 Managed Browser 关联的移动应用程序管理策略中配置了“访问需要简单 PIN”或“访问需要公司凭据”选项，且用户选择了“身份验证”页上的帮助链接，则他们可以浏览任何 Internet 站点，而无需考虑这些网站是否已添加到 Managed Browser 策略中的阻止列表。

-   Managed Browser 仅能在直接访问站点时阻止访问。 使用中间服务（例如翻译服务）访问站点时，该策略则无法阻止访问。

-   若要允许身份验证并确保可以访问 Intune 文档，请从允许或阻止列表设置中移除 **&#42;.microsoft.com**。 始终允许。

### <a name="turn-off-usage-data"></a>关闭用法数据
Microsoft 会自动收集有关性能和 Managed Browser 使用情况的匿名数据，以改进 Microsoft 产品和服务。 用户可通过使用设备上的“使用情况数据”设置关闭数据收集。 不具有对此数据的收集的控制。

## <a name="reference-information"></a>参考信息

### <a name="url-format-for-allowed-and-blocked-urls"></a>允许的 URL 和阻止的 URL 的格式
使用以下信息来了解有关指定允许和阻止列表中的 URL 时允许使用的格式和通配符：

-   可以根据以下允许模式列表中的规则使用通配符 (*)。

-   在将 URL 输入列表时，确保对所有 URL 添加 **“http”** 或 **“https”** 作为前缀。

-   可以在地址中指定端口号。 如果未指定端口号，将使用以下值：

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
    |http://www.contoso.com:80|匹配单个页面（使用端口号）|http://www.contoso.com:80||
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



