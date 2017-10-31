---
title: "早期版本"
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 10/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 973408b292261b86f0a49bfaf4c786d6a6dacf28
ms.sourcegitcommit: b8d3f8da6d8c2bd5d6140d538193a02d5875aefb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="the-early-edition-for-microsoft-intune---october-2017"></a>Microsoft Intune 的早期版本 - 2017 年 10 月

早期版本提供了一份即将发布的 Microsoft Intune 版本中将出现的功能列表。 此信息的提供具有条件限制，并且会不断变化。 请不要与公司外部共享此信息。 此处列出的某些功能有无法按期发布的风险并可能推迟到以后的版本。 正在以试验模式（外部测试）测试其他功能，以确保它们可立即供客户使用。 如果有任何问题或顾虑，请与 Microsoft 产品组联系人联系。

本页将定期更新。 返回查看其他更新。

> [!Note]
>下面的更改依据 Intune 开发。 有关新的混合功能的详细信息，请查看[混合新增功能页](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->



## <a name="intune-in-the-azure-portal"></a>Azure 门户中的 Intune

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory 网站可能需要 Intune Managed Browser 应用，并且支持 Managed Browser（公共预览版）的单一登录<!-- 710595 -->   
利用 Azure Active Directory (Azure AD)，可在移动设备上将对网站的访问限于 Intune Managed Browser 应用。 在 Managed Browser 中，网站数据可保持安全并且独立于最终用户的个人数据。 此外，Managed Browser 支持受 Azure AD 保护的站点的单一登录功能。 通过登录 Managed Browser，或在设备上将 Managed Browser 与由 Intune 管理的其他应用配合使用，用户无需输入凭据，Managed Browser 即可访问受 Azure AD 保护的公司站点。 此功能适用于 Outlook Web Access (OWA) 和 SharePoint Online 等站点，以及通过 Azure 应用代理访问的 Intranet 资源等其他公司站点。

### <a name="troubleshoot-enrollment-issues------746324----"></a>排查注册问题<!--- 746324 --->  
“故障排除”工作区显示用户注册问题。 问题的相关详细信息和建议的修正步骤可帮助管理员和支持人员排查问题。 某些注册问题可能无法捕获，还有某些错误可能没有修正建议。

### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>管理员现在可以使用设备配置文件在设备上配置防火墙设置<!-- 951708 -->   
管理员可以启用防火墙，还可以为域、专用网络和公用网络配置多种协议。  可在“Endpoint Protection”配置文件中找到这些防火墙设置。

### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>Windows Defender 应用程序防护根据组织的定义，帮助阻止设备访问不受信任的网站<!-- 958257 -->   
利用 Windows 信息保护工作流或设备配置下的新“网络边界”配置文件，管理员可将站点定义为“受信任站点”或“公司站点”。 如果使用 Microsoft Edge 访问未在 64 位 Windows 10 设备的受信任网络边界中列出的站点，这些站点将转为在 Hyper-V 虚拟计算机内的浏览器中打开。

可在设备配置文件“Endpoint Protection”中找到应用程序防护。 管理员可在其中配置虚拟化浏览器与主机，以及非受信任站点与受信任站点之间的交互，同时存储虚拟化浏览器中生成的数据。 要在设备上使用应用程序防护，首先必须配置网络边界。 仅可为每个设备定义一个网络边界，这一点非常重要。  

### <a name="windows-defender-application-guard-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>Windows 10 企业版上的 Windows Defender 应用程序防护提供仅信任经授权应用的模式<!-- 1031096 -->    
由于每天都有成千上万个新恶意文件生成，因此使用基于签名的防病毒检测来抵御恶意软件可能无法再针对新型攻击提供足够的防御。 通过在 Windows 10 企业版上使用 Windows Defender 应用程序防护，可以更改设备配置，从信任防病毒软件或其他安全解决方案未阻止的所有应用的模式，更改为操作系统仅信任经企业授权的应用的模式。 可在 Windows Defender 应用程序防护中将应用分配为信任的应用。

利用 Intune，可以在“仅审核”模式或强制执行模式下配置应用程序控制策略。 在“仅审核”模式下运行的应用不会受到阻止。 “仅审核”模式在本地客户端日志中记录所有事件。 还可以配置是仅允许运行 Windows 组件和 Windows 应用商店应用，还是允许运行 Intelligent Security Graph 定义的其他可信应用。

### <a name="new-enrollment-status-page-for-windows-10-enrollments---1063201--"></a>Windows 10 注册的新注册状态页<!--1063201-->    
现在可以配置用户注册 Windows 10 设备时显示的问候语。 使用“注册状态屏幕”，可配置最终用户注册其 Windows 10 设备时显示的自定义消息和超链接。  “注册状态屏幕”还将为最终用户提供策略设置应用到其设备的进度视图。  

### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>Windows Defender 攻击防护是面向 Windows 10 的一组新入侵防护功能<!-- 1063615 -->   
Windows Defender 攻击防护内含自定义规则，可降低应用程序受到攻击的可能性、预防宏和脚本威胁、自动阻止网络连接到可信度较低的 IP 地址，以及保护数据免受勒索软件和未知威胁的攻击。 Windows Defender 攻击防护包含以下组成部分：

- “攻击面减少(ASR)”提供用于预防宏、脚本和电子邮件威胁的规则。
- “控制文件夹访问”可自动阻止访问受保护文件夹中的内容。
- “网络筛选器”可阻止从任何应用到低可信度 IP/域的出站连接
- “攻击防护”提供内存、控制流和策略限制，可用于保护应用程序免受攻击。

### <a name="app-conditional-launch-support----1193313---"></a>应用条件启动支持<!-- 1193313 -->
IT 管理员现可通过 Azure 管理门户设置要求，通过移动应用管理 (MAM) 强制要求在应用程序启动时输入密码，而不是输入数字 PIN。 如果进行此配置，在访问启用 MAM 的应用程序前，用户需要在出现提示时设置并使用密码。 密码是至少包含一个特殊字符或大写/小写字母的数字 PIN。 此版本的 Intune 仅在 iOS 上支持此功能。 Intune 对密码的支持与支持数字 PIN 类似，设置了最短长度并且允许重复字符和序列。 此功能需要应用程序（即 WXP、Outlook、Managed Browser、Yammer）的参与，将 Intune APP SDK 与代码集成，以便此功能准备就绪并在目标应用程序中强制实施密码设置。

### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>设备安装状态报表中业务线的应用版本号 <!-- 1233999 -->  
设备安装状态报告显示适用于 iOS 和 Android 的业务线应用的应用版本号。 可使用此信息对应用进行故障排除，或者查找正在运行过时应用版本的设备。

### <a name="co-management-for-windows-10-devices-----124445---"></a>适用于 Windows 10 设备的共同管理<!-- 124445 -->
共同管理是一种解决方案，可在传统管理与现代管理之间架起一座桥梁，为你提供利用分阶段的方法实现转换的途径。 共同管理本质上是一种解决方案，其中 Configuration Manager 和 Microsoft Intune 同时管理 Windows 10 设备，并且这些设备可联接到 Active Directory (AD) 和 Azure Active Directory (Azure AD)。  此配置提供以适合组织的步调（如果无法即刻完成所有迁移）逐步实现现代化的方式。  

### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>通过在设备上定义最低 Android 安全修补程序版本设置对应用的访问权限<!-- 1278463 -->   
管理员可定义最低 Android 安全修补程序版本，必须在设备上安装该修补程序才能访问托管帐户下的托管应用程序。

> [!Note]  
> 此功能仅适用于在安装了 Android 6.0 及更高版本的设备上限制由 Google 发布的安全修补程序。

### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>适用于 Windows 10 的 Intune 新设备限制设置<!-- 1308850 -->
-    消息传送（仅限移动设备）- 禁用测试或 MMS 消息
-    密码 - 此设置用于启用 FIPS，并且支持使用 Windows Hello 设备辅助设备进行身份验证 
-    显示 - 此设置用于打开或关闭旧版应用的 GDI 缩放


### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Windows 10 设备的展台模式限制<!-- 1308872 -->   
可将 Windows 10 设备的用户限制为使用展台模式，从而限制这些用户仅使用一组预定义的应用。  为此，需创建 Windows 10 设备限制配置文件并设置展台设置。

展台模式支持两种模式：“单应用”模式（仅允许用户运行一个应用）或“多应用”模式（允许访问多个应用）。  可定义用户帐户和设备名，确定受支持的应用。  用户登录时，仅可访问定义的应用。  有关详细信息，请参阅 [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)。 

展台模式要求：

- MDM 机构必须是 Intune。
- 必须已在目标设备上安装应用。
- 设备必须[正确预配](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions)。

### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>用于创建网络边界的新设备配置文件<!-- 1311967 -->   
我们已创建名为“网络边界”的设备配置文件，该配置文件与其他设备配置文件位于同一位置。 使用此配置文件定义要视为公司资源和受信任资源的在线资源。 必须先为设备定义网络边界，然后才能在设备上使用 Windows Defender 应用程序防护和 Windows 信息保护等功能。 仅可为每个设备定义一个网络边界，这一点非常重要。

可以定义可信任的企业云资源、IP 地址范围和内部代理服务器。 定义后，Windows Defender 应用程序防护和 Windows 信息保护等功能即可使用网络边界。

###  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Windows Defender 防病毒软件的两个其他设置<!-- 1338409 -->  
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


### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>对 Symantec 云证书颁发机构 (CA) 的支持<!-- 1333638 -->    
Intune 现在支持 Symantec 云 CA，可允许 Intune 证书连接器从 Symantec 云 CA 向 Intune 受管理设备颁发 PKCS 证书。 如果现已将 Intune 证书连接器和 Microsoft 证书颁发机构 (CA) 配合使用，则可以利用现有 Intune 证书连接器设置添加 Symantec CA 支持。



### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>添加了适用于 Windows 10 设备的 Citrix VPN<!-- 1512457 -->  
客户可为其 Windows 10 设备配置 Citrix VPN。 为 Windows 10 或更高版本配置 VPN 时，可在“基础 VPN”边栏选项卡中的“选择连接类型”列表中选择“Citrix VPN”。

> [!Note]
> 适用于 iOS 和 Android 的 Citrix 配置已存在。





<!-- the following are present prior to 1710 -->

### <a name="google-play-protect-support-on-android----908720----"></a>Android 上的 Google Play Protect 支持 <!-- 908720  -->  
随着 Android Oreo 的发布，Google 引入了一系列名为 Google Play Protect 的安全功能，以便用户和组织可以运行安全的应用和 Android 映像。 Intune 将支持 Google Play Protect 功能，包括 SafetyNet 远程认证。  管理员可以设置符合性策略要求，要求配置和正常运行 Google Play Protect。 “SafetyNet 设备认证”设置要求设备连接到 Google 服务，以验证设备是否正常运行且未遭到入侵。 管理员还可以对 Android for Work 设置配置文件设置，以要求 Google Play 服务对已安装的应用进行验证。  如果设备不符合 Google Play Protect 要求，条件访问可能会禁止用户访问公司资源。 


### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>支持 Windows 10 版本升级策略 <!-- 903672(archived), 1119689 -->  
可以创建 Windows 10 版本升级策略，将 Windows 10 设备升级到 Windows 10 教育版、Windows 10 教育版 N、Windows 10 专业版、Windows 10 专业版 N、Windows 10 专业教育版和 Windows 10 专业教育版 N。有关 Windows 10 版本升级的详细信息，请参阅[如何配置 Windows 10 版本升级](edition-upgrade-configure-windows-10.md)。





<!-- the following are present prior to 1709 -->

### <a name="actions-for-non-compliance----730266--846515---"></a>针对不合规的操作<!--730266  846515 -->     
“针对不合规的操作”是合规性策略的新功能，允许在不合规的设备上执行操作。 可指定单个或多个操作，并指定这些操作必然会发生的时间段。 例如，可在设备变为不合规后，立即通过电子邮件通知该不合规设备的用户，或可在 3 天宽限期后，通过条件性访问阻止不合规设备访问公司资源。

### <a name="android-for-work-support-for-lookout----1087312---"></a>Lookout 的 Android for Work 支持<!-- 1087312 -->   
在使用 Lookout for Work 应用时，Lookout 的 Intune 连接器将支持 Android for Work 设备。 可以在容器内部或外部部署 Lookout 应用。

### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Intune 应用保护和 Citrix MDX 开发工具 <!-- 709185 -->
可以同时使用 Citrix XenMobile MDX 和 Microsoft Intune 来管理设备和应用。 通过使用此方法，可在使用 Citrix mVPN 技术的同时通过 Intune 应用保护策略管理应用。

能够查找包含适用于iOS 和 Android 的 App Wrapping Tool 和 Intune App SDK 的代码存储库，同时还能集成 Citrix MDX mVPN 技术。

#### <a name="how-integration-with-intune-works"></a>与 Intune 集成的工作原理
基于从运行 Zimperium 的设备收集的遥测评估风险。 可以基于通过 Intune 设备符合性策略启动的 Zimperium 风险评估配置 EMS 条件访问策略，从而根据检测到的威胁允许或阻止不符合要求的设备访问公司资源。

### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>本地 Exchange 连接器高可用性支持 <!-- 676614 -->   
能够拥有用于本地 Exchange 连接器的多个客户端访问服务器 (CAS) 角色。 例如，如果主 CAS 失败，Exchange 连接器会收到一个用于回退到其他 CAS 的查询。 此功能可确保服务不中断。

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>适用于 Exchange 连接器的 System Center Operations Manager 管理包<!-- 885457 -->   
将会提供适用于 Exchange 连接器的 System Center Operations Manager 管理包帮助你分析 Exchange 连接器日志。 此管理包将在需要进行问题故障排除时为你提供监控 Intune 的多种方式。


## <a name="intune-apps"></a>Intune 应用


### <a name="redirecting-macos-users-to-our-new-company-portal-app---1380728--"></a>将 macOS 用户重定向到新公司门户应用<!--1380728-->   
当最终用户登录公司门户网站注册其 macOS 设备时，系统会将其定向到下载 macOS 版新公司门户应用的页面，以便完成此过程。 使用 OS X El Capitan 10.11 或更高版本的 macOS 设备会出现这种情况。 

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>iOS 版公司门户上基于证书的身份验证支持<!--1029830-->
我们在 iOS 版公司门户应用中添加了对基于证书的身份验证 (CBA) 的支持。 使用 CBA 的用户可输入其用户名，然后点击“使用证书登录”链接。 Android 和 Windows 版公司门户应用中已实现了对 CBA 的支持。 有关详细信息，请参阅[登录公司门户应用](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal)页。

<!-- the following are present prior to 1710 -->



### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>现在可以在没有注册提示的情况下，安装可注册或不可注册的应用。 <!-- 1334712 -->
在 Android 公司门户应用中，可以在没有注册提示的情况下，安装可注册或不可注册的公司应用。


<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>iOS 和 Android 的 Intune Managed Browser 支持<!-- 1374196 -->
自 2017 年 10 月起，Android 版 Intune Managed Browser 应用将仅支持运行 Android 4.4 及更高版本的设备。 iOS 上的 Intune Managed Browser 应用将仅支持运行 iOS 9.0 及更高版本的设备。 早期版本的 Android 和 iOS 将能够继续使用 Managed Browser，但不能安装新版本的应用，并且可能无法访问所有应用功能。 建议将这些设备更新为受支持的操作系统版本。


### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>改进了用户达到允许注册的最大设备数时提示的错误消息 <!-- 1270370 -->
最终用户将不再看到普通错误消息，而将看到一条友好且可操作的错误消息：“注册设备数已达到 IT 管理员允许的最大数量。请删除已注册的设备，或者向 IT 管理员寻求帮助。”




## <a name="notices"></a>通知

### <a name="device-and-app-management-integration----677972---"></a>设备和应用管理集成<!-- 677972 -->   
由于 Intune 移动设备管理 (MDM) 和移动应用管理 (MAM) 均可通过 Azure 门户访问，因此 Intune 已开始集成有关应用程序和设备管理的 IT 管理员体验。 这些更改旨在简化设备和应用的管理体验。

有关 MDM 和 MAM 更改的详细信息，请参阅 [Intune 支持团队博客](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/)中的发布内容。




### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。
