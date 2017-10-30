---
title: "用户设备关联 | Microsoft Docs"
description: "Intune 数据仓库 API 中实体集合的“用户设备关联”类别的参考主题。"
keywords: "Intune 数据仓库"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 09/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: BCDBABCB-A7B1-42F2-BDD1-D055E33F2239
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 490e29f87c65875a385472e6abe9400363383f9b
ms.sourcegitcommit: bb2c181fd6de929cf1e5d3856e048d617eb72063
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/20/2017
---
# <a name="reference-for-user-device-association-entity"></a>用户设备关联实体参考

“用户设备关联”类别包含用于在组织中定义设备关联的“用户设备关联”实体。

**用户设备关联**

“用户设备关联”实体表示组织中定义的设备关联。

| Name               | 描述                                                                                      | 示例                |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
| UserKey            | 数据仓库中用户的唯一标识符 - 代理键。                             | 123                    |
| DeviceKey          | 数据仓库中设备的唯一标识符。                                           | 123                    |
| CreatedDateTimeUTC | 创建用户设备关联时的 UTC 日期和时间。                               | 2016/11/23 - 凌晨 12:00:00 |
| IsDeleted          | 指示用户已取消设备注册，并且该关联不再活跃。 | True                   |
| EndedDateTimeUTC   | IsDeleted 更改为 True 时的 UTC 日期和时间。                                         | 2017/06/23 凌晨 12:00:00 |