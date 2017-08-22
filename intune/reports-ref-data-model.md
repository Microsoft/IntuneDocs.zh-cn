---
title: "数据库仓库数据模型 | Microsoft Docs"
description: "Intune 数据仓库每天对数据进行采样，呈现不断变化的移动环境的历史视图。"
keywords: "Intune 数据仓库"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4D04D3D9-4B6C-41CD-AAF8-466AF8FA6032
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9257af29c65dbe27667738abc8ee06203177124f
ms.sourcegitcommit: b8ef9d8387b4d9b2ea4e6ce937635304771e6532
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/11/2017
---
# <a name="data-warehouse-data-model"></a>数据库仓库数据模型

Intune 数据仓库每天对数据进行采样，呈现不断变化的移动环境的历史视图。

从租户提取的数据会被添加到数据仓库中。 仓库是一组实体和关系，可帮助用户了解想询问的问题的类型。 例如，可查看上周每天安装内部开发的 Android 应用程序的次数，从而评估安装趋势是否为增长趋势。 借助数据仓库的结构可获取有关移动环境的见解。 而 Microsoft Power BI 等分析工具可使用数据仓库数据模型来创建可视化和动态仪表板。

Intune 数据仓库结构使用星型架构模型。 星型架构按时间维度组织事实。 在模型上下文中，一个“事实”是一个定量度量，例如设备数量、应用数量或注册时间。 在模型的上下文中，一个“维度”是一组类别及其层次结构关系。 例如，天数归入月，月份则归入年。 星型架构在灵活性和数据分析方面进行了优化，方便用户创建所需报表来了解不断发展的移动环境。

仓库公开以下高级类别中的数据：
  -  启用了应用保护的应用和使用情况
  -  已注册的设备、属性和清单
  -  应用和软件清单
  -  设备配置和符合性策略

**数据模型实体集**

实体集是数据模型中已命名的实体集合。 这些集中包含的实体用于定义模型中收集的数据。 每个实体集均提供一个针对数据仓库数据模型的访问点。 了解有关以下实体类别的详细信息：

  -  [日期](reports-ref-date.md)
  -  [User](reports-ref-user.md)
  -  [移动应用管理 (MAM)](reports-ref-mobile-app-management.md)
  -  [设备](reports-ref-devices.md)
  -  [应用程序](reports-ref-application.md)
  -  [策略](reports-ref-policy.md)

<!-- ## Data Model relationships

For more information on the relationships in the data model, see [Relationships of Entities](reports-api-entity-relationships.md). -->