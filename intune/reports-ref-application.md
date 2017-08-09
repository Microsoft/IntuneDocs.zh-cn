---
title: "应用程序 | Microsoft Docs"
description: "Intune 数据仓库 API 中实体集合的“应用程序”类别的参考主题。"
keywords: "Intune 数据仓库"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: A92DEF30-5D01-4774-9917-E26F5F0E2E68
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2e12792445b36ba6657cbe6b2f6c924f6d97fe3c
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2017
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
| AppKey |应用的唯一标识符 |123 |
| ApplicationId |应用的唯一标识符 - 类似于 AppKey，但该标识符是自然键。 |b66bc706-ffff-7437-0340-032819502773 |
| 修订 |上传二进制文件时管理员提到的版本 |2 |
| 标题 |应用标题 |Excel |
| 发布者 |应用发布者 |Microsoft |
| UploadState |应用的上传状态 |1 |
| AppTypeKey |对下一部分中所述的 AppType 的引用。 | |
| VppProgramTypeKey |对下述 VppProgramType 的引用 | |
| CreationTime |创建此修订版本的时间 |2016/11/23 - 中午 12:00:00 |
| ModifiedTime |上次更改与此修订版本相关的任何内容的时间 |2016/11/23 - 中午 12:00:00 |
| 大小 |二进制文件的大小 | |
| StartDateInclusiveUTC |在数据仓库中创建此应用修订版本的 UTC 日期和时间 |2016/11/23 - 中午 12:00:00 |
| EndDateExclusiveUTC |此应用修订版本停用时的 UTC 日期和时间 |2016/11/23 - 中午 12:00:00 |
| IsCurrent |表明此应用修订版本目前是否在数据仓库中 |True/False |
| RowLastModifiedDateTimeUTC |上次在数据仓库中修改此应用版本的 UTC 日期和时间 |2016/11/23 - 中午 12:00:00 |

## <a name="appinstallertypes"></a>AppInstallerTypes

AppInstallerTypes 实体列出了应用的安装源。

| 属性  | 描述 |
|---------|------------|
| AppTypeID |类型 ID |
| AppTypeKey |密钥的代理键 |
| AppTypeName |应用类型 |

## <a name="example"></a>示例

| AppTypeID  | Name | 描述 |
|---------|------------|--------|
| 0 |Android 应用商店应用 |Android 应用商店应用 |
| 1 |Android LOB 应用 |Android 业务线应用 |
| 2 |托管 Android 应用商店应用 (MAM) |启用了管理的 Android 应用商店应用 |
| 3 |iOS 应用商店应用 |iOS 应用商店应用 |
| 4 |iOS LOB 应用 |iOS 业务线应用 |
| 5 |托管 iOS App Store 应用 (MAM?) |启用了管理的 iOS APP Store 应用 |
| 6 |O365 Pro Plus 套件 |适用于 Windows 10 的 Office 365 Pro Plus 套件 |
| 7 |Web 应用 |Web 应用 |
| 8 |Windows Phone 8.1 应用商店应用 |Windows Phone 8.1 应用商店应用 |
| 9 |Windows 应用商店应用 |Windows 应用商店应用 |
| 10 |Windows LOB 应用 |Windows AppX 业务线应用 |
| 11 |Windows Mobile MSI |MSI 业务线应用 |
| 12 |Windows Phone LOB 应用 |Windows Phone 业务线应用 |

## <a name="applicationtypes"></a>ApplicationTypes

ApplicationTypes 实体列出了可能的应用类型。

| 属性  | 说明 |
|---------|------------|
| ApplicationTypeID |类型的 ID |
| ApplicationTypeKey |密钥的代理键 |
| ApplicationTypeName |应用类型 |

## <a name="example"></a>示例

| ApplicationTypeID  | Name | 说明 |
|---------|------------|--------|
| 0 |InHouse |内部开发的应用 |
| 1 |DeepLink |指向应用商店中应用的链接 |
| 2 |WebLink |指向 Web 应用的链接 |

## <a name="managedsoftwaretypes"></a>ManagedSoftwareTypes

ManagedSoftwareTypes 实体列出了应用的可能托管软件类型。

| 属性  | 说明 |
|---------|------------|
| SoftwareTypeID |类型 ID |
| SoftwareTypeKey |密钥的代理键 |
| SoftwareTypeName |软件类型 |

## <a name="example"></a>示例

| SoftwareTypeID  | Name | 描述 |
|---------|------------|--------|
| 0 |“桌面” |桌面应用 |
| 2 |更新 |窗口更新 |
| 5 |SideCarAgent | |
| 1 |“移动” |移动应用 |
| 3 |WebLink |网页链接 |
| 4 |VppDeepLink |指向应用商店中作为 VPP（批量购买计划）一部分的应用的链接 |

## <a name="vppprogramtypes"></a>VppProgramTypes

VppProgramTypes 实体列出了应用的可能 VPP 计划类型。

| 属性  | 描述 |
|---------|------------|
| VppProgramTypeID |类型的 ID |
| VppProgramTypeKey |密钥的代理键 |
| VppProgramTypeName |Vpp 计划类型 |

## <a name="example"></a>示例

| VppProgramID  | Name | 说明 |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 |Microsoft |Microsoft 的 VPP 计划 |
| 00000000-0000-0000-0000-000000000000 |尚未提供 |默认值，无 VPP |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B |Apple |Apple 的 VPP 计划 |
