---
title: Microsoft Intune 中的 iOS 设备功能设置 - Azure | Microsoft Docs
description: 查看 Microsoft Intune 中所有用于为 iOS 设备配置 AirPrint、主屏幕布局、应用通知、共享设备、单一登录和 Web 内容筛选器的设置。 在设备配置文件中使用这些设置，将 iOS 设备配置为在组织中使用 Apple 的这些功能。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/28/2019
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
ms.openlocfilehash: e3e0ea523d71ff036f1f23c9436c65e105328d8b
ms.sourcegitcommit: 807ab3e35f4d9ffa18655410b7d61e5e772ab348
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73057647"
---
# <a name="ios-and-ipados-device-settings-to-use-common-ios-features-in-intune"></a>用于使用 Intune 中常见 iOS 功能的 iOS 和 iPadOS 设备设置

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune 包括一些内置设置，可便于 iOS 用户在自己的设备上使用各种 Apple 功能。 例如，管理员可以控制 iOS 用户如何使用 AirPrint 打印机、如何向主屏幕上的程序坞和页面添加应用和文件夹、如何显示应用通知、如何在锁定屏幕上显示资产标记详细信息、如何使用单一登录身份验证，以及如何使用证书验证用户身份。

使用这些功能可以控制 iOS 设备，作为移动设备管理 (MDM) 解决方案的一部分。

本文列出了这些设置，并介绍了每个设置的用途。 有关这些功能的详细信息，请参阅[添加 iOS 或 macOS 设备功能设置](../device-features-configure.md)。

## <a name="before-you-begin"></a>在开始之前

[创建 iOS 设备配置文件](../device-features-configure.md)。

> [!NOTE]
> 这些设置适用于不同的注册类型，一些设置应用于所有注册选项。 有关不同注册类型的详细信息，请参阅[iOS 注册](../ios-enroll.md)。

## <a name="airprint"></a>AirPrint

### <a name="settings-apply-to-all-enrollment-types"></a>设置适用于：所有注册类型

> [!NOTE]
> 请确保将所有打印机添加到同一个配置文件。 Apple 禁止多个 AirPrint 配置文件定位于同一设备。

- **IP 地址**：输入打印机的 IPv4 或 IPv6 地址。 如果使用主机名标识打印机，可以通过在“终端”中对打印机执行 ping 操作来获取 IP 地址。 （本文中的）获取 IP 地址和路径提供了更多详细信息。
- **路径**：网络中打印机的路径通常是 `ipp/print`。 （本文中的）获取 IP 地址和路径提供了更多详细信息。
- **端口**：输入 AirPrint 目标的侦听端口。 如果将此属性留空，AirPrint 使用默认端口。 适用于 iOS 11.0 及更高版本。
- **TLS**：选择“启用”可使用传输层安全性 (TLS) 确保 AirPrint 连接安全  。 适用于 iOS 11.0 及更高版本。

若要添加 AirPrint 服务器，可以执行以下操作：

- **添加**：将 AirPrint 服务器添加到列表中。 可以添加多个 AirPrint 服务器。
- 导入  包含此类信息的逗号分隔文件 (.csv)。 或者，**导出**以创建所添加的 AirPrint 服务器的列表。

### <a name="get-server-ip-address-resource-path-and-port"></a>获取服务器 IP 地址、资源路径和端口

必须有打印机的 IP 地址、资源路径和端口，才能添加 AirPrinter 服务器。 下面逐步介绍了如何获取此类信息。

1. 在作为 AirPrint 打印机连接到同一本地网络（子网）的 Mac 上，打开“终端”  （路径为“/Applications/Utilities”  ）。
2. 在“终端”中，键入“`ippfind`”，再按 Enter。

    记下打印机信息。 例如，可能会返回类似于 `ipp://myprinter.local.:631/ipp/port1` 的内容。 第一部分是打印机名称。 最后一部分 (`ipp/port1`) 是资源路径。

3. 在“终端”中，键入“`ping myprinter.local`”，再按 Enter。

   记下 IP 地址。 例如，可能会返回类似于 `PING myprinter.local (10.50.25.21)` 的内容。

4. 使用 IP 地址和资源路径值。 在此示例中，IP 地址为 `10.50.25.21`，资源路径为 `/ipp/port1`。

## <a name="home-screen-layout"></a>主屏幕布局

此功能适用于：

