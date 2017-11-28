---
title: "用户 - Intune 数据仓库 | Microsoft Docs"
description: "Intune 数据仓库 API 中实体集合的“用户”类别的参考主题。"
keywords: "Intune 数据仓库"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 11/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: C10E6752-E925-40AD-ABBF-6B621FB7AFC4
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6f321a3a9ac09c004639a3db15df280fbdb5be3c
ms.sourcegitcommit: d26930f45ba9e6292a49bcb08defb5b3f14b704b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2017
---
# <a name="reference-for-current-user-entity"></a>当前用户实体引用

“当前用户”类别包含数据模型中的用户和代理属性。 “当前用户”实体集合仅限于当前活动的用户。 该实体包含当前分配了许可证的所有 Azure Active Directory 用户。 许可证可以是 Intune 许可证、混合许可证或 Microsoft Office 365 许可证。 如果用户已被删除，则不会在数据收集期间显示它们。 对于包含用户状态更改历史记录的集合，请参阅[用户实体引用](reports-ref-user.md)。


## <a name="user"></a>用户

用户实体列出了企业中分配有许可证的所有 Azure Active Directory (Azure AD) 用户。

| 属性  | 说明 | 示例 |
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
 - 你可以使用“用户”实体集合将用户数据扩展到当前不活动的用户。 有关详细信息，请参阅[用户实体引用](reports-ref-user.md)。 
 - 要了解有关数据仓库如何在 Intune 中跟踪用户生存期的详细信息，请参阅 [Intune 数据仓库中的用户生存期表示](reports-ref-user-timeline.md)。