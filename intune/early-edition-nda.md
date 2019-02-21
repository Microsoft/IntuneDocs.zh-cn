---
title: 早期版本 - Microsoft Intune
titlesuffix: ''
description: Microsoft Intune 的早期版本
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/04/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19994745a232a362d6bba0f09ed3934e492a17ed
ms.sourcegitcommit: 2f431f122ce3ee6b5d0cdb04a0b748d00f83e295
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265666"
---
# <a name="the-early-edition-for-microsoft-intune---february-2019"></a>Microsoft Intune 的早期版本 - 2019 年 2 月

> [!Note]
> NDA 通知：下面的更改依据 Intune 开发。 此信息在 NDA 下共享，但具有严格限制。 请勿在 Twitter、UserVoice、Reddit 等社交媒体或公共网站上发布此信息。 

早期版本提供了一份即将发布的 Microsoft Intune 版本中将出现的功能列表（在 NDA 下共享）。 此信息的提供具有条件限制，并且会不断变化。 请勿发布推文、在 UserVoice 上发帖，或者以其他方式在公司外部共享此信息。 此处列出的某些功能有无法按期发布的风险并可能推迟到以后的版本。 正在以试验模式（外部测试）测试其他功能，以确保它们可立即供客户使用。 如果有任何问题或顾虑，请与 Microsoft 产品组联系人联系。

本页将定期更新。 返回查看其他更新。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure 门户中的 Intune
<!-- 1902 start-->

### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675----"></a>PowerShell 脚本可以在 64 位设备上的 64 位主机上运行<!-- 1862675  -->
将 PowerShell 脚本添加到设备配置概要文件时，该脚本始终以 32 位执行，即使在 64 位操作系统上也是如此。 通过此更新，管理员可以在 64 位设备上的 64 位 PowerShell 主机中运行该脚本（“设备配置” > “PowerShell 脚本” > “添加” > “配置” > “在 64 位 PowerShell 主机中运行脚本”）。
有关使用 PowerShell 的更多详细信息，请参阅 [Intune 中的 PowerShell 脚本](intune-management-extension.md)。
适用于：Windows 10 及更高版本

### <a name="rename-an-enrolled-windows-device----1911112----"></a>重命名已注册的 Windows 设备<!-- 1911112  -->
你将能够重命名已注册的 Windows 10 设备（RS4 或更高版本）。 若要执行此操作，请选择“Intune” > “设备” > “所有设备”> 选择设备 >“重命名设备”。

