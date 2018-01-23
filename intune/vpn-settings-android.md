---
title: "适用于 Android 设备的 Intune VPN 设置"
titlesuffix: Azure portal
description: "了解可用于在 Android 设备上配置 VPN 连接的 Intune 设置"
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 12/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 16c056ca-320e-4107-ad03-a0cf96c28885
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 31d1e40c3cd352c00dd7a659f716b5690ea64ea1
ms.sourcegitcommit: 5877b650d93fc9a5e8f058f845acbdbfdff828b7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2018
---
# <a name="vpn-settings-for-android-devices-in-microsoft-intune"></a>Microsoft Intune 中适用于 Android 设备的 VPN 设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

作为 Intune 管理员，你可以配置以下平台的 VPN 设置：

- [Outlook Web Access (OWA)](#android-vpn-settings)
- [Android for Work](#android-for-work-vpn-settings)

取决于所选的设置，并非以下列出的所有值都可配置。

## <a name="android-vpn-settings"></a>Android VPN 设置
**连接名称** - 输入此连接的名称。 最终用户在浏览其设备的可用 VPN 连接列表时将看到此名称。
- **IP 地址或 FQDN** - 提供设备将连接到的 VPN 服务器的 IP 地址或完全限定的域名。 示例：**192.168.1.1**、**vpn.contoso.com**。
- **身份验证方法** - 从以下选项中选择设备向 VPN 服务器进行身份验证的方法：
    - **证书** - 选择之前创建的 SCEP 或 PKCS 证书配置文件对连接进行身份验证。 有关证书配置文件的更多详细信息，请参阅[如何配置证书](certificates-configure.md)。
    - **用户名和密码** - 最终用户必须提供用户名和密码才能登录 VPN 服务器。
- **连接类型** - 从以下供应商列表中选择 VPN 连接类型：
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **Dell SonicWALL Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **Citrix**

- **指纹**（仅限 Check Point Capsule VPN）- 指定一个将用于验证 VPN 服务器是否可以信任的字符串（例如“Contoso Fingerprint Code”）。 指纹可以：发送到客户端，因此在连接时它知道信任任何提供相同指纹的服务器。 如果设备还没有指纹，则会提示用户信任正在连接的 VPN 服务器，并显示指纹（用户手动验证指纹，并选择信任以进行连接）。
- **输入 Citrix VPN 属性的键值对**（仅限 Citrix）- 输入由 Citrix 提供的键值对，以配置 VPN 连接的属性。

## <a name="android-for-work-vpn-settings"></a>Android for Work VPN 设置

**连接名称** - 输入此连接的名称。 最终用户在浏览其设备的可用 VPN 连接列表时将看到此名称。
- **IP 地址或 FQDN** - 提供设备将连接到的 VPN 服务器的 IP 地址或完全限定的域名。 示例：**192.168.1.1**、**vpn.contoso.com**。
- **身份验证方法** - 从以下选项中选择设备向 VPN 服务器进行身份验证的方法：
    - **证书** - 选择之前创建的 SCEP 或 PKCS 证书配置文件对连接进行身份验证。 有关证书配置文件的更多详细信息，请参阅[如何配置证书](certificates-configure.md)。
    - **用户名和密码** - 最终用户必须提供用户名和密码才能登录 VPN 服务器。
- **连接类型** - 从以下供应商列表中选择 VPN 连接类型：
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **Dell SonicWALL Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**

