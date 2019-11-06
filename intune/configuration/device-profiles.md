---
title: Microsoft Intune 中的设备功能和设置 - Azure | Microsoft Docs
description: 不同 Microsoft Intune 设备配置文件的概述。 在 Azure 门户中获取有关功能、限制、电子邮件、WiFi、VPN、教育、证书、升级 Windows 10、BitLocker 和 Windows Defender、Windows 信息保护、管理模板，以及自定义设备配置设置的信息。 使用这些配置文件管理和保护公司内的数据和设备。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: karthib
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7c49445800f5d34fbb6ce0a845d4f29c3e587483
ms.sourcegitcommit: c2e62f1ebdf75599c8e544287123c602f0f15f2b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/22/2019
ms.locfileid: "72749353"
---
# <a name="apply-features-and-settings-on-your-devices-using-device-profiles-in-microsoft-intune"></a>对 Microsoft Intune 中使用设备配置文件的设备应用功能和设置

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune 提供可在组织内的不同设备上启用或禁用的设置和功能。 这些设置和功能将添加到“配置文件”。 你可以为不同的设备和不同的平台创建配置文件，包括 iOS、Android 和 Windows。 然后，使用 Intune 应用配置文件或将其“分配”给设备。

作为移动设备管理 (MDM) 解决方案的一部分，使用这些配置文件来完成不同的任务。 一些配置文件示例如下：

- 在 Windows 10 设备上，使用可阻止 Internet Explorer 中 ActiveX 控件的配置文件模板。
- 在 iOS 和 macOS 设备上，允许用户使用组织中的 AirPrint 打印机。
- 允许或阻止访问设备上的蓝牙。
- 创建 WiFi 或 VPN 配置文件，让不同设备访问公司网络。
- 管理软件更新，包括何时安装它们。
- 将 Android 设备作为专用的展台设备运行，该设备可以运行一个或多个应用。

本文概述了可创建的不同类型的配置文件。 使用这些配置文件来允许或阻止设备上的某些功能。

## <a name="administrative-templates"></a>管理模板

[管理模板](administrative-templates-windows.md)包括数百个可针对 Internet Explorer、OneDrive、远程桌面、Word、Excel 和其他 Office 程序配置的设置。

这些模板为管理员提供了类似于组策略的简化设置视图，但它们是完全基于云的。

此功能支持：

- 支持固件上的 Windows 10 1809 及更高版本。

## <a name="certificates"></a>证书

[证书](../protect/certificates-configure.md)配置分配到设备的受信任、SCEP 和 PKCS 证书。 这些证书会对 WiFi、VPN 和电子邮件配置文件进行身份验证。

此功能支持： 

- Android
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10 及更高版本

## <a name="custom-profile"></a>自定义配置文件

[自定义设置](custom-settings-configure.md)可让管理员分配未在 Intune 中内置的设备设置。 对于 Android 设备，可以输入 OMA-URI 值。 对于 iOS 设备，则可以导入在 Apple Configurator 中创建的配置文件。

此功能支持：

- Android
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows Phone 8.1

## <a name="delivery-optimization"></a>传递优化

[传递优化](delivery-optimization-windows.md)提供了更好的传递软件更新体验。 这些设置将替换“软件更新”   >   “Windows 10 更新通道”设置。

使用这些设置来控制如何将软件更新下载到组织中的设备。 例如，可以允许用户获取其自己的更新，或使用设备配置文件中的传递优化云服务获取更新。

此功能支持：

- Windows 10 及更高版本

## <a name="device-features"></a>设备功能

[设备功能](device-features-configure.md)控制 iOS 和 macOS 设备上的功能，例如 AirPrint、通知和锁屏消息。

此功能支持：

- iOS/iPadOS
- macOS

## <a name="device-firmware-configuration-interface"></a>设备固件配置接口

[设备固件配置接口](device-firmware-configuration-interface-windows.md) (DFCI) 允许管理员使用 Intune 启用或禁用 UEFI (BIOS) 设置。 使用这些设置增强固件级别的安全性，这样通常可以更好地抵抗恶意攻击。

此功能支持：

