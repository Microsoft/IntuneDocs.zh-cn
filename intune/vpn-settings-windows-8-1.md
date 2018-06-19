---
title: 适用于 Windows 8.1 设备的 Microsoft Intune VPN 设置
titleSuffix: ''
description: 了解可用于在运行 Windows 8.1 的设备上配置 VPN 连接的 Intune 设置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 30aa56913cc3bda2d1c8b8b67e982c565c44a2a8
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
ms.locfileid: "31834164"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-windows-81"></a>在 Microsoft Intune 中为运行 Windows 8.1 的设备配置 VPN 设置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文介绍可用于在运行 Windows 8.1 的设备上配置 VPN 连接的 Intune 设置。

下表中并非所有值都可配置，具体取决于所选择的设置。

## <a name="base-vpn-settings"></a>基础 VPN 设置


- **将所有设置仅应用于 Windows 8.1** - 可以在 Intune 经典门户中配置此设置。 在 Azure 门户中无法更改此设置。 如果将此项设置为“已配置”，则任何设置只应用于 Windows 8.1 设备。 如果将此项设置为“未配置”，则这些设置还会应用于 Windows 10 设备。
- **连接名称** - 输入此连接的名称。 用户在他们的设备上浏览可用 VPN 连接的列表时会看到此名称。
- **服务器** - 添加设备连接到的一个或多个 VPN 服务器。
    - **添加** - 这将打开“添加行”页面，可在其中指定以下信息：
        - **说明** - 为服务器指定一个描述性名称，例如“Contoso VPN 服务器”。
        - IP 地址或 FQDN - 提供设备连接到的 VPN 服务器的 IP 地址或完全限定的域名。 示例：**192.168.1.1**、**vpn.contoso.com**。
        - **默认服务器** - 启用此服务器作为设备建立连接时使用的默认服务器。 请确保只将一台服务器设置为默认服务器。
    - **导入** - 在格式描述、IP 地址或 FQDN 以及默认服务器中，浏览到包含以逗号分隔的服务器列表的文件。 选择“确定”，将这些内容导入到“服务器”列表。
    - **导出** - 将服务器列表导出到逗号分隔值 (csv) 文件。

- **连接类型** - 从以下供应商列表中选择 VPN 连接类型：
- **Check Point Capsule VPN**
- **SonicWall Mobile Connect**
- **F5 Edge Client**
- **Pulse Secure**

<!--- **Fingerprint** (Check Point Capsule VPN only) - Specify a string (for example, "Contoso Fingerprint Code") that will be used to verify that the VPN server can be trusted. A fingerprint can be sent to the client so it knows to trust any server that presents the same fingerprint when connecting. If the device doesn’t already have the fingerprint, it will prompt the user to trust the VPN server that they are connecting to while showing the fingerprint. (The user manually verifies the fingerprint and chooses **trust** to connect.) --->

- **登录组或域**（仅限 SonicWall Mobile Connect）- 指定要连接到的登录组或域的名称。

- **角色**（仅限 Pulse Secure）- 指定有权访问此连接的用户角色的名称。 用户角色用于定义个人设置和选项，并启用或禁用某些访问功能。

- **领域**（仅限 Pulse Secure）- 指定想要使用的身份验证领域的名称。 身份验证领域是“Pulse Secure”连接类型使用的身份验证资源的分组。


- **自定义 XML** - 指定配置 VPN 连接的任何自定义 XML 命令。

**Pulse Secure 的示例：**

```
    <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**CheckPoint Mobile VPN 的示例：**
```
    <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**SonicWall Mobile Connect 的示例：**
```
    <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**F5 Edge Client 的示例：**

```
    <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

有关详细信息，请参阅每个制造商的 VPN 文档以了解如何编写自定义 XML 命令。


## <a name="proxy-settings"></a>代理设置

- **自动检测代理设置** - 如果 VPN 服务器要求使用代理服务器进行连接，请指定是否希望设备自动检测连接设置。 有关详细信息，请参阅 Windows Server 文档。
- **自动配置脚本** - 使用文件配置代理服务器。 输入包含配置文件的代理服务器 URL（例如 http://proxy.contoso.com）。
- **使用代理服务器** - 如果想要手动输入代理服务器设置则启用此选项。
    - **地址** - 输入代理服务器地址（作为 IP 地址）。
    - **端口号** - 输入与代理服务器关联的端口号。
- **不对本地地址使用代理服务器** - 如果 VPN 服务器要求使用代理服务器进行连接，在不想对指定的本地地址使用代理服务器时选择此选项。 有关详细信息，请参阅 Windows Server 文档。
