---
title: "Azure 门户预览版中的 Intune 简介 | Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：获取有关 Azure 门户预览版中 Intune 的基础知识，以及它如何帮助你管理设备。"
keywords: 
author: robstackmsft
ms.author: robstack
nmanager: angrobe
ms.date: 01/08/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a085264-232a-4af0-97f1-747496c44517
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1024d2a33d843c628ffbb68f7b01a5d511191e7e
ms.openlocfilehash: f7f6dd79531d8d69eda3ed80bbb1cddf2692ab81


---


# <a name="introduction-to-microsoft-intune-in-the-azure-portal-preview"></a>Azure 门户预览版中的 Microsoft Intune 简介


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Microsoft Intune 正在向 Azure 门户迁移，这意味着你习惯使用的工作流和功能将发生改变。
新门户提供 Azure 门户中新功能和更新功能的预览，你可以在其中管理组织的移动设备、电脑和应用。
所有 Intune 功能最终都会迁移到 Azure，但现在可以在 Azure 门户中执行某些 Intune 任务。 由于此新体验是在预览版中，因此门户中可能尚不提供某些功能。 有关详细信息，请查看[预览版新增功能](#what's-new-in-the-preview)部分。

> [!IMPORTANT]
> **还没有看到新门户？**<br>
> 我们已经开始向选定的租户推出预览版。 现有租户将从 2017 年初开始迁移到新体验。 在租户迁移之前，你将在 Office 邮件中心收到通知。 如果对租户迁移的时间表有任何疑问，请通过 [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com) 联系我们的迁移团队。


可以在此库中找到新的产品文档，并且它将在预览期间不断更新。 如果你想提出建议，请在主题评论中留下反馈。 我们很乐意倾听你的想法。

<!--- You can view the new Intune technical preview console in Azure at [portal.azure.com]. --->

新体验的亮点包括：

- 用于所有企业移动性 + 安全性 (EMS) 组件的集成控制台
- 基于 Web 标准构建的基于 HTML 的控制台
- 可自动执行多种操作的 Microsoft Graph API 支持
- Azure AD 组在所有 Azure 应用程序中提供兼容性
- 支持大多数新式 Web 浏览器

若要查找有关经典 Intune 控制台的文档，请参阅 [Intune 文档库](https://docs.microsoft.com/en-us/intune/)。

## <a name="before-you-start"></a>开始之前

若要使用 Azure 门户中的 Intune，必须拥有 Intune 管理员和租户帐户。 可以在[此处](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20)注册帐户。

## <a name="supported-web-browsers-for-the-azure-portal"></a>受 Azure 门户支持的 Web 浏览器

Azure 门户在大多数新式电脑、Mac 和平板电脑上都可以运行。 不支持移动电话。
目前，支持以下浏览器：

- Microsoft Edge（最新版本）
- Microsoft Internet Explorer 11
- Safari（最新版本，仅限 Mac）
- Chrome（最新版本）
- Firefox（最新版本）

有关支持的浏览器的最新信息，请参阅[此处](https://docs.microsoft.com/azure/azure-preview-portal-supported-browsers-devices)。

## <a name="whats-in-this-library"></a>这个库中有什么？

该文档反映了 Intune 门户的布局，有助于你轻松查找所需信息。

![Azure 门户工作负荷](./media/azure-portal-workloads.png)

<!--- ### Plan and design
Information to help you plan and design your Intune environment.
[Read more](/intune-azure/plan-and-design/get-started) --->
### <a name="enroll-devices"></a>注册设备
如何通过 Intune 管理设备。
[了解详细信息](/intune-azure/enroll-devices/what-is)
### <a name="devices--groups"></a>设备和组
了解使用清单和报表管理的设备。
[了解详细信息](/intune-azure/manage-devices/what-is)
### <a name="manage-users"></a>管理用户
了解你管理的设备的用户。
[了解详细信息](/intune-azure/manage-users/what-is)
### <a name="manage-apps"></a>管理应用
包含有关如何发布、管理、配置和保护应用的信息。
[了解详细信息](/intune-azure/manage-apps/what-is-app-management)
### <a name="configure-devices"></a>配置设备
包含有关可用于在你管理的设备上配置设置和功能的配置文件的信息。
[了解详细信息](/intune-azure/configure-devices/what-are-device-profiles)
### <a name="set-device-compliance"></a>设置设备合规性
为设备定义符合性级别，然后报告不符合要求的任何设备 [了解详细信息](/intune-azure/set-device-compliance/what-is-device-compliance)
### <a name="conditional-access"></a>条件性访问
根据指定的条件限制对 Exchange 服务的访问。
[了解详细信息](/intune-azure/conditional-access/what-is-conditional-access)
### <a name="access-control"></a>访问控制
控制可以执行各种 Intune 操作的人员，以及这些操作适用的人员。 可以使用涵盖一些常见 Intune 方案的内置角色，也可以创建自己的角色。
[了解详细信息](/intune-azure/access-control/role-based-access-control)


## <a name="whats-new"></a>新增功能

[了解预览版新增功能](/intune-azure/introduction/whats-new)。


<!--HONumber=Feb17_HO1-->


