---
title: "适用于 Windows 10 设备的 Intune VPN 设置"
titleSuffix: Intune on Azure
description: "了解可用于在 Windows 10 设备上配置 VPN 连接的 Intune 设置。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 495e4ed6-b2ef-47cc-a110-13fa9b5f85a6
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6f112983a33c1af24d288f19140114084575f36d
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="vpn-settings-for-windows-10-devices-in-microsoft-intune"></a>Microsoft Intune 中适用于 Windows 10 设备的 VPN 设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

根据所选择的设置，下表中并非所有值都可配置。


## <a name="base-vpn-settings"></a>基础 VPN 设置


- **连接名称** - 输入此连接的名称。 最终用户在浏览其设备的可用 VPN 连接列表时将看到此名称。
- **服务器** - 添加设备将连接到的一个或多个 VPN 服务器。
    - **添加** - 打开“添加行”边栏选项卡，可在其中指定以下信息：
        - **说明** - 为服务器指定一个描述性名称，例如“Contoso VPN 服务器”。
        - **IP 地址或 FQDN** - 提供设备将连接到的 VPN 服务器的 IP 地址或完全限定的域名。 示例：**192.168.1.1**、**vpn.contoso.com**。
        - **默认服务器** - 启用此服务器作为设备建立连接时使用的默认服务器。 请确保只将一台服务器设置为默认服务器。
    - **导入** - 在格式描述、IP 地址或 FQDN 以及默认服务器中，浏览到包含以逗号分隔的服务器列表的文件。 选择“确定”，将这些内容导入到“服务器”列表。
    - **导出** - 将服务器列表导出到逗号分隔值 (csv) 文件。

**连接类型** - 从以下供应商列表中选择 VPN 连接类型：
- **Pulse Secure**
- **F5 Edge Client**
- **Dell SonicWALL Mobile Connect**
- **Check Point Capsule VPN**
- **自动**
- **IKEv2**
- **L2TP**
- **PPTP**

**登录组或域**（仅限 Dell SonicWALL Mobile Connect）- 指定要连接到的登录组或域的名称。

**自定义 XML**/**EAP XML** - 指定配置 VPN 连接的任何自定义 XML 命令。

**Pulse Secure 的示例：**

```
    <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**CheckPoint Mobile VPN 的示例：**

```
    <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**Dell SonicWALL Mobile Connect 的示例：**

```
    <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**F5 Edge Client 的示例：**

```
    <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

有关如何编写自定义 XML 命令的详细信息，请参阅每个制造商 VPN 文档。

“拆分隧道” - “启用”或“禁用”，此选项让设备根据流量确定使用哪个连接。 例如，旅馆中的用户使用 VPN 连接来访问工作文件，但使用旅馆的标准网络进行常规的 Web 浏览。
- **为此 VPN 连接分拆隧道路由** - 添加第三方 VPN 供应商的可选路由。 指定每个路由的目标前缀和前缀大小。

## <a name="apps-and-traffic-rules"></a>应用和通信规则

**对这些应用限制 VPN 连接** - 如果只希望指定的应用使用 VPN 连接，则启用此选项。
**关联应用** - 提供将自动使用 VPN 连接的应用列表。 应用类型将确定应用的标识符。 对于通用应用，提供包系列名称。 对于桌面应用，提供应用的文件路径。

>[!IMPORTANT]
>建议保护为配置 per-app VPN 而编制的应用的所有列表。 如果将未授权用户修改的列表导入 per-app VPN 应用列表，你将可能向不应具有访问权限的应用授权 VPN 访问权限。 保护应用列表的方法之一是使用访问控制列表 (ACL)。

**此 VPN 连接的网络通信规则** - 选择将为 VPN 连接启用的协议、本地和远程端口及地址范围。 如果未创建网络通信规则，则会启用所有协议、端口和地址范围。 创建规则后，VPN 连接将仅使用该规则指定的协议、端口和地址范围。


## <a name="conditional-access"></a>条件性访问

**对此 VPN 连接的条件访问** -
**使用备用证书进行单一登录 (SSO)** -
**扩展密钥用法** -
**颁发者哈希** -

## <a name="dns-settings"></a>DNS 设置

**此 VPN 连接的 DNS 名称和服务器** - 建立连接后，选择 VPN 连接将要使用的 DNS 服务器。
对于每个服务器， 指定：
- **DNS 名称**
- **DNS 服务器**
- **代理**

## <a name="proxy-settings"></a>代理设置

- **自动检测代理设置** - 如果 VPN 服务器要求使用代理服务器进行连接，请指定是否希望设备自动检测连接设置。 有关详细信息，请参阅 Windows Server 文档。
- **自动配置脚本** - 使用文件配置代理服务器。 输入包含配置文件的**代理服务器 URL**（例如 **http://proxy.contoso.com**）。
- **使用代理服务器** - 如果想要手动输入代理服务器设置则启用此选项。
    - **地址** - 输入代理服务器地址（作为 IP 地址）。
    - **端口号** - 输入与代理服务器关联的端口号。
- **不对本地地址使用代理服务器** - 如果 VPN 服务器要求使用代理服务器进行连接，在不想对指定的本地地址使用代理服务器时选择此选项。 有关详细信息，请参阅 Windows Server 文档。
