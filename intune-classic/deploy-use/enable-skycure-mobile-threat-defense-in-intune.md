---
title: 在 Intune 中启用 Skycure 移动威胁防御
description: 在 Intune 经典门户中启用 Skycure Mobile Threat Defense。
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 03/16/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0cc4e59d-819a-47a2-a26f-4f8d0f8df7bf
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: da4197a41798f4e47ff35d2dfab36c5317f92e21
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="enable-skycure-mobile-threat-defense-in-intune"></a>在 Intune 中启用 Skycure 移动威胁防御

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

若要启用 Skycure 移动威胁防御，应已[在 Skycure 控制台中配置 Intune 连接器](/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune)。

## <a name="to-enable-the-skycure-mtd-connection-in-intune"></a>在 Intune 中启用 Skycure MTD 连接

1.  转到 [Intune 经典门户](https://manage.microsoft.com/)，再输入凭据。

2.  选择“管理员”&gt;“第三方服务集成”，然后选择“Skycure 状态”并使用切换按钮启用“与 MTD 同步”。

    ![在 Intune 经典门户中启用 Skycure 切换](../media/mtp/enable-skycure-1.png)

> [!IMPORTANT] 
> 创建符合性策略规则和配置条件访问前，必须配置 Skycure 应用。 这样可以确保最终用户能够安装应用，以便访问电子邮件或其他公司资源。

按此步骤可在 Intune 管理控制台中完成 Skycure 与 Intune 的集成设置。 接下来执行此解决方案的几个步骤将涉及部署 Skycure for Work 应用和设置符合性策略。

## <a name="next-steps"></a>后续步骤

[创建 Skycure 移动威胁防御符合性策略](/intune-classic/deploy-use/create-skycure-mobile-threat-defense-compliance-policy)
