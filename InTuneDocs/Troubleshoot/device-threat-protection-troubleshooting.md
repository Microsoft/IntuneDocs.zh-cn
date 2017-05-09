---
title: "Lookout 集成疑难解答 | Microsoft Docs"
description: "本主题介绍了如何排查执行 Lookout 集成时遇到的常见问题"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbe0b5f4-b8bc-49f3-85a9-51fb2f226fca
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: e10453155343bb7fd91a4fd3874d393ef78d0b1a
ms.openlocfilehash: 0b5586a06af7658c0c7a328ae1a824f88129039f
ms.contentlocale: zh-cn
ms.lasthandoff: 04/25/2017


---

# <a name="troubleshoot-lookout-integration-with-intune"></a>使用 Intune 对 Lookout 集成进行故障排除

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本主题介绍了设置 Lookout Mobile Threat Protection (MTP) 时可能遇到的一些常见问题。

**登录错误**

## <a name="403-errors"></a>403 错误
登录 [Lookout MTP 控制台](https://aad.lookout.com)时可能会看到 403 错误：**你无权访问此服务**。当指定的用户名不属于配置为访问 Lookout MTP 的 Azure Active Directory (AD) 组时，这时就会出现这种情况。

Lookout MTP 只允许属于已配置 Azure AD 组的用户访问服务。 若要确定哪个组已配置为访问 Lookout MTP，请联系 Lookout 支持人员：

* 电子邮件：enterprisesupport@lookout.com
* 登录 [MTP 控制台](http://aad.lookout.com)，导航到“支持”模块。
* 转到 https://enterprise.support.lookout.com/hc/requests，然后提出支持请求。

## <a name="unable-to-sign-in"></a>无法登录
如果 Azure AD 全局管理员用户尚未接受初始 Lookout 设置时，你就会看到以下错误。

![Lookout 登录屏幕的屏幕截图显示登录出错](../media/mtp/lookout-mtp-consent-not-accepted-error.png)

若要解决此问题，全局管理员用户必须登录 https://aad.lookout.com/les?action=consent，然后接受初始设置提示。 有关更详细的信息，请参阅[使用 Lookout MTP 设置订阅](../deploy-use/set-up-your-subscription-with-lookout-mtp.md)主题

**设备状态问题**

## <a name="device-missing-from-lookout-device-list"></a>Lookout 设备列表中缺少设备

在以下其中一个情况中可能出现此问题：
* 设备用户不属于“Lookout MTP 控制台”中指定的“注册组”。  在“Lookout 控制台”[](http://aad.lookout.com)中，依次转到“系统” > “Intune 连接器” > “注册管理”。  查看已配置的 Azure AD 注册组，并确认设备用户是否属于 Azure AD 组之一。  将用户添加到注册组后，最多需要等待所配置的轮询间隔（默认为 5 分钟），相应设备才会显示在 Lookout MTP 控制台的“设备”模块中。
* 如果设备不受 Lookout MTP 支持。  不受支持的设备将在 Lookout MTP 控制台连接器设置的“托管的设备”部分显示。

### <a name="device-reported-as-pending"></a>设备被报告为“挂起”

如果最终用户尚未打开 Lookout for Work 应用，也未点击“激活”按钮，那么设备显示为“挂起”。 若要详细了解如何使用 Lookout for Work 应用激活设备，请参阅[系统提示在 Android 设备上安装 Lookout for Work](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android) 或[系统提示在 iOS 设备上安装 Lookout for Work](https://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-ios)。

## <a name="device-whos-active-but-has-no-device-id"></a>设备已激活但无设备 ID
在 Lookout MTP 控制台中，如果已激活设备没有设备 ID，表明设备用户不属于注册组。 如果设备用户已从注册组中删除，或所在注册组已被删除，那么设备就会处于这种状态。

在“Lookout 控制台”[](http://aad.lookout.com)中，依次转到“系统” > “Intune 连接器” > “注册”，然后查看设置。  查看 Azure AD 组，并确认设备用户是否属于 Azure AD 组之一。

在设备处于此状态时，Lookout 将继续通知用户任何检测到的威胁，但不会向 Intune 发送任何威胁信息。

## <a name="device-reported-as-disconnected"></a>设备被报告为“已断开连接”

“已断开连接”表示设备未在配置的时间间隔（默认为 30 天，最少 7 天）内与 Lookout MTP 同步。 设备中缺少公司门户应用或 Lookout for Work 应用。 重新安装该应用应当能够解决此问题。 用户打开 Lookout for Work 并激活该应用时，设备便与 Lookout MTP 和 Intune 重新同步。

### <a name="forcing-a-device-sync"></a>强制执行设备同步
在 Lookout MTP 控制台的“设备”模块中，管理员可以选择该设备，然后选择将其删除。   设备所有者下一次打开 Lookout for Work 应用并点击“激活”时，设备状态将执行完整的重新同步。

## <a name="device-has-a-new-user"></a>设备有新用户
应擦除设备并要求新用户进行注册。  在“Intune 管理员控制台”[](https://manage.microsoft.com)中，选择设备，然后右键单击并选择“停用/擦除”，以撤消管理设备。 可删除已停用的设备。

![Intune 管理员控制台中“设备”模块的屏幕截图，其中显示了“停用/擦除”选项](../media/mtp/mtp-retire-device-intune-console.png)

也可以转到“Lookout 控制台”[](http://aad.lookout.com)的“设备”模块，然后选择“删除”。

如果新用户属于 Lookout MTP 注册组，那么设备便会在 Azure AD 将其与新用户关联后立即显示。

## <a name="compliance-remediation-workflows"></a>合规性修正工作流
- [系统提示在 Android 设备上安装 Lookout for Work]( http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)
- [需要解决 Lookout for Work 在 Android 设备上发现的威胁](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)
- [需要解决 Lookout for Work 在 iOS 设备上发现的威胁](https://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-ios)


### <a name="see-also"></a>另请参阅
[设置 Lookout MTP 订阅](https://docs.microsoft.com/intune/deploy-use/set-up-your-subscription-with-lookout-mtp)

