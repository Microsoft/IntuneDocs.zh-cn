---
title: "使用 Power BI 从 OData 数据源创建报表 | Microsoft Docs"
description: "使用 Power BI Desktop 与 Intune 数据仓库 API 中的交互式筛选器创建树状图可视化效果。"
keywords: "Intune 数据仓库"
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: A2C8A336-29D3-47DF-BB4A-62748339391D
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: a81a3b0648c77e3adb7a57bdcecddea1e0412eb2
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="create-a-report-from-the-odata-feed-with-power-bi"></a>使用 Power BI 从 OData 数据源创建报表

在本教程中，将使用 Power BI Desktop 与交互式筛选器来创建树状图可视化效果。 例如，比起仅了解公司所拥有设备与个人设备的情况，CFO 可能更想了解设备的整体分布情况。 树状图可提供关于设备类型总数的深入见解。 可以查看 iOS、Android 和 Windows 设备的总数，无论它们属于公司还是个人。

### <a name="overview-of-creating-the-chart"></a>创建图表概述

要创建此图表，需要：
1. 安装 Power BI Desktop（如果还未安装）。
2. 连接到 Intune 数据库仓库数据模型，并检索模型的当前数据。
3. 创建或管理数据模型关系。
4. 使用来自“设备”表的数据创建图表。
5. 创建交互式筛选器。
6. 查看已完成的图表。

### <a name="a-note-about-tables-and-entities"></a>关于表和实体的注意事项

你是在 Power BI 中使用表。 表包含数据字段。 每个数据字段有一个数据类型。 字段只能包含该数据类型的数据。 数据类型包括数字、文本和日期等。 当加载模型时，Power BI 中的表格将填充来自租户的最新历史数据。 尽管特定数据会随时间而变化，但只要不更新基础数据模型，表结构就不会发生更改。

你可能对术语_实体_和_表_的使用感到困惑。 可通过 OData 数据源访问数据模型。 在 Power BI 中被称为“表”的容器，在 OData 中实则被称为“实体”。 这两个术语意思相同，都指保存数据的容器。

## <a name="install-power-bi-desktop"></a>安装 Power BI Desktop

安装最新版本的 Power BI Desktop。 可从 [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop) 下载 Power BI Desktop

## <a name="connect-to-the-odata-feed-for-the-intune-data-warehouse-for-your-tenant"></a>连接到租户的 Intune 数据仓库的 OData 数据源

> [!Note]  
> 在 Intune 中需要访问报表的权限。 有关详细信息，请参阅[授权](reports-api-url.md)。

1. 登录到 Azure 门户。
2. 选择“更多服务” > “监视 + 管理” + “Intune”。
3. 打开“Intune 数据仓库”边栏选项卡。
4. 复制自定义源 URL。 例如：`https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta`
5. 打开 Power BI Desktop。
6. 选择“获取数据” > “Odata 数据源”。
7. 在“OData 数据源”窗口中，将自定义源 URL 粘贴至 URL 框。
8. 选择“基本”。

    ![OData 数据源](media/reports-create-01-odatafeed.png)

9. 选择“确定”。
10. 选择“组织帐户”，然后使用 Intune 凭据登录。 

    ![组织帐户凭据](media/reports-create-02-org-account.png)

11. 选择“**连接**”。 导航器将开启，并显示 Intune 数据仓库中表的列表。 

    ![导航器](media/reports-create-02-loadentities.png)

12. 依次选择“设备”和“ownerTypes”表。  选择“加载”。 Power BI 会将数据加载至模型。

## <a name="create-a-relationship"></a>创建关系 

通过导入多个表，不仅可以分析单个表中的数据，还能跨表分析相关数据。  在 PowerBI 中有一项功能名为“自动检测”，可用于查找和创建关系。 数据仓库中已生成的表本就可配合 PowerBI 自动检测功能使用。 但是，即使 PowerBI 不自动查找关系，你仍然可以管理关系。

![管理关系](media/reports-create-03-managerelationships.png)

1. 选择“管理关系”。
2. 如果 PowerBI 未检测到关系，请选择“自动检测...”。  
关系将在 From 列至 To 列中显示。 在此示例中，“设备”表中的数据字段“ownerTypeKey”链接至“ownerTypes”表中的数据字段“ownerTypeKey”。 在“设备”表中使用关系查找设备类型代码的普通名词。

## <a name="create-a-treemap-visualization"></a>创建树状图可视化效果

树状图图表以框中框的形式显示分层数据。 每一层次结构分支都是一个框，其中包含显示子分支的更小的框。 可使用 Power BI Desktop 创建 Intune 数据树状图。

![可视化效果 > 树状图](media/reports-create-03-treemap.png)

1. 选择图表类型。 选择“树状图”。
2. 在数据模型中，查找“设备”表。
3. 展开“设备”表，在“字段”面板中选择“制造商”数据字段。
4. 将“制造商”数据字段拖动到报表画布上的树状图图表中。
5. 将“deviceKey”数字字段从“设备”表拖动到“可视化效果”面板中的“值”部分，并拖动至标有“在此拖动数据字段”的框内。  
现在，你已获得了一个视觉对象，它展示了组织中设备制造商的分布情况。

![包含数据的树状图](media/reports-create-06-treemapwdata.png)

## <a name="add-a-filter"></a>添加筛选器

可以向树状图添加筛选器，以便使用应用解答其他问题。 

1. 选择报表画布，然后选择位于“可视化效果”之下的“切片器图标”（![包含数据的树状图](media/reports-create-slicer.png)），以添加筛选器。
2. 查找“ownerTypes”表，并将“ownerTypeName”数据字段拖动到“可视化效果”面板下的“筛选器”部分中。  
   在设备表中有一个名为“OwnerTypeKey”的数据字段，它包含表示设备是公司拥有还是个人所有的代码。 若要在此筛选器中显示友好名称，请查找“ownerTypes”表，并拖动“ownerTypeName”。 以下示例说明数据模型如何支持表之间的关系。

![包含筛选器的树状图](media/reports-create-08_ownertype.png)

现在，通过交互式筛选器可在公司拥有设备与个人拥有设备之间进行切换，以查看分布的更改情况。

1. 选择“公司”查看公司拥有设备的分布。
2. 选择“个人”查看个人拥有设备。

## <a name="next-steps"></a>后续步骤

 - 有关[创建和管理关系](https://powerbi.microsoft.com/documentation/powerbi-desktop-create-and-manage-relationships/)的详细信息，请参阅 Power BI 文档中的 Power BI Desktop 部分。
 - 咨询 [Intune 数据仓库模型](https://docs.microsoft.com/intune/reports-ref-data-model)。