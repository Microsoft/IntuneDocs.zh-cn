---
title: 适用于 iOS 设备的 Intune AirPlay 设置
titlesuffix: Microsoft Intune
description: 了解如何使用 Microsoft Intune 来帮助 iOS 设备自动连接到与 AirPlay 兼容的设备。
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 712a79fb-14ef-4f6b-aba5-1dfca900afd2
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5f941d6c6d3e1aec9e53b97ad0700d3ad3070d56
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2018
---
# <a name="intune-airplay-settings-for-ios-devices"></a>适用于 iOS 设备的 Intune AirPlay 设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用这些设置帮助你所管理的 iOS 设备连接到网络上与 AirPlay 兼容的设备（如 Apple TV 设备）。
借助此功能，可以：

- **配置设备和密码列表** - 使用户自动连接到处于范围内的 AirPlay 设备。 为他们配置 AirPlay 设备的名称和密码，这样他们在进行连接时则无需提供这些内容。
- **配置允许的目标** - 配置 AirPlay 设备的列表（按设备 ID）。 最终用户仅能查看并连接到你所列出的设备（仅限监督的设备）。

## <a name="get-started"></a>入门

1. 从 [Azure 门户中的 Intune](https://portal.azure.com)，导航到[设备配置区域中的“设备功能”](device-features-configure.md)。 
1. 在“设备功能”窗格上，选择“AirPlay”。
2. 在“AirPlay”窗格上，选择以下一个或两个操作：

## <a name="configure-a-device-and-password-list"></a>配置设备和密码列表

1. 在“密码”窗格上，输入 AirPlay 设备的“设备名称”和“密码”，例如“Contoso Apple TV”。
2. 输入设备详细信息后，单击“添加”。 该设备将出现在“设备名称”列表中。
3. 继续添加设备。 完成后，请选择“确定”。


## <a name="configure-allowed-destinations"></a>配置允许的目标

1. 在“允许的目标”（仅限监督的设备）窗格中，输入 Airplay 设备的“设备 ID”，例如 52:46:CD:51:83:4C。
2. 输入设备 ID 后，单击“添加”。 该 ID 将出现在“设备 ID”列表中。
3. 继续添加设备。 完成后，请选择“确定”。

还可以从逗号分隔值 (csv) 文件中导入设备、密码和允许的目标。


## <a name="next-steps"></a>后续步骤

现在可将设备配置文件分配到所选择的组。 有关详细信息，请参阅[如何分配设备配置文件](device-profile-assign.md)。

