---
title: Microsoft Intune 中的 macOS 设备功能设置 - Azure | Microsoft Docs
description: 查看用于为 macOS 设备配置 AirPrint 的设置，自定义“登录”窗口以显示或隐藏 Microsoft Intune 中的电源按钮。 请参阅获取网络中 AirPrint 服务器的 IP 地址、路径和端口设置的步骤。 在设备配置配置文件中使用这些设置来配置 macOS 设备功能。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/02/2019
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
ms.openlocfilehash: 17d0baeeb6b193be6acf8d6087c26a66b18642c5
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506669"
---
# <a name="macos-device-feature-settings-in-intune"></a>Intune 中的 macOS 设备功能设置

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune 包含一些内置设置，用于自定义 macOS 设备上的功能。 例如，管理员可以添加 AirPrint 打印机、选择用户登录的方式、配置电源控制、使用单一登录身份验证等。

使用这些功能可以控制 macOS 设备，作为移动设备管理 (MDM) 解决方案的一部分。

本文列出了这些设置，并介绍了每个设置的用途。 它还列出了使用“终端”应用（仿真器）获取 AirPrint 打印机的 IP 地址、路径和端口的步骤。 有关设备功能的详细信息，请参阅[添加 iOS 或 macOS 设备功能设置](device-features-configure.md)。

## <a name="before-you-begin"></a>在开始之前

[创建 macOS 设备配置文件](device-features-configure.md)。

> [!NOTE]
> 这些设置适用于不同的注册类型，一些设置应用于所有注册选项。 有关不同注册类型的详细信息，请参阅[macOS 注册](../enrollment/macos-enroll.md)。

## <a name="airprint"></a>AirPrint

### <a name="settings-apply-to-device-enrollment"></a>设置适用于：设备注册

