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
ms.reviewer: lancecra
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 665f57a4cdb25c1e9f2bef7f1c25f284589df16f
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="wipe-for-exchange-managed-mobile-devices"></a>Exchange 管理的移动设备的擦除

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune 允许你擦除或重置结合使用 Exchange ActiveSync (EAS) 与 Intune Exchange Connector 管理的移动设备。 下表描述通过 Exchange ActiveSync 可用的擦除功能：

|擦除类型|Windows 8.1 和 Windows RT 8.1|iOS|Android|
|----------------|----------------------------------|--------------|-------------------|-------|-----------|
|完全擦除|删除邮件帐户和缓存的邮件。|XFactory 重置。|恢复出厂设置。|
|选择性擦除/电子邮件|删除电子邮件帐户。|不支持。|不支持。|
|选择性擦除/策略|删除策略实施，但设置不变|删除 XPolicy 实施，但设置不变。|删除策略实施，但设置不变。|
