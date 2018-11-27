---
title: Microsoft Intune 活动的审核日志
description: 了解如何查看记录 Microsoft Intune 活动的审核日志。
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.openlocfilehash: d9ecfa44e2619e5e123c9e8af169b6a8a95ee466
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52183887"
---
# <a name="audit-logs-for-intune-activities"></a>Intune 活动的审核日志
审核日志记录了导致 Microsoft Intune 有所变化的活动。 可以创建、更新（编辑）、删除和分配操作或远程任务，并能生成可查看的审核事件。 可以查看大多数 Intune 工作负载的审核日志。 默认针对所有客户启用审核且无法禁用。 审核事件从功能发布日期 2017 年 12 月开始记录；以前的事件不可用。

## <a name="who-can-access-the-data"></a>谁可以访问数据？
拥有以下权限的用户可以查看审核日志：
- 全局管理员
- Intune 服务管理员
- 分配到拥有“审核数据  - 读取”权限的 Intune 角色的管理员

## <a name="audit-logs-for-intune-workloads"></a>Intune 工作负载的审核日志
可以查看每个 Intune 工作负载的监视组中的审核日志。  
1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 在“Intune”窗格上，选择要查看其审核日志的工作负荷，例如“设备”。
4. 在工作负载的“监视”组中，选择“审核日志”。

## <a name="review-audit-events"></a>查看审核事件
![审核日志](./media/monitor-audit-logs.png "审核日志")

审核日志的默认列表视图显示以下各项：    

- 发生日期和时间
- 发起人(参与者)
- 应用程序名称
- 活动
- 目标
- Category
- 状态

单击列表视图中的项可以查看它的所有详细信息。

![审核日志](./media/monitor-audit-log-detail.png "审核日志")

> [!Note]    
> 在审核日志详细信息中的“发起人(参与者)”部分中，可以了解谁从哪里执行了活动。 例如，如果在 Azure 门户的 Intune 中执行活动，“应用”会始终列出“Microsoft Intune 门户扩展”，“应用 ID”会始终使用相同的 GUID。 
>    
> “目标”部分可以列出已更改的多个目标和属性。  


## <a name="filter-audit-events"></a>筛选审核事件
每个工作负荷都有一个菜单项，可预筛选与窗格关联的审核事件类别。 通过单独的筛选器选项，可以更改为其他类别以及此类别的事件操作详细信息。 可以按 UPN（例如，执行操作的用户）进行搜索。 日期范围筛选器支持 24 小时、7 天或 30 天选项。 默认情况下，显示过去 30 天的审核事件。

## <a name="use-graph-api-to-retrieve-audit-events"></a>使用 Graph API 检索审核事件
若要详细了解如何使用 Graph API 检索最多一年的审核事件，请参阅[列出 auditEvents](https://developer.microsoft.com/en-us/graph/docs/api-reference/beta/api/intune_auditing_auditevent_list)。