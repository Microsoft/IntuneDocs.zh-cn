---
title: "Exchange 管理的移动设备的擦除"
description: "Microsoft Intune 允许你擦除或重置结合使用 Exchange ActiveSync (EAS) 与 Intune Exchange Connector 管理的移动设备"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e116b620-1e12-4b5c-9905-2f7acf2ae530
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: lancecra
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 31c5707424e582c9e86d8a271e4c03d5668c315c
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/10/2017
---
# <a name="wipe-for-exchange-managed-mobile-devices"></a>Exchange 管理的移动设备的擦除

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune 允许你擦除或重置结合使用 Exchange ActiveSync (EAS) 与 Intune Exchange Connector 管理的移动设备。 下表描述通过 Exchange ActiveSync 可用的擦除功能：

|擦除类型|Windows 8.1 和 Windows RT 8.1|iOS|Android|
|----------------|----------------------------------|--------------|-------------------|-------|-----------|
|完全擦除|删除邮件帐户和缓存的邮件。|XFactory 重置。|恢复出厂设置。|
|选择性擦除/电子邮件|删除电子邮件帐户。|不支持。|不支持。|
|选择性擦除/策略|删除策略实施，但设置不变|删除 XPolicy 实施，但设置不变。|删除策略实施，但设置不变。|
