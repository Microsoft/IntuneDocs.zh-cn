---
title: "启动 Intune 迁移活动"
description: "本文介绍如何开始迁移活动。"
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 07/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f781b029-50f2-46ee-8ff7-03b4a6719e80
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: ae5e050c5222981ed7608bbf15a87a23c0bf6b04
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="phase-2-migration-campaign"></a>阶段 2：迁移活动

选择最能满足组织需求的迁移方法，并根据自身特殊需求调整实现策略。 本指南的其余部分提供所需工具，以实现用户设备注册 Intune 这一目标。

## <a name="keys-to-a-successful-migration"></a>迁移成功的关键要素

下面是从第三方 MDM 提供程序成功迁移到 Intune 的关键要素：

-   清晰有效的沟通能够将最终用户故障时间和不满将至最小。

-   请确保有专门的具体迁移说明。

-   所有托管设备必须从现有 MDM 提供程序中取消注册，然后才能在 Intune 中注册。

-   为最终用户提供从现有 MDM 提供程序取消注册其设备的指导。

-   使用分阶段方法。 从一小组实验性用户开始，以增量方式添加更多的用户组，直到达到完整的部署规模。

-   监视每个周期的支持人员负载以及注册是否成功。 保留计划时间以确保在迁移下一个之前，可以对每个组的成功条件进行评估。 你的试验部署应确定以下内容：

    -   注册成功率和失败率为预期结果。

    -   用户工作效率：

        -   VPN、Wi-fi、电子邮件和证书等企业资源正常运行。

        -   预配的应用可供访问。

    -   数据安全：

        -   出现相容性报告。

        -   强制实施移动应用保护。

如果对迁移的第一阶段感到满意，请重复[迁移周期](migration-guide-cycle.md)以执行下一阶段。

-   重复分阶段周期，直至将所有用户都迁移到 Intune。

-   确保技术支持团队在整个迁移活动中随时为最终用户提供支持。 在可以估计支持调用工作负载之前，请运行自愿迁移。

-   在支持人员可以处理剩余填充之前，请勿设置注册截止时间

> [!IMPORTANT]
> 请勿配置 Intune 和现有第三方 MDM 解决方案以将访问控件应用于 Exchange 或 SharePoint Online 等资源。 此外，一次只能在一个解决方案中注册设备。

## <a name="next-steps"></a>后续步骤

创建[通信计划](migration-guide-communication-plan.md)。
