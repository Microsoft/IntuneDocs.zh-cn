---
title: "移动应用管理 | Microsoft Docs"
description: "Intune 数据仓库 API 中实体集合的“移动应用管理”类别的参考主题。"
keywords: "Intune 数据仓库"
author: Erikre
ms.author: erikre
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 084F11AD-F7BA-45A4-8424-45E6E4564930
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1b73ba946bdf5e95231b3387885e353a170dbd17
ms.sourcegitcommit: d44c32aad3e84f6c0b296bdb010981d3a818befb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2018
---
# <a name="reference-for-mobile-app-management-mam-entities"></a>移动应用管理 (MAM) 实体引用

“移动应用管理”类别包含移动应用的实体，例如：

  -  应用
  -  Instances
  -  签入状态
  -  运行状况状态
  -  策略状态
  -  注册状态
  -  平台类型

## <a name="mamapplication"></a>MamApplication

MamApplication 实体列出了未在企业中注册便通过移动应用程序管理 (MAM) 托管的业务线 (LOB) 应用。

| 属性 | 描述 | 示例 |
|---------|------------|--------|
| ApplicationKey |数据仓库中 MAM 应用的唯一标识符。 |123 |
| ApplicationName |MAM 应用的名称。 |“Word” |
| ApplicationId |MAM 应用的应用程序 ID。 |b66bc706-ffff-7437-0340-032819502773 |
| IsDeleted |表明是否已更新此 MAM 应用记录。 <br>True - MAM 应用拥有新纪录，其中含有此表中的更新的字段。 <br>False - 此 MAM 应用的最新记录。 |True/False |
| StartDateInclusiveUTC |在数据仓库中创建此 MAM 应用时的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |
| DeletedDateUTC |IsDeleted 更改为 True 时的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |
| RowLastModifiedDateTimeUTC |上次在数据仓库中修改此 MAM 应用时的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |

## <a name="mamapplicationinstance"></a>MamApplicationInstance

MamApplicationInstance 实体将托管移动应用程序管理 (MAM) 应用列为单个实例（按每设备每用户）。 实体中列出的所有用户和设备都受保护，因为向它们分配了至少一个 MAM 策略。

| 属性 | 描述 | 示例 |
|---------|------------|--------|
| ApplicationInstanceKey |数据仓库中 MAM 应用实例的唯一标识符 - 代理键。 |123 |
| UserId |已安装此 MAM 应用的用户的用户 ID。 |b66bc706-ffff-7437-0340-032819502773 |
| ApplicationInstanceId |MAM 应用实例的唯一标识符 - 类似于 ApplicationInstanceKey，但该标识符是自然键。 |b66bc706-ffff-7437-0340-032819502773 |
| ApplicationId |此 MAM 应用的应用程序 ID |com.microsoft.groupies-daily.<IOS> |
| ApplicationVersion |此 MAM 应用的应用程序版本。 |2 |
| CreatedDate |创建此 MAM 应用实例记录的日期。 该值可以为 null。 |2016/11/23 - 中午 12:00:00 |
| 平台 |安装此 MAM 应用的设备平台。 |2 |
| PlatformVersion |安装此 MAM 应用的设备的平台版本。 |2.2 |
| SdkVersion |包装此 MAM 应用时所使用的 MAM SDK 版本。 |3.2 |
| DeviceId |安装此 MAM 应用的设备的设备 ID。 |b66bc706-ffff-7437-0340-032819502773 |
| DeviceName |安装此 MAM 应用的设备的设备名称。 |“MyDevice” |
| IsDeleted |表明是否已更新此 MAM 应用实例记录。 <br>True - 此 MAM 应用实例拥有新纪录，其中含有此表中的更新的字段。 <br>False - 此 MAM 应用实例的最新记录。 |True/False |
| StartDateInclusiveUtc |在数据仓库中创建此 MAM 应用实例时的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |
| DeletedDateUtc |IsDeleted 更改为 True 时的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |
| RowLastModifiedDateTimeUtc |上次在数据仓库中修改此 MAM 应用实例时的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |

## <a name="mamcheckin"></a>MamCheckin

MamCheckin 实体表示使用 Intune 服务签入移动应用程序管理 (MAM) 应用实例后收集的数据。 

