---
title: 在 Intune 中创建自定义角色
description: 了解如何在 Microsoft Intune 中创建自定义角色。
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
ms.openlocfilehash: 3ca83287c58f8d2fb7c8eec5f8cc793e2c67b77a
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390707"
---
# <a name="create-a-custom-role-in-intune"></a>在 Intune 中创建自定义角色

可创建自定义 Intune 角色，让其包含特定工作职能所需的全部权限。 例如，如果 IT 部门组管理应用程序、策略和配置的配置文件，则可以在一个自定义角色中添加所有这些权限。 创建自定义角色后，可将其[分配](assign-role.md)给需要这些权限的任何用户。

若要创建、编辑或分配角色，你的帐户必须在 Azure AD 中具有以下权限之一：
- **全局管理员**
- **Intune 服务管理员**

## <a name="to-create-a-custom-role"></a>若要创建自定义角色

1. 使用 Intune 凭据登录 [Azure 门户](https://portal.azure.com)。

2. 从左侧菜单中选择“所有服务”，然后在文本框筛选器中键入 Intune   。

3. 选择“Intune”   > “角色”   > “所有角色”   > “添加”  。

4. 在“添加自定义角色”  边栏选项卡上，输入新角色的名称和说明，然后单击“权限”  。

5. 在“权限”  边栏选项卡上，选择要用于此角色的权限。

6. 在“范围(标记)”边栏选项卡上，选择此角色的标记  。 此角色可访问同样具有这些标记的资源。

7. 完成后，选择“确定”  。

8. 在“添加自定义角色”  边栏选项卡上，单击“创建”  。 新角色会显示在“Intune 角色 - 所有角色”  边栏选项卡上的列表中。


## <a name="copy-a-role"></a>复制角色

还可以复制现有角色。

1. 使用 Intune 凭据登录 [Azure 门户](https://portal.azure.com)并选择“Intune”  。

2. 选择“角色”   > “所有角色”  >“选择列表中的一个角色”>“重复”  。

3. 在“重复角色”  下，输入名称。 确保使用唯一的名称。

4. 原始角色的所有权限和范围标记均已选中。 随后，可以更改重复角色的“名称”  、“说明”  、“权限”  和“范围(标记)”  。

5. 选择“创建”  。 

## <a name="next-steps"></a>后续步骤
- [向用户分配角色](assign-role.md)
- [详细了解 Intune 中基于角色的访问控制](role-based-access-control.md)
