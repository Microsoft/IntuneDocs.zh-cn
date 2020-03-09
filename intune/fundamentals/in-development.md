---
title: 开发过程中 - Microsoft Intune
titleSuffix: ''
description: 开发过程中的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/03/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e099537bce6327e9a8991bc42f406e4abd3dfd2e
ms.sourcegitcommit: 6608dc70d01376e0cd90aa620a2fe01337f6a2f1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2020
ms.locfileid: "78260225"
---
# <a name="in-development-for-microsoft-intune---march-2020"></a>Microsoft Intune 开发过程中的功能 - 2020 年 3 月

为了辅助就绪性和计划，此页面列出了正在开发但尚未发布的 Intune UI 更新和功能。 除本页上的信息外，另请注意： 

- 如果我们预计你需要在更改之前采取措施，我们将在 Office 消息中心发布补充性的文章。
- 当某个功能进入生产（无论是提供预览还是正式发布），其功能描述都将从本页移动到[新增功能](whats-new.md)。
- 此页和[新增功能页](whats-new.md)会定期更新。 返回查看其他更新。
- 有关策略性可交付内容和时间线，请参阅 [Microsoft 365 路线图](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)。

> [!NOTE]
> 此页反映了我们目前希望在未来版本中提供的 Intune 功能。 日期和各项功能可能会更改。 本页未介绍我们正在开发的全部功能。