> [!Note]  
> 若某个应用实例在一天中签入多次，数据仓库会将其存储为签入一次。

| 属性 | 描述 | 示例 |
|---------|------------|--------|
| DateKey |日期键，表明在数据仓库中记录 MAM 应用签入的时间。 | 20160703 |
| ApplicationInstanceKey |与此 MAM 应用签入关联的应用实例的键。 |1900/5/2 中午 12:00:00 |
| UserKey |与此 MAM 应用签入关联的用户的键。 |1900/1/12 中午 12:00:00 |
| ApplicationKey |已签入的 MAM 应用的键。 |1900/1/10 中午 12:00:00 |
| DeviceHealthKey |与此 MAM 应用签入关联的 DeviceHealth 的键。 |1900/1/2 中午 12:00:00 |
| PlatformKey |表示与此 MAM 应用签入关联的设备的平台。 |1900/1/1 中午 12:00:00 |
| EffectiveAppliedPolicyKey |表示与已签入的 MAM 应用关联的有效应用的策略。 有效应用的策略通过合并与特定应用和用户相关的所有策略生成。 |1900/5/2 中午 12:00:00 |
| LastCheckInDate |上次签入此 MAM 应用的日期和时间。 该值可以为 null。 |2016/11/23 - 中午 12:00:00 |

## <a name="mamdevicehealth"></a>MamDeviceHealth

MamDeviceHealth 实体表示部署有移动应用管理 (MAM) 策略的设备（即使是越狱设备）。

| 属性 | 描述 | 示例 |
|---------|------------|--------|
| DeviceHealthKey |数据仓库中设备及其相关运行状况的唯一标识符 - 代理键。 |1900/1/1 中午 12:00:00 |
| DeviceHealth |设备及其相关运行状况的的唯一标识符 - 类似于 DeviceHealthKey，但该标识符是自然键。 |1900/1/1 中午 12:00:00 |
| DeviceHealthName |表示设备的状态。 <br>不可用 - 此设备上没有信息。 <br>正常 - 设备未越狱。 <br>不正常 - 设备已越狱。 |不可用 正常 不正常 |
| RowLastModifiedDateTimeUtc |上次在数据仓库中修改此特定 MAM 设备运行状况时的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |

## <a name="mameffectivepolicy"></a>MamEffectivePolicy

MamEffectivePolicy 实体列出了组织中应用的所有移动应用管理 (MAM) 有效策略。 有效应用的策略通过合并与特定应用和用户相关的所有策略生成。

| 属性 | 描述 | 示例 |
|---------|------------|--------|
| EffectivePolicyKey |数据仓库中 MAM 有效策略的唯一标识符。 |2 |
| RealPolicyKey |由 IT 专业人员创作的 MAM 策略的唯一标识符。 |1 |
| RowCreatedDateTimeUtc |在数据仓库中创建 MAM 有效策略的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |

## <a name="mamglobalapplication"></a>MamGlobalApplication

MamGlobalApplication 实体列出了未在企业中注册便通过移动应用程序管理 (MAM) 托管的应用商店应用。

| 属性 | 描述 | 示例 |
|---------|------------|--------|
| ApplicationKey |数据仓库中应用商店应用的唯一标识符，称为代理键。 |123 |
| ApplicationId |应用商店的唯一标识符。 该标识符与 ApplicationKey 类似，但是一个自然键。 |com.microsoft.skydrive.<ios> |
| ApplicationName |MAM 全局应用程序名称。 |Skydrive |
| RowLastModifiedDateTimeUtc |上次在数据仓库中修改此特定 MAM 全局应用程序的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |

## <a name="mamplatform"></a>MamPlatform

MamPlatform 实体列出了安装有移动应用程序管理 (MAM) 应用的平台的名称和类型。

| 属性 | 描述 | 示例 |
|---------|------------|--------|
| PlatformKey |数据仓库中平台的唯一标识符 - 代理键。 |123 |
| 平台 |平台的唯一标识符 - 类似于 PlatformKey，但该标识符是自然键。 |123 |
| PlatformName |平台名称 |不可用 <br>无 <br>Windows <br>IOS <br>Android。 |
| RowLastModifiedDateTimeUtc |上次在数据仓库中修改此平台时的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |
