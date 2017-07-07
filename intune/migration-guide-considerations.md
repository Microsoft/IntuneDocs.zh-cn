---
title: "特殊迁移注意事项"
description: "本文的目的是在客户开始迁移活动之前为其提供特殊迁移注意事项。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: bc39ffd3a4f11a4c2b32f75dc5befcd8ce42f43e
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="special-migration-considerations"></a>特殊迁移注意事项

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

特殊迁移注意事项的适用性取决于你的现有 MDM 提供程序环境。

## <a name="factory-reset-for-apples-device-enrollment-program-dep"></a>恢复 Apple 设备注册计划 (DEP) 的出厂设置

Apple 设备注册计划 (DEP) 设置最终用户无法删除的设备配置。 若要保留 DEP 的高级管理功能，设备必须通过恢复出厂设置返回到全新状态以注册 Intune。

若要继续使用 DEP 管理 Intune 中的设备，请[使用设备注册计划设置 iOS 设备注册](/intune/device-enrollment-program-enroll-ios)。


## <a name="next-steps"></a>后续步骤 

[阶段 2：迁移活动](migration-guide-campaign.md)
