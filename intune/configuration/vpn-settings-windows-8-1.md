---
title: 在 Microsoft Intune 中配置 Windows 8.1 设备上的 VPN 设置 - Azure | Microsoft Docs
description: 使用虚拟专用网络（VPN）配置设置添加或创建 VPN 配置文件，包括连接详细信息，以及要在运行 Windows 8.1 的设备上 Microsoft Intune 中的 TCP 端口。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9f9a1399d5474d79ac8fd48a8aa3a844f20eb640
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207037"
---
# <a name="add-vpn-settings-on-windows-81-devices-in-microsoft-intune"></a>在 Microsoft Intune 中为 Windows 8.1 设备添加 VPN 设置



本文介绍可用于在运行 Windows 8.1 的设备上配置 VPN 连接的 Intune 设置。

下表中并非所有值都可配置，具体取决于所选择的设置。

## <a name="base-vpn-settings"></a>基础 VPN 设置

- **将所有设置仅应用于 Windows 8.1**：在 Intune 经典门户中配置此设置。 在 Microsoft 终结点管理器管理中心，无法更改此设置。 如果将此项设置为“已配置”，则任何设置只应用于 Windows 8.1 设备  。 如果将此项设置为“未配置”，则这些设置还会应用于 Windows 10 设备  。
- **连接名称**：为此连接输入名称。 用户在他们的设备上浏览可用 VPN 连接的列表时会看到此名称。
- **服务器**：添加设备连接到的一个或多个 VPN 服务器。
  - **添加**：这将打开“添加行”页面，可在其中指定以下信息  ：
    - **描述**：为服务器指定一个描述性名称，例如“Contoso VPN 服务器”  。
    - **IP 地址或 FQDN**：提供设备连接到的 VPN 服务器的 IP 地址或完全限定的域名。 例如：“192.168.1.1”、“vpn.contoso.com”   。
    - **默认服务器**：启用此服务器作为设备建立连接时使用的默认服务器。 请确保只将一台服务器设置为默认服务器。
  - **导入**：浏览到以逗号分隔的文件，该文件包含采用以下格式的服务器列表：描述、IP 地址或 FQDN、默认服务器。 选择“确定”，将这些服务器导入到“服务器”列表   。
  - **导出**：将服务器列表导出到逗号分隔值 (csv) 文件。

- **连接类型**：从以下供应商列表中选择 VPN 连接类型：
  - **Check Point Capsule VPN**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**

<!--- **Fingerprint** (Check Point Capsule VPN only): Specify a string (for example, "Contoso Fingerprint Code") that will be used to verify that the VPN server can be trusted. A fingerprint can be sent to the client so it knows to trust any server that presents the same fingerprint when connecting. If the device doesn’t already have the fingerprint, it will prompt the user to trust the VPN server that they are connecting to while showing the fingerprint. (The user manually verifies the fingerprint and chooses **trust** to connect.) --->

- **登录组或域**（仅限 SonicWall Mobile Connect）：指定你想要连接到的登录组或域的名称。

- **角色**（仅限 Pulse Secure）：指定有权访问此连接的用户角色的名称。 用户角色用于定义个人设置和选项，并启用或禁用某些访问功能。

- **领域**（仅限 Pulse Secure）：指定你想要使用的身份验证领域的名称。 身份验证领域是“Pulse Secure”连接类型使用的身份验证资源的分组。

- **自定义 XML**：指定配置 VPN 连接的任何自定义 XML 命令。

  **Pulse Secure 示例**：

  ```xml
  <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
  ```

  **CheckPoint Mobile VPN 示例**：

  ```xml
  <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
  ```

  **SonicWALL Mobile Connect 示例**：

  ```xml
  <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
  ```

  **F5 Edge Client 示例**：

  ```xml
  <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
  ```

  有关编写自定义 XML 的详细信息，请参阅制造商的 VPN 文档。

## <a name="proxy-settings"></a>代理设置

- **自动检测代理设置**：如果你的 VPN 服务器要求使用代理服务器进行连接，请指定你是否希望设备自动检测连接设置。
- **自动配置脚本**：使用文件配置代理服务器。 输入包含配置文件的“代理服务器 URL”  。 例如，输入 `http://proxy.contoso.com`。
- **使用代理服务器**：如果想要手动输入代理服务器设置则启用此选项。
  - **地址**：输入代理服务器地址（作为 IP 地址）。
  - **端口号**：输入与代理服务器关联的端口号。
- **绕过本地地址的代理**：如果 VPN 服务器要求使用代理服务器口进行连接，而你又不想对输入的本地地址使用代理服务器，则选择此选项。

## <a name="next-steps"></a>后续步骤

配置文件已创建，但它尚未起到任何作用。 下一步，[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

在[android](vpn-settings-android.md)、 [android Enterprise](vpn-settings-android-enterprise.md)、 [macOS](vpn-settings-macos.md)和[Windows 10](vpn-settings-windows-10.md)设备上配置 VPN 设置。
