---
title: "适用于 iOS 设备的 Intune Web 内容筛选器设置"
titlesuffix: Azure portal
description: "了解可用于允许和阻止从 iOS 设备访问网站的设置。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 1/18/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f46ddd58434be750bac74fb99b526d64fccdb179
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="web-content-filter-settings-for-ios-devices"></a>适用于 iOS 设备的 Web 内容筛选器设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用这些设置配置 iOS 设备上的 Web 浏览器的最终用户可以或不能访问的 URL。 可以使用两种方法配置 URL：

- **配置 URL** - 使用 Apple 的内置 Web 筛选器来查找诸如猥亵或色情语言的成人术语。 此功能将在每个网页加载时对网页进行评估，并尝试识别和阻止不合适的内容。 还可以配置不被筛选器检查的 URL，或被阻止的 URL，无需考虑筛选器的设置。

- **仅限特定网站**（仅适用于 Safari Web 浏览器）- 向 Safari 浏览器的书签添加这些 URL。 **仅**允许用户访问这些网站；不能访问其他网站。 仅在知道用户可以访问的 URL 的确切列表时使用此选项。
如果未指定任何 URL，则最终用户无法访问除 microsoft.com、microsoft.net 和 apple.com 以外的任何网站。



## <a name="get-started"></a>入门

1. 在设备功能边栏选项卡上，选择“Web 内容筛选器（仅限监督的设备）”。
2. 在“Web 内容筛选器”边栏选项卡上，从以下类型中选择想要进行配置的“筛选器类型”：
    - **未配置** - 未执行筛选。
    - **配置 URL**
    - **仅限特定网站**
3. 接下来，根据所使用的筛选器类型，执行以下过程之一：


## <a name="configure-urls"></a>配置 URL

1. 在“Web 内容筛选器”边栏选项卡上，根据需要选择以下设置之一：
   - **允许的 URL** - 在“允许的 URL”边栏选项卡上，输入想要允许的 URL（跳过 Apple Web 筛选器），并在每个 URL 后选择输入。
     > [!NOTE]
     > 此处指定的 URL 不受 Apple Web 筛选器的限制。 这些 URL 不表示仅获允许的网站列表。 如果希望表示仅获允许的网站列表，请使用“仅限特定网站”。

   - **阻止的 URL** - 在“阻止的 URL”边栏选项卡上，输入想要阻止的 URL（无需考虑 Apple Web 筛选器设置），并在每个 URL 后选择输入。
2. 完成后单击“确定” 。


## <a name="specific-websites-only"></a>仅限特定的网站

1. 在“Web 内容筛选器”边栏选项卡上，对想要允许的每个网站，配置以下设置：
    - **URL** - 输入想要允许的网站的 URL，例如 **http://www.contoso.com**。
    - **书签路径** - 输入想要存储书签的路径，例如 **/Contoso/Business Apps**。 如不添加路径，则书签将被添加到设备上的默认书签文件夹中。
    - **标题** - 为书签输入描述性的标题。
2. 为每个网站输入完信息后，单击“添加”。
3. 完成后单击“确定” 。

>[!IMPORTANT] 
> Intune 自动允许以下 URL。
> - www.microsoft.com
> - www.microsoft.net
> - www.apple.com

## <a name="finish-up"></a>完成

选择“确定”返回到“创建配置文件”边栏选项卡，然后选择“创建”。

## <a name="next-steps"></a>后续步骤

现在可将设备配置文件分配到所选择的组。 有关详细信息，请参阅[如何分配设备配置文件](device-profile-assign.md)。
