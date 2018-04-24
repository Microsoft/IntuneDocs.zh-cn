---
title: 使用 Microsoft Intune 保护设备
description: 了解有关 Intune 可帮助你保护你的设备免受未授权访问和其他威胁的一些方法。
keywords: ''
author: dougeby
ms.author: angrobe
manager: angrobe
ms.date: 02/21/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 71e0cbf3-2bfb-412e-8a12-8503df08b4cf
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ea1cc3bc2d662a0d74c87fb5616f3626d580a7e9
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="protect-devices-with-microsoft-intune"></a>使用 Microsoft Intune 保护设备

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune 提供一系列完整的功能，帮助保护你所管理的设备，以及存储在这些设备上的数据。 阅读本主题，了解这些功能的基础知识以及了解详细信息的方式。

## <a name="general-ways-to-protect-all-devices"></a>保护所有设备的常用方法

### <a name="device-configuration"></a>设备配置
Intune [配置策略](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)，通过控制大量设置和功能来帮助保护和配置设备。 例如：
- 可以限制照相机或蓝牙等设备上的硬件功能的使用。
- 可以配置合规和不合规应用。 如果安装了不合规应用，则会收到警报（一些平台实际上可以阻止该安装）。

### <a name="reset-passcodes-when-users-are-locked-out-of-their-devices"></a>在用户无法解锁其设备时重置密码
由于保护移动设备上公司数据的第一步是要求输入密码来使用该设备，所以有时必须通过删除密码或远程设置临时密码来[重置密码](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)或帮助员工重置密码。 如果设备丢失或被盗，还可以[远程锁定设备](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)。

### <a name="retire-devices-and-remove-data"></a>停用设备并删除数据
如果需要将某设备[从 Intune 管理删除](retire-devices-from-microsoft-intune-management.md)，（例如，用户离开，或设备丢失或被盗），你很可能想要从该设备删除数据。 Intune 提供了一系列方法，确保你的公司数据的安全性。

### <a name="require-devices-to-be-compliant"></a>要求设备合规
Intune 功能[设备合规策略](introduction-to-device-compliance-policies-in-microsoft-intune.md)能够让你评估（甚至在某些情况下修正）不符合指定规则的设备。 例如，可以报告越狱的 iOS 设备、设备是否已加密，或者 Windows 10 设备是否被运行状况证明服务报告为运行正常。

### <a name="protect-apps-and-the-data-they-use"></a>保护他们使用的应用和数据
Intune 为你提供了一系列功能，帮助保护应用及其数据。 例如，移动应用管理 (MAM) 策略可以阻止数据从受保护的应用进行备份、限制复制并向其他应用粘贴，以及在访问应用时要求提供 PIN 等。 有关保护应用的详细信息，请参阅[使用 Microsoft Intune 保护应用和数据](protect-apps-and-data-with-microsoft-intune.md)

### <a name="add-an-additional-layer-of-protection-to-devices"></a>向设备添加额外的保护层
[多重身份验证 (MFA)](multi-factor-authentication-azure-active-directory.md) 是验证网络中设备的用户身份的更安全方式。  使用 MFA 时，除用户名和密码外，用户还需要通过电话呼叫或短信确认其身份。

## <a name="further-capabilities-for-windows-devices"></a>适用于 Windows 设备的更多功能

### <a name="control-windows-hello-for-business-settings-on-windows-devices"></a>控制 Windows 设备上的 Windows Hello 企业版设置
Intune 允许集成 [Windows Hello 企业版](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md)（以前称为 Microsoft Passport），这是一种适用于 Windows 10 及更高版本的替代登录方法，它使用 Active Directory 或 Azure Active Directory 帐户来取代密码、智能卡或虚拟智能卡。

## <a name="further-capabilities-for-ios-devices"></a>适用于 iOS 设备的更多功能

### <a name="bypass-activation-lock-on-ios-devices"></a>在 iOS 设备上绕过激活锁定
激活锁定是一种帮助保护用户设备的功能，它要求任何人在擦除或重新激活设备前都要先输入其 Apple ID 和密码。 但是，如果用户离开了公司，但未删除该锁定，就可能会导致出现问题。 [绕过 iOS 激活锁定](help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune.md)通过从监管的 iOS 设备删除锁定并允许你重新分配或将其擦除可提供帮助。



## <a name="protect-windows-pcs-managed-with-the-intune-client"></a>保护通过 Intune 客户端管理的 Windows 电脑
Intune 继续支持适用于未注册但通过 Intune 计算机客户端软件管理的 Windows 电脑的安全性策略。 若要了解这些策略如何帮助你保护 Windows 电脑，请参阅[使用策略来帮助保护运行 Intune 客户端软件的 Windows 电脑](policies-to-protect-windows-pcs-in-microsoft-intune.md)。
