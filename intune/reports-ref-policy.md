---
title: "策略 | Microsoft Docs"
description: "Intune 数据仓库 API 中实体集合的“策略”类别的参考主题。"
keywords: "Intune 数据仓库"
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/12/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ab8393f3792611001d15fe4eb031225587126251
ms.sourcegitcommit: cccbb6730a8c84dc3a62093b8910305081ac9d24
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/15/2018
---
# <a name="reference-for-policy-entities"></a>策略实体引用

“策略”类别包含移动设备的实体，可用于跟踪此类信息：

  -  设备配置文件、应用配置文件和符合性策略的清单  
  -  每天处于成功、挂起、失败或错误状态的设备数  
  -  每天处于成功、挂起、失败或错误状态的用户数  
  -  处于成功、挂起、失败或错误状态的总设备数  

## <a name="policy"></a>策略

“策略”实体列出了设备配置文件、应用配置文件和符合性策略。 可使用移动设备管理 (MDM) 将策略分配给企业中的一个组。

| 属性  | 描述 | 示例 |
|---------|------------|--------|
| PolicyKey |表示数据仓库中策略的唯一键。 |123 |
| PolicyId |数据仓库中策略的唯一标识符。 |b66bc706-ffff-7437-0340-032819502773 |
| PolicyName |策略名称。 |“Windows 10 基线” |
| PolicyVersion |策略版本。 编辑或更改策略即会创建一个更新的策略版本。 |1, 2, 3 |
| IsDeleted |表明是否已更新策略记录。  <br>True - 策略拥有新纪录，其中含有更新的字段。 <br>False - 策略的最新记录。 |True/False |
| StartDateInclusiveUTC |在数据仓库中创建策略时的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |
| DeletedDateUTC |IsDeleted 更改为 True 时的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |
| RowLastModifiedDateTimeUTC |上次在数据仓库中修改策略时的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |

## <a name="policytype"></a>PolicyType

PolicyType 实体列出了设备配置文件、应用配置文件和符合性策略的类型。 可使用移动设备管理 (MDM) 将策略分配给企业中的一个组。

| 属性  | 描述 | 示例 |
|---------|------------|--------|
| PolicyTypeId |源系统中的策略的唯一标识符。 |123 |
| PolicyTypeKey |数据仓库中策略的唯一标识符。 |1 |
| PolicyTypeName |策略类型名称。 |Windows 10 符合性策略。 |

## <a name="deviceconfiguration"></a>DeviceConfiguration

DeviceConfigurationProfileDeviceActivity 实体列出每天处于成功、挂起、失败或错误状态的设备数。 该数字反映了分配给该实体的设备配置文件。 例如，如果对于分配给某设备的所有策略，该设备均为成功状态，则当天的成功计数增加一。 如果向设备分配了两个配置文件，一个处于成功状态，另一个处于错误状态，则实体会增加成功计数，同时让设备处于错误状态。 实体列出了过去 30 天中给定某天中处于各状态的设备数。

| 属性  | 描述 | 示例 |
|---------|------------|--------|
| DateKey |日期键，表明在数据仓库中记录设备配置文件签入的时间。 |20160703 |
| Pending |处于挂起状态的唯一设备数。 |123 |
| 成功 |处于成功状态的唯一设备数。 |12 |
| 错误 |处于错误状态的唯一设备数。 |10 |
| Failed |处于失败状态的唯一设备数。 |2 |



DeviceConfigurationProfileUserActivity 实体列出每天处于成功、挂起、失败或错误状态的用户数。 该数字反映了分配给该实体的设备配置文件。 例如，如果对于分配给某用户的所有策略，该用户均为成功状态，则当天的成功计数增加一。 如果向用户分配了两个配置文件，一个处于成功状态，另一个处于错误状态，则将用户计为错误状态。  DeviceConfigurationProfileUserActivity 实体列出了过去 30 天内给定某天中处于各状态的用户数。

| 属性  | 描述 | 示例 |
|---------|------------|--------|
| DateKey |日期键，表明在数据仓库中记录设备配置文件签入的时间。 |20160703 |
| Pending |处于挂起状态的唯一用户数。 |123 |
| 成功 |处于成功状态的唯一用户数。 |12 |
| 错误 |处于错误状态的唯一用户数。 |10 |
| Failed |处于失败状态的唯一用户数。 |2 |

## <a name="policytypeactivity"></a>PolicyTypeActivity

PolicyTypeActivity 列出了处于成功、挂起、失败或错误状态的总设备数。 它列出了每天与设备配置文件、应用配置文件或符合性策略相关的这些状态。

| 属性  | 描述 | 示例 |
|---------|------------|--------|
| DateKey |日期键，表明在数据仓库中记录设备配置文件签入的时间。 |20160703 |
| PolicyKey |策略键，可将其与策略相联接以获取 policyName。 |Windows 10 基线 |
| PolicyTypeKey |策略键类型，可将其与策略类型相联接以获取策略类型名称。 |Windows10 符合性策略 |
| Pending |处于挂起状态的唯一设备数。 |123 |
| 成功 |处于成功状态的唯一设备数。 |12 |
| 错误 |处于错误状态的唯一设备数。 |10 |
| Failed |处于失败状态的唯一设备数。 |2 |

