---
title: 用户设备关联 - Intune 数据仓库
titlesuffix: Microsoft Intune
description: UserDeviceAssociation 实体包含组织中的用户设备关联。
keywords: Intune 数据仓库
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/14/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: bff8e67a3c6df4364491ba1407aeaee43ff976c4
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/02/2019
ms.locfileid: "57236613"
---
# <a name="reference-for-user-device-association-entity"></a>用户设备关联实体参考

UserDeviceAssociation 实体包含组织中的用户设备关联。

## <a name="userdeviceassociation"></a>UserDeviceAssociation


|        名称        |                                           描述                                            |        示例         |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
|      UserKey       |              数据仓库中用户的唯一标识符。 （代理键）。               |          123           |
|     DeviceKey      |                      数据仓库中设备的唯一标识符。                      |          123           |
| CreatedDateTimeUTC |           创建用户设备关联时的日期和时间。 使用 UTC 格式。           | 2016/11/23 - 中午 12:00:00 |
|     IsDeleted      | 指示用户已取消设备注册，并且该关联不再活跃。 |       True/False       |
|  EndedDateTimeUTC  |              IsDeleted 更改为 True 时的 UTC 日期和时间。               | 2017/06/23 凌晨 12:00:00 |

## <a name="next-steps"></a>后续步骤

- 了解有关 [Intune 数据仓库](reports-nav-create-intune-reports.md)的详细信息。
