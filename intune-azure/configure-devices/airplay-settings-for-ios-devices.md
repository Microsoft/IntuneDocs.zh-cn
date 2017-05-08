---
title: "适用于 iOS 设备的 Intune AirPlay 设置"
titleSuffix: Intune Azure preview
description: "了解如何使用 Intune 来帮助 iOS 设备自动连接到与 AirPlay 兼容的设备。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 712a79fb-14ef-4f6b-aba5-1dfca900afd2
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: f1f7aa6a0b441b51f20d104c4353a1542a9e01ad
ms.contentlocale: zh-cn
ms.lasthandoff: 04/19/2017


---

# <a name="intune-airplay-settings-for-ios-devices"></a>适用于 iOS 设备的 Intune AirPlay 设置

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

使用这些设置帮助你所管理的 iOS 设备连接到你的网络上与 AirPlay 兼容的设备（如 Apple TV 设备）。
借助此功能，可以：

- **配置设备和密码列表** - 使用 AirPlay 设备的名称和密码配置设备，以使其在连接范围内自动连接。 如果提供了密码，则最终用户无需在进行连接时提供密码。
- **配置允许的目标** - 配置 AirPlay 设备的列表（按设备 ID）。 最终用户将仅能查看并连接到你所列出的设备（仅限监督的设备）。

## <a name="get-started"></a>入门

1. 在“设备功能”边栏选项卡上，选择“AirPlay”。
2. 在“AirPlay”边栏选项卡上，选择以下一个或两个操作：

## <a name="configure-a-device-and-password-list"></a>配置设备和密码列表

1. 在“密码”边栏选项卡上，输入 AirPlay 设备的“设备名称”和“密码”，例如“Contoso Apple TV”。
2. 输入设备详细信息后，单击“添加”。 该设备将出现在“设备名称”列表中。
3. 继续添加设备。 完成后，请选择“确定”。


## <a name="configure-allowed-destinations"></a>配置允许的目标

1. 在 *“允许的目标”（仅限监督的设备）边栏选项卡中，输入 Airplay 设备的“设备 ID”，例如 52:46:CD:51:83:4C。
2. 输入设备 ID 后，单击“添加”。 该 ID 将出现在“设备 ID”列表中。
3. 继续添加设备。 完成后，请选择“确定”。

还可以导入设备和密码，并允许来自逗号分隔的值 (csv) 文件的目标。



