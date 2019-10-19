---
title: 在 Microsoft Intune 中配置 macOS 设备的 VPN 设置 - Azure | Microsoft Docs
description: 添加或创建一个虚拟专用网络（VPN）配置文件，包括连接详细信息、拆分隧道、具有标识符、键和值对的自定义 VPN 设置、带有配置脚本的代理设置、IP 或 FQDN 地址和中的 TCP 端口在运行 macOS 的设备上 Microsoft Intune。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 044b35b34a9a5b01537e82dcfddca74a284ebdcc
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72491014"
---
# <a name="add-vpn-settings-on-macos-devices-in-microsoft-intune"></a>在 Microsoft Intune 中为 macOS 设备添加 VPN 设置

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

本文介绍可用于在运行 macOS 的设备上配置 VPN 连接的 Intune 设置。

下表中并非所有值都可配置，具体取决于所选择的设置。

## <a name="before-you-begin"></a>在开始之前

[创建设备配置文件](vpn-settings-configure.md)。

> [!NOTE]
> 这些设置适用于所有注册类型。 有关注册类型的详细信息，请参阅[macOS 注册](../enrollment/macos-enroll.md)。

## <a name="base-vpn-settings"></a>基础 VPN 设置

**连接名称**：输入此连接的名称。 最终用户在浏览其设备的可用 VPN 连接列表时将看到此名称。
- **IP 地址或 FQDN**：提供设备连接到的 VPN 服务器的 IP 地址或完全限定的域名。 示例：**192.168.1.1**、**vpn.contoso.com**。
- **身份验证方法**：从以下选项中选择设备向 VPN 服务器进行身份验证的方法：
  - **证书**在“身份验证证书”  下，选择之前创建的 SCEP 或 PKCS 证书配置文件以对连接进行身份验证。 有关证书配置文件的详细信息，请参阅[如何配置证书](../protect/certificates-configure.md)。
  - **用户名和密码**：最终用户必须提供用户名和密码才能登录 VPN 服务器。
- **连接类型**：从以下供应商列表中选择 VPN 连接类型：
  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **自定义 VPN**
- **拆分隧道**：“启用”或“禁用”此选项，让设备根据流量确定使用哪个连接   。 例如，旅馆中的用户使用 VPN 连接来访问工作文件，但使用旅馆的标准网络进行常规的 Web 浏览。

<!--- **Per-app VPN** - Select this option if you want to associate this VPN connection with an iOS or macOS app so that the connection will be opened when the app is run. You can associate the VPN profile with an app when you assign the software. For more information, see [How to assign and monitor apps](../apps/apps-deploy.md). --->

## <a name="custom-vpn-settings"></a>自定义 VPN 设置

如果选择“自定义 VPN”  ，请配置以下其他设置：

- **Vpn 标识符**：为要使用的 vpn 应用输入标识符。 此标识符由 VPN 提供商提供。
- **输入自定义 VPN 属性的键值对**：添加或导入用于自定义 VPN 连接的“键”和“值”   。 这些值通常由 VPN 提供商提供。

## <a name="proxy-settings"></a>代理设置

- **自动配置脚本**：使用文件配置代理服务器。 输入包含配置文件的“代理服务器 URL”  。 例如，输入 `http://proxy.contoso.com`。
- **地址**：输入代理服务器地址（作为 IP 地址）。
- **端口号**：输入与代理服务器关联的端口号。

## <a name="next-steps"></a>后续步骤

配置文件已创建，但它尚未起到任何作用。 下一步，[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

在[android](vpn-settings-android.md)、 [android 企业版](vpn-settings-android-enterprise.md)、 [iOS](vpn-settings-ios.md)版和[Windows 10](vpn-settings-windows-10.md)设备上配置 VPN 设置。
