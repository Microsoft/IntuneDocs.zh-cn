---
title: "同步 Active Directory 并将用户添加到 Intune | Microsoft Intune"
description: "将本地用户与 Azure AD 同步，并授予对 Intune 订阅的管理员权限"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 29b6e5a3d319c741482fcc2b600842e2e42b96e2
ms.openlocfilehash: 33534c685ad3a4ddfd4b605e088132f2b8ff2c36


---


# <a name="sync-active-directory-and-add-users-to-intune"></a>同步 Active Directory 并将用户添加到 Intune
你可以配置目录同步，将用户帐户从本地 Active Directory 导入到 Microsoft Azure Active Directory (Azure AD)。 让本地 Active Directory 服务与你所有基于 Azure Active Directory 的服务相连接，使管理用户标识变得更简单。 还可以配置单一登录功能，使用户的身份验证体验熟悉且简单。

当你使用具有相同 [Azure AD 租户](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/)的多个服务时，以前同步的用户帐户可供共享同一个 Azure AD 租户订阅的所有基于云的服务使用，这使得操作更加简单。

## <a name="synchronize-on-premises-users-with-azure-ad"></a>使用 Azure AD 同步本地用户
使用 Azure AD 同步本地用户所需的唯一工具是 [Azure AD Connect 向导](https://www.microsoft.com/download/details.aspx?id=47594)。 Azure AD Connect 向导为将你的本地身份基础结构连接到云提供简化的指导式体验。  选择拓扑和需求（单个或多个目录、密码同步或联合身份验证），该向导将部署和配置连接和运行所需的所有组件。 其中包括：同步服务、Active Directory 联合身份验证服务 (AD FS) 和 Azure AD PowerShell 模块。

> [!TIP]
> Azure AD 连接包含之前作为目录同步和 Azure AD Sync 发布的功能。 了解有关[目录集成](http://technet.microsoft.com/library/jj573653.aspx)的详细信息。 若要了解有关将用户帐户从本地目录同步到 Azure AD 的好处，请参阅 [Active Directory 与 Microsoft Azure AD 的相似之处](http://technet.microsoft.com/library/dn518177.aspx)。

## <a name="grant-administrator-permissions"></a>授予管理员权限

若要管理 Intune，你将使用：
- 两种类型的管理员帐户
- 具有额外权限的用户帐户
- 两个基于 Web 的管理控制台/门户，为你的管理员授予他们应管理的内容的访问权限。

向 Intune 订阅中添加用户之后，我们建议为一些用户帐户授予管理凭据。 用于分配管理凭据的控制台取决于你要分配的管理员的类型：

-   **租户管理员**：使用 **Microsoft Intune 帐户门户**分配此类型的管理员来管理你的订阅，包括帐单、云存储以及管理可使用 Intune 的用户。

-   **服务管理员**：使用 **Microsoft Intune 管理控制台**分配此类型的管理员来完成日常任务，包括管理移动设备或计算机、部署策略或软件，以及运行报表。

下列部分介绍了这些帐户和门户。

## <a name="administrator-accounts-and-user-accounts-with-special-permissions"></a>管理员帐户和具有特殊权限的用户帐户

以下将用于 Intune 的帐户和权限。

### <a name="tenant-administrator"></a>租户管理员
|权限级别|更多信息|
|--------------------------|-------------------------|
|将为租户管理员分配一个管理员角色，该角色定义用户的管理作用域以及他们可管理的任务。<br /><br />尽管部分服务可能不会支持某些角色，但不同的 Microsoft 云服务之间会共用管理员角色。<br /><br /> Microsoft Intune 使用以下角色：<br /><br />- 全局管理员<br />- 帐务管理员<br />- 密码管理员<br />- 服务支持管理员<br />-“用户管理”管理员|默认情况下，用于创建 Microsoft Intune 订阅的帐户是具有全局管理员角色的租户管理员。<br /></br>  作为租户管理员，你使用 [!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)] 来管理 Intune 的订阅并从 [!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)] 分配租户管理员。<br /><br />使用具有全局管理角色的租户管理员访问 [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)]以分配第一个服务管理员。 最佳做法是，不要将租户管理员用于日常管理任务。 租户管理员不需要 Intune 的许可证即可访问 [!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)]。<br /><br />租户管理员是 Microsoft 云服务之间的一个公共概念。 当订阅 Intune 时，你的服务就是 Microsoft Azure AD 的一个租户。 请参阅[什么是 Azure AD 目录？](http://technet.microsoft.com/library/jj573650.aspx)中的 Azure AD 租户部分。|


### <a name="service-administrator"></a>服务管理员
|权限级别|更多信息|
|--------------------------|-------------------------|
|将为服务管理员分配下列权限之一：<br /><br />**完全访问**：授予对 [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] 的所有区域的访问权限，不带任何限制。 可以添加和管理其他服务管理员。<br /><br />**只读访问**：授予对 [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] 的所有区域的读取权限。 只读服务管理员无法修改数据，但可以运行报表。<br /><br />**支持人员 - 组节点**：授予使服务管理员仅执行一系列通常与支持人员场景关联的任务的权限。 有关此权限集的信息，请参阅[根据管理员角色自定义 Intune 控制台视图](/intune/deploy-use/control-what-admins-can-see-in-the-microsoft-intune-admin-console)。|默认情况下，Intune 不会分配服务管理员。 作为替代，你必须使用具有全局管理员角色的租户管理员来为订阅分配第一个服务管理员。 </br></br> 作为服务管理员，你使用 [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] 来管理 Intune 的日常任务。<br /><br />你从管理员控制台分配服务管理员。 服务管理员需要 Intune 的许可证，之后帐户才能访问管理控制台。|



### <a name="device-enrollment-managers"></a>设备注册管理器
|权限级别|更多信息|
|--------------------------|-------------------------|
|设备注册管理器是标准用户帐户，其拥有可注册超过五台设备的额外权限。|默认情况下，每个 [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] 用户可以最多注册五台设备。 但是，你可为用户帐户提供设备注册管理器权限，然后使用此帐户注册大量公司拥有的设备。 当设备临时分配给用户或在展台模式（无需用户与设备关联）下运行时，这将非常有用。|




>[!div class="step-by-step"]

>[&larr;**域设置**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**管理 Intune 许可证**&rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)  



<!--HONumber=Nov16_HO4-->


