---
title: "用户 - Intune 数据仓库 | Microsoft Docs"
description: "Intune 数据仓库 API 中实体集合的“用户”类别的参考主题。"
keywords: "Intune 数据仓库"
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 12/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: C29A6EEA-72B7-427E-9601-E05B408F3BB0
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1f213cb735ab4dcad20c97b5924fef98774192ce
ms.sourcegitcommit: d44c32aad3e84f6c0b296bdb010981d3a818befb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2018
---
# <a name="reference-for-user-entity"></a>用户实体引用

User 类别包含定义数据模型中用户属性的 User 实体。

## <a name="user"></a>用户

用户实体列出了企业中分配有许可证的所有 Azure Active Directory (Azure AD) 用户。

User 实体集合包含用户数据。 这些记录包含数据收集期间的用户状态（即使用户已被删除）。 例如，在上个月期间，可能将某个用户添加到 Intune 然后又将其删除。 尽管在提交报告时该用户已不存在，但在上个月的数据中仍然会显示该用户及其状态。 可以创建一个报告，该报告将显示用户的历史记录在你的数据中存在的持续时间。

| 属性  | 描述 | 示例 |
|---------|------------|--------|
| UserKey |数据仓库中用户的唯一标识符 - 代理键。 |123 |
| UserId |用户的唯一标识符 - 类似于 UserKey，但该标识符是自然键。 |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |用户的电子邮件地址。 |John@constoso.com |
| UPN | 用户的用户主体名称。 | John@constoso.com |
| DisplayName |用户的显示名称。 |John |
| IntuneLicensed |指定此用户是否获得 Intune 许可。 |True/False |
| IsDeleted | 指示是否所有用户的许可证都已过期，以及是否因此将用户从 Intune 中删除。 对于单个记录，此标志不会更改。 相反，将为新用户状态创建新记录。 |True/False |
| StartDateInclusiveUTC |如果 IsDeleted = FALSE，用户分配了许可证并开始在 Intune 中显示时的 UTC 日期时间。 如果 IsDeleted = TRUE，当用户的许可证过期并从 Intune 中被删除时的 UTC 日期时间。 |2016/11/23 - 中午 12:00:00 |
| EndDateExclusiveUTC |如果 IsDeleted = FALSE，当用户的许可证过期并从 Intune 中被删除时的 UTC 日期时间。 许可证在前一天的某个时间过期。 如果 IsDeleted = TRUE，当用户重新获得了新的许可证并在 Intune 中被重新创建时的 UTC 日期时间。  |2016/11/23 - 中午 12:00:00 |
| IsCurrent |指示该记录是否表示用户的最新状态。 单个用户可能具有多条记录，但其中只有一条记录表示当前状态。  |True/False |
| RowLastModifiedDateTimeUTC |上次在数据仓库中修改记录时的 UTC 日期和时间  |2016/11/23 - 中午 12:00:00 |

## <a name="next-steps"></a>后续步骤
 - 可以使用“当前用户”实体集合将用户数据限制为当前活动的用户。 有关详细信息，请参阅[引用当前用户实体](reports-ref-current-user.md)。
 - 若要了解有关数据仓库如何在 Intune 中跟踪用户生存期的详细信息，请参阅 [Intune 数据仓库中的用户生存期表示](reports-ref-user-timeline.md)。
