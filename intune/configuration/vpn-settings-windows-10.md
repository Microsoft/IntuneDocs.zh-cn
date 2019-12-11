---
title: Microsoft Intune 中的 Windows 10 VPN 设置 - Azure | Microsoft Docs
description: 了解和浏览 Microsoft Intune 中可用的 VPN 设置、其用途及其执行的操作，包括流量规则、条件性访问，以及适用于 Windows 10 和 Windows Holographic for Business 设备的 DNS 与代理设置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.reviewer: tycast
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 122872eff92a37c8724fd4a853091e51a0a54c66
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506531"
---
# <a name="windows-10-and-windows-holographic-device-settings-to-add-vpn-connections-using-intune"></a>使用 Intune 添加 VPN 连接的 Windows 10 和 Windows Holographic 设备

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

可以使用 Microsoft Intune 为设备添加和配置 VPN 连接。 本文列出和介绍了创建虚拟专用网络 (VPN) 时常用的设置和功能。 这些 VPN 设置和功能可在推送或部署到设备的 Intune 中的设备配置文件中使用。

作为移动设备管理 (MDM) 解决方案的一部分，使用这些设置允许或禁用的功能包括使用 VPN 供应商、启用 Always On、使用 DNS、添加代理等。

这些设置适用于运行以下系统的设备：

- Windows 10
- Windows Holographic for Business

并非所有值都可配置（具体取决于所选设置）。

## <a name="before-you-begin"></a>开始之前

[创建VPN 设备配置文件](vpn-settings-configure.md)。

## <a name="base-vpn-settings"></a>基础 VPN 设置

- **连接名称**：输入此连接的名称。 最终用户在浏览其设备的可用 VPN 连接列表时将看到此名称。
- **服务器**：添加设备连接到的一个或多个 VPN 服务器。 添加服务器时，输入以下信息：
  - **说明**：为服务器输入一个描述性名称，例如“Contoso VPN 服务器” 
  - **IP 地址或 FQDN**：输入设备连接到的 VPN 服务器的 IP 地址或完全限定的域名 (FQDN)，例如“192.168.1.1”或“vpn.contoso.com”  
  - **默认服务器**：启用此服务器作为设备建立连接时使用的默认服务器。 只将一台服务器设置为默认服务器。
  - **导入**：浏览到以逗号分隔的文件，该文件包含采用以下格式的服务器列表：描述、IP 地址或 FQDN、默认服务器。 选择“确定”，将这些服务器导入到“服务器”列表   。
  - **导出**：将服务器列表导出到逗号分隔值 (csv) 文件

- **向内部 DNS 注册 IP 地址**：选择“启用”  ，将 Windows 10 VPN 配置文件配置为向内部 DNS 动态注册分配给 VPN 接口的 IP 地址。 选择“禁用”以免动态注册 IP 地址  。

- **连接类型**：从以下供应商列表中选择 VPN 连接类型：

  - **Pulse Secure**
  - **F5 Edge Client**
  - **SonicWALL Mobile Connect**
  - **Check Point Capsule VPN**
  - **Citrix**
  - **帕洛阿尔托网络全局保护**
  - **自动**
  - **IKEv2**
  - **L2TP**
  - **PPTP**

  选择 VPN 连接类型时，还可能要求你进行以下设置：  
  - **Always On**：选择“启用”可在发生下列情况时自动连接到 VPN 连接  ： 
    - 用户登录其设备
    - 设备上的网络发生更改
    - 设备屏幕在关闭后重新打开 

  -  身份验证方法：选择希望用户如何向 VPN 服务器进行身份验证。 使用证书可提供增强的功能，如“零接触”体验、按需 VPN 和按应用 VPN  。
  -  每次登录时记住凭据：选择缓存身份验证凭据。
  -  自定义 XML：输入配置 VPN 连接的任何自定义 XML 命令。
  -  EAP Xml：输入配置 VPN 连接的任何 EAP XML 命令

