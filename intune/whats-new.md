---
title: Microsoft Intune 中的新增功能 - Azure | Microsoft Docs
titlesuffix: ''
description: 了解 Intune Azure 门户新增功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/04/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
/ms.custom: intune-azure
ms.openlocfilehash: f1f6cac720e753e78bbabe091ce1c68cc58b7917
ms.sourcegitcommit: 21b08737c3366b81b0f3b981b29008563f63f036
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34758144"
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune 新增功能
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

了解 Microsoft Intune 每周新增功能。 另外，你还可以找到[即将发生的更改](#whats-coming)、有关服务的[重要说明](#notices)，以及有关[过去版本](whats-new-archive.md)的信息。 某些功能可能会在数周内推出，第一周内可能不能供所有客户使用。

> [!Note]
> 有关混合移动设备管理 (MDM) 中新功能的信息，请参阅[混合新增功能页面](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。


<!-- Common categories:  
### App management
### Device enrollment
### Device management
### Device configuration
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->   

## <a name="week-of-june-4-2018"></a>2018 年 6 月 4 日的这一周

### <a name="app-management"></a>应用管理

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>在展台模式下检索适用于企业的 Microsoft Store 应用相关联的应用用户模型 ID (AUMID) <!-- 1560077 ! -->
Intune 现在可以检索适用于企业的 Microsoft Store (WSfB) 应用的应用用户模型 ID，以改进展台配置文件的配置。

有关适用于企业的 Microsoft Store 应用的详细信息，请参阅[管理来自适用于企业的 Microsoft Store 应用](windows-store-for-business.md)。

#### <a name="new-company-portal-branding-page----1916370---"></a>新的公司门户品牌页 <!-- 1916370 -->
公司门户品牌页拥有新的布局、消息和工具提示。


### <a name="device-configuration"></a>设备配置

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680-eeready----"></a>支持 Palo Alto Networks GlobalProtect VPN 配置文件<!-- 1333680 eeready ! -->
通过此更新，可选择 Palo Alto Networks GlobalProtect 作为 Intune 中 VPN 配置文件的 VPN 连接类型（“设备配置” > “配置文件” > “创建配置文件” > “配置文件类型” > “VPN”）。 在此版本中，支持以下平台： 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings----1403702---"></a>新增本地设备安全选项设置<!-- 1403702 -->
现在可以配置适用于 Windows 10 设备的其他本地设备安全选项设置。 其他设置在 Microsoft 网络客户端、Microsoft 网络服务器、网络访问和安全性和交互式登录的区域内可用。 创建 Windows 10 设备配置策略时，可以在终结点保护类别中查找这些设置。

#### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>在 Windows 10 设备上启用展台模式 <!-- 1560072 ! -->
在 Windows 10 设备上，可以创建配置文件并启用展台模式（“设备配置” > “配置文件” > “创建配置文件” > “Windows 10” > “设备限制” > “展台”）。 在此更新中，“展台(预览版)”设置被重命名为“展台(旧版)”。 不再推荐使用“展台(旧版)”，但该版本在 7 月更新之前仍能正常使用。 “展台(旧版)”被替换为新的“展台”配置文件类型（“创建配置文件” > “Windows 10” > “展台(预览版)”），该类型将包含配置 Windows 10 RS4 和更高版本上的展台的设置。

适用于 Windows 10 和更高版本。

#### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>设备配置文件图形用户图表已恢复 <!-- 2160133 -->
为了改进设备配置文件图形图表上显示的计数（“设备配置” > “配置文件”> 选择现有配置文件 >“概述”），图形用户图表曾被暂时删除。

在此更新中，图形用户图表得到恢复，并显示在 Azure 门户中。

### <a name="device-enrollment"></a>设备注册

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication----1165118-wnready---"></a>支持无需用户身份验证的 Windows Autopilot 注册 <!-- 1165118 wnready -->
Intune 现在支持无需用户身份验证的 Windows Autopilot 注册。 这是 Windows Autopilot 部署配置文件中的新选项，“Autopilot 部署模式”设置为“自部署”。  该设备必须运行 Windows 10 版本 1803 或更高版本，并且拥有 TPM 2.0 才能授权此类注册。 由于不需要用户身份验证，因此应仅将此选项分配给你具有物理控制权限的设备。

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766-eeready---"></a>配置 Autopilot 的 OOBE 时的新语言/区域设置 <!-- 1821766 eeready -->
在 Out of Box Experience 期间，会提供新的配置设置，以设置 Autopilot 配置文件的语言和区域。 要查看新设置，请选择“设备注册” > “Windows 注册” > “部署配置文件” > “创建配置文件” > “部署模式” = “自部署” > “默认配置”。

#### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>配置设备键盘的新设置 <!-- 1821768 -->
在 Out of Box Experience 期间，将提供新的设置，以配置 Autopilot 配置文件的键盘。 要查看新设置，请选择“设备注册” > “Windows 注册” > “部署配置文件” > “创建配置文件” > “部署模式” = “自部署” > “默认配置”。

#### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>将 AutoPilot 配置文件移动到组目标<!-- 1877935 -->
AutoPilot 部署配置文件可以分配给包含 AutoPilot 设备的 Azure AD 组。

### <a name="device-management"></a>设备管理

#### <a name="set-compliance-by-device-location----851881----"></a>按设备位置设置符合性 <!-- 851881 ! -->
在某些情况下，你可能想要将访问企业资源的权限限制到某个特定位置（该位置由网络连接定义）。 现在可以基于设备的 IP 地址来创建符合性策略（“设备符合性” > “位置”）。 如果设备移动到 IP 范围以外，则该设备将无法访问企业资源。

适用于：拥有更新的公司门户应用的 Android 设备 6.0 及更高版本

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>在 Windows 10 企业版 RS4 AutoPilot 设备上阻止使用者应用和体验<!-- 1621980 -->
你将能够阻止在 Windows 10 企业版 RS4 AutoPilot 设备上安装使用者应用和体验。 要查看此功能，请转到“Intune” > “设备配置” > “配置文件” > “创建配置文件” > “平台” = “Windows 10 或更高版本” > “配置文件类型” = “设备限制” > “配置” > “Windows 聚焦” > “使用者功能”。 

#### <a name="uninstall-the-latest-from-windows-10-software-updates----1732948-eeready---"></a>从 Windows 10 软件更新中卸载最新版本 <!-- 1732948 eeready -->
如果发现 Windows 10 计算机上存在重大问题，则可以选择卸载（回滚）最新的功能更新或最新的质量更新。 卸载某功能或质量更新仅适用于设备所在的服务通道。 卸载将触发恢复 Windows 10 计算机上的先前更新的策略。 特别是对于功能更新，可以限制卸载最新版本的时间（2-60 天）。 要设置软件更新卸载选项，请从 Azure 门户中的“Microsoft Intune ”边栏选项卡中选择“软件更新”。 然后，从“软件更新”边栏选项卡中选择“Windows 10 更新通道”。 然后，可以从“概述”部分选择“卸载”选项。

#### <a name="search-all-devices-for-imei-and-serial-number----1793685---"></a>搜索所有设备以获取 IMEI 和序列号 <!-- 1793685 -->
现在可以在“所有设备”边栏选项卡上搜索 IMEI 和序列号（电子邮件、UPN、设备名称和管理名称仍然可用）。 在 Intune 中，选择“设备” > “所有设备”> 在搜索框中输入你的搜索。

#### <a name="management-name-field-will-be-editable----1875989---"></a>管理名称字段将可编辑 <!-- 1875989 -->
现在可以在设备的“属性”边栏选项卡上编辑管理名称字段。 若要编辑此字段，请选择“设备” > “所有设备”> 选择设备 >“属性”。 可以使用管理名称字段来唯一标识设备。

#### <a name="new-all-devices-filter-device-category----1878520---"></a>新建所有设备筛选器：设备类别 <!-- 1878520 -->
现在可以按设备类别筛选“所有设备”列表。 为此，请选择“设备” > “所有设备” > “筛选器” > “设备类别”。

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>使用 TeamViewer 共享 iOS 和 MacOS 设备的屏幕 <!-- 1985547 -->
管理员现在可以连接到 [TeamViewer](device-profile-android-teamviewer.md)，并启动与 iOS 和 macOS 设备之间的屏幕共享会话。 iPhone、iPad 和 macOS 用户可以与任何其他桌面或移动设备实时共享其屏幕。 

#### <a name="multiple-exchange-connector-support----2070451---"></a>多个 Exchange Connector 支持<!-- 2070451 -->
你不再受到每租户一个 Microsoft Intune Exchange Connector 的限制。 Intune 现在支持多个 Exchange Connector，你可以设置多个本地 Exchange 组织的 Intune 条件访问。

凭借 Intune 本地 Exchange 连接器，可以根据设备是否已在 Intune 中注册且是否符合 Intune 设备符合性策略来管理设备对本地 Exchange 邮箱的访问。 若要设置连接器，请从 Azure 门户下载 Intune 本地 Exchange 连接器，并将它安装在 Exchange 组织中的服务器上。 在 Microsoft Intune 仪表板上，选择“本地访问”，然后在“设置”下选择“Exchange ActiveSync 连接器”。 下载 Exchange 本地连接器，并将它安装在 Exchange 组织中的服务器上。 由于你已经不再受到每租户一个 Exchange 连接器的限制，因此，如果拥有其他的 Exchange 组织，则可以按照此相同的过程为其他每个 Exchange 组织下载并安装连接器。

#### <a name="new-device-hardware-detail-ccid----2156657---"></a>新的设备硬件详细信息：CCID <!-- 2156657 -->
现在每台设备均包含芯片卡接口设备 (CCID) 信息。 要查看该信息，请选择“设备” > “所有设备”> 选择一台设备 >“硬件”> 在“网络详情”下查看>

#### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>将所有用户和所有设备分配为范围组 <!-- 2196803 -->
现在可以分配所有用户、所有设备，以及范围组中的所有用户和所有设备。 要执行此操作，请选择“Intune 角色” > “所有角色” > “策略和配置文件管理器” > “分配”> 选择一项分配 >“范围(组)”。

#### <a name="udid-information-now-included-for-ios-and-macos-devices----2219806-wnready--"></a>现包括 iOS 和 macOS 设备的 UDID 信息 <!-- 2219806 wnready-->
要查看适用于 iOS 和 macOS 设备的唯一设备标识符 (UDID)，请转到“设备” > “所有设备”> 选择一台设备 >“硬件”。 UDID 仅适用于公司设备（如“设备” > “所有设备”> 选择一台设备 >“属性” > “设备所有权”下的设置）。

### <a name="intune-apps"></a>Intune 应用

#### <a name="improved-troubleshooting-for-app-installation----928990---"></a>改进了对应用安装的故障排除 <!-- 928990 -->
在 Microsoft Intune MDM 托管的设备上，有时应用安装可能会失败。 当这些应用安装失败时，可能难以了解失败原因或解决此问题。 我们将发布我们的应用疑难解答功能的公共预览版。 你将在每个设备下注意到名为“托管应用”的新节点。 该节点列出了通过 Intune MDM 提供的应用。 在该节点内，将看到应用安装状态的列表。 如果选择单个应用，将看到该特定应用的疑难解答视图。 在疑难解答视图中，将看到应用的端到端生命周期，例如，应用创建、修改、设为目标和提供给设备的时间。 此外，如果应用安装失败，将向你显示错误代码以及有有助于了解错误原因的消息。 

#### <a name="intune-app-protection-policies-and-microsoft-edge----1818968---"></a>Intune 应用保护策略和 Microsoft Edge <!-- 1818968 -->
移动设备（iOS 和 Android）的 Microsoft Edge 浏览器现在支持 Microsoft Intune 应用保护策略。 在 Edge 应用程序中使用其企业 Azure AD 帐户登录的 iOS 和 Android 设备用户将受 Intune 保护。 在 iOS 设备上，“Web 内容需要托管的浏览器”策略允许用户在管理 Edge 时打开其中的链接。

## <a name="week-of-may-14-2018"></a>2018 年 5 月 14 日当周

### <a name="app-management"></a>应用管理

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>需要安装策略、应用、证书和网络配置文件<!-- 1553555 -->

除非 Intune 在 AutoPilot 设备预配期间安装策略、应用、证书和网络配置文件，否则管理员将能够阻止最终用户访问 Windows 10 RS4 桌面。 有关详细信息，请参阅[设置注册状态页](windows-enrollment-status.md)。

#### <a name="configuring-your-app-protection-policies----2144597-part-2---"></a>配置应用保护策略<!-- 2144597 Part 2 -->

在 Azure 门户中，现在只需转到 Intune，而不是转到 Intune 应用保护服务边栏选项卡。 Intune 中现在只有一个应用保护策略位置。 请注意，所有应用保护策略都位于 Intune 中“移动应用”边栏选项卡上的“应用保护策略”下。 此集成将有助于简化云管理。 请记住，Intune 中已具备所有应用保护策略，并且你可以修改先前配置的任何策略。 Intune 应用策略保护 (APP) 和条件访问 (CA) 策略现在位于“Microsoft Intune”边栏选项卡中“管理”部分的“条件访问”下，或“Azure Active Directory”边栏选项卡中“安全性”部分的“条件访问”下。 有关修改条件访问策略的详细信息，请参阅 [Azure Active Directory 中的条件性访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)。 有关其他信息，请参阅[什么是应用保护策略？](app-protection-policy.md)

## <a name="week-of-may-7-2018"></a>2018 年 5 月 7 日的这一周

### <a name="app-management"></a>应用管理

#### <a name="samsung-knox-mobile-enrollment-support---1112863--"></a>Samsung Knox 移动注册支持 <!--1112863-->

将 Intune 与 Samsung Knox 移动注册 (KME) 结合使用时，可以注册大量公司拥有的 Android 设备。 使用 WiFi 或移动电话网络的用户在第一次打开他们的设备时，只需几次点击即可进行注册。 在使用 Knox 部署应用时，可使用蓝牙或 NFC 注册设备。 有关详细信息，请参阅[使用 Samsung 的 Knox 移动注册自动注册 Android 设备](android-samsung-knox-mobile-enroll.md)。

#### <a name="requesting-help-in-the-company-portal-for-windows-10----1874137---"></a>在 Windows 10 公司门户上请求帮助<!-- 1874137 -->

当用户启动获取问题的帮助的工作流时，Windows 10 公司门户现在将直接向 Microsoft 发送应用日志。 这样一来，可以更为轻松地排除和解决向 Microsoft 提出的问题。

## <a name="week-of-april-23-2018"></a>2018 年 4 月 23 日当周

### <a name="app-management"></a>应用管理

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Android 上对 MAM PIN 的密码支持<!-- 1438086 -->

Intune 管理员能够设置应用程序启动要求以强制使用密码而不是数字 MAM PIN。 如果进行此配置，在访问启用 MAM 的应用程序前，用户需要在出现提示时设置并使用密码。 密码是至少包含一个特殊字符或大写/小写字母的数字 PIN。 Intune 对密码的支持与支持现有数字 PIN 类似，可通过管理员控制台设置最短长度并且允许重复字符和序列。 此功能需要最新版 Android 公司门户。 此功能已可应用于 iOS。

#### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>对 macOS 的业务线 (LOB) 应用支持 <!-- 1473977 -->
Microsoft Intune 将提供从 Azure 门户安装 macOS LOB 应用的功能。 使用 GitHub 中提供的工具对 macOS LOB 应用进行预处理后，可以将该应用添加到 Intune。 在 Azure 门户的“Intune”边栏选项卡中，选择“移动应用”。 在“移动应用”边栏选项卡，选择“应用” > “添加”。 在“添加应用”边栏选项卡，选择“业务线应用”。 

#### <a name="built-in-all-users-and-all-devices-group-for-android-for-work-afw-app-assignment----1813073---"></a>面向 Android for Work (AFW) 应用分配的内置“所有用户”和“所有设备”组<!-- 1813073 -->
你可以利用面向 AFW 应用分配的内置“所有用户”和“所有设备”。 有关详细信息，请参阅[在 Microsoft Intune 中包括和排除应用分配](apps-inc-exl-assignments.md)。

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>Intune 将重新安装用户卸载的所需应用 <!-- 1947010 -->
如果最终用户卸载所需应用，Intune 将在 24 小时内自动重新安装该应用，而不是等待 7 天的重新评估周期。

### <a name="device-configuration"></a>设备配置

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153-eeready---"></a>设备配置文件图表和状态列表将显示组中的所有设备<!-- 1449153 eeready -->
配置设备配置文件（“设备配置” > “配置文件”）时，选择设备配置文件，如 iOS。 将此配置文件分配到包括 iOS 设备和非 iOS 设备的组。 图形图表显示应用到 iOS 和非 iOS 设备的配置文件计数（“设备配置” > “配置文件”> 选择一个现有配置文件 >“概述”）。 选择“概述”选项卡中的图形图表时，“设备状态”将列出组中的所有设备，而不仅仅是 iOS 设备。 

此次更新后，图形图表（“设备配置” > “配置文件”>选择一个现有配置文件>“概述”）将仅显示特定设备配置文件的计数。 例如，如果配置设备配置文件应用于 iOS 设备，则图表仅列出 iOS 设备的计数。 选中图形图表并打开“设备状态”后，将仅列出 iOS 设备。

当此更新正在进行时，用户图形图表将暂时删除。 

#### <a name="always-on-vpn-for-windows-10---1333666---"></a>适用于 Windows 10 的 Always On VPN<!--1333666 -->

目前，通过使用自定义虚拟专用网络 (VPN) 配置文件（使用 OMA-URI 创建），可在 Windows 10 设备上使用 [Always On](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on)。

此次更新后，管理员可以在 Azure 门户中的 Intune 中直接面向 Windows 10 VPN 配置文件启用 Always On。 Always On VPN 配置文件将在以下情况下自动连接：

- 用户登录其设备
- 设备上的网络发生更改
- 设备屏幕在关闭后重新打开

#### <a name="new-printer-settings-for-education-profiles----1308900---"></a>教育配置文件的新打印机设置 <!-- 1308900 -->

对于教育配置文件，新的设置在“打印机”类别下可用：“打印机”、“默认打印机”、“添加新的打印机”。

#### <a name="show-caller-id-in-personal-profile---android-for-work---1098984---"></a>在个人资料中显示呼叫方 ID - Android for Work <!--1098984 -->
在设备上使用个人资料时，最终用户可能不会看到工作联系人的呼叫方 ID 详细信息。 

进行此更新后，“Android for Work” > “设备限制” > “Work 配置文件设置”中将出现新设置：
- 在个人资料中显示工作联系人呼叫方 ID

启用（不配置）后，工作联系人的呼叫方详细信息将显示在个人资料中。 阻止后，工作联系人的呼叫方号码不会显示在个人资料中。 

适用范围：Android OS v6.0 和更高版本的 Android 工作配置文件设备

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>添加到 Endpoint Protection 设置的新 Windows Defender Credential Guard 设置<!--1102252 --><!--from 1802 and 1804-->

此次更新后，[Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard)（“设备配置” > “配置文件” > “Endpoint Protection”）将包括以下设置： 

- Windows Defender Credential Guard：以基于虚拟化的安全性启用 Credential Guard。 启用此功能可帮助在下次同时启用“使用安全启动的平台安全级别”和“基于虚拟化的安全性”而重新启动时保护凭据。 选项包括：
  - 禁用：如果之前已使用“无锁启用”选项启用 Credential Guard，则会远程关闭 Credential Guard。

  - 使用 UEFI 锁启用：可确保 Credential Guard 不能使用注册表项或使用组策略禁用。 若要使用此设置来禁用 Credential Guard，必须将组策略设置为“禁用”。 然后，与实际存在的用户一起，从每台计算机中删除安全功能。 这些步骤清除保留在 UEFI 中的配置。 只要 UEFI 配置仍然存在，Credential Guard 就会保持启用状态。

  - 无锁启用：允许使用组策略远程禁用 Credential Guard。 使用此设置的设备必须至少在 Windows 10（版本 1511）上运行。

配置 Credential Guard 时，会自动启用以下相关技术： 

  - 启用基于虚拟化的安全性 (VBS)：在下次重新启动时启用基于虚拟化的安全性 (VBS)。 基于虚拟化的安全性使用 Windows 虚拟机监控程序提供对安全服务的支持，并要求“安全启动”。
  - 安全启动和直接内存访问 (DMA)：通过“安全启动”和直接内存访问启用 VBS。 DMA 保护需要硬件支持，并且仅在正确配置的设备上启用。 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>对 SCEP 证书使用自定义使用者名称<!-- 2064190 -->
可以使用“OnPremisesSamAccountName”作为 SCEP 证书配置文件中自定义使用者的公用名称。 例如，你可以使用 `CN={OnPremisesSamAccountName})`。

####  <a name="block-camera-and-screen-captures-on-android-for-work----1098977-eeready--"></a>在 Android for Work 上阻止照相机和屏幕捕获<!-- 1098977 eeready-->
配置 Android 设备的设备限制时，可以阻止两个新属性： 
- 照相机：阻止访问设备上的所有照相机
- 屏幕捕获：阻止屏幕捕获，还会阻止在不具有安全视频输出的显示设备上显示内容

适用于 Android for Work。


### <a name="device-enrollment"></a>设备注册

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>用户在使用 macOS High Sierra 10.13.2+ 的设备上的新注册步骤<!--1734567 -->
macOS High Sierra 10.13.2 引入了“用户批准的”MDM 注册的概念。 批准的注册将允许 Intune 管理某些安全敏感设置。 有关详细信息，请参阅此处的 Apple 支持文档：https://support.apple.com/HT208019。

如果最终用户未打开“系统首选项”并手动批准，使用 macOS 公司门户注册的设备将被视为“未经用户批准”。 为此，macOS 公司门户现直接在注册过程末尾指示使用 macOS 10.13.2 及以上版本的用户手动批准注册。 Intune 管理员控制台将就注册设备的用户批准情况进行报告。



### <a name="device-management"></a>设备管理

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----eeready-1629303---"></a>高级威胁防护 (ATP) 和 Intune 完全集成 <!-- EEready 1629303 -->

[高级威胁防护 (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) 显示 Windows 10 设备的风险级别。 在 Windows Defender 安全中心（ATP 门户）中，可以创建到 Microsoft Intune 的连接。 创建后，将使用 Intune 符合性策略确定可接受的威胁级别。 如果超出威胁级别，则 Azure Active Directory (AD) 条件访问策略可以阻止访问组织内的不同应用。

此功能使 ATP 能够扫描文件、检测威胁并报告 Windows 10 设备上的任何风险。

请参阅[在 Intune 中启用具有条件访问的 ATP](advanced-threat-protection.md)。

#### <a name="support-for-user-less-devices----1637553---"></a>对无用户设备的支持<!-- 1637553 -->
Intune 支持在无用户设备（如 Microsoft Surface Hub）上评估符合性的功能。 符合性策略可以面向特定设备。 这样可以确定不具有关联用户的设备的符合性（和不符合性）。

#### <a name="delete-autopilot-devices----1713650---"></a>删除 AutoPilot 设备<!-- 1713650 -->
Intune 管理员可以[删除 AutoPilot 设备](enrollment-autopilot.md#delete-autopilot-devices)。

#### <a name="improved-device-deletion-experience---1832333---"></a>设备删除体验改进<!--1832333 -->
[删除 Intune 中的设备](devices-wipe.md#delete-devices-from-the-intune-portal)前，将不再需要删除公司数据或将设备恢复出厂设置。

要感受新体验，请登录 Intune，选择“设备” > “所有设备”> 设备的名称 >“删除”。

如果仍希望确认擦除/停用，可使用标准设备生命周期流程，即在“删除”前执行“删除公司数据”和“恢复出厂设置”。 

#### <a name="play-sounds-on-ios-when-in-lost-mode----1947769---"></a>“丢失”模式下在 iOS 上播放声音<!-- 1947769 -->
当受监督的 iOS 设备处于移动设备管理 (MDM)[丢失模式](device-lost-mode.md)时，可以[播放声音](device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device)（“设备” > “所有设备”>选择一个 iOS 设备 >“概述” > “更多”）。 声音将持续播放，直到将该设备移除“丢失”模式或用户在该设备上禁用声音。 适用于 iOS 9.3 和更高版本的设备。

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device---1972804--"></a>阻止或允许在 Intune 设备上所执行的搜索中出现 Web 结果 <!--1972804-->

管理员现在可以阻止在设备上所执行的搜索中出现 Web 结果。

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>针对 Apple MDM Push Certificate 上传失败的错误消息改进<!-- 2172331 -->

错误消息说明，续订现有 MDM 证书时必须使用相同 Apple ID。

#### <a name="test-the-company-portal-for-macos-on-virtual-machines----2216679---"></a>测试虚拟机上的 macOS 公司门户 <!-- 2216679 -->

我们已发布指南来帮助 IT 管理员在 Parallels Desktop 和 VMware Fusion 的虚拟机上测试 macOS 公司门户应用。 有关详细信息，请参阅[注册用于测试的虚拟 macOS 计算机](macos-enroll.md#enroll-virtual-macos-machines-for-testing)。


### <a name="user-interface"></a>用户界面

#### <a name="improved-device-tiles-in-the-windows-10-company-portal---2213364---"></a>改进了 Windows 10 公司门户中的设备磁贴 <!--2213364 -->

已对这些磁贴进行了更新，以便弱视用户更易于访问，并且可以更好地为屏幕阅读工具提供服务。

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>在 macOS 公司门户应用中发送诊断报告<!-- 2216677 -->
更新了适用于 macOS 设备的公司门户应用，以改进用户报告 Intune 相关错误的方式。 员工可从公司门户应用中：

- 将诊断报告直接上传给 Microsoft 开发人员团队。
- 通过电子邮件将事件 ID 发送给公司的 IT 支持团队。

有关详细信息，请参阅[发送 macOS 错误](/intune-user-help/send-errors-macos)。

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010-wnready---"></a>Intune 适用于 Windows 10 公司门户应用中的 Fluent 设计系统 <!-- 1195010 WNready -->
Windows 10 Intune 公司门户应用已更新 [Fluent 设计系统的导航视图](https://docs.microsoft.com/en-us/windows/uwp/design/basics/navigation-basics)。 在这款应用旁边，你会注意到一个静态、垂直的所有顶级页面列表。 单击任意链接，可以快速查看页面并在其之间进行切换。 这是你将看到的众多更新中的第一个更新，是我们持续不断努力成果的一部分，以便在 Intune 中创造更具适应性、更能感同身受且更为熟悉的体验。 若要查看更新后的外观，请转到[应用 UI 中的新增功能](whats-new-app-ui.md)。

## <a name="week-of-april-16-2018"></a>2018 年 4 月 16 日当周

#### <a name="use-cisco-anyconnect-client-for-ios----eeready-1333708---"></a>对 iOS 使用 Cisco AnyConnect 客户端 <!-- EEready 1333708 -->

为 iOS 创建新的 VPN 配置文件时，现在提供两个选项：Cisco AnyConnect 和 Cisco Legacy AnyConnect。 Cisco AnyConnect 配置文件支持 4.0.7x 和更新版本。 现有 iOS Cisco AnyConnect VPN 配置文件将被标记为“Cisco Legacy AnyConnect”，并将继续适用于 Cisco AnyConnect 4.0.5x 和较旧版本，如现在一样。

> [!NOTE]
> 此更改仅适用于 iOS。 将继续只提供一个适用于 Android、Android for Work 和 macOS 平台的 Cisco AnyConnect 选项。

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>Jamf 注册的 macOS 设备现在可以向 Intune 注册<!-- 2370684 -->

macOS 公司门户版本 1.3 和 1.4 未成功向 Intune 注册 Jamf 设备。 macOS 门户版本 1.4.2 可修复此问题。


## <a name="week-of-april-9-2018"></a>2018 年 4 月 9 日当周

#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>更新了 Android 适用的公司门户应用的帮助体验<!-- 1631531 -->

我们更新了 Android 适用的公司门户应用中的帮助体验，使其符合 Android 平台的最佳做法。 现在如果在使用应用时遇到问题，用户可以点击“菜单” > “帮助”，然后进行以下操作：
- 将诊断日志上传到 Microsoft。
- 向公司支持人员发送内含问题描述和事件 ID 的电子邮件。  

如需查看更新后的帮助体验，请转到[使用电子邮件发送日志](/intune-user-help/send-logs-to-your-it-admin-by-email-android)和[向 Microsoft 发送错误](/intune-user-help/send-logs-to-microsoft-android)。


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>新的注册失败趋势图表和失败原因表<!-- 1471783 -->

“注册概述”页中会显示注册失败趋势和前五个失败原因。 单击图表或表可查看详细信息，以查找故障排除建议和修正建议。

#### <a name="update-where-to-configure-your-app-protection-policies----2144597---"></a>更新配置应用保护策略的位置<!-- 2144597 -->

在 Microsoft Intune 服务的 Azure 门户中，我们会将“Intune 应用保护”服务边栏选项卡暂时重定向到“移动应用”边栏选项卡。 请注意，Intune 中“应用配置”下的“移动应用”边栏选项卡已包括所有应用保护策略。 直接转到 Intune 即可，无需转到“Intune 应用保护”。 在 2018 年 4 月，我们将停止重定向并将完全删除“Intune 应用保护服务”边栏选项卡，以便在 Intune 中只存在应用保护策略的一个位置。 

**这会对我产生哪些影响？**
此更改将同时影响 Intune 独立版客户和混合版（带 Configuration Manager 的 Intune）客户。 此集成将有助于简化云管理。

**我需要如何准备应对此项变化？**
请将 Intune 标记为收藏（而不是“Intune 应用保护”服务边栏选项卡），并确保熟悉 Intune 的“移动应用”边栏选项卡中的应用保护策略工作流。 我们将重定向一小段时间，然后删除“应用保护”边栏选项卡。 请记住，Intune 中已具备所有应用保护策略，并且你可以修改任何条件访问策略。 有关修改条件访问策略的详细信息，请参阅 [Azure Active Directory 中的条件性访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)。 有关其他信息，请参阅[什么是应用保护策略？](app-protection-policy.md) 


## <a name="week-of-april-2-2018"></a>2018 年 4 月 2 日当周

### <a name="intune-apps"></a>Intune 应用

#### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866---"></a>iOS 版公司门户应用的用户体验更新<!--1412866 -->
我们向 iOS 版公司门户应用发布了用户体验主要更新。 此更新具有经过完全重新设计的视觉效果，包括现代化的外观。 我们保留了应用的功能，但提高了其可用性和可访问性。  

你还会看到：
- 对 iPhone X 的支持。
- 应用启动速度和响应加载速度更快，可节省用户时间。
- 可为用户提供最新状态信息的附加进度条。
- 改进了用户上传日志的方式，因此可在出现问题时更轻松地报告该问题。  

若要查看更新后的外观，请转到[应用 UI 中的新增功能](whats-new-app-ui.md)。

#### <a name="protect-on-premise-exchange-data-using-intune-app-and-ca----1056954---"></a>使用 Intune APP 和 CA 保护本地 Exchange 数据<!-- 1056954 -->
现在可以使用 Intune 应用策略保护 (APP) 和条件访问 (CA) 保护通过 Outlook Mobile 对本地 Exchange 数据的访问权限。 若要在 Azure 门户中添加或修改应用保护策略，请选择“Microsoft Intune” > “移动应用” > “应用保护策略”。 使用此功能之前，请确保满足[适用于 iOS 和 Android 的 Outlook 要求](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx)。

## <a name="week-of-march-26-2018"></a>2018 年 3 月 26 日当周

### <a name="app-management"></a>应用管理

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Microsoft Intune 适用的 iOS 业务线 (LOB) 应用即将过期的警报<!-- 748789 -->

在 Azure 门户中，Intune 将发出警报，通知某些 iOS 业务线应用即将过期。 上传新版本的 iOS 业务线应用后，Intune 会从应用列表删除过期通知。 此过期通知只适用于新上传的 iOS 业务线应用。 系统将在 iOS LOB 应用预配配置文件到期前 30 天显示警告。 过期后，警报会变为已过期。

#### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>使用十六进制代码自定义公司门户主题 <!--1049561 -->

可以使用十六进制代码自定义公司门户应用中的主题颜色。 输入十六进制代码时，Intune 会确定文本颜色，用于提供文本颜色和背景颜色之间的最大对比度。 可以在“移动应用” > “公司门户”中预览文本颜色和公司徽标之间的颜色对比。

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>根据 Android Enterprise 组包括和排除应用分配 <!-- 1813081 -->

Android Enterprise（以前称为 Android for Work）支持包含和排除组，但不支持预创建的“所有用户”和“所有设备”内置组。 有关详细信息，请参阅[在 Microsoft Intune 中包括和排除应用分配](apps-inc-exl-assignments.md)。


### <a name="device-management"></a>设备管理

#### <a name="new-security-enhancements-in-the-intune-service-----1637539---"></a>Intune 服务中新的安全性增强功能<!-- 1637539 -->   

我们在 Azure 中引入了 Intune 的切换键。Intune 独立客户可以使用它将未分配任何策略的设备视为“符合”（安全功能关闭时），或将这些设备视为“不符合”（安全功能开启时）。 这样可以确保只在对设备符合性进行评估后才能访问资源。

不同的用户受此功能的影响不同，具体取决于其是否已分配有符合性策略。

- 如果是新帐户或现有帐户，且没有已分配符合性策略的任何设备，切换键将自动设置为“符合”。 该功能在控制台中的默认设置为“关闭”。 对最终用户没有任何影响。
- 如果是现有帐户，且具有已分配符合性策略的设备，切换键将自动设置为“不符合”。 三月版更新推出后，此功能的默认设置为“启用”。

如果通过条件访问 (CA) 使用符合性策略，且该功能已启用，CA 现在会阻止所有未分配至少 1 个符合性策略的设备。 除非向所有设备分配至少 1 个符合性策略，否则与这些设备关联的最终用户（以前允许访问电子邮件）会失去访问权限。   

请注意，尽管 Intune 服务三月更新版推出后，默认的切换状态会立即显示在 UI 中，但此切换状态不会立即强制执行。 我们将帐户设置为具有有效的切换键之前，你对切换键所作的任何更改都不会影响设备的符合性。 对帐户的设置完成时，我们将通过消息中心告知。 此操作可能会在 Intune 服务更新至三月版后几天内完成。

其他信息：[https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### <a name="enhanced-jailbreak-detection----846515---"></a>增强的越狱检测 <!-- 846515 -->

增强的越狱检测是一种新的符合性设置，能改善 Intune 评估已越狱设备的方式。 此设置会导致设备更频繁地与 Intune 进行确认，这会使用设备的位置服务并影响电池使用情况。

#### <a name="reset-passwords-for-android-o-devices----1238299---"></a>重置 Android O 设备的密码 <!-- 1238299 -->
可以使用 Work 配置文件重置已注册的 Android 8.0 设备的密码。 将“重置密码”请求发送到 Android 8.0 设备时，它将针对当前用户设置新的设备解锁密码或托管的配置文件质询。 系统会发送该密码或质询并立即生效。

#### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>将符合性策略定目标到设备组中的设备 <!--1307012 -->

可以将用户组中的用户设为应用符合性策略的目标用户。 进行此更新后，可以将设备组中的设备设为应用符合性策略的目标设备。 目标设备组中的设备不会收到任何符合性操作。

#### <a name="new-management-name-column----1333586---"></a>新的管理名称列 <!-- 1333586 -->
 设备边栏选项卡上提供一个名为“管理名称”的新列。 这是基于以下公式按每设备分配的自动生成、不可编辑的名称：
- 所有设备的默认名称：<username><em><devicetype></em><enrollmenttimestamp>
- 对于批量添加的设备：<PackageId/ProfileId><em><DeviceType></em><EnrollmentTime>

在设备边栏选项卡中，这是可选列。 默认情况下此列不可用，只能通过列选择器使用。 设备名称不受此新列的影响。

#### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes---1550837---"></a>系统会每 15 分钟提示一次 iOS 设备，要求设置 PIN <!--1550837 -->
符合性或配置策略应用到 iOS 设备后，系统会每 15 分钟提示用户一次，要求设置 PIN。 设置 PIN 之前，系统会持续提示用户。

#### <a name="schedule-your-automatic-updates---1805514---"></a>安排自动更新 <!--1805514 -->
Intune 使你能够使用 [Windows 更新通道设置](windows-update-for-business-configure.md)控制自动更新的安装。 进行此更新后，可以安排定期更新，包括每周更新、每日更新，甚至具体到某个时间更新。

#### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate---2221763---"></a>将完全可分辨名称用作 SCEP 证书的使用者 <!--2221763 -->
创建 SCEP 证书配置文件时，输入使用者名称。 进行此更新后，即可将完全可分辨名称用作使用者。 对于“使用者名称”，选择“自定义”，然后输入 `CN={{OnPrem_Distinguished_Name}}`。 要使用 `{{OnPrem_Distinguished_Name}}` 变量，请务必使用 [Azure Active Directory (AD) 连接](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)将 `onpremisesdistingishedname` 用户属性同步到 Azure AD。

### <a name="device-configuration"></a>设备配置

#### <a name="enable-bluetooth-contact-sharing---android-for-work---1098983---"></a>启用蓝牙联系人共享 - Android for Work <!--1098983 -->
Android 默认禁止通过蓝牙设备同步工作配置文件中的联系人。 因此，工作配置文件联系人不会显示在蓝牙设备的主叫方 ID 中。

进行此更新后，“Android for Work” > “设备限制” > “Work 配置文件设置”中将出现新设置：
- 通过蓝牙共享联系人

Intune 管理员可以配置这些设置，启用共享。 将设备与显示免提的主叫方 ID 的车载蓝牙设备配对时，这非常有用。 启用时，显示工作配置文件联系人。 未启用时，不会显示工作配置文件联系人。

#### <a name="configure-gatekeeper-to-control-macos-app-download-source----1690459---"></a>配置网关守卫以控制 macOS 应用下载源 <!-- 1690459 -->

可以配置网关守卫，通过控制可以下载应用的位置保护设备免受应用侵害。 可以配置以下下载源：Mac App Store、Mac App Store 和已识别的开发人员，或任意位置。 还可以配置用户是否可以通过按住 Control 并单击以替代这些网关守卫控件来安装应用。

可以在“设备配置” -> “创建配置文件” -> “macOS” -> “终结点保护”下找到这些设置。

#### <a name="configure-the-mac-application-firewall----1690461---"></a>配置 Mac 应用程序防火墙 <!-- 1690461 -->

可以配置 Mac 应用程序防火墙。 可以使用此操作以基于每个应用程序来控制连接，而不是基于每个端口来进行控制。 这样一来，可以更轻松地获得防火墙保护的优势，还有助于防止不良应用控制为合法应用打开的网络端口。

可以在“设备配置” -> “创建配置文件” -> “macOS” -> “终结点保护”下找到此功能。

启用防火墙设置后，即可使用两种策略来配置防火墙：

- 阻止所有传入连接

   可以阻止目标设备的所有传入连接。 如果选择进行此操作，系统会阻止所有应用的传入连接。

- 允许或阻止特定应用

   可以允许或阻止特定应用接收传入连接。 还可以启用隐藏模式，阻止对探测请求做出响应。

####  <a name="detailed-error-codes-and-messages----1376342---"></a>详细的错误代码和消息 <!-- 1376342 -->

在设备配置中，可以查看更详细的错误代码和错误消息。 这一改进的报告显示了相关设置、这些设置的状态以及详细的故障排查信息。

##### <a name="more-information"></a>更多信息

- 阻止所有传入连接

   这将阻止所有共享服务（例如文件共享和屏幕共享）接收传入连接。 仍然允许接收传入连接的系统服务包括：
  - configd - 实现 DHCP 和其他网络配置服务
  - mDNSResponder - 实现 Bonjour
  - racoon - 实现 IPSec

    若要使用共享服务，请确保将“传入连接”设置为“未配置”（不“阻止”）。

- 隐藏模式

   启用此选项可防止计算机对探测请求做出响应。 计算机仍然会响应授权应用的传入请求。 意外的请求将被忽略，如 ICMP (ping)。

#### <a name="disable-checks-on-device-restart---1805490---"></a>禁用设备重启检查 <!--1805490 -->
通过 Intune 可以 [管理软件更新]](windows-update-for-business-configure.md)。 进行此更新后，提供“重新启动检查”属性，并默认启用。 要跳过重启设备时出现的典型检查（如活动用户、电池水平等），请选择“跳过”。

#### <a name="new-windows-10-insider-preview-channels-available-for-deployment-rings----1746293---"></a>提供用于部署圈的新 Windows 10 Insider Preview 通道<!-- 1746293 -->
现在创建 Windows 10 部署圈时，可以选择是否选择以下 Windows 10 Insider Preview 服务通道：
- Windows 预览体验内部版本 - 快
- Windows 预览体验内部版本 - 慢
- 发布 Windows 预览体验内部版本 

有关这些通道的详细信息，请参阅[管理 Insider Preview 内部版本](https://insider.windows.com/en-us/for-business-organization-admin/)。   
有关在 Intune 中创建部署通道的详细信息，请参阅[在 Intune 中管理软件更新](windows-update-for-business-configure.md)。

### <a name="intune-apps"></a>Intune 应用

#### <a name="company-portal-enrollment-improved----1874230-eeready--"></a>改进的公司门户注册 <!-- 1874230 eeready-->
在 Windows 10 内部版本 1703 和更高版本上使用公司门户注册设备的用户能够在不退出应用的情况下完成注册的第一步。
#### <a name="hololens-and-surface-hub-now-appear-in-device-lists---1725868---"></a>HoloLens 和 Surface Hub 现在会出现在设备列表 <!--1725868 --> 中
我们向适用于 Android 的公司门户应用添加了对显示已注册 Intune 的 HoloLens 和 Surface Hub 设备的支持。

#### <a name="custom-book-categories-for-volume-purchase-progream-vpp-ebooks----1488911---"></a>批量采购计划 (VPP) 电子书的自定义书籍类别<!-- 1488911 -->
能够创建自定义电子书类别，然后将 VPP 电子书分配到自定义电子书类别。 最终用户即可以看到新建的电子书类别以及分配给该类别的书籍。 有关系详细信息，请参阅[使用 Microsoft Intune 管理批量购买的应用和书籍](vpp-apps.md)。  

#### <a name="support-changes-for-company-portal-app-for-windows-send-feedback-option----2070166---"></a>支持对 Windows 公司门户应用中的“发送反馈”选项进行更改 <!-- 2070166 -->
从 2018 年 4 月 30 日起，Windows 公司门户应用中的“发送反馈”选项将仅适用于运行 Windwos 10 周年更新 (1607) 和更高版本的设备。 当在以下版本中使用 Windows 公司门户应用时，将不再支持“发送反馈”选项：  
- Windows 10（1507 版本）  
- Windows 10（1511 版本）  
- Windows Phone 8.1 

如果你的设备在 Windows 10 RS1 或更高版本上运行，请从应用商店下载最新版本的 Windows 公司门户应用。 如果你运行的是不受支持的版本，请继续使用以下渠道发送反馈： 
- Windows 10 上的反馈中心应用
- 电子邮件 WinCPfeedback@microsoft.com  

#### <a name="new-windows-defender-application-guard-settings----1631890---"></a>新 Windows Defender 应用程序防护设置 <!-- 1631890 -->

- **启用图形加速**：管理员可以为 Windows Defender 应用程序防护启用虚拟图形处理器。 此设置使 CPU 可以将图形呈现卸载到 vGPU。 这可以提升使用图形密集型网站或在容器中观看视频时的性能。

- **SaveFilestoHost**：管理员可以使文件从在容器中运行的 Microsoft Edge 传递到主机文件系统。 打开此选项后，用户可以从容器中的 Microsoft Edge 将文件下载到主机文件系统。

#### <a name="mam-protection-policies-targeted-based-on-management-state----1665993---"></a>根据管理状态设置 MAM 保护策略的适用对象<!-- 1665993 -->
你可以根据设备的管理状态设置 MAM 策略的适用对象：
- **Android 设备** - 可以让非托管设备、Intune 托管设备和 Intune 托管的 Android Enterprise 配置文件（以前称为 Android for Work）使用该策略。
- **iOS 设备** - 可以让非托管设备（仅限 MAM）或 Intune 托管设备使用该策略。

    > [!NOTE]
    > - 2018 年 4 月推出了此功能对 iOS 的支持。

有关详细信息，请参阅[根据设备管理状态设置应用保护策略的适用对象](app-protection-policies.md)。

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows----1683758---"></a>改进了 Windows 适用的公司门户应用中的语言<!-- 1683758 -->
我们对 Windows 10 适用的公司门户中的语言进行了改进，使其更加用户友好，并且更适合你的公司。 如需查看新增功能的示例图片，请参阅[应用 UI 中的新增功能](whats-new-app-ui.md)。

#### <a name="new-additions-to-our-docs-about-user-privacy----1440709---"></a>新增了一些有关用户隐私的文档<!-- 1440709 -->
我们一直在努力增强用户对其数据和隐私的控制权，作为此工作的一部分，我们更新了一些文档，在其中介绍了如何通过公司门户应用查看和删除存储在本地的数据。 了解这些更新的方式如下：

- **Android**[如何从 Intune 删除 Android 设备](/intune-user-help/unenroll-your-device-from-intune-android.md)
- **Android（如果用户拒绝了使用条款）**：[拒绝“使用条款”后如何删除设备管理](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android.md)
- **iOS**：[从 Intune 删除 iOS 设备](/intune-user-help/unenroll-your-device-from-intune-ios.md)
- **Windows**：[从 Intune 删除 Windows 设备](/intune-user-help/unenroll-your-device-from-intune-windows.md)

## <a name="week-of-march-19-2018"></a>2018 年 3 月 19 日当周

### <a name="export-all-devices-into-csv-files-in-ie-edge-or-chrome----2258071---"></a>在 IE、Edge 或 Chrome 中将所有设备导出到 CSV 文件中<!-- 2258071 -->
在“设备” > “所有设备”中，可以将设备“导出”为 CSV 格式的列表。 设备数量 >10,000 台的 Internet Explorer (IE) 用户可以将其设备成功地导出到多个文件中。 每个文件中的设备数量最多为 10,000 台。

设备数量 >30,000 台的 Edge 和 Chrome 用户可以将其设备成功地导出到多个文件中。 每个文件中的设备数量最多为 30,000 台。

[管理设备](device-management.md)中对你管理的设备的用途进行了更详细的介绍。

## <a name="week-of-march-12-2018"></a>2018 年 3 月 12 日当周

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory 网站可能需要 Intune Managed Browser 应用，并且支持 Managed Browser（公共预览版）的单一登录<!-- 710595 -->

利用 Azure Active Directory (Azure AD)，现可在移动设备上将网站访问限制为仅可访问 Intune Managed Browser 应用。 在 Managed Browser 中，网站数据可保持安全并且独立于最终用户的个人数据。 此外，Managed Browser 支持受 Azure AD 保护的站点的单一登录功能。 通过登录 Managed Browser，或在设备上将 Managed Browser 与由 Intune 管理的其他应用配合使用，用户无需输入凭据，Managed Browser 即可访问受 Azure AD 保护的公司站点。 此功能适用于 Outlook Web Access (OWA) 和 SharePoint Online 等站点，以及通过 Azure 应用代理访问的 Intranet 资源等其他公司站点。 有关详细信息，请参阅 [Azure Active Directory 条件访问中的访问控制](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls)。

#### <a name="company-portal-app-for-android-visual-updates---976944---"></a>适用于 Android 的公司门户应用的可视化更新 <!--976944 -->

我们已更新适用于 Android 的公司门户应用以遵循 Android 的 [Material Design](https://material.io/)（材料设计）准则。 可以在[应用 UI 中的新增功能](whats-new-app-ui.md)一文中查看新图标的图像。

### <a name="new-windows-defender-exploit-guard-settings----1631893---"></a>新 Windows Defender 攻击防护设置 <!-- 1631893 -->

现可提供六个新的“攻击面减少”设置和扩展的“受控文件夹访问权限: 文件夹保护”功能。 这些设置可以在 Device configuration\Profiles\
Create profile\Endpoint protection\Windows Defender Exploit Guard 中找到。

#### <a name="attack-surface-reduction"></a>攻击面减少

|设置名  |设置选项  |描述  |
|---------|---------|---------|
|高级勒索软件防护|启用、审核、未配置|使用激进的勒索软件防护。|
|标记从 Windows 本地安全机构子系统窃取的凭据|启用、审核、未配置|标记从 Windows 本地安全机构子系统 (lsass.exe) 窃取的凭据。|
|来自 PSExec 和 WMI 命令的进程创建|阻止、审核、未配置|阻止来自 PSExec 和 WMI 命令的进程创建。|
|从 USB 运行的不受信任和未签名的进程|阻止、审核、未配置|阻止从 USB 运行的不受信任和未签名的进程。|
|不符合普及程度、年龄或信任列表条件的可执行文件|阻止、审核、未配置|阻止可执行文件的运行，除非这些文件符合普及程度、年龄或信任列表条件。|

#### <a name="controlled-folder-access"></a>受控文件夹访问权限

|              设置名               |                                                              设置选项                                                              | 描述 |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| 文件夹保护（已实现） | 未配置、启用、仅审核（已实现）<br><br> <strong>新建</strong><br>阻止磁盘修改、审核磁盘修改 |             |

阻止不友好应用对文件和文件夹进行未经授权的更改。<br><br>**启用**：阻止不受信任的应用修改或删除受保护文件夹中的文件，以及阻止写入到磁盘扇区。<br><br>
**仅阻止磁盘修改**：<br>阻止不受信任的应用写入到磁盘扇区。 不受信任的应用仍可以修改或删除受保护文件夹中的文件。|

## <a name="week-of-february-19-2018"></a>2018 年 2 月 19 日开始的这一周

### <a name="device-enrollment"></a>设备注册

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Intune 支持多个 Apple DEP/Apple School Manager 帐户 <!-- 747685 -->

Intune 现支持最多通过 100 个不同的 [Apple 设备注册计划 (DEP)](device-enrollment-program-enroll-ios.md) 或 [Apple School Manager](apple-school-manager-set-up-ios.md) 帐户注册设备。 可以单独管理注册配置文件和设备的每个已上传令牌。 可以根据已上传的 DEP/ School Manager 令牌自动分配不同的注册配置文件。 如果上传了多个 School Manager 令牌，一次只能与 Microsoft 学校数据同步共享一个令牌。

迁移后，通过 Graph 管理 Apple DEP 或 ASM 的 beta 版本 Graph API 和已发布脚本将不再有效。 新的 beta 版本 Graph API 正在进行开发，将在迁移后发布。

#### <a name="see-enrollment-restrictions-per-user----1634444-eeready-wnready---"></a>请参阅每个用户的注册限制 <!-- 1634444 eeready wnready -->
在“故障排除”边栏选项卡上，现可通过选择“分配”列表中的“注册限制”，查看对每个用户有效的[注册限制](enrollment-restrictions-set.md)。

### <a name="device-management"></a>设备管理
#### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Windows Defender 运行状况状态和威胁状态报告 <!--854704 -->

了解 Windows Defender 的运行状况和状态是管理 Windows 电脑的关键。  通过此更新，Intune 向 Windows Defender 代理的状态和健康状况添加新的报告和操作。 通过使用[设备符合性工作负载](compliance-policy-monitor.md)中的状态汇总报告，可以看到需要以下任一项的设备：
- 签名更新
- “重新启动”
- 手动干预
- 完全扫描
- 需要干预的其他代理状态

每个状态类别的深入报告列出需要注意的各个电脑，或者报告为“清理”的电脑。

#### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>设备限制的新隐私设置 <!--1308926 -->
现在将为设备提供[两个新的隐私设置](device-restrictions-windows-10.md#privacy)：
- **发布用户活动**：将此设置为“阻止”以阻止任务切换程序中最近使用资源的共享体验和发现。
- **仅限本地活动**：将此设置为“阻止”以仅基于本地活动阻止任务切换程序中最近使用资源的共享体验和发现。

#### <a name="new-settings-for-the-edge-browser---1469166---"></a>Microsoft Edge 浏览器的新设置 <!--1469166 -->
现在将为具有 Microsoft Edge 浏览器的设备提供[两个新设置](device-restrictions-windows-10.md#edge-browser)：“到收藏夹文件的路径”和“对收藏夹的更改”。

### <a name="app-management"></a>应用管理
#### <a name="protocol-exceptions-for-applications---1035509---"></a>应用程序的协议异常 <!--1035509 -->

现在可以为 Intune 移动应用程序管理 (MAM) 数据传输策略创建例外情况以打开特定的非托管应用程序。 此类应用程序必须受到 IT 的信任。 除创建的例外情况外，当数据传输策略设置为“仅限托管应用”时，数据传输仍仅限于由 Intune 托管的应用程序。 可以使用协议 (iOS) 或包 (Android) 创建限制。

例如，可以将 Webex 包作为异常添加到 MAM 数据传输策略。 这样使托管 Outlook 电子邮件消息中的 Webex 链接可以直接在 Webex 应用程序中打开。 其他非托管的应用程序中将继续限制数据传输。 有关详细信息，请参阅[应用的数据传输策略例外情况](app-protection-policies-exception.md)。

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Windows 搜索结果中的 Windows 信息保护 (WIP) 加密数据 <!-- 1469193 -->
借助 Windows 信息保护 (WIP) 策略中的设置，现在可以控制是否在 Windows 搜索结果中包含 WIP 加密数据。 通过在 Windows 信息保护策略的“高级设置”中选择“允许 Windows Search 索引器搜索加密项”设置此应用保护策略选项。 应用保护策略必须设置为 Windows 10 平台，应用策略“注册状态”必须设置为“已注册”。 有关详细信息，请参阅[允许 Windows Search 索引器搜索加密项](windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items)。

#### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>配置自我更新的移动 MSI 应用 <!-- 1740840 -->
可以配置已知的自我更新移动 MSI 应用以忽略版本检查过程。 此功能有助于避免出现争用条件。 例如，在应用是由应用开发者自动更新并且也由 Intune 更新时，可能会出现此类争用条件。 两者都可能在 Windows 客户端上尝试强制执行一个应用版本，这可能会产生冲突。 对于这些自动更新的 MSI 应用，可以在“应用信息”边栏选项卡中配置“忽略应用版本”设置。 当此设置切换为“是”时，Microsoft Intune 将会忽略在 Windows 客户端上安装的应用版本。

#### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Intune 中支持的应用许可证的相关集 <!-- 1864117 -->
Azure 门户中的 Intune 现在支持应用许可证的相关集，以作为 UI 中的单个应用项。 此外，任何从适用于企业的 Microsoft Store 同步的脱机许可的应用都将合并到单个应用条目中，并且各个包中的任何部署详细信息都将迁移到单个条目中。 若要在 Azure 门户中查看应用许可证的相关集，请从“移动应用”边栏选项卡中选择“应用许可证”。

### <a name="device-configuration"></a>设备配置
#### <a name="windows-information-protection-wip-file-extensions-for-automatic-encryption----1463582---"></a>自动加密的 Windows 信息保护 (WIP) 文件扩展名 <!-- 1463582 -->
Windows 信息保护 (WIP) 策略中的设置现在允许按照 WIP 策略中的定义，在从公司边界内的服务器消息块 (SMB) 共享进行复制时，指定自动加密哪些文件扩展名。

#### <a name="configure-resource-account-settings-for-surface-hubs"></a>为 Surface Hub 配置资源帐户设置

现在可以为 Surface Hub 远程配置资源帐户设置。

资源帐户由 Surface Hub 用于对 Skype/Exchange 进行身份验证，以便它可以加入会议。
需要创建一个唯一的资源帐户，以使 Surface Hub 可以作为会议室出现在会议中。
例如“会议室 B41/6233”等资源帐户。

> [!NOTE]
> - 如果将字段留空，则将替代之前在设备上配置的特性。
>
> - 资源帐户属性可以在 Surface Hub 上动态变化。 例如，在启用密码轮转的情况下。 所以，Azure 控制台中的值可能需要一些时间才能反映设备上的实际情况。
>
>   若要了解 Surface Hub 上当前配置的内容，可以将资源帐户信息包括在硬件清单中（已有 7 天的间隔时间）或者作为只读属性包括。 若要在远程操作发生后增强准确性，可以在运行操作以更新 Surface Hub 上的帐户/参数后立即获取参数的状态。


##### <a name="attack-surface-reduction"></a>攻击面减少


|设置名  |设置选项  |描述  |
|---------|---------|---------|
|从电子邮件中执行受密码保护的可执行内容|阻止、审核、未配置|防止运行通过电子邮件下载的受密码保护的可执行文件。|
|高级勒索软件防护|启用、审核、未配置|使用激进的勒索软件防护。|
|标记从 Windows 本地安全机构子系统窃取的凭据|启用、审核、未配置|标记从 Windows 本地安全机构子系统 (lsass.exe) 窃取的凭据。|
|来自 PSExec 和 WMI 命令的进程创建|阻止、审核、未配置|阻止来自 PSExec 和 WMI 命令的进程创建。|
|从 USB 运行的不受信任和未签名的进程|阻止、审核、未配置|阻止从 USB 运行的不受信任和未签名的进程。|
|不符合普及程度、年龄或信任列表条件的可执行文件|阻止、审核、未配置|阻止可执行文件的运行，除非这些文件符合普及程度、年龄或信任列表条件。|

##### <a name="controlled-folder-access"></a>受控文件夹访问权限

|              设置名               |                                                              设置选项                                                              | 描述 |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| 文件夹保护（已实现） | 未配置、启用、仅审核（已实现）<br><br> <strong>新建</strong><br>阻止磁盘修改、审核磁盘修改 |             |

阻止不友好应用对文件和文件夹进行未经授权的更改。<br><br>**启用**：阻止不受信任的应用修改或删除受保护文件夹中的文件，以及阻止写入到磁盘扇区。<br><br>
**仅阻止磁盘修改**：<br>阻止不受信任的应用写入到磁盘扇区。 不受信任的应用仍可以修改或删除受保护文件夹中的文件。|

#### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies---1704133--"></a>对适用于 Windows 10 及更高版本符合性策略的系统安全设置的添加<!--1704133-->

现在提供对 Windows 10 符合性设置的添加，包括需要防火墙和 Windows Defender 防病毒。


### <a name="role-based-access-control"></a>基于角色的访问控制
### <a name="intune-apps"></a>Intune 应用
#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business---1222672--"></a>支持适用于企业的 Microsoft 应用商店中的脱机应用<!--1222672-->
从适用于企业的 Microsoft Store 购买的脱机应用现在已同步到 Azure 门户。 可以将这些应用部署到设备组或用户组。 这些脱机应用由 Intune 安装，而不是由应用商店安装。

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>防止最终用户手动添加或删除工作配置文件中的帐户 <!-- 1728700 -->

将 Gmail 应用部署到 Android for Work 配置文件中后，现在可防止最终用户通过使用 Android for Work 设备限制配置文件中的“添加和删除帐户”设置手动添加或删除工作配置文件中的帐户。

## <a name="week-of-february-5-2018"></a>2018 年 2 月 5 日开始的这一周

### <a name="device-enrollment"></a>设备注册

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625-eeready---"></a>新增了 Apple 批量注册所需的用户身份验证选项 <!-- 747625 eeready -->

> [!NOTE]
> 新租户可立即查看此功能。 对于现有租户，此功能将于四月推出。 此次推出完成之前，你可能无权访问这些新功能。

对于以下注册方法，Intune 现支持使用“公司门户”应用验证设备：

- Apple 设备注册计划
- Apple School Manager
- Apple Configurator 注册

使用“公司门户”选项时，可以强制执行 Azure Active Directory 多重身份验证，而不会屏蔽这些注册方法。

使用“公司门户”选项时，Intune 会跳过 iOS 设置助理中用于用户关联注册的用户身份验证。 也就是说，设备最初注册为无用户设备，因此不会接收用户组的配置或策略。 只会接收设备组的配置和策略。 不过，Intune 会在设备上自动安装“公司门户”应用。 首个启动并登录“公司门户”应用的用户将与 Intune 中的设备相关联。 此时，用户将会接收用户组的配置和策略。 只有重新注册，才能更改用户关联。

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685-eeready---"></a>Intune 支持多个 Apple DEP/Apple School Manager 帐户 <!-- 747685 eeready -->

Intune 现支持最多通过 100 个不同的 Apple 设备注册计划 (DEP) 或 Apple School Manager 帐户注册设备。 可以单独管理注册配置文件和设备的每个已上传令牌。 可以根据已上传的 DEP/ School Manager 令牌自动分配不同的注册配置文件。 如果上传了多个 School Manager 令牌，一次只能与 Microsoft 学校数据同步共享一个令牌。

迁移后，通过 Graph 管理 Apple DEP 或 ASM 的 beta 版本 Graph API 和已发布脚本将不再有效。 新的 beta 版本 Graph API 正在进行开发，将在迁移后发布。

### <a name="remote-printing-over-a-secure-network----1709994----"></a>通过安全网络远程打印 <!-- 1709994  -->
使用 PrinterOn 的无线移动打印解决方案，用户将可以随时随地通过安全网络进行远程打印。 PrinterOn 将集成适用于 iOS 和 Android 的 Intune APP SDK。 将可以通过管理控制台中的 Intune“应用保护策略”边栏选项卡，将应用保护策略定目标到此应用。 最终用户将能够通过 Play 商店或 iTunes 下载“PrinterOn for Microsoft”应用，以便在 Intune 生态系统内使用。

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>对使用设备注册管理器的注册的 macOS 公司门户支持 <!-- 1352411 -->

用户现在能够在注册 macOS 公司门户时使用设备注册管理员。

## <a name="week-of-january-29-2018"></a>2018 年 1 月 29 日当周

### <a name="device-enrollment"></a>设备注册

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>已到期令牌和即将到期令牌的警报 <!-- 1639263 -->
概述页现在显示已到期令牌和即将到期令牌的警报。 单击一个令牌的警报后，将转到令牌的详细信息页。  如果单击多个令牌的警报，将转到所有令牌及其状态的列表。 管理员应在到期日期之前续订令牌。

### <a name="device-management"></a>设备管理

#### <a name="remote-erase-command-support-for-macos-devices----1438084---"></a>macOS 设备的远程“清除”命令支持<!-- 1438084 -->

管理员可以对 macOS 设备远程发出清除命令。

> [!IMPORTANT]
> 由于清除命令无法撤消，因此应谨慎使用。

清除命令不仅会从设备中删除所有数据（包括操作系统）， 还会从 Intune 管理范围中删除设备。 不过，并不会向用户发出警告，而是在命令发出后立即执行清除操作。

必须配置 6 位恢复 PIN。 此 PIN 可用于解锁已清除的设备，此时将开始重新安装操作系统。 开始清除后，PIN 便会显示在 Intune 中设备概述边栏选项卡上的状态栏中。 只要清除正在进行中，PIN 就会一直显示。 清除完成后，设备便会从 Intune 管理范围中完全消失。 请务必记录恢复 PIN。这样一来，无论是谁恢复设备，都可以使用它。

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>撤销 iOS 批量采购计划令牌的许可证<!-- 820870 -->
可以撤销给定 VPP 令牌的所有 iOS 批量采购计划 (VPP) 应用的许可证。

### <a name="app-management"></a>应用管理

#### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>撤销 iOS 批量采购计划应用<!-- 820863 -->
对于具有一个或多个 iOS 批量采购计划 (VPP) 应用的给定设备，可以撤销相关的基于设备的应用许可证。 撤销应用许可证将不会从设备中卸载相关的 VPP 应用。 若要卸载 VPP 应用，必须将分配操作更改为“卸载”。 有关详细信息，请参阅[如何使用 Microsoft Intune 管理通过批量采购计划购买的 iOS 应用](vpp-apps-ios.md)。

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>使用内置应用类型将 Office 365 移动应用分配到 iOS 和 Android 设备<!-- 1332318 -->
借助内置应用类型，可更轻松地创建 Office 365 应用并将其分配到管理的 iOS 和 Android 设备。 这些应用包括 Word、Excel、PowerPoint 和 OneDrive 等 Office 365 应用。 可将特定应用分配到应用类型并编辑应用信息配置。

#### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>根据组添加和排除应用分配 <!-- 1406920 -->

在应用分配期间以及在选择分配类型后，可以选择要包括和排除的组。

### <a name="device-configuration"></a>设备配置

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments-----1480316---"></a>可通过包括和排除分配来向组分配应用程序配置策略  <!-- 1480316 -->

可通过结合使用包括分配和排除分配来向一组用户和设备分配应用程序配置策略。 可通过自定义选择组或虚拟组的方式来选择分配。 虚拟组包括“所有用户”、“所有设备”或“所有用户 + 所有设备”。

#### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>支持 Windows 10 版本升级策略 <!-- 903672(archived), 1119689 -->  
可以创建 Windows 10 版本升级策略，将 Windows 10 设备升级到 Windows 10 教育版、Windows 10 教育版 N、Windows 10 专业版、Windows 10 专业版 N、Windows 10 专业教育版和 Windows 10 专业教育版 N。有关 Windows 10 版本升级的详细信息，请参阅[如何配置 Windows 10 版本升级](edition-upgrade-configure-windows-10.md)。

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>适用于 Intune 的条件访问策略只能通过 Azure 门户访问 <!-- 1737088 1634311 -->

从本次发布开始，必须在 [Azure 门户](https://portal.azure.com)中通过“Azure Active Directory” > “条件访问”配置和管理“条件访问”策略。 为方便起见，还可在 Azure 门户中通过“Intune” > “条件访问”，从 Intune 访问此边栏选项卡。

#### <a name="updates-to-compliance-emails---1637547---"></a>更新了符合性电子邮件 <!--1637547 -->

通过发送电子邮件来报告不符合设备时，将包括不符合设备的详细信息。


## <a name="week-of-january-22-2018"></a>2018 年 1 月 22 日当周

### <a name="intune-apps"></a>Intune 应用

#### <a name="new-functionality-for-the-resolve-action-for-android-devices---1583480--"></a>Android 设备的“解决”操作的新功能 <!--1583480-->

适用于 Android 的公司门户应用正在展开更新设备设置的“解决”操作，从而解决[设备加密问题](/intune-user-help/encrypt-your-device-android)。

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>适用于 Windows 10 的公司门户应用中提供远程锁定 <!--676506-->
最终用户现在可以从适用于 Windows 10 的公司门户应用远程锁定他们的设备。 此功能将不会为他们当前使用的本地设备显示。

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>可以更轻松地解决适用于 Windows 10 的“公司门户”应用的符合性问题 <!--676546-->
使用 Windows 设备的最终用户将能够点击“公司门户”应用中的不符合原因。 在可能的情况下，此操作会使用户直接转到“设置”应用中的适当位置，以修复问题。

## <a name="week-of-december-11-2017"></a>2017 年 12 月 11 日当周

### <a name="device-configuration"></a>设备配置

#### <a name="new-automatic-redeployment-setting----1469168---"></a>新的自动重新部署设置<!-- 1469168 -->
使用“自动重新部署”设置，具有管理权限的用户可在设备锁定屏幕上使用 CTRL+Win+R 删除所有用户数据和设置。 设备会自动进行重新配置并重新注册到管理。 此设置可在“Windows 10”>“设备限制”>“常规”>“自动重新部署”中找到。 有关详细信息，请参阅[适用于 Windows 10 的 Intune 设备限制设置](device-restrictions-windows-10.md#general)。

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy-----903672--1119689---"></a>支持在 Windows 10 版本升级策略中指定其他源版本  <!-- 903672,  1119689 -->
现在可以使用 Windows 10 版本升级策略从其他 Windows 10 版本（Windows 10 专业版、Windows 10 专业教育版、Windows 10 云端版等）升级。 在此版本发布前，支持的版本升级路径更加受限。 有关详细信息，请参阅[如何配置 Windows 10 版本升级](edition-upgrade-configure-windows-10.md)。

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>新的 Windows Defender 安全中心 (WDSC) 设备配置文件设置<!-- 1335507 -->

Intune 在名为“Windows Defender 安全中心”的端点保护下添加了一个新的设备配置文件设置部分。 IT 管理员可以配置最终用户能访问 Windows Defender 安全中心应用的哪些支柱。 如果 IT 管理员在 Windows Defender 安全中心应用中隐藏支柱，则与隐藏支柱相关的所有通知都不会显示在用户设备上。

以下是管理员可以在 Windows Defender 安全中心设备配置文件设置中隐藏的支柱：
- 病毒和威胁防护
- 设备性能和运行状况
- 防火墙和网络保护
- 应用和浏览器控制
- 产品系列选项

IT 管理员还可以自定义用户接收的通知。 例如，你可以配置用户是接收由 WDSC 中的可见支柱生成的所有通知还是仅接收关键通知。 非关键通知包括 Windows Defender 防病毒活动的周期性摘要以及扫描完成时的通知。 所有其他通知被视为是关键通知。 另外，还可以自定义通知内容，例如，可以提供 IT 联系信息以嵌入用户设备上显示的通知。

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling----1361755---"></a>SCEP 和 PFX 证书处理的多个连接器支持<!-- 1361755 -->

使用本地 NDES 连接器向设备提供证书的客户现在可以在一个租户中配置多个连接器。

这项新功能支持以下方案：

- 高可用性

每个 NDES 连接器从 Intune 中拉取证书请求。  如果一个 NDES 连接器脱机，另一个连接器可以继续处理请求。

#### <a name="customer-subject-name-can-use-aaddeviceid-variable-----1468599---"></a>客户的使用者名称可以使用 AAD_DEVICE_ID 变量  <!-- 1468599 -->

在 Intune 中创建 SCEP 证书配置文件时，现在可以使用 AAD_DEVICE_ID 变量生成自定义使用者名称。   如果使用此 SCEP 配置文件请求获取证书，这个变量会被替换为发出证书请求的设备的 AAD 设备 ID。


### <a name="device-management"></a>设备管理

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747---"></a>使用 Intune 的设备符合性引擎管理 Jamf 注册的 macOS 设备<!-- 1592747 -->
现在可以使用 Jamf 将 macOS 设备状态信息发送到 Intune。然后，Intune 会评估它与 Intune 控制台中定义的策略的符合性。 基于设备符合性状态以及其他条件（如位置、用户风险等），条件访问将强制实现 macOS 设备访问云和与 Azure AD 连接的本地应用程序（包括 Office 365）的符合性。 详细了解如何[设置 Jamf 集成](conditional-access-integrate-jamf.md)和[强制 Jamf 托管设备遵守策略](conditional-access-assign-jamf.md)。

#### <a name="new-ios-device-action------1424701---"></a>新的 iOS 设备操作<!-- 1424701 -->

现在可以关闭 iOS 10.3 监管的设备。 此操作会立即关闭设备，而不会向最终用户发出警告。 当你在“设备”工作负载中选择设备时，可以在设备属性中找到“关闭（仅监督）”操作。

#### <a name="disallow-datetime-changes-to-samsung-knox-devices----1468103---"></a>禁止对 Samsung Knox 设备更改日期/时间 <!-- 1468103 -->

我们新增了一项功能，以便用户能够禁止对 Samsung Knox 设备更改日期和时间。 此功能位于“设备配置文件” > “设备限制(Android)” > “常规”中。

#### <a name="surface-hub-resource-account-supported----1566442----"></a>支持的 Surface Hub 资源帐户<!-- 1566442  -->

我们新增了一项设备操作，以便管理员能够定义和更新与 Surface Hub 关联的资源帐户。

资源帐户由 Surface Hub 用于通过 Skype/Exchange 进行身份验证，以便它可以加入会议。 可以创建一个唯一的资源帐户，以使 Surface Hub 作为会议室出现在会议中。 例如，资源帐户可能会显示为“会议室 B41/6233”。 通常需要针对会议室位置以及何时需要更改其他资源帐户参数来配置 Surface Hub 的资源帐户（称为设备帐户）。

如果管理员需要更新设备上的资源帐户，他们必须提供与该设备关联的当前 Active Directory/Azure Active Directory 凭据。 如果为设备启用了密码轮换，则管理员必须转到 Azure Active Directory 以查找密码。

> [!NOTE]
> 所有字段都会向下发送到一个包中，覆盖之前配置的所有字段。 空字段也会覆盖现有字段。

以下是管理员可以配置的设置：

- 资源帐户
   - **Active Directory 用户**

      域名\用户名或用户主体名称 (UPN)：user@domainname.com

   - **密码**

- 可选的资源帐户参数（必须使用指定的资源帐户设置）

   - **密码轮转周期**

     出于安全原因，确保帐户密码每周由 Surface Hub 自动更新。 在启用此功能之后，要配置任何参数，Azure Active Directory 中的帐户必须先进行密码重置。

   - **SIP (会话初始协议)地址**

     仅在自动发现失败时使用。

   - **Email**

     设备/资源帐户的电子邮件地址。

   - **Exchange Server**

     仅在自动发现失败时需要。

   - **日历同步**

     指定是否启用日历同步和其他 Exchange Server 服务。 例如：会议同步。

#### <a name="install-office-apps-on-macos-devices----1494311---"></a>在 macOS 设备上安装 Office 应用<!-- 1494311 -->
现在可以在 macOS 设备上安装 Office 应用。 这个新的应用类型将允许你安装 Word、Excel、PowerPoint、Outlook 和 OneNote。 这些应用还随附 Microsoft AutoUpdate (MAU)，有助于保护和不断更新应用。

### <a name="app-management"></a>应用管理

#### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>删除 iOS 批量采购计划令牌<!-- 820879 -->
可以使用控制台删除 iOS Volume Purchase Program (VPP) 令牌。 当你有重复的 VPP 令牌实例时，可能需要执行此操作。

### <a name="intune-apps"></a>Intune 应用


### <a name="role-based-access-control"></a>基于角色的访问控制

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1667026---"></a>名为“当前用户”的新实体集合仅限于当前活动的用户数据<!-- 1667026 -->

User 实体集合包含企业中分配有许可证的所有 Azure Active Directory (Azure AD) 用户。 例如，在上个月期间，可能将某个用户添加到 Intune 然后又将其删除。 尽管在提交报告时该用户已不存在，但在数据中仍然会显示该用户及其状态。 可以创建一个报告，该报告将显示用户的历史记录在你的数据中存在的持续时间。

相比之下，新的“当前用户”实体集合只包含尚未被删除的用户。 “当前用户”实体集合仅包含当前活动的用户。 有关“当前用户”实体集合的信息，请参阅[引用当前用户实体](reports-ref-current-user.md)。


### <a name="updated-graph-apis----1736360---"></a>更新了 Graph API <!-- 1736360 -->

在此版本中，我们更新了一些适用于 Intune 且处于 beta 阶段的 Graph API。 有关详细信息，请查看每月的 [Graph API 更改日志](https://developer.microsoft.com/graph/docs/concepts/changelog)。

## <a name="week-of-december-4-2017"></a>2017 年 12 月 4 日当周

### <a name="monitor-and-troubleshoot"></a>监视和故障排除

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>Intune 支持 Windows 信息保护 (WIP) 拒绝的应用<!-- 1479103 -->
可在 Intune 中指定已拒绝的应用。 如果某个应用被拒，它会被阻止访问公司信息，允许的应用列表则与此相反。 有关详细信息，请参阅 [Recommended deny list for Windows Information Protection](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection)（Windows 信息保护的推荐拒绝列表）。


## <a name="week-of-november-27-2017"></a>2017 年 11 月 27 日当周

### <a name="device-enrollment"></a>设备注册

#### <a name="troubleshoot-enrollment-issues-----746324---"></a>排查注册问题<!-- 746324 -->

“疑难解答”工作区现在显示用户注册问题。 问题的相关详细信息和建议的修正步骤可帮助管理员和支持人员排查问题。 某些注册问题可能无法捕获，还有某些错误可能没有修正建议。

#### <a name="group-assigned-enrollment-restrictions----747598---"></a>组分配注册限制 <!-- 747598 -->

作为 Intune 管理员，现在可[为用户组创建自定义设备类型和设备限制注册限制](enrollment-restrictions-set.md)。

使用 Intune Azure 门户，每种限制类型最多可创建 25 个实例，然后这些实例可分配给用户组。 组分配限制会替代默认限制。

所有限制类型实例均保存在严格有序的列表中。 此顺序定义冲突解决的优先级值。 受多个限制实例影响的用户仅受优先级值最高的实例限制。 通过将给定实例拖至列表中其他位置，可更改其优先级。

将 Android for Work 设置从 Android For Work 注册菜单迁移到注册限制菜单时，会随之发布此功能。 由于这种迁移可能需要几天时间，帐户可能会在 11 月版本的其他部分中升级，然后才能看到已为注册限制启用组分配。

#### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>支持多个网络设备注册服务 (NDES) 连接器 <!-- 1528104 -->

NDES 允许无域凭据运行的移动设备基于简单证书注册协议 (SCEP) 获取证书。
利用此更新可支持多个 NDES 连接器。

#### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>独立于 Android 设备管理 Android for Work 设备 <!-- 1490731 EEready-->

Intune 支持独立于 Android 平台管理 Android for Work 设备的注册。 这些设置位于“设备注册” > “注册限制” > “设备类型限制”下。 （这些设置之前位于“设备注册” > “Android for Work 注册” > “Android for Work 注册设置”下。）

默认情况下，Android for Work 设备的设置与 Android 设备的设置相同。 但是，更改 Android for Work 设置后则不再相同。

如果阻止个人 Android for Work 注册，那么仅公司 Android 设备可注册为 Android for Work。

使用新设置时，请考虑下列几点：

##### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>如果之前从未载入 Android for Work 注册

默认设备类型限制将阻止新的 Android for Work 平台。 载入该功能后，可允许设备注册 Android for Work。 为此，请更改默认值或新建一个设备类型限制，取代默认设备类型限制。

##### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>如果已载入 Android for Work 注册

如果之前已载入，那么情况取决于所选设置：

| Setting | 默认设备类型限制中的 Android for Work 状态 | 注意 |
| --- | --- | --- |
| **将所有设备作为 Android 管理** | 已阻止 | 所有 Android 设备均不注册 Android for Work。 |
| 将受支持设备作为 Android for Work 管理 | ，然后用户才能访问 | 所有支持 Android for Work 的 Android 设备均须注册 Android for Work。 |
| **仅为这些组中的用户将受支持设备作为 Android for Work 管理** | 已阻止 | 创建单独的设备类型限制策略替代默认值。 此策略将之前选择的组定义为允许 Android for Work 注册。 允许所选组中的用户继续注册 Android for Work 设备。 所有其他用户则不能注册 Android for Work。 |

所有情况下都将保留预期规则。 对你来说，无需任何操作即可维护环境中的 Android for Work 全局或按组允许。

### <a name="app-management"></a>应用管理

#### <a name="app-install-report-updated-to-include-install-pending-status----1249446---"></a>应用安装报表已更新以包括安装挂起状态 <!-- 1249446 -->  

通过“移动应用”工作负荷中的“应用”列表，可获取每个应用的“应用安装状态”报表，该报表现在包括用户和设备的“安装挂起”计数。

#### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>移动威胁检测的 iOS 11 应用清单 API <!-- 1391759 -->

Intune 从个人和公司所有的设备收集应用清单信息，这些信息可供移动威胁检测 (MTD) 提供程序提取，例如 Lookout for Work。 可通过 iOS 11+ 设备的用户收集应用清单。

**应用清单**  
清单（来自公司所有的 iOS 11+ 和个人所有的设备）将发送给 MTD 服务提供程序。 应用清单中的数据包括：

 - 应用 ID
 - 应用版本
 - 应用内部版本号
 - 应用程序名称
 - 应用程序包大小
 - 应用动态大小
 - 应用是否经过验证
 - 应用是否受管理


### <a name="device-management"></a>设备管理

#### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone----1463747-wnready---"></a>将混合 MDM 用户及其设备迁移至 Intune 独立版<!-- 1463747 wnready -->
现有新的流程和工具可用于将混合 MDM 的用户及其设备迁移至 Azure 门户中的 Intune，这可让你执行以下任务：
- 将 Configuration Manager 控制台中的策略和配置文件复制到 Azure 门户中的 Intune
- 将一部分用户移至 Azure 门户中的 Intune，同时将剩余用户保留在混合 MDM 中
- 将设备迁移至 Azure 门户中的 Intune，而无需重新注册这些设备

有关详细信息，请参阅[将混合 MDM 用户及其设备迁移至 Intune 独立版](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)。

#### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>本地 Exchange 连接器高可用性支持 <!-- 676614 -->
使用指定的 CAS 建立与 Exchange 的连接后，Exchange 连接器现在可以发现其他 CAS。 如果主 CAS 不可用，在主 CAS 的故障修复前，连接器会先故障转移到其他可用的 CAS。 有关详细信息，请参阅[本地 Exchange 连接器高可用性支持](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support)。

#### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>远程重启 iOS 设备（仅限被监督的设备）<!-- 1424595 -->

可使用设备操作触发受监督的 iOS 10.3+ 设备重启。 要详细了解如何使用设备重启操作，请参阅[使用 Intune 远程重启设备](device-restart.md)。

> [!Note]
> 此命令需要受监督的设备和“设备锁定”访问权限。 设备会立即重启。 密码锁定的 iOS 设备重启后不会重新加入 Wi-Fi 网络；重启后，它们可能无法与服务器进行通信。

#### <a name="single-sign-on-support-for-ios----1333645---"></a>iOS 的单一登录支持 <!-- 1333645 -->  

可对 iOS 用户使用 SSO。 编码为在单一登录有效负载中查找用户凭据的 iOS 应用可使用此有效负载配置更新。 还可使用 UPN 和 Intune 设备 ID 配置主体名称和领域。 有关详细信息，请参阅[配置 Intune for iOS 设备 SSO](sso-ios.md)。

#### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>为个人设备添加“查找我的 iPhone” <!--1427287-->
现可查看 iOS 设备是否已开启“激活锁”。 经典门户中的 Intune 之前并不提供此功能。


#### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>使用 Intune 远程锁定受管理的 macOS 设备 <!-- 1437691 -->

可锁定丢失的 macOS 设备并设置 6 位数的恢复 PIN。 锁定时，“设备概述”边栏选项卡会显示 PIN，直到发送另一个设备操作。

有关详细信息，请参阅[使用 Intune 远程锁定受管理设备](device-remote-lock.md)。

#### <a name="new-scep-profile-details-supported----1559808---"></a>支持新的 SCEP 配置文件详细信息 <!-- 1559808 -->

在 Windows、iOS、macOS 和 Android 平台上创建 SCEP 配置文件时，管理员现可设置其他设置。  管理员可设置 IMEI、序列号或公用名，包括采用使用者名称格式的电子邮件。

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

#### <a name="retain-data-during-a-factory-reset----1588489---"></a>在恢复出厂设置过程中保留数据 <!--1588489 -->
将 Windows 10 版本 1709 及更高版本重置为出厂设置时，可使用新功能。 管理员可指定在恢复出厂设置过程中，是否将设备注册和其他配置数据保留在设备上。

恢复出厂设置过程中保留以下数据：
- 与设备关联的用户帐户
- 计算机状态（域加入，已加入 Azure Active Directory）
- MDM 注册
- OEM 安装的应用（存储和 Win32 应用）
- 用户配置文件
- 用户配置文件以外的用户数据
- 用户自动登录

不保留以下数据：
- 用户文件
- 用户安装的应用（存储和 Win32 应用）
- 非默认设备设置

### <a name="monitor-and-troubleshoot"></a>监视和故障排除
#### <a name="window-10-update-ring-assignments-are-displayed----1621837---"></a>显示 Windows 10 更新通道分配<!-- 1621837 -->
进行故障排除时，对于正在查看的用户，可看到任何 Windows 10 更新通道分配。  

#### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings-----1455974----"></a>Windows Defender 高级威胁防护报告频率设置 <!-- 1455974  -->
Windows Defender 高级威胁防护 (WDATP) 服务允许管理员对受管理设备的报告频率进行管理。 借助新的“提高遥测报告频率”选项，WDATP 可提高收集数据和评估风险的频率。 报告的默认值可优化速度和性能。 提高报告频率十分适合高风险设备。 在“设备配置”的“Windows Defender ATP”配置文件中可找到此设置。

#### <a name="audit-updates----1412961---"></a>审核更新 <!-- 1412961 -->  
Intune 审核提供与 Intune 相关的更改操作记录。  捕获所有创建、更新、删除和远程任务操作，并保留一年。  通过 Azure 门户，可查看每个工作负荷中过去 30 天的审核数据，还可对这些数据进行筛选。  利用相应的图形 API，可检索过去一年存储的审核数据。

“审核”位于“监视”组下。 每个工作负荷都有一个“审核日志”菜单项。




## <a name="week-of-november-20-2017"></a>2017 年 11 月 20 日当周

### <a name="app-management"></a>应用管理

#### <a name="google-play-protect-support-on-android----908720---"></a>Android 上的 Google Play Protect 支持 <!-- 908720 -->

随着 Android Oreo 的发布，Google 引入了一系列名为 Google Play Protect 的安全功能，以便用户和组织可以运行安全的应用和 Android 映像。 Intune 现支持 Google Play Protect 功能，包括 SafetyNet 远程认证。 管理员可以设置符合性策略要求，要求配置和正常运行 Google Play Protect。
“SafetyNet 设备认证”设置要求设备连接到 Google 服务，以验证设备是否正常运行且未遭到入侵。 管理员还可以对 Android for Work 设置配置文件设置，以要求 Google Play 服务对已安装的应用进行验证。 如果设备不符合 Google Play Protect 要求，条件访问可能会阻止用户访问公司资源。

- 了解[如何创建用于启用 Google Play 保护的设备符合性策略](https://docs.microsoft.com/intune/compliance-policy-create-google-play-protect)。

#### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>允许受管理应用发送文本协议 <!-- 1414050  -->

由 Intune App SDK 管理的应用可发送短信。

## <a name="week-of-november-13-2017"></a>2017 年 11 月 13 日当周

### <a name="intune-apps"></a>Intune 应用
#### <a name="company-portal-app-for-macos-is-available---1541700--"></a>现已提供适用于 macOS 的公司门户应用 <!--1541700-->
macOS 上的 Intune 公司门户提供了经过优化的更新体验，可以清楚地显示用户所需要的针对已注册的所有设备的所有信息和符合性通知。 而且，Intune 公司门户部署到设备后，Microsoft AutoUpdate for macOS 将为其提供更新。 从 macOS 设备登录到 Intune 公司门户网站，可以下载适用于 macOS 的新 Intune 公司门户。

#### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps-----1248473---"></a>Microsoft Planner 现在属于已批准应用的移动应用管理 (MAM) 列表的一部分<!-- 1248473 -->
适用于 iOS 和 Android 的 Microsoft Planner 应用现在属于已批准应用的移动应用管理 (MAM) 列表的一部分。 可以通过 Azure 门户中的“Intune 应用保护”边栏选项卡为所有租户配置应用。
- 了解有关[已批准应用的 MAM 列表](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)的详细信息。

#### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices------1547061---"></a>iOS 设备上的每个应用程序 VPN 要求更新频率<!-- 1547061 -->  
管理员现在可以删除 iOS 设备上应用程序的每个应用程序 VPN 要求；受影响的设备将在下一次 Intune 签入后更新，通常在 15 分钟内发生。  

### <a name="monitor-and-troubleshoot"></a>监视和故障排除
#### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>支持适用于 Exchange 连接器的 System Center Operations Manager 管理包<!-- 885457 -->
现已提供适用于 Exchange 连接器的 System Center Operations Manager (SCOM) 管理包帮助你分析 Exchange 连接器日志。 在你需要进行故障排除时，此功能可提供多种监视该服务的方式。

## <a name="week-of-november-6-2017"></a>2017 年 11 月 6 日当周

### <a name="device-enrollment"></a>设备注册
#### <a name="co-management-for-windows-10-devices-----1243445---"></a>适用于 Windows 10 设备的共同管理<!-- 1243445 -->
共同管理是一种解决方案，可在传统管理与现代管理之间架起一座桥梁，为你提供利用分阶段的方法实现转换的途径。 共同管理本质上是一种解决方案，其中 Configuration Manager 和 Microsoft Intune 同时管理 Windows 10 设备，并且这些设备可联接到 Active Directory (AD) 和 Azure Active Directory (Azure AD)。  此配置提供以适合组织的步调（如果无法即刻完成所有迁移）逐步实现现代化的方式。  

#### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>通过 OS 版本限制 Windows 注册<!-- 245498 -->
作为 Intune 管理员，现在可为设备注册指定 Windows 10 的最低和最高版本。 可以在“平台配置”边栏选项卡中设置这些限制。

Intune 将继续支持 Windows 8.1 电脑和手机注册。 但只有对 Windows 10 才可设置最高和最低版本限制。 若要允许注册 8.1 设备，请将最低限制留空。

#### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Windows AutoPilot 未分配设备警报<!-- 1631236 -->
在“Microsoft Intune” > “设备注册” > “概述”页中，为 Windows AutoPilot 未分配设备提供了一个新警报。 此警报显示有多少来自 AutoPilot 计划的设备尚未分配 AutoPilot 部署配置文件。 使用警报中的信息可创建配置文件，并将其分配到未分配的设备。 单击警报时，会看到 Windows AutoPilot 设备的完整列表，以及与之相关的详细信息。 有关详细信息，请参阅[使用 Windows AutoPilot Deployment 计划注册 Windows 设备](https://docs.microsoft.com/intune/enrollment-autopilot)。

### <a name="device-management"></a>设备管理

#### <a name="refresh-button-for-devices-list-------1333581---"></a>设备列表的刷新按钮 <!-- 1333581 -->
由于设备列表不会自动刷新，可使用新的“刷新”按钮来更新列表中显示的设备。

#### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>对 Symantec 云证书颁发机构 (CA) 的支持<!-- 1333638 -->    
Intune 现在支持 Symantec 云 CA，允许 Intune 证书连接器从 Symantec 云 CA 向 Intune 受管理设备颁发 PKCS 证书。 如果现已将 Intune 证书连接器和 Microsoft 证书颁发机构 (CA) 配合使用，则可以利用现有 Intune 证书连接器设置添加 Symantec CA 支持。

#### <a name="new-items-added-to-device-inventory-----1404455---"></a>添加到设备清单的新项目<!--1404455 -->
以下新项目现在适用于[由已注册设备获取的清单](device-inventory.md)：

- Wi-Fi MAC 地址
- 总存储空间
- 总可用空间
- MEID
- 订阅者运营商


### <a name="app-management"></a>应用管理
#### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>通过在设备上定义最低 Android 安全修补程序版本设置对应用的访问权限<!-- 1278463 -->   
管理员可定义最低 Android 安全修补程序版本，必须在设备上安装该修补程序才能访问托管帐户下的托管应用程序。

> [!Note]  
> 此功能仅适用于在安装了 Android 6.0 及更高版本的设备上限制由 Google 发布的安全修补程序。

#### <a name="app-conditional-launch-support----1193313---"></a>应用条件启动支持<!-- 1193313 -->
IT 管理员现可通过 Azure 管理门户设置要求，通过移动应用管理 (MAM) 强制要求在应用程序启动时输入密码，而不是输入数字 PIN。 如果进行此配置，在访问启用 MAM 的应用程序前，用户需要在出现提示时设置并使用密码。 密码是至少包含一个特殊字符或大写/小写字母的数字 PIN。 此版本的 Intune 仅在 iOS 上支持此功能。 Intune 对密码的支持与支持数字 PIN 类似，设置了最短长度并且允许重复字符和序列。 该功能需要一些应用程序（例如 WXP、Outlook、Managed Browser、Yammer）的参与，将 Intune APP SDK 与代码集成，以便此功能准备就绪并在目标应用程序中强制实施密码设置。

#### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>设备安装状态报告中业务线应用的应用版本号<!-- 1233999 -->
在此版本中，设备安装状态报告显示适用于 iOS 和 Android 的业务线应用的应用版本号。 可使用此信息对应用进行故障排除，或者查找正在运行过时应用版本的设备。


### <a name="device-configuration"></a>设备配置
#### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>管理员现在可以使用设备配置文件在设备上配置防火墙设置<!-- 951708 -->   
管理员可以启用防火墙，还可以为域、专用网络和公用网络配置多种协议。  可在“Endpoint Protection”配置文件中找到这些防火墙设置。

#### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>Windows Defender 应用程序防护根据组织的定义，帮助阻止设备访问不受信任的网站<!-- 958257 -->   
利用 Windows 信息保护工作流或设备配置下的新“网络边界”配置文件，管理员可将站点定义为“受信任站点”或“公司站点”。 如果使用 Microsoft Edge 访问未在 64 位 Windows 10 设备的受信任网络边界中列出的站点，这些站点将转为在 Hyper-V 虚拟计算机内的浏览器中打开。

可在设备配置文件“Endpoint Protection”中找到应用程序防护。 管理员可在其中配置虚拟化浏览器与主机，以及非受信任站点与受信任站点之间的交互，同时存储虚拟化浏览器中生成的数据。 要在设备上使用应用程序防护，首先必须配置网络边界。 仅可为每个设备定义一个网络边界，这一点非常重要。  

#### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>Windows 10 企业版上的 Windows Defender 应用程序控制提供仅信任经授权应用的模式<!-- 1031096 -->    
由于每天都有成千上万个新恶意文件生成，因此使用基于签名的防病毒检测来抵御恶意软件可能无法再针对新型攻击提供足够的防御。 通过在 Windows 10 企业版上使用 Windows Defender 应用程序控制，可以更改设备配置，从信任防病毒软件或其他安全解决方案未阻止的所有应用的模式，更改为操作系统仅信任经企业授权的应用的模式。 可在 Windows Defender 应用程序控制中将信任分配给应用。

利用 Intune，可以在“仅审核”模式或强制执行模式下配置应用程序控制策略。 在“仅审核”模式下运行的应用不会受到阻止。 “仅审核”模式在本地客户端日志中记录所有事件。 还可以配置是仅允许运行 Windows 组件和 Microsoft Store 应用，还是允许运行 Intelligent Security Graph 定义的信誉良好的其他应用。

#### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>Windows Defender 攻击防护是面向 Windows 10 的一组新入侵防护功能<!-- 1063615 -->   
Windows Defender 攻击防护内含自定义规则，可降低应用程序受到攻击的可能性、预防宏和脚本威胁、自动阻止网络连接到可信度较低的 IP 地址，以及保护数据免受勒索软件和未知威胁的攻击。 Windows Defender 攻击防护包含以下组成部分：

- “攻击面减少(ASR)”提供用于预防宏、脚本和电子邮件威胁的规则。
- “控制文件夹访问”可自动阻止访问受保护文件夹中的内容。
- “网络筛选器”可阻止从任何应用到低可信度 IP/域的出站连接
- “攻击防护”提供内存、控制流和策略限制，可用于保护应用程序免受攻击。


#### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices----790537---"></a>在 Intune 中管理 PowerShell 脚本以供 Windows 10 设备使用<!-- 790537 -->

Intune 管理扩展允许你在 Intune 中上传 PowerShell 脚本以在 Windows 10 设备上运行。 扩展对 Windows 10 移动设备管理 (MDM) 功能进行了补充，使你可更轻松地采用新式管理。 有关详细信息，请参阅[在 Intune 中管理 PowerShell 脚本以供 Windows 10 设备使用](intune-management-extension.md)。

#### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>适用于 Windows 10 的 Intune 新设备限制设置<!-- 1308850 -->
-    消息传送（仅限移动设备）- 禁用测试或 MMS 消息
-    密码 - 此设置用于启用 FIPS，并且支持使用 Windows Hello 设备辅助设备进行身份验证 
-    显示 - 此设置用于打开或关闭旧版应用的 GDI 缩放

#### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Windows 10 设备的展台模式限制<!-- 1308872 -->   
可将 Windows 10 设备的用户限制为使用展台模式，从而限制这些用户仅使用一组预定义的应用。  为此，需创建 Windows 10 设备限制配置文件并设置展台设置。

展台模式支持两种模式：“单应用”模式（仅允许用户运行一个应用）或“多应用”模式（允许访问多个应用）。  可定义用户帐户和设备名，确定受支持的应用。  用户登录时，仅可访问定义的应用。  有关详细信息，请参阅 [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)。 

展台模式要求：

- MDM 机构必须是 Intune。
- 必须已在目标设备上安装应用。
- 设备必须[正确预配](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions)。

#### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>用于创建网络边界的新设备配置文件<!-- 1311967 -->   
名为“网络边界”的新设备配置文件与其他设备配置文件可以位于同一位置。 使用此配置文件定义要视为公司资源和受信任资源的在线资源。 必须先为设备定义网络边界，然后才能在设备上使用 Windows Defender 应用程序防护和 Windows 信息保护等功能。 仅可为每个设备定义一个网络边界，这一点非常重要。

可以定义可信任的企业云资源、IP 地址范围和内部代理服务器。 定义后，Windows Defender 应用程序防护和 Windows 信息保护等功能即可使用网络边界。

####  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Windows Defender 防病毒软件的两个其他设置<!-- 1338409 -->  
**文件阻止级别**

| | |
|---|---|
| 未配置 | “未配置”使用 Windows Defender 防病毒软件的默认阻止级别，并提供强大的检测功能而不会增加检测出合法文件的风险。 |
| 高 | “高”级别执行级别较高的检测。
| 高 +  | “高 +”级别执行“高”级别检测，同时采取额外的保护措施，但可能会影响客户端性能。
| 零容差  | “零容差”可阻止所有未知的可执行文件。 |

级别设置为“高”可能导致检测出一些合法文件，但出现此情况的可能性不大。
建议将文件阻止级别设置为默认级别，即“未配置”。

**云扫描文件的超时延长**  

| | |
|--|--|
| 秒数 (0 - 50) | 指定等待云返回结果时，Windows Defender 防病毒软件应阻止文件的最长时间。 默认值为 10 秒：此处指定的任意额外时间（最多 50 秒）都将与这 10 秒相加。 大多数情况下，扫描所需的时间远少于最大值。 延长时间可使云对可疑文件进行全面调查。 建议启用此设置，并至少指定 20 秒的延长时间。 |

#### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>添加了适用于 Windows 10 设备的 Citrix VPN<!-- 1512457 -->  
可为 Windows 10 设备配置 Citrix VPN。 为 Windows 10 或更高版本配置 VPN 时，可在“基础 VPN”边栏选项卡中的“选择连接类型”列表中选择“Citrix VPN”。

> [!Note]
> 适用于 iOS 和 Android 的 Citrix 配置已存在。

#### <a name="wi-fi-connections-support-pre-shared-keys-on-ios----1550823---"></a>iOS 上的 Wi-Fi 连接支持预共享密钥<!-- 1550823 -->
客户可配置 Wi-Fi 配置文件，以便在 iOS 设备上为“WPA/WPA2 个人”连接使用预共享密钥 (PSK)。 当设备在 Intune 中注册时，这些配置文件将被推送至用户的设备。

当配置文件推送到设备时，下一步采取何种操作取决于配置文件的配置。  如果设置为自动连接，则它将在下一次需要网络时执行自动连接。  如果手动连接配置文件，则用户必须手动激活连接。  

### <a name="intune-apps"></a>Intune 应用

#### <a name="access-to-managed-app-logs-for-ios----1469920---"></a>访问 iOS 的托管应用日志<!-- 1469920 -->
安装了 Managed Browser 的最终用户现在可查看所有 Microsoft 已发布应用的管理状态，并可针对托管 iOS 应用的疑难问题发送日志。

若要了解如何在运行于 iOS 设备上的 Managed Browser 中启用疑难解答模式，请参阅[如何在 iOS 上使用 Managed Browser 访问托管应用日志](app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios)。

#### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>在适用于 iOS 的公司门户（版本 2.9.0）中对设备设置工作流的改进<!-- 1417174 -->

改进了适用于 iOS 的公司门户应用中的设备设置工作流。 语言对用户更加友好，在可能的情况下我们还对屏幕进行了合并。 通过在整个设置文本中使用公司名称使语言特定于你的公司。 可以在 [应用 UI 的新增功能](whats-new-app-ui.md)页上看到此更新的工作流。

### <a name="monitor-and-troubleshoot"></a>监视和故障排除

#### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>用户实体包含数据仓库数据模型中的最新用户数据 <!-- 1544273 -->
Intune 数据库仓库数据模型的第一个版本只包含 Intune 的最近历史数据。 报表制作者无法捕获用户的当前状态。 在此更新中，用户实体将包含最新用户数据。


## <a name="notices"></a>通知

### <a name="plan-for-change-new-windows-10-setting-for-kiosk-configuration-in-intune----1560072---"></a>更改计划：Intune 中新增用于 Kiosk 配置的 Windows 10 设置<!-- 1560072 -->
我们会在 Intune Azure 门户中对配置 Windows 10 1709 及更高版本（RS3 及更高版本）的方式和位置进行调整。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？ 
我们的记录表明你正在使用“Windows 10”>“设备限制”>“Kiosk(预览版)”设置。 我们会在五月将 UI 中的这一设置重命名为“Windows 10”>“设备限制”>“Kiosk(已过时)”，以表示不推荐使用此设置。 但是，在 Intune 的六月更新前此设置仍然可用。 六月之后，它会在后端中被设为已过时，无法再使用。 我们将在五月发布一个新的设备配置文件：“Windows 10”>“Kiosk”，其中包含了在 Windows 10 RS4 及更高版本上配置 Kiosks 所需的设置。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？  
Intune 将在五月底前后发布五月服务更新，届时，我们会为你提供说明，你可以根据该说明测试和验证你是否能将 Kiosk 配置从 Windows 10 RS3 迁移到 Windows 10 RS4。 使用这些说明将设备配置为 Kiosks 并让其使用 Kiosks 适用的新设备配置文件。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
此更改将同时影响 Intune 独立版客户和混合版（带 Configuration Manager 的 Intune）客户。 此集成将有助于简化云管理。 当前在 Azure 中，只可转到一个边栏选项卡（Intune 边栏选项卡）来管理组、策略、应用以及任何移动设备管理。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
请将 Intune 标记为收藏（而不是“Intune 应用保护服务”边栏选项卡），并确保熟悉 Intune 的“移动应用”边栏选项卡中的应用保护策略工作流。 我们将重定向一小段时间，然后删除“应用保护”边栏选项卡。 请记住，所有应用保护策略都已转到 Intune，可按照此处的文档操作，修改任何条件访问策略：[https://aka.ms/azuread_ca](https://aka.ms/azuread_ca)。

其他信息：[https://aka.ms/intuneapppolicy](https://aka.ms/intuneapppolicy)

### <a name="plan-for-change-change-in-support-for-the-microsoft-intune-app-sdk-for-cordova-plugin"></a>计划更改：更改对 Microsoft Intune App SDK for Cordova 插件的支持
Intune 对 [Microsoft Intune App SDK Cordova](app-sdk-cordova.md) 插件的支持于 2018 年 5 月 1 日结束。 建议改为使用 Intune App Wrapping Tool 准备基于 Cordova 的应用，以实现 Intune 中的可管理性和可用性。 此更改生效时，将不再维护 Microsoft Intune APP SDK for Cordova 插件，也不接收更新。 应用开发者将不能使用此插件。 Intune 计划继续支持使用 Cordova 构建的应用。 但使用 Microsoft Intune APP SDK for Cordova 插件构建的任何应用在 Intune 中都会减少功能。 使用 Intune App Wrapping Tool 包装后，应用可以照常部署给最终用户。 针对基于 Cordova 且发布到 Google Play 商店的 Android 应用：
- 最终用户首次启动时，系统会提示其输入凭据以接收 Intune 策略。
- 应用应被发布到面向 Intune 用户的应用商店，例如“Contoso App for Intune”。

有关 App Wrapping Tool 的详细信息，请参阅 [App Wrapping Tool for iOS](app-wrapper-prepare-ios.md) 和 [App Wrapping Tool for Android](app-wrapper-prepare-android.md)。 如有任何问题或疑问，请联系 [msintuneappsdk@microsoft.com](mailto:msintuneappsdk@microsoft.com)。

### <a name="plan-for-change-use-intune-on-azure-now-for-your-mdm-management----1227338---"></a>更改计划：立刻使用 Azure 上的 Intune 进行 MDM 管理<!-- 1227338 -->
一年前，我们推出了 [Azure 上 Intune 的公共预览版](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/)，六个月前，我们推出了 Intune [新管理员体验的正式版](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/)。 自 2018 年 8 月 31 日起，我们将面向使用 Intune 独立版的客户关闭经典 Silverlight 控制台中的移动设备管理 (MDM)。 但客户可以使用 [Azure 上的 Intune](https://aka.ms/Intune_on_Azure) 满足 MDM 需求。 如果仍在使用经典控制台进行 MDM，请停止此做法并开始熟悉 Azure 上的 Intune。 我们不希望任何最终用户受到此次更改的影响。 Silverlight 中将保留经典电脑管理。 可在[此处](https://aka.ms/Intune_on_Azure_mdm)详细了解此次更改及其带来的影响。

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接访问 Apple 注册方案<!--951869-->
对于在 2017 年 1 月之后创建的 Intune 帐户，Intune 支持在 Azure 门户中使用注册设备工作负荷直接访问 Apple 注册方案。 以前，只能通过 Intune 经典门户中的链接访问 Apple 注册预览版。 2017 年 1 月之前创建的 Intune 帐户需要进行一次性迁移，然后才能使用 Azure 中的这些功能。 迁移的计划目前尚未公布，但详细信息将尽快发布。 如果现有帐户无法访问 Azure 门户，强烈建议创建一个试用帐户测试新体验。

## <a name="whats-coming"></a>即将推出

### <a name="local-device-security-option-settings----1251887---"></a>本地设备安全选项设置 <!-- 1251887 -->
可以使用新的“本地设备安全选项”设置在 Windows 10 设备上启用安全设置。 创建 Windows 10 设备配置策略时，可以在终结点保护类别中查找这些设置。

### <a name="new-user-experience-update-for-the-company-portal-website---2000968--"></a>公司门户网站的新用户体验更新<!--2000968-->

我们将于 4 月引入新的公司门户网站体验，带来 UI 更新、简化的工作流和辅助功能改进。 这将包括应用共享等客户驱动的增强功能和改进的整体性能，以便带来更为用户友好的体验。
我们根据客户反馈添加了一些新功能，这些功能将显著提高现有功能和可用性：

-   整个网站的 UI 改进
-   共享指向应用的直接链接的功能
- 改善了大型应用目录的性能

不需要执行任何操作，即可准备好迎接此更改。 更新后的公司门户网站可访问后，我们会通知你。 但是，最终可能需要使用更新后的屏幕截图更新最终用户文档。 请注意，可能还需要更新 iOS 公司门户应用的文档，因为网站驱动 iOS 应用的“应用”部分。 可在[应用 UI 中的新增功能](whats-new-app-ui.md)页上查看此更新的示例图像。

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 将要求更新应用传输安全<!--748318-->
Apple 宣布他们将强制对应用程序传输安全 (ATS) 实施特定要求。 使用 ATS 对所有通过 HTTPS 的应用通信实施更严格的安全措施。 此更改会影响使用 iOS 公司门户应用的 Intune 客户。 我们将在 [Intune 支持博客](https://aka.ms/compportalats)中介绍详细信息。



## <a name="see-also"></a>另请参阅
* [Microsoft Intune 博客](http://go.microsoft.com/fwlink/?LinkID=273882)
* [云平台路线图](https://www.microsoft.com/cloud-platform/roadmap)
* [What's new in the Company Portal UI](whats-new-app-ui.md)（公司门户 UI 新增功能）
* [前几个月的新增功能](whats-new-archive.md)
