---
title: Lookout 集成故障排除
description: 本主题介绍了 Lookout 集成中常见的故障排除问题
keywords: ''
author: NathBarn
ms.author: nathbarn
manager: dougeby
ms.date: 12/19/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bbe0b5f4-b8bc-49f3-85a9-51fb2f226fca
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6262fee0051827794c49ebe10361b1a3b280b140
ms.sourcegitcommit: f21287c66dd5559688f08bd98b6c976a0dea055d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/31/2018
ms.locfileid: "34470791"
---
# <a name="troubleshoot-lookout-integration-with-intune"></a>使用 Intune 对 Lookout 集成进行故障排除

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

本主题介绍设置 Lookout 移动威胁保护 (MTP) 时可能遇到的一些常见问题。

**登录错误**

## <a name="403-errors"></a>403 错误
登录 [Lookout MTP 控制台](https://aad.lookout.com)时可能出现 403 错误：**你无权访问此服务** 当指定用户名不属于配置以访问 Lookout MTP 的 Azure Active Directory (AD) 组时，可能出现此错误。

Lookout MTP 只允许已配置 Azure AD 组中的用户访问服务。 要确定配置了 Lookout MTP 访问权限的组，请联系 Lookout 支持：

* 电子邮件：enterprisesupport@lookout.com
* 登录到 [MTP 控制台](http://aad.lookout.com)，并导航到“支持”模块。
* 转到：<https://enterprise.support.lookout.com/hc/requests> 并提出支持请求。

## <a name="unable-to-sign-in"></a>无法登陆
Azure AD 全局管理员用户未接受初始 Lookout 设置时，会出现以下错误。

![Lookout 登录屏幕的屏幕截图显示登录出错](../media/mtp/lookout-mtp-consent-not-accepted-error.png)

若要解决此问题，全局管理员用户必须登录 https://aad.lookout.com/les?action=consent，然后接受初始设置提示。 有关更详细的信息，请参阅[使用 Lookout MTP 设置订阅](../deploy-use/setup-your-lookout-mtd-subscription.md)主题

**设备状态问题**

## <a name="device-missing-from-lookout-device-list"></a>Lookout 设备列表中缺少设备

在以下其中一个情况中可能出现此问题：
* 设备用户不属于“Lookout MTP 控制台”中指定的“注册组”。  在 [Lookout 控制台](http://aad.lookout.com)中，转到“系统” > “Intune 连接器” > “注册管理”。  查看为注册配置的 Azure AD 组，并验证设备用户是否属于 Azure AD 组。  将某用户添加到注册组后，最多需要在配置的轮训间隔后（默认为 5 分钟），设备才会显示在 Lookout MTP 控制台的“设备”模块中。
* 如果 Lookout MTP 不支持此设备。  不受支持的设备将显示在 Lookout MTP 控制台上连接器设置的“托管设备”部分。

### <a name="device-reported-as-pending"></a>报告为“挂起”的设备

如果最终用户未打开 Lookout for Work 应用并点击“激活”按钮，设备显示为“挂起”。 有关通过 Lookout for Work 应用激活设备的更多详细信息，请参阅[系统提示在 Android 设备上安装 Lookout for Work](http://docs.microsoft.com/intune-user-help/you-are-prompted-to-install-lookout-for-work-android) 或[系统提示在 iOS 设备上安装 Lookout for Work](https://docs.microsoft.com/intune-user-help/you-are-prompted-to-install-lookout-for-work-ios)

## <a name="device-whos-active-but-has-no-device-id"></a>设备处于活动状态，但没有设备 ID
在 Lookout MTP 控制台中，如果活动设备没有设备 ID，则该设备用户不属于注册组。 如果设备用户已从注册组删除，或其所在注册组已被删除，设备会处于此状态。

在 [Lookout 控制台](http://aad.lookout.com)中，转到“系统” > “Intune 连接器” > “注册”查看设置。  查看 Azure AD 组，并验证设备用户是否属于 Azure AD 组。

设备处于此状态时，Lookout 会继续通知用户检测到的威胁，但不会向 Intune 发送任何威胁信息。

## <a name="device-reported-as-disconnected"></a>报告为“已断开连接”的设备

“已断开连接”意味着该设备未在配置的时间间隔内（默认为 30 天，最少 7 天）与 Lookout MTP 同步。 设备缺少公司门户应用或 Lookout for Work 应用。 重新安装该应用应当能够解决此问题。 用户打开 Lookout for Work 并激活该应用时，设备将重新同步到 Lookout MTP 和 Intune。

### <a name="forcing-a-device-sync"></a>强制设备同步
管理员从 Lookout MTP 控制台的“设备”模块选择和删除设备。   设备所有者再次打开 Lookout for Work 应用并点击“激活”时，设备状态将彻底重新同步。

## <a name="device-has-a-new-user"></a>设备有新用户
应擦除设备并要求新用户注册。  从 [Intune 管理员控制台](https://manage.microsoft.com)选择设备，右键单击并选择“停用/擦除”，以删除对该设备的管理。 停用设备后可删除该设备。

![Intune 管理员控制台中“设备”模块的屏幕截图，其中显示了“停用/擦除”选项](../media/mtp/mtp-retire-device-intune-console.png)

还可转到 [Lookout 控制台](http://aad.lookout.com)的“设备”模块，选择“删除”。

如果新用户属于 Lookout MTP 注册组，Azure AD 将设备与该新用户关联后即显示该设备。

## <a name="compliance-remediation-workflows"></a>合规性修正工作流
- [系统提示在 Android 设备上安装 Lookout for Work](http://docs.microsoft.com/intune-user-help/you-are-prompted-to-install-lookout-for-work-android)
- [解除 Lookout for Work 在 Android 设备上发现的威胁](http://docs.microsoft.com/intune-user-help/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)
- [解除 Lookout for Work 在 iOS 设备上发现的威胁](https://docs.microsoft.com/intune-user-help/you-need-to-resolve-a-threat-found-by-lookout-for-work-ios)


### <a name="see-also"></a>另请参阅
[Set up you subscription with Lookout MTP](/intune-classic/deploy-use/set-up-your-subscription-with-lookout-mtp)（为订阅设置 Lookout MTP）
