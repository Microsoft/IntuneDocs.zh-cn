---
title: "保护设备 | Microsoft Intune"
description: "了解有关 Intune 可帮助你保护你的设备免受未授权访问和其他威胁的一些方法。"
keywords: 
author: Robstackmsft
manager: arob98
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71e0cbf3-2bfb-412e-8a12-8503df08b4cf
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a409d36c1c5fcfd3d81ce0cbdf1f69af4747157a
ms.openlocfilehash: 53201c36e7a210c1c62d3ed3183093ed8e63dc53


---

# 使用 Microsoft Intune 保护设备
一旦通过 Intune 管理设备，需要确保设备得到保护，以阻止未授权访问和其他威胁。 以下 Intune 功能有助于实现这些目标。

> [!TIP]
> 本主题不包含 Intune 可帮助你保护设备的所有方式。 例如，可以使用 Intune 策略为设备配置多个安全性设置，例如配置密码、加密设置和硬件功能（例如蓝牙和设备照相机）。 请参阅[使用 Microsoft Intune 管理设备上的设置和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)，了解这些设置的详细信息。

## 在用户无法解锁其设备时重置密码
由于保护移动设备上公司数据的第一步是要求输入密码来使用该设备，所以有时必须通过删除密码或远程设置临时密码来[重置密码](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)或帮助员工重置密码。 如果设备丢失或被盗，还可以[远程锁定设备](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)。

## 向 Windows 设备添加额外的保护层
[多重身份验证 (MFA)](protect-windows-devices-with-multi-factor-authentication.md) 是验证网络中 Windows 和 Windows Phone 设备用户身份更安全的方式。  使用 MFA 时，除用户名和密码外，用户还需要通过电话呼叫或短信确认其身份。

## 控制 Windows 设备上的 Microsoft Passport 设置
Intune 允许集成 [Microsoft Passport for Work](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md)，这是一种适用于 Windows 10 及更高版本的替代登录方法，它使用 Active Directory 或 Azure Active Directory 帐户来取代密码、智能卡或虚拟智能卡。

## 在 iOS 设备上绕过激活锁定
激活锁定是一种功能，通过在任何人都可以擦除或激活该设备前要求输入其 Apple ID 和密码来帮助保护用户设备。 但是，如果用户离开了公司，但未删除该锁定，就可能会导致出现问题。 [绕过 iOS 激活锁定](help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune.md)通过从监管的 iOS 设备删除锁定并允许你重新分配或将其擦除可提供帮助。

## 保护通过 Intune 客户端管理的 Windows 电脑
Intune 继续支持适用于未注册但通过 Intune 计算机客户端软件管理的 Windows 电脑的安全性策略。 若要了解这些策略如何帮助你保护 Windows 电脑，请参阅[使用策略来帮助保护运行 Intune 客户端软件的 Windows 电脑](policies-to-protect-windows-pcs-in-microsoft-intune.md)。



<!--HONumber=Jul16_HO3-->


