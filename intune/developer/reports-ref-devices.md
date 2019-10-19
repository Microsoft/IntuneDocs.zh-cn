---
title: 设备 - Intune 数据仓库
titleSuffix: Microsoft Intune
description: Intune 数据仓库 API 中实体集合的“设备”类别的参考主题。
keywords: Intune 数据仓库
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6955E12D-70D7-4802-AE3B-8B276F01FA4F
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 36407bda1f74d0c4601f78cedc2af5426e944fee
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503412"
---
# <a name="reference-for-devices-entities"></a>设备实体引用

“设备”类别包含移动设备的实体，可用于跟踪此类信息  ：

- 设备类型
- 设备登记和注册状态
- 设备所有权
- 设备管理状态
- 设备 Azure AD 成员身份状态
- 注册状态
- 设备的历史信息
- 设备上的应用的清单

## <a name="devicetypes"></a>deviceTypes

deviceTypes 实体表示由其他数据仓库实体引用的设备类型  。 设备类型通常描述设备型号、制造商或同时包含这两项内容。

| 属性  | 描述 |
|---------|------------|
| deviceTypeID |设备类型的唯一标识符 |
| deviceTypeKey |数据仓库中设备类型的唯一标识符 - 代理键 |
| deviceTypeName |设备类型 |

### <a name="example"></a>示例

| deviceTypeID  | 名称 | 描述 |
|---------|------------|--------|
| 0 |“桌面” |Windows 桌面设备 |
| 1 |WindowsRT |WindowsRT 设备 |
| 2 |WinMO6 |Windows Mobile 6.0 设备 |
| 3 |Nokia |Nokia 设备 |
| 4 |WindowsPhone |Windows Phone 设备 |
| 5 |Mac |Mac 设备 |
| 6 |WinCE |Windows CE 设备 |
| 7 |WinEmbedded |Windows Embedded 设备 |
| 8 |iPhone |iPhone 设备 |
| 9 |iPad |iPad 设备 |
| 10 |iPod |iPod 设备 |
| 11 |Android |使用 Device Administrator 管理的 Android 设备 |
| 12 |ISocConsumer |iSoc 使用者设备 |
| 14 |MacMDM |使用内置 MDM 代理管理的 Mac OS X 设备 |
| 15 |HoloLens |HoloLens 设备 |
| 16 |SurfaceHub |Surface Hub 设备 |
| 17 |AndroidForWork |使用 Android Profile Owner 管理的 Android 设备 |
| 100 |Blackberry |Blackberry 设备 |
| 101 |Palm |Palm 设备 |
| 255 |Unknown |未知设备类型 |

## <a name="enrollmentactivities"></a>enrollmentActivities 
enrollmentActivity 实体表示设备注册活动  。

| 属性                      | 描述                                                               |
|-------------------------------|---------------------------------------------------------------------------|
| dateKey                       | 记录此注册活动时的日期键。               |
| deviceEnrollmentTypeKey       | 注册类型的键。                                        |
| deviceTypeKey                 | 设备类型的键。                                                |
| enrollmentEventStatusKey      | 表示注册成功或失败的状态键钥。    |
| enrollmentFailureCategoryKey  | 注册失败类别的键（如果注册失败）。        |
| enrollmentFailureReasonKey    | 注册失败原因的键（如果注册失败）。          |
| osVersion                     | 设备的操作系统版本。                               |
| 计数                         | 符合上述分类的注册活动总数。  |

## <a name="enrollmenteventstatuses"></a>enrollmentEventStatuses 
enrollmentEventStatus 实体表示设备注册结果  。

| 属性                   | 描述                                                                       |
|----------------------------|-----------------------------------------------------------------------------------|
| enrollmentEventStatusKey   | 数据仓库中注册状态的唯一标识符（代理键）  |
| enrollmentEventStatusName  | 注册状态的名称。 请参阅以下示例。                            |

### <a name="example"></a>示例

| enrollmentEventStatusName  | 描述                            |
|----------------------------|----------------------------------------|
| 成功                    | 成功的设备注册         |
| Failed                     | 失败的设备注册             |
| 不可用              | 注册状态不可用。  |

## <a name="enrollmentfailurecategories"></a>enrollmentFailureCategories 
EnrollmentFailureCategory 实体指示设备注册失败的原因  。 

