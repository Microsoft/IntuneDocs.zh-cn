---
title: 使用 Power BI 从 OData 源创建 Intune 报表
titleSuffix: Microsoft Intune
description: 使用 Power BI Desktop 与 Intune 数据仓库 API 中的交互式筛选器创建树状图可视化效果。
keywords: Intune 数据仓库
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A2C8A336-29D3-47DF-BB4A-62748339391D
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: e18279fd9cca88de5f04c57a8bcccce1c211c6de
ms.sourcegitcommit: 4f3fcc6dcbfe2c4e0651d54a130907a25a4ff66e
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69894332"
---
# <a name="create-an-intune-report-from-the-odata-feed-with-power-bi"></a>使用 Power BI 从 OData 源创建 Intune 报表

本文介绍如何使用 Power BI Desktop 用户交互式筛选器创建 Intune 数据的树状图可视化。 例如, 你的 CFO 可能想知道设备的总体分布在公司拥有的设备和个人设备之间的比较情况。 树状图可提供关于设备类型总数的深入见解。 可以查看 iOS、Android 和 Windows 设备的总数，无论它们属于公司还是个人。

## <a name="overview-of-creating-the-chart"></a>创建图表概述

要创建此图表，需要：
1. 安装 Power BI Desktop（如果还未安装）。
2. 连接到 Intune 数据库仓库数据模型，并检索模型的当前数据。
3. 创建或管理数据模型关系。
4. 使用来自“设备”表的数据创建图表  。
5. 创建交互式筛选器。
6. 查看已完成的图表。

### <a name="a-note-about-tables-and-entities"></a>关于表和实体的注意事项

你是在 Power BI 中使用表。 表包含数据字段。 每个数据字段有一个数据类型。 字段只能包含该数据类型的数据。 数据类型包括数字、文本和日期等。 当加载模型时，Power BI 中的表格将填充来自租户的最新历史数据。 尽管特定数据会随时间而变化，但只要不更新基础数据模型，表结构就不会发生更改。

你可能对术语*实体*和*表*的使用感到困惑。 数据模型可通过 OData (Open Data Protocol) 源进行访问。 在 Power BI 中被称为“表”的容器，在 OData 中实则被称为“实体”。 这两个术语意思相同，都指保存数据的容器。 有关 OData 的详细信息, 请参阅[Odata 概述](/odata/overview)。

## <a name="install-power-bi-desktop"></a>安装 Power BI Desktop

安装最新版本的 Power BI Desktop。 可从 [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop) 下载 Power BI Desktop

## <a name="connect-to-the-odata-feed-for-the-intune-data-warehouse-for-your-tenant"></a>连接到租户的 Intune 数据仓库的 OData 数据源

> [!Note]  
> 在 Intune 中需要访问报表的权限  。 有关详细信息，请参阅[授权](reports-api-url.md)。

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“Microsoft Intune - 概述”  边栏选项卡右侧“其他任务”  下的数据仓库链接，打开“Intune 数据仓库”  窗格。
3. 复制自定义源 URL。 例如：`https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta`
4. 打开 Power BI Desktop。
5. 从菜单栏中选择 "**文件** > " "**获取数据** > " "**Odata 源**"。
6. 将从前面的步骤中复制的自定义源 URL 粘贴到 " **OData 源**" 窗口的 "URL" 框中。
7. 选择“基本”  。

    ![租户的 Intune 数据仓库的 OData 数据源](media/reports-create-01-odatafeed.png)

8. 选择“确定”  。
9. 选择“组织帐户”，然后使用 Intune 凭据登录  。

    ![组织帐户凭据](media/reports-create-02-org-account.png)

10. 选择“**连接**”。 导航器将开启，并显示 Intune 数据仓库中表的列表。

    ![“导航器”-“数据仓库表的列表”的屏幕截图](media/reports-create-02-loadentities.png)

