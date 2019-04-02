---
title: 审核更改和 Microsoft Intune-Azure 中的事件 |Microsoft Docs
description: 了解如何查看记录 Microsoft Intune 活动的审核日志。
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 03/18/2019
ms.topic: troubleshooting
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 93072ba4730de0252f54d93fa1169062d496ce38
ms.sourcegitcommit: 1069b3b1ed593c94af725300aafd52610c7d8f04
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2019
ms.locfileid: "58394895"
---
# <a name="use-audit-logs-to-track-and-monitor-events-in-microsoft-intune"></a>使用审核日志来跟踪和监视在 Microsoft Intune 中的事件

审核日志包括导致 Microsoft Intune 有所变化的活动。 创建、 更新 （编辑）、 删除、 分配和远程操作所有创建的管理员可以查看大多数 Intune 工作负载的审核事件。 默认情况下，为所有客户启用审核。 无法禁用它。

> [!NOTE]
> 审核事件上 2017 年 12 月功能版本启动录制。 以前的事件不可用。

## <a name="who-can-access-the-data"></a>谁可以访问数据？

拥有以下权限的用户可以查看审核日志：

- 全局管理员
- Intune 服务管理员
- 分配到拥有“审核数据  - 读取”权限的 Intune 角色的管理员

## <a name="audit-logs-for-intune-workloads"></a>Intune 工作负载的审核日志

可以查看每个 Intune 工作负载的监视组中的审核日志：

1. 在 [Azure 门户](https://portal.azure.com/)中，选择“所有服务”> 筛选“Intune”> 选择“Intune”。
2. 选择你想要查看的审核日志的工作负荷。 例如，选择**设备**。
3. 下**监视**，选择**审核日志**。

## <a name="route-logs-to-azure-monitor"></a>将日志路由到 Azure Monitor

审核日志和操作日志还会路由到 Azure Monitor。 在中**审核日志**，选择**导出数据设置**:

![导出到 Azure 的日志数据通过选择在 Intune 中导出数据设置的监视器](./media/audit-logs-export-data-settings.png)

有关此功能的详细信息，请参阅[将日志数据发送到存储、事件中心或 Log Analytics](review-logs-using-azure-monitor.md)。

## <a name="review-audit-events"></a>查看审核事件

![在 Intune，请参阅操作和事件发生时的日期选择审核日志](./media/monitor-audit-logs.png "审核日志")

审核日志的默认列表视图显示以下各项：

- 发生日期和时间
- 发起人(参与者)
- 应用程序名称
- 活动
- 目标
- 类别
- 状态

若要查看有关事件的更多具体信息，请在列表中选择某项：

![获取有关谁做了什么在审核日志在 Intune 中的更多特定信息](./media/monitor-audit-log-detail.png "审核日志详细信息")

> [!NOTE]
> **发起人 （参与者）** 包括运行该任务，并运行的位置的信息。 例如，如果在 Azure 门户的 Intune 中运行活动，“应用”会始终列出“Microsoft Intune 门户扩展”，“应用 ID”会始终使用相同的 GUID。
> 
> “目标”部分将列出已更改的多个目标和属性。  

## <a name="filter-audit-events"></a>筛选审核事件

每个工作负荷都有一个菜单项，可预筛选与窗格关联的审核事件类别。 通过单独的筛选器选项，可以更改为其他类别以及此类别的事件操作详细信息。 您可以搜索 UPN，例如执行该操作的用户。 日期范围筛选器支持 24 小时、7 天或 30 天选项。 默认情况下，显示过去 30 天的审核事件。

## <a name="use-graph-api-to-retrieve-audit-events"></a>使用 Graph API 检索审核事件

有关使用图形 API 以获取最多一年的审核事件的详细信息，请参阅[列出 auditEvents](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0)。

## <a name="next-steps"></a>后续步骤

[将日志数据发送到存储，事件中心或 log analytics](review-logs-using-azure-monitor.md)。

[查看客户端应用保护日志](app-protection-policy-settings-log.md)。
