---
title: 教程 - 保护非托管设备上的 Exchange Online 电子邮件
titleSuffix: Microsoft Intune
description: 了解如何使用 Intune 应用保护策略和 Azure AD 条件访问来保护 Office 365 Exchange Online。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/26/2019
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e6224a0dae7c0aa3d80d4e64331a668953220f65
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61515700"
---
# <a name="tutorial-protect-exchange-online-email-on-unmanaged-devices"></a>教程：保护非托管设备上的 Exchange Online 电子邮件

了解如何使用应用保护策略和条件访问来保护 Exchange Online，即使未在 Intune 等设备管理解决方案中注册设备。 在本教程中，你将学习如何执行以下操作： 

> [!div class="checklist"]
> * 为 Outlook 应用创建 Intune 应用保护策略。 可以通过阻止“另存为”和限制剪切、复制和粘贴操作来限制用户对应用数据的使用。 
> * 创建 Azure Active Directory (Azure AD) 条件访问策略，仅允许 Outlook 应用访问 Exchange Online 中的公司电子邮件。 还需要为新式身份验证客户端（如 Outlook for iOS 和 Outlook for Android）提供多重身份验证 (MFA)。

## <a name="prerequisites"></a>必备条件
  - 在本教程中，你将需要一个具有以下订阅的测试租户：
    - Azure Active Directory Premium（[免费试用版](https://azure.microsoft.com/free/?WT.mc_id=A261C142F)）
    - Intune 订阅（[免费试用](free-trial-sign-up.md)）
    - Office 365 商业版订阅，包括 Exchange（[免费试用版](https://go.microsoft.com/fwlink/p/?LinkID=510938)）

## <a name="sign-in-to-intune"></a>登录到 Intune

以全局管理员或 Intune 服务管理员身份登录 [Intune](https://aka.ms/intuneportal)。 通过选择“所有服务” > “Intune”，在 Azure 门户中查找 Intune。

## <a name="create-the-app-protection-policy"></a>创建应用保护策略
对于本教程，我们将设置面向 Outlook 应用的 Intune 应用保护策略，以便在应用程序级别设置保护。 我们需要一个 PIN 在工作环境中打开应用程序。 我们还将限制应用程序之间的数据共享，并防止公司数据被保存到个人位置。

1.  在 Intune 中，选择“客户端应用” > “应用保护策略” > “添加策略”。
2.  在“名称”中，输入“Outlook 应用策略测试”。
3.  在“描述”中，输入“Outlook 应用策略测试”。
4.  选择“应用”。 在应用程序列表中，选择“Outlook”，然后选择“选择”。
5.  选择“设置”。 
6.  在“数据重定位”下，为本教程选择以下设置：

    - 对于“允许应用向其他应用传送数据”，选择“无”。
    - 对于“允许应用从其他应用接收数据”，选择“无”。
    - 对于阻止“另存为”，选择“是”。
    - 对于“限制使用其他应用进行剪切、复制和粘贴”，选择“阻止”。
   
     ![选择 Outlook 应用保护策略数据重定位设置](media/tutorial-protect-email-on-unmanaged-devices/outlook-app-data-relocation.png)
    
7.  在“访问操作”下，为本教程选择以下设置：

    - 对于“需要 PIN 才能进行访问”，选择“是”。
    - 对于“访问需要公司凭据”，选择“是”。
    - 保留所有其他设置的默认值。
 
     ![选择 Outlook 应用保护策略访问操作](media/tutorial-protect-email-on-unmanaged-devices/outlook-app-access-actions.png)

9.  选择“确定”。
10. 选择“创建”。

将创建 Outlook 的应用保护策略。 现在可以设置条件访问以要求设备使用 Outlook 应用。

## <a name="create-conditional-access-policies"></a>创建条件访问策略
现在我们将创建两个条件访问策略，以涵盖所有设备平台。 第一个策略将要求新式身份验证客户端（如 Outlook for iOS 和 Outlook for Android）使用已批准的 Outlook 应用和 MFA。 第二个策略要求 Exchange ActiveSync 客户端使用已批准的 Outlook 应用。 （目前，Exchange Active Sync 不支持设备平台以外的条件）。 可在 Azure AD 门户或 Intune 门户中配置条件访问策略。 由于我们已在 Intune 门户中，我们将在此处创建该策略。
### <a name="create-an-mfa-policy-for-modern-authentication-clients"></a>为新式身份验证客户端创建 MFA 策略
1.  在 Intune 中，选择“条件访问” > “策略” > “新建策略”。
1.  在“名称”中，输入“新式身份验证客户端的测试策略”。 
3.  在“分配”下，选择“用户和组”。 在“包含”选项卡上，选择“所有用户”，然后选择“完成”。

4.  在“分配”下，选择“云应用”。 因为我们要保护 Office 365 Exchange Online 电子邮件，我们将通过执行以下步骤来进行选择：
     
    1. 在“包含”选项卡上，选择“选择应用”。
    2. 选择“选择”。 
    3. 在应用程序列表中，选择“Office 365 Exchange Online”，然后选择“选择”。 
    4. 选择“完成”。
  
    ![选择 Office 365 Exchange Online 应用](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-cloud-apps.png)

5.  在“分配”下，选择“条件” > “设备平台”。
     
    1. 在“配置”下，选择“是”。
    2. 在“包含”选项卡上，选择“任何设备”。
    1. 选择“完成”。
   
6.  在“条件”窗格上，选择“客户端应用”。
     
    1. 在“配置”下，选择“是”。
    2. 选择“移动应用和桌面客户端”和“新式身份验证客户端”。
    3. 清除其他复选框。
    4. 选择“完成”，然后再次选择“完成”。
    
    ![选择 Office 365 Exchange Online 应用](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-client-apps.png)

7.  在“访问控制”下，选择“授予”。 
     
    1. 在“授予”窗格上，选择“授予访问权限”。
    2. 选择“需要多重身份验证”。
    4. 选择“需要已批准的客户端应用”。
    5. 在“对于多个控件”下，选择“需要所有已选控件”。 此设置可确保当设备尝试访问电子邮件时强制执行所选的这两项要求。
    6. 选择“选择”。
     
    ![选择 Office 365 Exchange Online 应用](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-mfa.png)

8.  在“启用策略”下，选择“开启”。
     
    ![选择 Office 365 Exchange Online 应用](media/tutorial-protect-email-on-unmanaged-devices/enable-policy.png)

9.  选择“创建”。

将创建新式身份验证客户端条件访问策略。 现在可以为 Exchange Active Sync 客户端创建一个策略。

### <a name="create-a-policy-for-exchange-active-sync-clients"></a>为 Exchange Active Sync 客户端创建策略
1.  在 Intune 中，选择“条件访问” > “策略” > “新建策略”。
2.  在“名称”中，输入“EAS 客户端的测试策略”。 
3.  在“分配”下，选择“用户和组”。 在“包含”选项卡上，选择“所有用户”，然后选择“完成”。

4.  在“分配”下，选择“云应用”。 通过以下步骤选择 Office 365 Exchange Online 电子邮件：
     
    1. 在“包含”选项卡上，选择“选择应用”。
    2. 选择“选择”。 
    3. 在应用程序列表中，选择“Office 365 Exchange Online”，然后选择“选择”。 
    4. 选择“完成”。

5.  在“分配”下，选择“条件” > “设备平台”。
     
    1. 在“配置”下，选择“是”。
    2. 在“包含”选项卡上，选择“任何设备”，然后选择“完成”。 
    3. 再次选择“完成”。

6.  在“条件”窗格上，选择“客户端应用”。
     
    1. 在“配置”下，选择“是”。
    2. 选择“移动应用和桌面客户端”。
    3. 选择“Exchange ActiveSync 客户端”和“仅将策略应用于受支持的平台”。 
    4. 清除所有其他复选框。
    5. 选择“完成”，然后再次选择“完成”。
    
    ![选择 Office 365 Exchange Online 应用](media/tutorial-protect-email-on-unmanaged-devices/eas-client-apps.png)

7.  在“访问控制”下，选择“授予”。 
     
    1. 在“授予”窗格上，选择“授予访问权限”。
    4. 选择“需要已批准的客户端应用”。 清除所有其他复选框。
    6. 选择“选择”。
     
    ![选择 Office 365 Exchange Online 应用](media/tutorial-protect-email-on-unmanaged-devices/eas-grant-access.png)

8.  在“启用策略”下，选择“开启”。

9.  选择“创建”。

应用保护策略和条件访问现已就绪，可以进行测试了。 

## <a name="try-it-out"></a>试试看
使用已创建的策略后，设备将需要在 Intune 中注册并使用 Outlook 移动应用才能访问 Office 365 电子邮件。 若要在 iOS 设备上测试此方案，请尝试使用测试租户中用户的凭据登录到 Exchange Online。
1. 若要在 iPhone 上测试，请转到“设置” > “密码和帐户” > “添加帐户” > “Exchange”。
2. 在测试租户中，为用户输入电子邮件地址，然后按“下一步”。
3. 按“登录”。
4. 输入测试用户的密码，然后按“登录”。
5. 将出现消息“需要更多信息”，这意味着系统会提示你设置 MFA。 继续操作并设置其他验证方法。
6. 接下来你将看到一条消息，指示你正试图用 IT 部门尚未批准的应用打开此资源。 这意味着你将被阻止使用本机邮件应用。 取消登录。
7.  打开 Outlook 应用，并选择“设置” > “添加帐户” > “添加电子邮件帐户”。
8. 在测试租户中，为用户输入电子邮件地址，然后按“下一步”。
9. 按“使用 Office 365 登录”。 系统将提示你进行额外的身份验证和注册。 登录后，可以测试操作，如剪切、复制、粘贴和“另存为”。

## <a name="clean-up-resources"></a>清理资源
当不再需要测试策略时，可以删除它们。
1. 以全局管理员或 Intune 服务管理员身份登录 [Intune](https://aka.ms/intuneportal)。
2. 选择“设备符合性” > “策略”。
3. 在“策略名称”列表中，为测试策略选择上下文菜单 (...)，然后选择“删除”。 选择“确定”进行确认。
4. 选择“条件访问” > “策略”。
5. 在“策略名称”列表中，为每个测试策略选择上下文菜单 (...)，然后选择“删除”。 单击“是”以确认。

 ## <a name="next-steps"></a>后续步骤 
在本教程中，创建了应用保护策略来限制用户对 Outlook 应用的操作，还创建了需要 Outlook 应用并要求对新式身份验证客户端进行 MFA 的条件访问策略。 若要了解如何将 Intune 与条件访问结合使用来保护其他应用和服务，请参阅[设置条件访问](conditional-access.md)。
