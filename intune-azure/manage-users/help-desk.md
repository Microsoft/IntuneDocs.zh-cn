---
title: "支持人员疑难解答门户 | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "支持人员使用疑难解答门户解决用户遇到的技术问题"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 03/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: c8715f96f532ee6bacda231e1147d03226ecbb48
ms.openlocfilehash: 4916b66e1f2eeabb42401645dbece28dad28eb19
ms.contentlocale: zh-cn
ms.lasthandoff: 04/26/2017

---
# <a name="help-users-with-the-troubleshooting-portal-in-microsoft-intune"></a>通过 Microsoft Intune 中的疑难解答门户帮助用户

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

使用疑难解答门户，支持人员和 Intune 管理员可以查看用户及其设备，并执行任务来解决 Intune 技术问题。

## <a name="add-help-desk-operators"></a>添加支持人员
Intune 管理员可以向用户分配支持人员权限。 然后，技术支持用户可以查看 Intune 门户，但无法在疑难解答工作负载外查看或执行管理任务。

1. 以 Intune 管理员身份登录 [Azure 门户](https:portal.azure.com)，依次选择“更多服务” > “监视 + 管理” > “Intune”。
2. 在左侧导航边栏选项卡中，选择“Intune 角色”。
3. 在“Intune 角色”工作负载上，选择“支持人员”，然后选择“分配”。
4. 键入“分配名称”（必填）、“分配说明”（可选），然后分配“成员(组)”和“范围(组)”。
5. 现在，具有支持人员角色的成员可以使用疑难解答门户。

有关 Intune 角色的详细信息，请参阅 [Intune 角色 (RBAC)](https://docs.microsoft.com/intune-azure/access-control/role-based-access-control)。

## <a name="access-the-troubleshooting-portal"></a>访问疑难解答门户

支持人员和 Intune 管理员可以通过以下两种方法访问疑难解答门户：
- 在 [Azure 门户](https://portal.azure.com)中，依次选择“更多服务” > “监视 + 管理” > “Intune”，然后选择左侧导航边栏选项卡中的“疑难解答”。 其他工作负载显示在左侧导航边栏选项卡中，但无法选择。

![包含“选择用户”链接的 Intune“疑难解答”工作负载的屏幕截图](media/help-desk-user.png)
- 在 Web 浏览器中，打开 [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting)。 只能看见疑难解答门户。

## <a name="use-the-troubleshooting-portal"></a>使用疑难解答门户

在疑难解答门户中，可以选择“选择用户”查看用户信息。 用户信息有助于了解用户及其设备的当前状态。 疑难解答门户显示以下 Intune 用户和设备详细信息：
- 用户帐户信息
- 用户组成员身份
- 设备详细信息

技术支持用户还可以在设备上执行远程任务，如**远程锁定**。

