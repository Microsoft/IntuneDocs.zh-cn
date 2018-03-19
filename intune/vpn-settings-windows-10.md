---
title: "在 Microsoft Intune 中查看 VPN 设置 - Azure | Microsoft Docs"
description: "了解和浏览 Microsoft Intune 中可用的 VPN 设置、其用途及其执行的操作，包括流量规则、条件性访问，以及适用于 Windows 10 设备和 Windows Holographic for Business 设备的 DNS 与代理设置。"
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/8/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.reviewer: tycast
ms.custom: intune-azure
ms.openlocfilehash: 1c1ed2946782f92313aacec05a65a80b2704ddaa
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2018
---
# <a name="read-about-the-vpn-settings-in-intune"></a>了解 Intune 中的 VPN 设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

可使用 Intune 配置 VPN 连接。 本文介绍这些设置、流量规则、条件性访问和 DNS 与代理设置。

这些设置适用于：

- 运行 Windows 10 的设备
- 运行 Windows Holographic for Business 的设备

并非所有值都可配置（具体取决于所选设置）。

## <a name="base-vpn-settings"></a>基础 VPN 设置

- **连接名称**：输入此连接的名称。 最终用户在浏览其设备的可用 VPN 连接列表时将看到此名称。
- **服务器**：添加设备连接到的一个或多个 VPN 服务器。
  - **添加**：打开“添加行”，在其中输入以下信息：
    - **说明**：为服务器输入一个描述性名称，例如“Contoso VPN 服务器”
    - **IP 地址或 FQDN**：输入设备连接到的 VPN 服务器的 IP 地址或完全限定的域名，例如“192.168.1.1”或“vpn.contoso.com”
    - **默认服务器**：启用此服务器作为设备建立连接时使用的默认服务器。 只将一台服务器设置为默认服务器。
  - **导入**：浏览到按以下格式包含服务器列表的逗号分隔文件：描述、IP 地址或 FQDN、默认服务器。 选择“确定”，将这些服务器导入到“服务器”列表。
  - **导出**：将服务器列表导出到逗号分隔值 (csv) 文件

**连接类型**：从以下供应商列表中选择 VPN 连接类型：

- **自动**
- **Check Point Capsule VPN**
- **Citrix VPN**
- **SonicWALL Mobile Connect**
-  **F5 Edge Client**
- **IKEv2**
- **L2TP**
- **PPTP**
- **Pulse Secure**

**登录组或域**（仅限 SonicWALL Mobile Connect）：无法在 VPN 配置文件中设置此属性。 相反，如果用户名和域是以 `username@domain` 或 `DOMAIN\username` 格式输入的，则 Mobile Connect 会分析此值。

**自定义 XML**/**EAP XML**：输入配置 VPN 连接的任何自定义 XML 命令。

**Pulse Secure 的示例：**

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**CheckPoint Mobile VPN 的示例：**

```
<CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**SonicWALL Mobile Connect 的示例：**

```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**F5 Edge Client 的示例：**

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

有关编写自定义 XML 的详细信息，请参阅各制造商的 VPN 文档。

有关创建自定义 EAP XML 的详细信息，请参阅 [EAP configuration](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration)（EAP 配置）。

**拆分隧道**：启用或禁用此设置，让设备根据流量确定使用哪个连接。 例如，旅馆中的用户使用 VPN 连接访问工作文件，但使用旅馆的标准网络进行常规的 Web 浏览。
- **为此 VPN 连接拆分隧道路由**：添加第三方 VPN 供应商的可选路由。 输入每个路由的目标前缀和前缀大小。

## <a name="apps-and-traffic-rules"></a>应用和通信规则

**对这些应用限制 VPN 连接**：如果只希望某些应用使用 VPN 连接，则启用此设置。
**关联应用**：输入自动使用 VPN 连接的应用列表。 应用的类型决定应用的标识符。 对于通用应用，输入包系列名称。 对于桌面应用，输入应用的文件路径。

>[!IMPORTANT]
>建议保护为每应用 VPN 创建的所有应用列表。 如果未经授权的用户更改了此列表，而你将其导入每应用 VPN 的应用列表中，则可能会向不应具有访问权限的应用授予 VPN 访问权限。 一种保护应用列表的方法是使用访问控制列表 (ACL)。

**此 VPN 连接的网络通信规则**：选择为 VPN 连接启用的协议、本地和远程端口及地址范围。 如果未创建网络通信规则，则会启用所有协议、端口和地址范围。 创建规则后，VPN 连接仅使用在该规则中输入的协议、端口和地址范围。

## <a name="conditional-access"></a>条件性访问

**此 VPN 连接的条件性访问**：从客户端启用设备符合性流。 如果启用，VPN 客户端会尝试与 Azure Active Directory 进行通信，以获取用于身份验证的证书。 VPN 应设置为使用证书进行身份验证，并且 VPN 服务器必须信任由 Azure Active Directory 返回的服务器。

**使用替代证书进行单一登录 (SSO)**：为验证设备符合性，可使用除 VPN 身份验证证书以外的其他证书来进行 Kerberos 身份验证。 使用以下设置输入证书：

- **扩展密钥用法**：扩展密钥用法 (EKU) 的名称
- **对象标识符**：EKU 的对象标识符
- **颁发者哈希**：SSO 证书的指纹

## <a name="dns-settings"></a>DNS 设置

**此 VPN 连接的 DNS 名称和服务器**：建立连接后，选择 VPN 连接使用的 DNS 服务器。
对于每个服务器，输入：
- **DNS 名称**
- **DNS 服务器**
- **代理**

## <a name="proxy-settings"></a>代理设置

- **自动检测代理设置**：如果 VPN 服务器要求使用代理服务器进行连接，请选择是否希望设备自动检测连接设置。
- **自动配置脚本**：使用文件配置代理服务器。 输入包含配置文件的代理服务器 URL，例如 `http://proxy.contoso.com`。
- **使用代理服务器**：启用此选项即可手动输入代理服务器设置。
  - **地址**：输入代理服务器地址（作为 IP 地址）
  - **端口号**：输入与代理服务器关联的端口号
- **不对本地地址使用代理服务器**：如果 VPN 服务器要求使用代理服务器进行连接，在不想对输入的本地地址使用代理服务器时选择此设置。
