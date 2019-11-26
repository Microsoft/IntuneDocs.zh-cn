---
title: 应用实体参考
titleSuffix: Microsoft Intune
description: Intune 数据仓库 API 中实体集合的“应用程序”类别的参考主题。
keywords: Intune 数据仓库
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A92DEF30-5D01-4774-9917-E26F5F0E2E68
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a4a8fa34673340e4adca7b64707d8c79d4808460
ms.sourcegitcommit: 1cf063c98e1caae00a6e6fab821cc3254562bca9
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2019
ms.locfileid: "74290946"
---
# <a name="reference-for-application-entities"></a>应用程序实体引用

“应用程序”类别包含设备的实体，可用于跟踪此类信息  ：

- 应用版本
- 应用的安装源
- 创建应用的开发人员类型
- 应用的托管软件类型，例如移动版或桌面版  
- 应用的批量购买计划 (VPP) 状态

## <a name="apprevisions"></a>appRevisions

appRevision  实体列出了应用的所有版本。

| 属性  | 描述 | 示例 |
|---------|------------|--------|
| appKey |应用的唯一标识符。 |123 |
| applicationId |应用的唯一标识符 - 类似于 AppKey，但该标识符是自然键。 |b66bc706-ffff-7437-0340-032819502773 |
| revision |上传二进制文件时管理员提到的版本。 |2 |
| title |应用标题。 |Excel |
| publisher |应用发布者。 |Microsoft |
| uploadState |应用的上传状态。 |1 |
| appTypeKey |对下一部分中所述的 AppType 的引用。 | |
| vppProgramTypeKey |对下述 VppProgramType 的引用。 | |
| creationTime |创建此修订版本的时间。 |2016/11/23 - 中午 12:00:00 |
| modifiedTime |上次更改与此修订版本相关的任何内容的时间。 |2016/11/23 - 中午 12:00:00 |
| 大小 |二进制文件的大小。 | |
| startDateInclusiveUTC |在数据仓库中创建此应用修订版本时的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |
| endDateExclusiveUTC |此应用修订版本停用时的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |
| isCurrent |表明此应用修订版本目前是否在数据仓库中。 |True/False |
| rowLastModifiedDateTimeUTC |上次在数据仓库中修改此应用版本时的 UTC 日期和时间。 |2016/11/23 - 中午 12:00:00 |

## <a name="apptypes"></a>appTypes

appType  实体列出了应用的安装源。

| 属性  | 描述 |
|---------|------------|
| appTypeID |类型的 ID |
| appTypeKey |密钥的代理键 |
| appTypeName |应用类型 |

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


## <a name="vppprogramtypes"></a>vppProgramTypes

vppProgramType  实体列出了应用的可能 VPP 计划类型。

| 属性  | 描述 |
|---------|------------|
| vppProgramTypeID | 类型 ID。 |
| vppProgramTypeKey | 密钥的代理键。 |
| vppProgramTypeName | VPP 计划类型。 |

### <a name="example"></a>示例

| VppProgramID  | 名称 | 描述 |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft | Microsoft 的 VPP 计划。 |
| 00000000-0000-0000-0000-000000000000 | 尚未提供 | 默认值，无 VPP。 |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple | Apple 的 VPP 计划。 |



## <a name="applicationinventories"></a>applicationInventories

applicationInventory 项列出了收集清单时在设备上找到的应用程序  。

| 属性  | 描述 |
|---------|------------|
| deviceKey | 这是对包含 Intune 设备 ID 的“设备”表的引用。 |
| dateKey | 对表明清单日期的日期表格的引用。 |
| applicationName | 应用程序名称。 |
| applicationVersion | 应用程序版本。 |
| bundleSize | 应用的大小（以字节为单位）。 |

## <a name="mobileappinstallstates"></a>mobileAppInstallStates

mobileAppInstallState  实体表示已分配到包含设备和/或用户的组的移动应用程序的安装状态。

| 属性 | 描述 |
|---|---|
| appInstallStateKey | 帐户的应用安装状态的唯一 ID。 |
| appInstallState | 应用安装状态的枚举值。 |
| appInstallStateName | 应用安装状态的名称。 |



