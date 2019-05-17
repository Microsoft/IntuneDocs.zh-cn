---
title: 开发过程中 - Microsoft Intune
titleSuffix: ''
description: 开发过程中的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/15/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa38a684a32756d4f2c3be3b750f8e79b66e98f6
ms.sourcegitcommit: 8c795b041cd39e3896595f64f53ace48be0ec84c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2019
ms.locfileid: "59587376"
---
# <a name="in-development-for-microsoft-intune---april-2019"></a>在 Microsoft Intune 的开发中 - 2019 年 4 月

为了辅助就绪性和计划，此页面列出了正在开发但尚未发布的 Intune UI 更新和功能。 此外：

- 如果我们预计你需要在更改之前采取措施，我们将发布补充性的 Office 消息中心文章。
- 当某个功能在生产环境中推出时（无论是预览功能还是正式发布的功能），功能描述都将从此页移至[新增功能页](whats-new.md)。
- 此页和[新增功能页](whats-new.md)会定期更新。 返回查看其他更新。
- 有关策略性可交付内容和时间线，请参阅 [M365 路线图](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)。

> [!Note]
> 这些项目反映了 Microsoft 目前对将来版本中 Intune 功能的期望。 日期和各项功能可能会更改。 并非所有开发中的项目在此页上都有功能描述。

