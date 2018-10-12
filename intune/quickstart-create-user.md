---
title: 快速入门 - 在 Intune 中创建用户
description: 快速入门 - 在 Intune 中创建用户。
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.openlocfilehash: 6a1d591e635dccd99551d9b8d40e099724a85d77
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581545"
---
# <a name="quickstart-create-a-user-and-assign-a-license-to-it"></a>快速入门：创建用户并为其分配许可证

在本快速入门中，你将创建用户，然后为其分配许可证。 使用 Intune 时，你希望有权访问公司数据的每个人都必须拥有用户帐户。 然后，Intune 管理员可以配置此类用户来管理访问控制。

如果没有 Intune 订阅，请[注册免费试用帐户](free-trial-sign-up.md)。

## <a name="sign-in-to-intune"></a>登录到 Intune

以全局管理员或 Intune 服务管理员身份登录 [Intune](https://aka.ms/intuneportal)。

## <a name="create-a-user"></a>创建用户

用户必须拥有用户帐户才能注册 Intune 设备管理。

1. 在 Intune 中，选择“用户” > “所有用户” > “新建用户”。
![浏览器](media/quickstart-create-user/create-user.png)
2. 在“名称”框中，输入“Dewey Kellum”。
3. 在“用户名”框中，输入 Dewey@contoso.onmicrosoft.com。
4. 选择“组” > “所有用户” > “选择”。
5. 选择“显示密码”并记下的自动生成的密码，以便登录到测试设备。
6. 选择“创建”。

## <a name="assign-a-license-to-the-user"></a>向用户分配许可证

创建用户之后，必须使用 [Office 365 门户](http://go.microsoft.com/fwlink/p/?LinkId=698854)为其分配 Intune 许可证。 如果没有分配许可证，用户就无法将他们的设备注册到 Intune 中。 

1. 使用登录 Intune 的凭据登录 [Office 365 门户](http://go.microsoft.com/fwlink/p/?LinkId=698854)。
2. 选择“用户” > “活动用户”> 选择刚刚创建的用户。
3. 在“位置”下，为用户选择位置。
3. 选择“产品许可证”，并将“企业移动性 + 安全性 E3”（或你拥有的另一个包含 Intune 的许可证）设置为“启用”。
   > [!NOTE]
   > 此操作会为此用户使用一个许可证。 如果使用的是实时环境，可在之后停用此许可证，以将其重新分配给一个真正的用户。
5. 选择 **“保存”**。

## <a name="clean-up-resources"></a>清理资源

如果不再需要此用户，可以选择“用户” > “所有用户”> 在列表中选择用户 >“删除用户” > “是”将其删除。

## <a name="next-steps"></a>后续步骤

在本快速入门中，你创建了用户并为其分配了许可证。 现在可以将该用户分配到组。

> [!div class="nextstepaction"]
> [创建组](quickstart-create-group.md)
