---
title: 特殊迁移注意事项
titleSuffix: Microsoft Intune
description: 本文提供开始 Microsoft Intune 迁移活动前，需注意的特殊事项。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86cef30c31b53c6bfd1873390fb7546cbeab2a53
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72510037"
---
# <a name="special-migration-considerations"></a>特殊迁移注意事项

特殊迁移注意事项的适用性取决于现有 MDM 提供程序环境。

## <a name="wipe-for-apples-device-enrollment-program-dep"></a>擦除 Apple 设备注册计划 (DEP)

Apple 设备注册计划 (DEP) 设置最终用户无法删除的设备配置。 若要保留 DEP 的高级管理功能，设备必须通过擦除返回到全新状态以注册 Intune。

若要继续使用 DEP 管理 Intune 中的设备，请[使用设备注册计划设置 iOS 设备注册](../enrollment/device-enrollment-program-enroll-ios.md)。


## <a name="next-steps"></a>后续步骤

[第 2 阶段：迁移活动](../migration-guide-campaign.md)
