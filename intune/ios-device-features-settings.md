---
title: Microsoft Intune 中的 iOS 设备功能设置 - Azure | Microsoft Docs
description: 查看 Microsoft Intune 中所有用于为 iOS 设备配置 AirPrint、主屏幕布局、应用通知、共享设备、单一登录和 Web 内容筛选器的设置。 在设备配置文件中使用这些设置，将 iOS 设备配置为在组织中使用这些不同的 Apple 功能。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/30/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4a2acd4e54329dbfd43e468a3a0f3b1fa62eee44
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55850099"
---
# <a name="ios-device-feature-settings-in-intune"></a>Intune 中的 iOS 设备功能设置

Intune 包括一些内置设置，可便于 iOS 用户在自己的设备上使用各种 Apple 功能。 例如，管理员可以控制 iOS 用户如何使用 AirPrint 打印机、如何向主屏幕上的程序坞和页面添加应用和文件夹、如何显示应用通知、如何在锁定屏幕上显示资产标记详细信息、如何使用单一登录身份验证，以及如何使用证书验证用户身份。

本文列出了这些设置，并介绍了每个设置的用途。

## <a name="before-you-begin"></a>在开始之前

[创建 iOS 设备配置文件](device-features-configure.md#create-a-device-profile)。

## <a name="airprint-settings"></a>AirPrint 设置

借助此功能，iOS 用户可使用已知 AirPrint 打印机进行打印。

1. 选择“设置”中的“AirPrint”。 输入 AirPrint 服务器的以下属性：

    - **IP 地址**：输入打印机的 IPv4 或 IPv6 地址。 如果使用主机名标识打印机，可以通过在“终端”中对打印机执行 ping 操作来获取 IP 地址。 （本文中的）[获取 IP 地址和路径](#get-the-ip-address-and-path)提供了更多详细信息。
    - **路径**：网络中打印机的路径通常是 `ipp/print`。 （本文中的）[获取 IP 地址和路径](#get-the-ip-address-and-path)提供了更多详细信息。
    - **端口**：输入 AirPrint 目标的侦听端口。 如果将此属性留空，AirPrint 使用默认端口。 适用于 iOS 11.0 及更高版本。
    - **TLS**：选择“启用”可使用传输层安全性 (TLS) 确保 AirPrint 连接安全。 适用于 iOS 11.0 及更高版本。

2. 选择“添加”。 此时，AirPrint 服务器添加到列表中。 可以添加多个 AirPrint 服务器。

    还可以导入包含此类信息的逗号分隔文件 (.csv)。 创建列表后，还可以导出 AirPrint 服务器列表。

3. 完成后，选择“确定”，以保存列表。

必须有打印机的 IP 地址、资源路径和端口，才能添加 AirPrinter 服务器。 下面逐步介绍了如何获取此类信息。

1. 在作为 AirPrint 打印机连接到同一本地网络（子网）的 Mac 上，打开“终端”（路径为“/Applications/Utilities”）。
2. 在“终端”中，键入“`ippfind`”，再按 Enter。

    记下打印机信息。 例如，可能会返回类似于 `ipp://myprinter.local.:631/ipp/port1` 的内容。 第一部分是打印机名称。 最后一部分 (`ipp/port1`) 是资源路径。

3. 在“终端”中，键入“`ping myprinter.local`”，再按 Enter。

   记下 IP 地址。 例如，可能会返回类似于 `PING myprinter.local (10.50.25.21)` 的内容。

4. 使用 IP 地址和资源路径值。 在此示例中，IP 地址为 `10.50.25.21`，资源路径为 `/ipp/port1`。

## <a name="home-screen-layout-settings"></a>主屏幕布局设置

这些设置配置 iOS 设备的程序坞和主屏幕中的应用布局和文件夹。 iOS 设备必须处于监督模式，并运行 iOS 9.3 或更高版本，才能使用此功能。

### <a name="dock"></a>程序坞

使用“程序坞”设置最多可以向 iOS 屏幕的程序坞添加六个项或文件夹。 许多设备支持添加的项数更少。 例如，iPhone 设备最多支持添加四个项。 在此示例中，设备上仅显示你添加的前四个项。

1. 在“设置”中，依次选择“主屏幕布局(仅监督模式)” > “程序坞” > “添加”。 最多可以对设备程序坞添加六个项（应用和文件夹加起来）。
2. 在“类型”中，选择添加“应用”或“文件夹”。

    - **添加应用**：选择此选项可向屏幕上的程序坞添加应用。 输入：

      - **应用名称**：输入应用程序的名称。 此名称可便于你在 Azure 门户中参考。 它不会显示在 iOS 设备上。
      - **应用捆绑 ID**：输入应用的捆绑 ID。 有关一些示例，请参阅（本文中的）[内置 iOS 应用的捆绑 ID](#bundle-ids-for-built-in-ios-apps)。

      选择“确定”，保存所做更改。

    - **添加文件夹**：选择此选项可向屏幕上的程序坞添加文件夹。 

      添加到文件夹中页面的应用按照列表中的相同顺序从左向右排列。 如果添加的应用数超过了页面能够容纳的量，应用会移到其他页面。

      1. 填写“文件夹名称”。 此名称在设备上向用户显示。
      2. 选择“添加”，并输入以下属性：

          - **页面名称**：输入页面名称。 此名称可便于你在 Azure 门户中参考。 它不会显示在 iOS 设备上。
          - **应用名称**：输入应用程序的名称。 此名称可便于你在 Azure 门户中参考。 它不会显示在 iOS 设备上。
          - **应用捆绑 ID**：输入应用的捆绑 ID。 有关一些示例，请参阅（本文中的）[内置 iOS 应用的捆绑 ID](#bundle-ids-for-built-in-ios-apps)。

      3. 选择“添加”。 最多可以对设备程序坞添加 20 个页面。
      4. 选择“确定”，保存所做更改。

#### <a name="example"></a>示例

在下面的示例中，程序坞屏幕仅显示“Safari”、“邮件”和“股市”应用。 “邮件”应用被选为显示自己的属性：

![示例 iOS 停靠设置](./media/FfFiUcP.png)

在你向 iPhone 分配策略后，程序坞如下图所示：

![iPhone 上的示例 iOS 停靠布局](./media/bAgCe8F.png)

### <a name="pages"></a>页面

添加要在主屏幕上显示的页面，以及要在每个页面上显示的应用。 添加到页面中的应用按照列表中的相同顺序从左向右排列。 如果添加的应用数超过了页面能够容纳的量，应用会移到其他页面。

> [!TIP]
> 若要对任何主屏幕和页面列表中的项重新排序，可以拖放这些项。

1. 在“设置”中，依次选择“主屏幕布局(仅监督模式)” > “页面” > “添加”。 最多可以在设备上添加 40 个页面。
2. 填写“页面名称”。 此名称可便于你在 Azure 门户中参考，不会显示在 iOS 设备上。 

    选择“添加”。 最多可以在设备上添加 60 个项（应用和文件夹加起来）。

3. 在“类型”中，选择添加“应用”或“文件夹”。

    - **添加应用**：选择此选项可向屏幕上的页面添加应用。 输入：

      - **应用名称**：输入应用程序的名称。 此名称可便于你在 Azure 门户中参考。 它不会显示在 iOS 设备上。
      - **应用捆绑 ID**：输入应用的捆绑 ID。 有关一些示例，请参阅（本文中的）[内置 iOS 应用的捆绑 ID](#bundle-ids-for-built-in-ios-apps)。

      选择“确定”，保存所做更改。

    - **添加文件夹**：选择此选项可向屏幕上的程序坞添加文件夹。 

      添加到文件夹中页面的应用按照列表中的相同顺序从左向右排列。 如果添加的应用数超过了页面能够容纳的量，应用会移到其他页面。

      1. 填写“文件夹名称”。 此名称在设备上向用户显示。
      2. 选择“添加”，并输入以下属性：

          - **页面名称**：输入页面名称。 此名称可便于你在 Azure 门户中参考。 它不会显示在 iOS 设备上。
          - **应用名称**：输入应用程序的名称。 此名称可便于你在 Azure 门户中参考。 它不会显示在 iOS 设备上。
          - **应用捆绑 ID**：输入应用的捆绑 ID。 有关一些示例，请参阅（本文中的）[内置 iOS 应用的捆绑 ID](#bundle-ids-for-built-in-ios-apps)。

      3. 选择“添加”。
      4. 选择“确定”，保存所做更改。

#### <a name="example"></a>示例

在下面的示例中，添加了名为“Contoso”的新页面。 此页面显示“查找朋友”和“设置”应用。 “设置”应用被选为显示自己的属性：

![iOS 主屏幕设置示例](./media/Jc2OxyX.png)

在你向 iPhone 分配策略后，页面如下图所示：

![使用修改后的主屏幕的 iOS 设备](./media/Bd37PHa.png)

## <a name="app-notifications-settings"></a>应用通知设置

选择在 iOS 设备上安装的应用如何发送通知。 这些设置支持运行 iOS 9.3 及更高版本的已监督设备。

1. 在“设置”中，依次选择“应用通知(仅监督模式)” > “添加”：

    ![在 Intune 中的 iOS 配置文件内添加应用通知](./media/ios-macos-app-notifications.png)

2. 输入以下属性：

    - **应用捆绑 ID**：输入要添加的应用的“应用捆绑 ID”。 有关一些示例，请参阅（本文中的）[内置 iOS 应用的捆绑 ID](#bundle-ids-for-built-in-ios-apps)。
    - **应用名称**：输入要添加的应用的名称。 此名称可便于你在 Azure 门户中参考。 它不会显示在设备上。
    - **发布者**：输入要添加的应用的发布者。 此名称可便于你在 Azure 门户中参考。 它不会显示在设备上。
    - **通知**：选择“启用”或“禁用”可启用或禁用应用向设备发送通知。
       - **在通知中心内显示**：选择“启用”可允许应用在设备通知中心内显示通知。 选择“禁用”可阻止应用在设备通知中心内显示通知。
       - **在锁定屏幕中显示**：选择“启用”可允许应用在设备锁定屏幕中显示通知。 选择“禁用”可阻止应用在锁定屏幕中显示通知。
       - **警报类型**：选择在设备解锁后的通知显示方式。 选项包括：
         - **无**：不显示通知。
         - **横幅**：短暂显示包含通知的横幅。
         - **模式**：显示通知，并且用户必须先手动关闭通知，然后才能继续使用设备。
       - **应用图标上的通知提醒**：选择“启用”可向应用图标添加通知提醒。 通知提醒表示应用已发送通知。
       - **声音**：选择“启用”可在通知送达时播放声音。

3. 选择“确定”，保存所做更改。 继续添加所需的应用。 完成时，选择“确定”。

## <a name="lock-screen-message-settings"></a>锁定屏幕消息设置

使用这些设置在登录窗口和锁定屏幕中显示自定义消息或文本。 例如，可输入“如果丢失，请送还至…”消息和资产标记信息。 

该功能支持受监管设备运行：

- iOS 9.3 及更高版本

1. 在“设置”中，请选择“锁屏信息(仅受监督模式)”。
2. 输入以下设置：

    - **资产标记信息：** 输入有关该设备资产标记的信息。 例如，输入 `Owned by Contoso Corp` 或 `Serial Number: {{serialnumber}}`。 

      输入的文本显示在设备上的登录窗口和锁定屏幕中。

    - **锁屏脚注：** 输入一个可帮助在设备丢失或被盗时将其找回的注释。 可以输入所需的任何文本。 例如，输入类似于 `If found, call Contoso at ...` 的内容。

    设备令牌还可以用于向这些字段添加特定于设备的信息。 例如，若要显示序列号，请输入 `Serial Number: {{serialnumber}}`。 在锁屏上，文本显示类似于 `Serial Number 123456789ABC`。 输入变量时，请务必使用大括号 `{{ }}`。 [应用配置令牌](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list)包含可用变量的列表。 还可以使用 `deviceName` 或任何其他特定于设备的值。

    > [!NOTE]
    > 变量不在 UI 中验证。 因此，可能会看到使用不正确输入保存的配置文件。 例如，如果输入 `{{Devicename}}` 而不是 `{{devicename}}`，则显示文本字符串而不是设备的唯一名称。

3. 完成后，选择“确定”，以保存更改。

## <a name="single-sign-on-settings"></a>单一登录设置

大多数业务线 (LOB) 应用需要某种级别的用户身份验证，才能支持安全性。 在许多情况下，此类身份验证要求用户重复输入相同凭据，这可能会让用户感到不快。 为了提升用户体验，开发人员可以创建使用单一登录 (SSO) 的应用。 使用单一登录减少了用户必须输入凭据的次数。

若要使用单一登录，请务必确保：

- 已将应用编码为，在设备上的单一登录中查找用户凭据存储。
- Intune 配置有 iOS 设备 SSO。

1. 选择“设置”中的“单一登录”：

   ![“单一登录”页](./media/sso-blade.png)

2. 输入以下设置：

    - **AAD 中的用户名属性**：Intune 为 Azure AD 中的每个用户查找此属性。 然后，Intune 先填充相应字段（如“UPN”），再生成在设备上安装的 XML。 选项包括：

      - **用户主体名称**：UPN 分析方式如下：

        ![用户名属性](media/User-name-attribute.png)

        还可以使用在“领域”文本框中键入的文本覆盖该领域。

        例如，Contoso 有多个区域，包括欧洲、亚洲和北美。 Contoso 希望亚洲用户使用 SSO，且应用要求采用 `username@asia.contoso.com` 格式的 UPN。 在你选择“用户主体名称”后，系统从 Azure AD 中获取每个用户的领域，即 `contoso.com`。 因此，对于亚洲用户，选择“用户主体名称”，再输入“`asia.contoso.com`”。 最终用户的 UPN 变成 `username@asia.contoso.com`，而不是 `username@contoso.com`。

      - **Intune 设备 ID**：Intune 自动选择 Intune 设备 ID。

        默认情况下，应用只需使用设备 ID。 但如果应用使用领域和设备 ID，你可以在“领域”文本框中键入领域。

        > [!NOTE]
        > 如果使用设备 ID，则默认将领域留空。

      - **Azure AD 设备 ID**

    - **领域**：输入 URL 的域部分。 例如，输入 `contoso.com`。
    - **使用单一登录的 URL 前缀**：添加组织中任何要求用户进行单一登录身份验证的 URL。

        例如，用户连接到任何这些站点时，iOS 设备会使用单一登录凭据。 用户不需要输入任何其他凭据。 如果已启用多重身份验证，用户必须输入第二重身份验证凭据。

        > [!NOTE]
        > 这些 URL 必须采用正确格式化的 FQDN。 Apple 要求这些 URL 必须采用 `http://<yourURL.domain>` 格式。

        匹配模式的 URL 必须以 `http://` 或 `https://` 开头。 由于运行的是简单字符串匹配，因此 `http://www.contoso.com/` URL 前缀与 `http://www.contoso.com:80/` 不匹配。 在 iOS 10.0 或更高版本中，可使用一个通配符 \* 输入所有匹配值。 例如，`http://*.contoso.com/` 同时匹配 `http://store.contoso.com/` 和 `http://www.contoso.com`。

        `http://.com` 和 `https://.com` 模式分别匹配所有 HTTP 和 HTTPS URL。

    - **使用单一登录的应用**：在最终用户的设备上添加可使用单一登录的应用。

        `AppIdentifierMatches` 数组必须包含与应用捆绑 ID 匹配的字符串。 这些字符串可以是完全匹配项（如 `com.contoso.myapp`），也可以使用 \* 通配符输入捆绑 ID 的前缀匹配项。 通配符必须位于句点字符 (.) 后面，并只能在字符串末尾出现一次（如 `com.contoso.*`）。 如果包括通配符，则程序包 ID 以前缀开头的任何应用都将被授予对帐户的访问权限。

        使用应用名称输入一个用户友好名称，帮助识别捆绑 ID。

    - **凭据续订证书**：如果使用证书（而不是密码）进行身份验证，选择现有 SCEP 或 PFX 证书作为身份验证证书。 通常，此证书是针对其他配置文件（如 VPN、Wi-Fi 或电子邮件）部署到用户的相同证书。

3. 完成后，选择“确定”，以保存更改。

## <a name="web-content-filter-settings"></a>Web 内容筛选器设置

这些设置控制 iOS 设备上的浏览器 URL 访问。

1. 选择“设置”中的“Web 内容筛选器(仅监督模式)”。
2. 选择“筛选器类型”。 选项包括：

    - **配置 URL**：使用 Apple 的内置 Web 筛选器来查找成人术语，包括猥亵和露骨色情语言。 此功能在网页加载时评估每个网页，并发现和阻止不适合的内容。 还可以添加不希望筛选器检查的 URL。 或屏蔽特定 URL，无论 Apple 的筛选器设置如何。

      - **允许的 URL**：添加要允许的 URL。 这些 URL 可绕过 Apple 的 Web 筛选器。

        > [!NOTE]
        > 输入的 URL 是你不希望 Apple Web 筛选器评估的 URL。 这些 URL 不是允许的网站列表。 若要创建允许的网站列表，请将“筛选器类型”设置为“仅特定网站”。

        选择“确定”，保存所做更改。

      - **屏蔽的 URL**：添加要阻止打开的 URL，无论 Apple Web 筛选器设置如何。

        选择“确定”，保存所做更改。

    - **仅特定网站**（仅适用于 Safari Web 浏览器）：这些 URL 会添加到 Safari 浏览器的书签中。 用户只能访问这些网站；无法打开其他任何网站。 仅在知道用户可以访问的 URL 的确切列表时使用此选项。

      - **URL**：输入要允许的网站的 URL。 例如，输入 `https://www.contoso.com`。
      - **书签路径**：输入用来存储书签的路径。 例如，输入 `/Contoso/Business Apps`。 如不添加路径，则书签将被添加到设备上的默认书签文件夹中。
      - **标题**：输入书签的描述性标题。

      如果未输入任何 URL，最终用户无法访问任何网站（`microsoft.com`、`microsoft.net` 和 `apple.com` 除外）。 Intune 自动允许这些 URL。

      选择“确定”，保存所做更改。

## <a name="wallpaper-settings"></a>壁纸设置

将自定义 .png、.jpg 或 .jpeg 图像添加到受监督的 iOS 设备。 例如，在锁定屏幕上使用公司徽标。

无映像的配置文件分配给具有现有映像的设备时，可能会遇到意外行为。 例如，创建无映像的配置文件。 此配置文件分配给已有映像的设备。 在此方案中，映像可能会变为设备默认值，或者初始映像可能保留在设备上。 此行为受 Apple 的 MDM 平台控制和限制。

- **壁纸显示位置**：选择要在设备上显示图像的位置。 选项包括：
  - **未配置**：自定义图像不会添加到设备。 设备使用操作系统默认图像。
  - **锁定屏幕**：向锁定屏幕添加图像。
  - **主屏幕**：向主屏幕添加图像。
  - **锁定屏幕和主屏幕**：在锁定屏幕和主屏幕上使用相同的图像。
- **壁纸图像**：上传要使用的现有 .png、.jpg 或 .jpeg 图像。 请确保文件小于 750KB。 还可以删除已添加的图像。

> [!TIP]
> 若要在锁定屏幕和主屏幕上显示不同的图像，请创建包含锁定屏幕图像的配置文件， 以及另一个包含主屏幕图像的配置文件。 将两个配置文件分配到 iOS 用户组或设备组。

## <a name="bundle-ids-for-built-in-ios-apps"></a>内置 iOS 应用的捆绑 ID

下表显示了一些常见的内置 iOS 应用的捆绑 ID。 若要查找其他应用的捆绑 ID，请联系软件供应商。

|||
|-|-|
|应用程序名称|BundleID|
|App Store|com.apple.AppStore|
|计算器|com.apple.calculator|
|日历|com.apple.mobilecal|
|照相机|com.apple.camera|
|时钟|com.apple.mobiletimer|
|指南针|com.apple.compass|
|联系人|com.apple.MobileAddressBook|
|FaceTime|com.apple.facetime|
|查找好友|com.apple.mobileme.fmf1|
|查找 iPhone|com.apple.mobileme.fmip1|
|游戏中心|com.apple.gamecenter|
|GarageBand|com.apple.mobilegarageband|
|运行状况|com.apple.Health|
|iBooks|com.apple.iBooks|
|iTunes 商店|com.apple.MobileStore|
|iTunes U|com.apple.itunesu|
|Keynote|com.apple.Keynote|
|Mail|com.apple.mobilemail|
|映射|com.apple.Maps|
|消息|com.apple.MobileSMS|
|音乐|com.apple.Music|
|新闻|com.apple.news|
|注意|com.apple.mobilenotes|
|数字|com.apple.Numbers|
|页面|com.apple.Pages|
|Photo Booth|com.apple.Photo-Booth|
|照片|com.apple.mobileslideshow|
|播客|com.apple.podcasts|
|提醒|com.apple.reminders|
|Safari|com.apple.mobilesafari|
|设置|com.apple.Preferences|
|股票|com.apple.stocks|
|提示|com.apple.tips|
|视频|com.apple.videos|
|VoiceMemos|com.apple.VoiceMemos|
|电子钱包|com.apple.Passbook|
|观看|com.apple.Bridge|
|天气|com.apple.weather|

## <a name="next-steps"></a>后续步骤

[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

还可以为 [macOS](macos-device-features-settings.md) 设备创建设备功能配置文件。
