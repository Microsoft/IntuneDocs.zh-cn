---
# required metadata

title: Microsoft Intune 中的管理帐户、网站和权限 | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: db3075e7-38fd-4dfe-b266-26aed10ac8ea

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune 中的管理帐户、网站和权限

设置 Microsoft Intune 之前，请查看本主题以及[启动 Microsoft Intune 前须知](what-to-know-before-you-start-microsoft-intune.md)中列出的其他要求

若要管理 Intune，你将使用：
- 两种类型的管理员帐户
- 具有额外权限的用户帐户
- 两个基于 Web 的管理控制台/门户，为你的管理员授予他们应管理的内容的访问权限。

下列部分介绍了这些帐户和门户。

## 管理员帐户和具有特殊权限的用户帐户

以下帐户和权限将用于 Intune。

### 租户管理员
|权限级别|更多信息|
|--------------------------|-------------------------|
|将为租户管理员分配一个管理员角色，该角色定义用户的管理作用域以及他们可管理的任务。<br /><br />尽管部分服务可能不会支持某些角色，但不同的 Microsoft 云服务之间会共用管理员角色。<br /><br /> Microsoft Intune 使用以下角色：<br /><br />- 全局管理员<br />- 帐务管理员<br />- 密码管理员<br />- 服务支持管理员<br />-“用户管理”管理员|默认情况下，用于创建 Microsoft Intune 订阅的帐户是具有全局管理员角色的租户管理员。<br /></br>  作为租户管理员，你使用 [!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)]来管理 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 的订阅并从帐户门户分配租户管理员。<br /><br />使用具有全局管理角色的租户管理员访问 [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)]以分配第一个服务管理员。 最佳做法是，不要将租户管理员用于日常管理任务。 租户管理员不需要 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 的许可证即可访问<br /><br />租户管理员是 Microsoft 云服务之间的一个公共概念。 当你订阅 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 时，你的服务就是 Microsoft Azure AD 的一个租户。 请参阅[什么是 Azure AD 目录？](http://technet.microsoft.com/library/jj573650.aspx)中的 Azure AD 租户部分|


### 服务管理员
|权限级别|更多信息|
|--------------------------|-------------------------|
|将为服务管理员分配下列权限之一：<br /><br />**完全访问**：授予对 [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] 的所有区域的访问权限，不带任何限制。 可以添加和管理其他服务管理员。<br /><br />**只读访问**：授予对 [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] 的所有区域的读取权限。 只读服务管理员无法修改数据，但可以运行报表。<br /><br />**支持人员 - 组节点**：授予使服务管理员仅执行一系列通常与支持人员场景关联的任务的权限。 有关此权限集的信息，请参阅[根据管理员角色自定义 Intune 控制台视图](/intune/deploy-use/control-what-admins-can-see-in-the-microsoft-intune-admin-console)|默认情况下，[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 不会分配服务管理员。 作为替代，你必须使用具有全局管理员角色的租户管理员来为订阅分配第一个服务管理员。 </br></br> 作为服务管理员，你使用 [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)]来管理 Intune 的日常任务。<br /><br />你从管理员控制台分配服务管理员。 服务管理员需要 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 的许可证，之后帐户才能访问管理控制台。|



### 设备注册管理器
|权限级别|更多信息|
|--------------------------|-------------------------|
|设备注册管理器是标准用户帐户，其拥有可注册超过五台设备的额外权限。|默认情况下，每个 [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] 用户可以最多注册五台设备。 但是，你可为用户帐户提供设备注册管理器权限，然后使用此帐户注册大量公司拥有的设备。 当设备临时分配给用户或在展台模式（无需用户与设备关联）下运行时，这将非常有用。|


## Intune 的管理网站
 不同的管理任务要求你使用以下管理网站之一，这些网站可以通过[受支持的 Web 浏览器](supported-web-browsers.md)访问

- [Office 365 门户](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Microsoft Intune 管理员控制台](https://admin.manage.microsoft.com/)

### [Office 365 门户](http://go.microsoft.com/fwlink/p/?LinkId=698854)

**作为租户管理员，请使用此门户来管理你的订阅**，包括下列任务（如果你的管理员角色允许）：

- 管理订阅的用户帐户，并配置从本地 Active Directory 进行的目录同步。
- 管理用户的组（称为安全组）。
- 将使用 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 的许可证分配给用户。
- 配置用于订阅的域名。 域名定义用户登录所使用的帐户。
- 管理订阅的帐单和采购详细信息，包括你拥有的许可证的数量，或者可使用的云存储空间量。
- 查找链接以查看 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 服务的运行状况。
- 作为租户管理员，你可以登录到 Office 365 门户来管理订阅（即使没有为你的帐户分配使用 Intune 的许可证）。
- 拥有 Intune 许可证但不是管理员的任何用户都可使用此门户重置其帐户密码和编辑其配置文件。
- 若要访问 Office 365 门户，帐户的登录状态必须为“已允许”。 此状态与拥有订阅许可证不同。 默认情况下，所有用户帐户均为“已允许”


### [Microsoft Intune 管理员控制台](https://admin.manage.microsoft.com/)

**作为服务管理员，使用此门户来管理日常操作**，其中包括：

- 为计算机和移动设备设置策略。
- 上载和部署软件（如软件更新和应用）。
- 管理计算机上的 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Endpoint Protection。
- 查看设备状态和运行报表。
- 登录到此门户。 你必须拥有服务管理员权限或者是具有全局管理员角色的租户管理员，才能登录到此门户。


只有拥有服务管理员权限或者身份是具有全局管理员角色的租户管理员的用户才能登录到此门户。 若要访问管理控制台，你的帐户必须具有使用 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 的许可证，并且登录状态为“已允许”

详细了解[为你的订阅添加用户](start-with-a-paid-subscription-to-microsoft-intune-step-3.md)以及[为你的订阅分配许可证](start-with-a-paid-subscription-to-microsoft-intune-step-4.md)

 ### 另请参阅
 [启动 Microsoft Intune 前须知](what-to-know-before-you-start-microsoft-intune.md)


<!--HONumber=May16_HO2-->


