---
title: 如何配置公司门户应用
titleSuffix: Microsoft Intune
description: 了解如何将特定于公司的品牌应用到 Intune 公司门户应用。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5a7213608a8147178633ccd8129ab40eef5d4a15
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>如何配置 Microsoft Intune 公司门户应用

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

在 Microsoft Intune 公司门户中，用户可以访问公司数据和执行常见任务，比如注册设备、安装应用，以及查找信息以从 IT 部门获得帮助。        

> [!Tip]        
> 当你自定义公司门户时，配置会同时应用于公司门户网站和公司门户应用。       

自定义公司门户有助于为最终用户提供熟悉且有帮助的体验。 为此，请从“移动应用”工作负荷中，选择“设置” > “公司门户品牌”，然后配置所需设置。      

## <a name="company-contact-information-and-privacy-statement"></a>公司联系人信息和隐私声明        
公司名称显示为公司门户的标题。 联系人信息和详细信息将在公司门户的“联系 IT 部门”屏幕中向用户显示。 当用户单击隐私链接时，将显示隐私声明。

标有星号 (*) 的字段是必填字段。       


| 字段名称 | 最大长度 | 更多信息 |
|---|---|---|
|**公司名称**| 40 | 此名称显示为公司门户的标题。 |
|**IT 部门联系人姓名** | 40 | 此名称显示在“联系 IT”页上。 |
|**IT 部门的电话号码** | 20 | 此联系人号码显示在“联系 IT”页上。 |
|**IT 部门的电子邮件地址**| 40 | 此联系人地址显示在“联系 IT”页上。 必须以 `alias@domainname.com` 格式输入有效的电子邮件地址。 |
| **其他信息**|    120     | 显示在“联系 IT”页上。 |
| **公司隐私声明 URL** |     79     | 你可以指定自己的公司隐私声明，当用户从公司门户中单击隐私链接时，该隐私声明将出现。 必须以 `<https://www.contoso.com>` 格式输入有效的 URL。 |

## <a name="support-contacts"></a>支持联系人     
在公司门户向用户显示支持网站，以使他们能够访问在线支持。        

|字段名称|最大长度|更多信息|
|---|---|---|
|**支持网站 URL**|150|如果你拥有希望用户可以使用的支持网站，请在此处指定 URL。 该 URL 必须采用 https://www.contoso.com格式。如果不指定 URL，则公司门户中的“联系 IT”页上将不会显示支持网站的任何内容。|
|**支持网站名称**|40|此名称是为支持网站的 URL 显示的友好名称。 如果指定支持网站 URL 而不指定友好名称，则公司门户中的“联系 IT 部门”页上将显示“转到 IT 网站”。

## <a name="company-branding-customization"></a>公司品牌自定义       
你可以使用公司徽标、公司名称、主题颜色和背景来自定义公司门户。     

|字段名称|更多信息|
|---|---|
|**主题颜色**|选择要应用于公司门户的主题颜色。 可以从颜色选取器中选择，也可以输入特定的十六进制代码。|
|**显示公司徽标**|如果启用此选项，你可以上传公司徽标以显示在公司门户中。 你可以上传两个徽标：一个在公司门户背景为白色时显示的徽标，以及一个在公司门户背景使用所选主题颜色时使用的徽标。 每个徽标必须是 .png 或 .jpg 文件类型，最大分辨率为 400 x 100 像素，大小等于或小于 750 KB。<br>还可以显示在已上传徽标旁边输入的公司名称。|

保存所做的更改后，可以选择“预览 Intune Web 门户中的设置”，查看配置的外观。
