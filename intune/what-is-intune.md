---
title: "Azure 门户中的 Intune 简介"
titleSuffix: Intune on Azure
description: "获取有关 Azure 门户中 Intune 的基础知识，以及它如何帮助你管理设备。"
keywords: 
author: robstackmsft
ms.author: robstack
nmanager: angrobe
ms.date: 07/17/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a085264-232a-4af0-97f1-747496c44517
ms.suite: ems
ms.custom: 
ms.openlocfilehash: a51b3c59d922b0c150073017222dca0c90c5b7a0
ms.sourcegitcommit: 36ae73f59ff5e9fdfe4f930ad0aa4b7795fe11f2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/18/2017
---
# <a name="introduction-to-microsoft-intune-in-the-azure-portal"></a>Azure 门户中的 Microsoft Intune 简介


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Intune 现在位于 Azure 门户中，这意味着你习惯使用的工作流和功能已经不同了。
新门户提供了 Azure 门户中的新功能和更新功能，可在其中管理组织的移动设备、电脑和应用。

* [我的功能位于 Azure 的什么位置？](ui-changes.md)是一个参考，显示随着移动到 Azure 而更改的特定工作流程和 UI。
* [Azure 门户中的 Intune 经典组](groups-get-started.md)解释了转移到 Azure Active Directory 安全组以进行组管理的含义。




你可以在此库中查找有关新门户的信息，并且信息会不断更新。 如果你有什么建议，请在主题评论中留下反馈。 我们很乐意倾听你的想法。

新体验的亮点包括：

- 用于所有企业移动性 + 安全性 (EMS) 组件的集成控制台
- 基于 Web 标准构建的基于 HTML 的控制台
- 可自动执行多种操作的 Microsoft Graph API 支持
- Azure Active Directory (AD) 组提供跨所有 Azure 应用程序的兼容性
- 支持大多数新式 Web 浏览器

> [!IMPORTANT]
> **还没有看到新门户？**<br>
> 现有租户正在迁移到新的门户体验。 你的租户迁移之前，通知会显示在 Office 消息中心中。
>
> 2017 年 1 月之前创建的 Intune 帐户需要进行一次性迁移，然后才能使用 Azure 中的 Apple 注册工作流。 迁移计划尚未宣布。 如果现有帐户无法访问 Azure 门户，我们强烈建议创建一个试用帐户。
>
> 查看潜在阻止程序的列表 https://blogs.technet.microsoft.com/intunesupport/2017/05/17/intune-migration-blockers-for-grouping-targeting/


## <a name="before-you-start"></a>开始之前

若要使用 Azure 门户中的 Intune，必须拥有 Intune 管理员和租户帐户。 如果尚没有帐户，请[注册帐户](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20)。

## <a name="supported-web-browsers-for-the-azure-portal"></a>受 Azure 门户支持的 Web 浏览器

Azure 门户在大多数新式电脑、Mac 和平板电脑上都可以运行。 不支持移动电话。
目前，支持以下浏览器：

- Microsoft Edge（最新版本）
- Microsoft Internet Explorer 11
- Safari（最新版本，仅限 Mac）
- Chrome（最新版本）
- Firefox（最新版本）

请查看 [Azure 门户](https://docs.microsoft.com/azure/azure-preview-portal-supported-browsers-devices)，了解支持的浏览器的最新相关信息。

## <a name="whats-in-this-library"></a>这个库中有什么？

该文档反映了 Intune 门户的布局，有助于你轻松查找所需信息。

![Azure 门户工作负荷](./media/azure-portal-workloads.png)

### <a name="introduction-and-get-started"></a>简介和入门
本部分包含[介绍性信息](introduction-intune.md)，可帮助你开始使用 Intune。
### <a name="plan-and-design"></a>规划和设计
帮助你[规划和设计](/intune-classic/plan-design/introduction) Intune 环境的信息。
### <a name="device-enrollment"></a>设备注册
[如何通过 Intune 管理设备](device-enrollment.md)。
### <a name="device-compliance"></a>设备符合性
[为设备定义符合性级别，然后报告不符合要求的任何设备](device-compliance.md)。
### <a name="device-configuration"></a>设备配置
[了解可在管理的设备上用来配置设置和功能的配置文件](device-profiles.md)。
### <a name="devices"></a>设备
[了解使用清单和报表管理的设备](device-management.md)。
### <a name="mobile-apps"></a>移动应用
[如何发布、管理、配置和保护应用](app-management.md)。
### <a name="conditional-access"></a>条件性访问
[根据指定的条件限制对 Exchange 服务的访问](conditional-access.md)。
### <a name="on-premises-access"></a>本地访问
[配置本地 Exchange ActiveSync 和 Exchange 访问权限](/intune-classic/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune)
### <a name="users"></a>Users
[了解有关所管理的以及将资源分类到组的设备的用户](users-add.md)。
### <a name="groups"></a>组
[了解如何通过 Intune 使用 Azure Active Directory 组](groups-get-started.md)
### <a name="intune-roles"></a>Intune 角色
[控制可以执行各种 Intune 操作的人员，以及这些操作适用的人员](role-based-access-control.md)。 可以使用涵盖一些常见 Intune 方案的内置角色，也可以创建自己的角色。
### <a name="software-updates"></a>软件更新
[了解如何配置 Windows 10 设备的软件更新](windows-update-for-business-configure.md)。



## <a name="whats-new"></a>新增功能

[了解 Intune 中的新增功能](whats-new.md)。
