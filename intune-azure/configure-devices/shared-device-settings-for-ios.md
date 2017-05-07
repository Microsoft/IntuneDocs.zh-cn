---
title: "iOS 的 Intune 共享设备配置设置"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解在 iOS 设备锁定屏幕上显示信息可以使用的 Intune 设置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 4/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f122e4ee-90e7-4b42-b801-8c1c7c0a5bf7
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: 2bc107054f438d5ed72de87dec85900f871c0acc
ms.lasthandoff: 04/19/2017


---

# <a name="shared-device-configuration-settings-to-display-messages-on-the-ios-device-lock-screen"></a>用于在 iOS 设备锁定屏幕上显示消息的共享设备配置设置

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

共享设备配置设置使你能够指定在登录窗口和锁定屏幕上显示的可选文本（即“如果丢失，返回到”消息和资产标记信息）。 

>[!IMPORTANT]
> 此功能支持运行 iOS 9.3 和更高版本的监督设备。

1. 在“设备功能”边栏选项卡上，选择“共享设备配置（仅限监督设备）”。
2. 在“共享设备配置（仅限监督设备）”边栏选项卡上，配置以下信息：
    - **资产标记信息** - 输入有关设备的资产标记的信息。 例如：“由 Contoso 公司拥有”。所输入的信息将应用于分配此配置文件的所有设备。
    - **锁定屏幕脚注** - 输入注释，该注释可能在设备丢失或被盗时帮助将其找回。 例如：“如果找到，请呼叫“号码””。
3. 完成后，选择“确定”，直到返回到“创建配置文件”边栏选项卡，然后选择“创建”。 

