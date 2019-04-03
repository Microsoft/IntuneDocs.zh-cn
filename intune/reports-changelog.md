---
title: Intune 数据仓库更改日志
titlesuffix: Microsoft Intune
description: 此主题提供 Microsoft Intune 数据仓库 API 的更改列表。
keywords: Intune 数据仓库
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/21/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: d7d69c602471e8508744f2a00008294cbd335204
ms.sourcegitcommit: 93286c22426dcb59191a99e3cf2af4ff6ff16522
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2019
ms.locfileid: "58358252"
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Intune 数据仓库 API 的更改日志

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

随时了解 Intune 数据仓库的更新。

## <a name="1903"></a>1903
发行时间：2019 年 3 月

### <a name="v10-changes-reflecting-back-to-beta"></a>V1.0 更改专用于反映将返回到 beta
V1.0 在 1808年中首次引入，它有差异在一些重要方面与 beta 版 API。 在 1903年这些更改将反映回 beta API 版本。 如果使用的测试 API 版的重要报表，我们强烈建议切换到 V1.0 以避免重大更改的那些报表。 请参阅[API 版本信息](reports-api-url.md)有关详细信息在数据仓库 API 版本和向后兼容性。 

## <a name="1902"></a>1902 
发布时间：2019 年 2 月

### <a name="power-bi-compliance-app"></a>符合性的 power BI 应用 

访问 Intune 数据仓库中使用 Power BI Online [Intune 符合性 （数据仓库）](https://app.powerbi.com/groups/me/getapps/services/Intune_dw_compliance)应用。 使用此 Power BI 应用，现在可以访问并共享预创建的报表，而无需任何设置，而无需离开你的 web 浏览器。 

> [!NOTE]
> 有两个附加的筛选器可以应用到 Intune 符合性应用程序。

#### <a name="add-additional-filters-to-the-intune-compliance-app"></a>将其他筛选器添加到 Intune 符合性应用
1. 打开[Intune 符合性 （数据仓库）](https://app.powerbi.com/groups/me/getapps/services/Intune_dw_compliance)在 web 浏览器中的应用。
2. 单击**非合规的设备**，然后选择**不符合**中**complianceStatus**筛选器。 
3. 单击**未知设备**，然后选择**尚不可用**中**complianceStatus**筛选器。 

## <a name="1812"></a>1812 
_2018 年 12 月发布_

### <a name="enrollment-activities-collection-released-to-v10"></a>发布到 v1.0 的注册活动集合 

注册活动集合现已在 v1.0 中提供。 可以使用此集合来了解环境中的注册失败量和趋势。 有关详细信息，请参阅 [enrollmentActivities](intune-data-warehouse-collections.md#enrollmentactivities)、[enrollmentEventStatuses](intune-data-warehouse-collections.md#enrollmenteventstatuses)、[enrollmentFailureCategories](intune-data-warehouse-collections.md#enrollmentfailurecategories) 和 [enrollmentFailureReasons](intune-data-warehouse-collections.md#enrollmentfailurereasons)。

## <a name="1808"></a>1808
发布于 2018 年 8 月

### <a name="v10-collections"></a>v1.0 集合  

现在可以通过设置查询参数 `api-version=v1.0` 来使用 v1.0 版的 Intune 数据仓库。 数据仓库中集合的更新本质上是附加更新，不会破坏现有方案。

### <a name="enrollment-activities-collection-released-to-beta"></a>发布到 beta 版本的注册活动集合

新的 `Enrollment Activities` 集合发布到 beta 版。 使用此集合，可以通过查看最常见的故障来了解注册过程。 


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

 - 已添加实体 [MobileAppDeviceuserInstallStatus](reports-ref-application.md)。 MobileAppDeviceUserInstallStatus 表示给定设备和用户的移动应用安装状态。
 - 已添加实体 [MobileAppInstallState](reports-ref-application.md#mobileappinstallstate)。 MobileAppInstallState 实体表示已分配到包含设备和/或用户的组的移动应用程序的安装状态。 

## <a name="1710"></a>1710
发布于 2017 年 11 月

### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1544273---"></a>名为“当前用户”的新实体集合仅限于当前活动的用户数据 <!-- 1544273 -->

User 实体集合包含企业中分配有许可证的所有 Azure Active Directory (Azure AD) 用户。 这些记录包含数据收集期间的用户状态（即使用户已被删除）。 例如，在上个月期间，可能将某个用户添加到 Intune 然后又将其删除。 尽管在提交报告时该用户已不存在，但在数据中仍然会显示该用户及其状态。 可以创建一个报告，该报告将显示用户的历史记录在你的数据中存在的持续时间。

相比之下，新的“当前用户”实体集合只包含尚未被删除的用户。 “当前用户”实体集合仅包含当前活动的用户。 有关“当前用户”实体集合的信息，请参阅[引用当前用户实体](reports-ref-current-user.md)。

## <a name="1709"></a>1709
发布于 2017 年 10 月

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>添加到 Intune 数据仓库数据模型的用户设备关联实体集合 <!-- 1187917 -->

现在可使用用户设备关联信息（该信息将用户和设备实体集合相关联）生成报表和数据可视化效果。 可通过从“数据仓库 Intune”页检索到的 Power BI 文件 (PBIX)、通过 OData 终结点或通过开发自定义客户端，访问数据模型。 有关详细信息，请参阅[用户设备关联](reports-ref-user-device.md)。

### <a name="new-entities-in-the-in-data-warehouse-data-model----1479526--------"></a>数据仓库数据模型中的新实体 <!-- 1479526 --><!-- -->

 - 添加了实体 [UserDeviceAssociation](reports-ref-user-device.md)。 UserDeviceAssociation 包含组织中的用户设备关联。 现在可使用用户设备关联信息（该信息将用户和设备实体集合相关联）生成报表和数据可视化效果。  
 - 添加了 [IntuneManagementExtension](reports-ref-intunemanagementextension.md) 实体。 IntuneManagementExtension 包含移动设备的实体，可用于跟踪版本和安装状态等信息。

## <a name="next-steps"></a>后续步骤
 - 了解 [Intune 每周新增功能](whats-new.md)。 另外，还可找到即将发生的更改、有关服务的重要说明，以及有关过去版本的信息。
 - 请参阅 [Microsoft Intune 博客](https://go.microsoft.com/fwlink/?LinkID=273882)。
