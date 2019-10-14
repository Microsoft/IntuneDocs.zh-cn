---
title: Microsoft Intune 中适用于 Windows 10 的设备限制设置 - Azure | Microsoft Docs
description: 有关如何在 Windows 10 及更高版本设备上创建设备限制的信息，请参阅所有设置及其说明的列表。 使用配置文件中的这些设置可以控制 Microsoft Intune 中的屏幕截图、密码要求、展台设置、应用商店中的应用、Microsoft Edge 浏览器、Windows Defender、对云的访问权限、开始菜单等。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 149da4c5aafc436156b7b29566bb5d792506de7c
ms.sourcegitcommit: b1e97211db7cb949eb39be6776b3a11d434fdab0
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/10/2019
ms.locfileid: "72251546"
---
# <a name="windows-10-and-newer-device-settings-to-allow-or-restrict-features-using-intune"></a>便于使用 Intune 允许或限制功能的 Windows 10（及更高版本）设备设置

本文列出并介绍了可以在 Windows 10 和更高版本设备上控制的所有不同设置。 作为移动设备管理 (MDM) 解决方案的一部分，请使用这些设置以允许或禁用功能、设置密码规则、自定义锁屏界面，使用 Microsoft Defender 等。

这些设置将添加到 Intune 中的设备配置配置文件中，然后分配或部署到 Windows 10 设备。

> [!Note]
> 并非所有选项在所有版本的 Windows 上都可用。 若要查看受支持的版本，请参阅 [policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider)（策略 CSP）（打开另一个 Microsoft 网站）。

## <a name="before-you-begin"></a>开始之前

