---
title: 如何配置公司门户应用
titleSuffix: Microsoft Intune
description: 了解如何将特定于公司的品牌应用到 Intune 公司门户应用。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bd388131445715a4037cc0480c194d338212dbb0
ms.sourcegitcommit: e814cfbbefe818be3254ef6f859a7bf5f5b99123
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2018
ms.locfileid: "43329967"
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>如何配置 Microsoft Intune 公司门户应用

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

在 Microsoft Intune 公司门户中，用户可以访问公司数据和执行常见任务，比如注册设备、安装应用，以及查找信息以从 IT 部门获得帮助。        

> [!Tip]        
> 当你自定义公司门户时，配置会同时应用于公司门户网站和公司门户应用。       

自定义公司门户有助于为最终用户提供熟悉且有帮助的体验。 为此，请从“客户端应用”工作负荷中，选择“设置” > “公司门户品牌”，然后配置所需设置。  

> [!Note]       
> 当用户启动获取问题的帮助的工作流时，Windows 10 公司门户现在将直接向 Microsoft 发送应用日志。 这样一来，可以更为轻松地排除和解决向 Microsoft 提出的问题。  

## <a name="company-information-and-privacy-statement"></a>公司信息和隐私声明        
公司名称显示为公司门户的标题。 当用户单击隐私链接时，将显示隐私声明。

标有星号 (*) 的字段是必填字段。       


| 字段名称 | 最大长度 | 更多信息 |
|---|---|---|
|**公司名称**| 40 | 此名称显示为公司门户的标题，并且以文本形式显示在整个 Intune 用户体验中。 |
| **隐私声明 URL** |     79     | 你可以指定自己的公司隐私声明，当用户从公司门户中单击隐私链接时，该隐私声明将出现。 必须以 `<https://www.contoso.com>` 格式输入有效的 URL。 |

## <a name="support-information"></a>支持信息      
输入公司的支持信息，为员工提供 Intune 相关问题的联系人。       

|字段名称|最大长度|更多信息|
|---|---|---|
|**联系人姓名** | 40 | 此名称显示在“联系 IT”页上。 |
|**电话号码** | 20 | 此联系人号码会显示在“联系 IT”页上，以便员工与你联系以获得支持。 |
|**电子邮件地址**| 40 | 此联系人地址显示在“联系 IT”页上。 必须以 `alias@domainname.com` 格式输入有效的电子邮件地址。 |
|**网站名称**| 40 | 此名称是为支持网站的 URL 显示的友好名称。 如果指定支持网站 URL 而不指定友好名称，则公司门户中的“联系 IT 部门”页上将显示“转到 IT 网站”。 |
|**网站 URL**| 150 | 如果你拥有希望用户可以使用的支持网站，请在此处指定 URL。 该 URL 必须采用 `https://www.contoso.com` 格式。 如果不指定 URL，则公司门户中的“联系 IT”页上将不会显示支持网站的任何内容。 |
| **其他信息**| 120 | 显示在“联系 IT”页上。 |


## <a name="company-branding-customization"></a>公司品牌自定义       
你可以使用公司徽标、公司名称、主题颜色和背景来自定义公司门户。     

### <a name="theme-color"></a>主题颜色
向公司门户应用主题颜色。 选择一种标准颜色，或输入自定义颜色的六位十六进制代码。

|字段名称|更多信息|
|---|---|
|**颜色类型**| 选择要应用于公司门户的主题颜色。 可以从标准颜色中选择，也可以输入特定的十六进制代码。 |
|**选择颜色**或**十六进制颜色代码**| 选择要应用于公司门户的主题颜色。 可以从标准颜色中选择，也可以输入特定的十六进制代码。 这些选项是基于选择的“颜色类型”提供的。  |

### <a name="company-logo"></a>公司徽标
上传公司徽标，在整个 Intune 用户体验中显示它。

|字段名称|更多信息|
|---|---|
|**显示公司徽标**|如果启用此选项，你可以上传公司徽标以显示在公司门户中。 你可以上传两个徽标：一个在公司门户背景为白色时显示的徽标，以及一个在公司门户背景使用所选主题颜色时使用的徽标。 |
|**上传要在主题颜色背景上使用的徽标**| 如果选择显示公司徽标，则此选项可用。 徽标必须是 .png 或 .jpg 文件类型，最大分辨率为 400 x 400 像素，大小等于或小于 750 KB。 |
|**上传要在浅色背景上使用的徽标**| 如果选择显示公司徽标，则此选项可用。 徽标必须是 .png 或 .jpg 文件类型，最大分辨率为 400 x 400 像素，大小等于或小于 750 KB。 |
|**在徽标旁显示公司名称**| 选择此选项，以在上传的徽标旁显示输入的公司名称。 |

保存更改后，可以选择边栏选项卡顶部的“预览 Intune Web 门户中的设置”，以查看配置的外观。
