---
title: 教程 - 保护 Intune 托管设备上的 Exchange Online 电子邮件
titleSuffix: Microsoft Intune
description: 了解如何使用 iOS Intune 符合性策略和 Azure AD 条件访问保护 Exchange Online，以要求托管设备和 Outlook 应用。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/26/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a2d6f14b4b3e1e981cce789664203b74523b2474
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71727930"
---
# <a name="tutorial-protect-exchange-online-email-on-managed-devices"></a>教程：保护托管设备上的 Exchange Online 电子邮件
了解如何使用设备符合性策略与条件访问，以确保 iOS 设备仅在由 Intune 托管并使用已批准的电子邮件应用时才可以访问 Exchange Online 电子邮件。 

在本教程中，你将学习如何执行以下操作： 
> [!div class="checklist"]
> * 创建 Intune iOS 设备符合性策略以设置设备必须满足才能被视为符合的条件。
> * 创建 Azure Active Directory (Azure AD) 条件访问策略，该策略要求在 Intune 中注册 iOS 设备、符合 Intune 策略并使用已批准的 Outlook 移动应用访问 Exchange Online 电子邮件。

如果没有 Intune 订阅，请[注册免费试用帐户](../fundamentals/free-trial-sign-up.md)。

## <a name="prerequisites"></a>必备条件
- 在本教程中，你将需要一个具有以下订阅的测试租户：
  - Azure Active Directory Premium（[免费试用版](https://azure.microsoft.com/free/?WT.mc_id=A261C142F)）
  - Office 365 商业版订阅，包括 Exchange（[免费试用版](https://go.microsoft.com/fwlink/p/?LinkID=510938)）
- 在开始之前，按照[快速入门：创建适用于 iOS 的电子邮件设备配置文件](../configuration/quickstart-email-profile.md)中的步骤创建适用于 iOS 设备的测试设备配置文件。

## <a name="sign-in-to-intune"></a>登录到 Intune

以全局管理员或 Intune 服务管理员身份登录 [Intune](https://aka.ms/intuneportal)。 如果已创建 Intune 试用版订阅，则用于创建订阅的帐户就是全局管理员。

## <a name="create-the-ios-device-compliance-policy"></a>创建 iOS 设备符合性策略
设置 Intune 设备符合性策略以设置设备必须满足才能被视为符合的条件。 在本教程中，我们将为 iOS 设备创建设备符合性策略。 符合性策略是特定于平台的，因此针对要评估的每个设备平台需要单独的符合性策略。

1. 在 Intune 中，选择“设备符合性”   > “策略”   > “创建策略”  。
2. 在“名称”  中，输入“iOS 符合性策略测试”  。 
3. 在“描述”  中，输入“iOS 符合性策略测试”  。
4. 在“平台”  下，选择“iOS”  。 
5. 选择“设置”   > “电子邮件”  。 
     
    1. 在“需要移动设备具有托管电子邮件配置文件”  旁边，选择“需要”  。
    2. 选择“确定”  。

    ![将电子邮件符合性策略设置为需要托管电子邮件配置文件](./media/tutorial-protect-email-on-enrolled-devices/ios-compliance-policy-email.png)
    
6. 选择“设备健康状况”  。 在“已越狱的设备”  旁边，选择“块”  ，然后选择“确定”  。
7. 选择“系统安全”  并输入“密码”  设置。 对于本教程，选择以下建议的设置：
     
    - 对于“需要密码才可解锁移动设备”  ，请选择“需要”  。
    - 对于“简单密码”  ，请选择“阻止”  。
    - 对于“最短密码长度”  ，请输入“4”  。
    - 对于“所需的密码类型”  ，请选择“字母数字”  。
    - 对于“屏幕锁定后要求提供密码之前的最大分钟数”  ，请选择“立即”  。
    - 对于“密码过期(天数)”  ，请输入“41”  。
    - 对于“阻止重用的曾用密码数”  ，请输入“5”  。
 
    ![设置电子邮件符合性策略的密码设置](./media/tutorial-protect-email-on-enrolled-devices/ios-compliance-policy-system-security.png)

8. 选择“确定”  ，然后再次选择“确定”  。
9. 选择“创建”  。

## <a name="create-the-conditional-access-policy"></a>创建条件访问策略
现在我们将创建一个条件访问策略，要求所有设备平台在 Intune 中注册并符合我们的 Intune 符合性策略，之后才能访问 Exchange Online。 我们也将要求使用 Outlook 应用访问电子邮件。 条件访问策略可在 Azure AD 门户或 Intune 门户中配置。 由于我们已在 Intune 门户中，我们将在此处创建该策略。
1. 在 Intune 中，选择“条件访问”   > “策略”   > “新建策略”  。
1. 在“名称”  中，输入“Office 365 电子邮件的测试策略”  。 
3. 在“分配”  下，选择“用户和组”  。 在“包含”  选项卡上，选择“所有用户”  ，然后选择“完成”  。

4. 在“分配”  下，选择“云应用”  。 因为我们要保护 Office 365 Exchange Online 电子邮件，我们将通过执行以下步骤来进行选择：
     
    1. 在“包含”  选项卡上，选择“选择应用”  。
    2. 选择“选择”  。 
    3. 在应用程序列表中，选择“Office 365 Exchange Online”  ，然后选择“选择”  。 
    4. 选择“完成”  。
  
    ![选择 Office 365 Exchange Online 应用](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-cloud-apps.png)

5. 在“分配”  下，选择“条件”   > “设备平台”  。
     
    1. 在“配置”  下，选择“是”  。
    2. 在“包含”  选项卡上，选择“任何设备”  ，然后选择“完成”  。 
    3. 再次选择“完成”  。
   
    ![选择 Office 365 Exchange Online 应用](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-cloud-device-platforms.png)

6. 在“分配”  下，选择“条件”   > “客户端应用”  。
     
    1. 在“配置”  下，选择“是”  。
    2. 对于本教程，请选择“移动应用和桌面客户端”  以及“新式身份验证客户端”  （是指 Outlook for iOS 和 Outlook for Android 等应用）。 清除所有其他复选框。
    3. 选择“完成”  ，然后再次选择“完成”  。
    
    ![选择 Office 365 Exchange Online 应用](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-client-apps.png)

7. 在“访问控制”  下，选择“授予”  。 
     
    1. 在“授予”  窗格上，选择“授予访问权限”  。
    2. 选择“需要将设备标记为兼容”  。 
    3. 选择“需要已批准的客户端应用”  。
    4. 在“对于多个控件”  下，选择“需要所有已选控件”  。 此设置可确保当设备尝试访问电子邮件时强制执行所选的这两项要求。
    5. 选择“选择”  。
     
    ![选择 Office 365 Exchange Online 应用](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-grant-access.png)

8. 在“启用策略”  下，选择“开启”  。
     
    ![选择 Office 365 Exchange Online 应用](./media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-enable-policy.png)

9. 选择“创建”  。

## <a name="try-it-out"></a>试试看
使用已创建的策略后，尝试登录到 Office 365 电子邮件的任何 iOS 设备都将需要在 Intune 中注册并使用适用于 iOS 的 Outlook 移动应用。 若要在 iOS 设备上测试此方案，请尝试使用测试租户中用户的凭据登录到 Exchange Online。 系统将提示你注册该设备并安装 Outlook 移动应用。
1. 若要在 iPhone 上测试，请转到“设置”   > “密码和帐户”   > “添加帐户”   > “Exchange”  。
2. 在测试租户中，为用户输入电子邮件地址，然后按“下一步”  。
3. 按“登录”  。
4. 输入测试用户的密码，然后按“登录”  。
5. 此时将显示一条消息，指出你的设备必须进行托管才能访问资源，并显示一个注册选项。 

## <a name="clean-up-resources"></a>清理资源
当不再需要测试策略时，可以删除它们。
1. 以全局管理员或 Intune 服务管理员身份登录 [Intune](https://aka.ms/intuneportal)。
2. 选择“设备符合性”   > “策略”  。
3. 在“策略名称”  列表中，为测试策略选择上下文菜单 (...  )，然后选择“删除”  。 选择“确定”  进行确认。
4. 选择“条件访问”   > “策略”  。
5. 在“策略名称”  列表中，为测试策略选择上下文菜单 (...  )，然后选择“删除”  。 单击“是”  以确认。

## <a name="next-steps"></a>后续步骤 
在本教程中，创建了需要在 Intune 中注册 iOS 设备并使用 Outlook 应用访问 Exchange Online 电子邮件的策略。 若要了解如何将 Intune 与条件访问结合使用来保护其他应用和服务（包括适用于 Office 365 Exchange Online 的 Exchange ActiveSync 客户端），请参阅[设置条件访问](conditional-access.md)。
