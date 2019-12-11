---
title: 在 Intune 中使用基于角色的访问控制（RBAC）和作用域标记进行分发 |Microsoft Docs
description: 使用作用域标记将配置文件筛选到特定角色。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.technology: ''
ms.assetid: a21d3039-f2ed-4f43-b6fa-d00c071edbc4
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6b92dca399afeb035bf58d998efdd469318de389
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72504955"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>对分布式 IT 使用基于角色的访问控制 (RBAC) 和范围标记

可使用基于角色的访问控制和范围标记来确保适当的管理员对适当的 Intune 对象具有适当的访问权限并可适当查看这些对象。 角色确定了管理员对哪些对象具有哪种访问权限。 而范围标记确定了管理员可查看哪些对象。

例如，假设向西雅图区域办事处的一名管理员分配了“策略和配置文件管理员”角色。 而你希望该管理员仅查看和管理只适用于西雅图区域设备的配置文件和策略。 若要设置此访问权限，请执行以下操作：

1. 创建一个名为“西雅图”的范围标记。
2. 通过下列项为“策略和配置文件管理员”角色创建角色分配： 
    - 成员（组）：一个名为“西雅图 IT 管理员”的安全组。 该组中的所有管理员都将有权管理范围（组）中用户/设备的策略和配置文件。
    - 范围（组）：一个名为“西雅图用户”的安全组。 该组中的所有用户/设备都可让成员（组）中的管理员管理其配置文件和策略。 
    - 范围（标记）：西雅图。 成员（组）中的管理员可查看还具有“西雅图”范围标记的 Intune 对象。
3. 将“西雅图”范围标记添加到希望成员（组）中的管理员可访问的策略和配置文件中。
4. 将“西雅图”范围标记添加到希望在成员（组）中向管理员显示的设备。 

## <a name="default-scope-tag"></a>默认作用域标记
默认范围标记会自动添加到支持作用域标记的所有未标记的对象。

默认作用域标记功能类似于 System Center Configuration Manager 中的安全作用域功能。 

## <a name="to-create-a-scope-tag"></a>创建作用域标记

1. 在 Intune 中，选择“角色” > “范围(标记)” > “创建”    。

    ![显示创建范围标记的屏幕截图。](./media/scope-tags/create-scope-tag.png)

3. 如果要将所有设备置于特定组中，请选择 "**向所选组中的所有设备分配作用域标记**"。
    1. 在 "**选择要包括的组**" 页中，选择包含要将此作用域标记分配到的设备的组。
    2. 选择“选择”  。
4. 选择 **“创建”** 。

## <a name="to-assign-a-scope-tag-to-a-role"></a>向角色分配作用域标记

1. 在 Intune 中，选择“角色” > “所有角色”，选择一个角色，然后选择“分配” > “分配”     。

    ![显示向角色分配范围的屏幕截图。](./media/scope-tags/assign-scope-to-role.png)

2. 提供分配名称和说明   。
3. 选择“成员(组)” > “添加”，再选择要纳入此分配的组，然后选中“选择” > 确定”     。 此组中的用户将有权管理作用域（组）中的用户/设备。

    ![选择成员组的屏幕截图。](./media/scope-tags/select-member-groups.png)

4. 如果要管理特定组中的用户/设备，请选择“范围（组）” > 选定的组” > 选择要包含的组”> 选择组>“选择” > “确定”      。 此组中的所有用户/设备将由成员（组）中的管理员管理。

    ![显示选择范围组的屏幕截图。](./media/scope-tags/select-scope-groups.png)

    或者，可选择“所有设备”、“所有用户”或“所有用户和设备”    。

    ![显示用于选择范围组的其他选项的屏幕截图。](./media/scope-tags/scope-group-other-options.png)
    
5. 选择“范围(标记)” > “添加”，选择要添加到此角色的标记，然后选中“选择” > “确定”     。 成员（组）中的用户将有权访问也具有相同作用域标记的 Intune 对象。

    ![显示选择范围标记的屏幕截图。](./media/scope-tags/select-scope-tags.png)

6. 选择“确定”  。 

## <a name="assign-scope-tags-to-other-objects"></a>将作用域标记分配给其他对象

对于支持作用域标记的对象，范围标记通常出现在 "**属性**" 下。 例如，若要将作用域标记分配到配置文件，请执行以下步骤：

1. 在 Intune 中，选择“设备配置” > “配置文件”，再选择一个配置文件   。

    ![显示选择配置文件的屏幕截图。](./media/scope-tags/choose-profile.png)

2. 选择“属性” > “范围(标记)” > “添加”    。

    ![显示添加范围标记的屏幕截图。](./media/scope-tags/add-scope-tags.png)

3. 在“选择标记”下，选择要添加到配置文件的标记  。
4. 选中“选择” > “确定” > “保存”    。


## <a name="scope-tag-details"></a>范围标记详细信息
使用范围标记时，请谨记下列详细信息： 

- 如果租户可以拥有该对象的多个版本（如角色分配或应用），则可以将作用域标记分配给 Intune 对象类型。
  以下 Intune 对象是此规则的例外情况，目前不支持作用域标记：
    - Windows ESP 配置文件
    - 设备类别
    - 注册限制
    - 公司设备标识符
    - Autopilot 设备
    - 设备符合性位置
    - Jamf 设备
- 与 VPP 令牌关联的 VPP 应用和电子书继承分配给关联的 VPP 令牌的作用域标记。
- 与 DEP 令牌关联的设备注册计划（DEP）设备和 DEP 配置文件继承分配给关联的 DEP 令牌的作用域标记。
- 管理员在 Intune 中创建对象时，分配给该管理员的所有范围标记都将自动分配给新对象。
- Intune RBAC 不适用于 Azure Active Directory 角色。 因此，无论 Intune 服务管理员和全局管理员角色具有哪些范围标记，它们都对 Intune 具有完整的管理员访问权限。
- 如果角色分配没有范围标记，则 IT 管理员可以根据 IT 管理员权限查看所有对象。 没有作用域标记的管理员实质上具有所有作用域标记。
- 只能在角色分配中分配所拥有的范围标记。
- 仅可面向在角色分配的范围（组）中列出的组。
- 如果向角色分配了范围标记，则无法删除 Intune 对象上的所有范围标记。 必须至少有一个范围标记。

## <a name="next-steps"></a>后续步骤

了解[多个角色分配](role-based-access-control.md#multiple-role-assignments)时范围标记的行为方式。
管理[角色](role-based-access-control.md)和[配置文件](../configuration/device-profile-assign.md)。
