---
title: Microsoft Intune 中适用于 iOS 设备的 VPN 设置 - Azure | Microsoft Docs
description: 在运行 iOS 的设备上的 Microsoft Intune 中，查看：可用的虚拟专用网络 (VPN) 配置设置，包括基本设置中的连接详细信息、身份验证方法和拆分隧道；具有标识符的自定义 VPN 设置和键值对；包括 Safari URL 的每应用 VPN 设置，和具有 SSID 或 DNS 搜索域的按需 VPN；以及代理设置，包括配置脚本、IP 或 FQDN 地址和 TCP 端口。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: eb87d75512d9f04abac9db256d0d968bb85116ef
ms.sourcegitcommit: 6a9830de768dd97a0e95b366fd5d2f93980cee05
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-ios"></a>在 Microsoft Intune 中为运行 iOS 的设备配置 VPN 设置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文介绍可用于在运行 iOS 的设备上配置 VPN 连接的 Intune 设置。

下表中并非所有值都可配置，具体取决于所选择的设置。

## <a name="base-vpn-settings"></a>基础 VPN 设置

- **连接名称**：输入此连接的名称。 最终用户在浏览其设备的可用 VPN 连接列表时将看到此名称。
- **IP 地址或 FQDN**：输入设备连接到的 VPN 服务器的 IP 地址或完全限定的域名 (FQDN)。 例如，输入 192.168.1.1 或 contoso.com。
- **身份验证方法**：从以下选项中选择设备向 VPN 服务器进行身份验证的方法：
  - “证书”：在“身份验证证书”下，选择现有 SCEP 或 PKCS 证书配置文件以对连接进行身份验证。 [配置证书](certificates-configure.md)提供了有关证书配置文件的一些指导。
  - **用户名和密码**：最终用户必须输入用户名和密码才能登录 VPN 服务器。

    > [!NOTE]
    > 如果用户名和密码被用作 Cisco IPsec VPN 的身份验证方法，则它们必须通过自定义 Apple 配置器配置文件来提供 SharedSecret。
  
- **连接类型**：从以下供应商列表中选择 VPN 连接类型：
  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **Cisco 旧式 AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **Cisco (IPSec)**
  - **Citrix**
  - **自定义 VPN**

    > [!NOTE]
    > - “Cisco 旧式 AnyConnect VPN”配置文件适用于 [Cisco 旧式 AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924) 应用版本 4.0.5x 以及较旧版本
    > - “Cisco AnyConnect VPN”配置文件适用于 [Cisco AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690) 应用版本 4.0.7x 以及较新版本

- **拆分隧道**：启用或禁用此设置，让设备根据流量确定使用哪个连接。 例如，旅馆中的用户使用 VPN 连接访问工作文件，但使用旅馆的标准网络进行常规的 Web 浏览。

## <a name="custom-vpn-settings"></a>自定义 VPN 设置

如果选择“自定义 VPN”作为连接类型，还需配置以下设置：

- **VPN 标识符**：所用 VPN 应用的标识符，由 VPN 提供商提供。
- **输入自定义 VPN 属性的键值对**：添加或导入用于自定义 VPN 连接的“键”和“值”。 同样，这些值通常由 VPN 提供商提供。

## <a name="apps-per-app-vpn-settings"></a>应用（每应用 VPN）设置

- **每应用 VPN**：从 Safari 浏览器访问 URL 时，启用此选项可使用这些 URL 来启用 VPN 连接。 要配置“每应用 VPN”，必须在基础 VPN 设置中选择“证书”作为身份验证方法。
  - **将触发此 VPN 的 Safari URL**：选择此选项可添加一个或多个网站 URL。 访问这些 URL 时将启用 VPN 连接。

- **按需 VPN**：配置用于控制何时启动 VPN 连接的条件规则。 例如，创建一个条件，仅在设备未连接到公司 Wi-fi 网络时才使用 VPN 连接。 或者创建一个条件，如果设备无法访问指定的 DNS 搜索域，则不启动 VPN 连接。

  - **SSID 或 DNS 搜索域**：选择此条件将使用无线网络“SSID”还是“DNS 搜索域”。 选择“添加”以配置一个或多个 SSID 或搜索域。
  - **URL 字符串探测**：可选。 输入规则用作测试的 URL。 如果安装有此配置文件的设备能在不重定向的情况下访问此 URL，则启动 VPN 连接，且该设备将连接到目标 URL。 用户看不到该 URL 字符串探测站点。 URL 字符串探测示例是审核 Web 服务器的地址，用于在连接 VPN 前检查设备的符合性。 另一种可能性是 URL 通过 VPN 将设备连接到目标 URL 前，测试 VPN 连接至站点的能力。
  - **域操作**：选择以下项之一：
    - 需要时连接
    - 从不连接
  - **操作**：选择以下项之一：
    - 连接
    - 评估连接
    - 忽略
    - 断开连接

## <a name="proxy-settings"></a>代理设置

- **自动配置脚本**：使用文件配置代理服务器。 输入包含配置文件的代理服务器 URL（例如 http://proxy.contoso.com）。
- **地址**：输入代理服务器的完全限定的主机名的 IP 地址。
- **端口号**：输入与代理服务器关联的端口号。

## <a name="next-step"></a>下一步
[在 Intune 中创建 VPN 配置文件](vpn-settings-configure.md)
