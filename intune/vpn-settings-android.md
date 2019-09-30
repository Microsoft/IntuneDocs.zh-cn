---
title: 在 Microsoft Intune 中使用适用于 Android 设备的 VPN 设置 - Azure | Microsoft Docs
description: 请参阅在 Microsoft Intune 中的 Android 设备上创建 VPN 连接的所有设置。 输入 VPN 服务器的连接名称、IP 地址或 FQDN，选择用户进行身份验证的方式，并选择 Citrix、SonicWall、检查点胶囊和脉冲安全连接类型。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/06/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 36806769e3b4c2c726038c23edf22cb006819d8c
ms.sourcegitcommit: b78793ccbef2a644a759ca3110ea73e7ed6ceb8f
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 08/16/2019
ms.locfileid: "71302802"
---
# <a name="android-device-settings-to-configure-vpn-in-intune"></a>Android 设备设置，用于在 Intune 中配置 VPN

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文列出并介绍了可以在 Android 设备上控制的各种 VPN 连接设置。 作为移动设备管理（MDM）解决方案的一部分，请使用以下设置创建 VPN 连接、选择 VPN 的身份验证方式、选择 VPN 服务器类型等。

作为 Intune 管理员，可以创建 VPN 设置，并将它们分配到 Android 设备。 

若要详细了解 Intune 中的 VPN 配置文件，请参阅[vpn 配置文件](vpn-settings-configure.md)。

## <a name="before-you-begin"></a>在开始之前

[创建设备配置文件](vpn-settings-configure.md#create-a-device-profile)，并选择“Android”  。

## <a name="base-vpn"></a>基本 VPN

- **连接名称**：输入此连接的名称。 最终用户在浏览其设备的可用 VPN 连接时将看到此名称。 例如，输入 `Contoso VPN`。
- **IP 地址或 FQDN**：输入设备连接到的 VPN 服务器的 IP 地址或完全限定的域名 (FQDN)。 例如，输入 192.168.1.1 或 contoso.com   。

  - **身份验证方法**：选择设备向 VPN 服务器进行身份验证的方法。 选项包括：

    - **证书**：选择现有 SCEP 或 PKCS 证书配置文件以对连接进行身份验证。 [配置证书](certificates-configure.md)列出了创建证书配置文件的步骤。
    - **用户名和密码**：登录 VPN 服务器时，系统会提示最终用户输入其用户名和密码。

- **连接类型**：选择 VPN 连接类型。 选项包括：

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Access**
  - **Pulse Secure**
  - **Citrix SSO**

- **指纹**（仅限 Check Point Capsule VPN）：输入字符串（例如“Contoso Fingerprint Code”），验证 VPN 服务器是否可以信任  。 指纹将发送到客户端，因此客户端知道信任任何具有相同指纹的服务器。 如果设备没有指纹，则会提示用户信任 VPN 服务器，并显示指纹。 用户手动验证指纹，并选择“信任”进行连接。
- **输入 Citrix VPN 属性的键值对**（仅限 Citrix）：输入由 Citrix 提供的键值对。 这些值配置 VPN 连接的属性。 

  还可以**导入**包含键和值对的逗号分隔值文件（.csv）。 确保查看 "我的**数据" 具有标题**和**键**属性。

  添加了键和值对之后，使用 "**导出**" 将数据备份到 .csv 文件。

## <a name="next-steps"></a>后续步骤

[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

你还可以为[Android Enterprise](vpn-settings-android-enterprise.md)、 [iOS](vpn-settings-ios.md)、 [macOS](vpn-settings-macos.md)、 [Windows 10 和更高版本](vpn-settings-windows-10.md)、 [Windows 8.1](vpn-settings-windows-8-1.md)和[Windows Phone 8.1](vpn-settings-windows-phone-8-1.md)设备创建 VPN 配置文件。
