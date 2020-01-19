---
title: 添加用于组织用户和设备的组
titleSuffix: Microsoft Intune
description: 添加组，以便按地理位置、部门或硬件详情来组织用户和设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: altsou
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 237eca2f8e00f00fda5fa3cf401be87de9602743
ms.sourcegitcommit: de663ef5f3e82e0d983899082a7f5b62c63f24ef
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2020
ms.locfileid: "75956261"
---
# <a name="add-groups-to-organize-users-and-devices"></a>添加用于组织用户和设备的组

Intune 使用 Azure Active Directory (Azure AD) 组来管理设备和用户。 作为 Intune 管理员，可以设置适合组织需要的组。 创建组，以便按地理位置、部门或硬件特性来组织用户或设备。 使用组来管理大规模的任务。 例如，可设置用于大量用户的策略，或向一组设备部署应用。

可以添加下列类型的组：

- **分配组** - 将用户或设备手动添加到静态组。 
- **动态组**（需要 Azure AD Premium）- 根据你创建的表达式，自动将用户或设备添加到用户组或设备组。

  例如，当用户添加有经理职务时，会自动将该用户添加到“所有经理”  用户组中。 或者，当设备具有 iOS 设备 OS 类型时，设备会自动添加到“所有 iOS 设备”  设备组中。

## <a name="add-a-new-group"></a>添加新组

使用以下步骤来创建新组。

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“组”   > “新建组”  ：

   ![此屏幕截图显示了已选择“新建组”的 Azure 门户](./media/groups-add/groups-add-new.png)

3. 在“组类型”  中，选择下列选项之一：

    - **安全性**：安全组定义谁可以访问资源，并建议用于 Intune 中的组。 例如，可以为用户创建组，如“所有 Charlotte 员工”  或“远程辅助角色”  。 或者，为设备创建组，如“所有 iOS 设备”  或“所有 Windows 10 学生设备”  。

        > [!TIP]
        > 还可以在 [Microsoft 365 管理中心](https://admin.microsoft.com)、Azure Active Directory 管理中心和 [Azure 门户中的 Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 中查看创建的用户和组。 在组织租户中，可以创建和管理所有这些区域中的组。
        >
        > 如果你的主要角色是设备管理，我们建议使用 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

    - **Office 365**：通过授予成员访问共享邮箱、日历、文件、SharePoint 站点等的权限来提供协作机会。 使用此选项还可以向组织外部的用户授予对组的访问权限。 有关详细信息，请参阅[了解 Office 365 组](https://support.office.com/article/learn-about-office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2)。

4. 对于新组，输入“组名称”  和“组说明”  。 具体明确并包含信息，使其他人知道组的用途。

    例如，对于“组名称”，请输入“所有 Windows 10 学生设备”  ，对于“组说明”，请输入“Contoso 高中 9-12 年级学生使用的所有 Windows 10 设备”  。

5. 输入“成员身份类型”  。 选项包括：

    - **已分配**：管理员手动将用户或设备分配给此组，并手动删除用户或设备。
    - **动态用户**：管理员创建成员身份规则以自动添加和删除成员。
    - **动态设备**：管理员创建动态组规则以自动添加和删除设备。

        ![Intune 组属性的屏幕截图](./media/groups-add/groups-add-properties.png)

    有关这些成员身份类型和创建动态表达式的详细信息，请参阅：

    - [使用 Azure AD 创建基本组并添加成员](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)
    - [Azure AD 中的动态组成员身份规则](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership)

    > [!NOTE]
    > 在此管理中心，当你创建用户或组时，你可能看不到“Azure Active Directory”  品牌。 但这就是你正在使用的内容。

6. 选择“创建”  以添加新组。 此时，组显示在列表中。

> [!TIP]
> 请考虑你可以创建的一些其他动态用户和设备组，例如：
>
> - Contoso 高中的所有学生
> - 所有 Android Enterprise 设备
> - 所有 iOS 11 及更早版本设备
> - “营销”
> - 人力资源
> - 所有 Charlotte 员工
> - 所有 WA 员工

## <a name="groups-and-policies"></a>组和策略

对组织资源的访问权限由你创建的用户和组控制。

创建组时，请考虑[符合性策略](../protect/device-compliance-get-started.md)和[配置文件](../configuration/device-profiles.md)的应用方式。 例如，你可能具有：

- 特定于设备操作系统的策略。
- 特定于组织中不同角色的策略。
- 特定于在 Active Directory 中定义的组织单位的策略。

若要建立组织的基本合规性要求，可以创建适用于所有组和设备的默认策略。 然后，可针对范围最广泛的用户和设备创建更具体的策略。 例如，可为每个设备操作系统创建电子邮件策略。

有关配置文件建议和指南，请参阅[将策略分配给用户组或设备组](../configuration/device-profile-assign.md#user-groups-vs-device-groups)和[配置文件建议](../configuration/device-profile-create.md#recommendations)。

## <a name="see-also"></a>另请参阅

- [使用 Microsoft Intune 的基于角色的访问控制 (RBAC)](role-based-access-control.md)
- [使用 Azure AD 组管理对资源的访问](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
