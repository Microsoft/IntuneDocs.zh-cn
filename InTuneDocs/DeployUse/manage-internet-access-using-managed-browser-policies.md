---
# required metadata

title: 使用托管浏览器策略管理 Internet 访问 | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: dc946303-e09b-4d73-8bf4-87742299bc54

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用 Microsoft Intune 的托管浏览器策略管理 Internet 访问
托管浏览器是一个 Web 浏览应用程序，可以使用 Microsoft Intune 在组织中进行部署。 托管浏览器策略可配置允许列表或阻止列表，限制托管浏览器的用户可以访问的网站。

由于此应用是托管应用，因此你还可以向其应用移动应用程序管理策略，如控制使用剪切、复制和粘贴，阻止屏幕捕获，以及确保用户单击的内容链接仅在其他托管应用中打开。 有关详细信息，请参阅 [Configure and deploy mobile application management policies in the Microsoft Intune console（在 Microsoft Intune 控制台中配置和部署移动应用程序管理策略）](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)。

> [!IMPORTANT]
>如果用户从应用商店安装托管浏览器且该浏览器不由 Intune 管理，则以下行为适用：
iOS – 托管浏览器应用可以被用作基础 Web 浏览器，但一些功能将不可用，且它将不能访问其他 Intune 管理的应用中的数据。
Android – 无法使用托管浏览器应用。 如果用户自己在版本低于 iOS 9 的 iOS 设备上安装托管浏览器，那么创建的任何策略都不能对它进行管理。 若要确保浏览器由 Intune 管理，则用户必须先卸载该应用，然后你才可以将其作为托管应用部署给这些用户。

在 iOS 9 及更高版本中，如果用户自己安装托管浏览器，系统将提示他们允许托管浏览器变为由策略管理。

-   可以针对以下设备类型创建托管浏览器策略：

-   运行 Android 4 和更高版本的设备

运行 iOS 7.1 和更高版本的设备

## Intune 托管浏览器支持打开 [Microsoft Intune 应用程序合作伙伴](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)的 Web 内容

1.  创建托管浏览器策略

2.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，单击“策略” &gt; “添加策略”

    -   **配置以下 **“软件”** 策略类型之一：**

    -   **托管浏览器策略 （Android 4 和更高版本）**

    托管浏览器策略（iOS 7.1 及更高版本）

3.  有关如何创建和部署策略的详细信息，请参阅 [Manage settings and features on your devices with Microsoft Intune Policies（使用 Microsoft Intune 策略管理设备的设置和功能）](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)主题。

|使用下表来帮助你配置托管浏览器策略设置：|设置名|
    |----------------|--------------------|
    |**详细信息**|Name|
    |**输入托管浏览器策略的唯一名称，以帮助你在 Intune 控制台中识别它。**|说明|
    |**提供对托管浏览器策略的概述以及可帮助你查找策略的其他相关信息。**|启用允许列表或阻止列表，以限制托管浏览器可以打开的 URL<br /><br />选择下列选项之一：<br /><br />“仅允许托管浏览器打开下面列出的 URL”– 指定托管浏览器可以打开的 URL 列表。 “阻止托管浏览器打开下面列出的 URL”– 指定将阻止托管浏览器打开的 URL 列表。<br />**注意：**不能在相同的托管浏览器策略中同时包括允许的 URL 和阻止的 URL。|

4.  有关可以指定的 URL 格式的详细信息，请参阅本主题中的**允许的和阻止的 URL 的 URL 格式**。

完成后，请单击“保存策略”

## 新的策略将在“策略”  工作区的“配置策略”  节点处显示。
创建托管浏览器应用的部署

> [!IMPORTANT]
> 在创建托管浏览器策略后，可以创建托管浏览器应用的软件部署，并将它与所创建的托管浏览器策略相关联。 托管浏览器策略的部署方式不同于其他 Intune 策略。

这种类型的策略必须与托管浏览器软件包相关联。

部署该应用，确保在 **“移动应用管理”** 页上选择托管浏览器策略，以使策略与应用相关联。

## 有关如何部署应用的详细信息，请参阅[在 Microsoft Intune 中部署应用](deploy-apps-in-microsoft-intune.md)。

