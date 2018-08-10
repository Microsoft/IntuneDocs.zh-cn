---
title: 早期版本
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ab6c808fc860491ddece5751983071d40864c8dd
ms.sourcegitcommit: 8f68cd3112a71d1cd386da6ecdae3cb014d570f2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2018
ms.locfileid: "39575077"
---
# <a name="the-early-edition-for-microsoft-intune---august-2018"></a>Microsoft Intune 的早期版本 - 2018 年 8 月

> [!Note]
> NDA 通知：下面的 Intune 更改仍处于开发阶段。 此信息在 NDA 下共享，但具有严格限制。 请勿在 Twitter、UserVoice、Reddit 等社交媒体或公共网站上发布此信息。 

早期版本提供了一份即将发布的 Microsoft Intune 版本中将出现的功能列表（在 NDA 下共享）。 此信息的提供具有条件限制，并且会不断变化。 请勿发布推文、在 UserVoice 上发帖，或者以其他方式在公司外部共享此信息。 此处列出的某些功能有无法按期发布的风险并可能推迟到以后的版本。 正在以试验模式（外部测试）测试其他功能，以确保它们可立即供客户使用。 如果有任何问题或顾虑，请与 Microsoft 产品组联系人联系。

本页将定期更新。 返回查看其他更新。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure 门户中的 Intune

<!-- 1808 start -->

### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>Windows Hello 面向用户和设备 <!-- 1106609 -->
创建 [Windows hello 企业版](windows-hello.md)策略后，该策略会应用到组织中的所有用户（租户范围）。 进行此更新后，还可使用设备配置策略（“设备配置” > “配置文件” > “创建配置文件” > “标识保护” > “Windows Hello 企业版”），将此策略应用于特定用户或特定设备。

在 Intune Azure 门户中，Windows Hello 配置和设置同时存在于“设备注册”和“设备配置”中。 **设备注册**面向整个组织（租户范围内），并支持 Windows AutoPilot (OOBE)。 **设备配置**面向使用某种策略的设备和用户，该策略会在签入期间应用。

适用于：  
- Windows 10 及更高版本
- Windows Holographic for Business

### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>在 Windows 10 和更高版本的设备上控制 S 模式 - 公共预览版 <!-- 1958649 -->
可创建一个设备配置文件，用于将 Windows 10 设备从 S 模式下切换出来，或用于防止用户将设备从 S 模式下切换出来。 此功能的位置：Intune >“设备配置” > “配置文件” >  “Windows 10 及更高版本” > “版本升级和模式切换”。
[S 模式下的 Windows 10 简介](https://www.microsoft.com/windows/s-mode)提供了有关 S 模式的详细信息。
适用于：Windows 10 及更高版本（1809 及更高版本）

### <a name="modern-vpn-support-updates-for-ios----2459928-1819876-and-2650856---"></a>适用于 iOS 的新式 VPN 支持更新 <!-- 2459928, 1819876, and 2650856 -->
未来的某个更新将支持以下 iOS VPN 客户端： 
- F5 Access（版本 3.0.1 及更高版本）
- Citrix SSO
- Palo Alto Networks GlobalProtect（版本 5.0 及更高版本） 在未来的某个更新中：
- 现有 **F5 Access** 连接类型将重命名为 **F5 Access (旧)**（按 F5 品牌更新）
- 现有 **Palo Alto Networks GlobalProtect** 连接类型将重命名为**旧版 Palo Alto Networks GlobalProtect**（按 Palo Alto 品牌更新）。 

使用这些连接类型的现有配置文件将继续使用旧的 VPN 客户端。 如果要将 Cisco 旧式 AnyConnect、F5 Access (旧)、Citrix VPN 或旧版 Palo Alto Networks GlobalProtect 与 iOS 配合使用，应改为使用新应用。 尽快执行此操作以确保可在更新到 iOS 12 的 iOS 设备上实现 VPN 访问。

### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in---1067692---"></a>将公司门户锁定在单应用模式下，直至用户登录 <!--1067692 --> 
如果在 DEP 注册过程中通过公司门户而非“设置助手”来对用户进行身份验证，可选择在单应用模式下运行公司门户。 此选项会在“设置助手”操作完成后立即锁定设备，这样用户须登录才能访问设备。 此过程可确保设备完成载入，且不会进入无任何用户绑定的孤立状态。

### <a name="scope-tags-for-policies---1081974-eeready--"></a>策略的作用域标记 <!--1081974 eeready-->

可创建作用域标记来限制对 Intune 资源的访问。 将作用域标记添加到某个角色分配，然后将作用域标记添加到某个配置文件。 角色将仅有权访问符合后列条件的资源：其资源配置文件的作用域标记与角色标记匹配或无作用域标记。
若要创建作用域标记，选择“Intune 角色” > “作用域(标记)” > “创建”。
要向角色分配添加作用域标记，选择“Intune 角色” > “所有角色” > “策略和配置文件管理器” > “分配” > “作用域(标记)”。
要向配置文件添加作用域标记，选择“设备配置” > “配置文件”>“选择配置文件”>“属性” > “作用域(标记)”。

### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device---1346521---"></a>为 AutoPilot 设备分配一个用户和友好名称 <!--1346521 -->
未来的一个公共预览版将允许管理员将用户分配到单个 Autopilot 设备。  在使用 Autopilot 为用户设置设备时，管理员还可提供友好名称来问候用户。

适用于：Windows 预览体验计划 1809 版或更高版本（预览版）。

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>另一个 MDM 使用的 Apple VPP 令牌 <!-- 1488946 -->
Intune 会检测是否 Intune 和另一个 MDM 同时在使用同一个 Apple 批量采购计划 (VPP) 令牌，并显示相关详细信息。

### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types----1520957---"></a>针对自定义和 Pulse Secure 连接类型的 iOS 每应用 VPN 配置文件的数据包隧道支持 <!-- 1520957 -->
如果使用 iOS 每应用 VPN 配置文件，可使用应用层隧道（应用-代理）或数据包级别隧道（数据包-隧道）。 这些选项适用于以下连接类型：
- 自定义 VPN
- Pulse Secure - 如果不确定使用哪个值，请查阅 VPN 提供商的文档。
适用于：iOS

### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858-eeready---"></a>Zscaler 是适用于 iOS 上 VPN 配置文件的可用连接 <!-- 1769858 eeready -->
创建 iOS VPN 设备配置文件时（“设备配置” > “配置文件” > “创建配置文件” > “iOS”“平台”>“VPN 配置文件类型”），有几种连接类型，包括 Cisco、Citrix 等。 未来的一个更新中会将 Zscaler 添加为一个连接类型。 
[运行 iOS 的设备的 VPN 设置](vpn-settings-ios.md)列出了可用的连接类型。

### <a name="block-windows-personal-device-enrollments----1849498---"></a>阻止 Windows 个人设备注册 <!-- 1849498 -->
可通过 Intune 中的[移动设备管理](windows-enroll.md)阻止 Windows 个人设备进行注册。 无法使用此功能阻止注册了 [Intune PC 代理](manage-windows-pcs-with-microsoft-intune.md)的设备。
若要查看此功能，请选择“设备注册” > “设备限制”。
启用此限制不会影响已注册的设备。
启用限制后，Intune 将进行检查以确保每个新 Windows 注册请求已授权为企业注册。 如果符合以下条件，则视为已授权为企业注册：
- 注册用户使用的是[设备注册管理员帐户]( device-enrollment-manager-enroll.md)。

- 设备通过 [Windows AutoPilot](enrollment-autopilot.md) 进行注册。
- 设备的 IMEI 号在“设备注册” > “[公司设备标识符]( corporate-identifiers-add.md)”中列出）。
- 设备通过[批量预配包](windows-bulk-enroll.md)进行注册。
- 设备通过[从 SCCM 自动注册以进行共同管理](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview#how-to-configure-co-management)进行注册。
将阻止未经授权的注册。
以下注册被 Intune 标记为企业注册，但由于其不提供 Intune 管理员每设备控制而将被阻止：
- 通过 [Windows 设置过程中的 Azure Active Directory 加入](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx.md)实现的[自动 MDM 注册](windows-enroll.md#enable-windows-10-automatic-enrollment)。
- 通过 [Windows 设置中的 Azure Active Directory 加入](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx.md)实现的[自动 MDM 注册](windows-enroll.md#enable-windows-10-automatic-enrollment)。
以下个人注册方法也将被阻止：
- 通过[从 Windows 设置中添加工作帐户](https://docs.microsoft.com/azure/active-directory/user-help/device-management-azuread-registered-devices-windows10-setup)实现的[自动 MDM 注册](windows-enroll.md#enable-windows-10-automatic-enrollment)。

- 通过 Windows 设置中的[仅 MDM 注册]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device)选项。

### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>在 AutoPIlot 配置文件中指定计算机名称模式 <!--1849855-->
可指定一个计算机名称模板，用于在 AutoPilot 注册过程中生成和设置[计算机名](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp)。 需要在 AutoPilot 配置文件中指定此模板，该文件位于“设备注册” > “Windows 注册” > “Windows Autopilot 部署服务” > “配置文件”。 仅可使用字母数字字符和连字符。
适用于：Windows 预览体验计划 1809 版或更高版本（预览版）。

### <a name="ios-version-number-and-build-number-are-shown----1892471---"></a>显示 iOS 版本号和生成号 <!-- 1892471 -->
在“设备符合性” > “设备符合性”中，会显示 iOS 操作系统版本。 在未来的某个更新中，会显示生成号。
Apple 每次发布安全更新时，会保留版本号，更新生成号。 通过所显示的生成号，可轻松确认是否已安装漏洞更新。

### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>对于 Windows AutoPilot 配置文件，隐藏公司登录页和域错误页上的“更改帐户”选项 <!--1901669 -->
公共预览版包含新的 Windows AutoPilot 配置文件选项，允许管理员隐藏公司登录页和域错误页上的“更改帐户”选项。 要隐藏这些选项，需在 Azure Active Directory 中配置公司品牌。 适用于：Windows 预览体验计划 1809 版或更高版本（预览版）。

### <a name="delay-when-ios-software-updates-are-shown-on-the-device----1949583---"></a>延迟 iOS 软件更新在设备上的显示时间 <!-- 1949583 -->
在 Intune >“软件更新” > “适用于 iOS 的更新策略”中，可配置不希望设备安装任何更新的日期和时间段。 在未来的某个更新中，可延迟软件更新在设备上的显示时间（1-90 天）。 
[在 Microsoft Intune 中配置 iOS 更新策略](software-updates-ios.md)列出了当前设置。

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>“设备符合性仪表板”中的停用设备 <!-- 1981119 -->
未来的某个更新将从设备符合性仪表板中删除已停用的设备。 这会改变符合性数字。

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>公司门户网站的新用户体验更新<!--2000968 -->
将根据客户的反馈向公司门户网站添加新功能。 可从 Android、iOS 和 Windows 设备上体验到现有功能和可用性方面的重大改进。 该网站的各个区域（如设备详细信息、反馈与支持以及设备概述）都采用了全新的现代化快速响应设计。 你还会看到：
- 简化了所有设备平台上的工作流
- 改进了设备识别和注册流
- 提供了更多有用的错误消息
- 语言更加友好，减少了技术术语的使用
- 共享指向应用的直接链接的功能
- 改善了大型应用目录的性能
- 为所有用户增加了辅助功能

### <a name="office-365-proplus-version----2213968-eeready---"></a>Office 365 专业增强版 <!-- 2213968 eeready -->
如果使用 Intune 将 Office 365 专业增强版应用分配到 Windows 10 设备，可选择 Office 的版本。 在 Azure 门户中，选择“Microsoft Intune” > “应用” > “添加应用”。 然后，从“类型”下拉列表中选择“Office 365 专业增强版套件(Windows 10)”。 选择“应用套件设置”以显示关联的边栏选项卡。 将“更新通道”设置为一个值，如“每月”。 （可选）选择“是”，从最终用户设备中删除其他版本的 Office (msi)。 选择“特定”，在最终用户设备上为所选通道安装特定的 Office 版本。 此时，可选择要使用的“特定版本”的 Office。 可用版本会随时间发生变化。 因此，在创建新部署时，可用版本可能为更新的版本，而不再提供某些较旧版本。 当前部署会继续部署旧版本，但版本列表会持续按通道更新。 有关详细信息，请参阅 [Office 365 专业增强版的更新频道概述](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)。

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>将配置文件配置为在“设置助手”期间跳过某些屏幕 <!-- 2276470 -->
创建 macOS 注册配置文件时，可将其配置为在用户使用设置助手期间跳过以下任一屏幕：
- Android 迁移
- 显示基调
- 隐私
- iCloudStorage

### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>本地连接器更新过程的更改 <!-- 2277554 -->
将根据客户反馈更改本地连接器的更新方式。 初次安装本地连接器之后，会自动对其进行更新。 此更改首先应用于适用于 Microsoft Intune 的全新 PFX 证书连接器，随后会推广至其他类型的本地连接器。 

### <a name="support-for-register-dns-setting-for-windows-10-vpn----2282852---"></a>支持面向 Windows 10 VPN 的“注册 DNS”设置 <!-- 2282852 -->
可将 Windows 10 VPN 配置文件配置为使用内部 DNS 动态注册分配给 VPN 接口的 IP 地址，而无需使用自定义配置文件。
[Windows 10 VPN 设置](vpn-settings-windows-10.md)列出了当前可用的 VPN 配置文件设置。 

### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-for-work-devices----2451462---"></a>限制应用，并阻止对 iOS for Work 和 Android for Work 设备上公司资源的访问 <!-- 2451462 -->
在“设备符合性” > “策略” > “创建策略” > “Android for Work” > “系统安全”中，有一个全新的“受限制的应用程序”设置。 如果设备上安装了某些应用，此新设置会使用符合性策略来阻止对公司资源的访问。 除非从设备中删除受限制的应用，否则设备会一直被视为不符合要求。
适用于： 
- iOS

### <a name="export-azure-classic-portal-compliance-policies-to-csv-file----2469637---"></a>将 Azure 经典门户符合性策略导出到 .csv 文件 <!-- 2469637 -->
将弃用 Azure 经典门户中创建的符合性策略。  在此情况下，可查看和删除任何现有策略，但无法更新它们。 可将策略导出为逗号分隔的文件（.csv 文件）。 然后使用文件中的详细信息在 Intune Azure 门户中重新创建这些策略。
> [!IMPORTANT]
> Azure 经典门户停用后，无法访问策略，也无法看到策略。 因此，务必导出策略，并在 Azure 经典门户停用之前，在 Azure 门户中重新创建这些策略。

<!-- 1807 start -->

### <a name="more-sync-opportunities-in-the-company-portal-app-for-windows----2683177---"></a>适用于 Windows 的公司门户应用中的更多同步机会 <!-- 2683177 -->
适用于 Windows 的公司门户应用即将向 Windows 任务栏和“开始”菜单跳转列表添加设备同步操作。 单击两个位置之一，即可快速同步设备，并获取对公司资源的访问权限。  

### <a name="reset-device-passcodes-from-company-portal-app-for-windows-10----2101282---"></a>从适用于 Windows 10 的公司门户重置设备密码 <!-- 2101282 --> 
员工很快就可以直接从 Windows 10 的公司门户应用重置其设备的 PIN 或密码。 此功能将在支持重置密码的远程和本地 Intune 管理的设备上提供。 根据设备类型，对远程设备的请求将删除设备的当前密码或创建临时密码。 请求重置本地设备的用户将重定向到设备的“设置”应用。  

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows----2317227---"></a>适用于 Windows 的公司门户应用中的新浏览体验<!-- 2317227 -->  
在适用于 Windows 的公司门户应用中浏览或搜索应用时，用户将能在现有的“磁贴”视图和新添加的“详细信息”视图之间切换。 新视图列出应用程序详细信息，如名称、发布服务器、发布日期和安装状态。  

“应用”页将介绍“已安装的”视图，通过该视图可查看已完成和正在进行的应用安装的详细信息。 想分享有关新变化的反馈或想法吗？ 请在公司门户应用中向我们发送反馈。

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>针对设备注册管理员用户，改进了公司门户应用体验 <!-- 675800 -->
当设备注册管理员 (DEM) 登录到适用于 Windows 的公司门户应用时，该应用将仅列出 DEM 的当前正在运行的设备。 此改进将减少以前应用尝试加载所有 DEM 注册设备时出现的超时。  

### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>在 DEP 注册期间，使用 VPP 设备许可证预先设置公司门户 <!-- 1608345 -->
在设备注册计划 (DEP) 注册期间，可以使用批量采购计划 (VPP) 设备许可证预先设置公司门户。 若要完成此操作，在创建或编辑注册配置文件时，指定要用于安装公司门户的 VPP 令牌。 请确保令牌没有过期，并且具有足够的公司门户应用许可证。 如果令牌过期或许可证用完，Intune 将改为推送 App Store 公司门户（这将提示输入 Apple ID）。

###  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Windows 业务线 (LOB) 应用文件扩展名 <!-- 1884873 -->
Windows LOB 应用的文件扩展名现在包括 .msi、.appx、.appxbundle、.msix 和 .msixbundle。 可以在 Microsoft Intune 中添加应用，方法是通过选择“移动应用” > “应用” > “添加”。 将显示“添加应用”窗格，可选择“应用类型”。 对于 Windows LOB 应用，选择“业务线”应用作为应用类型，选择“应用包文件”，然后输入带有扩展名的安装文件。

### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Windows Defender ATP 配置包自动添加到配置文件 <!-- 2144658 -->
在 Intune 中使用[高级威胁防护和加入](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile)设备时，下载配置包，并将其添加到配置文件。 在未来的更新中，Intune 自动从 Windows Defender 安全中心获取包，并将其添加到配置文件。

适用于 Windows 10 和更高版本。

### <a name="check-for-sccm-compliance----2192052---"></a>检查 SCCM 符合性 <!-- 2192052 -->
未来的更新将包括新的 System Center Configuration Manager (SCCM) 符合性设置（“设备符合性” > “策略” > “创建策略” > “Windows 10”。 SCCM 向 Intune 符合性发送信号。 使用 Intune 设置，可以要求所有 SCCM 信号都返回“符合”。

例如，要求所有软件更新都安装在设备上。 在 SCCM, 中，此要求具有“已安装”状态。 如果设备上的任何计划都处于未知状态，则此设备在 Intune 中不兼容。

适用于 Windows 10 及更高版本

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>针对即将过期的 VPP 令牌或公司门户许可证不足的警报 <!-- 2237572 -->
如果在 DEP 注册期间使用批量采购计划 (VPP) 预先设置公司门户，则在 VPP 令牌即将过期以及公司门户的许可证不足的情况下，Intune 将发出警报。

### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>需要确认才能删除正用于公司门户预先设置的 VPP 令牌 <!-- 2237634 -->
如果在 DEP 注册期间正在使用批量购买计划 (VPP) 预先设置公司门户，则需要确认是否删除此令牌。

#### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Windows Installer 的其他安全设置 <!-- 2282430 -->
可允许用户控制应用安装。 如果启用，则允许因安全冲突而停止的安装继续进行。 当 Windows Installer 在系统上安装任何程序时，可指示它使用提升的权限。 此外，将能够对 Windows 信息保护 (WIP) 项目编制索引，并将有关这些项目的元数据存储在未加密的位置。 禁用策略后，将不会对受 WIP 保护的项编制索引，也不会在 Cortana 或文件资源管理器的结果中显示这些项。 默认情况下将禁用这些选项的功能。 

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>可通过 iOS 上的 APP 设置阻止第三方键盘 <!-- 1248481 -->
在 iOS 设备上，Intune 管理员可以阻止使用第三方键盘在受策略保护的应用中访问组织数据。 当应用程序保护策略 (APP) 设置为阻止第三方键盘时，设备用户将在首次使用第三方键盘与公司数据交互时收到一条消息。 将阻止本地键盘以外的所有选项都，设备用户不会看到它们。 设备用户只会看到一次对话消息。 

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>在应用启动和超时时要求输入非生物识别密码 <!-- 1506985 -->

在应用启动时和管理员指定的超时时长后要求输入非生物识别密码，Intune 会限制使用生物识别来访问公司数据，从而为启用了移动应用程序管理 (MAM) 的应用提升安全性。 这些设置将影响依靠 Touch ID (iOS)、Face ID (iOS)、Android Biometric 或其他未来生物识别身份验证方法访问启用了 APP/MAM 的应用程序的用户。 这些设置将使 Intune 管理员能够更精细地控制用户访问，让带有多个指纹或其他生物识别访问方法的设备只能向正确的用户显示公司数据。 在 Azure 门户中，打开“Microsoft Intune”。 选择“移动应用” > “应用保护策略” > “添加策略” > “设置”。 找到特定设置的“访问”部分。

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus 语言包 <!-- 1833450 -->
作为 Intune 管理员，你将能够为通过 Intune 管理的 Office 365 Pro Plus 应用部署其他语言。 可用语言列表包括语言包的“类型”（核心、部分和校对）。 在 Azure 门户中，选择“Microsoft Intune” > “移动应用” > “应用” > “添加”。 在“添加应用”边栏选项卡的“应用类型”列表中，选择“Office 365 套件”下的“Windows 10”。 在“应用套件设置”边栏选项卡中选择“语言”。

### <a name="preview-a-new-user-experience-update-for-the-company-portal-website---2000968---"></a>预览公司门户网站的新用户体验更新<!--2000968 -->
我们根据客户的反馈向公司门户网站/iOS 应用目录添加新功能。 可从 Android、iOS 和 Windows 设备上体验到现有功能和可用性方面的重大改进。 该网站的各个区域（如设备详细信息、反馈与支持以及设备概述）都采用了全新的现代化快速响应设计。 你还会看到：

- 简化了所有设备平台上的工作流
- 改进了设备识别和注册流
- 提供了更多有用的错误消息
- 语言更加友好，减少了技术术语的使用
- 共享指向应用的直接链接的功能
- 改善了大型应用目录的性能
- 为所有用户增加了辅助功能

更新当前处于预览状态。 可以在 http://aka.ms/webcpflighting 注册以加入预览

<!-- 1805 start -->

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>在冷应用启动和超时时要求非生物识别密码 <!-- 1506985 --> 

在冷应用启动时和管理员指定的超时时长后要求输入非生物识别密码，Intune 会限制使用生物识别来访问公司数据，从而为启用了移动应用程序管理 (MAM) 的应用提升安全性。 这些设置将影响依靠 Touch ID (iOS)、Face ID (iOS)、Android Biometric 或其他未来生物识别身份验证方法访问启用了 APP/MAM 的应用程序的用户。 这些设置将使 Intune 管理员能够更精细地控制用户访问，让带有多个指纹或其他生物识别访问方法的设备只能向正确的用户显示公司数据。 在 Azure 门户中，打开“Microsoft Intune”。 选择“移动应用” > “应用保护策略” > “添加策略” > “设置”。 找到特定设置的“访问”部分。

<!-- 1803 start -->

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>可以将所需的业务线 (LOB) 应用部署到 Windows 10 桌面版设备上的所有用户 <!-- 1627835 RS4 -->
客户将能够部署所需的业务线 Windows 10 应用以安装在设备上下文中。 这将使这些应用可供此设备上的所有用户可用。 这仅适用于 Windows 10 桌面版设备。

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>更新适用于 Android 的公司门户应用上的“帮助和反馈”体验 <!--1631531 -->

将更新适用于 Android 的公司门户应用上的“帮助和反馈”体验以符合 Android 应用的最佳做法。 在未来的几个月里将更新适用于 Android 的公司门户应用，将“帮助和反馈”菜单项分为不同的“帮助”和“发送反馈”菜单项。 “帮助”页面将包含“常见问题”部分和“电子邮件支持”按钮，引导最终用户向 Microsoft 上传日志并向公司支持部门发送电子邮件以描述问题。 “发送反馈”将引导用户完成标准的 Microsoft 反馈提交，这将提示用户选择“我喜欢一些内容”、“我不喜欢一些内容”还是“我有个主意”。

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>应用保护策略<!-- 679615 -->
Intune 应用保护策略将提供创建默认全局策略的功能，以便快速对整个租户中所有用户启用保护。

<!-- the following are present prior to 1711 -->

## <a name="notices"></a>通知

此时没有任何活动通知。

### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。



