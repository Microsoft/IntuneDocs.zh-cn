---
title: 当前用户 - Intune 数据仓库
titlesuffix: Microsoft Intune
description: Intune 数据仓库 API 中实体集合的“当前用户”类别的参考主题。
keywords: Intune 数据仓库
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: C10E6752-E925-40AD-ABBF-6B621FB7AFC4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; seodec18
ms.openlocfilehash: a6329a44f1ccfa55025ad558fe2f277a41293538
ms.sourcegitcommit: 0f19bc5c76b7c0835bfd180459f2bbd128eec1c2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2018
ms.locfileid: "53266896"
---
# <a name="reference-for-current-user-entity"></a>CurrentUser 实体参考

CurrentUser 类别包含数据模型中的用户属性。 “当前用户”实体集合仅限于当前活动的用户。 该实体包含当前分配了许可证的所有 Azure Active Directory 用户。 许可证可以是 Intune 许可证、混合许可证或 Microsoft Office 365 许可证。 CurrentUser 集合中不会表示已删除的用户。 对于包含用户状态更改历史记录的集合，请参阅[用户实体引用](reports-ref-user.md)。


## <a name="current-user"></a>当前用户

CurrentUser 实体列出了企业中分配有许可证的所有 Azure Active Directory (Azure AD) 用户。

| 属性  | 描述 | 示例 |
|---------|------------|--------|
| UserKey |数据仓库中用户的唯一标识符 - 代理键。 |123 |
| UserId |用户的唯一标识符 - 类似于 UserKey，但该标识符是自然键。 |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |用户的电子邮件地址。 |John@constoso.com |
| UPN | 用户的用户主体名称。 | John@constoso.com |
| DisplayName |用户的显示名称。 |John |
| IntuneLicensed |指定此用户是否获得 Intune 许可。 |True/False |
| StartDateInclusiveUTC |在数据仓库中创建此用户时的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |
| RowLastModifiedDateTimeUTC |上次在数据仓库中修改此用户时的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |

## <a name="next-steps"></a>后续步骤
 - 可以使用 User 实体集合将用户数据扩展为包含当前不活跃的用户。 有关详细信息，请参阅[用户实体引用](reports-ref-user.md)。
 - 要了解有关数据仓库如何在 Intune 中跟踪用户生存期的详细信息，请参阅 [Intune 数据仓库中的用户生存期表示](reports-ref-user-timeline.md)。
