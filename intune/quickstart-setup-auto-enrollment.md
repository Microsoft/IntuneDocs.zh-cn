---
title: 快速入门 - 在 Intune 中设置自动注册
description: 快速入门 - 在 Intune 中设置 Windows 10 设备的自动注册。
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.openlocfilehash: 3b713f090fb6ada884a269e286f55f6e1b1087c4
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581521"
---
# <a name="quickstart-set-up-automatic-enrollment-for-windows-10-devices"></a>快速入门 - 设置 Windows 10 设备的自动注册

在本快速入门中，将 Microsoft Intune 设置为在特定用户登录到 Windows 10 设备时自动注册设备。

如果没有 Intune 订阅，请[注册免费试用帐户](free-trial-sign-up.md)。

## <a name="prerequisites"></a>必备条件

- 要完成本快速入门，必须先[创建用户](quickstart-create-user.md)并[创建组](quickstart-create-group.md)。

## <a name="sign-in-to-intune"></a>登录到 Intune

以全局管理员或 Intune 服务管理员身份登录 [Intune](https://aka.ms/intuneportal)。

## <a name="set-up-windows-10-automatic-enrollment"></a>设置 Windows 10 自动注册

在本示例中，你将使用 MDM 注册，以便可以自动注册公司和自带设备。

1. 在 Azure 中，选择“Azure Active Directory” > “移动性 (MDM 和 MAM)” > “Microsoft Intune” > “某些”。
![浏览器](media/quickstart-setup-auto-enrollment/setup-automatic-enrollment-win10.png)
2. 选择“选择组” > “Contoso 测试人员” > “选择”。
3. 对以下 URL 使用默认值：
    - MDM 使用条款 URL
    - MDM 发现 URL
    - MDM 符合性 URL
4. 选择 **“保存”**。
5. 在 Windows 10 设备上以组中的用户身份登录，然后按照提示进行操作。

## <a name="clean-up-resources"></a>清理资源

要重新配置 Intune 自动注册，请查看[设置适用于 Windows 设备的注册](windows-enroll.md)。

## <a name="next-steps"></a>后续步骤

在本快速入门中，你已了解如何设置 Windows 10 设备的自动注册。 还可以了解在所有平台上注册设备的其他方法。

> [!div class="nextstepaction"]
> [什么是设备注册？（文章）](device-enrollment.md)