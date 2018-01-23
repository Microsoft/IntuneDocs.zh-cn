---
title: "使用 Intune 数据仓库 | Microsoft Docs"
description: "使用 Intune 数据仓库生成报表，获取有关企业移动环境的见解。"
keywords: "Intune 数据仓库"
author: Erikre
ms.author: erikre
manager: angrobe
ms.date: 10/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 57019B11-DF9B-4D8A-95FE-254C75398DDE
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 910d279b57c885040d2ad092e460d3e7ca71090e
ms.sourcegitcommit: d44c32aad3e84f6c0b296bdb010981d3a818befb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2018
---
# <a name="use-the-intune-data-warehouse"></a>使用 Intune 数据仓库

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用 Intune 数据仓库生成报表，获取有关企业移动环境的见解。 例如，一些报表包括：
-   用户注册 Intune 的趋势，可帮助优化许可证购买
-   应用和操作系统版本细目，可供查看移动设备的状态
-   注册和设备符合性趋势，有助于顺利推出策略更新

相比 Azure 门户，通过数据仓库可访问更多有关移动环境的信息。 借助 Intune 数据仓库可访问：

  -  Intune 历史数据
  -  每日刷新的数据
  -  一个使用 OData 标准的数据模型

> [!Note]
> 如果将混合移动设备管理 (MDM) 与 System Center Configuration Manager 和 Microsoft Intune 配合使用，建议通过 SCCM 检索数据。 Intune 数据仓库仅包含 Intune 数据。 可将 SCCM Power BI 仪表板用于自定义报表。 有关详细信息，请参阅 [Announcing the Power BI solution template for System Center Configuration Manager]( https://powerbi.microsoft.com/blog/sccm-solution-template)（宣布推出适用于 System Center Configuration Manager 的 Power BI 解决方案模板） 和 [Create a Power BI report and dashboard](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/analytics/create-powerbi-report-dashboard)（创建 Power BI 报表和仪表板）。


> [!Important]  
> 可通过使用 beta 版本，试用数据仓库的最新功能。 若要使用 beta 版本，URL 中必须包含查询参数 `api-version=beta`。 Beta 版本会提供尚未正式推出为支持服务的功能。 随着 Intune 不断添加新功能，beta 版本可能会更改行为和数据协定。 任何依赖于 beta 版本的自定义代码或报告工具都可能会因不断推出的更新而临时中断运行。

**后续步骤**

- 获取链接并使用 Power BI 来获取见解。 有关说明，请参阅[使用 Power BI 连接到 Intune 数据仓库](reports-proc-get-a-link-powerbi.md)。
- 通过链接，使用 Power BI 创建自定义报表。 有关说明，请参阅[使用 Power BI 从 OData 数据源创建报表](reports-proc-create-with-odata.md)。
- 有关 Intune 数据仓库 API、数据模型及实体间关系的详细信息<!-- , and an example of creating a custom client to retrieve data,-->，请参阅 [Intune 数据仓库 API](reports-nav-intune-data-warehouse.md)。