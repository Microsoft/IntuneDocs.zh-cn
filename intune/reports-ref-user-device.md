---
title: 用户设备关联 - Intune 数据仓库
titlesuffix: Microsoft Intune
description: Intune 数据仓库 API 中的更改列表。
keywords: Intune 数据仓库
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: de14444376cb2998f17f406f084c428523ef4e4f
ms.sourcegitcommit: 21db583d6a9d3c15a8a8ee5579309dff1cfe1f8b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2018
---
# <a name="user-device-association"></a>用户设备关联

UserDeviceAssociation 实体包含组织中的用户设备关联。

| 名称               | 描述                                                                                      | 示例                |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
| UserKey            | 数据仓库中用户的唯一标识符。 （代理键）。                              | 123                    |
| DeviceKey          | 数据仓库中设备的唯一标识符。                                            | 123                    |
| CreatedDateTimeUTC | 创建用户设备关联时的日期和时间。 使用 UTC 格式。                                | 2016/11/23 - 中午 12:00:00 |
| IsDeleted          | 指示用户已取消设备注册，并且该关联不再活跃。 | True/False             |
| EndedDateTimeUTC   | IsDeleted 更改为 True 时的 UTC 日期和时间。                                              | 2017/06/23 凌晨 12:00:00 |
