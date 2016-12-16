---
title: "Lookout 集成故障排除 | Microsoft Docs"
description: "本主题介绍了 Lookout 集成中常见的故障排除问题"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbe0b5f4-b8bc-49f3-85a9-51fb2f226fca
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d6ff74f0b46baf384dbdedf13ad75538dd33a089
ms.openlocfilehash: 416f200bdb72bae98897cb8d279dbdb767757da9


---

# <a name="troubleshoot-lookout-integration-with-intune"></a>使用 Intune 集成 Lookout 的故障排除
本主题介绍设置 Lookout 移动威胁保护 (MTP) 时可能遇到的一些常见问题。
## <a name="troubleshoot-login-errors"></a>登录错误故障排除
### <a name="403-errors"></a>403 错误
登录 [Lookout MTP 控制台](https://aad.lookout.com)时可能出现 403 错误：**你无权访问此服务** 当指定的用户名不属于配置了 Lookout MTP 访问权限的 Azure Active Directory (Azure AD) 组时，可能出现此错误。

Lookout MTP 配置为仅允许已配置 Azure AD 组的用户访问。 若不确定配置了 Lookout MTP 访问权限的组，请联系 Lookout 支持。

可通过以下方式联系 Lookout 支持：

* 电子邮件：enterprisesupport@lookout.com
* 登录到 [MTP 控制台](http://aad.lookout.com)，并导航到“支持”模块。
* 转到：https://enterprise.support.lookout.com/hc/en-us/requests，并请求支持。

### <a name="unable-to-sign-in"></a>无法登陆
Azure AD 全局管理员用户未接受初始 Lookout 设置时，可能出现以下错误。

![显示登录错误的 Lookout 登录界面屏幕截图](../media/mtp/lookout-mtp-consent-not-accepted-error.png)

若要解决此问题，全局管理员用户必须登录到 https://aad.lookout.com/les?action=consent，并接受启用设置的提示。 [为订阅设置 Lookout MTP](../deploy-use/set-up-your-subscription-with-lookout-mtp.md)主题中提供了更多详细信息

## <a name="troubleshoot-device-status-issues"></a>设备状态问题故障排除

### <a name="device-not-showing-up-in-the-lookout-mtp-console-device-list"></a>Lookout MTP 控制台设备列表中不显示设备

以下任一情况都可能导致此问题：
* 此设备的所有者不属于“Lookout MTP 控制台”中指定的“注册组”。  从“系统”模块转到“Intune 连接器”选项卡，查看“注册管理”设置。  应可看到配置待注册的一个或多个 Azure AD 组。  验证丢失设备的用户是否属于指定的 Azure AD 组。  将新用户添加到注册组后，至多需要在配置的轮训间隔后（默认为 5 分钟），设备才会显示在 Lookout MTP 控制台的“设备”中。

* 如果 Lookout MTP 不支持此设备。  不受支持的设备将显示在 Lookout MTP 控制台上连接器设置的“托管设备”部分。

### <a name="device-continues-to-be-reported-as-pending"></a>会继续将设备报告为“待定”

设备显示为“待定”表明最终用户未打开 Lookout for Work 应用并点击“激活”按钮。 有关 Lookout for Work 应用设备激活的详细信息，请参阅下列主题：

[系统提示在 Android 设备上安装 Lookout for Work](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

### <a name="in-the-lookout-mtp-console-a-device-is-showing-as-active-but-does-not-have-a-device-id"></a>在 Lookout MTP 控制台中，设备显示为活动但无设备 ID。  
这表明此设备的所有者不属于 Lookout MTP 控制台指定的注册组。   从注册组中删除设备所有者，或删除设备所有者所在注册组，则设备进入此状态。

从 Lookout MTP 控制台的“系统”模块转到“Intune 连接器”选项卡，查看“注册”设置。  应可看到配置待注册的一个或多个 Azure AD 组。  验证设备的所有者是否属于指定的 Azure AD 组。  

设备处于此状态时，Lookout 会继续通知用户检测到的威胁，但不会向 Intune 发送任何威胁信息。

### <a name="device-shows-disconnected-state"></a>设备显示断开连接状态

断开连接表明 Lookout MTP 在预配置的时间间隔内（默认为 30 天，最短为 7 天）未收到设备信息。 这表示设备上未安装或已卸载公司门户应用或 Lookout for Work 应用。 重新安装该应用可以解决此问题。 用户打开 Lookout for Work 并激活该应用时，设备将重新同步到 Lookout MTP 和 Intune。    

### <a name="forcing-a-resync-on-the-device"></a>在设备上强制重新同步
管理员从 Lookout MTP 控制台的“设备”模块选择和删除设备。   设备所有者再次打开 Lookout for Work 应用并点击“激活”时，设备状态将彻底重新同步。

### <a name="the-owner-of-the-device-is-no-longer-using-this-device"></a>设备所有者不再使用此设备
必须擦除设备并要求新用户注册。  从 [Intune 管理员控制台](https://manage.microsoft.com)选择设备，右键单击并选择“停用/擦除”，以删除对该设备的管理。 停用设备后可删除该设备。

![Intune 管理员控制台“设备”模块的屏幕截图，其中显示了“停用/擦除”选项](../media/mtp/mtp-retire-device-intune-console.png)

还可转到 Lookout MTP 控制台的“设备”模块，并选择“删除”。  

只要新用户属于 Lookout MTP 控制台中指定的注册组，Azure AD 将设备关联到该新用户后即显示该设备。

## <a name="compliance-remediation-workflows"></a>合规性修正工作流
[系统提示在 Android 设备上安装 Lookout for Work]( http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

[Lookout for Work 在 Android 设备上发现威胁，请解除该威胁](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)


### <a name="see-also"></a>另请参阅
[Set up you subscription with Lookout MTP](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-your-subscription-with-lookout-mtp)（为订阅设置 Lookout MTP）



<!--HONumber=Dec16_HO2-->


