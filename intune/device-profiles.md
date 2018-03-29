---
title: Microsoft Intune 中的设备配置文件 - Azure | Microsoft Docs
description: Azure 门户中的不同 Microsoft Intune 设备配置文件概述，包括功能、限制、电子邮件、WiFi、VPN、教育、证书、升级 Windows 10、BitLocker 和 Windows Defender、Windows 信息保护，以及自定义设备配置设置。 使用这些配置文件管理和保护公司内的数据和设备。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/22/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e92a10f51fb403c802c1c6d3ea79ccf49a1e93fb
ms.sourcegitcommit: a22309174e617e59ab0cdd0a55abde38711a5f35
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/23/2018
---
# <a name="what-are-microsoft-intune-device-profiles"></a>什么是 Microsoft Intune 设备配置文件？

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Intune 提供可在组织内的不同设备上启用或禁用的设置和功能。 这些设置和功能通过配置文件进行管理。 一些配置文件示例如下： 

- WiFi 配置文件可让不同设备访问公司 WiFi
- VPN 配置文件可让不同设备访问公司网络中的 VPN 服务器

本主题提供可为设备创建的不同配置文件的概述。 使用这些配置文件来允许和/或阻止设备上的某些功能。

## <a name="before-you-begin"></a>在开始之前
若要查看可用功能，请打开 [Azure 门户](https://portal.azure.com)，然后打开 Intune 资源。 

设备配置包括以下选项：

- **概述**：列出配置文件的状态，并提供有关分配给用户和设备的配置文件的其他详细信息
- **管理**：创建设备配置文件，并上传自定义 [PowerShell 脚本](intune-management-extension.md)以在配置文件中运行
- **监视**：检查配置文件的状态（成功或失败），并查看配置文件中的日志
- **设置**：为配置文件添加证书颁发机构（SCEP 或 PFX），或启用电信费用管理

## <a name="create-the-profile"></a>创建配置文件

[创建设备配置文件](device-profile-create.md)提供创建配置文件的分步指导。 

## <a name="device-features-profile"></a>设备功能配置文件

[设备功能](device-features-configure.md)控制 iOS 和 macOS 设备上的功能，例如 AirPrint、通知和共享设备配置。

此功能支持：  
- iOS 
- macOS

## <a name="device-restrictions-profile"></a>设备限制配置文件
[设备限制](device-restrictions-configure.md)控制设备上的安全性、硬件、数据共享，以及更多设置。 例如，创建一个可阻止 iOS 设备用户使用设备相机的设备限制配置文件。 

此功能支持： 

- Android
- iOS
- macOS
- Windows 10
- Windows 10 协同版

## <a name="email-profile"></a>电子邮件配置文件
[电子邮件设置](email-settings-configure.md)配置文件创建、分配和监视设备上的 Exchange ActiveSync 电子邮件设置。 邮件配置文件可帮助确保一致性、减少支持呼叫，并让最终用户能够在不进行任何所需设置的情况下在其个人设备上访问公司电子邮件。 

此功能支持： 

- Android
- iOS
- Windows Phone 8.1
- Windows 10

## <a name="wi-fi-profile"></a>Wi-Fi 配置文件
[Wi-Fi 设置](wi-fi-settings-configure.md)将无线网络设置分配给用户和设备。 分配 WiFi 配置文件后，用户无需自行配置即可访问公司 Wi-Fi。 

此功能支持： 

- Android
- iOS
- macOS
- Windows 8.1 （仅限导入）

## <a name="vpn-profile"></a>VPN 配置文件
[VPN 设置](vpn-settings-configure.md)将配置文件分配到组织中的用户和设备，从而使其方便安全地连接到网络。 

虚拟专用网络 (VPN) 可让用户安全地远程访问公司网络。 设备使用 VPN 连接配置文件来初始化与 VPN 服务器的连接。 

此功能支持： 

- Android
- iOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10

## <a name="education-profile"></a>教育配置文件
[教育设置](education-settings-configure.md)配置针对 [Windows 参加测验应用](https://education.microsoft.com/gettrained/win10takeatest)的选项。 在配置这些选项时，直到测试完成才可以在设备上运行其他应用。

## <a name="certificates-profile"></a>证书配置文件
[证书](certificates-configure.md)配置可分配到设备的受信任证书、SCEP 证书和 PKCS 证书，用于对 Wi-Fi、VPN 和电子邮件配置文件进行身份验证。

此功能支持： 

- Android
- iOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10

## <a name="edition-upgrade-profile"></a>版本升级配置文件
[Windows 10 版本升级](edition-upgrade-configure-windows-10.md)将运行某些 Windows 10 版本的设备自动升级到较新的版本。

此功能支持：仅限 Windows 10

## <a name="endpoint-protection-profile"></a>Endpoint Protection 配置文件
[适用于 Windows 10 的 Endpoint Protection 设置](endpoint-protection-windows-10.md)配置适用于 Windows 10 设备的 BitLocker 和 Windows Defender 设置。

若要使用 Microsoft Intune 载入 Windows Defender 高级威胁防护 (WDATP)，请参阅 [Configure endpoints using Mobile Device Management (MDM) tools](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-mdm-windows-defender-advanced-threat-protection)（使用移动设备管理 (MDM) 工具配置终结点）。

此功能支持：仅限 Windows 10

## <a name="windows-information-protection-profile"></a>Windows 信息保护配置文件
[Windows 信息保护](windows-information-protection-configure.md)有助于防范数据泄露，而不会干扰员工体验。 它还有助于防范企业应用和数据在企业自有设备和员工工作使用的个人设备上发生意外数据泄露。 它无需对环境或其他应用进行更改即可实现此目的。

此功能支持：仅限 Windows 10

## <a name="custom-profile"></a>自定义配置文件
[自定义设置](custom-settings-configure.md)能够分配未在 Intune 中内置的设备设置。 例如，对于 Android 设备，可以输入 OMA-URI 值。 对于 iOS 设备，则可以导入在 Apple Configurator 中创建的配置文件。 

此功能支持：

- Android
- iOS
- macOS
- Windows Phone 8.1