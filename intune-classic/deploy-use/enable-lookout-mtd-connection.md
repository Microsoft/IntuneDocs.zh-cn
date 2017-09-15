---
title: "在 Intune 中启用 Lookout MTP"
description: "在 Intune 管理员控制台中启用 Lookout 移动威胁保护。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2f835fd0-4e62-42f3-b7ca-ce8b7ddd40e4
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 57cdcb50920566c61ed43b5eada5bbde35c2438e
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2017
---
# <a name="enable-lookout-mtd-connection-in-the-intune-classic-portal"></a>在 Intune 经典门户中启用 Lookout MTD 连接

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

若要在 Intune 中启用 Lookout 移动威胁防御 (MTD) 连接，应已在 Lookout 控制台中配置了 Intune 连接器。  若未执行此操作，则应该[设置 Lookout 移动威胁防御订阅](setup-your-lookout-mtd-subscription.md)。

若要在 Intune 中启用 Lookout MTP 连接，请在 [Microsoft Intune 管理员控制台](https://manage.microsoft.com)的“管理”页，选择“第三方服务集成”。 选择“Lookout 状态”，使用切换按钮启用“与 MTP 同步”。

![Lookout 同步页的屏幕截图，其中突出显示了启动切换按钮](../media/mtp/lookout-intune-synchronization.png)

>[!IMPORTANT]
> 创建合规性策略规则和配置条件访问前，**必须**配置 Lookout for Work 应用。 这样可以确保最终用户能够安装应用，以便访问电子邮件或其他公司资源。

按此步骤可在 Intune 管理控制台中完成 Lookout 与 Intune 的集成设置。  实现此解决方案的后续几个步骤涉及部署 [Lookout for Work 应用](/intune-classic/deploy-use/device-threat-protection-policy)策略。


## <a name="next-steps"></a>后续步骤
[配置 Lookout for Work 应用](/intune-classic/deploy-use/device-threat-protection-apps)
