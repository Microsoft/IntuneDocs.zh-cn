---
title: 使用 Microsoft Intune 中的作用域标记来筛选策略 - Azure | Microsoft Docs
description: 使用作用域标记将配置文件筛选到特定角色。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fb57ea2ef5c99c58968ee25b3a75b2165ece787a
ms.sourcegitcommit: 0adb41c0640743d5cb726e66ad2427e3ad6faf20
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58658543"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>使用基于角色的访问控制 (RBAC) 和作用域标记为分布式 IT

可以使用基于角色的访问控制和作用域标记以确保正确的管理员具有正确的访问权限和对正确的 Intune 对象的可见性。 角色确定哪些访问管理员拥有对哪些对象。 作用域标记确定管理员可以看到哪些对象。

例如，假设西雅图地区办事处管理员分配的策略和配置文件管理器角色。 您希望此管理员查看和管理配置文件和仅应用于西雅图设备策略。 要执行此操作，您应该：

1. 创建名为西雅图的范围标记。
2. 创建使用的策略和配置文件管理器角色的角色分配： 
    - 成员 （组） = 名为西雅图 IT 管理员的安全组。 此组中的所有管理员将都有权管理策略和作用域 （组） 中的用户/设备的配置文件。
    - 范围 （组） = 安全组命名为西雅图的用户。 此组中的所有用户/设备可以都具有其配置文件和策略管理的成员 （组） 中的管理员。 
    - 作用域 （标记） = Seattle。 中的成员 （组） 的管理员可以看到还具有西雅图作用域标记的设备。
3. 将西雅图作用域标记添加到策略和配置文件所需成员 （组），以便能够访问中的管理员。
4. 将西雅图作用域标记添加到设备所需成员 （组） 中的管理员可见。 


## <a name="to-create-a-scope-tag"></a>创建作用域标记

1. 在 Intune 中，选择**角色** > **作用域 （标记）** > **创建**。

    ![屏幕截图创建范围标记。](./media/scope-tags/create-scope-tag.png)

2. 提供名称和说明。
3. 选择“创建”。

## <a name="to-assign-a-scope-tag-to-a-role"></a>向角色分配作用域标记

1. 在 Intune 中，选择**角色** > **的所有角色**> 选择角色 >**分配** > **分配**。

    ![屏幕截图向角色分配作用域。](./media/scope-tags/assign-scope-to-role.png)

2. 提供**分配名称**并**说明**。
3. 选择**成员 （组）** > **添加**> 选择你希望作为此分配的一部分的组 >**选择** >  **确定**。 此组中的 mUsers 将有权管理策略和用户/设备在范围 （组） 中的配置文件。

    ![选择成员组的屏幕截图。](./media/scope-tags/select-member-groups.png)

4. 如果你想要管理用户/设备在一组特定的组中，选择**范围 （组）** > **所选用户组** > **选择要包含组**> 选择的组 >**选择** > **确定**。 此组中的所有用户/设备可以都具有其配置文件和策略管理的成员 （组） 中的管理员。

    ![选择作用域组的屏幕截图。](./media/scope-tags/select-scope-groups.png)

    或者，可以选择**的所有设备**，**的所有用户**，或**所有用户和所有设备**。

    ![用于选择作用域组的其他选项的屏幕截图。](./media/scope-tags/scope-group-other-options.png)
    
5. 选择**作用域 （标记）** > **添加**> 选择你想要添加到此角色的标记 >**选择** > **确定**. 成员 （组） 中的用户将有权访问的策略和配置文件也具有相同的作用域标记。

    ![选择作用域标记的屏幕截图。](./media/scope-tags/select-scope-tags.png)

6. 选择“确定”。 

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>将作用域标记添加到配置文件
1. 在 Intune 中，选择**设备配置** > **配置文件**> 选择配置文件。

    ![选择配置文件的屏幕截图。](./media/scope-tags/choose-profile.png)

2. 选择**属性** > **作用域 （标记）** > **添加**。

    ![添加作用域标记的屏幕截图。](./media/scope-tags/add-scope-tags.png)

3. 下**选择标记**，选择你想要添加到配置文件的标记。
4. 选择**选择** > **确定** > **保存**。

## <a name="to-assign-a-scope-tag-to-an-app-configuration-policy"></a>若要将作用域标记分配到应用配置策略
使用对设备**设备注册类型**设置为**托管设备**:
1. 选择**客户端应用** > **应用配置策略**> 选择应用配置策略。
2. 选择**属性** > **作用域 （标记）** > 选择你想要分配到策略的标记。

使用对设备**设备注册类型**设置为**托管应用**:
1. 选择**客户端应用** > **应用配置策略**> 选择应用配置策略。
2. 选择**作用域 （标记）** > 选择你想要分配到策略的标记。


## <a name="to-assign-a-scope-tag-to-an-ios-app-provisioning-profile"></a>若要向 iOS 应用预配配置文件分配的范围标记
1. 在 Intune 中，选择**客户端应用** > **iOS 应用预配配置文件**> 选择配置文件。
2. 选择**属性** > **作用域 （标记）** > 选择你想要分配到配置文件的标记。
3. 选择**选择** > **确定** > **保存**。

## <a name="scope-tag-details"></a>作用域标记详细信息
当使用具有作用域标记，请牢记这些详细信息：

- 目前可以将分配到作用域标记：
    - 角色分配
    - 设备合规性策略
    - 设备配置文件
    - Windows 10 更新圈
    - 托管设备
    - 应用
    - 应用配置策略 – 托管设备
    - PowerShell 脚本
    - DEP 令牌
    - iOS 应用预配配置文件
- 当管理员在 Intune 中创建一个对象时，所有作用域标记分配给该管理员将自动分配给新的对象。
- Intune RBAC 不适用于 Azure Active Directory 角色。 因此，Intune 服务管理员和全局管理员角色具有完全管理员访问 Intune，无论它们有哪些作用域标记。
- 使用作用域标记的角色分配中的管理员还可以查看 Intune 无作用域标记的对象。
- 只能将分配有角色分配中的范围标记。
- 你可以在您的角色分配范围 （组） 中列出的目标组。
- 如果您有分配给你的角色的作用域标记，则无法删除 Intune 对象上的所有作用域标记。 至少一个范围标记是必需的。

## <a name="next-steps"></a>后续步骤

管理[角色](role-based-access-control.md)和[配置文件](device-profile-assign.md)。