-   托管浏览器的安全和隐私

-   在 iOS 设备上，如果用户访问的网站的证书已过期或不受信任，则无法打开该网站。 托管浏览器不使用用户在设备上对内置浏览器进行的设置。

-   这是因为托管浏览器无权访问这些设置。

-   如果在与托管浏览器关联的移动应用程序管理策略中配置 **“访问需要简单 PIN”** 或 **“访问需要公司凭据”** 选项，并且用户单击身份验证页上的帮助链接，则他们可以浏览任何 Internet 站点，而无论这些网站是否已添加到托管浏览器策略中的阻止列表。 托管浏览器仅能在直接访问站点时阻止访问。

-   使用中间服务（例如翻译服务）访问站点时，该策略则无法阻止访问。

### 若要允许身份验证并确保可以访问 Intune 文档，请从允许或阻止列表设置中移除 **&#42;.microsoft.com** - 将始终允许此操作。
关闭用法数据 Microsoft 会自动收集有关性能和利用托管浏览器来改进 Microsoft 产品和服务的匿名数据，但用户可以通过使用设备上的“用法数据”设置关闭数据收集。

## 不具有对此数据的收集的控制。

### 参考信息
允许的 URL 和阻止的 URL 的格式

-   使用以下信息来了解有关指定允许和阻止列表中的 URL 时允许使用的格式和通配符。

-   可以根据下面的允许模式列表中的规则使用通配符“&#42;”。

-   在将 URL 输入列表时，确保对所有 URL 添加 **“http”** 或 **“https”** 作为前缀。 可以在地址中指定端口号。

    -   如果未指定端口号，将使用以下值：

    -   对于 http，使用端口 80

    对于 https，使用端口 443

-   不支持对端口号使用通配符，例如，**http://www.contoso.com:*;** 和 **http://www.contoso.com: /*

|使用下表了解指定 URL 时可以使用的允许模式：|URL|详细信息|匹配|
    |-------|---------------|-----------|------------------|
    |不匹配|http://www.contoso.com|匹配单个页面|www.contoso.com<br /><br />host.contoso.com<br /><br />www.contoso.com/images|
    |contoso.com/|http://contoso.com|匹配单个页面|contoso.com/<br /><br />host.contoso.com<br /><br />www.contoso.com/images|
    |www.contoso.com|http://www.contoso.com/&#42;|匹配以 www.contoso.com 开头的所有 URL<br /><br />www.contoso.com<br /><br />www.contoso.com/images|www.contoso.com/videos/tvshows<br /><br />host.contoso.com|
    |host.contoso.com/images|http://&#42;.contoso.com/&#42;|匹配 contoso.com 下的所有子域<br /><br />developer.contoso.com/resources<br /><br />news.contoso.com/images|news.contoso.com/videos|
    |contoso.host.com|http://www.contoso.com/images|匹配单个文件夹|www.contoso.com/images|
    |www.contoso.com/images/dogs|http://www.contoso.com:80|匹配单个页面（使用端口号）||
    |http://www.contoso.com:80|https://www.contoso.com|匹配单个安全页面|https://www.contoso.com|
    |http://www.contoso.com|http://www.contoso.com/images/&#42;|匹配单个文件夹和所有子文件夹<br /><br />www.contoso.com/images/dogs|www.contoso.com/images/cats|

-   www.contoso.com/videos

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

### http://www.contoso.com: /&#42;
允许和阻止列表之间的冲突的解决方式 如果向一个设备部署多个托管浏览器策略，并且出现设置冲突，则将评估模式（允许或阻止）以及 URL 列表中的冲突。

-   发生冲突时，以下行为适用：

-   如果每个策略中的模式相同但 URL 列表不同，则不会在设备上强制执行 URL。

-   如果每个策略中的模式不同但 URL 列表相同，则不会在设备上强制执行 URL。 如果设备是首次接收托管浏览器策略而两个策略发生冲突，则不会在设备上强制执行 URL。

-   使用 **“策略”** 工作区的 **“策略冲突”** 节点查看这些冲突。 如果设备已接收托管浏览器策略而部署的第二个策略具有冲突的设置，则将在设备上保留原始设置。


<!--HONumber=May16_HO2-->


