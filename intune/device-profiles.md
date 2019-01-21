---
title: Microsoft Intune 中的设备功能和设置 - Azure | Microsoft Docs
description: Azure 门户中的不同 Microsoft Intune 设备配置文件概述，包括功能、限制、电子邮件、WiFi、VPN、教育、证书、升级 Windows 10、BitLocker 和 Windows Defender、Windows 信息保护、管理模板，以及自定义设备配置设置。 使用这些配置文件管理和保护公司内的数据和设备。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: bc28bca31c43140a7bca528655825bab60c53be1
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203512"
---
# <a name="apply-features-settings-on-your-devices-using-device-profiles-in-microsoft-intune"></a>对 Microsoft Intune 中使用设备配置文件的设备应用功能设置

Microsoft Intune 提供可在组织内的不同设备上启用或禁用的设置和功能。 这些设置和功能将添加“配置文件”。 可以为不同的设备、不同的平台（包括 iOS、Android 和 Windows）创建配置文件，然后使用 Intune 将该配置文件应用于组织中的设备。

一些配置文件示例如下：

- 在 Windows 10 设备上，使用可阻止 Internet Explorer 中 ActiveX 控件的配置文件模板。
- 在 iOS 和 macOS 设备上，允许用户使用组织中的 AirPrint 打印机。
- 允许或阻止访问设备上的蓝牙。
- 创建 WiFi 或 VPN 配置文件，让不同设备访问公司网络。
- 管理软件更新，包括何时安装它们。
- 运行 Android 设备和专用的展台设备，该设备可以运行一个或多个应用。

本文列出了创建配置文件的步骤，并概述可创建的不同类型的配置文件。 使用这些配置文件来允许或阻止设备上的某些功能。

## <a name="create-the-profile"></a>创建配置文件

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”> 筛选“Intune”> 选择“Intune”。

2. 选择“设备配置”。 你有下列选择：

    - **概述**：列出配置文件的状态，并提供有关分配给用户和设备的配置文件的其他详细信息。
    - **管理**：创建设备配置文件，并上传自定义 [PowerShell 脚本](intune-management-extension.md)以在配置文件中运行，并使用 [eSIM](esim-device-configuration.md) 向设备添加数据计划。
    - **监视**：检查配置文件的状态（成功或失败），并查看配置文件中的日志。
    - **设置**：在配置文件中添加 SCEP 或 PFX 证书颁发机构，或启用[电信费用管理](telecom-expenses-monitor.md)。

