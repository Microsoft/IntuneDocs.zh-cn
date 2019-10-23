---
title: 了解应用保护策略交付和时间安排
titleSuffix: Microsoft Intune
description: 了解应用保护策略的不同部署窗口，以了解最终用户设备上应何时出现变更。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ec111319-7e02-434f-946b-88647726bf1a
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7460d5ccf046b25510d798c3a7ed4aa9ecd87a8a
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72499167"
---
# <a name="understand-app-protection-policy-delivery-timing"></a>了解应用保护策略交付时间安排

了解应用保护策略的不同部署窗口，以了解最终用户设备上应何时出现变更。

## <a name="delivery-timing-summary"></a>交付时间安排摘要

应用程序保护策略交付取决于用户的许可证状态和 Intune 服务注册情况。  

|    用户状态    |    应用保护行为     |    重试间隔（查看注释）    |    为什么会出现此情况？    |
|-----------------------------------------------------|-------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
|    租户未载入    |    等待下一个重试间隔。  用户的应用保护未处于激活状态。    |    24 小时    |    未设置 Intune 租户时发生。    |
|    用户未获授权     |    等待下一个重试间隔。  用户的应用保护未处于激活状态。     |    12 小时 - 在 Android 设备上，该间隔的设置需要 Intune APP SDK 版本 5.6.0 或更高版本。 否则，Andriod 设备的间隔为 24 小时。   |    未向用户授权 Intune 时发生。    |
|    用户未分配应用保护策略    |    等待下一个重试间隔。  用户的应用保护未处于激活状态。    |    12 小时        |    未向用户分配应用设置时发生。    |
|    用户已成功注册 Intune MAM    |    已按策略设置应用应用保护。    基于重试间隔进行更新    |    已基于用户负载定义 Intune 服务。    通常为 30 分钟。     |    在用户已成功注册 Intune 服务以获取 MAM 配置时发生。    |

> [!NOTE]
> 重试间隔可能需要应用处于活动状态时才生效，也就是说应用已启动并正在使用。  如果重试间隔为 24 小时，而用户等待 48 小时后启动应用，则应用程序保护客户端将按 48 小时重试。

## <a name="handling-network-connectivity-issues"></a>处理网络连接问题

如果用户注册因网络连接问题而失败，重试间隔时间会缩短。  应用程序保护客户端将逐渐按更长的间隔重试，直到间隔达到 60 分钟或连接成功。  然后客户端会以 60 分钟的间隔重试，直到连接成功。 然后客户端会根据用户状态恢复标准重试间隔。

## <a name="next-steps"></a>后续步骤

[向用户分配许可证，以便他们能够在 Intune 中注册设备](../fundamentals/licenses-assign.md)

