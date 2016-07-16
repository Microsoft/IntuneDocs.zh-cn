---
title: "同步 Active Directory 并将用户添加到 Intune | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed26d65b98a0ae1bbc4fbac682fb53fddd50b4e5
ms.openlocfilehash: 70a2d32de67f0a69bbc29ca68a1c831c9cf38796


---


# 同步 Active Directory 并将用户添加到 Intune
你可以配置目录同步，将用户帐户从本地 Active Directory 导入到 Microsoft Azure Active Directory (Azure AD)。 让本地 Active Directory 服务与你所有基于 Azure Active Directory 的服务相连接，使管理用户标识变得更简单。 还可以配置单一登录功能，使用户的身份验证体验熟悉且简单。

当你使用具有相同 [Azure AD 租户](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant)的多个服务时，以前同步的用户帐户可供共享同一个 Azure AD 租户订阅的所有基于云的服务使用，这使得操作更加简单。

## 使用 Azure AD 同步本地用户
使用 Azure AD 同步本地用户所需的唯一工具是 [Azure AD Connect 向导](https://www.microsoft.com/download/details.aspx?id=47594)。 Azure AD Connect 向导为将你的本地身份基础结构连接到云提供简化的指导式体验。  选择拓扑和需求（单个或多个目录、密码同步或联合身份验证），该向导将部署和配置连接和运行所需的所有组件。 其中包括：同步服务、Active Directory 联合身份验证服务 (AD FS) 和 Azure AD PowerShell 模块。

> [!TIP]
> Azure AD 连接包含之前作为目录同步和 Azure AD Sync 发布的功能。 了解有关[目录集成](http://technet.microsoft.com/library/jj573653.aspx)的详细信息。 若要了解有关将用户帐户从本地目录同步到 Azure AD 的好处，请参阅 [Active Directory 与 Microsoft Azure AD 的相似之处](http://technet.microsoft.com/library/dn518177.aspx)。

## 授予管理员权限
向 Intune 订阅中添加用户之后，我们建议为一些用户帐户授予[管理凭据](administrative-accounts-websites-perms.md)。 用于分配管理凭据的控制台取决于你要分配的管理员的类型：

-   **租户管理员**：使用 **[!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)]** 分配此类型的管理员来管理你的订阅，包括帐单、云存储以及管理可使用 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 的用户。

-   **服务管理员**：使用 **[!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)]** 分配此类型的管理员来完成日常任务，包括管理移动设备或计算机、部署策略或软件，以及运行报表。


### 后续步骤
祝贺你！ 你刚刚完成了 *Intune 快速入门指南*的步骤 3。

>[!div class="step-by-step"]

>[&larr;**域设置**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**管理 Intune 许可证**&rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)  



<!--HONumber=Jun16_HO4-->


