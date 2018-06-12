---
title: 解决 Intune 中设置的访问点限制
description: 查看 Intune 访问点限制策略的 3 个常见消息，并了解其解决方式
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.openlocfilehash: a6f5fb0ae4ab5f4f5cafbba6122c0b42e4591c4b
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745113"
---
# <a name="resolve-access-point-restrictions"></a>解决访问点限制

组织可能会限制设备访问公司数据的位置。
若要配置这些访问点限制，需指定并设置已批准的网络位置。  

当尝试连接到无法识别或未经批准的网络时，可能会收到以下一条或多条消息：

* 未设置访问点限制。
* 未连接到已批准的网络。
* 出现错误，无法强制执行访问点限制。

 下表列出了每条消息及其含义，以及如何再次访问工作资源。

## <a name="access-point-restrictions-not-set-up"></a>未设置访问点限制  
| 公司门户消息 | 此消息的含义 | 需要执行的操作                                                               
|------------------------|--------------------------|--------------------------|
| **未设置访问点限制 - 访问点限制处于活动状态，必须进行设置。** | 公司在你的设备上应用了访问点限制。 此设置要求通过公司门户应用验证你的设备上的一些网络设置。 | 点击“解析”。 公司门户应用将检查以确保你已连接到公司已批准的网络。 |

## <a name="not-connected-to-an-approved-network"></a>未连接到已批准的网络  

| 公司门户消息 | 此消息的含义 | 需要执行的操作                                                                   
|------------------------|-----------------------------------|--------------------------|
| **设备未连接到已批准的网络 - 连接到已批准的无线网络。** | 已连接到未获批准进行工作访问的网络。 只要连接到此网络，就无法访问工作电子邮件、应用和其他受保护的公司资源。 | 连接到公司已批准的网络。 然后，点击“解析”以重试。 |

## <a name="restrictions-couldnt-be-enforced"></a>无法强制执行限制  

| 公司门户消息 | 此消息的含义 | 需要执行的操作                                                                      
|------------------------|-----------------------------------|--------------------------|
| **无法强制执行访问点限制 - 公司门户网站遇到一个错误。** | Intune 无法确定是否连接到已批准的网络。 此错误可能是由于网络连接不良、电池电量不足、节电模式或公司门户错误造成的。 | 请确保有强大的网络信号。 关闭节电模式并确保电池续航时间至少剩余 30%。 然后，点击“解析”以重试。 

仍需帮助？ 建议联系公司支持人员获取帮助。 有关特定联系人信息，请转到[公司门户网站](https://portal.manage.microsoft.com/#HelpDeskDialog)。