- iOS 9.3 或更高版本

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>设置适用于：自动化设备注册（监督）

### <a name="dock"></a>程序坞

使用“程序坞”  设置最多可以向 iOS 屏幕的程序坞添加六个项或文件夹。 许多设备支持添加的项数更少。 例如，iPhone 设备最多支持添加四个项。 在此示例中，设备上仅显示你添加的前四个项。

最多可以对设备程序坞添加六个  项（应用和文件夹加起来）。

- **添加**：将应用或文件夹添加到设备的程序坞。
- **类型**：添加应用或文件夹：  

  - **应用**：选择此选项可向屏幕上的程序坞添加应用。 输入：

    - **应用名**：输入应用的名称。 此名称可便于你在 Azure 门户中参考。 它不  会显示在 iOS 设备上。
    - **应用程序包 ID**：输入应用的捆绑 ID。 有关一些示例，请参阅[内置 iOS 应用的捆绑 ID](bundle-ids-built-in-ios-apps.md)。

  - **文件夹**：选择此选项可向屏幕上的程序坞添加文件夹。

    添加到文件夹中页面的应用按照列表中的相同顺序从左向右排列。 如果添加的应用数超过了页面能够容纳的量，应用会移到其他页面。

    - **文件夹名称**：输入文件夹的名称。 此名称在设备上向用户显示。
    - **页面列表**：添加一个页面，并输入以下属性： 

      - **页名称**：输入页面的名称。 此名称可便于你在 Azure 门户中参考。 它不  会显示在 iOS 设备上。
      - **应用名**：输入应用的名称。 此名称可便于你在 Azure 门户中参考。 它不  会显示在 iOS 设备上。
      - **应用程序包 ID**：输入应用的捆绑 ID。 有关一些示例，请参阅[内置 iOS 应用的捆绑 ID](bundle-ids-built-in-ios-apps.md)。

      最多可以对设备程序坞添加 20  个页面。

> [!NOTE]
> 使用 Dock 设置添加图标时，将锁定主屏幕上的图标和页面，并且无法移动。 这可能是 iOS 和 Apple 的 MDM 策略的固有设计。

#### <a name="example"></a>示例

在下面的示例中，程序坞屏幕仅显示“Safari”、“邮件”和“股市”应用。 “邮件”应用被选为显示自己的属性：

![示例 iOS 停靠设置](./media/ios-device-features-settings/FfFiUcP.png)

在你向 iPhone 分配策略后，程序坞如下图所示：

![iPhone 上的示例 iOS 停靠布局](./media/ios-device-features-settings/bAgCe8F.png)

### <a name="pages"></a>页面

添加要在主屏幕上显示的页面，以及要在每个页面上显示的应用。 添加到页面中的应用按照列表中的相同顺序从左向右排列。 如果添加的应用数超过了页面能够容纳的量，应用会移到其他页面。

> [!TIP]
> 若要对任何主屏幕和页面列表中的项重新排序，可以拖放这些项。

最多可以在设备上添加 40  个页面。

- **页面列表**：添加一个页面，并输入以下属性： 

  - **页名称**：输入页面的名称。 此名称可便于你在 Azure 门户中参考，不  会显示在 iOS 设备上。

  最多可以在设备上添加 60  个项（应用和文件夹加起来）。

  - **添加**：将应用或文件夹添加到设备的页面。

    - **类型**：添加应用或文件夹：  

      - **应用**：选择此选项可向屏幕上的页面添加应用。 此外请输入：

        - **应用名**：输入应用的名称。 此名称可便于你在 Azure 门户中参考。 它不  会显示在 iOS 设备上。
        - **应用程序包 ID**：输入应用的捆绑 ID。 有关一些示例，请参阅[内置 iOS 应用的捆绑 ID](bundle-ids-built-in-ios-apps.md)。

      - **文件夹**：选择此选项可向屏幕上的程序坞添加文件夹。

        添加到文件夹中页面的应用按照列表中的相同顺序从左向右排列。 如果添加的应用数超过了页面能够容纳的量，应用会移到其他页面。

        - **文件夹名称**：输入文件夹的名称。 此名称在设备上向用户显示。
        - **添加**：将页面添加到文件夹。 同时输入以下属性：

          - **页名称**：输入页面的名称。 此名称可便于你在 Azure 门户中参考。 它不  会显示在 iOS 设备上。
          - **应用名**：输入应用的名称。 此名称可便于你在 Azure 门户中参考。 它不  会显示在 iOS 设备上。
          - **应用程序包 ID**：输入应用的捆绑 ID。 有关一些示例，请参阅[内置 iOS 应用的捆绑 ID](bundle-ids-built-in-ios-apps.md)。

