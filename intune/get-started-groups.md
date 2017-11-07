---
title: "组入门"
titleSuffix: Azure portal
description: "将用户归组，以便更轻松地管理其可访问的策略和应用。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 39a93fb5-d318-4997-a409-b64549a00e7a
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 964732be680273c62f341086ce23f0e40d981479
ms.sourcegitcommit: 94d3d86f8ae9f82a9872384bbaae53580036a4ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2017
---
# <a name="get-started-with-groups"></a>组入门

使用组来管理用户，并控制员工对公司资源的访问。 这些资源可能为目录的一部分或 SaaS 应用或 SharePoint 站点等外部资源。

Microsoft Intune 使用 Azure Active Directory (Azure AD) 管理公司资源的访问权限。 此访问权限通过目录中的角色进行控制。 然后，Intune 为移动设备管理此访问权限，以允许该组成员访问资源。

## <a name="how-do-i-create-a-group"></a>如何创建组？

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 使用“搜索资源”，搜索 Intune。
3. 打开“Microsoft Intune”边栏选项卡后，选择“组”。
4. 在“用户和组 – 所有组”边栏选项卡上，选择“新建组”命令。
5. 在“组”边栏选项卡上，为组添加名称和说明。
6. 将“成员身份类型”设置为“已分配”。 请不要为测试组**启用 Office 功能**。
7. 单击“创建”。

如果已成功创建一个组，该组应显示在“所有组”列表中。 如果未在其中显示，请尝试创建另一个组。

## <a name="next-steps"></a>后续步骤

[策略入门](get-started-policies.md) - 通过创建策略防止用户使用其设备进行未授权的操作。

## <a name="learn-more"></a>了解详细信息

* [在 Intune 中使用组设置注册限制](groups-add.md)
* [使用 Azure Active Directory 中的组管理公司资源访问权限](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
