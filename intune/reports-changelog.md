---
title: "Intune 数据仓库更改日志 | Microsoft Docs"
description: "Intune 数据仓库 API 中的更改列表。"
keywords: "Intune 数据仓库"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 11/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7269d0552a0c01e4702eaae861d6c24f3f4f6f02
ms.sourcegitcommit: d26930f45ba9e6292a49bcb08defb5b3f14b704b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2017
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Intune 数据仓库 API 的更改日志

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

随时了解 Intune 数据仓库的更新。

## <a name="1710"></a>1710
发布于 2017 年 11 月

### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1544273---"></a>名为“当前用户”的新实体集合仅限于当前活动的用户数据<!-- 1544273 -->

“用户”实体集合包含自上个月的数据。 这些记录包含数据收集期间的用户状态（即使用户已被删除）。 例如，在上个月期间，可能将某个用户添加到 Intune 然后又将其删除。 尽管在提交报告时该用户已不存在，但在数据中仍然会显示该用户及其状态。 可以创建一个报告，该报告将显示用户的历史记录在你的数据中存在的持续时间。

相比之下，新的“当前用户”实体集合只包含尚未被删除的用户。 “当前用户”实体集合仅包含当前活动的用户。 有关“当前用户”实体集合的信息，请参阅[引用当前用户实体](reports-ref-current-user.md)。

## <a name="1709"></a>1709
发布于 2017 年 10 月

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>用户设备关联实体集合被添加到 Intune 数据仓库数据模型 <!-- 1187917 -->

现在可使用用户设备关联信息（该信息将用户和设备实体集合相关联）生成报表和数据可视化效果。 可通过从“数据仓库 Intune”页检索到的 Power BI 文件 (PBIX)、通过 OData 终结点或通过开发自定义客户端，访问数据模型。 有关详细信息，请参阅[用户设备关联](reports-ref-user-device.md)。

### <a name="new-entities-in-the-in-data-warehouse-data-model----1479526--------"></a>数据库仓库数据模型中的新实体 <!-- 1479526 --><!-- -->

 - 添加了实体 [UserDeviceAssociation](reports-ref-user-device.md)。 UserDeviceAssociation 包含组织中的用户设备关联。 现在可使用用户设备关联信息（该信息将用户和设备实体集合相关联）生成报表和数据可视化效果。  
 - 添加了 [IntuneManagementExtension](reports-ref-intunemanagementextension.md) 实体。 IntuneManagementExtension 包含移动设备的实体，可用于跟踪版本和安装状态等信息。

## <a name="next-steps"></a>后续步骤
 - 了解 [Intune 每周新增功能](whats-new.md)。 另外，还可找到即将发生的更改、有关服务的重要说明，以及有关过去版本的信息。 
 - 请参阅 [Microsoft Intune 博客](http://go.microsoft.com/fwlink/?LinkID=273882)。