| 属性                       | 描述                                                                                 |
|--------------------------------|---------------------------------------------------------------------------------------------|
| enrollmentFailureCategoryKey   | 数据仓库中注册失败类别的唯一标识符（代理键）  |
| enrollmentFailureCategoryName  | 注册失败类别的名称。 请参阅以下示例。                            |

### <a name="example"></a>示例

| enrollmentFailureCategoryName   | 描述                                                                                                   |
|---------------------------------|---------------------------------------------------------------------------------------------------------------|
| 不适用                  | 注册失败类别不适用。                                                            |
| 不可用                   | 注册失败类别不可用。                                                             |
| Unknown                         | 未知错误。                                                                                                |
| 身份验证                  | 身份验证失败。                                                                                        |
| 授权                   | 调用已通过身份验证，但未得到注册授权。                                                         |
| AccountValidation               | 未能验证注册帐户。 （已阻止帐户，未启用注册）                      |
| UserValidation                  | 无法验证用户。 （用户不存在，缺少许可证）                                           |
| DeviceNotSupported              | 移动设备管理不支持设备。                                                         |
| InMaintenance                   | 帐户处于维护中。                                                                                    |
| BadRequest                      | 客户端发送了服务不理解/不支持的请求。                                        |
| FeatureNotSupported             | 此帐户不支持此注册所使用的功能。                                        |
| EnrollmentRestrictionsEnforced  | 管理员配置的注册限制阻止了此注册。                                          |
| ClientDisconnected              | 客户端超时或最终用户终止了注册。                                                        |
| UserAbandonment                 | 最终用户放弃了注册。 （最终用户启动了加入，但未能及时完成）  |

## <a name="enrollmentfailurereasons"></a>enrollmentFailureReasons  
EnrollmentFailureReason 实体表示特定失败类别中设备注册失败的详细原因  。  

| 属性                     | 描述                                                                               |
|------------------------------|-------------------------------------------------------------------------------------------|
| enrollmentFailureReasonKey   | 数据仓库中注册失败原因的唯一标识符（代理键）  |
| enrollmentFailureReasonName  | 注册失败原因的名称。 请参阅以下示例。                            |

### <a name="example"></a>示例

| enrollmentFailureReasonName      | 描述                                                                                                                                                                                            |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 不适用                   | 注册失败原因不适用。                                                                                                                                                       |
| 不可用                    | 注册失败原因不可用。                                                                                                                                                        |
| Unknown                          | 未知错误。                                                                                                                                                                                         |
| UserNotLicensed                  | 未在 Intune 中找到用户或用户没有有效许可证。                                                                                                                                     |
| UserUnknown                      | 用户对 Intune 未知。                                                                                                                                                                           |
| BulkAlreadyEnrolledDevice        | 只有一位用户可以注册设备。 此设备之前已由另一位用户注册。                                                                                                                |
| EnrollmentOnboardingIssue        | 尚未配置 Intune 移动设备管理 (MDM) 机构。                                                                                                                                 |
| AppleChallengeIssue              | iOS 管理配置文件安装延迟或失败。                                                                                                                                         |
| AppleOnboardingIssue             | 注册 Intune 需要 Apple MDM Push Certificate。                                                                                                                                       |
| DeviceCap                        | 用户尝试注册的设备数超过最大允许数量。                                                                                                                                        |
| AuthenticationRequirementNotMet  | Intune 注册服务未能对此请求进行授权。                                                                                                                                            |
| UnsupportedDeviceType            | 此设备不满足 Intune 注册的最低要求。                                                                                                                                  |
| EnrollmentCriteriaNotMet         | 因已配置的注册限制规则而未能注册此设备。                                                                                                                          |
| BulkDeviceNotPreregistered       | 未找到该设备的国际移动设备标识符 (IMEI) 或序列号。  没有此标识符的设备会识别为个人所有设备，目前此类设备受到阻止。  |
| FeatureNotSupported              | 用户试图访问尚未面向所有客户发布的功能，或者试图访问与 Intune 配置不兼容的功能。                                                            |
| UserAbandonment                  | 最终用户放弃了注册。 （最终用户启动了加入，但未能及时完成）                                                                                           |
| APNSCertificateExpired           | 无法使用 Apple MDM Push Certificate 管理 Apple 设备。                                                                                                                            |
## <a name="ownertypes"></a>ownerTypes