#### <a name="example"></a>示例

在下面的示例中，添加了名为“Contoso”  的新页面。 此页面显示“查找朋友”和“设置”应用。 “设置”应用被选为显示自己的属性：

![iOS 主屏幕设置示例](./media/ios-device-features-settings/Jc2OxyX.png)

在你向 iPhone 分配策略后，页面如下图所示：

![使用修改后的主屏幕的 iOS 设备](./media/ios-device-features-settings/Bd37PHa.png)

## <a name="app-notifications"></a>应用通知

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>设置适用于：自动化设备注册（监督）

- **添加**：添加应用通知：

    ![在 Intune 中的 iOS 配置文件内添加应用通知](./media/ios-device-features-settings/ios-macos-app-notifications.png)

  - **应用程序包 ID**：输入要添加的应用的“应用程序包 ID”  。 有关一些示例，请参阅[内置 iOS 应用的捆绑 ID](bundle-ids-built-in-ios-apps.md)。
  - **应用名**：输入要添加的应用名称。 此名称可便于你在 Azure 门户中参考。 它不  会显示在设备上。
  - **发布者**：输入要添加的应用的发布者。 此名称可便于你在 Azure 门户中参考。 它不  会显示在设备上。
  - **通知**：“启用”或“禁用”应用向设备发送通知   。
    - **在通知中心中显示**：“启用”可允许应用在设备通知中心显示通知  。 选择“禁用”  可阻止应用在设备通知中心内显示通知。
    - **在锁定屏幕中显示**：选择“启用”可在设备锁定屏幕上看到应用的通知  。 选择“禁用”  可阻止应用在锁定屏幕中显示通知。
    - **警报类型**：选择在设备解锁后的通知显示方式。 选项包括：
      - **无**：不显示通知。
      - **横幅**：短暂显示包含通知的横幅。
      - **模式**：显示通知，并且用户必须先手动关闭通知，然后才能继续使用设备。
    - **应用图标上的锁屏提醒**：选择“启用”可向应用图标添加锁屏提醒  。 通知提醒表示应用已发送通知。
    - **声音**：选择“启用”可在通知送达时播放声音  。

## <a name="lock-screen-message"></a>锁屏界面消息

此功能适用于：

- iOS 9.3 及更高版本

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>设置适用于：自动化设备注册（监督）

- **资产标记信息**：输入有关设备的资产标记的信息。 例如，输入 `Owned by Contoso Corp` 或 `Serial Number: {{serialnumber}}`。

  输入的文本显示在设备上的登录窗口和锁定屏幕中。

- **锁定屏幕脚注**：输入一个可帮助在设备丢失或被盗时将其找回的注释。 可以输入所需的任何文本。 例如，输入类似于 `If found, call Contoso at ...` 的内容。

  设备令牌还可以用于向这些字段添加特定于设备的信息。 例如，若要显示序列号，请输入 `Serial Number: {{serialnumber}}`。 在锁屏上，文本显示类似于 `Serial Number 123456789ABC`。 输入变量时，请务必使用大括号 `{{ }}`。 [应用配置令牌](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list)包含可用变量的列表。 还可以使用 `deviceName` 或任何其他特定于设备的值。

  > [!NOTE]
  > 变量不在 UI 中进行验证，且区分大小写。 因此，可能会看到使用不正确输入保存的配置文件。 例如，如果输入 `{{DeviceID}}` 而不是 `{{deviceid}}`，则显示文本字符串而不是设备的唯一 ID。 请确保输入正确的信息。

## <a name="single-sign-on"></a>单一登录

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>设置适用于：设备注册，自动设备注册（监督）