- Windows 10 及更高版本

## <a name="device-restrictions"></a>设备限制

[设备限制](device-restrictions-configure.md)控制设备上的安全性、硬件、数据共享，以及更多设置。 例如，创建一个可阻止 iOS 设备用户使用设备相机的设备限制配置文件。 

此功能支持：

- Android
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows 10 及更高版本
- Windows 10 协同版

## <a name="edition-upgrade"></a>版本升级

[Windows 10 版本升级](edition-upgrade-configure-windows-10.md)将运行某些 Windows 10 版本的设备自动升级到较新的版本。

此功能支持：

- Windows 10 及更高版本

## <a name="education"></a>教育水平

[教育设置 - Windows 10](education-settings-configure.md) 配置针对 [Windows 参加测验应用](https://education.microsoft.com/gettrained/win10takeatest)的选项。 在配置这些选项时，直到测试完成才可以在设备上运行其他应用。

[教育设置 - iOS](../fundamentals/education-settings-configure-ios-shared.md) 使用 iOS Classroom 应用来指导学习，并控制课堂中的学生设备。 可以将 iPad 设备配置为多名学生可以共享一台设备。

## <a name="email"></a>电子邮件

[电子邮件设置](email-settings-configure.md)创建、分配和监视设备上的 Exchange ActiveSync 电子邮件设置。 邮件配置文件可帮助确保一致性、减少支持呼叫，并让最终用户能够在不进行任何所需设置的情况下在其个人设备上访问公司电子邮件。 

此功能支持： 

- Android
- Android Enterprise
- iOS/iPadOS
- Windows Phone 8.1
- Windows 10 及更高版本

## <a name="endpoint-protection"></a>Endpoint Protection

[适用于 Windows 10 的 Endpoint Protection 设置](../protect/endpoint-protection-windows-10.md)配置适用于 Windows 10 设备的 BitLocker 和 Windows Defender 设置。

若要使用 Microsoft Intune 载入 Microsoft Defender 高级威胁防护 (WDATP)，请参阅[使用移动设备管理 (MDM) 工具配置终结点](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints-mdm)。

此功能支持：

- Windows 10 及更高版本

## <a name="esim-cellular---public-preview"></a>eSIM 手机网络 - 公共预览版

[eSIM 手机网络配置文件](esim-device-configuration.md)可让管理员在受管理设备上配置手机网络流量套餐以进行 Internet 和数据访问。 从移动运营商处获取激活码后，使用 Intune 导入这些激活码，然后分配给支持 eSIM 的设备。

此功能支持：

- Windows 10 Fall Creators Update 及更高版本

## <a name="extensions"></a>扩展

[内核扩展](kernel-extensions-overview-macos.md)允许管理员在 macOS 设备的内核级别添加功能或程序。 配置这些设置以信任来自特定开发人员或合作伙伴的所有扩展，或允许特定内核扩展。

此功能支持：

- macOS

## <a name="identity-protection"></a>标识保护

[标识保护](../protect/identity-protection-configure.md)控制 Windows 10 和 Windows 10 移动版设备上的 Windows Hello 企业版体验。 配置这些设置，使 Windows Hello 企业版可供用户和设备使用，以及指定设备 PIN 和手势的要求。  

此功能支持：  

- Windows 10 及更高版本
- Windows Holographic for Business  

## <a name="kiosk"></a>Kiosk

[展台设置](kiosk-settings.md)配置文件可将设备配置为运行一个应用，或运行多个应用。 还可以自定义展台的其他功能，包括“开始”菜单和 Web 浏览器。

此功能支持：

- Windows 10 及更高版本

展台设置也可用作适用于 [Android](device-restrictions-android.md#kiosk)、[Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings) 和 [iOS](device-restrictions-ios.md#kiosk) 的设备限制。

## <a name="oemconfig"></a>OEMConfig

[OEMConfig](android-oem-configuration-overview.md) 标准允许 OEM（原始设备制造商）和 EMM（企业移动性管理）按照标准方式构建和支持特定于 OEM 的 Android Enterprise 设备功能。 OEM 使用 OEMConfig 创建架构来定义特定于 OEM 的管理功能，并将其嵌入上传到 Google Play 的应用。 Intune 从该应用读取此架构，允许 Intune 管理员配置架构中的设置。

此功能支持：

- Android Enterprise (OEMConfig)

## <a name="powershell-scripts"></a>PowerShell 脚本

[Windows 10 设备的 PowerShell 脚本](../apps/intune-management-extension.md)使用 Intune 管理扩展从 Intune 上传 PowerShell 脚本，然后在设备上运行这些脚本。 另请参阅使用此扩展所需的条件、如何将它们添加到 Intune，以及其他重要信息。


此功能支持：

- Windows 10 及更高版本
- Windows Holographic for Business

## <a name="shared-multi-user-device"></a>共享的多用户设备

[Windows 10](shared-user-device-settings-windows.md) 和 [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md) 包括用于管理多用户设备（也称为共享设备或共享电脑）的设置。 当用户登录设备时，你可选择用户是否可更改睡眠选项，或在设备上保存文件。 在其他示例中，为节省空间，可以创建可删除 Windows HoloLens 设备中非活动凭据的配置文件。

这些共享多用户设备设置允许管理员控制部分设备功能，并使用 Intune 管理这些共享设备。

此功能支持：

- Windows 10 及更高版本
- Windows Holographic for Business

## <a name="update-policies"></a>更新策略

[ iOS 更新策略](../protect/software-updates-ios.md)展示了创建和分配 iOS 策略以在 iOS 设备上安装软件更新的方式。 你还可以查看安装状态。

有关 Windows 设备上的更新策略，请参阅[传递优化](delivery-optimization-windows.md)。 

此功能支持：

- iOS/iPadOS

## <a name="vpn"></a>VPN

[VPN 设置](vpn-settings-configure.md)将配置文件分配到组织中的用户和设备，从而使其方便安全地连接到网络。 

虚拟专用网络 (VPN) 可让用户安全地远程访问公司网络。 设备使用 VPN 连接配置文件来初始化与 VPN 服务器的连接。 

此功能支持： 

- Android
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10 及更高版本

## <a name="wi-fi"></a>Wi-Fi

[Wi-Fi 设置](wi-fi-settings-configure.md)将无线网络设置分配给用户和设备。 分配 WiFi 配置文件后，用户无需自行配置即可访问公司 Wi-Fi。 

此功能支持： 

- Android
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows 8.1 （仅限导入）
- Windows 10 及更高版本

## <a name="windows-information-protection-profile"></a>Windows 信息保护配置文件

[Windows 信息保护](../protect/windows-information-protection-configure.md)有助于防范数据泄露，而不会干扰员工体验。 它还有助于防范企业应用和数据在企业自有设备和员工工作使用的个人设备上发生意外数据泄露。 使用 Windows 信息保护不需要对你的环境或其他应用进行更改。

此功能支持：

- Windows 10 及更高版本

## <a name="zebra-mobility-extensions-mx"></a>Zebra 移动性扩展 (MX)

通过 [Zebra 移动性扩展 (MX)](android-zebra-mx-overview.md)，管理员可以在 Intune 中使用和管理 Zebra 设备。 创建具有你的设置的 StageNow 配置文件，然后使用 Intune 将这些配置文件分配并部署到 Zebra 设备。 [StageNow 日志及常见问题](android-zebra-mx-logs-troubleshoot.md)是一个不错的资源，有助于在使用 StageNow 时对配置文件进行故障排除并查看一些潜在问题。

此功能支持：

- Android（移动性扩展）

## <a name="manage-and-troubleshoot"></a>管理和故障排除

[管理配置文件](device-profile-monitor.md)以检查设备的状态和分配的配置文件。 还可以通过查看导致冲突的设置以及包含这些设置的配置文件来帮助解决冲突。 [常见问题和解决方法](device-profile-troubleshoot.md)可帮助管理员处理配置文件。 它介绍了删除配置文件时发生的情况，导致将通知发送到设备的原因等等。

## <a name="next-steps"></a>后续步骤

选择平台开始使用。
