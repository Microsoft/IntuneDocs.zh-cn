---
title: "Azure 门户中 Intune 的简介"
titlesuffix: Azure portal
description: "了解 Azure 门户中 Intune 的基础知识及其如何有助于管理设备。”"
keywords: 
author: arob98
ms.author: angrobe
nmanager: dougeby
ms.date: 02/14/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a085264-232a-4af0-97f1-747496c44517
ms.suite: ems
ms.custom: 
ms.openlocfilehash: 6e2528c243938e81a6f730a950ee3949ca44047c
ms.sourcegitcommit: cccbb6730a8c84dc3a62093b8910305081ac9d24
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/15/2018
---
# <a name="introduction-to-microsoft-intune-in-the-azure-portal"></a>Azure 门户中的 Microsoft Intune 简介


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

与其他 Azure 服务一样，Microsoft Intune 也可在 Azure 门户中使用。 通过在 Azure 门户中选择 Intune，可管理组织的移动设备、电脑和应用。

>[!NOTE] 
> 如果已使用以前版本的 Microsoft Intune，可参考以下信息：
    * [我的功能位于 Azure 的什么位置？](ui-changes.md)是一个参考，显示随着移动到 Azure 而更改的特定工作流程和 UI。
    * [Azure 门户中的 Intune 经典组](groups-get-started.md)解释了转移到 Azure Active Directory 安全组以进行组管理的含义。

Azure 门户中 Microsoft Intune 的重要功能包括：

- 用于所有企业移动性 + 安全性 (EMS) 组件的集成控制台
- 基于 Web 标准构建的基于 HTML 的控制台
- 可自动执行多种操作的 Microsoft Graph API 支持
- Azure Active Directory (AD) 组提供跨所有 Azure 应用程序的兼容性
- 支持大多数新式 Web 浏览器

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

## <a name="microsoft-intune-in-the-azure-portal"></a>Azure 门户中的 Microsoft Intune

可在 [Azure 门户](https://portal.azure.com)中找到 Microsoft Intune 服务。 Azure 提供多种服务，其中许多服务可能不会经常使用。 若要获取自定义门户体验的快速指南，请参阅[开始使用 Azure 门户中的 Intune](get-started-azure.md)。

## <a name="the-microsoft-intune-documentation"></a>Microsoft Intune 文档

本主题以及整个 Microsoft Intune 文档集将持续更新。 如果你有什么建议，请在主题评论中留下反馈。 我们很乐意倾听你的想法。

文档反映了 Microsoft Intune 在 Azure 门户中的布局（如下所示），可方便读者更轻松地找到所需信息。

![Azure 门户工作负荷](./media/azure-portal-workloads.png)

### <a name="documentation-guide"></a>文档指南

使用下表快速查找和了解 Microsoft Intune 的主要区域。

| 部分                                                      | 描述                                                                                                                                                                                                                                                                                      |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [简介和入门](introduction-intune.md)       | 了解 Intune 的基础知识，包括：<br /> - 常见解决方案<br /> - Microsoft Intune 工作原理<br /> - Intune 中的设备管理<br /> - Intune 中的应用管理<br /> - 企业移动性管理 (EMM)（需或无需设备注册）                                                         |
| [规划和设计](planning-guide.md)                         | 用于帮助成功规划和设计 Microsoft Intune 环境的指南。                                                                                                                                                                                                             |
| [设备注册](device-enrollment.md)                    | 了解如何使用 Microsoft Intune，通过将设备注册到 Intune 服务，帮助管理员工设备。 可通过几种方法来注册员工的设备。                                                                                                         |
| [设备符合性](device-compliance.md)                    | Intune 设备符合性策略定义设备必须遵从的规则和设置，以便将设备视为符合 Microsoft Intune。 例如，要求访问设备时提供密码、为设备加密、要求最低操作系统版本，这些都是实施符合性的例子。 |
| [设备配置](device-profiles.md)                   | 使用 Microsoft Intune，通过创建设备配置文件，配置所管理的所有设备上的设置和功能。 例如，可配置后列功能：通知、数据共享、电子邮件支持、wi-fi 连接、证书和终结点保护等。              |
| [设备](device-management.md)                              | 确保所管理的设备提供最终用户工作时所需的资源，同时保护公司数据免遭风险。 通过查看员工设备清单和执行远程设备操作来管理设备。                                                      |
| [移动应用](app-management.md)                             | 了解如何添加、部署、监视、配置和保护应用。                                                                                                                                                                                                                             |
| [条件性访问](conditional-access.md)                  | 定义基于设备和基于应用的条件，用于控制公司数据访问权限。                                                                                                                                                                                                            |
| [用户](users-add.md)                                        | 了解如何为所管理的设备和应用添加用户。                                                                                                                                                                                                                                           |
| [组](groups-get-started.md)                              | 了解如何使用 Intune 创建和管理组。 使用组，可快速分配设备和应用的配置和保护策略。                                                                                                                                             |
| [Intune 角色](role-based-access-control.md)                 | 了解如何控制可执行各种 Intune 操作的人员，以及这些操作的应用方式。 可以使用涵盖一些常见 Intune 方案的内置角色，也可以创建自己的角色。                                                                                 |
| [软件更新](windows-update-for-business-configure.md) | 了解如何配置 Windows 10 设备的软件更新。                                                                                                                                                                                                                                  |

## <a name="whats-new"></a>新增功能

若要了解有关 Microsoft Intune 的最新功能，请参阅[新增功能](whats-new.md)。
