---
# required metadata

title: VPN 连接 | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: abc57093-7351-408f-9f41-a30877f96f73

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune 中的 VPN 连接
 虚拟专用网络 (VPN) 可让你的用户安全远程访问你的公司网络。 远程用户可以像其设备物理连接到网络一样地工作。 设备使用 VPN 连接配置文件来初始化与 VPN 服务器的连接。 使用 Microsoft Intune 中的**VPN 配置文件**来将 VPN 设置部署到你组织中的用户和设备。 通过部署这些设置，你可以最大限度减少最终用户连接到公司网络资源需要进行的工作。

例如，你想要用连接到公司网络上的文件共享所需的设置来设置所有 iOS 设备。 创建包含连接到公司网络所必需的设置的 VPN 配置文件，然后将此配置文件部署到所有使用 iOS 设备的用户。 用户将在可用网络的列表中看到 VPN 连接，并可以轻松连接。

你可以使用 VPN 配置文件配置下列设备类型：

* 运行 Android 4 和更高版本的设备
* 运行 iOS 7.1 和更高版本的设备
* 运行 Max OS X 10.9 和更高版本的设备
* 运行 Windows 8.1 和更高版本的已注册设备
* 运行 Windows Phone 8.1 和更高版本的设备
* 运行 Windows 10 桌面版和移动版的设备。

VPN 配置文件配置选项将因你选择的设备类型而有所不同。

## VPN 连接类型

Intune 支持使用以下连接类型创建 VPN 配置文件：




连接类型 |iOS 和 Mac OS X  |Android|Windows 8.1|Windows RT|Windows RT 8.1|Windows Phone 8.1  |Windows 10 桌面版和移动版 |
----------------|------------------|-------|-----------|----------|--------------|-----------------|------------|
Cisco AnyConnect|是 |是   |否    |     否    |否  |否    | 是，（OMA URI，仅限移动版）|     
脉冲安全|是  |是 |是   |否  |是  |是| 是|        
F5 Edge Client|是 |是 |是 |否  |是  |   是 |  是|   
Dell SonicWALL Mobile Connect|是 |是 |是 |否  |是 |是 |是|         
CheckPoint Mobile VPN|是 |是 |是 |是 |是|是|是|
Microsoft SSL (SSTP)|否 |否 |否 |否 |否|否|否|
Microsoft Automatic|否 |否 |否 |否 |否|否|是|
IKEv2|否 |否 |否 |否 |否|否|是|
PPTP|否 |否 |否 |否 |否|否|是|
L2TP|否 |否 |否 |否 |否|否|是|


> [!IMPORTANT] 在你能够使用已部署到设备的 VPN 配置文件之前，你必须安装适用于该配置文件的 VPN 应用。 你可以利用[在 Microsoft Intune 中部署应用](deploy-apps-in-microsoft-intune.md)主题中的信息帮助你使用 Intune 部署适用的应用。  

 了解使用 [VPN 配置文件的自定义配置](custom-configurations-for-vpn-profiles.md)中的 URI 设置如何创建自定义 VPN 配置文件。     

## 如何保护 VPN 配置文件

VPN 配置文件可以使用来自不同制造商的多种不同的连接类型和协议。 这些连接通常使用以下两种方法之一进行保护：

### 证书

在创建 VPN 配置文件时，选择之前已在 Intune 中创建的 SCEP 或 .PFX 证书配置文件。

该配置文件又称为身份证书，用于对你创建的受信任的身份证书配置文件（或根证书）进行身份验证，以确定户的设备可以连接。 受信任的证书会部署到对 VPN 连接（通常是 VPN 服务器）进行身份验证的计算机。

有关如何在 Intune 中创建和使用配置文件的详细信息，请参阅[使用证书配置文件的安全资源访问](secure-resource-access-with-certificate-profiles.md)。

### 用户名和密码

用户通过提供其用户名和密码向 VPN 服务器进行身份验证。

## 创建 VPN 配置文件

1. 在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，选择**策略>添加策略**。
2. 展开相关设备类型以选择新策略模板，然后为该设备选择 VPN 配置文件：
    * **VPN 配置文件（Android 4 及更高版本）**
    * **VPN 配置文件（iOS 7.1 及更高版本）**
    * **VPN 配置文件（Mac OS X 10.9 及更高版本）**
    * **VPN 配置文件（Windows 8.1 及更高版本）**
    * **VPN 配置文件（Windows Phone 8.1 及更高版本）**
    * **VPN 配置文件（Windows 10 桌面版和移动版及更高版本）**

    你仅可以创建和部署自定义 VPN 配置文件策略。 建议的设置不可用。

3. 使用下表来帮助你配置 VPN 配置文件设置：