**RSS 源**：通过将以下 URL 复制并粘贴到源阅读器中，可以在页面更新时收到通知：`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure 门户中的 Intune

<!-- 1904 start-->

### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083---"></a>在 macOS 设备上设置登录设置和控制重启选项 <!-- 1210083 -->
在 macOS 设备上，可以创建设备配置文件（依次选择“设备配置” > “配置文件” > “创建配置文件” > 针对平台选择“macOS”> 针对配置文件类型选择“设备功能”）。 新的登录窗口设置将包括显示自定义横幅、选择用户登录方式、显示或隐藏电源设置等项。

若要查看当前设置，请转到 [macOS 设备功能设置](macos-device-features-settings.md)。

适用范围：macOS

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Windows Defender 防火墙的高级设置 <!-- 1311949 -->
你很快就可以使用 Intune 在客户端上管理 Windows Defender 的自定义防火墙规则。 规则可以指定应用程序、网络地址和端口的入站和出站行为。 

### <a name="require-app-protection-conditional-access----1634317---"></a>需要使用应用保护条件访问  <!--1634317 -->
你将能够使用“需要应用保护策略”，该策略确认策略在登录完成之前应用于用户的应用，以防止用户访问你使用条件访问保护的数据。 虽然策略保证可能会减慢首次使用体验，但它有助于防范网络问题、管理错误配置或避免故意破坏应用程序保护策略。 

### <a name="retire-noncompliant-devices----1827291---"></a>停用不合规的设备 <!-- 1827291 -->
我们将添加一个新的符合性操作来停用不符合要求的设备。 如果停用不符合要求的设备，则会从中删除所有公司数据，并且还会将设备从 Intune 管理中删除。 当达到配置的天数值时，此操作将运行。 最小值为 30 天。 

### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>在 macOS 设备上配置内核扩展的设置 <!-- 2043024 -->
在 macOS 设备上，可以创建设备配置文件（依次选择“设备配置” > “配置文件” > “创建配置文件”> 针对平台选择“macOS”）。 通过一组新设置，可在设备上配置和使用内核扩展。

适用于：10.13.2 及更高版本

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>将配置文件配置为在“设置助手”期间跳过某些屏幕 <!-- 2276470 -->
创建 macOS 注册配置文件时，可将其配置为在用户使用设置助手期间跳过以下任一屏幕：
- Android 迁移
- 显示基调
- 隐私
- iCloudStorage：如果你新建或编辑配置文件，选定跳过屏幕需要与 Apple MDM 服务器同步。 用户可以发起手动同步设备，这样在选取配置文件变更时就不会有任何延迟。
有关详细信息，请参阅[通过设备注册计划或 Apple School Manager 自动注册 macOS 设备](device-enrollment-program-enroll-macos.md)。

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>设备用户可以查看他们已安装或尝试安装的所有托管应用 <!-- 2352913 -->
Company Portal for Windows 将列出用户设备上安装的所有要求的和可用的托管应用。 用户将能够查看已尝试和待处理的应用安装及其当前状态。 如果组织未提供所需或可用的应用，则用户将看到一条消息，说明尚未安装任何公司应用。 用户还可以按安装状态对其应用进行排序或筛选。

### <a name="scope-tags-for-apple-vpp-tokens---2371886---"></a>Apple VPP 令牌的范围标记 <!--2371886 -->
你能够将范围标记添加到 Apple VPP 令牌。 只有分配有相同范围标记的用户才能访问带有该标记的 Apple VPP 令牌。 使用该令牌购买的 VPP 应用和电子书会继承其范围标记。 有关范围标记的详细信息，请参阅[使用 RBAC 和范围标记](scope-tags.md)。

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>在创建 Windows 10 设备配置配置文件时使用“适用性规则” <!-- 2549910 -->
创建 Windows 10 设备配置配置文件（“设备配置” > “配置文件” > “创建配置文件” > 适用于平台的“Windows 10”）。 你将能够创建“适用性规则”，使配置文件仅应用于特定版本。 例如，创建一个启用某些 BitLocker 设置的配置文件。 添加配置文件后，请使用适用性规则，使配置文件仅适用于运行 Windows 10 企业版的设备。

适用于： 
- Windows 10 及更高版本

### <a name="enable-win32-app-dependencies----2617348---"></a>启用 Win32 应用依赖项 <!-- 2617348 -->
公共预览版 - 管理员可以要求在安装 Win32 应用之前，将其他应用作为依赖项进行安装。 具体来说，设备必须先安装相关应用，再安装 Win32 应用。 只有在 Intune 管理代理升级为 1904 版本（1.18.120.0 之后的版本）后的一到两周才能使用应用依赖项功能。 在 Intune 中，选择“客户端应用” > “应用” > “添加”，以显示“添加应用”边栏选项卡。 选择“Windows 应用(Win32)”作为“应用类型”。 有关详细信息，请参阅 [Intune 独立版 - Win32 应用管理](apps-win32-app-management.md)。

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-connect-to-wi-fi-networks-on-android-enterprise-dedicated-devices-running-multi-app-kiosk-mode---3041940---"></a>针对 Android Enterprise，Device Owner 的新设备限制设置：让用户连接到运行多应用展台模式的 Android Enterprise 专用设备上的 Wi-Fi 网络 <!--3041940 -->
管理员能够切换新设置，使用户可以在运行多应用展台模式的 Android Enterprise 专用设备上配置蓝牙。 若要在 Intune 控制台中查看此设置，请选择“Intune” > “设备配置” > “配置文件” > “创建配置文件”> 选择适用于平台的“Android Enterprise”>“仅限设备所有者，配置文件类型的设备限制”>“设置” > “专用设备”> 选择“展台模式”设置下拉菜单中的“多应用”。 将启用名为“Wi-Fi 配置”的选项。 

适用范围：运行多应用展台模式的 Android 企业专用设备。 

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-configure-bluetooth-and-pairing-on-android-enterprise-dedicated-devices---3041941---"></a>Android Enterprise，Device Owner 新设备限制设置：允许用户在 Android Enterprise 专用设备上配置蓝牙和配对 <!--3041941 -->
管理员能够切换新设置，使用户可以在运行多应用展台模式的 Android Enterprise 专用设备上配置蓝牙。 若要在 Intune 控制台中查看此设置，请选择“Intune” > “设备配置” > “配置文件” > “创建配置文件”> 选择适用于平台的“Android Enterprise”>“仅限设备所有者，配置文件类型的设备限制”>“设置” > “专用设备”> 选择“展台模式”设置下拉菜单中的“多应用”。 将启用名为“蓝牙配置”的选项。 

适用范围：运行多应用展台模式的 Android Enterprise 专用设备。 

### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>监控安全基线状态（公共预览版） <!-- 3082047 --> 
当监视安全基线的“设备状态”时，视图将按基线类别组织状态，如“上述锁”、“BitLocker”和“浏览器”。 所有可用的基线类别将表示出来。 对于每个类别，你将看到有多少设备与特定基线类别不匹配、配置错误或不适用。

###  <a name="intune-security-tasks-for-defender-atp-in-public-preview----3208597---"></a>适用于 Defender ATP 的 Intune 安全任务（公共预览版） <!-- 3208597 -->
作为公共预览版，Intune 将很快为新发布的 Microsoft Defender 威胁和漏洞管理添加安全任务。  通过此集成，Windows Defender ATP (WDATP) 中的安全操作管理员可以更有效地向 Intune 管理员传达针对新兴威胁的建议修正措施。 添加安全任务操作增加了基于风险的方法来发现终结点漏洞和配置错误，并对其设置优先级和进行修正。

若要了解有关 Intune 中安全任务的详细信息，请参阅有关[使用 Intune 安全任务扩展 Microsoft Defender ATP 威胁和漏洞管理](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-security-tasks-extend-Microsoft-Defender-ATP-s/ba-p/369857)的博客文章。 

### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883---"></a>在 Intune 中创建和使用 OEMConfig 设备配置文件 <!-- 3305883 -->
Intune 将支持使用 OEMConfig 配置 Android Enterprise 设备。 具体来说，可以使用 OEMConfig 创建设备配置文件并将设置应用于 Android Enterprise 设备（依次选择“设备配置” > “配置文件” > “创建配置文件” >  针对平台选择“Android Enterprise”）。

对 OEM 的支持目前基于每个 OEM。 如果 OEMConfig 应用列表中未包含所需 OEMConfig 应用，请联系 `IntuneOEMConfig@microsoft.com`。

适用于： 
- Android Enterprise

### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254---"></a>针对 Android Enterprise 和设备所有者的新设备限制设置 <!-- 3574254 -->
在 Android Enterprise 设备上，可以创建设备限制配置文件，以允许或限制功能和设置密码规则等（依次选择“设备配置” > “配置文件” > “创建配置文件”> 针对平台选择“Android Enterprise”> 针对配置文件类型选择“仅限设备所有者”>“设备限制”）。 

新设置（包括密码设置）将推出，允许完全托管设备完全访问 Google Play 商店中的应用等。 

要查看设置的当前列表，请转到[用于允许或限制功能的 Android Enterprise 设备设置](device-restrictions-android-for-work.md)。 

适用范围：Android Enterprise 完全托管设备

### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>了解 Windows 10 设备合规性策略中的 TPM 芯片组 <!-- 3617671 -->
许多 Windows 10 及更高版本设备都具有受信任的平台模块 (TPM) 芯片组。 新的符合性设置将检查设备上是否有 TPM。

[Windows 10 及更高版本的符合性策略设置](compliance-policy-create-windows.md)列出了当前设置。

适用于： 
- Windows 10 及更高版本

### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227---"></a>配置要在已注册到 Intune 并且已加入 Azure AD 的设备上安装的 Win32 应用 <!-- 3695227 -->
可分配要在已注册到 Intune 并且已加入 Azure AD 的设备上安装的 Win32 应用。 有关 Intune 中 Win32 应用的详细信息，请参阅 [Win32 应用管理](apps-win32-app-management.md)。

### <a name="windows-defender-advanced-threat-protection-baseline----3754134---"></a>Windows Defender 高级威胁防护基线 <!-- 3754134 -->
我们将添加新的基线来帮助配置 Windows Defender 高级威胁防护设置。

### <a name="device-overview-shows-primary-user---794259---"></a>设备概述显示主要用户 <!--794259 -->
“设备概述”页将显示主要用户，也称为用户设备相关性用户 (UDA)。 要查看设备的主要用户，请选择“Intune” > “设备” > “所有设备”> 选择一个设备。 主要用户将显示在靠近“概述”页顶部的位置。

### <a name="expanded-support-for-android-enterprise-fully-managed-devices----3903241-3903244-3903246---"></a>扩展了对 Android 企业完全托管设备的支持 <!-- 3903241, 3903244, 3903246 -->
我们将扩展对 Android Enterprise 完全托管设备的支持（[于 2019 年 1 月首次发布](whats-new.md#week-of-january-14-2019)，包括以下内容：
- 合规性
- 条件性访问
- 新的最终用户应用

若要设置完全托管的 Android 设备，请转到“设备注册” > “Android 注册” > “公司拥有的完全托管的用户设备”。 完全托管的 Android 设备的支持仍为预览版，某些 Intune 功能可能无法完全正常运行。 

### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925---"></a>Android Enterprise 工作配置文件设备的其他托管 Google Play 应用报告 <!-- 4105925 -->
对于部署到 Android 企业工作配置文件设备的托管 Google Play 应用，将可查看设备上安装的应用的特定版本号。 这仅适用于所需的应用。 对于可用的应用，相同的功能将在未来版本中启用。

### <a name="ios-third-party-keyboards----4111843---"></a>iOS 第三方键盘 <!-- 4111843 -->
由于 iOS 平台更改，对“第三方键盘”设置的 Intune 应用保护策略 (APP) 的支持将结束。 你将无法在 Intune 管理控制台中配置此设置，并且不会在 Intune App SDK 中的客户端上强制执行此设置。

<!-- 1903 start-->

### <a name="block-users-from-scanning-for-windows-updates----3316758---"></a>阻止用户扫描 Windows 更新 <!-- 3316758 -->
我们将添加一个新的 Windows 更新环设置，该设置可用于阻止用户扫描 Windows 更新。 门户中不会提供此设置，但可以使用 Intune 图形 API 对其进行配置。

### <a name="windows-update-notifications----3316782---"></a>Windows 更新通知 <!-- 3316782 -->
我们将添加对 Windows 更新环配置的支持，使你能够配置用户看到的 Windows 更新通知。 门户中不会提供此设置，但可以使用 Intune 图形 API 对其进行配置。

### <a name="easier-access-to-diagnostic-settings----3804627---"></a>更轻松访问诊断设置 <!-- 3804627 -->
我们将在 Intune 控制台中的每个审核日志工作负载中为“审核日志”边栏选项卡添加一个新选项，可使用该选项直接打开“诊断设置”页。

## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。


