---
title: Microsoft Intune 中适用于 Windows 10 的设备限制设置 - Azure | Microsoft Docs
description: 有关如何在 Windows 10 及更高版本设备上创建设备限制的信息，请参阅所有设置及其说明的列表。 使用配置文件中的这些设置可以控制 Microsoft Intune 中的屏幕截图、密码要求、展台设置、应用商店中的应用、Microsoft Edge 浏览器、Windows Defender、对云的访问权限、开始菜单等。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/08/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8957c8d8aad2eaa1741b1a625afd4b5a41a8bb51
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "59423690"
---
# <a name="windows-10-and-newer-device-settings-to-allow-or-restrict-features-using-intune"></a>便于使用 Intune 允许或限制功能的 Windows 10（及更高版本）设备设置

本文列出并介绍了可以在 Windows 10 和更高版本设备上控制的所有不同设置。 作为移动设备管理 (MDM) 解决方案的一部分，请使用这些设置以允许或禁用功能、设置密码规则、自定义锁屏界面，使用 Windows Defender 等。

这些设置将添加到 Intune 中的设备配置配置文件中，然后分配或部署到 Windows 10 设备。

> [!Note]
> 并非所有选项在所有版本的 Windows 上都可用。 若要查看受支持的版本，请参阅 [policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider)（策略 CSP）（打开另一个 Microsoft 网站）。

## <a name="before-you-begin"></a>在开始之前

