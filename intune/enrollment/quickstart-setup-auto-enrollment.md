---
title: 快速入门 - 在 Intune 中设置自动注册
description: 快速入门 - 在 Intune 中设置 Windows 10 设备的自动注册。
services: microsoft-intune
author: ErikjeMS
manager: dougeby
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 03/26/2019
ms.author: erikje
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 78620818bfd13f0292e159c6a3670b5e3af53dab
ms.sourcegitcommit: 556b7ea2049014c9027f0e44affd3f301fab55fc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/06/2019
ms.locfileid: "73709509"
---
# <a name="quickstart-set-up-automatic-enrollment-for-windows-10-devices"></a>快速入门：设置适用于 Windows 10 设备的自动注册

在本快速入门中，将 Microsoft Intune 设置为在特定用户登录到 Windows 10 设备时自动注册设备。

如果没有 Intune 订阅，请[注册免费试用帐户](../fundamentals/free-trial-sign-up.md)。

## <a name="prerequisites"></a>必备条件

- Microsoft Intune 订阅 - [注册免费试用帐户](../fundamentals/free-trial-sign-up.md)。
- 要完成本快速入门，必须先[创建用户](../fundamentals/quickstart-create-user.md)并[创建组](../fundamentals/quickstart-create-group.md)。

## <a name="sign-in-to-intune"></a>登录到 Intune

以全局管理员或 Intune 服务管理员身份登录 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。 如果已创建 Intune 试用版订阅，则用于创建订阅的帐户就是全局管理员。

## <a name="set-up-windows-10-automatic-enrollment"></a>设置 Windows 10 自动注册

本示例将使用 MDM 注册，以便可以自动注册公司设备和自带设备。 你将注册免费的 Azure Active Directory Premium 订阅。

1. 在 Azure 中，选择“Azure Active Directory” > “移动性(MDM 和 MAM)”   。
2. 选择“获取免费的 Premium 试用版以使用此功能”  。 选择此选项将允许使用 Azure Active Directory Premium 免费试用版进行自动注册。 

    ![选择 Azure Active Directory Premium 免费试用版](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-01.png)

    选择“企业移动性 + 安全性 E5”免费试用版选项  。 此外，必须选择“激活”免费试用版  。

    ![选择“企业移动性 + 安全性 E5”免费试用版](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-02.png)

3. 选择“Microsoft Intune”  。 

    ![从列表中选择“Microsoft Intune”](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-03.png)

4. 从“MDM 用户范围”中选择“某些”，以使用 MDM 自动注册来管理员工 Windows 设备上的企业数据   。 将为 AAD 加入的设备和自带的设备配置 MDM 自动注册。

    ![从“配置”列表中选择“某些”](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-04.png)

5. 选择“选择组” > “Contoso 测试人员” > “选择”作为已分配的组    。

    ![选择要注册的组](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-05.png)

6. 从“MAM 用户范围”中选择“某些”以管理员工设备上的数据   。
7. 选择“选择组” > “Contoso 测试人员” > “选择”作为已分配的组    。 
8. 对于剩余的配置，可以使用默认值。
9. 选择 **“保存”** 。

## <a name="clean-up-resources"></a>清理资源

要重新配置 Intune 自动注册，请查看[设置适用于 Windows 设备的注册](windows-enroll.md)。

## <a name="next-steps"></a>后续步骤

在本快速入门中，你已了解如何设置 Windows 10 设备的自动注册。 有关设备注册的详细信息，请参阅[什么是设备注册？](device-enrollment.md)

要完成这一系列的 Intune 快速入门，请继续学习下一篇快速入门。

> [!div class="nextstepaction"]
> [快速入门：注册 Windows 10 设备](../quickstart-enroll-windows-device.md)
