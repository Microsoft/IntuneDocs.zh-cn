---
title: "适用于 Windows 10 协同版的 Intune 设备限制"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解 Windows 10 协同版设备的设备限制。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 677c41a2-5344-4c52-85f0-809dce3a5d5b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: afbbe6b7649e1ffc3f84ada64396d9033a2db200
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="windows-10-team-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune 中的 Windows 10 协同版设备限制设置

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

- **有人在房间内时唤醒屏幕** - 允许设备在其传感器检测到房间内有人时自动唤醒。
- **用于无线投影的 PIN** - 指定是否必须先输入 PIN，然后才能使用设备的无线投影功能。
- **Miracast 无线投影** - 如果想让 Windows 10 协同版设备使用 Miracast 启用的设备进行投影，则启用此选项。
- **显示在欢迎屏幕上的会议信息** - 启用此选项以选择显示在“欢迎”屏幕上的“会议”磁贴下的信息。 你可以：
    - **仅显示组织者和时间**
    - **显示组织者、时间和主题（私人会议的主题为隐藏状态）**
- **欢迎屏幕背景图像 URL** - 启用此设置以在 Windows 10 协同版设备上的“欢迎”屏幕上显示来自指定 URL 的自定义背景。<br>图片必须为 PNG 格式，并且 URL 必须以 **https://** 开头。
- **用于更新的维护时段** - 配置可以对设备进行更新的时段。 可以配置该时段的开始时间和持续时间（1-5 小时）。
- **Azure Operational Insights** - Azure Operational Insights 是 Microsoft Operations Manager 套件的一部分，对 Windows 10 协同版设备的日志文件数据进行收集、存储和分析。<br>若要连接到 Azure Operational insights，必须指定**工作区 ID** 和**工作区密钥**。

