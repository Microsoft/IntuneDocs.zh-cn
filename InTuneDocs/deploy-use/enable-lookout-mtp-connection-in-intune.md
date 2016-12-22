---
title: "在 Intune 中启用 Lookout MTP | Microsoft Intune"
description: "在 Intune 管理员控制台中启用 Lookout 移动威胁保护。"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 2f835fd0-4e62-42f3-b7ca-ce8b7ddd40e4
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: 1bef6c15387309e1b36bc85758ca699acd54fdd0


---

# <a name="enable-lookout-mtp-connection-in-the-intune-admin-console"></a>在 Intune 管理控制台中启用 Lookout MTP 连接
本主题介绍如何在 Intune 中启用 Lookout MTP 连接。 执行此步骤前，应在 Lookout 控制台配置好 Intune 连接器。  若未执行此操作，请按[为订阅设置 Lookout 移动威胁保护](set-up-your-subscription-with-lookout-mtp.md)所述步骤进行操作。

若要在 Intune 中启用 Lookout MTP 连接，请在 [Microsoft Intune 管理员控制台](https://manage.microsoft.com)的“管理”页，选择“第三方服务集成”。 选择“Lookout 状态”，使用切换按钮启用“与 MTP 同步”。

![Lookout 同步页的屏幕截图，其中突出显示了启动切换按钮](../media/mtp/lookout-intune-synchronization.png)

按此步骤可在 Intune 管理控制台中完成 Lookout 与 Intune 的集成设置。  接下来执行此解决方案的几个步骤将涉及部署 [Lookout for Work 应用](configure-and-deploy-lookout-for-work-apps.md)、设置[合规性](enable-device-threat-protection-rule-in-compliance-policy.md)策略。

>[!IMPORTANT]
> 创建合规性策略规则和配置条件访问前，**必须**配置 Lookout for Work 应用。 这样可以确保最终用户能够安装应用，以便访问电子邮件或其他公司资源。
## <a name="next-steps"></a>后续步骤
[配置 Lookout for Work 应用](configure-and-deploy-lookout-for-work-apps.md)



<!--HONumber=Dec16_HO2-->


