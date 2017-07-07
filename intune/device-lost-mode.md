---
title: "使用 Intune 激活 iOS 丢失模式"
titleSuffix: Intune on Azure
description: "了解如何使用 Intune 在丢失或被盗的 iOS 设备上激活丢失模式。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 126a7489-fe3e-43fd-a681-defb2fe0bb66
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a34d008ae76355578c6f24a932c9e1e501d5b46b
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="activate-lost-mode-on-ios-devices"></a>激活 iOS 设备上的丢失模式


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

“丢失模式”设备操作可帮助你在丢失或被盗的 iOS 设备上启用丢失模式。 此模式可让你指定一条在设备锁屏界面上显示的信息和电话号码

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“**Intune**”边栏选项卡上，选择“**设备**”。
4. 在“设备和组”边栏选项卡上，选择“所有设备”。
5. 从管理设备列表中，选择一台 iOS 设备，然后选择“丢失模式”远程操作。
6. 在“丢失模式”边栏选项卡上，启用丢失模式，输入将要显示的消息，以及联系电话号码（可选）。
7. 单击“确定”。

启用丢失模式时，将阻止对该设备的所有使用。 最终用户无法访问设备，直到你禁用丢失模式。 虽然丢失模式已启用，但可以使用“定位设备”操作找到设备所在的位置。
要使用丢失模式，此设备必须是处于监督模式下通过 EDP 注册的公司所有的 iOS 设备。

若要查看刚执行的操作的状态，请在“设备和组”边栏选项卡上选择“设备操作”。

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>丢失模式的安全与隐私信息和查找设备操作
- 在开启此操作之前，任何设备的位置信息都不会发送到 Intune。
- 使用查找设备操作时，设备的纬度和经度坐标会发送到 Intune，并在 Azure 门户中显示。
- 该数据存储 24 小时，然后删除。 不能手动删除位置数据。
- 位置数据在存储和传输时均进行加密处理。
- 在配置丢失模式时，我们建议在锁屏界面上显示的输入消息中加入可帮助捡到设备的人返还设备的信息。

