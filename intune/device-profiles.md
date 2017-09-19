---
title: "什么是 Microsoft Intune 中的设备配置文件？"
titlesuffix: Azure portal
description: "了解 Intune 设备配置文件，以及它们如何帮助管理和保护公司的设备。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 101e19a9de67a3a47f488988957bc1e7ef7626a3
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2017
---
# <a name="what-are-microsoft-intune-device-profiles"></a>什么是 Microsoft Intune 设备配置文件？

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用 Microsoft Intune“设备配置”工作负荷来管理你管理的所有设备上的设置和功能。 主要使用此工作负荷创建设备配置文件，从而管理并控制设备上各种不同功能。

打开此工作负荷时，将看到以下选项：

- **概述** - 此页提供状态和报告，可帮助监视为用户和设备分配的设备配置。
- **管理配置文件** - 此处是你创建设备配置描述文件的位置。 可在本主题后面部分中找到可创建的所有配置文件类型的列表。
- **安装证书颁发机构** - 此工作流介绍配置 Intune 证书配置文件所需的各个步骤。

## <a name="getting-started"></a>开始使用

创建设备配置文件的工作流对于所有配置文件来说是类似的。 请参阅[如何创建 Microsoft Intune 设备配置描述文件](device-profile-create.md)，获取有关信息。 然后继续阅读有关为每种配置文件类型创建设置的具体信息。

可在设备上管理以下功能：

## <a name="device-features"></a>设备功能

借助设备功能，你能够在 iOS 和 macOS 设备上控制 AirPrint、通知，和共享设备配置等功能。
有关详细信息，请参阅[如何配置设备功能设置](device-features-configure.md)支持：iOS 和 macOS。

## <a name="device-restrictions"></a>设备限制
借助设备限制，可控制所管理设备上的众多类别的设置，包括安全性、硬件和数据共享设置。 例如，可以创建一个设备限制配置文件，用于阻止 iOS 设备用户访问设备相机。
有关详细信息，请参阅[如何配置设备限制设置](device-restrictions-configure.md) 支持：Android、iOS、macOS、Windows 10 和 Windows 10 Team。

## <a name="email"></a>Email
电子邮件配置文件让你可在管理的设备上创建、分配和监视 Exchange ActiveSync 电子邮件设置。 邮件配置文件可以帮助确保一致性，减少支持呼叫，并让最终用户能够在不进行任何所需设置的情况下在其个人设备上访问公司电子邮件。
有关详细信息，请参阅[如何配置电子邮件设置](email-settings-configure.md) 支持：Android、iOS、Windows Phone 8.1 和 Windows 10。

## <a name="wi-fi"></a>Wi-Fi
使用 Wi-Fi 配置文件将无线网络设置分配到组织中的用户和设备。 分配 Wi-Fi 配置文件时，你的用户将有权访问你公司的 Wi-Fi，而无需自行配置。
有关详细信息，请参阅[如何配置 Wi-Fi 设置](wi-fi-settings-configure.md) 支持：Android、iOS、macOS 和 Windows 8.1（仅可导入）。

## <a name="vpn"></a>VPN
虚拟专用网络 (VPN) 可让你的用户安全远程访问你的公司网络。 设备使用 VPN 连接配置文件来初始化与 VPN 服务器的连接。 将 VPN 配置文件分配到组织中的用户和设备，从而可以方便且安全地连接到网络。
有关详细信息，请参阅[如何配置 VPN 设置](vpn-settings-configure.md)。
支持：Android、iOS、macOS、Windows Phone 8.1、Windows 8.1 和 Windows 10。

## <a name="education"></a>教育
你可以配置 Windows Take a Test 应用的选项。 在配置这些选项时，直到测试完成才可以在设备上运行其他应用。
有关详细信息，请参阅[如何配置教育设置](education-settings-configure.md)

## <a name="certificates"></a>证书
此配置文件类型让你可以配置受信任证书、SCEP 证书和 PKCS 证书，这些证书可以分配到设备，并用于对 Wi-Fi、VPN 和电子邮件配置文件进行身份验证。
有关详细信息，请参阅[如何配置证书](certificates-configure.md) 支持：Android、iOS、Windows Phone 8.1、Windows 8.1 和 Windows 10。

## <a name="edition-upgrade"></a>版本升级
此配置文件类型可以将运行某些 Windows 10 版本的设备自动升级至较新的版本。
有关详细信息，请参阅[如何配置 Windows 10 版本升级](edition-upgrade-configure-windows-10.md) 支持：仅限 Windows 10。

## <a name="endpoint-protection"></a>Endpoint Protection
此配置文件类型允许配置适用于 Windows 10 设备的 BitLocker 设置和 Windows Defender 设置。
有关详细信息，请参阅[适用于 Windows 10 的 Endpoint Protection 设置](endpoint-protection-windows-10.md)支持：仅限 Windows 10。

## <a name="windows-information-protection"></a>Windows 信息保护
Windows 信息保护有助于防范数据泄露，而不会干扰员工体验。 它还有助于防范企业应用和数据在企业自有设备和员工带到工作中的个人设备上的意外数据泄露，而无需对你的环境或其他应用进行更改。
有关详细信息，请参阅[如何配置 Windows 信息保护](windows-information-protection-configure.md) 支持：仅限 Windows 10。

## <a name="custom"></a>自定义
自定义设置可让你分配未在 Intune 中内置的设备设置。 例如，在 Android 设备上，可以指定配置设备的 OMA-URI 值。 对于 iOS 设备，则可以导入在 Apple Configurator 中创建的配置文件。
有关详细信息，请参阅[如何配置自定义设置](custom-settings-configure.md) 支持：Android、iOS、macOS 和 Windows Phone 8.1。

## <a name="next-steps"></a>后续步骤
从列表中选择一种配置文件类型开始配置设备。
