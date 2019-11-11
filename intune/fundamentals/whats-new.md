---
title: Microsoft Intune 中的新增功能 - Azure | Microsoft Docs
titleSuffix: ''
description: 了解 Intune Azure 门户新增功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: ac6da1b15d482d20340163b0bb79e88d74e8e375
ms.sourcegitcommit: 2c8a41ee95a3fde150667a377770e51b621ead65
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/06/2019
ms.locfileid: "73635340"
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune 新增功能

了解 Microsoft Intune 每周新增功能。 还可以找到[重要通知](#notices)、[过去版本](whats-new-archive.md)，以及有关[如何发布 Intune 服务更新](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728)的信息。

> [!Note]
> 每个[每月更新](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728)可能需要长达三天才能推出，顺序如下：
>
> - 第 1 天：亚太地区 (APAC)
> - 第 2 天：欧洲、中东和非洲 (EMEA)
> - 第 3 天：北美
>
> 某些功能可能会在数周内推出，第一周内可能不能供所有客户使用。
>
> 有关版本中即将推出的功能的列表，请查看[开发过程中页面](in-development.md)。

**RSS 源**：通过将以下 URL 复制并粘贴到源阅读器中，可以在页面更新时收到通知：`https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Device security
### Intune apps
### Monitor and troubleshoot
### Role-based access control
-->  

## <a name="week-of-october-28-2019"></a>2019 年 10 月 28 日当周

### <a name="app-management"></a>应用管理

#### <a name="improved-checklist-design-in-company-portal-app-for-android---5550857---"></a>在适用于 Android 的公司门户应用中改进了清单设计<!-- 5550857 -->  
使用轻型设计和新图标更新了适用于 Android 的公司门户应用中的安装清单。 所做的更改与对适用于 iOS 的公司门户应用所做的最新更新一致。 我们正在将应用更新推出给所有客户，希望在下周结束前完成。 有关更改的并行比较，请参阅[应用 UI 中的新增功能](whats-new-app-ui.md)。 若要查看更新的注册步骤，请参阅[使用 Android 工作配置文件注册](/intune-user-help/enroll-device-android-work-profile)和[注册 Android 设备](/intune-user-help/enroll-device-android-company-portal)。  

#### <a name="win32-apps-on-windows-10-s-mode-devices---3747604---"></a>Windows 10 S 模式设备上的 Win32 应用<!-- 3747604 --> 
可以在 Windows 10 S 模式托管设备上安装和运行 Win32 应用。 为此，可以使用 Windows Defender 应用程序控制 (WDAC) PowerShell 工具为 S 模式创建一个或多个补充策略。 使用设备保护签名服务对补充策略进行签名，然后通过 Intune 上传和分发策略。 在 Intune 中，可以通过选择“客户端应用”   > “Windows 10 S 补充策略”  来查找此功能。 有关详细信息，请参阅[在 S 模式设备上启用 Win32 应用](~/apps/apps-win32-s-mode.md)。

#### <a name="set-win32-app-availability-based-on-a-date-and-time---3510685---"></a>基于日期和时间设置 Win32 应用可用性<!-- 3510685 -->
管理员可以为所需的 Win32 应用配置开始时间和截止时间。 在开始时间，Intune 管理扩展将启动应用内容下载并缓存它。 应用将在截止时间安装。 对于可用应用，开始时间将指示应用在公司门户中的可见时间。 有关详细信息，请参阅 [Intune Win32 应用管理](~/apps/apps-win32-app-management.md#set-win32-app-availability-and-notifications)。

#### <a name="require-device-restart-based-on-grace-period-after-win32-app-install---3136567---"></a>需要在安装 Win32 应用后基于宽限期重新启动设备<!-- 3136567 -->
可以要求必须在成功安装 Win32 应用后重新启动设备。 有关详细信息，请参阅 [Win32 应用管理 - 配置应用安装详细信息](~/apps/apps-win32-app-management.md#step-4-configure-app-installation-details)。

#### <a name="dark-mode-for-ios-company-portal---4911422---"></a>适用于 iOS 公司门户的深色模式<!-- 4911422 -->
深色模式适用于 iOS 公司门户。 用户可以下载公司应用、管理其设备，并根据设备设置在所选的配色方案中获取 IT 支持。 iOS 公司门户将自动与最终用户的设备设置匹配，自动应用深色或浅色模式。 有关详细信息，请参阅[适用于 iOS 的 Microsoft Intune 公司门户上的深色模式简介](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Introducing-dark-mode-on-Microsoft-Intune-Company-Portal-for-iOS/ba-p/918453)。 有关 iOS 公司门户的详细信息，请参阅[如何配置 Microsoft Intune 公司门户应用](~/apps/company-portal-app.md)。

#### <a name="android-company-portal-enforced-minimum-app-version---2378776---"></a>Android 公司门户强制执行最低应用版本<!-- 2378776 -->
通过使用应用保护策略的最小公司门户版本设置，可以指定在最终用户设备上强制执行的公司门户的特定最低定义版本  。 使用此条件启动设置，可以在不满足值时将“阻止访问”、“擦除数据”和“警告”作为可能的操作    。 此值的可能格式遵循 [主版本].[次版本]、[主版本].[次版本].[内部版本] 或 [主版本].[次版本].[内部版本].[修订版本]    。

如果已配置最小公司门户版本设置，则将影响获取公司门户版本 5.0.4560.0 的任何最终用户以及公司门户的任何未来版本  。 此设置对使用版本低于与此功能一起发布的公司门户版本的用户没有任何影响。 在设备上使用应用自动更新的最终用户可能看不到此功能的任何对话框，因为他们可能使用最新的公司门户版本。 此设置仅适用于已注册和未注册设备具有应用保护的 Android。 有关详细信息，请参阅 [Android 应用保护策略设置 - 条件启动](~/apps/app-protection-policy-settings-android.md#conditional-launch)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->

### <a name="microsoft-365-device-management"></a>Microsoft 365 设备管理

#### <a name="introducing-endpoint-security-node-in-microsoft-365-device-management---5630102---"></a>Microsoft 365 设备管理中的终结点安全节点简介<!-- 5630102 -->

终结点安全节点现已在 https://devicemanagement.microsoft.com 上的 Microsoft 365 设备管理专家工作区中公开发布，可将这些功能组合在一起以保护终结点，例如  ：

- 安全基线：预配置的设置组，这些设置可帮助你应用 Microsoft 推荐的已知设置组和默认值。

- 安全任务：利用 Microsoft Defender ATP 威胁和漏洞管理 (TVM)，并使用 Intune 修正终结点漏洞。

- Microsoft Defender ATP：集成了 Microsoft Defender 高级威胁防护 (ATP) 来帮助阻止安全漏洞。

这些设置仍能够从其他适用的节点（如设备）访问，并且，无论在何处访问和启用这些功能，当前配置的状态都是相同的。

有关这些改进的详细信息，请参阅 Microsoft 技术社区网站上的 [Intune 客户成功博客文章](https://aka.ms/Endpoint_security_node)。

### <a name="device-management"></a>设备管理

#### <a name="intune-supports-ios-11-and-later---4665324----"></a>Intune 支持 iOS 11 及更高版本<!-- 4665324  -->

Intune 注册和公司门户现在支持 iOS 版本 11 及更高版本。 不支持早期版本。

### <a name="device-security"></a>设备安全性

#### <a name="microsoft-edge-baseline-preview----3787164----"></a>Microsoft Edge 基线（预览版）<!--  3787164  -->

已添加用于 [Microsoft Edge 设置](../protect/security-baseline-settings-edge.md)的安全基线（预览版）。 

<!-- ########################## -->
## <a name="week-of-october-21-2019"></a>2019 年 10 月 21 日当周

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="microsoft-365-device-management"></a>Microsoft 365 设备管理

#### <a name="improved-administration-experience-in-microsoft-365-device-management---5551239---"></a>改进了 Microsoft 365 设备管理中的管理体验<!-- 5551239 -->

已刷新并简化的管理体验现已在 [https://devicemanagement.microsoft.com](https://devicemanagement.microsoft.com) 上的 Microsoft 365 设备管理专家工作区中公开发布，其中包括：

- **更新的导航**：你会发现简化的第一级导航（可对功能进行逻辑分组）。
- **新平台筛选器**：可以在“设备和应用”页上选择单一平台，该平台仅显示所选平台的策略和应用。
- **新主页**：在新主页上快速查看服务运行状况、租户状态、新闻等。

有关这些改进的详细信息，请参阅 Microsoft 技术社区网站上的[企业移动性 + 安全性博客文章](https://go.microsoft.com/fwlink/?linkid=2109094)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>应用管理

#### <a name="add-mobile-threat-defense-apps-to-unenrolled-devices---3005337---"></a>将移动威胁防御应用添加到未注册的设备<!-- 3005337 -->
可以创建可阻止的 Intune 应用保护策略，或者根据设备的运行状况选择性擦除用户的公司数据。 设备的运行状况使用所选的移动威胁防御 (MTD) 解决方案来确定。 此功能目前作为设备符合性设置存在于在 Intune 中注册的设备。 利用这项新功能，我们扩展了移动威胁防御供应商的威胁检测，使其在未注册的设备上正常工作。 在 Android 上，此功能需要在设备上使用最新的公司门户。 在 iOS 上，当应用集成最新的 Intune SDK (v 12.0.15+) 时，此功能将可供使用。 当第一个应用采用最新的 Intune SDK 时，我们将更新“新增功能”主题。 剩余的应用将陆续可用。 有关详细信息，请参阅[使用 Intune 创建移动威胁防御应用保护策略](~/protect/mtd-app-protection-policy.md)。

### <a name="device-configuration"></a>设备配置

#### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices---2266073----"></a>适用于 Windows 10 及更高版本设备的新设备固件配置接口配置文件<!-- 2266073  -->

在 Windows 10 及更高版本中，可以创建设备配置文件来控制设置和功能（适用于平台的“设备配置” > “配置文件” > “创建配置文件” > “Windows 10 及更高版本”）     。 在此更新中，有一个新的设备固件配置接口配置文件类型，该类型允许 Intune 管理 UEFI (BIOS) 设置。

有关此功能的详细信息，请参阅[在 Microsoft Intune 中使用 Windows 设备上的 DFCI 配置文件](../configuration/device-firmware-configuration-interface-windows.md)。

适用于：
- 支持固件上的 Windows 10 RS5 (1809) 及更高版本

### <a name="device-enrollment"></a>设备注册

#### <a name="toggle-to-only-show-enrollment-status-page-on-devices-provisioned-by-out-of-box-experience-oobe--3959566--"></a>切换为在由全新体验 (OOBE) 预配的设备上仅显示注册状态页<!--3959566-->
现在，你可以选择在由 Autopilot OOBE 预配的设备上仅显示注册状态页。

若要查看新的切换，请选择“Intune”   > “设备注册”   > “Windows 注册”   > “注册状态页”   > “创建配置文件”   > “设置”   >   “在由全新体验 (OOBE) 预配的设备上仅显示页”。


<!-- ########################## -->
## <a name="week-of-october-14-2019"></a>2019 年 10 月 14 日当周

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>应用管理 

#### <a name="available-google-play-app-reporting-for-android-work-profiles---3041956-----"></a>用于 Android 工作配置文件的可用 Google Play 应用报告<!-- 3041956   -->
对于 Android Enterprise 工作配置文件、专用和完全托管设备上的可用应用安装，可以查看应用安装状态以及托管 Google Play 应用的安装版本。 有关详细信息，请查看[如何监视应用保护策略](~/apps/app-protection-policies-monitor.md)、[使用 Intune 管理 Android 工作配置文件设备](~/enrollment/android-enterprise-overview.md)和[托管的 Google Play 应用类型](~/apps/apps-add-android-for-work.md#managed-google-play-app-types)。

#### <a name="microsoft-edge-version-77-and-later-for-windows-10-and-macos-public-preview---3872025-4678761----"></a>适用于 Windows 10 和 MacOS 的 Microsoft Edge 77 及更高版本（公共预览版）<!-- 3872025, 4678761  -->
Microsoft Edge 版本 77 及更高版本将可以部署到运行 Windows 10 和 MacOS 的电脑上。 

公共预览版为 Windows 10 提供了“开发”和“Beta”通道，为 macOS 提供了“Beta”通道    。 部署仅使用英语 (EN)，但最终用户可以在“设置” > “语言”下更改浏览器中的显示语言   。 Microsoft Edge 是一款安装在系统上下文和类似体系结构中的 Win32 应用（在 x86 OS 上安装为 x86 应用，在 x64 OS 上安装为 x64 应用）。 另外，默认“启用”浏览器自动更新，且无法卸载 Microsoft Edge  。 有关详细信息，请参阅[将 Microsoft Edge for Windows 10 添加到 Microsoft Intune](~/apps/apps-windows-edge.md) 和 [Microsoft Edge 文档](https://go.microsoft.com/fwlink/?linkid=2103823)。

#### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui---4102027-4102029-----"></a>更新至应用保护 UI 和 iOS 应用预配 UI<!-- 4102027, 4102029   -->
Intune 中用于创建和编辑应用保护策略和 iOS 应用预配配置文件的 UI 已更新。 UI 更改包括：
- 简化了体验，现可使用压缩在一个边栏选项卡中的向导式格式。 
- 对创建流进行了更新，使其包含分配。
- 在创建新策略前查看属性时，或在编辑属性时，将显示包含已设置的所有内容的摘要页。 此外，编辑属性时，摘要将仅显示正在编辑的属性类别的项目列表。

有关详细信息，请参阅[如何创建和分配应用保护策略](~/apps/app-protection-policies.md)和[使用 iOS 应用预配配置文件](~/apps/app-provisioning-profile-ios.md)。

#### <a name="intune-guided-scenarios---4850318-4831296-3610611----"></a>Intune 引导式方案<!-- 4850318, 4831296, 3610611  -->
Intune 现在提供引导式方案，可帮助你完成 Intune 中的特定任务或一组任务。 引导式方案是围绕一个端到端用例而定制的一系列步骤（工作流）。 常见方案基于管理员、用户或设备在组织中扮演的角色定义。 这些工作流通常需要精心设计的配置文件、设置、应用程序和安全控件的集合，以提供最佳的用户体验和安全性。 新引导式方案包括：
- [部署 Microsoft Edge for Mobile](~/fundamentals/guided-scenarios-edge.md)
- [保护 Microsoft Office 移动应用的安全](~/fundamentals/guided-scenarios-office-mobile.md) 
- [云托管的新式桌面](~/fundamentals/guided-scenarios-cloud-managed-pc.md)

有关详细信息，请参阅 [Intune 引导式方案概述](guided-scenarios-overview.md)。

#### <a name="additional-app-configuration-variable-available---4969237-----"></a>其他应用程序配置变量可用<!-- 4969237   -->
创建应用配置策略时，可以将 `AAD Device ID` 配置变量作为配置设置的一部分。 在 Intune 中，选择“客户端应用”   > “应用配置策略”   > “添加”  。 输入配置策略详细信息并选择“配置设置”以查看“配置设置”边栏选项卡   。 有关详细信息，请参阅[托管 Android Enterprise 设备的应用配置策略 - 使用配置设计器](~/apps/app-configuration-policies-use-android.md#use-the-configuration-designer)。


#### <a name="create-groups-of-management-objects-called-policy-sets---3762880----"></a>创建称为策略集的管理对象组<!-- 3762880  -->
策略集允许创建对现有管理实体的一系列引用，这些实体需要作为单个概念单元进行标识、定位和监视。 策略集不会替换现有的概念或对象。 你可以继续在 Intune 中分配各个对象，也可以将各个对象作为策略集的一部分进行引用。 因此，对各对象的任何更改都将反映在策略集中。  在 Intune 中，选择“策略集” > “创建”来创建新的策略集   。 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>设备配置

#### <a name="ui-update-for-creating-and-editing-windows-10-update-rings---4099089-----------"></a>创建和编辑 Windows 10 更新通道的 UI 更新<!-- 4099089         -->
我们为 Intune 更新了[创建和编辑 Windows 10 更新通道](../protect/windows-update-for-business-configure.md#create-and-assign-update-rings)的 UI 体验。 对 UI 的更改包括：  
- 将向导式格式压缩到单个控制台边栏选项卡中，它与配置更新通道时看到的扩展边栏选项卡无关。   
- 修改后的工作流包括“分配”，分配在完成通道的初始配置之前进行。
- 在保存和部署新更新通道之前，可以使用摘要页面来查看已进行的所有配置。 编辑更新通道时，摘要仅显示在你编辑的属性类别内设置的项目列表。

#### <a name="ui-update-for-creating-and-editing-ios-software-update-policy---4099090---------"></a>创建和编辑 iOS 软件更新策略的 UI 更新<!-- 4099090       --> 
我们为 Intune 更新了[创建](../protect/software-updates-ios.md#configure-the-policy)和[编辑](../protect/software-updates-ios.md#edit-a-policy) iOS 软件更新策略的 UI 体验。  对 UI 的更改包括：  
- 将向导式格式压缩到单个控制台边栏选项卡中，它与配置更新策略时看到的扩展边栏选项卡无关。   
- 修改后的工作流包括“分配”，分配在完成策略的初始配置之前进行。
- 在保存和部署新策略之前，可以使用摘要页面来查看已进行的所有配置。 编辑策略时，摘要仅显示在你编辑的属性类别内设置的项目列表。

#### <a name="engaged-restart-settings-are-removed-from-windows-update-rings----4464404---wnready-----"></a>预定重启设置已从 Windows 更新通道中删除<!--  4464404   WNReady   -->
如前所述，Intune 的 Windows 10 更新通道现在[支持设置截止时间](../protect/windows-update-settings.md)，而不再支持预定重启  。 在 Intune 中配置或管理更新通道时，预定重启的设置将不再可用  。  

此更改与最新的 [Windows 服务更改](https://docs.microsoft.com//windows/whats-new/whats-new-windows-10-version-1903#servicing)一致。在运行 Windows 10 1903 或更高版本的设备上，截止时间将取代“预定重启”的配置   。

#### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-work-profile-devices---4760025-----"></a>防止在 Android Enterprise 工作配置文件设备上安装来自未知源的应用<!-- 4760025   -->
在 Android Enterprise 工作配置文件设备上，用户永远无法安装来自未知来源的应用。 此次更新添加了一个新设置 -“防止应用在个人配置文件中安装来自未知来源的应用”  。 默认情况下，此设置可以防止用户将来自未知来源的应用程序旁加载到设备上的个人配置文件中。

要查看可以配置的设置，请转到[允许或限制使用 Intune 的功能的 Android Enterprise 设备设置](../configuration/device-restrictions-android-for-work.md)。

适用于：
- Android Enterprise 工作配置文件

#### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices---4816339-----"></a>在 Android Enterprise 设备所有者设备上创建一个全局 HTTP 代理<!-- 4816339   -->
在 Android Enterprise 设备上，你可以配置全局 HTTP 代理，以满足组织的 Web 浏览标准（“设备配置” > “配置文件” > “创建配置文件” > 针对平台选择“Android Enterprise”> 设备所有者 > 针对配置文件类型选择“设备限制”>“连接”）       。 配置完成后，所有 HTTP 流量都将使用此代理。

要配置此功能并查看所配置的所有设置，请转到[允许或限制使用 Intune 的功能的 Android Enterprise 设备设置](../configuration/device-restrictions-android-for-work.md)。

适用于：
- Android Enterprise 设备所有者

#### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-device-administrator-and-android-enterprise---5021055-----"></a>在 Android 设备管理员和 Android Enterprise 的 Wi-Fi 配置文件中删除了“自动连接”设置<!-- 5021055   -->
在 Android 设备管理员和 Android Enterprise 设备上，你可以创建 Wi-Fi 配置文件以配置其他设置（“设备配置” > “配置文件” > “创建配置文件” > “Android 设备管理员”或针对平台选择“Android Enterprise”> 针对配置文件类型选择“Wi-Fi”）       。 在此更新中，删除了“自动连接”设置，因为它[不受 Android 支持](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29)  。 

如果在 Wi-Fi 配置文件中使用此设置，则可能会注意到“自动连接”不起作用  。 无需执行任何操作，但请注意，此设置已在 Intune 用户界面中删除。

若要查看当前设置，请转到 [Android Wi-Fi 设置](../configuration/wi-fi-settings-android.md)或 [Android Enterprise Wi-Fi 设置](../configuration/wi-fi-settings-android-enterprise.md)。

适用于：
- Android 设备管理员 
- Android Enterprise


#### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices---5199328-----"></a>受监督的 iOS 和 iPadOS 设备的新设备配置设置<!-- 5199328   -->
在 iOS 和 iPadOS 设备上，你可以创建配置文件以限制设备上的功能和设置（依次选择“设备配置” > “配置文件” > “创建配置文件” > 针对平台选择“iOS/iPadOS”> 针对配置文件类型选择“设备限制”）      。 在此更新中，可以控制以下新设置： 
- 在“文件”应用中访问网络驱动器  
- 在“文件”应用中访问 USB 驱动器 
- Wi-Fi 始终打开 

若要查看这些设置，请转到[允许或限制使用 Intune 的功能的 iOS 设备设置](../configuration/device-restrictions-ios.md)。

适用于：
- iOS 13.0 及更高版本
- iPadOS 13.0 及更高版本

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>设备注册

#### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment---4350697-----"></a>指定使用工作配置文件或设备管理员注册注册哪些 Android 设备操作系统版本<!-- 4350697   -->
使用 Intune 设备类型限制，你可以使用设备的 OS 版本来指定哪些用户设备将使用 Android Enterprise 工作配置文件注册或 Android 设备管理员注册。  有关详细信息，请参阅[创建注册限制](../enrollment/enrollment-restrictions-set.md)。

#### <a name="windows-autopilot-deployment-reports---3856172---"></a>Windows Autopilot 部署报表<!-- 3856172 -->
新报告说明了通过 Windows Autopilot 部署的每个设备的详细信息。 有关详细信息，请参阅 [Autopilot 部署报告](../enrollment/enrollment-autopilot.md#autopilot-deployments-report)。 我们正在将此功能推出到所有客户，预计在下周末前完成。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>设备管理

#### <a name="new-restrictions-for-renaming-windows-devices---3478938----"></a>重命名 Windows 设备的新限制<!-- 3478938  -->
重命名 Windows 设备时，必须遵循新规则：
- 小于或等于 15 个字符（必须小于或等于 63 个字节，不包括尾随 NULL）
- 非 Null 或空字符串
- 允许的 ASCII：字母（a-z、A-Z），数字 (0-9) 和连字符
- 允许的 Unicode：0x80 及以后的字符，必须是有效的 UTF8，必须是可映射到 IDN（即 RtlIdnToNameprepUnicode 成功；请参阅 RFC 3492）
- 名称不得只包含数字
- 名称中不能包含空格
- 不允许的字符：{ | } ~ [ \ ] ^ ' : ; < = > ? & @ ! " # $ % ` ( ) + / , . _ *)

 有关详细信息，请参阅[在 Intune 中重命名设备](../remote-actions/device-rename.md)。

