---
title: "Azure 门户预览版中的 Intune 简介"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：获取有关 Azure 门户预览版中 Intune 的基础知识，以及它如何帮助你管理设备。"
keywords: 
author: robstackmsft
ms.author: robstack
nmanager: angrobe
ms.date: 04/24/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a085264-232a-4af0-97f1-747496c44517
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 16d7ff50eb821e0927c3c6ea21f3cdb1257762a0
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---


# <a name="introduction-to-microsoft-intune-in-the-azure-portal-preview"></a>Azure 门户预览版中的 Microsoft Intune 简介


[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Microsoft Intune 正在向 Azure 门户迁移，这意味着你习惯使用的工作流和功能将发生改变。
新门户提供 Azure 门户中新功能和更新功能的预览，可在其中管理组织的移动设备、电脑和应用。
所有 Intune 功能最终都会迁移到 Azure，但现在可以在 Azure 门户中执行许多 Intune 任务。 由于此新体验是在预览版中，因此门户中可能尚不提供某些功能。 有关详细信息，请查看[新增功能](#whats-new)部分。

> [!IMPORTANT]
> **还没有看到新门户？**<br>
> 我们已经开始向选定的租户推出预览版。 现有租户将从 2017 年初开始迁移到新体验。 在租户迁移之前，你将在 Office 邮件中心收到通知。
>
> 2017 年 1 月之前创建的 Intune 帐户需要进行一次性迁移，然后才能使用 Azure 中的 Apple 注册工作流。 迁移的计划目前尚未公布，但详细信息将尽快发布。 强烈建议创建一个试用帐户，在现有帐户无法访问预览版时测试新体验。


可以在此库中找到新的产品文档，并且它将在预览期间不断更新。 如果你想提出建议，请在主题评论中留下反馈。 我们很乐意倾听你的想法。

<!--- You can view the new Intune technical preview console in Azure at [portal.azure.com]. --->

新体验的亮点包括：

- 用于所有企业移动性 + 安全性 (EMS) 组件的集成控制台
- 基于 Web 标准构建的基于 HTML 的控制台
- 可自动执行多种操作的 Microsoft Graph API 支持
- Azure Active Directory (AD) 组提供跨所有 Azure 应用程序的兼容性
- 支持大多数新式 Web 浏览器

若要查找有关经典 Intune 控制台的文档，请参阅 [Intune 文档库](https://docs.microsoft.com/intune-classic/)。

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
本部分包含有关 Intune 的[新增功能](whats-new.md)、[已知问题](known-issues.md)、[如何获得支持](get-support.md)和如何[开始使用免费试用版](free-trial-sign-up.md)的信息。
### <a name="plan-and-design"></a>规划和设计
帮助你[规划和设计](/intune-classic/plan-and-design/introduction) Intune 环境的信息。
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
[了解有关所管理的以及将资源分类到组的设备的用户](user-management.md)。
### <a name="groups"></a>组
[了解如何通过 Intune 使用 Azure Active Directory 组](groups-get-started.md)
### <a name="intune-roles"></a>Intune 角色
[控制可以执行各种 Intune 操作的人员，以及这些操作适用的人员](role-based-access-control.md)。 可以使用涵盖一些常见 Intune 方案的内置角色，也可以创建自己的角色。
### <a name="software-updates"></a>软件更新
[了解如何配置 Windows 10 设备的软件更新](windows-update-for-business-configure.md)。



## <a name="whats-new"></a>新增功能

[了解预览版新增功能](whats-new.md)。

