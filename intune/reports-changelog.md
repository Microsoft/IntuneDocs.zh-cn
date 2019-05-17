---
title: Intune 数据仓库更改日志
titleSuffix: Microsoft Intune
description: 此主题提供 Microsoft Intune 数据仓库 API 的更改列表。
keywords: Intune 数据仓库
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/11/2019
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
ms.openlocfilehash: 30f315f58a905e690a43ab3c44aee783bd0ef8c9
ms.sourcegitcommit: a2cd14c30949cef17bfc6576513e7660a8015669
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/15/2019
ms.locfileid: "59571801"
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Intune 数据仓库 API 的更改日志

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

随时了解 Intune 数据仓库的更新。

## <a name="1903-part-2"></a>1903（第 2 部分）
发行日期：2019 年 4 月

### <a name="beta-changes"></a>beta 版本更改

下表列出了 Intune 数据仓库中最近删除的集合和替换集合。

|    收集                          |    “更改”     |    其他信息                                                                                                                                                                                                                                                                                                                                                                 |
|----------------------------------------|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    mobileAppDeviceUserInstallStatus    |    已删除    |    请改用 [mobileAppInstallStatusCounts](intune-data-warehouse-collections.md#mobileappinstallstatuscounts)。                                                                                                                                                                                                                                                                     |
|    enrollmentTypes                     |    已删除    |    请改用 [deviceEnrollmentTypes](intune-data-warehouse-collections.md#deviceenrollmenttypes)。                                                                                                                                                                                                                                                                                      |
|    mdmStatuses                         |    已删除    |    请改用 [complianceStates](intune-data-warehouse-collections.md#compliancestates)。                                                                                                                                                                                                                                                                                               |
|    workPlaceJoinStateTypes             |    已删除    |    请改用 [devices](intune-data-warehouse-collections.md#devices) 和 [devicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories) 集合中的 `azureAdRegistered` 属性。                                                                                                                                                                                                             |
|    clientRegistrationStateTypes        |    已删除    |    请改用 [deviceRegistrationStates](intune-data-warehouse-collections.md#deviceregistrationstates)。                                                                                                                                                                                                                                                                             |
|    currentUser                         |    已删除    |    请改用 [users](intune-data-warehouse-collections.md#users) 集合。                                                                                                                                                                                                                                                                                                      |
|    mdmDeviceInventoryHistories         |    已删除    |    许多属性都是冗余的，或者现在可在 [devicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories) 或 [devices](intune-data-warehouse-collections.md#devices) 集合中找到。 这两个集合中未列出的所有 mdmDeviceInventoryHistories 属性都不再可用。 请查看下面的详细信息。    |

下表列出了以前在 mdmDeviceInventoryHistories 集合中找到的旧属性以及 change/replacement。 已删除 mdmDeviceInventoryHistories 中未在下面列出的所有属性。

|    旧属性                |    Change/replacement                                                           |
|--------------------------------|---------------------------------------------------------------------------------|
|    cellularTechnology          |    devices 集合中的 cellularTechnology                                     |
|    deviceClientId              |    devices 集合中的 deviceId                                               |
|    deviceManufacturer          |    devices 集合中的制造商                                           |
|    deviceModel                 |    devices 集合中的模型                                                  |
|    deviceName                  |    devices 集合中的 deviceName                                             |
|    deviceOsPlatform            |    devices 集合中的 deviceTypeKey                                          |
|    deviceOsVersion             |    devicePropertyHistories 集合中的 osVersion                              |
|    deviceType                  |    devices 集合中的 deviceTypeKey，引用 deviceTypes 集合    |
|    encryptionState             |    devices 集合中的 encryptionState 属性                           |
|    exchangeActiveSyncId        |    devices 集合中的 easDeviceId 属性                               |
|    exchangeDeviceId            |    devices 集合中的 easDeviceId                                            |
|    imei                        |    devices 集合中的 imei                                                   |
|    isSupervised                |    devices 集合中的 isSupervised 属性                              |
|    jailBroken                  |    devicePropertyHistories 集合中的 jailBroken                             |
|    meid                        |    devices 集合中的 meid 属性                                      |
|    oem                         |    devices 集合中的制造商                                           |
|    osName                      |    devices 集合中的 deviceTypeKey，引用 deviceTypes 集合    |
|    phoneNumber                 |    devices 集合中的 phoneNumber                                            |
|    platformType                |    devices 集合中的模型                                                  |
|    product                     |    devices 集合中的 deviceTypeKey                                          |
|    productVersion              |    devicePropertyHistories 集合中的 osVersion                              |
|    serialNumber                |    设备集合中的 serialNumber                                           |
|    storageFree                 |    devices 集合中的 freeStorageSpaceInBytes 属性                   |
|    storageTotal                |    devices 集合中的 totalStorageSpaceInBytes 属性                |
|    subscriberCarrierNetwork    |    devices 集合中的 subscriberCarrier 属性                         |
|    wifimac                     |    devices 集合中的 wiFiMacAddress                                         |

下表列出了 [devicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories) 集合中找到的属性更改： 

|    旧属性                  |    Change/replacement                                               |
|----------------------------------|---------------------------------------------------------------------|
|    categoryId                    |    deviceCategoryKey，可引用 deviceCategories 集合       |
|    certExpirationDate            |    已删除                                                          |
|    clientRegistrationStateKey    |    deviceRegistrationStateKey                                       |
|    createdDate                   |    devices 集合中的 enrolledDateTime                           |
|    deviceTypeKey                 |    devices 集合中的 deviceTypeKey                              |
|    easID                         |    devices 集合中的 easDeviceId                                |
|    enrolledByUser                |    devices 集合中的 userId                                     |
|    enrollmentTypeKey             |    devices 集合中的 deviceEnrollmentTypeKey                    |
|    graphDeviceIsCompliant        |    已删除                                                          |
|    graphDeviceIsManaged          |    已删除                                                          |
|    lastContact                   |    devices 集合中的 lastSyncDateTime                           |
|    lastContactNotification       |    已删除                                                          |
|    lastContactWorkplaceJoin      |    已删除                                                          |
|    lastExchangeStatusUtc         |    已删除                                                          |
|    lastModifiedDateTimeUTC       |    已删除                                                          |
|    lastPolicyUpdateUtc           |    已删除                                                          |
|    managementAgentKey            |    managementStateKey                                               |
|    制造商                  |    devices 集合中的 manufacturer                               |
|    mdmStatusKey                  |    complianceStateKey，可引用 complianceStates 集合    |
|    model                         |    devices 集合中的模型                                      |
|    osFamily                      |    devices 集合中的 operatingSystem                            |
|    osRevisionNumber              |    devices 集合中的 osVersion                                  |
|    processorArchitecture         |    已删除                                                          |
|    referenceId                   |    devices 集合中的 azureAdDeviceId                            |
|    serialNumber                  |    devices 集合中的 serialNumber                               |
|    workplaceJoinStateKey         |    azureAdRegistered                                                |

下表列出了 [devices](intune-data-warehouse-collections.md#devices) 集合中找到的属性更改： 

|    旧属性                  |    Change/replacement                                               |
|----------------------------------|---------------------------------------------------------------------|
|    categoryId                    |    deviceCategoryKey，可引用 deviceCategories 集合       |
|    certExpirationDate            |    已删除                                                          |
|    clientRegistrationStateKey    |    deviceRegistrationStateKey                                       |
|    createdDate                   |    enrolledDateTime                                                 |
|    easId                         |    easDeviceId                                                      |
|    enrolledByUser                |    userId                                                           |
|    enrollmentTypeKey             |    deviceEnrollmentTypeKey                                          |
|    graphDeviceIsCompliant        |    已删除                                                          |
|    graphDeviceIsManaged          |    已删除                                                          |
|    lastContact                   |    lastSyncDateTime                                                 |
|    lastContactNotification       |    已删除                                                          |
|    lastContactWorkplaceJoin      |    已删除                                                          |
|    lastExchangeStatusUtc         |    已删除                                                          |
|    lastPolicyUpdateUtc           |    已删除                                                          |
|    mdmStatusKey                  |    complianceStateKey，可引用 complianceStates 集合    |
|    osFamily                      |    operatingSystem                                                  |
|    processorArchitecture         |    已删除                                                          |
|    referenceId                   |    azureAdDeviceId                                                  |
|    workplaceJoinStateKey         |    azureAdRegistered                                                |

下表列出了 [enrollmentActivities](intune-data-warehouse-collections.md#enrollmentactivities) 集合中找到的属性更改： 

|    旧属性         |    Change/replacement         |
|-------------------------|-------------------------------|
|    enrollmentTypeKey    |    deviceEnrollmentTypeKey    |

下表列出了 [mamApplications](intune-data-warehouse-collections.md#mamapplications) 集合中找到的属性更改： 

|    旧属性       |    Change/replacement    |
|-----------------------|--------------------------|
|    applicationKey     |    mamApplicationKey     |
|    applicationName    |    mamApplicationName    |
|    applicationId      |    mamApplicationId      |

下表列出了 [mamApplicationInstances](intune-data-warehouse-collections.md#mamapplicationinstances) 集合中找到的属性更改： 

|    旧属性     |    Change/replacement    |
|---------------------|--------------------------|
|    applicationId    |    mamApplicationId      |
|    deviceId         |    mamDeviceId           |
|    deviceType       |    mamDeviceType         |
|    deviceName       |    mamDeviceName         |

下表列出了 [mamCheckins](intune-data-warehouse-collections.md#mamcheckins) 集合中找到的属性更改： 

|    旧属性      |    Change/replacement    |
|----------------------|--------------------------|
|    applicationKey    |    mamApplicationKey     |

下表列出了 [users](intune-data-warehouse-collections.md#users) 集合中找到的属性更改： 

|    旧属性             |    Change/replacement    |
|-----------------------------|--------------------------|
|    startDateInclusiveUtc    |    已删除               |
|    endDateInclusiveUtc      |    已删除               |
|    isCurrent                |    已删除               |

## <a name="1903"></a>1903
发行时间：2019 年 3 月

### <a name="v10-changes-reflecting-back-to-beta"></a>V1.0 更改在 beta 版本中体现
V1.0 在 1808 版本首次引入后，它在某些重要方面与 beta 版 API 有所不同。 在 1903 版本中，这些更改将在 beta 版 API 中体现。 如果有使用 beta 版 API 的重要报表，我们强烈建议将这些报表切换到 V1.0 以避免中断性变更。 要详细了解数据仓库 API 版本和后向兼容性，请参阅 [API 版本信息](reports-api-url.md)。 

## <a name="1902"></a>1902 
发布时间：2019 年 2 月

### <a name="power-bi-compliance-app"></a>Power BI 合规性应用 

使用 [Intune 合规性（数据仓库）](https://app.powerbi.com/groups/me/getapps/services/Intune_dw_compliance)应用访问 Power BI Online 中的 Intune 数据仓库。 使用此 Power BI 应用，可立即访问和共享预创建的报表，无需任何设置，也无需离开 Web 浏览器。 

> [!NOTE]
> 可将两个附加筛选器应用于 Intune Compliance 应用。

#### <a name="add-additional-filters-to-the-intune-compliance-app"></a>将附加筛选器添加到 Intune Compliance 应用
1. 在 Web 浏览器中打开 [Intune Compliance（数据仓库）](https://app.powerbi.com/groups/me/getapps/services/Intune_dw_compliance)应用。
2. 在“complianceStatus”筛选器中单击“不符合设备”并选择“不符合”。 
3. 在“complianceStatus”筛选器中单击“未知设备”并选择“尚未提供”。 

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
