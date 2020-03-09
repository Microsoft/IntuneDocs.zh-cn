---
title: 使用 Intune 创建移动威胁防御 (MTD) 应用保护策略
titleSuffix: Microsoft Intune
description: 使用 Microsoft Intune 创建移动威胁防御 (MTD) 应用保护策略。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/20/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 900858d9c437f2d2662260ca62534a987446d2b2
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782121"
---
# <a name="create-mobile-threat-defense-app-protection-policy-with-intune"></a>使用 Intune 创建移动威胁防御应用保护策略

搭载移动威胁防御 MTD 的 Intune 可帮助检测移动设备上存在的威胁和评估相关风险。 可以创建 Intune 应用保护策略，用于评估风险以确定是否允许设备访问公司数据。

> [!NOTE]
> 本文适用于支持应用保护策略的所有移动威胁防御合作伙伴：
>
> - Better Mobile（Android、iOS/iPadOS）
> - Zimperium（Android、iOS/iPadOS）
> - Lookout for Work（Android、iOS/iPadOS）。

## <a name="before-you-begin"></a>在开始之前

在 MTD 设置过程中，需在 MTD 合作伙伴控制台中创建一个将各种威胁分类为高、中和低的策略。 现在需要在 Intune 应用保护策略中设置移动威胁防御级别。

具有 MTD 应用保护策略的先决条件：

- 使用 Intune 设置 MTD 集成。 如果没有此集成，MTD 应用保护策略将无效。

## <a name="to-create-an-mtd-app-protection-policy"></a>创建 MTD 应用保护策略

使用此过程 [创建适用于 iOS/iPadOS 或 Android 的应用程序保护策略](../apps/app-protection-policies.md#app-protection-policies-for-iosipados-and-android-apps)，并使用“应用”、“条件启动”和“分配”页上的以下信息    ：

- **应用**：选择你希望应用保护策略针对的应用。 对于此功能集，根据你选择的移动威胁防御供应商提供的设备风险评估，阻止使用或选择性擦除这些应用。
- **条件启动**：在“设备条件”  下，使用下拉框选择“允许的最大设备威胁级别”  。

  威胁级别“值”选项  ：

  - **安全**：此级别是最安全的。 设备不能存在任何威胁，且仍可访问公司资源。 如果发现了任何威胁，设备都会被评估为不符合。
  - **低**：如果设备上仅存在低级威胁，则该设备符合要求。 低级以上的任意威胁都将使设备不合规。
  - **中**：如果有低级别或中等级别威胁，则设备符合要求。 如果检测到高级别威胁，则设备会被确定为不合规。
  - **高**：此级别的安全性最低并且允许所有威胁级别，且仅将移动威胁防御用作报告目的。 设备必须使用此设置激活 MTD 应用。

  “操作”选项  ：

  - **阻止访问**
  - **擦除数据**

- **分配**：向用户组分配策略。  将通过 Intune 应用保护评估组成员所使用的设备，以确定是否允许其访问目标应用上的公司数据。

## <a name="next-steps"></a>后续步骤

- 详细了解 Microsoft Intune 中的[移动威胁防御](~/protect/mobile-threat-defense.md)。
