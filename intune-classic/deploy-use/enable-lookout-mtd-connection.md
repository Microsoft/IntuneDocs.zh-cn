---
title: 在 Intune 中启用 Lookout MTP
description: 在 Intune 管理控制台中启用 Lookout Mobile Threat Protection。
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 12/19/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2f835fd0-4e62-42f3-b7ca-ce8b7ddd40e4
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 99c9952b8df3e9b4b1992cbc45366a5ceed458aa
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="enable-lookout-mtd-connection-in-the-intune-classic-portal"></a>在 Intune 经典门户中启用 Lookout MTD 连接

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

若要在 Intune 中启用 Lookout 移动威胁防御 (MTD) 连接，应已在 Lookout 控制台中配置了 Intune 连接器。  若未执行此操作，则应该[设置 Lookout 移动威胁防御订阅](setup-your-lookout-mtd-subscription.md)。

若要在 Intune 中启用 Lookout MTP 连接，请在 [Microsoft Intune 管理员控制台](https://manage.microsoft.com)的“管理”页，选择“第三方服务集成”。 选择“Lookout 状态”，然后使用切换按钮启用“与 MTP 同步”。

![Lookout 同步页的屏幕截图，其中突出显示了启动切换按钮](../media/mtp/lookout-intune-synchronization.png)

>[!IMPORTANT]
> **必须**先配置 Lookout for Work 应用，然后才创建合规性策略规则和配置条件性访问。 这确保了最终用户有权访问电子邮件和其他公司资源之前，应用已准备就绪并且可用。

这样就完成了在 Intune 管理员控制台中设置 Lookout 和 Intune 的集成。  实现此解决方案的后续几个步骤涉及部署 [Lookout for Work 应用](/intune-classic/deploy-use/device-threat-protection-policy)策略。


## <a name="next-steps"></a>后续步骤
[配置 Lookout for Work 应用](/intune-classic/deploy-use/device-threat-protection-apps)
