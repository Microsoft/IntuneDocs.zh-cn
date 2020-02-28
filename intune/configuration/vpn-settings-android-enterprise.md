---
title: 在 Microsoft Intune 中使用适用于 Android Enterprise 的 VPN 设置 - Azure | Microsoft Docs
description: 请参阅所有设置以在 Microsoft Intune 中的 Android Enterprise 设备上创建 VPN 连接。 输入 VPN 服务器的连接名称、IP 地址或 FQDN，选择用户进行身份验证的方式，并选择 Citrix、SonicWall、Check Point Capsule 和 Pulse Secure 连接类型。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 81300651355e52f438ea2a314eeb1d0d48e3fcbc
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2020
ms.locfileid: "77510858"
---
# <a name="android-enterprise-device-settings-to-configure-vpn-in-intune"></a>用于在 Intune 中配置 VPN 的 Android Enterprise 设备设置

本文列出并介绍了可以在 Android Enterprise 设备上控制的各种 VPN 连接设置。 作为移动设备管理 (MDM) 解决方案的一部分，请使用以下设置创建 VPN 连接、选择 VPN 的身份验证方式、选择 VPN 服务器类型等。

Intune 管理员可以创建 VPN 设置，并将它们分配到 Android Enterprise 设备。 

若要详细了解 Intune 中的 VPN 配置文件，请参阅 [VPN 配置文件](vpn-settings-configure.md)。

> [!NOTE]
> 若要配置 always-on VPN，需要创建 VPN 配置文件，并在配置了 Always-on VPN 设置的情况下创建[设备限制](device-restrictions-android-for-work.md#connectivity)配置文件。

## <a name="before-you-begin"></a>在开始之前

[创建设备配置文件](vpn-settings-configure.md#create-a-device-profile)，并选择“Android Enterprise”  。

## <a name="device-owner-only"></a>仅设备所有者

- **连接名称**：为此连接输入名称。 最终用户在浏览其设备的可用 VPN 连接时将看到此名称。 例如，输入 `Contoso VPN`。
- **IP 地址或 FQDN**：输入设备连接到的 VPN 服务器的 IP 地址或完全限定的域名 (FQDN)。 例如，输入 192.168.1.1 或 contoso.com   。

  - **身份验证方法**：选择设备向 VPN 服务器进行身份验证的方法。 选项包括：
  
    - **证书**：选择现有 SCEP 或 PKCS 证书配置文件，以对连接进行身份验证。 [配置证书](../protect/certificates-configure.md)列出了创建证书配置文件的步骤。
    - **用户名和密码**：登录 VPN 服务器时，最终用户会看到输入用户名和密码的提示。

- **连接类型**：选择 VPN 连接类型。 选项包括：

  - **Cisco AnyConnect**
  - **F5 Access**
  - **Pulse Secure**

## <a name="work-profile-only"></a>仅工作配置文件

- **连接名称**：为此连接输入名称。 最终用户在浏览其设备的可用 VPN 连接时将看到此名称。 例如，输入 `Contoso VPN`。
- **IP 地址或 FQDN**：输入设备连接到的 VPN 服务器的 IP 地址或完全限定的域名 (FQDN)。 例如，输入 192.168.1.1 或 contoso.com   。

  - **身份验证方法**：选择设备向 VPN 服务器进行身份验证的方法。 选项包括：
  
    - **证书**：选择现有 SCEP 或 PKCS 证书配置文件，以对连接进行身份验证。 [配置证书](../protect/certificates-configure.md)列出了创建证书配置文件的步骤。
    - **用户名和密码**：登录 VPN 服务器时，最终用户会看到输入用户名和密码的提示。

- **连接类型**：选择 VPN 连接类型。 选项包括：

  - **Cisco AnyConnect**
  - **F5 Access**
  - **Pulse Secure**
  - **SonicWall Mobile Connect**
  - **Check Point Capsule VPN**

## <a name="next-steps"></a>后续步骤

[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

另外，还可以为 [Android](vpn-settings-android.md)、[iOS/iPadOS](vpn-settings-ios.md)、[macOS](vpn-settings-macos.md)、[Windows 10 和更高版本](vpn-settings-windows-10.md)、[Windows 8.1](vpn-settings-windows-8-1.md) 和 [Windows Phone 8.1](vpn-settings-windows-phone-8-1.md) 设备创建 VPN 配置文件。
