---
title: 在 Microsoft Intune 中创建组
titleSuffix: ''
description: 将用户归组，以便更轻松地管理其可访问的策略和应用。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 39a93fb5-d318-4997-a409-b64549a00e7a
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: fcf6f3071e50304216a182a21dd542cace1b6390
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186454"
---
# <a name="create-a-group-to-manage-your-users-and-data-access"></a>创建组来管理用户和数据访问

使用组来管理用户并控制员工对公司资源的访问。 这些资源可能为目录的一部分或 SaaS 应用或 SharePoint 站点等外部资源。

Microsoft Intune 使用 Azure Active Directory (Azure AD) 管理公司资源的访问权限。 此访问权限通过目录中的角色进行控制。 然后，Intune 为移动设备管理此访问权限，以允许该组成员访问资源。

## <a name="how-do-i-create-a-group"></a>如何创建组？

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 打开“Microsoft Intune”窗格后，选择“组”。
4. 在“用户和组 – 所有组”窗格上，选择“新建组”命令。
5. 在“组”窗格上，选择“组类型”。
5. 为组选择名称和描述。
6. 将“成员身份类型”设置为“已分配”。 请不要为测试组**启用 Office 功能**。
7. 为组选择成员。
7. 单击“创建”。

如果已成功创建一个组，该组应显示在“所有组”列表中。 如果未在其中显示，请尝试创建另一个组。

## <a name="next-steps"></a>后续步骤

[策略入门](get-started-policies.md) - 通过创建策略防止用户使用其设备进行未授权的操作。

## <a name="learn-more"></a>了解详细信息

* [在 Intune 中使用组设置注册限制](groups-add.md)
* [使用 Azure Active Directory 中的组管理公司资源访问权限](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
