---
title: "添加用户并授予权限 | Microsoft Docs"
description: "将本地用户与 Azure AD 同步，并授予对 Intune 订阅的管理员权限"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 4a90d0bdebafeb8a9e5c73892b6f1f11b76eb9f6
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="add-users-and-give-administrative-permission-to-intune"></a>添加用户并授予对 Intune 的管理权限

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本主题指导管理员如何向 Intune 添加用户以及 Intune 服务中可用的管理权限。

作为管理员，可直接添加用户或从本地 Active Directory 同步用户。 添加后，用户可注册设备并访问公司资源。 还可为用户提供更多权限，包括“租户管理员”、“服务管理员”和“设备注册管理器”权限。

本主题可帮助：

- [将用户添加到 Intune](#add-users-to-intune)
- [授予其他 Intune 权限](#grant-intune-permissions)，包括：
  - [租户管理员](#tenant-administrator)
  - [服务管理员](#service-administrator)
  - [设备注册管理器](#device-enrollment-managers)

## <a name="add-users-to-intune"></a>添加用户到 Intune
可通过 [Office 365 门户](http://go.microsoft.com/fwlink/p/?LinkId=698854)手动将用户添加到 Intune 订阅，但系统不会自动向这些用户分配 Intune 许可证。 相反，Intune 租户管理员必须稍后编辑用户帐户才能从 Office 365 门户中向用户分配许可证。 有关操作指南，请参阅[向 Office 365 门户逐一或批量添加用户](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec)。

### <a name="sync-active-directory-and-add-users-to-intune"></a>同步 Active Directory 并将用户添加到 Intune
可配置目录同步，将用户帐户从本地 Active Directory 导入到包含 Intune 用户的 Microsoft Azure Active Directory (Azure AD)。 让本地 Active Directory 服务与你所有基于 Azure Active Directory 的服务相连接，使管理用户标识变得更简单。 还可以配置单一登录功能，使用户的身份验证体验熟悉且简单。 通过将同一 [Azure AD 租户](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/)与多个服务相链接，先前同步的用户帐户便可用于所有基于云的服务。

### <a name="how-to-sync-on-premises-users-with-azure-ad"></a>如何使用 Azure AD 同步本地用户
使用 Azure AD 同步本地用户所需的唯一工具是 [Azure AD Connect 向导](https://www.microsoft.com/download/details.aspx?id=47594)。 Azure AD Connect 向导为将你的本地身份基础结构连接到云提供简化的指导式体验。  选择拓扑和需求（单个或多个目录、密码同步或联合身份验证），该向导将部署和配置连接和运行所需的所有组件。 其中包括：同步服务、Active Directory 联合身份验证服务 (AD FS) 和 Azure AD PowerShell 模块。

> [!TIP]
> Azure AD 连接包含之前作为目录同步和 Azure AD Sync 发布的功能。 了解有关[目录集成](http://technet.microsoft.com/library/jj573653.aspx)的详细信息。 若要了解有关将用户帐户从本地目录同步到 Azure AD 的好处，请参阅 [Active Directory 与 Microsoft Azure AD 的相似之处](http://technet.microsoft.com/library/dn518177.aspx)。

## <a name="grant-intune-permissions"></a>授予 Intune 权限

向 Intune 订阅中添加用户之后，我们建议为一些用户帐户授予管理权限。 若要管理 Intune，可向用户提供三种类型的 Intune 权限
-   **租户管理员**：使用 Office 365 门户分配此类型的管理员来管理订阅，包括帐单、云存储以及管理可使用 Intune 的用户。
-   **服务管理员**：使用 Microsoft Intune 管理控制台分配此类型的管理员来完成日常任务，包括设备和计算机管理、部署策略和应用，以及运行报表。
-   **设备注册管理器**：使用 Microsoft Intune 管理控制台分配此类型的管理员来完成日常任务，包括设备或计算机管理、部署策略和应用，以及运行报表。


### <a name="tenant-administrator"></a>租户管理员


将为租户管理员分配一个管理员角色，该角色定义用户的管理作用域以及他们可管理的任务。 尽管部分服务可能不会支持某些角色，但不同的 Microsoft 云服务之间会共用管理员角色。 Intune 使用以下角色：
- **全局管理员** - 访问 Intune 中的所有管理功能。 默认注册 Intune 的人员为全局管理员。 全局管理员是唯一可分配其他管理员角色的管理员。 在组织中可有多个全局管理员。 建议最好只向公司中的少数人授予此角色，以降低业务风险。
- **计费管理员** - 采购、管理订阅、管理支持票证并监视服务运行状况。
- **密码管理员** - 重置密码、管理服务请求并监视服务运行状况。 密码管理员仅限为用户重置密码。
- **服务支持管理员** - 打开 Microsoft 支持请求，并查看服务仪表板和消息中心。 除打开支持票证并读取外，他们还具有“仅查看”权限。
- **用户管理员** - 重置密码、监视服务运行状况、添加和删除用户帐户以及管理服务请求。 用户管理员不能删除全局管理员、创建其他管理员角色，或为计费、全局和服务管理员重置密码。

默认情况下，用于创建 Microsoft Intune 订阅的帐户是具有全局管理员角色的租户管理员。 作为租户管理员，使用 Intune 管理员控制台来管理 Intune 的订阅，并从 [Office 365 门户](http://go.microsoft.com/fwlink/p/?LinkId=698854)分配租户管理员。 使用具有全局管理角色的租户管理员访问门户，并分配第一个服务管理员。 最佳做法是，不要将租户管理员用于日常管理任务。 租户管理员不需要 Intune 的许可证即可访问 Intune 管理员控制台。 租户管理员是 Microsoft 云服务之间的一个公共概念。 订阅 Intune 时，服务就是 Azure AD 的一个租户。 有关详细信息，请参阅 [What is an Azure AD directory?](http://technet.microsoft.com/library/jj573650.aspx)（什么是 Azure AD 目录？）中的 Azure AD 租户部分。

作为租户管理员，使用 [Office 365 门户](http://go.microsoft.com/fwlink/p/?LinkId=698854)来管理订阅，包括下列任务（如果管理员角色允许）：

- 管理用户帐户，并从本地 Active Directory 配置目录同步
- 管理用户的组（称为安全组）
- 分配 Intune 用户许可证
- 为用户登录时使用的订阅配置域名（例如 contoso.com）
- 管理计费和采购，包括许可证和云存储空间
- 查找链接以查看 Intune 服务的运行状况

若要访问 Office 365 门户，帐户的登录状态必须为“已允许”。 此状态与拥有订阅许可证不同。 默认情况下，所有用户帐户均为“已允许”。 无管理员权限的用户可使用 Office 365 门户重置 Intune 密码。

### <a name="service-administrator"></a>服务管理员

默认情况下，Intune 不会分配服务管理员。 作为替代，你必须使用具有全局管理员角色的租户管理员来为订阅分配第一个服务管理员。 作为服务管理员，使用 [Intune 管理员控制台](https://manage.microsoft.com/)来管理 Intune 的日常任务。 你从管理员控制台分配服务管理员。 服务管理员需要 Intune 的许可证才能访问管理控制台。

将为服务管理员分配下列权限之一：
- **完全访问权限**：可不受限制地访问 Intune 管理员控制台中的所有区域，添加和管理其他服务管理员
- **只读访问权限**：对 Intune 管理员控制台中所有区域的读取权限，无法修改数据，但可运行报表
- **支持人员 - 组节点**：允许服务管理员仅执行与支持人员方案关联的任务，请参阅[根据管理员角色自定义 Intune 控制台视图](/intune-classic/deploy-use/control-what-admins-can-see-in-the-microsoft-intune-admin-console)

作为服务管理员，使用此门户来管理日常操作，其中包括：

- 为计算机和移动设备创建并管理策略
- 上传和部署软件更新和应用
- 管理计算机上的 Endpoint Protection
- 查看设备状态和运行报表

### <a name="device-enrollment-managers"></a>设备注册管理器

设备注册管理器是标准用户帐户，具有可注册更多无用户设备的额外权限。 默认情况下，每个 Intune 用户最多可注册 15 台设备。 作为管理员，可向用户账户授予设备注册管理器权限。 该帐户可注册大量企业自有设备。 当设备临时分配给用户或在展台模式（无需用户与设备关联）下运行时，这将非常有用。 有关详细信息，请参阅[设备注册管理器](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)。

>[!div class="step-by-step"]

>[&larr;**域设置**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**管理 Intune 许可证**&rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)  

