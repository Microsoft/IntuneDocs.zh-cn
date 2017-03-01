---
title: "如何监视设备符合性"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解如何监视设备合规性。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0790934b-48b9-435b-a8aa-e83ed5b73191
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: d59d94aafa71a9891a6746902339255ea7a9ad15
ms.lasthandoff: 02/18/2017


---
# <a name="how-to-monitor-compliance-in-intune-azure-preview"></a>如何监视 Intune Azure 预览版中的合规性

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

可以在“概述”边栏选项卡中查看“合规性配置文件”的状态摘要。
可以以交互方式单击各图表以深入查看详细信息。 如果配置了多个合规性配置文件，则还可以通过转到“策略”边栏选项卡并选择“管理”部分中的“报表”来查看每个策略的状态。  下面列出了可用于预览的报表的详细信息。

##  <a name="device-compliance"></a>设备合规性

设备合规性报表的摘要视图首先向你显示有关设备数的聚合信息，其报告为以下之一：

- **合规**：设备最近已进行了合规性评估，并已被确定为符合你指定的合规性配置文件设置。
- **不合规**：设备已进行评估并被确定为不合规。  如果在配置文件中指定了宽限期，则表明宽限期已到期，使得设备处于不合规状态。
- **宽限期**：设备已进行评估并被确定为不合规。 但是，在设备实际标记为不合规之前，宽限期仍然适用。

你可以向下钻取每个部分，以查看有关各个设备和用户的更多详细信息。

## <a name="setting-compliance"></a>设置合规性

设置合规性报表提供每个合规性设置的详细信息，例如：

- 不符合设置的设备数。
- 设置所应用到的平台。

可以向下钻取每个设置，以查看有关已启用这些设置的配置文件的详细信息以及设置的配置值。

