---
title: 确定针对推出和时间段的组
titleSuffix: Microsoft Intune
description: 本文可帮助你决定向 Microsoft Intune 推出的组和针对这些部署的时间段。
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
ms.assetid: 3a63f78f-a7e7-4f44-9288-16b28d5d58ca
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 777267f10edac5bbdbe23ceb3068d4366a8df7b7
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509948"
---
# <a name="develop-a-rollout-plan"></a>制定推出计划

推出计划将标识要针对 Intune 推出的组织组、每个组的推出时间段和你将要使用的注册方法。

## <a name="targeted-groups-and-timeframes"></a>目标组和时间段

首先，查看针对 Intune 推出的组和你在[用例方案](planning-guide-scenarios.md)中标识的组。

其次，确定每个目标组的时间段。 该任务通常需要在 Intune 部署团队内部和目标组之间进行讨论，以确定每个组最适合的推出时段。 此类讨论中要涵盖的点包括：
* 组的更改意愿
* 用户和设备数
* 设备平台类型
* 要求
* 地理位置
* 业务风险

## <a name="rollout-phases"></a>实施阶段
组织通常会在 IT 部门中选择一小组用户进行初步试点，然后开始推出 Intune。 可以扩大试点，加入更多的 IT 部门用户，还可以加入其他组织组的用户。

### <a name="pilot"></a>试点
推出的第一阶段应是试点用户。 试点用户应了解自己是新解决方案的第一批用户。 试点用户必须愿意提供反馈以帮助改进配置、文档、通知，为后续推出阶段的所有其他用户简化方法。 这些用户不应是主管人员或 VIP。

试点是你测试各种[挑战](../planning-guide-deployment-goals.md)和优化之前收集的[要求](../planning-guide-requirements.md)的好机会。

包括你的[通信](../planning-guide-communication-plan.md)计划、[支持](planning-guide-support-plan.md)计划和[测试和验证](planning-guide-test-validation.md)，以将影响用户的问题解决在萌芽状态。

### <a name="production-rollout"></a>产品推出
一个试点成功后，即可开始进行针对组织中其他组进行完整生产推出。 不同的推出组和阶段的示例如下：

- **部门** <br/>每个部门可以为一个推出阶段。 一次针对整个部门。 在此类推出中，每个部门中的用户都有可能以相同的方式使用移动设备并访问相同的应用程序。 用户很可能具有相同类型的策略。

- **地理位置** <br/>通过这种方法，可以部署到特定地理位置中的所有用户，无论是在同一洲、同一国家/地区，还是在同一公司大楼。 这种分阶段部署让你能重点关注用户的特定位置。 这让你能够提供多个[白色手套](#user-assisted-enrollment)方法，因为同时部署 Intune 的位置数目会减少。 由于同一位置可能存在不同部门或用例，因此可同时部署不同的用例。

- **平台** <br/>这种部署包括同时部署几个类似的平台。 例如，第一个月可能部署所有的 iOS 设备，然后依次部署 Android 和 Windows 设备。 这种分阶段部署有助于简化支持人员的支持，因为支持人员一次只需支持一个单个平台。

下面是包括目标组和时间线的 Intune 推出计划示例：

| **推出阶段** | **7 月** | **8 月** | **9 月** | **10 月** |
|:---:|:---:|:---:|:---:|:---:|
| 小范围试点 | IT（50 位用户） |  |  |  |                                                         
| 扩展试点 | IT（200 位用户），IT 主管人员（10 位用户） |  |  |  |                                                         
| 产品推出阶段 1 |  | 销售和营销（2000 位用户） |  |  |
| 产品推出阶段 2 |  |  | 零售（1000 位用户） |  |
| 产品推出阶段 3 |  |  |  | 人力资源（50 位用户），财务（40 位用户），主管人员（30 位用户） |

你可以[下载上表的模板](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)来输入组织的推出阶段。
## <a name="match-rollout-groups-to-enrollment-approaches"></a>将推出组与注册方法匹配

至此，已确定 Intune 推出的目标组和时段，接下来为每个组选择最合适的 Intune 注册方法。 你可以使用不同的注册方法，包括：
* 用户自助服务
* 用户辅助注册
* IT 技术博览会

### <a name="user-self-service"></a>用户自助服务

在这种情况下，用户通常按照 IT 组织所提供的注册说明自行注册其设备。 此方法最常用于组织中，相比用户辅助注册，可扩展性更强。

### <a name="user-assisted-enrollment"></a>用户辅助注册

这称为“白色手套”方法。 IT 团队成员会亲自或通过 Skype 帮助用户完成注册过程。 这种方法通常用于主管人员以及其他在注册过程中可能需要获得更多帮助的组。

### <a name="it-tech-fair"></a>IT 技术博览会

Intune 用户注册的途径还可以选择 IT 技术博览会。 在此活动中，IT 小组将安排一个 Intune 注册辅助展位，用户可以在展位上了解 Intune 注册信息、询问以及获得注册帮助。 该方法对 IT 小组和用户都大有益处，尤其是在 Intune 推出的早期阶段。

下面是上述 Intune 推出计划的更新示例，包含注册方法：

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
| 自助服务 |  |  | 零售 |  |
| 产品推出阶段 3 |  |  |  | 主管、人力资源、金融 |
| 自助服务 |  |  |  | 人力资源、财务 |
| 白色手套 |  |  |  | 高级管理人员 |

## <a name="next-steps"></a>后续步骤

下一节提供[如何开发 Intune 推出交流计划](../planning-guide-communication-plan.md)的相关指南。
