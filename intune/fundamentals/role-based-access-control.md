---
title: 使用 Microsoft Intune 的基于角色的访问控制 (RBAC)
description: 了解 RBAC 如何使你控制可执行操作并在 Microsoft Intune 中进行更改的人员。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6e9df15efc7a16a0ce1ee6b0412f9160831efdec
ms.sourcegitcommit: 884654da8e72a63bfaea6b5def6c7891b065f251
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163510"
---
# <a name="role-based-access-control-rbac-with-microsoft-intune"></a>使用 Microsoft Intune 的基于角色的访问控制 (RBAC)

基于角色的访问控制 (RBAC) 有助于管理有权访问组织资源的用户及其可以对这些资源执行的操作。  通过为 Intune 用户[分配角色](assign-role.md)，可以限制其可查看和更改的内容。 每个角色都有一组权限，用于确定具有该角色的用户可以在组织内访问和更改的内容。

若要创建、编辑或分配角色，你的帐户必须在 Azure AD 中具有以下权限之一：
- **全局管理员**
- Intune 服务管理员（也称为 Intune 管理员）  

有关 Intune RBAC 的建议和意见，可查看此系列的五个视频，它们展示了示例和演练：[1](https://www.youtube.com/watch?v=5deXLMLcnKY)、[2](https://www.youtube.com/watch?v=38dnMBLuxbQ)、[3](https://www.youtube.com/watch?v=6vqg9cAkMbY)、[4](https://www.youtube.com/watch?v=5yOLajFFMHE)、[5](https://www.youtube.com/watch?v=P5DDvsSF4Wk)。

## <a name="roles"></a>角色
角色定义授予分配给该角色的用户的权限集。
可以使用内置和自定义角色。 内置角色涵盖一些常见的 Intune 方案。 可以使用所需的确切权限集[创建自己的自定义角色](create-custom-role.md)。 一些 Azure Active Directory 角色具有对 Intune 的权限。
要查看角色，请选择“Intune” > “角色” > “所有角色”> 选择一个角色    。 你将看到以下页面：

- **属性**：角色的名称、说明、类型、分配和作用域标记。 
- **权限**：列出一组定义该角色具有哪些权限的开关。
- **分配**：[角色分配]( assign-role.md)列表，用于定义有权访问哪些用户/设备的用户。 一个角色可以有多个分配，并且一个用户可以位于多个分配中。

### <a name="built-in-roles"></a>内置角色
无需进一步配置，即可向组分配内置角色。 无法删除或编辑内置角色的名称、说明、类型或权限。

- **支持人员操作员**：对用户和设备执行远程任务，并可以将应用或策略分配到用户或设备。
- **策略和配置文件管理员**：管理符合性策略、配置文件、Apple 注册、企业设备标识符和安全性基线。
- **只读操作员**：查看用户、设备、注册、配置和应用信息。 无法更改 Intune。
- **应用管理员**：管理移动应用和托管应用，并可以读取设备信息和查看设备配置文件。
- **Intune 角色管理员**：管理自定义 Intune 角色，并添加内置 Intune 角色分配。 这是唯一可向管理员分配权限的 Intune 角色。
- **学校管理员**：管理 [Intune for Education](../introduction-intune-education.md) 中的 Windows 10 设备。

### <a name="custom-roles"></a>自定义角色
使用自定义权限，可以创建自己的角色。 有关自定义角色的详细信息，请参阅[创建自定义角色](create-custom-role.md)。

### <a name="azure-active-directory-roles-with-intune-access"></a>具有 Intune 访问权限的 Azure Active Directory 角色
| Azure Active Directory 角色 | 所有 Intune 数据 | Intune 审核数据 |
| --- | :---: | :---: |
| 全局管理员 | 读/写 | 读/写 |
| Intune 服务管理员 | 读/写 | 读/写 |
| 条件访问管理 | 无 | 无 |
| 安全管理员 | 只读 | 只读 |
| 安全操作员 | 只读 | 只读 |
| 安全性读者 | 只读 | 只读 |
| 合规性管理员 | 无 | 只读 |
| 符合性数据管理员 | 无 | 只读 |
| 全局读取者 | 只读 | 只读 |

> [!TIP]
> Intune 还显示三个 Azure AD 扩展：“用户”  、“组”  和“条件访问”  （使用 Azure AD RBAC 进行控制）。 此外，**用户帐户管理员**仅执行 AAD 用户/组活动，而不具备在 Intune 中执行所有活动的完全权限。 有关详细信息，请参阅 [RBAC 与 Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles)。
### <a name="roles-created-in-the-intune-classic-portal"></a>在 Intune 经典门户中创建的角色
只有拥有“完全”权限的 Intune 服务管理员  ，才能从 Intune 经典门户迁移到 Azure 门户中 Intune。 必须在 Azure 门户中向拥有“只读”或“支持人员”访问权限的 Intune 服务管理员  用户重新分配 Intune 角色，并将他们从经典门户中删除。
> [!IMPORTANT]
> 如果管理员仍需要有权使用 Intune 管理电脑，你可能需要保留经典门户中的 Intune 服务管理员访问权限。

## <a name="role-assignments"></a>角色分配
角色分配定义：

- 分配到角色的用户
- 用户可以使用的资源
- 用户可以更改的资源。

可以为用户分配自定义和内置角色。 用户必须有 Intune 许可证，才能分配有 Intune 角色。
要查看角色分配，请选择“Intune” > “角色” > “所有角色”> 选择一个角色 > 选择分配    。 你将看到以下页面：

- **属性**：分配的名称、说明、角色、成员、作用域和标记。
- **成员**：列出的 Azure 安全组中的所有用户都有权管理作用域（组）中列出的用户/设备。
- **作用域(组)** ：这些 Azure 安全组中的所有用户/设备都可以由“成员”中的用户管理。
- **[作用域(标记)](scope-tags.md)** ：成员中的用户可以查看具有相同作用域标记的资源。

### <a name="multiple-role-assignments"></a>多个角色分配
如果用户有多个角色分配、权限和作用域标记，这些角色分配会扩展到不同的对象，如下所示：

- 分配权限和作用域标记仅适用于相应角色的分配作用域（组）中的对象（如策略或应用）。 分配权限和作用域标记不适用于其他角色分配中的对象，除非其他分配专门授予它们。
- 其他权限（如“创建”、“读取”、“更新”、“删除”）和作用域标记适用于任何用户分配中相同类型的所有对象（如所有策略或所有应用）。
- 不同类型对象（如策略或应用）的权限和作用域标记彼此不适用。 例如，策略的读取权限不会为用户分配中的应用提供读取权限。

## <a name="next-steps"></a>后续步骤
- [向用户分配角色](assign-role.md)
- [创建自定义角色](create-custom-role.md)
