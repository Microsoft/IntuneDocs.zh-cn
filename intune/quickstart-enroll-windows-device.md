---
title: 快速入门 - 在 Microsoft Intune 中注册 Windows 10 桌面版设备
description: 快速入门 - 使用公司门户将 Windows 10 桌面版设备注册到 Microsoft Intune。
services: microsoft-intune
author: ErikRe
ms.author: erikre
manager: dougeby
ms.date: 11/09/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 658a7655-a6df-4dbe-b56c-22c7fc60e706
ms.openlocfilehash: 18e724d83514bf0df7fcc4f4085f6204669a468f
ms.sourcegitcommit: 4c4e87cb0d8906085fcb7cdd170bd6b0cfeb23ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51510936"
---
# <a name="quickstart-enroll-your-windows-10-device"></a>快速入门：注册 Windows 10 设备

在本快速入门中，你将首先扮演 Intune 用户的角色，将 Windows 10 设备注册到 Microsoft Intune。 然后，返回 Intune 并确认已注册的设备。

在 Microsoft Intune 中注册设备可使 Windows 10 设备获取访问组织安全数据（包括电子邮件、文件和其他资源）的权限。 这适用于 Windows 10 桌面设备和 Windows 10 移动设备。 注册设备有助于为你和你的组织确保这类访问的安全，且有助于将工作数据与个人数据分开。

> [!TIP]
> 了解[在 Intune 中注册设备](/intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md)后会发生的情况，以及这对[设备上的信息](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)的意义。

如果没有 Intune 订阅，请[注册免费试用帐户](free-trial-sign-up.md)。

## <a name="prerequisites"></a>必备条件

- Microsoft Intune 订阅 - [注册免费试用帐户](free-trial-sign-up.md)
- 要完成本快速入门，必须完成[在 Intune 中设置自动注册](quickstart-setup-auto-enrollment.md)的相关步骤。

## <a name="confirm-your-windows-10-desktop-version"></a>请确认 Windows 10 桌面版版本

在注册 Windows 10 桌面版之前，必须先确认已安装的 Windows 版本。

1. 右键单击 Windows“开始”图标，然后选择“设置”以显示 Windows 设置选项。

   ![“Windows 设置”-“系统”的屏幕截图](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-01.png)

2. 选择“系统” > “关于”。 

   ![系统设置的屏幕截图](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-02.png)

    > [!TIP]
    > 此外，还可以在“搜索栏”中键入“关于电脑”，然后选择“关于电脑”。

3. 在“设置”窗口中，你将看到电脑的“Windows 规范”列表。 在此列表中，找到“版本”。

4. 请确认 Windows 10 版本为 1607 或更高版本。

    > [!IMPORTANT]
    > 本快速入门中提供的步骤适用于 Windows 10 版本1607 或更高版本，如果你的版本是 1511 或更低版本，请继续[这些步骤](/intune-user-help/enroll-your-w10-device-your-account.md)。

## <a name="enroll-windows-10-desktop"></a>注册 Windows 10 桌面版

1. 返回到 Windows 设置，然后选择“帐户”。

   ![系统设置 -“帐户”的屏幕截图](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-03.png)

2. 选择“访问工作或学校” > “连接”。

    ![选择“访问工作学校帐户”](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-04.png)

3. 使用你的工作或学校帐户登录 Intune，然后选择“下一步”。 如果你已执行 [创建用户并分配许可证] 快速入门，则可以使用创建的用户帐户登录。

    > [!NOTE]
    > 如果你设置了“.onmicrosoft.com”，则用户帐户会将“.onmicrosoft.com”作为帐户地址的一部分。 

   ![输入工作或学校帐户](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-05.png)

    你将看到指示你的公司或学校正在注册你的设备的消息。

4. 当你看到**设置完成!** 屏幕，请选择“完成”。 大功告成。

5. 现在，你将在 Windows 桌面上看到添加的帐户已作为“访问工作或学校”设置的一部分。

   ![新添加的帐户的屏幕截图](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-06.png)

    如果执行了之前的步骤，但仍无法访问你的工作或学校电子邮件帐户和文件，请按照[看到“访问工作单位或学校”时要执行的故障排除步骤](/intune-user-help/troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-access-work-or-school)中的步骤操作。

## <a name="confirm-your-device-enrollment-in-intune"></a>确认 Intune 中的设备注册

1. 以全局管理员或 Intune 服务管理员身份登录 [Intune](https://aka.ms/intuneportal)。
2. 选择“设备”，在 Intune 中查看已注册的设备。
3. 验证已在 Intune 中注册其他设备。

   ![Intune 已注册的设备的屏幕截图](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-07.png)

## <a name="clean-up-resources"></a>清理资源

要取消注册 Windows 设备，请参阅[从管理删除 Windows 设备](/intune-user-help/unenroll-your-device-from-intune-windows.md)。

## <a name="next-steps"></a>后续步骤

在本快速入门中，你已了解如何如何将 Windows 10 设备注册到 Intune 中。 还可以了解在所有平台上注册设备的其他方法。 有关将设备与 Intune 配合使用的详细信息，请参阅[使用托管设备完成工作](/intune-user-help/use-managed-devices-to-get-work-done.md)。

要完成这一系列的 Intune 快速入门，请继续学习下一篇快速入门。

> [!div class="nextstepaction"]
> [快速入门：为 Android 设备设置所需的密码长度](quickstart-set-password-length-android.md)