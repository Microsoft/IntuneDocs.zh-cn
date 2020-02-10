---
title: 向 Intune 用户分配角色
description: 了解如何向 Microsoft Intune 中的用户分配内置角色或自定义角色。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 780a248f16a8a5028875c9c2401921ea23d0af24
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "76540922"
---
# <a name="assign-a-role-to-an-intune-user"></a>向 Intune 用户分配角色

可向 Intune 用户分配[内置](role-based-access-control.md#built-in-roles)角色或[自定义](create-custom-role.md)角色。

若要创建、编辑或分配角色，你的帐户必须在 Azure AD 中具有以下权限之一：
- **全局管理员**
- **Intune 服务管理员**

1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“租户管理”   > “角色”   > “所有角色”  。

2. 在“Intune 角色 - 所有角色”  边栏选项卡上，选择要分配的内置角色。

3. 在“<角色名称  > - 概述”  边栏选项卡上，选择“管理”   > “分配”  。

4. 在“自定义角色”边栏选项卡，选择“分配”  。

5. 在“角色分配”  边栏选项卡上，输入分配的“分配名称”  和可选“分配说明”  。

6. 对于“成员(组)”  ，选择包含要对其授予权限的用户的组。

7. 对于“范围(组)”，选择包含上述成员将有权管理的用户/设备的组  。

8. 对于“范围(标记)”，选择将要应用此角色分配的标记  。

9. 完成后，选择“确定”  。 新分配将显示在分配列表中。


## <a name="next-steps"></a>后续步骤
- [详细了解 Intune 中基于角色的访问控制](role-based-access-control.md)
- [创建自定义角色](create-custom-role.md)
