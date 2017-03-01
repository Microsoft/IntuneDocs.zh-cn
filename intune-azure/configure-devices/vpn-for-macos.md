---
title: "适用于 macOS 设备的 Intune VPN 设置"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解可用于在 macOS 设备上配置 VPN 连接的 Intune 设置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d203a70d-37df-4195-85f7-ad5ef14ac2a1
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 068dcd5209ff1cc2b2799919fe38bdfbf809423a
ms.lasthandoff: 02/18/2017


---

# <a name="vpn-settings-for-macos-devices-in-microsoft-intune"></a>Microsoft Intune 中适用于 macOS 设备的 VPN 设置

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

根据所选择的设置，下表中并非所有值都可配置。

## <a name="base-vpn-settings"></a>**基础 VPN 设置**

**连接名称** - 输入此连接的名称。 最终用户在浏览其设备的可用 VPN 连接列表时将看到此名称。
- **IP 地址或 FQDN** - 提供设备将连接到的 VPN 服务器的 IP 地址或完全限定的域名。 示例：**192.168.1.1**、**vpn.contoso.com**。
- **身份验证方法** - 从以下选项中选择设备向 VPN 服务器进行身份验证的方法：
    - **证书** - 在“身份验证证书”下，选择之前创建的 SCEP 或 PKCS 证书配置文件以对连接进行身份验证。 有关证书配置文件的更多详细信息，请参阅[如何配置证书](how-to-configure-certificates.md)。
    - **用户名和密码** - 最终用户必须提供用户名和密码才能登录 VPN 服务器。
- **连接类型** - 从以下供应商列表中选择 VPN 连接类型：
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **Dell SonicWALL Mobile Connect**
    - ** F5 Edge Client**
    - **Pulse Secure**
    - **自定义 VPN**
- “拆分隧道” - “启用”或“禁用”，此选项让设备根据流量确定使用哪个连接。 例如，旅馆中的用户使用 VPN 连接来访问工作文件，但使用旅馆的标准网络进行常规的 Web 浏览。

<!--- **Per-app VPN** - Select this option if you want to associate this VPN connection with an iOS or Mac OS X app so that the connection will be opened when the app is run. You can associate the VPN profile with an app when you deploy the software. For more information, see [How to deploy and monitor apps](/intune-azure/manage-apps/deploy-apps). --->

## <a name="custom-vpn-settings"></a>自定义 VPN 设置

如果选择“自定义 VPN”，请配置以下其他设置：

- **VPN 标识符** 这是所使用 VPN 应用的标识符，由 VPN 提供商提供。
- **输入自定义 VPN 属性的键值对** 添加或导入用于自定义 VPN 连接的**键**和**值**。 同样，这些值通常由 VPN 提供商提供。


## <a name="proxy-settings"></a>代理设置

- **自动配置脚本** - 使用文件配置代理服务器。 输入包含配置文件的**代理服务器 URL**（例如 **http://proxy.contoso.com**）。
- **地址** - 输入代理服务器地址（作为 IP 地址）。
- **端口号** - 输入与代理服务器关联的端口号。

