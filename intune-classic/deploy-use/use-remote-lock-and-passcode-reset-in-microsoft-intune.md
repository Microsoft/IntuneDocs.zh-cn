---
title: "远程锁定和密码重置 | Microsoft Docs"
description: "Intune 提供远程锁定和密码重置功能。"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 970f8c81-7c7f-4789-9ed4-2133d50b9db6
ms.reviewer: chrisgre
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: e7cc218f34173443057eaa628ca8c7e4de8e3507
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017

---
# <a name="help-protect-your-devices-with-remote-lock-and-passcode-reset"></a>使用远程锁定和密码重置功能帮助保护设备

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune 提供远程锁定和密码重置功能。

## <a name="lock-a-device-remotely"></a>远程锁定设备
如果用户丢失其设备，你可以远程锁定该设备。 设备必须已设置 PIN 或密码才能使用远程锁定。

下表列出了是如何在不同的移动平台上进行远程锁定的。

|平台|远程锁定|
|------------|---------------|
|macOS|不支持|
|iOS|支持|
|Android|支持|
|Android for Work|支持|
|Windows 10（移动版）|支持|
|Windows 10（桌面版）|不支持|
|Windows Phone 8 和 Windows Phone 8.1|支持|
|Windows RT 8.1 和 Windows RT|如果设备的当前用户是注册设备的相同用户，则支持。|
|Windows 8.1|如果设备的当前用户是注册设备的相同用户，则支持。|

使用 Intune 软件客户端注册的 Windows 电脑不支持远程锁定。

### <a name="lock-a-mobile-device-remotely-through-the-intune-console"></a>通过 Intune 控制台远程锁定移动设备

1.  在 [Intune 管理员控制台](https://manage.microsoft.com/)中，依次选择“组”&gt;“所有设备”&gt;“所有移动设备”。

2.  选择“所有直接托管设备”（对于在 Intune 中注册的设备）或“所有 Exchange ActiveSync 托管设备”。

    > [!TIP]
    > 你还可以按用户导航到设备。 选择**所有用户**。 在用户的“属性”页，选择“设备”，然后选择要锁定的移动设备的名称。

3.  在列表中，选择要锁定的某个设备或多个设备。 在任务栏上，选择“远程任务”，然后选择“远程锁定”。

## <a name="reset-the-passcode-on-a-device"></a>重置设备的密码
如果用户忘记密码，则你可以删除设备中的密码，或者在设备上强制使用新的临时密码，从而帮助用户解决问题。 下表列出了在不同移动平台上重置密码的方法。

|平台|密码重置|
|------------|------------------|
|macOS|不支持|
|iOS|支持以便清除设备中的密码。 不创建新的临时密码。|
|Android|在早于 Android 7.0 的版本上受支持。 创建临时密码。|
|Android for Work|不支持|
|Windows 10 移动版|支持加入了 Azure AD 的 Windows 10 创意者版本和更高版本移动设备。|
|Windows Phone 8 和 Windows Phone 8.1|支持|
|Windows RT 8.1|不支持|
|Windows 8.1|不支持|
|Windows 10 桌面版|不支持|

使用 Intune 软件客户端注册的 Windows 电脑不支持密码重置。

### <a name="reset-a-passcode"></a>重置密码

1.  在 [Intune 管理员控制台](https://manage.microsoft.com/)中，依次选择“组”&gt;“所有设备”&gt;“所有移动设备”。

2.  选择“所有直接托管设备”（对于在 Intune 中注册的设备）或“所有 Exchange ActiveSync 托管设备”。

    > [!TIP]
    > 你还可以按用户导航到设备。 单击“所有用户”。 在用户的“属性”页，单击“设备”，然后单击你要擦除的移动设备的名称。

3.  在列表中，选择要锁定的某个设备或多个设备。 在任务栏上，选择“远程任务”，然后选择“密码重置”。


### <a name="see-also"></a>另请参阅
[停用设备](retire-devices-from-microsoft-intune-management.md)和[设备数据管理的 Windows 选择性擦除](http://technet.microsoft.com/library/dn486874.aspx)

