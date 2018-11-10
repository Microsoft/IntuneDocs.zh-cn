---
title: 适用于 Windows Phone 8.1 设备的 Microsoft Intune VPN 设置
titleSuffix: ''
description: 了解可用于在运行 Windows Phone 8.1 的设备上配置 VPN 连接的 Intune 设置。
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
ms.openlocfilehash: 822be56db10f4659ba9cd027c2612d7960e40e5b
ms.sourcegitcommit: cac71802b2782700f0d52ea114089d73620cd1ed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50679196"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-windows-phone-81"></a>在 Microsoft Intune 中为运行 Windows Phone 8.1 的设备配置 VPN 设置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文介绍可用于在运行 Windows Phone 8.1 的设备上配置 VPN 连接的 Intune 设置。


下表中并非所有值都可配置，具体取决于所选择的设置。

## <a name="base-vpn-settings"></a>基础 VPN 设置

- **将所有设置仅应用于 Windows Phone 8.1** - 可以在 Intune 经典门户中配置此设置。 在 Azure 门户中无法更改此设置。 如果将此项设置为“已配置”，则任何设置仅应用于 Windows Phone 8.1 设备。 如果将此项设置为“未配置”，则这些设置也适用于 Windows 10 移动版设备。
- **连接名称** - 输入此连接的名称。 用户在他们的设备上浏览可用 VPN 连接的列表时会看到此名称。
- 身份验证方法 - 从以下选项中选择设备向 VPN 服务器进行身份验证的方法：
    - **证书** - 在“身份验证证书”下，选择之前创建的 SCEP 或 PKCS 证书配置文件以对连接进行身份验证。 有关证书配置文件的更多详细信息，请参阅[如何配置证书](certificates-configure.md)。
    - **用户名和密码** - 最终用户必须提供用户名和密码才能登录 VPN 服务器。
- **服务器** - 添加设备连接到的一个或多个 VPN 服务器。
    - **添加** - 打开“添加行”边栏选项卡，可在其中指定以下信息：
        - **说明** - 为服务器指定一个描述性名称，例如“Contoso VPN 服务器”。
        - IP 地址或 FQDN - 提供设备连接到的 VPN 服务器的 IP 地址或完全限定的域名。 示例：**192.168.1.1**、**vpn.contoso.com**。
        - **默认服务器** - 启用此服务器作为设备建立连接时使用的默认服务器。 请确保只将一台服务器设置为默认服务器。
    - **导入** - 在格式描述、IP 地址或 FQDN 以及默认服务器中，浏览到包含以逗号分隔的服务器列表的文件。 选择“确定”，将这些内容导入到“服务器”列表。
    - **导出** - 将服务器列表导出到逗号分隔值 (csv) 文件。

- **不在公司 Wi-Fi 网络上使用 VPN** - 启用此选项以指定当设备连接到公司 Wi-Fi 网络时不使用 VPN 连接。
- **不在家庭 Wi-Fi 网络上使用 VPN** - 启用此选项以指定当设备连接到家庭 Wi-Fi 网络时不使用 VPN 连接。

- **连接类型** - 从以下供应商列表中选择 VPN 连接类型：
    - **Check Point Capsule VPN**
    - **SonicWall Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**

- **登录组或域**（仅限 SonicWall Mobile Connect）- 指定要连接到的登录组或域的名称。
- **角色**（仅限 Pulse Secure）- 指定有权访问此连接的用户角色的名称。 用户角色用于定义个人设置和选项，并启用或禁用某些访问功能。
- **领域**（仅限 Pulse Secure）- 指定想要使用的身份验证领域的名称。 身份验证领域是“Pulse Secure”连接类型使用的身份验证资源的分组。

- “DNS 后缀搜索列表” - “添加”一个或多个 DNS 后缀。 通过使用短名称连接到网站时，会搜索你指定的每个 DNS 后缀。 例如，指定 DNS 后缀“domain1.contoso.com”和“domain2.contoso.com”并访问 URL `http://mywebsite` 后，将会搜索 URL `http://mywebsite.domain1.contoso.com` 和 `http://mywebsite.domain2.contoso.com`。

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

有关如何编写自定义 XML 命令的详细信息，请参阅每个制造商 VPN 文档。

- **拆分隧道** - “启用”或“禁用”此选项，让设备根据流量确定使用哪个连接。 例如，旅馆中的用户使用 VPN 连接来访问工作文件，但使用旅馆的标准网络进行常规的 Web 浏览。




## <a name="proxy-settings"></a>代理设置

- **自动检测代理设置** - 如果 VPN 服务器要求使用代理服务器进行连接，请指定是否希望设备自动检测连接设置。 有关详细信息，请参阅 Windows Server 文档。
- **自动配置脚本** - 使用文件配置代理服务器。 输入包含配置文件的代理服务器 URL（例如 `** http://proxy.contoso.com**`）。
- **使用代理服务器** - 如果想要手动输入代理服务器设置则启用此选项。
    - **地址** - 输入代理服务器地址（作为 IP 地址）。
    - **端口号** - 输入与代理服务器关联的端口号。
- **不对本地地址使用代理服务器** - 如果 VPN 服务器要求使用代理服务器进行连接，在不想对指定的本地地址使用代理服务器时选择此选项。 有关详细信息，请参阅 Windows Server 文档。
