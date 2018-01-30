---
title: "如何从公司门户网站重置密码 | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 06/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
searchScope:
- User help
ROBOTS: 
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 111cbc1aa2dd9c537a7f5581d0dd6f2e75d8c7f3
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-reset-your-device-passcode-from-the-company-portal-website"></a>如何从公司门户网站重置设备密码

如果丢失了设备 PIN 或在 Intune 中注册的设备的密码，则可以使用[公司门户网站](https://portal.manage.microsoft.com#HelpDeskDialog)进行重置。 可使用公司门户网站管理在 Intune 中注册的计算机和设备，还可以用于执行大多数使用公司门户应用时执行的相同任务。

> [!NOTE]
> 如果使用企业注册设备，在公司门户网站上可能看不到“重置密码”按钮。 如果看不到，请联系公司支持人员为你重置密码。

重置密码：

1.  在[公司门户网站](https://portal.manage.microsoft.com#HelpDeskDialog)上，点击“菜单”按钮![菜单按钮的小图像，3 个水平条平行叠放。](/intune/media/CP_hamburger_menu.png)，然后选择“我的设备”。

2. 在“我的设备”页上，选择想要重置密码的设备名称。

  ![“我的设备”页的屏幕截图，横幅上方显示一些未识别的设备，提示注册未列出的设备或识别未识别的设备。](./media/macOS_enroll_002_tap_here_banner.png)

3.  设备将在弹出窗口中打开。 选择“重置密码”按钮。

    ![公司门户网站上已选设备的所有选项，包括重命名、删除、重置设备、重置密码和远程锁定。 ](./media/iwp-screen-with-all-options.png)

4.  系统会显示横幅，询问你是否确定要重置密码并在重置密码后从设备中注销。 然后，需要等待 5 分钟后才能重新登录。

  ![重置密码横幅，显示关于重置设备密码的警告以及用户将如何注销。用户输入的按钮为“注销”和“取消”。](./media/iwp-reset-passcode-popup.png)

5.  选择“注销”，将收到最后一条消息，告知你已删除设备中的密码。 如果设备未在身边，请勿删除密码，因为对设备具有物理访问权限的任何人将能够访问设备上的大部分信息（个人或公司信息）。 

  ![第二条重置密码横幅，显示关于重置设备密码的警告以及将如何删除设备中的密码。 该横幅还介绍了通过设备设置来设置新密码的方法。](./media/iwp-reset-passcode-2nd-popup.png)

  不同的设备具有不同的密码类型。

  **Android**：删除现有密码，然后使用字母和数字创建临时密码 
  
  > [!NOTE]
  > 不能为 Android 7.0 或更高版本的设备重置密码。 如果忘记密码，必须将设备重置为出厂设置。

  **iOS**：删除现有密码且不创建临时密码。 如果你使用 Touch ID 指纹扫描仪打开设备或购买商品，你将需要再次设置。

  **Windows 10 移动版**：删除现有密码，然后使用字母和数字创建临时密码。 使用 Windows Hello 面部识别进行登录时仍然受支持。
    
  **Windows Phone 8.1**：删除现有密码，然后使用数字创建临时密码

  对于 Android 和 Windows 设备，临时密码将显示在“设备详细信息”中。 

6.  解锁设备，然后通过转到设备上的“设置”来设置新密码或更改临时密码。

若要查看确认密码已重置成功的通知，请单击公司门户网站右上角的通知标志。

仍需帮助？ 请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://portal.manage.microsoft.com#HelpDeskDialog)。
