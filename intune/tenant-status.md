---
title: Microsoft Intune 租户状态页面
titleSuffix: Microsoft Intune
description: 使用 Intune 租户状态页可以在不离开 Intune 门户的情况下查看重要的租户详细信息
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2d3b6aeb7efc60d32891f4b1c69b387a61a2bc25
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2019
ms.locfileid: "66040513"
---
# <a name="intune-tenant-status-page"></a>Intune 租户状态页面
“租户状态”页是一个集中式中心，可在其中查看有关租户的当前信息和重要详细信息。 详细信息包括许可证可用性及其使用、连接器状态以及有关 Intune 服务的重要通信。  

若要查看仪表板，请在 Azure 门户中转到“Intune”>“租户状态”。  租户状态下将出现“帮助和支持组”。  

该页面分为四个区域：

## <a name="tenant-details"></a>租户详细信息
租户详细信息区域清晰明了地提供了有关租户的信息。 查看租户名称和位置、MDM 机构和租户服务发行版号等详细信息。 服务版本号是一个链接，可用于打开 Microsoft Docs 的“Intune 中的新增功能”一文。在“新增功能”中，可阅读有关 Intune 服务的最新功能和更新。  

本部分还提供有关可用许可证和分配给用户的许可证数量的基本信息。 未显示设备许可证。

## <a name="connector-status"></a>连接器状态
连接器状态是一站式位置，用于查看 Intune 的所有可用连接器的状态。  

连接器是：
- **配置到外部服务的连接**。 例如，Apple Volume Purchase Program 服务或 Windows Autopilot 服务。  此类连接器的状态基于上次成功的同步时间。
- 连接到外部非托管服务所需的证书或凭据，例如 Apple Push Notification Services (APNS) 证书。 此类连接器的状态基于证书或凭证的到期时间戳。  

默认情况下，屏幕将最多显示五个连接器。 可以选择“查看所有连接器”展开此列表，查看所有可用连接器，包括尚未配置使用的连接器。  

运行不正常的连接器始终显示在列表的顶部。 接着是带警告的连接器，然后是正常运行的连接器的列表。 尚未配置的连接器会最后显示。

如果任何一种类型的连接器不止一个，状态则为所有此类连接器的汇总。 任何单个连接器的非正常运行状态将用作组的运行状况。  

**连接器状态：**
- **运行不正常：**
    - 证书或凭据已过期
    - 上次同步是在三天或更多天前
- **警告：**
    - 证书或凭据将在七天内到期
    - 距离上次同步已超过一天
- **正常运行：**
    - 证书或凭据在接下来的七天内不会到期
    - 距离上次同步还不到一天  

从列表中选择连接器时，门户将显示与创建或配置该连接器相关的门户页面。  例如，选择“VPP 到期日期”连接器时，将打开“iOS 批量采购计划令牌”页面，可以在其中查看有关该连接器的更多详细信息。 然后，可以创建新配置或编辑和修复现有配置中的问题。  

## <a name="intune-service-health"></a>Intune 服务运行状况  
无需导航到位于 [Microsoft 365 管理中心](https://admin.microsoft.com)的 Microsoft 365 服务运行状况仪表板或消息中心，即可查看活动事件和建议的详细信息。 仅显示已发现影响租户的事件。  

选择事件时，事件详细信息将直接显示在“租户状态”页面中。 若要查看过去的建议和事件，请选择“查看过去的事件/建议”。 随即打开 Microsoft 365 管理中心，然后可以查看租户过去 30 天内的建议和事件。  

要查看“Intune 服务运行状况”的信息，你的帐户必须在 Azure Active Directory 或 Microsoft 365 管理中心具有“全局管理员”或“服务管理员”角色。 若要分配这些权限，请使用全局管理员权限登录 [Microsoft 365 管理中心](https://admin.microsoft.com)。 选择“用户”>“活动用户”，然后选择需要访问权限的帐户。 选择角色的“编辑”，选择“服务管理员”或“全局管理员”，然后“保存”所做的编辑以分配该权限。  

仅可以通过 Microsoft 365 管理中心设置 Intune 服务运行状况的通信首选项。

## <a name="intune-news"></a>Intune 新闻  
无需导航到 Office 消息中心，即可查看来自 Intune 服务团队的信息性通信。 通信内容包括最近发生在 Intune 服务上的更改或者租户即将产生的更改的相关消息。  

默认情况下，显示最后 10 个活动消息。 要查看更早的消息，请选择“查看之前的消息”，在 Microsoft 365 管理中心打开“消息中心”。  

要查看“Intune 新闻”的信息，你的帐户必须在 Azure Active Directory 中具有“全局管理员”或“服务管理员”角色；或者在 Microsoft 365 管理中心具有“消息中心读取者”角色。  若要分配此权限，请使用管理员权限登录 [Microsoft 365 管理中心](https://admin.microsoft.com)。 选择“用户”>“活动用户”，然后选择需要访问权限的帐户。 选择角色的“编辑”，选择“团队通信管理员”，然后“保存”所做的编辑以分配该权限。  

仅可以通过 Microsoft 365 管理中心为 Intune 新闻设置通信首选项。
