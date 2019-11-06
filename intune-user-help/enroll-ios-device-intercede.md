---
title: 向 Intune 公司门户和调解注册 iOS 或 iPadOS 设备
description: 了解如何注册 iOS 或 iPadOS 设备，以及如何使用调解设置派生凭据身份验证。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilver
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 02293b29f8634161582af2348b1cb30039ca3c52
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73415706"
---
# <a name="set-up-ios-or-ipados-device-with-company-portal-and-intercede"></a>设置 iOS 或 iPadOS 设备，并提供公司门户和调解

通过 Intune 公司门户应用注册设备，以获取对组织的电子邮件、文件和应用的安全移动访问权限。  注册设备后，它将成为托管设备  。 组织可通过移动设备管理 (MDM) 提供程序（如 Intune）为该设备分配策略和应用。  

在注册期间，你还将在设备上安装派生凭据。 你的组织可能需要在访问资源时使用派生凭据作为身份验证方法，或对电子邮件进行签名和加密。 

如果使用智能卡执行以下操作，则可能需要设置派生凭据：

* 登录到学校或工作应用、Wi-fi 和虚拟专用网络（VPN）
* 使用 S/MIME 证书对学校或工作电子邮件进行签名和加密  

在本文中，你将：  

* 使用 Intune 公司门户注册移动 iOS 或 iPadOS 设备。  
* 从组织的派生凭据提供程序（[调解](https://www.intercede.com/)）获取派生凭据。   


## <a name="what-are-derived-credentials"></a>什么是派生凭据？  
派生凭据是派生自智能卡凭据并在设备上安装的证书。 它授予你对工作资源的远程访问权限，同时防止未经授权的用户访问敏感信息。  

派生凭据用于： 
* 对登录到学校或工作应用、Wi-fi 和 VPN 的学生和员工进行身份验证
* 使用 S/MIME 证书对学校或工作电子邮件进行签名和加密  

派生凭据实现美国国家标准与技术研究院 (NIST) 关于派生个人身份验证 (PIV) 凭据的准则（属于《特殊出版物 (SP) 800-157》）。  

## <a name="prerequisites"></a>必备条件

 若要完成注册，你必须具有：

* 你的学校或工作提供的智能卡
* 访问计算机或自助服务展台，你可以在其中使用智能卡登录
* 你的移动设备
* 设备上安装的适用于 iOS 和 iPadOS 的 Intune 公司门户应用


## <a name="enroll-device"></a>注册设备  
1. 在你的移动设备上打开适用于 iOS/iPadOS 的公司门户应用，并使用你的工作帐户登录。  
2. 记下屏幕上显示的代码。  

    ![带有屏幕消息和代码的公司门户应用的示例图像。](./media/copy-code-intercede.png)  
1. 切换到已启用智能卡的设备，然后转到 https://microsoft.com/devicelogin 。 

1. 输入先前记下的代码。
 
2. 插入智能卡进行登录。   

3. 返回到移动设备上的公司门户应用，然后按照屏幕上的说明注册设备。  
4. 注册完成后，公司门户会通知你设置智能卡。 点击通知。 如果你没有收到通知，请检查你的电子邮件。   

    ![设备主屏幕上的公司门户推送通知的示例屏幕截图。](./media/action-required-in-app-intercede.png)  

5. 在 "**设置移动智能卡访问**" 屏幕上：  
    a. 点击指向组织设置说明的链接。 如果你的组织未提供其他说明，你将发送到本文。  
    b. 点击 "**开始**"。  

    ![公司门户设置移动智能卡访问屏幕的示例屏幕截图。](./media/smart-card-info-intercede.png)  

6. 切换到已启用智能卡的设备或自助服务展台，并打开 MyID 应用。 使用工作凭据登录。  
7. 选择请求 ID 的选项。 
8. 当系统询问你要使用的配置文件时，请选择要使用移动凭据激活的选项。 将显示 QR 码。  
9. 返回到你的移动设备。 在公司门户 >**获取 QR 码**屏幕上，点击 "**继续**"。  

    ![公司门户获取 QR 码屏幕的示例屏幕截图。](./media/get-qr-code-intercede.png) 
 
10. 点击 "**使用照相机** >  **" 确定 "** 。  

    ![公司门户提示符的示例屏幕截图，并请求允许相机访问的权限。](./media/allow-cp-camera-access-intercede.png)  

11. 扫描启用智能卡的设备上的 QR 码的映像。 
12. 等待公司门户完成设置设备。  

## <a name="next-steps"></a>后续步骤  
注册完成后，你将可以访问工作资源，如电子邮件、Wi-fi 和你的组织提供的任何应用。 有关如何获取、搜索、安装和卸载应用程序的详细信息公司门户参阅：

* [通过公司门户网站管理应用](manage-apps-cpweb.md)  
* [在设备上使用托管应用](use-managed-apps-on-your-device-ios.md)  

仍需帮助？ 请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)。
