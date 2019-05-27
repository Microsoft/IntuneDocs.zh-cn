---
title: 在 Microsoft Intune 中向 iOS 设备添加 VPN 设置 - Azure | Microsoft Docs
description: 使用虚拟专用网络 (VPN) 配置设置添加或创建 VPN 配置配置文件，包括基本设置中的连接详细信息、身份验证方法和拆分隧道；具有标识符的自定义 VPN 设置和键值对；包括 Safari URL 的每应用 VPN 设置和具有 SSID 或 DNS 搜索域的按需 VPN；以及代理设置，包括配置脚本、IP 或 FQDN 地址和 TCP 端口。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: eb7ff33384b86267e007e986737eeea6b8d3203e
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2019
ms.locfileid: "66040123"
---
# <a name="configure-vpn-settings-on-ios-devices-in-microsoft-intune"></a>在 Microsoft Intune 中为 iOS 设备配置 VPN 设置

Microsoft Intune 包含许多可以部署到 iOS 设备的 VPN 设置。 可使用这些设置创建和配置组织网络的 VPN 连接。 本文将说明这些设置。 某些设置仅适用于某些 VPN 客户端，例如 Citrix、Zscaler 等。

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
- **Zscaler**：要使用条件访问，或允许用户绕过 Zscaler 登录屏幕，必须将 Zscaler Private Access (ZPA) 与 Azure AD 帐户集成。 有关详细步骤，请参阅 [Zscaler 文档](https://help.zscaler.com/zpa/configuration-example-microsoft-azure-ad#Azure_UserSSO)。 
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
  - “证书”：在“身份验证证书”下，选择现有 SCEP 或 PKCS 证书配置文件以对连接进行身份验证。 [配置证书](certificates-configure.md)提供了有关证书配置文件的一些指导。
  - **用户名和密码**：最终用户必须输入用户名和密码才能登录 VPN 服务器。  

    > [!NOTE]
    > 如果用户名和密码被用作 Cisco IPsec VPN 的身份验证方法，则它们必须通过自定义 Apple 配置器配置文件来提供 SharedSecret。

- **排除的 URL**（仅限 Zscaler）：连接到 Zscaler VPN 时，可从 Zscaler 云外部访问列出的 URL。 

- **拆分隧道**：启用或禁用此设置，让设备根据流量确定使用哪个连接。 例如，旅馆中的用户使用 VPN 连接访问工作文件，但使用旅馆的标准网络进行常规的 Web 浏览。

- **VPN 标识符**（自定义 VPN、Zscaler 和 Citrix）：所用 VPN 应用的标识符，由 VPN 提供商提供。
  - **输入组织的自定义 VPN 属性的键/值对**：添加或导入用于自定义 VPN 连接的“键”和“值”。 请记住，这些值通常由 VPN 提供商提供。

- **启用网络访问控制 (NAC)** （Citrix SSO、F5 Access）：选择“我同意”后，设备 ID 将包含在 VPN 配置文件中。 此 ID 可用于对 VPN 进行身份验证以允许或阻止网络访问。

  使用 F5 Access 时，请务必：

  - 确认所使用的是 F5 BIG-IP 13.1.1.5。 BIG-IP 14 不受支持。
  - 将 BIG-IP 与 Intune for NAC 集成。 请参阅[概述：使用终结点管理系统配置 APM 以进行设备状态检查](https://support.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html#guid-0bd12e12-8107-40ec-979d-c44779a8cc89) F5 指南。
  - 在 VPN 配置文件中启用 NAC。

  将 Citrix SSO 与 Gateway 配合使用时，请务必：

  - 确认使用的是 Citrix Gateway 12.0.59 或更高版本。
  - 确认你的用户已在其设备上安装 Citrix SSO 1.1.6 或更高版本。
  - 将 Citrix 网关与 Intune for NAC 集成。 请参阅 [Integrating Microsoft Intune/Enterprise Mobility Suite with NetScaler (LDAP+OTP Scenario)](https://www.citrix.com/content/dam/citrix/en_us/documents/guide/integrating-microsoft-intune-enterprise-mobility-suite-with-netscaler.pdf) Citrix 部署指南（将 Microsoft Intune/Enterprise Mobility Suite 与 NetScaler（LDAP+OTP 方案）集成）。
  - 在 VPN 配置文件中启用 NAC。

  **重要详细信息**：  

  - 启用 NAC 后，VPN 将每隔 24 小时断开一次连接。 可以立即重新连接 VPN。
  - 设备 ID 是配置文件的一部分，但不显示在 Intune 中。 Microsoft 不会将此 ID 存储在任何位置，也不会由 Microsoft 共享。

  如果设备 ID 受 VPN 合作伙伴支持，Citrix SSO 等 VPN 客户端可获取该 ID。 然后，它可以查询 Intune 以确认该设备是否已注册，以及 VPN 配置文件是否符合要求。

  - 要删除此设置，请重新创建配置文件，不要选择“我同意”。 然后，重新分配配置文件。

## <a name="automatic-vpn-settings"></a>自动 VPN 设置

- **每应用 VPN**：启用每应用 VPN。 允许 VPN 连接在打开某些应用时自动触发。 还可以将应用与此 VPN 配置文件相关联。 有关详细信息，请参阅[为 iOS 设置每应用 VPN 的说明](vpn-setting-configure-per-app.md)。
  - **提供程序类型**：仅适用于 Pulse Secure 和自定义 VPN。
  - 在结合使用 iOS 每应用 VPN 配置文件和 Pulse Secure 或自定义 VPN 时，选择使用应用层隧道（应用-代理）或数据包级别隧道（数据包-隧道）。 针对应用层隧道，将 ProviderType 值设置为 app-proxy，针对数据包层隧道，将其设置为 packet-tunnel。 如果不确定使用哪个值，请查阅 VPN 提供商的文档。
  - **将触发此 VPN 的 Safari URL**：添加一个或多个网站 URL。 使用设备上的 Safari 浏览器访问这些 URL 时，将自动建立 VPN 连接。

- **按需 VPN**：配置用于控制何时启动 VPN 连接的条件规则。 例如，创建一个条件，仅在设备未连接到公司 Wi-fi 网络时才使用 VPN 连接。 或者创建条件。 例如，如果设备无法访问输入的 DNS 搜索域，则不启动 VPN 连接。

  - **SSID 或 DNS 搜索域**：选择此条件将使用无线网络“SSID”还是“DNS 搜索域”。 选择“添加”以配置一个或多个 SSID 或搜索域。
  - **URL 字符串探测**：可选。 输入规则用作测试的 URL。 如果具有此配置文件的设备在不重定向的情况下访问此 URL，则会启动 VPN 连接。 并且，设备会连接到目标 URL。 用户看不到该 URL 字符串探测站点。 URL 字符串探测示例是审核 Web 服务器的地址，用于在连接 VPN 前检查设备的符合性。 另一种可能性是 URL 通过 VPN 将设备连接到目标 URL 前，测试 VPN 连接至站点的能力。
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

- **自动配置脚本**：使用文件配置代理服务器。 输入包含配置文件的代理服务器 URL（例如 `http://proxy.contoso.com`）。
- **地址**：输入代理服务器的完全限定的主机名的 IP 地址。
- **端口号**：输入与代理服务器关联的端口号。

## <a name="next-step"></a>下一步
[在 Intune 中创建 VPN 配置文件](vpn-settings-configure.md)  
