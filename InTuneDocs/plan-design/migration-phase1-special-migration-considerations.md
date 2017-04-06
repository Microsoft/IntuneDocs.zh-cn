---
title: "特殊迁移注意事项 | Microsoft Docs"
description: "本文的目的是在客户开始迁移活动之前为其提供特殊迁移注意事项。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab5aa4e12d951d818c5afb4e1ac5e866b05733fb
ms.openlocfilehash: 634e84312fa1a93eb85bf70e1593ca11359b72ff
ms.lasthandoff: 03/27/2017


---

# <a name="phase-1-special-migration-considerations"></a>阶段 1：特殊迁移注意事项

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

特殊迁移注意事项的适用性取决于你的现有 MDM 提供程序环境。

## <a name="factory-reset-for-apples-device-enrollment-program-dep"></a>恢复 Apple 设备注册计划 (DEP) 的出厂设置

Apple 设备注册计划 (DEP) 设置最终用户无法删除的设备配置。 若要保留 DEP 的高级管理功能，设备必须通过恢复出厂设置返回到全新状态以注册 Intune。

若要继续使用 DEP 来管理 Intune 中的设备，请执行以下操作：

1.  载入 [Intune 中的 DEP](https://docs.microsoft.com/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune)

2.  请转到你的 Apple DEP 帐户，并从现有的 MDM 提供程序[将 DEP 设备序列号重新分配](https://help.apple.com/deployment/business/#/tesf9562af26)给 Intune。

3.  将 DEP 帐户与 Intune [同步](https://docs.microsoft.com/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune)

4.  [创建相应的 DEP 注册配置文件并将其分配给 Intune 中的序列号](https://docs.microsoft.com/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune)。

5.  恢复设备的出厂重置（通过当前 MDM 提供程序远程执行或在每个设备上手动操作）

6.  将设备分发给最终用户。

## <a name="next-steps"></a>后续步骤 

[阶段 2：迁移活动](https://docs.microsoft.com/intune/plan-design/migration-phase2-migration-campaign)

