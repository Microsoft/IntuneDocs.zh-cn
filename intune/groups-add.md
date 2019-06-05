---
title: 添加用于组织用户和设备的组
titleSuffix: Microsoft Intune
description: 添加组，以便按地理位置、部门或硬件详情来组织用户和设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/13/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: amyros
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 60f2368fc8c6d4f8e2713a8386ccdd7e5958ac6b
ms.sourcegitcommit: 063177c6c365fef3642edd7c455790958469aad9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/30/2019
ms.locfileid: "66412610"
---
# <a name="add-groups-to-organize-users-and-devices"></a>添加用于组织用户和设备的组
Intune 使用 Azure Active Directory (AD) 组来管理设备和用户。 作为 Intune 管理员，可以设置适合组织需要的组。 创建组，以便按地理位置、部门或硬件特性来组织用户或设备。 使用组来管理大规模的任务。 例如，可设置用于大量用户的策略，或向一组设备部署应用。

可以添加下列类型的组：
- **分配组** - 将用户或设备手动添加到静态组
- 动态组 -（使用 Azure Active Directory Premium）允许动态生成使用简单或高级规则定义的用户或设备组 

## <a name="add-a-new-group"></a>添加新组

使用以下步骤来创建新组。
1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在 Intune 窗格中，选择“组”，然后在“所有组”窗格中选择“新建组”     。
   ![显示“新建组”已选择的 Azure 门户的屏幕截图](./media/groups-add-new.png)
4. 对于“组类型”，选择下列选项之一  ：
    - **安全性**：安全组是用于填充用户组的绝佳资源。 由于安全组定义谁有权访问哪些资源，因此可顺利地转换到 Intune 用户组。 在 Intune 中创建用户组时，可使用从 Active Directory 同步到 Azure Active Directory 的安全组，也可使用在 Azure Active Directory 中通过 Microsoft 365 管理中心或 Azure 门户直接创建的安全组。
    - **Office 365**

5. 为新组键入“名称”和“描述”   。 这些属性仅出现在管理门户中，并且不会向用户显示。

6. 选择成员身份类型  ：
   - **已分配**：创建一个手动分配的成员的组。 深入了解 [Azure AD 已分配的组](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal)。
   - **动态用户**：创建使用动态查询定义的用户组  。
   - **动态设备**：创建使用**动态查询**定义的设备组。

   ![Intune 组属性的屏幕截图](./media/groups-add-properties.png)

   Azure AD 允许基于定义成员身份的规则创建动态组。 了解如何[创建基于属性的动态组](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal)。

7. 可选择“启用 Office 功能”向用户组成员授予访问共享 Office 365 应用的权限。  了解有关 [Office 365 组](https://support.office.com/article/Learn-about-Office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2)的详细信息。
8. 选择“创建”  以添加新组。

## <a name="groups-and-policies"></a>组和策略

创建组时，请考虑将如何应用[“策略”](device-compliance-get-started.md)。 例如，你可能有特定于设备操作系统的策略、特定于组织中不同角色的策略或特定于已在 Active Directory 中定义的组织单位的策略。 分别设置 iOS、Android 和 Windows 设备组，并为每个组织角色分别设置用户组，可能会很有用。

还可创建适用于所有组和设备的默认策略，以建立组织的基本合规性要求。 然后，可针对范围最广泛的用户和设备创建更具体的策略。 例如，可为每个设备操作系统创建电子邮件策略。



## <a name="see-also"></a>另请参阅
- [使用 Azure Active Directory 组管理对资源的访问](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
- [Azure 门户中的 Intune 经典组](groups-get-started.md)
