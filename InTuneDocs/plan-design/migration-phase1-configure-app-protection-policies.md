---
title: "在 Intune 迁移过程中配置应用保护策略 | Microsoft Docs"
description: "本文主旨是在 Intune 迁移过程中提供设置应用保护策略的必要步骤。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 93cda587-bf56-4d41-b123-9fe203fad788
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: f30ab8799b2e049372139c7f9ee7213547736bb0
ms.lasthandoff: 04/14/2017


---

# <a name="phase-1-configure-app-protection-policies-optional"></a>阶段 1：配置应用保护策略（可选）

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

应用保护策略可用于加密应用、在访问应用时定义 PIN、阻止应用在越狱的设备或取得 root 权限的设备上运行，以及许多其他保护。 如果用户的电话丢失或被盗，可以选择性地远程擦除公司数据，同时通过应用移动应用保护策略使个人数据完好无损。

应用保护策略在应用级别应用安全性并且不需要设备注册。 无论设备注册 Intune 与否，都可以使用该策略。 此外，它还可用于注册第三方 MDM 提供程序的设备。

## <a name="app-protection-policies-with-lob-apps"></a>LOB 应用的应用保护策略

还可以通过利用适用于 [IOS](https://www.microsoft.com/download/details.aspx?id=45218&751be11f-ede8-5a0c-058c-2ee190a24fa6=True) 和 [Android](https://www.microsoft.com/download/details.aspx?id=47267) 平台的 [Microsoft Intune APP SDK](https://docs.microsoft.com/intune/deploy-use/use-the-sdk-to-enable-apps-for-mobile-application-management) 或 Microsoft Intune App Wrapping Tool 将移动应用保护策略扩展到业务线 (LOB) 应用。

## <a name="how-do-app-protection-policies-help-during-migration"></a>应用保护策略在迁移过程中起到什么作用？

迁移需要从旧的 MDM 提供程序中删除设备并注册 Intune。 应对此制定计划，并鼓励最终用户在保留旧的 MDM 提供程序后立即注册 Intune。 但是，在迁移期间，可能会存在延迟完成注册过程的用户，并且其设备不受任一 MDM 提供程序管理。

如果仍允许访问企业资源，此时间段可能会使组织更易处于设备被盗和企业数据丢失风险下，并且/或者如果阻止访问企业资源，则会导致用户工作效率降低。

Intune 可以在迁移过程中提供企业数据保护，因此，在没有设备级管理的情况下，你仍可以安全访问企业数据。

在旧的 MDM 提供程序中禁用条件访问时，如果将用户载入 Intune，他们仍然可以保持较高的工作效率。

## <a name="task-list-for-app-protection-policies"></a>应用保护策略的任务列表

-   任务 1：了解[如何准备好配置移动应用保护](https://docs.microsoft.com/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)策略

-   任务 2：了解[如何创建和部署移动应用保护策略](https://docs.microsoft.com/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)

## <a name="next-steps"></a>后续步骤 

[阶段 1：特殊迁移注意事项](https://docs.microsoft.com/intune/plan-design/migration-phase1-special-migration-considerations)

