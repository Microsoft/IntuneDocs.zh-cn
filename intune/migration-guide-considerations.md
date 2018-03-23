---
title: 特殊迁移注意事项
titlesuffix: Microsoft Intune
description: 本文提供开始 Microsoft Intune 迁移活动前，需注意的特殊事项。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: bd59cf3a4764cc66d0e7d1f47e69c2ff93352387
ms.sourcegitcommit: 21db583d6a9d3c15a8a8ee5579309dff1cfe1f8b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2018
---
# <a name="special-migration-considerations"></a>特殊迁移注意事项

特殊迁移注意事项的适用性取决于现有 MDM 提供程序环境。

## <a name="factory-reset-for-apples-device-enrollment-program-dep"></a>恢复 Apple 设备注册计划 (DEP) 的出厂设置

Apple 设备注册计划 (DEP) 设置最终用户无法删除的设备配置。 若要保留 DEP 的高级管理功能，设备必须通过恢复出厂设置返回到全新状态以注册 Intune。

若要继续使用 DEP 管理 Intune 中的设备，请[使用设备注册计划设置 iOS 设备注册](device-enrollment-program-enroll-ios.md)。


## <a name="next-steps"></a>后续步骤

[阶段 2：迁移活动](migration-guide-campaign.md)
