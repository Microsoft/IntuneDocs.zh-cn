---
title: Intune 数据仓库更改日志
titlesuffix: Microsoft Intune
description: Intune 数据仓库 API 中的更改列表。
keywords: Intune 数据仓库
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: dd9fb36bb1b8c5e66d104f530690c5d236ea25e4
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34223690"
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Intune 数据仓库 API 的更改日志

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

随时了解 Intune 数据仓库的更新。

## <a name="1805"></a>1805
发行时间：2018 年 5 月

### <a name="correction-to-device-count-in-devices-collection"></a>更正“设备”集合中的设备计数 

已对“设备”集合进行修复，可能会降低 `isDeleted` 属性筛选的总设备计数。 此下降是更正的结果，而非错误。 有关“设备”集合的详细信息，请参阅[设备实体引用](reports-ref-devices.md)。 


## <a name="1801"></a>1801
2018 年 1 月发布

### <a name="intune-data-warehouse-application-only-authentication----1867540---"></a>Intune 数据仓库仅应用程序身份验证 <!-- 1867540 -->

你可以使用 Azure Active Directory (Azure AD) 设置应用程序并通过 Intune 数据仓库进行身份验证。 有关详细信息，请参阅 [Intune 数据仓库仅应用程序身份验证](data-warehouse-app-only-auth.md)。

### <a name="azure-ad-and-intune-credential-requirements----2077525---"></a>Azure AD 和 Intune 凭据要求 <!-- 2077525 -->

- 在访问 Intune 数据仓库（包括 API）时，不再需要向用户分配 Intune 许可证。
- Intune 角色名称已从“报表”更改为“Intune 数据仓库”。 

    有关详细信息，请参阅 [Azure AD 和 Intune 凭据要求](reports-api-url.md#azure-ad-and-intune-credential-requirements)。

### <a name="odata-query-options----2077711---"></a>OData 查询选项 <!-- 2077711 -->

可以使用 <code>$select</code> 作为 OData 查询参数。 当前版本支持以下 OData 查询参数：<code>$filter</code>、<code>$orderby</code>、<code>$select</code>、<code>$skip</code> 和 <code>$top</code>。 有关详细信息，请参阅 [OData 查询选项](reports-api-url.md#odata-query-options)。

### <a name="new-entities-in-the-in-data-warehouse-data-model----2077804---"></a>数据仓库数据模型中的新实体 <!-- 2077804 -->

 - 已添加实体 [MobileAppDeviceuserInstallStatus](reports-ref-application.md#mobileappdeviceuserinstallstatus)。 MobileAppDeviceUserInstallStatus 表示给定设备和用户的移动应用安装状态。
 - 已添加实体 [MobileAppInstallState](reports-ref-application.md#mobileappinstallstate)。 MobileAppInstallState 实体表示已分配到包含设备和/或用户的组的移动应用程序的安装状态。 

## <a name="1710"></a>1710
发布于 2017 年 11 月

### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1544273---"></a>名为“当前用户”的新实体集合仅限于当前活动的用户数据<!-- 1544273 -->

User 实体集合包含企业中分配有许可证的所有 Azure Active Directory (Azure AD) 用户。 这些记录包含数据收集期间的用户状态（即使用户已被删除）。 例如，在上个月期间，可能将某个用户添加到 Intune 然后又将其删除。 尽管在提交报告时该用户已不存在，但在数据中仍然会显示该用户及其状态。 可以创建一个报告，该报告将显示用户的历史记录在你的数据中存在的持续时间。

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
