---
title: 使用 Microsoft Intune 中的范围标记来筛选策略 - Azure | Microsoft Docs
description: 使用范围标记将配置文件筛选到特定角色。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2019
ms.topic: article
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 57a14e1e3c4caea570667096fec71cecf2d88ddf
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2019
ms.locfileid: "66045194"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>对分布式 IT 使用基于角色的访问控制 (RBAC) 和范围标记

可使用基于角色的访问控制和范围标记来确保适当的管理员对适当的 Intune 对象具有适当的访问权限并可适当查看这些对象。 角色确定了管理员对哪些对象具有哪种访问权限。 而范围标记确定了管理员可查看哪些对象。

例如，假设向西雅图区域办事处的一名管理员分配了“策略和配置文件管理员”角色。 而你希望该管理员仅查看和管理只适用于西雅图区域设备的配置文件和策略。 为此，你需要：

1. 创建一个名为“西雅图”的范围标记。
2. 通过下列项为“策略和配置文件管理员”角色创建角色分配： 
    - 成员（组）：一个名为“西雅图 IT 管理员”的安全组。 该组中的所有管理员都将有权管理范围（组）中用户/设备的策略和配置文件。
    - 范围（组）：一个名为“西雅图用户”的安全组。 该组中的所有用户/设备都可让成员（组）中的管理员管理其配置文件和策略。 
    - 范围（标记）：西雅图。 成员（组）中的管理员可查看还具有“西雅图”范围标记的设备。
3. 将“西雅图”范围标记添加到希望成员（组）中的管理员可访问的策略和配置文件中。
4. 将“西雅图”范围标记添加到希望在成员（组）中向管理员显示的设备。 


## <a name="to-create-a-scope-tag"></a>创建范围标记

1. 在 Intune 中，选择“角色” > “范围(标记)” > “创建”    。

    ![显示创建范围标记的屏幕截图。](./media/scope-tags/create-scope-tag.png)

2. 提供名称和说明   。
3. 选择“创建”  。

## <a name="to-assign-a-scope-tag-to-a-role"></a>向角色分配范围标记

1. 在 Intune 中，选择“角色” > “所有角色”，选择一个角色，然后选择“分配” > “分配”     。

    ![显示向角色分配范围的屏幕截图。](./media/scope-tags/assign-scope-to-role.png)

2. 提供分配名称和说明   。
3. 选择“成员(组)” > “添加”，再选择要纳入此分配的组，然后选中“选择” > 确定”     。 此组中的 mUser 都将有权管理范围（组）中用户/设备的策略和配置文件。

    ![选择成员组的屏幕截图。](./media/scope-tags/select-member-groups.png)

4. 如果要管理特定组中的用户/设备，请选择“范围（组）” > 选定的组” > 选择要包含的组”> 选择组>“选择” > “确定”      。 此组中的所有用户/设备都可以由其成员（组）中的管理员管理其配置文件和策略。

    ![显示选择范围组的屏幕截图。](./media/scope-tags/select-scope-groups.png)

    或者，可选择“所有设备”、“所有用户”或“所有用户和设备”    。

    ![显示用于选择范围组的其他选项的屏幕截图。](./media/scope-tags/scope-group-other-options.png)
    
5. 选择“范围(标记)” > “添加”，选择要添加到此角色的标记，然后选中“选择” > “确定”     。 成员（组）中的用户将可访问还具有同一范围标记的策略和配置文件。

    ![显示选择范围标记的屏幕截图。](./media/scope-tags/select-scope-tags.png)

6. 选择“确定”  。 

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>将作用域标记添加到配置文件
1. 在 Intune 中，选择“设备配置” > “配置文件”，再选择一个配置文件   。

    ![显示选择配置文件的屏幕截图。](./media/scope-tags/choose-profile.png)

2. 选择“属性” > “范围(标记)” > “添加”    。

    ![显示添加范围标记的屏幕截图。](./media/scope-tags/add-scope-tags.png)

3. 在“选择标记”下，选择要添加到配置文件的标记  。
4. 选中“选择” > “确定” > “保存”    。

## <a name="to-assign-a-scope-tag-to-an-app-configuration-policy"></a>向应用配置策略分配范围标记
对于设备注册类型设置为“受管理设备”的设备   ：
1. 选择“客户端应用” > “应用配置策略”，再选择应用配置策略   。
2. 选择“属性” > “范围(标记)”，再选择要分配给策略的标记   。

对于设备注册类型设置为托管应用的设备   ：
1. 选择“客户端应用” > “应用配置策略”，再选择应用配置策略   。
2. 选择“范围(标记)”，再选择要分配给策略的标记  。


## <a name="to-assign-a-scope-tag-to-an-ios-app-provisioning-profile"></a>向 iOS 应用预配配置文件分配范围标记
1. 在 Intune 中，选择“客户端应用” > “iOS 应用预配配置文件”，再选择一个配置文件   。
2. 选择“属性” > “范围(标记)”，再选择要分配给配置文件的标记   。
3. 选中“选择” > “确定” > “保存”    。

## <a name="to-assign-a-scope-tag-to-an-apple-volume-purchase-program-vpp-token"></a>向 Apple Volume Purchase Program (VPP) 令牌分配范围标记
1. 在 Intune 中，选择“客户端应用” > “Apple VPP 令牌”，再选择一个 VPP 令牌   。
2. 选择“范围(标记)”，再选择要分配给配置文件的标记  。 与 VPP 令牌关联的 VPP 应用和电子书会继承所分配的标记。
3. 选中“选择” > “确定” > “保存”    。

## <a name="scope-tag-details"></a>范围标记详细信息
使用范围标记时，请谨记下列详细信息：

- 当前可将范围标记分配给：
    - 角色分配
    - 设备合规性策略
    - 设备配置文件
    - Windows 10 更新通道
    - 受管理设备
    - 应用
    - 应用配置策略 - 受管理设备
    - PowerShell 脚本
    - DEP 令牌
    - iOS 应用预配配置文件
    - Volume Purchase Program (VPP) 令牌
- 管理员在 Intune 中创建对象时，分配给该管理员的所有范围标记都将自动分配给新对象。
- Intune RBAC 不适用于 Azure Active Directory 角色。 因此，无论 Intune 服务管理员和全局管理员角色具有哪些范围标记，它们都对 Intune 具有完整的管理员访问权限。
- 而角色分配中带有范围标记的管理员也可查看不带范围标记的 Intune 对象。
- 只能在角色分配中分配所拥有的范围标记。
- 仅可面向在角色分配的范围（组）中列出的组。
- 如果向角色分配了范围标记，则无法删除 Intune 对象上的所有范围标记。 必须至少有一个范围标记。

## <a name="next-steps"></a>后续步骤

管理[角色](role-based-access-control.md)和[配置文件](device-profile-assign.md)。