enrollmentType 实体表明拥有设备的是公司、个人还是未知对象  。

| 属性  | 描述 | 示例 |
|---------|------------|--------|
| ownerTypeID |所有者类型的唯一标识符。 | |
| ownerTypeKey |数据仓库中所有者类型的唯一标识符 - 代理键。 | |
| ownerTypeName |表示设备的所有者类型：  <br>公司 - 设备为企业所有。 <br>个人 - 设备为个人所有 (BYOD)。  <br>未知 - 此设备上无此信息。 |公司/个人未知 |

> [!Note]  
> 对于在为设备创建动态组时 Azure AD 中的 `ownerTypeName`，需要将筛选器值 `deviceOwnership` 设置为 `Company`。 有关详细信息，请参阅[设备规则](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices)。 

## <a name="managementstates"></a>managementStates

managementStates 实体提供有关设备状态的详细信息  。 详细信息适用于应用远程操作、设备越狱或进行 root 的情况。

| 属性  | 描述 |
|---------|------------|
| managementStateID | 管理状态的唯一标识符。 |
| managementStateKey | 数据仓库中管理状态的唯一标识符 - 代理键。 |
| managementStateName | 表明应用于此设备的远程操作的状态。 |

### <a name="example"></a>示例

| managementStateID  | 名称 | 描述 |
|---------|------------|--------|
| 0 |托管 | 托管时不存在挂起的远程操作。 |
| 1 |RetirePending | 存在一个针对设备的挂起的停用命令。 |
| 2 |RetireFailed | 设备上的停用命令失败。 |
| 3 |WipePending | 存在一个针对设备的挂起的擦除命令。 |
| 4 |WipeFailed | 设备上的擦除命令失败。 |
| 5 |Unhealthy | 不正常状态。 |
| 6 |DeletePending | 存在一个针对设备的挂起的删除命令。 |
| 7 |RetireIssued | 已向设备发布停用命令。 |
| 8 |WipeIssued | 已发布擦除命令。 |
| 9 |WipeCanceled | 已取消擦除命令。 |
| 10 |RetireCanceled | 已取消停用命令。 |
| 11 |Discovered | 该设备是 Intune 新发现的设备，首次签入后，即会变为“托管”状态。 |

## <a name="managementagenttypes"></a>managementAgentTypes

ManagementAgentType  实体表示用于管理设备的代理。

| 属性  | 描述 |
|---------|------------|
| managementAgentTypeID | 管理代理类型的唯一标识符。 |
| managementAgentTypeKey | 数据仓库中管理代理类型的唯一标识符 - 代理键。 |
| managementAgentTypeName |表明用于管理设备的代理类型。 |

### <a name="example"></a>示例

| ManagementAgentTypeID  | 名称 | 描述 |
|---------|------------|--------|
| 1 |EAS | 设备通过 Exchange Active Sync 管理 |
| 2 |MDM | 设备由 MDM 代理管理 |
| 3 |EasMdm | 设备由 Exchange Active Sync 和 MDM 代理共同管理 |
| 4 |IntuneClient | 设备由 Intune 电脑代理管理 |
| 5 |EasIntuneClient | 设备由 Exchange Active Sync 和 Intune 电脑代理共同管理 |
| 8 |ConfigManagerClient | 设备由 System Center Configuration Manager 代理管理 |
| 16 |Unknown | 未知的管理代理类型 |

## <a name="devices"></a>设备

设备实体列出受管理的所有已注册设备及相应属性  。

