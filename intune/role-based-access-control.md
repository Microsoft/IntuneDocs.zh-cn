---
title: 基于角色的访问控制 (RBAC) 与 Microsoft Intune
description: 了解基于角色的访问控制 (RBAC) 如何使你能够控制可在 Microsoft Intune 中执行各种操作并进行更改的人员。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/27/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: edf17d98bb733f7567a615eec856fb7122ba251b
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2018
---
# <a name="role-based-administration-control-rbac-with-microsoft-intune"></a>基于角色的管理控制 (RBAC) 与 Microsoft Intune

RBAC 可以帮助你控制组织中哪些人员可执行各种 Intune 任务，以及这些任务适用于哪些人员。 可以使用涵盖一些常见 Intune 方案的内置角色，也可以创建自己的角色。 角色是根据以下几点定义的：

- **角色定义**：角色名称、其管理的资源和授予每个资源的权限。
- **成员**：获得授权的用户组。
- **范围**：成员可以管理的用户组或设备组。
- **作用域**：配置定义、成员和作用域后，将分配角色。

![Intune RBAC 示例](./media/intune-rbac-1.PNG)

从新的 Azure 门户开始，Azure Active Directory (Azure AD) 提供两个可用于 Intune 的目录角色。 这些角色被授予完全权限，可在 Intune 中执行所有活动：

- **全局管理员：**具有此角色的用户可访问 Azure AD 中的所有管理功能以及与 Azure AD 联合的服务（如 Exchange Online、SharePoint Online 和 Skype for Business Online）。 注册 Azure AD 租户的人员均将成为全局管理员。 只有全局管理员才能分配其他 Azure AD 管理员角色。 组织中可以有多个全局管理员。 全局管理员可以重置任意用户和所有其他管理员的密码。

- **Intune 服务管理员：**服务存在时，具有该角色的用户拥有 Intune 内的全局权限。 此外，除任何取代的 Azure 限制以外，此角色提供用于管理用户、设备，以及创建并管理 Intune 组的功能。

- 条件访问管理员：具有此角色的用户仅有权查看、创建、修改和删除条件访问策略。

    > [!IMPORTANT]
    > Intune 服务管理员角色不提供管理 Azure AD 条件性访问设置的功能。

    > [!TIP]
    > Intune 还显示三个 Azure AD 扩展：用户、组和条件访问，均使用 Azure AD RBAC 控制。 此外，**用户帐户管理员**仅执行 AAD 用户/组活动，而不具备在 Intune 中执行所有活动的完全权限。 请参阅[使用 Azure AD 的 RBAC](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles)获取详细信息。

## <a name="roles-created-in-the-intune-classic-portal"></a>在 Intune 经典门户中创建的角色

只有拥有“完全”权限的 Intune 服务管理员，才能从 Intune 经典门户迁移到 Azure 门户中 Intune。 你需要对 Azure 门户中的 Intune 角色重新分配具有“只读”或“支持人员”访问权限的 Intune **服务管理员**，并将其从经典门户中删除。

> [!IMPORTANT]
> 如果管理员仍需要有权使用 Intune 管理电脑，可能需要保留经典门户中的 Intune 服务管理员访问权限。

## <a name="built-in-roles"></a>内置角色

以下角色内置在 Intune 中，无需做更多配置即可将它们分配到组：

- 技术支持人员：对用户和设备执行远程任务，并可以将应用程序或策略分配给用户或设备。
- 策略和配置文件管理员：管理符合性策略、配置的配置文件、Apple 注册和企业设备标识符。
- 只读操作员：查看用户、设备、注册、配置和应用程序信息。 不能对 Intune 进行更改。
- **应用程序管理员**：管理移动和托管应用程序，并可以读取设备信息。
- **学校管理员**：在 [Intune for Education](introduction-intune-education.md) 中管理 Windows 10 设备并且可以执行以下操作： 

|权限|操作|
|---|---|
|审核数据|读取|
|DeviceConfigurations|分配、创建、删除、读取、更新|
|设备注册管理器|读取、更新|
|托管设备|读取、更新<!--, Delete [To be added in 1803]-->|
|移动应用|分配、创建、删除、读取、更新|
|Reports|读取|
|远程操作|清理电脑、重启、远程锁定、停用、同步设备、擦除|
|组织|读取|

### <a name="to-assign-a-built-in-role"></a>若要分配一个内置角色

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 在“Intune”窗格上，选择“Intune 角色”，然后选择“所有角色”。
1. 在“Intune 角色 - 所有角色”窗格上，选择要分配的内置角色。

2. 在<角色名称> -“概述”窗格上，依次选择“管理”、“分配”。

    > [!NOTE]
    > 无法删除或编辑内置角色

3. 在“自定义角色”窗格上，选择“分配”。

4. 在“角色分配”窗格上，输入分配的“名称”和可选“说明”，然后选择以下各项：
    - **成员** - 选择包含想要对其授予权限的用户的组。
    - **作用域** - 选择包含上述成员将有权管理的用户的组。
<br></br>
5. 完成后，请单击“确定”。 新分配将显示在分配列表中。

### <a name="intune-rbac-table"></a>Intune RBAC 表

- 下载 [Intune RBAC 表](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a)，以查看有关每个角色可以执行的操作的详细信息。

## <a name="custom-roles"></a>自定义角色

你可以创建一个自定义角色，以包含具体作业职能所需的任何权限。 例如，如果 IT 部门组管理应用程序、策略和配置的配置文件，则可以在一个自定义角色中添加所有这些权限。

> [!IMPORTANT]
> 若要创建、编辑或分配角色，你的帐户必须在 Azure AD 中具有以下权限之一：
> - **全局管理员**
> - **Intune 服务管理员**

### <a name="to-create-a-custom-role"></a>若要创建自定义角色

1. 使用 Intune 凭据登录 [Azure 门户](https://portal.azure.com)。

2. 从左侧菜单中选择“所有服务”，然后在文本框筛选器中键入 Intune。

3. 选择 Intune 后，即打开“Intune 仪表板”，选择“Intune 角色”。

4. 在“Intune 角色”窗格上，依次选择“所有角色”、“添加自定义”。

5. 在“添加自定义角色”窗格上，输入新角色的名称和说明，然后单击“权限”。

3. 在“权限”窗格上，选择要用于此角色的权限。 使用 [Intune RBAC 表](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a)帮助你确定要应用哪些权限。

4. 完成后，选择“确定”。

5. 在“添加自定义角色”窗格上，单击“创建”。 新角色会显示在“Intune 角色 - 所有角色”窗格的列表中。

### <a name="to-assign-a-custom-role"></a>若要分配自定义角色

1. 在“Intune 角色 - 所有角色”窗格上，选择要分配的自定义角色。

2. 在<角色名称> -“概述”窗格上，依次选择“管理”、“分配”。 在此窗格上，还可以编辑或删除现有角色。

3. 在“自定义角色”窗格上，选择“分配”。

4. 在“角色分配”窗格上，输入分配的“名称”和可选“说明”，然后选择以下各项：
    - **成员** - 选择包含想要对其授予权限的用户的组。
    - **作用域** - 选择包含上述成员将有权管理的用户的组。
<br></br>
5. 完成后，请单击“确定”。 新分配将显示在分配列表中。

## <a name="next-steps"></a>后续步骤

[通过疑难解答门户使用 Intune 支持操作员角色](help-desk-operators.md)

## <a name="see-also"></a>另请参阅

[使用 Azure AD 的分配角色](https://docs.microsoft.com/azure/active-directory/active-directory-users-assign-role-azure-portal)
