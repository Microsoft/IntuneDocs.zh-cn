---
title: IntuneManagementExtension 实体
titleSuffix: Microsoft Intune
description: Intune 数据仓库 API 中实体集合的 IntuneManagementExtension 实体类别的参考主题。
keywords: Intune 数据仓库
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/03/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 73DF3B90-6D52-4EF6-AFFD-1873A18C7421
ms.reviewer: dariusz
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: b2efddc75c5819a25d9ba097cb24726e80df14f2
ms.sourcegitcommit: 8d7406b75ef0d75cc2ed03b1a5e5f74ff10b98c0
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2020
ms.locfileid: "75654186"
---
# <a name="reference-for-intune-management-extensions"></a>Intune 管理扩展参考

intuneManagementExtensions 类别包含移动设备的实体，可用于跟踪如下信息： 

- IntuneManagementExtension 的版本
- IntuneManagementExtension 的安装状态

## <a name="intunemanagementextensionversions"></a>intuneManagementExtensionVersions

intuneManagementExtensionVersion  实体列出 intuneManagementExtensions 使用的所有版本。

| 属性  | 说明 | 示例 |
|---------|------------|--------|
| extensionVersionKey |intuneManagementExtensions 版本的唯一标识符。 | 1 |
| extensionVersion |4 位版本号。 |1.0.2.0 |

## <a name="intunemanagementextensionhealthstates"></a>intuneManagementExtensionHealthStates

intuneManagementExtensionHealthState  列出 intuneManagementExtensions 的所有可能运行状况状态。

| 属性  | 说明 | 示例 |
|---------|------------|--------|
| extensionStateKey |运行状况状态的唯一标识符。 | 2 |
| extensionState |IntuneManagementExtension 的运行状况状态。 | Healthy |

## <a name="intunemanagementextensions"></a>intuneManagementExtensions

intuneManagementExtension  列出每日在每台 Windows 10 设备上的 IntuneManagementExtensions 运行状况。
将保留过去 60 天内的数据。 


|      属性       |                         说明                         | 示例 |
|---------------------|-------------------------------------------------------------|---------|
|       dateKey       |               日期的唯一标识符。                |   123   |
|      tenantKey      |              租户的唯一标识符。               |   456   |
|      deviceKey      |              设备的唯一标识符。               |   789   |
| extensionVersionKey | intuneManagementExtension 版本的唯一标识符。 |    1    |
|  extensionStateKey  |             运行状况状态的唯一标识符。              |    2    |

