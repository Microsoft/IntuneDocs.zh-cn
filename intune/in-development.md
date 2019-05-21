---
title: 开发过程中 - Microsoft Intune
titleSuffix: ''
description: 开发过程中的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/29/2019
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
ms.openlocfilehash: 7bba992c79f69a126f0199d9cdac52779910ff38
ms.sourcegitcommit: 068c4e4bc6e6d778ece4a83d000128c4d2b732db
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2019
ms.locfileid: "64910324"
---
# <a name="in-development-for-microsoft-intune---may-2019"></a>Microsoft Intune 开发过程中的功能 - 2019 年 5 月

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


<!-- 1905 start-->


### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>从 Apple 门户删除设备时，Intune 门户将反映此操作 <!--2489996 -->
如果从 Apple 的设备注册计划或 Apple Business Manager 门户删除设备，下次同步时将自动从 Intune 删除该设备。

### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>关键字搜索的基线支持  <!-- 3082036         -->
创建或编辑安全基线配置文件时，即将能够使用搜索功能来筛选控制台中显示的设置。   

### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>使用图形 API 批量重置和擦除设备 <!-- 3295288 -->
用户能够使用图形 API 批量重置和擦除多达 100 台设备。

### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>了解 Windows 10 设备合规性策略中的 TPM 芯片组 <!-- 3617671 -->
许多 Windows 10 及更高版本设备都具有受信任的平台模块 (TPM) 芯片组。 此更新包含一个新符合性设置，它将检查设备上的 TPM 芯片版本。 

[Windows 10 及更高版本的符合性策略设置](compliance-policy-create-windows.md#device-security)介绍了此设置。

适用于：Windows 10 及更高版本

### <a name="intune-management-extension-powershell-scripts-----3734186------"></a>Intune 管理扩展 PowerShell 脚本  <!-- 3734186    -->
用户将能够在设备上配置使用用户的管理员权限运行的 PowerShell 脚本。 有关详细信息，请参阅[在 Intune 中的 Windows 10 设备上使用 PowerShell 脚本](intune-management-extension.md)。

### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-supervised-devices----4097904----"></a>防止最终用户修改其个人热点，并禁止 Siri 服务器登录 iOS 受监督设备 <!-- 4097904  --> 
为 iOS 设备创建设备限制配置文件（在“设备配置” > “配置文件” > “创建配置文件” >  针对平台选择“iOS”> 针对配置文件类型选择“设备限制”）。 此更新包括可配置的新设置：

- 个人热点
- Siri 服务器日志记录

要查看最新设置，请转到[允许或限制功能的 iOS 设备设置](device-restrictions-ios.md)。 

适用于：iOS 12.2 及更新版本

### <a name="new-classroom-app-device-restriction-settings-for-dep-enrolled-macos-devices----4097905----"></a>已注册 DEP 的 macOS 设备的新 Classroom 应用设备限制设置 <!-- 4097905  --> 
可以为 macOS 设备创建设备配置文件（依次选择“设备配置” > “配置文件” > “创建配置文件” >  针对平台选择“macOS”> 针对配置文件类型选择“设备限制”）。 此更新包含用于已注册 DEP 的设备的新 Classroom 应用设置，以及用于禁用 iCloud 照片库的选项。

要查看最新设置，请转到[使用 Intune 允许或限制功能的 macOS 设备设置](device-restrictions-macos.md)。

适用于：macOS 10.14.4 及更新版本

### <a name="android-enterprise-app-management----4459905-idready---"></a>Android Enterprise 应用管理 <!-- 4459905 idready -->
Intune 将自动向 Intune 管理控制台添加四个常见的与 Android Enterprise 相关的应用，以便 IT 管理员可以轻松配置和使用 Android Enterprise 管理。 这四个 Android Enterprise 应用如下所示：

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - 用于 Android Enterprise 完全托管方案。
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** - 帮助你使用双因素身份验证登录帐户。
- **[Intune 公司门户](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - 用于应用保护策略 (APP) 和 Android Enterprise 工作配置文件方案。
- [托管的主屏幕](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) - 用于 Android Enterprise 专用/展台方案。

在过去，IT 管理员需要在设置过程中从[托管的 Google Play 商店](https://play.google.com/store/apps)手动查找并批准这些应用。 此更改消除了这些以前的手动步骤，客户可以更轻松快速地使用 Android Enterprise 管理。

当管理员首次将 Intune 租户连接到托管的 Google Play 时，他们将看到已自动添加到其 Intune 应用列表的这四个应用。 有关详细信息，请参阅[如何将 Intune 帐户连接到托管的 Google Play 帐户](connect-intune-android-enterprise.md)。 对于已连接其租户或已使用 Android Enterprise 的租户，管理员无需执行任何操作。 在完成 2019 年 5 月服务推出后的 7 天内，将自动显示这四个应用。

<!-- 1904 start-->

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Windows Defender 防火墙的高级设置 <!-- 1311949 -->
你很快就可以使用 Intune 在客户端上管理 Windows Defender 的自定义防火墙规则。 规则可以指定应用程序、网络地址和端口的入站和出站行为。 


### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>设备用户可以查看他们已安装或尝试安装的所有托管应用 <!-- 2352913 -->
Company Portal for Windows 将列出用户设备上安装的所有要求的和可用的托管应用。 用户将能够查看已尝试和待处理的应用安装及其当前状态。 如果组织未提供所需或可用的应用，则用户将看到一条消息，说明尚未安装任何公司应用。 用户还可以按安装状态对其应用进行排序或筛选。

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>在创建 Windows 10 设备配置配置文件时使用“适用性规则” <!-- 2549910 -->
创建 Windows 10 设备配置配置文件（“设备配置” > “配置文件” > “创建配置文件” > 适用于平台的“Windows 10”）。 你将能够创建“适用性规则”，使配置文件仅应用于特定版本。 例如，创建一个启用某些 BitLocker 设置的配置文件。 添加配置文件后，请使用适用性规则，使配置文件仅适用于运行 Windows 10 企业版的设备。

适用于： 
- Windows 10 及更高版本

###  <a name="intune-security-tasks-for-defender-atp-in-public-preview----3208597---"></a>适用于 Defender ATP 的 Intune 安全任务（公共预览版） <!-- 3208597 -->
作为公共预览版，Intune 将很快为新发布的 Microsoft Defender 威胁和漏洞管理添加安全任务。  通过此集成，Windows Defender ATP (WDATP) 中的安全操作管理员可以更有效地向 Intune 管理员传达针对新兴威胁的建议修正措施。 添加安全任务操作增加了基于风险的方法来发现终结点漏洞和配置错误，并对其设置优先级和进行修正。

若要了解有关 Intune 中安全任务的详细信息，请参阅有关[使用 Intune 安全任务扩展 Microsoft Defender ATP 威胁和漏洞管理](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-security-tasks-extend-Microsoft-Defender-ATP-s/ba-p/369857)的博客文章。 

### <a name="windows-defender-advanced-threat-protection-baseline----3754134---"></a>Windows Defender 高级威胁防护基线 <!-- 3754134 -->
我们将添加新的基线来帮助配置 Windows Defender 高级威胁防护设置。



## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。


