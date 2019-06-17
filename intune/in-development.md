---
title: 开发过程中 - Microsoft Intune
titleSuffix: ''
description: 开发过程中的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: bc5ea7076e77e5071724168fab58fa78f59601c4
ms.sourcegitcommit: 7ceae61e036ccf8b33704751b0b39fee81944072
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744307"
---
# <a name="in-development-for-microsoft-intune---june-2019"></a>Microsoft Intune 开发过程中的功能 - 2019 年 6 月

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

<!-- ***********************************************-->
### <a name="app-management"></a>应用管理

#### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>设备用户可以查看他们已安装或尝试安装的所有托管应用 <!-- 2352913 -->
Company Portal for Windows 将列出用户设备上安装的所有（要求的和可用的）托管应用。 用户将能够查看已尝试和待处理的应用安装及其当前状态。 如果组织未提供所需或可用的应用，则用户将看到一条消息，说明尚未安装任何公司应用。 用户还可以按安装状态对其应用进行排序或筛选。

#### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956---"></a>用于 Android 工作配置文件的可用 Google Play 应用报告 <!-- 3041956 -->
对于 Android 工作配置文件设备上的可用应用安装，可以查看应用安装状态以及托管的 Google Play 应用的安装版本。 有关详细信息，请查看[如何监视应用保护策略](app-protection-policies-monitor.md)、[使用 Intune 管理 Android 工作配置文件设备](android-enterprise-overview.md)和[托管的 Google Play 应用类型](apps-add-android-for-work.md#managed-google-play-app-type)。

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data----3145939---"></a>配置允许哪种浏览器链接到组织数据 <!-- 3145939 -->
借助 Android 和 iOS 设备上的 Intune 应用保护策略 (APP)，可以将 Org web 链接转移到特定的浏览器（不仅限于 Intune Managed Browser 和 Microsoft Edge）。  有关 APP 的详细信息，请参阅[什么是应用保护策略？](app-protection-policy.md)。

#### <a name="installed-apps-page-on-the-company-portal-website-----4224326---"></a>公司门户网站上的已安装应用页  <!-- 4224326 -->
[公司门户网站](https://portal.manage.microsoft.com/)将添加一个新网页，该网页向用户显示已安装在他们设备上的所有应用。 此列表包括可用的应用和组织要求使用的应用。 在此页中，用户可以查看其设备上应用的安装和要求状态。 有关公司门户网站的详细信息，请参阅[使用 Intune 公司门户网站](/intune-user-help/using-the-intune-company-portal-website.md)和[如何配置 Microsoft Intune 公司门户应用](company-portal-app.md)。

#### <a name="call-graph-api-read-operations-from-an-application-without-user-credentials----4655885---"></a>在不使用用户凭据的情况下从应用程序调用 Graph API 读取操作 <!-- 4655885 -->
应用程序将能够在不使用用户凭据的情况下通过应用标识调用 Intune Graph API 读取操作。 要了解详细信息，请参阅[在没有用户的情况下访问](https://docs.microsoft.com/graph/auth-v2-service)。

<!-- ***********************************************-->
### <a name="device-configuration"></a>设备配置


#### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>支持适用于 iOS 的 IKEv2 VPN 配置文件 <!-- 1943438 -->
可以使用 IKEv2 协议为 iOS 本机 VPN 客户端创建 VPN 配置文件。 IKEv2 是以下位置中的新连接类型：  “设备配置” >   “配置文件” > “创建配置文件”   > 平台为“iOS”  >配置文件类型为“VPN”  >“设置”  。

这些 VPN 配置文件配置本机 VPN 客户端。 因此，没有 VPN 客户端应用安装或推送到托管设备。 此功能要求设备在 Intune （MDM 注册）中注册。

要查看当前可配置的 VPN 设置，请转到[在 iOS 设备上的 Microsoft Intune 中配置 VPN 设置](vpn-settings-ios.md)。

适用于：iOS

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices----20430240---"></a>在 macOS 设备上配置内核扩展的设置 <!-- 20430240 -->
在 macOS 设备上，可以创建设备配置文件（依次选择“设备配置” > “配置文件” > “创建配置文件”> 针对平台选择“macOS”）     。 未来的更新将包括一组新设置，可在设备上配置和使用内核扩展。

适用于：10.13.2 及更高版本

#### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>关键字搜索的基线支持  <!-- 3082036         -->
创建或编辑安全基线配置文件时，即将能够使用搜索功能来筛选控制台中显示的设置。    

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>在创建 Windows 10 设备配置配置文件时使用“适用性规则” <!-- 2549910 -->
创建 Windows 10 设备配置配置文件（“设备配置” > “配置文件” > “创建配置文件” > 适用于平台的“Windows 10”）     。 你将能够创建“适用性规则”，使配置文件仅应用于特定版本  。 例如，创建一个启用某些 BitLocker 设置的配置文件。 添加配置文件后，请使用适用性规则，使配置文件仅适用于运行 Windows 10 企业版的设备。

适用于： 
- Windows 10 及更高版本

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options----2697002----"></a>来自 Windows 10 设备的“仅 Store”设置的应用包括更多配置选项。 <!-- 2697002  -->

为 Windows 设备创建设备限制配置文件时，可以使用“仅来自 Store 的应用”设置  ，使用户仅从 Windows 应用商店安装应用（“设备配置”   > “配置文件”   > “创建配置文件”   > 平台为“Windows 10 和更高版本”  >配置文件类型为“设备限制”  ）。 在未来更新中，将扩展此设置以支持更多选项。 

要查看最新设置，请转到[使用 Intune 允许或限制功能的 Windows 10（和更高版本）设备设置](device-restrictions-windows-10.md#app-store)。

适用于：Windows 10 及更高版本

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group----4089955---"></a>将多个 Zebra 移动扩展设备配置文件部署到一台设备、同一用户组或同一设备组 <!-- 4089955 -->
在 Intune 中，可以在设备配置配置文件中使用 Zebra 移动扩展 (MX) 以自定义设置，或将未内置的设置添加到 Intune。 目前，可以将一个配置文件部署到一台设备。 在未来更新中，能够将多个配置文件部署到：

- 同一用户组
- 同一设备组
- 一台设备

[通过 Microsoft Intune 中的 Zebra 移动扩展来使用和管理 Zebra 设备](android-zebra-mx-overview.md)显示了如何在 Intune 中使用 MX。

适用于 Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow----4404075----"></a>iOS 设备上的一些展台设置是使用“阻止”（替代“允许”）设置的 <!-- 4404075  -->
在 iOS 设备上创建设备限制配置文件时（“设备配置”   > “配置文件”   > “创建配置文件”   > 平台为“iOS”  >配置文件类型为“设备限制”  >“展台”  ），可以设置“自动锁定”  、“响铃切换”  、“屏幕旋转”  、“屏幕睡眠按钮”  和“音量按钮”  。 

目前，这些设置通过“允许”（阻止此功能）或“未配置”（允许此功能）进行配置   。 在未来的更新中，值将会是“阻止”（阻止此功能）或“未配置”（允许此功能）   。

要查看最新设置，请转到[允许或限制功能的 iOS 设备设置](device-restrictions-ios.md)。 

适用于：iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices----4490704----"></a>在 iOS 设备上使用人脸 ID 进行密码身份验证 <!-- 4490704  -->
创建用于 iOS 设备的设备限制配置文件时，可将指纹用作密码。 在未来的更新中，指纹密码设置也将允许面部识别（“设备配置”   > “配置文件”   > “创建配置文件”   >  平台为“iOS”  > 配置文件类型为“设备限制”  >“密码”  ）。 因此，对以下设置进行了更改：

- “指纹解锁”现在更改为“Touch ID 和 Face ID 解锁”   。
- 指纹修改（仅限监管模式）现在更改为“Touch ID 和 Face ID 修改（仅限监管模式）”   。

Face ID 可在 iOS 11.0 和更高版本中使用。 要查看最新设置，请转到[使用 Intune 允许或限制功能的 iOS 设备设置](device-restrictions-ios.md#password)。

适用于：iOS

#### <a name="apps-feature-is-dependent-on-ratings-region-when-restricting-gaming-and-app-store-features-on-ios-devices----4593948----"></a>在 iOS 设备上限制游戏和应用商店功能时，应用功能取决于分级区域 <!-- 4593948  -->
在 iOS 设备上，可以允许或限制与游戏、应用商店和查看文档相关的功能（“设备配置”   > “配置文件”   > “创建配置文件”   >  平台为“iOS”  > 配置文件类型为“设备限制”  >“应用商店、文档查看、游戏”  ）。 此外还可以选择分级区域，例如美国。 在未来更新中，“应用”功能将更改为“分级区域”的子级，依赖于“分级区域”    。

要查看最新设置，请转到[使用 Intune 允许或限制功能的 iOS 设备设置](device-restrictions-ios.md#app-store-doc-viewing-gaming)。

适用于：iOS

#### <a name="administrative-templates-for-group-policy---------3510695---"></a>用于组策略的管理模板     <!--  3510695 -->
为提高云端设备安全性，我们将发布管理模板，让用户使用 Intune 为 Windows 电脑配置精选的组策略设置。  这些模板使用策略配置服务提供商 (CSP) 来提供 Office、Windows 和 OneDrive 中的多达 2500 个其他设置。

####  <a name="new-settings-for-the-windows-security-baseline-----3534649-4217151------------"></a>用于 Windows 安全基线的新设置  <!-- 3534649, 4217151          -->
我们将新设置添加到 Windows 安全基线。 第一个设置针对基于虚拟化的安全性，这需要安全启动。 第二个设置使你能够在屏幕锁定时管理 Windows 应用的语音激活。

#### <a name="security-baselines-will-be-generally-available------3785395---------"></a>安全基线将公开发布  <!--  3785395       -->
安全基线功能将很快结束预览状态，推出正式版。 

#### <a name="the-windows-security-baseline-template-will-be-generally-available-------3794072---------"></a>Windows 安全基线模板将公开发布   <!--  3794072       -->
Windows 安全基线模板将很快结束预览状态，推出正式版。 该模板的预览版将停用，新模板将推出。

<!-- ***********************************************-->
### <a name="device-management"></a>设备管理

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group----3173810---"></a>将范围标记分配给安全组中的所有托管设备 <!-- 3173810 -->
目前，可以将范围标记分配给设备，方法是转到各设备的“属性”页面并选择范围标记  。 在未来更新中，可以将范围标记分配给安全组，安全组中的所有设备也将与这些范围标记关联。 要执行此操作，请选择“Intune”   > “角色”   > “范围(标记)”   > “创建”   > “范围(标记)”  > 选择要将范围标记分配到的组。 这些组中的所有设备也将分配有范围标记。 使用此功能设置的范围标记将覆盖使用当前设备范围标记流设置的范围标记。 （在未来更新中，将范围标记分配给设备的当前流将设置为只读。）

#### <a name="see-the-security-patch-level-for-android-devices----4461911----"></a>查看 Android 设备的安全修补程序级别 <!-- 4461911  -->
你将能查看 Android 设备的安全修补程序级别。 要执行此操作，选择“Intune”   > “设备”   > “所有设备”  > 选择一个设备 >“监视器”   > “硬件”  。


<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。


