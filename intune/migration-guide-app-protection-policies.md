---
title: "在 Intune 迁移过程中配置应用保护策略"
description: "本文提供在 Intune 迁移过程中设置应用保护策略的必要步骤。"
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 07/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 93cda587-bf56-4d41-b123-9fe203fad788
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 009759aa826872fc2c608c6786749d6706cd2f93
ms.sourcegitcommit: 9bd6278d129fa29f184b2d850138f8f65f3674ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
---
# <a name="configure-app-protection-policies-optional"></a>配置应用保护策略（可选）


通过应用保护策略，可以：
* 加密应用
* 定义访问应用所需的 PIN
* 阻止应用在越狱或取得 root 权限的设备上运行，以及许多其他保护。

如果用户的电话丢失或被盗，可以选择性地远程擦除公司数据，同时使个人数据完好无损。

应用保护策略在应用级别应用安全性并且不需要设备注册。 无论设备注册 Intune 与否，都可以使用这些策略。 此外，还可将其用于注册第三方 MDM 提供程序的设备。

## <a name="app-protection-policies-with-lob-apps"></a>LOB 应用的应用保护策略

此外，你还可以通过适用于 IOS 和 Android 平台的 [Microsoft Intune APP SDK](app-sdk-get-started.md) 或 Microsoft Intune App Wrapping Tool 将移动应用保护策略扩展到业务线 (LOB) 应用。 有关详细信息，请参阅 [App Wrapping Tool for iOS](app-wrapper-prepare-ios.md) 和 [App Wrapping Tool for Android](app-wrapper-prepare-android.md)。 此外，请参阅[准备 LOB 应用以实现应用保护](apps-prepare-mobile-application-management.md)。

## <a name="how-do-app-protection-policies-help-during-migration"></a>应用保护策略在迁移过程中起到什么作用？

迁移时，必须从旧的 MDM 提供程序中删除设备并注册 Intune。 应对此制定计划，并鼓励最终用户在保留旧的 MDM 提供程序后立即注册 Intune。 但是，在迁移期间，可能会存在延迟完成注册过程的用户，并且其设备不受任一 MDM 提供程序管理。

如果仍允许访问公司资源，此时间段可能会使组织更易处于设备被盗和公司数据丢失风险下。 如果阻止访问公司资源，还有可能导致用户工作效率降低。

Intune 可以在迁移过程中提供企业数据保护，因此，在没有设备级管理的情况下，你仍可以安全访问企业数据。

在旧的 MDM 提供程序中禁用条件访问时，如果将用户载入 Intune，他们仍然可以保持较高的工作效率。

## <a name="task-list-for-app-protection-policies"></a>应用保护策略的任务列表

1. [创建应用保护策略](app-protection-policies.md#create-an-app-protection-policy)
2. [部署策略](app-protection-policies.md#deploy-a-policy-to-users)


## <a name="next-steps"></a>后续步骤

[特殊迁移注意事项](migration-guide-considerations.md)