- **IP 地址**：输入打印机的 IPv4 或 IPv6 地址。 如果使用主机名标识打印机，可以通过在“终端”应用中对打印机执行 ping 操作来获取 IP 地址。 （本文中的）[获取 IP 地址和路径](#get-the-ip-address-and-path)提供了更多详细信息。
- **路径**：输入打印机的路径。 网络中打印机的路径通常是 `ipp/print`。 （本文中的）[获取 IP 地址和路径](#get-the-ip-address-and-path)提供了更多详细信息。
- **端口**（iOS 11.0 及更高版本）：输入 AirPrint 目标的侦听端口。 如果将此属性留空，AirPrint 使用默认端口。
- **TLS**（iOS 11.0 及更高版本）：选择“启用”可使用传输层安全性 (TLS) 确保 AirPrint 连接安全  。

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

### <a name="settings-apply-to-all-enrollment-types"></a>设置适用于：所有注册类型

- **文件、文件夹和自定义应用**：在用户登录到设备时，**添加**要打开的文件、文件夹、自定义应用或系统应用的路径。 系统应用或为组织生成或自定义的应用通常位于 `Applications` 文件夹中，路径类似于 `/Applications/AppName.app`。 

  可以添加多个文件、文件夹和应用。 例如，输入：  
  
  - `/Applications/Calculator.app`
  - `/Applications`
  - `/Applications/Microsoft Office/root/Office16/winword.exe`
  - `/Users/UserName/music/itunes.app`
  
  添加任何应用、文件夹或文件时，请确保输入正确的路径。 并非所有项都位于 `Applications` 文件夹中。 如果用户将项从一个位置移到另一个位置，则路径会更改。 当用户登录时，此移动的项目将不会打开。

## <a name="login-window"></a>登录窗口

### <a name="settings-apply-to-device-enrollment"></a>设置适用于：设备注册

#### <a name="window-layout"></a>Window 布局

- **在菜单栏中显示其他信息**：选中菜单栏上的时间区域时，选择“允许”可显示主机名和 macOS 版本  。 如果选择“未配置”（默认），则菜单栏上不会显示此信息  。
- **横幅**：输入一条在设备登录屏幕上显示的消息。 例如，输入组织信息、欢迎消息、失物招领信息等。
- **选择登录格式**：选择用户登录设备的方式。 选项包括：
  - **提示输入用户名和密码**（默认）：要求用户输入用户名和密码。
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

### <a name="settings-apply-to-all-enrollment-types"></a>设置适用于：所有注册类型 

- **SSO 应用扩展类型**：选择凭据 SSO 应用扩展的类型。 保存 SSO 应用扩展配置文件时，无法更改 SSO 应用扩展类型。 选项包括：

  - **未配置**：不使用应用扩展。 若要禁用 SSO 应用扩展，请将 SSO 应用扩展类型从**Kerberos**或**凭据**切换为 "**未配置**"。
  - **Credential**：使用通用的可自定义凭据应用扩展来使用 SSO。 请确保了解组织的 SSO 应用扩展的扩展 ID 和团队 ID。  
  - **Kerberos**：使用 Apple 的内置 Kerberos 扩展，其中包含在 macOS Catalina 10.15 和更高版本中。 此选项为**凭据**应用扩展的 Kerberos 特定版本。

  > [!TIP]
  > 使用**凭据**类型时，你可以添加自己的配置值以通过扩展。 请考虑使用 Apple 在**Kerberos**类型中提供的内置配置设置。

- **扩展 ID** （仅限凭据）：输入标识 SSO 应用扩展的绑定标识符，如 `com.apple.ssoexample`。
- **团队 ID** （仅凭据）：输入 SSO 应用扩展的团队标识符。 团队标识符是由 Apple 生成的10个字符的字母数字（数字和字母）字符串（例如 `ABCDE12345`）。 

  [找到你的团队 ID](https://help.apple.com/developer-account/#/dev55c3c710c) （打开 Apple 网站）以了解详细信息。

- **领域**：输入 Kerberos 领域的名称。 领域名称应大写，如 `CONTOSO.COM`。 通常情况下，你的领域名称与 DNS 域名相同，但全部为大写。
- **域**：输入可以通过 SSO 进行身份验证的站点的域名或主机名。 例如，如果你的网站 `mysite.contoso.com`，则 `mysite` 为主机名，`contoso.com` 是域名。 当用户连接到这些站点中的任何一个时，应用扩展会处理身份验证质询。 此身份验证允许用户使用人脸 ID、Touch ID 或 Apple pincode/密码进行登录。

  - 单一登录应用扩展 Intune 配置文件中的所有域都必须是唯一的。 即使使用的是不同类型的 SSO 应用扩展，也不能在任何登录应用扩展配置文件中重复域。
  - 这些域不区分大小写。

- **其他配置**（仅凭据）：输入要传递到 SSO 应用扩展的其他特定于扩展的数据：
  - **配置项**：输入要添加的项的名称，如 `user name`。
  - **值类型**：输入数据的类型。 选项包括：

    - 字符串
    - 布尔：在**配置值**中，输入 `True` 或 `False`。
    - 整数：在 "**配置值**" 中，输入一个数字。
    
  - **配置值**：输入数据。
  
  - **添加**：选择此项可添加配置项。

- **密钥链用法**（仅 Kerberos）：选择 "**阻止**" 以阻止密码保存并存储在密钥链中。 "**未配置**" （默认值）允许保存密码并将其存储在密钥链中。  
- 人**脸 id、TOUCH id 或密码**（仅 Kerberos）：**要求**用户输入其人脸 id、Touch id 或 Apple 密码，以登录到你添加的域。 "**未配置**" （默认）不要求用户使用生物识别或密码进行登录。
- **默认领域**（仅 Kerberos）：选择 "**启用**" 可将输入的**领域**值设置为默认领域。 **未配置**（默认值）不设置默认领域。

  > [!TIP]
  > - 如果要在组织中配置多个 Kerberos SSO 应用扩展，请**启用**此设置。
  > - 如果要使用多个领域，请**启用**此设置。 它将你输入的**领域**值设置为默认领域。
  > - 如果只有一个领域，请将其保留为 "**未配置**" （默认值）。

- **自动发现**（仅 Kerberos）：设置为 "**阻止**" 时，kerberos 扩展不会自动使用 LDAP 和 DNS 来确定其 Active Directory 站点名称。 "**未配置**" （默认值）允许扩展自动查找 Active Directory 站点名称。
- **密码更改**（仅 Kerberos）：**阻止**用户更改登录到所输入域时所用的密码。 "**未配置**" （默认）允许密码更改。  
- **密码同步**（仅 Kerberos）：选择 "**启用**" 将用户的本地密码同步到 Azure AD。 **未配置**（默认）禁用要 Azure AD 的密码同步。 使用此设置作为备用或备份到 SSO。 如果用户使用 Apple mobile 帐户登录，则此设置不起作用。
- **Windows Server Active Directory 密码复杂性**（仅 Kerberos）：选择 "**需要**强制用户密码" 以满足 Active Directory 的密码复杂性要求。 有关详细信息，请参阅[密码必须满足复杂性要求](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/password-must-meet-complexity-requirements)。 "**未配置**" （默认）不要求用户满足 Active Directory 的密码要求。
- **最短密码长度**（仅限 Kerberos）：输入可以组成用户密码的最小字符数。 "**未配置**" （默认值）不会强制用户使用最短密码长度。
- **密码重复使用限制**（仅 Kerberos）：输入必须使用的新密码数（1-24），才能在域上重复使用以前的密码。 **未配置**（默认）不强制使用密码重用限制。
- **最短密码期限**（仅限 Kerberos）：输入在用户可以更改密码之前，必须在域中使用该密码的天数。 "**未配置**" （默认值）在更改密码之前不会强制使用密码的最短期限。
- **密码过期通知**（仅 Kerberos）：输入在密码过期之前用户收到其密码将过期的通知的天数。 **未配置**（默认）使用 `15` 天。
- **密码过期**（仅 Kerberos）：输入必须更改设备密码前的天数。 "**未配置**" （默认值）表示用户密码永不过期。
- **主体名称**（仅 Kerberos）：输入 Kerberos 主体的用户名。 不需要包含领域名称。 例如，在 `user@contoso.com` 中，`user` 为主体名称，`contoso.com` 是领域名称。
- **Active Directory 站点代码**（仅 kerberos）：输入 Kerberos 扩展应使用 Active Directory 站点的名称。 您可能不需要更改此值，因为 Kerberos 扩展可能会自动查找 Active Directory 站点代码。
- **缓存名称**（仅 Kerberos）：输入 kerberos 缓存的一般安全服务（GSS）名称。 您很可能不需要设置此值。  
- **密码要求消息**（仅 Kerberos）：输入向用户显示的组织密码要求的文本版本。 如果不需要 Active Directory 的密码复杂性要求，或者不输入最小密码长度，则会显示消息。  
- **应用程序包 id** （仅 Kerberos）：**添加**应用捆绑标识符，这些标识符应在设备上使用单一登录。 这些应用将被授予对 Kerberos 票证授予票证（身份验证票证）的访问权限，并对用户进行身份验证，以对他们有权访问的服务进行身份验证。
- **域领域映射**（仅 Kerberos）：**添加**应映射到领域的域 DNS 后缀。 当主机的 DNS 名称与领域名称不匹配时，请使用此设置。 您很可能不需要创建此自定义的域到领域映射。

## <a name="associated-domains"></a>关联域

在 Intune 中，可以：

- 添加多个应用到域关联。
- 将多个域与同一应用相关联。

此功能适用于：

- macOS 10.15 及更高版本

### <a name="settings-apply-to-all-enrollment-types"></a>设置适用于：所有注册类型

- **应用 ID**：输入要与网站关联的应用的应用标识符。 应用标识符包括团队 ID 和捆绑 ID： `TeamID.BundleID`。

  团队 ID 是由 Apple 为应用开发人员生成的由10个字符组成的字母数字（字母和数字）字符串，如 `ABCDE12345`。 [找到你的团队 ID](https://help.apple.com/developer-account/#/dev55c3c710c)   （打开 Apple 网站）中包含详细信息。

  捆绑 ID 唯一标识应用，通常采用反向域名表示法格式。 例如，查找器的绑定 ID 是 `com.apple.finder`。 若要查找捆绑 ID，请使用终端中的 AppleScript：

  `osascript -e 'id of app "ExampleApp"'`

- **域**：输入要与应用关联的网站域。 域包括服务类型和完全限定的主机名，例如 `webcredentials:www.contoso.com`。

  您可以通过在域开始之前输入 `*.` （星号通配符和句点）来匹配关联域的所有子域。 时间段是必需的。 与通配符域相比，精确的域具有更高的优先级。 因此，*如果*在完全限定的子域中找不到匹配项，则会匹配父域中的模式。

  服务类型可以是：

  - **authsrv**：单一登录应用扩展
  - **applink**：通用链接
  - **webcredentials**：密码自动填充

- **添加**：选择此添加应用和关联的域。

> [!TIP]
> 若要进行故障排除，请在 macOS 设备上，打开 "**系统首选项**"  > **配置文件**。 确认所创建的配置文件位于 "设备配置文件" 列表中。 如果已列出，请确保关联的**域配置**在配置文件中，并且包含正确的应用程序 ID 和域。

## <a name="next-steps"></a>后续步骤

[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

你还可以在[iOS](ios-device-features-settings.md)上配置设备功能。