[创建设备配置文件](device-restrictions-configure.md#create-the-profile)。

## <a name="app-store"></a>App Store

- **应用商店(仅限移动版)**：在 Windows 10 移动设备上启用或阻止使用应用商店。
- **自动更新应用商店的应用**：允许自动更新从 Microsoft 应用商店安装的应用。
- **受信任的应用安装**：允许对使用受信任的证书签名的应用进行旁加载。
- **开发人员解锁**：允许 Windows 开发人员设置，如允许最终用户修改旁加载的应用。
- **共享用户应用数据**：允许应用在同一设备上的不同用户之间共享数据。
- **仅使用专用存储**：启用此选项，仅允许最终用户从你的专用存储下载应用。
- **启动来自应用商店的应用**：用于禁用设备上预安装或从 Microsoft 应用商店下载的所有应用。
- **在系统卷上安装应用数据**：阻止应用在设备的系统卷上存储数据。
- **在系统驱动器上安装应用**：阻止应用在设备的系统驱动器上存储数据。
- **游戏 DVR (仅限桌面版)**：配置是否允许游戏的录制和广播。
- **仅限来自应用商店的应用**：配置用户是否可以安装应用商店以外位置的应用。

## <a name="cellular-and-connectivity"></a>手机网络和连接性

- **手机网络数据通道**：阻止用户在连接到手机网络时使用数据，例如浏览 Web。 
- **数据漫游**：允许在访问数据时进行网络之间的漫游。
- **通过手机网络使用 VPN**：控制设备在连接到手机网络时是否能够访问 VPN 连接。
- **通过手机网络漫游 VPN**：控制设备在手机网络上漫游时是否能够访问 VPN 连接。
- **蓝牙**：控制用户是否可以在设备上启用和配置蓝牙。
- **蓝牙可发现性**：允许其他已启用蓝牙的设备可发现此设备。
- **蓝牙预配对**：允许配置特定蓝牙设备以自动与主机设备配对。
- **蓝牙广告**：允许设备通过蓝牙接收广告。
- **连接设备服务**：允许选择允许连接设备服务，以便启用对其他蓝牙设备的发现和连接。
- **NFC**：允许用户在设备上启用和配置近场通信 (NFC) 功能。
- **Wi-Fi**：允许用户在设备上启用和配置 Wi-Fi（仅限 Windows 10 移动版）。
- **自动连接到 Wi-Fi 热点**：可让设备自动连接到免费 Wi-Fi 热点并自动接受该连接的任何条款和条件。
- **手动配置 Wi-Fi**：控制用户是否可以配置自己的 Wi-Fi 连接或是否只能使用 Wi-Fi 配置文件配置的连接（仅限 Windows 10 移动版）。
- **Wi-Fi 扫描间隔**：输入设备扫描 Wi-Fi 网络的频率。 输入从 1（频率最高）到 500（频率最低）的值。
- **蓝牙允许的服务**：以十六进制字符串输入允许的蓝牙服务和配置文件列表。

## <a name="cloud-and-storage"></a>云和存储

- **Microsoft 帐户**：使用户可以将 Microsoft 帐户与设备关联。
- **非 Microsoft 帐户**：使用户可以将电子邮件帐户添加到不与 Microsoft 帐户相关联的设备。
- **Microsoft 帐户的设置同步**：允许设备和应用设置与 Microsoft 帐户关联以在设备之间进行同步。
- **Microsoft 帐户登录助手**：选择“禁用”可防止最终用户控制 Microsoft 登录助手服务 (wlidsvc)，例如手动停止或启动服务。 当设置为“未配置”时，wlidsvc NT 服务将使用操作系统 (OS) 默认设置，这可能会允许最终用户启动和停止该服务。 操作系统使用此服务以允许用户登录到其 Microsoft 帐户。

## <a name="cloud-printer"></a>云打印机

- **打印机发现 URL**：输入用于发现云打印机的 URL。
- **打印机访问授权机构 URL**：输入身份验证终结点 URL 以获取 OAuth 令牌。 例如，输入类似于 `https://login.microsoftonline.com/your Azure AD Tenant ID` 的内容。
- **Azure 本机客户端应用 GUID**：输入有权从 OAuthAuthority 获取 OAuth 令牌的客户端应用程序的 GUID。
- **打印服务资源 URI**：输入 Azure 门户中配置的打印服务 OAuth 资源 URI。 例如，输入类似于 `http://MicrosoftEnterpriseCloudPrint/CloudPrint` 的内容。
- **要查询的最大打印机数(仅限移动版)**：输入要查询的最大打印机数。 例如，输入 `10`。
- **打印机发现服务资源 URI**：输入 Azure 门户中配置的打印机发现服务 OAuth 资源 URI。 例如，输入类似于 `http://MopriaDiscoveryService/CloudPrint` 的内容。

> [!TIP]
> 设置 [Windows Server 混合云打印](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-overview)后，可以配置这些设置，然后部署到 Windows 设备。

## <a name="control-panel-and-settings"></a>控制面板和设置

- **设置应用**：阻止访问 Windows 设置应用。
  - **系统**：阻止访问设置应用的系统区域。
    - **电源和睡眠设置修改(仅限桌面版)**：阻止最终用户更改设备上的电源和睡眠设置。
  - **设备**：阻止访问设置应用的设备区域。
  - **网络 Internet**：阻止访问设置应用的网络和 Internet 区域。
  - **个性化设置**：阻止访问设置应用的个性化设置区域。
  - **帐户**：阻止访问设置应用的帐户区域。
  - **时间和语言**：阻止访问设置应用的时间和语言区域。
    - **系统时间修改**：阻止最终用户更改设备日期和时间。
    - **区域设置修改(仅限桌面版)**：阻止最终用户更改设备上的区域设置。
    - **语言设置修改(仅限桌面版)**：阻止最终用户更改设备上的语言设置。
  - **游戏**：阻止访问设置中的“游戏”应用。
  - **轻松访问**：阻止访问设置应用的轻松访问区域。
  - **隐私**：阻止访问设置应用的隐私区域。
  - **更新和安全性**：阻止访问设置应用的更新和安全区域。

## <a name="display"></a>显示

- **对应用启用 GDI 缩放**
- **对应用禁用 GDI 缩放**

  借助 GDI DPI 缩放，应用可以从非 DPI 感知变成按监视器 DPI 感知。 输入已启用 GDI DPI 缩放的旧应用。 如果将 GDI DPI 缩放配置为在应用上先启用后禁用，则对应用禁用缩放。

## <a name="general"></a>常规

- **屏幕捕获(仅限移动版)**：允许用户以图像形式捕获设备屏幕。
- **复制和粘贴(仅限移动版)**：允许设备上应用间的复制和粘贴操作。
- **手动注销**：允许用户手动从设备中删除工作区帐户。
  - 如果计算机已加入 Azure AD 并启用自动注册，此策略设置不适用。 
  - 此策略设置不适用于运行 Windows 10 家庭版的计算机。
- **手动安装根证书(仅限移动版)**：阻止用户手动安装根证书和中间 CAP 证书。

- **照相机**：允许或阻止使用设备上的照相机。
- **OneDrive 文件同步**：阻止设备将文件同步到 OneDrive。
- **可移动存储**：指定外部存储设备（如 SD 卡）是否可以与该设备结合使用。
- **地理位置**：指定设备是否可以使用位置服务信息。
- **Internet 共享**：允许在设备上使用 Internet 连接共享。
- **手机重置**：控制用户是否可以对设备进行擦除。
- **USB 连接(仅限移动版)**：控制设备是否可以通过 USB 连接访问外部存储设备。
- **防盗模式(仅限移动版)**：配置是否启用 Windows 防盗模式。
- **Cortana**：启用或禁用 Cortana 语音助手。
- **语音录制(仅限移动版)**：允许或阻止使用设备的语音录音机。
- **设备名称修改**：阻止最终用户更改设备名称（仅限 Windows 10 移动版）
- **添加配置包**：阻止安装配置包的运行时配置代理。
- **删除配置包**：阻止删除配置包的运行时配置代理。
- **设备发现**：阻止设备被其他设备发现。
- **任务切换器(仅限移动版)**：阻止设备上的任务切换器。
- **SIM 卡错误对话框(仅限移动版)**：阻止在未检测到 SIM 卡时在设备上显示错误消息。
- **墨迹工作区**：阻止用户访问墨迹工作区。 “未配置”可启用墨迹工作区，并且允许用户在锁屏界面上使用它。
- **自动重新部署**：允许具有管理权限的用户在设备锁定屏幕上使用 CTRL+Win+R 删除所有用户数据和设置。 设备会自动进行重新配置并重新注册到管理。
- **要求用户在设备设置期间连接到网络**：选择“需要”以便在 Windows 10 安装过程中设备先连接到网络，然后再通过“网络”页。

  该设置在下次擦除或重置设备时生效。 与任何其他 Intune 配置一样，该设备必须由 Intune 注册和管理才能接收配置设置。 但注册后，接收策略并在下一次 Windows 设置期间重置设备会强制执行该设置。

- **直接内存访问**：“阻止”将防止所有热插拔 PCI 下游端口进行直接内存访问 (DMA)，直到用户登录 Windows。 “启用”（默认设置）允许访问 DMA，即使用户未登录。

  CSP：[DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess)

- **从任务管理器结束进程**：此设置确定非管理员是否可以使用任务管理器来结束任务。 选择“阻止”，则会阻止标准用户（非管理员）使用任务管理器结束设备上的进程或任务。 选择“未配置”（默认选项），则会允许标准用户使用任务管理器结束进程或任务。

## <a name="locked-screen-experience"></a>锁定屏幕体验

- **操作中心通知(仅限移动版)**：允许设备锁定屏幕上显示操作中心通知（仅限 Windows 10 移动版）。
- **锁定屏幕图片 URL (仅限桌面版)**：输入将用作 Windows 锁定屏幕墙纸的图片（格式为 JPEG）的 URL。 此设置将锁定映像。 此后无法更改该映像。
- **用户可配置屏幕超时(仅限移动版)**：允许用户配置时间量 
- **锁定屏幕上的 Cortana (仅限桌面版)**：当设备处于锁定屏幕时，不允许用户与 Cortana 交互（仅限 Windows 10 桌面版）。
- **锁屏界面上的 Toast 通知**：阻止在设备锁屏界面上显示警报消息。
- **屏幕超时(仅限移动版)**：指定在屏幕锁定后多长时间黑屏（秒）。

## <a name="messaging"></a>Messaging

- **消息同步(仅移动设备)**：禁用“随时随地传送消息”以及短信备份和还原。
- **彩信(仅限移动版)**：对设备禁用彩信发送/接收功能。
- **富通信(仅限移动版)**：对设备禁用富通信服务发送/接收功能。

## <a name="microsoft-edge-browser"></a>Microsoft Edge 浏览器

### <a name="use-microsoft-edge-kiosk-mode"></a>使用 Microsoft Edge 展台模式

可用设置因你所选的项而异。 选项包括：

- **否**（默认）：Microsoft Edge 未在展台模式下运行。 可更改和配置所有 Microsoft Edge 设置。
- **数字/交互式标牌（单应用展台）**：筛选适用于数字/交互式标牌 Microsoft Edge 展台模式的 Microsoft Edge 设置，仅用于 Windows 10 单应用展台。 选择此设置可打开 URL 全屏，仅显示该网站上的内容。 [设置数字标牌](https://docs.microsoft.com/windows/configuration/setup-digital-signage)提供有关此功能的详细信息。
- **InPrivate 公共浏览（单应用展台）**：筛选适用于 InPrivate 公共浏览 Microsoft Edge 展台模式的 Microsoft Edge 设置，用于 Windows 10 单应用展台。 运行 Microsoft Edge 的多选项卡版本。
- **普通模式(多应用展台)**：筛选适用于普通 Microsoft Edge 展台模式的 Microsoft Edge 设置。 使用所有浏览功能运行完整版 Microsoft Edge。
- **公共浏览（多应用展台）**：筛选适用于 Windows 10 多应用展台上公共浏览的 Microsoft Edge 设置。  运行 Microsoft Edge InPrivate 的多选项卡版本。

> [!TIP]
> 有关这些选项用途的详细信息，请参阅 [Microsoft Edge 展台模式配置类型](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types)。

此设备限制配置文件与你使用 [Windows 展台设置](kiosk-settings-windows.md)创建的展台配置文件直接相关。 总结：

1. 创建 [Windows 展台设置](kiosk-settings-windows.md)配置文件以在展台模式下运行设备。 选择 Microsoft Edge 作为应用程序，并在展台配置文件中设置 Microsoft Edge 展台模式。
2. 创建本文中介绍的设备限制配置文件，并配置 Microsoft Edge 中允许的特定功能和设置。 请务必选择展台配置文件中所选的同一 Microsoft Edge 展台模式类型（[Windows 展台设置](kiosk-settings-windows.md)）。 

    [受支持的展台模式设置](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-policies-for-kiosk-mode)是出色的资源。

> [!IMPORTANT] 
> 请务必将此 Microsoft Edge 配置文件分配到与展台配置文件相同的设备（[Windows 展台设置](kiosk-settings-windows.md)）。

[ConfigureKioskMode CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configurekioskmode)

### <a name="start-experience"></a>开始体验

- **启动 Microsoft Edge 的结果**：选择在启动 Microsoft Edge 时打开的页面。 选项包括：
  - **起始页**：启动 Microsoft Edge 后将显示由 OS 定义的默认起始页
  - **新标签页**：Microsoft Edge 加载“新标签页 URL”设置中定义的任何内容
  - **最后一次会话的页面**：Microsoft Edge 加载最后一次会话的页面 
  - **自定义起始页**：Microsoft Edge 加载由 IT 管理员定义的起始页
- **用户可以更改起始页**：“允许”可让用户更改起始页。 管理员可以使用 `EdgeHomepageUrls` 输入在打开 Microsoft Edge 时用户默认看到的起始页。 “未配置”可阻止用户更改起始页。
- **新标签页 URL**：输入要在新标签页上打开的 URL。 例如，输入 `https://www.bing.com`。
- **在新标签页上打开 Web 内容**：选择“阻止”可阻止 Microsoft Edge 打开新标签上的网站。阻止时，新标签打开为空白。 “未配置”可在设备上使用 OS 默认行为，这可能会允许用户选择所显示的内容。
- **主页按钮**：选择按主页按钮时会发生的情况。 选项包括：
  - **起始页**：打开为“启动 Microsoft Edge 的结果”设置选择的选项
  - **新标签页**：打开为“新标签页 URL”设置选择的选项
  - **自定义主页按钮 URL**：打开为“主页按钮 URL”设置选择的选项
  - **隐藏主页按钮**：隐藏主页按钮
- **用户可以更改主页按钮**：“允许”可让用户更改主页按钮。 用户的更改会覆盖对主页按钮进行的任何管理员设置。 “未配置”可在设备上使用 OS 默认行为，这可能会阻止用户更改管理员配置主页按钮的方式。
- **显示首次运行体验页**：“阻止”可在首次运行 Microsoft Edge 时阻止显示简介页。 借助此功能，诸如在零排放配置中注册的企业组织可以阻止此页面。 “未配置”可显示简介页。
  - **首次运行体验 URL**：输入用户首次运行 Microsoft Edge 时要显示的页面 URL（仅限 Windows 10 移动版）。
- **空闲时间后刷新浏览器**：输入刷新浏览器之前的空闲分钟数，范围为 0-1440 分钟。 默认为 `5` 分钟。 设置为 `0`（零）时，浏览器在空闲后不刷新。

  此设置仅在 [InPrivate 公共浏览（单应用展台）](#use-microsoft-edge-kiosk-mode)中运行时可用。

  CSP：[ConfigureKioskResetAfterIdleTimeout](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configurekioskresetafteridletimeout)

- **弹出窗口**：选择“阻止”可阻止浏览器中的弹出窗口。 仅适用于 Windows 10 桌面版。 “未配置”则允许 Web 浏览器中的弹出窗口。
- **将 Intranet 流量发送到 Internet Explorer**：“允许”可让用户在 Internet Explorer 中打开 Intranet 网站（仅限 Windows 10 桌面版）。 “未配置”则允许用户使用 Microsoft Edge。
- **企业模式站点列表位置**：输入包括以企业模式打开的网站的列表的 URL。 用户无法更改此列表。 仅适用于 Windows 10 桌面版。
- **在 Internet Explorer 中打开站点时显示消息**：使用此设置可将 Microsoft Edge 配置为在 Internet Explorer 11 中打开站点之前显示通知。 选项包括：
  - **未配置**：使用 OS 默认行为，这可能不会显示消息。
  - **在没有在 Microsoft Edge 中打开站点的选项时显示消息**：在 IE 中打开站点时显示消息。 将在 IE 中打开站点。 没有在 Microsoft Edge 中打开站点的选项。
  - **在 Microsoft Edge 中打开站点时显示消息**：在 IE 中打开站点时显示消息。 该消息包含“在 Microsoft Edge 中继续”链接，以便用户可以选择 Microsoft Edge，而不是 IE。

  > [!IMPORTANT]
  > 此设置要求你启用“配置企业模式站点列表”设置和/或“将所有 Intranet 站点发送到 Internet Explorer 11”设置。

- **Microsoft 兼容性列表**：“阻止”可阻止 Microsoft Edge 中的 Microsoft 兼容性列表。 Microsoft 的此列表可帮助 Microsoft Edge 正确显示具有已知兼容性问题的站点。 “未配置”则允许使用 Microsoft 兼容性列表。
- **预加载起始页和新标签页**：选择“阻止”可阻止 Microsoft Edge 预加载起始页和新标签页。 预加载可最大程度地缩短启动 Microsoft Edge 和加载新标签的时间。“未配置”可使用 OS 默认行为，这可能会预加载这些页面。
- **预启动起始页和新标签页**：选择“阻止”可阻止 Microsoft Edge 预启动起始页和新标签页。 预启动可帮助提高 Microsoft Edge 的性能并最大程度地缩短启动 Microsoft Edge 所需的时间。 “未配置”可使用 OS 默认行为，这可能会预启动这些页面。

### <a name="favorites-and-search"></a>收藏夹和搜索

- **收藏夹栏**：选择任何 Microsoft Edge 页面上的收藏夹栏会发生的情况。 选项包括：
  - **未配置**：使用 OS 默认行为，这可能会隐藏所有页面上的收藏夹栏。 用户可以更改此设置。
  - **隐藏**：隐藏所有页面上的收藏夹栏。 用户无法更改此设置。
  - **显示**：显示所有页面上的收藏夹栏。 用户无法更改此设置。
- **收藏夹列表**：将 URL 列表添加到收藏夹文件。 例如：添加 `http://contoso.com/favorites.html`。
- **限制对收藏夹的更改**：“阻止”可阻止用户添加、导入、排序或编辑收藏夹列表。 “未配置”可使用 OS 默认值，这可能会允许用户更改列表。
- **同步 Microsoft 浏览器之间的收藏夹(仅限桌面版)**：将此设置为“必需”会强制 Windows 同步 Internet Explorer 和 Microsoft Edge 之间的收藏夹。 在浏览器之间共享对收藏夹执行的添加、删除、修改和顺序更改操作。  “未配置”可使用 OS 默认值，这可能会为用户提供在浏览器之间同步收藏夹的选项。
- **默认搜索引擎**：选择设备上的默认搜索引擎。 最终用户可以随时更改此值。 选项包括：
  - 默认
  - 必应
  - Google
  - Yahoo
  - 自定义值
- **搜索建议**：“未配置”允许搜索引擎在你在地址栏中键入搜索短语时建议站点。 “阻止”则阻止此功能。
- **允许更改搜索引擎**：“是”（默认）允许用户添加新搜索引擎，或更改 Microsoft Edge 中的默认搜索引擎。 选择“否”可阻止用户自定义搜索引擎。

  此设置仅在[普通模式（多应用展台）](#use-microsoft-edge-kiosk-mode)中运行时可用。

  CSP：[AllowSearchEngineCustomization](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsearchenginecustomization)

### <a name="privacy-and-security"></a>隐私和安全性

- **InPrivate 浏览**：“阻止”可阻止最终用户打开 InPrivate 浏览会话。 “未配置”则允许此功能。
- **保存浏览历史记录**：“阻止”可阻止 Microsoft Edge 保存浏览历史记录。 “未配置”则允许保存浏览历史记录。
- **退出时清除浏览数据(仅限桌面版)**：将此设置为“必需”可在用户退出 Microsoft Edge 时清除历史记录和浏览数据。 “未配置”可使用 OS 默认值，这可能会缓存浏览数据。
- **同步用户设备之间的浏览器设置**：选择同步设备之间的浏览器设置的方式。 选项包括：
  - **允许**：允许同步用户的设备之间的 Microsoft Edge 浏览器设置
  - **阻止和启用用户覆盖**：阻止同步用户的设备之间的 Microsoft Edge 浏览器设置。 用户可以覆盖此设置。
  - **阻止**：阻止同步用户的设备之间的 Microsoft Edge 浏览器设置。 用户无法覆盖此设置。
- **密码管理器**：“阻止”可禁用 Microsoft Edge 密码管理器功能。 “未配置”则允许此功能。
- **Cookie**：选择在 Web 浏览器中处理 Cookie 的方式。 选项包括：
  - **允许**：Cookie 存储在设备上。
  - **阻止所有 Cookie**：Cookie 未存储在设备上。
  - **仅阻止第三方 Cookie**：第三方或合作伙伴 Cookie 未存储在设备上。
- **自动填充**：“阻止”可禁用设备上的自动填充功能。 “未配置”则允许用户更改浏览器中的自动完成设置（仅限 Windows 10 桌面版）。
- **发送“不跟踪”标题**：“未配置”要求设备将“不跟踪”标题发送到请求跟踪信息的网站（推荐）。 选择“阻止”可阻止设备发送这些标题，这些标题允许网站跟踪用户。
- **WebRtc localhost IP 地址**：“阻止”可在使用 Web RTC 协议拨打电话时，阻止显示用户 localhost IP 地址。 “未配置”可在使用此协议拨打电话时，允许显示用户 localhost IP 地址。
- **实时磁贴数据收集**：选择“阻止”可在从 Microsoft Edge 将站点固定到开始菜单时，阻止 Windows 从实时磁贴收集信息。 “未配置”则允许收集此信息。
- **用户可以覆盖证书错误**：“阻止”可阻止用户访问出现 SSL 或 TLS 错误的网站。 “未配置”则允许用户访问这些网站。

### <a name="additional"></a>Additional

- **Microsoft Edge 浏览器(仅限移动版)**：选择“阻止”可阻止在设备上使用 Microsoft Edge。 如果阻止 Microsoft Edge，则个人设置仅适用于桌面。 **未配置**：允许在设备上使用 Microsoft Edge Web 浏览器。
- **地址栏下拉列表(仅限桌面版)**：选择“阻止”可在键入内容时，阻止 Microsoft Edge 在下拉列表中显示建议列表。 此选项有助于最大程度减少 Microsoft Edge 和 Microsoft 服务之间的网络带宽使用。 “未配置”则允许 Microsoft Edge 显示建议列表。
- **全屏**：选择“阻止”可阻止 Microsoft Edge 仅显示 Web 内容以及隐藏 Microsoft Edge（全屏模式）。 “未配置”可使用 OS 默认值，这样允许 Microsoft Edge 使用全屏模式。
- **关于标志**：“阻止”可阻止最终用户在 Microsoft Edge 中访问包含开发人员和实验性设置的 `about:flags` 页面。 “未配置”可使用 OS 默认值，这可能会允许更改 `about:flags` 页面。
- **开发人员工具**：“阻止”可阻止最终用户打开 Microsoft Edge 开发人员工具。 “未配置”则允许用户打开开发人员工具。
- **扩展**：“未配置”允许最终用户在设备上安装 Microsoft Edge 扩展。 “阻止”可阻止安装。
- **旁加载开发人员扩展**：选择“阻止”可阻止 Microsoft Edge 进行旁加载，这样会使用“加载扩展”功能安装并运行未验证的扩展。 “未配置”可使用 OS 默认值，这可能会允许进行旁加载。
- **必需扩展**：选择最终用户在 Microsoft Edge 中不能关闭的扩展。 输入包系列名称，然后选择“添加”。 [查找包系列名称 (PFN)](https://docs.microsoft.com/sccm/protect/deploy-use/find-a-pfn-for-per-app-vpn) 列表提供了一些指导。

  还可以导入包含包系列名称的 CSV 文件。

- **JavaScript**：选择“阻止”可阻止在设备上运行浏览器中的 Java 脚本。 “未配置”则允许脚本（如 Javascript）在 Microsoft Edge 浏览器中运行。

## <a name="network-proxy"></a>网络代理

- **自动检测代理设置**：启用后，设备会尝试查找 PAC 脚本的路径。
- **使用代理脚本**：选择此选项可输入 PAC 脚本的路径，以配置代理服务器。
  - **设置脚本地址 URL**：输入想要使用的 PAC 脚本的 URL，以配置代理服务器。
- **使用手动代理服务器**：选择此选项可手动输入代理服务器信息。
  - **地址**：输入代理服务器的名称或 IP 地址。
  - **端口号**：输入代理服务器的端口号。
  - **代理例外**：输入不得使用代理服务器的任何 URL。 请使用分号分隔每一项。
  - **对本地地址跳过代理服务器**：如果不想在 Intranet 上对本地地址使用代理服务器，请启用此选项。

## <a name="password"></a>密码

- **密码**：需要最终用户输入密码才能访问设备。
  - **所需的密码类型**：指定密码是否只能是数字或字母数字。
  - **最短密码长度**：仅适用于 Windows 10 移动版。
  - **擦除设备前的登录失败次数**：对于运行 Windows 10 的设备：如果该设备已启用 BitLocker，在超过指定的登录失败次数后将进入 BitLocker 恢复模式。 如果该设备未启用 BitLocker，则不会应用此设置。 对于运行 Windows 10 移动版的设备：超过输入的登录失败次数后，将擦除设备。
  - **屏幕锁定前的最大非活动状态分钟数**：指定锁定屏幕前，设备必须处于空闲状态的时间长度。
  - **密码过期(天)**：指定必须更改设备密码之前的时间长度。
  - **防止重用以前的密码**：指定设备记住的以前用过的密码数目。
  - **设备从空闲状态返回时需要输入密码(仅限移动版)**：指定用户必须输入密码才能解锁设备（仅限 Windows 10 移动版）。
  - **简单密码**：允许使用简单密码，如 1111 和 1234。 此设置还允许或阻止使用 Windows 图片密码。
- **AADJ 期间的自动加密**：设备加入 Azure AD 后，准备首次使用时，“阻止”会阻止自动 BitLocker 设备加密。 “未配置”（默认）使用操作系统默认值，可以启用加密。 有关详细信息，请参阅 [BitLocker 设备加密](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-device-encryption-overview-windows-10#bitlocker-device-encryption)。

  [Security/PreventAutomaticDeviceEncryptionForAzureADJoinedDevices CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-security#security-preventautomaticdeviceencryptionforazureadjoineddevices)

- **美国联邦信息处理标准 (FIPS) 政策**：“允许”使用美国联邦信息处理标准 (FIPS) 政策，该政策是美国政府加密、散列和签名的标准。 “未配置”（默认）使用操作系统默认值，它不会使用 FIPS。

  [Cryptography/AllowFipsAlgorithmPolicy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-cryptography#cryptography-allowfipsalgorithmpolicy)

- **Windows Hello 设备身份验证**：“允许”用户使用 Windows Hello 配套设备（如手机、健身手环或 IoT 设备）登录到 Windows 10 计算机。 “未配置”（默认）使用操作系统默认值，这可能会阻止 Windows Hello 配套设备进行 Windows 身份验证。

  [Authentication/AllowSecondaryAuthenticationDevice CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowsecondaryauthenticationdevice)

- **Web 登录**：为非 ADFS（Active Directory 联合身份验证服务）联合提供程序（如安全断言标记语言 (SAML)）启用 Windows 登录支持。 SAML 使用安全令牌，该令牌为 Web 浏览器提供单一登录 (SSO) 体验。 选项包括：

  - **未配置**（默认）：在设备上使用操作系统默认值。
  - **已启用**：已为登录启用了 Web 凭据提供程序。
  - **已禁用**：已为登录禁用了 Web 凭据提供程序。

  [Authentication/EnableWebSignIn CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-enablewebsignin)

- **首选 Azure AD 租户域**：在你的 Azure AD 组织中输入现有域名。 当此域中的用户登录时，无需键入域名。 例如，输入 `contoso.com`。 `contoso.com` 域中的用户可使用其用户名登录，如“abby”，而不是“abby@contoso.com”。

  [Authentication/PreferredAadTenantDomainName CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-preferredaadtenantdomainname)

## <a name="per-app-privacy-exceptions"></a>每应用隐私异常

可以添加隐私行为不同于“默认隐私”中所定义设置的应用。

- **包名称**：应用包系列名称。
- **应用名称**：应用的名称。

### <a name="exceptions"></a>例外

- **帐户信息**：定义此应用能否访问用户名、图片和其他联系人信息。
- **后台应用**：定义此应用能否在后台运行。
- **日历**：定义此应用能否访问日历。
- **呼叫历史记录**：定义此应用能否访问我的呼叫历史记录。
- **照相机**：定义此应用能否访问照相机。
- **联系人**：定义此应用能否访问联系人。
- **电子邮件**：定义此应用能否访问和发送电子邮件。
- **位置**：定义此应用能否访问位置信息。
- **消息**：定义此应用能否读取或发送短信/彩信。
- **麦克风**：定义此应用能否使用麦克风。
- **运动**：定义此应用能否访问设备运动信息。
- **通知**：定义此应用能否访问通知。
- **电话**：定义此应用能否访问电话。
- **无线收发器**：一些应用使用设备中的无线收发器（例如，蓝牙）发送和接收数据，需要打开或关闭这些无线收发器。 定义此应用能否控制这些无线收发器。
- **任务**：定义此应用能否访问任务。
- **受信任的设备**：选择此应用能否使用受信任的设备。 受信任的设备是连接的硬件或设备随附的硬件。 例如，将 TV、投影仪等用作受信任的设备。
- **反馈和诊断**：定义此应用能否访问诊断信息。
- **与设备同步**：选择此应用能否自动与设备未显式配对的无线设备共享和同步信息。

## <a name="personalization"></a>个性化设置

- **桌面背景图片 URL (仅限桌面版)**：输入要用作 Windows 桌面墙纸的图片（格式为 JPEG）的 URL。 用户无法更改图片。

## <a name="printer"></a>打印机

- **打印机**：已添加的本地打印机的列表。
- **默认打印机**：设置默认打印机。
- **用户添加新打印机的权限**：允许或阻止使用本地打印机。

## <a name="privacy"></a>隐私

- **输入个性化**：不允许使用 Cortana、听写或 Microsoft 应用商店应用的基于云的语音服务。 如果允许这些服务，Microsoft 可能会收集语音数据以改进服务。
- **自动接受配对和隐私用户同意提示**：允许 Windows 在运行应用时自动接受配对和隐私同意消息。
- **发布用户活动**：“阻止”可阻止任务切换程序中最近使用资源的共享体验和发现。
- **仅限本地活动**：“阻止”可仅基于本地活动阻止任务切换程序中最近使用资源的共享体验和发现。

可以配置设备上的所有应用可以访问的信息。 此外，使用“每应用隐私异常”对每个应用定义异常。

### <a name="exceptions"></a>例外

- **帐户信息**：定义此应用能否访问用户名、图片和其他联系人信息。
- **后台应用**：定义此应用能否在后台运行。
- **日历**：定义此应用能否访问日历。
- **呼叫历史记录**：定义此应用能否访问我的呼叫历史记录。
- **照相机**：定义此应用能否访问照相机。
- **联系人**：定义此应用能否访问联系人。
- **电子邮件**：定义此应用能否访问和发送电子邮件。
- **位置**：定义此应用能否访问位置信息。
- **消息**：定义此应用能否读取或发送短信/彩信。
- **麦克风**：定义此应用能否使用麦克风。
- **运动**：定义此应用能否访问设备运动信息。
- **通知**：定义此应用能否访问通知。
- **电话**：定义此应用能否访问电话。
- **无线收发器**：一些应用使用设备中的无线收发器（例如，蓝牙）发送和接收数据，需要打开或关闭这些无线收发器。 定义此应用能否控制这些无线收发器。
- **任务**：定义此应用能否访问任务。
- **受信任的设备**：选择此应用能否使用受信任的设备。 受信任的设备是连接的硬件或设备随附的硬件。 例如，将 TV、投影仪等用作受信任的设备。
- **反馈和诊断**：选择此应用能否访问诊断信息。
- **与设备同步** - 定义此应用能否自动与这台 PC、平板电脑或手机未显式配对的无线设备共享和同步信息。

## <a name="projection"></a>投影

- **来自无线显示接收方的用户输入**：阻止来自无线显示接收方的用户输入。
- **此电脑的投影**：阻止其他设备发现用于投影的电脑。
- **需要用于配对的 PIN**：在连接到投影设备时需要 PIN。

## <a name="reporting-and-telemetry"></a>报告和遥测

- **共享使用情况数据**：选择已提交的诊断数据的级别。 选项包括：
  - 安全
  - 基本
  - 已增强
  - 完整
- **将 Microsoft Edge 浏览数据发送到 Microsoft 365 Analytics**：若要使用此功能，请将“共享使用情况数据”设置为“已增强”或“完整”。 此功能可控制 Microsoft Edge 向适用于具有已配置商业 ID 的企业设备的 Microsoft 365 Analytics 发送的数据。 选项包括：
  - **未配置**：使用 OS 默认值，这可能不会发送任何浏览历史数据
  - **仅发送 Intranet 数据**：允许管理员发送 Intranet 数据历史记录
  - **仅发送 Internet 数据**：允许管理员发送 Internet 数据历史记录
  - **发送 Intranet 和 Internet 数据**：允许管理员发送 Intranet 和 Internet 数据历史记录
- **遥测代理服务器**：输入代理服务器的完全限定的域名 (FQDN) 或 IP 地址，以使用安全套接字层 (SSL) 连接转发连接用户体验和遥测请求。 此设置的格式为“服务器:端口”。 如果已命名代理失败，或在启用此策略时没有输入代理，那么连接用户体验和遥测数据不会进行发送，而是仍保留在本地设备上。

  示例格式：

  ```
  IPv4: 192.246.246.106:100
  IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100
  FQDN: www.contoso.com:345
  ```

## <a name="search"></a>搜索

- **安全搜索(仅限移动版)**：控制 Cortana 在搜索结果中筛选成人内容的方式。 可以选择“严格”或“中等”或允许最终用户选择自己的设置。
- **在搜索中显示 Web 结果**：阻止或允许在设备搜索中显示 Web 结果。

## <a name="start"></a>启动

- **开始菜单布局**：要自定义桌面设备上的开始菜单，可以上传包含自定义项的 XML 文件，包括列出应用的顺序等。 用户无法更改输入的“开始”菜单布局。
- **在开始菜单中将网站固定到磁贴上**：从 Microsoft Edge 导入图像，这些图像在桌面设备的 Windows 开始菜单中显示为链接。
- **从任务栏取消固定应用**：选择“阻止”可阻止用户从任务栏取消固定应用。
- **快速用户切换**：选择“阻止”可防止在未注销的情况下在同时登录的用户之间切换。
- **最常用的应用**：选择“阻止”可隐藏最常用的应用，使其不在开始菜单上显示。 还可通过此设置禁用“设置”应用中的相应切换。
- **最近添加的应用**：选择“阻止”可隐藏最近添加的应用，使其不在开始菜单上显示。 还可通过此设置禁用“设置”应用中的相应切换。
- **开始屏幕模式**：选择开始屏幕的显示方式。 选择此项可将开始屏幕显示为“全屏”或“非全屏”。
- **跳转列表中最近打开的项目**：选择“阻止”可隐藏最近的跳转列表，使其不在开始菜单和任务栏上显示。 还可通过此设置禁用“设置”应用中的相应切换。
- **应用列表**：选择“设置”应用的显示方式。 选项包括： 
  - 折叠
  - 折叠并禁用“设置”应用 
  - 删除并禁用“设置”应用
- **电源按钮**：选择“阻止”可隐藏电源按钮，使其不在开始菜单中显示。
- **用户磁贴**：选择“阻止”可隐藏用户磁贴，使其不在开始菜单中显示。
  - **锁定**：选择“阻止”可隐藏 `Lock` 选项，使其不在开始菜单的用户磁贴中显示。
  - **注销**：选择“阻止”可隐藏 `Sign out` 选项，使其不在开始菜单的用户磁贴中显示。
- **关机**：选择“阻止”可隐藏 `Update and shut down` 和 `Shut down` 选项，使其不在开始菜单的电源按钮中显示。
- **睡眠**：选择“阻止”可隐藏 `Sleep` 选项，使其不在开始菜单的电源按钮中显示。
- **休眠**：选择“阻止”可隐藏 `Hibernate` 选项，使其不在开始菜单的电源按钮中显示。
- **切换帐户**：选择“阻止”可隐藏 `Switch account`，使其不在开始菜单的用户磁贴中显示。
- **重新启动选项**：选择“阻止”可隐藏 `Update and restart` 和 `Restart` 选项，使其不在开始菜单的电源按钮中显示。
- **“开始”上的文档**：隐藏或显示 Windows 开始菜单中的文档文件夹。
- **“开始”上的下载**：隐藏或显示 Windows 开始菜单中的下载文件夹。
- **“开始”上的文件资源管理器**：隐藏或显示 Windows 开始菜单中的文件资源管理器应用。
- **“开始”上的家庭组**：隐藏或显示 Windows 开始菜单中的家庭组文件夹。
- **“开始”上的音乐**：隐藏或显示 Windows 开始菜单中的音乐文件夹。
- **“开始”上的网络**：隐藏或显示 Windows 开始菜单中的网络文件夹。
- **“开始”上的个人文件夹**：隐藏或显示 Windows 开始菜单中的个人文件夹。
- **“开始”上的图片**：隐藏或显示 Windows 开始菜单中的图片文件夹。
- **“开始”上的设置**：隐藏或显示 Windows 开始菜单中的设置应用。
- **“开始”上的视频**：隐藏或显示 Windows 开始菜单中的视频文件夹。

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen

- **Microsoft Edge SmartScreen**：启用 Microsoft Edge SmartScreen，以便访问网站和下载文件。
- **恶意网站访问**：阻止用户忽略 Windows Defender SmartScreen 筛选器警告，并阻止用户转到网站。
- **未验证的文件下载**：阻止用户忽略 Windows Defender SmartScreen 筛选器警告，并阻止用户下载未验证的文件。

## <a name="windows-spotlight"></a>Windows 聚焦

- **Windows 聚焦**：使用此设置在 Windows 10 设备上阻止所有 Windows 聚焦功能。 如果阻止此设置，以下设置也将不可用：
  - **锁定屏幕上的 Windows 聚焦**：阻止 Windows 聚焦在设备锁定屏幕上显示信息。
  - **Windows 聚焦中的第三方建议**：阻止 Windows 聚焦建议不由 Microsoft 发布的内容。
  - **使用者功能**：使你能够阻止开始菜单建议等使用者功能和成员资格通知。
  - **Windows 提示**：使你能够阻止在 Windows 中显示弹出窗口提示。
  - **操作中心中的 Windows 聚焦**：阻止 Windows 聚焦建议（如新应用或安全内容）在 Windows 操作中心显示。
  - **Windows 聚焦个性化**：阻止 Windows 聚焦基于设备使用情况对结果进行个性化设置。
  - **Windows 欢迎体验**：阻止 Windows 欢迎体验向用户显示有关新功能或更新功能的信息。

## <a name="windows-defender-antivirus"></a>Windows Defender 防病毒

- **实时监控**：启用对恶意软件、间谍软件和其他不需要的软件的实时扫描。
- **行为监控**：允许 Defender 检查设备上是否存在某些已知模式的可疑活动。
- **网络检查系统 (NIS)**：NIS 可帮助保护设备免遭基于网络的攻击。 它使用 Microsoft Endpoint Protection 中心中的已知漏洞签名来帮助检测和阻止恶意流量。
- **扫描所有下载**：控制 Defender 是否扫描从 Internet 下载的所有文件。
- **扫描 Microsoft Web 浏览器中加载的脚本**：允许 Defender 扫描在 Internet Explorer 中使用的脚本。
- **Defender 的最终用户访问权限**：控制是否对最终用户隐藏 Windows Defender 用户界面。 此设置更改后，在最终用户的电脑下次重启时生效。
- **签名更新间隔(小时)**：输入 Defender 检查新签名文件的时间间隔。
- **监视文件和程序活动**：允许 Defender 监视设备上的文件和程序活动。
- **删除已隔离恶意软件之前的天数**：按输入的天数继续跟踪已解决的恶意软件，以便可以手动检查之前受影响的设备。 如果你将天数设置为 0，则恶意软件将保留在隔离文件夹中，并且不会自动删除。
- **在扫描期间限制 CPU 使用率**：限制允许扫描使用的 CPU 量（从 1 到 100）。
- **扫描存档文件**：允许 Defender 扫描存档的文件（如 Zip 或 Cab 文件）。
- **扫描传入的电子邮件**：允许 Defender 在电子邮件到达设备时扫描它们。
- **完全扫描期间扫描可移动驱动器**：允许 Defender 扫描可移动驱动器（如 U 盘）。
- **完全扫描期间扫描映射的网络驱动器**：允许 Defender 扫描映射网络驱动器上的文件。
  如果驱动器上的文件是只读的，则 Defender 无法删除在其中找到的任何恶意软件。
- **扫描从网络文件夹打开的文件**：允许 Defender 扫描共享网络驱动器上的文件（例如，从 UNC 路径访问的文件）。 如果驱动器上的文件是只读的，则 Defender 无法删除在其中找到的任何恶意软件。
- **Cloud 保护**：允许或阻止 Microsoft Active Protection Service 接收来自你管理的设备的恶意软件活动的相关信息。 此信息可在将来改进本服务。
- **在示例提交前提示用户**：控制是否自动向 Microsoft 发送可能需要进一步分析的潜在恶意文件。
- **每天执行快速扫描的时间**：选择要运行每天快速扫描的时间。 “未配置”（默认）不运行每天扫描。 如果需要更多自定义，请配置“要执行的系统扫描类型”设置。

  [Defender/ScheduleQuickScanTime CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime)
- **要执行的系统扫描类型**：计划系统扫描，包括扫描级别以及运行扫描的日期和时间。 选项包括：
  - **未配置**：不在设备上计划系统扫描。 最终用户可根据需要在其设备上手动运行扫描。
  - **禁用**：禁用设备上的所有系统扫描。 如果使用的是扫描设备的合作伙伴防病毒解决方案，请选择此选项。
  - **快速扫描**：查看可能注册恶意软件的常见位置，如注册表项和已知的 Windows 启动文件夹。
    - **计划日期**：选择运行扫描的日期。
    - **计划时间**：选择运行扫描的时间。
  - **完全扫描**：查看可能注册恶意软件的常见位置，并扫描设备上的每个文件和文件夹。
    - **计划日期**：选择运行扫描的日期。
    - **计划时间**：选择运行扫描的时间。

  此设置可能与“要执行每日快速扫描的时间”设置相冲突。 一些建议：

  - 若要运行每日快速扫描，请配置“要执行每日快速扫描的时间”设置。
  - 若要每周运行每日快速扫描和完全扫描，请配置“要执行每日快速扫描的时间”，并将“要执行的系统扫描类型”设置为带日期和时间的完全扫描。
  - 请勿在“要执行的系统扫描类型”设置为“快速扫描”的同时配置“要执行每日快速扫描的时间”设置。 这些设置可能会发生冲突，扫描可能无法运行。
  - 若要在每周二上午 6 点运行快速扫描，请配置“要执行的系统扫描类型”设置。

  [Defender/ScanParameter CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter)  
  [Defender/ScheduleScanDay CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday)  
  [Defender/ScheduleScanTime CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime)

- **检测可能不需要的应用程序**：在Windows 检测到可能不需要的应用程序时选择保护级别：
  - **阻止**
  - **审核**有关可能不需要的应用程序的详细信息，请参阅[检测和阻止可能不需要的应用程序](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus)。
- **检测到恶意软件威胁时的操作**：选择 Defender 针对其检测到的每个威胁级别（低、中、高和严重）要执行的操作。 选项包括：
  - **清理**
  - **隔离**
  - **移除**
  - **允许**
  - **用户定义**
  - **阻止**

### <a name="windows-defender-antivirus-exclusions"></a>Windows Defender 防病毒排除项

- **要从扫描和实时保护排除的文件和文件夹**：向排除列表添加一个或多个文件和文件夹（如 C:\Path 或 %ProgramFiles%\Path\filename.exe）。 不会在任何实时或计划的扫描中包括这些文件和文件夹。
- **要从扫描和实时保护排除的文件扩展名**：向排除列表添加一个或多个文件扩展名（如 jpg 或 txt）。 不会在任何实时或计划的扫描中包括具有这些扩展名的任何文件。
- **要从扫描和实时保护排除的进程**：向排除列表添加一个或多个类型为 .exe、.com 或 .scr 的进程。 这些进程不会包括在任何实时或计划的扫描中。

## <a name="next-steps"></a>后续步骤

有关每个设置以及支持的 Windows 版本的其他技术详细信息，请参阅 [Windows 10 策略 CSP 参考](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider)
