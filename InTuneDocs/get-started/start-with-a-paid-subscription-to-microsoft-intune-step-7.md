---
title: "自定义公司门户 | Microsoft Docs"
description: "Intune 公司门户允许用户执行常见任务，如注册设备、安装应用和查找 IT 部门信息。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/13/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: eb4a9f01-f857-4563-ab6f-5d0d7dfa659d
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 77f1af3a07e5a5758227c81010ce853906803b08
ms.openlocfilehash: f103a919d0708c2925cb6af4cf7231ed05029e46


---

# <a name="customize-the-company-portal"></a>自定义公司门户

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

在 Intune 公司门户中，用户可以访问公司数据和执行常见任务，比如注册设备、安装应用，以及查找信息以从 IT 部门获得帮助。

Intune 公司门户向用户提供对公司数据和应用的访问权限。 公司门户有两种形式：

-   **公司门户应用**：在使用 Intune.管理的设备上可用的一个应用程序。 深入了解适用于 [Android](/Intune/EndUser/using-your-android-device-with-intune)、[iOS](/Intune/EndUser/using-your-iOS-or-macOS-device-with-intune) 和 [Windows](/Intune/EndUser/using-your-windows-device-with-intune)的公司门户应用。


- **公司门户网站**：一个可让最终用户通过公司门户应用完成大部分可执行任务的网站。 Intune 公司门户 URL 为 [http://portal.manage.microsoft.com](http://portal.manage.microsoft.com)。 有关此网站的详细信息，请参阅[使用 Intune 公司门户网站](/Intune/EndUser/using-the-intune-company-portal-website)。

> [!TIP]
> 当你自定义公司门户时，配置会同时应用于公司门户网站和公司门户应用。

在公司门户中用户可执行的一些任务有：

-   注册设备
-   查看其设备的状态
-   重置设备
-   重置密码
-   远程锁定设备
-   下载组织部署的软件
-   联系 IT 部门以获得支持

## <a name="customize-company-portal-settings"></a>自定义公司门户设置
自定义公司门户有助于为最终用户提供熟悉且有帮助的体验。 以租户或服务管理员的身份登录到 [Microsoft Intune 管理控制台](https://manage.microsoft.com)，选择“管理员”&gt;“公司门户”，然后配置公司门户设置。

![admin-console-admin-workspace-comp-portal-settings](./media/companyportal.png)

## <a name="company-contact-information-and-privacy-statement"></a>公司联系人信息和隐私声明
公司名称显示为公司门户的标题。 联系人信息和详细信息将在公司门户的“联系 IT 部门”屏幕中向用户显示。 当用户单击隐私链接时，将显示隐私声明。

|字段名称|最大长度|更多信息|
    |----------|------------------------|----------------|
    |公司名称|40|此名称显示为公司门户的标题。|
    |IT 部门联系人姓名|40|此名称显示在“联系 IT”页上。|
    |IT 部门的电话号码|20|此联系人号码显示在“联系 IT”页上。|
    |IT 部门的电子邮件地址|40|此联系人地址显示在“联系 IT”页上。 必须以 **alias@domainname.com** 格式输入有效的电子邮件地址。|
    |其他信息|120|显示在“联系 IT”页上。|
    |公司隐私声明 URL|79|你可以指定自己的公司隐私声明，当用户从公司门户中单击隐私链接时，该隐私声明将出现。 必须以 https://www.contoso.com 格式输入有效的 URL。|

## <a name="support-contacts"></a>支持联系人
在公司门户向用户显示支持网站，以使他们能够访问在线支持。

|字段名称|最大长度|更多信息|
    |----------|------------------------|----------------|
    |支持网站 URL|150|如果你拥有希望用户可以使用的支持网站，请在此处指定 URL。 该 URL 必须采用 https://www.contoso.com 格式。 如果不指定 URL，则公司门户中的“联系 IT”页上将不会显示支持网站的任何内容。|
    |网站名称|40|此名称是为支持网站的 URL 显示的友好名称。 如果指定支持网站 URL 而不指定友好名称，则公司门户中的“联系 IT”页上将显示“转到 IT 网站”。|

## <a name="company-branding-customization"></a>公司品牌自定义
你可以使用公司徽标、公司名称、主题颜色和背景来自定义公司门户。

|字段名称|更多信息|
    |----------|----------------|
    |主题颜色|选择要应用于公司门户的主题颜色。|
    |包括公司徽标|如果启用此选项，你可以上传公司徽标以显示在公司门户中。 你可以上传两个徽标：一个在公司门户背景为白色时显示的徽标，以及一个在公司门户背景使用所选主题颜色时使用的徽标。 每个徽标必须是 .png 或 .jpg 文件类型，最大分辨率为 400 x 100 像素，大小等于或小于 750 KB。|
    |为 [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)] 公司门户应用选择背景|此设置只影响 [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)] 公司门户应用的背景。|


保存更改之后，你可以使用管理控制台的“公司门户”页面底部提供的链接来查看公司门户网站。 无法更改这些链接。 当用户登录时，这些链接将在公司门户中显示你的订阅。

>[!div class="step-by-step"]

>[&larr;**创建策略和应用**](.\start-with-a-paid-subscription-to-microsoft-intune-step-6.md)       [**注册设备**&rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md)  



<!--HONumber=Jan17_HO1-->