- **来自 AAD 的用户名属性**：Intune 为 Azure AD 中的每个用户寻找此属性。 然后，Intune 先填充相应字段（如“UPN”），再生成在设备上安装的 XML。 选项包括：

  - **用户主体名称**：将按以下方式分析 UPN：

    ![用户名属性](./media/ios-device-features-settings/User-name-attribute.png)

    还可以使用在“领域”文本框中键入的文本覆盖该领域  。

    例如，Contoso 有多个区域，包括欧洲、亚洲和北美。 Contoso 希望亚洲用户使用 SSO，且应用要求采用 `username@asia.contoso.com` 格式的 UPN。 在你选择“用户主体名称”  后，系统从 Azure AD 中获取每个用户的领域，即 `contoso.com`。 因此，对于亚洲用户，选择“用户主体名称”  ，再输入“`asia.contoso.com`”。 最终用户的 UPN 变成 `username@asia.contoso.com`，而不是 `username@contoso.com`。

  - **Intune 设备 ID**：Intune 会自动选择 Intune 设备 ID。

    默认情况下，应用只需使用设备 ID。 但如果应用使用领域和设备 ID，你可以在“领域”文本框中键入领域。

    > [!NOTE]
    > 如果使用设备 ID，则默认将领域留空。

  - **Azure AD 设备 ID**

- **领域**：输入 URL 的域部分。 例如，输入 `contoso.com`。
- **使用单一登录的 URL 前缀**：添加组织中要求用户进行单一登录身份验证的任何 URL  。

  例如，用户连接到任何这些站点时，iOS 设备会使用单一登录凭据。 用户不需要输入任何其他凭据。 如果已启用多重身份验证，用户必须输入第二重身份验证凭据。

  > [!NOTE]
  > 这些 URL 必须采用正确格式化的 FQDN。 Apple 要求这些 URL 必须采用 `http://<yourURL.domain>` 格式。

  匹配模式的 URL 必须以 `http://` 或 `https://` 开头。 由于运行的是简单字符串匹配，因此 `http://www.contoso.com/` URL 前缀与 `http://www.contoso.com:80/` 不匹配。 在 iOS 10.0 或更高版本中，可使用一个通配符 \* 输入所有匹配值。 例如，`http://*.contoso.com/` 同时匹配 `http://store.contoso.com/` 和 `http://www.contoso.com`。

  `http://.com` 和 `https://.com` 模式分别匹配所有 HTTP 和 HTTPS URL。

- **使用单一登录的应用**：在可以使用单一登录的用户设备上添加应用  。

  `AppIdentifierMatches` 数组必须包含与应用捆绑 ID 匹配的字符串。 这些字符串可以是完全匹配项（如 `com.contoso.myapp`），也可以使用 \* 通配符输入捆绑 ID 的前缀匹配项。 通配符必须位于句点字符 (.) 后面，并只能在字符串末尾出现一次（如 `com.contoso.*`）。 如果包括通配符，则程序包 ID 以前缀开头的任何应用都将被授予对帐户的访问权限。

  使用应用名称输入一个用户友好名称，帮助识别捆绑 ID  。

- **凭据续订证书**：如果使用证书（而不是密码）进行身份验证，选择现有 SCEP 或 PFX 证书作为身份验证证书。 通常，此证书是针对其他配置文件（如 VPN、Wi-Fi 或电子邮件）部署到用户的相同证书。

## <a name="web-content-filter"></a>Web 内容筛选器

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>设置适用于：自动化设备注册（监督）

- **筛选器类型**：选择以允许特定网站。 选项包括：

  - **配置 URL**：使用 Apple 的内置 Web 筛选器来查找成人术语，包括猥亵和露骨色情语言。 此功能在网页加载时评估每个网页，并发现和阻止不适合的内容。 还可以添加不希望筛选器检查的 URL。 或屏蔽特定 URL，无论 Apple 的筛选器设置如何。

    - **允许的 URL**：添加允许的 URL  。 这些 URL 可绕过 Apple 的 Web 筛选器。

        > [!NOTE]
        > 输入的 URL 是你不希望 Apple Web 筛选器评估的 URL。 这些 URL 不是允许的网站列表。 若要创建允许的网站列表，请将“筛选器类型”  设置为“仅特定网站”  。

    - **阻止的 URL**：添加要阻止打开的 URL，无论 Apple Web 筛选器设置如何  。

  - **仅限特定网站**（仅适用于 Safari Web 浏览器）：向 Safari 浏览器的书签添加这些 URL。 用户只能  访问这些网站；无法打开其他任何网站。 仅在知道用户可以访问的 URL 的确切列表时使用此选项。

    - **URL**：输入要允许的网站 URL。 例如，输入 `https://www.contoso.com`。
    - **书签路径**： Apple 更改了此设置。 所有书签都将进入 "**已批准的站点**" 文件夹。 书签不会进入您输入的书签路径。
    - **标题**：为书签输入描述性标题。

    如果未输入任何 URL，最终用户无法访问任何网站（`microsoft.com`、`microsoft.net` 和 `apple.com` 除外）。 Intune 自动允许这些 URL。

