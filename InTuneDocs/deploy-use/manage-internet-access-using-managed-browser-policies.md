---
title: "使用 Managed Browser 管理 Web 访问 | Microsoft Docs"
description: "部署托管浏览器应用程序以限制 Web 浏览和传输到其他应用的 Web 数据传输。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc946303-e09b-4d73-8bf4-87742299bc54
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e7d1760a10e63233fe7cc7f6fd57a68c5283647c
ms.openlocfilehash: 3982f05e4c81c26d2eb8bdab3a266597d6aab4df
ms.lasthandoff: 12/30/2016


---

# <a name="manage-internet-access-using-managed-browser-policies-with-microsoft-intune"></a>使用 Microsoft Intune 的托管浏览器策略管理 Internet 访问

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

托管浏览器是一个 Web 浏览应用程序，可以使用 Microsoft Intune 在组织中进行部署。 托管浏览器策略可配置允许列表或阻止列表，限制托管浏览器的用户可以访问的网站。

因为该应用为托管应用，因此你还可以将移动应用程序管理策略应用到该应用中。 这些策略可能包括控制剪切、复制和粘贴的使用，阻止屏幕捕获，以及确保用户选择的内容链接仅在其他托管应用中打开。 有关详细信息，请参阅[在 Microsoft Intune 控制台中配置和部署移动应用程序管理策略](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)。

> [!IMPORTANT]
>如果用户从应用商店安装托管浏览器且该浏览器不由 Intune 管理，则以下行为适用：<br /><br />
iOS – 托管浏览器应用可以被用作基础 Web 浏览器，但一些功能将不可用，且它将不能访问其他 Intune 管理的应用中的数据。<br />
Android – 无法使用托管浏览器应用。<br /><br />
如果用户自己在版本早于 iOS 9 的 iOS 设备上安装托管浏览器，那么你创建的任何策略都不能对该浏览器进行管理。 若要确保浏览器由 Intune 管理，则用户必须先卸载该应用，然后你才能将其作为托管应用部署给这些用户。 在 iOS 9 及更高版本中，如果用户自己安装托管浏览器，系统将提示他们允许托管浏览器由策略管理。

可以针对以下设备类型创建托管浏览器策略：

-   运行 Android 4 和更高版本的设备

-   运行 iOS 8.0 及更高版本的设备

Intune 托管浏览器支持从 [Microsoft Intune 应用程序合作伙伴](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)打开 Web 内容。

## <a name="create-a-managed-browser-policy"></a>创建托管浏览器策略

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，选择“策略”&gt;“添加策略”。

2.  配置以下 **“软件”** 策略类型之一：

    -   **Managed Browser（Android 4 和更高版本）**

    -   **Managed Browser（iOS 8.0 及更高版）**

    有关如何创建和部署策略的详细信息，请参阅 [Manage settings and features on your devices with Microsoft Intune Policies（使用 Microsoft Intune 策略管理设备的设置和功能）](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)主题。

3.  使用以下内容来帮助你配置托管浏览器策略设置：

    - **名称**。 输入托管浏览器策略的唯一名称，以帮助你在 Intune 控制台中识别它。
    - **说明**。 提供对托管浏览器策略的概述以及可帮助你查找策略的其他相关信息。
    - “启用允许列表或阻止列表，以限制托管浏览器可以打开的 URL”。 选择下列选项之一：
        - “允许托管的浏览器仅打开下面列出的 URL”。 指定托管浏览器可以打开的 URL 列表。
        - “阻止托管浏览器打开下面列出的 URL”。 指定将阻止托管浏览器打开的 URL 列表。
**注意：**不能在相同的托管浏览器策略中同时包括允许的 URL 和阻止的 URL。
有关可以指定的 URL 格式的详细信息，请参阅本主题中的**允许的和阻止的 URL 的 URL 格式**。

4.  完成后，请选择“保存策略”。

新的策略将在“**策略**”工作区的“**配置策略**”节点处显示。

## <a name="create-a-deployment-for-the-managed-browser-app"></a>创建托管浏览器应用的部署
在创建托管浏览器策略后，可以创建托管浏览器应用的软件部署，并将它与所创建的托管浏览器策略相关联。

> [!IMPORTANT]
> 托管浏览器策略的部署方式不同于其他 Intune 策略。 这种类型的策略必须与托管浏览器软件包相关联。

部署该应用，确保在 **“移动应用管理”** 页上选择托管浏览器策略，以使策略与应用相关联。

有关如何部署应用的详细信息，请参阅[在 Microsoft Intune 中部署应用](deploy-apps-in-microsoft-intune.md)。

## <a name="security-and-privacy-for-the-managed-browser"></a>托管浏览器的安全和隐私

-   在 iOS 设备上，如果用户访问的网站的证书已过期或不受信任，则无法打开该网站。

-   托管浏览器不使用用户在设备上对内置浏览器进行的设置。 这是因为托管浏览器无权访问这些设置。

-   如果你在与托管浏览器关联的移动应用程序管理策略中配置了“访问需要简单 PIN”或“访问需要公司凭据”选项，且用户选择了“身份验证”页上的帮助链接，则他们可以浏览所有 Internet 站点，而无需考虑这些网站是否已添加到托管浏览器策略中的阻止列表中。

-   托管浏览器仅能在直接访问站点时阻止访问。 使用中间服务（例如翻译服务）访问站点时，该策略则无法阻止访问。

-   若要允许身份验证并确保可以访问 Intune 文档，请从允许或阻止列表设置中移除 ***.microsoft.com**。 始终允许。

### <a name="turn-off-usage-data"></a>关闭用法数据
Microsoft 会自动收集有关性能和托管浏览器使用情况的匿名数据以改进 Microsoft 产品和服务。 用户可通过使用设备上的“使用情况数据”设置关闭数据收集。 不具有对此数据的收集的控制。

## <a name="reference-information"></a>参考信息

### <a name="url-format-for-allowed-and-blocked-urls"></a>允许的 URL 和阻止的 URL 的格式
使用以下信息来了解有关指定允许和阻止列表中的 URL 时允许使用的格式和通配符：

-   可以根据以下允许模式列表中的规则使用通配符 (*)。

-   在将 URL 输入列表时，确保对所有 URL 添加 **“http”** 或 **“https”** 作为前缀。

-   可以在地址中指定端口号。 如果未指定端口号，将使用以下值：

    -   对于 http，使用端口 80

    -   对于 https，使用端口 443

    不支持对端口号使用通配符。 例如，**http&colon;//www&period;contoso&period;com:*;**和**http&colon;//www&period;contoso&period;com: /*;** 不受支持。

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

### <a name="how-conflicts-between-the-allow-and-block-list-are-resolved"></a>允许和阻止列表之间的冲突的解决方式
如果向一个设备部署多个托管浏览器策略，并且出现设置冲突，则将评估模式（允许或阻止）以及 URL 列表中的冲突。 发生冲突时，以下行为适用：

-   如果每个策略中的模式相同但 URL 列表不同，则不会在设备上强制执行 URL。

-   如果每个策略中的模式不同但 URL 列表相同，则不会在设备上强制执行 URL。

-   如果设备是首次接收托管浏览器策略而两个策略发生冲突，则不会在设备上强制执行 URL。 使用 **“策略”** 工作区的 **“策略冲突”** 节点查看这些冲突。

-   如果设备已接收托管浏览器策略而部署的第二个策略具有冲突的设置，则将在设备上保留原始设置。 使用 **“策略”** 工作区的 **“策略冲突”** 节点查看这些冲突。

