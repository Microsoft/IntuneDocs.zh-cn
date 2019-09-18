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
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0539e4d12173ba2c7ba8d3af3364daf69ddbbf34
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71071536"
---
# <a name="assign-a-role-to-an-intune-user"></a>向 Intune 用户分配角色

可向 Intune 用户分配[内置](role-based-access-control.md#built-in-roles)角色或[自定义](create-custom-role.md)角色。

若要创建、编辑或分配角色，你的帐户必须在 Azure AD 中具有以下权限之一：
- **全局管理员**
- **Intune 服务管理员**

有关每个内置角色的完整权限列表，请参阅 [Intune RBAC 表](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a)。

1. 登录到 [Azure 门户](https://portal.azure.com)。

2. 选择“所有服务” > “Intune”   。 Intune 位于“监视 + 管理”部分中  。

3. 在“Intune”  边栏选项卡上，选择“角色”   > “所有角色”  。

4. 在“Intune 角色 - 所有角色”  边栏选项卡上，选择要分配的内置角色。

5. 在“<角色名称  > - 概述”  边栏选项卡上，选择“管理”   > “分配”  。

6. 在“自定义角色”边栏选项卡，选择“分配”  。

7. 在“角色分配”  边栏选项卡上，输入分配的“分配名称”  和可选“分配说明”  。

8. 对于“成员(组)”  ，选择包含要对其授予权限的用户的组。

9. 对于“范围(组)”，选择包含上述成员将有权管理的用户/设备的组  。

10. 对于“范围(标记)”，选择将要应用此角色分配的标记  。

11. 完成后，选择“确定”  。 新分配将显示在分配列表中。


## <a name="next-steps"></a>后续步骤
- [详细了解 Intune 中基于角色的访问控制](role-based-access-control.md)
- [创建自定义角色](create-custom-role.md)