|          属性          |                                                                                       描述                                                                                      |
|:--------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| deviceKey                  | 数据仓库中设备的唯一标识符 - 代理键。                                                                                                               |
| deviceId                   | 设备的唯一标识符。                                                                                                                                                     |
| deviceName                 | 允许对设备命名的平台上设备的名称。 在其他平台上，Intune 从其他属性创建名称。 此属性不可同时用于所有设备。 |
| deviceTypeKey              | 此设备的设备类型属性的键。                                                                                                                                    |
| deviceRegistrationState    | 此设备的客户端注册状态属性的键。                                                                                                                      |
| ownerTypeKey               | 此设备的所有者类型属性的键：企业、个人或未知。                                                                                                    |
| enrolledDateTime           | 设备注册的日期和时间。                                                                                                                                         |
| lastSyncDateTime           | 使用 Intune 签入的上一已知设备。                                                                                                                                              |
| managementAgentKey         | 与此设备关联的管理代理键。                                                                                                                             |
| managementStateKey         | 与此设备关联的管理状态键，表明远程操作的最新状态或设备是否越狱/获取了 root 权限。                                                |
| azureADDeviceId            | 此设备 Azure deviceID。                                                                                                                                                  |
| azureADRegistered          | 是否在 Azure Active Directory 中注册了该设备。                                                                                                                             |
| deviceCategoryKey          | 与此设备关联的类别的键。                                                                                                                                     |
| deviceEnrollmentType       | 与此设备关联的注册类型的键，表明注册方法。                                                                                             |
| complianceStateKey         | 与此设备关联的符合性状态的键。                                                                                                                             |
| osVersion                  | 设备的操作系统版本。                                                                                                                                                |
| easDeviceId                | 设备的 Exchange ActiveSync ID。                                                                                                                                                  |
| serialNumber               | SerialNumber                                                                                                                                                                           |
| userId                     | 与设备关联的用户的唯一标识符。                                                                                                                           |
| rowLastModifiedDateTimeUTC | 上次在数据仓库中修改此设备时的 UTC 日期和时间。                                                                                                       |
| 制造商               | 设备制造商                                                                                                                                                             |
| model                      | 设备型号                                                                                                                                                                    |
| operatingSystem            | 设备的操作系统。 Windows、iOS 等。                                                                                                                                   |
| isDeleted                  | 显示设备是否被删除的二进制文件。                                                                                                                                 |
| androidSecurityPatchLevel  | Android 安全修补程序级别                                                                                                                                                           |
| MEID                       | MEID                                                                                                                                                                                   |
| isSupervised               | 设备受监督的状态                                                                                                                                                               |
| freeStorageSpaceInBytes    | 可用存储（以字节为单位）。                                                                                                                                                                 |
| totalStorageSpaceInBytes   | 总存储（以字节为单位）。                                                                                                                                                                |
| encryptionState            | 设备的加密状态。                                                                                                                                                      |
| subscriberCarrier          | 设备的订阅者运营商                                                                                                                                                       |
| phoneNumber                | 设备的电话号码                                                                                                                                                             |
| IMEI                       | IMEI                                                                                                                                                                                   |
| cellularTechnology         | 设备的移动电话技术                                                                                                                                                    |
| WiFiMacAddress             | Wi-Fi MAC                                                                                                                                                                              |
| ICCD                       | 集成卡标识符                                                                                                                                                     |

## <a name="devicepropertyhistories"></a>devicePropertyHistories

devicePropertyHistory 实体具有的属性与设备表格和过去 90 天每个设备记录的每日快照的属性相同  。 DateKey 列表明每行的日期。

|          属性          |                                                                                      描述                                                                                     |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| dateKey                    | 引用日期表格，该表格表明当日日期。                                                                                                                                          |
| deviceKey                  | 数据仓库中设备的唯一标识符 - 代理键。 这是对包含 Intune 设备 ID 的设备表格的引用。                               |
| deviceName                 | 允许对设备命名的平台上设备的名称。 在其他平台上，Intune 从其他属性创建名称。 此属性不可同时用于所有设备。 |
| deviceRegistrationStateKey | 此设备的设备注册状态属性的键。                                                                                                                    |
| ownerTypeKey               | 此设备的所有者类型属性的键：企业、个人或未知。                                                                                                  |
| managementStateKey         | 与此设备关联的管理状态键，表明远程操作的最新状态或设备是否越狱/获取了 root 权限。                                                |
| azureADRegistered          | 是否在 Azure Active Directory 中注册了该设备。                                                                                                                             |
| complianceStateKey         | ComplianceState 的键。                                                                                                                                                            |
| OSVersion                  | 操作系统版本。                                                                                                                                                                          |
| jailBroken                 | 设备是否越狱或取得 root 权限。                                                                                                                                         |
| deviceCategoryKey          | 此设备的设备类别属性的键。 

