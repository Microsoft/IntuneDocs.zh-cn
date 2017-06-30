---
title: "典型 Intune 迁移周期的工作方式"
description: "本文旨在说明 Intune 迁移周期的工作方式，并提供有关客户如何处理迁移周期的示例。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3688b724-9521-4210-bf4d-bcf47d8d4ca0
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 1911c8a2460a98218027c40a26d81f1ca4c482f5
ms.openlocfilehash: 70aa7155e050450a2d786a1f16e42ce2a3c77f9e
ms.contentlocale: zh-cn
ms.lasthandoff: 06/13/2017


---

# <a name="typical-migration-cycle"></a>典型迁移周期

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

以下情况非常常见，组织通过面向 IT 部门中的用户子集使用小型试验启动其 Intune 迁移。 此外，组织可能需要讨论组的更改意愿、用户数量、复杂性、要求、位置和业务风险等因素来帮助确定迁移时间范围。

以下示例说明如何安排目标组：

  | **迁移目标组** | **时间段 1** | **时间段 2** | **时间段 3** | **时间段 4** | **...**
|:---:|:---:|:---:|:---:|:---:|:---:|
| 有限的试验 IT 组织（50 个用户） | 宣布计划 | 指示注册 | 给出截止时间 | 强制执行条件访问 |  |                                                        
| 扩展的试验 IT 组织（200 个用户） |  | 宣布计划 | 指示注册 | 给出截止时间 | 强制执行条件访问 | 
| 迁移阶段 1：精通技术的用户（2000 个） |  |  | 宣布计划 | 指示注册 | 给出截止时间 | 
| 迁移阶段 2：美国东部 |  |  |  | 宣布计划 | 指示注册 | 
| 所有区域 |  |  |  |  | 宣布计划 | 

## <a name="customer-migration-case-study"></a>客户迁移案例研究

### <a name="adatum-corporation"></a>Adatum Corporation

- 查看 [Adatum Corporation 如何完成从第三方 MDM 提供程序到 Intune 的迁移过程](https://gallery.technet.microsoft.com/Intune-migration-guide-893a95e3?redir=0)。

## <a name="monitoring-migration"></a>监视迁移

Microsoft Intune 提供了几种方法，可用于监视迁移情况：

1.  Intune 用户组视图

2.  一组内置报表和

3.  控制台内警报。

应在每个阶段完成之后跟踪注册设备的用户数量，从而可以：

-   评估通信计划的有效性。

-   估计强制实施条件访问的影响。


## <a name="post-migration"></a>迁移后

在迁移到 Intune 后，需要停用之前的 MDM 提供程序和取消订阅服务。 此外，还需要执行 MDM 提供程序的说明，删除任何不需要的基础结构要求。

