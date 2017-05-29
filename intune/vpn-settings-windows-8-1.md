---
title: "适用于 Windows 8.1 设备的 Intune VPN 设置"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解可用于在 Windows 8.1 设备上配置 VPN 连接的 Intune 设置。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 71e842d24e435c25bf24e453b36449c68d281370
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="vpn-settings-for-windows-81-devices-in-microsoft-intune"></a>Microsoft Intune 中适用于 Windows 8.1 设备的 VPN 设置

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

根据所选择的设置，下表中并非所有值都可配置。

## <a name="base-vpn-settings"></a>基础 VPN 设置


- **将所有设置仅应用于 Windows 8.1** - 可在经典 Intune 门户中配置此设置。 在 Azure 门户中无法更改此设置。 如果将此项设置为“已配置”，则任何设置将只应用于 Windows 8.1 设备。 如果将此项设置为“未配置”，则这些设置也将适用于 Windows 10 设备。
- **连接名称** - 输入此连接的名称。 最终用户在浏览其设备的可用 VPN 连接列表时将看到此名称。
- **服务器** - 添加设备将连接到的一个或多个 VPN 服务器。
    - **添加** - 打开“添加行”边栏选项卡，可在其中指定以下信息：
        - **说明** - 为服务器指定一个描述性名称，例如“Contoso VPN 服务器”。
        - **IP 地址或 FQDN** - 提供设备将连接到的 VPN 服务器的 IP 地址或完全限定的域名。 示例：**192.168.1.1**、**vpn.contoso.com**。
        - **默认服务器** - 启用此服务器作为设备建立连接时使用的默认服务器。 请确保只将一台服务器设置为默认服务器。
    - **导入** - 在格式描述、IP 地址或 FQDN 以及默认服务器中，浏览到包含以逗号分隔的服务器列表的文件。 选择“确定”，将这些内容导入到“服务器”列表。
    - **导出** - 将服务器列表导出到逗号分隔值 (csv) 文件。

- **连接类型** - 从以下供应商列表中选择 VPN 连接类型：
- **Check Point Capsule VPN**
- **Dell SonicWALL Mobile Connect**
-  **F5 Edge Client**
- **Pulse Secure**

<!--- **Fingerprint** (Check Point Capsule VPN only) - Specify a string (for example, "Contoso Fingerprint Code") that will be used to verify that the VPN server can be trusted. A fingerprint can be sent to the client so it knows to trust any server that presents the same fingerprint when connecting. If the device doesn’t already have the fingerprint, it will prompt the user to trust the VPN server that they are connecting to while showing the fingerprint. (The user manually verifies the fingerprint and chooses **trust** to connect.) --->

- **登录组或域**（仅限 Dell SonicWALL Mobile Connect）- 指定要连接到的登录组或域的名称。

- **角色**（仅限 Pulse Secure）- 指定有权访问此连接的用户角色的名称。 用户角色用于定义个人设置和选项，并启用或禁用某些访问功能。

- **领域**（仅限 Pulse Secure）- 指定想要使用的身份验证领域的名称。 身份验证领域是“脉冲安全”连接类型使用的身份验证资源的分组。


- **自定义 XML** - 指定配置 VPN 连接的任何自定义 XML 命令。

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


## <a name="proxy-settings"></a>代理设置

- **自动检测代理设置** - 如果 VPN 服务器要求使用代理服务器进行连接，请指定是否希望设备自动检测连接设置。 有关详细信息，请参阅 Windows Server 文档。
- **自动配置脚本** - 使用文件配置代理服务器。 输入包含配置文件的**代理服务器 URL**（例如 **http://proxy.contoso.com**）。
- **使用代理服务器** - 如果想要手动输入代理服务器设置则启用此选项。
    - **地址** - 输入代理服务器地址（作为 IP 地址）。
    - **端口号** - 输入与代理服务器关联的端口号。
- **不对本地地址使用代理服务器** - 如果 VPN 服务器要求使用代理服务器进行连接，在不想对指定的本地地址使用代理服务器时选择此选项。 有关详细信息，请参阅 Windows Server 文档。

