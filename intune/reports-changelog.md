---
title: "Intune 数据仓库更改日志 | Microsoft Docs"
description: "Intune 数据仓库 API 中的更改列表。"
keywords: "Intune 数据仓库"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b81846c2e45f968184d50d2ea7c50aabb86b4964
ms.sourcegitcommit: e9f9fccccef691333143b7523d1b325ee7d1915a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2017
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Intune 数据仓库 API 的更改日志

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

随时了解 Intune 数据仓库的更新。

## <a name="1710"></a>1710
发布于 2017 年 10 月

### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>用户实体包含数据仓库数据模型中的最新用户数据 <!-- 1544273 -->

Intune 数据库仓库数据模型的第一个版本只包含 Intune 的最近历史数据。 报表制作者无法捕获用户的当前状态。 在此更新中，[用户实体](reports-ref-user.md)将包含最新用户数据。

### <a name="new-entity-in-the-in-data-warehouse-data-model----1479526---"></a>Intune 数据库仓库数据模型中的新实体 <!-- 1479526 -->

添加了实体 [UserDeviceAssociation](reports-ref-user-device.md)。 UserDeviceAssociation 包含组织中的用户设备关联。

## <a name="next-steps"></a>后续步骤
 - 了解 [Intune 每周新增功能](whats-new.md)。 另外，还可找到即将发生的更改、有关服务的重要说明，以及有关过去版本的信息。 
 - 请参阅 [Microsoft Intune 博客](http://go.microsoft.com/fwlink/?LinkID=273882)。