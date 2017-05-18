---
title: "在 Intune 中启用 Skycure 移动威胁防御 | Microsoft Docs"
description: "在 Intune 经典控制台中启用 Skycure 移动威胁防御。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0cc4e59d-819a-47a2-a26f-4f8d0f8df7bf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: e76d66768ac58df25313e102b7f60d2bc7bbc59b
ms.openlocfilehash: a110f2ae4d8a101a7fb977aa651e5ce2c8828e7e
ms.contentlocale: zh-cn
ms.lasthandoff: 03/22/2017


---

# <a name="enable-skycure-mobile-threat-defense-in-intune"></a>在 Intune 中启用 Skycure 移动威胁防御

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

若要在 Intune 中启用 Skycure 移动威胁防御 (MTD) 连接，应已[在 Skycure 控制台中配置 Intune 连接器](https://docs.microsoft.com/intune/deploy-use/setup-the-skycure-integration-with-Intune)。

## <a name="to-enable-the-skycure-mtd-connection-in-intune"></a>在 Intune 中启用 Skycure MTD 连接

1.  转到“[Intune 经典控制台](https://manage.microsoft.com/)”，然后输入你的凭据。

2.  选择“管理员”&gt;“第三方服务集成”，然后选择“Skycure 状态”并使用切换按钮启用“与 MTD 同步”。

    ![在 Intune 经典控制台中启用 Skycure 切换](../media/mtp/enable-skycure-1.png)

> [!IMPORTANT] 
> 创建符合性策略规则和配置条件访问前，必须配置 Skycure 应用。 这样可以确保最终用户能够安装应用，以便访问电子邮件或其他公司资源。

按此步骤可在 Intune 管理控制台中完成 Skycure 与 Intune 的集成设置。 接下来执行此解决方案的几个步骤将涉及部署 Skycure for Work 应用和设置符合性策略。

## <a name="next-steps"></a>后续步骤

[创建 Skycure 移动威胁防御符合性策略](https://docs.microsoft.com/intune/deploy-use/create-skycure-mobile-threat-defense-compliance-policy)

