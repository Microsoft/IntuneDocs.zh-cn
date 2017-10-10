---
title: "如何登录公司门户应用 | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cfd214bc-f072-4808-af2e-a3cbf7af9bca
searchScope: User help
ROBOTS: 
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: ca6d811d884b5405bdb4e5f096366c123d8e00d1
ms.sourcegitcommit: db7a7bbead3a3fa78c4d643607f709a2909eb608
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/28/2017
---
# <a name="how-do-i-sign-in-to-the-company-portal-app---user-story-1132123--"></a>如何登录公司门户应用？ <!--User Story 1132123-->

使用公司门户应用访问公司资源，如电子邮件和企业应用。 主要可以通过两种方式登录到公司门户：

* 使用工作电子邮件地址和密码
* 从另一台设备登录

虽然以下图片是基于 iOS 设备，但这一过程与适用于 Android 和 Windows 设备的过程几乎相同。

## <a name="signing-in-with-your-email-address-and-password"></a>使用电子邮件地址和密码登陆

1. 在设备上打开公司门户应用，点击“登录”。

  ![公司门户登录页，网站的图形表示形式前面显示一个人形图标。 下面是“登录”按钮。 底部的链接指向 Microsoft 隐私和 Cookie 信息。](/intune/media/cp_ios_aad_signin_after_1704_001.png)

  还没有公司门户应用？ 了解如何为 [iOS](install-and-sign-in-to-the-intune-company-portal-app-ios.md) 或 [Android](install-the-company-portal-app-android.md) 安装和下载该应用。

2. 输入**工作或学校账户**。

  ![提示用户只提供电子邮件地址，而不是在同一屏幕上同时提供电子邮件和密码。](/intune/media/cp_ios_aad_signin_after_1704_002.png)

3. 等待片刻，直至电子邮件地址被接受，然后输入密码。

  ![在接受其电子邮件地址之后，提示用户输入密码。](/intune/media/cp_ios_aad_signin_after_1704_003.png)

4. 公司门户接受登录请求之后，便成功登录，并可开始访问公司资源。   

  ![在经过身份验证过程后，公司门户应用进行登录，并通过加载栏进行提示。](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

## <a name="signing-in-from-another-device"></a>从另一台设备登录

如果不使用密码登录到公司资源，作为确认自己拥有正确访问级别的一个方法，也可以使用另一台设备登录。 如果公司使用智能卡访问用户的电脑，用户很可能需要使用另一台设备登录。

1. 选择电子邮件文本框下方的“从另一台设备登录”链接，而不是输入电子邮件地址。

  ![公司门户登录页，网站的图形表示形式前面显示一个人形图标。 下面是“登录”按钮。 底部的链接指向 Microsoft 隐私和 Cookie 信息。](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_001.png)

2. 会收到用于登录公司门户的一次性唯一验证码。

  ![通过使用工作计算机的唯一密码访问 aka.ms/devicelogin 页面，然后使用验证码进行登录可获得说明。](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_003.png)

3. 在其他设备上打开浏览器，转到 [https://aka.ms/devicelogin](https://aka.ms/devicelogin) 并输入验证码。

  ![用户工作计算机上用户浏览器的图像，而不是公司门户应用的图像。 显示的“设备登录”页将提示用户输入他们在公司门户应用中收到的验证码。](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

4. “设备登录”页面验证该验证码之后，选择“继续”以允许公司门户在其他设备上登录。

  ![用户已将唯一代码输入到字段中，“设备登录”站点要求确认 Intune 公司门户是接收授权以进行登录的正确应用。](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

5. 验证码经验证后，便可关闭窗口。

  ![确认页显示用户现在已登录其设备上的公司门户应用，可以关闭此页。](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

6. 在原始设备上，公司门户应用开始登录。

  ![通过身份验证过程后，公司门户应用登录，并通过一个加载条提示进程。](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

仍需要帮助？ 请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://portal.manage.microsoft.com)。
