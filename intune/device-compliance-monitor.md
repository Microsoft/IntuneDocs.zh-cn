---
title: 监视设备符合性
titlesuffix: Microsoft Intune
description: 了解如何监视设备符合性。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0790934b-48b9-435b-a8aa-e83ed5b73191
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0fec00b18bd63986a537549715af84cd44539fbb
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="monitor-device-compliance-in-intune"></a>在 Intune 中监视设备符合性

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

可以在“概述”边栏选项卡中查看“合规性配置文件”的状态摘要。
可以以交互方式单击各图表以深入查看详细信息。 如果配置了多个符合性配置文件，则可以在“管理” > “报告”下的策略边栏选项卡上查看策略状态。

##  <a name="device-compliance"></a>设备符合性

设备符合性报告的摘要视图列出了有关设备数的聚合信息，其报告为以下状态之一：

- **符合**：设备最近进行了评估，并符合指定的符合性配置文件设置。
- **不合规**：设备已进行评估并被确定为不合规。  如果在配置文件中指定了宽限期，则表明宽限期已到期，使得设备处于不合规状态。
- **宽限期**：设备已进行评估并被确定为不合规。 但是，在设备标记为不合规之前，宽限期仍然适用。

你可以向下钻取每个部分，以查看有关各个设备和用户的更多详细信息。

## <a name="setting-compliance"></a>设置合规性

设置符合性报告提供每个符合性设置的详细信息，例如：

- 不符合设置的设备数。
- 设置所应用到的平台。

可以向下钻取每个设置，以查看有关已启用这些设置的配置文件的详细信息以及设置的值。
