---
title: "技术支持疑难解答门户"
titleSuffix: Intune on Azure
description: "技术支持人员使用疑难解答门户来解决用户的技术问题"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 05/30/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: fcf14d2ed8a91f37ad286c84df889d02cbf7063e
ms.contentlocale: zh-cn
ms.lasthandoff: 06/08/2017

---
# <a name="help-users-with-the-troubleshooting-portal-in-microsoft-intune"></a>使用 Microsoft Intune 中的疑难解答门户帮助用户

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

疑难解答门户允许技术支持人员和 Intune 管理员查看用户及其设备，并执行任务以解决 Intune 技术问题。

## <a name="add-help-desk-operators"></a>添加技术支持人员
Intune 管理员可以向技术支持人员分配用户权限。 然后，技术支持用户可以查看 Intune 门户，但无法查看或执行疑难解答工作负荷以外的管理任务。

1. 以 Intune 管理员身份登录到 Intune 门户，并选择“Intune 角色”。
3. 在“Intune 角色”工作负荷中，选择“技术支持人员”，然后选择“分配”。
4. 键入“分配名称”（必需）、“分配说明”（可选），然后分配“成员（组）”和“作用域（组）”。
5. 技术支持人员角色的成员现在可以使用疑难解答门户。

有关 Intune 角色的详细信息，请参阅“Intune 角色 (RBAC)”[](role-based-access-control.md)。

## <a name="access-the-troubleshooting-portal"></a>访问疑难解答门户

技术支持人员和 Intune 管理员可以使用两种方式访问疑难解答门户：
- 在 Intune 门户中，选择“疑难解答”。 其他工作负载显示在左侧导航边栏选项卡中，但无法选择。

![包含“选择用户”链接的 Intune“疑难解答”工作负载的屏幕截图](media/help-desk-user.png)
- 在 Web 浏览器中，打开 [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting)。 仅疑难解答门户可见。

## <a name="use-the-troubleshooting-portal"></a>使用疑难解答门户

在疑难解答门户中，可以选择“选择用户”以查看用户的信息。 用户信息可以帮助你了解用户及其设备的当前状态。 疑难解答门户显示以下疑难解答详细信息：
- **租户状态**
- **用户状态**
- **设备**
- **组成员身份**
- **应用保护状态**

技术支持人员还可以在设备上执行远程任务，如“远程锁定”。