设置名  |更多信息  
---------|---------
**Name**     |输入 VPN 配置文件的唯一名称，以帮助你在 Intune 控制台中识别它。         
**说明**     |提供相关描述，对 VPN 配置文件以及其他相关的信息的进行概述，这可帮助你找到 VPN 配置文件。         
**VPN 连接名称（向用户显示）**     |指定 VPN 配置文件的名称。 用户将在其设备上的可用 VPN 连接列表中看到该名称。         
**连接类型**     |  选择在 VPN 配置文件中使用以下连接类型之一：“Cisco AnyConnect”（不可用于 Windows 8.1 或 Windows Phone 8.1）、“Pulse Secure”、“F5 Edge Client”、“Dell SonicWALL Mobile Connect”、“CheckPoint Mobile VPN”
**VPN 服务器说明**     | 指定设备将连接到的 VPN 服务器的说明。 **示例：**Contoso VPN 服务器。 当连接类型是“F5 Edge Client”时，使用“服务器列表”字段来指定服务器说明和 IP 地址的列表。
**服务器 IP 地址或 FQDN**    |提供 IP 地址或设备将连接到的 VPN 服务器的完全限定的域名。 **示例：**192.168.1.1、vpn.contoso.com。  当连接类型是“F5 Edge Client”时，使用“服务器列表”字段来指定服务器说明和 IP 地址的列表。         |         
**服务器列表**     |选择**添加**以添加用于 VPN 连接的新 VPN 服务器。 你还可以指定哪个服务器将作为连接的默认服务器。 此选项仅在连接类型为“F5 Edge Client”时显示。         
**通过 VPN 连接发送所有网络流量**     |如果选择此选项，所有网络流量都会通过 VPN 连接发送。 如果不选择此选项，则在连接到第三方 VPN 服务器时客户端将动态协商拆分隧道的路由。 仅将通过 VPN 隧道发送与公司网络的连接。 你连接到 Internet 上的资源时，不会使用 VPN 隧道。
**身份验证方法**| 选择 VPN 连接使用的身份验证方法：“证书”或“用户名和密码”。 （连接类型为“Cisco AnyConnect”时，“用户名和密码”不可用。）“身份验证方法”选项不可用于 Windows 8.1。
**在每次登录时记住用户凭据**|选择此选项以确保记住用户凭据，使用户不必在每次建立连接时输入凭据。
**请选择客户端证书用于客户端身份验证（身份证书）**|选择之前创建的客户端 SCEP 证书，它将用于对 VPN 连接进行身份验证。 有关如何在 Intune 中使用配置文件的详细信息，请参阅[使用证书配置文件的安全资源访问](secure-resource-access-with-certificate-profiles.md)。 仅当身份验证方法为“证书”时才会显示此选项。
**角色**| 指定有权访问此连接的用户角色的名称。 用户角色用于定义个人设置、选项以及启用或禁用某些访问功能。 此选项仅在连接类型为“脉冲安全”时显示。
**领域**|指定你想要使用的身份验证领域的名称。 身份验证领域是“脉冲安全”连接类型使用的身份验证资源的分组。 此选项仅在连接类型为“脉冲安全”时显示。
**登录组或域**|指定你想要连接到的登录组或域的名称。 此选项仅在连接类型为“Dell SonicWALL Mobile Connect”时显示。
**指纹**|指定一个将用于验证 VPN 服务器是否可以信任的字符串（例如“Contoso Fingerprint Code”）。 指纹可以：发送到客户端，因此在连接时它知道信任任何提供相同指纹的服务器。 如果设备还没有指纹，则会提示用户信任正在连接的 VPN 服务器，并显示指纹（用户手动验证指纹，并选择**信任**以进行连接）。 此选项仅在连接类型为“CheckPoint Mobile VPN”时显示。
**按应用 VPN**|如果你想要将此 VPN 连接与 iOS 或 Mac OS X 应用相关联，以便在运行该应用时打开连接，请选择此选项。 可在部署软件时将 VPN 配置文件与应用关联。 有关详细信息，请参阅[在 Microsoft Intune 中部署应用](deploy-apps-in-microsoft-intune.md)
“自动检测代理设置”（仅限 iOS、Mac OS X、Windows 8.1 和 Windows Phone 8.1）|如果你的 VPN 服务器要求使用代理服务器进行连接，请指定你是否希望设备自动检测连接设置。 有关详细信息，请参阅 Windows Server 文档。
“使用自动配置脚本”（仅限 iOS、Mac OS X、Windows 8.1 和 Windows Phone 8.1）|如果你的 VPN 服务器要求使用代理服务器进行连接，请指定是否想要使用自动配置脚本来定义设置，然后指定包含该设置的文件的 URL。 有关详细信息，请参阅 Windows Server 文档。
“使用代理服务器”（仅限 iOS、Mac OS X、Windows 8.1 和 Windows Phone 8.1）|如果你的 VPN 服务器要求使用代理服务器进行连接，请选择此选项，然后指定代理服务器的地址和端口号。 有关详细信息，请参阅 Windows Server 文档。
“绕过本地地址的代理设置”（仅限 iOS、Mac OS X、Windows 8.1 和 Windows Phone 8.1）|如果你的 VPN 服务器要求使用代理服务器口进行连接，在你不想对指定的本地地址使用代理服务器时选择此选项。 有关详细信息，请参阅 Windows Server 文档。
“自定义 XML”（Windows 8.1 及更高版本和 Windows Phone 8.1 及更高版本）|使你可以指定配置 VPN 连接的自定义 XML 命令。 示例。 对于“脉冲安全”：&lt;pulse-schema&gt;&lt;isSingleSignOnCredential&gt;true&lt;/isSingleSignOnCredential&gt;&lt;/pulse-schema&gt;。 对于“CheckPoint Mobile VPN”：&lt;CheckPointVPN port="443" name="CheckPointSelfhost" sso="true"  debug="3" /&gt;。 对于“Dell SonicWALL Mobile Connect”：&lt;MobileConnect&gt;&lt;Compression&gt;false&lt;/Compression&gt;&lt;debugLogging&gt;True&lt;/debugLogging&gt;&lt;packetCapture&gt;False&lt;/packetCapture&gt;&lt;/MobileConnect&gt;。 对于“F5 Edge Client”：&lt;f5-vpn-conf&gt;&lt;single-sign-on-credential /&gt;&lt;/f5-vpn-conf&gt;。 有关如何编写自定义 XML 命令的详细信息，请参阅每个制造商 VPN 文档。
“DNS 后缀搜索列表”（仅限 Windows Phone 8.1）|在每个行上指定一个 DNS 后缀。 使用短名称连接到网站时，将搜索你指定的每个 DNS 后缀。 例如，指定 DNS 后缀 **domain1.contoso.com** 和 **domain2.contoso.com**，访问 URL **http://mywebsite**，并且将搜索 URL **http://mywebsite.domain1.contoso.com** 和 **http://mywebsite.domain2.contoso.com**。
“连接到公司 Wi-Fi 网络时绕过 VPN”（仅限 Windows Phone 8.1）|指定当设备连接到公司 Wi-Fi 网络时将不使用 VPN 连接。
“连接到家庭 Wi-Fi 网络时绕过 VPN”（仅限 Windows Phone 8.1）|指定当设备连接到家庭 Wi-Fi 网络时将不使用 VPN 连接。

