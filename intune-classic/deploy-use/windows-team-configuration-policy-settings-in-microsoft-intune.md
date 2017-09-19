---
title: "Windows 协同版配置策略设置"
description: "使用 Microsoft Intune **Windows 10 协同版常规配置策略**可为已注册的 Windows 10 协同版设备（如 Microsoft Surface Hub）配置设置。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38194ef3-e26e-4682-958d-14b395fccba1
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d8d0ec02fccd7aff391d794f4db4c5c2db03c4dd
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2017
---
# <a name="windows-team-configuration-policy-settings-in-microsoft-intune"></a>Microsoft Intune 中的 Windows 协同版配置策略设置

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

使用 Microsoft Intune **Windows 10 协同版常规配置策略**可为已注册的 Windows 10 协同版设备（如 Microsoft Surface Hub）配置设置。

|设置名|详细信息|
|----------------|-----------|
|**房间内有人时允许屏幕自动唤醒**|允许设备在其传感器检测到房间内有人时自动唤醒。|
|**无线投影需要 PIN**|指定是否必须先输入 PIN，然后才能使用设备的无线投影功能。|
|**设置维护时段以进行设备更新**|配置可以对设备进行更新的时段。 可以配置该时段的开始时间和持续时间（1-5 小时）。|
|**启用 Azure Operational Insights**|Azure Operational Insights 是 Microsoft Operations Manager 套件的一部分，对 Windows 10 协同版设备的日志文件数据进行收集、存储和分析。<br /><br />若要连接到 Azure Operational insights，必须指定**工作区 ID** 和**工作区密钥**。|
|**启用 Miracast 无线投影**|如果想让 Windows 10 协同版设备使用 Miracast 启用的设备进行投影，则启用此选项。<br /><br />如果启用了此选项，请从“选择 Miracast 频道”中选择用于投影内容的 Miracast 频道。|
|**选择“欢迎”屏幕上显示的会议信息**|如果启用了此选项，你可以选择显示在“欢迎”屏幕上的“会议”标题下的信息。 你可以：<br /><br />-   “仅显示组织者和时间”<br />-   “显示组织者、时间和主题(私人会议隐藏主题)”|
|**锁屏背景图像 URL**|启用此设置以在 Windows 10 Team 设备上的“欢迎”屏幕上显示来自指定 URL 的自定义背景。<br /><br />图片必须为 PNG 格式，并且 URL 必须以 **https://** 开头。|


### <a name="see-also"></a>另请参阅
[使用 Microsoft Intune 策略管理设备上的设置和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

