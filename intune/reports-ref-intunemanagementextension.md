---
title: IntuneManagementExtension 实体
titleSuffix: Microsoft Intune
description: Intune 数据仓库 API 中实体集合的 IntuneManagementExtension 实体类别的参考主题。
keywords: Intune 数据仓库
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 73DF3B90-6D52-4EF6-AFFD-1873A18C7421
ms.reviewer: dariusz
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: ea55c92fb3254b6e610bec1074e35d9d9c32cd18
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58797989"
---
# <a name="reference-for-intune-management-extension"></a>Intune 管理扩展参考

IntuneManagementExtension 类别包含移动设备的实体，可用于跟踪如下信息：

  -  IntuneManagementExtension 的版本
  -  IntuneManagementExtension 的安装状态

## <a name="intunemanagementextensionversion"></a>IntuneManagementExtensionVersion

IntuneManagementExtensionVersion 实体列出 IntuneManagementExtension 使用的所有版本。

| 属性  | 描述 | 示例 |
|---------|------------|--------|
| ExtensionVersionKey |IntuneManagementExtension 版本的唯一标识符。 | 1 |
| ExtensionVersion |4 位版本号。 |1.0.2.0 |

## <a name="intunemanagementextensionhealthstate"></a>IntuneManagementExtensionHealthState

IntuneManagementExtensionHealthState 列出 IntuneManagementExtension 的所有可能运行状况状态。

| 属性  | 描述 | 示例 |
|---------|------------|--------|
| ExtensionStateKey |运行状况状态的唯一标识符。 | 2 |
| ExtensionState |IntuneManagementExtension 的运行状况状态。 | Healthy |

## <a name="intunemanagementextension"></a>IntuneManagementExtension

IntuneManagementExtension 列出每日在每台 Windows 10 设备上的 IntuneManagementExtension 运行状况。
将保留过去 60 天内的数据。 


|      属性       |                         描述                         | 示例 |
|---------------------|-------------------------------------------------------------|---------|
|       DateKey       |               日期的唯一标识符。                |   123   |
|      TenantKey      |              租户的唯一标识符。               |   456   |
|      DeviceKey      |              设备的唯一标识符。               |   789   |
| ExtensionVersionKey | IntuneManagementExtension 版本的唯一标识符。 |    1    |
|  ExtensionStateKey  |             运行状况状态的唯一标识符。              |    2    |