3. 依次选择“配置文件” > “创建配置文件”。 输入以下属性：

   - **名称**：输入配置文件的描述性名称。
   - **说明**：输入配置文件的说明。 此设置是可选的，但建议进行。
   - **平台**：选择设备平台。 选项包括：  

       - **Outlook Web Access (OWA)**
       - **Android 企业**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 及更高版本**
       - **Windows 10 及更高版本**

   - **配置文件类型**：选择要创建的设置类型。 显示的列表取决于所选择的平台：

       - [管理模板](administrative-templates-windows.md)
       - [自定义](custom-settings-configure.md)
       - [传递优化](delivery-optimization-windows.md)
       - [设备功能](device-features-configure.md)
       - [设备限制](device-restrictions-configure.md)
       - [版本升级和模式切换](edition-upgrade-configure-windows-10.md)
       - [教育](education-settings-configure.md)
       - [Email](email-settings-configure.md)
       - [Endpoint protection](endpoint-protection-configure.md)
       - [标识保护](identity-protection-configure.md)  
       - [展台](kiosk-settings.md)
       - [PKCS 证书](certficates-pfx-configure.md)
       - [SCEP 证书](certificates-scep-configure.md)
       - [受信任的证书](certificates-configure.md)
       - [更新策略](software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [Windows Defender ATP](advanced-threat-protection.md)
       - [Windows 信息保护](windows-information-protection-configure.md)

     例如，如果选择“iOS”作为平台，配置文件类型选项外观将如下所示：

     ![在 Intune 中创建 iOS 配置文件](./media/create-device-profile.png)

4. 选择“设置”。 按类别对设置进行排列。 选择某个类别，查看可配置的所有设置的列表。

5. 完成后，选择“确定” > “创建”，保存所做更改。

若要了解有关不同配置文件类型的详细信息，请阅读本文的下一个部分。

## <a name="administrative-templates-preview"></a>管理模板（预览版）

[管理模板](administrative-templates-windows.md)包括数百个可针对 Internet Explorer、OneDrive、远程桌面、Word、Excel 和其他 Office 程序等配置的设置。

这些模板会为管理员提供了类似于组策略的简易设置视图，但它们是 100% 基于云的。 

此功能支持：

- Windows 10 及更高版本

## <a name="device-features"></a>设备功能

[设备功能](device-features-configure.md)控制 iOS 和 macOS 设备上的功能，例如 AirPrint、通知和锁屏消息。

此功能支持：

- iOS 
- macOS

## <a name="device-restrictions"></a>设备限制

[设备限制](device-restrictions-configure.md)控制设备上的安全性、硬件、数据共享，以及更多设置。 例如，创建一个可阻止 iOS 设备用户使用设备相机的设备限制配置文件。 

此功能支持：

- Android
- Android Enterprise
- iOS
- macOS
- Windows 10
- Windows 10 协同版

## <a name="delivery-optimization"></a>传递优化

[传递优化](delivery-optimization-windows.md)提供了更好的传递软件更新体验。 这些设置将替换“软件更新” > “Windows 10 更新通道”设置。

使用这些设置来控制如何将软件更新下载到组织中的设备。 例如，可以允许用户获取其自己的更新，或使用设备配置文件中的传递优化云服务获取更新。

此功能支持：

- Windows 10 及更高版本

## <a name="endpoint-protection"></a>Endpoint Protection

[适用于 Windows 10 的 Endpoint Protection 设置](endpoint-protection-windows-10.md)配置适用于 Windows 10 设备的 BitLocker 和 Windows Defender 设置。

若要使用 Microsoft Intune 载入 Windows Defender 高级威胁防护 (WDATP)，请参阅 [Configure endpoints using Mobile Device Management (MDM) tools](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-mdm-windows-defender-advanced-threat-protection)（使用移动设备管理 (MDM) 工具配置终结点）。

此功能支持：

- Windows 10 及更高版本

## <a name="identity-protection"></a>标识保护

[标识保护](identity-protection-configure.md)控制 Windows 10 和 Windows 10 移动版设备上的 Windows Hello 企业版体验。 配置这些设置，使 Windows Hello 企业版可供用户和设备使用，以及指定设备 PIN 和手势的要求。  

此功能支持：  

- Windows 10 及更高版本
- Windows Holographic for Business  

## <a name="kiosk"></a>Kiosk

[展台设置](kiosk-settings.md)配置文件可将设备配置为运行一个应用，或运行多个应用。 还可以自定义展台的其他功能，包括“开始”菜单和 Web 浏览器。

此功能支持：

- Windows 10 及更高版本

展台设置也可用作适用于 [Android](device-restrictions-android.md#kiosk)、[Android Enterprise](device-restrictions-android-for-work.md#kiosk-settings) 和 [ios](device-restrictions-ios.md#kiosk-supervised-only) 的设备限制。

## <a name="email"></a>Email

[电子邮件设置](email-settings-configure.md)创建、分配和监视设备上的 Exchange ActiveSync 电子邮件设置。 邮件配置文件可帮助确保一致性、减少支持呼叫，并让最终用户能够在不进行任何所需设置的情况下在其个人设备上访问公司电子邮件。 

此功能支持： 

- Android
- iOS
- Windows Phone 8.1
- Windows 10

## <a name="vpn"></a>VPN

[VPN 设置](vpn-settings-configure.md)将配置文件分配到组织中的用户和设备，从而使其方便安全地连接到网络。 

虚拟专用网络 (VPN) 可让用户安全地远程访问公司网络。 设备使用 VPN 连接配置文件来初始化与 VPN 服务器的连接。 

此功能支持： 

- Android
- iOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10

## <a name="wi-fi"></a>Wi-Fi

[Wi-Fi 设置](wi-fi-settings-configure.md)将无线网络设置分配给用户和设备。 分配 WiFi 配置文件后，用户无需自行配置即可访问公司 Wi-Fi。 

此功能支持： 

- Android
- iOS
- macOS
- Windows 8.1 （仅限导入）

## <a name="esim-cellular---public-preview"></a>eSIM 手机网络 - 公共预览版

[eSIM 手机网络配置文件](esim-device-configuration.md)可让管理员在受管理设备上配置手机网络流量套餐以进行 Internet 和数据访问。 从移动运营商处获取激活码后，使用 Intune 导入这些激活码，然后分配给支持 eSIM 的设备。

此功能支持：
- Windows 10 Fall Creators Update 及更高版本

## <a name="education"></a>教育

[教育设置 - Windows 10](education-settings-configure.md) 配置针对 [Windows 参加测验应用](https://education.microsoft.com/gettrained/win10takeatest)的选项。 在配置这些选项时，直到测试完成才可以在设备上运行其他应用。

[教育设置 - iOS](education-settings-configure-ios-shared.md) 使用 iOS Classroom 应用来指导学习，并控制课堂中的学生设备。 可以将 iPad 设备配置为多名学生可以共享一台设备。

## <a name="edition-upgrade"></a>版本升级

[Windows 10 版本升级](edition-upgrade-configure-windows-10.md)将运行某些 Windows 10 版本的设备自动升级到较新的版本。

此功能支持： 
- Windows 10 及更高版本

## <a name="update-policies"></a>更新策略

[ iOS 更新策略](software-updates-ios.md)展示了创建和分配 iOS 策略以在 iOS 设备上安装软件更新的方式。 你还可以查看安装状态。

有关 Windows 设备上的更新策略，请参阅[传递优化](delivery-optimization-windows.md)。 

此功能支持：
- iOS

## <a name="certificates"></a>证书

[证书](certificates-configure.md)配置已分配到设备的受信任证书、SCEP 证书和 PKCS 证书，用于对 Wi-Fi、VPN 和电子邮件配置文件进行身份验证。

此功能支持： 

- Android
- iOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10

## <a name="windows-information-protection-profile"></a>Windows 信息保护配置文件

[Windows 信息保护](windows-information-protection-configure.md)有助于防范数据泄露，而不会干扰员工体验。 它还有助于防范企业应用和数据在企业自有设备和员工工作使用的个人设备上发生意外数据泄露。 使用 Windows 信息保护不需要对你的环境或其他应用进行更改。

此功能支持：

- Windows 10 及更高版本

## <a name="shared-multi-user-device"></a>共享的多用户设备

[Windows 10](shared-user-device-settings-windows.md) 和 [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md) 包括用于管理多用户设备（也称为共享设备或共享电脑）的设置。 当用户登录设备时，你可选择用户是否可更改睡眠选项，或在设备上保存文件。 在其他示例中，可以创建可检测 Windows HoloLens 设备中非活动凭据的策略，以节省空间。

这些共享多用户设备设置允许管理员控制部分设备功能，并使用 Intune 管理这些共享设备。

此功能支持：

- Windows 10 及更高版本
- Windows Holographic for Business

## <a name="custom-profile"></a>自定义配置文件

[自定义设置](custom-settings-configure.md)可让管理员分配未在 Intune 中内置的设备设置。 例如，对于 Android 设备，可以输入 OMA-URI 值。 对于 iOS 设备，则可以导入在 Apple Configurator 中创建的配置文件。 

此功能支持：

- Android
- iOS
- macOS
- Windows Phone 8.1

## <a name="manage-and-troubleshoot"></a>管理和故障排除

[管理配置文件](device-profile-monitor.md)以检查设备的状态和分配的配置文件。 还可以通过查看导致冲突的设置以及包含这些设置的配置文件来帮助解决冲突。 [常见问题和解决方法](device-profile-troubleshoot.md)提供了一个问答，以帮助使用配置文件，包括删除配置文件时发生的情况以及导致通知发送到设备的原因等。

## <a name="next-steps"></a>后续步骤
选择平台，并开始：