### <a name="pulse-secure-example"></a>Pulse Secure 示例

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

### <a name="f5-edge-client-example"></a>F5 Edge Client 示例

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

### <a name="sonicwall-mobile-connect-example"></a>SonicWALL Mobile Connect 示例
 登录组或域：无法在 VPN 配置文件中设置此属性。 相反，如果用户名和域是以 `username@domain` 或 `DOMAIN\username` 格式输入的，则 Mobile Connect 会分析此值。

例如：

```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

### <a name="checkpoint-mobile-vpn-example"></a>CheckPoint Mobile VPN 示例

```
<CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

### <a name="writing-custom-xml"></a>编写自定义 XML
有关编写自定义 XML 的详细信息，请参阅各制造商的 VPN 文档。

有关创建自定义 EAP XML 的详细信息，请参阅 [EAP configuration](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration)（EAP 配置）。

## <a name="apps-and-traffic-rules"></a>应用和通信规则

-  将 WIP 或应用与此 VPN 相关联：如果只希望某些应用使用 VPN 连接，则启用此设置。 选项包括：

  -  将 WIP 与此连接相关联：为此连接输入 WIP 域。 
  -  将应用与此连接相关联：可以将 VPN 连接限制到这些应用  ，然后添加“关联应用”  。 输入的应用会自动使用 VPN 连接。 应用的类型决定应用的标识符。 对于通用应用，输入包系列名称。 对于桌面应用，输入应用的文件路径。
  >[!IMPORTANT]
  >建议保护为每应用 VPN 创建的所有应用列表。 如果未经授权的用户更改了此列表，而你将其导入每应用 VPN 的应用列表中，则可能会向不应具有访问权限的应用授予 VPN 访问权限。 一种保护应用列表的方法是使用访问控制列表 (ACL)。

- **此 VPN 连接的网络通信规则**：选择为 VPN 连接启用的协议、本地和远程端口及地址范围。 如果未创建网络通信规则，则会启用所有协议、端口和地址范围。 创建规则后，VPN 连接仅使用在该规则中输入的协议、端口和地址范围。

## <a name="conditional-access"></a>条件性访问

- **此 VPN 连接的条件性访问**：从客户端启用设备符合性流。 启用后，VPN 客户端与 Azure Active Directory（AD）通信以获取用于身份验证的证书。 VPN 应设置为使用证书进行身份验证，并且 VPN 服务器必须信任由 Azure AD 返回的服务器。

- **使用替代证书进行单一登录 (SSO)** ：为验证设备符合性，可使用除 VPN 身份验证证书以外的其他证书来进行 Kerberos 身份验证。 使用以下设置输入证书：

  -  名称：扩展密钥用法 (EKU) 的名称
  - **对象标识符**：EKU 的对象标识符
  - **颁发者哈希**：SSO 证书的指纹

## <a name="dns-settings"></a>DNS 设置

- **DNS 后缀搜索列表**：在“DNS 后缀”中，输入 DNS 后缀，然后单击“添加”   。 可以添加多个后缀。

  使用 DNS 后缀时，可以使用其短名称而不是完全限定的域名 (FQDN) 搜索网络资源。 在使用短名称进行搜索时，后缀由 DNS 服务器自动确定。 例如，`utah.contoso.com` 位于 DNS 后缀列表中。 对 `DEV-comp` 执行 Ping 操作。 在本方案中，它解析为 `DEV-comp.utah.contoso.com`。

  DNS 后缀按列出的顺序解析，并且可以更改顺序。 例如，`colorado.contoso.com` 和 `utah.contoso.com` 位于 DNS 后缀列表中，并且都具有名为 `DEV-comp` 的资源。 由于 `colorado.contoso.com` 在列表中排第一，因此它解析为 `DEV-comp.colorado.contoso.com`。
  
  要更改顺序，请单击 DNS 后缀左侧的点，然后将后缀拖到顶部：

  ![选择三个点，然后单击并拖动以移动 DNS 后缀](./media/vpn-settings-windows-10/vpn-settings-windows10-move-dns-suffix.png)

