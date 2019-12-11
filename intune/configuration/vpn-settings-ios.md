---
title: 在 Microsoft Intune 中配置 iOS 设备的 VPN 设置 - Azure | Microsoft Docs
description: 使用虚拟专用网络 (VPN) 配置设置添加或创建 VPN 配置配置文件，包括基本设置中的连接详细信息、身份验证方法和拆分隧道；具有标识符的自定义 VPN 设置和键值对；包括 Safari URL 的每应用 VPN 设置和具有 SSID 或 DNS 搜索域的按需 VPN；以及代理设置，包括配置脚本、IP 或 FQDN 地址和 TCP 端口。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/13/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e45d51feb91e0e188971133185ac0f0f13e5b1f4
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74781135"
---
# <a name="add-vpn-settings-on-ios-devices-in-microsoft-intune"></a>在 Microsoft Intune 中为 iOS 设备添加 VPN 设置

Microsoft Intune 包含许多可以部署到 iOS 设备的 VPN 设置。 可使用这些设置创建和配置组织网络的 VPN 连接。 本文将说明这些设置。 某些设置仅适用于某些 VPN 客户端，例如 Citrix、Zscaler 等。

## <a name="before-you-begin"></a>开始之前

[创建设备配置文件](vpn-settings-configure.md)。

> [!NOTE]
> 这些设置适用于所有注册类型。 有关注册类型的详细信息，请参阅[iOS 注册](../enrollment/ios-enroll.md)。

## <a name="connection-type"></a>连接类型

从以下供应商列表中选择 VPN 连接类型：

