---
title: Microsoft Intune 中的设备操作疑难解答 - Azure | Microsoft Docs
description: 获取设备操作问题的疑难解答帮助。
keywords: ''
author: erikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ROBOTS: ''
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: e1b3139db8b217dceb495f67e809eae8319eae0c
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71735696"
---
# <a name="troubleshoot-device-actions-in-intune"></a>Intune 中的设备操作故障排除

Microsoft Intune 提供了许多可帮助管理设备的操作。 本文提供了一些常见问题的答案，这些问题可帮助你排除设备操作问题。

## <a name="bypass-activation-lock-action"></a>绕过激活锁定操作

### <a name="i-clicked-the-bypass-activation-lock-action-in-the-portal-but-nothing-happened-on-the-device"></a>我单击了门户中的 "跳过激活锁" 操作，但设备上没有任何内容。
这是正常情况。 开始绕过激活锁操作之后，Intune 会从 Apple 请求更新的代码。 你将在设备位于激活锁屏幕后，手动在 "密码" 字段中输入代码。 此代码仅适用于15天，因此请确保单击该操作并在发出擦除之前复制代码。

### <a name="why-dont-i-see-the-bypass-activation-lock-code-in-the-hardware-overview-blade-of-my-ios-device"></a>为什么我在 iOS 设备的 "硬件概述" 边栏选项卡中看不到跳过的激活锁代码？
最可能的原因包括：
- 代码已过期，已从服务中清除。
- 设备未受到设备限制策略的监督，无法允许激活锁。

可以通过以下查询在图形资源管理器中检查代码：

```GET - https://graph.microsoft.com/beta/deviceManagement/manageddevices('deviceId')?$select=activationLockBypassCode.```

### <a name="why-is-the-bypass-activation-lock-action-greyed-out-for-my-ios-device"></a>为什么 "绕过激活锁" 操作在我的 iOS 设备上灰显？
最可能的原因包括： 
- 代码已过期，已从服务中清除。
- 设备未受到设备限制策略的监督，无法允许激活锁。

### <a name="is-the-bypass-activation-lock-code-case-sensitive"></a>旁路激活锁代码是否区分大小写？
不能。 不需要输入短划线。

## <a name="remove-devices-action"></a>删除设备操作

### <a name="how-do-i-tell-who-started-a-retirewipe"></a>如何实现告诉谁开始停用/擦除？
中转到**Intune** > **台设备** > **设备操作**> 检查 "**启动者**" 列。
如果看不到某个条目，则很可能是该设备的用户启动了该操作。 它们可能使用公司门户应用程序或 portal.manage.microsoft.com。

### <a name="why-wasnt-my-application-uninstalled-after-using-retire"></a>为什么应用程序在停用后无法卸载？
因为它不被视为托管应用程序。 在此上下文中，托管应用程序是使用 Intune 服务安装的应用程序。 这包括：
- 应用已根据需要部署
- 应用部署为 "可用"，然后由最终用户在公司门户应用内安装。

### <a name="why-is-wipe-grayed-out-for-android-enterprise-work-profile-devices"></a>为什么对于 Android 企业工作配置文件设备，擦除会灰显？
这是预期行为。 Google 不允许从 MDM 提供程序恢复工作配置文件设备的出厂设置。

### <a name="why-can-i-sign-back-into-my-office-apps-after-my-device-was-retired"></a>为何我的设备停用后，我可以登录到 Office 应用？
由于停用设备不会吊销访问令牌。 可以使用条件性访问策略来缓解这种情况。

### <a name="how-can-i-monitor-a-retirewipe-action-after-it-was-issued"></a>如何在颁发后监视停用/擦除操作？
中转到**Intune** >  个**设备**， >  个**设备操作**。

### <a name="why-do-wipes-sometimes-show-as-pending-indefinitely"></a>为什么擦除有时会无限期地显示为挂起？
在重置开始之前，设备不会始终将其状态报告回 Intune 服务。 因此，操作显示为 "挂起"。 如果已确认操作成功，请从服务中删除该设备。

### <a name="what-happens-if-i-start-a-retirewipe-on-an-offline-device-or-a-device-that-hasnt-communicated-with-the-service-in-a-while"></a>如果在脱机设备上或在一段时间内未与此服务通信的设备上开始停用/擦除，会发生什么情况？
在 MDM 证书过期之前，设备将保持**停用/擦除挂起**状态。 MDM 证书的注册期限为一年，并每年自动续订一次。 如果设备在 MDM 证书过期之前签入，则该设备将被停用/擦除。 如果设备在 MDM 证书过期之前未签入，它将无法签入到服务。 MDM 证书过期后180天后，将从 Azure 门户中自动删除该设备。


## <a name="reset-passcode-action"></a>重置密码操作

### <a name="why-is-the-reset-passcode-action-greyed-out-on-my-android-device-admin-enrolled-device"></a>为什么我的 Android 设备管理员注册设备上的 "重置密码" 操作灰显？
为了对付 Ransom 的软件，Google 在设备管理员 API （适用于 Android 版本7.0 或更高版本的设备）上删除了密码重置功能。

### <a name="why-do-i-get-a-not-supported-message-when-i-issue-a-passcode-reset-to-my-android-80-or-later-work-profile-enrolled-device"></a>为什么向 Android 8.0 或更高版本的工作配置文件注册设备发出密码重置时，会收到 "不受支持" 消息？
因为未在设备上激活重置令牌。 若要激活重置令牌：
1. 你必须在配置策略中要求使用工作配置文件密码。
2. 最终用户必须设置合适的工作配置文件密码。
3. 最终用户必须接受辅助提示符才能允许重置密码。
完成这些步骤后，你将不会再收到此响应。

### <a name="why-am-i-prompted-to-set-a-new-passcode-on-my-ios-device-when-i-issue-the-remove-passcode-action"></a>我发出 "删除密码" 操作时，为什么会提示在 iOS 设备上设置新的密码？
因为你的符合性策略之一需要密码。

## <a name="next-steps"></a>后续步骤

[从 Microsoft 获取支持帮助](../fundamentals/get-support.md)，或使用[社区论坛](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune)。
