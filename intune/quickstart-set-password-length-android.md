---
title: 快速入门 - 为 Android 设备设置所需的密码长度
titlesuffix: Microsoft Intune
description: 在此快速入门中，你将使用 Microsoft Intune 为 Android 设备设置所需的密码长度。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/17/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f925df731c3ddd45b13d976b0686d76d941c71e6
ms.sourcegitcommit: 2e88ec7a412a2db35034d30a70d20a5014ddddee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/17/2018
ms.locfileid: "49395270"
---
# <a name="quickstart-set-a-required-password-length-for-android-devices"></a>快速入门：为 Android 设备设置所需的密码长度

在此快速入门中，你将使用 Microsoft Intune 来要求工作场所的 Android 用户输入特定长度的密码后才能被授权访问其 Android 设备上的信息。 

> [!IMPORTANT]
> 除密码设置以外，还应考虑其他系统安全设置，以保护工作场所的安全。 有关详细信息，请参阅[系统安全设置](compliance-policy-create-android-for-work.md#system-security-settings)。

如果没有 Intune 订阅，请[注册免费试用帐户](free-trial-sign-up.md)。

## <a name="sign-in-to-intune"></a>登录到 Intune

以全局管理员或 Intune 服务管理员身份登录 [Intune](https://aka.ms/intuneportal)。 通过选择“所有服务” > “Intune”，在 Azure 门户中查找 Intune。 Intune 位于“监视 + 管理”部分中。

## <a name="create-a-device-compliance-policy"></a>创建设备合规性策略
1. 打开“Microsoft Intune”边栏选项卡后，选择“设备符合性” > “策略” > “创建策略”。
2. 添加“Android 符合性”作为“名称”。 此外，添加“说明”。
3. 对于“平台”，请选择“Android”。 
4. 选择“设置” > “系统安全”以显示 Android“系统安全”边栏选项卡。
5. 在“密码”部分中的“需要密码才可解锁移动设备”旁，单击“需要”。
6. 在“最短密码长度”旁，输入“6”。  

    ![在 Microsoft Intune 中创建组的屏幕截图](./media/quickstart-set-password-length-android-01.png)

7. 完成后，单击“确定”以关闭“系统安全”边栏选项卡。 
8. 单击“确定”以关闭“Android 合规性策略”边栏选项卡。 
9. 单击“创建”以创建策略。

如果已成功创建策略，则该策略将显示在“设备符合性 - 策略”列表中。 

## <a name="next-steps"></a>后续步骤

在此快速入门中，你使用了 Intune 来为你的工作场所的 Android 设备创建符合性策略，以要求提供长度为至少六个字符的密码。

> [!div class="nextstepaction"]
> [设置自动注册](quickstart-setup-auto-enrollment.md)
