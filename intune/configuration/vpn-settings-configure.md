---
title: 在 Microsoft Intune 中向设备添加 VPN 设置 - Azure | Microsoft Docs
description: 对于 Android、Android Enterprise、iOS、macOS 和 Windows 设备，请使用内置设置在 Microsoft Intune 中创建虚拟专用网络 (VPN) 连接。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b11cbd3427b3b8e0a43a6e6e2af5fa80da45e16a
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206272"
---
# <a name="create-vpn-profiles-to-connect-to-vpn-servers-in-intune"></a>在 Intune 中创建 VPN 配置文件以连接到 VPN 服务器



虚拟专用网络 (VPN) 可让你的用户安全远程访问你的组织网络。 设备使用 VPN 连接配置文件来启动与 VPN 服务器的连接。 Microsoft Intune 中的“VPN 配置文件”  将 VPN 设置分配到你组织中的用户和设备，从而可以方便且安全地连接到组织网络。

例如，你希望用连接到组织网络上的文件共享所需的设置来配置所有 iOS 设备。 创建包含这些设置的 VPN 配置文件。 然后，将此配置文件分配到拥有 iOS 设备的所有用户。 用户能在可用网络的列表中看到 VPN 连接，并可以轻松连接。

> [!NOTE]
> 可使用 [Intune 自定义配置策略](custom-settings-configure.md)为以下平台创建 VPN 配置文件：
>
> * Android 4 及更高版本
> * 运行 Windows 8.1 和更高版本的已注册设备
> * Windows Phone 8.1 及更高版本
> * 运行 Windows 10 桌面版的已注册设备
> * Windows 10 移动版
> * Windows Holographic for Business

## <a name="vpn-connection-types"></a>VPN 连接类型

可以使用以下连接类型创建 VPN 配置文件：

|连接类型|平台|
|-|-|
|自动|Windows 10|
|Check Point Capsule VPN|- Android<br/>- Android Enterprise 工作配置文件<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|Cisco AnyConnect|- Android<br/>- Android Enterprise 工作配置文件<br/>- Android Enterprise 设备所有者（完全托管）<br/>- iOS<br/>- macOS|
|Cisco (IPSec)|iOS|
|Citrix SSO|- Android<br/>- Android Enterprise 工作配置文件：使用[应用配置策略](../apps/app-configuration-policies-use-android.md)<br/>- Android Enterprise 设备所有者（完全托管）：使用[应用配置策略](../apps/app-configuration-policies-use-android.md)<br/>- iOS<br/>- Windows 10|
|自定义 VPN|- iOS<br/>- macOS|
|F5 Access|- Android<br/>- Android Enterprise 工作配置文件<br/>- Android Enterprise 设备所有者（完全托管）<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|IKEv2| - iOS<br/>- Windows 10|
|L2TP|Windows 10|
|帕洛阿尔托网络全局保护|- Android Enterprise 工作配置文件：使用[应用配置策略](../apps/app-configuration-policies-use-android.md)<br/>- iOS<br/>- Windows 10|
|PPTP|Windows 10|
|脉冲安全|- Android<br/>- Android Enterprise 工作配置文件<br/>- Android Enterprise 设备所有者（完全托管）<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|SonicWall Mobile Connect|- Android<br/>- Android Enterprise 工作配置文件<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|Zscaler|- Android Enterprise 工作配置文件：使用[应用配置策略](../apps/app-configuration-policies-use-android.md)<br/>- iOS|

> [!IMPORTANT]
> 在你能够使用已分配到设备的 VPN 配置文件之前，必须安装适用于该配置文件的 VPN 应用。 [什么是 Microsoft Intune 中的应用管理？](../apps/app-management.md)一文中的信息可帮助使用 Intune 分配应用。  

关于如何使用 URI 设置创建自定义 VPN 配置文件，请参阅[创建具有自定义设置的配置文件](custom-settings-configure.md)。

## <a name="create-a-device-profile"></a>创建设备配置文件

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“设备”   > “配置文件”   > “创建配置文件”  。
3. 输入以下属性：

    - **名称**：输入配置文件的描述性名称。 为配置文件命名，以便稍后可以轻松地识别它们。 例如，配置文件名称最好是“整个公司的 VPN 配置文件”  。
    - **描述**：输入配置文件的说明。 此设置是可选的，但建议进行。
    - **平台**：选择设备平台。 选项包括：

      - **Android**
      - “Android Enterprise”   > “仅设备所有者” 
      - “Android Enterprise”   > “仅工作配置文件” 
      - **iOS/iPadOS**
      - **macOS**
      - **Windows Phone 8.1**
      - **Windows 8.1 及更高版本**
      - **Windows 10 及更高版本**

    - **配置文件类型**：选择“VPN”  。

4. 根据所选择的平台，可配置的设置有所不同。 有关每个平台的详细设置，请参阅以下文章：

    - [Android 设置](vpn-settings-android.md)
    - [Android Enterprise 设置](vpn-settings-android-enterprise.md)
    - [iOS/iPadOS 设置](vpn-settings-ios.md)
    - [macOS 设置](vpn-settings-macos.md)
    - [Windows Phone 8.1 设置](vpn-settings-windows-phone-8-1.md)
    - [Windows 8.1 设置](vpn-settings-windows-8-1.md)
    - [Windows 10 设置](vpn-settings-windows-10.md)（包括 Windows Holographic for Business）

5. 完成后，选择“确定”   > “创建”  以保存所做的更改。

配置文件随即创建并显示在配置文件列表中。 要向组分配此配置文件，请参阅[分配设备配置文件](device-profile-assign.md)。

## <a name="secure-your-vpn-profiles"></a>保护 VPN 配置文件

VPN 配置文件可以使用来自不同制造商的多种不同的连接类型和协议。 这些连接通常通过以下方法进行保护。

### <a name="certificates"></a>证书

在创建 VPN 配置文件时，选择之前已在 Intune 中创建的 SCEP 或 PKCS 证书配置文件。 该配置文件又称为身份证书。 用于对你创建的受信任的身份证书配置文件（或根证书）进行身份验证，以允许用户的设备进行连接  。 受信任的证书会分配到对 VPN 连接（通常是 VPN 服务器）进行身份验证的计算机。

有关如何在 Intune 中创建和使用证书配置文件的详细信息，请参阅[如何使用 Microsoft Intune 配置证书](../protect/certificates-configure.md)。

### <a name="user-name-and-password"></a>用户名和密码

用户通过提供用户名和密码向 VPN 服务器进行身份验证。

## <a name="next-steps"></a>后续步骤

配置文件已创建，但它尚未起到任何作用。 下一步是[将配置文件分配](device-profile-assign.md)到一些设备。

你也可以在 [Android](android-pulse-secure-per-app-vpn.md) 和 [iOS](vpn-setting-configure-per-app.md) 设备上创建并使用每应用 VPN。
