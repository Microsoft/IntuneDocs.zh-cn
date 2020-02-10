---
title: 快速入门 - 在 Intune 中创建用户
description: 快速入门 - 在 Intune 中创建用户。
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 01/17/2020
ms.author: erikje
ms.manager: dougeby
ms.assetid: 820fcb18-0927-4ebd-be79-dce92b51c261
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: f6aa57b71e052e3fc8566fcdff8bdd9ef5d1c39e
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754484"
---
# <a name="quickstart-create-a-user-in-intune-and-assign-the-user-a-license"></a>快速入门：在 Intune 中创建用户并向用户分配许可证

在本快速入门中，你将创建用户，然后向用户分配 Intune 许可证。 使用 Intune 时，你希望有权访问公司数据的每个人都必须拥有自己的用户帐户。 Intune 管理员稍后可以配置用户来管理访问控制。

## <a name="prerequisites"></a>必备条件

- Microsoft Intune 订阅。 [注册免费试用帐户](../fundamentals/free-trial-sign-up.md)。

## <a name="sign-in-to-intune-in-microsoft-endpoint-manager"></a>在 Microsoft 终结点管理器中登录到 Intune

以[全局管理员或 Intune 服务管理员](users-add.md#types-of-administrators)身份登录 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。 如果已创建 Intune 试用版订阅，则用于创建订阅的帐户就是全局管理员。

## <a name="create-a-user"></a>创建用户

用户必须拥有用户帐户才能注册 Intune 设备管理。 若要创建新用户，请执行以下操作：

1. 在 Microsoft 终结点管理器中，选择“用户”  >“所有用户”  >“新用户”  ：![在 Microsoft 终结点管理器中，选择“新用户”](./media/quickstart-create-user/create-user.png)
2. 在“名称”  框中，输入一个名称，例如“Dewey Kellum”  ：![添加用户详情](./media/quickstart-create-user/create-user-02.png)
3. 在“用户名”  框中输入用户标识符，例如 Dewey@contoso.onmicrosoft.com。

    > [!NOTE]
    > 如果尚未配置客户端域名，请使用用于创建 Intune 订阅（或[免费试用版](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial)）的已验证的域名。 

4. 选择“显示密码”  并确保记下自动生成的密码，以便登录到测试设备。
5. 选择“创建”。 

## <a name="assign-a-license-to-the-user"></a>向用户分配许可证

创建用户后，必须使用 [Microsoft 365 管理中心](https://go.microsoft.com/fwlink/p/?LinkId=698854)向用户分配 Intune 许可证。 如果不向用户分配许可证，他们将无法在 Intune 中注册其设备。

若要向用户分配 Intune 许可证，请执行以下操作：

1. 使用登录 Intune 所用的凭据登录 [Microsoft 365 管理中心](https://go.microsoft.com/fwlink/p/?LinkId=698854)。
2. 选择“用户”   > “活动用户”  ，然后选择刚创建的用户。
3. 选择“许可证和应用”  选项卡。
4. 在“选择位置”  中，为用户选择一个位置（如果尚未设置）。
2. 选中“许可证”  部分中的“Intune”  复选框。 如果其他许可证包括 Intune，则可以选择该许可证。 显示的[产品名称](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)用作 Azure 管理中的服务计划。

    ![选择位置和 Intune 许可证](./media/quickstart-create-user/create-user-03.png)

   > [!NOTE]
   > 此设置会为该用户使用其中一个许可证。 如果使用的是试用环境，则稍后会将此许可证重新分配给实际环境中的真实用户。

6. 选择“保存更改”  。

新的活跃 Intune 用户现将显示他们正在使用 Intune 许可证  。

## <a name="clean-up-resources"></a>清理资源

如果不再需要此用户，可以通过转到 [Microsoft 365 管理中心](https://go.microsoft.com/fwlink/p/?LinkId=698854)并选择“用户”   > “指定用户”   > “删除用户”图标   > “删除用户”   > “关闭”  。

   ![选择“删除”图标](./media/quickstart-create-user/create-user-04.png)

## <a name="next-steps"></a>后续步骤

在本快速入门中，你创建了一个用户并向其分配了 Intune 许可证。 有关将用户添加到 Intune 的详细信息，请参阅[添加用户并授予对 Intune 的管理权限](users-add.md)。

若要继续这一系列的 Intune 快速入门，请转到下一篇快速入门：

> [!div class="nextstepaction"]
> [快速入门：创建组以管理用户](../quickstart-create-group.md)
