---
title: 快速入门 - 在 Intune 中创建用户
description: 快速入门 - 在 Intune 中创建用户。
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 10/30/2018
ms.author: erikje
ms.openlocfilehash: ffc1f0140f98b17e060df3308af779ddcb77549e
ms.sourcegitcommit: 4c4e87cb0d8906085fcb7cdd170bd6b0cfeb23ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51510918"
---
# <a name="quickstart-create-a-user-and-assign-a-license-to-it"></a>快速入门：创建用户并为其分配许可证

在本快速入门中，你将创建一个用户，然后为该用户分配许可证。 使用 Intune 时，你希望有权访问公司数据的每个人都必须拥有用户帐户。 Intune 管理员稍后可以配置此类用户来管理访问控制。

如果没有 Intune 订阅，请[注册免费试用帐户](free-trial-sign-up.md)。

## <a name="sign-in-to-intune"></a>登录到 Intune

以[全局管理员或 Intune 服务管理员身份](users-add.md#types-of-administrators)登录 [Intune](https://aka.ms/intuneportal)。 如果已创建 Intune 试用版订阅，则用于创建订阅的帐户就是全局管理员。

## <a name="create-a-user"></a>创建用户

用户必须拥有用户帐户才能注册 Intune 设备管理。

1. 在 Intune 中，选择“用户” > “所有用户” > “新建用户”。
![浏览器](media/quickstart-create-user/create-user.png)
2. 在“名称”框中，输入一个名称，例如“Dewey Kellum”。
3. 在“用户名”框中输入用户标识符，例如 Dewey@contoso.onmicrosoft.com。

    > [!NOTE]
    > 如果尚未配置客户的域名，请使用用于创建 Intune 订阅的已验证的域名（或[免费试用版](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial)）。 

4. 选择“显示密码”并记下的自动生成的密码，以便登录到测试设备。
5. 选择“创建”。

## <a name="assign-a-license-to-the-user"></a>向用户分配许可证

创建用户之后，必须使用 [Office 365 门户](http://go.microsoft.com/fwlink/p/?LinkId=698854)为其分配 Intune 许可证。 如果没有分配许可证，用户就无法将他们的设备注册到 Intune 中。 

1. 使用登录 Intune 的凭据登录 [Office 365 门户](http://go.microsoft.com/fwlink/p/?LinkId=698854)。
2. 选择“用户” > “活动用户”> 选择刚刚创建的用户。
3. 选择“产品许可证”旁边的“编辑”。
4. 在“位置”下，为用户选择位置。
5. 单击 Intune 许可证（或拥有的包含 Intune 的其他许可证）旁边的“开启”。 显示的[产品名称](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference) ** 用作 Azure 管理中的服务计划 

   > [!NOTE]
   > 此设置会为该用户使用其中一个许可证。 如果使用的是试用环境，则稍后会将此许可证重新分配给实际环境中的真实用户。
6. 选择“保存” > “关闭”。

新的活跃 Intune 用户现将显示他们正在使用 Intune 许可证。

## <a name="clean-up-resources"></a>清理资源

如果不再需要此用户，则可以删除该用户，方法是导航到 [Office 365 门户](http://go.microsoft.com/fwlink/p/?LinkId=698854)，然后选择“用户” > “活跃用户” > 选择列表中的用户 > “删除用户” > “删除用户” > “确认更改” > “关闭”。

## <a name="next-steps"></a>后续步骤

在本快速入门中，你创建了一个用户并为该用户分配了许可证。 有关将用户添加到 Intune 的详细信息，请参阅[添加用户并授予对 Intune 的管理权限](users-add.md)。

要完成这一系列的 Intune 快速入门，请继续学习下一篇快速入门。

> [!div class="nextstepaction"]
> [快速入门：创建组以管理用户](quickstart-create-group.md)
