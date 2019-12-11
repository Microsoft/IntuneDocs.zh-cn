---
title: 在 Intune 公司门户中注册 Windows 10 设备 | Microsoft Docs
description: 在 Intune 公司门户中注册 Windows 10 设备的步骤
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/21/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 812e82df-76df-402b-bfe9-29302838f40e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: ca8b24a1e8d0da4386ab185533fec38d9b34eb21
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506251"
---
# <a name="enroll-windows-10-devices-with-intune-company-portal"></a>使用 Intune 公司门户注册 Windows 10 设备

使用 Intune 公司门户在组织的管理下注册 Windows 10 设备。 本文介绍如何注册使用 Windows 10 1607 版及更高版本和 Windows 10 1511 版及更早版本的设备。 在开始之前，请确保[验证你的设备上的版本](windows-enrollment-company-portal.md#find-windows-10-version-number)，以便可以按照正确的步骤操作。  

各种设备类型（包括桌面、手机和平板电脑）都支持 Windows 10。 无论使用哪种设备，注册步骤都是相同的。 但是，屏幕可能与本文中显示的图像略有不同。  
</br>
> [!VIDEO https://www.youtube.com/embed/TKQxEckBHiE?rel=0]

## <a name="enroll-windows-10-version-1607-and-later-device"></a>注册使用 Windows 10 1607 版及更高版本的设备 
以下步骤介绍如何注册在 Windows 10 1607 版及更高版本上运行的设备。  

1. 转到“开始”  。 如果使用的是 Windows 10 移动版设备，请继续访问“所有应用”列表  。

2. 打开“设置”应用  。 如果应用列表中没有随时可用的应用，请转到搜索栏，然后键入“settings”。

3. 选择“帐户”   > “访问工作或学校”   > “连接”  。  


    ![选择“访问工作学校帐户”](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

4. 若要转到你的组织的 Intune 登录页，请输入你的工作或学校电子邮件地址。 然后选择“下一步”  。  


   ![输入你的工作或学校帐户](./media/w10-enroll-rs1-set-up-work-or-school-account.png)  

5. 使用你的工作或学校帐户登录 Intune。  


    ![添加工作或学校帐户](./media/w10-enroll-rs1-enter-your-credentials.png)  

    你最后会看到一条显示你的公司或学校正在注册你的设备的消息。

6. 如果组织要求为 Windows Hello 设置 PIN，系统将提示输入验证码。 输入代码并继续完成屏幕上的步骤以创建 PIN。  

7. 在“设置完成!”  上 屏幕，请选择“完成”  。 你的设备现已注册。  

8. 要再次检查连接，请返回到“设置” > “帐户” > “使用工作或学校帐户”    。  现在应列出你的帐户。  


    ![验证已正确设置了连接](./media/w10-enroll-rs1-validate-successful-enrollment.png)  

仍无法访问工作或学校电子邮件、文件或其他数据？ 了解如何[解决帐户问题](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-access-work-or-school)。  

## <a name="enroll-windows-10-version-1511-and-earlier-device"></a>注册使用 Windows 10 1511 版及更早版本的设备  
以下步骤介绍如何注册在 Windows 10 1511 版及更早版本上运行的设备。  

1. 转到“开始”  。 如果使用的是 Windows 10 移动版设备，请继续访问“所有应用”列表  。

2. 打开“设置”应用  。 如果应用列表中没有随时可用的应用，请转到搜索栏，然后键入“settings”。

3. 选择“帐户” > “你的帐户”   。  


    ![选择“你的帐户”](./media/W10-enroll-2-accounts-your-account.png)  

5. 选择“添加工作单位或学校帐户”  。  


    ![选择“添加工作单位或学校帐户”](./media/w10-enroll-3-add-work-school-acct.png)  

6. 使用工作单位或学校凭据登录。  


    ![登录](./media/W10-enroll-4-sign-in.png)  

仍无法访问工作或学校电子邮件、文件或其他数据？ 了解如何在注册过程[解决与帐户相关的问题](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-your-account)。  

## <a name="it-administrator-support"></a>IT 管理员支持   

如果你是 IT 管理员且在注册设备时遇到问题，请参阅 [Microsoft Intune 中的 Windows 设备注册问题疑难解答](https://support.microsoft.com/help/4469913)。 本文列出了常见错误、错误原因及其解决方法步骤。 

## <a name="next-steps"></a>后续步骤  
如果需要有关公司门户或注册的帮助，请联系组织的 IT 支持团队。 可以在[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)中找到他们的联系信息。 使用你的工作或学校帐户登录到网站。  

 

