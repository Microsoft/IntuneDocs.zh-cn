---
title: Microsoft Intune 租户状态页面
titleSuffix: Microsoft Intune
description: 使用 Intune 租户状态页可以在不离开 Intune 门户的情况下查看重要的租户详细信息
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: 7954a686-25dc-4fce-b395-324816f46d3b
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c79f24d44ad0aed78ed0ae6fce0873a080b2904d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504842"
---
# <a name="use-the-intune-tenant-status-page"></a>使用 Intune 租户状态页面
Microsoft Intune“租户状态”页是一个集中式中心，可在其中查看有关租户的当前信息和重要详细信息。 详细信息包括许可证可用性及其使用、连接器状态以及有关 Intune 服务的重要通信。  

若要查看仪表板，请登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)，然后选择“租户状态”  。  “帮助和支持”下显示“租户状态”   。  

该页分为三个选项卡：

## <a name="tenant-details"></a>租户详细信息
租户详细信息区域清晰明了地提供了有关租户的信息。 查看租户名称和位置、MDM 机构和租户服务发行版号等详细信息。 服务版本号是一个链接，可用于打开 Microsoft Docs 的“Intune 中的新增功能”一文  。在“新增功能”中，可阅读有关 Intune 服务的最新功能和更新  。  

在此选项卡上，还可以找到有关可用许可证和分配给用户的许可证数量的基本信息。 未显示设备许可证。

## <a name="connector-status"></a>连接器状态
连接器状态是一站式位置，用于查看 Intune 的所有可用连接器的状态。  

连接器是：
- **配置到外部服务的连接**。 例如，Apple Volume Purchase Program 服务或 Windows Autopilot 服务   。  此类连接器的状态基于上次成功的同步时间。
- 连接到外部非托管服务所需的证书或凭据，例如 Apple Push Notification Services (APNS) 证书   。 此类连接器的状态基于证书或凭证的到期时间戳。  

打开“连接器状态”  选项卡时，列表顶部将显示所有运行不正常的连接器。 接着是带警告的连接器，然后是正常运行的连接器的列表。 尚未配置的连接器最后显示为“未启用”  。

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

从列表中选择连接器时，门户将显示与该连接器相关的门户页面。 在连接器页中，可以查看以前配置的连接器的状态，或选择用于添加或创建该类型的新连接器的选项。

例如，如果选择“VPP 到期日期”连接器，将打开“iOS 批量采购计划令牌”页面，可以在其中查看有关该连接器的更多详细信息   。 还可以创建新配置或编辑和修复现有配置中的问题。

## <a name="service-health-dashboard"></a>服务运行状况仪表板  
在“服务运行状况”仪表板上，可以查看影响租户的“服务事件”  的详细信息，以及提供有关更新和计划更改的信息的“Intune 新闻”  。

### <a name="intune-service-health"></a>Intune 服务运行状况
无需导航到位于 [Microsoft 365 管理中心](https://admin.microsoft.com)的 Microsoft 365 服务运行状况仪表板或消息中心，即可查看活动事件和建议的详细信息。 仅显示影响租户的事件。  

选择事件时，事件详细信息将直接显示在“租户状态”页面中。 若要查看过去的建议和事件，请选择“查看过去的事件/建议”  。 随即打开 Microsoft 365 管理中心，然后可以查看租户过去 30 天内的建议和事件。  

要查看“Intune 服务运行状况”的信息，你的帐户必须在 Azure Active Directory 或 Microsoft 365 管理中心具有“全局管理员”或“服务管理员”角色    。 若要分配这些权限，请使用全局管理员权限登录 [Microsoft 365 管理中心](https://admin.microsoft.com)。 选择“用户”>“活动用户”，然后选择需要访问权限的帐户  。 选择角色的“编辑”，选择“服务管理员”或“全局管理员”，然后“保存”所做的编辑以分配该权限     。  

仅可以通过 Microsoft 365 管理中心设置 Intune 服务运行状况的通信首选项。

### <a name="intune-news"></a>Intune 新闻  
无需导航到 Office 消息中心，即可查看来自 Intune 服务团队的信息性通信。 通信内容包括最近发生在 Intune 服务上的更改或者租户即将产生的更改的相关消息。  

默认情况下，将显示最新的 10 条活动消息。 要查看更早的消息，请选择“查看之前的消息”，在 Microsoft 365 管理中心打开“消息中心”   。  

要查看“Intune 新闻”的信息，你的帐户必须在 Azure Active Directory 中具有“全局管理员”或“服务管理员”角色；或者在 Microsoft 365 管理中心具有“消息中心读取者”角色    。  若要分配此权限，请使用管理员权限登录 [Microsoft 365 管理中心](https://admin.microsoft.com)。 选择“用户”>“活动用户”，然后选择需要访问权限的帐户  。 选择角色的“编辑”，选择“团队通信管理员”，然后“保存”所做的编辑以分配该权限     。  

仅可以通过 Microsoft 365 管理中心为 Intune 新闻设置通信首选项。
