---
title: 快速入门 - 在 Intune 中创建并分配自定义角色
description: 快速入门 - 为远程设备管理器创建和分配自定义角色。
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 03/26/2019
ms.author: erikje
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: f63bbc80c055cfcb3bd52f79e7b810094107ec2a
ms.sourcegitcommit: d2989b9992d10d133573d9bc31479659fb7e242c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2019
ms.locfileid: "71080058"
---
# <a name="quickstart-create-and-assign-a-custom-role"></a>快速入门：创建和分配自定义角色

在本 Intune 快速入门中，你将创建具有安全操作部门特定权限的自定义角色。 然后，将角色分配给一组此类运算符。 存在可供立即使用的几个默认角色。 但是通过创建像这样的自定义角色，可以对移动设备管理系统的所有部分进行精确的访问控制。

如果没有 Intune 订阅，请[注册免费试用帐户](free-trial-sign-up.md)。

## <a name="prerequisites"></a>必备条件

- 要完成本快速入门，必须先[创建组](quickstart-create-group.md)。

## <a name="sign-in-to-intune"></a>登录到 Intune

以全局管理员或 Intune 服务管理员身份登录 [Intune](https://aka.ms/intuneportal)。 如果已创建 Intune 试用版订阅，则用于创建订阅的帐户就是全局管理员。

## <a name="create-a-custom-role"></a>创建自定义角色

创建自定义角色时，可以为各种操作设置权限。 对于安全操作角色，我们将设置一些读取权限，以便操作员可以查看设备的配置和策略。

1. 在 Intune 中，选择“角色” > “所有角色” > “添加”    。
![浏览器](media/quickstart-create-custom-role/add-custom-role.png)
2. 在“添加自定义角色”下的“名称”框中，输入“安全操作”    。
3. 在“说明”框中，输入“此角色允许安全操作员监控设备配置和符合性信息”   。
4. 选择“配置” > “公司设备标识符” > “读取”旁边的“是” > “确定”      。
![浏览器](media/quickstart-create-custom-role/corp-device-id-read.png)
5. 选择“设备符合性策略” > “读取”旁边的“是” > “确定”     。
6. 选择“设备配置” > “读取”旁边的“是” > “确定”     。
7. 选择“组织” > “读取”旁边的“是” > “确定”     。
8. 选择“确定” > “创建”   。

## <a name="assign-the-role-to-a-group"></a>将角色分配给组

必须先将角色分配给包含安全用户的组，安全操作员才可以使用新权限。

1. 在 Intune 中，选择“角色” > “所有角色” > “安全操作”    。
2. 在“Intune 角色”下，选择“工作” > “分配”    。
3. 在“分配名称”框中，输入“Sec ops”   。
4. 选择“成员 (组)” > “添加”   。
5. 选择“Contoso 测试人员”组  。
6. 选择“选择” > “确定”   。
7. 选择“范围 (组)” > “选择要包含的组” > “Contoso 测试人员”    。
8. 选择“选择” > “确定” > “确定”    。

现在，该组中的每个人都是“安全操作”角色的成员，可以查看有关设备的以下信息：公司设备标识符、设备符合性策略、设备配置和组织信息  。

## <a name="clean-up-resources"></a>清理资源

如果不想再使用新的自定义角色，可以将其删除。 选择“角色” > “所有角色”> 选择角色旁的省略号 >“删除”    。

## <a name="next-steps"></a>后续步骤

在本快速入门中，你创建了自定义安全操作角色并将其分配给组。 有关 Intune 中角色的详细信息，请参阅 [Microsoft Intune 的基于角色的管理控制 (RBAC)](role-based-access-control.md)

要完成这一系列的 Intune 快速入门，请继续学习下一篇快速入门。

> [!div class="nextstepaction"]
> [快速入门：创建适用于 iOS 的电子邮件设备配置文件](quickstart-email-profile.md)
