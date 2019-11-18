---
title: 使用 Microsoft Intune 开启 iOS 监督模式
titleSuffix: ''
description: 了解如何使用 Intune 开启 iOS 监督模式。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8190814-07f0-42d8-9b3a-87c67dd2b7ed
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1e995dbc89321bf844151accd654a2d17d35afd9
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "73713408"
---
# <a name="turn-on-ios-supervised-mode"></a>开启 iOS 监督模式


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Apple iOS 监督模式为管理员提供更多用于管理 Apple 设备的选择，很适合用于大规模部署的公司设备。 例如，可限制 AirDrop 或阻止用户更改设备的名称。 有关需要监督模式的设置的列表，请参阅 [Intune 中的 iOS 设备限制设置](../configuration/device-restrictions-ios.md)。

在 Apple [设备注册计划 (DEP)](../enrollment/device-enrollment-program-enroll-ios.md) 中，Intune 支持监督模式。

有关需要监督的 Apple 控件的列表，请参阅 Apple 的[负载设置参考](http://help.apple.com/configurator/mac/2.4/#/cad5370d089)。

## <a name="turn-on-supervised-mode-during-enrollment"></a>在注册过程中启用监督模式

在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，如果已[在 DEP 中创建 Apple 注册配置文件](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile)，则可为设备启用监督模式。 在“设备管理设置”下  ，勾选“监督”  框。

## <a name="turn-on-supervised-mode-after-enrollment"></a>在注册后启用监督模式

注册后，启用监督模式的唯一[方法是将 iOS 设备连接到 Mac](../enrollment/apple-configurator-enroll-ios.md) 并使用 Apple Configurator（该操作会重置设备）。 注册后无法在 Intune 中为设备配置监督模式。

## <a name="identify-a-supervised-device"></a>标识监督的设备

若要确定设备是否受监督，可检查锁定屏幕或“关于”  页：
- 在设备锁定屏幕上，会显示“此 iPhone 由“公司名称”管理”。 
- 在设备的“关于”  页上，会显示“此 iPhone 受监督。  公司名可监视你的 Internet 流量并找到此设备”。

## <a name="next-steps"></a>后续步骤

有关其他设备管理选项，请参阅[什么是 Microsoft Intune 设备管理？](device-management.md)
