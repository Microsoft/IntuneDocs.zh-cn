---
title: Microsoft Intune 中的新增功能 - Azure | Microsoft Docs
titleSuffix: ''
description: 了解 Intune Azure 门户新增功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/31/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7c14568a0581220cf5941984645bd0b9044e00c1
ms.sourcegitcommit: cb76efd3db60a422a65478ebce83d3aea7b5eeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2019
ms.locfileid: "66749944"
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune 新增功能

了解 Microsoft Intune 每周新增功能。 此外，还可找到[即将发生的更改](in-development.md)、[重要说明](#notices)以及有关[过去版本](whats-new-archive.md)的信息。 

> [!Note]
> 某些功能可能会在数周内推出，第一周内可能不能供所有客户使用。

**RSS 源**：通过将以下 URL 复制并粘贴到源阅读器中，可以在页面更新时收到通知：`https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->  

<!-- ########################## -->

## <a name="week-of-may-27-2019"></a>2019 年 5 月 27 日当周 

### <a name="app-management"></a>应用管理

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices----4223162---"></a>报告 Android 设备上可能有害的应用 <!-- 4223162 -->
Intune 现在提供有关 Android 设备上可能有害的应用的其他报告信息。 

## <a name="week-of-may-20-2019"></a>2019 年 5 月 20 日当周 

### <a name="app-management"></a>应用管理

#### <a name="windows-company-portal-app----3316993---"></a>Windows 公司门户应用 <!-- 3316993 -->
Windows 公司门户应用将具有一个标记为“设备”的新页面。 “设备”页面将显示最终用户已注册的所有设备。 在用户使用 10.3.4291.0 或更高版本时，公司门户中将显示此更改。 要了解如何配置公司门户，请参阅[如何配置 Microsoft Intune 公司门户应用](company-portal-app.md)。

### <a name="device-enrollment"></a>设备注册

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Autopilot 设备的 OrderID 属性名称已更改为“组标记” <!-- 4659453 -->

为更直观地显示，Autopilot 设备上的 OrderID 属性名称已更改“组标记”。 在使用 CSV 上传 Autopilot 设备信息时，必须使用“组标记”而不是 OrderID 作为列标题。  

## <a name="week-of-may-13-2019"></a>2019 年 5 月 13 日当周 

### <a name="app-management"></a>应用管理

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359-idready-wnready--"></a>Intune 策略更新身份验证方法和公司门户应用安装  <!-- 1927359 idready wnready-->
在已通过 Apple 公司设备注册方法之一经由“设置助理”注册的设备上，Intune 将不再支持由最终用户从应用商店手动安装的公司门户。 仅当在注册过程中使用 Apple 设置助理进行身份验证时，此更改才适用。 此更改也只会影响通过以下方式注册的 iOS 设备：  
* Apple 配置器

* Apple Business Manager

* Apple School Manager

* Apple 设备注册计划 (DEP)

如果用户从应用商店安装公司门户应用，然后尝试通过该应用注册这些设备，则他们将收到错误。 在注册过程中由 Intune 自动推送公司门户时，这些设备应仅使用公司门户。 将更新 Azure 门户中的 Intune 注册配置文件，以便你可以指定设备的身份验证方式以及是否收到公司门户应用。 如果希望 DEP 设备用户具有公司门户，则需要在注册配置文件中指定你的首选项。 

此外，iOS 公司门户中的“标识设备”屏幕将被删除。 因此，想要启用条件访问或部署公司应用的管理员必须更新 DEP 注册配置文件。 仅当使用设置助理对 DEP 注册进行身份验证时，此要求才适用。 在这种情况下，必须将公司门户推送到设备上。 为此，请选择“Intune” > “设备注册” > “Apple 注册” > “注册计划令牌”，依次选择令牌和“配置文件”，选择配置文件，再选择“属性”，然后将“安装公司门户”设置为“是”。

若要在已注册的 DEP 设备上安装公司门户，需要转到“Intune”>“客户端应用”，并将其作为具有应用配置策略的托管应用进行推送。 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy----3568384---"></a>配置最终用户使用应用保护策略更新业务线 (LOB) 应用的方式 <!-- 3568384 -->
用户现在可以配置最终用户可获取业务线 (LOB) 应用的更新版本的位置。 最终用户将在“最低应用版本”条件启动对话框中看到此功能，系统将提示最终用户更新到 LOB 应用的最低版本。 必须提供这些更新详细信息作为 LOB 应用保护策略（应用）的一部分。 此功能在 iOS 和 Android 中可用。 在 iOS 上，此功能要求应用与 Intune SDK for iOS v. 10.0.7 或更高版本集成（或使用包装工具包装）。 在 Android 上，此功能需要使用最新的公司门户。 若要配置最终用户更新 LOB 应用的方式，应用需要使用键 `com.microsoft.intune.myappstore` 发送给它的托管应用配置策略。 发送的值将定义最终用户从哪个应用商店中下载应用。 如果应用是通过公司门户部署的，则值必须为 `CompanyPortal`。 对于任何其他应用商店，必须输入完整的 URL。

#### <a name="intune-management-extension-powershell-scripts-----3734186-idready---"></a>Intune 管理扩展 PowerShell 脚本  <!-- 3734186 idready -->
用户可以在设备上配置使用用户的管理员权限运行的 PowerShell 脚本。 有关详细信息，请参阅[在 Intune 中的 Windows 10 设备上使用 PowerShell 脚本](intune-management-extension.md)和 [Win32 应用管理](apps-win32-app-management.md)。

#### <a name="android-enterprise-app-management----4459905---"></a>Android Enterprise 应用管理 <!-- 4459905 -->
Intune 将自动向 Intune 管理控制台添加四个常见的与 Android Enterprise 相关的应用，以便 IT 管理员可以轻松配置和使用 Android Enterprise 管理。 这四个 Android Enterprise 应用如下所示：

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - 用于 Android Enterprise 完全托管方案。
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** - 帮助你使用双因素身份验证登录帐户。
- **[Intune 公司门户](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - 用于应用保护策略 (APP) 和 Android Enterprise 工作配置文件方案。
- [托管的主屏幕](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) - 用于 Android Enterprise 专用/展台方案。

在过去，IT 管理员需要在设置过程中从[托管的 Google Play 商店](https://play.google.com/store/apps)手动查找并批准这些应用。 此更改消除了这些以前的手动步骤，客户可以更轻松快速地使用 Android Enterprise 管理。

当管理员首次将 Intune 租户连接到托管的 Google Play 时，他们将看到已自动添加到其 Intune 应用列表的这四个应用。 有关详细信息，请参阅[如何将 Intune 帐户连接到托管的 Google Play 帐户](connect-intune-android-enterprise.md)。 对于已连接其租户或已使用 Android Enterprise 的租户，管理员无需执行任何操作。 在完成 2019 年 5 月服务推出后的 7 天内，将自动显示这四个应用。

### <a name="device-configuration"></a>设备配置

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune-----1533038---"></a>更新了 Microsoft Intune 的 PFX 证书连接器  <!-- 1533038 -->
我们已发布[用于 Microsoft Intune 的 PFX 证书连接器](certficates-pfx-configure.md#whats-new-for-connectors)的更新，该更新解决了以下问题：因现有 PFX 证书持续重新处理而导致连接器停止处理新请求。

####  <a name="intune-security-tasks-for-defender-atp-in-public-preview--------3208597---"></a>适用于 Defender ATP 的 Intune 安全任务（公共预览版）     <!-- 3208597 -->
在公共预览版中，可以使用 Intune 管理 [Microsoft Defender 高级威胁防护 (ATP) 的安全任务](atp-manage-vulnerabilities.md)。 这与 ATP 集成，并增加了基于风险的方法来发现终结点漏洞和配置错误，并对其设置优先级和进行修正，同时缩短了从发现到缓解的时间。

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---idstaged--"></a>了解 Windows 10 设备合规性策略中的 TPM 芯片组 <!-- 3617671   idstaged-->
许多 Windows 10 及更高版本设备都具有受信任的平台模块 (TPM) 芯片组。 此更新包含一个新符合性设置，它将检查设备上的 TPM 芯片版本。 

[Windows 10 及更高版本的符合性策略设置](compliance-policy-create-windows.md#device-security)介绍了此设置。

适用于：Windows 10 及更高版本

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices----4097904-----"></a>防止最终用户修改其个人热点，并禁止 Siri 服务器登录 iOS 设备 <!-- 4097904   -->  
为 iOS 设备创建设备限制配置文件（在“设备配置” > “配置文件” > “创建配置文件” >  针对平台选择“iOS”> 针对配置文件类型选择“设备限制”）。 此更新包括可配置的新设置：

- **内置应用**：Siri 命令的服务器端日志记录
- **无线**：个人热点的用户修改（仅限监管模式）

若要查看这些设置，请转到[适用于 iOS 的内置应用设置](device-restrictions-ios.md#built-in-apps)和[适用于 iOS 的无线设置](device-restrictions-ios.md#wireless)。

适用于：iOS 12.2 及更新版本

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices----4097905-----"></a>macOS 设备的新 Classroom 应用设备限制设置 <!-- 4097905   --> 
可以为 macOS 设备创建设备配置文件（依次选择“设备配置” > “配置文件” > “创建配置文件” >  针对平台选择“macOS”> 针对配置文件类型选择“设备限制”）。 此更新包含新 Classroom 应用设置，用于阻止屏幕截图的选项以及用于禁用 iCloud 照片库的选项。

要查看最新设置，请转到[使用 Intune 允许或限制功能的 macOS 设备设置](device-restrictions-macos.md)。

适用范围：macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>已重命名用于访问应用商店设置的 iOS 密码<!-- 4557891  -->
“用于访问应用商店的密码”设置已重命名为“要求所有购买都输入 iTunes Store 密码”（“设备配置” > “配置文件” > “创建配置文件” > “iOS”(针对平台) > 配置文件类型的“设备限制”>“App Store、文档查看和游戏”）。

若要查看可用设置，请转到 [App Store、文档查看和游戏 iOS 设置](device-restrictions-ios.md#app-store-doc-viewing-gaming)。

适用于：iOS

####  <a name="microsoft-defender-advanced-threat-protection--baseline--preview------3754134---"></a>Microsoft Defender 高级威胁防护基线（预览版）  <!--  3754134 -->
已添加用于 [Microsoft Defender 高级威胁防护](security-baseline-settings-defender-atp.md)设置的安全基线（预览版）。 当环境满足使用 [Microsoft Defender 高级威胁防护](advanced-threat-protection.md#prerequisites)的先决条件时，此基线才可用。

### <a name="device-enrollment"></a>设备注册

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available----3605348---"></a>Windows 注册状态页 (ESP) 现已正式发布 <!-- 3605348 -->
注册状态页现在没有预览版。 有关详细信息，请参阅[设置注册状态页](windows-enrollment-status.md)。


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation-----4593669---"></a>Intune 用户界面更新 - Autopilot 注册配置文件创建  <!-- 4593669 -->
用于创建 Autopilot 注册配置文件的用户界面已更新为与 Azure 用户界面样式保持一致。 有关详细信息，请参阅[创建 Autopilot 注册配置文件](https://docs.microsoft.com/intune/enrollment-autopilot#create-an-autopilot-deployment-profile)。 接下来，其他 Intune 方案将更新为此新 UI 样式。

#### <a name="enable-autopilot-reset-for-all-windows-devices----4225665---"></a>为所有 Windows 设备启用 Autopilot 重置 <!-- 4225665 -->
Autopilot 重置现在适用于所有 Windows 设备，甚至包括那些未配置为使用注册状态页的设备。 如果在初始设备注册过程中未为设备配置注册状态页，则设备将在登录后直接转到桌面。 可能最多需要 8 小时才能同步并在 Intune 中显示符合。 有关详细信息，请参阅[使用远程 Windows Autopilot 重置功能重置设备](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote)。

#### <a name="exact-imei-format-not-required-when-searching-all-devices---30407680---"></a>搜索所有设备时不需要确切的 IMEI 格式 <!--30407680 -->
搜索“所有设备”时，无需在 IMEI 号码中包含空格。

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>从 Apple 门户删除设备时，Intune 门户将反映此操作 <!--2489996 -->
如果从 Apple 的设备注册计划或 Apple Business Manager 门户删除设备，下次同步时将自动从 Intune 删除该设备。

### <a name="the-enrollment-status-page-now-tracks-win32-apps----2714451---"></a>注册状态页现在跟踪 Win32 应用 <!-- 2714451 -->
这仅适用于运行 Windows 10 版本 1903 及更高版本的设备。 有关详细信息，请参阅[设置注册状态页](windows-enrollment-status.md)。

### <a name="device-management"></a>设备管理

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>使用图形 API 批量重置和擦除设备 <!-- 3295288 -->
用户现在可以使用图形 API 批量重置和擦除多达 100 台设备。


### <a name="monitor-and-troubleshoot"></a>监视和故障排除

#### <a name="the-encryption-report-is-out-of-public-preview------4587546--------"></a>加密报表没有公共预览版   <!-- 4587546      -->
[BitLocker 和设备加密的报表](encryption-monitor.md)现已正式发布，并且不再是公共预览版的一部分。 

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices----4050557---"></a>适用于 iOS 和 Android 设备的 Outlook 签名和生物识别设置 <!-- 4050557 -->
现在可以指定是否在 iOS 和 Android 设备上的 Outlook 中启用了默认签名。 此外，还可以选择允许用户更改 iOS 上的 Outlook 中的生物识别设置。

## <a name="week-of-may-6-2019"></a>2019 年 5 月 6 日当周 

### <a name="device-configuration"></a>设备配置

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices----4500808---"></a>面向 iOS 设备针对 F5 Access 的网络访问控制 (NAC) 支持 <!-- 4500808 -->

F5 发布了针对 BIG-IP 13 的更新，在 Intune 中实现了针对 iOS 上的 F5 Access 的 NAC 功能支持。 使用此功能需要：

- 将 BIG-IP 更新为 13.1.1.5 版。 不支持 BIG-IP 14。
- 将 BIG-IP 与 Intune 相集成以配置 NAC。 [概述：使用终结点管理系统配置 APM 以进行设备状态检查](https://support.f5.com/kb/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html#guid-0bd12e12-8107-40ec-979d-c44779a8cc89)中列出了相关步骤。
- 在 Intune 中的 VPN 配置文件中选择“启用网络访问控制(NAC)”设置。

若要查看可用设置，请转至[在 iOS 设备上配置 VPN](vpn-settings-ios.md)。

适用于：iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune----doc-vso-1521237----"></a>更新了 Microsoft Intune 的 PFX 证书连接器 <!-- doc-vso 1521237  -->  
我们发布了针对 [Microsoft Intune 的 PFX 证书连接器](certficates-pfx-configure.md#whats-new-for-connectors)的更新，将轮询间隔从 5 分钟降到了 30 秒。

## <a name="week-of-april-22-2019"></a>2019 年 4 月 22 日当周

### <a name="use-compliance-manager-to-create-assessments-for-microsoft-intune---4404750---"></a>使用合规性管理器为 Microsoft Intune 创建评估<!-- 4404750 -->

[合规性管理器](https://servicetrust.microsoft.com/ComplianceManager)（打开另一个 Microsoft 站点）是 Microsoft 服务信任门户中基于工作流的风险评估工具。 它使你能够跟踪、分配和验证组织的与 Microsoft 服务相关的法规遵从性活动。 可以使用 Office 365、Azure、Dynamics、专业服务和 Intune 创建自己的合规性评估。 Intune 提供两种评估：FFIEC 和 GDPR。

合规性管理器可将控件分类（由 Microsoft 管理的控件和由组织管理的控件），从而帮助你节省精力。 你可以完成评估，然后导出并打印评估。

[联邦金融机构检查委员会 (FFIEC)](https://www.microsoft.com/trustcenter/compliance/FFIEC)（打开另一个 Microsoft 站点）合规性是 FFIEC 发布的一套网上银行标准。 对于使用 Intune 的金融机构来说，这是最必不可少的评估。 它诠释了 Intune 如何帮助遵循与公有云工作负载相关的 FFIEC 网络安全指南。 Intune 的 FFIEC 评估是合规性管理器中的第二种 FFIEC 评估。

以下示例介绍 FFIEC 控件的明细。 Microsoft 负责 64 个控件。 你负责其余 12 个控件。

![请参阅 FFIEC 的 Intune 评估示例，其中包括客户操作和 Microsoft 操作](./media/intune-ffiec-assessment-status.png)

[一般数据保护条例 (GDPR)](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-overview)（打开另一个 Microsoft 站点）是欧盟 (EU) 法律，用于帮助保护个人及其数据的权利。 GDPR 是帮助遵守隐私法规的必不可少的评估。 

以下示例介绍 GDPR 控件的明细。 Microsoft 负责 49 个控件。 你负责其余 66 个控件。

![请参阅 GDPR 的 Intune 评估示例，其中包括客户操作和 Microsoft 操作](./media/intune-assessment-status.png)

## <a name="week-of-april-15-2019"></a>2019 年 4 月 15 日当周

### <a name="app-management"></a>应用管理

#### <a name="openssl-encryption-for-android-app-protection-policies----3747362---"></a>Android 应用保护策略的 OpenSSL 加密 <!-- 3747362 -->
Android 设备上的 Intune 应用保护策略 (APP) 现在使用符合 FIPS 140-2 标准的 OpenSSL 加密库。 有关详细信息，请参阅 [Microsoft Intune 中的 Android 应用保护策略设置](app-protection-policy-settings-android.md)的[加密](app-protection-policy-settings-android.md#encryption)部分。

#### <a name="enable-win32-app-dependencies----2617348----"></a>启用 Win32 应用依赖项 <!-- 2617348  -->
管理员可以要求在安装 Win32 应用之前，将其他应用作为依赖项进行安装。 具体来说，设备必须先安装相关应用，再安装 Win32 应用。 在 Intune 中，选择“客户端应用” > “应用” > “添加”，以显示“添加应用”边栏选项卡。 选择“Windows 应用(Win32)”作为“应用类型”。 添加应用后，可以选择“依赖项”，添加在安装 Win32 应用之前必须安装的相关应用。 有关详细信息，请参阅 [Intune 独立版 - Win32 应用管理](apps-win32-app-management.md)。 

#### <a name="app-version-installation-information-for-microsoft-store-for-business-apps----3537391-----"></a>适用于企业的 Microsoft Store 应用的应用版本安装信息 <!-- 3537391   -->
应用安装报告包括适用于企业的 Microsoft Store 应用的应用版本信息。 在 Intune 中，选择“客户端应用” > “应用”。 选择“适用于企业的 Microsoft Store 应用”，然后在“监视”部分下选择“设备安装状态”。

#### <a name="additions-to-win32-apps-requirement-rules----3676883-----"></a>Win32 应用要求规则的新增内容 <!-- 3676883   -->
可以基于 PowerShell 脚本、注册表值和文件系统信息创建要求规则。 在 Intune 中，选择“客户端应用” > “应用” > “添加”。 然后，在“添加应用”边栏选项卡中选择“Windows 应用(Win32)”作为“应用类型”。  选择“要求” > “添加”，以配置其他要求规则。 然后，选择“文件类型”、“注册表”或“脚本”作为“要求类型”。 有关详细信息，请参阅 [Win32 应用管理](apps-win32-app-management.md)。

 #### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227----"></a>配置要在已注册到 Intune 并且已加入 Azure AD 的设备上安装的 Win32 应用 <!-- 3695227  -->
可以分配要在已注册到 Intune 并且已加入 Azure AD 的设备上安装的 Win32 应用。 有关 Intune 中 Win32 应用的详细信息，请参阅 [Win32 应用管理](apps-win32-app-management.md)。

#### <a name="device-overview-shows-primary-user---794259----"></a>设备概述显示主要用户 <!--794259  -->
“设备概述”页将显示主要用户，也称为用户设备相关性用户 (UDA)。 要查看设备的主要用户，请选择“Intune” > “设备” > “所有设备”> 选择一个设备。 主要用户将显示在靠近“概述”页顶部的位置。

#### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925----"></a>Android Enterprise 工作配置文件设备的其他托管 Google Play 应用报告 <!-- 4105925  -->
对于部署到 Android Enterprise 工作配置文件设备的托管 Google Play 应用，可以查看设备上安装的应用的特定版本号。 这仅适用于所需的应用。  

#### <a name="ios-third-party-keyboards----4111843-----"></a>iOS 第三方键盘 <!-- 4111843   -->
由于 iOS 平台更改，不再支持适用于针对 iOS 的“第三方键盘”设置的 Intune 应用保护策略 (APP) 的支持。 你将无法在 Intune 管理控制台中配置此设置，并且此设置将不会在 Intune App SDK 中的客户端上强制执行。

### <a name="device-configuration"></a>设备配置

#### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083----"></a>在 macOS 设备上设置登录设置和控制重启选项 <!-- 1210083  -->
在 macOS 设备上，可以创建设备配置文件（依次选择“设备配置” > “配置文件” > “创建配置文件” > 针对平台选择“macOS”> 针对配置文件类型选择“设备功能”）。 此更新包括新的登录窗口设置，例如显示自定义横幅、选择用户登录方式、显示或隐藏电源设置等。

要查看这些设置，请转到 [macOS 设备功能设置](macos-device-features-settings.md)。

#### <a name="configure-wifi-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode---3041940----"></a>在以多应用展台模式运行的 Android Enterprise 和设备所有者专用设备上配置 WiFi <!--3041940  -->
可以在以多应用展台模式运行的 Android Enterprise 和设备所有者专用设备上启用设置。 在此更新中，可让用户配置和连接到 WiFi 网络（依次选择“Intune” > “设备配置” > “配置文件” > “创建配置文件” >  针对平台选择“Android Enterprise”> 针对配置文件类型选择“仅限设备所有者”>“设备限制”>“专用设备” > “展台模式”：“多应用” > “WiFi 配置”。 

要查看可以配置的所有设置，请转到[用于允许或限制功能的 Android Enterprise 设备设置](device-restrictions-android-for-work.md)。

适用于：以多应用展台模式运行的 Android Enterprise 专用设备


#### <a name="configure-bluetooth-and-pairing-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode----3041941----"></a>在以多应用展台模式运行的 Android Enterprise 和设备所有者专用设备上配置蓝牙和配对 <!-- 3041941  -->
可以在以多应用展台模式运行的 Android Enterprise 和设备所有者专用设备上启用设置。 在此更新中，你可以允许最终用户启用蓝牙并通过蓝牙进行设备配对（依次选择“Intune” > “设备配置” > “配置文件” > “创建配置文件” >  针对平台选择“Android Enterprise”> 针对配置文件类型选择“仅限设备所有者”>“设备限制”>“专用设备” > “展台模式”：“多应用” > “蓝牙配置”。 

要查看可以配置的所有设置，请转到[用于允许或限制功能的 Android Enterprise 设备设置](device-restrictions-android-for-work.md)。

适用于：以多应用展台模式运行的 Android Enterprise 专用设备

#### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883----"></a>在 Intune 中创建和使用 OEMConfig 设备配置文件 <!-- 3305883  -->
在此更新中，Intune 支持使用 OEMConfig 配置 Android Enterprise 设备。 具体来说，可以使用 OEMConfig 创建设备配置文件并将设置应用于 Android Enterprise 设备（依次选择“设备配置” > “配置文件” > “创建配置文件” >  针对平台选择“Android Enterprise”）。

对 OEM 的支持目前基于每个 OEM。 如果 OEMConfig 应用列表中未包含所需 OEMConfig 应用，请联系 `IntuneOEMConfig@microsoft.com`。

要了解有关此功能的详细信息，请转到[在 Microsoft Intune 中通过 OEMConfig 使用和管理 Android Enterprise 设备](android-oem-configuration-overview.md)。

适用于：Android Enterprise

#### <a name="windows-update-notifications-----3316758-3316782----"></a>Windows 更新通知  <!-- 3316758, 3316782  -->
我们已将两个“用户体验设置”添加到了你可以在 Intune 控制台中管理的 Windows 更新通道配置中。 现在可以执行以下操作：
- 阻止或允许用户[扫描 Windows 更新](windows-update-settings.md#block-user-from-scanning-for-windows-updates)。
- 管理向用户显示的 [Windows 更新通知级别](windows-update-settings.md#windows-update-notification-level)。

#### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254----"></a>针对 Android Enterprise 和设备所有者的新设备限制设置 <!-- 3574254  -->
在 Android Enterprise 设备上，可以创建设备限制配置文件，以允许或限制功能和设置密码规则等（依次选择“设备配置” > “配置文件” > “创建配置文件”> 针对平台选择“Android Enterprise”> 针对配置文件类型选择“仅限设备所有者”>“设备限制”）。 

此更新包括新密码设置，允许完全托管设备对 Google Play 商店中应用的完全访问权限，等等。 要查看设置的当前列表，请转到[用于允许或限制功能的 Android Enterprise 设备设置](device-restrictions-android-for-work.md)。 

适用于：Android Enterprise 完全托管设备

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>了解 Windows 10 设备合规性策略中的 TPM 芯片组 <!-- 3617671 -->

此功能已推迟，并计划稍后发布。

#### <a name="updated-ui-changes-for-microsoft-edge-browser-on-windows-10-and-later-devices----3775833-----"></a>更新了 Windows 10 及更高版本设备上 Microsoft Edge 浏览器的 UI 更改 <!-- 3775833   -->
创建设备配置文件时，可以允许或限制 Windows 10 及更高版本设备上的 Microsoft Edge 功能（依次选择“设备配置” > “配置文件” > “创建配置文件”> 针对平台选择“Windows 10 和更高版本”> 针对配置文件类型选择“设备限制”>“Microsoft Edge 浏览器” > ）。 在此更新中，Microsoft Edge 设置的描述更具体，更易于理解。 

要查看这些功能，请转到 [Microsoft Edge 浏览器设备限制设置](device-restrictions-windows-10.md#microsoft-edge-browser)。

适用于：Windows 10 及更高版本

#### <a name="expanded-support-for-android-enterprise-fully-managed-devices--preview-------3903241-3903244-3903246-----"></a>扩展了对 Android Enterprise 完全托管设备（预览版）的支持  <!--   3903241, 3903244, 3903246   -->
我们继续在公开预览版中扩展了对 Android Enterprise 完全托管设备的支持（[于 2019 年 1 月首次发布](whats-new.md#week-of-january-14-2019)，包括以下内容： 

- 在完全托管设备和专用设备上，可以创建[合规性策略](compliance-policy-create-android-for-work.md)以包括密码规则和操作系统要求（依次选择“设备合规性” > “策略” > “创建策略”> 针对平台选择“Android Enterprise”> 针对配置文件类型选择“设备所有者” > ）。 

  在专用设备上，设备可能显示为“不合规”。 在专用设备上无法进行条件访问。 请务必完成使专用设备符合分配的策略的任何任务或操作。

- [条件访问](conditional-access.md) - 适用于 Android 的条件访问策略也适用于 Android Enterprise 完全托管设备。 用户现在可以使用 Microsoft Intune 应用在 Azure Active Directory 中注册其完全托管设备。 然后，查看并解决任何合规性问题，以访问组织资源。

- 新最终用户应用（Microsoft Intune 应用）- 有一种新的最终用户应用适用于 Android 完全托管设备，名为 Microsoft Intune。 此新应用质轻、现代，可提供与公司门户应用类似的功能，但适用于完全托管设备。 有关详细信息，请参阅 [Google Play 上的 Microsoft Intune 应用](https://play.google.com/store/apps/details?id=com.microsoft.intune)。

若要设置完全托管的 Android 设备，请转到“设备注册” > “Android 注册” > “公司拥有的完全托管的用户设备”。 完全托管的 Android 设备的支持仍为预览版，某些 Intune 功能可能无法完全正常运行。  

要详细了解此预览版，请参阅我们的博客 [Microsoft Intune - Preview 2 for Android Enterprise Fully Managed devices](https://aka.ms/preview2_AE_fullymanaged)（适用于 Android Enterprise 完全托管设备的 Microsoft Intune - 预览版 2）。


### <a name="device-enrollment"></a>设备注册

#### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470--wnstaged--"></a>将配置文件配置为在“设置助手”期间跳过某些屏幕 <!-- 2276470  wnstaged-->
创建 macOS 注册配置文件时，可将其配置为在用户使用设置助手期间跳过以下任一屏幕：
- 外观
- 显示基调
- iCloudStorage：如果你新建或编辑配置文件，选定跳过屏幕需要与 Apple MDM 服务器同步。  用户可以发起手动同步设备，这样在选取配置文件变更时就不会有任何延迟。
有关详细信息，请参阅[通过设备注册计划或 Apple School Manager 自动注册 macOS 设备](device-enrollment-program-enroll-macos.md)。

#### <a name="bulk-device-naming-when-enrolling-corporate-ios-devices--3566569----"></a>注册企业 iOS 设备时批量命名设备<!--3566569  -->
使用 Apple 的任一企业注册方法 (DEP/ABM/ASM) 时，可以设置设备名格式，以自动命名传入的 iOS 设备。 可以在模板中指定包含设备类型和序列号的格式。 为此，请选择“Intune” > “设备注册” > “Apple 注册” > “注册程序令牌” > “选择令牌” >“创建配置文件” > “设备命名格式”。 可以编辑现有配置文件，但只有新同步的设备才会应用该名称。

#### <a name="updated-default-timeout-message-on-enrollment-status-page----3959331---"></a>更新了“注册状态”页上的默认超时消息 <!-- 3959331 -->
我们更新了在“注册状态”页 (ESP) 超过 ESP 配置文件中指定的超时值时用户看到的默认超时消息。 新的默认消息是用户看到的内容，可帮助他们了解 ESP 部署的下一步操作。  

### <a name="device-management"></a>设备管理

#### <a name="retire-noncompliant-devices-----1827291-----"></a>停用不合规的设备  <!-- 1827291   -->
此功能已推迟，并计划在将来版本中发布。


### <a name="monitor-and-troubleshoot"></a>监视和故障排除

#### <a name="intune-data-warehouse-v10-changes-reflecting-back-to-beta----4403765---"></a>Intune 数据仓库 V1.0 更改在 beta 版本中体现 <!-- 4403765 -->
V1.0 在 1808 版本首次引入后，它在某些重要方面与 beta 版 API 有所不同。 在 1903 版本中，这些更改将在 beta 版 API 中体现。 如果有使用 beta 版 API 的重要报表，我们强烈建议将这些报表切换到 V1.0 以避免中断性变更。 有关详细信息，请参阅 [Intune 数据仓库 API 的更改日志](reports-changelog.md#1903-part-2)。

#### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>监控安全基线状态（公共预览版） <!-- 3082047 --> 
我们向安全基线的监控添加了[每个类别的视图](security-baselines-monitor.md#per-category-view)。 （安全基线仍为预览版）。 每个类别的视图显示基线中的每个类别以及属于该类别的每个状态组的设备百分比。 现可查看与各个类别不匹配、配置错误或不适用的设备数量。

### <a name="role-based-access-control"></a>基于角色的访问控制

#### <a name="scope-tags-for-apple-vpp-tokens---2371886----"></a>Apple VPP 令牌的范围标记 <!--2371886  -->
现可将范围标记添加到 Apple VPP 令牌。 只有分配有相同范围标记的用户才能访问带有该标记的 Apple VPP 令牌。 使用该令牌购买的 VPP 应用和电子书会继承其范围标记。 有关范围标记的详细信息，请参阅[使用 RBAC 和范围标记](scope-tags.md)。







## <a name="week-of-april-1-2019"></a>2019 年 4 月 1 日当周

### <a name="device-configuration"></a>设备配置

#### <a name="updated-certificate-connectors-----icm-113304612---"></a>更新了证书连接器  <!-- ICM 113304612 -->
我们已经发布了针对 [Microsoft Intune 的 Intune 证书连接器和 PFX 证书连接器](certficates-pfx-configure.md#whats-new-for-connectors)的更新。 新版本修复了几个已知问题。  

### <a name="app-management"></a>应用管理

#### <a name="user-experience-update-for-the-company-portal-app-for-ios----2536024---"></a>iOS 版公司门户应用的用户体验更新 <!-- 2536024 -->
适用于 iOS 设备的公司门户应用的主页已经过重新设计。 经此更改后，主页将更好地遵循 iOS UI 模式，更易于查找应用和电子书。

#### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>对 iOS 12 设备用户的公司门户注册的更改 <!--3448635 -->  
适用于 iOS 的公司门户的注册屏幕和步骤已更新，以与 Apple iOS 12.2 中发布的 MDM 注册更改保持一致。 更新的工作流提示用户执行以下操作：  

* 允许 Safari 在返回公司门户应用之前打开公司门户网站并下载管理配置文件。  
* 打开“设置”应用以在其设备上安装管理配置文件。
* 返回公司门户应用以完成注册。  

要了解更新的注册步骤和屏幕，请参阅[在 Intune 中注册 iOS 设备](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)。  

## <a name="week-of-march-25-2019"></a>2019 年 3 月 25 日当周

### <a name="monitor-and-troubleshoot"></a>监视和故障排除

### <a name="support-for-the-power-bi-compliance-app-from-the-data-warehouse-blade-in-microsoft-intune----4260871---"></a>Microsoft Intune 中的“数据仓库”边栏选项卡中对 Power BI 合规性应用的支持 <!-- 4260871 -->
以前，“Intune 数据仓库”边栏选项卡中的“下载 Power BI 文件”链接会下载 Intune 数据仓库报表（.pbix 文件）。 此报表已替换为 Power BI 合规性应用。 Power BI 合规性应用无需特殊加载或设置。 它将直接在 Power BI 在线门户中打开，并根据凭据专门向 Intune 租户显示数据。 在 Intune 中，选择“Intune”边栏选项卡右侧的“设置 Intune 数据仓库”链接。 然后，单击“获取 Power BI 应用”。 有关详细信息，请参阅[使用 Power BI 连接到数据仓库](reports-proc-get-a-link-powerbi.md)。

## <a name="week-of-march-18-2019"></a>2019 年 3 月 18 日当周

### <a name="app-management"></a>应用管理

#### <a name="deploy-microsoft-visio-and-microsoft-project----3725386----"></a>部署 Microsoft Visio 和 Microsoft Project <!-- 3725386  -->
现可使用 Microsoft Intune，将 Microsoft Visio Pro for Office 365 和 Microsoft Project Online 桌面客户端作为独立应用部署到 Windows 10 设备（如果拥有这些应用的许可证）。 在 Intune 中，选择“客户端应用” > “应用” > “添加”，以显示“添加应用”边栏选项卡。 在“添加应用”边栏选项卡上，选择“Windows 10”作为“应用类型”。 然后，选择“配置应用套件”，以选择要安装的应用。 有关适用于 Windows 10 设备的 Office 365 应用的详细信息，请参阅[使用 Microsoft Intune 将 Office 365 应用分配给 Windows 10 设备](apps-add-office365.md)。

#### <a name="microsoft-visio-pro-for-office-365-product-name-change----3593653----"></a>Microsoft Visio Pro for Office 365 产品名称更改 <!-- 3593653  -->
Microsoft Visio Pro for Office 365 现在称为 Microsoft Visio Online 计划 2。  有关 Microsoft Visio 的详细信息，请参阅 [Visio Online 计划 2](https://products.office.com/visio/visio-online-plan-2)。 有关适用于 Windows 10 设备的 Office 365 应用的详细信息，请参阅[使用 Microsoft Intune 将 Office 365 应用分配给 Windows 10 设备](apps-add-office365.md)。

#### <a name="intune-app-protection-policy-app-character-limit-setting----3291302----"></a>Intune 应用保护策略 (APP) 字符限制设置 <!-- 3291302  -->
Intune 管理员可以指定 Intune APP“限制使用其他应用剪切、复制和粘贴”策略设置的例外情况。  管理员可以指定可能会从托管应用中剪切或复制的字符数。 此设置允许将指定数量的字符共享到任何应用，而不受“限制使用其他应用剪切、复制和粘贴”设置的限制。 请注意，适用于 Android 的 Intune 公司门户应用版本需要 5.0.4364.0 或更高版本。 有关详细信息，请参阅 [iOS 数据保护](app-protection-policy-settings-ios.md#data-protection)、[Android 数据保护](app-protection-policy-settings-android.md#data-protection)和[查看客户端应用保护日志](app-protection-policy-settings-log.md#app-protection-policy-settings)。

#### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477-----"></a>用于进行 Office ProPlus 部署的 Office 部署工具 (ODT) XML <!-- 3192477   -->
在 Intune 管理控制台中创建 Office Pro Plus 实例时，将能够提供 Office 部署工具 (ODT) XML。 如果现有的 Intune UI 选项无法满足需求，这将允许进行更多自定义。 有关详细信息，请参阅[使用 Microsoft Intune 将 Office 365 应用分配到 Windows 10 设备](https://docs.microsoft.com/intune/apps-add-office365)以及 [Office 部署工具的配置选项](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool)。

#### <a name="app-icons-will-now-be-displayed-with-an-automatically-generated-background----1429026----"></a>现在将显示自动生成背景的应用图标 <!-- 1429026  -->
在 Windows 公司门户应用中，现在将显示应用图标，其中的背景根据图标主色（如果可检测到）自动生成。 如果适用，此背景将替换以前应用磁贴上显示的灰色边框。 用户将在 10.3.3451.0 之后的公司门户版本中看到此更改。

#### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523-----"></a>在 Windows 批量注册后，使用公司门户应用安装可用的应用 <!-- 2751523   -->
使用 [Windows 批量注册](windows-bulk-enroll.md)（预配包）注册到 Intune 的 Windows 设备将能够使用公司门户应用安装可用的应用。 有关公司门户应用的详细信息，请参阅[手动添加 Windows 10 公司门户](store-apps-company-portal-app.md)和[如何配置 Microsoft Intune 公司门户应用](company-portal-app.md)。

> [!Note]
> 此功能尚未完全部署到所有客户。 如果无法在批量注册的设备上使用公司门户，则可能需要等到此更改发布到你的帐户时才能使用。

#### <a name="the-microsoft-teams-app-can-be-selected-as-part-of-the-office-app-suite----3828932----"></a>可以选择 Microsoft Teams 应用作为 Office 应用套件的一部分 <!-- 3828932  -->
在安装 Office Pro Plus 应用套件的过程中，可以包含或排除 Microsoft Teams 应用。 此功能适用于 Office Pro Plus 内部版本号 16.0.11328.20116+。 用户必须先注销，然后登录设备，才能完成安装。 在 Intune 中，选择“客户端应用” > “应用” > “添加”。 选择一种“Office 365 套件”应用类型，然后选择“配置应用套件”。

### <a name="device-configuration"></a>设备配置

#### <a name="automatically-start-an-app-when-running-multiple-apps-in-kiosk-mode-on-windows-10-and-later-devices----2351390---"></a>在 Windows 10 及更高版本的设备上以展台模式运行多个应用时自动启动应用 <!-- 2351390 -->

在 Windows 10 及更高版本的设备上，能够以展台模式运行设备，并运行许多应用。 在此更新中，可以进行自动启动设置（依次选择“设备配置” > “配置文件” > “创建配置文件” >  针对平台选择“Windows 10 和更高版本”> 针对配置文件类型选择“展台”>“多应用展台”）。 使用此设置可在用户登录设备时自动启动应用。

要查看所有展台设置的列表和说明，请参阅 [Intune 中作为展台运行的 Windows 10 和更高版本设备的设置](kiosk-settings-windows.md)。

适用于：Windows 10 及更高版本

#### <a name="operational-logs-also-show-details-on-non-compliant-devices----4063755----"></a>操作日志还显示有关不合规设备的详细信息 <!-- 4063755  -->
将 Intune 日志路由到 Azure 监视器功能时，还可以路由操作日志。 在此更新中，操作日志还提供有关不合规设备的信息。 

有关此功能的详细信息，请参阅[在 Intune 中将日志数据发送到存储、事件中心或日志分析](review-logs-using-azure-monitor.md)。

#### <a name="route-logs-to-azure-monitor-in-more-intune-workloads----3804627---"></a>在更多 Intune 工作负载中，将日志路由到 Azure Monitor <!-- 3804627 -->
在 Intune 中，可以将审核和操作日志路由到 Azure Monitor 中的事件中心、存储和日志分析（依次选择“Intune” > “监视” > “诊断设置”）。 在此更新中，可以路由更多 Intune 工作负载中的这些日志，包括合规性、配置、客户端应用等。 

要了解有关将日志路由到 Azure Monitor 的详细信息，请参阅[将日志数据发送到存储、事件中心或日志分析](review-logs-using-azure-monitor.md)。

#### <a name="create-and-use-mobility-extensions-on-android-zebra-devices-in-intune----3305880-----"></a>使用 Android Zebra 设备在 Intune 中创建和使用移动扩展 <!-- 3305880   -->
在此更新中，Intune 支持配置 Android Zebra 设备。 具体来说，可以创建设备配置文件，并使用 StageNow 生成的移动扩展 (MX) 配置文件将设置应用于 Android Zebra 设备（依次选择“设备配置” > “配置文件” > “创建配置文件” >  针对平台选择“Android”> 针对配置文件类型选择“MX 配置文件(仅限 Zebra)”）。

有关此功能的详细信息，请参阅[通过 Intune 中的移动扩展使用和管理 Zebra 设备](android-zebra-mx-overview.md)。

适用于：Android

### <a name="device-management"></a>设备管理

#### <a name="encryption-report-for-windows-10-devices-in-public-preview---2351538---"></a>Windows 10 设备的加密报表（公共预览版）<!-- 2351538 -->  
使用新的[加密报表（预览版）](encryption-monitor.md)查看关于 Windows 10 设备加密状态的详细信息。 可用的详细信息包括设备 TPM 版本、加密准备和状态、错误报告等。  

#### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-in-public-preview----2351547-----"></a>从 Intune 门户访问 BitLocker 恢复密钥（公共预览版） <!-- 2351547   -->  
现在可以使用 Intune 从 Azure Active Directory [查看有关 BitLocker 密钥 ID 和 BitLocker 恢复密钥的详细信息](encryption-monitor.md)。

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Microsoft Edge 支持 iOS 和 Android 设备上的 Intune 方案 <!-- 3411007 -->
Microsoft Edge 将增加对最终用户体验的改进，支持与 Intune 托管浏览器相同的所有管理方案。 Intune 策略启用的 Microsoft Edge 企业功能包括双重标识、应用保护策略集成、Azure 应用程序代理集成、托管收藏夹和主页快捷方式。 有关详细信息，请参阅 [Microsoft Edge 支持](app-configuration-managed-browser.md#microsoft-edge-support)。

#### <a name="exchange-onlineintune-connector-deprecate-support-for-eas-only-devices---3105122----"></a>Exchange Online/Intune 连接器不再支持只有 EAS 的设备 <!--3105122  -->
Intune 控制台不再支持查看和管理使用 Intune 连接器连接到 Exchange Online 的只有 EAS 的设备。 但你有以下选项：
- 在移动设备管理 (MDM) 中注册设备
- 使用 Intune 应用保护策略管理设备
- 使用 [Exchange Online 中的客户端和移动设备](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online)中所述的 Exchange 控件

### <a name="search-the-all-devices-page-for-an-exact-device-by-using-name---4254930---"></a>使用[名称]在“所有设备”页中精确搜索设备 <!--4254930 -->
现在可以精确搜索的设备名。 转到“Intune” > “设备” > “所有设备”> 在搜索框中，使用 {} 将设备名括起来，以精确搜索匹配项。 例如，{Device12345}。

### <a name="monitor-and-troubleshoot"></a>监视和故障排除

#### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202----"></a>支持“租户状态”页上的其他连接器 <!-- 3617202  -->
[“租户状态”页](tenant-status.md)现可显示其他连接器的状态信息，包括 Windows Defender 高级威胁防护 (ATP) 和其他 Mobile Threat Defense 连接器。

### <a name="role-based-access-control"></a>基于角色的访问控制

#### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917----"></a>向某些 Azure Active Directory 角色授予 Intune 只读访问权限 <!-- 3637917  -->
已向以下 Azure AD 角色授予 Intune 只读访问权限。 通过 Azure AD 角色授予的权限取代了通过 Intune 基于角色的访问控制 (RBAC) 授予的权限。

对 Intune 审核数据的只读访问权限：

- 合规性管理员
- 符合性数据管理员

对所有 Intune 数据的只读访问权限：

- 安全管理员
- 安全操作员
- 安全性读者

有关详细信息，请参阅[基于角色的访问控制](role-based-access-control.md)。

#### <a name="scope-tags-for-ios-app-provisioning-profiles---2934430-----"></a>iOS 应用预配配置文件的范围标记 <!--2934430   -->
可以向 iOS 应用预配配置文件添加范围标记，以便只有角色也分配有该范围标记的人员才能够访问 iOS 应用预配配置文件。 有关详细信息，请参阅[使用 RBAC 和范围标记](scope-tags.md)。

#### <a name="scope-tags-for-app-configuration-policies---2371891-----"></a>应用配置策略的范围标记 <!--2371891   -->
可以向应用配置策略添加范围标记，以便只有角色也分配有该范围标记的人员才能够访问应用配置策略。 应用配置策略仅针对或关联到分配有相同范围标记的应用。 有关详细信息，请参阅[使用 RBAC 和范围标记](scope-tags.md)。

### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Microsoft Edge 支持 iOS 和 Android 设备上的 Intune 方案 <!-- 3411007 -->
Microsoft Edge 将增加对最终用户体验的改进，支持与 Intune 托管浏览器相同的所有管理方案。 Intune 策略启用的 Microsoft Edge 企业功能包括双重标识、应用保护策略集成、Azure 应用程序代理集成、托管收藏夹和主页快捷方式。 有关详细信息，请参阅 [Microsoft Edge 支持](app-configuration-managed-browser.md#microsoft-edge-support)。

## <a name="week-of-february-25-2019"></a>2019 年 2 月 25 日当周

### <a name="device-configuration"></a>设备配置

#### <a name="intune-powershell-module----951068----"></a>Intune PowerShell 模块 <!-- 951068  -->
现在，[Microsoft PowerShell 库](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune/6.1902.1.10)中提供了 Intune PowerShell 模块，该模块可通过 Microsoft Graph 提供对 Intune API 的支持。

- [有关如何使用此模块的详细信息](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/README.md)
- [使用此模块的方案示例](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/Samples/README.md)

#### <a name="improved-support-for-delivery-optimization----3183757----"></a>改进了对传递优化的支持  <!--3183757  -->
我们扩展了 Intune 中对配置传递优化的支持。 现在可以配置[传递优化设置](delivery-optimization-settings.md)的扩展列表，并直接从 Intune 控制台将其定向到设备。


## <a name="week-of-february-18-2019"></a>2019 年 2 月 18 日当周

### <a name="app-management"></a>应用管理

#### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355-----"></a>Intune 将在 Android 设备上使用 Google Play 保护 API <!-- 2577355   -->
某些 IT 管理员面临着 BYOD 情况，最终用户可能会使他们的手机获取 root 权限或越狱。 此行为虽然有时并非恶意，但会导致绕过许多 Intune 策略，这些策略是为了保护组织在最终用户设备上的数据而设置的。 因此，Intune 为已注册和未注册的设备提供 root 权限和越狱检测。 在此版本中，Intune 现在将利用 Google Play 保护 API 添加到我们对未注册设备的现有 root 权限检测检查。 虽然 Google 不会共享发生的所有 root 权限检测检查，但我们预期这些 API 能够检测出因设备自定义而导致设备获取 root 权限的用户，以及能够在旧设备上获得较新 OS 更新的用户。 然后，可以阻止这些用户访问公司数据，或者可以从其启用策略的应用中删除其公司帐户。 为了获得额外价值，IT 管理员现在将在 Intune 应用保护边栏选项卡中进行多次报告更新 -“已标记的用户”报告将显示通过 Google Play 保护的 SafetyNet API 扫描检测到的用户，“潜在有害应用”报告将显示通过 Google 的验证应用 API 扫描检测到的应用。 此功能在 Android 中可用。

#### <a name="win32-app-information-available-in-troubleshooting-blade----2617342-----"></a>“故障排除”边栏选项卡显示的 Win32 应用信息 <!-- 2617342   -->
现在可以从 Intune 应用“排除故障”边栏选项卡收集 Win32 应用安装的失败日志文件。 有关应用安装排除故障的详细信息，请参阅[排查应用安装问题](troubleshoot-app-install.md)和[排查 Win32 应用问题](apps-win32-app-management.md#troubleshoot-win32-app-issues)。

#### <a name="app-status-details-for-ios-apps----3761235-----"></a>iOS 应用的应用状态详细信息 <!-- 3761235   -->
将出现与以下内容相关的新应用安装错误消息：
- 在共享 iPad 上安装 VPP 应用失败
- 禁用 App Store 失败
- 未能找到应用的 VPP 许可证
- 无法使用 MDM 提供程序安装系统应用
- 设备处于丢失模式或展台模式时无法安装应用
- 用户未登录 App Store 时无法安装应用

在 Intune 中，选择“客户端应用” > “应用”>“应用名称”>“设备安装状态”。 “状态详细信息”列中将提供新的错误消息。

#### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780----"></a>适用于 Windows 10 的公司门户应用中的全新应用类别屏幕<!-- 3834780  -->
添加了名为“应用类别”的新屏幕，以改善适用于 Windows 10 的公司门户中的应用浏览和选择体验。 用户现在可以看到他们的应用按照“特别推荐”、“教育”和“工作效率”等类别进行排序。 此更改将出现在公司门户 10.3.3451.0 版及更高版本中。 要查看新屏幕，请参阅[应用 UI 中的新增功能](https://docs.microsoft.com/intune/whats-new-app-ui)。 有关公司门户中应用的详细信息，请参阅[在设备上安装和共享应用](/intune-user-help/install-apps-cpapp-windows)。  

#### <a name="power-bi-compliance-app----1455231-doc-work-item---"></a>Power BI 合规性应用 <!-- 1455231 doc-work-item -->
使用 [Intune 合规性（数据仓库）](https://aka.ms/intune/datawarehouseapi/getpowerbiapp)应用访问 Power BI Online 中的 Intune 数据仓库。 使用此 Power BI 应用，可立即访问和共享预创建的报表，无需任何设置，也无需离开 Web 浏览器。 有关详细信息，请参阅[更改日志 - Power BI 合规性应用](reports-changelog.md#power-bi-compliance-app)。


### <a name="device-configuration"></a>设备配置

#### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675-----"></a>PowerShell 脚本可以在 64 位设备上的 64 位主机上运行 <!-- 1862675   -->
将 PowerShell 脚本添加到设备配置概要文件时，该脚本始终以 32 位执行，即使在 64 位操作系统上也是如此。 通过此更新，管理员可以在 64 位设备上的 64 位 PowerShell 主机中运行该脚本（“设备配置” > “PowerShell 脚本” > “添加” > “配置” > “在 64 位 PowerShell 主机中运行脚本”）。

有关使用 PowerShell 的更多详细信息，请参阅 [Intune 中的 PowerShell 脚本](intune-management-extension.md)。

适用于：Windows 10 及更高版本

#### <a name="macos-users-are-prompted-to-update-their-password----1873216---"></a>系统会提示 macOS 用户更新密码 <!-- 1873216 -->
Intune 会在 macOS 设备上强制实施 ChangeAtNextAuth 设置。 此设置会影响具有合规性密码策略或设备限制密码配置文件的最终用户和设备。 系统会提示一次最终用户更新其密码。 每当用户首次运行需要身份验证的任务（例如，登录设备）时，就会出现此提示。 在执行需要管理权限的任何操作（例如，请求密钥链访问权限）时，系统也会提示用户更新密码。 

管理员更改任何新的或现有的密码策略时，系统会再次提示最终用户更新密码。

适用于：  
macOS

#### <a name="assign-scep-certificates-to-a-userless-macos-device-----2340521----"></a>将 SCEP 证书分配给无用户的 macOS 设备  <!-- 2340521  -->
可以使用设备属性将简单证书注册协议 (SCEP) 证书分配给 macOS 设备（包括没有用户关联的设备），并将证书配置文件与 Wi-Fi 或 VPN 配置文件相关联。 此操作扩展了现有的支持，可向[运行 Windows、iOS 和 Android 的具有和没有用户关联的设备分配 SCEP 证书](certificates-scep-configure.md#create-a-scep-certificate-profile)。  此更新添加了一个选项，可在配置 macOS 的 SCEP 证书配置文件时，选择设备的证书类型。

适用于： 
- macOS

#### <a name="intune-conditional-access-ui-update------2432313-----"></a>Intune 条件访问 UI 更新   <!-- 2432313   -->
我们已对 Intune 控制台中条件访问的 UI 进行了改进。 这些地方包括：
-  使用 Azure Active Directory 中的边栏选项卡替换了 Intune“条件访问”边栏选项卡。 这将确保可在 Intune 控制台中访问[条件访问](conditional-access.md)的所有设置和配置，这仍是 Azure AD 技术。 
- 我们已将“本地访问”边栏选项卡重命名为“Exchange 访问”，并将 Exchange 服务连接器设置重定位到此重命名的边栏选项卡。  此更改合并了[配置和监视与 Exchange Online 和 Exchange 本地相关的详细信息](exchange-connector-install.md)的位置。  

#### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135-----"></a>展台浏览器和 Microsoft Edge 浏览器应用能够在 Windows 10 设备上以展台模式运行 <!-- 2935135   -->
可以在展台模式下使用 Windows 10 设备运行一个应用或多个应用。 此更新包括在展台模式下使用浏览器应用的若干更改，包括：

- 添加 Microsoft Edge 浏览器或 Kiosk Browser 以在展台设备上作为应用程序运行（“设备配置” > “配置文件” > “新配置文件” > “Windows 10 及更高版本”（针对平台）>“展台”（针对配置文件类型））。
- 可以允许或限制新的功能和设置（依次选择“设备配置” > “配置文件” > “新配置文件” >  针对平台选择“Windows 10 和更高版本”> 针对配置文件类型选择“设备限制”），包括：

  - Microsoft Edge 浏览器：
  - 使用 Microsoft Edge 展台模式
  - 空闲时间后刷新浏览器

 - 收藏夹和搜索：
  - 允许更改搜索引擎

有关这些设置的列表，请参阅：

- [将 Windows 10 及更高版本设备作为展台运行的设置](kiosk-settings-windows.md)
- [Microsoft Edge 浏览器的设备限制](device-restrictions-windows-10.md#microsoft-edge-browser)
- [收藏夹和搜索设备限制](device-restrictions-windows-10.md##favorites-and-search)

适用于：Windows 10 及更高版本

#### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774-----"></a>适用于 iOS 和 macOS 设备的新设备限制设置 <!-- 3448774   -->
你可以在运行 iOS 和 macOS 的设备上限制某些设置和功能（“设备配置” > “配置文件” > “新配置文件” > “iOS”或“macOS”（针对平台）>“设备限制”（针对配置文件类型））。 此更新添加了可以控制的更多功能和设置，包括在 iOS 设备上设置屏幕时间、更改 eSIM 设置更改和蜂窝计划等。 此外，还包括在 macOS 设备上延迟用户见到软件更新的时间和阻止内容缓存。 

要查看可以限制的功能和设置，请参阅：

- [iOS 设备限制设置](device-restrictions-ios.md)
- [macOS 设备限制设置](device-restrictions-macos.md)

适用于：

- iOS
- macOS

#### <a name="kiosk-devices-are-now-called-dedicated-devices-on-android-enterprise-devices----3598402-----"></a>在 Android Enterprise 设备上，“展台”设备现在称为“专用设备” <!-- 3598402   -->
为了与 Android 术语保持一致，“展台”将更改为适用于 Android Enterprise 设备的“专用设备”（依次选择“设备配置” > “配置文件” > “创建配置文件”> 针对平台选择“Android Enterprise”>“仅限设备所有者” > “设备限制” > “专用设备”）。

要查看可用设置，请转到[允许或限制功能的设备设置](device-restrictions-android-for-work.md#dedicated-device-settings)。

适用于：  
Android Enterprise

#### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850-3803313-----"></a>Safari 和“延迟用户软件更新可见性”iOS 设置将移至 Intune UI <!-- 3640850, 3803313   -->
对于 iOS 设备，可以设置 Safari 设置并配置软件更新。 在此更新中，这些设置将移至 Intune UI 的不同部分：

- Safari 设置已从“Safari”（“设备配置” > “配置文件” > “新配置文件” > “iOS”（针对平台）>“设备限制”（针对配置文件类型））移动到[内置应用](device-restrictions-ios.md#built-in-apps)。
- 受监督的 iOS 设备的“延迟用户软件更新可见性”设置（“软件更新” > “iOS 的更新策略”）将移至“设备限制” >  [常规](device-restrictions-ios.md#general)。  有关对现有策略的影响的详细信息，请参阅 [iOS 软件更新](software-updates-ios.md#configure-the-policy)。 

有关设置列表，请参阅：

- [iOS 设备限制](device-restrictions-ios.md) 
- [iOS 软件更新](software-updates-ios.md)

此功能适用于： 

- iOS

#### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164-----"></a>在 iOS 设备上将设备设置中的启用限制重命名为屏幕时间 <!-- 3699164   -->
可以在受监管的 iOS 设备上配置“设备设置中的启用限制”（“设备配置” > “配置文件” > “新配置文件” > “iOS”（针对平台）>“设备限制”（针对配置文件类型）>“常规”）。 在此更新中，此设置将重命名为“屏幕时间(仅监管模式)”。 

操作是相同的。 具体而言： 

- iOS 11.4.1 及更早版本：“阻止”阻止最终用户在设备设置中设置自己的限制。 
- iOS 12.0 及更高版本：“阻止”阻止最终用户在设备设置中设置自己的“屏幕时间”，包括内容和隐私限制。 升级到 iOS 12.0 的设备将不再在设备设置中看到限制选项卡。 这些设置位于“屏幕时间”。 

有关设置列表，请参阅 [iOS 设备限制](device-restrictions-ios.md#general)。

适用于： 
- iOS


### <a name="device-management"></a>设备管理

#### <a name="rename-an-enrolled-windows-device----1911112----"></a>重命名已注册的 Windows 设备 <!-- 1911112  -->
现在可以重命名已注册的 Windows 10 设备（RS4 或更高版本）。 若要执行此操作，请选择“Intune” > “设备” > “所有设备”> 选择设备 >“重命名设备”。 此功能当前不支持重命名混合 Azure AD Windows 设备。

#### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>将范围标记自动分配给具有该范围的管理员创建的资源 <!-- 3173823  -->
管理员创建资源时，分配给管理员的任何范围标记都将自动分配给这些新资源。

### <a name="monitor-and-troubleshoot"></a>监视和故障排除

#### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202----"></a>“失败注册”报表将移至“设备注册”边栏选项卡 <!-- 3560202  -->
“失败注册”报表已迁移到“设备注册”边栏选项卡的“监视”部分。 已添加两个新列（“注册方法”和“OS 版本”）。

#### <a name="company-portal-abandonment-report-renamed-to-incomplete-user-enrollments---3815076-eemiss---"></a>“公司门户放弃报表”已重命名为“部分用户注册” <!--3815076 eemiss -->
“公司门户放弃报表”已重命名为“部分用户注册”。


<!-- ########################## -->
## <a name="week-of-february-4-2019"></a>2019 年 2 月 4 日当周

### <a name="app-management"></a>应用管理

#### <a name="intune-macos-company-portal-dark-mode----3300524----"></a>Intune macOS 公司门户深色模式 <!-- 3300524  -->
Intune macOS 公司门户现在支持 macOS 的深色模式。 在 macOS 10.14+ 设备上启用深色模式时，公司门户将调整其外观以反映该模式的颜色。

<!-- ########################## -->
## <a name="week-of-january-21-2019"></a>2019 年 1 月 21 日当周

### <a name="app-management"></a>应用管理

#### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Win32 应用的 Toast 通知 <!-- 3136566   -->
可以取消显示每个应用分配的最终用户 Toast 通知。 在 Intune 中，依次选择“客户端应用” > “应用”> 应用 >“分配” > “包括组”。 

#### <a name="intune-app-protection-policies-ui-update----3251427----"></a>Intune 应用保护策略用户界面更新 <!-- 3251427  -->
我们已更改 Intune 应用保护的设置和按钮的标签，以使用户更容易理解每个选项。 一些更改包括：  
- 控件从“是” / “否”控件更改为主要“阻止” / “允许”和“禁用” / “启用”控件。 标签也会更新。  
- 将对设置重新设置格式，以在控件中并排显示设置及其标签，从而提供更好的浏览。   

默认设置和设置数目将保持不变，但此更改可使用户更轻松地了解、浏览以及利用设置，以应用所选的应用保护策略。 有关信息，请参阅 [iOS 设置](app-protection-policy-settings-ios.md)和 [Android 设置](app-protection-policy-settings-android.md)。

### <a name="additional-settings-for-outlook----3301182----"></a>Outlook 的其他设置 <!-- 3301182  -->
现在可以使用 Intune 为 iOS 和 Android 配置 Outlook 以下其他设置：

- 仅允许在 iOS 和 Android 的 Outlook 中使用工作或学校帐户
- 部署适用于 Office 365 和混合新式身份验证本地帐户的新式身份验证
- 选择基本身份验证时，请使用 `SAMAccountName` 作为电子邮件配置文件中的用户名字段
- 允许保存联系人
- 配置外部收件人邮件提示
- 配置“重点收件箱”
- 需要进行生物识别来访问适用于 iOS 的 Outlook
- 阻止外部图像

> [!NOTE]
> 如果使用 Intune 应用保护策略来管理公司标识的访问权限，则应考虑不启用“需要生物识别”。 有关详细信息，请参阅 [iOS 访问设置](app-protection-policy-settings-ios.md#access-requirements)和 [Android 访问设置](app-protection-policy-settings-android.md#access-requirements)的“必须有公司凭据才能访问”。

有关详细信息，请参阅 [Microsoft Outlook 配置设置](app-configuration-policies-outlook.md)。

#### <a name="delete-android-enterprise-apps----1352553---"></a>删除 Android Enterprise 应用 <!-- 1352553 -->
可以从 Microsoft Intune 中删除托管 Google Play 应用。 若要删除托管 Google Play 应用，请在 Azure 门户中打开“Microsoft Intune”，并依次选择“客户端应用” > “应用”。 在应用列表中，选择托管 Google Play 应用右侧的省略号 (...)，再从随即显示的列表中选择“删除”。 从应用列表删除托管的 Google Play 应用时，托管的 Google Play 应用会自动变为未批准状态。

#### <a name="managed-google-play-app-type----1352580---"></a>“托管 Google Play”应用类型 <!-- 1352580 -->
“托管的 Google Play”应用类型让你可以专门将[托管的 Google Play 应用](https://play.google.com/work/search?q=microsoft&c=apps)添加到 Intune。 作为 Intune 管理员，现在可以在 Intune 中浏览、搜索、批准、同步和分配已批准的托管 Google Play 应用。  不再需要单独转到托管 Google Play 控制台，也不再需要重新进行身份验证。  在 Intune 中，选择“客户端应用” > “应用” > “添加”。 在“应用类型”列表中，将应用类型选择为“托管的 Google Play”。

### <a name="default-android-pin-keyboard----3802457---"></a>默认为 Android PIN 键盘 <!-- 3802457 -->
对于在 Android 设备上使用“数字”PIN 类型设置 Intune 应用保护策略 (App) PIN 的最终用户来说，他们将看到默认的 Android 键盘，而不是之前设计的固定 Android 键盘 UI。 在 Android 和 iOS 上使用默认键盘时，此更改对于“数字”和/或“密码”这两种 PIN 类型是一致的。 有关 Android 上最终用户访问设置的详细信息，如应用 PIN，请参阅 [Android 访问要求](app-protection-policy-settings-android.md#access-requirements)。

### <a name="device-configuration"></a>设备配置

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview----2055484-----"></a>结合使用 Microsoft 建议设置与安全基线（公共预览版） <!-- 2055484   -->

Intune 可与其他专注于安全性的服务集成，包括 Windows Defender ATP 和 Office 365 ATP。 客户要求能在各项 Microsoft 365 服务中采用通用策略和一组统一的端到端安全工作流。 我们的目标是实现策略一致，构建连接安全操作和常见管理员任务的解决方案。 在 Intune 中，我们旨在通过发布一组 Microsoft 推荐的“安全基线”（“Intune” > “安全基线”）来实现这一目标。  管理员可以直接通过这些基线创建安全策略，再将它们部署到用户。 还可以自定义最佳做法建议，以满足组织需求。 Intune 可确保设备始终符合这些基线，并通知不符合的用户管理员或设备。

此功能存在于公共预览版，因此现在创建的任何配置文件都不会转移到通用 (GA) 的安全基线模板。 不应计划在生产环境中使用这些预览模板。

若要详细了解安全基线，请参阅[在 Intune 中创建 Windows 10 安全基线](security-baselines-monitor.md)。

此功能适用于：Windows 10 及更高版本

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>非管理员可以在已加入 Azure AD 的 Windows 10 设备上启用 BitLocker<!-- 2147379   -->
在 Windows 10 设备上启用 BitLocker 设置时（“设备配置” > “配置文件” > “创建配置文件” > “Windows 10 及更高版本”作为平台 >“Endpoint protection”作为配置文件类型 >“Windows 加密”），将添加 BitLocker 设置。 

此更新包括新的 BitLocker 设置，以允许标准用户（非管理员）启用加密。 

若要查看设置，请转到[适用于 Windows 10 的 Endpoint Protection 设置](endpoint-protection-windows-10.md#windows-encryption)。

#### <a name="check-for-configuration-manager-compliance----2192052--eepublished----"></a>检查 Configuration Manager 合规性 <!-- 2192052  eepublished  -->
此更新包括新的 System Center Configuration Manager 符合性设置（“设备符合性” > “策略” > “创建策略” > “Windows 10 及更高版本” > “Configuration Manager 符合性）。 Configuration Manager 向 Intune 符合性发送信号。 使用此设置，可以要求所有 Configuration Manager 信号都返回“符合”。

例如，要求所有软件更新都安装在设备上。 在 Configuration Manager 中，此要求具有“已安装”状态。 如果设备上的任意计划处于未知状态，此设备在 Intune 中不符合要求。

[Configuration Manager 符合性](compliance-policy-create-windows.md#configuration-manager-compliance)介绍了此设置。

适用于：Windows 10 及更高版本

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324-----"></a>使用设备配置配置文件在受监管的 iOS 设备上自定义壁纸 <!-- 2809324   -->
为 iOS 设备创建设备配置文件时，可以自定义一些功能（“设置配置” > “配置文件” > “创建配置文件” > “iOS”（作为平台）>“设备功能”（作为配置文件类型））。 此更新包括新的墙纸设置，可便于管理员在主屏幕或锁定屏幕上使用 .png、.jpg 或 .jpeg 格式图像。 这些壁纸设置仅适用于受监督的设备。 

有关这些设置的列表，请参阅 [iOS 设备功能设置](ios-device-features-settings.md)。

#### <a name="windows-10-kiosk-is-generally-available----3594661----"></a>Windows 10 展台已全面推出 <!-- 3594661  -->
在此更新中，Windows 10 及更高版本设备上的展台功能已全面推出（正式版）。 若要查看可以添加和配置的所有设置，请参阅[适用于 Windows 10（及更高版本）的展台设置](kiosk-settings.md)。

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396-----"></a>在“设备限制”>“Android Enterprise 的设备所有者”中删除“通过蓝牙共享联系人” <!-- 3598396   -->
在创建 Android Enterprise 设备的设备限制配置文件时，会有一个“通过蓝牙共享联系人”设置。 在此更新中，“通过蓝牙共享联系人”设置遭删除（“设备配置” > “配置文件” > “创建配置文件” > “Android Enterprise”（作为平台）>“设备限制”>“设备所有者”（作为配置文件类型）>“常规”）。 

Android Enterprise 设备所有者管理不支持“通过蓝牙共享联系人”设置。 因此，在删除此设置时，即使在环境中启用并配置了此设置，此更改也不会影响任何设备或租户。

要查看设置的当前列表，请转到[用于允许或限制功能的 Android Enterprise 设备设置](device-restrictions-android-for-work.md)。

适用于：Android Enterprise 设备所有者

### <a name="device-management"></a>设备管理

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>对未注册的 WIP 设备的选择性擦除支持 <!-- 1434452 -->
未注册的 Windows 信息保护 (WIP-WE) 允许客户保护其在 Windows 10 设备上的公司数据，而不需要完整的 MDM 注册。 使用 WIP-WE 策略保护文档后，Intune 管理员可以选择性擦除受保护的数据。 通过选择用户和设备，并发送擦除请求，所有通过 WIP-WE 策略保护的数据都将不可用。 从 Azure 门户中的 Intune，选择“移动应用” > “应用选择性擦除”。

### <a name="monitor-and-troubleshoot"></a>监视和故障排除

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services----3762211----"></a>新推出运行日志，以及向 Azure Monitor 服务发送日志的功能 <!-- 3762211  -->
Intune 有内置审核日志，可以在事件变更时跟踪事件。 此更新包含新日志功能，包括： 
- 运行日志（预览版）显示已注册用户和设备的详细信息，其中包括成功和失败尝试次数。
- 可将审核日志和运行日志发送到 Azure Monitor，包括存储帐户、事件中心和 Log Analytics。 借助这些服务，可以存储数据、使用分析工具（如 Splunk 和 QRadar），并能获取日志数据的可视化效果。

[使用 Intune 将日志数据发送到存储、事件中心或 Log Analytics](review-logs-using-azure-monitor.md) 详细介绍了此功能。

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509----"></a>在 iOS DEP 设备上跳过更多设置助理屏幕 <!-- 2687509  -->
除了当前可以跳过的屏幕之外，还可以将 iOS DEP 设备设置为在用户注册设备时跳过设置助理中的以下屏幕：显示色调、隐私、Android 迁移、主页按钮、iMessage 和 FaceTime、载入、监视迁移、外观、屏幕时间、软件更新、SIM 安装程序。
若要选择要跳过的屏幕，请转到“设备注册” > “Apple 注册” > “注册计划令牌”> 选择令牌 >“配置文件”> 选择配置文件 >“属性” > “设置助理的自定义项”> 对于要跳过的任何屏幕选择“隐藏”>“确定”。
如果你新建或编辑配置文件，选定跳过屏幕需要与 Apple MDM 服务器同步。 用户可以发起手动同步设备，这样在选取配置文件变更时就不会有任何延迟。

#### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android Enterprise APP-WE 应用部署 <!-- 1171203 -->
对于没有注册 (APP-WE) 部署方案的未注册应用保护策略中的 Android 设备，现在可以使用托管的 Google Play 将应用商店应用和 LOB 应用部署到用户。 具体而言，可以向最终用户提供应用目录以及不再需要最终用户通过允许从未知源进行安装来放宽其设备的安全状况的安装体验。 此外，此部署方案将改进最终用户体验。

<!-- ########################## -->
## <a name="week-of-january-14-2019"></a>2019 年 1 月 14 日当周

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>对 Android 公司拥有的完全托管设备的支持（预览版） <!-- 1574342  -->
Intune 现支持完全托管的 Android 设备，这是公司拥有的“设备所有者”方案，其中设备由 IT 管理员严格管理并与各个用户关联。 这样，管理员便可以管理整个设备、强制扩展不可用于工作配置文件的策略控制的范围并限制用户仅从托管的 Google Play 安装应用。 有关详细信息，请参阅[设置 Android 完全托管的设备的 Intune 注册](android-fully-managed-enroll.md)和[注册专用设备或完全托管的设备](android-dedicated-devices-fully-managed-enroll.md)。  请注意，此功能处于预览状态。 Android 完全托管的用户设备目前无法使用部分 Intune 功能，例如证书、符合性以及条件访问。

<!-- ########################## -->
## <a name="week-of-january-7-2019"></a>2019 年 1 月 7 日当周

### <a name="app-management"></a>应用管理

#### <a name="intune-app-pin----2298397---"></a>Intune 应用 PIN <!-- 2298397 -->
作为 IT 管理员，你现在可以配置在最终用户必须更改其 Intune 应用 PIN 之前可以等待的天数。 新设置是在该等待天数之后重置的 PIN，同时，通过选择“Intune”“客户端应用” > “应用保护策略” > “创建策略” > “设置” > “访问要求” > ，便会在 Azure 门户中提供新设置。 可用于 [iOS](app-protection-policy-settings-ios.md) 和 [Android](app-protection-policy-settings-android.md) 设备，此功能支持正整数。


#### <a name="intune-device-reporting-fields----2748738---"></a>Intune 设备报告字段 <!-- 2748738 -->
Intune 提供其他设备报告字段，包括 Android 注册 ID、Android 制造商、模型和安全修补程序版本以及 iOS 型号。 在 Intune 中，通过选择“客户端应用” > “应用保护状态”并选择“应用保护报告: iOS、Android”来获取这些字段。 此外，这些参数将帮助你配置设备制造商“允许”列表 (Android)、设备型号的“允许”列表（Android 和 iOS）和最低 Android 安全修补程序版本设置。 


### <a name="device-configuration"></a>设备配置

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>管理模板为公共预览版，并移动到其自己的配置文件 <!-- 3322847 -->

Intune 中的管理模板（“设备配置” > “管理模板”）当前为公共预览版。 借助此更新：

- 管理模板包括可在 Intune 中托管的大约 300 个设置。 以前，这些设置仅存在于组策略编辑器中。
- 管理模板现已推出公共预览版。
- 管理模板从“设备配置” > “管理模板”移动到“设备配置” > “配置文件” > “创建配置文件”> 在“平台”中，选择“Windows 10 及更高版本”，在“配置文件类型”中，选择“管理模板”。
- 已启用报告

有关此功能的更多信息，请转到[用于配置组策略设置的 Windows 10 模板](administrative-templates-windows.md)。

适用于：Windows 10 及更高版本

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user-----1333642---"></a>使用 S/MIME 对用户的多个设备进行加密和签名  <!-- 1333642 -->
此更新包括使用新导入的证书配置文件进行 S/MIME 电子邮件加密（“设备配置” > “配置文件” > “创建配置文件”>“选择平台”>“PKCS 导入的证书”配置文件类型）。 在 Intune 中，可以 PFX 格式导入证书。 然后 Intune 可以将这些相同的证书传递给单个用户注册的多个设备。 还包括：
- 本机 iOS 电子邮件配置文件支持使用 PFX 格式的导入证书启用 S/MIME 加密。
- Windows Phone 10 设备上的本机电子邮件应用自动使用 S/MIME 证书。
- 可以跨多个平台传递私有证书。 但并非所有电子邮件应用都支持 S/MIME。
- 在其他平台上，可能需要手动配置电子邮件应用以启用 S/MIME。  
- 支持 S/MIME 加密的电子邮件应用可能以 MDM 不支持的方式（例如从发布者的证书存储读取）处理对 S/MIME 电子邮件加密的证书检索。
有关此功能的详细信息，请参阅[对电子邮件进行签名和加密的 S/MIME 概述](certificates-s-mime-encryption-sign.md)。
在以下设备上受支持：Windows、Windows Phone 10、macOS、iOS、Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>用于在 Windows 10 及更高版本设备上使用 DNS 设置时自动连接并保留规则的新选项 <!-- 1333665, 2999078 -->
在 Windows 10 及更高版本设备上，可以创建包含 DNS 服务器列表的 VPN 配置文件来解析域，如 contoso.com。 这一升级包括名称解析的新设置（“设备配置” > “配置文件” > “创建配置文件”> 选择“Windows 10 及更高版本”作为平台 > 选择“VPN”作为配置文件类型 >“DNS 设置” >“添加”）： 
- **自动连接**：如果为“已启用”，则当设备与所输入的域（如 contoso.com）通信时，会自动连接到 VPN。
- **永久性**：默认情况下，只要使用此 VPN 配置文件连接设备，所有名称解析策略表 (NRPT) 规则就会处于活动状态。 当 NRPT 规则的此设置为“已启用”时，该规则将在设备上保持活动状态，即使 VPN 断开连接也是如此。 该规则会保持活动状态，直到删除 VPN 配置文件或手动删除该规则，删除操作可以使用 PowerShell 完成。
[Windows 10 VPN 设置](vpn-settings-windows-10.md)介绍了设置。 

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>在 Windows 10 设备上使用 VPN 配置文件的受信任网络检测 <!-- 1500165 -->
使用受信任的网络检测时，可以在用户已使用受信任的网络时阻止 VPN 配置文件自动创建 VPN 连接。 通过此更新，可以添加 DNS 后缀，以便在运行 Windows 10 及更高版本的设备上启用受信任的网络检测（“设备配置” > “配置文件” > “创建配置文件” > “Windows 10 及更高版本”作为平台 >“VPN”作为配置文件类型）。
[Windows 10 VPN 设置](vpn-settings-windows-10.md)列出了当前的 VPN 设置。

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users----1907917-1063203---"></a>管理多个用户使用的 Windows Holographic for Business 设备 <!-- 1907917, 1063203 -->
目前，你可以在使用自定义 OMA-URI 设置的 Windows 10 和 Windows Holographic for Business 设备上配置共享电脑设置。 通过此更新，会添加新的配置文件以配置共享设备设置（“设备配置” > “配置文件” > “创建配置文件” > “Windows 10 及更高版本” > “共享多用户设备”）。
若要了解关于此功能的更多信息，请转到[用于托管共享设备的 Intune 设置](shared-user-device-settings.md)。
适用于：Windows 10 及更高版本、Windows Holographic for Business

#### <a name="new-windows-10-update-settings---2626030--2512994----"></a>新的 Windows 10 更新设置 <!--2626030  2512994  -->
对于 [Windows 10 更新通道](windows-update-for-business-configure.md)，可以配置：
- **自动更新行为** - 使用新选项“重置为默认值”，在运行“2018 年 10 月更新”的 Windows 10 计算机上还原初始的自动更新设置
- **阻止用户暂停 Windows 更新** - 配置新的软件更新设置，使你能够阻止或允许用户通过其计算机的“设置”暂停更新安装。 

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>iOS 电子邮件配置文件可以使用 S/MIME 签名和加密 <!-- 2662949 -->
你可以创建包含不同设置的电子邮件配置文件。 此更新包括可用于在 iOS 设备上对电子邮件通信进行签名和加密的 S/MIME 设置（“设备配置” > “配置文件” > “创建配置文件”> 选择“iOS”作为平台 >“电子邮件”作为配置文件类型）。
[iOS 电子邮件配置设置](email-settings-ios.md)列出了设置。

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>某些 BitLocker 设置支持 Windows 10 专业版<!-- 2727036 -->
你可以创建在 Windows 10 设备上设置 Endpoint Protection 设置的配置文件，包括 BitLocker。 此更新会为某些 BitLocker 设置添加对 Windows 10 专业版的支持。 若要查看这些保护设置，请转到[适用于 Windows 10 的 Endpoint protection 设置](endpoint-protection-windows-10.md#windows-encryption)。

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>Azure 门户中的共享设备配置将重命名为适用于 iOS 设备的“锁屏消息”<!-- 2809362 -->
创建适用于 iOS 设备的配置文件时，你可以添加“共享设备配置”设置以在锁屏上显示特定文本。 此更新包括以下更改： 
- Azure 门户中的“共享设备配置”设置将重命名为“锁定屏幕消息(仅限受监督的设备)”（“设备配置” > “配置文件” > “创建配置文件”> 选择“iOS”作为平台 > 选择“设备功能”作为配置文件类型 >“锁定屏幕消息”）。
- 添加锁屏消息时，可以插入序列号、设备名称或另一个特定于设备的值作为“资产标记信息”和“锁屏脚注”中的变量。 例如，可以使用大括号输入 `Device name: {{devicename}}` 或 `Serial number is {{serialnumber}}`。 [iOS 令牌](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list)列出了可用的令牌。
[用于在锁屏上显示消息的设置](shared-device-settings-ios.md)列出了设置。

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices----2827760--"></a>添加到 iOS 设备的新 App Store、文档查看和游戏设备限制设置 <!-- 2827760-->
在“设备配置” > “配置文件” > “创建配置文件” > 平台选择“iOS”> 配置文件类型选择“设备限制”>“App Store、文档查看和游戏”中，添加了以下设置：允许托管应用将联系人写入非托管联系人帐户。允许非托管应用从托管联系人帐户中读取联系人。要查看这些设置，请转到 [iOS 设备限制](device-restrictions-ios.md#app-store-doc-viewing-gaming)。

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Android Enterprise 设备所有者设备的新通知、提示和锁屏设置 <!-- 3201839 3201843 -->
以设备所有者身份运行时，此更新包括 Android Enterprise 设备上的多项新功能。 若要使用这些功能，请转到“设备配置” > “配置文件” > “创建配置文件”> 在“平台”中，选择“Android Enterprise” > 在“配置文件类型”中，选择“仅设备所有者” > “设备限制”。

新的功能包括： 

- 禁止显示系统通知，包括传入呼叫、系统警报、系统错误等。
- 建议跳过首次打开的应用的启动教程和提示。
- 禁用高级锁屏设置，例如照相机、通知、指纹解锁等。


若要查看这些设置，请转到 [Android Enterprise 设备限制设置](device-restrictions-android-for-work.md)。

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Android Enterprise 设备所有者设备可以使用 Always On VPN 连接 <!-- 3202194 -->
在此更新中，可以在 Android Enterprise 设备所有者设备上使用始终可用的 VPN 连接。 始终可用 VPN 连接一直保持连接状态，或在用户解锁设备、设备重启或无线网络更改时立即重新连接。 还可以将连接置于“锁定”模式，该模式会阻止所有网络流量，直到 VPN 连接处于活动状态。
可以在“设备配置” > “配置文件” > “创建配置文件” >  适用于平台的“Android 企业版”>“仅设备所有者”的“设备限制”>“连接”设置中启用始终可用的 VPN。 若要查看这些设置，请转到 [Android Enterprise 设备限制设置](device-restrictions-android-for-work.md)。

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Windows 10 设备上的任务管理器中的结束进程的新设置 <!-- 3285177 --> 
此更新包括使用 Windows 10 设备上的任务管理器的结束进程的新设置。 使用设备配置文件（“设备配置” > “配置文件” > “创建配置文件”> 在“平台”中，选择“Windows 10”> 在“配置文件类型”中，选择“设备限制” > “常规”设置），选择允许或阻止此设置。
若要查看这些设置，请转到 [Windows 10 设备限制设置](device-restrictions-windows-10.md)。
适用于：Windows 10 及更高版本


### <a name="device-enrollment"></a>设备注册

#### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564---"></a>更详细的注册限制失败消息传送 <!-- 3111564 -->
不满足注册限制时，会收到更详细的错误消息。 若要查看这些消息，请转到“Intune” > “故障排除”> 并检查“注册故障”表。 有关详细信息，请参阅[注册失败列表](help-desk-operators.md#enrollment-failure-reference)。

### <a name="monitor-and-troubleshoot"></a>监视和故障排除

#### <a name="tenant-status-dashboard-----1124854---"></a>租户状态仪表板  <!-- 1124854 -->
新[租户状态页](tenant-status.md)会提供一个位置，可以在其中查看租户状态和相关详情。  该仪表板分为 4 个区域：
- **租户详细信息** - 显示租户姓名和位置、MDM 机构、租户中的注册设备总数以及许可证计数等信息。 此部分还为租户列出当前服务版本。
- **连接器状态** - 显示有关已配置的可用连接器的信息，还可以列出尚未启用的连接器。  
   根据每个连接器的当前状态，将其标记为“正常”、“警告”或“不正常”。 选择要了解的连接器，并查看其详细信息或为其配置其他信息。
-  **Intune 服务运行状况** - 显示租户活动事件或服务中断情况的详细信息。 该部分信息直接检索自 Office 消息中心。
-  **Intune 新闻** - 显示租户的活动信息。 消息包括在租户收到最新 Intune 功能时的通知等。  该部分信息直接检索自 Office 消息中心。

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10----1488939--"></a>适用于 Windows 10 的公司门户的新“帮助和支持”体验 <!-- 1488939-->
新的公司门户“帮助和支持”页有助于用户针对应用和访问问题进行故障排除和请求帮助。 在新页面中，用户可以通过电子邮件发送错误和诊断日志的详细信息，并查找其组织的支持人员详细信息。 用户还可以查找常见问题解答部分，其中带有相关 Intune 文档的链接。 

#### <a name="new-help-and-support-experience-for-intune------3307080---"></a>Intune 的新的“帮助和支持”体验   <!-- #3307080 -->
我们将在未来几天向所有租户推出新的“帮助和支持”体验。 可以在 Intune 上进行此新体验，并且可以在使用 [Azure 门户](https://portal.azure.com/)中的“Intune”边栏选项卡时对其进行访问。
通过新体验，可以用自己的语言描述问题，并获得故障排除见解和基于 Web 的修复内容。 这些解决方案通过基于规则的机器学习算法提供并依赖于用户查询。 除特定于问题的指南之外，还会使用新的案例创建工作流通过电子邮件或电话打开支持案例。 此新体验取代了一组静态预选选项的先前的“帮助和支持”体验，这些选项基于打开“帮助和支持”时所在控制台的区域。 有关详细信息，请参阅[如何获取对 Microsoft Intune 的支持](get-support.md)。

### <a name="role-based-access-control"></a>基于角色的访问控制

#### <a name="scope-tags-for-apps----1081941---"></a>应用的作用域标记 <!-- 1081941 -->
可创建作用域标记来限制对角色和应用的访问。 可向应用添加作用域标记，以便只有具有特定角色（该角色也分配有该作用域标记）的人员才可以访问该应用。 目前，无法向从托管 Google Play 添加到 Intune 的应用或使用 Apple Volume Purchase Program (VPP) 购买的应用分配作用域标记（但计划在将来提供此支持）。 有关详细信息，请参阅[使用作用域标记筛选策略](scope-tags.md)。

<!-- ########################## -->
## <a name="week-of-december-10-2018"></a>2018 年 12 月 10 日当周

### <a name="app-management"></a>应用管理

#### <a name="updates-for-application-transport-security----748318---"></a>针对应用传输安全进行更新 <!-- 748318 -->

Microsoft Intune 支持传输层安全性 (TLS) 1.2+，以提供一流的加密，确保 Intune 在默认情况下更为安全，并与 Microsoft Office 365 等其他 Microsoft 服务一致。 为了满足此要求，iOS 和 macOS 公司门户将强制执行 Apple 更新的应用程序传输层安全性 (ATS) 要求，这些要求也需要 TLS 1.2+。 使用 ATS 对所有通过 HTTPS 的应用通信实施更严格的安全措施。 此更改会影响使用 iOS 和 macOS 公司门户应用的 Intune 客户。 有关详细信息，请参阅 [Intune 支持博客](https://aka.ms/compportalats)。

#### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Intune App SDK 将支持 256 位加密密钥 <!-- 1832174 -->
由应用保护策略启用加密时，适用于 Android 的 Intune App SDK 现在将使用 256 位加密密钥。 SDK 将继续提供 128 位密钥支持以与使用旧版 SDK 的内容和应用兼容。

### <a name="microsoft-auto-update-version-450-required-for-macos-devices----3503442---"></a>macOS 设备所需的 Microsoft Auto Update 版本 4.5.0 <!-- 3503442 -->
若要继续接收公司门户和其他 Office 应用程序的更新，由 Intune 管理的 macOS 设备必须升级到 Microsoft Auto Update 4.5.0。 用户可能已经拥有此版本的 Office 应用程序。

### <a name="intune-requires-macos-1012-or-later----2827778---"></a>Intune 需要 macOS 10.12 或更高版本 <!-- 2827778 -->
Intune 现在需要 macOS 版本 10.12 或更高版本。 使用以前的 macOS 版本的设备无法使用公司门户注册到 Intune。 若要获得支持协助和新功能，用户必须将设备升级到 macOS 10.12 或更高版本，并将公司门户升级到最新版本。

<!-- ########################## -->
## <a name="week-of-november-26-2018"></a>2018 年 11 月 26 日当周

### <a name="app-management"></a>应用管理

#### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>卸载公司拥有的受监督 iOS 设备上的应用 <!-- 1281677 -->

你可以删除公司拥有的受监督 iOS 设备上的应用。 可以通过以“卸载”分配类型的用户或设备组为目标来删除任何应用。 对于个人或无监督的 iOS 设备，你将继续只能删除使用 Intune 安装的应用。

#### <a name="downloading-intune-win32-app-content----2617320---"></a>下载 Intune Win32 应用内容 <!-- 2617320 -->
Windows 10 RS3 及更高版本的客户端将在 Windows 10 客户端上使用传递优化组件下载 Intune Win32 应用内容。 传递优化提供了在默认情况下处于打开状态的对等功能。 目前，可以通过组策略配置传递优化。 有关详细信息，请参阅[适用于 Windows 10 的传递优化](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization)。 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>最终用户设备的应用内容菜单 <!-- 2771453 -->
最终用户现在可以使用设备上的上下文菜单和应用来触发常见操作，例如，重命名设备或检查合规性。

#### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>在托管的主屏幕应用中设置自定义背景  <!-- 3041945 -->
我们将添加一种设置，使你可自定义 Android Enterprise、多应用和展台模式设备上托管的主屏幕应用的背景外观。  要配置“自定义 URL 背景”，请转到的 Azure 门户中的 Intune >“设备配置”。 选择当前设备配置文件或创建新配置文件以编辑其展台设置。
若要查看展台设置，请参阅 [Android Enterprise 设备限制](device-restrictions-android-for-work.md)。

#### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>应用保护策略分配将保存并应用 <!-- 3104570 -->
现在可以更好地控制[应用保护策略分配](app-protection-policies.md#deploy-a-policy-to-users)。 选择“分配”以设置或编辑策略的分配时，必须先保存你的配置才能使更改生效。 使用“放弃”以清除你所做的所有更改，而不保存对包括或排除列表进行的任何更改。  通过要求“保存”或“放弃”，仅向你预期的用户分配应用保护策略。

#### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>适用于 Windows 10 及更高版本的新 Microsoft Edge 浏览器设置 <!-- 3174639 -->
此更新包括用于帮助控制和管理设备上的 Microsoft Edge 浏览器的新设置。 有关这些设置的列表，请参阅[适用于 Windows 10（及更高版本）的设备限制](device-restrictions-windows-10.md#microsoft-edge-browser)。

#### <a name="new-apps-support-with-app-protection-policies----3330037---"></a>具有应用保护策略的新应用支持 <!-- 3330037 -->
现在可以管理以下具有 [Intune 应用保护策略](app-protection-policies.md)的应用：
- Stream (iOS)
- To DO（Android、iOS）
- PowerApps（Android、iOS）
- Flow（Android、iOS）

使用应用保护策略来保护这些应用（如其他 Intune 策略托管应用）的公司数据和控制数据传输。 注意：如果 Flow 在控制台中尚不可见，则在创建或编辑应用保护策略时添加 Flow。 若要执行此操作，请使用“+ 更多应用”选项，然后在输入字段中指定 Flow 的“应用 ID”。 对于 Android，请使用“com.microsoft.flow”，对于 iOS，请使用“com.microsoft.procsimo”。


### <a name="device-configuration"></a>设备配置

#### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown----1892471---"></a>将显示 iOS 和 macOS 的版本号和生成号 <!-- 1892471 -->
在“设备符合性” > “设备符合性”中，iOS 和 macOS 操作系统版本都会显示，并且可在符合性策略中使用。 此更新包括可为这两个平台配置的生成号。
Apple 每次发布安全更新时，会保留版本号，更新生成号。 通过在符合性策略中使用生成号，可轻松地检查是否已安装漏洞更新。
若要使用此功能，请参阅 [iOS](compliance-policy-create-ios.md#device-health) 和 [macOS](compliance-policy-create-mac-os.md#device-properties) 符合性策略。

#### <a name="update-rings-are-being-replaced-with-delivery-optimization-settings-for-windows-10-and-later----2753807---"></a>更新通道被替换为适用于 Windows 10 及更高版本的传递优化设置 <!-- 2753807 -->
传递优化是适用于 Windows 10 及更高版本的新配置文件。 此功能可简化将软件更新传递到组织中的设备的过程。 此更新还可帮助你使用配置文件传递新更新通道和现有更新通道中的设置。
若要配置传递优化配置文件，请参阅 [Windows 10（及更高版本）传递优化设置](delivery-optimization-windows.md)。

#### <a name="new-device-restriction-settings-added-to-ios-and-macos-devices----2827760---"></a>将新设备限制设置添加到 iOS 和 macOS 设备 <!-- 2827760 -->
此更新包括随 iOS 12 发布的 iOS 和 macOS 设备的新设置：

**iOS 设置**： 
- 常规：阻止应用删除（仅监管模式）
- 常规：阻止 USB 受限模式（仅监管模式）
- 常规：强制执行自动日期和时间（仅监管模式）
- 密码:阻止密码自动填充（仅监管模式）
- 密码:阻止密码临近感应请求（仅监管模式）
- 密码:阻止密码共享（仅监管模式）

**macOS 设置**： 
- 密码:阻止密码自动填充
- 密码:阻止密码临近感应请求
- 密码:阻止密码共享

要了解有关这些设置的详细信息，请参阅 [iOS](device-restrictions-ios.md) 和 [macOS](device-restrictions-macos.md) 设备限制设置。

### <a name="device-enrollment"></a>设备注册

#### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>选择注册状态页上跟踪的应用<!-- 2531007 -->
可以选择在“注册状态”页面上跟踪的应用。 在安装这些应用之前，用户无法使用该设备。 有关详细信息，请参阅[设置注册状态页](windows-enrollment-status.md)。

#### <a name="search-for-autopilot-device-by-serial-number---2595788---"></a>按序列号搜索 Autopilot 设备 <!--2595788 -->
现在可以按序列号搜索 Autopilot 设备。 若要执行此操作，请选择“设备注册” > “Windows 注册” > “设备”> 在“按序列号搜索”框中键入序列号 > 按 Enter。

#### <a name="track-installation-of-office-proplus---2620217---"></a>跟踪 Office 专业增强版的安装过程 <!--2620217 -->
用户可以使用[注册状态页面](windows-enrollment-status.md)来跟踪 [Office 专业增强版](apps-add-office365.md)的安装进度。 有关详细信息，请参阅[设置注册状态页](windows-enrollment-status.md)。

#### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>针对即将过期的 VPP 令牌或公司门户许可证不足的警报 <!-- 2237572 -->
如果在 DEP 注册期间使用批量采购计划 (VPP) 预先设置公司门户，则在 VPP 令牌即将过期以及公司门户的许可证不足的情况下，Intune 将发出警报。

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133---"></a>macOS 设备注册计划支持 Apple School Manager 帐户 <!--3006133 -->
Intune 现在支持对 Apple School Manager 帐户使用 macOS 设备上的设备注册计划。  有关详细信息，请参阅[通过 Apple School Manager 或设备注册计划自动注册 macOS 设备](device-enrollment-program-enroll-macos.md)。

### <a name="new-intune-device-subscription-sku---3312071--"></a>新的 Intune 设备订阅 SKU <!--3312071-->
为了帮助降低企业中管理设备的成本，现在已提供基于设备的新订阅 SKU。 此 Intune 设备 SKU 按月按设备获取许可。 价格因许可计划而异。 可直接通过 Microsoft 365 管理中心，以及通过[企业协议](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2) (EA)、[Microsoft 产品和服务协议](https://www.microsoft.com/licensing/mpsa/default) (MPSA)、[Microsoft 开放式协议](https://partner.microsoft.com/licensing/licensing-agreements)和[云解决方案提供商](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453) (CSP) 获得许可。

### <a name="device-management"></a>设备管理

#### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>暂时暂停 Android 设备上的展台模式以进行更改 <!-- 3041935 -->
在多应用展台模式下使用 Android 设备时，IT 管理员可能需要对设备进行更改。 此更新包括新的多应用展台设置，允许 IT 管理员使用 PIN 临时暂停展台模式，并有权访问整个设备。
若要查看展台设置，请参阅 [Android Enterprise 设备限制](device-restrictions-android-for-work.md)。

#### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>启用 Android Enterprise 展台设备上的虚拟主页按钮  <!-- 3042021 -->
新的设置将允许用户点击其设备上的软键按钮，以在其多应用展台设备上托管的主屏幕应用和其他已分配的应用之间进行切换。 此设置在用户的展台应用未对“后退”按钮及时做出响应的情况下特别有用。 可为公司拥有的一次性 Android 设备配置此设置。 要启用或禁用“虚拟主页”按钮，请转至 Azure 门户中的 Intune >“设备配置”。 选择当前设备配置文件或创建新配置文件以编辑其展台设置。
若要查看展台设置，请参阅 [Android Enterprise 设备限制](device-restrictions-android-for-work.md)。

<!-- ########################## -->
## <a name="week-of-november-12-2018"></a>2018 年 11 月 12 日当周

### <a name="network-access-control-nac-support-for-citrix-sso-for-ios----3259404---"></a>对 Citrix SSO for iOS 的网络访问控制 (NAC) 支持 <!-- 3259404 -->

Citrix 已向 Citrix Gateway 发布更新以允许对 Intune 中的 Citrix SSO for iOS 使用网络访问控制 (NAC)。 可以选择在 Intune 中将设备 ID 包括在 VPN 配置文件中，然后将此配置文件推送到 iOS 设备。 你需要将最新更新安装到 Citrix Gateway 才能使用此功能。

[在 iOS 设备上配置 VPN 设置](vpn-settings-ios.md#base-vpn-settings)提供了有关使用 NAC 的详细信息，包括一些附加要求。 

<!-- ########################## -->
## <a name="week-of-november-5-2018"></a>2018 年 11 月 5 日当周

### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>支持 iOS 电子邮件配置文件中的 iOS 12 OAuth <!--2155106 -->

Intune 的 iOS 电子邮件配置文件支持 iOS 12 Open Authorization (OAuth)。 要查看此功能，请创建新配置文件（“设备配置” > “配置文件” > “创建配置文件” >  iOS 平台 >“电子邮件”配置文件类型），或更新现有的 iOS 电子邮件配置文件。 如果在已部署到用户的配置文件中启用 OAuth，则会提示用户重新进行身份验证，然后再次下载其电子邮件。

[iOS 电子邮件配置文件](email-settings-ios.md)提供了有关在电子邮件配置文件中使用 OAuth 的详细信息。

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview----1048100--"></a>已加入混合 Azure Active Directory 的设备的 Autopilot 支持（预览） <!-- 1048100-->
现在可以使用 Autopilot 对已加入混合 Azure Active Directory 的设备进行设置。 设备必须加入组织网络中，才能使用混合 Autopilot 功能。 有关详细信息，请参阅[使用 Intune 和 Windows Autopilot 部署已加入混合 Azure AD 的设备](windows-autopilot-hybrid.md)。
此功能将在未来几天内在整个用户群中推出。 因此，在推送到你的帐户之前，你可能无法执行这些步骤。

<!-- ########################## -->
## <a name="week-of-october-29-2018"></a>2018 年 10 月 29 日当周

### <a name="app-management"></a>应用管理

#### <a name="require-non-biometric-pin-after-a-specified-timeout----1506985---"></a>在指定的超时后需要非生物识别 PIN <!-- 1506985 -->
在管理员指定的超时时长后要求输入非生物识别 PIN，Intune 会限制使用生物识别来访问公司数据，从而为启用了移动应用管理 (MAM) 的应用提升安全性。 这些设置会影响依靠 Touch ID (iOS)、Face ID (iOS)、Android Biometric 或其他未来生物识别身份验证方法访问启用了 APP/MAM 的应用程序的用户。 这些设置会使 Intune 管理员能够更精细地控制用户访问，让带有多个指纹或其他生物识别访问方法的设备只能向正确的用户显示公司数据。 在 Azure 门户中，打开“Microsoft Intune”。 选择“客户端应用” > “应用保护策略” > “添加策略” > “设置”。 找到特定设置的“访问”部分。 有关访问设置的信息，请参阅 [iOS 设置](app-protection-policy-settings-ios.md#access-requirements)和 [Android 设置](app-protection-policy-settings-android.md#access-requirements)。

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>iOS MDM 注册设备上的 Intune 应用数据传输设置 <!-- 2244713 -->
可以将 iOS MDM 注册设备上的 Intune 应用数据传输设置控制与指定注册用户的身份（也称为用户主体名称 (UPN)）分开。 不使用 IntuneMAMUPN 的管理员不会观察到行为更改。 当此功能可用时，使用 IntuneMAMUPN 控制已注册设备上的数据传输行为的管理员应检查新设置，并根据需要更新其应用设置。

#### <a name="windows-10-win32-apps----2617325---"></a>Windows 10 Win32 应用 <!-- 2617325 -->
可以将 Win32 应用配置为在单个用户的用户上下文中安装，而不是为该设备的所有用户安装应用。

#### <a name="windows-win32-apps-and-powershell-scripts----2617330---"></a>Windows Win32 应用和 PowerShell 脚本 <!-- 2617330 -->
最终用户无需登录设备即可安装 Win32 应用或执行 PowerShell 脚本。 

#### <a name="troubleshooting-client-app-installation----1363711---"></a>客户端应用安装疑难解答 <!-- 1363711 -->
可以通过查看“故障排除”边栏选项卡中标有“应用安装”的列来解决客户端应用的安装问题。 要查看“故障排除”边栏选项卡，请在 Intune 门户中，选择“故障排除”下的“帮助和支持”。

### <a name="device-configuration"></a>设备配置

#### <a name="network-access-control-support-on-ios-vpn-clients----1333693---"></a>iOS VPN 客户端上的网络访问控制支持 <!-- 1333693 -->
通过此更新，可以在为 Cisco AnyConnect、F5 Access 和 Citrix SSO for iOS 创建 VPN 配置文件时启用网络访问控制 (NAC)。 此设置允许将设备的 NAC ID 包含在 VPN 配置文件中。 目前，没有任何支持此新 NAC ID 的 VPN 客户端或 NAC 合作伙伴解决方案，但我们将通过[支持博客文章](ttps://aka.ms/iOS12_and_vpn)发送通知。

要使用 NAC，需要：
1. 选择加入以允许 Intune 在 VPN 配置文件中包含设备 ID
2. 使用直接来自 NAC 提供程序的指导更新 NAC 提供程序软件/固件

有关 iOS VPN 配置文件中此设置的信息，请参阅[在 Microsoft Intune 的 iOS 设备上添加 VPN 设置](vpn-settings-ios.md)。 有关网络访问控制的详细信息，请参阅[网络访问控制 (NAC) 与 Intune 集成](network-access-control-integrate.md)。 

适用于：iOS

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile----1818139---"></a>即使只有一个电子邮件配置文件，也可从设备中删除该电子邮件配置文件 <!-- 1818139 -->
以前，如果只有唯一一个电子邮件配置文件，则无法从设备删除该电子邮件配置文件。 有了此更新，该行为发生了变化。 现在，即使设备上只有唯一一个电子邮件配置文件，也可删除该电子邮件配置文件。 有关详细信息，请参阅[使用 Intune 向设备添加电子邮件设置](email-settings-configure.md)。

#### <a name="powershell-scripts-and-aad----2309469---"></a>PowerShell 脚本和 AAD <!-- 2309469 -->
Intune 中的 PowerShell 脚本可应用于 AAD 设备安全组。

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>适用于 Android、Android 企业版的新的“所需密码类型”默认设置<!-- 2649963 -->
创建新的符合性策略时（“Intune” > “设备符合性” > “策略” > “创建策略” > > Android 或 Android Enterprise 平台 >“系统安全性”），所需密码类型的默认值会更改：

更改自：设备默认设置：最少数字

适用于：Android、Android Enterprise

要查看这些设置，请转到 [Android](compliance-policy-create-android.md) 和 [Android Enterprise](compliance-policy-create-android-for-work.md)。

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>在 Windows 10 Wi-Fi 配置文件中使用预共享密钥 <!-- 2662938 -->
通过本次更新，用户能够使用预共享密钥 (PSK) 和 WPA/WPA2 个人安全协议对 Windows 10 的 Wi-Fi 配置的配置文件进行身份验证。 还可以在 Windows 10 的 2018 年 10 月更新中为设备指定按流量计费的网络的成本配置。

目前，必须导入 Wi-Fi 配置文件，或创建自定义配置文件才能使用预共享密钥。 [Windows 10 的 Wi-Fi 设置](wi-fi-settings-windows.md)列出了当前设置。 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices----3218390---"></a>从设备中删除 PKCS 和 SCEP 证书 <!-- 3218390 -->
在某些情况下，即使从组中删除策略，删除配置或合规性部署，或是由管理员更新现有 SCEP 或 PKCS 配置文件，PKCS 和 SCEP 证书仍会存留在设备上。 此更新改变了这种情况。 在某些情况下，PKCS 和 SCEP 证书会从设备中删除，而在其他一些情况下，这些证书会存留在设备上。 请参阅[在 Microsoft Intune 中删除 SCEP 和 PKCS 证书](remove-certificates.md)了解这些情况。

#### <a name="use-gatekeeper-on-macos-devices-for-compliance----2504381---"></a>在 macOS 设备上使用网关守卫实现合规性 <!-- 2504381 -->
此更新包括 macOS 网关守卫，用于评估设备的符合性。 要设置网关守卫属性，请[为 macOS 设备添加设备符合性策略](compliance-policy-create-mac-os.md)。


### <a name="device-enrollment"></a>设备注册

#### <a name="enrollment-abandonment-report----1382924---"></a>注册放弃报告 <!-- 1382924 -->
我们在“设备注册” > “监视”下发布了新报表，其中提供了有关已放弃注册的详细信息。 有关详细信息，请参阅[公司门户放弃报表](enrollment-report-company-portal-abandon.md)。

#### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>新的 Azure Active Directory 使用条款功能 <!-- 2870393 -->
Azure Active Directory 具备可供使用的使用条款功能，而不必再使用现有的 Intune 条款和条件。 Azure AD 使用条款功能在显示哪些条款以及何时显示这些条款方面更加灵活，并能更好地支持本地化，更好地控制条款的呈现方式以及改进报告。 Azure AD 使用条款功能需要 Azure Active Directory Premium P1，后者也是企业移动性 + 安全性 E3 套件的一部分。 要了解详情，请参阅[管理公司的用户访问条款和条件](terms-and-conditions-create.md)一文。

#### <a name="android-device-owner-mode-support---3188762--"></a>Android 设备所有者模式支持 <!--3188762-->
对于 Samsung Knox 移动注册，Intune 现在支持将设备注册到 Android 设备所有者管理模式。 使用 WiFi 或移动电话网络的用户在第一次打开他们的设备时，只需几次点击即可进行注册。 有关详细信息，请参阅[使用 Samsung 的 Knox 移动注册自动注册 Android 设备](android-samsung-knox-mobile-enroll.md)。

### <a name="device-management"></a>设备管理
#### <a name="new-settings-for-software-updates------1907869---"></a>软件更新的新设置   <!-- 1907869 -->  
- 现在可以将某些通知配置为向最终用户发出完成最新软件更新安装后需要重新启动的警报。   
- 现在可以配置在非工作时间重新启动的重新启动警告提示，这支持 BYOD 方案。

#### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>按交换码 ID 对已注册 Windows Autopilot 的设备进行分组 <!-- 2075110 -->
通过 Configuration Manager [使用 Autopilot 为现有设备注册](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430)时，Intune 现已支持按交换码 ID 对 Windows 设备进行分组。 交换码 ID 是 Autopilot 配置文件的参数。 Intune 会自动将 [Azure AD 设备属性 enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) 设置为“OfflineAutopilotprofile - <correlator ID>”。 如此，即可通过离线 Autopilot 注册的 enrollmentprofileName 属性，根据交换码 ID 创建任意 Azure AD 动态组。 有关详细信息，请参阅[现有设备的 Windows Autopilot](enrollment-autopilot.md#windows-autopilot-for-existing-devices)。

#### <a name="intune-app-protection-policies----2984657---"></a>Intune 应用保护策略 <!-- 2984657 -->
可使用 Intune 应用保护策略为受 Intune 保护的应用（如 Microsoft Outlook 和 Microsoft Word）配置各种数据保护设置。 我们为 [iOS](app-protection-policy-settings-ios.md) 和 [Android](app-protection-policy-settings-android.md) 更改了这些设置的外观，以便更轻松地查找单个设置。 策略设置分为三类：
- **数据重定位** - 此组包含数据丢失防护 (DLP) 控件，如剪切、复制、粘贴和另存为限制。 这些设置决定了用户与应用中的数据的交互方式。
- **访问要求** - 该组包含每个应用的 PIN 选项，用于确定最终用户在工作环境中访问应用的方式。  
- **条件启动** - 该组包含最低操作系统设置、已越狱和取得 Root 权限的设备检测以及脱机宽限期等设置。  
  
设置的功能不会更改，但在处理策略创作流程时会更容易找到它们。

### <a name="intune-apps"></a>Intune 应用

#### <a name="intune-will-support-a-maximum-package-size-of-8-gb-for-lob-apps----1727158---"></a>对于 LOB 应用，Intune 将支持最大为 8 GB 的包大小 <!-- 1727158 -->
Intune 将业务线 (LOB) 应用的最大包大小增加到 8 GB。 有关详细信息，请参阅[将应用添加到 Microsoft Intune](apps-add.md)。

#### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>为公司门户应用添加自定义品牌图像 <!-- 1916266 -->
Microsoft Intune 管理员可以上传自定义品牌图像，该图像将在 iOS 公司门户应用的用户配置文件页面上作为背景图像显示。 有关配置公司门户应用的详细信息，请参阅[如何配置 Microsoft Intune 公司门户应用](company-portal-app.md)。

#### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>在最终用户计算机上更新 Office 时，Intune 将维护维持 Office 本地化语言 <!-- 2971030 -->
Intune 在最终用户计算机上安装 Office 时，最终用户将自动获得与以前安装的 .MSI Office 相同的语言包。 有关详细信息，请参阅[使用 Microsoft Intune 将 Office 365 应用分配到 Windows 10 设备](apps-add-office365.md)。

### <a name="monitor-and-troubleshoot"></a>监视和故障排除

#### <a name="new-intune-support-experience-in-the-microsoft-365-device-management-portal----3076965---"></a>Microsoft 365 设备管理门户中的新 Intune 支持体验 <!-- 3076965 -->
我们正在 [Microsoft 365 设备管理门户]( http://devicemanagement.microsoft.com)中推出适用于 Intune 的新的“帮助和支持”体验。 通过新体验，可以用自己的语言描述问题，并获得故障排除见解和基于 Web 的修复内容。 这些解决方案通过基于规则的机器学习算法提供并依赖于用户查询。  

除特定于问题的指南之外，还可以使用新的案例创建工作流通过电子邮件或电话打开支持案例。  

对于参与部署的客户，此新体验取代了一组静态预选选项的当前“帮助和支持”体验，这些选项基于打开“帮助和支持”时所在控制台的区域。  

我们正在向部分租户（不是所有租户）推出此新的“帮助和支持”体验，你可在“设备管理”门户中进行找到。此新体验的参与者是在可用的 Intune 租户中随机选择的。在我们扩大推出时，将添加新租户。  

有关详细信息，请参阅“如何获取对 Microsoft Intune 的支持”中的[“帮助和支持”体验](get-support.md#help-and-support-experience)。  

### <a name="powershell-module-for-intune--preview-available----951068---"></a>适用于 Intune 的 PowerShell 模块 - 提供预览版 <!-- 951068 -->
现在，[GitHub]( https://aka.ms/intunepowershell) 上提供了新 PowerShell 模块的预览版，该模块可通过 Microsoft Graph 提供对 Intune API 的支持。 有关如何使用此模块的详细信息，请参阅该处的自述文件。 


<!-- ########################## -->
## <a name="week-of-october-15-2018"></a>2018 年 10 月 15 日当周

### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device-----2637704----"></a>当你在 iOS 设备上更改指纹或 Face ID 时，系统将提示你输入 PIN  <!-- 2637704  -->
当用户在其 iOS 设备上进行生物识别更改后，系统将提示用户输入 PIN。 这包括对已注册的指纹或 Face ID 的更改。 出现提示的时间取决于如何配置“以下时间(以分钟为单位)之后重新检查访问要求”超时。  未设置 PIN 时，会提示用户设置一个 PIN。 
 
此功能仅适用于 iOS，并且需要集成了 Intune APP SDK for iOS 版本 9.0.1 或更高版本的应用程序参与。 必须集成 SDK，以便可以在目标应用程序上强制执行行为。 此集成陆续进行，取决于特定应用程序团队。 参与的一些应用包括 WXP、Outlook、Managed Browser 和 Yammer。


<!-- ########################## -->
## <a name="week-of-october-1-2018"></a>2018 年 10 月 1 日当周

### <a name="app-management"></a>应用管理

#### <a name="access-to-key-profile-properties-using-the-company-portal-app----772203---"></a>使用公司门户应用访问键配置文件属性 <!-- 772203 -->
最终用户现在可以从公司门户应用访问关键帐户属性和操作，如密码重置。 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>可通过 iOS 上的 APP 设置阻止第三方键盘 <!-- 1248481 -->
在 iOS 设备上，Intune 管理员可以阻止使用第三方键盘在受策略保护的应用中访问组织数据。 当应用程序保护策略 (APP) 设置为阻止第三方键盘时，设备用户将在首次使用第三方键盘与公司数据交互时收到一条消息。 将阻止本地键盘以外的所有选项，设备用户不会看到它们。 设备用户只会看到一次对话消息。 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices----1248496---"></a>托管的 Android 和 iOS 设备上的 Intune 应用的用户帐户访问权限 <!-- 1248496 -->
作为 Microsoft Intune 管理员，可控制将哪些用户帐户添加到托管设备上的 Microsoft Office 应用程序。 可以将访问权限限制为仅允许的组织用户帐户，并阻止已注册设备上的个人帐户。 

#### <a name="outlook-ios-and-android-app-configuration-policy---1828527---"></a>Outlook for iOS 和 Outlook for Android 应用配置策略 <!--1828527 -->
现在可以为通过 ActiveSync 协议进行基本身份验证的本地用户创建适用于 iOS 和 Android 的 Outlook for iOS 和 Outlook for Android 应用配置策略。 将为 Outlook for iOS 和 Outlook for Android 启用和添加其他配置设置。

#### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus 语言包 <!-- 1833450 -->
作为 Intune 管理员，你将能够为通过 Intune 管理的 Office 365 Pro Plus 应用部署其他语言。 可用语言列表包括语言包的“类型”（核心、部分和校对）。 在 Azure 门户中，选择“Microsoft Intune” > “客户端应用” > “应用” > “添加”。 在“添加应用”边栏选项卡的“应用类型”列表中，选择“Office 365 套件”下的“Windows 10”。 在“应用套件设置”边栏选项卡中选择“语言”。

####  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Windows 业务线 (LOB) 应用文件扩展名 <!-- 1884873 -->
Windows LOB 应用的文件扩展名现在包括 .msi、.appx、.appxbundle、.msix 和 .msixbundle。 可以在 Microsoft Intune 中添加应用，方法是通过选择“客户端应用” > “应用” > “添加”。 将显示“添加应用”窗格，可选择“应用类型”。 对于 Windows LOB 应用，选择“业务线”应用作为应用类型，选择“应用包文件”，然后输入带有扩展名的安装文件。

#### <a name="windows-10-app-deployment-using-intune----2309001---"></a>使用 Intune 部署 Windows 10 应用 <!-- 2309001 -->
在业务线 (LOB) 应用和适用于企业的 Microsoft Store 应用的现有支持上进行构建时，管理员可以使用 Intune 将其组织的大部分现有应用程序部署到 Windows 10 设备上的最终用户。 管理员可以使用各种格式（例如 MSI、Setup.exe 或 MSP）为 Windows 10 用户添加、安装和卸载应用程序。 Intune 将在下载和安装、使用 Windows 10 操作中心通知最终用户状态或重新启动需求之前评估要求规则。 此功能将有效地清除对将此工作负荷转移到 Intune 和云感兴趣的组织所存在的阻碍。 此功能目前处于公共预览状态，我们预计在未来的几个月内为此功能添加重要的新功能。 

#### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>适用于 Web 数据的应用保护策略 (APP) 设置 <!-- 2662995 -->
将更新 Android 和 iOS 设备上适用于 Web 内容的应用策略设置，以更好地处理 http 和 https Web 链接，以及通过 iOS 通用链接和 Android 应用链接进行的数据传输。 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>最终用户设备的应用内容菜单 <!-- 2771453 -->
最终用户现在可以在设备和应用上使用上下文菜单触发常见操作，例如重命名设备或检查符合性。 

#### <a name="windows-company-portal-keyboard-shortcuts----2771518---"></a>Windows 公司门户键盘快捷方式 <!-- 2771518 -->
最终用户现在可以使用键盘快捷方式（快捷键）在 Windows 公司门户中触发应用和设备操作。

### <a name="device-configuration"></a>设备配置

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>在运行 Windows 10 的设备上的 VPN 配置文件中创建 DNS 后缀<!-- 1333668 -->
在创建 VPN 设备配置的配置文件（“设备配置” > “配置文件” > “创建配置文件” > “Windows 10 及更高版本”平台>“VPN”配置文件类型）时，需要输入一些 DNS 设置。 通过此更新，还可以在 Intune 中输入多个 DNS 后缀。 使用 DNS 后缀时，可以使用其短名称而不是完全限定的域名 (FQDN) 搜索网络资源。 此更新还允许在 Intune 中更改 DNS 后缀的顺序。
[Windows 10 VPN 设置](vpn-settings-windows-10.md#dns-settings)列出了当前的 DNS 设置。
适用于：Windows 10 设备

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>支持 Android 企业工作配置文件的始终可用 VPN <!-- 1333705 -->
在此更新中，可以在具有托管工作配置文件的 Android 企业设备上使用始终可用的 VPN 连接。 始终可用 VPN 连接一直保持连接状态，或在用户解锁设备、设备重启或无线网络更改时立即重新连接。 还可以将连接置于“锁定”模式，该模式会阻止所有网络流量，直到 VPN 连接处于活动状态。
可以在“设备配置” > “配置文件” > “创建配置文件” >  适用于平台的“Android 企业版”>“设备限制” > “连接”设置中启用始终可用的 VPN。

#### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>向无用户设备颁发 SCEP 证书 <!-- 1744554 -->
目前证书的颁发对象是用户。 通过此更新，SCEP 证书可以颁发给设备，包括无用户设备，例如网亭（“设备配置” > “配置文件” > “创建配置文件” >  适用于平台的“Windows 10 及更高版本”> 配置文件的“SCEP 证书”）。 其他更新包括：
- SCEP 配置文件中的“使用者”属性现在是自定义文本框，可以包含新的变量。 
- SCEP 配置文件中的“使用者可选名称(SAN)”属性现在是表格式，可以包含新的变量。 在表中，管理员可以添加属性并在自定义文本框中填写值。 SAN 将支持以下属性： 
  - DNS
  - 电子邮件地址
  - UPN

  可以在自定义值文本框中使用静态文本添加这些新变量。 例如，可以将 DNS 属性添加为 `DNS = {{AzureADDeviceId}}.domain.com`。

  > [!NOTE]
  > 在 SAN 的静态文本中无法使用大括号 ({ })、分号 (;) 和竖杠符号 (|)。 `Subject` 或 `Subject alternative name` 只接受大括号仅包含一个新设备证书变量的情况。 

新的设备证书变量：  

```
"{{AAD_Device_ID}}",
"{{Device_Serial}}",
"{{Device_IMEI}}",
"{{SerialNumber}}",
"{{IMEINumber}}",
"{{AzureADDeviceId}}",
"{{WiFiMacAddress}}",
"{{IMEI}}",
"{{DeviceName}}",
"{{FullyQualifiedDomainName}}",
"{{MEID}}",
```

> [!NOTE]
>  - `{{FullyQualifiedDomainName}}` 仅适用于 Windows 和已加入域的设备。 
>  -  在使用者或 SAN 中为设备证书指定设备属性（如 IMEI、序列号和完全限定的域名）时，请注意这些属性可能被有权访问设备的人员模仿。 

[创建 SCEP 证书配置文件](certificates-scep-configure.md#create-a-scep-certificate-profile)列出了创建 SCEP 配置的配置文件时的当前变量。 

适用于：Windows 10 及更高版本和 iOS，支持用于 Wi-fi

#### <a name="remotely-lock-uncompliant-devices----2064495---"></a>远程锁定不兼容的设备 <!-- 2064495 -->
如果设备不兼容，可以根据符合性策略创建一个可以远程锁定设备的操作。 在 Intune >“设备符合性”中，创建新的策略或选择现有策略 >“属性”。 选择“针对非符合性的操作” > “添加”，然后选择远程锁定设备。
在以下设备上受支持： 
- Android
- iOS
- macOS
- Windows 10 移动版 
- Windows Phone 8.1 及更高版本 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224---"></a>Azure 门户中的 Windows 10 和更高版本的展台配置文件改进 <!-- 2748224 -->
此更新包括对 Windows 10 网亭设备配置文件的以下改进（“设备配置” > “配置文件” > “创建配置文件” >  适用于平台的“Windows 10 及更高版本”> 配置文件类型的“网亭预览”）： 
- 目前，用户可以在同一设备上创建多个网亭配置文件。 利用此更新，Intune 将支持每台设备只有一个网亭配置文件。 如果你仍需要在单台设备上创建多个网亭配置文件，可以使用自定义 URI。
- 在“多应用网亭”配置文件中，可以在应用程序网格中对“开始菜单布局”选择应用程序磁贴大小和顺序。 如果需要更多自定义设置，可以继续上传 XML 文件。
- 网亭浏览器设置移入“网亭”设置。 目前，“网亭 Web 浏览器”设置在 Azure 门户中具有其自己的类别。
适用于：Windows 10 及更高版本




### <a name="device-enrollment"></a>设备注册

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>将 Autopilot 配置文件应用到尚未注册 Autopilot 的已注册 Win 10 设备 <!-- 1558983 -->
可以将 Autopilot 配置文件应用到尚未注册 Autopilot 的已注册 Win 10 设备。 在 Autopilot 配置文件中，选择“将所有目标设备转换为 Autopilot”选项，以使用 Autopilot 部署服务自动注册非 Autopilot 设备。 等待 48 小时来处理注册。 取消注册设备并重置后，Autopilot 将对其进行配置。

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564---"></a>创建多个注册状态页配置文件并将其分配给 Azure AD 组 <!-- 2526564 -->
现在可以[创建](windows-enrollment-status.md)多个注册状态页面配置文件并将其分配给 Azure AD 组。

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune---2748613--"></a>在 Intune 中从设备注册计划迁移到 Apple Business Manager <!--2748613-->
Apple Business Manager (ABM) 在 Intune 中工作，可以将你的帐户从设备注册计划 (DEP) 升级到 ABM。 Intune 中的过程是相同的。 若要将你的 Apple 帐户从 DEP 升级到 ABM，请转到 [ https://support.apple.com/HT208817]( https://support.apple.com/HT208817)。

### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page---2748656--"></a>“设备注册概述”页上的“警报”和“注册状态”选项卡 <!--2748656-->
警报和注册失败现在显示在“设备注册概述”页的单独选项卡上。

### <a name="device-management"></a>设备管理

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices----2451462----"></a>限制应用，并阻止对 Android 设备上公司资源的访问 <!-- 2451462  -->  
在“设备符合性” > “策略” > “创建策略” > “Android” > “系统安全”中，“设备安全”部分下有一个名为“受限制的应用”的新设置。 如果设备上安装了某些应用，“受限制的应用”设置将使用符合性策略来阻止对公司资源的访问。 除非从设备中删除受限制的应用，否则设备会一直被视为不符合要求。
适用于： 
- Android

<!-- ########################### -->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]
