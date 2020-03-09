---
title: 使用 Power BI 从 OData 源创建 Intune 报表
titleSuffix: Microsoft Intune
description: 使用 Power BI Desktop 与 Intune 数据仓库 API 中的交互式筛选器创建树状图可视化效果。
keywords: Intune 数据仓库
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/03/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A2C8A336-29D3-47DF-BB4A-62748339391D
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7fbbffb187fc9e9537bf647bc33e3d98879369c3
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576049"
---
# <a name="create-an-intune-report-from-the-odata-feed-with-power-bi"></a>使用 Power BI 从 OData 源创建 Intune 报表

本文介绍如何使用 Power BI Desktop 和交互式筛选器创建 Intune 数据的树状图可视化效果。 例如，比起了解公司所拥有设备与个人设备的情况，CFO 可能更想了解设备的整体分布情况。 树状图可提供关于设备类型总数的深入见解。 可以查看 iOS/iPadOS、Android 和 Windows 设备的总数，无论它们属于公司还是个人。

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

你可能对术语*实体*和*表*的使用感到困惑。 可通过 OData (Open Data Protocol) 数据源访问数据模型。 在 Power BI 中被称为“表”的容器，在 OData 中实则被称为“实体”。 这两个术语意思相同，都指保存数据的容器。 有关 OData 的详细信息，请参阅 [OData 概述](/odata/overview)。

## <a name="install-power-bi-desktop"></a>安装 Power BI Desktop

安装最新版本的 Power BI Desktop。 可从以下地址下载 Power BI Desktop：[PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop)

## <a name="connect-to-the-odata-feed-for-the-intune-data-warehouse-for-your-tenant"></a>连接到租户的 Intune 数据仓库的 OData 数据源

> [!Note]  
> 在 Intune 中需要访问报表的权限  。 有关详细信息，请参阅[授权](../reports-api-url.md)。

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“Microsoft Intune - 概述”  边栏选项卡右侧“其他任务”  下的数据仓库链接，打开“Intune 数据仓库”  窗格。
3. 复制自定义源 URL。 例如：`https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta`
4. 打开 Power BI Desktop。
5. 从菜单栏中，选择“文件” > “获取数据” > “Odata 源”    。
6. 在“OData 数据源”窗口中，将从之前步骤中复制的自定义源 URL 粘贴到 URL 框  。
7. 选择“基本”  。

    ![租户的 Intune 数据仓库的 OData 数据源](./media/reports-proc-create-with-odata/reports-create-01-odatafeed.png)

8. 选择“确定”  。
9. 选择“组织帐户”，然后使用 Intune 凭据登录  。

    ![组织帐户凭据](./media/reports-proc-create-with-odata/reports-create-02-org-account.png)

10. 选择“**连接**”。 导航器将开启，并显示 Intune 数据仓库中表的列表。

    ![“导航器”-“数据仓库表的列表”的屏幕截图](./media/reports-proc-create-with-odata/reports-create-02-loadentities.png)

11. 依次选择“设备”和“ownerTypes”表   。  选择“加载”  。 Power BI 会将数据加载至模型。

## <a name="create-a-relationship"></a>创建关系

通过导入多个表，不仅可以分析单个表中的数据，还能跨表分析相关数据。 Power BI 提供“自动检测”  功能，可用于为你查找和创建关系。 数据仓库中的表已生成为，使用 Power BI 中的自动检测功能。 不过，即使 Power BI 不自动查找关系，你仍可以管理关系。

![管理多个表中相关数据的关系](./media/reports-proc-create-with-odata/reports-create-03-managerelationships.png)

1. 选择“管理关系”  。
2. 如果 Power BI 尚未检测到关系，请选择“自动检测...”  。

关系将在 From 列至 To 列中显示。 在此示例中，“设备”表中的数据字段“ownerTypeKey”链接至“ownerTypes”表中的数据字段“ownerTypeKey”     。 可以使用关系在“设备”  表中查找设备类型代码的普通名称。

## <a name="create-a-treemap-visualization"></a>创建树状图可视化效果

树状图以框中框的形式显示分层数据。 每一层次结构分支都是一个框，其中包含显示子分支的更小的框。 可使用 Power BI Desktop 创建 Intune 租户数据的树状图，用于显示相对数量的设备制造商类型。

![Power BI 树状图可视化效果](./media/reports-proc-create-with-odata/reports-create-03-treemap.png)

1. 在“可视化效果”窗格中，查找并选择“树状图”   。 “树状图”图表将被添加到报表画布  。
2. 在“字段”窗格中，找到 `devices` 表  。
3. 展开 `devices` 表，然后选择 `manufacturer` 数据字段。
4. 将 `manufacturer` 数据字段拖到报表画布，并将其放在“树状图”图表中  。
5. 将 `deviceKey` 数据字段从 `devices` 表拖到“可视化效果”窗格中，并将其拖到复选框“在此处添加数据字段”中的“值”部分下    。  

现在就有了一个视觉对象，它显示组织中设备制造商的分布情况。

![包含“设备制造商的分布情况”数据的树状图](./media/reports-proc-create-with-odata/reports-create-06-treemapwdata.png)

## <a name="add-a-filter"></a>添加筛选器

可以向树状图添加筛选器，以便使用应用解答其他问题。

1. 要添加筛选器，请选择报表画布，然后选择“可视化效果”  下的切片器图标  （带数据模型和支持的关系的树状图![](./media/reports-proc-create-with-odata/reports-create-slicer.png)）。 空的“切片器”可视化效果将显示在画布上  。
2. 在“字段”窗格中，找到 `ownerTypes` 表  。
3. 展开 `ownerTypes` 表，然后选择 `ownerTypeName` 数据字段。
4. 将 `onwerTypeName` 数据字段从 `ownerTypes` 表拖到“筛选器”窗格中，并将其放在复选框“在此处添加数据字段”中的“此页上的筛选器”部分下    。  

   在 `OwnerTypes` 表中有一个名为 `OwnerTypeKey` 的数据字段，它包含表示设备是公司拥有还是个人所有的数据。 由于要在此筛选器中显示易记名称，因此查找 `ownerTypes` 表，并将“ownerTypeName”  拖到切片器中。 此示例说明数据模型如何支持表之间的关系。

![包含“支持表之间的关系”筛选器的树状图](./media/reports-proc-create-with-odata/reports-create-08_ownertype.png)

现在有了一个交互式筛选器，可用于在公司自有设备和个人拥有的设备之间切换。 可使用此筛选器查看分布变化情况。

1. 选择切片器中的“公司”可查看公司拥有设备的分布  。
2. 选择切片器中的“个人”可查看个人拥有设备  。

## <a name="next-steps"></a>后续步骤

- 有关[创建和管理关系](https://powerbi.microsoft.com/documentation/powerbi-desktop-create-and-manage-relationships/)的详细信息，请参阅 Power BI 文档中的 Power BI Desktop 部分。
- 咨询 [Intune 数据仓库模型](reports-ref-data-model.md)。
