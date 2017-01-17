---
title: "从公司门户网站重置设备密码 | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 09/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: db5714009d4d0bcdd77be23314e4f2ff4db44b6e
ms.openlocfilehash: 975759db98854c8276999592d6ecdba195438681


---


# <a name="reset-your-device-passcode-from-the-company-portal-website"></a>从公司门户网站重置设备密码

如果丢失了设备 PIN 或在 Intune 中注册的设备的密码，则可以使用[公司门户网站](http://portal.manage.microsoft.com)进行重置。 可使用公司门户网站管理在 Intune 中注册的计算机和设备，还可以用于执行大多数使用公司门户应用时执行的相同任务。

> [!NOTE]
> 公司门户网站上可能不会显示“重置密码”按钮，这具体取决于 IT 管理员配置 Intune 的方式。 Windows 8.1 设备不支持密码重置。

重置密码：

1.  打开[公司门户网站](http://portal.manage.microsoft.com)，然后选择要重置密码的设备。

2.  选择“重置密码”。

    ![具有“重置密码”按钮的设备详细信息](./media/iwp-screen-with-all-options.png)

3.  选择“注销”，然后使用工作或学校凭据重新登录。 必须在五分钟内重新登录。

    ![具有“注销”按钮的重置消息](./media/iwp-2-sign-out.png)

4.  选择“重置密码”。

    ![重置密码时说明当前操作的消息](./media/iwp-3-tap-reset-passcode-after-signin.png)

    查看此表以了解“重置密码”在设备上的工作方式。

    |平台|Support|
    |------------|-----------|
    |Android|创建临时字母数字密码。|
    |iOS|从设备删除密码且不会创建临时密码。 如果使用的是 Touch ID，则需要在设备上对其进行重新设置，因为重置密码时会将其删除。|
    |Windows 10（仅适用于移动设备）|创建临时字母数字密码。 支持 Windows Hello。|
    |Windows Phone 8.1|创建临时数字密码。|
    解锁设备后，可以转到设备上的“设置”来设置新密码。

5.  解锁设备，然后通过转到设备上的“设置”来设置新密码或更改临时密码。

    若要查看确认密码已重置成功的通知，请单击公司门户网站右上角的通知标志。

仍需要帮助？ 请与 IT 管理员联系。 有关联系信息，请查看[公司门户网站](http://portal.manage.microsoft.com)。



<!--HONumber=Dec16_HO3-->


