---
title: 适用于 iOS 设备的 Microsoft Intune Web 内容筛选器设置
titlesuffix: ''
description: 了解哪些 Microsoft Intune 设置可用于允许和阻止运行 iOS 的设备访问网站。
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c5e3dbdc339fd25289e1aed526bc03e4691c3812
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="web-content-filter-settings-for-ios-devices"></a>适用于 iOS 设备的 Web 内容筛选器设置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文介绍一些 Microsoft Intune 设置，它们可用于控制运行 iOS 的设备对浏览器 URL 的访问。

可使用两种方法配置 URL：

- **配置 URL** - 使用 Apple 的内置 Web 筛选器来查找诸如猥亵或色情语言的成人术语。 此功能将在每个网页加载时对网页进行评估，并尝试识别和阻止不合适的内容。 还可以配置不被筛选器检查的 URL，或被阻止的 URL，无需考虑筛选器的设置。

- **仅限特定网站**（仅适用于 Safari Web 浏览器）- 向 Safari 浏览器的书签添加这些 URL。 **仅**允许用户访问这些网站；不能访问其他网站。 仅在知道用户可以访问的 URL 的确切列表时使用此选项。
如果未指定任何 URL，则最终用户无法访问除 microsoft.com、microsoft.net 和 apple.com 以外的任何网站。

## <a name="get-started"></a>入门

1. 在设备功能页上，选择“Web 内容筛选器(仅限监督的设备)”。
2. 在“Web 内容筛选器”页上，从以下项中选择要配置的“筛选器类型”：
    - **未配置** - 未执行筛选。
    - **配置 URL**
    - **仅限特定网站**
3. 接下来，根据所使用的筛选器类型，执行以下过程之一：


## <a name="configure-urls"></a>配置 URL

1. 在“Web 内容筛选器”页上，根据需要选择以下设置之一：
   - **允许的 URL** - 在“允许的 URL”页上，输入要允许的 URL（跳过 Apple Web 筛选器），再选择“继续输入”。
     > [!NOTE]
     > 此处指定的 URL 不受 Apple Web 筛选器的限制。 这些 URL 不表示仅获允许的网站列表。 如果希望表示仅获允许的网站列表，请使用“仅限特定网站”。

   - **阻止的 URL** - 在“阻止的 URL”页上，输入要阻止的 URL（不考虑 Apple Web 筛选器设置），然后选择“继续输入”。
2. 完成后单击“确定” 。


## <a name="specific-websites-only"></a>仅限特定的网站

1. 在“Web 内容筛选器”窗格上，针对要允许的每个网站配置以下设置：
    - **URL** - 输入想要允许的网站的 URL，例如 http://www.contoso.com。
    - **书签路径** - 输入想要存储书签的路径，例如 **/Contoso/Business Apps**。 如不添加路径，则书签将被添加到设备上的默认书签文件夹中。
    - **标题** - 为书签输入描述性的标题。
2. 为每个网站输入完信息后，单击“添加”。
3. 完成后单击“确定” 。

> [!IMPORTANT]
> Intune 自动允许以下 URL。
> - www.microsoft.com
> - www.microsoft.net
> - www.apple.com

## <a name="finish-up"></a>完成

选择“确定”返回到“创建配置文件”窗格，然后选择“创建”。

## <a name="next-steps"></a>后续步骤

现在可将设备配置文件分配到所选择的组。 有关详细信息，请参阅[如何分配设备配置文件](device-profile-assign.md)。
