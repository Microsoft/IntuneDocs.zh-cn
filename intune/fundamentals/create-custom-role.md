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
ms.openlocfilehash: bfa2758546595d1e6237d88e128958c50759eb04
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569177"
---
# <a name="create-a-custom-role-in-intune"></a>在 Intune 中创建自定义角色

可创建自定义 Intune 角色，让其包含特定工作职能所需的全部权限。 例如，如果 IT 部门组管理应用程序、策略和配置的配置文件，则可以在一个自定义角色中添加所有这些权限。 创建自定义角色后，可将其[分配](assign-role.md)给需要这些权限的任何用户。

若要创建、编辑或分配角色，你的帐户必须在 Azure AD 中具有以下权限之一：
- **全局管理员**
- **Intune 服务管理员**

## <a name="to-create-a-custom-role"></a>若要创建自定义角色

1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“租户管理” > “角色” > “所有角色” > “创建”     。

2. 在“基本信息”页上，输入新角色的名称和说明，然后选择“下一步”   。

3. 在“权限”页上，选择要用于此角色的权限  。

4. 在“范围(标记)”页上，选择此角色的标记  。 此角色可访问同样具有这些标记的资源。 选择“下一步”  。

5. 完成后，在“查看 + 创建”页上，选择“创建”   。 新角色会显示在“Intune 角色 - 所有角色”  边栏选项卡上的列表中。

## <a name="copy-a-role"></a>复制角色

还可以复制现有角色。

1. 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“租户管理” > “角色” > “所有角色”> 选择列表中的一个角色 >“复制”     。

2. 在“基本信息”页上，输入名称  。 确保使用唯一的名称。

3. 原始角色的所有权限和范围标记均已选中。 随后，可以更改重复角色的“名称”  、“说明”  、“权限”  和“范围(标记)”  。

4. 完成所需的所有更改后，选择“下一步”转到“查看 + 创建”页   。 选择“创建”。  

## <a name="next-steps"></a>后续步骤
- [向用户分配角色](assign-role.md)
- [详细了解 Intune 中基于角色的访问控制](role-based-access-control.md)