### <a name="new-android-report-on-devices-overview-page---4924364---"></a>“设备概述”页面上新增 Android 报告<!-- 4924364 -->
“设备概述”页面的新报告显示每个设备管理解决方案中注册了多少 Android 设备。 此图表显示工作配置文件、完全托管、专用和设备管理员注册的设备计数。 若要查看报告，请选择“Intune” > “设备” > “概述”    。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>设备安全性

#### <a name="pkcs-certificates-for-macos---1333650---------"></a>适用于 macOS 的 PKCS 证书<!-- 1333650       -->
现在可以[在 macOS 上使用 PKCS 证书](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile)。 可以选择 PKCS 证书作为 macOS 的配置文件类型，并部署具有[自定义主题和主题可选名称字段](../protect/certficates-pfx-configure.md#subject-name-format-for-macos)的用户和设备证书。  

MacOS 的 PKCS 证书还支持新设置“允许所有应用访问”  。 使用此设置，可以启用对证书私钥的所有关联应用访问。  有关此设置的更多信息，请参阅 https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf 处的 Apple 文档。

####   <a name="derived-credentials-to-provision-ios-mobile-devices-with-certificates----1736036-1736037-1772050-2777333-----------"></a>派生凭据以向 iOS 移动设备提供证书<!--  1736036, 1736037, 1772050, 2777333         -->  
Intune 支持使用[派生凭据](../protect/derived-credentials.md)作为身份验证方法，并支持 iOS 设备的 S/MIME 签名和加密。 派生凭据是美国国家标准与技术研究院 (NIST) 800-157 标准的实现，用于将证书部署到设备  。  

派生凭据依赖于使用个人身份验证 (PIV) 或通用访问卡 (CAC) 卡（如智能卡）。 若要获取移动设备的派生凭据，用户需从公司门户应用中开始，并遵循你所使用的提供商特有的注册工作流。  所有提供商都要求使用计算机上的智能卡向派生凭据提供商进行身份验证。 然后，该提供商向从用户智能卡派生的设备颁发证书。  

Intune 支持以下派生凭据提供商：
- DISA Purebred
- Entrust Datacard
- Intercede

使用派生凭据作为 VPN、Wi-Fi 和电子邮件的设备配置文件的身份验证方法。 还可以将它们用于应用身份验证、S/MIME 签名和加密。  

有关该标准的详细信息，请参阅 www.nccoe.nist.gov 上的[派生 PIV 凭据](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials)。

#### <a name="use-graph-api-to-specify-a-on-premises-user-principal-name-as-a-variable-for-scep-certificates----5437939----------"></a>使用图形 API 将本地用户主体名称指定为 SCEP 证书的变量<!--  5437939        -->  
使用 [Intune 图形 API](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0) 时，可以将 onPremisesUserPrincipalName 指定为 SCEP 证书的使用者可选名称 (SAN) 的变量。



<!-- ########################## -->

## <a name="week-of-september-23-2019"></a>2019 年 9 月 23 日当周

#### <a name="ios-user-enrollment-in-preview---4817900---"></a>预览版中的 iOS 用户注册<!-- 4817900 -->
Apple 的 iOS 13.1 版本包括用户注册，它是一种新的 iOS 设备轻型管理形式。 它可用于代替个人所有的设备的设备注册或自动设备注册（以前称为设备注册计划）。 Intune 预览版支持此功能集，方法是让你：

- 将用户注册面向用户组。
- 让最终用户在注册其设备时，可以在较轻的用户注册或更强的设备注册之间进行选择。

从 2019 年 9 月 24 日开始，随着 iOS 13.1 的发布，我们正在将这些更新推出给所有客户，希望在下周结束前完成。
适用于：

iOS 13.1 及更高版本

#### <a name="intune-support-for-ipados-and-ios-131-devices--5439574--"></a>Intune 支持 iPadOS 和 iOS 13.1 设备<!--5439574-->
Intune 现在支持管理 iPadOS 和 iOS 13.1 设备。 有关详细信息，请参阅[此博客文章](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-1-and-iPadOS/ba-p/873094)。

<!-- ########################## -->

## <a name="week-of-september-16-2019"></a>2019 年 9 月 16 日当周

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>应用管理 

#### <a name="managed-google-play-private-lob-apps---1464182----"></a>托管 Google Play 专用 LOB 应用<!-- 1464182  -->
现在，借助 Intune，IT 管理员可以通过在 Intune 控制台中嵌入的 iframe 将专用 Android LOB 应用发布到托管 Google Play。  以前，IT 管理员需要将 LOB 应用直接发布到 Google Play 发布控制台，这需要执行几个步骤，并且很耗时。 这项新功能可让你轻松地使用一组最少的步骤发布 LOB 应用，而无需离开 Intune 控制台。  管理员不再需要使用 Google 手动注册为开发人员，并且不再需要向 Google 支付 25 美元注册费。  使用托管 Google Play 的任何 Android 企业管理方案都可以利用此功能（工作配置文件、专用、完全托管和非注册设备）。 在 Intune 中，选择“客户端应用”   > “应用”   > “添加”  。 从“应用类型”  列表中，选择“托管的 Google Play”  。 有关托管的 Google Play 应用的详细信息，请参阅[使用 Intune 将托管的 Google Play 应用添加到 Android Enterprise 设备](../apps/apps-add-android-for-work.md)。

#### <a name="windows-company-portal-experience---1473353-3598357---"></a>Windows 公司门户体验<!-- 1473353, 3598357 -->
Windows 公司门户正在更新。 你将能够在 Windows 公司门户中的“应用”页上使用多个筛选器。 “设备详细信息”页也正在使用改进的用户体验进行更新。 我们正在将这些更新推出给所有客户，希望在下周结束前完成。

#### <a name="macos-support-for-web-apps---3174427---"></a>Web 应用的 macOS 支持<!-- 3174427 -->
可以使用 macOS 公司门户将 Web 应用（此类应用可将快捷方式添加到网页 URL）安装到 Dock。 最终用户可以从 macOS 公司门户中的 Web 应用的应用详细信息页访问安装  操作。 有关 Web 链接  应用类型的详细信息，请参阅[将应用添加 Microsoft Intune](../apps/apps-add.md)和[将 Web 应用添加到 Microsoft Intune](../apps/web-app.md)。

#### <a name="macos-support-for-vpp-apps---3173501----"></a>VPP 应用的 macOS 支持<!-- 3173501  -->
当 Apple VPP 令牌在 Intune 中同步时，使用 Apple Business Manager 购买的 macOS 应用将显示在控制台中。 可以使用 Intune 控制台为组分配、撤消和重新分配设备和基于用户的许可证。 Microsoft Intune 可通过以下方式帮助用户管理为贵公司购买的 VPP 应用：

- 从应用商店中报告许可证信息。
- 跟踪已使用的许可证数量。
- 帮助防止安装的应用副本数超过所拥有的数目。

有关 Intune 和 VPP 的系详细信息，请参阅[使用 Microsoft Intune 管理批量购买的应用和书籍](../apps/vpp-apps.md)。

#### <a name="managed-google-play-iframe-support---2871756----"></a>托管 Google Play iframe 支持<!-- 2871756  -->
Intune 现在支持通过托管的 Google Play iframe 直接在 Intune 控制台中添加和管理 Web 链接。  这使 IT 管理员可以提交 URL 和图标图形，然后将这些链接部署到设备，就像常规 Android 应用一样。 使用托管 Google Play 的任何 Android 企业管理方案都可以利用此功能（工作配置文件、专用、完全托管和非注册设备）。 在 Intune 中，选择“客户端应用”   > “应用”   > “添加”  。 从“应用类型”  列表中，选择“托管的 Google Play”  。 有关托管的 Google Play 应用的详细信息，请参阅[使用 Intune 将托管的 Google Play 应用添加到 Android Enterprise 设备](../apps/apps-add-android-for-work.md)。

#### <a name="silently-install-android-lob-apps-on-zebra-devices---4252734----"></a>在 Zebra 设备上以无提示方式安装 Android LOB 应用<!-- 4252734  -->
当在 [Zebra 设备](../configuration/android-zebra-mx-overview.md)上安装 Android 业务线 (LOB) 应用时，不会提示你下载并安装 LOB 应用，而是能够以无提示方式安装应用。 在 Intune 中，选择“客户端应用” > “应用” > “添加”    。 在“添加应用”  窗格中，选择“业务线应用”  。 有关详细信息，请参阅[将 Android 业务线应用添加到 Microsoft Intune](../apps/lob-apps-android.md)。

目前，下载 LOB 应用后，会在用户的设备上显示下载成功  通知。 只能通过在通知底纹中点击“全部清除”  来消除通知。 此通知问题将在即将发布的版本中得到解决，安装将完全无提示且无可视指示器。

#### <a name="read-and-write-graph-api-operations-for-intune-apps---5031704----"></a>针对 Intune 应用的读取和写入 Graph API 操作<!-- 5031704  -->
应用程序可以使用应用标识（而无需使用用户凭据）来调用 Intune Graph API 读写操作。 若要详细了解如何访问用于 Intune 的 Microsoft Graph API，请参阅[在 Microsoft Graph 中使用 Intune](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)。

#### <a name="protected-data-sharing-and-encryption-for-intune-app-sdk-for-ios---3586942----"></a>适用于 iOS 的 Intune App SDK 受保护的数据共享和加密<!-- 3586942  -->
应用保护策略启用加密时，适用于 iOS 的 Intune App SDK 将使用 256 位加密密钥。 所有应用都需要 SDK 8.1.1 版本才能进行受保护的数据共享。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>设备配置

#### <a name="support-for-ikev2-vpn-profiles-for-ios---1943438-----"></a>支持适用于 iOS 的 IKEv2 VPN 配置文件<!-- 1943438   -->
在此更新中，可以使用 IKEv2 协议为 iOS 本机 VPN 客户端创建 VPN 配置文件。 IKEv2 是以下位置中的新连接类型：“设备配置”   > “配置文件”   > “创建配置文件”   > 针对平台选择“iOS”  > 针对配置文件类型选择“VPN”  >“连接类型”  。

这些 VPN 配置文件配置本机 VPN 客户端，因此不会安装 VPN 客户端应用，也不会将其推送到托管设备。 此功能要求设备在 Intune （MDM 注册）中注册。

要查看当前可配置的 VPN 设置，请转到[在 iOS 设备上配置 VPN 设置](../configuration/vpn-settings-ios.md)。

适用于：
- iOS

#### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type---4886161-----"></a>适用于 iOS 和 macOS 设置的设备功能、设备限制和扩展配置文件按注册类型显示<!-- 4886161   -->

在 Intune 中，为 iOS 和 macOS 设备创建配置文件（依次选择“设备配置”   > “配置文件”   > “创建配置文件”   >  针对平台选择“iOS”或“macOS”   > 针对配置文件类型选择“设备功能”、“设备限制”或“扩展”    ）。 

在此更新中，Intune 门户中的可用设置按它们适用的注册类型分类：

- iOS
  - 用户注册
  - 设备注册
  - 自动设备注册（监督）
  - 所有注册类型

- macOS
  - 用户已批准
  - 设备注册
  - 自动设备注册
  - 所有注册类型

适用于：
- iOS

#### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode---4892835-----"></a>在展台模式下运行的受监督 iOS 设备的新语音控制设置<!-- 4892835   -->
在 Intune 中，你可以创建策略以将受监督的 iOS 设备作为展台或专用设备运行（“设备配置”   >  **“配置文件”**  > “创建配置文件”   > 针对平台选择“iOS”>  针对配置文件类型选择“设备限制”>“展台”   ）。

在此更新中，可以控制以下新设置：
- **语音控件**：在展台模式下启用设备上的语音控件。
- **修改语音控件**：允许用户在展台模式下更改设备上的语音控件设置。

若要查看当前设置，请转到 [iOS 展台设置](../configuration/device-restrictions-ios.md#kiosk)。

适用于：
- iOS 13.0 及更高版本

#### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices---4893175-----"></a>在 iOS 和 macOS 设备上对应用和网站使用单一登录<!-- 4893175   -->
在此更新中，有一些用于 iOS 和 macOS 设备的新单一登录设置（依次选择“设备配置”   > “配置文件”   > “创建配置文件”   >  针对平台选择“iOS”或“macOS”   > 针对配置文件类型选择“设备功能”  ）。

使用这些设置来配置单一登录体验，特别是对于使用 Kerberos 身份验证的应用和网站。 你可以在通用凭据单一登录应用扩展和 Apple 的内置 Kerberos 扩展之间进行选择。

若要查看可配置的当前设备功能，请转到 [iOS 设备功能](../configuration/ios-device-features-settings.md)和 [macOS 设备功能](../configuration/macos-device-features-settings.md)。

适用于：
- iOS 13.0 及更高版本
- macOS 10.15 及更高版本

#### <a name="associate-domains-to-apps-on-macos-1015-devices---4898079-----"></a>将域关联到 macOS 10.15 + 设备上的应用<!-- 4898079   -->
在 macOS 设备上，可以配置不同的功能，并使用策略将这些功能推送到设备（依次选择“设备配置”   > “配置文件”   > 创建配置文件   > 针对平台选择“macOS”  > 针对配置文件选择“设备功能”  ）。 在此更新中，你可以将域关联到应用。 此功能可帮助与应用相关的网站共享凭据，并可与 Apple 的单一登录扩展、通用链接和密码自动填充配合使用。 

若要查看可配置的当前功能，请转到 [Intune 中的 macOS 设备功能设置](../configuration/macos-device-features-settings.md)。

适用于：
- macOS 10.15 及更高版本

#### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices---4928474-----"></a>显示或隐藏 iOS 受监督设备上的应用时，请使用 iTunes 应用商店 URL 中的“iTunes”和“应用”<!-- 4928474   --> 
在 Intune 中，你可以创建策略以显示或隐藏受监督 iOS 设备上的应用（依次选择“设备配置”   > “配置文件”   > “创建配置文件”   > 针对平台选择“iOS”>  针对配置文件类型选择“设备限制”>  “显示或隐藏应用”  ）。 

可以输入 iTunes 应用商店 URL，例如 `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`。 在此更新中，`apps` 和`itunes` 均可用于 URL，例如：
- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

有关这些设置的详细信息，请参阅[显示或隐藏应用](../configuration/device-restrictions-ios.md#show-or-hide-apps)。

适用于：
- iOS

#### <a name="windows-10-compliance-policy-password-type-values-are-clearer-and-match-csp---5138985---"></a>Windows 10 合规性策略密码类型值更加清晰且匹配 CSP<!-- 5138985 -->
在 Windows 10 设备上，你可以创建需要特定密码功能的合规性策略（依次选择“设备合规性”   > “策略”   > “创建策略”   > 针对平台选择“Windows 10 及更高版本”>  “系统安全”  ）。 在此更新中：
- “密码类型”  值更加清晰，并更新以匹配 [DeviceLock/AlphanumericDevicePasswordRequired CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired)。
- “密码过期(天)”  设置将更新为允许 1-730 天内的值。 

有关 Windows 10 合规性设置的详细信息，请参阅 [Windows 10 及更高版本设置以将设备标记为合规或不合规](../protect/compliance-policy-create-windows.md)。 

适用于：
- Windows 10 及更高版本

 #### <a name="updated-ui-for-configuring-microsoft-exchange-on-premises-access---4092920---"></a>更新了用于配置 Microsoft Exchange 本地访问的 UI<!-- 4092920 -->  
我们更新了控制台，你可在其中[配置 Microsoft Exchange 本地访问权限](../protect/conditional-access-exchange-create.md)。 现在，可以在控制台上用于*启用 Exchange 本地访问控制*的同一个窗格中提供 Exchange 本地访问权限的所有配置。  

#### <a name="allow-or-restrict-adding-app-widgets-to-the-home-screen-on-android-enterprise-work-profile-devices---1109650----"></a>允许或限制将应用小组件添加到 Android Enterprise 工作配置文件设备上的主屏幕<!-- 1109650  --> 
在 Android Enterprise 设备上，你可以配置工作配置文件中的功能（依次选择“设备配置”   > “配置文件”   > 创建配置文件”   > 针对平台选择“Android Enterprise”>  “仅限工作配置文件”>  针对配置文件类型选择“设备限制”）。 在此更新中，可以允许用户将工作配置文件应用公开的小组件添加到设备主屏幕。

要查看可以配置的设置，请转到[便于使用 Intune 允许或限制功能的 Android Enterprise 设备设置](../configuration/device-restrictions-android-for-work.md)。

适用于：
- Android Enterprise 工作配置文件

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>设备注册

#### <a name="new-tenants-will-default-away-from-android-device-administrator-management---4869790-----"></a>新租户将默认离开 Android 设备管理员管理<!-- 4869790   -->
Android Enterprise 已取代 Android 的设备管理员功能。 因此，建议改为使用 Android Enterprise 进行新注册。 在将来的更新中，新租户需要在 Android 注册中完成以下先决条件步骤，才能使用设备管理员管理：转到“Intune”   > “设备注册”   > “Android 注册”   > “个人和企业所有的具有设备管理权限的设备”   > “使用设备管理员管理设备”  。

现有租户的环境不会有任何变化。

有关 Intune 中 Android 设备管理员的详细信息，请参阅 [Android 设备管理员注册](https://docs.microsoft.com/intune/android-enroll-device-administrator)。

#### <a name="list-of-dep-devices-associated-with-a-profile---5012045-idmiss---"></a>与配置文件关联的 DEP 设备的列表<!-- 5012045 idmiss -->
你现在可以查看与配置文件关联的 Apple 自动设备注册计划 (DEP) 设备的页面列表。 你可以从列表中的任何页面搜索列表。 要查看列表，请转到“Intune”   > “设备注册”   > “Apple 注册”   > “注册计划令牌”  > 选择令牌 >“配置文件”  > 选择配置文件 >“分配的设备”  （在“监视器”下  ）。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>设备管理

#### <a name="more-android-fully-managed-support---3464667-4631425-4631440-5227935-4062195-----"></a>更多 Android 完全托管支持<!-- 3464667, 4631425, 4631440, 5227935, 4062195   -->
我们为 Android 完全托管设备添加了以下支持：

- 完全托管 Android 的 SCEP 证书可用于作为设备所有者管理的设备上的证书身份验证。 工作配置文件设备上已支持 SCEP 证书。  有了针对设备所有者的 SCEP 证书，你将能够： <!-- 5227935 -->
    - 在 Android Enterprise 的 DO 部分下创建 SCEP 配置文件
    - 将 SCEP 证书链接到 DO Wi-Fi 配置文件以进行身份验证
    - 将 SCEP 证书链接到 DO VPN 配置文件以进行身份验证
    - 将 SCEP 证书链接到 DO 电子邮件配置文件以进行身份验证（通过 AppConfig）
- Android Enterprise 设备支持系统应用。 在 Intune 中，通过选择“客户端应用”   > “应用”   > “添加”  来添加 Android Enterprise 系统应用。 在“应用类型”  列表中，选择“Android Enterprise 系统应用”  。 有关详细信息，请参阅[将 Android Enterprise 系统应用添加到 Microsoft Intune](../apps/apps-ae-system.md)。 <!-- 4062195 -->
- 在“设备合规性”   > “Android Enterprise”   > “设备所有者”  中，你可以创建用于设置 Google SafetyNet 证明级别的合规性策略。   <!-- 4631425 -->
- 在 Android Enterprise 完全托管设备上，支持移动威胁防御提供程序。 在“设备合规性”   > “Android Enterprise”   > “设备所有者”  中，可以选择可接受的威胁级别。 <!-- 4631440 --> [使用 Intune 将设备标记为符合或不符合的 Android Enterprise 设置](../protect/compliance-policy-create-android-for-work.md#device-owner)会列出当前设置。
- 在 Android Enterprise 完全托管的设备上，现在可以通过应用配置策略配置 Microsoft Launcher 应用，以便在完全托管的设备上实现标准化的最终用户体验。 Microsoft Launcher 应用可用于个性化 Android 设备。 将该应用与 Microsoft 帐户或工作/学校帐户结合使用，可以访问个性化源中的日历、文档和最近活动。 <!-- 5334044 -->

有了此更新，我们很高兴地宣布 Intune 对 Android Enterprise 完全托管的支持现已正式发布。

适用于：

- Android Enterprise 完全托管设备

#### <a name="send-custom-notifications-to-a-single-device---4928910---"></a>向单个设备发送自定义通知<!-- 4928910 -->
现在，你可以选择单个设备，然后使用远程设备操作[仅向该设备发送自定义通知](../remote-actions/custom-notifications.md#send-a-custom-notification-to-a-single-device)。

#### <a name="wipe-and-passcode-reset-actions-arent-available-for-ios-devices-that-are-enrolled-by-using-user-enrollment---4950491---"></a>擦除和密码重置操作不适用于通过使用“用户注册”注册的 iOS 设备<!-- 4950491 -->
用户注册是一种新的 Apple 设备注册类型。 使用“用户注册”注册设备时，“擦除”和“密码重置”远程操作对此类设备不可用。

#### <a name="intune-support-for-ios-13-and-macos-catalina-devices---4665317---"></a>Intune 对 iOS 13 和 macOS Catalina 设备的支持<!-- 4665317 -->
Intune 现在支持管理 iOS 13 和 macOS Catalina 设备。
有关详细信息，请参阅 [Microsoft Intune 对 iOS 13 和 iPadOS 的支持博客文章](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-and-iPadOS/ba-p/861998)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>设备安全性

#### <a name="bitlocker-support-for-client-driven-recovery-password-rotation----3444125---"></a>对客户端驱动的恢复密码轮转的 BitLocker 支持<!--  3444125 -->
使用 Intune 终结点保护设置，可为运行 Windows 版本 1909 或更高版本的设备上的 BitLocker 配置[客户端驱动的恢复密码轮转](../protect/endpoint-protection-windows-10.md#windows-encryption)。

在 OS 驱动器恢复（通过使用 bootmgr 或 WinRE）和固定数据驱动器上的恢复密码解锁后，此设置启动客户端驱动的恢复密码刷新。 此设置将刷新使用的特定恢复密码，而卷上的其他未使用的密码仍保持不变。 有关详细信息，请参阅 BitLocker CSP 文档 [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)。

#### <a name="tamper-protection-for-windows-defender-antivirus---4705448----------"></a>Windows Defender 防病毒的篡改防护<!-- 4705448        -->
使用 Intune 管理 Windows Defender 防病毒的篡改防护  。 当将设备配置文件用于 Windows 10 终结点保护时，你将在 Microsoft Defender 安全中心组中找到[篡改防护设置](../protect/endpoint-protection-windows-10.md#windows-defender-security-center)。 你可以将“篡改防护”设置为“启用”  以开启篡改防护限制，设置为“禁用”  以关闭限制，或者设置为“未配置”  以保持设备的当前配置。  

有关篡改防护的详细信息，请参阅 Windows 文档中的[篡改防护防止安全设置更改](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection)。

#### <a name="advanced-settings-for-windows-defender-firewall-are-now-generally-available----5317392---------"></a>Windows Defender 防火墙高级设置现在已正式发布<!--  5317392       -->  
[用于终结点保护的 Windows Defender 自定义防火墙规则](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices)（配置为设备配置文件的一部分）已脱离公共预览版，并已正式发布 (GA)。  可以使用这些规则指定应用程序、网络地址和端口的入站和出站行为。 这些规则已在 7 月作为公共预览版发布。 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>基于角色的访问控制

#### <a name="scope-tags-now-support-terms-of-use-policies---2358863-idmiss---"></a>作用域标记现在支持“使用条款”策略<!-- 2358863 idmiss -->
现在，你可以将[作用域标记](scope-tags.md)分配给“使用条款”策略。 为此，请转到“Intune”   > “设备注册”   > “条款和条件”  > 在列表中选择一项 >“属性”   > “作用域标记”  > 选择作用域标记。

## <a name="week-of-september-9-2019"></a>2019 年 9 月 9 日当周

### <a name="app-management"></a>应用管理

#### <a name="updates-to-microsoft-intune-app---4997846---"></a>对 Microsoft Intune 应用的更新<!-- 4997846 -->
适用于 Android 的 Microsoft Intune 应用已更新，具有以下改进：
- 更新并改进了布局，包含最重要操作的底部导航。
- 添加了一个显示用户个人资料的附加页面。
- 在应用中为用户添加了对可操作通知（例如需要更新其设备设置）的显示。
- 添加了对自定义推送通知的显示，将应用与适用于 iOS 和 Android 的公司门户应用中最近新增的支持保持一致。 有关详细信息，请参阅[使用 Intune 发送自定义通知](../remote-actions/custom-notifications.md)。

#### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal---4394993---"></a>对于 iOS 设备，自定义公司门户的“注册过程隐私”屏幕<!-- 4394993 -->
使用 Markdown，可以自定义最终用户在 iOS 注册期间看到的公司门户的隐私屏幕。 具体来说，将能够自定义组织无法在设备上查看或执行的操作列表。 有关详细信息，请参阅[如何配置 Intune 公司门户应用](../apps/company-portal-app.md#privacy-statement-customization)。


## <a name="week-of-september-2-2019"></a>2019 年 9 月 2 日当周

### <a name="monitor-and-troubleshoot"></a>监视和故障排除

#### <a name="intune-user-interface-update--tenant-status-dashboard---5273210----"></a>Intune 用户界面更新 - 租户状态仪表板<!-- 5273210  -->
租户状态仪表板的用户界面已更新为与 Azure 用户界面样式保持一致。 有关详细信息，请参阅[租户状态](../tenant-status.md)。

## <a name="week-of-august-26-2019"></a>2019 年 8 月 26 日当周

### <a name="configure-microsoft-edge-settings-using-administrative-templates-for-windows-10-and-newer---5228061---"></a>使用适用于 Windows 10 和更高版本的管理模板配置 Microsoft Edge 设置<!-- 5228061 -->

在使用 Windows 10 和更高版本的设备上，可以创建管理模板以在 Intune 中配置组策略设置。 在此更新中，可以配置适用于 Microsoft Edge 版本 77 和更高版本的设置。

要详细了解管理模板，请参阅[使用 Windows 10 模板在 Intune 中配置组策略设置](../configuration/administrative-templates-windows.md)。

适用于：

- Windows 10 和更高版本 (Windows RS4+)

## <a name="week-of-august-12-2019"></a>2019 年 8 月 12 日当周

### <a name="app-management"></a>应用管理

#### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment---3504144-----"></a>控制设备取消注册时的 iOS 应用卸载行为<!-- 3504144   -->
管理员可以管理当设备在用户或设备组级别取消注册时，应用是被删除还是保留在设备上。 

#### <a name="categorize-microsoft-store-for-business-apps---3926922---"></a>为适用于企业的 Microsoft Store 应用分类<!-- 3926922 -->
可以对适用于企业的 Microsoft Store 应用进行分类。 为此，请依次选择“Intune”   > “客户端应用”   > “应用”  ，选择适用于企业的 Microsoft Store 应用，再依次选择“应用信息”   > “类别”  。 在下拉菜单上，分配类别。

#### <a name="customized-notifications-for-microsoft-intune-app-users---4843354----"></a>面向 Microsoft Intune 应用用户的自定义通知<!-- 4843354  -->
适用于 Android 的 Microsoft Intune 应用现在支持显示自定义推送通知，这与适用于 iOS 和 Android 的公司门户应用中最近新增的支持保持一致。 有关详细信息，请参阅[使用 Intune 发送自定义通知](../remote-actions/custom-notifications.md)。

### <a name="device-configuration"></a>设备配置

#### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode---3755304-3041943-3041946-----"></a>新增了适用于多应用模式下 Android Enterprise 专用设备的功能<!-- 3755304 3041943 3041946   -->

在 Intune 中，可以在 Android Enterprise 专用设备上通过展台样式体验来控制功能和设置（依次选择“设备配置”   > “配置文件”   > “创建配置文件”   > “Android Enterprise”  （作为平台）>“仅限设备所有者，设备限制”  （作为配置文件类型））。

在此更新中，新增了以下功能：

- “专用设备”   > “多应用”  ：虚拟主页按钮  可以通过在设备上向上轻扫来显示，也可以悬浮在屏幕上，这样用户就可以移动它。
- “专用设备”   > “多应用”  ：“闪光灯访问”  允许用户使用闪光灯。 
- “专用设备”   > “多应用”  ：“媒体音量控制”  允许用户使用滑块控制设备的媒体音量。 
- “专用设备”   > “多应用”  ：允许用户启用屏幕保护程序  ，上传自定义图像，并控制屏幕保护程序的显示时间。

要查看当前设置，请转到[便于使用 Intune 允许或限制功能的 Android Enterprise 设备设置](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings)。

适用于：

- Android Enterprise 专用设备

#### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices---3574215-3574238-3574235-3574232-----"></a>新增了适用于 Android Enterprise 完全托管设备的应用配置文件<!-- 3574215 3574238 3574235 3574232   -->
使用配置文件，可以配置设置，从而将 VPN、电子邮件和 Wi-Fi 设置应用于 Android Enterprise 设备所有者（完全托管）设备。 在此更新中，可以：

- 使用[应用配置策略](../apps/app-configuration-policies-use-android.md)来部署 Outlook、Gmail 和 Nine Work 电子邮件设置。
- 使用设备配置文件来部署[受信任的根证书设置](../protect/certificates-configure.md)。
- 使用设备配置文件来部署 [VPN](../configuration/vpn-settings-android-enterprise.md) 和 [Wi-Fi](../configuration/wi-fi-settings-android-enterprise.md) 设置。

> [!IMPORTANT]
> 利用此功能，用户可以使用 VPN、Wi-Fi 和电子邮件配置文件的用户名和密码进行身份验证。 目前，无法使用基于证书的身份验证。

适用于：  
- Android Enterprise 设备所有者（完全托管）

#### <a name="control-the-apps-files-documents-and-folders-that-open-when-users-sign-in-to-macos-devices--3914202-----"></a>控制在用户登录 macOS 设备后打开哪些应用、文件、文档和文件夹<!--3914202   -->
可以在 macOS 设备上启用和配置功能（依次选择“设备配置”   > “配置文件”   > “创建配置文件”   > “macOS”  （作为平台）>“设备功能”  （作为配置文件类型））。 

在此更新中，新增了“登录项”设置，用于控制在用户登录注册的设备后打开哪些应用、文件、文档和文件夹。 

若要查看当前设置，请转到 [Intune 中的 macOS 设备功能设置](../configuration/macos-device-features-settings.md)。

适用于：  
- macOS

#### <a name="deadlines-replace-engaged-restart-settings-for-windows-update-rings---4464404----------"></a>Windows 更新通道的“预定重启”设置替换为“截止时间”<!-- 4464404        -->
为了与最近的 [Windows 服务变更](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1903#servicing)保持一致，Intune 的 Windows 10 更新通道现在[支持“截止时间”设置](../protect/windows-update-settings.md)。 “截止时间”  确定设备何时安装功能和安全更新程序。  在运行 Windows 10 1903 或更高版本的设备上，“截止时间”  取代“预定重启”  配置。  未来在旧版 Windows 10 上，“截止时间”  也会取代“预定重启”  。  

如果你未配置“截止时间”，设备会继续使用“预定重启”设置，但在将来的更新中 Intune 将会不支持“预定重启”设置   。  

请计划对所有 Windows 10 设备使用“截止时间”  。 在“截止时间”  设置就位后，可以将 Intune 配置“预定重启”更改为“未配置”  。 设置为“未配置”后，Intune 会停止管理设备上的这些设置，但不会从设备中删除上次配置的这些设置。 因此，上次配置的“预定重启”  设置会继续处于活动状态并用于设备，直到这些设置被除 Intune 以外的其他方法修改。 稍后，当设备 Windows 版本发生更改时，或当 Intune 对“截止时间”  的支持扩展到设备 Windows 版本时，设备就会开始使用已就位的新设置。

#### <a name="support-for-multiple-microsoft-intune-certificate-connectors-----4704642--------"></a>支持多个 Microsoft Intune 证书连接器<!--   4704642      -->
Intune 现在支持安装和使用多个 [Microsoft Intune 证书连接器来执行 PKCS 操作](../protect/certficates-pfx-configure.md)。 此变更支持连接器的负载均衡和高可用性。 每个连接器实例都可以处理来自 Intune 的证书请求。  如果一个连接器不可用，其他连接器将继续处理请求。

无需升级到最新版连接器软件，即可使用多个连接器。  

#### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices---4867699-4867709-----"></a>限制 iOS 和 macOS 设备上功能的新设置和现有设置变更<!-- 4867699 4867709   -->
可以在运行 iOS 和 macOS 的设备上创建限制设置的配置文件（依次选择“设备配置”   > “配置文件”   > “创建配置文件”   > “iOS”  或“macOS”  （作为平台）>“设备限制”  ）。 此更新包括以下功能：

- 依次转到“macOS”   > “设备限制”   > “云和存储”  ，使用新设置“移交”  来阻止用户在一台 macOS 设备上启动工作，并继续在另一台 macOS 或 iOS 设备上工作。

  要查看最新设置，请转到[使用 Intune 允许或限制功能的 macOS 设备设置](../configuration/device-restrictions-macos.md)。

- 依次转到“iOS”   > “设备限制”  ，有下面的一些变更：

  - “内置应用”   > “查找我的 iPhone (仅限受监督)”  ：“查找我的应用”功能中新增阻止此功能的设置。 
  - “内置应用”   > “查找我的好友(仅限受监督)”  ：“查找我的应用”功能中新增阻止此功能的设置。 
  - “无线”   > “修改 Wi-Fi 状态(仅限受监督)”  ：新增阻止用户在设备上打开或关闭 Wi-Fi 的设置。
  - “键盘和字典”   > “QuickPath (仅限受监督)”  ：新增阻止 QuickPath 功能的设置。
  - “云和存储”  ：“活动延续”  重命名为“移交”  。

  要查看最新设置，请转到[使用 Intune 允许或限制功能的 iOS 设备设置](../configuration/device-restrictions-ios.md)。

适用于：  
- macOS 10.15 及更高版本
- iOS 13 及更高版本

#### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release---4867809-----"></a>随着 iOS 13.0 版本推出，一些适用于不受监督的 iOS 设备的限制将适用于仅限受监督的设备<!-- 4867809   -->
在此更新中，随着 iOS 13.0 版本推出，一些设置适用于仅限受监督的设备。 如果这些设置是在 iOS 13.0 版本推出前配置并分配到不受监督的设备，它们仍适用于不受监督的设备。 在设备升级到 iOS 13.0 后，它们仍适用。 这些限制不适用于已备份和还原的不受监督的设备。

这些设置包括：

- App Store、文档查看和游戏
  - App Store
  - iTunes 限制级音乐、播客或新闻内容
  - 添加 Game Center 好友
  - 多玩家游戏
- 内置应用
  - 照相机
    - FaceTime
  - Safari
    - 自动填充
- 云和存储
  - 备份到 iCloud
  - 阻止 iCloud 文档同步
  - 阻止 iCloud 密钥链同步

要查看最新设置，请转到[使用 Intune 允许或限制功能的 iOS 设备设置](../configuration/device-restrictions-ios.md)。

适用于：  
- iOS 13.0 及更高版本

#### <a name="improved-device-status-for-macos-filevault-encryption---4944983-----------"></a>针对 macOS FileVault 加密改进了设备状态<!-- 4944983         -->
我们针对 macOS 设备上的 FileVault 加密更新了[多个设备状态消息](../protect/encryption-monitor.md#device-encryption-status)。

#### <a name="some-windows-defender-antivirus-scan-settings-in-the-reporting-show-a-failed-status---5119229---"></a>报告中的一些 Windows Defender 防病毒扫描设置显示“失败”状态<!-- 5119229 -->
在 Intune 中，可以创建使用 Windows Defender 防病毒来扫描 Windows 10 设备的策略（依次选择“设备配置”   > “配置文件”   > “创建配置文件”   > “Windows 10 及更高版本”  （作为平台）> “设备限制”  （作为配置文件类型）>“Windows Defender 防病毒”  ）。 “执行每日快速扫描的时间”  和“要执行的系统扫描类型”  报告显示“失败”状态（实际为“成功”状态）。 

在此更新中，这种行为得到了修复。 因此，“执行每日快速扫描的时间”  和“要执行的系统扫描类型”  设置在扫描成功完成后显示“成功”状态，并在无法应用设置时显示“失败”状态。

若要详细了解 Windows Defender 防病毒设置，请参阅[使用 Intune 允许或限制功能的 Windows 10（及更高版本）设备设置](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus)。

### <a name="device-enrollment"></a>设备注册

#### <a name="default-scope-tags---3702875----"></a>默认作用域标记<!-- 3702875  -->
新增了内置默认作用域标记。 所有支持作用域标记的未标记 Intune 对象都会自动分配到默认作用域标记。 默认  作用域标记被添加到所有现有角色分配中，以与目前的管理员体验保持一致。 如果不想让管理员看到有默认作用域标记的 Intune 对象，请从角色分配中删除默认作用域标记。 此功能类似于 System Center Configuration Manager 中的安全作用域功能。 有关详细信息，请参阅[将 RBAC 和作用域标记用于分布式 IT](scope-tags.md)。

#### <a name="android-enrollment-device-administrator-support---4869749-----"></a>Android 注册设备管理员支持<!-- 4869749   -->
Android 设备管理员注册选项已添加到“Android 注册”页（依次转到“Intune”   > “设备注册”   > “Android 注册”  ）。 默认情况下，所有租户仍将启用 Android 设备管理员。  有关详细信息，请参阅 [Android 设备管理员注册](../enrollment/android-enroll-device-administrator.md)。

#### <a name="skip-more-screens-in-setup-assistant---4877451----"></a>跳过设置助理中的更多屏幕 <!--4877451  -->
可以将设备注册计划配置文件设置为，跳过以下设置助理屏幕：
- 适用于 iOS
    - 外观
    - Express 语言
    - 首选语言
    - 设备间迁移
- 对于 macOS
    - 屏幕时间
    - Touch ID 设置

若要详细了解设置助理的自定义项，请参阅[创建适用于 iOS 的 Apple 注册配置文件](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile)和[创建适用于 macOS 的 Apple 注册配置文件](../enrollment/device-enrollment-program-enroll-macos.md#create-an-apple-enrollment-profile)。

#### <a name="add-a-user-column-to-the-autopilot-device-csv-upload-process---3823054---"></a>将用户列添加到 Autopilot 设备 CSV 上传过程<!-- 3823054 -->
现在可以将用户列添加到 Autopilot 设备 CSV 上传内容中。 这样一来，就能在导入 CSV 时批量分配用户。 有关详细信息，请参阅[在 Intune 中使用 Windows AutoPilot 注册 Windows 设备](../enrollment/enrollment-autopilot.md)。


### <a name="device-management"></a>设备管理

#### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days--4231059----"></a>将自动设备清理时间限制配置缩短到 30 天<!--4231059  -->
可以将自动设备清理时间限制设置为，上次登录后 30 天（而不是之前的 90 天限制）。 为此，请依次转到“Intune”   > “设备”   > “设置”   > “设备清理规则”  。

#### <a name="build-number-included-on-android-device-hardware-page---4461910-----"></a>Android 设备“硬件”页上包含生成号<!-- 4461910   -->
每个 Android 设备的“硬件”页上都新增了包括设备操作系统生成号的条目。 有关详细信息，请参阅[使用 Intune 查看设备详细信息](../remote-actions/device-inventory.md)。


<!-- ########################## -->

## <a name="week-of-august-5-2019"></a>2019 年 8 月 5 日当周

### <a name="zebra-technologies-is-a-supported-oem-for-oemconfig-on-android-enterprise-devices---4843713---"></a>Zebra Technologies 是 Android Enterprise 设备上受支持的 OEMConfig OEM<!-- 4843713 -->

在 Intune 中，可以创建设备配置文件，并使用 OEMConfig 将设置应用于 Android Enterprise 设备（依次选择“设备配置”   > “配置文件”   > “创建配置文件”   > “Android Enterprise”  （作为平台）>“OEMConfig”  （作为配置文件类型））。

在此更新中，Zebra Technologies 是受支持的 OEMConfig 原始设备制造商 (OEM)。 若要详细了解 OEMConfig，请参阅[通过 OEMConfig 使用和管理 Android Enterprise 设备](../configuration/android-oem-configuration-overview.md)。

适用于：  
- Android Enterprise

<!-- ########################## -->

## <a name="week-of-july-22-2019"></a>2019 年 7 月 22 日当周 

### <a name="app-management"></a>应用管理

#### <a name="customized-notifications-for-users-and-groups---16766574------------"></a>发送给用户和组的自定义通知<!-- 16766574          -->
从公司门户应用向使用 Intune 管理的 iOS 和 Android 设备上的用户发送自定义推送通知。 这些移动推送通知是高度可自定义的免费文本，可以用于任何目的。 可以将它们的目标设定成组织中的不同用户组。 有关详细信息，请参阅[自定义通知](../remote-actions/custom-notifications.md)。

#### <a name="googles-device-policy-controller-app---3041950----"></a>Google 的 Device Policy Controller 应用<!-- 3041950  -->
托管主屏幕应用现在可以访问 Google 的 Android 设备策略应用。 托管主屏幕应用是一种自定义启动器，用于使用多应用展台模式在 Intune 中注册为 Android Enterprise (AE) 专用设备的设备。 你可以访问 Android 设备策略应用，或引导用户访问 Android 设备策略应用，以获取支持和进行调试。 此启动功能在设备注册并锁定到托管主屏幕时可用。 无需其他安装项，即可使用此功能。

#### <a name="outlook-protection-settings-for-ios-and-android-devices---3212619---"></a>适用于 iOS 和 Android 设备的 Outlook 保护设置<!-- 3212619 -->
现在可以使用简单的 Intune 管理控件，配置用于 Outlook for iOS 和 Outlook for Android 的常规应用配置设置和数据保护配置设置，而无需注册设备。 常规应用配置设置等同于，管理员在管理已注册设备上的 Outlook for iOS 和 Outlook for Android 时可以启用的设置。 若要详细了解 Outlook 设置，请参阅[部署 Outlook for iOS 和 Outlook for Android 应用配置设置](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)。

### <a name="device-configuration"></a>设备配置

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910-eeready---idstaged---"></a>在创建 Windows 10 设备配置配置文件时使用“适用性规则” <!-- 2549910 eeready   idstaged -->

可以创建 Windows 10 设备配置文件，具体方法为依次单击“设备配置”   > “配置文件”   > “创建配置文件”   > “Windows 10”  （作为平台）>“适用性规则”  。 在此次更新中，可以创建适用性规则  ，让配置文件仅应用于特定版本。 例如，创建一个启用某些 BitLocker 设置的配置文件。 添加配置文件后，请使用适用性规则，使配置文件仅适用于运行 Windows 10 企业版的设备。

若要添加适用性规则，请参阅[适用性规则](../configuration/device-profile-create.md#applicability-rules)。

适用于：Windows 10 及更高版本

#### <a name="use-tokens-to-add-device-specific-information-in-custom-profiles-for-ios-and-macos-devices---3330008----"></a>使用标记在 iOS 和 macOS 设备的自定义配置文件中添加设备专用信息<!-- 3330008  -->
可以使用 iOS 和 macOS 设备上的自定义配置文件，配置没有内置到 Intune 中的设置和功能，具体方法为依次单击“设备配置”   > “配置文件”   > “创建配置文件”   > “iOS”  或“macOS”  （作为平台）>“自定义”  （作为配置文件类型）。 在此次更新中，你可以向 `.mobileconfig` 文件添加标记，用于添加设备专用信息。 例如，可以将 `Serial Number: {{serialnumber}}` 添加到配置文件，用于显示设备序列号。

若要创建自定义配置文件，请参阅 [iOS 自定义设置](../configuration/custom-settings-ios.md)或 [macOS 自定义设置](../configuration/custom-settings-macos.md)。

适用于：
- iOS
- macOS

#### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise---3712769-----"></a>在创建 Android Enterprise 的 OEMConfig 配置文件时使用新配置设计器<!-- 3712769   -->
在 Intune 中，可以创建使用 OEMConfig 应用的设备配置文件，具体方法为依次单击“设备配置”>“配置文件”>“创建配置文件”>“Android Enterprise”（作为平台）>“OEMConfig”（作为配置文件类型）。 当你这样做时，系统会打开 JSON 编辑器，其中包含模板和值以供你更改。 

在此次更新中，我们新增了配置设计器，它的用户体验更佳，显示应用中嵌入的详细信息，包括标题、说明等。 JSON 编辑器仍可用，并显示你在配置设计器中所做的任何更改。

若要查看当前设置，请转到[通过 OEMConfig 使用和管理 Android Enterprise 设备](../configuration/android-oem-configuration-overview.md)。

适用于：Android Enterprise

#### <a name="updated-ui-for-configuring-windows-hello---4089576--------------"></a>更新了用于配置 Windows Hello 的 UI<!-- 4089576            -->
我们更新了用于[将 Intune 配置为使用 Windows Hello 企业版](../protect/windows-hello.md)的控制台。 所有配置设置现在都位于用于启用支持 Windows Hello 的控制台的同一个窗格中。

#### <a name="intune-powershell-sdk---4924113---"></a>Intune PowerShell SDK<!-- 4924113 --> 
通过 Microsoft Graph 支持 Intune API 的 Intune PowerShell SDK 已更新到版本 6.1907.1.0。 SDK 现在支持以下功能：
- 用于 Azure 自动化。
- 支持仅限应用的身份验证读取操作。 
- 支持将易记的缩短名称用作别名。
- 符合 PowerShell 命名约定。 具体而言，`Connect-MSGraph` cmdlet 上的 `PSCredential` 参数已重命名为 `Credential`。
- 支持在使用 `Invoke-MSGraphRequest` cmdlet 时手动指定 `Content-Type` 标头的值。

有关详细信息，请参阅[用于 Microsoft Intune Graph API 的 PowerShell SDK](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune)。


### <a name="device-enrollment"></a>设备注册

#### <a name="updates-for-enrollment-restrictions---2871968---"></a>更新了注册限制<!-- 2871968 -->
新租户的注册限制已更新为，默认允许 Android Enterprise 工作配置文件。 现有租户不会有任何变化。 若要使用 Android Enterprise 工作配置文件，仍需[将 Intune 帐户连接到托管的 Google Play 帐户](../enrollment/connect-intune-android-enterprise.md)。

#### <a name="ui-updates-for-apple-enrollment-and-enrollment-restrictions--4089575-4089579----"></a>更新了用于 Apple 注册和注册限制的 UI<!--4089575, 4089579  -->
以下两个过程都使用向导样式的用户界面：
- Apple 设备注册。 有关详细信息，请参阅[通过 Apple 设备注册计划自动注册 iOS 设备](../enrollment/device-enrollment-program-enroll-ios.md)。
- 注册限制创建。 有关详细信息，请参阅[创建注册限制](../enrollment/enrollment-restrictions-set.md)。

#### <a name="handling-pre-configuration-of-corporate-device-identifiers-for-android-q-devices---4711509--idmiss---"></a>处理如何预配置 Android Q 设备的企业设备标识符<!-- 4711509  idmiss -->
在 Android Q (v10) 中，Google 将撤消旧版托管（设备管理员）Android 设备上的 MDM 代理收集设备标识符信息的功能。  Intune 有一项功能，可便于 IT 管理员[预配置设备序列号或 IMEI 列表](../enrollment/corporate-identifiers-add.md#identify-corporate-owned-devices-with-imei-or-serial-number)，以便自动将这些设备标记为企业所有。 此功能不适用于由设备管理员托管的 Android Q 设备。  无论设备的序列号或 IMEI 是否已上传，设备在 Intune 注册过程中始终被视为个人设备。  注册后，可以手动将所有权切换给企业。  这只影响了新注册的设备，而现有已注册设备则不受影响。  使用工作配置文件托管的 Android 设备不受此更改的影响，并将继续按目前的方式运行。  另外，注册为设备管理员的 Android Q 设备无法再将 Intune 控制台中的序列号或 IMEI 作为设备属性进行报告。

#### <a name="icons-have-changed-for-android-enterprise-enrollments-work-profile-dedicated-devices-and-fully-managed-devices---4977730---"></a>更改了用于 Android Enterprise 注册（工作配置文件、专用设备和完全托管设备）的图标<!-- 4977730 -->
Android Enterprise 注册配置文件的图标已更改。 若要查看新图标，请先依次转到“Intune”   > “注册”   > “Android 注册”  ，再在“注册配置文件”下查看  。


#### <a name="windows-diagnostic-data-collection-change---4113859---"></a>更改了 Windows 诊断数据收集<!-- 4113859 -->
对于运行 Windows 10 版本 1903 及更高版本的设备，用于诊断数据收集的默认值已更改。 自 Windows 10 1903 起，默认启用了诊断数据收集。 Windows 诊断数据是来自 Windows 设备的至关重要技术数据，包含设备相关信息以及 Windows 和相关软件的性能。 有关详细信息，请参阅[配置组织中的 Windows 诊断数据](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization)。 Autopilot 设备也选择启用“全”遥测，除非在 Autopilot 配置文件中使用 [System/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry) 进行了其他设置。

### <a name="device-management"></a>设备管理

#### <a name="improve-device-location---3855417----"></a>改进了设备位置<!-- 3855417  -->
可以使用“定位设备”  操作来放大到设备的确切坐标。 若要详细了解如何定位丢失的 iOS 设备，请参阅[查找丢失的 iOS 设备](../remote-actions/device-locate.md)。

### <a name="device-security"></a>设备安全性

#### <a name="advanced-settings-for-windows-defender-firewall--public-preview----1311949-------"></a>Windows Defender 防火墙（公共预览版）的高级设置<!--  1311949     -->  
使用 Intune 管理[作为设备配置文件一部分的自定义防火墙规则](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices)，以在 Windows 10 设备上实现终结点保护。 规则可以指定应用程序、网络地址和端口的入站和出站行为。 

#### <a name="updated-ui-for-managing-security-baselines---4091125-------"></a>更新了用于管理安全基线的 UI<!-- 4091125     -->
我们在 Intune 控制台中更新了安全基线的[创建和编辑体验](../protect/security-baselines.md#create-the-profile)。 具体更改包括：

简化了向导样式格式，已压缩为一个边栏选项卡 。 这项新设计杜绝了边栏选项卡扩张，IT 专业人员不再需要向下钻取多个单独的窗格。  
现在可以在创建和编辑基线的过程中创建分配，而不必稍后返回来分配基线。 我们添加了设置摘要，你可以在新建基线和编辑现有基线前查看。 编辑时，摘要只显示正在编辑的一个属性类别中设置的项列表。

<!-- ########################## -->

## <a name="week-of-july-15-2019"></a>2019 年 7 月 15 日当周 

### <a name="app-management"></a>应用管理

#### <a name="managed-home-screen-and-managed-settings-icons---4918107---"></a>Managed Home Screen 应用图标和“托管设置”图标<!-- 4918107 -->
Managed Home Screen 应用图标和“托管设置”  图标已更新。 Managed Home Screen 应用仅用于，在 Intune 中注册为 Android Enterprise (AE) 的专用设备，且在多应用展台模式下运行的设备。 若要详细了解 Managed Home Screen 应用，请参阅[配置用于 Android Enterprise 的 Microsoft Managed Home Screen 应用](../apps/app-configuration-managed-home-screen-app.md)。

#### <a name="android-device-policy-on-android-enterprise-dedicated-devices---4918136---"></a>Android Enterprise 专用设备上的 Android Device Policy<!-- 4918136 -->
可以从 Managed Home Screen 应用的调试屏幕访问 Android Device Policy 应用。 Managed Home Screen 应用仅用于，在 Intune 中注册为 Android Enterprise (AE) 的专用设备，且在多应用展台模式下运行的设备。 有关详细信息，请参阅[配置用于 Android Enterprise 的 Microsoft Managed Home Screen 应用](../apps/app-configuration-managed-home-screen-app.md)。

#### <a name="ios-company-portal-updates---3902931---"></a>更新了 iOS 公司门户<!-- 3902931 -->
iOS 应用管理提示中的公司名称将替换当前的“i.manage.microsoft.com”文本。 例如，当尝试从公司门户安装 iOS 应用或允许管理应用时，用户将看到公司名称，而不是“i.manage.microsoft.com”。 这将在未来几天内向所有客户推出。

### <a name="device-configuration"></a>设备配置

#### <a name="manage-filevault-for-macos----3858502--4557986--1210104----"></a>管理用于 macOS 的 FileVault<!--  3858502 + 4557986 + 1210104  -->
可以使用 Intune [管理用于 macOS 设备的 FileVault 密钥加密](../protect/encrypt-devices.md)。 若要加密设备，请使用终结点保护设备配置文件。

我们对 FileVault 的支持包括，加密未加密设备、托管设备个人恢复密钥、自动或手动轮换个人加密密钥，以及检索企业设备密钥。 最终用户还可以使用公司门户网站来获取加密设备的个人恢复密钥。

我们还扩展了加密报告，增加了 BitLocker 的 [FileVault 相关信息](../protect/encryption-monitor.md)，这样你就可以在一个地方集中查看所有设备加密详细信息了。

### <a name="device-enrollment"></a>设备注册

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user---4156123---"></a>Windows Autopilot 重置导致设备的主要用户遭删除<!-- 4156123 -->
如果设备使用 Autopilot 重置，设备的主要用户将会遭删除。 在重置后登录的下一个用户将被设置为主要用户。 此功能将在未来几天内向所有客户推出。

## <a name="week-of-july-8-2019"></a>2019 年 7 月 8 日当周

### <a name="new-office-windows-and-onedrive-settings-in-windows-10-administrative-templates----3510695---"></a>Windows 10 管理模板中新增 Office、Windows 和 OneDrive 设置 <!-- 3510695 -->

可以在 Intune 中创建模拟本地组策略管理的管理模板，具体方法为依次单击“设备管理”   > “配置文件”   > “创建配置文件”   > “Windows 10 及更高版本”  （作为平台）>“管理模板”  （作为配置文件类型）。

在此次更新中，我们新增了更多可添加到模板中的 Office、Windows 和 OneDrive 设置。 现在，利用这些新设置，可以配置超过 2500 项完全基于云的设置。

若要详细了解此功能，请参阅[使用 Windows 10 模板在 Intune 中配置组策略设置](../configuration/administrative-templates-windows.md)。

适用于：Windows 10 及更高版本

## <a name="week-of-july-1-2019"></a>2019 年 7 月 1 日当周 

### <a name="app-management"></a>应用管理

#### <a name="aad-and-app-on-android-enterprise-devices---3574267---"></a>Android Enterprise 设备上的 AAD 和 APP<!-- 3574267 -->
上手使用完全托管 Android Enterprise 设备时，用户现在会在初始设置新设备或恢复出厂设置的设备期间，向 Azure Active Directory (AAD) 注册。 之前，对于完全托管设备，在设置完成后，用户必须手动启动 Microsoft Intune 应用，才能启动 AAD 注册过程。 现在，当用户在初始设置后登陆设备主页时，设备就已注册。

除了更新了 AAD 之外，现在还支持在完全托管 Android Enterprise 设备上运行 Intune 应用保护策略 (APP)。 此功能将在我们推出后可用。有关详细信息，请参阅[使用 Intune 将托管 Google Play 应用添加到 Android Enterprise 设备](../apps/apps-add-android-for-work.md)。

## <a name="week-of-june-24-2019"></a>2019 年 6 月 24 日当周

### <a name="app-management"></a>应用管理

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data---3145939---"></a>配置允许哪种浏览器链接到组织数据<!-- 3145939 -->
现在，借助 Android 和 iOS 设备上的 Intune 应用保护策略 (APP)，可以将 组织网页链接
转移到特定浏览器，而不仅仅是 Intune Managed Browser 和 Microsoft Edge。  有关 APP 的详细信息，请参阅[什么是应用保护策略？](../apps/app-protection-policy.md)。

#### <a name="all-apps-page-identifies-onlineoffline-microsoft-store-for-business-apps--4089647---"></a>“所有应用”页标识适用于企业的 Microsoft Store 联机/脱机应用<!--4089647 -->
“所有应用”  页现在包含标签，用于将适用于企业的 Microsoft Store (MSFB) 应用识别为联机或脱机应用。 每个 MSFB 应用现在都包含“Online”  或“Offline”  后缀。 应用详细信息页还包含“许可证类型”  和“支持设备上下文安装”  （仅限脱机许可应用）信息。

#### <a name="company-portal-app-on-windows-shared-devices--4393553---"></a>Windows 共享设备上的公司门户应用<!--4393553 -->
用户现在可以在 Windows 共享设备上访问公司门户应用。 最终用户会在设备磁贴上看到“共享”  标签。 这适用于 Windows 公司门户应用版本 10.3.45609.0 及更高版本。

#### <a name="view-all-installed-apps-from-new-company-portal-web-page---4224326---"></a>从新版公司门户网页查看所有已安装应用<!-- 4224326 -->
公司门户网站的新增“已安装应用”  页面将列出用户设备上安装的所有（要求安装和允许安装的）托管应用。 除了分配类型，用户还可以看到应用的发布者、发布日期和当前安装状态。 如果你并未要求或允许用户安装任何应用，则用户将看到一条消息，说明尚未安装任何公司应用。 若要在 Web 上查看新页面，请转到[公司门户网站](https://portal.manage.microsoft.com)，并单击“已安装应用”  。  

#### <a name="new-view-lets-app-users-see-all-managed-apps-installed-on-device---2352913---"></a>新增视图，可让应用用户查看设备上安装的所有托管应用<!-- 2352913 -->  
现在，适用于 Windows 的公司门户应用将列出用户设备上安装的所有（要求安装和允许安装的）托管应用。 用户还可以看到已尝试和待处理的应用安装及其当前状态。 如果你并未要求或允许用户安装应用，则用户将看到一条消息，说明尚未安装任何公司应用。 若要查看新视图，请转到公司门户的导航窗格，并选择“应用”   > “已安装应用”  。

### <a name="device-configuration"></a>设备配置

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices---2043024---"></a>在 macOS 设备上配置内核扩展的设置<!-- 2043024 -->
在 macOS 设备上，可以创建设备配置文件（依次选择“设备配置” > “配置文件” > “创建配置文件”> 针对平台选择“macOS”）     。 在此次更新中，我们新增了一组设置，可便于你在设备上配置和使用内核扩展。 你可以添加特定扩展，也可以允许来自特定合作伙伴或开发人员的所有扩展。

若要详细了解此功能，请参阅[内核扩展概述](../configuration/kernel-extensions-overview-macos.md)和[内核扩展设置](../configuration/kernel-extensions-settings-macos.md)。

适用于：macOS 10.13.2 及更高版本

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options---2697002---"></a>Windows 10 设备的“仅来自 Store 的应用”的设置包括更多配置选项<!-- 2697002 -->
为 Windows 设备创建设备限制配置文件时，可以使用“仅来自 Store 的应用”设置  ，使用户仅从 Windows 应用商店安装应用（“设备配置”   > “配置文件”   > “创建配置文件”   > 平台为“Windows 10 和更高版本”  >配置文件类型为“设备限制”  ）。 在此次更新中，我们扩展了这项设置，以支持更多选项。

若要查看新设置，请转到[允许或限制功能的 Windows 10（及更高版本）设备设置](../configuration/device-restrictions-windows-10.md#app-store)。

适用于：Windows 10 及更高版本

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group---4089955---"></a>将多个 Zebra 移动扩展设备配置文件部署到一台设备、同一用户组或同一设备组<!-- 4089955 -->
在 Intune 中，可以使用设备配置文件中的 Zebra 移动性扩展 (MX)，为没有内置到 Intune 中的 Zebra 设备自定义设置。 目前，可以将一个配置文件部署到一台设备。 在此次更新中，你可以将多个配置文件部署到：
- 同一用户组
- 同一设备组
- 一台设备

[通过 Microsoft Intune 中的 Zebra 移动扩展来使用和管理 Zebra 设备](../configuration/android-zebra-mx-overview.md)显示了如何在 Intune 中使用 MX。

适用于：Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow---4404075----"></a>iOS 设备上的一些展台设置是使用“阻止”（替代“允许”）设置的<!-- 4404075  -->
在 iOS 设备上创建设备限制配置文件时（“设备配置”   > “配置文件”   > “创建配置文件”   > 平台为“iOS”  >配置文件类型为“设备限制”  >“展台”  ），可以设置“自动锁定”  、“响铃切换”  、“屏幕旋转”  、“屏幕睡眠按钮”  和“音量按钮”  。

在此次更新中，值是“阻止”  （阻止此功能）或“未配置”  （允许此功能）。 若要查看设置，请转到[允许或限制功能的 iOS 设备设置](../configuration/device-restrictions-ios.md#kiosk)。

适用于：iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices---4490704---"></a>在 iOS 设备上使用人脸 ID 进行密码身份验证<!-- 4490704 -->
创建用于 iOS 设备的设备限制配置文件时，可将指纹用作密码。 在此次更新中，指纹密码设置还允许面部识别，具体方法为依次单击“设备配置”   > “配置文件”   > “创建配置文件”   > “iOS”  （作为平台）>“设备限制”  （作为配置文件类型）>“密码”  。 因此，更改了以下设置：

- “指纹解锁”现在更改为“Touch ID 和 Face ID 解锁”   。
- 指纹修改（仅限监管模式）现在更改为“Touch ID 和 Face ID 修改（仅限监管模式）”   。

Face ID 可在 iOS 11.0 和更高版本中使用。 若要查看设置，请转到[使用 Intune 允许或限制功能的 iOS 设备设置](../configuration/device-restrictions-ios.md#password)。

适用于：iOS

#### <a name="restricting-gaming-and-app-store-features-on-ios-devices-is-now-dependent-on-ratings-region---4593948---"></a>限制 iOS 设备上的游戏和应用商店功能现在取决于分级区域<!-- 4593948 -->
在 iOS 设备上，可以允许或限制与游戏、应用商店和查看文档相关的功能（“设备配置”   > “配置文件”   > “创建配置文件”   >  平台为“iOS”  > 配置文件类型为“设备限制”  >“应用商店、文档查看、游戏”  ）。 此外还可以选择分级区域，例如美国。

在此次更新中，“应用”  功能更改为“分级区域”  的子级，且依赖“分级区域”  。 若要查看设置，请转到[使用 Intune 允许或限制功能的 iOS 设备设置](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming)。

适用于：iOS

### <a name="device-enrollment"></a>设备注册

#### <a name="windows-autopilot-support-for-hybrid-azure-ad-join---4809146--"></a>Windows Autopilot 支持混合 Azure AD 联接<!-- 4809146-->
除了现有的 Azure AD 联接支持之外，现有设备的 Windows Autopilot 现在还支持混合 Azure AD 联接。 适用于运行 Windows 10 版本 1809 及更高版本的设备。 有关详细信息，请参阅[现有设备的 Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices)。

### <a name="device-management"></a>设备管理

#### <a name="see-the-security-patch-level-for-android-devices---4461911---"></a>查看 Android 设备的安全修补程序级别<!-- 4461911 -->
现在可以查看 Android 设备的安全修补程序级别。 为此，请先依次选择“Intune”   > “设备”   > “所有设备”  ，再选择设备和“硬件”  。
此时，“操作系统”  部分列出了修补程序级别。

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group---3173810---"></a>将范围标记分配给安全组中的所有托管设备<!-- 3173810 -->
现在可以将范围标记分配给安全组，安全组中的所有设备也会与这些范围标记关联。 这些组中的所有设备也将分配有范围标记。 使用此功能设置的范围标记将覆盖使用当前设备范围标记流设置的范围标记。 有关详细信息，请参阅[将 RBAC 和范围标记用于分布式 IT](scope-tags.md)。

### <a name="device-security"></a>设备安全性

#### <a name="use-keyword-search-with-security-baselines------"></a>对安全基线使用关键字搜索<!--  -->
创建或编辑[安全基线配置文件](../protect/security-baselines.md#create-the-profile)时，可以在新“搜索”  栏中指定关键字，以从可用设置组中筛选出与搜索条件匹配的设置组。

#### <a name="the-security-baselines-feature-is-now-generally-available---3785395---"></a>安全基线功能现已推出正式版<!-- 3785395 -->
安全基线  功能已不再处于预览阶段，现已推出正式版 (GA)。  也就是说，此功能可供在生产中使用。 不过，各个基线模板可能仍处于预览阶段，并按自己的计划接受评估并推出正式版。

#### <a name="the-mdm-security-baseline-template-is-now-generally-available---3794072-4217151--3534649---"></a>MDM 安全基线模板现已推出正式版<!-- 3794072, 4217151,  3534649 -->
MDM 安全基线模板已不再处于预览阶段，现已推出正式版 (GA)。 此 GA 模板的标识为“2019 年 5 月 MDM 安全基线”  。  这是新模板，而不是从预览版升级的模板。  由于它是新模板，你需要先审阅[它包含的设置](../protect/security-baseline-settings-mdm.md)，再新建将此模板部署到设备的配置文件。 其他安全基线模板可能仍处于预览阶段。 有关可用基线的列表，请参阅[可用安全基线](../protect/security-baselines.md#available-security-baselines)。  

“2019 年 5 月 MDM 安全基线”  除了是新模板之外，还包含我们最近在开发文章中公布的两项设置：  
- 越过锁定：语音激活屏幕锁定的应用  
- DeviceGuard：在下次重启设备时使用基于虚拟化的安全性 (VBS)。  

“2019 年 5 月 MDM 安全基线”  还新增了几项新设置，删除了其他一些设置，并修订了一项设置的默认值。 有关从预览版到 GA 的更改的详细列表，请参阅“新模板中发生了什么变化”  。

#### <a name="security-baseline-versioning---3194322---"></a>安全基线版本控制<!-- 3194322 -->
用于 Intune 的安全基线支持版本控制。 借助此支持，在每个安全基线的新版本发布时，可以将现有安全基线配置文件更新为使用更高版本的基线，而无需从头开始重新创建和部署新基线。 此外，在 Intune 控制台中，还可以查看每个基线的相关信息，如使用基线的各个配置文件的数量、配置文件使用的不同基线版本的数量，以及特定安全基线的最新版本的发布时间。  有关详细信息，请参阅**安全基线**。

#### <a name="the-use-security-keys-for-sign-in-setting-has-moved---4501151---"></a>“使用安全密钥登录”设置已移动<!-- 4501151 -->
用于标识保护的设备配置设置“使用安全密钥登录”  不再是“配置 Windows Hello 企业版”  的子设置。 它现在是始终可用的顶级设置，即使你没有启用 Windows Hello 企业版，也不例外。 有关详细信息，请参阅[标识保护](../protect/identity-protection-windows-settings.md)。

### <a name="role-based-access-control"></a>基于角色的访问控制

#### <a name="new-permissions-for-assigned-group-admins---4504437-----"></a>新增了已分配的组管理员的权限<!-- 4504437   -->
Intune 的内置学校管理员角色现在对托管应用拥有创建、读取、更新和删除 (CRUD) 权限。 也就是说，在此次更新中，如果你在 Intune for Education 中被分配为组管理员，现在可以创建、查看、更新和删除 iOS MDM Push Certificate、iOS MDM 服务器令牌和 iOS VPP 令牌，此外还拥有[所有现有权限](https://docs.microsoft.com/intune-education/group-admin-delegate#group-admin-permissions)。 若要执行其中任何一项操作，请依次转到“租户设置”   > “iOS 设备管理”  。  

#### <a name="applications-can-use-the-graph-api-to-call-read-operations-without-user-credentials---4655885---"></a>应用可以使用 Graph API 来调用读取操作，而无需使用用户凭据<!-- 4655885 -->
应用可以通过应用标识来调用 Intune Graph API 读取操作，而无需使用用户凭据。 若要详细了解如何访问用于 Intune 的 Microsoft Graph API，请参阅[在 Microsoft Graph 中使用 Intune](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)。

#### <a name="apply-scope-tags-to-microsoft-store-for-business-apps---4392555---"></a>将范围标记应用于适用于企业的 Microsoft Store 应用<!-- 4392555 -->
现在可以将范围标记应用于适用于企业的 Microsoft Store 应用。 若要详细了解范围标记，请参阅[将基于角色的访问控制 (RBAC) 和范围标记用于分布式 IT](scope-tags.md)。

## <a name="week-of-june-17-2019"></a>2019 年 6 月 17 日当周

### <a name="app-management"></a>应用管理

#### <a name="new-features-in-microsoft-intune-app"></a>Microsoft Intune 应用中的新功能
我们已向适用于 Android 的 Microsoft Intune 应用（预览版）添加新功能。 完全托管的 Android 设备上的用户现在可以：  

* 查看和管理通过 Intune 公司门户或 Microsoft Intune 应用注册的设备。
* 联系他们的组织以获取支持。
* 向 Microsoft 发送反馈。
* 如果组织已制定相关条款和条件，请进行查阅。

## <a name="week-of-june-10-2019"></a>2019 年 6 月 10 日当周

### <a name="app-management"></a>应用管理

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github---2653471---"></a>显示 GitHub 上提供的 Intune SDK 集成的新示例应用<!-- 2653471 -->
msintuneappsdk GitHub 帐户新增了适用于 iOS (Swift)、Android、Xamarin.iOS、Xamarin Forms 和 Xamarin.Android 的新示例应用。 这些应用旨在补充现有文档并演示如何将 Intune APP SDK 集成到自己的移动应用中。 如果你是需要其他 Intune SDK 指南的应用开发人员，请参阅以下链接示例：
- [Chatr](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App) - 使用 Azure Active Directory 身份验证库 (ADAL) 进行中转身份验证的原生 iOS (Swift) 即时消息应用
。
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App) - 使用 ADAL 进行中转身份验证的原生 Android 待办事项列表应用
。
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps) - 使用 ADAL 进行代理身份验证的 Xamarin.Android 待办事项列表应用，此存储库还具有 Xamarin.Forms 应用。
- [Xamarin.iOS 示例应用](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) - 基本 Xamarin.iOS 示例应用。

## <a name="week-of-may-27-2019"></a>2019 年 5 月 27 日当周

### <a name="app-management"></a>应用管理

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices---4223162---"></a>报告 Android 设备上可能有害的应用<!-- 4223162 -->
Intune 现在提供有关 Android 设备上可能有害的应用的其他报告信息。 

## <a name="week-of-may-20-2019"></a>2019 年 5 月 20 日当周

### <a name="app-management"></a>应用管理

#### <a name="windows-company-portal-app---3316993---"></a>Windows 公司门户应用<!-- 3316993 -->
Windows 公司门户应用将具有一个标记为“设备”的新页面  。 “设备”页面将显示最终用户已注册的所有设备  。 在用户使用 10.3.4291.0 或更高版本时，公司门户中将显示此更改。 要了解如何配置公司门户，请参阅[如何配置 Microsoft Intune 公司门户应用](../apps/company-portal-app.md)。

### <a name="device-enrollment"></a>设备注册

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Autopilot 设备的 OrderID 属性名称已更改为“组标记” <!-- 4659453 -->

为更直观地显示，Autopilot 设备上的 OrderID 属性名称已更改“组标记”   。 在使用 CSV 上传 Autopilot 设备信息时，必须使用“组标记”而不是 OrderID 作为列标题。  

## <a name="week-of-may-13-2019"></a>2019 年 5 月 13 日当周

### <a name="app-management"></a>应用管理

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation---1927359----"></a>Intune 策略更新身份验证方法和公司门户应用安装<!-- 1927359  -->
在已经由“设置助理”注册的设备上（通过 Apple 公司设备注册方法之一），Intune 将不再支持由最终用户从应用商店手动安装的公司门户。 仅当在注册过程中使用 Apple 设置助理进行身份验证时，此更改才适用。 此更改也只会影响通过以下方式注册的 iOS 设备：  
* Apple 配置器

* Apple Business Manager

* Apple School Manager

* Apple 设备注册计划 (DEP)

如果用户从应用商店安装公司门户应用，然后尝试通过该应用注册这些设备，则他们将收到错误。 这些设备应仅在注册过程中通过 Intune 自动推送时，才会使用公司门户。 将更新 Azure 门户中的 Intune 注册配置文件，以便你可以指定设备的身份验证方式以及是否收到公司门户应用。 如果希望 DEP 设备用户具有公司门户，则需要在注册配置文件中指定你的首选项。 

此外，iOS 公司门户中的  “标识设备”屏幕将被删除。 因此，想要启用条件访问或部署公司应用的管理员必须更新 DEP 注册配置文件。 仅当使用设置助理对 DEP 注册进行身份验证时，此要求才适用。 在这种情况下，必须将公司门户推送到设备上。 为此，请选择“Intune” > “设备注册” > “Apple 注册” > “注册计划令牌”，依次选择令牌和“配置文件”，选择配置文件，再选择“属性”，然后将“安装公司门户”设置为“是”         。

若要在已注册的 DEP 设备上安装公司门户，需要转到“Intune”>“客户端应用”，并将其作为具有应用配置策略的托管应用进行推送。 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy---3568384---"></a>配置最终用户使用应用保护策略更新业务线 (LOB) 应用的方式<!-- 3568384 -->
用户现在可以配置最终用户可获取业务线 (LOB) 应用的更新版本的位置。 最终用户将在“最低应用版本”  条件启动对话框中看到此功能，系统将提示最终用户更新到 LOB 应用的最低版本。 必须提供这些更新详细信息作为 LOB 应用保护策略（APP）的一部分。 此功能在 iOS 和 Android 中可用。 在 iOS 上，此功能要求应用与 Intune SDK for iOS v. 10.0.7 或更高版本集成（或使用包装工具包装）。 在 Android 上，此功能需要使用最新的公司门户。 若要配置最终用户更新 LOB 应用的方式，应用需要使用键 `com.microsoft.intune.myappstore` 发送给它的托管应用配置策略。 发送的值将定义最终用户从哪个应用商店中下载应用。 如果应用是通过公司门户部署的，则值必须为 `CompanyPortal`。 对于任何其他应用商店，必须输入完整的 URL。

#### <a name="intune-management-extension-powershell-scripts---3734186----"></a>Intune 管理扩展 PowerShell 脚本<!-- 3734186  -->
用户可以在设备上配置使用用户的管理员权限运行的 PowerShell 脚本。 有关详细信息，请参阅[在 Intune 中的 Windows 10 设备上使用 PowerShell 脚本](../apps/intune-management-extension.md)和 [Win32 应用管理](../apps/app-management.md)。

#### <a name="android-enterprise-app-management---4459905---"></a>Android Enterprise 应用管理<!-- 4459905 -->
Intune 将自动向 Intune 管理控制台添加四个常见的与 Android Enterprise 相关的应用，以便 IT 管理员可以轻松配置和使用 Android Enterprise 管理。 这四个 Android Enterprise 应用如下所示：

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - 用于 Android Enterprise 完全托管方案。
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** - 帮助你使用双因素身份验证登录帐户。
- **[Intune 公司门户](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - 用于应用保护策略 (APP) 和 Android Enterprise 工作配置文件方案。
- [托管的主屏幕](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) - 用于 Android Enterprise 专用/展台方案。

在过去，IT 管理员需要在设置过程中从[托管的 Google Play 商店](https://play.google.com/store/apps)手动查找并批准这些应用。 此更改消除了这些以前的手动步骤，客户可以更轻松快速地使用 Android Enterprise 管理。

当管理员首次将 Intune 租户连接到托管的 Google Play 时，他们将看到已自动添加到其 Intune 应用列表的这四个应用。 有关详细信息，请参阅[如何将 Intune 帐户连接到托管的 Google Play 帐户](../enrollment/connect-intune-android-enterprise.md)。 对于已连接其租户或已使用 Android Enterprise 的租户，管理员无需执行任何操作。 这四个应用将在 2019 年 5 月服务推出结束后的 7 天内自动显示。

### <a name="device-configuration"></a>设备配置

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---1533038---"></a>更新了 Microsoft Intune 的 PFX 证书连接器<!-- 1533038 -->
我们已发布[用于 Microsoft Intune 的 PFX 证书连接器](../protect/certficates-pfx-configure.md#whats-new-for-connectors)的更新，该更新解决了以下问题：因现有 PFX 证书持续重新处理而导致连接器停止处理新请求。

#### <a name="intune-security-tasks-for-defender-atp-in-public-preview---3208597---"></a>适用于 Defender ATP 的 Intune 安全任务（公共预览版）<!-- 3208597 -->
在公共预览版中，可以使用 Intune 管理 [Microsoft Defender 高级威胁防护 (ATP) 的安全任务](../protect/atp-manage-vulnerabilities.md)。 这与 ATP 集成，并增加了基于风险的方法来发现终结点漏洞和配置错误，并对其设置优先级和进行修正，同时缩短了从发现到缓解的时间。

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy---3617671---idstaged--"></a>了解 Windows 10 设备合规性策略中的 TPM 芯片组<!-- 3617671   idstaged-->
许多 Windows 10 及更高版本设备都具有受信任的平台模块 (TPM) 芯片组。 此更新包含一个新符合性设置，它将检查设备上的 TPM 芯片版本。

[Windows 10 及更高版本的符合性策略设置](../protect/compliance-policy-create-windows.md#device-security)介绍了此设置。

适用于：Windows 10 及更高版本

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices---4097904-----"></a>防止最终用户修改其个人热点，并禁止 Siri 服务器登录 iOS 设备<!-- 4097904   -->  
为 iOS 设备创建设备限制配置文件（在“设备配置”   > “配置文件”   > “创建配置文件”   >  针对平台选择“iOS”  > 针对配置文件类型选择“设备限制”  ）。 此更新包括可配置的新设置：

- **内置应用**：Siri 命令的服务器端日志记录
- **无线**：个人热点的用户修改（仅限监管模式）

若要查看这些设置，请转到[适用于 iOS 的内置应用设置](../configuration/device-restrictions-ios.md#built-in-apps)和[适用于 iOS 的无线设置](../configuration/device-restrictions-ios.md#wireless)。

适用于：iOS 12.2 及更新版本

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices---4097905-----"></a>macOS 设备的新 Classroom 应用设备限制设置<!-- 4097905   --> 
可以为 macOS 设备创建设备配置文件（依次选择“设备配置”   > “配置文件”   > “创建配置文件”   >  针对平台选择“macOS”  > 针对配置文件类型选择“设备限制”  ）。 在此次更新中，我们新增了 Classroom 应用设置
、用于阻止屏幕截图的选项，以及用于禁用 iCloud 照片库的选项。

要查看最新设置，请转到[使用 Intune 允许或限制功能的 macOS 设备设置](../configuration/device-restrictions-macos.md)。

适用范围：macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>已重命名用于访问应用商店设置的 iOS 密码<!-- 4557891  -->
“用于访问应用商店的密码”  设置已重命名为“要求所有购买都输入 iTunes Store 密码”  （“设备配置”   > “配置文件”   > “创建配置文件”   > “iOS”  (针对平台) > 配置文件类型的“设备限制”  >“App Store、文档查看和游戏”  ）。

若要查看可用设置，请转到 [App Store、文档查看和游戏 iOS 设置](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming)。

适用于：iOS

#### <a name="microsoft-defender-advanced-threat-protection--baseline--preview----3754134---"></a>Microsoft Defender 高级威胁防护基线（预览版）<!--  3754134 -->
已添加用于 [Microsoft Defender 高级威胁防护](../protect/security-baseline-settings-defender-atp.md)设置的安全基线（预览版）。 当环境满足使用 [Microsoft Defender 高级威胁防护](../protect/advanced-threat-protection.md#prerequisites)的先决条件时，此基线才可用。

### <a name="device-enrollment"></a>设备注册

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available---3605348---"></a>Windows 注册状态页 (ESP) 现已正式发布<!-- 3605348 -->
注册状态页现在没有预览版。 有关详细信息，请参阅[设置注册状态页](../enrollment/windows-enrollment-status.md)。


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation---4593669---"></a>Intune 用户界面更新 - Autopilot 注册配置文件创建<!-- 4593669 -->
用于创建 Autopilot 注册配置文件的用户界面已更新为与 Azure 用户界面样式保持一致。 有关详细信息，请参阅[创建 Autopilot 注册配置文件](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile)。 接下来，其他 Intune 方案将更新为此新 UI 样式。

#### <a name="enable-autopilot-reset-for-all-windows-devices---4225665---"></a>为所有 Windows 设备启用 Autopilot 重置<!-- 4225665 -->
Autopilot 重置现在适用于所有 Windows 设备，甚至包括那些未配置为使用注册状态页的设备。 如果在初始设备注册过程中未为设备配置注册状态页，则设备将在登录后直接转到桌面。 可能最多需要 8 小时才能同步并在 Intune 中显示符合。 有关详细信息，请参阅[使用远程 Windows Autopilot 重置功能重置设备](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote)。

#### <a name="exact-imei-format-not-required-when-searching-all-devices--30407680---"></a>搜索所有设备时不需要确切的 IMEI 格式<!--30407680 -->
搜索“所有设备”  时，无需在 IMEI 号码中包含空格。

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal--2489996---"></a>从 Apple 门户删除设备时，Intune 门户将反映此操作<!--2489996 -->
如果从 Apple 的设备注册计划或 Apple Business Manager 门户删除设备，下次同步时将自动从 Intune 删除该设备。

### <a name="the-enrollment-status-page-now-tracks-win32-apps---2714451---"></a>注册状态页现在跟踪 Win32 应用<!-- 2714451 -->
这仅适用于运行 Windows 10 版本 1903 及更高版本的设备。 有关详细信息，请参阅[设置注册状态页](../enrollment/windows-enrollment-status.md)。

### <a name="device-management"></a>设备管理

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api---3295288---"></a>使用 Graph API 批量重置和擦除设备<!-- 3295288 -->
用户现在可以使用 Graph API 批量重置和擦除多达 100 台设备。

### <a name="monitor-and-troubleshoot"></a>监视和故障排除

#### <a name="the-encryption-report-is-out-of-public-preview---4587546--------"></a>加密报表没有公共预览版<!-- 4587546      -->
[BitLocker 和设备加密的报表](../protect/encryption-monitor.md)现已正式发布，并且不再是公共预览版的一部分。

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices---4050557---"></a>适用于 iOS 和 Android 设备的 Outlook 签名和生物识别设置<!-- 4050557 -->
现在可以指定是否在 iOS 和 Android 设备上的 Outlook 中启用了默认签名。 此外，还可以选择允许用户更改 iOS 上的 Outlook 中的生物识别设置。

## <a name="week-of-may-6-2019"></a>2019 年 5 月 6 日当周

### <a name="device-configuration"></a>设备配置

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices---4500808---"></a>面向 iOS 设备针对 F5 Access 的网络访问控制 (NAC) 支持<!-- 4500808 -->

F5 发布了针对 BIG-IP 13 的更新，在 Intune 中实现了针对 iOS 上的 F5 Access 的 NAC 功能支持。 使用此功能需要：

- 将 BIG-IP 更新为 13.1.1.5 版。 不支持 BIG-IP 14。
- 将 BIG-IP 与 Intune 相集成以配置 NAC。 [概述：使用终结点管理系统配置 APM 以进行设备状态检查](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html)中列出了相关步骤。
- 在 Intune 中的 VPN 配置文件中选择“启用网络访问控制(NAC)”设置  。

若要查看可用设置，请转至[在 iOS 设备上配置 VPN](../configuration/vpn-settings-ios.md)。

适用于：iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---doc-vso-1521237----"></a>更新了 Microsoft Intune 的 PFX 证书连接器<!-- doc-vso 1521237  -->  
我们发布了针对 [Microsoft Intune 的 PFX 证书连接器](../protect/certficates-pfx-configure.md#whats-new-for-connectors)的更新，将轮询间隔从 5 分钟降到了 30 秒。




## <a name="notices"></a>通知

[!INCLUDE [Intune notices](../includes/intune-notices.md)]