- **名称解析策略表（nrpt）规则**：名称解析策略表（nrpt）规则定义在连接到 VPN 时 DNS 解析名称的方式。 创建 VPN 连接后，可以选择 VPN 连接将要使用的 DNS 服务器。

  可向包括域、DNS 服务器、代理和其他详细信息的表添加规则，以解析输入的域。 当用户连接到你输入的域时，VPN 连接将使用这些规则。

  选择“添加”以添加新规则  。 对于每个服务器，输入：

  - **域**：输入完全限定的域名 (FQDN) 或 DNS 后缀，应用规则。 此外，还可以在 DNS 后缀的开头输入句点 (.)。 例如，输入 `contoso.com` 或 `.allcontososubdomains.com`。
  - **DNS 服务器**：输入可解析域的 IP 地址或 DNS 服务器。 例如，输入 `10.0.0.3` 或 `vpn.contoso.com`。
  - **代理**：输入可解析域的 Web 代理服务器。 例如，输入 `http://proxy.com`。
  - **自动连接**：如果为“已启用”，则当设备连接到输入的域（如 `contoso.com`）时，会自动连接到 VPN  。 如果为“未配置”（默认），则设备不会自动连接到 VPN 
  - **持续**：如果设置为“已启用”，规则将保持在名称解析策略表 (NRPT) 中，直到从设备中手动删除该规则，甚至是 VPN 断开连接后  。 如果设置为“未配置”（默认），VPN 断开连接时将从设备中删除 VPN 配置文件中的 NRPT 规则  。

## <a name="proxy-settings"></a>代理设置

- **自动配置脚本**：使用文件配置代理服务器。 输入包含配置文件的代理服务器 URL，例如 `http://proxy.contoso.com`  。
-  地址：输入代理服务器地址，例如 IP 地址或 `vpn.contoso.com`
-  端口号：输入代理服务器使用的 TCP 端口号
-  绕过本地地址代理：如果你不想为本地地址使用代理服务器，请选择“启用”。 如果 VPN 服务器需要代理服务器进行连接，则此设置适用。

## <a name="split-tunneling"></a>拆分隧道

- **拆分隧道**：启用或禁用此设置，让设备根据流量确定使用哪个连接   。 例如，旅馆中的用户使用 VPN 连接访问工作文件，但使用旅馆的标准网络进行常规的 Web 浏览。
- **为此 VPN 连接拆分隧道路由**：添加第三方 VPN 供应商的可选路由。 输入每个连接的目标前缀和前缀大小。

## <a name="trusted-network-detection"></a>受信任的网络检测

**受信任的网络 DNS 后缀**：如果用户已连接到受信任的网络，可阻止设备自动连接到其他 VPN 连接。

在“DNS 后缀”中，输入要信任的 DNS 后缀（例如，contoso.com），并选择“添加”   。 可以添加所需数目的后缀。

如果用户连接到列表中的 DNS 后缀，则用户不会自动连接到其他 VPN 连接。 用户可以继续使用你所输入的受信任的 DNS 后缀列表。 即使设置了任何自动触发，仍将使用受信任的网络。

例如，如果用户已连接到受信任的 DNS 后缀，则会忽略以下自动触发。 具体而言，列表中的 DNS 后缀将取消其他所有连接自动触发，包括：

- Always On
- 基于应用的触发器
- DNS 自动触发器

## <a name="next-steps"></a>后续步骤

配置文件已创建，但它尚未起到任何作用。 下一步，[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

在 [Android](vpn-settings-android.md)、[iOS](vpn-settings-ios.md) 和 [macOS](vpn-settings-macos.md) 设备上配置 VPN 设置。