### <a name="assign-scep-certificates-to-a-userless-macos-device-------2340521-----"></a>将 SCEP 证书分配给无用户的 macOS 设备<!-- 2340521   -->
你可以将简单证书注册协议 (SCEP) 证书分配给无用户 macOS 设备，并将证书与 Wi-Fi 或 VPN 配置文件相关联。 这扩展了现有的支持，我们已向[运行 Windows、iOS 和 Android 的无用户设备分配证书](certificates-scep-configure.md#create-a-scep-certificate-profile)。

### <a name="intune-conditional-access-ui-update------2432313----"></a>Intune 条件访问 UI 更新<!-- 2432313  -->
我们正在对 Intune 控制台中条件访问的 UI 进行改进。 这些地方包括：
- 使用 Azure Active Directory 中的边栏选项卡替换 Intune“条件访问”边栏选项卡。 这将确保你可访问条件访问的所有设置和配置，这仍是 Azure AD 技术。
- 将“Exchange 服务连接器”设置重新定位到当前“本地访问”边栏选项卡。 我们还将该边栏选项卡重命名为“Exchange 访问”。 此更改将合并配置和监视与 Exchange 联机和本地相关的详细信息。

### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355----"></a>Intune 将在 Android 设备上使用 Google Play 保护 API<!-- 2577355  -->
某些 IT 管理员面临着 BYOD 情况，最终用户可能会使他们的手机获取 root 权限或越狱。 此行为虽然有时并非恶意，但会导致绕过许多 Intune 策略，这些策略是为了保护组织在最终用户设备上的数据而设置的。 因此，Intune 为已注册和未注册的设备提供 root 权限和越狱检测。 在此版本中，Intune 现在将利用 Google Play 保护 API 添加到我们对未注册设备的现有 root 权限检测检查。 虽然 Google 不会共享发生的所有 root 权限检测检查，但我们预期这些 API 能够检测出因设备自定义而导致设备获取 root 权限的用户，以及能够在旧设备上获得较新 OS 更新的用户。 然后，可以阻止这些用户访问公司数据，或者可以从其启用策略的应用中删除其公司帐户。 为了获得额外价值，IT 管理员现在将在 Intune 应用保护边栏选项卡中进行多次报告更新 -“已标记的用户”报告将显示通过 Google Play 保护的 SafetyNet API 扫描检测到的用户，“潜在有害应用”报告将显示通过 Google 的验证应用 API 扫描检测到的应用。 此功能在 Android 中可用。 

### <a name="win32-app-information-available-in-troubleshooting-blade----2617342------"></a>“故障排除”边栏选项卡显示的 Win32 应用信息<!-- 2617342    -->
你将能够从 Intune 应用“排除故障”边栏选项卡服务器收集 Win32 应用安装的失败日志文件。 有关应用安装排除故障的详细信息，请参阅[排查应用安装问题](troubleshoot-app-install.md)。

### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135----"></a>Kiosk Browser 和 Microsoft Edge 浏览器应用可以在展台模式下在 Windows 10 设备上运行<!-- 2935135  -->
可以在展台模式下使用 Windows 10 设备来运行一个应用或多个应用。 此更新包括在展台模式下使用浏览器应用的若干更改，包括：

- 添加 Microsoft Edge 浏览器或 Kiosk Browser 以在展台设备上作为应用程序运行（“设备配置” > “配置文件” > “新配置文件” > “Windows 10 及更高版本”（针对平台）>“展台”（针对配置文件类型））。
- 限制 Microsoft Edge 以便可以（或无法）以展台模式运行（“设备配置” > “配置文件” > “新配置文件” > “Windows 10 及更高版本”（针对平台）>“设备限制”（针对配置文件类型）>“Microsoft Edge 浏览器”）。 如果未在展台模式下运行，最终用户可以更改 Microsoft Edge 设置。

有关当前设置的列表，请参阅：

- [将 Windows 10 及更高版本设备作为展台运行的设置](kiosk-settings-windows.md)
- [Microsoft Edge 浏览器的设备限制](device-restrictions-windows-10.md#microsoft-edge-browser)

适用于：Windows 10 及更高版本

### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>将范围标记自动分配给具有该范围的管理员创建的资源<!-- 3173823  -->
管理员创建资源时，分配给管理员的任何范围标记都将自动分配给这些新资源。

### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774---"></a>适用于 iOS 和 macOS 设备的新设备限制设置<!-- 3448774 -->
你可以在运行 iOS 和 macOS 的设备上限制某些设置和功能（“设备配置” > “配置文件” > “新配置文件” > “iOS”或“macOS”（针对平台）>“设备限制”（针对配置文件类型））。 此更新添加了可以控制的更多功能和设置，包括设置屏幕时间、更改 eSIM 设置和蜂窝计划、延迟用户对软件更新的可见性、阻止内容缓存等。
若要查看可以限制的当前功能和设置，请参阅：
- [iOS 设备限制设置](device-restrictions-ios.md)
- [macOS 设备限制设置](device-restrictions-macos.md)

适用于：
- iOS
- macOS

### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202---"></a>“失败注册”报告将移至“设备注册”边栏选项卡<!-- 3560202 -->
“失败注册”报告将迁移到“设备注册”边栏选项卡的“监视”部分。 还添加了两个新列（“注册方法”和“OS 版本”）。

### <a name="change-kiosk-to-dedicated-devices----3598402----"></a>将“展台”更改为“专用设备”<!-- 3598402  -->
若要与 Android 术语保持一致，“展台”将更改为设备配置配置文件下的“专用设备”、“Android 企业” > “设备所有者” > “设备限制”。

### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850--3803313----"></a>Safari 和“延迟用户软件更新可见性”iOS 设置将移至 Intune UI<!-- 3640850, , 3803313  -->
对于 iOS 设备，可以设置 Safari 设置并配置软件更新。 在此更新中，这些设置将移至 Intune UI 的不同部分：

- Safari 设置将从“Safari”（“设备配置” > “配置文件” > “新配置文件” > “iOS”（针对平台）>“设备限制”（针对配置文件类型））移动到“内置应用”。 
- 受监督的 iOS 设备的“延迟用户软件更新可见性”设置（“软件更新” > “iOS 的更新策略”）将移至“设备限制” > “常规”。

有关当前设置的列表，请参阅 [iOS 设备限制](device-restrictions-ios.md)和 [iOS 软件更新](software-updates-ios.md)。

适用于： 
- iOS

### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164----"></a>在 iOS 设备上将设备设置中的启用限制重命名为屏幕时间<!-- 3699164  -->
可以在受监管的 iOS 设备上配置“设备设置中的启用限制”（“设备配置” > “配置文件” > “新配置文件” > “iOS”（针对平台）>“设备限制”（针对配置文件类型）>“常规”）。 在此更新中，此设置将重命名为“屏幕时间(仅监管模式)”。 操作是相同的。 具体而言： 

- iOS 11.4.1 及更早版本：“阻止”阻止最终用户在设备设置中设置自己的限制。 
- iOS 12.0 及更高版本：“阻止”阻止最终用户在设备设置中设置自己的“屏幕时间”，包括内容和隐私限制。 升级到 iOS 12.0 的设备将不再在设备设置中看到限制选项卡。 这些设置位于“屏幕时间”。 

有关当前设置的列表，请参阅 [iOS 设备限制](device-restrictions-ios.md)。

适用于： 
- iOS

### <a name="app-status-details-for-ios-apps----3761235----"></a>iOS 应用的应用状态详细信息<!-- 3761235  -->
将出现与以下内容相关的新应用安装错误消息：
- 在共享 iPad 上安装 VPP 应用失败
- 禁用 App Store 失败
- 未能找到应用的 VPP 许可证
- 无法使用 MDM 提供程序安装系统应用
- 设备处于丢失模式或展台模式时无法安装应用
- 用户未登录 App Store 时无法安装应用

在 Intune 中，选择“客户端应用” > “应用”>“应用名称”>“设备安装状态”。 “状态详细信息”列中将提供新的错误消息。

<!-- 1901 start -->

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>部署获得许可的适用于企业的 Microsoft Store 联机应用 <!-- 1672660  -->
你将能够在设备上下文中分配所需的适用于企业的 Microsoft Store 联机应用，这些应用已获得许可。 如果以这种方式部署适用于企业的 Microsoft Store 应用，则可在设备上为所有用户安装该应用。 这仅适用于 Windows 10 RS4+ 桌面版设备。 对于获得许可的适用于企业的 Microsoft Store 联机应用，可在客户端应用分配页面中选择安装在设备上下文中。

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android Enterprise APP-WE 应用部署 <!-- 1171203 -->
对于没有注册 (APP-WE) 部署方案的未注册应用保护策略中的 Android 设备，能够使用托管的 Google Play 将应用商店应用和 LOB 应用部署到用户。 具体而言，IT 管理员可以向最终用户提供应用目录以及不再需要最终用户通过允许从未知源进行安装来放宽其设备的安全状况的安装体验。 此外，此部署方案将改进最终用户体验。

### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Intune 策略更新身份验证方法和公司门户应用安装  <!-- 1927359 -->
在已通过 Apple 公司设备注册方法之一经由“设置助理”注册的设备上，Intune 将不再支持由最终用户从应用商店手动安装的公司门户。 仅当在注册过程中使用 Apple 设置助理进行身份验证时，此更改才适用。 此更改也只会影响通过以下方式注册的 iOS 设备：  
* Apple 配置器
* Apple Business Manager
* Apple School Manager
* Apple 设备注册计划 (DEP)

如果用户从应用商店安装公司门户应用，然后尝试通过该应用注册这些设备，则他们将收到错误。 在注册过程中由 Intune 自动推送公司门户时，这些设备应仅使用公司门户。 将更新 Azure 门户中的 Intune 注册配置文件，以便你可以指定设备的身份验证方式以及是否收到公司门户应用。 如果希望 DEP 设备用户具有公司门户，则需要在注册配置文件中指定你的首选项。 此外，公司门户应用中的“标识设备”屏幕很快就会过时。  
若要在已注册的 DEP 设备上安装公司门户，需要转到“Intune”>“客户端应用”，并将其作为具有应用配置策略的托管应用进行推送。 未来的文档中将详细概述执行这些步骤的方式。

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>管理模板为公共预览版，并移动到其自己的配置文件 <!-- 3322847 -->
Intune 中的管理模板（“设备配置” > “管理模板”）目前为个人预览版。 借助此更新：管理模板包括可在 Intune 中管理的大约 300 个设置。 以前，这些设置仅存在于组策略编辑器中。
管理模板现已推出公共预览版，管理模板从“设备配置” > “管理模板”移动到“设备配置” > “配置文件” >“创建配置文件”> 在“平台”中，选择“Windows 10 及更高版本”，在“配置文件类型”中，选择“管理模板”。
“已启用报告”适用于：Windows 10 及更高版本

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>Intune macOS 公司门户深色模式 <!-- 3300524 -->
Intune macOS 公司门户现在支持 macOS 的深色模式。 在 macOS 10.14+ 设备上启用深色模式时，公司门户将调整其外观以反映该模式的颜色。

<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>适用于 Web 数据的应用保护策略 (APP) 设置 <!-- 2662995 -->
将更新 Android 和 iOS 设备上适用于 Web 内容的应用策略设置，以更好地处理 http 和 https Web 链接，以及通过 iOS 通用链接和 Android 应用链接进行的数据传输。  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>另一个 MDM 使用的 Apple VPP 令牌 <!-- 1488946 -->
Intune 会检测是否 Intune 和另一个 MDM 同时在使用同一个 Apple 批量采购计划 (VPP) 令牌，并显示相关详细信息。

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>“设备符合性仪表板”中的停用设备 <!-- 1981119 -->
未来的某个更新将从设备符合性仪表板中删除已停用的设备。 这会改变符合性数字。

## <a name="notices"></a>通知

此时没有任何活动通知。

### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。
