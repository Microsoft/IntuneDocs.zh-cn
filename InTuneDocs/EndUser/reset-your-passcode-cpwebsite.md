---
title: "如何从公司门户网站重置密码 | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
searchScope:
- Company Portal
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: a87fe0cf9591040f1455d71b1f40cd0705ba8abf
ms.openlocfilehash: a8ce59755a74199eda6865feda68c0613d10c2a7


---

# <a name="how-to-reset-your-device-passcode-from-the-company-portal-website"></a>如何从公司门户网站重置设备密码

如果丢失了设备 PIN 或在 Intune 中注册的设备的密码，则可以使用[公司门户网站](http://portal.manage.microsoft.com)进行重置。 可使用公司门户网站管理在 Intune 中注册的计算机和设备，还可以用于执行大多数使用公司门户应用时执行的相同任务。

> [!NOTE]
> 很可能你在公司门户网站中看不到“重置密码”按钮。 如果看不到该按钮，将需要联系 IT 管理员以通过公司门户网站获得支持。

重置密码：

1.  打开[公司门户网站](http://portal.manage.microsoft.com)，然后选择要重置密码的设备。

2.  选择“重置密码”。

    ![具有“重置密码”按钮的设备详细信息](./media/iwp-screen-with-all-options.png)

3.  选择“注销”，然后使用工作或学校凭据重新登录。 必须在五分钟内重新登录。

    ![具有“注销”按钮的重置消息](./media/iwp-2-sign-out.png)

4.  选择“重置密码”。

    ![重置密码时说明当前操作的消息](./media/iwp-3-tap-reset-passcode-after-signin.png)

    查看此表以了解“重置密码”在设备上的工作方式。

    |设备类型|重置密码时会发生什么情况|
    |------------|-----------|
    |Android|删除现有密码，然后使用字母和数字创建临时密码|
    |iOS|删除现有密码且不创建临时密码。 如果你使用 Touch ID 指纹扫描仪打开设备或购买商品，你将需要再次设置。|
    |Windows 10 移动版|删除现有密码，然后使用字母和数字创建临时密码。 使用 Windows Hello 面部识别进行登录时仍然受支持。|
    |Windows Phone 8.1|删除现有密码，然后使用数字创建临时密码。|

    5.  解锁设备，然后通过转到设备上的“设置”来设置新密码或更改临时密码。

    若要查看确认密码已重置成功的通知，请单击公司门户网站右上角的通知标志。

仍需要帮助？ 请与 IT 管理员联系。 有关联系信息，请查看[公司门户网站](http://portal.manage.microsoft.com)。



<!--HONumber=Jan17_HO4-->


