---
title: 快速入门 - 创建适用于 Android 设备的密码符合性策略
titleSuffix: Microsoft Intune
description: 本快速入门将使用 Microsoft Intune 为 Android 设备设置所需的密码长度。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/26/2019
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f4a16272f32b8546e7e9bb12a22f16235ab49aed
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58799652"
---
# <a name="quickstart-create-a-password-compliance-policy-for-android-devices"></a>快速入门：创建适用于 Android 设备的密码符合性策略

在此快速入门中，你将使用 Microsoft Intune 来要求工作场所的 Android 用户输入特定长度的密码后才能被授权访问其 Android 设备上的信息。 

Intune 设备符合性策略指定设备为实现符合性而必须满足的规则和设置。 可以将符合性策略与条件访问结合使用，从而允许或阻止访问公司资源。 还可获取设备报表并针对非符合性采取措施。

> [!IMPORTANT]
> 除密码设置以外，还应考虑其他系统安全设置，以保护工作场所的安全。 有关详细信息，请参阅[系统安全设置](compliance-policy-create-android-for-work.md#system-security-settings)。

如果没有 Intune 订阅，请[注册免费试用帐户](free-trial-sign-up.md)。

## <a name="sign-in-to-intune"></a>登录到 Intune

以全局管理员或 Intune 服务管理员身份登录 [Intune](https://aka.ms/intuneportal)。 

## <a name="create-a-device-compliance-policy"></a>创建设备合规性策略

在本快速入门中，你将使用 Intune 来要求工作场所的 Android 用户输入特定长度的密码后才能被授权访问其 Android 设备上的信息。

1. 在 Intune 中，选择“设备符合性” > “策略” > “创建策略”。
2. 添加“Android 符合性”作为“名称”。 此外，添加“说明”。
3. 对于“平台”，请选择“Android”。 
4. 选择“设置” > “系统安全”以显示 Android“系统安全”边栏选项卡。
5. 单击“需要密码才可解锁移动设备”旁边的“需要”。
6. 选择“所需的密码类型”旁边的“至少为数字”。
7. 在“最短密码长度”旁边输入“6”。 

    ![在 Microsoft Intune 中创建组的屏幕截图](media/quickstart-set-password-length-android/quickstart-set-password-length-android-01.png)

7. 完成后，单击“确定” > “确定” > “创建”以创建策略。

成功创建策略后，该策略将显示在“设备符合性策略”列表中。 

## <a name="clean-up-resources"></a>清理资源

不再需要时，删除该策略。 要执行此操作，请选择“符合性策略”，然后单击“删除”。

## <a name="next-steps"></a>后续步骤

在此快速入门中，你使用了 Intune 来为你的工作场所的 Android 设备创建符合性策略，以要求提供长度为至少六个字符的密码。 有关创建符合性策略的详细信息，请参阅 [Intune 中的设备符合性策略入门](device-compliance-get-started.md)。

要完成这一系列的 Intune 快速入门，请继续学习下一篇快速入门。

> [!div class="nextstepaction"]
> [快速入门：将通知发送到不相容设备](quickstart-send-notification.md)
