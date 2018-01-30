---
title: "使用 Intune 激活 iOS 丢失模式"
titlesuffix: Azure portal
description: "了解如何使用 Intune 在丢失或被盗的 iOS 设备上激活丢失模式。"
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 08/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 126a7489-fe3e-43fd-a681-defb2fe0bb66
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7884682b765fe0df0ecb8b55b18f7a85ac4b2ec9
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="activate-lost-mode-on-ios-devices"></a>激活 iOS 设备上的丢失模式


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

“丢失模式”设备操作可帮助你在丢失或被盗的 iOS 设备上启用丢失模式。 通过此模式可指定一条在设备锁屏界面上显示的消息和电话号码。

## <a name="supported-platforms"></a>受支持的平台

- Windows - 不支持
- Windows Phone - 不支持
- iOS - iOS 9.3 及更高版本，公司拥有的受监督设备支持
- macOS - 不支持
- Android - 不支持

## <a name="how-to-activate-lost-mode"></a>如何激活丢失模式

1. 登录 Azure 门户。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在 Intune 边栏选项卡上，选择“设备”。
4. 在“设备和组”边栏选项卡上，选择“所有设备”。
5. 从管理设备列表中，选择一台 iOS 设备，然后选择“丢失模式”远程操作。
6. 在“丢失模式”边栏选项卡，启用丢失模式。 然后，输入要显示的消息，并输入联系人电话号码（可选）。
7. 单击" **确定**"。

启用丢失模式时，将阻止对该设备的所有使用。 最终用户无法访问设备，直到你禁用丢失模式。 虽然丢失模式已启用，但可以使用“定位设备”操作找到设备所在的位置。
若要使用丢失模式，设备必须是处于监督模式下的公司拥有的 iOS 设备。

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>丢失模式的安全与隐私信息和查找设备操作
- 启用此操作之前，不会向 Intune 发送任何设备的位置信息。
- 使用查找设备操作时，设备的纬度和经度坐标会发送到 Intune，并在 Azure 门户中显示。
- 该数据存储 24 小时，然后删除。 不能手动删除位置数据。
- 位置数据在存储和传输时均进行加密处理。
- 建议在锁屏界面上显示的输入消息中加入可帮助捡到设备的人归还设备的信息。

## <a name="next-steps"></a>后续步骤

若要查看刚执行的操作的状态，请在“设备和组”边栏选项卡上选择“设备操作”。

