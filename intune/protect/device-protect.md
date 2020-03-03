---
title: 使用 Microsoft Intune 保护设备
titleSuffix: Microsoft Intune
description: 了解有关 Intune 可帮助你保护你的设备免受未授权访问和其他威胁的一些方法。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/19/2018
ms.topic: conceptual
ms.subservice: protect
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 49c629039c08c892c7d6b19422d79c9eb1a8d760
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2020
ms.locfileid: "77510463"
---
# <a name="protect-devices-with-microsoft-intune"></a>使用 Microsoft Intune 保护设备

Microsoft Intune 有助于保护你所管理的设备，以及存储在这些设备上的数据。

## <a name="device-configuration"></a>设备配置
Intune [配置策略](../configuration/device-profiles.md)，通过控制大量设置和功能来帮助保护和配置设备。 例如：

- 可以限制照相机或蓝牙等设备上的硬件功能的使用。
- 可以配置合规和不合规应用。 如果安装了不合规应用，则会收到警报（一些平台实际上可以阻止该安装）。

## <a name="reset-passcodes-when-users-are-locked-out-of-their-devices"></a>在用户无法解锁其设备时重置密码
由于保护移动设备上公司数据的第一步是要求输入密码来使用该设备，所以有时必须通过删除密码或远程设置临时密码来[重置密码](../remote-actions/device-passcode-reset.md)或帮助员工重置密码。 如果设备丢失或被盗，还可以[远程锁定设备](../remote-actions/device-remote-lock.md)。

## <a name="retire-devices-and-remove-data"></a>停用设备并删除数据
如果需要将某设备[从 Intune 管理删除](../remote-actions/devices-wipe.md)，（例如，用户离开，或设备丢失或被盗），你很可能想要从该设备删除数据。 Intune 提供了一系列方法，确保你的公司数据的安全性。

## <a name="require-devices-to-be-compliant"></a>要求设备合规
Intune 功能[设备符合性策略](device-compliance-get-started.md)能够让你评估（甚至在某些情况下修正）不符合指定规则的设备。 例如，可获取关于以下内容的报表：
- 已越狱的 iOS/iPadOS 设备
- 加密或未加密设备
- Windows 10 设备的运行状况（由运行状况证明服务确定）。

## <a name="protect-apps-and-the-data-they-use"></a>保护他们使用的应用和数据
Intune 为你提供了一系列功能，帮助保护应用及其数据。 例如，移动应用管理 (MAM) 策略可以：
- 防止数据从受保护的应用备份
- 限制复制和粘贴到其他应用中
- 要求提供 PIN 才能访问应用 有关详细信息，请参阅[使用 Microsoft Intune 保护应用和数据](../apps/app-protection-policy.md)

## <a name="add-an-additional-layer-of-protection-to-devices"></a>向设备添加额外的保护层
[多重身份验证 (MFA)](../enrollment/multi-factor-authentication.md) 是验证网络中设备的用户身份的更安全方式。  使用 MFA 时，除用户名和密码外，用户还需要通过电话呼叫或短信确认其身份。

## <a name="control-windows-hello-for-business-settings-on-windows-devices"></a>控制 Windows 设备上的 Windows Hello 企业版设置
Intune 允许集成 [Windows Hello 企业版](windows-hello.md)，这是一种适用于 Windows 10 及更高版本的替代登录方法，它使用 Active Directory 或 Azure Active Directory 帐户来取代密码、智能卡或虚拟智能卡。

## <a name="disable-activation-lock-on-ios-devices"></a>在 iOS 设备上禁用激活锁定
激活锁是一种帮助保护用户设备的功能。 此功能要求用户输入其 Apple ID 和密码，才能擦除或重新激活该设备。 但是，如果用户离开了公司，但未删除该锁定，此功能可能会导致出现问题。 [禁用 iOS/iPadOS 激活锁](../remote-actions/device-activation-lock-disable.md)可通过从监管的 iOS/iPadOS 设备删除锁定并允许你重新分配或擦除锁定来提供帮助。

## <a name="next-steps"></a>后续步骤

了解 [Mobile Threat Defense](mobile-threat-defense.md)
