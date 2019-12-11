---
title: 移动应用管理 (MAM)
titleSuffix: Microsoft Intune
description: Intune 数据仓库 API 中实体集合的“移动应用管理”类别的参考主题。
keywords: Intune 数据仓库
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 084F11AD-F7BA-45A4-8424-45E6E4564930
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: eb1833a6a54fe0a7f78958e653468921df952b4d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72505694"
---
# <a name="reference-for-mobile-app-management-mam-entities"></a>移动应用管理 (MAM) 实体引用

“移动应用管理”类别包含移动应用的实体，例如  ：

- “应用”
- Instances
- 签入状态
- 运行状况状态
- 策略状态
- 注册状态
- 平台类型

## <a name="mamapplications"></a>mamApplications

mamApplication 实体列出了未在企业中注册便通过移动应用程序管理 (MAM) 托管的业务线 (LOB) 应用  。

| 属性 | 描述 | 示例 |
|---------|------------|--------|
| mamApplicationKey |MAM 应用程序的唯一标识符。 | 432 |
| mamApplicationName |MAM 应用程序的名称。 |MAM 应用程序示例名称 |
| mamApplicationId |MAM 应用程序的应用程序 ID。 | 123 |
| isDeleted |表明是否已更新此 MAM 应用记录。 <br>True - MAM 应用拥有新纪录，其中含有此表中的更新的字段。 <br>False - 此 MAM 应用的最新记录。 |True/False |
| startDateInclusiveUTC |在数据仓库中创建此 MAM 应用时的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |
| deletedDateUTC |IsDeleted 更改为 True 时的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |
| rowLastModifiedDateTimeUTC |上次在数据仓库中修改此 MAM 应用时的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |


## <a name="mamapplicationinstances"></a>mamApplicationInstances

mamApplicationInstance 实体将托管移动应用程序管理 (MAM) 应用列为单个实例（按每设备每用户）  。 实体中列出的所有用户和设备都受保护，因为向它们分配了至少一个 MAM 策略。


|          属性          |                                                                                                  描述                                                                                                  |               示例                |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------|
|   applicationInstanceKey   |                                                               数据仓库中 MAM 应用实例的唯一标识符 - 代理键。                                                                |                 123                  |
|           userId           |                                                                              已安装此 MAM 应用的用户的用户 ID。                                                                              | b66bc706-ffff-7437-0340-032819502773 |
|   applicationInstanceId    |                                              MAM 应用实例的唯一标识符 - 类似于 ApplicationInstanceKey，但该标识符是自然键。                                              | b66bc706-ffff-7437-0340-032819502773 |
| mamApplicationId | 创建此 MAM 应用程序实例的 MAM 应用程序的应用程序 ID。   | 2016/11/23 - 中午 12:00:00   |
|     applicationVersion     |                                                                                     此 MAM 应用的应用程序版本。                                                                                      |                  2                   |
|        createdDate         |                                                                 创建此 MAM 应用实例记录的日期。 该值可以为 null。                                                                 |        2016/11/23 - 中午 12:00:00        |
|          平台          |                                                                          安装此 MAM 应用的设备平台。                                                                           |                  2                   |
|      platformVersion       |                                                                      安装此 MAM 应用的设备的平台版本。                                                                       |                 2.2                  |
|         sdkVersion         |                                                                            包装此 MAM 应用时所使用的 MAM SDK 版本。                                                                            |                 3.2                  |
| mamDeviceId | 与 MAM 应用程序实例关联的设备的设备 ID。   | 2016/11/23 - 中午 12:00:00   |
| mamDeviceType | 与 MAM 应用程序实例关联的设备的设备类型。   | 2016/11/23 - 中午 12:00:00   |
| mamDeviceName | 与 MAM 应用程序实例关联的设备的设备名。   | 2016/11/23 - 中午 12:00:00   |
|         isDeleted          | 表明是否已更新此 MAM 应用实例记录。 <br>True - 此 MAM 应用实例拥有新纪录，其中含有此表中的更新的字段。 <br>False - 此 MAM 应用实例的最新记录。 |              True/False              |
|   startDateInclusiveUtc    |                                                              在数据仓库中创建此 MAM 应用实例时的 UTC 日期和时间。                                                               |        2016/11/23 - 中午 12:00:00        |
|       deletedDateUtc       |                                                                             IsDeleted 更改为 True 时的 UTC 日期和时间。                                                                              |        2016/11/23 - 中午 12:00:00        |
| rowLastModifiedDateTimeUtc |                                                           上次在数据仓库中修改此 MAM 应用实例时的 UTC 日期和时间。                                                            |        2016/11/23 - 中午 12:00:00        |


