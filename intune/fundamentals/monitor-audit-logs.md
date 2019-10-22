---
title: 审核 Microsoft Intune 中的更改和事件 - Azure | Microsoft Docs
description: 了解如何查看记录 Microsoft Intune 活动的审核日志。
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 03/18/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: fd00a0ae4cb6c3b150fe40cfc6cd7b71cfa973f3
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585249"
---
# <a name="use-audit-logs-to-track-and-monitor-events-in-microsoft-intune"></a>使用审核日志跟踪和监视 Microsoft Intune 中的事件

审核日志包括导致 Microsoft Intune 有所变化的活动。 对大多数 Intune 工作负载而言，创建、更新（编辑）、删除、分配和远程操作均可创建能供管理员查看的审核事件。 默认为所有客户启用审核功能。 该功能无法禁用。

> [!NOTE]
> 审核事件自 2017 年 12 月的功能版本起开始记录。 不提供在此之前的事件。

## <a name="who-can-access-the-data"></a>谁可以访问数据？

拥有以下权限的用户可以查看审核日志：

- 全局管理员
- Intune 服务管理员
- 分配到拥有“审核数据   - 读取”  权限的 Intune 角色的管理员

## <a name="audit-logs-for-intune-workloads"></a>Intune 工作负载的审核日志

可以查看每个 Intune 工作负载的监视组中的审核日志：

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择要查看其审核日志的工作负载。 例如，选择“设备”  。
3. 在“监视”下，选择“审核日志”   。

## <a name="route-logs-to-azure-monitor"></a>将日志路由到 Azure Monitor

审核日志和运行日志也可路由到 Azure Monitor。 在“审核日志”中，选择“导出数据设置”   ：

![通过在 Intune 中选择“导出数据”设置，将日志数据导出到 Azure Monitor](./media/monitor-audit-logs/audit-logs-export-data-settings.png)

> [!NOTE]
> 有关此功能的详细信息以及若要查看使用该功能的先决条件，请参阅[将日志数据发送到存储、事件中心或 log analytics](review-logs-using-azure-monitor.md)。

## <a name="review-audit-events"></a>查看审核事件

![在 Intune 中选择审核日志以查看事件日期及采取的操作](./media/monitor-audit-logs/monitor-audit-logs.png "审核日志")

审核日志的默认列表视图显示以下各项：

- 发生日期和时间
- 发起人(参与者)
- 应用程序名称
- 活动
- 目标
- Category
- 状态

要查看更具体的事件信息，请在列表中选择某项：

![更具体地了解谁在 Intune 中的审计日志中执行了哪些操作](./media/monitor-audit-logs/monitor-audit-log-detail.png "|::ref2::|")

> [!NOTE]
> 发起人（参与者）显示了谁在何处运行了此任务  。 例如，如果在 Azure 门户的 Intune 中运行活动，“应用”  会始终列出“Microsoft Intune 门户扩展”  ，“应用 ID”  会始终使用相同的 GUID。
>
> “目标”  部分将列出已更改的多个目标和属性。  

## <a name="filter-audit-events"></a>筛选审核事件

每个工作负荷都有一个菜单项，可预筛选与窗格关联的审核事件类别。 通过单独的筛选器选项，可以更改为其他类别以及此类别的事件操作详细信息。 可按 UPN（例如执行操作的用户）进行搜索。 日期范围筛选器支持 24 小时、7 天或 30 天选项。 默认情况下，显示过去 30 天的审核事件。

## <a name="use-graph-api-to-retrieve-audit-events"></a>使用 Graph API 检索审核事件

要详细了解如何使用图形 API 获取长达 1 年的审核事件，请参阅[列出 auditEvents](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0)。

## <a name="next-steps"></a>后续步骤

[将日志数据发送到存储、事件中心或日志分析](review-logs-using-azure-monitor.md)。

[查看客户端应用保护日志](../apps/app-protection-policy-settings-log.md)。
