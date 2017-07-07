---
title: "使用 Intune 定位丢失的 iOS 设备"
titleSuffix: Intune on Azure
description: "了解如何使用 Intune 定位丢失或被盗的 iOS 设备。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 80aa0e5afd1f8862b181d455ff6b545e462f90c9
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>使用 Intune 定位丢失或被盗的 iOS 设备


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

这款“定位设备”的设备操作可在地图上显示丢失或被盗 iOS 设备的位置。 此设备必须是处于监督模式下通过 EDP 注册的公司所有的 iOS 设备。 使用此操作之前，必须将此设备置于[丢失模式](/intune-azure/manage-devices/lost-mode.md)。

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“**Intune**”边栏选项卡上，选择“**设备**”。
4. 在“设备和组”边栏选项卡上，选择“所有设备”。
5. 从管理的设备列表中，选择一台 iOS 设备，然后选择“定位设备”远程操作。
6. 定位到设备后，“定位设备”边栏选项卡上会显示其位置。
    ![定位设备边栏选项卡](./media/locate-device.png)

>[!NOTE]
>出于隐私目的，地图可放大的尺寸受到限制。

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>丢失模式的安全与隐私信息和查找设备操作
- 在开启此操作之前，任何设备的位置信息都不会发送到 Intune。
- 使用查找设备操作时，设备的纬度和经度坐标会发送到 Intune，并在 Azure 门户中显示。
- 该数据存储 24 小时，然后删除。 不能手动删除位置数据。
- 位置数据在存储和传输时均进行加密处理。
- 在配置丢失模式时，我们建议在锁屏界面上显示的输入消息中加入可帮助捡到设备的人返还设备的信息。
