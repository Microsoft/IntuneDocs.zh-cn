---
title: Microsoft Intune 中的设备操作疑难解答 - Azure | Microsoft Docs
description: 获取设备操作问题的故障排除帮助。
keywords: ''
author: erikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ROBOTS: ''
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7d4517d89e3b7365834e904c815b30a362540906
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755589"
---
# <a name="troubleshoot-device-actions-in-intune"></a>在 Intune 中排除设备操作故障问题

Microsoft Intune 提供了许多可帮助管理设备的操作。 本文提供了一些常见问题的答案，可帮助你排除设备操作故障问题。

## <a name="disable-activation-lock-action"></a>禁用激活锁操作

### <a name="i-clicked-the-disable-activation-lock-action-in-the-portal-but-nothing-happened-on-the-device"></a>我单击了门户中的“禁用激活锁”操作，但设备上没有任何反应。
这是正常情况。 开始禁用激活锁操作后，Intune 将从 Apple 请求更新的代码。 设备显示“激活锁”屏幕后，你需要在“密码”字段中手动输入该代码。 此代码仅在 15 天内有效，因此在你发出“擦除”之前，请确保单击此操作并复制代码。

### <a name="why-dont-i-see-the-disable-activation-lock-code-in-the-hardware-overview-blade-of-my-ios-device"></a>为什么我在 iOS 设备的“硬件概述”边栏选项卡中看不到“禁用激活锁”代码？
最可能的原因包括：
- 代码已过期，并已从服务中清除。
- 设备未受到设备限制策略的监管，无法允许激活锁。

可以通过以下查询在图形资源管理器中检查代码：

```GET - https://graph.microsoft.com/beta/deviceManagement/manageddevices('deviceId')?$select=activationLockBypassCode.```

### <a name="why-is-the-disable-activation-lock-action-greyed-out-for-my-ios-device"></a>为什么“禁用激活锁”操作在我的 iOS 设备上灰显？
最可能的原因包括： 
- 代码已过期，并已从服务中清除。
- 设备未受到设备限制策略的监管，无法允许激活锁。

### <a name="is-the-disable-activation-lock-code-case-sensitive"></a>“禁用激活锁”代码是否区分大小写？
不能。 并且无需输入短划线。

## <a name="remove-devices-action"></a>删除设备操作

### <a name="how-do-i-tell-who-started-a-retirewipe"></a>我如何知道谁开始了停用/擦除？
在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)，转到“租户管理” > “审核日志”> 检查“启动者”列    。
如果你看不到某个条目，则最有可能发起该操作的人是此设备的用户。 他们可能使用了“公司门户”应用或 portal.manage.microsoft.com。

### <a name="why-wasnt-my-application-uninstalled-after-using-retire"></a>为什么停用我的应用程序后未将其卸载？
因为它未被视为托管应用程序。 在此上下文中，托管应用程序是指使用 Intune 服务安装的应用程序。 这包括：
- 应用已按要求部署
- 应用已部署为“可用”，然后由最终用户在“公司门户”应用内进行安装。

### <a name="why-is-wipe-grayed-out-for-android-enterprise-work-profile-devices"></a>为什么“擦除”对于 Android 企业版工作配置文件设备灰显？
这是预期行为。 Google 不允许从 MDM 提供程序将工作配置文件设备恢复出厂设置。

### <a name="why-can-i-sign-back-into-my-office-apps-after-my-device-was-retired"></a>为什么在我的设备停用后，我仍可以重新登录到 Office 应用？
因为停用设备不会撤销访问令牌。 可以使用条件访问策略来缓解这种情况。

### <a name="how-can-i-monitor-a-retirewipe-action-after-it-was-issued"></a>发出停用/擦除操作后，我如何对其进行监视？
在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)，转到“租户管理” > “审核日志”   。

### <a name="why-do-wipes-sometimes-show-as-pending-indefinitely"></a>为什么擦除有时会无限期地显示为挂起？
在重置开始之前，设备不会始终将其状态报告回 Intune 服务。 因此，操作显示为挂起。 如果已确认操作成功，请从服务中删除该设备。

### <a name="what-happens-if-i-start-a-retirewipe-on-an-offline-device-or-a-device-that-hasnt-communicated-with-the-service-in-a-while"></a>如果我在离线设备上或在一段时间内未与此服务通信的设备上开始停用/擦除，会发生什么情况？
在 MDM 证书过期之前，设备将保持“停用/擦除挂起”状态  。 MDM 证书自注册起有效期为一年，并每年自动续订一次。 如果设备在 MDM 证书过期之前签入，则该设备将被停用/擦除。 如果设备在 MDM 证书过期之前未签入，它将无法签入到服务。 MDM 证书过期 180 天后，设备将自动从 Azure 门户中删除。


## <a name="reset-passcode-action"></a>重置密码操作

### <a name="why-is-the-reset-passcode-action-greyed-out-on-my-android-device-admin-enrolled-device"></a>为什么我 Android 设备管理员注册设备上的“重置密码”操作灰显？
为了对付勒索软件，Google 删除了设备管理员 API（适用于 Android 版本 7.0 或更高版本的设备）上的密码重置功能。

### <a name="why-do-i-get-a-not-supported-message-when-i-issue-a-passcode-reset-to-my-android-80-or-later-work-profile-enrolled-device"></a>为什么我向 Android 8.0 或更高版本的工作配置文件注册设备发出密码重置时，会收到“不受支持”消息？
因为未在设备上激活重置令牌。 若要激活重置令牌：
1. 你必须在配置策略中要求使用工作配置文件密码。
2. 最终用户必须设置合适的工作配置文件密码。
3. 最终用户必须接受第二次提示以允许密码重置。
完成这些步骤后，你应不会再收到此响应。

### <a name="why-am-i-prompted-to-set-a-new-passcode-on-my-ios-device-when-i-issue-the-remove-passcode-action"></a>发出“删除密码”操作时，为什么会提示我在 iOS 设备上设置新密码？
因为你的符合性策略之一需要密码。

## <a name="next-steps"></a>后续步骤

[从 Microsoft 获取支持帮助](../fundamentals/get-support.md)，或使用[社区论坛](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune)。
