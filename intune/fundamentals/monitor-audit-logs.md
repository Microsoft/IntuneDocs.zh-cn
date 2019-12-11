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
ms.openlocfilehash: d6af0718f2b926383bb943b6321b4d5839346ce7
ms.sourcegitcommit: df8e2c052fafb2d5d4e9b4fcd831ae0ecf7f8d16
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991993"
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

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择 "**租户管理** > **审核日志**"。
3. 若要筛选结果，请选择 "**筛选**" 并使用以下选项优化结果。
    - **类别**：例如**符合性**、**设备**和**角色**。
    - **活动**：此处列出的选项受 "**类别**" 下选择的选项限制。
    - **日期范围**：可以选择上个月、周或日的日志。
4. 选择“应用”  。
4. 在列表中选择一项以查看活动详细信息。

## <a name="route-logs-to-azure-monitor"></a>将日志路由到 Azure Monitor

审核日志和运行日志也可路由到 Azure Monitor。 在“审核日志”中，选择“导出数据设置”   ：

![通过在 Intune 中选择“导出数据”设置，将日志数据导出到 Azure Monitor](./media/monitor-audit-logs/audit-logs-export-data-settings.png)

> [!NOTE]
> 有关此功能的详细信息以及若要查看使用该功能的先决条件，请参阅[将日志数据发送到存储、事件中心或 log analytics](review-logs-using-azure-monitor.md)。

> [!NOTE]
> 发起人（参与者）显示了谁在何处运行了此任务  。 例如，如果在 Azure 门户的 Intune 中运行活动，“应用”  会始终列出“Microsoft Intune 门户扩展”  ，“应用 ID”  会始终使用相同的 GUID。
>
> “目标”  部分将列出已更改的多个目标和属性。  

## <a name="use-graph-api-to-retrieve-audit-events"></a>使用 Graph API 检索审核事件

要详细了解如何使用图形 API 获取长达 1 年的审核事件，请参阅[列出 auditEvents](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0)。

## <a name="next-steps"></a>后续步骤

[将日志数据发送到存储、事件中心或日志分析](review-logs-using-azure-monitor.md)。

[查看客户端应用保护日志](../apps/app-protection-policy-settings-log.md)。
