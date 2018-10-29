---
title: 快速入门：为 Windows 10 设备添加设备符合性策略
description: 使用本快速入门创建策略来帮助保护公司数据并管理最终用户用于访问公司资源的设备。 然后，向组分配策略。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9d9169ab353da30e0f7b292cea4f5b9c93e316aa
ms.sourcegitcommit: 2e88ec7a412a2db35034d30a70d20a5014ddddee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/17/2018
ms.locfileid: "49391546"
---
# <a name="quickstart-add-a-device-compliance-policy-for-a-windows-10-device"></a>快速入门：为 Windows 10 设备添加设备符合性策略
适用于 Windows 的 Intune 设备符合性策略可指定 Windows 设备须满足才能被视为符合的规则和设置。 可以将这些策略与[条件访问](https://docs.microsoft.com/intune/conditional-access)结合使用，从而允许或阻止访问公司资源。 还可获取设备报表并针对非符合性采取措施。

在本快速入门中，将为 Windows 10 设备创建设备符合性策略，然后将设备组分配给该策略。

如果没有 Intune 订阅，请[注册免费试用帐户](free-trial-sign-up.md)。

## <a name="prerequisites"></a>先決條件
- 要完成本快速入门，必须先[创建用户](quickstart-create-user.md)并[创建组](quickstart-create-group.md)。


## <a name="sign-in-to-intune"></a>登录到 Intune
以全局管理员或 Intune 服务管理员身份登录 [Intune](https://aka.ms/intuneportal)。

## <a name="create-a-device-compliance-policy"></a>创建设备合规性策略
1. 选择“设备符合性” > “策略” > “创建策略”。
2. 在“名称”中输入“Windows 10 符合性”，在“说明”中输入“适用于 Windows 10 的示例符合性政策”。
3. 在“平台”中，选择“Windows 10 及更高版本”。
4. 在“设置”中，选择“系统安全”，然后将“需要密码才可解锁移动设备”设置为“需要”。 策略设置完成后，选择“确定”。
   ![符合性策略](/intune/media/quickstart-create-policy/compliance-policy.png)
5. 关闭“Windows 10 符合性策略”窗格。 
6. 在“创建策略”窗格下，选择“创建”。 此步骤可创建策略并在“设备符合性” > “策略”下列出该策略。
7. 选择新策略，然后选择“分配”。 可以包括或排除 Azure Active Directory (AD) 安全组。
8. 选择“所选组”可查看现有 Azure AD 安全组。 选择“Contoso 测试人员”，然后选择“保存”，将策略部署到组中的用户。 如果未在[创建组](quickstart-create-group.md)中创建此组，则可以使用你选择的组。 

## <a name="clean-up-resources"></a>清理资源
不再需要时，删除该策略。 要执行此操作，请选择“Windows 10 符合性”策略，然后单击“删除”。 

## <a name="next-steps"></a>后续步骤
在本快速入门中，已创建并分配了一个简单的设备符合性策略。 要注册将接收该策略的 Windows 10 设备，请继续按快速入门设置自动注册。 
 
> [!div class="nextstepaction"]
> [设置设备密码长度](quickstart-set-password-length-android.md)