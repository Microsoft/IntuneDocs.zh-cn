---
title: "组入门"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 39a93fb5-d318-4997-a409-b64549a00e7a
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 04843a918a3c661ab69dfa711f4d22a8feedf5f3
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2017
---
# <a name="get-started-with-groups"></a>组入门

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

[](./media/generic-users-groups.png)

Microsoft Intune 使用 Azure Active Directory (Azure AD) [管理公司资源的访问权限](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)。 此访问权限通过目录中的角色进行控制。 然后，Intune 为移动设备管理此访问权限，以允许该组成员访问资源。

__如何创建组？__

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 使用“搜索资源”，搜索“用户和组”。
3. 打开“用户和组”边栏选项卡后，选择“所有组”。
4. 在“用户和组 – 所有组”边栏选项卡上，选择“新建组”命令。
5. 在“组”边栏选项卡上，为组添加名称和说明。
6. 将“成员身份类型”设置为“已分配”。 请不要为测试组**启用 Office 功能**。
7. 单击“创建”。

如果已成功创建一个组，该组应显示在“所有组”列表中。 如果未在其中显示，请尝试创建另一个组。
