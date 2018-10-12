---
title: 快速入门 - 创建适用于 iOS 设备的电子邮件设备配置文件
titlesuffix: Microsoft Intune
description: 了解如何使用 Microsoft Intune 创建电子邮件设备配置文件，以便 iOS 设备可以安全地连接到公司电子邮件。
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 09/21/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a0c554315168147249e0842b69e3e6195ed85979
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581550"
---
# <a name="quickstart-create-an-email-device-profile-for-ios"></a>快速入门：创建适用于 iOS 设备的电子邮件设备配置文件

在本快速入门中，你将了解如何创建适用于 iOS 设备的电子邮件设备配置文件。 本配置文件指定了 iOS 设备上内置电子邮件应用连接到公司电子邮件所需的设置。 电子邮件设备配置文件有助于跨设备标准化设置，并允许最终用户在不进行任何所需设置的情况下在其个人设备上访问公司电子邮件。 要进一步保护电子邮件，可以使用电子邮件配置文件来确定设备是否符合要求，然后设置条件访问权限以仅允许兼容设备访问电子邮件。 有关电子邮件配置文件的详细信息，请参阅[如何在 Microsoft Intune 中配置电子邮件设置](email-settings-configure.md)

如果没有 Intune 订阅，请[注册免费试用帐户](free-trial-sign-up.md)。

## <a name="sign-in-to-intune"></a>登录到 Intune

以全局管理员或 Intune 服务管理员身份登录 [Intune](https://aka.ms/intuneportal)。 通过选择“所有服务” > “Intune”，在 Azure 门户中查找 Intune。

## <a name="create-an-ios-email-profile"></a>创建 iOS 电子邮件配置文件
1. 在 Intune 中选择“设备配置”，然后选择“配置文件”。
2. 选择“创建配置文件”。
   
   ![创建适用于 iOS 的电子邮件配置文件](media/quickstart-email-profile/ios-create-profile.png)

3. 在“名称”下，输入新配置文件的描述性名称。 对于本示例，请输入“iOS 需要的工作电子邮件”。
4. 输入以下配置文件信息：
   - 对于“描述”，请输入“需要 iOS 设备使用工作电子邮件”。
   - 对于“平台”，请选择“iOS”。
   - 对于“配置文件类型”，请选择“电子邮件”。
    
     ![创建适用于 iOS 的电子邮件配置文件](media/quickstart-email-profile/ios-email-profile-name.png)

5. 选择“设置”，并输入以下设置（保留其他设置的默认值）：
   - **电子邮件服务器**：对于本快速入门，输入“outlook.office365.com”。 本设置指定 iOS 邮件应用用于连接到电子邮件的电子邮件服务器的 Exchange 位置 (URL)。
   - **帐户名称**：输入“公司电子邮件”。
   - **AAD 中的用户名属性**：此名称是 Intune 从 Azure Active Directory (Azure AD) 获取的属性。 Intune 使用此名称动态生成此配置文件的用户名。 在本快速入门中，我们假设希望将“用户主体名称”用作配置文件的用户名（例如，user1@contoso.com）。
   - **AAD 中的电子邮件地址属性**：此设置将设置 Azure AD 中用于登录 Exchange 的电子邮件地址。 在本快速入门中，选择“用户主体名称”。
   - **身份验证方法**：在本快速入门中，选择“用户名和密码”。 （如果已经为 Intune 设置了证书，也可以选择“证书”。）
    
     ![创建适用于 iOS 的电子邮件配置文件](media/quickstart-email-profile/ios-email-profile.png)

6. 选择“确定”。
7. 选择“创建”。 新的配置文件将显示在配置文件列表中，并显示仪表板，以便监视如何将配置文件分配给 iOS 设备和 iOS 用户。
8. 选择“分配”。
9. 选择“Include”选项卡，然后选择“所有用户和所有设备”。 
10. 选择“保存”。

## <a name="clean-up-resources"></a>清理资源
如果不想使用为其他教程或测试创建的配置文件，可以立即删除它。
1. 在 Intune 中选择“设备配置”，然后选择“配置文件”。
2. 选择创建的测试配置文件，“iOS 需要的工作电子邮件”。
3. 选择配置文件旁边的省略号（“...”），然后选择“删除”。

## <a name="next-steps"></a>后续步骤

在本快速入门中，创建适用于 iOS 设备的电子邮件配置文件。 现在可以使用此配置文件来确定 iOS 设备是否合规，方法是创建符合性策略，将任何与该配置文件不匹配的 iOS 设备标记为不合规。 对于进一步保护，可以创建条件访问策略，阻止不符合的 iOS 设备访问电子邮件。

> [!div class="nextstepaction"]
> [Intune 中的设备符合性策略入门](device-compliance-get-started.md)
