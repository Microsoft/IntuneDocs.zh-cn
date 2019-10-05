---
title: 策略实体参考
titleSuffix: Microsoft Intune
description: Intune 数据仓库 API 中实体集合的“策略”类别的参考主题。
keywords: Intune 数据仓库
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a812234588081443c2ee8ea8d42b161c22ad4232
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71940341"
---
# <a name="reference-for-policy-entities"></a>策略实体参考

“策略”类别包含移动设备的实体，可用于跟踪此类信息  ：

- 设备配置文件、应用配置文件和符合性策略的清单  
- 每天处于成功、挂起、失败或错误状态的设备数  
- 每天处于成功、挂起、失败或错误状态的用户数  
- 处于成功、挂起、失败或错误状态的总设备数  

## <a name="policies"></a>策略

“策略”实体列出了设备配置文件、应用配置文件和符合性策略  。 可使用移动设备管理 (MDM) 将策略分配给企业中的一个组。

| 属性  | 描述 | 示例 |
|---------|------------|--------|
| policyKey |表示数据仓库中策略的唯一键。 |123 |
| policyId |数据仓库中策略的唯一标识符。 |b66bc706-ffff-7437-0340-032819502773 |
| policyName |策略名称。 |“Windows 10 基线” |
| policyVersion |策略版本。 编辑或更改策略即会创建一个更新的策略版本。 |1, 2, 3 |
| isDeleted |表明是否已更新策略记录。  <br>True - 策略拥有新纪录，其中含有更新的字段。 <br>False - 策略的最新记录。 |True/False |
| startDateInclusiveUTC |在数据仓库中创建策略时的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |
| deletedDateUTC |IsDeleted 更改为 True 时的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |
| rowLastModifiedDateTimeUTC |上次在数据仓库中修改策略时的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |

## <a name="policytypes"></a>policyTypes

policyType 实体列出了设备配置文件、应用配置文件和符合性策略的类型  。 可使用移动设备管理 (MDM) 将策略分配给企业中的一个组。

| 属性  | 描述 | 示例 |
|---------|------------|--------|
| policyTypeId |源系统中的策略的唯一标识符。 |123 |
| policyTypeKey |数据仓库中策略的唯一标识符。 |1 |
| policyTypeName |策略类型名称。 |Windows 10 符合性策略。 |

## <a name="device-configuration"></a>设备配置

deviceConfigurationProfileDeviceActivity 实体列出每天处于成功、挂起、失败或错误状态的设备数   。 该数字反映了分配给该实体的设备配置文件。 例如，如果对于分配给某设备的所有策略，该设备均为成功状态，则当天的成功计数增加一  。 如果向设备分配了两个配置文件，一个处于成功状态，另一个处于错误状态，则实体会增加成功计数，同时让设备处于错误状态。 实体列出了过去 30 天中给定某天中处于各状态的设备数。

| 属性  | 描述 | 示例 |
|---------|------------|--------|
| dateKey |日期键，表明在数据仓库中记录设备配置文件签入的时间。 |20160703 |
| 挂起 |处于挂起状态的唯一设备数。 |123 |
| 成功 |处于成功状态的唯一设备数。 |12 |
| 错误 |处于错误状态的唯一设备数。 |10 |
| 失败 |处于失败状态的唯一设备数。 |2 |

deviceConfigurationProfileUserActivity 实体列出每天处于成功、挂起、失败或错误状态的用户数   。 该数字反映了分配给该实体的设备配置文件。 例如，如果对于分配给某用户的所有策略，该用户均为成功状态，则当天的成功计数增加一  。 如果向用户分配了两个配置文件，一个处于成功状态，另一个处于错误状态，则将用户计为错误状态。  deviceConfigurationProfileUserActivity 实体列出了过去 30 天内给定某天中处于各状态的用户数  。

| 属性  | 描述 | 示例 |
|---------|------------|--------|
| dateKey |日期键，表明在数据仓库中记录设备配置文件签入的时间。 |20160703 |
| 挂起 |处于挂起状态的唯一用户数。 |123 |
| 成功 |处于成功状态的唯一用户数。 |12 |
| 错误 |处于错误状态的唯一用户数。 |10 |
| 失败 |处于失败状态的唯一用户数。 |2 |

## <a name="policytypeactivities"></a>policyTypeActivities

policyTypeActivity 列出了处于成功、挂起、失败或错误状态的总设备数  。 它列出了每天与设备配置文件、应用配置文件或符合性策略相关的这些状态。

| 属性  | 描述 | 示例 |
|---------|------------|--------|
| dateKey |日期键，表明在数据仓库中记录设备配置文件签入的时间。 |20160703 |
| policyKey |策略键，可将其与策略相联接以获取 policyName。 |Windows 10 基线 |
| policyTypeKey |策略键类型，可将其与策略类型相联接以获取策略类型名称。 |Windows10 符合性策略 |
| 挂起 |处于挂起状态的唯一设备数。 |123 |
| 成功 |处于成功状态的唯一设备数。 |12 |
| 错误 |处于错误状态的唯一设备数。 |10 |
| 失败 |处于失败状态的唯一设备数。 |2 |