## <a name="mamcheckins"></a>mamCheckins

mamCheckin 实体表示使用 Intune 服务签入移动应用程序管理 (MAM) 应用实例后收集的数据  。 

> [!Note]  
> 若某个应用实例在一天中签入多次，数据仓库会将其存储为签入一次。

| 属性 | 描述 | 示例 |
|---------|------------|--------|
| dateKey |日期键，表明在数据仓库中记录 MAM 应用签入的时间。 | 20160703 |
| applicationInstanceKey |与此 MAM 应用签入关联的应用实例的键。 | 123 |
| userKey |与此 MAM 应用签入关联的用户的键。 | 4323 |
| mamApplicationKey |与 MAM 应用程序签入相关联的应用程序的应用程序密钥。 | 432 |
| deviceHealthKey |与此 MAM 应用签入关联的 DeviceHealth 的键。 | 321 |
| platformKey |表示与此 MAM 应用签入关联的设备的平台。 |123 |
| effectiveAppliedPolicyKey |表示与已签入的 MAM 应用关联的有效应用的策略。 有效应用的策略通过合并与特定应用和用户相关的所有策略生成。 | 322 |
| pastCheckInDate |上次签入此 MAM 应用的日期和时间。 该值可以为 null。 |2016/11/23 - 中午 12:00:00 |


## <a name="mamdevicehealth"></a>mamDeviceHealth

mamDeviceHealth 实体表示部署有移动应用管理 (MAM) 策略的设备（即使是越狱设备）  。

| 属性 | 描述 | 示例 |
|---------|------------|--------|
| deviceHealthKey |数据仓库中设备及其相关运行状况的唯一标识符 - 代理键。 |123 |
| deviceHealth |设备及其相关运行状况的的唯一标识符 - 类似于 DeviceHealthKey，但该标识符是自然键。 |b66bc706-ffff-7777-0340-032819502773 |
| deviceHealthName |表示设备的状态。 <br>不可用 - 此设备上没有信息。 <br>正常 - 设备未越狱。 <br>不正常 - 设备已越狱。 |不可用 正常 不正常 |
| rowLastModifiedDateTimeUtc |上次在数据仓库中修改此特定 MAM 设备运行状况时的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |

## <a name="mameffectivepolicies"></a>mamEffectivePolicies

mamEffectivePolicy 实体列出了组织中应用的所有移动应用管理 (MAM) 有效策略  。 有效应用的策略通过合并与特定应用和用户相关的所有策略生成。

| 属性 | 描述 | 示例 |
|---------|------------|--------|
| effectivePolicyKey |数据仓库中 MAM 有效策略的唯一标识符。 |2 |
| realPolicyKey |由 IT 专业人员创作的 MAM 策略的唯一标识符。 |1 |
| rowCreatedDateTimeUtc |在数据仓库中创建 MAM 有效策略的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |

## <a name="mamplatforms"></a>mamPlatforms

mamPlatform 实体列出了安装有移动应用程序管理 (MAM) 应用的平台的名称和类型  。


|          属性          |                                    描述                                    |                         示例                         |
|----------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------|
|        platformKey         |     数据仓库中平台的唯一标识符 - 代理键。      |                           123                           |
|          平台          | 平台的唯一标识符 - 类似于 PlatformKey，但该标识符是自然键。 |                           123                           |
|        platformName        |                                   平台名称                                   | 不可用 <br>无 <br>Windows <br>IOS <br>Android。 |
| rowLastModifiedDateTimeUtc | 上次在数据仓库中修改此平台时的 UTC 日期和时间。  |                 2016/11/23 - 中午 12:00:00                  |