- **Check Point Capsule VPN**
- **Cisco 旧式 AnyConnect**：适用于 [Cisco 旧式 AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924) 应用版本 4.0.5x 以及较早版本。
- **Cisco AnyConnect**：适用于 [Cisco AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690) 应用版本 4.0.7x 以及更高版本。
- **SonicWall Mobile Connect**
- **F5 Access 旧版**：适用于 F5 Access 应用版本 2.1 及较早版本。
- **F5 Access**：适用于 F5 Access 应用版本 3.0 及更高版本。
- **Palo Alto 网络全局保护(旧版)** ：适用于 Palo Alto 网络全局保护应用版本 4.1 及较早版本。
- **Palo Alto 网络全局保护**：适用于 Palo Alto 网络全局保护应用版本 5.0 及更高版本。
- **Pulse Secure**
- **Cisco (IPSec)**
- **Citrix VPN**
- **Citrix SSO**
- **Zscaler**：若要使用条件访问，或允许用户绕过 Zscaler 登录屏幕，必须将 Zscaler Private Access (ZPA) 与 Azure AD 帐户集成。 有关详细步骤，请参阅 [Zscaler 文档](https://help.zscaler.com/zpa/configuration-example-microsoft-azure-ad)。 
- **Ikev2**： [ikev2 设置](#ikev2-settings)（在本文中）介绍属性。
- **自定义 VPN**

> [!NOTE]
> Cisco、Citrix、F5 和 Palo Alto 已宣布，其旧版客户端在 iOS 12 上无法正常运行。 应尽快迁移到新应用。 有关详细信息，请参阅 [Microsoft Intune 支持团队博客](https://go.microsoft.com/fwlink/?linkid=2013806&clcid=0x409)。

## <a name="base-vpn-settings"></a>基础 VPN 设置

以下列表中显示的设置由所选的 VPN 连接类型决定。  

- **连接名称**：最终用户在浏览其设备的可用 VPN 连接列表时将看到此名称。
- **自定义域名**（仅限 Zscaler）：使用用户所属的域预填充 Zscaler 应用的登录字段。 例如，如果用户名为 `Joe@contoso.net`，则应用打开时，`contoso.net` 域将静态显示在字段中。 如果未键入域名，则使用 Azure Active Directory (AD) 中的 UPN 的域部分。
- **IP 地址或 FQDN**：设备连接到的 VPN 服务器的 IP 地址或完全限定的域名 (FQDN)。 例如，输入 `192.168.1.1` 或 `vpn.contoso.com`。
- **组织的云名称（仅限 Zscaler）** ：键入在其中预配组织的云的名称。 用于登录 Zscaler 的 URL 包含此名称。  
- **身份验证方法**：选择设备向 VPN 服务器进行身份验证的方法。 
  - “证书”  ：在“身份验证证书”  下，选择现有 SCEP 或 PKCS 证书配置文件以对连接进行身份验证。 [配置证书](../protect/certificates-configure.md)提供了有关证书配置文件的一些指导。
  - **用户名和密码**：最终用户必须输入用户名和密码才能登录 VPN 服务器。  

    > [!NOTE]
    > 如果用户名和密码被用作 Cisco IPsec VPN 的身份验证方法，则它们必须通过自定义 Apple 配置器配置文件来提供 SharedSecret。

  - **派生凭据**：使用从用户的智能卡派生的证书。 如果未配置任何派生凭据颁发者，Intune 会提示你添加一个。 有关详细信息，请参阅[在 Microsoft Intune 中使用派生凭据](../protect/derived-credentials.md)。

- **排除的 URL**（仅限 Zscaler）：连接到 Zscaler VPN 时，可从 Zscaler 云外部访问列出的 URL。 

- **拆分隧道**：启用或禁用此设置，让设备根据流量确定使用哪个连接   。 例如，旅馆中的用户使用 VPN 连接访问工作文件，但使用旅馆的标准网络进行常规的 Web 浏览。

- **VPN 标识符**（自定义 VPN、Zscaler 和 Citrix）：所用 VPN 应用的标识符，由 VPN 提供商提供。
  - **输入组织的自定义 VPN 属性的键/值对**：添加或导入用于自定义 VPN 连接的“键”和“值”   。 请记住，这些值通常由 VPN 提供商提供。

- **启用网络访问控制 (NAC)** （Citrix SSO、F5 Access）：选择“我同意”后，设备 ID 将包含在 VPN 配置文件中  。 此 ID 可用于对 VPN 进行身份验证以允许或阻止网络访问。

  使用 F5 Access 时，请务必  ：

  - 确认所使用的是 F5 BIG-IP 13.1.1.5。 BIG-IP 14 不受支持。
  - 将 BIG-IP 与 Intune for NAC 集成。 请参阅[概述：使用终结点管理系统配置 APM 以进行设备状态检查](https://support.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html#guid-0bd12e12-8107-40ec-979d-c44779a8cc89) F5 指南。
  - 在 VPN 配置文件中启用 NAC。

  将 Citrix SSO 与 Gateway 配合使用时  ，请务必：

  - 确认使用的是 Citrix Gateway 12.0.59 或更高版本。
  - 确认你的用户已在其设备上安装 Citrix SSO 1.1.6 或更高版本。
  - 将 Citrix 网关与 Intune for NAC 集成。 请参阅 [Integrating Microsoft Intune/Enterprise Mobility Suite with NetScaler (LDAP+OTP Scenario)](https://www.citrix.com/content/dam/citrix/en_us/documents/guide/integrating-microsoft-intune-enterprise-mobility-suite-with-netscaler.pdf) Citrix 部署指南（将 Microsoft Intune/Enterprise Mobility Suite 与 NetScaler（LDAP+OTP 方案）集成）。
  - 在 VPN 配置文件中启用 NAC。

  **重要详细信息**：  

  - 启用 NAC 后，VPN 将每隔 24 小时断开一次连接。 可以立即重新连接 VPN。
  - 设备 ID 是配置文件的一部分，但不显示在 Intune 中。 Microsoft 不会将此 ID 存储在任何位置，也不会由 Microsoft 共享。

  对于支持设备 ID 的 VPN 合作伙伴，VPN 客户端（如 Citrix SSO）可以获取 ID。 然后，它可以查询 Intune 以确认该设备是否已注册，以及 VPN 配置文件是否符合要求。

  - 要删除此设置，请重新创建配置文件，不要选择“我同意”  。 然后，重新分配配置文件。

## <a name="ikev2-settings"></a>IKEv2 设置

选择**连接类型** > **IKEv2**时，将应用这些设置。

- **远程标识符**：输入 IKEv2 服务器的网络 IP 地址、FQDN、USERFQDN 或 ASN1DN。 例如，输入 `10.0.0.3` 或 `vpn.contoso.com`。 通常，输入与[**连接名称**](#base-vpn-settings)相同的值（在本文中）。 但它确实依赖于 IKEv2 服务器设置。

- **客户端身份验证类型**：选择 vpn 客户端向 vpn 进行身份验证的方式。 选项包括：
  - **用户身份验证**（默认值）：向 VPN 验证用户凭据。
  - **计算机身份验证**：设备凭据对 VPN 进行身份验证。

- **身份验证方法**：选择要发送到服务器的客户端凭据的类型。 选项包括：
  - **证书**：使用现有的证书配置文件对 VPN 进行身份验证。 请确保已将此证书配置文件分配给用户或设备。 否则，VPN 连接会失败。
    - **证书类型**：选择证书使用的加密类型。 确保将 VPN 服务器配置为接受此类证书。 选项包括：
      - **RSA** （默认值）
      - **ECDSA256**
      - **ECDSA384**
      - **ECDSA521**

  - **用户名和密码**（仅限用户身份验证）：当用户连接到 VPN 时，系统将提示他们输入用户名和密码。
  - **共享机密**（仅限计算机身份验证）：允许你输入共享机密以发送到 VPN 服务器。
    - **共享机密**：输入共享机密，也称为预共享密钥（PSK）。 请确保该值与 VPN 服务器上配置的共享机密相匹配。

- **服务器证书颁发者公用名**：允许 vpn 服务器向 vpn 客户端进行身份验证。 输入发送到设备上的 VPN 客户端的 VPN 服务器证书的证书颁发者公用名（CN）。 请确保 CN 值与 VPN 服务器上的配置相匹配。 否则，VPN 连接会失败。
- **服务器证书公用名**：输入证书本身的 CN。 如果留空，则使用远程标识符值。

- **死对等方检测率**：选择 vpn 客户端检查 vpn 隧道是否处于活动状态的频率。 选项包括：
  - **未配置**：使用 iOS 系统默认值，这可能与选择 "**中**" 相同。
  - **None**：禁用死对等检测。
  - **Low**：每隔30分钟发送一条 keepalive 消息。
  - **中**（默认）：每10分钟发送一次 keepalive 消息。
  - **High**：每60秒发送一条 keepalive 消息。

- **TLS 版本最小值**：输入要使用的最低 tls 版本。 输入 `1.0`、`1.1`或 `1.2`。 如果留空，则使用 `1.0` 的默认值。
- **Tls 版本范围最大值**：输入要使用的最大 tls 版本。 输入 `1.0`、`1.1`或 `1.2`。 如果留空，则使用 `1.2` 的默认值。
- **完全向前保密**：选择 "**启用**" 以启用 "完全向前保密（PFS）"。 PFS 是一项 IP 安全功能，可降低会话密钥泄露时的影响。 **Disable** （默认值）不使用 PFS。
- **证书吊销检查**：选择 "**启用**" 以确保在允许 VPN 连接成功之前证书未被吊销。 这项检查最为重要。 如果 VPN 服务器在确定证书是否已吊销之前超时，则授予访问权限。 **禁用**（默认）不检查吊销的证书。

- **配置安全关联参数**： "**未配置**" （默认）使用 iOS 系统默认值。 选择 "**启用**" 以输入在与 VPN 服务器建立安全关联时使用的参数：
  - **加密算法**：选择所需算法：
    - DES
    - 3DES
    - AES 128
    - AES-256 （默认值）
    - AES-128-GCM
    - AES-256-GCM
  - **完整性算法**：选择所需算法：
    - SHA1-96
    - SHA1-160
    - SHA2-256 （默认值）
    - SHA2-384
    - SHA2-512
  - **Diffie-hellman 组**：选择所需的组。 默认值为组 `2`。
  - **生存期**（分钟）：选择安全关联保持活动状态的时间，直到密钥旋转。 输入 `10` 和 `1440` 之间的一个整数值（1440分钟为24小时）。 默认值为 `1440`。

- **为子安全关联配置单独的参数集**： iOS 允许你为 IKE 连接和任何子连接配置单独的参数。 

  "**未配置**" （默认值）使用在前面的 "**配置安全关联参数**" 设置中输入的值。 选择 "**启用**" 以输入在与 VPN 服务器建立*子*安全关联时使用的参数：
  - **加密算法**：选择所需算法：
    - DES
    - 3DES
    - AES 128
    - AES-256 （默认值）
    - AES-128-GCM
    - AES-256-GCM
  - **完整性算法**：选择所需算法：
    - SHA1-96
    - SHA1-160
    - SHA2-256 （默认值）
    - SHA2-384
    - SHA2-512
  - **Diffie-hellman 组**：选择所需的组。 默认值为组 `2`。
  - **生存期**（分钟）：选择安全关联保持活动状态的时间，直到密钥旋转。 输入 `10` 和 `1440` 之间的一个整数值（1440分钟为24小时）。 默认值为 `1440`。

## <a name="automatic-vpn-settings"></a>自动 VPN 设置

- **每应用 VPN**：启用每应用 VPN。 允许 VPN 连接在打开某些应用时自动触发。 还可以将应用与此 VPN 配置文件相关联。 IKEv2 上不支持按应用的 VPN。 有关详细信息，请参阅[为 iOS 设置每应用 VPN 的说明](vpn-setting-configure-per-app.md)。 
  - **提供程序类型**：仅适用于 Pulse Secure 和自定义 VPN。
  - 在结合使用 iOS 每应用 VPN 配置文件和 Pulse Secure 或自定义 VPN 时，选择使用应用层隧道（应用-代理）或数据包级别隧道（数据包-隧道）  。 针对应用层隧道，将 ProviderType 值设置为 app-proxy，针对数据包层隧道，将其设置为 packet-tunnel    。 如果不确定使用哪个值，请查阅 VPN 提供商的文档。
  - **将触发此 VPN 的 Safari URL**：添加一个或多个网站 URL。 使用设备上的 Safari 浏览器访问这些 URL 时，将自动建立 VPN 连接。

- **按需 VPN**：配置用于控制何时启动 VPN 连接的条件规则。 例如，创建一个条件，仅在设备未连接到公司 Wi-fi 网络时才使用 VPN 连接。 或者创建条件。 例如，如果设备无法访问输入的 DNS 搜索域，则不启动 VPN 连接。

  - **SSID 或 DNS 搜索域**：选择此条件将使用无线网络“SSID”还是“DNS 搜索域”   。 选择“添加”以配置一个或多个 SSID 或搜索域  。
  - **URL 字符串探测**：可选。 输入规则用作测试的 URL。 如果设备在不重定向的情况下访问此 URL，则会启动 VPN 连接。 并且，设备会连接到目标 URL。 用户看不到该 URL 字符串探测站点。

    例如，URL 字符串探测是一个审核 Web 服务器 URL，用于在连接 VPN 前检查设备的符合性。 或者，该 URL 通过 VPN 在将设备连接到目标 URL 前，测试 VPN 连接到站点的能力。
.
  - **域操作**：选择以下项之一：
    - 需要时连接
    - 从不连接
  - **操作**：选择以下项之一：
    - 连接
    - 评估连接
    - 忽略
    - 断开连接

## <a name="proxy-settings"></a>代理设置

如果使用代理，请配置以下设置。 代理设置不可用于 Zscaler VPN 连接。  

- **自动配置脚本**：使用文件配置代理服务器。 输入包含配置文件的代理服务器 URL（例如 `http://proxy.contoso.com`）  。
- **地址**：输入代理服务器的完全限定的主机名的 IP 地址。
- **端口号**：输入与代理服务器关联的端口号。

## <a name="next-steps"></a>后续步骤

配置文件已创建，但它尚未起到任何作用。 下一步，[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

在[android](vpn-settings-android.md)、 [android Enterprise](vpn-settings-android-enterprise.md)、 [macOS](vpn-settings-macos.md)和[Windows 10](vpn-settings-windows-10.md)设备上配置 VPN 设置。
