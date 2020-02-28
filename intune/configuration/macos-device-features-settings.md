---
title: Microsoft Intune 中的 macOS 设备功能设置 - Azure | Microsoft Docs
description: 查看用于为 macOS 设备配置 AirPrint 的设置，自定义“登录”窗口以显示或隐藏 Microsoft Intune 中的电源按钮。 请参阅获取网络中 AirPrint 服务器的 IP 地址、路径和端口设置的步骤。 在设备配置配置文件中使用这些设置来配置 macOS 设备功能。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: df5b53be159fd082090e61fd736e4c9329644c85
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512732"
---
# <a name="macos-device-feature-settings-in-intune"></a>Intune 中的 macOS 设备功能设置

Intune 包含一些内置设置，用于自定义 macOS 设备上的功能。 例如，管理员可以添加 AirPrint 打印机、选择用户登录的方式、配置电源控制、使用单一登录身份验证等。

使用这些功能可以控制 macOS 设备，作为移动设备管理 (MDM) 解决方案的一部分。

本文列出了这些设置，并介绍了每个设置的用途。 它还列出了使用“终端”应用（仿真器）获取 AirPrint 打印机的 IP 地址、路径和端口的步骤。 有关设备功能的详细信息，请参阅[添加 iOS/iPadOS 或 macOS 设备功能设置](device-features-configure.md)。

## <a name="before-you-begin"></a>在开始之前

[创建 macOS 设备配置文件](device-features-configure.md)。

> [!NOTE]
> 这些设置适用于不同的注册类型，其中一些设置应用于所有注册选项。 有关不同注册类型的详细信息，请参阅 [macOS 注册](../enrollment/macos-enroll.md)。

## <a name="airprint"></a>AirPrint

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>设置适用范围：设备注册和自动设备注册 

