---
title: "Microsoft Intune 新增功能"
titlesuffix: Azure portal
description: "了解 Intune Azure 门户新增功能"
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 11/18/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1f3f9832a643628cf18aee6131b9c8a43843e94d
ms.sourcegitcommit: 71e6e80b7370024624ce2e5fad1ca5b372975748
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune 新增功能

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

了解 Microsoft Intune 每周新增功能。 另外，你还可以找到[即将发生的更改](#whats-coming)、有关服务的[重要说明](#notices)，以及有关[过去版本](whats-new-archive.md)的信息。

> [!Note]
> 许多功能最终将支持带 Configuration Manager 的混合客户部署。 有关新的混合功能的详细信息，请查看[混合新增功能页](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。


<!-- Common categories:  
  ### Device enrollment
  ### Device management
  ### App management
  ### Device configuration
  ### Role-based access control
  ### Intune apps
  ### Monitor and troubleshoot

-->   

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
现已提供适用于 Exchange 连接器的 System Center Operations Manager (SCOM) 管理包帮助你分析 Exchange 连接器日志。 在你需要进行故障排除时，它可提供多种监视该服务的方式。

## <a name="week-of-november-6-2017"></a>2017 年 11 月 6 日当周

### <a name="device-enrollment"></a>设备注册
#### <a name="co-management-for-windows-10-devices-----1243445---"></a>适用于 Windows 10 设备的共同管理<!-- 1243445 -->
共同管理是一种解决方案，可在传统管理与现代管理之间架起一座桥梁，为你提供利用分阶段的方法实现转换的途径。 共同管理本质上是一种解决方案，其中 Configuration Manager 和 Microsoft Intune 同时管理 Windows 10 设备，并且这些设备可联接到 Active Directory (AD) 和 Azure Active Directory (Azure AD)。  此配置提供以适合组织的步调（如果无法即刻完成所有迁移）逐步实现现代化的方式。  

#### <a name="new-enrollment-status-page-for-windows-10-enrollments---1063201--"></a>Windows 10 注册的新注册状态页<!--1063201-->    
现在可以配置用户注册 Windows 10 设备时显示的问候语。 使用“注册状态屏幕”，可配置最终用户注册其 Windows 10 设备时显示的自定义消息和超链接。  “注册状态屏幕”还将为最终用户提供策略设置应用到其设备的进度视图。  

#### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>通过 OS 版本限制 Windows 注册<!-- 245498 -->
作为 Intune 管理员，现在可为设备注册指定 Windows 10 的最低和最高版本。 可以在“平台配置”边栏选项卡中设置这些限制。

Intune 将继续支持 Windows 8.1 电脑和手机注册。 但只有对 Windows 10 才可设置最高和最低版本限制。 若要允许注册 8.1 设备，请将最低限制留空。

#### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Windows AutoPilot 未分配设备警报<!-- 1631236 -->
在“Microsoft Intune” > “设备注册” > “概述”页中，为 Windows AutoPilot 未分配设备提供了一个新警报。 此警报显示有多少来自 AutoPilot 计划的设备尚未分配 AutoPilot 部署配置文件。 使用警报中的信息可创建配置文件，并将其分配到未分配的设备。 单击警报时，会看到 Windows AutoPilot 设备的完整列表，以及与之相关的详细信息。 有关详细信息，请参阅[使用 Windows AutoPilot Deployment 计划注册 Windows 设备](https://docs.microsoft.com/intune/enrollment-autopilot)。

### <a name="device-management"></a>设备管理

#### <a name="refresh-button-for-devices-list-------1333581---"></a>设备列表的刷新按钮 <!-- 1333581 -->
由于设备列表不会自动刷新，可使用新的“刷新”按钮来更新列表中显示的设备。

#### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>对 Symantec 云证书颁发机构 (CA) 的支持<!-- 1333638 -->    
Intune 现在支持 Symantec 云 CA，可允许 Intune 证书连接器从 Symantec 云 CA 向 Intune 受管理设备颁发 PKCS 证书。 如果现已将 Intune 证书连接器和 Microsoft 证书颁发机构 (CA) 配合使用，则可以利用现有 Intune 证书连接器设置添加 Symantec CA 支持。

#### <a name="new-items-added-to-device-inventory-----1404455---"></a>添加到设备清单的新项目<!--1404455 -->
在此版本中，我们向[由已注册设备获取的清单](device-inventory.md)添加了以下新项目：

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

#### <a name="windows-defender-application-guard-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>Windows 10 企业版上的 Windows Defender 应用程序防护提供仅信任经授权应用的模式<!-- 1031096 -->    
由于每天都有成千上万个新恶意文件生成，因此使用基于签名的防病毒检测来抵御恶意软件可能无法再针对新型攻击提供足够的防御。 通过在 Windows 10 企业版上使用 Windows Defender 应用程序防护，可以更改设备配置，从信任防病毒软件或其他安全解决方案未阻止的所有应用的模式，更改为操作系统仅信任经企业授权的应用的模式。 可在 Windows Defender 应用程序防护中将应用分配为信任的应用。

利用 Intune，可以在“仅审核”模式或强制执行模式下配置应用程序控制策略。 在“仅审核”模式下运行的应用不会受到阻止。 “仅审核”模式在本地客户端日志中记录所有事件。 还可以配置是仅允许运行 Windows 组件和 Windows 应用商店应用，还是允许运行 Intelligent Security Graph 定义的其他可信应用。

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
我们已创建名为“网络边界”的设备配置文件，该配置文件与其他设备配置文件位于同一位置。 使用此配置文件定义要视为公司资源和受信任资源的在线资源。 必须先为设备定义网络边界，然后才能在设备上使用 Windows Defender 应用程序防护和 Windows 信息保护等功能。 仅可为每个设备定义一个网络边界，这一点非常重要。

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

#### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>在适用于 iOS 的公司门户（版本 2.9.0）中对设备设置工作流的改进<!---1417174--->

我们改进了适用于 iOS 的公司门户应用中的设备设置工作流。 语言对用户更加友好，在可能的情况下我们还对屏幕进行了合并。 我们还通过在整个设置文本中使用公司名称使语言特定于你的公司。 可以在 [应用 UI 的新增功能](whats-new-app-ui.md)页上看到此更新的工作流。

### <a name="monitor-and-troubleshoot"></a>监视和故障排除

#### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>用户实体包含数据仓库数据模型中的最新用户数据 <!-- 1544273 -->
Intune 数据库仓库数据模型的第一个版本只包含 Intune 的最近历史数据。 报表制作者无法捕获用户的当前状态。 在此更新中，用户实体将包含最新用户数据。


## <a name="week-of-october-30-2017"></a>2017 年 10 月 30 日当周

### <a name="app-management"></a>应用管理

#### <a name="ios-and-android-line-of-business-app-version-number-is-visible----1380712---"></a>iOS 和 Android 业务线应用版本号是可见的 <!-- 1380712 -->

现在，Intune 中的应用会显示 iOS 和 Android 业务线应用的版本号。 版本号会在 Azure 门户、应用列表和应用概述边栏选项卡中显示。 最终用户可在公司门户应用和 Web 门户中查看应用的版本号。

__完整版本号__ 完整版本号标识应用的特定版本。 该号码显示为“版本号(内部版本号)”。 例如：2.2(2.2.17560800)

完整版本号包含两个部分：

 - **版本**  
   版本号是应用的发行版号（可人工读取）。 最终用户使用版本号确定应用的不同发行版。

 - **内部版本号**  
    内部版本号是一个内部号码，可在应用检测中使用，并可用于以编程方式管理应用。 内部版本号是指应用的迭代，应用可引用代码中的更改。

要详细了解版本号以及如何开发业务线应用，请参阅 [Microsoft Intune App SDK 入门](app-sdk-get-started.md#line-of-business-app-version-numbers)。

#### <a name="device-and-app-management-integration----677972---"></a>设备和应用管理集成<!-- 677972 -->   
由于 Intune 移动设备管理 (MDM) 和移动应用管理 (MAM) 均可通过 Azure 门户访问，因此 Intune 已开始集成有关应用程序和设备管理的 IT 管理员体验。 这些更改旨在简化设备和应用的管理体验。

有关 MDM 和 MAM 更改的详细信息，请参阅 [Intune 支持团队博客](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/)中的发布内容。

#### <a name="new-enrollment-alerts-for-apple-devices----1471790---"></a>Apple 设备的新注册警报 <!-- 1471790 -->
注册的概述页将介绍一些有关 Apple 设备管理的警报，这些警报适用于 IT 管理员。 如果存在下列情况，“概述”页上就会显示警报：Apple MDM 推送消息称证书将过期或已过期；设备注册计划令牌将过期或已过期；设备注册计划中存在未分配的设备。

#### <a name="support-token-replacement-for-app-configuration-without-device-enrollment----1080364---"></a>支持使用令牌替换应用配置（无需设备注册）<!-- 1080364 -->

对于未注册设备上的应用，可在应用配置期间使用令牌获取动态值。 有关详细信息，请参阅[为受管理应用添加应用配置策略（无需设备注册）](app-configuration-policies-managed-app.md)。

### <a name="intune-apps"></a>Intune 应用

#### <a name="updates-to-the-company-portal-app-for-windows-10---1299474--"></a>更新适用于 Windows 10 的公司门户应用<!--1299474-->
适用于 Windows 10 的公司门户应用的“设置”页面已更新，以使设置和预期的用户操作在所有设置中更加一致。 其更新也旨在匹配其他 Windows 应用的布局。 你可以在[应用 UI 中的新增功能](whats-new-app-ui.md)页找到更新之前/之后的图像。

#### <a name="inform-end-users-what-device-information-can-be-seen-for-windows-10-devices---1337920--"></a>告知最终用户可以查看 Windows 10 设备的哪些设备信息 <!--1337920-->
我们已在适用于 Windows 10 的公司门户应用的“设备详细信息”屏幕上添加了“所有权类型”。 这样，用户便可直接在 Intune 最终用户文档的此页中发现详细隐私信息。用户还将在“关于”屏幕中找到此信息。

#### <a name="feedback-prompts-for-the-company-portal-app-for-android---1165249--"></a>适用于 Android 的公司门户应用的反馈提示<!--1165249-->
适用于 Android 的公司门户应用现在可请求最终用户反馈。 此反馈将被直接发送给 Microsoft，让最终用户有机会在公用 Google Play 商店中查看应用。 反馈不是必需的，很容易消除，所以用户可以继续使用该应用。

#### <a name="update-to-what-device-details-an-organization-can-see---1616825--"></a>有关设备更新的详细信息，组织可以参阅<!--1616825-->
适用于 Android 的公司门户应用现在可以使用地理围栏来保护对公司资源的访问。 它使用 IP 地址、默认网关地址和域名系统 (DNS) 等网络详细信息，以确定是否允许访问受保护的公司资源。

#### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>利用 Android 版公司门户应用帮助用户自助 <!---1573324, 1573150, 1558616, 1564878--->

适用于 Android 的公司门户应用为最终用户添加了说明，帮助他们了解并自行解决（如果可能）新用例。
- 如果最终用户达到允许添加的最大设备数，他们将被引导至 (Azure Active Directory 门户)[https://account.activedirectory.windowsazure.com/r/#/profile]，以删除设备。
- 最终用户会得到可遵循的步骤，帮助他们[修复 Samsung KNOX 设备上的激活错误](https://go.microsoft.com/fwlink/?linkid=859718)或[关闭节能模式](/intune-user-help/power-saving-mode-android)。 如果这些解决方案均无法解决问题，请查看[将日志提交给 Microsoft](/intune-user-help/send-logs-to-microsoft-ios) 的相关说明。

#### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>适用于 Android 设备的新“解决”操作<!---1583480--->

Android 版公司门户应用在“更新设备设置”页中引入了“解决”操作。 选择此选项会将最终用户直接转至导致其设备不符合的设置。 Android 版公司门户应用当前为以下设置提供此操作：[设备密码](/intune-user-help/set-your-pin-or-password-android)、[USB 调试](/intune-user-help/you-need-to-turn-off-usb-debugging-android)和[未知源](/intune-user-help/you-need-to-turn-off-unknown-sources-android)。

#### <a name="device-setup-progress-indicator-in-android-company-portal----1565657---"></a>适用于 Android 的公司门户中的设备设置进度指示器<!---1565657--->
适用于 Android 的公司门户应用在用户注册设备时显示设备设置进度指示器。 该指示器将显示最新状态，从“设置设备...”，再“注册设备...”，接着“完成设备注册...”，然后“完成设备设置...”。

## <a name="week-of-october-23-2017"></a>2017 年 10 月 23 日当周

### <a name="intune-apps"></a>Intune 应用
#### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>iOS 版公司门户上基于证书的身份验证支持<!--1029830-->
我们在 iOS 版公司门户应用中添加了对基于证书的身份验证 (CBA) 的支持。 使用 CBA 的用户可输入其用户名，然后点击“使用证书登录”链接。 Android 和 Windows 版公司门户应用中已实现了对 CBA 的支持。 有关详细信息，请参阅[登录公司门户应用](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal)页。

#### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>现在可以在没有注册提示的情况下，安装可注册或不可注册的应用。 <!-- 1334712 -->

在 Android 公司门户应用中，现可在没有注册提示的情况下，安装通过/不通过注册而获取的公司应用。

## <a name="week-of-october-16-2017"></a>2017 年 10 月 16 日当周
### <a name="device-enrollment"></a>设备注册
#### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune-----747617----"></a>Microsoft Intune 中的 Windows AutoPilot Deployment 计划支持<!-- 747617  -->
现在可将 Microsoft Intune 与 Windows AutoPilot Deployment 计划配合使用，授权用户在不劳烦 IT 的情况下设置其企业设备。 可以自定义全新体验 (OOBE)，引导用户将设备加入 Azure AD 并在 Intune 中注册。 在配合使用 Microsoft Intune 与 Windows AutoPilot 时，完全无需部署、维护和管理操作系统映像。 有关详细信息，请参阅 [Enroll Windows devices using Windows AutoPilot Deployment Program](https://docs.microsoft.com/intune/enrollment-autopilot)（使用 Windows AutoPilot Deployment 计划注册 Windows 设备）。

#### <a name="quick-start-for-device-enrollment-----1425655---"></a>设备注册快速入门  <!-- 1425655 --> 
快速入门当前在设备注册中可用，此外还提供了用于管理平台和配置注册过程的参考表格。 对每个项目的简短说明和包含分步说明的文档链接提供了有用的文章，可帮助简化入门过程。

#### <a name="device-categorization----1427491---"></a>设备分类 <!-- 1427491 -->
“设备”>“概述”边栏选项卡中的已注册设备平台图可以按平台（包括 Android、iOS、macOS、Windows 和 Windows Mobile）整理设备。  运行其他操作系统的设备将被分到“其他”组。  这包括由 Blackberry 和 NOKIA 等厂家生产的设备。  

要了解租户中的哪些设备会受到影响，请选择“管理”>“所有设备”，然后使用“筛选器”限制“操作系统”字段。

### <a name="device-management"></a>设备管理
#### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium - 新移动威胁防御合作伙伴<!-- 954681 -->  
可根据 Zimperium 进行的风险评估，使用条件访问控制移动设备对公司资源的访问，Zimperium 是与 Microsoft Intune 集成的移动威胁防御解决方案。

##### <a name="how-integration-with-intune-works"></a>与 Intune 集成的工作原理
基于从运行 Zimperium 的设备收集的遥测评估风险。 可以基于通过 Intune 设备符合性策略启动的 Zimperium 风险评估配置 EMS 条件访问策略，从而根据检测到的威胁允许或阻止不符合要求的设备访问公司资源。

#### <a name="new-settings-for-windows-10-device-restriction-profile------978575-1308849---"></a>Windows 10 设备限制配置文件的新设置  <!--- 978575, 1308849, -->  
我们将向 Windows Defender SmartScreen 类别中的 Windows 10 设备限制配置文件中添加新设置。

有关 Windows 10 设备限制配置文件的详细信息，请参阅 [Windows 10 和更高版本的设备限制设置]( device-restrictions-windows-10.md)。

#### <a name="remote-support-for-windows-and-windows-mobile-devices------1070473---"></a>Windows 和 Windows Mobile 设备的远程支持   <!-- 1070473 -->  
Intune 现在可以使用 [TeamViewer](https://www.teamviewer.com) 软件（单独购买），为运行 Windows 和 Windows Mobile 设备的用户提供远程协助。

#### <a name="scan-devices-with-windows-defender----1280988--1280990-----"></a>使用 Windows Defender 扫描设备 <!-- 1280988  1280990   -->
现可在托管的 Windows 10 设备上，使用 Windows Defender 防病毒运行“快速扫描”、“完全扫描”和“更新签名”。 在设备的“概览”边栏选项卡上，选择要在设备上运行的操作。 在命令发送到设备之前，系统会提示用户确认操作。 

**快速扫描**：快速扫描可扫描恶意软件注册启动的位置，如注册表项和已知的 Windows 启动文件夹。 快速扫描平均需要五分钟才能完成。 “始终开启实时保护”设置可在用户打开、关闭文件、转到文件夹时扫描文件。与此设置配合使用，快速扫描可有助于保护系统或内核免遭潜在恶意软件威胁。 扫描完成时，用户可以在设备上查看扫描结果。 

**完全扫描**：完全扫描非常适合受恶意软件威胁的设备，以确定是否需要更彻底地清理任何停用组件，并且十分适用于运行按需扫描。 完全扫描可能需要一小时才能完成。 扫描完成时，用户可以在设备上查看扫描结果。 

**更新签名**：更新签名命令可更新 Windows Defender 防病毒恶意软件定义和签名。 这有助于确保 Windows Defender 防病毒可以有效地检测恶意软件。 此功能仅适用于挂起设备 Internet 连接的 Windows 10 设备。 

#### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal-----1400455---"></a>已将“启用/禁用”按钮从 Intune Azure 门户的 Intune 证书颁发机构页中删除  <!-- 1400455 -->
 我们正在删除在 Intune 上设置证书连接器这一额外步骤。 当前，需要下载证书连接器，然后在 Intune 控制台中启用它。 但如果在 Intune 控制台中禁用它，该连接器仍将持续颁发证书。

##### <a name="how-does-this-affect-me"></a>这对我有何影响？
从 10 月开始，Azure 门户的证书颁发机构页中将不再显示“启用/禁用”按钮。 连接器功能保持不变。 证书仍将部署到在 Intune 中注册的设备。 可以继续下载并安装证书连接器。 若要停止颁发证书，当前需卸载证书连接器，而不是禁用它。

##### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
如果目前已禁用证书连接器，则应该卸载它。

### <a name="device-configuration"></a>设备配置
#### <a name="new-settings-for-windows-10-team-device-restriction-profile-------1308838---"></a>Windows 10 协同版设备限制配置文件的新设置   <!--- 1308838 -->
在此版本中，我们向 Windows 10 协同版设备限制配置文件添加了许多新设置，以帮助用户控制 Surface Hub 设备。

有关此配置文件的详细信息，请参阅 [Windows 10 协同版设备限制设置](device-restrictions-windows-10-teams.md)。

#### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time-----1333292---"></a>禁止 Android 设备用户更改设备日期和时间 <!-- 1333292 -->
将可以使用 [Android 自定义设备策略](custom-settings-android.md)，禁止 Android 设备用户更改设备日期和时间。

为此，请将 URI ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange 设置为 TRUE，配置 Android 自定义策略，再将策略分配给相应组。

#### <a name="bitlocker-device-configuration----1397398---"></a>BitLocker 设备配置 <!-- 1397398 -->
在“Windows 加密”>“基本设置”中，现可以使用新的“针对其他磁盘加密的警告”设置，从而禁止对用户设备上可能使用的其他磁盘加密显示[警告提示](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption)。  警告提示要求先征得最终用户同意，然后才能在设备上设置 BitLocker，并且会在最终用户确认之前禁止设置 BitLocker。  这一新设置可以禁用最终用户警告。


### <a name="app-management"></a>应用管理
#### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant----800882---"></a>适用于业务应用的 Volume Purchase Program 现在将同步到你的 Intune 租户 <!-- 800882 -->  
第三方开发人员可以私下将应用分发给适用于 iTunes Connect 中指定的业务成员的经授权 Volume Purchase Program。 这些面向业务成员的 VPP 可以登录 Volume Purchase Program App Store 并购买应用。

此版本中，最终用户购买的适用于业务应用的 VPP 将开始同步到其 Intune 租户中。

#### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>选择 Apple 国家/地区应用商店以同步 VPP 应用 <!-- 1332311 -->  
将可以在上传 VPP 令牌时，配置 Volume Purchase Program (VPP) 国家/地区应用商店。 Intune 将同步指定 VPP 国家/地区应用商店中所有区域设置对应的 VPP 应用。

> [!NOTE]  
> 目前，Intune 只会同步 VPP 国家/地区应用商店中，区域设置与创建 Intune 租户所用的 Intune 区域设置一致的 VPP 应用。


### <a name="intune-apps"></a>Intune 应用
#### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>在 Android for Work 中，禁止在工作配置文件与个人配置文件之间进行复制粘贴 <!-- 1098994 -->
在此版本中，将可以配置 Android for Work 工作配置文件，以禁止在工作应用与个人应用之间进行复制粘贴。 可以转到 Android for Work 平台的“设备限制”配置文件，在“工作配置文件设置”中找到这一新设置。

#### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>创建特定区域 Apple App Store 专属的 iOS 应用 <!-- 1281692 -->
将可以在创建 Apple App Store 管理的应用期间，指定国家/地区区域设置。

> [!Note]  
> 目前，只能创建美国应用商店中具备的 Apple App Store 托管应用。

####  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>更新 iOS VPP 用户和设备许可的应用 <!-- 1305564 -->  
将可以把 iOS VPP 令牌配置为，更新针对此令牌通过 Intune 服务购买的所有应用。 Intune 将在应用商店内检测 VPP 应用更新，并在设备进行检测时自动将这些更新推送到设备中。

有关设置 VPP 令牌和启用自动更新的步骤，请参阅 [如何使用 Microsoft Intune 管理通过批量采购计划购买的 iOS 应用] (/intune/vpp-apps-ios)。


### <a name="monitor-and-troubleshoot"></a>监视和故障排除
#### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>用户设备关联实体集合被添加到 Intune 数据仓库数据模型 <!-- 1187917 -->
现在可使用用户设备关联信息（该信息将用户和设备实体集合相关联）生成报表和数据可视化效果。 可通过从“数据仓库 Intune”页检索到的 Power BI 文件 (PBIX)、通过 OData 终结点或通过开发自定义客户端，访问数据模型。

#### <a name="review-policy-compliance-for-windows-10-update-rings----1067886---"></a>检查 Windows 10 更新通道的策略符合性 <!-- 1067886 -->
将可以在“软件更新”>“每个更新通道的部署状态”中检查 Windows 10 更新通道的策略报告。 策略报告包括已配置的更新通道的部署状态。 

#### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>列出使用较旧 iOS 版本的 iOS 设备的新报表   <!-- 1352223 -->
可在“软件更新”工作区中获取“过期 iOS 设备”报告。 在报表中，可以查看已应用 iOS 更新策略且具有可用更新的受监督 iOS 设备的列表。 可以查看每个设备的状态，了解该设备未自动更新的原因。 

#### <a name="view-app-protection-policy-assignments-for-troubleshooting-----1475003---"></a>查看应用保护策略分配以进行故障排除 <!--  1475003 -->
在即将发布的这一版本中，“应用保护策略”选项将添加到“疑难解答”边栏选项卡上的“分配”下拉列表中。 现在可以选择应用保护策略，查看分配给选定用户的应用保护策略。



## <a name="week-of-october-2-2017"></a>2017 年 10 月 2 日那周
### <a name="intune-apps"></a>Intune 应用
#### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>对公司门户中的设备设置工作流的改进<!--1490692-->
我们改进了适用于 Android 的公司门户应用中的设备设置工作流。 语言更贴近你公司的用语习惯，在可能的情况下我们还对屏幕进行了合并。 可以在[应用 UI 的新增功能](whats-new-app-ui.md#week-of-october-2-2017)页中查看这些更改。

#### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>改进了与请求访问 Android 设备上的联系人相关的指南<!--1484985-->

适用于 Android 的公司门户应用需要最终用户接受“联系人”权限。 如果最终用户拒绝授予此访问权限，现在他们将看到应用内通知，提醒他们授予此权限以实现条件访问。 

#### <a name="secure-startup-remediation-for-android---1490712--"></a>面向 Android 的安全启动修正<!--1490712-->

使用 Android 设备的最终用户将能够点击公司门户应用中的不合规原因。 在可能的情况下，此操作会使用户直接转到“设置”应用中的适当位置，以修复问题。 

#### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo---1475932--"></a>向最终用户额外发送有关 Android Oreo 公司门户应用的推送通知 <!--1475932-->

最终用户可以看到其他通知，其中指明了 Android Oreo 公司门户应用何时执行后台任务，如从 Intune 服务检索策略。 这进一步提高了透明度，可方便最终用户了解公司门户应用何时在其设备上执行管理任务。 这是 Android Oreo 公司门户应用的全部[公司门户 UI 优化](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune)中的一部分。 

Android Oreo 中启用的新 UI 元素有进一步的优化。  最终用户将看到附加通知，指示他们公司门户何时执行从 Intune 服务中检索策略等后台任务。  最终用户可以更加清楚地了解公司门户何时在设备上执行管理任务。

#### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Android 公司门户应用与工作配置文件配合使用时的新行为 <!---1485783--->

使用工作配置文件注册 Android for Work 设备时，在设备上执行管理任务的正是工作配置文件中的公司门户应用。 

除非在个人配置文件中使用已启用 MAM 的应用，否则 Android 公司门户应用不再提供任何服务。 为了改善工作配置文件体验，Intune 将在成功使用工作配置文件注册后自动隐藏个人公司门户应用。

随时都可以在 [Play Store 中搜索公司门户](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)并点击“启用”，从而在个人配置文件中启用 Android 公司门户应用。

#### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>适用于 Windows 8.1 和 Windows Phone 8.1 的公司门户将进入持续性模式 <!--1428681-->

自 2017 年 10 月起，适用于 Windows 8.1 和 Windows Phone 8.1 的公司门户应用将进入持续性模式。 也就是说，这些平台将继续支持应用和现有方案（如注册和符合性）。 将仍可以通过现有发布通道（如 Microsoft 应用商店）下载这些应用。 

一旦进入持续性模式，这些应用就只会收到关键安全更新程序。 对于这些应用，将不会发布其他任何更新或功能。 若要使用新功能，建议将设备更新到 Windows 10 或 Windows 10 移动版。 


### <a name="device-enrollment"></a>设备注册

#### <a name="block-unsupported-samsung-knox-device-enrollment------1490695----"></a>阻止不受支持的 Samsung Knox 设备注册<!--- 1490695 --->

公司门户应用仅尝试注册受支持的 Samsung Knox 设备。 若要避免出现会阻止 MDM 注册的 KNOX 激活错误，将仅在设备显示在 [Samsung 发布的设备列表](https://www.samsungknox.com/knox-supported-devices/knox-workspace)中时才尝试设备注册。 Samsung 设备可能有支持 KNOX 的型号，其他设备则不具备。 购买并部署前，请与设备经销商确认 Knox 兼容性。 可以在 [Android 和 Samsung KNOX 标准版策略设置](/intune/supported-devices-browsers.md#intune-supported-devices)中找到经验证设备的完整列表。

#### <a name="end-of-support-for-android-43-and-lower----1171126-1326920----"></a>停止对 Android 4.3 及更低版本的支持 <!---1171126, 1326920 --->
Android 托管的应用和公司门户应用需要使用 Android 4.4 和更高版本访问公司资源。 截至 12 月，所有已注册的设备将在 12 月强制停用，从而导致无法访问公司资源。 如果使用应用保护策略而不使用 MDM，应用将不会收到更新，并且随着时间推移其体验质量将会降低。

#### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices---1165314--"></a>告知最终用户可在注册设备上查看哪些设备信息<!--1165314-->
我们将在所有公司门户应用的“设备详细信息”屏幕上添加“所有权类型”。 这样，用户便可直接在[公司可看到哪些信息？](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune)文章中发现详细隐私信息。 近期将在所有公司门户应用中推出此更新。 我们在 [9 月](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017)宣布了面向 iOS 的此项更新。


## <a name="week-of-september-25-2017"></a>2017 年 9 月 25 日那周

### <a name="device-enrollment"></a>设备注册

#### <a name="intune-supports-ios-11---1428975--"></a>Intune 支持 iOS 11<!--1428975-->
Intune 支持 iOS 11。 此信息之前已在 [Intune 支持博客](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/)中发布。

#### <a name="end-of-support-for-ios-80----1164477---"></a>停止对 iOS 8.0 的支持<!---1164477--->
适用于 iOS 的托管应用和公司门户应用需要使用 iOS 9.0 和更高版本才能访问公司资源。 今年 9 月之前不更新的设备将不再能够访问公司门户应用或这些应用。 

### <a name="intune-apps"></a>Intune 应用

#### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>刷新操作被添加到 Windows 10 公司门户应用 <!--1132468-->
使用 Windows 10 版公司门户应用，用户可以通过下拉刷新或在桌面上按 F5 来刷新应用中的数据。



## <a name="notices"></a>通知

### <a name="deprecating-support-for-os-x-yosemite-1010-and-previous-versions-of-macos---1489263-plan-for-change-for-1802--"></a>即将停止对 OS X Yosemite 10.10 及 macOS 早期版本的支持<!--1489263, plan for change for 1802-->

我们宣布，自 2018 年 2 月起，将开始停止对运行 OS X Yosemite 10.10 及 macOS 早期版本的设备的注册。 Intune 完全支持 OS X Capitan 10.11 和更高版本。

### <a name="new-path-for-managed-devices-in-graph-api----1586728---"></a>在图形 API 中访问受管理设备的新路径<!-- 1586728 -->
我们正在更改用于在 beta 版本图形 API 中访问托管设备的路径。 

| | |
|--|--|
| 当前路径 |  https://graph.microsoft.com/beta/managedDevices |
| 新路径 | https://graph.microsoft.com/beta/deviceManagement/managedDevices |

这两个路径在 10 月均可使用。 10 月服务发布后，仅可使用新路径。  如果目前使用图形 API 受管理设备，请使用新路径更新和验证脚本和应用程序。 有关其他更改，请查看每月[图形 API 更改日志](https://developer.microsoft.com/graph/docs/concepts/changelog)。


### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接访问 Apple 注册方案<!--951869-->
对于在 2017 年 1 月之后创建的 Intune 帐户，Intune 支持在 Azure 门户中使用注册设备工作负荷直接访问 Apple 注册方案。 以前，只能通过 Intune 经典门户中的链接访问 Apple 注册预览版。 2017 年 1 月之前创建的 Intune 帐户需要进行一次性迁移，然后才能使用 Azure 中的这些功能。 迁移的计划目前尚未公布，但详细信息将尽快发布。 强烈建议创建一个试用帐户，在现有帐户无法访问 Azure 门户时测试新体验。

### <a name="administration-roles-being-replaced-in-azure-portal"></a>在 Azure 门户中被替换的管理角色
在 Intune 经典门户 (Silverlight) 中使用的现有移动应用程序管理 (MAM) 管理角色（参与者、所有者和只读）被替换为 Intune Azure 门户中一套完整的基于角色的新的管理控制方法 (RBAC)。 在迁移到 Azure 门户后，需要将管理员重新分配到这些新的管理角色。 有关 RBAC 和新角色的详细信息，请参阅 [Microsoft Intune 基于角色的访问控制](/intune/role-based-access-control)。



## <a name="whats-coming"></a>即将推出

### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747---"></a>使用 Intune 的设备符合性引擎管理 Jamf 注册的 macOS 设备<!---1592747--->
从 2018 年初开始，Jamf 将把 macOS 设备状态信息发送给 Intune，然后由 Intune 评估它是否符合 Intune 控制台中定义的策略。 基于设备符合性状态以及其他条件（如位置、用户风险等），条件访问将强制实现 macOS 设备访问云和与 Azure AD 连接的本地应用程序（包括 Office 365）的符合性。

### <a name="changes-in-support-for-the-intune-ios-company-portal-app-----1164474----"></a>Intune iOS 公司门户应用的支持更改 <!-- 1164474  -->
Microsoft Intune 公司门户应用 iOS 版即将会有新的版本，该版本仅支持运行 iOS 9.0 或更高版本的设备。 支持 iOS 8 的公司门户版本在未来短时间内仍将可用。 但是请注意，如果还使用启用了 MAM 的 iOS 应用（支持 iOS 9.0 和更高版本），需确保最终用户更新到最新 OS。 

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
虽然我们无法提供具体日期，但我们仍将此提前告知于你，以便你有时间做出计划。 请确保你的用户更新到 iOS 9+，且当公司门户应用发布后，请求最终用户更新其公司门户应用。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
鼓励用户更新到 iOS 9.0 或更高版本以充分利用 Intune 的新功能。  鼓励用户安装公司门户的新版本，从而利用它将提供的新功能。

转到 Azure 门户中 Intune，依次查看“设备”>“所有设备”，并按 iOS 版本进行筛选，以确定当前是否有任何设备的操作系统低于 iOS 9。


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 将要求更新应用传输安全<!--748318-->
Apple 宣布他们将强制对应用程序传输安全 (ATS) 实施特定要求。 使用 ATS 对所有通过 HTTPS 的应用通信实施更严格的安全措施。 此更改会影响使用 iOS 公司门户应用的 Intune 客户。

我们通过强制实施新的 ATS 要求的 Apple TestFlight 计划提供了适用于 iOS 的公司门户应用的可用版本。 如果你想要试用以测试你的 ATS 符合性，请发送电子邮件至 <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a>，并提供你的名字、姓氏、电子邮件地址和公司名称。 请查看 [Intune 支持博客](https://aka.ms/compportalats)，了解更多详细信息。

## <a name="see-also"></a>另请参阅
* [Microsoft Intune 博客](http://go.microsoft.com/fwlink/?LinkID=273882)
* [云平台路线图](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [What's new in the Company Portal UI](whats-new-app-ui.md)（公司门户 UI 新增功能）
* [前几个月的新增功能](whats-new-archive.md)
