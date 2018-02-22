---
title: "适用于 Windows 10 设备的 Intune VPN 设置"
titlesuffix: Azure portal
description: "了解可用于在 Windows 10 设备上配置 VPN 连接的 Intune 设置。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 1/26/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d126853051bb4a6c2f1ea6fbd54195ae06254b51
ms.sourcegitcommit: 2c7794848777e73d6a9502b4e1000f0b07ac96bc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2018
---
# <a name="vpn-settings-for-windows-10-devices-in-microsoft-intune"></a>Microsoft Intune 中适用于 Windows 10 设备的 VPN 设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

下表中并非所有值都可配置，具体取决于所选择的设置。

> [!NOTE]
> 这些设置也适用于运行 Windows Holographic for Business 的设备。


## <a name="base-vpn-settings"></a>基础 VPN 设置


- **连接名称** - 输入此连接的名称。 最终用户在浏览其设备的可用 VPN 连接列表时将看到此名称。
- **服务器** - 添加设备连接到的一个或多个 VPN 服务器。
    - **添加** - 打开“添加行”边栏选项卡，可在其中指定以下信息：
        - **说明** - 为服务器指定一个描述性名称，例如“Contoso VPN 服务器”。
        - IP 地址或 FQDN - 提供设备连接到的 VPN 服务器的 IP 地址或完全限定的域名。 示例：**192.168.1.1**、**vpn.contoso.com**。
        - **默认服务器** - 启用此服务器作为设备建立连接时使用的默认服务器。 请确保只将一台服务器设置为默认服务器。
    - **导入** - 在格式描述、IP 地址或 FQDN 以及默认服务器中，浏览到包含以逗号分隔的服务器列表的文件。 选择“确定”，将这些内容导入到“服务器”列表。
    - **导出** - 将服务器列表导出到逗号分隔值 (csv) 文件。

**连接类型** - 从以下供应商列表中选择 VPN 连接类型：
- **自动**
- **Check Point Capsule VPN**
- **Citrix VPN**
- **Dell SonicWALL Mobile Connect**
- **F5 Edge Client**
- **IKEv2**
- **L2TP**
- **PPTP**
- **Pulse Secure**


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

有关编写自定义 XML 的详细信息，请参阅各制造商的 VPN 文档。

有关创建自定义 EAP XML 的详细信息，请参阅 [EAP configuration](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration)（EAP 配置）。

“拆分隧道” - “启用”或“禁用”，此选项让设备根据流量确定使用哪个连接。 例如，旅馆中的用户使用 VPN 连接来访问工作文件，但使用旅馆的标准网络进行常规的 Web 浏览。
- **为此 VPN 连接分拆隧道路由** - 添加第三方 VPN 供应商的可选路由。 指定每个路由的目标前缀和前缀大小。

## <a name="apps-and-traffic-rules"></a>应用和通信规则

**对这些应用限制 VPN 连接** - 如果只希望指定的应用使用 VPN 连接，则启用此选项。
**关联应用** - 提供自动使用 VPN 连接的应用列表。 应用的类型决定应用的标识符。 对于通用应用，提供包系列名称。 对于桌面应用，提供应用的文件路径。

>[!IMPORTANT]
>建议保护为配置 per-app VPN 而编制的应用的所有列表。 如果未经授权的用户修改了列表，而你将此列表导入每应用 VPN 的应用列表中，则可能会向不应具有访问权限的应用授予 VPN 访问权限。 保护应用列表的方法之一是使用访问控制列表 (ACL)。

**此 VPN 连接的网络通信规则** - 选择为 VPN 连接启用的协议、本地和远程端口及地址范围。 如果未创建网络通信规则，则会启用所有协议、端口和地址范围。 创建规则后，VPN 连接将仅使用该规则指定的协议、端口和地址范围。


## <a name="conditional-access"></a>条件性访问

此 VPN 连接的条件性访问 - 从客户端启用设备符合性流。 如果启用，VPN 客户端会尝试与 Azure Active Directory 进行通信，以获取用于身份验证的证书。 VPN 应设置为使用证书进行身份验证，并且 VPN 服务器必须信任由 Azure Active Directory 返回的服务器。

使用替代证书进行单一登录 (SSO) - 为验证设备符合性，可使用除 VPN 身份验证证书以外的其他证书来进行 Kerberos 身份验证。 使用以下设置指定证书： 

- 扩展密钥用法 - 扩展密钥用法 (EKU) 的名称。
- 对象标识符 - EKU 的对象标识符。
- 颁发者哈希 - SSO 证书的指纹。

## <a name="dns-settings"></a>DNS 设置

**此 VPN 连接的 DNS 名称和服务器** - 建立连接后，选择 VPN 连接将要使用的 DNS 服务器。
对于每个服务器， 指定：
- **DNS 名称**
- **DNS 服务器**
- **代理**

## <a name="proxy-settings"></a>代理设置

- **自动检测代理设置** - 如果 VPN 服务器要求使用代理服务器进行连接，请指定是否希望设备自动检测连接设置。 有关详细信息，请参阅 Windows Server 文档。
- **自动配置脚本** - 使用文件配置代理服务器。 输入包含配置文件的代理服务器 URL（例如 **http://proxy.contoso.com）。
- **使用代理服务器** - 如果想要手动输入代理服务器设置则启用此选项。
    - **地址** - 输入代理服务器地址（作为 IP 地址）。
    - **端口号** - 输入与代理服务器关联的端口号。
- **不对本地地址使用代理服务器** - 如果 VPN 服务器要求使用代理服务器进行连接，在不想对指定的本地地址使用代理服务器时选择此选项。 有关详细信息，请参阅 Windows Server 文档。
