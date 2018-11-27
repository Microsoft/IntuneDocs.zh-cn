---
title: 确定用例方案
titlesuffix: Microsoft Intune
description: 本文可帮助你确定用于 Microsoft Intune 仅云实现的 Intune 用例以及子用例场景。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4b3c9af9-78da-44d2-8bd2-3f0f8885952d
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 8058a6f4cda02a044e050f07bb6264e29b83f879
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179909"
---
# <a name="identify-mobile-device-management-use-case-scenarios"></a>确定移动设备管理用例场景

确定用例场景是成功 Intune 部署规划过程的重要组成部分。 通过用例场景，你可以根据用户类型或角色以及用户设备的所有权（例如，公司或个人）将用户划分成若干个可管理的组，因此，用例场景非常有用。

我们在这里将讨论几个示例，帮助组织确定 Intune 用例场景，以及与每个用例关联的组织组和移动设备平台。

## <a name="device-ownership"></a>设备所有权
首先可以参考组织的 Intune 部署目标和宗旨，帮助确定用于部署的主要用例场景。 在 Intune 部署计划的范围内，回答以下问题：

-   是否打算支持企业拥有的设备？

-   是否打算支持个人拥有的设备 (BYOD)？

这些不是选择题。 你可能会发现，你需要同时支持两种形式的设备所有权才能满足你的组织目标。 子用例将帮助阐明应用不同设备管理策略的位置。

### <a name="user-type-or-device-role"></a>用户类型或设备角色

确定是否每个用例场景还包括子用例。 例如，你的组织可能已确定要求，用以支持包含基于用户类型或设备角色的其他子用例的企业用例场景，例如：

-   信息工作者

-   高级管理人员

-   Kiosk

下面是几个用例和子用例场景的示例：

| **用例** | **子用例** |
|:---:|:---:|
| 企业 | 信息工作者 |              
| 企业 | 高级管理人员 |           
| 企业 | Kiosk |
| BYOD | 信息工作者 |           
| BYOD | 高级管理人员 |

你可以[下载上表的模板](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)来输入组织的用例和子用例场景。

## <a name="organizational-groups-for-your-scenarios"></a>你的场景的组织组

现需确定与每个用例和子用例场景关联的组织组。 例如：

| **用例** | **子用例** | **组织组** |
|:---:|:---:|:---:|
| 企业 | 信息工作者 | 人力资源、财务 |               
| 企业 | 高级管理人员 | 人力资源、财务 |            
| 企业 | Kiosk | 零售 |
| BYOD | 信息工作者 | 营销、销售 |            
| BYOD | 高级管理人员 | 营销、销售 |


## <a name="mobile-device-platforms-for-your-scenarios"></a>适用于你场景的移动设备平台

下一步是确定与每个用例场景关联的移动设备平台。 可能有多个。

例如，公司的用例方案可能支持 iOS 和 Android Samsung Knox 设备平台。 BYOD 策略可能支持其他移动设备平台，如 Android（非 Samsung Knox）和 Windows 10 移动版。 基于前面的示例，我们已将移动设备平台与每个用例场景关联。

| **用例** | **子用例** | **组** | **设备平台** |   
|:---:|:---:|:---:|:---:|
| 企业 | 信息工作者 | 人力资源、财务 | iOS |                                                           
| 企业 | 高级管理人员 | 人力资源、财务 | iOS |                                                           
| 企业 | Kiosk | 零售 | Android |
| BYOD | 信息工作者 | 营销、销售 | iOS |                                                           
| BYOD | 高级管理人员 | 营销、销售 | iOS |

## <a name="next-steps"></a>后续步骤

下一节提供[如何为每个用例场景确定 Intune 要求](planning-guide-requirements.md)的相关指南。
