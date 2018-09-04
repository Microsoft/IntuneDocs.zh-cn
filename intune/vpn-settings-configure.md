---
title: 在 Microsoft Intune 中创建 VPN 设备配置文件 - Azure | Microsoft Docs
description: 对于 iOS 设备，查看虚拟专用网络 (VPN) 连接类型，在 Azure 门户中创建 VPN 设备配置文件，以及查看在 Microsoft Intune 中使用证书或用户名和密码来保护 VPN 配置文件的选项。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 97bddc1a183e3a546e76b346f53f80aba6a81c50
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2018
ms.locfileid: "43312867"
---
# <a name="create-vpn-profiles-in-intune"></a>在 Intune 中创建 VPN 配置文件

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

虚拟专用网络 (VPN) 可让你的用户安全远程访问你的公司网络。 设备使用 VPN 连接配置文件来初始化与 VPN 服务器的连接。 使用 Microsoft Intune 中的“VPN 配置文件”将 VPN 设置分配到你组织中的用户和设备，从而可以方便且安全地连接到网络。

例如，假定你想要用连接到公司网络上的文件共享所需的设置预配所有 iOS 设备。 创建 VPN 配置文件，该配置文件包含用于连接企业网络的设置。 然后，将此配置文件分配到拥有 iOS 设备的所有用户。 用户能在可用网络的列表中看到 VPN 连接，并可以轻松连接。

可使用 Intune 自定义配置策略为以下平台创建 VPN 配置文件：

* Android 4 及更高版本
* 运行 Windows 8.1 和更高版本的已注册设备
* Windows Phone 8.1 及更高版本
* 运行 Windows 10 桌面版的已注册设备
* Windows 10 移动版
* Windows Holographic for Business

## <a name="vpn-connection-types"></a>VPN 连接类型

可以使用以下连接类型创建 VPN 配置文件：

|连接类型|Android<br>Android 工作配置文件|iOS|macOS|Windows Phone 8.1|Windows 8.1|Windows 10|
|-|-|-|-|-|-|-|
|自动|否|否|否|否|否|是|
|Check Point Capsule VPN|是|是|是|是|是|是|
|Cisco AnyConnect|是|是|是|否|否|否|
|SonicWall Mobile Connect|是|是|是|是|是|是|
|F5 Edge Client|是|是|是|是|是|是|
|帕洛阿尔托网络全局保护|否|是|否|否|否|是|
|脉冲安全|是|是|是|是|是|是|
|Cisco (IPSec)|否|是|否|否|否|否|
|Citrix|是（仅 Android）|是|否|否|否|是|
|IKEv2|否|否|否|否|否|是|
|L2TP|否|否|否|否|否|是|
|PPTP|否|否|否|否|否|是|
|Zscaler|否|是|否|否|否|否|
|自定义 VPN|否|是|是|否|否|否|

> [!IMPORTANT]
> 在你能够使用已分配到设备的 VPN 配置文件之前，必须安装适用于该配置文件的 VPN 应用。 [什么是 Microsoft Intune 中的应用管理？](app-management.md)一文中的信息可帮助使用 Intune 分配应用。  

关于如何使用 URI 设置创建自定义 VPN 配置文件，请参阅[创建具有自定义设置的配置文件](custom-settings-configure.md)。

## <a name="create-a-device-profile-containing-vpn-settings"></a>创建包含 VPN 设置的设备配置文件

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 选择“设备配置” > “配置文件” > “创建配置文件”。
4. 输入 VPN 配置文件的“名称”和“说明”。
5. 从“平台”下拉列表中，选择要应用 VPN 设置的设备平台。 目前，可以为 VPN 设备设置选择以下平台之一：
   - **Outlook Web Access (OWA)**
   - **Android 企业**
   - **iOS**
   - **macOS**
   - **Windows Phone 8.1**
   - **Windows 8.1 及更高版本**
   - **Windows 10 及更高版本**
6. 在“配置文件”类型下拉列表中，选择“VPN”。
7. 根据所选择的平台，可配置的设置有所不同。 有关每个平台的详细设置，请转到以下主题之一：
   - [Android 和 Android 工作配置文件设置](vpn-settings-android.md)
   - [iOS 设置](vpn-settings-ios.md)
   - [macOS 设置](vpn-settings-macos.md)
   - [Windows Phone 8.1 设置](vpn-settings-windows-phone-8-1.md)
   - [Windows 8.1 设置](vpn-settings-windows-8-1.md)
   - [Windows 10 设置](vpn-settings-windows-10.md)（包括 Windows Holographic for Business）
8. 完成后，单击“创建”来创建配置文件

配置文件随即创建并显示在配置文件列表中。 要向组分配此配置文件，请参阅[分配设备配置文件](device-profile-assign.md)。

## <a name="methods-of-securing-vpn-profiles"></a>保护 VPN 配置文件的方法

VPN 配置文件可以使用来自不同制造商的多种不同的连接类型和协议。 这些连接通常通过以下两种方法之一进行保护：

### <a name="certificates"></a>证书

在创建 VPN 配置文件时，选择之前已在 Intune 中创建的 SCEP 或 PKCS 证书配置文件。 该配置文件又称为身份证书。 用于对你创建的受信任的身份证书配置文件（或根证书）进行身份验证，以允许用户的设备进行连接。 受信任的证书会分配到对 VPN 连接（通常是 VPN 服务器）进行身份验证的计算机。

有关如何在 Intune 中创建和使用证书配置文件的详细信息，请参阅[如何使用 Microsoft Intune 配置证书](certificates-configure.md)。

### <a name="user-name-and-password"></a>用户名和密码

用户通过提供用户名和密码向 VPN 服务器进行身份验证。
