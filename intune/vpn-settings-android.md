---
title: 在 Microsoft Intune 中配置适用于 Android 设备的 VPN 设置 - Azure | Microsoft Docs
description: 创建适用于 Android 和 Android for work 设备的 VPN 配置文件时，输入 VPN 服务器的连接名称、IP 地址或 FQDN，选择用户与 VPN 服务器进行身份验证的方式，然后选择 Citrix、SonicWall、Check Point Capsule、Pulse Secure 和 Microsoft Edge 连接类型。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f37d19beddd96fdad63c61d83b0012869a7f9cd3
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55843708"
---
# <a name="configure-vpn-settings-for-devices-running-android-in-intune"></a>在 Intune 中为运行 Android 的设备配置 VPN 设置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文介绍可用于在运行 Android 的设备上配置 VPN 连接的 Intune 设置。

可以配置以下平台的 VPN 设置：

- [Outlook Web Access (OWA)](#android-vpn-settings)
- [Android 企业](#android-enterprise-vpn-settings)

以下值并非都可配置，具体取决于所选设置。

## <a name="android-vpn-settings"></a>Android VPN 设置

- **连接名称**：为此连接输入名称。 最终用户在浏览其设备的可用 VPN 连接时将看到此名称。
- **IP 地址或 FQDN**：输入设备连接到的 VPN 服务器的 IP 地址或完全限定的域名 (FQDN)。 例如，输入 192.168.1.1 或 contoso.com。

  - **身份验证方法**：选择设备向 VPN 服务器进行身份验证的方法。 选项包括：

    - **证书**：选择现有 SCEP 或 PKCS 证书配置文件，以对连接进行身份验证。 [配置证书](certificates-configure.md)列出了创建证书配置文件的步骤。
    - **用户名和密码**：登录 VPN 服务器时，最终用户会看到输入用户名和密码的提示。

- **连接类型**：选择 VPN 连接类型。 选项包括：

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **Citrix**

- **指纹**（仅限 Check Point Capsule VPN）：输入字符串（如“Contoso 指纹代码”），以验证能否信任 VPN 服务器。 可将指纹发送到客户端，使其在连接时知道信任具有相同指纹的任何服务器。 如果设备没有指纹，则会提示用户信任 VPN 服务器，并显示指纹。 用户手动验证指纹，并选择“信任”进行连接。
- **输入 Citrix VPN 属性的键值对**（仅限 Citrix）：输入由 Citrix 提供的键值对。 这些值配置 VPN 连接的属性。

## <a name="android-enterprise-vpn-settings"></a>Android Enterprise VPN 设置

- **连接名称**：为此连接输入名称。 最终用户在浏览其设备的可用 VPN 连接时将看到此名称。
- **IP 地址或 FQDN**：输入设备连接到的 VPN 服务器的 IP 地址或完全限定的域名 (FQDN)。 例如，输入 192.168.1.1 或 contoso.com。

  - **身份验证方法**：选择设备向 VPN 服务器进行身份验证的方法。 选项包括：
  
    - **证书**：选择现有 SCEP 或 PKCS 证书配置文件，以对连接进行身份验证。 [配置证书](certificates-configure.md)列出了创建证书配置文件的步骤。
    - **用户名和密码**：登录 VPN 服务器时，最终用户会看到输入用户名和密码的提示。

- **连接类型**：选择 VPN 连接类型。 选项包括：

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Access**
  - **Pulse Secure**

## <a name="next-steps"></a>后续步骤
[Intune 中的 VPN 配置文件](vpn-settings-configure.md)
