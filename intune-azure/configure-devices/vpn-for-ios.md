---
title: "适用于 iOS 设备的 VPN 设置 | Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：了解可用于在 iOS 设备上配置 VPN 连接的 Intune 设置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1447c123-ea33-4ea0-aab4-69577cdb8d00
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6cd3069a63bd657d1c9f5e33b96db39a3b3f98d2
ms.openlocfilehash: 23322313bfedb089f2665f53795996a26efe40e0


---

# <a name="vpn-settings-for-ios-devices-in-intune-azure-preview"></a>Intune Azure 预览版中适用于 iOS 设备的 VPN 设置

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

根据所选择的设置，下表中并非所有值都可配置。

## <a name="base-vpn-settings"></a>基础 VPN 设置


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
    - **Cisco (IPSec)**
    - **Citrix**
    - **自定义 VPN**
- “拆分隧道” - “启用”或“禁用”，此选项让设备根据流量确定使用哪个连接。 例如，旅馆中的用户使用 VPN 连接来访问工作文件，但使用旅馆的标准网络进行常规的 Web 浏览。


## <a name="custom-vpn-settings"></a>自定义 VPN 设置

如果选择“自定义 VPN”作为连接类型，请配置以下其他设置：

- **VPN 标识符** 这是所使用 VPN 应用的标识符，由 VPN 提供商提供。
- **输入自定义 VPN 属性的键值对** 添加或导入用于自定义 VPN 连接的**键**和**值**。 同样，这些值通常由 VPN 提供商提供。

## <a name="apps-per-app-vpn-settings"></a>应用（每应用 VPN）设置

- **每应用 VPN** - 如果希望从 Safari 浏览器访问 URL 时启用 VPN 连接，则启用此选项。 若要配置此项，在基础 VPN 设置中必须已选择“证书”作为身份验证方法。
- **在使用 Safari 浏览器时将启用 VPN 连接的 URL** 单击“添加”以添加一个或多个网站 URL。 访问这些 URL 时，将启用 VPN 连接。

- **按需规则** - 此设置让你可以配置条件规则，用于控制何时启动 VPN 连接。 例如，可以创建一个条件，仅在设备未连接到任何公司 Wi-Fi 网络时才使用 VPN 连接。 或者可以创建一个条件，如果设备无法访问指定的 DNS 搜索域，则不启动 VPN 连接。

    - **SSID 或 DNS 搜索域** - 选择此条件将使用无线网络 **SSID** 还是 **DNS 搜索域**。 选择“添加”以配置一个或多个 SSID 或搜索域。
    - **URL 字符串探测** -（可选）提供规则用作测试的 URL。 如果安装有此配置文件的设备能在不重定向的情况下访问此 URL，则将启动 VPN，且该设备将连接到目标 URL。 用户将看不到该 URL 字符串探测站点。 URL 字符串探测示例是审核 Web 服务器的地址，用于在连接 VPN 前检查设备的相容性。 另一种可能性是 URL 通过 VPN 将设备连接到目标 URL 前，测试 VPN 连接至站点的能力。
    - **域操作** - 选择以下选项之一：
        - 需要时连接 - 
        - 从不连接 - 
    - **操作** - 选择以下选项之一：
        - 连接 - 
        - 评估连接 - 
        - 忽略 - 
        - 断开连接 - 


## <a name="proxy-settings"></a>代理设置

- **自动配置脚本** - 使用文件配置代理服务器。 输入包含配置文件的**代理服务器 URL**（例如 **http://proxy.contoso.com**）。
- **地址** - 输入代理服务器地址（作为 IP 地址）。
- **端口号** - 输入与代理服务器关联的端口号。



<!--HONumber=Feb17_HO2-->