**RSS 源**：通过将以下 URL 复制并粘贴到源阅读器中，可以在页面更新时收到通知：`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>应用管理

### <a name="retarget-web-clips-to-microsoft-edge-on-iosipados-devices---5455276---"></a>在 iOS/iPadOS 设备上将 Web 剪辑重定向到 Microsoft Edge<!-- 5455276 -->
Web 剪辑在 iOS/iPadOS 设备上充当已固定的 Web 应用，需要更新。 如果需要在受保护的浏览器中打开新部署的 Web 剪辑，将在 Microsoft Edge（而不是在 Intune Managed Browser 中）打开它们。 必须重定向现有 Web 剪辑，以确保它们在 Microsoft Edge 而不是 Managed Browser 中打开。

### <a name="macos-and-ios-company-portal-updates---5779439-5780234----"></a>macOS 和 iOS 公司门户更新<!-- 5779439, 5780234  -->
将更新 macOS 和 iOS 公司门户的“配置文件”窗格，使其包含注销按钮。 此外，此更新还包括对 macOS 公司门户中“配置文件”窗格的 UI 改进。 有关公司门户的详细信息，请参阅[如何配置 Microsoft Intune 公司门户应用](~/apps/company-portal-app.md)。

### <a name="updates-to-branding-and-customization-pane---5236032---"></a>对“品牌和自定义”窗格的更新<!-- 5236032 -->
我们即将更新目前名为“品牌和自定义”的 Intune 窗格，改进内容包括：

- 将该窗格重命名为“自定义”  。
- 改进设置的组织和设计。
- 改进设置文本和工具提示。

若要在 Intune 中查找这些设置，请导航到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)并选择“租户管理”   > “自定义”  。 有关现有自定义的信息，请参阅[如何配置 Microsoft Intune 公司门户应用](~/apps/company-portal-app.md)。

### <a name="configure-the-ios-microsoft-azure-ad-sso-app-extension---567534----"></a>配置 iOS Microsoft Azure AD SSO 应用扩展<!-- 567534  -->
Microsoft Azure AD 团队正在开发重定向单一登录 (SSO) 应用扩展，让 iOS 和 iPadOS 13.0 以上的用户能够通过一次登录无缝获取对 Microsoft 应用和网站的访问权限。 AAD SSO 应用扩展发布后，使用管理控制台中的“设备功能”   >   “单一登录应用扩展”配置文件，通过寥寥数次单击即可配置 SSO 扩展。 

有关 iOS SSO 应用扩展或如何配置设备功能的详细信息，请参阅[单一登录应用扩展](~/configuration/device-features-configure.md#single-sign-on-app-extension)。

### <a name="company-portal-for-ios-to-support-landscape-mode--6048329----"></a>适用于 iOS 的公司门户将支持横向模式<!--6048329  -->
用户将能够使用自己选择的的屏幕方向注册设备、查找应用并获得 IT 支持。 应用会自动检测并调整屏幕以适应纵向或横向模式，除非你将屏幕锁定为纵向模式。 

### <a name="configure-if-enrollment-is-available-in-company-portal-for-android-and-ios---4260128-idready-idstaged---"></a>配置可否在适用于 Android 和 iOS 的公司门户中注册<!-- 4260128 idready idstaged -->
将提供一项新设置，可以通过它配置 Android 和 iOS 设备上的公司门户中是在有提示、无提示的情况下允许用户注册设备，还是不允许注册。 若要在 Intune 中查找这些设置，请导航到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)并选择“租户管理”   > “自定义”   >   “编辑” >   “设备注册”。 有关现有公司门户自定义的详细信息，请参阅[如何配置 Microsoft Intune 公司门户应用](~/apps/company-portal-app.md)。

### <a name="improved-sign-in-experience-in-company-portal-for-android---6103997----"></a>改进了适用于 Android 的公司门户中的登录体验<!-- 6103997  -->
我们即将更新适用于 Android 的公司门户应用中多个登录屏幕的布局，让用户体验更现代化、更简洁。

<!-- ***********************************************-->
## <a name="device-configuration"></a>设备配置

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>macOS 设备的有线网络设备配置文件<!-- 3508686  -->
可使用新的 macOS 设备配置文件来配置有线网络（“设备配置” > “配置文件” > “创建配置文件” > 选择“macOS”作为平台 > 选择“有线网络”作为配置文件类型      ）。 使用此功能创建 802.1x 配置文件来管理有线网络，并将这些有线网络部署到 macOS 设备。

适用于：
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-iosipados-devices----1947932----"></a>具有 IKEv2 VPN 连接的 VPN 配置文件可将“始终可用”用于 iOS/iPadOS 设备 <!-- 1947932  -->
在 iOS/iPadOS 设备上，可创建使用 IKEv2 连接的 VPN 配置文件（“设备配置” > “配置文件” > 创建配置文件 >  选择“iOS/iPadOS”作为平台 > 选择“VPN”作为配置文件类型      ）。 在未来的更新中，可为 IKEv2 配置“始终可用”。 配置后，IKEv2 VPN 配置文件会自动连接并保持连接（或快速重新连接）到 VPN。 即使切换网络或重启设备，它仍会保持连接。

在 iOS/iPadOS 上，始终可用 VPN 仅限于 IKEv2 配置文件。

要查看当前可配置的 IKEv2 设置，请转到[在 iOS/iPadOS 设备上的 Microsoft Intune 中添加 VPN 设置](../configuration/vpn-settings-ios.md#ikev2-settings)。

适用于：
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-iosipados-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984----"></a>改善了在 iOS/iPadOS 和 macOS 设备上创建配置文件时的用户界面体验<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984  -->
为 iOS/iPadOS 或 macOS 设备创建配置文件时，将更新“终结点管理”管理中心中的体验。 此更改会影响以下设备配置文件（“设备” > “配置文件” > “创建配置文件” >  选择“iOS”或“macOS”作为平台      ）：

- 自定义：iOS/iPadOS、macOS
- 设备功能：iOS/iPadOS、macOS
- 设备限制：iOS/iPadOS、macOS
- 终结点保护：macOS
- 扩展：macOS
- 首选项文件：macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-----"></a>改善了在 Android 企业版设备上创建 OEMConfig 配置文件时的用户界面体验<!-- 5568645   -->
创建或编辑适用于 Android 企业版设备的 OEMConfig 配置文件时，将更新“终结点管理”管理中心中的体验。 更新的体验将提供已配置设置的摘要的概览。 此更改会影响 OEMConfig 设备配置文件（“设备” > “配置文件” > “创建配置文件” >  选择“Android 企业版”作为平台 > 选择“OEMConfig”作为配置文件类型      ）。

此功能适用于：
- Android Enterprise 

### <a name="enterprise-app-trust-settings-modification-setting-will-be-removed-from-iosipados-device-restriction-profiles---6225131----"></a>将从 iOS/iPadOS 设备限制配置文件中删除“修改企业应用信任设置”设置<!-- 6225131  -->
在 iOS/iPadOS 设备上，创建设备限制配置文件（“设备”   > “配置文件”   > “创建配置文件”   > “iOS/iPadOS”  > 选择“设备限制”作为配置文件类型  ）。 Apple 将删除“修改企业应用信任设置”设置  ，因此 Intune 中也会删除它。 如果当前在配置文件中使用此设置，则此更新不会产生任何影响，此设置将保留在配置文件中，直到你创建新的配置文件。 也将从 Intune 中的任何报表中删除此设置。

适用于：
- iOS/iPadOS

要查看可以限制的设置，请转到[允许或限制功能的 iOS 和 iPadOS 设备设置](../configuration/device-restrictions-ios.md)。

### <a name="device-configuration-profile-settings-and-values-will-be-updated-for-windows-platforms---4091122---"></a>将为 Windows 平台更新设备配置文件设置和值<!-- 4091122 -->
为 Windows 平台创建设备配置文件时（“设备”   > “配置文件”   > “创建配置文件”  > 任意“Windows”  平台选项），某些设置及其值与 CSP 不同，可能会令人不解。 将更新这些设置名称及其值，为清晰地反应其功能。

适用于：

- Windows 10 及更高版本的设备配置文件
- Windows Holographic for Business 设备配置文件
- Windows 8.1 设备配置文件
- Windows Phone 8.1 设备配置文件

### <a name="improved-user-interface-experience-when-creating-device-restrictions-profiles-on-android-and-android-enterprise-devices---5841361---"></a>改进了在 Android 和 Android Enterprise 设备上创建设备限制配置文件时的用户界面体验<!-- 5841361 -->
将改进在“终结点管理”管理中心为 Android 或 Android Enterprise 设备创建配置文件时的体验。 此更改会影响以下设备配置文件（“设备”   >   “配置文件” >   “创建配置文件” >    选择“Android 设备管理员”或“Android Enterprise”平台）：

- 设备限制：Android 设备管理员
- 设备限制：Android Enterprise 设备所有者
- 设备限制：Android Enterprise 工作配置文件

有关可配置设备限制的详细信息，请参阅 [Android 设备管理员](../configuration/device-restrictions-android.md)和 [Android Enterprise ](../configuration/device-restrictions-android-for-work.md)。

### <a name="delete-bundles-and-bundle-arrays-in-oemconfig-device-configuration-profiles-on-android-enterprise-devices---5550355----"></a>在 Android Enterprise 设备上删除 OEMConfig 设备配置文件中的捆绑包和捆绑包系列<!-- 5550355  -->
在 Android Enterprise 设备上，可以创建和更新 OEMConfig 配置文件。 用户可以使用 Intune 中的“配置设计器”  删除捆绑包和捆绑包系列。

若要详细了解 OEMConfig 配置文件，请参阅[通过 Microsoft Intune 中的 OEMConfig 使用和管理 Android Enterprise 设备](../configuration/android-oem-configuration-overview.md)。

此功能适用于：
- Android Enterprise

### <a name="support-for-wpa-and-wpa2-in-ios-enterprise-wi-fi-profiles--6215273-----"></a>iOS 企业 Wi-Fi 配置文件中对 WPA 和 WPA2 的支持<!--6215273   -->
我们将向  [适用于 iOS 的 企业 Wi-Fi 配置文件](../configuration/wi-fi-settings-ios.md)添加“安全类型”字段（转到“设备”   > “配置文件”   > “创建配置文件”，选择“iOS/iPadOS”      作为“平台”，然后选择“Wi-Fi”作为“配置文件”）。 这与适用于 iOS 的基本 Wi-Fi 配置文件的选项类似。 在此更改后，你可以创建新的配置文件，在其中指定“WPA-企业”或“WPA/WPA2-企业”安全类型，并指定“EAP 类型”选项。   

### <a name="new-user-experience-for-certificate-email-vpn-and-wi-fi-profiles---5615208-----"></a>证书、电子邮件、VPN 和 Wi-Fi 配置文件的新用户体验<!-- 5615208   -->
我们即将更新在“终结点管理”管理中心创建和修改以下配置文件类型的[用户体验](../configuration/device-profile-create.md)（“设备”   >   “配置文件” >   “创建配置文件”）。 新体验将显示与以前相同的设置，但使用类似向导的体验，减少了需要进行的水平滚动。 新体验推出后，无需修改现有配置。
- 派生凭据
- 电子邮件
- PKCS 证书
- PKCS 导入的证书
- SCEP 证书
- 受信任的证书
- VPN
- Wi-Fi

（转到“设备”   >   “配置文件” >    “创建配置文件”，然后选择前面的任何配置文件作为“配置文件类型”。）

### <a name="configure-the-microsoft-defender-atp-app-for-macos-----5520115----"></a>配置适用于 macOS 的 Microsoft Defender ATP 应用  <!-- 5520115  -->
很快就可以在 Endpoint Protection 设备配置文件中为运行 macOS 的设备配置 Microsoft Defender ATP 应用的[设置](../protect/endpoint-protection-macos.md)了（转到“设备”   >   “配置文件” >       “创建配置文件”，选择“macOS”作为“平台”，然后选择“Endpoint Protection”作为“配置文件类型”）。 macOS 设备配置将提供 8 项设置。 

macOS 10.13 (High Sierra) 及更高版本支持 Defender ATP，必须在应用这些设置之后才能将 [Microsoft Defender ATP](../apps/apps-advanced-threat-protection-macos.md) 应用部署到设备。  应在部署应用之前将这些设置下发到设备。 不支持 macOS 的 Beta 版本。

### <a name="new-filevault-setting-for-macos-endpoint-protection-device-configuration-policy---5459801-----"></a>macOS Endpoint Protection 设备配置策略中新增 FileVault 设置<!-- 5459801   -->
我们将向 [macOS Endpoint Protection](../protect/endpoint-protection-macos.md) 模板中的 FileVault 类别添加新设置：隐藏恢复密钥。 （转到“设备”   >   “配置文件” >       “创建配置文件”，选择“macOS”作为“平台”，然后选择“Endpoint Protection”作为“配置文件类型”）。 此设置将在 FileVault 2 加密过程中向最终用户隐藏个人密钥。 设备用户可随时从 iOS 公司门户应用或公司门户网站查看其加密 macOS 设备的个人恢复密钥。 若要查看个人恢复密钥，用户可以转到设备详细信息，然后单击“获取恢复密钥”  。

此设置在以前创建的策略中不可用。 需要重新创建 FileVault 策略以配置此设置，才能利用它。 

###  <a name="ui-update-when-configuring-compliance-policy----3961639----"></a>配置合规性策略时的 UI 更新 <!-- 3961639  -->
我们将更新在 Microsoft 终结点管理器中配置合规性策略时的 UI（“设备”   >   “合规性策略” >   “策略” >   “创建策略”）。 你将看到新的用户体验，它提供与以前使用过的相同的设置和详细信息。 新体验将遵循类似向导的过程来创建合规性策略，并包含用于为策略添加“分配”的页面，然后是用于在创建策略前检查配置的“摘要”页面。   

### <a name="configure-delivery-optimization-agent-when-downloading-win32-app-content---5410945----"></a>下载 Win32 应用内容时配置传递优化代理<!-- 5410945  -->
你将能够配置传递优化代理以，使其基于分配在后台或前台模式下下载 Win32 应用内容。 对于现有的 Win32 应用，将继续在后台模式下下载内容。 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“设备”   > “配置文件”   > “创建配置文件”  。 选择“Windows 10 及更高版本”作为“平台”。   在“配置文件类型”下，选择“传递优化”。   有关传递优化的详细信息，请参阅 [Win32 应用管理 - 传递优化](~/apps/apps-win32-app-management.md#delivery-optimization)。


<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
## <a name="device-management"></a>设备管理

### <a name="change-primary-user-for-windows-devices----3794742---"></a>更改 Windows 设备的主要用户 <!-- 3794742 -->
你能够更改 Windows 混合设备和 Azure AD 联接设备的主要用户。 为此，请转到“Intune”   > “设备”   > “所有设备”  > 选择设备 >“属性”   > “主要用户”  。 

### <a name="new-android-report-on-android-devices-overview-page---5435435---"></a>“Android 设备概述”页面上新增 Android 报告<!-- 5435435 -->
我们将向“Android 设备概述”页面中的“Microsoft 终结点管理器”管理控制台添加报告，显示每个设备管理解决方案中已注册的 Android 设备数。 此图表（像 Azure 控制台中已经存在的相同图表一样）显示工作配置文件、完全托管、专用和设备管理员注册的设备计数。 若要查看报告，请选择“设备”   >   “Android” >   “概述”。

### <a name="powershell-scripts-support-for-byod-devices---1862833----"></a>对 BYOD 设备的 PowerShell 脚本支持<!-- 1862833  -->
PowerShell 脚本将支持 Intune 中已注册到 Azure AD 的设备。 有关 PowerShell 的详细信息，请参阅[在 Intune 中的 Windows 10 设备上使用 PowerShell 脚本](~/apps/intune-management-extension.md)。 此功能不支持运行 Windows 10 家庭版的设备。

### <a name="additional-data-warehouse-device-inventory-properties---6125732----"></a>额外的数据仓库设备清单属性<!-- 6125732  -->
将使用 Intune 数据仓库提供额外的设备清单属性。 将通过[设备](~/developer/intune-data-warehouse-collections.md#devices)收集公开以下属性：
- 存储容量 
- 内存容量
- Office 365 版本
- 设备型号

有关数据仓库的详细信息，请参阅 [Microsoft Intune 数据仓库 API](~/developer/reports-nav-intune-data-warehouse.md)。

### <a name="guide-users-from-android-device-administrator-management-to-work-profile-management--5857738--"></a>指导用户从 Android 设备管理员管理转到工作配置文件管理<!--5857738-->
我们将发布 Android 设备管理员平台的新合规性性设置。 通过此设置，可以将不通过设备管理员管理的设备设为不合规。

在这些不合规的设备上，用户将在“更新设备设置”页上看到“转到新设备管理设置”消息。   如果用户点击“解决”按钮，将引导其完成以下操作： 

1. 从设备管理员管理取消注册
2. 在工作配置文件管理中注册
3. 解决合规性问题 
 
Google 将在新的 Android 版本中减少设备管理员支持，以便通过 Android Enterprise 实现更现代化、更丰富、更安全的设备管理。  Intune 将只能在 2020 年第二季度之前为运行 Android 10 及更高版本的设备管理员管理的 Android 设备提供完全支持。 在此之后，无法再对运行 Android 10 或更高版本的设备管理员管理的设备进行全面管理（Samsung 设备除外）。 特别是，受影响的设备将不会收到新的密码要求。 有关详细信息，请参阅此[通知](#decreasing-support-for-android-device-administrator)。

### <a name="retire-noncompliant-devices---1827291---"></a>停用不合规的设备<!-- 1827291 -->
我们将添加新的可选合规性操作，用于停用不合规的设备（转到“设备”   >   “合规性策略” >   “策略” >     “创建策略”，然后在“对于不合规项的操作”页面上查看可用的“操作”）。  如果停用不符合要求的设备，则会从中删除所有公司数据，并且还会将设备从 Intune 管理中删除。 当达到配置的天数值时，此操作将运行。 最小值为 30 天。  需要明确的 IT 管理员批准，才能使用“停用不合规的设备”  部分（管理员可在其中停用所有符合条件的设备）停用设备。

### <a name="new-information-in-device-details---5604099---"></a>设备详细信息中的新信息<!-- 5604099 -->
以下信息将显示在设备的“概述”  页上：
- 存储容量（设备上的物理存储量）
- 内存容量（设备上的物理内存量）

### <a name="script-support-for-macos-devices---4280361----"></a>对 macOS 设备的脚本支持<!-- 4280361  -->
你将能够向 macOS 设备添加和部署脚本。 此支持扩展了你配置 macOS 设备的能力，让你不再限于使用 macOS 设备上的本机 MDM 功能进行配置。 

<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
## <a name="monitor-and-troubleshoot"></a>监视和故障排除

### <a name="help-and-support-workflow-update-to-support-additional-services---5654170---"></a>帮助和支持工作流更新以支持其他服务<!-- 5654170 -->
我们将更新“Microsoft 终结点管理器”管理中心的“帮助和支持”页面，让你将能够选择自己使用的管理类型，以便提供更好的特殊支持（“故障排除 + 支持”   >    “帮助和支持”）。 此次更改后，你可以从以下管理类型中进行选择：
- Configuration Manager（包括桌面分析）
- Intune
- 共同管理

<!-- ***********************************************-->
<!--
## Role-based access control
-->

<!-- ***********************************************-->
## <a name="security"></a>安全

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Android COBO 设备上的派生凭据支持<!--4839592-->
你将能够在 Android 企业版完全托管设备上使用派生凭据。 将添加有关为 Entrust Datacard、Intercede 和 DISA Purebred 检索派生凭据的支持。 你将能够使用派生凭据进行应用身份验证、Wi-Fi、VPN 或 S/MIME 签名，并/或通过支持该凭据的应用进行加密。

### <a name="use-antivirus-policy-to-manage-settings-for-microsoft-defender-antivirus-and-the-windows-security-experience--6131401---"></a>使用防病毒策略管理 Microsoft Defender 防病毒和 Windows 安全体验的设置<!--6131401 -->
在“终结点安全”  节点中，你能够配置防病毒设置  。 配置防病毒策略时，需通过两种配置文件类型来定义 Windows 10 设备的设置：

- Microsoft Defender 防病毒：管理云保护、防病毒排除项、修正、扫描选项等设置。
- Windows 安全体验：管理用户在其设备上体验 Windows 安全设置的方式。 你可配置最终用户可在 Microsoft Defender 安全中心查看的内容以及他们收到的通知。

### <a name="users-personal-encrypted-recovery-key---6273943---"></a>用户的个人加密恢复密钥<!-- 6273943 -->
这将提供新的 Intune 功能，使用户能够通过 Android 公司门户应用程序或 Android Intune 应用程序检索其个人加密 FileVault 恢复密钥。  公司门户应用程序和 Intune 应用程序中都会提供一个链接，该链接将打开 Chrome 浏览器并转到 Web 公司门户，用户可以在其中查看访问其 Mac 设备所需的 FileVault 恢复密钥。  有关加密的详细信息，请参阅 [使用 Intune 设备加密](~/protect/encrypt-devices.md)。

### <a name="privacy-preferences-settings-for-macos-devices---2934232---"></a>macOS 设备的隐私首选项设置<!-- 2934232 --> 
随着 macOS Catalina 10.15 的发布，Apple 添加了新的安全和隐私增强功能。 默认情况下，应用程序和进程只有取得用户许可才能访问特定数据。 如果用户不提供许可，则应用程序和进程可能无法正常工作。 Intune 即将添加对以下设置的支持：对于运行 macOS 10.14 及更高版本的设备，允许 IT 管理员代表最终用户授予或不授予数据访问许可。 这些设置将确保应用程序和进行继续正常工作，并减少向最终用户显示的提示。 

### <a name="updated-ui-text-and-labels-for-windows-10-endpoint-protection-profile-settings---5983747---"></a>更新了 Windows 10 Endpoint Protection 配置文件设置的 UI 文本和标签<!-- 5983747 -->
我们将更新以 Windows 10 设备配置文件的形式配置的各项设置的文本，让你能更轻松地了解设置的用途和效果。 

我们将更新的设置包括以下 Windows 10 设备配置文件： 
- [设备限制](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus) > Microsoft Defender 防病毒  
- [Endpoint Protection](../protect/endpoint-protection-windows-10.md) > Microsoft Defender 防病毒

不会更改 Intune 支持的设置。 这只是对“Microsoft 终结点管理”管理中心 UI 文本的更新。 


<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。



