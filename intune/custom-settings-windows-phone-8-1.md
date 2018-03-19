---
title: "适用于运行 Windows Phone 8.1 的设备的 Microsoft Intune 自定义设置"
titleSuffix: 
description: "了解可以在 Windows Phone 8.1 自定义配置文件中使用的设置。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f45b2dd9cab0ccfd912d1f1348d90264bf8906b8
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-windows-phone-81"></a>适用于运行 Windows Phone 8.1 的设备的 Microsoft Intune 自定义设备设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用 Microsoft Intune 的 Windows Phone 8.1 **自定义**配置文件来分配可用于控制 Windows Phone 8.1 设备功能的 OMA-URI 设置。 这些设置是许多移动设备制造商用来控制设备功能的标准设置。

此功能的目的是允许用户分配不能使用其他 Intune 策略配置的设置。

## <a name="custom-policy-settings-for-windows-phone-81-devices"></a>适用于 Windows Phone 8.1 设备的自定义策略设置

1. 按照[如何在 Microsoft Intune 中配置自定义设备设置](custom-settings-configure.md)中的说明进行操作。
2. 在“自定义 OMA-URI 设置”窗格中，选择“添加”以添加一个或多个 OMA-URI 设置。
3. 在“添加行”窗格上，为每个设置配置以下值：
    - **名称** - 输入 OMA-URI 设置的唯一名称，以帮助你在设置列表中识别它。
    - **说明** - 提供对设置进行概述的说明以及帮助你找到该设置的其他相关信息。
    - **OMA-URI** 指定需为其提供设置的 OMA-URI。
    - **数据类型** - 选择将在其中指定此 OMA-URI 设置的数据类型。 从“字符串”、“字符串 (XML)”、“日期和时间”、“整数”、“浮点”、“布尔值”或“Base64”中进行选择。
    - **值** - 输入要与已输入的 OMA-URI 关联的值或文件。

4. 完成后，单击“确定”，根据需要继续添加其他设置。
