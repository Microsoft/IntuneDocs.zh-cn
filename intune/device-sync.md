---
title: "将设备与 Intune 同步"
titlesuffix: Azure portal
description: "了解如何将设备与 Intune 同步以获取最新的策略和操作。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3906b567935f026202ccf0e81424a1bb36e376ef
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2017
---
# <a name="sync-devices-with-intune-to-get-the-latest-policies-and-actions"></a>将设备与 Intune 同步以获取最新的策略和操作


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

“同步”设备操作会强制所选设备立即通过 Intune 签入。 当设备签入时，该设备会立即收到已分配给自己的任何挂起的操作或策略。  此操作可帮助立即验证和对已分配的策略进行故障排除，而无需等待下一个安排的签入。

## <a name="supported-platforms"></a>受支持的平台

- Windows - 支持
- Windows Phone - 支持
- iOS - 支持
- macOS - 支持
- Android - 支持

## <a name="how-to-sync-a-device"></a>如何同步设备

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“**Intune**”边栏选项卡上，选择“**设备**”。
4. 在“设备和组”边栏选项卡上，选择“所有设备”。
5. 从管理的设备列表中，选择一台设备，然后选择“同步”远程操作。
7. 选择“是”确认操作。

## <a name="next-steps"></a>后续步骤

选择“设备操作”，查看同步操作的状态。 
