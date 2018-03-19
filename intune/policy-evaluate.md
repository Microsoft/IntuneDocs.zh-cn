---
title: "找出某个策略所面向的用户数"
titlesuffix: Microsoft Intune
description: "找出某个策略所面向的用户数"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/09/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38e8a2e2-2329-11e8-b467-0ed5f89f718b
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: decfd33b540fcb72c838e09034ba4bf312142a5b
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2018
---
# <a name="evaluate-how-many-users-are-targeted-by-a-policy"></a>评估某个策略所面向的用户数
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

可以使用“评估”按钮，找出某个设备符合性或设备配置策略所面向的用户数。 此功能仅计算用户数，而不计算设备数。

1.  在 [Azure 门户的 Intune](https://aka.ms/intuneportal) 中，选择“设备符合性”或“设备配置”，然后选择“策略”。
2.  从中选择某个策略，或创建一个新策略，然后选择“分配”。
3.  选择“评估”。 随即将显示一条消息，显示此策略所面向的用户数。

如果“评估”按钮呈灰显状态，请确保策略已分配到一个或多个组。

