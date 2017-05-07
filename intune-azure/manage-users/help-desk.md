---
title: "技术支持疑难解答门户 | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "技术支持人员使用疑难解答门户来解决用户的技术问题"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 03/18/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e0ecc775f70703574c4e1adf0f0aa204f2745b72
ms.openlocfilehash: 723830f686991fe13de13f75c6a5d1bc84e6920b
ms.lasthandoff: 04/20/2017

---
# <a name="help-users-with-the-troubleshooting-portal-in-microsoft-intune"></a>使用 Microsoft Intune 中的疑难解答门户帮助用户

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

疑难解答门户允许技术支持人员和 Intune 管理员查看用户及其设备，并执行任务以解决 Intune 技术问题。

## <a name="add-help-desk-operators"></a>添加技术支持人员
Intune 管理员可以向技术支持人员分配用户权限。 然后，技术支持用户可以查看 Intune 门户，但无法查看或执行疑难解答工作负荷以外的管理任务。

1. 作为 Intune 管理员，登录到“Azure 门户”[](https:portal.azure.com)，选择“更多服务” > “监视 + 管理” > “Intune”。
2. 在左侧导航边栏选项卡中，选择“Intune 角色”。
3. 在“Intune 角色”工作负荷中，选择“技术支持人员”，然后选择“分配”。
4. 键入“分配名称”（必需）、“分配说明”（可选），然后分配“成员（组）”和“作用域（组）”。
5. 技术支持人员角色的成员现在可以使用疑难解答门户。

有关 Intune 角色的详细信息，请参阅“Intune 角色 (RBAC)”[](https://docs.microsoft.com/intune-azure/access-control/role-based-access-control)。

## <a name="access-the-troubleshooting-portal"></a>访问疑难解答门户

技术支持人员和 Intune 管理员可以使用两种方式访问疑难解答门户：
- 在“Azure 门户”[](https:portal.azure.com)中，选择“更多服务” > “监视 + 管理” > “Intune”，然后在左侧导航边栏中，选择“疑难解答”。 其他工作负荷在左侧导航边栏选项卡中可见，但不可用。
![选择用户链接的 Intune 疑难解答工作负荷的屏幕快照](media/help-desk-user.png)
- 在 Web 浏览器中打开 [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting)。 仅疑难解答门户可见。

## <a name="use-the-troubleshooting-portal"></a>使用疑难解答门户

在疑难解答门户中，可以选择“选择用户”以查看用户的信息。 用户信息可以帮助你了解用户及其设备的当前状态。 疑难解答门户显示以下 Intune 用户和设备详细信息：
- 用户帐户信息
- 用户组成员身份
- 设备详细信息

技术支持人员还可以在设备上执行远程任务，如“远程锁定”。

