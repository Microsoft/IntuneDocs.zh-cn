---
title: 用户 - Intune 数据仓库
titleSuffix: Microsoft Intune
description: Intune 数据仓库 API 中实体集合的“用户”类别的参考主题。
keywords: Intune 数据仓库
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/03/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: C29A6EEA-72B7-427E-9601-E05B408F3BB0
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 202d9e53ff21e5677a212012d37b0e909cc8c562
ms.sourcegitcommit: 8d7406b75ef0d75cc2ed03b1a5e5f74ff10b98c0
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2020
ms.locfileid: "75654084"
---
# <a name="reference-for-user-entity"></a>用户实体引用

Users  类别包含定义数据模型中用户属性的 user  实体。

## <a name="users"></a>用户

用户  实体列出了企业中分配有许可证的所有 Azure Active Directory (Azure AD) 用户。

用户  实体集合包含用户数据。 这些记录包含数据收集期间的用户状态（即使用户已被删除）。 例如，在上个月期间，可能将某个用户添加到 Intune 然后又将其删除。 尽管在提交报告时该用户已不存在，但在上个月的数据中仍然会显示该用户及其状态。 可以创建一个报告，该报告将显示用户的历史记录在你的数据中存在的持续时间。

|          属性          |                                                                                                           说明                                                                                                          |                示例               |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------:|
| userKey                    | 数据仓库中用户的唯一标识符 - 代理键。                                                                                                                                                         | 123                                  |
| userId                     | 用户的唯一标识符 - 类似于 UserKey，但该标识符是自然键。                                                                                                                                                    | b66bc706-ffff-7437-0340-032819502773 |
| userEmail                  | 用户的电子邮件地址。                                                                                                                                                                                                     | John@constoso.com                    |
| userPrincipalName                        | 用户的用户主体名称。                                                                                                                                                                                               | John@constoso.com                    |
| displayName                | 用户的显示名称。                                                                                                                                                                                                      | John                                 |
| intuneLicensed             | 指定此用户是否获得 Intune 许可。                                                                                                                                                                              | True/False                           |
| isDeleted                  | 指示是否所有用户的许可证都已过期，以及是否因此将用户从 Intune 中删除。 对于单个记录，此标志不会更改。 相反，将为新用户状态创建新记录。 | True/False                           |
| RowLastModifiedDateTimeUTC | 上次在数据仓库中修改记录时的 UTC 日期和时间                                                                                                                                                 | 2016/11/23 0:00                      |


## <a name="next-steps"></a>后续步骤
- 可以使用“当前用户”  实体集合将用户数据限制为当前活动的用户。 有关详细信息，请参阅[引用当前用户实体](../reports-ref-current-user.md)。
- 要了解有关数据仓库如何在 Intune 中跟踪用户生存期的详细信息，请参阅 [Intune 数据仓库中的用户生存期表示](reports-ref-user-timeline.md)。
