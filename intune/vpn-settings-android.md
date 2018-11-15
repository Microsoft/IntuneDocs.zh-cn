---
title: 在 Microsoft Intune 中配置适用于 Android 设备的 VPN 设置 - Azure | Microsoft Docs
description: 创建适用于 Android 和 Android for work 设备的 VPN 配置文件时，输入 VPN 服务器的连接名称、IP 地址或 FQDN，选择用户与 VPN 服务器进行身份验证的方式，然后选择 Citrix、SonicWall、Check Point Capsule、Pulse Secure 和 Microsoft Edge 连接类型。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 113d2e52783f3c7e9f013d2cc239efad45408c87
ms.sourcegitcommit: d8edd1c3d24123762dd6d14776836df4ff2a31dd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2018
ms.locfileid: "51576811"
---
# <a name="configure-vpn-settings-for-devices-running-android-in-intune"></a>在 Intune 中为运行 Android 的设备配置 VPN 设置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文介绍可用于在运行 Android 的设备上配置 VPN 连接的 Intune 设置。

可以配置以下平台的 VPN 设置：

- [Outlook Web Access (OWA)](#android-vpn-settings)
- [Android for Work](#android-for-work-vpn-settings)

以下值并非都可配置，具体取决于所选设置。

## <a name="android-vpn-settings"></a>Android VPN 设置

- **连接名称**：输入此连接的名称。 最终用户在浏览其设备的可用 VPN 连接时将看到此名称。
- **IP 地址或 FQDN**：输入设备连接到的 VPN 服务器的 IP 地址或完全限定的域名 (FQDN)。 例如，输入 192.168.1.1 或 contoso.com。

  - **身份验证方法**：选择设备向 VPN 服务器进行身份验证的方法。 选项包括：

    - **证书**：选择现有 SCEP 或 PKCS 证书配置文件以对连接进行身份验证。 [配置证书](certificates-configure.md)列出了创建证书配置文件的步骤。
    - **用户名和密码**：登录 VPN 服务器时，系统会提示最终用户输入用户名和密码。

- **连接类型**：选择 VPN 连接类型。 选项包括：

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **Citrix**

- **指纹**（仅限 Check Point Capsule VPN）：输入字符串（例如“Contoso Fingerprint Code”），验证 VPN 服务器是否可以信任。 可将指纹发送到客户端，使其在连接时知道信任具有相同指纹的任何服务器。 如果设备没有指纹，则会提示用户信任 VPN 服务器，并显示指纹。 用户手动验证指纹，并选择“信任”进行连接。
- **输入 Citrix VPN 属性的键值对**（仅限 Citrix）：输入由 Citrix 提供的键值对。 这些值配置 VPN 连接的属性。

## <a name="android-for-work-vpn-settings"></a>Android for work VPN 设置

- **连接名称**：输入此连接的名称。 最终用户在浏览其设备的可用 VPN 连接时将看到此名称。
- **IP 地址或 FQDN**：输入设备连接到的 VPN 服务器的 IP 地址或完全限定的域名 (FQDN)。 例如，输入 192.168.1.1 或 contoso.com。

  - **身份验证方法**：选择设备向 VPN 服务器进行身份验证的方法。 选项包括：
  
    - **证书**：选择现有 SCEP 或 PKCS 证书配置文件以对连接进行身份验证。 [配置证书](certificates-configure.md)列出了创建证书配置文件的步骤。
    - **用户名和密码**：登录 VPN 服务器时，系统会提示最终用户输入用户名和密码。

- **连接类型**：选择 VPN 连接类型。 选项包括：

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**

## <a name="next-steps"></a>后续步骤
[Intune 中的 VPN 配置文件](vpn-settings-configure.md)
