---
title: 数据库仓库数据模型
titlesuffix: Microsoft Intune
description: Microsoft Intune 数据仓库每天都会采样数据，显示不断变化的移动环境的历史视图。
keywords: Intune 数据仓库
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4D04D3D9-4B6C-41CD-AAF8-466AF8FA6032
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 228b662739d161a4f4d6d145746fc68e7c3b87e0
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52188103"
---
# <a name="data-warehouse-data-model"></a>数据库仓库数据模型

Intune 数据仓库每天对数据进行采样，呈现不断变化的移动设备环境的历史视图。 该视图由一段时间内相关的实体组成。

## <a name="entities-entity-sets"></a>实体：实体集

仓库公开以下高级区域中的数据：

  -  启用了应用保护的应用和使用情况
  -  已注册的设备、属性和清单
  -  应用和软件清单
  -  设备配置和符合性策略

这些区域包含对 Intune 环境有意义的实体。 你可在以下主题中找到关于实体集的详细信息：

  -  [应用程序](reports-ref-application.md)
  -  [日期](reports-ref-date.md)
  -  [设备](reports-ref-devices.md)
  -  [Intune 管理扩展](reports-ref-intunemanagementextension.md)
  -  [策略](reports-ref-policy.md)
  -  [移动应用管理 (MAM)](reports-ref-mobile-app-management.md)
  -  [User](reports-ref-user.md)
  -  [当前用户](reports-ref-current-user.md)
  -  [用户设备关联](reports-ref-user-device.md)

## <a name="relationships-star-schema-model"></a>关系：星型架构模型

仓库对关系中的实体进行排列，这些实体对用户想提出的问题类型有实际意义。 例如，你可以查看内部开发的 Android 应用程序的安装次数。 借助数据仓库的结构可获取有关移动环境的见解。 而 Microsoft Power BI 等分析工具可使用数据仓库数据模型来创建可视化效果和动态仪表板。

实体和关系使用星型架构模型。 星型架构将时间维度上的事实互相关联。 在模型上下文中，一个“事实”是一个定量度量，例如设备数量、应用数量或注册时间。 事实数据表存储大量数据。 它们可以变得很大，因此它们通常将信息保存期限制为 30 天。 维度提供事实数据的上下文。 如果事实是用来测量发生了什么情况，则维度会表明情况发生在谁身上。 维度表（例如“用户”表）更小并可以重新导流比事实数据表保存时间更长的数据。 

星型架构在灵活性和数据分析方面进行了优化，方便用户创建所需报表来了解不断发展的移动环境。

## <a name="time-daily-snapshots"></a>时间：每日快照

仓库在 Intune 数据的下游。 Intune 在午夜 UTC 拍摄每日快照，并将快照存储在仓库中。 保存快照的持续时间因事实数据表而异。 有些事实数据表可能保存 7 天，有些 30 天，有些甚至更长。

## <a name="next-steps"></a>后续步骤

 - 要了解有关数据仓库如何在 Intune 中跟踪用户生存期的详细信息，请参阅 [Intune 数据仓库中的用户生存期表示](reports-ref-user-timeline.md)。
 - 在[创建第一个数据仓库](https://www.codeproject.com/Articles/652108/Create-First-Data-WareHouse)中了解有关使用数据仓库的详细信息。
 - 在[通过导入数据集创建新的 Power BI 报表](https://powerbi.microsoft.com/documentation/powerbi-service-create-a-new-report/)了解有关使用 Power BI 和数据仓库的详细信息。 
