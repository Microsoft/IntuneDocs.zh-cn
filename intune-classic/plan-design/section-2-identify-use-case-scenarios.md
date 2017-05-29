---
title: "确定 Intune 用例场景 | Microsoft Docs"
description: "本文可帮助确定用于 Microsoft Intune 仅云实现的 Intune 用例以及子用例场景。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4b3c9af9-78da-44d2-8bd2-3f0f8885952d
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 031820d505e0e9cb007e47a5397934d0e505aed4
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="identify-intune-use-case-scenarios"></a>确定 Intune 用例场景

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

移动设备管理用例场景描述了用户类型或角色及其设备的所有权（例如公司或个人）。 用例场景非常有用，因为它们使你得以将用户细分到可管理的组中。 确定用例场景是成功 Intune 部署规划过程的重要组成部分。

我们将讨论几个示例，帮助组织确定 Intune 用例场景，以及与每个用例关联的组织组和移动设备平台。

## <a name="use-case-scenarios"></a>用例场景

可通过引用组织的 Intune 部署目标和目的开始，帮助确定用于部署的主要用例场景。 在 Intune 部署计划的范围内，需要回答以下问题：

-   是否打算支持企业拥有的设备？

-   是否打算支持个人拥有的设备 (BYOD)？

### <a name="sub-use-case-scenarios"></a>子用例场景

确定主要用例场景后，需确定每个用例场景是否还包括子用例。 例如，某组织可能已确定要求，用以支持包含其他子用例的企业用例场景：

-   信息工作者

-   高级管理人员

-   Kiosk

下面是几个用例和子用例场景示例。 还可使用下表输入组织的用例和子用例场景：

| **用例** | **子用例** |
|:---:|:---:|
| 企业 | 信息工作者 |              
| 企业 | 高级管理人员 |           
| 企业 | Kiosk |
| BYOD | 信息工作者 |           
| BYOD | 高级管理人员 |

## <a name="identify-organizational-groups-associated-with-use-case-scenarios"></a>确定与用例场景关联的组织组

现需确定与每个用例和子用例场景关联的组织组。 下面是几个与用例和子用例场景关联的组织组示例，可用作模板来输入组织的信息：

| **用例** | **子用例** | **组织组** |
|:---:|:---:|:---:|
| 企业 | 信息工作者 | 人力资源、财务 |               
| 企业 | 高级管理人员 | 人力资源、财务 |            
| 企业 | Kiosk | 零售 |
| BYOD | 信息工作者 | 营销、销售 |            
| BYOD | 高级管理人员 | 营销、销售 |

## <a name="identify-mobile-device-platforms-for-use-case-scenarios"></a>为用例场景确定移动设备平台

下面将确定与每个用例场景关联的移动设备平台。 例如，公司用例场景可能支持 iOS 和 Android Samsung KNOX 设备平台，而 BYOD 策略可能包含对其他移动设备平台的支持，如 Android（非 Samsung KNOX）和 Windows 10 移动版。 下面是一个与每个用例场景关联的移动设备平台示例。 可使用下表输入与相应用例场景关联的组织设备平台：

| **用例** | **子用例** | **组** | **设备平台** |   
|:---:|:---:|:---:|:---:|
| 企业 | 信息工作者 | 人力资源、财务 | iOS |                                                           
| 企业 | 高级管理人员 | 人力资源、财务 | iOS |                                                           
| 企业 | Kiosk | 零售 | Android |
| BYOD | 信息工作者 | 营销、销售 | iOS |                                                           
| BYOD | 高级管理人员 | 营销、销售 | iOS |

## <a name="next-steps"></a>后续步骤

下一节提供[如何为每个用例场景确定 Intune 要求](section-3-determine-use-case-requirements.md)的相关指南。

