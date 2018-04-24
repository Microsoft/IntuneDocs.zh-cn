---
title: 应用程序
titlesuffix: Microsoft Intune
description: Intune 数据仓库 API 中实体集合的“应用程序”类别的参考主题。
keywords: Intune 数据仓库
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: A92DEF30-5D01-4774-9917-E26F5F0E2E68
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5fd8f9744e68a19cc9411fe366aff4050cc3caa6
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="reference-for-application-entities"></a>应用程序实体引用

“应用程序”类别包含移动设备的实体，可用于跟踪此类信息：

  -  应用版本
  -  应用的安装源
  -  创建应用的开发人员类型
  -  应用的托管软件类型，例如移动版或桌面版
  -  应用的批量购买计划 (VPP) 状态

## <a name="apprevision"></a>AppRevision

AppRevision 实体列出了应用的所有版本。

| 属性  | 描述 | 示例 |
|---------|------------|--------|
| AppKey |应用的唯一标识符。 |123 |
| ApplicationId |应用的唯一标识符 - 类似于 AppKey，但该标识符是自然键。 |b66bc706-ffff-7437-0340-032819502773 |
| 修订 |上传二进制文件时管理员提到的版本。 |2 |
| 标题 |应用标题。 |Excel |
| 发布者 |应用发布者。 |Microsoft |
| UploadState |应用的上传状态。 |1 |
| AppTypeKey |对下一部分中所述的 AppType 的引用。 | |
| VppProgramTypeKey |对下述 VppProgramType 的引用。 | |
| CreationTime |创建此修订版本的时间。 |2016/11/23 - 中午 12:00:00 |
| ModifiedTime |上次更改与此修订版本相关的任何内容的时间。 |2016/11/23 - 中午 12:00:00 |
| 大小 |二进制文件的大小。 | |
| StartDateInclusiveUTC |在数据仓库中创建此应用修订版本时的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |
| EndDateExclusiveUTC |此应用修订版本停用时的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |
| IsCurrent |表明此应用修订版本目前是否在数据仓库中。 |True/False |
| RowLastModifiedDateTimeUTC |上次在数据仓库中修改此应用版本时的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |

## <a name="apptypes"></a>AppTypes

AppTypes 实体列出了应用的安装源。

| 属性  | 描述 |
|---------|------------|
| AppTypeID |类型 ID |
| AppTypeKey |密钥的代理键 |
| AppTypeName |应用类型 |

### <a name="example"></a>示例

| AppTypeID  | 名称 | 描述 |
|---------|------------|--------|
| 0 |Android 应用商店应用 | Android 应用商店应用。 |
| 1 |Android LOB 应用 | Android 业务线应用。 |
| 2 |托管 Android 应用商店应用 (MAM) | 启用了管理的 Android 应用商店应用。 |
| 3 |iOS 应用商店应用 | iOS 应用商店应用。 |
| 4 |iOS LOB 应用 | iOS 业务线应用。 |
| 5 |托管 iOS App Store 应用 (MAM?) | 启用了管理的 iOS APP Store 应用。 |
| 6 |O365 Pro Plus 套件 | 适用于 Windows 10 的 Office 365 专业增强版套件。 |
| 7 |Web 应用 | Web 应用。 |
| 8 |Windows Phone 8.1 应用商店应用 | Windows Phone 8.1 应用商店应用。 |
| 9 |Windows 应用商店应用 | Windows 应用商店应用。 |
| 10 |Windows LOB 应用 | Windows AppX 业务线应用。 |
| 11 |Windows Mobile MSI | MSI 业务线应用。 |
| 12 |Windows Phone LOB 应用 | Windows Phone 业务线应用。 |


## <a name="vppprogramtypes"></a>VppProgramTypes

VppProgramTypes 实体列出了应用的可能 VPP 计划类型。

| 属性  | 描述 |
|---------|------------|
| VppProgramTypeID | 类型 ID。 |
| VppProgramTypeKey | 密钥的代理键。 |
| VppProgramTypeName | VPP 计划类型。 |

### <a name="example"></a>示例

| VppProgramID  | 名称 | 描述 |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft | Microsoft 的 VPP 计划。 |
| 00000000-0000-0000-0000-000000000000 | 尚未提供 | 默认值，无 VPP。 |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple | Apple 的 VPP 计划。 |



## <a name="applicationinventory"></a>ApplicationInventory

ApplicationInventory 项列出了收集清单时在设备上找到的应用程序。

| 属性  | 描述 |
|---------|------------|
| DeviceKey | 这是对包含 Intune 设备 ID 的“设备”表的引用。 |
| DateKey | 对表明清单日期的日期表格的引用。 |
| ApplicationName | 应用程序名称。 |
| ApplicationVersion | 应用程序版本。 |
| BundleSize | 应用的大小（以字节为单位）。 |

## <a name="mobileappinstallstate"></a>MobileAppInstallState

MobileAppInstallState 实体表示已分配到包含设备和/或用户的组的移动应用的安装状态。

| 属性 | 描述 |
|---|---|
| AppInstallStateKey | 帐户的应用安装状态的唯一 ID。 |
| AppInstallState | 应用安装状态的枚举值。 |
| AppInstallStateName | 应用安装状态的名称。 |

## <a name="mobileappdeviceuserinstallstatus"></a>MobileAppDeviceUserInstallStatus

MobileAppDeviceUserInstallStatus 表示给定设备和用户的移动应用安装状态。


|      属性      |                                                         描述                                                         |
|--------------------|-----------------------------------------------------------------------------------------------------------------------------|
|      DateKey       |                                  记录应用安装状态的当天日期的键。                                  |
|       AppKey       |                             用于标识 AppRevision 实例的移动应用键。                              |
|     DeviceKey      |                              用于标识 Device 实例的目标设备键。                               |
|      UserKey       |                                用于标识 User 实例的目标用户键。                                 |
| AppInstallStateKey |                     用于标识 MobileAppInstallState 实例的应用安装状态键。                     |
|     错误代码      | 应用安装程序、移动平台或与应用安装相关的服务返回的错误代码。 |

