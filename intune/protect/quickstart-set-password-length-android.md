---
title: 快速入门 - 适用于 Android 设备的密码符合性策略
titleSuffix: Microsoft Intune
description: 本快速入门将使用 Microsoft Intune 为 Android 设备设置所需的密码长度。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 61fdf91d57ce5d187a0c43153f317b0b42c6b46c
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74409788"
---
# <a name="quickstart-create-a-password-compliance-policy-for-android-devices"></a>快速入门：创建适用于 Android 设备的密码符合性策略

在此快速入门中，你将使用 Microsoft Intune 来要求工作场所的 Android 用户输入特定长度的密码后才能被授权访问其 Android 设备上的信息。

Intune 设备符合性策略指定设备为实现符合性而必须满足的规则和设置。 可以将符合性策略与条件访问结合使用，从而允许或阻止访问公司资源。 还可获取设备报表并针对非符合性采取措施。

> [!IMPORTANT]
> 除密码设置以外，还应考虑其他系统安全设置，以保护工作场所的安全。 有关详细信息，请参阅[系统安全设置](compliance-policy-create-android-for-work.md)。

如果没有 Intune 订阅，请[注册免费试用帐户](../fundamentals/free-trial-sign-up.md)。

## <a name="sign-in-to-intune"></a>登录到 Intune

以[全局管理员](../fundamentals/users-add.md#types-of-administrators)或 Intune [服务管理员](../fundamentals/users-add.md#types-of-administrators)身份登录 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

## <a name="create-a-device-compliance-policy"></a>创建设备合规性策略

创建设备符合性策略，以要求员工的 Android 用户必须输入特定长度的密码，才能获得对 Android 设备上信息的访问权限。

1. 在 Intune 中，选择“设备”   > “符合性策略”   > “创建策略”  。

2. 添加“Android 符合性”  作为“名称”  。 此外，添加“说明”  。

3. 对于“平台”，选择“Android Enterprise”   。

4. 对于“配置文件类型”  ，选择“工作配置文件”  。

5. 选择“设置”   > “系统安全”  以显示 Android“系统安全”  边栏选项卡。

6. 对于“需要密码才可解锁移动设备”  ，请选择“需要”  。

7. 对于“所需的密码类型”  ，选择“至少为数字”  。

8. 对于“最短密码长度”  ，请输入“6”  。

    ![在 Microsoft Intune 中创建组的屏幕截图](./media/quickstart-set-password-length-android/quickstart-set-password-length-android-01.png)

9. 完成后，选择“确定”   > “确定”   > “创建”  以创建策略。

成功创建策略后，该策略将显示在“设备符合性策略”列表中。

## <a name="clean-up-resources"></a>清理资源

不再需要时，删除该策略。 要执行此操作，请选择“符合性策略”，然后单击“删除”  。

## <a name="next-steps"></a>后续步骤

在此快速入门中，你使用了 Intune 来为你的工作场所的 Android 设备创建符合性策略，以要求提供长度为至少六个字符的密码。 有关创建符合性策略的详细信息，请参阅 [Intune 中的设备符合性策略入门](device-compliance-get-started.md)。

要完成这一系列的 Intune 快速入门，请继续学习下一篇快速入门。

> [!div class="nextstepaction"]
> [快速入门：将通知发送到不相容设备](../quickstart-send-notification.md)