以下附加设置适用于 Windows 10 桌面和移动设备

设置名  |更多信息  
---------|---------
**网络通信规则**| 设置将为 VPN 连接启用的协议、本地和远程端口及地址范围。 如果未创建网络通信规则，则会启用所有协议、端口和地址范围。 创建规则后，VPN 连接将仅使用该规则或其他规则中指定的协议、端口和地址范围。
**路由**|将使用 VPN 连接的路由。
**DNS 服务器**| 建立 VPN 连接后该连接将使用的 DNS 服务器。         
**关联应用**     | 你可以提供将自动使用 VPN 连接的应用列表。 应用类型将确定应用的标识符。 对于通用应用，提供包系列名称，对于桌面应用，提供应用的文件路径。          


> [!IMPORTANT] 建议保护为配置 per-app VPN 而编制的应用的所有列表。 如果将未授权用户修改的列表导入 per-app VPN 应用列表，你将可能向不应具有访问权限的应用授权 VPN 访问权限。 保护应用列表的方法之一是使用访问控制列表 (ACL)。

以下是可以使用公司边界设置情形的一个示例。 如果希望仅为远程桌面启用 VPN，请创建一个在外部端口 3996 上允许协议编号 27 的流量的网络通信规则。 其他流量将不使用该 VPN。

当 VPN 连接类型不允你许定义流量在拆分隧道的处理方式时，在公司边界内定义路由非常有用。 在这种情况下，请使用“路由”列出将使用 VPN 的路由。

通过创建自定义的 OMA-URI 设置，可以将 Windows 10 设备的 VPN 使用限于特定应用。

新的策略将在“策略”  工作区的“配置策略”  节点处显示。

## 部署策略

1.  在“策略”工作区中，选择想要部署的策略，然后选择“管理部署”。

2.  在“管理部署”  对话框中：

    -   **部署策略** - 选择要向其部署策略的一个组或多个组，然后选择**添加**&gt;**确定**。

    -   **关闭对话框而不部署** — 选择**取消**。


成功部署后，用户将在其设备上的 VPN 连接列表中看到你指定的 VPN 连接名称。

“策略”  工作区“概述”  页的状态摘要和警报可识别需要关注的策略问题。 此外，状态摘要会显示在“仪表板”工作区中。

### 另请参阅
[VPN 配置文件的自定义配置](Custom-configurations-for-VPN-profiles.md)
[用于 Android Pulse Secure 的 Per-app VPN](per-app-vpn-for-android-pulse-secure.md)


<!--HONumber=May16_HO5-->