## <a name="single-sign-on-app-extension"></a>单一登录应用扩展

此功能适用于：

- iOS 13.0 及更高版本
- iPadOS 13.0 及更高版本

### <a name="settings-apply-to-all-enrollment-types"></a>设置适用于：所有注册类型

- **SSO 应用扩展类型**：选择凭据 SSO 应用扩展的类型。 选项包括：

  - **未配置**：不使用应用扩展。 若要禁用应用扩展，可将 SSO 应用扩展类型从**Kerberos**或**凭据**切换为 "**未配置**"。
  - **Credential**：使用通用的可自定义凭据应用扩展来执行 SSO。 确保你知道组织的 SSO 应用扩展的扩展 ID。
  - **Kerberos**：使用 Apple 的内置 Kerberos 扩展，该扩展包含在 iOS 13.0 （和更高版本）和 iPadOS 13.0 （和更高版本）上。 此选项为**凭据**应用扩展的 Kerberos 特定版本。

  > [!TIP]
  > 使用**凭据**类型时，你可以添加自己的配置值以通过扩展。 请考虑使用 Apple 在**Kerberos**类型中提供的内置配置设置。

- **扩展 ID** （仅限凭据）：输入标识 SSO 应用扩展的绑定标识符，如 `com.apple.extensiblesso`。
- **团队 ID** （仅凭据）：输入 SSO 应用扩展的团队标识符。 团队标识符是由 Apple 生成的10个字符的字母数字（数字和字母）字符串（例如 `ABCDE12345`）。 不需要团队 ID。

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

- **主体名称**（仅 Kerberos）：输入 Kerberos 主体的用户名。 不需要包含领域名称。 例如，在 `user@contoso.com` 中，`user` 为主体名称，`contoso.com` 是领域名称。
- **Active Directory 站点代码**（仅 kerberos）：输入 Kerberos 扩展应使用 Active Directory 站点的名称。 您可能不需要更改此值，因为 Kerberos 扩展可能会自动查找 Active Directory 站点代码。
- **缓存名称**（仅 Kerberos）：输入 kerberos 缓存的一般安全服务（GSS）名称。 您很可能不需要设置此值。
- **应用程序包 id** （仅 Kerberos）：**添加**应用捆绑标识符，这些标识符应在设备上使用单一登录。 这些应用将被授予对 Kerberos 票证授予票证（身份验证票证）的访问权限，并对用户进行身份验证，以对他们有权访问的服务进行身份验证。
- **域领域映射**（仅 Kerberos）：**添加**应映射到领域的域 DNS 后缀。 当主机的 DNS 名称与领域名称不匹配时，请使用此设置。 您很可能不需要创建此自定义的域到领域映射。

## <a name="wallpaper"></a>壁纸

无映像的配置文件分配给具有现有映像的设备时，可能会遇到意外行为。 例如，创建无映像的配置文件。 此配置文件分配给已有映像的设备。 在此方案中，映像可能会变为设备默认值，或者初始映像可能保留在设备上。 此行为受 Apple 的 MDM 平台控制和限制。

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>设置适用于：自动化设备注册（监督）

- **壁纸显示位置**：选择要在设备上显示图像的位置。 选项包括：
  - **未配置**：自定义图像不会添加到设备。 设备使用操作系统默认图像。
  - **锁屏界面**：向锁屏界面添加图像。
  - **主屏幕**：向主屏幕添加图像。
  - **锁屏界面和主屏幕**：在锁屏界面和主屏幕上使用相同的图像。
- **壁纸图像**：上传要使用的现有 .png、.jpg 或 .jpeg 图像。 请确保文件小于 750KB。 还可以删除  已添加的图像。

> [!TIP]
> 若要在锁定屏幕和主屏幕上显示不同的图像，请创建包含锁定屏幕图像的配置文件， 以及另一个包含主屏幕图像的配置文件。 将两个配置文件分配到 iOS 用户组或设备组。

## <a name="next-steps"></a>后续步骤

[分配配置文件](../device-profile-assign.md)并[监视其状态](../device-profile-monitor.md)。

还可以为 [macOS](macos-device-features-settings.md) 设备创建设备功能配置文件。
