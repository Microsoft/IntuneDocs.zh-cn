---
title: 移动 Intune 数据仓库帐户数据
titlesuffix: Microsoft Intune
description: 了解如何在移动帐户时备份 Intune 数据仓库数据。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ee3ccbf9-82fc-4fbf-9d3d-8f05e431d090
ms.reviewer: aanavath
ms.suite: ems
ms.custom: ''
ms.openlocfilehash: f1b2af2723ddb4c89f7f3d6409ced12f7a16883a
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34223656"
---
# <a name="move-your-intune-data-warehouse-account-data"></a>移动 Intune 数据仓库帐户数据 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

请求移动帐户意味着请求将你的数据中心更改为其他位置。 移动后，你的数据仓库将根据指定的移动开始日期重置并开始在新位置记录数据。 要备份以前的数据仓库数据，请先完成以下步骤，然后再移动帐户。 大多数数据仓库表将数据保留 30 天，因此，在帐户移动 30 天后，将无法再看到这些表中的任何数据差距。 要详细了解特定表的保留期，请参阅[数据仓库数据模型](reports-ref-data-model.md)。 

## <a name="back-up-your-data-warehouse-data"></a>备份数据仓库数据 

要备份数据仓库数据，必须使用数据仓库 API 将数据仓库数据保存到 .csv 文件中：  

1. 如果是首次使用数据仓库 API，请按照以下文章中提供的一次性过程进行操作：[使用 REST 客户端从 Intune 数据仓库 API 获取数据](reports-proc-data-rest.md)。
2. 使用标题为[使用 PowerShell 访问 Intune 数据仓库](https://github.com/Microsoft/Intune-Data-Warehouse/tree/master/Samples/PowerShell)的 PowerShell 示例将所有数据下载到 CSV 文件。 

## <a name="back-up-your-trend-charts-from-the-azure-portal"></a>备份来自 Azure 门户的趋势图表

你在 Azure 门户视图中的一些趋势图表将重置。 可以通过在“图表”中运行以下脚本来备份这些图表：   

### <a name="terms--conditions-acceptance-reports"></a>条款和条件接受报表
1. 在 Azure 门户中，导航到“Microsoft Intune” -> “设备注册” -> “条款和条件”。
2. 对于每个“条款和条件”条目，请选择“接受报表”，然后选择“导出”。
3. 将报表保存在本地。
 
### <a name="app-protection-reports"></a>应用保护报表  
1. 在 Azure 门户中，导航到“Microsoft Intune” -> “移动应用” -> “应用保护状态”。
2. 单击下载图标 ( ⤓ ) 可保存每个报表。

### <a name="device-configuration-charts"></a>设备配置图表 
1. 在 Azure 门户中，导航到“Microsoft Intune” -> “设备配置”。
2. 使用 Microsoft [Graph 浏览器](https://developer.microsoft.com/graph/graph-explorer)下载图表后面的数据。 
    - 有关所有设备的所有设备配置配置文件的部署状态，请参阅[设备部署状态](https://graph.microsoft.com/beta/reports/deviceConfigurationDeviceActivity/content)。

    - 有关所有用户的所有设备配置配置文件的部署状态，请参阅[用户部署状态](https://graph.microsoft.com/beta/reports/deviceConfigurationUserActivity/content)。

    - 有关配置文件部署状态，请参阅[提供部署状态](https://graph.microsoft.com/beta/deviceManagement/deviceConfigurations?$select=id,displayName,lastModifiedDateTime,deviceStatusOverview&$expand=deviceStatusOverview)。
  
    > [!NOTE]
    > 必须拥有有效的身份验证令牌才能访问设备配置和部署状态信息。

## <a name="device-enrollment-charts"></a>设备注册图表
1. 在 Azure 门户中，导航到“Microsoft Intune” -> “设备注册”。
2. 使用 Microsoft [Graph 浏览器](https://developer.microsoft.com/graph/graph-explorer)下载图表后面的数据。
    - 有关注册状态，请参阅 
    - 有关本周前几个注册失败， 
    - 有关注册状态，请复制此[注册状态查询](https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentFailureTrends()/content)并将其粘贴到 [Graph 浏览器](https://developer.microsoft.com/graph/graph-explorer)中。
    - 有关本周前几个注册失败，请复制此[注册失败查询](https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentTopFailures(period=null)/content)并将其粘贴到 [Graph 浏览器](https://developer.microsoft.com/graph/graph-explorer)中。

    > [!NOTE]
    > 必须拥有有效的身份验证令牌才能访问设备注册数据。 

## <a name="after-a-data-warehouse-account-move"></a>数据仓库帐户移动后

数据仓库帐户移动后，可以在 Intune 中看到数据仓库已重置，并且你的数据现在存储在新位置。 图表和导出选项将重置，你会看到一个通知，单击此通知后会将你定向到一篇介绍为何重置图表的文章。  

## <a name="data-warehouse-move-example"></a>数据仓库移动示例 

客户 X 请求在 2018 年 1 月 6 日开始移动帐户。 响应请求后，客户将收到一个链接，用于查看详细说明他们希望备份以前的数据仓库时要采取的步骤的文档。 在 2018 年 1 月 6 日，数据仓库和它支持的图表将重置，并开始在新的数据中心中存储数据。 

## <a name="next-steps"></a>后续步骤

 - 了解 [Intune 每周新增功能](whats-new.md)。 另外，还可找到即将发生的更改、有关服务的重要说明，以及有关过去版本的信息。
 - 请参阅 [Microsoft Intune 博客](http://go.microsoft.com/fwlink/?LinkID=273882)。