- **IP 地址**：输入打印机的 IPv4 或 IPv6 地址。 如果使用主机名标识打印机，可以通过在“终端”应用中对打印机执行 ping 操作来获取 IP 地址。 （本文中的）[获取 IP 地址和路径](#get-the-ip-address-and-path)提供了更多详细信息。
- **路径**：输入打印机的路径。 网络中打印机的路径通常是 `ipp/print`。 （本文中的）[获取 IP 地址和路径](#get-the-ip-address-and-path)提供了更多详细信息。
- **端口**（iOS 11.0 以上版本、iPadOS 13.0 以上版本）：输入 AirPrint 目标的侦听端口。 如果将此属性留空，AirPrint 使用默认端口。
- **TLS**（iOS 11.0 以上版本、iPadOS 13.0 以上版本）：选择“启用”可使用传输层安全性 (TLS) 确保 AirPrint 连接安全  。

- **添加**：AirPrint 服务器。 可以添加多个 AirPrint 服务器。

还可以导入  包含 AirPrint 打印机列表的逗号分隔文件 (.csv)。 此外，在 Intune 中添加 AirPrint 打印机后，还可以导出  此列表。

### <a name="get-the-ip-address-and-path"></a>获取 IP 地址和路径

必须有打印机的 IP 地址、资源路径和端口，才能添加 AirPrinter 服务器。 下面逐步介绍了如何获取此类信息。

1. 在作为 AirPrint 打印机连接到同一本地网络（子网）的 Mac 上，打开“终端”  （路径为“/Applications/Utilities”  ）。
2. 在“终端”应用中，键入“`ippfind`”，再按 Enter。

    记下打印机信息。 例如，可能会返回类似于 `ipp://myprinter.local.:631/ipp/port1` 的内容。 第一部分是打印机名称。 最后一部分 (`ipp/port1`) 是资源路径。

3. 在“终端”中，键入“`ping myprinter.local`”，再按 Enter。

   记下 IP 地址。 例如，可能会返回类似于 `PING myprinter.local (10.50.25.21)` 的内容。

4. 使用 IP 地址和资源路径值。 在此示例中，IP 地址为 `10.50.25.21`，资源路径为 `/ipp/port1`。

## <a name="login-items"></a>登录项

### <a name="settings-apply-to-all-enrollment-types"></a>设置适用范围：所有注册类型

- **文件、文件夹和自定义应用**：添加在用户登录到设备时要打开的文件、文件夹、自定义应用或系统应用的路径  。 系统应用或为组织生成或自定义的应用通常位于 `Applications` 文件夹中，路径类似于 `/Applications/AppName.app`。 

  可以添加多个文件、文件夹和应用。 例如，输入：  
  
  - `/Applications/Calculator.app`
  - `/Applications`
  - `/Applications/Microsoft Office/root/Office16/winword.exe`
  - `/Users/UserName/music/itunes.app`
  
  添加任何应用、文件夹或文件时，请确保输入正确的路径。 并非所有项都位于 `Applications` 文件夹中。 如果用户将某个项从一个位置移到另一个位置，则路径会更改。 当用户登录时，这个移动的项将不会打开。

## <a name="login-window"></a>登录窗口

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>设置适用范围：设备注册和自动设备注册

#### <a name="window-layout"></a>Window 布局

- **在菜单栏中显示其他信息**：选中菜单栏上的时间区域时，选择“允许”可显示主机名和 macOS 版本  。 如果选择“未配置”（默认），则菜单栏上不会显示此信息  。
- **横幅**：输入一条在设备登录屏幕上显示的消息。 例如，输入组织信息、欢迎消息、失物招领信息等。
- **选择登录格式**：选择用户登录设备的方式。测验的方式。 选项包括：
  - **提示输入用户名和密码**（默认值）：要求用户输入用户名和密码。
  - **列出所有用户，提示输入密码**：要求用户从用户列表中选择其用户名，然后输入其密码。 还需配置：

    - **本地用户**：选择“隐藏”则不会在用户列表中显示本地用户帐户，其中可能包含标准帐户和管理员帐户  。 仅显示网络和系统用户帐户。 如果选择“未配置”（默认），会显示用户列表中的本地用户帐户  。
    - **移动帐户**：选择“隐藏”则不会在用户列表中显示移动帐户  。 如果选择“未配置”（默认），会显示用户列表中的移动帐户  。 一些移动帐户可能会显示为网络用户。
    - **网络用户**：选择“显示”会在用户列表中显示网络用户  。 如果选择“未配置”（默认），则不显示用户列表中的网络用户帐户  。
    - **管理员用户**：选择“隐藏”则不在用户列表中显示管理员用户帐户  。 选择“未配置”（默认）则显示用户列表中的管理员用户帐户  。
    - **其他用户**：选择“显示”则列出用户列表中的“其他...”用户   。 选择“未配置”（默认）则不显示用户列表中的其他用户帐户  。

#### <a name="login-screen-power-settings"></a>登录屏幕电源设置

- **关闭按钮**：选择“隐藏”则不会在登录屏幕上显示关机按钮  。 选择“未配置”（默认）则显示关闭按钮  。
- **重启按钮**：选择“隐藏”则不会在登录屏幕上显示重启按钮  。 选择“未配置”（默认）则显示重启按钮  。
- **睡眠按钮**：选择“隐藏”则不会在登录屏幕上显示睡眠按钮  。 选择“未配置”（默认）则显示睡眠按钮  。

#### <a name="other"></a>其他

- **禁止用户从控制台登录**：“禁用”会隐藏用于登录的 macOS 命令行  。 对一般用户“禁用”此设置  。 选择“未配置”（默认）则允许高级用户使用 macOS 命令行登录  。 要进入控制台模式，用户必须在“用户名”字段中输入 `>console`，并且必须在控制台窗口中进行身份验证。

#### <a name="apple-menu"></a>Apple 菜单

用户登录设备后，以下设置会影响他们的操作。

- **禁用关机**：选择“禁用”会阻止用户在其登录后选择“关机”选项   。 选择“未配置”（默认）则允许用户选择设备上的“关机”菜单项   。
- **禁用重启**：选择“禁用”则阻止用户在其登录后选择“重启”选项   。 选择“未配置”（默认）则允许用户选择设备上的“重启”菜单项   。
- **禁用关闭电源**：选择“禁用”则阻止用户在其登录后选择“关闭电源”选项   。 选择“未配置”（默认）则允许用户选择设备上的“关闭电源”菜单项   。
- **禁用注销**（macOS 10.13 及更高版本）：选择“禁用”则阻止用户在其登录后选择“注销”选项   。 选择“未配置”（默认）则允许用户选择设备上的“注销”菜单项   。
- **禁用锁屏**（macOS 10.13 及更高版本）：选择“禁用”则阻止用户在其登录后选择“锁屏”选项   。 选择“未配置”（默认）则允许用户选择设备上的“锁屏”菜单项   。

## <a name="single-sign-on-app-extension"></a>单一登录应用扩展

此功能适用于：

- macOS 10.15 及更高版本

### <a name="settings-apply-to-all-enrollment-types"></a>设置适用范围：所有注册类型 

- **SSO 应用扩展类型**：选择凭据 SSO 应用扩展的类型。 选项包括：

  - **未配置**：不使用应用扩展。 若要禁用应用扩展，请将 SSO 应用扩展类型切换为“未配置”  。
  - **重定向**：使用通用的可自定义重定向应用扩展，通过新式身份验证流执行 SSO。 请务必了解组织的应用扩展的扩展和团队 ID。
  - **凭据**：使用通用的可自定义凭据应用扩展，通过质询和响应身份验证流来执行 SSO。 请务必了解组织的 SSO 应用扩展的扩展 ID 和团队 ID。  
  - **Kerberos**：使用 Apple 的内置 Kerberos 扩展，该扩展包含在 macOS Catalina 10.15 和更高版本中。 此选项是“凭据”  应用扩展的 Kerberos 特定版本。

  > [!TIP]
  > 使用“重定向”  和“凭据”  类型，可以添加自己的配置值以传递扩展。 如果你使用的是“凭据”  ，请考虑使用 Apple 在“Kerberos”  类型中提供的内置配置设置。

- **扩展 ID**（“重定向”和“凭据”）：输入可标识 SSO 应用扩展的程序包标识符，如 `com.apple.ssoexample`。
- **团队 ID**（“重定向”和“凭据”）：输入 SSO 应用扩展的团队标识符。 团队标识符是由 Apple 生成的 10 个字符的字母数字（包含数字和字母）字符串，如 `ABCDE12345`。 

  [找到你的团队 ID](https://help.apple.com/developer-account/#/dev55c3c710c)（打开 Apple 网站）提供了详细信息。

- **领域**（“凭据”和“Kerberos”）：输入身份验证领域的名称。 领域名称应为大写形式，如 `CONTOSO.COM`。 通常情况下，你的领域名称与 DNS 域名相同，但全部为大写形式。

- **域**（“凭据”和“Kerberos”）：输入可通过 SSO 进行身份验证的站点的域名或主机名。 例如，如果你的网站是 `mysite.contoso.com`，则 `mysite` 为主机名，`contoso.com` 为域名。 当用户连接到这些站点中的任何一个时，应用扩展会处理身份验证质询。 通过此身份验证，用户可以使用 Face ID、Touch ID 或 Apple PIN 码/密码登录。

  - 单一登录应用扩展 Intune 配置文件中的所有域都必须是唯一的。 即使使用的是不同类型的 SSO 应用扩展，也不能在任何登录应用扩展配置文件中使用重复的域。
  - 这些域不区分大小写。

- **URL**（仅用于“重定向”）：输入标识提供者的 URL 前缀，重定向应用扩展将代表它们执行 SSO。 当用户重定向到这些 URL 时，SSO 应用扩展将介入并提示 SSO。

  - Intune 单一登录应用扩展配置文件中的所有 URL 都必须是唯一的。 即使使用的是不同类型的 SSO 应用扩展，也不能在任何 SSO 应用扩展配置文件中使用重复的域。
  - URL 必须以 http:// 或 https:// 开头。

- **其他配置**（“重定向”和“凭据”）：输入要传递到 SSO 应用扩展的其他特定于扩展的数据：
  - **键**：输入要添加的项的名称，如 `user name`。
  - **类型**：输入数据的类型。 选项包括：

    - 字符串
    - 布尔：在“配置值”  中，输入 `True` 或 `False`。
    - 整数：在“配置值”  中，输入一个数字。
    
  - **值**：输入数据。
  
  - **添加**：选择此项可添加配置项。

- **密钥链用法**（仅用于“Kerberos”）：选择“阻止”  以防止密码被保存和存储在密钥链中。 如果选择“未配置”  （默认设置），则允许保存密码并将其存储在密钥链中。  
- **Face ID、Touch ID 或密码**（仅用于“Kerberos”）：选择“需要”将强制  用户输入其 Face ID、Touch ID 或 Apple 密码登录到你添加的域。 如果选择“未配置”  （默认设置），则不要求用户使用生物识别或密码进行登录。
- **默认领域**（仅用于“Kerberos”）：选择“启用”  可将输入的“领域”  值设置为默认领域。 如果选择“未配置”  （默认设置），则不设置默认领域。

  > [!TIP]
  > - 如果要在组织中配置多个 Kerberos SSO 应用扩展，请“启用”  此设置。
  > - 如果要使用多个领域，请“启用”  此设置。 它将你输入的“领域”  值设置为默认领域。
  > - 如果只有一个领域，请将其保留为“未配置”  （默认设置）。

- **自动发现**（仅用于“Kerberos”）：设置为“阻止”  时，kerberos 扩展不会自动使用 LDAP 和 DNS 来确定其 Active Directory 站点名称。 如果选择“未配置”  （默认设置），则允许扩展自动查找 Active Directory 站点名称。
- **密码更改**（仅用于“Kerberos”）：“阻止”  设置会阻止用户更改登录到你输入的域时所用的密码。 “未配置”  （默认设置）设置允许更改密码。  
- **密码同步**（仅用于“Kerberos”）：选择“启用”  可将用户的本地密码同步到 Azure AD。 “未配置”  （默认设置）会禁止将密码同步到 Azure AD。 使用此设置作为 SSO 的备选设置或备份。 如果用户使用 Apple 移动帐户登录，则此设置不起作用。
- **Windows Server Active Directory 密码复杂性**（仅用于“Kerberos”）：选择“需要”将  强制用户密码满足 Active Directory 的密码复杂性要求。 有关详细信息，请参阅[密码必须满足复杂性要求](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/password-must-meet-complexity-requirements)。 如果选择“未配置”  （默认设置），将不要求用户满足 Active Directory 的密码要求。
- **最短密码长度**（仅用于“Kerberos”）：输入可以组成用户密码的最小字符数。 如果选择“未配置”  （默认设置），将不强制用户使用最短密码长度。
- **密码重复使用限制**（仅用于“Kerberos”）：输入可以在域上重复使用以前的密码之前，必须使用的新密码数（1 - 24）。 如果选择“未配置”  （默认设置），将不强制输入密码重复使用限制。
- **最短密码期限**（仅用于“Kerberos”）：输入在用户可以更改密码之前，必须在域中使用该密码的天数。 如果选择“未配置”  （默认设置），则不强制输入在更改密码之前使用密码的最短期限。
- **密码过期通知**（仅用于“Kerberos”）：输入在密码过期之前用户收到其密码将过期的通知的天数。 如果选择“未配置”  （默认设置），则使用 `15` 天。
- **密码过期**（仅 Kerberos）：输入在用户必须更改设备密码前设备密码保持有效的天数。 如果选择“未配置”  （默认设置），则表示用户密码永不过期。
- **密码更改 URL**（仅用于“Kerberos”）：输入用户启动 Kerberos 密码更改时启动的 URL。
- **主体名称**（仅用于“Kerberos”）：输入 Kerberos 主体的用户名。 不需要加上领域名称。 例如，在 `user@contoso.com` 中，`user` 是主体名称，`contoso.com` 是领域名称。

  > [!TIP]
  > - 还可以通过输入大括号 `{{ }}` 来使用主体名称中的变量。 例如，若要显示用户名，请输入 `Username: {{username}}`。 
  > - 不过，请注意变量替换，因为变量未在 UI 中验证，并且它们区分大小写。 请确保输入正确的信息。
  
- **Active Directory 站点代码**（仅用于“Kerberos”）：输入 Kerberos 扩展应使用的 Active Directory 站点的名称。 可能不需要更改此值，因为 Kerberos 扩展可能会自动查找 Active Directory 站点代码。
- **缓存名称**（仅用于“Kerberos”）：输入 Kerberos 缓存的通用安全服务 (GSS) 名称。 很可能不需要设置此值。  
- **密码要求消息**（仅用于“Kerberos”）：输入向用户显示的组织密码要求的文本版本。 如果不需要 Active Directory 的密码复杂性要求，或者不输入最小密码长度，则会显示消息。  
- **应用程序包 ID**（仅用于“Kerberos”）：添加  应用程序包标识符，这些标识符应在设备上使用单一登录。 这些应用将被授权访问 Kerberos 票证授予票证（身份验证票证），并在用户访问他们有权访问的服务时对其进行身份验证。
- **域领域映射**（仅用于“Kerberos”）：添加  应映射到领域的域 DNS 后缀。 当主机的 DNS 名称与领域名称不匹配时，使用此设置。 很可能不需要创建此自定义域到领域的映射。
- **PKINIT 证书**（仅用于“Kerberos”）：选择  可用于 Kerberos 身份验证的初始身份验证 (PKINIT) 证书的公钥加密。 可以从已在 Intune 中添加的 [PKCS](../protect/certficates-pfx-configure.md) 或 [SCEP](../protect/certificates-scep-configure.md) 证书中进行选择。 有关证书的详细信息，请参阅[在 Microsoft Intune 中使用证书进行身份验证](../protect/certificates-configure.md)。

## <a name="associated-domains"></a>关联域

在 Intune 中，可以：

- 添加多个应用到域关联。
- 将多个域与同一应用相关联。

此功能适用于：

- macOS 10.15 及更高版本

### <a name="settings-apply-to-all-enrollment-types"></a>设置适用范围：所有注册类型

- **应用 ID**：输入要与网站关联的应用的应用标识符。 应用标识符包括团队 ID 和程序包 ID：`TeamID.BundleID`。

  团队 ID 是由 Apple 生成的 10 个字符的字母数字（包含字母和数字）字符串，如 `ABCDE12345`。 [找到你的团队 ID](https://help.apple.com/developer-account/#/dev55c3c710c) （打开 Apple 网站）提供了详细信息。

  程序包 ID 唯一标识应用，通常采用反向域名表示法格式。 例如，查找器的程序包 ID 是 `com.apple.finder`。 若要查找程序包 ID，请在“终端”中使用 AppleScript：

  `osascript -e 'id of app "ExampleApp"'`

- **域**：输入要与应用关联的网站域。 该域包含服务类型和完全限定的主机名，例如 `webcredentials:www.contoso.com`。

  可以通过在域的最开头位置输入 `*.`（星号通配符和句点）来匹配关联域的所有子域。 必须加上句点。 与通配符域相比，精确的域具有更高的优先级。 因此，如果  在完全限定的子域中找不到匹配项，则会匹配父域中的模式。

  服务类型可以是：

  - **authsrv**：单一登录应用扩展
  - **applink**：通用链接
  - **webcredentials**：密码自动填充

- **添加**：选择此选项可添加应用和关联的域。

> [!TIP]
> 若要进行故障排除，在 macOS 设备上，打开“系统首选项”   > “配置文件”  。 确认所创建的配置文件位于设备配置文件列表中。 如果已列出，请确保配置文件中存在“关联的域配置”  ，并且它包含正确的应用程序 ID 和域。

## <a name="next-steps"></a>后续步骤

[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

另外，还可以在 [iOS/iPadOS](ios-device-features-settings.md) 上配置设备功能。
