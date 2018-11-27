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
search.appverid: MET150
ms.openlocfilehash: 039b3dc4d45b340a7d7f8ed0314661a2505a779b
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179807"
---
# <a name="special-migration-considerations"></a>特殊迁移注意事项

特殊迁移注意事项的适用性取决于现有 MDM 提供程序环境。

## <a name="wipe-for-apples-device-enrollment-program-dep"></a>擦除 Apple 设备注册计划 (DEP)

Apple 设备注册计划 (DEP) 设置最终用户无法删除的设备配置。 若要保留 DEP 的高级管理功能，设备必须通过擦除返回到全新状态以注册 Intune。

若要继续使用 DEP 管理 Intune 中的设备，请[使用设备注册计划设置 iOS 设备注册](device-enrollment-program-enroll-ios.md)。


## <a name="next-steps"></a>后续步骤

[阶段 2：迁移活动](migration-guide-campaign.md)
