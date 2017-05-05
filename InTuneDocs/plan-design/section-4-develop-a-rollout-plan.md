---
title: "确定 Intune 推出的目标组和时段 | Microsoft Docs"
description: "本文帮助确定推出 Microsoft Intune 仅限云的实施的目标组和时段。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3a63f78f-a7e7-4f44-9288-16b28d5d58ca
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e10453155343bb7fd91a4fd3874d393ef78d0b1a
ms.openlocfilehash: 2a970badf5ac18a05115a72dc267ee455ba4628d
ms.lasthandoff: 04/25/2017


---

# <a name="develop-an-intune-rollout-plan"></a>制定 Intune 推出计划

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

本节帮助确定 Intune 推出面向的组织组、每组的推出时段以及所采用的的注册方法。

## <a name="determine-intune-rollout-targeted-groups-and-timeframes"></a>确定 Intune 推出的目标组和时段

首先，请务必确定 Intune 推出的目标组。 之前已在本指南的确定 Intune 用例方案部分讨论过目标组。

其次，需确定每组的 Intune 推出时段。 通常需要在 Intune 部署团队内部以及和目标组进行讨论，帮助确定每个组最适合的推出时段。

例如，Intune 部署团队可能就用户对更改的意愿、用户和设备数量、设备平台的类型、要求、地理位置和业务风险等因素进行讨论以确定推出时段。

组织通常会在 IT 部门中选择一小组用户进行初步试点，然后开始推出 Intune。 然后再扩展试点，加入更多的 IT 部门用户和其他组织组的用户。 试点成功后，组织准备针对剩余的组织组开始完整的生产推出，下面提供了推出的不同组和阶段的部分示例：

-   **试点：**推出的第一阶段应该是用户试点。 试点用户应了解自己是新解决方案的第一批用户，愿意提供反馈以帮助改进配置、文档、通知，为后续推出阶段的所有其他用户简化方法。 这些用户不应该是主管人员或 VIP。

-   **部门：**每个部门可以为一个推出阶段。 此方案一次性针对整个部门。 在此类推出中，每个阶段都极有可能以相同的方式使用移动设备并访问相同的应用程序。 用户也极有可能具有相同类型的策略。

-   **地理位置：**这种部署包括部署到特定地理位置中的所有用户，无论其是否位于同一大洲、国家/地区、区域或公司大楼。 这种分阶段部署能够重点关注用户的特定位置。 这允许实施多个[白色手套](#user-assisted-enrollment)方法，因为同时部署 Intune 的位置数目会减少。 由于同一位置可能存在不同部门或用例，因此可同时部署不同的用例。

-   **平台：**这种部署包括同时部署几个类似的平台。 例如，第一个月可能部署所有的 iOS 设备，然后依次部署 Android 和 Windows 设备。 这种分阶段部署可帮助简化帮助台支持。 帮助台支持一次只能支持一个平台。

下面是包括目标组和时间线的 Intune 推出计划示例：

| **推出阶段** | **7 月** | **8 月** | **9 月** | **10 月** |
|:---:|:---:|:---:|:---:|:---:|
| 小范围试点 | IT（50 位用户） |  |  |  |                                                         
| 扩展试点 | IT（200 位用户），IT 主管人员（10 位用户） |  |  |  |                                                         
| 产品推出阶段 1 |  | 销售和营销（2000 位用户） |  |  |
| 产品推出阶段 2 |  |  | 零售（1000 位用户） |  |
| 产品推出阶段 3 |  |  |  | 人力资源（50 位用户），财务（40 位用户），主管人员（30 位用户） |

## <a name="determine-the-intune-enrollment-approach"></a>确定 Intune 注册方法

现在已确定 Intune 推出的目标组和时段，接下来请为每个组选择最合适的 Intune 注册方法。 组织可采用不同的注册方法来完成 Intune 推出。 几个常用的注册方法包括用户自助服务、用户辅助注册和 IT 技术博览会。

### <a name="user-self-service"></a>用户自助服务

使用此方法，用户通常按照 IT 组织所提供的注册说明自行注册其设备。 此方法最常用于组织中，并且可扩展性比用户辅助注册更强。

### <a name="user-assisted-enrollment"></a>用户辅助注册

这称为“白色手套”方法，IT 团队成员将亲自或通过 Skype 帮助用户完成注册流程。 这种方法通常用于主管人员以及其他在注册过程中可能需要获得更多帮助的组。

### <a name="it-tech-fair"></a>IT 技术博览会

Intune 用户注册的途径还可以选择 IT 技术博览会。 在此活动中，IT 小组将安排一个 Intune 注册辅助展位，用户可以在展位上了解 Intune 注册信息、询问以及获得注册帮助。 该方法对 IT 小组和用户都大有益处，尤其是在 Intune 推出的早期阶段。

下面是 Intune 推出计划的目标组、时间线和注册方法示例：

| **推出阶段** | **7 月** | **8 月** | **9 月** | **10 月** |
|:---:|:---:|:---:|:---:|:---:|
| 小范围试点 |  |  |  |  |                                                         
| 自助服务 | IT |  |  |  |
| 扩展试点 |  |  |  |  |                                                         
| 自助服务 | IT |  |  |  |
| 白色手套 | IT 主管人员 |  |  |  |
| 产品推出阶段 1 |  | 销售、营销 |  |  |
| 自助服务 |  | 销售和营销 |  |  |
| 产品推出阶段 2 |  |  | 零售 |  |
| 自助服务 |  |  |  |  |
| 产品推出阶段 3 |  |  | 零售 |  |
| 自助服务 |  |  |  | 人力资源、财务 |
| 白色手套 |  |  |  | 高级管理人员 |

## <a name="next-section"></a>下一节

下一节提供[如何开发 Intune 推出交流计划](section-5-develop-a-rollout-communication-plan.md)的相关指南。