## <a name="compliance-policy"></a>合规性策略

符合性策略 API 参考包含的实体提供有关分配给设备的符合性策略的状态信息。

### <a name="compliancepolicystatusdeviceactivities"></a>compliancePolicyStatusDeviceActivities

下表总结了分配给设备的符合性策略的分配状态。 它列出每种符合性状态的设备的计数。


|属性     |描述  |示例  |
|---------|---------|---------|
|dateKey  |为符合性策略创建了摘要时的日期键。|20161204 |
|unknown  |由于其他原因脱机或无法与 Intune 或 Azure AD 通信的设备数量。 |5|
|notApplicable      |对于管理员指定的设备符合性策略不适用的设备数。|201 |
|compliant      |已成功应用管理员指定的一个或多个设备符合性策略的设备数。 |4083 |
|inGracePeriod      |不符合要求但处于管理员定义的宽限期内的设备数。 |57|
|nonCompliant      |为后列情况的设备数：未能应用由管理员指定的一个或多个设备符合性策略，或其用户未遵守管理员指定的策略。|43 |
|错误      |无法与 Intune 或 Azure AD 通信，以及返回了错误信息的设备数量。 |3|

### <a name="compliancepolicystatusdeviceperpolicyactivities"></a>compliancePolicyStatusDevicePerPolicyActivities 

下表按策略以及策略类型总结了分配给设备的符合性策略的分配状态。 它针对每个已分配的符合性策略，列出每种符合性状态的设备的计数。



|属性  |描述  |示例  |
|---------|---------|---------|
|dateKey  |为符合性策略创建了摘要时的日期键。|20161219|
|policyKey     |创建了摘要的符合性策略的键。 |10178 |
|policyPlatformKey      |创建了相应摘要的符合性策略的键。|5|
|unknown     |由于其他原因脱机或无法与 Intune 或 Azure AD 通信的设备数量。|13|
|notApplicable     |对于管理员指定的设备符合性策略不适用的设备数。|3|
|compliant      |已成功应用管理员指定的一个或多个设备符合性策略的设备数。 |45|
|inGracePeriod      |不符合要求但处于管理员定义的宽限期内的设备数。 |3|
|nonCompliant      |为后列情况的设备数：未能应用由管理员指定的一个或多个设备符合性策略，或其用户未遵守管理员指定的策略。|7|
|错误      |无法与 Intune 或 Azure AD 通信，以及返回了错误信息的设备数量。 |3|

### <a name="policyplatformtypes"></a>policyPlatformTypes

下表包含所有已分配的策略的平台类型。 此表中不包含从未分配给任何设备的策略平台类型。


|属性  |描述  |示例  |
|---------|---------|---------|
|policyPlatformTypeKey      |策略平台类型的唯一键。 |20170519 |
|policyPlatformTypeId      |策略平台类型的唯一标识符。|1|
|policyPlatformTypeName      |策略平台类型的名称。|AndroidForWork |

### <a name="policydeviceactivities"></a>policyDeviceActivities

下表列出了每天处于成功、挂起、失败或错误状态的设备数。 此数字反映每个策略类型配置文件的数据。 例如，如果对于分配给某设备的所有策略，该设备均为成功状态，则当天的成功计数增加一。 如果向设备分配了两个配置文件，一个处于成功状态，另一个处于错误状态，则实体会增加成功计数，同时让设备处于错误状态。 policyDeviceActivity 实体列出了过去 30 天中给定某天中处于各状态的设备数。

|属性  |描述  |示例  |
|---------|---------|---------|
|dateKey|日期键，表明在数据仓库中记录设备配置文件签入的时间。|20160703|
|挂起|处于挂起状态的唯一设备数。|123|
|成功|处于成功状态的唯一设备数。|12|
|policyKey|策略键，可将其与策略相联接以获取 policyName。|Windows 10 基线|
|错误|处于错误状态的唯一设备数。|10|
|失败|处于失败状态的唯一设备数。|2|

### <a name="policyuseractivities"></a>policyUserActivities

下表列出了每天处于成功、挂起、失败或错误状态的用户数。 此数字反映每个策略类型配置文件的数据。 例如，如果对于分配给某用户的所有策略，该用户均为成功状态，则当天的成功计数增加一。 如果向用户分配了两个配置文件，一个处于成功状态，另一个处于错误状态，则将用户计为错误状态。 PolicyDeviceActivity 实体列出了过去 30 天中给定某天中处于各状态的用户数。


| 属性  |                                         描述                                         |       示例       |
|-----------|---------------------------------------------------------------------------------------------|---------------------|
|  dateKey  | 日期键，表明在数据仓库中记录设备配置文件签入的时间。 |      20160703       |
|  挂起  |                         处于挂起状态的唯一设备数。                          |         123         |
| 成功 |                         处于成功状态的唯一设备数。                          |         12          |
| policyKey |                 策略键，可将其与策略相联接以获取 policyName。                 | Windows 10 基线 |
|   错误   |                          处于错误状态的唯一设备数。                           |         10          |

