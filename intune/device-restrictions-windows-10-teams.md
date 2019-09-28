---
title: 适用于 Windows 10 协同版的 Microsoft Intune 设备限制
titleSuffix: ''
description: 了解可用于运行 Windows 10 协同版的设备的设备限制。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 20621246f76810ba7efaac3cadbdde1a0229c923
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2019
ms.locfileid: "71302340"
---
# <a name="microsoft-intune-windows-10-team-device-restriction-settings"></a>Microsoft Intune Windows 10 协同版设备限制设置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文介绍可为运行 Windows 10 协同版的设备配置的 Microsoft Intune 设备限制设置。


## <a name="apps-and-experience"></a>应用和体验

- **有人在房间内时唤醒屏幕** - 允许设备在其传感器检测到房间内有人时自动唤醒。
- 显示在欢迎屏幕上的会议信息 - 启用此选项以选择显示在“欢迎”屏幕上的“会议”磁贴下的信息  。 你可以：
  - **仅显示组织者和时间**
  - “显示组织者、时间和主题(私人会议隐藏主题)” 
- **欢迎屏幕背景图像 URL** - 启用此设置以在 Windows 10 协同版设备上的“欢迎”  屏幕上显示来自指定 URL 的自定义背景。<br>图片必须为 PNG 格式，并且 URL 必须以 **https://** 开头。

## <a name="azure-operational-insights"></a>Azure Operational Insights

- **Azure Operational Insights** - Azure Operational Insights 是 Microsoft Operations Manager 套件的一部分，对 Windows 10 协同版设备的日志文件数据进行收集、存储和分析。
若要连接到 Azure Operational insights，必须指定**工作区 ID** 和**工作区密钥**。

## <a name="maintenance"></a>维护

- **用于更新的维护时段** - 配置可以对设备进行更新的时段。 可以配置该时段的开始时间和持续小时数（1-5 小时）   。

## <a name="wireless-projection"></a>无线投影

- **用于无线投影的 PIN** - 指定是否必须先输入 PIN，然后才能使用设备的无线投影功能。
- Miracast 无线投影 - 如果想让 Windows 10 协同版设备使用 Miracast 启用的设备进行投影，则选择此选项  。
- **Miracast 无线投影频道** - 选择用于建立连接的 Miracast 频道。


## <a name="next-steps"></a>后续步骤

使用[如何配置设备限制设置](device-restrictions-configure.md)中的信息保存配置文件，并将其分配给用户和设备。