[创建设备配置文件](device-restrictions-configure.md#create-the-profile)。

## <a name="app-store"></a>App Store

这些设置使用 [ApplicationManagement 策略 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement)，该策略还列出了受支持的 Windows 版本。

- **应用商店**（仅限移动设备）：选择性“未配置”（默认）可允许最终用户访问移动设备上的应用商店  。 选择“阻止”可阻止使用应用商店  。
- **自动更新应用商店的应用**：选择“未配置”（默认）可允许自动更新从 Microsoft 应用商店安装的应用  。 选择“阻止”可阻止自动安装更新  。
- **受信任的应用安装**：选择是否可以安装非 Microsoft Store 应用，也称为旁加载。 安装旁加载，然后运行或测试未经 Microsoft Store 认证的应用。 例如，仅适用于公司内部的应用。 选项包括：
  - **未配置**（默认）：使用操作系统默认值。
  - **阻止**：阻止旁加载。 无法安装非 Microsoft Store 应用程序。
  - **允许**：允许旁加载。 可以安装非 Microsoft Store 应用程序。
- **开发人员解锁**：允许 Windows 开发人员设置，如允许最终用户修改旁加载的应用。 选项包括：
  - **未配置**（默认）：使用操作系统默认值。
  - **阻止**：阻止开发者模式和旁加载应用。
  - **允许**：允许开发者模式和旁加载应用。

  有关此功能的详细信息，请参阅[启用设备进行开发](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)。

- **共享用户应用数据**：选择“允许”可在同一设备上的不同用户之间以及该应用的其他实例之间共享应用数据  。 选择“未配置”（默认）可阻止与其他用户和同一应用的其他实例共享数据  。
- **仅使用专用应用商店**：选择“允许”仅允许从专用应用商店下载应用，而不从公用应用商店下载，包括零售目录  。 选择“未配置”（默认）则允许从专用应用商店和公用应用商店下载应用  。
- **启动来自应用商店的应用**：选择“阻止”可禁用设备上预安装或从 Microsoft 应用商店下载的所有应用  。 选择“未配置”（默认）则允许打开这些应用  。
- **在系统卷上安装应用数据**：选择“阻止”可阻止应用在设备的系统卷上存储数据  。 选择“未配置”（默认）则允许应用在系统磁盘卷上存储数据  。
- **在系统驱动器上安装应用**：选择“阻止”可阻止在设备的系统驱动器上安装应用  。 选择“未配置”（默认）则允许在系统驱动器上安装应用  。
- **游戏 DVR**（仅桌面版）：选择“阻止”可禁用 Windows 游戏录制和播放  。 选择“未配置”（默认）则允许录制和播放游戏  。
- **仅限来自应用商店的应用**：此设置确定用户从 Microsoft Store 以外的位置安装应用时的用户体验。 选项包括：

  - **未配置**（默认）：允许最终用户从 Microsoft Store 以外的位置安装应用，包括其他策略设置中定义的应用。  
  - **任何地方**：关闭应用建议，并允许用户从任何位置安装应用。  
  - **仅限应用商店**：强制最终用户仅从 Microsoft Store 安装应用。
  - **建议**：从 Microsoft Store 中提供的 web 安装应用时，用户将看到一条消息，建议用户从应用商店下载该应用。  
  - **首选存储**：当用户安装来自 Microsoft Store 以外的位置时警告用户。

  [SmartScreen/EnableAppInstallControl CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen#smartscreen-enableappinstallcontrol)

- **用户对安装进行控制**：当设置为“未配置”  （默认），Windows Installer 将阻止用户更改通常为系统管理员保留的安装选项，如输入安装文件的目录。 “块”  允许用户更改这些安装选项，并绕过某些 Windows Installer 的安全功能。

  [ApplicationManagement/MSIAllowUserControlOverInstall CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-msiallowusercontroloverinstall)

- **使用提升的权限安装应用程序**：当设置为“未配置”  （默认），如果系统安装系统管理员没有部署或提供的程序，它将应用当前用户的权限。 当 Windows Installer 在系统上安装任何程序时，“块”  将指示它使用提升的权限。 这些权限扩展到所有程序。

  [ApplicationManagement/MSIAlwaysInstallWithElevatedPrivileges CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-msialwaysinstallwithelevatedprivileges)

- **启动应用**：输入用户登录设备后要打开的应用程序列表。 请确保使用分号分隔的 Windows 应用程序包系列名称 (PFN) 列表。 若要运行此策略，Windows 应用程序清单必须使用启动任务。

  [ApplicationManagement/LaunchAppAfterLogOn CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-launchappafterlogon)

## <a name="cellular-and-connectivity"></a>手机网络和连接性

这些设置使用[连接策略](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity)和 [Wi-Fi 策略](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) CSP，它们还列出了受支持的 Windows 版本。

- [Wi-Fi 策略 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi)

- **手机网络数据通道**：选择最终用户在连接到手机网络时是否可以使用数据，例如浏览 Web。 选项包括：
  - **未配置**（默认）：使用默认的操作系统，可能允许手机网络数据信道。 最终用户可以将其关闭。
  - **阻止**：不允许手机网络数据信道。 最终用户无法将其打开。
  - **允许(不可编辑)** ：允许手机网络数据信道。 最终用户不能将其关闭。

- **数据漫游**：选择“阻止”可阻止设备上的手机网络数据漫游  。 选择“未配置”（默认）则允许在访问数据时进行网络之间的漫游  。
- **通过手机网络使用 VPN**：选择“阻止”会可阻止设备在连接到手机网络时访问 VPN 连接  。 选择“未配置”（默认）则允许 VPN 使用任何连接，包括手机网络  。
- **通过手机网络漫游 VPN**：选择“阻止”可阻止设备在手机网络上漫游时访问 VPN 连接  。 选择“未配置”（默认）则允许漫游时的 VPN 连接  。
- **已连接的设备服务**：选择“阻止”可禁用已连接的设备平台 (CDP) 组件  。 CDP 支持发现和连接到其他设备（通过蓝牙/LAN 或云），以支持远程应用启动、远程消息传递、远程应用会话和其他跨设备体验。 选择“未配置”（默认）则允许使用已连接的设备服务，这样可以发现并连接到其他蓝牙设备  。
- **NFC**：选择“阻止”可阻止近场通信 (NFC) 功能  。 选择“未配置”（默认）则允许用户在设备上启用和配置 NFC 功能  。
- **Wi-Fi**：选择“阻止”可阻止用户在设备上启用、配置和使用 Wi-Fi 连接  。 选择“未配置”（默认）则允许 Wi-Fi 连接  。
- **自动连接到 Wi-Fi 热点**：选择“阻止”可阻止设备自动连接到 Wi-Fi 热点  。 选择“未配置”（默认）可让设备自动连接到免费 Wi-Fi 热点并自动接受该连接的任何条款和条件  。
- **手动 Wi-Fi 配置**：选择“阻止”可阻止设备连接到 MDM 服务器安装的网络之外的 Wi-Fi  。 选择“未配置”（默认）则允许终端用户添加和配置自己的 Wi-Fi 连接网络 SSID  。
- **Wi-Fi 扫描间隔**：输入设备扫描 Wi-Fi 网络的频率。 输入从 1（频率最高）到 500（频率最低）的值。 默认值为 `0`。

### <a name="bluetooth"></a>Bluetooth

这些设置使用[蓝牙策略 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth)，该策略还列出了受支持的 Windows 版本。

- **蓝牙**：选择“阻止”可阻止用户启用蓝牙  。 选择“未配置”（默认）则允许使用设备上的蓝牙  。
- **蓝牙可发现性**：选择“阻止”可阻止其他已启用蓝牙的设备发现此设备  。 选择“未配置”（默认）则允许其他支持蓝牙的设备（如耳机）发现该设备  。
- **蓝牙预配对**：选择“阻止”可阻止配置特定蓝牙设备自动与主机设备配对  。 选择“未配置”（默认）则允许与主机设备自动配对  。
- **蓝牙广告**：选择“阻止”可阻止设备发送蓝牙广告  。 选择“未配置”（默认）则允许设备发送蓝牙广告  。
- **蓝牙允许的服务**：将允许的蓝牙服务和配置文件列表“添加”为十六进制字符串，例如 `{782AFCFC-7CAA-436C-8BF0-78CD0FFBD4AF}`  。

  有关服务列表的详细信息，请参阅 [ServicesAllowedList 用法指南](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth#servicesallowedlist-usage-guide)。

## <a name="cloud-and-storage"></a>云和存储

这些设置使用[帐户策略 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-accounts)，该策略还列出了受支持的 Windows 版本。

- **Microsoft 帐户**：选择“阻止”可阻止最终用户将 Microsoft 帐户与设备关联  。 选择“未配置”（默认）则允许添加和使用 Microsoft 帐户  。
- **非 Microsoft 帐户**：选择“阻止”可阻止最终用户使用用户界面添加非 Microsoft 帐户  。 选择“未配置”（默认）可允许用户添加与 Microsoft 帐户无关的电子邮件帐户  。
- **Microsoft 帐户的设置同步**：选择“未配置”（默认）可允许设备和应用设置与 Microsoft 帐户关联以在设备之间进行同步  。 选择“阻止”可阻止这种同步  。
- **Microsoft 帐户登录助手**：设置为“未配置”（默认）时，最终用户可以启动和停止“Microsoft 帐户登录助手”(wlidsvc) 服务   。 此操作系统服务允许用户登录到其 Microsoft 帐户。 选择“禁用”可防止终端用户控制 Microsoft 登录助手服务 (wlidsvc)  。

## <a name="cloud-printer"></a>云打印机

这些设置使用 [EnterpriseCloudPrint 策略 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-enterprisecloudprint)，该策略还列出了受支持的 Windows 版本。

- **打印机发现 URL**：输入用于发现云打印机的 URL。 例如，输入 `https://cloudprinterdiscovery.contoso.com`。
- **打印机访问授权机构 URL**：输入身份验证终结点 URL 以获取 OAuth 令牌。 例如，输入 `https://azuretenant.contoso.com/adfs`。
- **Azure 本机客户端应用 GUID**：输入有权从 OAuthAuthority 获取 OAuth 令牌的客户端应用程序的 GUID。 例如，输入 `E1CF1107-FF90-4228-93BF-26052DD2C714`。
- **打印服务资源 URI**：输入 Azure 门户中配置的打印服务 OAuth 资源 URI。 例如，输入 `http://MicrosoftEnterpriseCloudPrint/CloudPrint`。
- **要查询的最大打印机数**：输入要查询的最大打印机数。 默认值为 `20`。
- **打印机发现服务资源 URI**：输入 Azure 门户中配置的打印机发现服务 OAuth 资源 URI。 例如，输入 `http://MopriaDiscoveryService/CloudPrint`。

> [!TIP]
> 设置 [Windows Server 混合云打印](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-overview)后，可以配置这些设置，然后部署到 Windows 设备。

## <a name="control-panel-and-settings"></a>控制面板和设置

- **设置应用**：选择“阻止”可阻止最终用户访问 Windows 设置应用  。 选择“未配置”（默认）则允许用户打开设备上的设置应用  。
  - **系统**：选择“阻止”可阻止访问设置应用的系统区域  。 选择“未配置”（默认）则允许访问  。
    - **电源和睡眠设置修改**（仅限桌面版）：选择“阻止”可阻止最终用户更改设备上的电源和睡眠设置  。 选择“未配置”（默认）则允许用户更改电源和睡眠设置  。
  - **设备**：选择“阻止”可阻止访问设备上设置应用的设备区域  。 选择“未配置”（默认）则允许访问  。
  - **网络 Internet**：选择“阻止”可阻止访问设备上设置应用的网络和 Internet 区域  。 选择“未配置”（默认）则允许访问  。
  - **个性化设置**：选择“阻止”可阻止访问设备上设置应用的个性化设置区域  。 选择“未配置”（默认）则允许访问  。
  - **应用**：选择“阻止”可阻止访问设备上设置应用的应用区域  。 选择“未配置”（默认）则允许访问  。
  - **帐户**：选择“阻止”可阻止访问设备上设置应用的帐户区域  。 选择“未配置”（默认）则允许访问  。
  - **时间与语言**：选择“阻止”可阻止访问设备上设置应用的时间与语言区域  。 选择“未配置”（默认）则允许访问  。
    - **系统时间修改**：选择“阻止”可阻止最终用户更改设备上的日期和时间设置  。 “未配置”  则允许用户更改这些设置。
    - **区域设置修改**（仅限桌面版）：选择“阻止”可阻止最终用户更改设备上的区域设置  。 “未配置”  则允许用户更改这些设置。
    - **语言设置设置修改**（仅限桌面版）：选择“阻止”可阻止最终用户更改设备上的语言设置  。 “未配置”  则允许用户更改这些设置。

      [设置策略 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings)

  - **游戏**：选择“阻止”可阻止访问设备上设置应用的游戏区域  。 选择“未配置”（默认）则允许访问  。
  - **轻松访问**：选择“阻止”可阻止访问设备上设置应用的轻松访问区域  。 选择“未配置”（默认）则允许访问  。
  - **隐私**：选择“阻止”可阻止访问设备上设置应用的隐私区域  。 选择“未配置”（默认）则允许访问  。
  - **更新安全**：选择“阻止”可阻止访问设备上设置应用的更新安全区域  。 选择“未配置”（默认）则允许访问  。

## <a name="display"></a>显示器

这些设置使用[显示策略 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-display)，该策略还列出了受支持的 Windows 版本。

借助 GDI DPI 缩放，应用程序可以从非 DPI 感知变成按监视器 DPI 感知。

- **对应用启用 GDI 缩放**：“添加”希望启用 GDI DPI 扩展的旧应用  。 例如，输入 `filename.exe` 或 `%ProgramFiles%\Path\Filename.exe`。

  对列表中的所有旧应用启用 GDI DPI 缩放。

- **对应用禁用 GDI 缩放**：“添加”希望禁用 GDI DPI 扩展的旧应用  。 例如，输入 `filename.exe` 或 `%ProgramFiles%\Path\Filename.exe`。

  对列表中的所有旧应用禁用 GDI DPI 缩放。

还可以使用应用列表“导入”.csv 文件  。

## <a name="general"></a>常规

这些设置使用[体验策略 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience)，该策略还列出了受支持的 Windows 版本。 

- **屏幕捕获**（仅限移动版）：“阻止”可阻止最终用户获取设备的屏幕截图  。 选择“未配置”（默认）则允许此功能  。
- **复制并粘贴（仅限移动版）** ：“阻止”可阻止最终用户在设备上的应用之间使用复制粘贴  。 选择“未配置”（默认）则允许此功能  。
- **手动取消注册**：“阻止”可阻止最终用户使用设备上的工作区控制面板删除工作区帐户  。 选择“未配置”（默认）则允许此功能  。

  如果计算机已加入 Azure AD 并启用自动注册，此策略设置不适用。

- **手动安装根证书**（仅限移动版）：“阻止”可阻止最终用户手动安装根证书和中间 CAP 证书  。 选择“未配置”（默认）则允许此功能  。
- **相机**：“阻止”可阻止最终用户使用设备上的相机  。 选择“未配置”（默认）则允许此功能  。
- **OneDrive 文件同步**：“阻止”可阻止最终用户将文件从设备同步到 OneDrive  。 选择“未配置”（默认）则允许此功能  。
- **可移动存储**：选择“阻止”可阻止最终用户使用外部存储设备，如设备的 SD 卡  。 选择“未配置”（默认）则允许此功能  。
- **地理位置**：选择“阻止”可阻止最终用户打开设备上的位置服务  。 选择“未配置”（默认）则允许此功能  。
- **Internet 共享**：选择“阻止”可阻止在设备上使用 Internet 连接共享  。 选择“未配置”（默认）则允许此功能  。
- **手机重置**：选择“阻止”可阻止最终用户在设备上进行删除或恢复出厂设置  。 选择“未配置”（默认）则允许此功能  。
- **USB 连接**：选择“阻止”可阻止在设备上通过 USB 连接访问外部存储设备  。 选择“未配置”（默认）则允许此功能  。 USB 充电不受此设置影响。
- **防盗模式**（仅限移动版）：“阻止”可阻止最终用户选择设备上的防盗模式首选项  。 选择“未配置”（默认）则允许此功能  。
- **Cortana**：选择“阻止”可禁用设备上的 Cortana 语音助手  。 Cortana 关闭时，用户仍然可以搜索设备上的条目。 选择“未配置”（默认）则允许 Cortana  。
- **语音录制**（仅限移动版）：选择“阻止”可阻止最终用户在设备上使用设备语音录制器  。 选择“未配置”（默认）则允许应用进行语音录制  。
- **设备名称修改**（仅限移动版）：选择“阻止”可阻止最终用户更改设备名称  。 选择“未配置”（默认）则允许此功能  。
- **添加预配包**：选择“阻止”可阻止运行时配置代理在设备上安装预配包  。 选择“未配置”（默认）则允许此功能  。
- **删除预配包**：选择“阻止”可阻止运行时配置代理从设备上删除预配包  。 选择“未配置”（默认）则允许此功能  。
- **设备发现**：选择“阻止”可阻止设备被其他设备发现  。 选择“未配置”（默认）则允许此功能  。
- **任务切换器**（仅限移动版）：选择“阻止”可阻止设备上的任务切换  。 选择“未配置”（默认）则允许此功能  。
- **SIM 卡错误对话框**（仅限移动版）：选择“阻止”可阻止在未检测到 SIM 卡时在设备上显示错误消息  。 选择“未配置”（默认）则会显示错误消息  。
- **墨迹工作区**：选择用户是否以及如何访问墨迹工作区。 选项包括：
  - **未配置**（默认）：可启用墨迹工作区，并且允许用户在锁屏界面上使用它。
  - **在锁定屏幕上禁用**：启用了墨迹工作区并开启功能。 但是，用户不能在锁定屏幕上方访问它。
  - **禁用**：禁止访问墨迹工作区。 该功能处于禁用状态。

  [WindowsInkWorkspace 策略 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace)

- **自动重新部署**：选择“允许”以便具有管理权限的用户可在设备锁定屏幕上使用 CTRL+Win+R 删除所有用户数据和设置   。 设备会自动进行重新配置并重新注册到管理。 “未配置”（默认）会阻止此功能  。
- **要求用户在设备设置期间连接到网络**：选择“需要”以便在 Windows 安装过程中设备先连接到网络，然后再通过“网络”页  。 选择“未配置”（默认）可允许用户通过网络页面，即使它没有连接到网络  。

  该设置在下次擦除或重置设备时生效。 与任何其他 Intune 配置一样，该设备必须由 Intune 注册和管理才能接收配置设置。 但注册后，接收策略并在下一次 Windows 设置期间重置设备会强制执行该设置。

- **直接内存访问**：“阻止”将防止所有热插拔 PCI 下游端口进行直接内存访问 (DMA)，直到用户登录 Windows  。 “启用”  （默认设置）允许访问 DMA，即使用户未登录。

  CSP：[DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess)

- **从任务管理器结束进程**：此设置确定非管理员是否可以使用任务管理器来结束任务。 选择“阻止”，则会阻止标准用户（非管理员）使用任务管理器结束设备上的进程或任务  。 选择“未配置”（默认选项），则会允许标准用户使用任务管理器结束进程或任务  。

## <a name="locked-screen-experience"></a>锁定屏幕体验

- **操作中心通知（仅限移动版）** ：选择“阻止”可阻止设备锁定屏幕上显示操作中心通知  。 选择“未配置”（默认）则允许用户选择哪些应用可在锁定屏幕上显示通知  。

  [AboveLock/AllowActionCenterNotifications CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowactioncenternotifications)

- **锁定屏幕图片 URL（仅限桌面版）** ：输入将用作 Windows 锁定屏幕墙纸的图片（格式为 JPG、JPEG 或 PNG）的 URL。 例如，输入 `https://contoso.com/image.png`。 此设置将锁定该图像，并且无法在以后更改。
- **用户可配置的屏幕超时（仅限移动版）** ：选择“允许”可允许用户配置屏幕超时  。 选择“未配置”（默认）则不向用户提供该选项  。

  [DeviceLock/AllowScreenTimeoutWhileLockedUserConfig CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-allowscreentimeoutwhilelockeduserconfig)

- **锁定屏幕上的 Cortana** （仅限桌面版）：选择“阻止”可阻止用户在设备处于锁定屏幕时与 Cortana 交互  。 选择“未配置”（默认）则允许与 Cortana 交互  。

  [AboveLock/AllowCortanaAboveLock CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowcortanaabovelock)

- **锁屏界面上的 Toast 通知**：选择“阻止”可阻止在设备锁屏界面上显示 Toast 通知  。 选择“未配置”（默认）则允许这些通知  。

  [AboveLock/AllowToasts CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowtoasts)

- **屏幕超时（仅限移动版）** ：设置从屏幕锁定到屏幕关闭之间的持续时间（以秒为单位）。 支持的值为 11-1800。 例如，输入 `300` 以将超时设置为 5 分钟。

  [DeviceLock/ScreenTimeoutWhileLocked CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-screentimeoutwhilelocked)

## <a name="messaging"></a>Messaging

这些设置使用[消息策略 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-messaging)，该策略还列出了受支持的 Windows 版本。

- **消息同步（仅限移动版）** ：选择“阻止”可禁用备份和还原文本消息，以及在 Windows 设备之间同步消息  。 禁用有助于避免将信息存储在组织控件之外的服务器上。 选择“未配置”（默认）则允许用户更改这些设置并同步其消息  。
- **彩信（仅限移动版）** ：选择“阻止”可对设备禁用彩信发送和接收功能  。 对于企业，使用此策略在设备上禁用彩信，作为审计或管理需求的一部分。 选择“未配置”（默认）则允许发送和接收彩信  。
- **富通信(仅限移动版)** ：选择“阻止”可对设备禁用富通信服务 (RCS) 发送和接收功能  。 对于企业，使用此策略在设备上禁用富通信，作为审计或管理需求的一部分。 选择“未配置”（默认）则允许发送和接收富通信  。

## <a name="microsoft-edge-browser"></a>Microsoft Edge 浏览器

这些设置使用[浏览器策略 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser)，该策略还列出了受支持的 Windows 版本。

### <a name="use-microsoft-edge-kiosk-mode"></a>使用 Microsoft Edge 展台模式

可用设置因你所选的项而异。 选项包括：

- **否**（默认）：Microsoft Edge 未在展台模式下运行。 可更改和配置所有 Microsoft Edge 设置。
- **数字/交互式标牌（单应用展台）** ：筛选适用于数字/交互式标牌 Microsoft Edge 展台模式的 Microsoft Edge 设置，仅用于 Windows 10 单应用展台。 选择此设置可打开 URL 全屏，仅显示该网站上的内容。 [设置数字标牌](https://docs.microsoft.com/windows/configuration/setup-digital-signage)提供有关此功能的详细信息。
- **InPrivate 公共浏览（单应用展台）** ：筛选适用于 InPrivate 公共浏览 Microsoft Edge 展台模式的 Microsoft Edge 设置，用于 Windows 10 单应用展台。 运行 Microsoft Edge 的多选项卡版本。
- **普通模式(多应用展台)** ：筛选适用于普通 Microsoft Edge 展台模式的 Microsoft Edge 设置。 使用所有浏览功能运行完整版 Microsoft Edge。
- **公共浏览（多应用展台）** ：筛选适用于 Windows 10 多应用展台上公共浏览的 Microsoft Edge 设置。  运行 Microsoft Edge InPrivate 的多选项卡版本。

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
  - **自定义起始页**：输入起始页，例如 `http://www.contoso.com`。 Microsoft Edge 加载所输入的起始页。
  - **新标签页**：Microsoft Edge 加载“新标签 URL”  设置中输入的任何内容。
  - **最后一次会话的页面**：Microsoft Edge 加载最后一次会话的页面。
  - **本地应用设置起始页**：启动 Microsoft Edge 后将显示由操作系统定义的默认起始页。

- **允许用户更改起始页**：选择“是”（默认）  可让用户更改起始页。 管理员可以使用 `EdgeHomepageUrls` 输入在打开 Microsoft Edge 时用户默认看到的起始页。 选择“否”  可阻止用户更改起始页。
- **在新标签页上允许 Web 内容**：当设置为“是”（默认）时，Microsoft Edge 会打开在“新选项卡 URL”设置中输入的网址   。 如果“新选项卡 URL”设置为空，Microsoft Edge 将打开 Microsoft Edge 设置中列出的新选项卡页  。 用户可更改它。 设置为“否”时，Microsoft Edge 将打开一个带有空白页的新选项卡  。 用户无法更改它。
- **新标签 URL**：输入要在新标签页上打开的 URL。 例如，输入 `https://www.bing.com` 或 `https://www.contoso.com`。

- **主页按钮**：选择按主页按钮时会发生的情况。 选项包括：
  - **起始页**：打开在“启动 Microsoft Edge 的结果”  设置中选择的选项
  - **新标签页**：打开你在“新选项卡 URL”设置中输入的 URL  。
  - **主页按钮 URL**：输入要打开的 URL。 例如，输入 `https://www.bing.com` 或 `https://www.contoso.com`。
  - **隐藏主页按钮**：隐藏主页按钮
- **允许用户更改主页按钮**：选择“是”允许用户更改主页按钮  。 用户的更改会覆盖对主页按钮进行的任何管理员设置。 选择“否”（默认）可阻止用户更改管理员配置主页按钮的方式  。
- **显示首次运行体验页面（仅限移动版）** ：选择“是”（默认）可显示 Microsoft Edge 中的首次使用简介页  。 选择“否”可在首次运行 Microsoft Edge 时阻止显示简介页  。 借助此功能，诸如在零排放配置中注册的企业组织可以阻止此页面。
- **首次运行体验 URL 列表位置**（仅限 Windows 10 移动版）：输入指向包含首次运行页 URL 的 XML 文件的 URL。 例如，输入 `https://www.contoso.com/sites.xml`。

- **空闲时间后刷新浏览器**：输入刷新浏览器之前的空闲分钟数，范围为 0-1440 分钟。 默认为 `5` 分钟。 设置为 `0`（零）时，浏览器在空闲后不刷新。

  此设置仅在 [InPrivate 公共浏览（单应用展台）](#use-microsoft-edge-kiosk-mode)中运行时可用。

- **允许弹出窗口**（仅限桌面版）：选择“是”（默认）可允许在网络浏览器中弹出窗口  。 选择“否”可阻止在浏览器中弹出窗口  。
- **将 Intranet 流量发送到 Internet Explorer**（仅限桌面版）：选择“是”  可让用户在 Internet Explorer 中打开 Intranet 网站。 此设置用于后向兼容性。 选择“否”（默认）可允许用户使用 Microsoft Edge  。
- **企业模式站点列表位置**（仅限桌面版）：输入指向 XML 文件的 URL，该文件包含在企业模式下打开的网站列表。 用户无法更改此列表。 例如，输入 `https://www.contoso.com/sites.xml`。
- **在 Internet Explorer 中打开站点时显示消息**：使用此设置可将 Microsoft Edge 配置为在 Internet Explorer 11 中打开站点之前显示通知。 选项包括：
  - **不显示消息**：使用操作系统的默认行为，这可能不会显示消息。
  - **显示在 Internet Explorer 11 中打开站点的消息**：在 IE 中打开站点时显示消息。 将在 IE 中打开站点。 
  - **显示“在 Microsoft Edge 中打开站点”选项的消息**：在 Microsoft Edge 中打开站点时显示消息。 该消息包含  “在 Microsoft Edge 中继续”链接，以便用户可以选择 Microsoft Edge，而不是 IE。

  > [!IMPORTANT]
  > 此设置要求你使用“企业模式站点列表位置”设置、“将 intranet 流量发送到 Internet Explorer”设置或这两个设置   。

- **允许 Microsoft 兼容性列表**：选择“是”（默认）允许使用 Microsoft 兼容性列表  。 选择“否”会阻止 Microsoft Edge 中的 Microsoft 兼容性列表  。 Microsoft 的此列表可帮助 Microsoft Edge 正确显示具有已知兼容性问题的站点。
- **预加载起始页和“新建选项卡”页**：选择“是”（默认）可使用操作系统默认行为，可能是预加载这些页面  。 预加载可最大程度地缩短启动 Microsoft Edge 和加载新标签的时间。 选择“否”可阻止 Microsoft Edge 预加载起始页和“新建选项卡”页  。
- **预启动起始页和“新建选项卡”页**：选择“是”（默认）可使用操作系统默认行为，可能是预启动这些页面  。 预启动可帮助提高 Microsoft Edge 的性能并最大程度地缩短启动 Microsoft Edge 所需的时间。 选择“否”可阻止 Microsoft Edge 预启动起始页和“新建选项卡”页  。

### <a name="favorites-and-search"></a>收藏夹和搜索

- **显示收藏夹栏**：选择任何 Microsoft Edge 页面上的收藏夹栏会发生的情况。 选项包括：
  - **在起始和新选项卡页上**：在 Microsoft Edge 启动时在所有标签页上显示收藏夹栏。 最终用户无法更改此设置。
  - **所有页面上**：显示所有页面上的收藏夹栏。 最终用户无法更改此设置。
  - **隐藏**：隐藏所有页面上的收藏夹栏。 最终用户无法更改此设置。
- **允许更改收藏夹**：选择“是”（默认）可使用操作系统默认值，允许用户更改列表  。 选择“否”可阻止最终用户添加、导入、排序或编辑收藏夹列表  。
  - **收藏夹列表**：将 URL 列表添加到收藏夹文件。 例如：添加 `http://contoso.com/favorites.html`。
- **同步 Microsoft 浏览器之间的收藏夹（仅限桌面版）** ：选择“是”  会强制 Windows 同步 Internet Explorer 和 Microsoft Edge 之间的收藏夹。 在浏览器之间共享对收藏夹执行的添加、删除、修改和顺序更改操作。  选择“否”（默认）  可使用 OS 默认值，这可能会为用户提供在浏览器之间同步收藏夹的选项。
- **默认搜索引擎**：选择设备上的默认搜索引擎。 最终用户可以随时更改此值。 选项包括：
  - 客户端 Microsoft Edge 设置中的搜索引擎
  - 必应
  - Google
  - Yahoo
  - 自定义值：在“OpenSearch Xml URL”中，输入带有 XML 文件的 HTTPS URL，该文件至少包含短名称和搜索引擎的 URL  。 例如，输入 `https://www.contoso.com/opensearch.xml`。
- **显示搜索建议**：选择“是”（默认）  可允许搜索引擎在你在地址栏中键入搜索短语时建议站点。 选择“否”  则阻止此功能。
- **允许更改搜索引擎**：“是”（默认）允许用户添加新搜索引擎，或更改 Microsoft Edge 中的默认搜索引擎  。 选择“否”可阻止用户自定义搜索引擎  。

  此设置仅在[普通模式（多应用展台）](#use-microsoft-edge-kiosk-mode)中运行时可用。

### <a name="privacy-and-security"></a>隐私和安全性

- **允许 InPrivate 浏览**：选择“是”（默认）可允许在 Microsoft Edge 中进行 InPrivate 浏览  。 关闭所有 InPrivate 选项卡后，Microsoft Edge 将从设备中删除浏览数据。 选择“否”可阻止最终用户打开 InPrivate 浏览会话  。
- **保存浏览历史记录**：选择“是”（默认）可允许在 Microsoft Edge 中保存浏览历史记录  。 选择“否”可阻止保存浏览历史记录  。
- **退出时清除浏览数据(仅限桌面版)** ：选择“是”  可在用户退出 Microsoft Edge 时清除历史记录和浏览数据。 选择“否”（默认）  可使用 OS 默认值，这可能会缓存浏览数据。
- **同步用户设备之间的浏览器设置**：选择同步设备之间的浏览器设置的方式。 选项包括：
  - **允许**：允许同步用户的设备之间的 Microsoft Edge 浏览器设置
  - **阻止和启用用户覆盖**：阻止同步用户的设备之间的 Microsoft Edge 浏览器设置。 用户可以覆盖此设置。
  - **阻止**：阻止同步用户的设备之间的 Microsoft Edge 浏览器设置。 用户无法覆盖此设置。

当选择“阻止并启用用户覆盖”时，用户可以覆盖管理员指定内容。

- **允许使用密码管理器**：选择“是”（默认）可允许 Microsoft Edge 自动使用密码管理器，因此用户可在设备上保存和管理密码  。 选择“否”可阻止 Microsoft Edge 使用密码管理器  。
- **Cookie**：选择在 Web 浏览器中处理 Cookie 的方式。 选项包括：
  - **允许**：Cookie 存储在设备上。
  - **阻止所有 Cookie**：Cookie 未存储在设备上。
  - **仅阻止第三方 Cookie**：第三方或合作伙伴 Cookie 未存储在设备上。
- **允许自动填充表单**：选择“是”（默认）可允许用户更改浏览器中的自动完成设置，并自动填充表单字段  。 选择“否”可禁用 Microsoft Edge 中的自动填充功能  。
- **发送不跟踪标头**：选择“是”可向请求跟踪信息的网站发送不跟踪标头（推荐）  。 选择“否”（默认）不会发送允许网站跟踪用户的标头  。 用户可以配置。
- **显示 WebRTC 本地主机 IP 地址**：选择“是”（默认）可允许在使用此协议拨打电话时显示用户的本地主机 IP 地址  。 选择“否”会阻止显示用户的本地主机 IP 地址  。 
- **允许动态磁贴数据收集**：选择“是”（默认）可允许 Microsoft Edge 从固定到开始菜单的动态磁贴收集信息  。 选择“否”会阻止收集此信息，这可能会为用户提供有限的体验  。
- **用户可以覆盖证书错误**：选择“是”（默认）可允许用户访问具有安全套接字层/传输层安全性 (SSL/TLS) 错误的网站  。 选择“否”（建议用于提高安全性）可阻止用户访问具有 SSL 或 TLS 错误的网站  。

### <a name="additional"></a>Additional

- **允许 Microsoft Edge 浏览器**（仅限移动版）：选择“是”（默认）可允许在移动设备上使用 Microsoft Edge Web 浏览器  。 选择“否”可阻止在设备上使用 Microsoft Edge  。 如果选择“否”，则其他个人设置仅适用于桌面  。
- **允许地址栏下拉列表**：选择“是”（默认）可允许 Microsoft Edge 显示地址栏下拉列表以及建议列表  。 选择“否”可阻止 Microsoft Edge 在键入内容时在下拉列表中显示建议列表  。 设置为“否”时，可  ：
  - 有助于最大程度减少 Microsoft Edge 和 Microsoft 服务之间的网络带宽使用。
  - 在“Microsoft Edge”>“设置”中键入内容时，禁用显示搜索和网站建议  。
- **允许全屏模式**：选择“是”（默认）可允许 Microsoft Edge 使用全屏模式，该模式仅显示 Web 内容并隐藏 Microsoft Edge UI  。 选择“否”会阻止 Microsoft Edge 使用全屏模式  。
- **允许标记页面**：选择“是”（默认）可使用操作系统默认值，这可能允许访问 `about:flags` 页面  。 `about:flags` 页面允许用户更改开发人员设置并启用实验性功能。 选择“否”可阻止最终用户访问 Microsoft Edge 中的 `about:flags` 页面  。
- **允许开发人员工具**：选择“是”（默认）可允许用户默认使用 F12 开发人员工具来生成和调试网页  。 选择“否”可阻止最终用户使用 F12 开发人员工具  。
- **允许 JavaScript**：选择“是”（默认）可允许脚本（如 Javascript）在 Microsoft Edge 浏览器中运行  。 选择“否”可阻止在设备上运行浏览器中的 Java 脚本  。
- **用户可安装扩展**：选择“是”（默认）可允许最终用户在设备上安装 Microsoft Edge 扩展  。 选择“否”可阻止安装  。
- **允许旁加载开发人员扩展**：选择“是”（默认）可使用操作系统默认值，这可能允许旁加载  。 旁加载安装并运行未经验证的扩展。 选择“否”可阻止 Microsoft Edge 使用“加载扩展”功能进行旁加载   。 它不会阻止使用其他方式加载扩展，例如 PowerShell。
- **必需扩展**：选择最终用户在 Microsoft Edge 中不能关闭的扩展。 输入包系列名称，然后选择“添加”  。 [查找包系列名称 (PFN)](https://docs.microsoft.com/sccm/protect/deploy-use/find-a-pfn-for-per-app-vpn) 提供一些指导。

  还可以  导入包含包系列名称的 CSV 文件。 或者，“导出”输入的包系列名称  。

## <a name="network-proxy"></a>网络代理

这些设置使用 [NetworkProxy 策略 CSP](https://docs.microsoft.com/windows/client-management/mdm/networkproxy-csp)，该策略还列出了受支持的 Windows 版本。

- **自动检测代理设置**：选择“阻止”可禁用设备自动检测代理自动配置 (PAC) 脚本  。 选择“未配置”（默认）可启用此功能  。 启用后，设备会尝试查找 PAC 脚本的路径。
- **使用代理脚本**：选择“允许”可输入 PAC 脚本的路径以配置代理服务器  。 选择“未配置”（默认）则不允许你输入 PAC 脚本的 URL  。
  - **设置脚本地址 URL**：输入想要使用的 PAC 脚本的 URL，以配置代理服务器。
- **使用手动代理服务器**：选择“允许”可手动输入代理服务器的名称或 IP 地址和 TCP 端口号  。 选择“未配置”（默认）则不允许手动输入代理服务器的详细信息  。
  - **地址**：输入代理服务器的名称或 IP 地址。
  - **端口号**：输入代理服务器的端口号。
  - **代理例外**：输入不得使用代理服务器的任何 URL。 请使用分号分隔每一项。
  - **跳过本地地址的代理服务器**：选择“未配置”（默认）可阻止在 Intranet 上使用代理服务器作为本地地址  。 选择“允许”可将代理服务器用于本地地址  。

## <a name="password"></a>密码

这些设置使用 [DeviceLock 策略 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock)，该策略还列出了受支持的 Windows 版本。

- **密码**：选择“必需”  ，最终用户输入密码才能访问设备。 选择“未配置”（默认）可允许在没有密码的情况下访问设备  。 仅适用于本地帐户。 域帐户密码保留 Active Directory （AD）和 Azure AD 配置。

  - **所需的密码类型**：选择密码类型。 选项包括：
    - **未配置**：密码可以包含数字和字母。
    - **数字**：密码必须只是数字。
    - **字母数字**：密码必须是数字和字母的混合。
  - **最短密码长度**：输入所需的最小数量或字符数，范围为 4-16。 例如，输入 `6` 可要求密码长度至少为六个字符。
  
    > [!IMPORTANT]
    > 当 Windows 桌面的密码要求更改时，用户下次登录时会受到影响，因为此时设备从空闲状态变为活动状态。 密码满足要求的用户仍然会被提示更改密码。
    
  - **登录失败多少次后擦除设备**：输入身份验证失败多少次后可擦除设备，最多为 11 次。 输入的有效数字取决于版本。 [DeviceLock/MAXDEVICEPASSWORDFAILEDATTEMPTS CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxdevicepasswordfailedattempts)列出了支持的值。 如果为 `0`（零），可能会禁用设备擦除功能。

    此设置的影响也因版本而异。 有关此设置的具体详细信息，请参阅 [DeviceLock/MaxDevicePasswordFailedAttempts CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxdevicepasswordfailedattempts)。

  - **屏幕锁定前的最大非活动状态分钟数**：输入锁定屏幕前，设备必须处于空闲状态的时间长度。
  - **密码过期(天)** ：必须更改设备密码时，输入时间长度（天数），从 1 到 365。 例如，要使密码在 90 天后过期，请输入 `90`。
  - **阻止重用以前的密码**：输入以前用过的不能重用的密码数，从 1 到 24。 例如，输入 `5` 意味着用户不能将其新密码设置为当前密码或以前四个密码中的任何一个。
  - **设备从空闲状态返回时需要密码**（移动和全息）：选择“需要”，以便用户在空闲后必须输入密码才能解锁设备  。 选择“未配置”（默认）可在设备从空闲状态恢复时不需要 PIN 或密码  。
  - **简单密码**：设置为“阻止”  后，用户无法创建简单密码，如 `1234` 或 `1111`。 设置为“未配置”（默认），可允许用户创建 `1234` 或 `1111` 等密码  。 此设置还允许或阻止使用 Windows 图片密码。
- **AADJ 期间的自动加密**：设备加入 Azure AD 后，准备首次使用时，“阻止”会阻止自动 BitLocker 设备加密  。 “未配置”（默认）使用操作系统默认值，可以启用加密  。 有关详细信息，请参阅 [BitLocker 设备加密](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-device-encryption-overview-windows-10#bitlocker-device-encryption)。

  [Security/PreventAutomaticDeviceEncryptionForAzureADJoinedDevices CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-security#security-preventautomaticdeviceencryptionforazureadjoineddevices)

- **美国联邦信息处理标准 (FIPS) 政策**：“允许”使用美国联邦信息处理标准 (FIPS) 政策，该政策是美国政府加密、散列和签名的标准  。 “未配置”（默认）使用操作系统默认值，它不会使用 FIPS  。

  [Cryptography/AllowFipsAlgorithmPolicy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-cryptography#cryptography-allowfipsalgorithmpolicy)

- **Windows Hello 设备身份验证**：“允许”用户使用 Windows Hello 配套设备（如手机、健身手环或 IoT 设备）登录到 Windows 10 计算机  。 “未配置”（默认）使用操作系统默认值，这可能会阻止 Windows Hello 配套设备进行 Windows 身份验证  。

  [Authentication/AllowSecondaryAuthenticationDevice CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowsecondaryauthenticationdevice)

- **Web 登录**：为非 ADFS（Active Directory 联合身份验证服务）联合提供程序（如安全断言标记语言 (SAML)）启用 Windows 登录支持。 SAML 使用安全令牌，该令牌为 Web 浏览器提供单一登录 (SSO) 体验。 选项包括：

  - **未配置**（默认）：在设备上使用操作系统默认值。
  - **已启用**：已为登录启用了 Web 凭据提供程序。
  - **已禁用**：已为登录禁用了 Web 凭据提供程序。

  [Authentication/EnableWebSignIn CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-enablewebsignin)

- **首选 Azure AD 租户域**：在你的 Azure AD 组织中输入现有域名。 当此域中的用户登录时，无需键入域名。 例如，输入 `contoso.com`。 `contoso.com` 域中的用户可使用其用户名登录，如 `abby`，而不是 `abby@contoso.com`。

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

这些设置使用[个性化设置策略 CSP](https://docs.microsoft.com/windows/client-management/mdm/personalization-csp)，该策略还列出了受支持的 Windows 版本。

- **桌面背景图片 URL (仅限桌面版)** ：输入要用作 Windows 桌面墙纸的图片（格式为 .jpg、.jpeg 或 .png）的 URL。 用户无法更改图片。 例如，输入 `https://contoso.com/logo.png`。

## <a name="printer"></a>打印机

- **打印机**：已添加的本地打印机的列表。
- **默认打印机**：设置默认打印机。
- **用户添加新打印机的权限**：允许或阻止使用本地打印机。

## <a name="privacy"></a>隐私

这些设置使用[隐私策略 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-privacy)，该策略还列出了受支持的 Windows 版本。

- **输入个性化**：如果设置为“阻止”  ，可阻止使用语音进行听写，以及与 Cortana 和其他使用基于 Microsoft 云的语音识别的应用进行对话。 已将其禁用，用户无法使用设置启用在线语音识别。 选择“未配置”（默认）则允许用户选择  。 如果允许这些服务，Microsoft 可能会收集语音数据以改进服务。
- **自动接受配对和隐私用户同意提示**：选择“允许”以便 Windows 可在运行应用时自动接受配对和隐私同意消息  。 选择“未配置”（默认）会阻止打开应用时自动接受配对和隐私用户同意窗口  。
- **发布用户活动**：选择“阻止”  可阻止活动源中最近使用资源的共享体验和发现。 选择“未配置”（默认）可启用此功能，以便应用可以发布最终用户活动  。
- **仅限本地活动**：“阻止”  可仅基于本地活动阻止任务切换程序中最近使用资源的共享体验和发现。 选择“未配置”（默认）可启用此功能  。

可以配置设备上的所有应用可以访问的信息。 此外，使用“每应用隐私异常”  对每个应用定义异常。

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

这些设置使用[ 策略 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wirelessdisplay)，该策略还列出了受支持的 Windows 版本。

- **来自无线显示接收方的用户输入**：“阻止”可阻止来自无线显示接收方的用户输入  。 选择“未配置”（默认）可允许无线显示器将键盘、鼠标、笔和触摸输入发送回源设备  。
- **投影到此电脑**：选择“阻止”可阻止其他设备发现用于投影的设备  。 选择“未配置”（默认）使设备可发现，并可投影到锁定屏幕上方的设备  。
- **需要用于配对的 PIN**：选择“需要”在连接投影设备时始终提示输入 PIN  。 选择“未配置”（默认）则无需使用 PIN 将设备与投影设备配对  。

## <a name="reporting-and-telemetry"></a>报告和遥测

- **共享使用情况数据**：选择已提交的诊断数据的级别。 选项包括：
  - **未配置**：不共享任何数据。
  - **安全**：帮助保持 Windows 更安全所需的信息，包括有关“连接的用户体验”和“遥测组件”设置、恶意软件删除工具和 Windows Defender 的数据。
  - **基本**：基本设备信息，包括质量相关数据、应用兼容性、应用使用率数据和安全级别的数据。
  - **增强**：其他见解，包括：如何使用 Windows、Windows Server、System Center 和应用，它们的执行方式，高级可靠性数据以及基本级别和安全级别的数据。
  - **全部**：识别和帮助解决问题所需的所有数据，以及来自安全级别、基本级别和增强级别的数据。

  [System/AllowTelemetry CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry)

- **将 Microsoft Edge 浏览数据发送到 Microsoft 365 Analytics**：若要使用此功能，请将  “共享使用情况数据”设置为  “已增强”或“完整”  。 此功能可控制 Microsoft Edge 向适用于具有已配置商业 ID 的企业设备的 Microsoft 365 Analytics 发送的数据。 选项包括：
  - **未配置**：使用 OS 默认值，这可能不会发送任何浏览历史数据
  - **仅发送 Intranet 数据**：允许管理员发送 Intranet 数据历史记录
  - **仅发送 Internet 数据**：允许管理员发送 Internet 数据历史记录
  - **发送 Intranet 和 Internet 数据**：允许管理员发送 Intranet 和 Internet 数据历史记录

  [Browser/ConfigureTelemetryForMicrosoft365Analytics CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configuretelemetryformicrosoft365analytics)

- **遥测代理服务器**：输入代理服务器的完全限定的域名 (FQDN) 或 IP 地址，以使用安全套接字层 (SSL) 连接转发连接用户体验和遥测请求。 此设置的格式为“服务器  :端口  ”。 如果已命名代理失败，或在启用此策略时没有输入代理，那么连接用户体验和遥测数据不会进行发送，而是仍保留在本地设备上。

  示例格式：

  ```
  IPv4: 192.246.246.106:100
  IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100
  FQDN: www.contoso.com:345
  ```

  [System/TelemetryProxy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-telemetryproxy)

选择“确定”，保存所做更改  。

## <a name="search"></a>搜索

这些设置使用[搜索策略 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search)，该策略还列出了受支持的 Windows 版本。 

- **安全搜索(仅限移动版)** ：控制 Cortana 在搜索结果中筛选成人内容的方式。 选项包括：
  - **用户定义**：允许最终用户选择自己的设置。
  - **严格**：针对成人内容的最高筛选。
  - **中等**：针对成人内容的中等筛选。 不会筛选有效的搜索结果。
- **在搜索中显示 Web 结果**：设置为“阻止”时，用户无法搜索，且搜索中不会显示 Web 结果  。 选择“未配置”（默认）允许用户搜索 Web，并在设备上显示结果  。

## <a name="start"></a>以管理员身份启动

这些设置使用[开始策略 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-start)，该策略还列出了受支持的 Windows 版本。  

- **“开始”菜单布局**：替代默认的“开始”布局并自定义桌面设备上的“开始”菜单。 上传包含自定义项的 XML 文件，包括列出的应用的顺序等。 用户无法更改输入的“开始”菜单布局。
- **在开始菜单中将网站固定到磁贴上**：从 Microsoft Edge 导入图像，这些图像在桌面设备的 Windows 开始菜单中显示为链接。
- **从任务栏取消固定应用**：选择“阻止”可阻止用户从任务栏取消固定应用  。 选择“未配置”（默认）则允许用户从任务栏中取消固定应用  。
- **快速用户切换**：选择“阻止”  可防止在未注销的情况下在同时登录的用户之间切换。 选择“未配置”（默认）可在用户磁贴上显示“切换用户”   。
- **最常用的应用**：选择“阻止”  可隐藏最常用的应用，使其不在开始菜单上显示。 还可通过此设置禁用“设置”应用中的相应切换。 选择“未配置”（默认）可显示最常用的应用  。
- **最近添加的应用**：选择“阻止”  可隐藏最近添加的应用，使其不在开始菜单上显示。 还可通过此设置禁用“设置”应用中的相应切换。 选择“未配置”（默认）可在开始菜单中显示最近添加的应用  。
- **开始屏幕模式**：选择开始屏幕的显示方式。 选项包括：
  - **用户定义**：不强制启动的大小。 用户可以设置大小。
  - **全屏**：强制启动的全屏大小。
  - **非全屏**：强制非全屏启动大小。
- **跳转列表中最近打开的项目**：选择“阻止”  可隐藏最近的跳转列表，使其不在开始菜单和任务栏上显示。 还可通过此设置禁用“设置”应用中的相应切换。 选择“未配置”（默认）可显示跳转列表中最近打开的项  。
- **应用列表**：选择显示所有应用列表的方式。 选项包括：
  - **用户定义**：不强制任何设置。 用户可以选择应用列表在设备上的显示方式。
  - **折叠**：隐藏所有应用列表。
  - **折叠并禁用设置应用**：隐藏所有应用列表，并在设置应用中禁用“在开始菜单中显示应用列表”  。
  - **折叠并禁用设置应用**：隐藏所有应用列表，删除所有应用按钮，并在设置应用中禁用“在开始菜单中显示应用列表”  。
- **电源按钮**：选择“阻止”  可隐藏电源按钮，使其不在开始菜单中显示。 选择“未配置”（默认）则显示电源按钮  。
- **用户磁贴**：选择“阻止”可隐藏用户磁贴，使其不在开始菜单中显示  。 选择“未配置”（默认）可显示用户磁贴，并设置以下设置  ：
  - **锁定**：选择“阻止”可隐藏“锁定”选项，使其不在开始菜单的用户磁贴中显示   。 选择“未配置”（默认）可显示“锁定”选项   。
  - **注销**：选择“阻止”可隐藏“注销”选项，使其不在开始菜单的用户磁贴中显示   。 选择“未配置”（默认）则显示注销按钮   。
- **关机**：选择“阻止”可隐藏“更新并关机”和“关机”选项，使其不在开始菜单的电源按钮中显示    。 选择“未配置”（默认）可会显示这些选项  。
- **休眠**：选择“阻止”可隐藏“休眠”选项，使其不在开始菜单的电源按钮中显示   。 选择“未配置”（默认）可显示该选项  。
- **休眠**：选择“阻止”可隐藏“休眠”选项，使其不在开始菜单的电源按钮中显示   。 选择“未配置”（默认）可显示该选项  。
- **切换帐户**：选择“阻止”可隐藏“切换帐户”，使其不在开始菜单的用户磁贴中显示   。 选择“未配置”（默认）可显示该选项  。
- **重新启动选项**：选择“阻止”可隐藏“更新并重启”和“重启”选项，使其不在开始菜单的电源按钮中显示    。 选择“未配置”（默认）可会显示这些选项  。
- **“开始”上的文档**：隐藏或显示 Windows 开始菜单中的文档文件夹。 选项包括：
  - **未配置**（默认）：没有强制设置。 用户选择显示或隐藏快捷方式。
  - **隐藏**：隐藏快捷方式并在设置应用中禁用设置。
  - **显示**：显示快捷方式并在设置应用中禁用设置。
- **“开始”上的下载**：隐藏或显示 Windows 开始菜单中的下载文件夹。 选项包括：
  - **未配置**（默认）：没有强制设置。 用户选择显示或隐藏快捷方式。
  - **隐藏**：隐藏快捷方式并在设置应用中禁用设置。
  - **显示**：显示快捷方式并在设置应用中禁用设置。
- **“开始”上的文件资源管理器**：隐藏或显示 Windows 开始菜单中的文件资源管理器。 选项包括：
  - **未配置**（默认）：没有强制设置。 用户选择显示或隐藏快捷方式。
  - **隐藏**：隐藏快捷方式并在设置应用中禁用设置。
  - **显示**：显示快捷方式并在设置应用中禁用设置。
- **“开始”上的家庭组**：隐藏或显示 Windows 开始菜单中的家庭组快捷方式。 选项包括：
  - **未配置**（默认）：没有强制设置。 用户选择显示或隐藏快捷方式。
  - **隐藏**：隐藏快捷方式并在设置应用中禁用设置。
  - **显示**：显示快捷方式并在设置应用中禁用设置。
- **“开始”上的音乐**：隐藏或显示 Windows 开始菜单中的音乐文件夹。 选项包括：
  - **未配置**（默认）：没有强制设置。 用户选择显示或隐藏快捷方式。
  - **隐藏**：隐藏快捷方式并在设置应用中禁用设置。
  - **显示**：显示快捷方式并在设置应用中禁用设置。
- **“开始”上的网络**：隐藏或显示 Windows 开始菜单中的网络。 选项包括：
  - **未配置**（默认）：没有强制设置。 用户选择显示或隐藏快捷方式。
  - **隐藏**：隐藏快捷方式并在设置应用中禁用设置。
  - **显示**：显示快捷方式并在设置应用中禁用设置。
- **“开始”上的个人文件夹**：隐藏或显示 Windows 开始菜单中的个人文件夹。 选项包括：
  - **未配置**（默认）：没有强制设置。 用户选择显示或隐藏快捷方式。
  - **隐藏**：隐藏快捷方式并在设置应用中禁用设置。
  - **显示**：显示快捷方式并在设置应用中禁用设置。
- **“开始”上的图片**：隐藏或显示 Windows 开始菜单中的图片文件夹。 选项包括：
  - **未配置**（默认）：没有强制设置。 用户选择显示或隐藏快捷方式。
  - **隐藏**：隐藏快捷方式并在设置应用中禁用设置。
  - **显示**：显示快捷方式并在设置应用中禁用设置。
- **“开始”上的设置**：隐藏或显示 Windows 开始菜单中的设置快捷方式。 选项包括：
  - **未配置**（默认）：没有强制设置。 用户选择显示或隐藏快捷方式。
  - **隐藏**：隐藏快捷方式并在设置应用中禁用设置。
  - **显示**：显示快捷方式并在设置应用中禁用设置。
- **“开始”上的视频**：隐藏或显示 Windows 开始菜单中的视频文件夹。 选项包括：
  - **未配置**（默认）：没有强制设置。 用户选择显示或隐藏快捷方式。
  - **隐藏**：隐藏快捷方式并在设置应用中禁用设置。
  - **显示**：显示快捷方式并在设置应用中禁用设置。

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen

- **Microsoft Edge SmartScreen**：选择“需要”可关闭 Windows Defender SmartScreen，并阻止用户将其打开  。 选择“未配置”（默认）可启动 SmartScreen  。 帮助保护用户免受潜在威胁，防止用户将其关闭。

  Microsoft Edge 使用 Windows Defender SmartScreen（已启用）防止用户受潜在网络钓鱼诈骗和恶意软件侵袭。

  [Browser/AllowSmartScreen CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)

- **恶意网站访问**：选择“阻止”可阻止用户忽略 Windows Defender SmartScreen 筛选器警告，并阻止用户转到网站  。 选择“未配置”（默认）可允许用户忽略警告，继续访问网站  。

  [Browser/PreventSmartScreenPromptOverride CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)

- **未验证的文件下载**：选择“阻止”可阻止用户忽略 Windows Defender SmartScreen 筛选器警告，并阻止用户下载未验证的文件  。 选择“未配置”（默认）可允许用户忽略警告，继续访问下载未经验证的文件  。

  [Browser/PreventSmartScreenPromptOverrideForFiles CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)

## <a name="windows-spotlight"></a>Windows 聚焦

这些设置使用[体验策略 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience)，该策略还列出了受支持的 Windows 版本。

- **Windows 聚焦功能**：选择“阻止”可关闭锁屏界面上的 Windows 聚焦、Windows 提示、Microsoft 使用者功能和其他相关的功能  。 如果目标为最大限度地减少设备的网络流量，请将其设置为“阻止”  。 选择“未配置”（默认）可允许 Windows 聚焦功能，并可能由最终用户控制  。 启用时，还可以允许或阻止以下设置：

  - **锁定屏幕上的 Windows 聚焦**：选择“阻止”可阻止 Windows 聚焦在设备锁定屏幕上显示信息  。 选择“未配置”（默认）可启用此功能  。
  - **Windows 聚焦中的第三方建议**：选择“阻止”可阻止 Windows 聚焦建议不由 Microsoft 发布的内容  。 选择“未配置”（默认）可允许合作伙伴软件发布者在 Windows 屏幕聚焦功能（例如，锁屏界面聚焦、“开始”菜单中的建议应用和 Windows 提示）中提供应用和内容建议  。
  - **使用者功能**：选择“阻止”可禁用通常只面向使用者的体验，例如“入门”建议、成员资格通知、现成体验后应用安装和重定向磁贴  。 “未配置”（默认）允许这些请求  。
  - **Windows 提示**：选择“阻止”可禁用弹出窗口提示  。 选择“未配置”（默认）可允许显示窗口提示  。
  - **操作中心中的 Windows 聚焦**：选择“阻止”可阻止 Windows 聚焦通知在操作中心中显示  。 选择“未配置”（默认）可能会在操作中心显示提示应用或功能的通知，以帮助用户在 Windows 上提高工作效率  。
  - **Windows 聚焦个性化设置**：选择“阻止”可阻止 Windows 使用诊断数据为用户提供自定义体验  。 选择“未配置”（默认）可允许 Microsoft 使用诊断数据提供个性化的建议、提示和套餐，以根据用户的需求定制 Windows  。
  - **Windows 欢迎使用体验**：选择“阻止”可禁用 Windows 聚焦 Windows 欢迎体验功能  。 当 Windows 及其应用有更新和更改时，Windows 欢迎体验使用将不会显示。 选择“未配置”（默认）则允许 Windows 欢迎使用体验显示有关新功能或更新功能的用户信息  。

## <a name="microsoft-defender-antivirus"></a>Microsoft Defender 防病毒

这些设置使用[defender 策略 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender)，该策略还列出了受支持的 Windows 版本。

- **实时监控**：选择“启用”可启用对恶意软件、间谍软件和其他不需要的软件的实时扫描  。 用户不能将其关闭。 

  当设置为 "**未配置**" （默认值）时，Intune 不会接触此设置。 如果启用该设置，然后将其更改回 "**未配置**"，则 Intune 会将设置保留为以前配置的状态。 默认情况下，操作系统会启用此功能，并允许用户对其进行更改。

  Intune 不会关闭此功能。 若要禁用它，请使用自定义 URI。

  [Defender/AllowRealtimeMonitoring CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

- **行为监控**：选择“启用”可启用行为监控，并检查设备上是否存在某些已知模式的可疑活动  。 用户无法关闭行为监视。 

  当设置为 "**未配置**" （默认值）时，Intune 不会接触此设置。 如果启用该设置，然后将其更改回 "**未配置**"，则 Intune 会将设置保留为以前配置的状态。 默认情况下，操作系统会启用行为监视，并允许用户对其进行更改。

  Intune 不会关闭此功能。 若要禁用它，请使用自定义 URI。

  [Defender/AllowBehaviorMonitoring CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring)

- **网络检查系统 (NIS)** ：NIS 可帮助保护设备免遭基于网络的攻击。 它使用 Microsoft Endpoint Protection 中心中的已知漏洞签名来帮助检测和阻止恶意流量。

  **启用启用**网络保护和网络阻止。 用户不能将其关闭。 启用后，阻止用户连接到已知的漏洞。

  当设置为 "**未配置**" （默认值）时，Intune 不会接触此设置。 如果启用该设置，然后将其更改回 "**未配置**"，则 Intune 会将设置保留为以前配置的状态。 默认情况下，操作系统会启用 NIS，并允许用户对其进行更改。

  Intune 不会关闭此功能。 若要禁用它，请使用自定义 URI。

  [Defender/EnableNetworkProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection)

- **扫描所有下载**：**启用启用**此设置，而 Defender 扫描从 Internet 下载的所有文件。 用户无法关闭此设置。 

  当设置为 "**未配置**" （默认值）时，Intune 不会接触此设置。 如果启用该设置，然后将其更改回 "**未配置**"，则 Intune 会将设置保留为以前配置的状态。 默认情况下，操作系统会启用此设置，并允许用户对其进行更改。

  Intune 不会关闭此功能。 若要禁用它，请使用自定义 URI。

  [Defender/AllowIOAVProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection)

- **扫描 Microsoft Web 浏览器中加载的脚本**：选择“启用”  可允许 Defender 扫描在 Internet Explorer 中使用的脚本。 用户无法关闭此设置。 

  当设置为 "**未配置**" （默认值）时，Intune 不会接触此设置。 如果启用该设置，然后将其更改回 "**未配置**"，则 Intune 会将设置保留为以前配置的状态。 默认情况下，操作系统会启用此设置，并允许用户对其进行更改。

  Intune 不会关闭此功能。 若要禁用它，请使用自定义 URI。

  [Defender/AllowScriptScanning CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning)

- **Defender 的最终用户访问权限**：选择“阻止”可对最终用户隐藏 Microsoft Defender 用户界面  。 所有 Microsoft Defender 通知也被禁止。

  当设置为 "**未配置**" （默认值）时，Intune 不会接触此设置。 如果阻止设置，然后将其更改回 "**未配置**"，则 Intune 会将设置保留为以前配置的状态。 默认情况下，操作系统允许用户访问 Microsoft Defender UI，并允许用户对其进行更改。

  Intune 不会关闭此功能。 若要禁用它，请使用自定义 URI。

  此设置更改后，在最终用户的电脑下次重启时生效。

  [Defender/AllowUserUIAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowuseruiaccess)

- **安全智能更新间隔（小时）** ：输入从0-24 开始检查新安全智能的时间间隔（以小时为单位）。 选项包括：

  - **未配置**（默认）：每8小时检查一次更新。
  - 不**检查**： Defender 不检查是否有新的安全智能更新。
  - **1 到 24**：`1` 表示每小时检查一次，`2` 表示每两小时检查一次，`24` 表示每天检查一次，依此类推。
  
  [Defender/SignatureUpdateInterval CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval)
  
- **监视文件和程序活动**：允许 Defender 监视设备上的文件和程序活动。 选项包括：

  - **未配置**（默认）：监视所有文件
  - **已禁用监视**
  - **监视所有文件**
  - **仅监视传入的文件**
  - **仅监视传出的文件**

  [Defender/RealTimeScanDirection CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection)

- **删除已隔离恶意软件之前的天数**：按输入的天数继续跟踪已解决的恶意软件，以便可以手动检查之前受影响的设备。 如果你将天数设置为 `0`，则恶意软件将保留在隔离文件夹中，并且不会自动删除。 设置为 `90` 时，隔离项目将在系统上存储 90 天，然后删除。

  [Defender/DaysToRetainCleanedMalware CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware)

- **在扫描期间限制 CPU 使用率**：限制允许扫描使用的 CPU 量（从 `0` 到 `100`）。
- **扫描存档文件**：**启用启用**Defender，使其扫描存档文件（如 Zip 或 Cab 文件）。 用户无法关闭此设置。

  当设置为 "**未配置**" （默认值）时，Intune 不会接触此设置。 如果启用该设置，然后将其更改回 "**未配置**"，则 Intune 会将设置保留为以前配置的状态。 默认情况下，操作系统会启用此扫描，并允许用户对其进行更改。

  Intune 不会关闭此功能。 若要禁用它，请使用自定义 URI。

  [Defender/AllowArchiveScanning CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning)

- **扫描传入的电子邮件**：选择“启用”可允许 Defender 在电子邮件到达设备时扫描它们  。 启用后，引擎会分析邮箱和邮件文件，以分析邮件正文和附件。 可以扫描 .pst （Outlook）、.dbx、. mbx、MIME （Outlook Express）和 BinHex （Mac）格式。

  当设置为 "**未配置**" （默认值）时，Intune 不会接触此设置。 如果启用该设置，然后将其更改回 "**未配置**"，则 Intune 会将设置保留为以前配置的状态。 默认情况下，操作系统会关闭此扫描，并允许用户对其进行更改。

  Intune 不会关闭此功能。 若要禁用它，请使用自定义 URI。

  [Defender/AllowEmailScanning CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning)

- **完全扫描期间扫描可移动驱动器**：在完全扫描期间**启用**Defender 可移动驱动器扫描。 用户无法关闭此设置。

  当设置为 "**未配置**" （默认值）时，Intune 不会接触此设置。 如果启用该设置，然后将其更改回 "**未配置**"，则 Intune 会将设置保留为以前配置的状态。 默认情况下，操作系统允许 Defender 扫描可移动驱动器（如 USB 棒），并允许用户更改此设置。

  在快速扫描过程中，可能仍会扫描可移动驱动器。

  Intune 不会关闭此功能。 若要禁用它，请使用自定义 URI。

  [Defender/AllowFullScanRemovableDriveScanning CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning)

- **完全扫描期间扫描映射的网络驱动器**：选择“启用”  可允许 Defender 扫描映射网络驱动器上的文件。 如果驱动器上的文件是只读的，则 Defender 无法删除在其中找到的任何恶意软件。 用户无法关闭此设置。

  当设置为 "**未配置**" （默认值）时，Intune 不会接触此设置。 如果启用该设置，然后将其更改回 "**未配置**"，则 Intune 会将设置保留为以前配置的状态。 默认情况下，操作系统会启用此功能，并允许用户对其进行更改。

  在快速扫描过程中，可能仍会扫描映射的网络驱动器。

  Intune 不会关闭此功能。 若要禁用它，请使用自定义 URI。

  [Defender/AllowFullScanOnMappedNetworkDrives CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanonmappednetworkdrives)

- **扫描从网络文件夹打开的文件**： **Enable 允许**Defender 扫描从网络文件夹或共享的网络驱动器打开的文件，例如从 UNC 路径访问的文件。 用户无法关闭此设置。 如果驱动器上的文件是只读的，则 Defender 无法删除在其中找到的任何恶意软件。

  当设置为 "**未配置**" （默认值）时，Intune 不会接触此设置。 如果启用该设置，然后将其更改回 "**未配置**"，则 Intune 会将设置保留为以前配置的状态。 默认情况下，操作系统会扫描从网络文件夹打开的文件，并允许用户对其进行更改。

  Intune 不会关闭此功能。 若要禁用它，请使用自定义 URI。

  [Defender/AllowScanningNetworkFiles CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles)

- **云保护**：选择“启用”可启用 Microsoft Active Protection Service 以接收来自你管理的设备的恶意软件活动的相关信息  。 用户无法更改此设置。 

  当设置为 "**未配置**" （默认值）时，Intune 不会接触此设置。 如果启用该设置，然后将其更改回 "**未配置**"，则 Intune 会将设置保留为以前配置的状态。 默认情况下，操作系统允许 Microsoft Active Protection Service 接收信息，并允许用户更改此设置。

  Intune 不会关闭此功能。 若要禁用它，请使用自定义 URI。

  [Defender/AllowCloudProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection)

- **在示例提交前提示用户**：控制是否自动向 Microsoft 发送可能需要进一步分析的潜在恶意文件。 选项包括：

  - **未配置**（默认）：自动发送安全示例。
  - **始终提示**
  - **发送个人数据之前进行提示**
  - **从不发送数据**
  - **发送所有数据而不提示**：自动发送数据。

  [Defender/SubmitSamplesConsent CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent)

- **每天执行快速扫描的时间**：选择要运行每天快速扫描的时间。 “未配置”（默认）不运行每天扫描  。 如果需要更多自定义，请配置“要执行的系统扫描类型”设置  。

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

  > [!TIP]
  > 此设置可能与“要执行每日快速扫描的时间”设置相冲突  。 一些建议：  
  >
  > - 如果要计划每日一次的快速扫描和每周完全扫描，请执行以下操作：
  >   1. 配置**执行每日快速扫描**设置的时间。
  >   2. 配置执行完全扫描**要执行的系统扫描类型**。
  > 
  > - 如果你只想每天进行一次快速扫描（无完全扫描），请使用以下设置： **Time 执行每日快速扫描**或**执行的系统扫描类型**。 例如，若要在每周二上午 6 点运行快速扫描，请配置“要执行的系统扫描类型”设置  。
  > 
  > - 请勿在“要执行的系统扫描类型”设置为“快速扫描”的同时配置“要执行每日快速扫描的时间”设置    。 这些设置可能会发生冲突，扫描可能无法运行。

  [Defender/ScanParameter CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter)  
  [Defender/ScheduleScanDay CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday)  
  [Defender/ScheduleScanTime CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime)

- **检测可能不需要的应用程序**：在 Windows 检测到可能不需要的应用程序时选择保护级别。 选项包括：
  - **未配置**（默认）：禁用 Windows Defender 可能不需要的应用程序保护。
  - **阻止**：Windows Defender 检测可能不需要的应用程序，并阻止检测到的项目。 这些项目与其他威胁一起显示在历史记录中。
  - **审核**：Windows Defender 检测可能不需要的应用程序，但不执行任何操作。 可以查看有关 Windows Defender 将对其采取行动的应用程序的信息。 例如，在事件查看器中搜索 Windows Defender 创建的事件。

  有关可能不需要的应用程序的详细信息，请参阅[检测和阻止可能不需要的应用程序](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus)。

  [Defender/PUAProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection)

- **针对检测到的恶意软件威胁的操作**：选择要如何处理恶意软件线程。 **未配置**（默认值）允许 Microsoft Defender 选择最佳选项。 设置为“启用”  后，可选择 Defender 针对其探测到的每个威胁级别（低、中、高和严重）要执行的操作。 选项包括：
  
  - **清理**
  - **隔离**
  - **移除**
  - **允许**
  - **用户定义**
  - **阻止**

  如果你的操作不可行，Windows Defender 将选择最佳选项以确保修正威胁。 

  [Defender/ThreatSeverityDefaultAction CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-threatseveritydefaultaction)

### <a name="windows-defender-antivirus-exclusions"></a>Windows Defender 防病毒排除项

- **要从扫描和实时保护排除的文件和文件夹**：向排除列表添加一个或多个文件和文件夹（如 C:\Path  或 %ProgramFiles%\Path\filename.exe  ）。 不会在任何实时或计划的扫描中包括这些文件和文件夹。
- **要从扫描和实时保护排除的文件扩展名**：向排除列表添加一个或多个文件扩展名（如 jpg  或 txt  ）。 不会在任何实时或计划的扫描中包括具有这些扩展名的任何文件。
- **要从扫描和实时保护排除的进程**：向排除列表添加一个或多个类型为 .exe  、.com  或 .scr  的进程。 这些进程不会包括在任何实时或计划的扫描中。

## <a name="next-steps"></a>后续步骤

有关每个设置以及支持的 Windows 版本的其他技术详细信息，请参阅 [Windows 10 策略 CSP 参考](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider)