## <a name="compliance-policy"></a>合规性策略

符合性策略 API 参考包含的实体提供有关分配给设备的符合性策略的状态信息。

### <a name="compliancepolicystatusdeviceactivities"></a>CompliancePolicyStatusDeviceActivities

下表总结了分配给设备的符合性策略的分配状态。 它列出每种符合性状态的设备的计数。


|属性     |描述  |示例  |
|---------|---------|---------|
|DateKey  |为符合性策略创建了摘要时的日期键。|20161204 |
|Unknown  |由于其他原因脱机或无法与 Intune 或 Azure AD 通信的设备数量。 |5|
|NotApplicable      |对于管理员指定的设备符合性策略不适用的设备数。|201 |
|是否满足条件      |已成功应用管理员指定的一个或多个设备符合性策略的设备数。 |4083 |
|InGracePeriod      |不符合要求但处于管理员定义的宽限期内的设备数。 |57|
|不符合      |为后列情况的设备数：未能应用由管理员指定的一个或多个设备符合性策略，或其用户未遵守管理员指定的策略。|43 |
|错误      |无法与 Intune 或 Azure AD 通信，以及返回了错误信息的设备数量。 |3|

### <a name="compliancepolicystatusdeviceperpolicyactivities"></a>CompliancePolicyStatusDevicePerPolicyActivities 

下表按策略以及策略类型总结了分配给设备的符合性策略的分配状态。 它针对每个已分配的符合性策略，列出每种符合性状态的设备的计数。



|属性  |描述  |示例  |
|---------|---------|---------|
|DateKey  |为符合性策略创建了摘要时的日期键。|20161219|
|PolicyKey     |创建了摘要的符合性策略的键。 |10178 |
|PolicyPlatformKey      |创建了相应摘要的符合性策略的键。|5|
|Unknown     |由于其他原因脱机或无法与 Intune 或 Azure AD 通信的设备数量。|13|
|NotApplicable     |对于管理员指定的设备符合性策略不适用的设备数。|3|
|是否满足条件      |已成功应用管理员指定的一个或多个设备符合性策略的设备数。 |45|
|InGracePeriod      |不符合要求但处于管理员定义的宽限期内的设备数。 |3|
|不符合      |为后列情况的设备数：未能应用由管理员指定的一个或多个设备符合性策略，或其用户未遵守管理员指定的策略。|7|
|错误      |无法与 Intune 或 Azure AD 通信，以及返回了错误信息的设备数量。 |3|

### <a name="policyplatformtypes"></a>PolicyPlatformTypes

下表包含所有已分配的策略的平台类型。 此表中不包含从未分配给任何设备的策略平台类型。


|属性  |描述  |示例  |
|---------|---------|---------|
|PolicyPlatformTypeKey      |策略平台类型的唯一键。 |20170519 |
|PolicyPlatformTypeId      |策略平台类型的唯一标识符。|1|
|PolicyPlatformTypeName      |策略平台类型的名称。|AndroidForWork |

### <a name="policydeviceactivity"></a>PolicyDeviceActivity

下表列出了每天处于成功、挂起、失败或错误状态的设备数。 此数字反映每个策略类型配置文件的数据。 例如，如果对于分配给某设备的所有策略，该设备均为成功状态，则当天的成功计数增加一。 如果向设备分配了两个配置文件，一个处于成功状态，另一个处于错误状态，则实体会增加成功计数，同时让设备处于错误状态。 PolicyDeviceActivity 实体列出了过去 30 天中给定某天中处于各状态的设备数。

|属性  |描述  |示例  |
|---------|---------|---------|
|DateKey|日期键，表明在数据仓库中记录设备配置文件签入的时间。|20160703|
|Pending|处于挂起状态的唯一设备数。|123|
|成功|处于成功状态的唯一设备数。|12|
PolicyKey|策略键，可将其与策略相联接以获取 policyName。|Windows 10 基线|
|错误|处于错误状态的唯一设备数。|10|
|Failed|处于失败状态的唯一设备数。|2|

### <a name="policyuseractivity"></a>PolicyUserActivity 

下表列出了每天处于成功、挂起、失败或错误状态的用户数。 此数字反映每个策略类型配置文件的数据。 例如，如果对于分配给某用户的所有策略，该用户均为成功状态，则当天的成功计数增加一。 如果向用户分配了两个配置文件，一个处于成功状态，另一个处于错误状态，则将用户计为错误状态。 PolicyDeviceActivity 实体列出了过去 30 天中给定某天中处于各状态的用户数。

|属性  |描述  |示例  |
|---------|---------|---------|
|DateKey|日期键，表明在数据仓库中记录设备配置文件签入的时间。|20160703|
|Pending|处于挂起状态的唯一设备数。|123|
|成功|处于成功状态的唯一设备数。|12|
PolicyKey|策略键，可将其与策略相联接以获取 policyName。|Windows 10 基线|
|错误|处于错误状态的唯一设备数。|10|
