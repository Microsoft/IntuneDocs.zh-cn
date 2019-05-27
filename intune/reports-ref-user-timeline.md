---
title: 数据仓库用户实体时间线
titleSuffix: Microsoft Intune
description: 了解 Microsoft Intune 数据仓库如何表示时间线中的用户。
keywords: Intune 数据仓库
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/26/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 363D148E-688F-4830-B6DE-AB4FE3648817
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3fa483a49ad7fa44172a83f024540a75d1d881dc
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2019
ms.locfileid: "66040926"
---
# <a name="user-lifetime-representation-in-the-microsoft-intune-data-warehouse"></a>使用 Microsoft Intune 数据仓库中的生存期表示形式

可以使用存储在 Intune 数据仓库中的数据快照月份来回答有关时间-趋势的问题。 例如，可以查看近一个月所添加的用户数。 你还可能会提出有关已从系统中删除的用户数的问题。

为了提供此类型信息，数据仓库存储了历史信息。 数据仓库可跟踪实体的生存期。 数据仓库记录实体的创建时间、实体状态的更改时间以及实体的删除时间。 有了通过定量度量的每日快照捕获的历史记录，可以将今天与昨天相比较，依次类推。

由于实体状态不断更改，使用实体生存期可能会引起混淆。 这意味着如果你在第 30 天查看快照，在数据中用户记录可能已不是有效状态。 在第 29-28 天，实体记录可能处于有效状态。 然后在第 28 天之前，用户根本不存在。

如果浏览实体的整个生存期，这种情况可能就更为明显。

假定用户 John Smith 在 2017 年 6 月 1 日分配了许可证，那么“用户”表将具有以下条目： 
 
| DisplayName | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| John Smith | FALSE | 06/01/2017 | 12/31/9999 | TRUE
 
John Smith 在 2017 年 7 月 25 日放弃其许可证。 “用户”表具有以下条目。 现有记录中的更改是 `marked`。 

| DisplayName | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| John Smith | FALSE | 06/01/2017 | `07/26/2017` | `FALSE` 
| John Smith | TRUE | 07/26/2017 | 12/31/9999 | TRUE 

第一行指明 John Smith 从 2017 年 6 月 1 日到 2017 年 7 月 25 日存在于 Intune。 第二个记录指明该用户已于 2017 年 7 月 25 日删除并且不存在于 Intune 中。

现在假定用户 John Smith 在 2017 年 8 月 31 日获得一个新许可证，那么“用户”表将具有以下条目：
 
| DisplayName | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| John Smith | FALSE | 06/01/2017 | 07/26/2017 | FALSE 
| John Smith | TRUE | 07/26/2017 | `08/31/2017` | `FALSE` 
| John Smith | FALSE | 08/31/2017 | 12/31/9999 | TRUE 
 
想要查看所有用户的当前状态的人员希望应用筛选器 `IsCurrent = TRUE`。 
 
想要仅查看现有用户的人员希望应用筛选器 `IsCurrent = TRUE AND IsDeleted = FALSE`。

## <a name="dimension-tables-in-the-entity-lifetime"></a>实体生存期的维度表

若要在实体中存储状态更改的历史记录，Intune 不会删除记录， 而是会将记录标记为已删除。 这称为软删除。 维度表使用各种元数据列来跟踪记录的生存期。 

最常使用的元数据列包括： 

| 元数据属性名称  | 值的解释 |
|--|--|
| IsDeleted | 指明是否已在 Intune 中删除该实体。 |
| StartDateInclusiveUTC  | 将实体加载到 Intune 数据仓库中的 UTC 日期。 在将实体导入 Intune 数据仓库之前可能已创建该实体。 |
| DeletedDateUTC  | 在 Intune 中删除该实体的 UTC 日期。 |  

任何前缀为 Row 的元数据列，例如 RowLastModifiedDateTimeUTC，指明在 Intune 数据仓库中创建或修改记录的时间。 仓库在 Intune 数据的下游。 该值与 Intune 中实体的生存期无关。  
 
任何想要仅查看当前存在的维度实体的人员都希望应用筛选器 **IsDeleted = FALSE**。

## <a name="next-steps"></a>后续步骤

 - 要了解有关 Current User 实体的详细信息，请参阅 [current user 实体参考](reports-ref-current-user.md)。
 - 要了解有关 User 实体的详细信息，请参阅 [User 实体参考](reports-ref-user.md)。