11. 依次选择“设备”和“ownerTypes”表   。  选择“加载”  。 Power BI 会将数据加载至模型。

## <a name="create-a-relationship"></a>创建关系

通过导入多个表，不仅可以分析单个表中的数据，还能跨表分析相关数据。 Power BI 提供“自动检测”  功能，可用于为你查找和创建关系。 数据仓库中的表已生成为，使用 Power BI 中的自动检测功能。 不过，即使 Power BI 不自动查找关系，你仍可以管理关系。

![管理多个表中相关数据的关系](media/reports-create-03-managerelationships.png)

1. 选择“管理关系”  。
2. 如果 Power BI 尚未检测到关系，请选择“自动检测...”  。

关系将在 From 列至 To 列中显示。 在此示例中，“设备”表中的数据字段“ownerTypeKey”链接至“ownerTypes”表中的数据字段“ownerTypeKey”     。 可以使用关系在“设备”  表中查找设备类型代码的普通名称。

## <a name="create-a-treemap-visualization"></a>创建树状图可视化效果

树状图以框中框的形式显示分层数据。 每一层次结构分支都是一个框，其中包含显示子分支的更小的框。 你可以使用 Power BI 桌面创建可显示设备制造商类型相对数量的 Intune 租户数据的树状图。

![Power BI 树状图可视化效果](media/reports-create-03-treemap.png)

1. 在 "**可视化效果**" 窗格中, 找到并选择 "**树状图**"。 **树状图**图将添加到报表画布。
2. 在 "**字段**" 窗格中, `devices`查找表。
3. 展开该表, 然后`manufacturer`选择数据字段。 `devices`
4. 将数据字段拖到报表画布上, 并将其放在树状图图表上。  `manufacturer`
5.    将表中的数据字段拖放到"可视化效果"窗格中,并将其放在标记为"在此处添加数据字段"框中的"值"部分下。`deviceKey` `devices`  

现在就有了一个视觉对象，它显示组织中设备制造商的分布情况。

![包含“设备制造商的分布情况”数据的树状图](media/reports-create-06-treemapwdata.png)

## <a name="add-a-filter"></a>添加筛选器

可以向树状图添加筛选器，以便使用应用解答其他问题。

1. 要添加筛选器，请选择报表画布，然后选择“可视化效果”  下的切片器图标  （带数据模型和支持的关系的树状图![](media/reports-create-slicer.png)）。 空**切片器**可视化将显示在画布上。
2. 在 "**字段**" 窗格中, `ownerTypes`查找表。
3. 展开该表, 然后`ownerTypeName`选择数据字段。 `ownerTypes`
4. `ownerTypes`将 "    数据" 字段从表拖到 "筛选器" 窗格, 并将其放在 "在此处添加数据字段" 部分的 "筛选器" 下。 `onwerTypeName`  

   在下`OwnerTypeKey`表中, 有一个名为的数据字段, 其中包含一个设备是公司拥有的数据还是个人设备。 `OwnerTypes` 由于要在此筛选器中显示易记名称，因此查找 `ownerTypes` 表，并将“ownerTypeName”  拖到切片器中。 此示例说明数据模型如何支持表之间的关系。

![包含“支持表之间的关系”筛选器的树状图](media/reports-create-08_ownertype.png)

现在有了一个交互式筛选器，可用于在公司自有设备和个人拥有的设备之间切换。 可使用此筛选器查看分布变化情况。

1. 在切片器中选择 "**公司**", 以查看公司拥有的设备分布。
2. 选择切片器中的 "**个人**" 以查看个人拥有的设备。

## <a name="next-steps"></a>后续步骤

- 有关[创建和管理关系](https://powerbi.microsoft.com/documentation/powerbi-desktop-create-and-manage-relationships/)的详细信息，请参阅 Power BI 文档中的 Power BI Desktop 部分。
- 咨询 [Intune 数据仓库模型](https://docs.microsoft.com/intune/reports-ref-data-model)。
