---
title: Microsoft Intune 中的疑难解答策略 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中使用策略时的常见问题及解决方案
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: bb55ddc283ce4633b5057d5b96ae2ed6973dcf8a
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52181762"
---
# <a name="troubleshoot-policies-in-intune"></a>Intune 中的疑难解答策略

如果你在部署和管理 Intune 策略时出现问题，请从这里开始。 本主题介绍可能会遇到的一些常见问题和可能的解决方案。

## <a name="general-issues"></a>一般问题

### <a name="was-a-deployed-policy-applied-to-the-device"></a>部署的策略是否已应用于该设备？
问题：不确定策略是否已得到正确应用。

在 Intune 中，单击“设备” > “所有设备”，选择设备，然后单击“设备配置”，每台设备将列出其策略。 每个策略都具有状态。 状态是指综合考虑应用于设备的所有策略（包括硬件和操作系统的限制及要求）时应用的内容。 可能的状态为：

- 符合：设备已收到策略，并向服务报告该策略符合设置。

- 不适用：策略设置不适用。 例如，iOS 设备的电子邮件设置不适用于 Android 设备。

- 挂起：策略已发送到设备，但尚未将状态报告给服务。 例如，Android 上的加密需要用户启用加密，可能显示为挂起状态。

> [!NOTE]
> 当具有不同限制级别的两个策略应用于同一个设备或用户时，会使用限制更严格的策略。

## <a name="issues-with-enrolled-devices"></a>已注册设备的问题

### <a name="alert-saving-of-access-rules-to-exchange-has-failed"></a>警报：将访问规则保存到 Exchange 中的操作失败
**问题**：你在管理控制台中收到警报“将访问规则保存到 Exchange 中的操作失败”   。

如果在管理控制台下的 Exchange 本地策略工作区中创建了策略，但使用的是 O365，则 Intune 不会强制执行所配置的策略设置。 记下警报中的策略源。  在 Exchange 本地策略工作区下删除旧规则。 旧规则是 Intune 内本地 Exchange 的全局 Exchange 规则，与 O365 无关。 然后，为 O365 创建新策略。

### <a name="cannot-change-security-policy-for-various-enrolled-devices"></a>无法更改各种已注册设备的安全策略
Windows Phone 设备不允许通过 MDM 或 EAS 设置安全策略后降低其安全性。 例如，将“最小字符密码数”设置为 8，然后尝试将其减少到 4。 已向设备应用更严格的策略。

如果要将策略更改为安全级别较低的值，可能需要重置安全策略，具体视设备平台而定。

例如，在 Windows 中，在桌面上从右轻扫打开“超级按钮”栏。 选择“设置” > “控制面板”，然后选择“用户帐户”。 在左侧，选择“重置安全策略”链接，然后选择“重置策略”。

对于其他 MDM 设备（例如 Android、Windows Phone 8.1 及更高版本以及 iOS），可能需要将其停用并重新注册到服务，这样才能应用限制较少的策略。

## <a name="issues-with-pcs-that-run-the-intune-software-client"></a>运行 Intune 软件客户端的电脑的问题

适用于经典门户。

### <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>policyplatform.log 中与 Microsoft Intune 策略相关的错误
对于使用 Intune 软件客户端进行管理的 Windows 电脑，policyplatform.log 文件中的策略错误可能是因设备上 Windows 用户帐户控制 (UAC) 中的非默认设置导致的。 某些非默认 UAC 设置会影响 Microsoft Intune 客户端安装和策略执行。

#### <a name="resolve-uac-issues"></a>解决 UAC 问题

1. 停用计算机。 请参阅[删除设备](devices-wipe.md)。

2. 等待 20 分钟，以便删除客户端软件。

    > [!NOTE]
    > 请勿尝试从“程序和功能”中删除客户端。

3. 在开始菜单上，键入 **UAC** 以打开用户帐户控制设置。

4. 将通知滑块移动到默认设置。

### <a name="error-cannot-obtain-the-value-from-the-computer-0x80041013"></a>错误：无法从计算机中获取值，0x80041013
如果本地系统上的时间不同步达到或超过五分钟或更长时间，则会出现此问题。 如果本地计算机上的时间不同步，安全事务将因时间戳无效而失败。

若要解决此问题，请使设置的本地系统时间尽可能地接近 Internet 时间，或接近网络中域控制器上设置的时间。

### <a name="next-steps"></a>后续步骤
如果此疑难解答信息没有帮助到你，请联系 Microsoft 支持部门，如[获取对 Microsoft Intune 的支持](get-support.md)中所述。
