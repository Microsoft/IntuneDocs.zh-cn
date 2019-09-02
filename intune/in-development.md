---
title: 开发过程中 - Microsoft Intune
titleSuffix: ''
description: 开发过程中的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2b96fa9fac25f6de4180d3dcc9ee4022a2cc43fe
ms.sourcegitcommit: 7484ef8006f6b81d8976c328dd704512a31872ec
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2019
ms.locfileid: "70190247"
---
# <a name="in-development-for-microsoft-intune---september-2019"></a>开发过程中的 Microsoft Intune 功能 - 2019 年 9 月

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

<!-- Common categories:  
#### App management
#### Device configuration
#### Device enrollment
#### Device management
#### Intune apps
#### Monitor and troubleshoot
#### Role-based access control
#### Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>应用管理

### <a name="managed-google-play-private-lob-apps----1464182----"></a>托管 Google Play 专用 LOB 应用 <!-- 1464182  -->
Intune 允许 IT 管理员通过在 Intune 控制台中嵌入的 iframe 将私有 Android LOB 应用发布到托管 Google Play。  目前, IT 管理员需要将 LOB 应用程序直接发布到 Google Play 发布控制台, 这需要执行许多步骤, 并且非常耗时。  这项新功能可让你轻松地使用一组最少的步骤来发布 LOB 应用, 而无需离开 Intune 控制台。  使用托管 Google Play 的任何 Android 企业管理方案都可以利用此功能 (工作配置文件、专用、完全托管和非注册设备)。  在 Intune 中，选择“客户端应用”   > “应用”   > “添加”  。 然后, 从 "**应用类型**" 列表中选择 "**托管 Google Play** "。 有关托管 Google Play 应用的详细信息, 请参阅[将托管 Google Play 应用添加到带 Intune 的 Android 企业设备](apps-add-android-for-work.md)。

### <a name="company-portal-app-installation-status-messages----2514416----"></a>公司门户应用安装状态消息 <!-- 2514416  -->
公司门户应用会向最终用户显示其他应用安装状态消息。 以下条件适用于新的 Win32 依赖项功能:
- 应用安装失败。 不符合管理员定义的依赖关系。
- 应用已成功安装, 但需要重新启动。
- 应用正在安装, 但需要重新启动才能继续。

### <a name="managed-google-play-iframe-support----2871756----"></a>托管 Google Play iframe 支持 <!-- 2871756  -->
Intune 将通过托管的 Google Play iframe 为直接在 Intune 控制台中添加和管理 web 链接提供支持。  这使 IT 管理员可以提交 URL 和图标图形, 然后将这些链接部署到设备, 就像常规 Android 应用一样。 使用托管 Google Play 的任何 Android 企业管理方案都可以利用此功能 (工作配置文件、专用、完全托管和非注册设备)。  在 Intune 中，选择“客户端应用”   > “应用”   > “添加”  。 然后, 从 "**应用类型**" 列表中选择 "**托管 Google Play** "。 有关托管 Google Play 应用的详细信息, 请参阅[将托管 Google Play 应用添加到带 Intune 的 Android 企业设备](apps-add-android-for-work.md)。

### <a name="macos-support-for-vpp-apps----3173501----"></a>macOS 对 VPP 应用的支持 <!-- 3173501  -->
当 Apple VPP 令牌在 Intune 中同步时, 使用 Apple Business Manager 购买的 macOS 应用将显示在控制台中。 可以使用控制台为组分配、吊销和重新分配设备和基于用户的许可证。 Microsoft Intune 可帮助你通过以下方式管理为在公司购买的 VPP 应用:
- 从应用商店中报告许可证信息。
- 跟踪已使用的许可证数量。
- 帮助防止安装的应用副本数超过所拥有的数目。
有关 Intune 和 VPP 的系详细信息，请参阅[使用 Microsoft Intune 管理批量购买的应用和书籍](vpp-apps.md)。

### <a name="macos-support-for-web-apps----3174427----"></a>对 web 应用的 macOS 支持 <!-- 3174427  -->
你将能够安装 Web 应用, 该应用允许你使用 macOS 公司门户向坞添加 URL 的快捷方式。 最终用户可以从 macOS 公司门户中 web 应用的应用详细信息页访问**安装**操作。 有关**Web 链接**应用类型的详细信息, 请参阅[将应用添加到 Microsoft Intune](apps-add.md)。

#### <a name="assign-microsoft-edge-beta-for-macos----4678761----"></a>为 macOS 分配 Microsoft Edge beta <!-- 4678761  -->
你将能够将最新版本的 Microsoft Edge beta 添加到 Intune for macOS 设备。 在 Intune 中, 选择 "**客户端应用** > **应用** > " "**添加应用** > " "**Microsoft Edge-macOS**"。 然后, 将 Microsoft Edge beta 分配给目标组。 Microsoft 自动更新 (MAU) 将 Microsoft Edge 保持最新状态。 有关 Microsoft Edge 的详细信息, 请参阅[使用 Microsoft Intune 的 Microsoft Edge 管理 web 访问](manage-microsoft-edge.md)。

### <a name="read-and-write-graph-api-operations-for-intune-apps----5031704----"></a>针对 Intune 应用的读取和写入图形 API 操作 <!-- 5031704  -->
应用程序将能够使用没有用户凭据的应用程序标识调用 Intune 图形 API, 同时进行读写操作。 若要详细了解如何访问用于 Intune 的 Microsoft Graph API，请参阅[在 Microsoft Graph 中使用 Intune](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)。

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>为组织帐户配置应用通知内容 <!-- 2576686 -->
Android 和 iOS 设备上的 Intune 应用保护策略 (应用) 允许您控制组织帐户的应用通知内容。 此功能需要应用程序的支持, 可能无法用于所有启用应用的应用程序。 有关 APP 的详细信息，请参阅[什么是应用保护策略？](app-protection-policy.md)。

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>用于 Android 工作配置文件的可用 Google Play 应用报告 <!-- 3041956  -->
对于 Android 工作配置文件设备上的可用应用安装，可以查看应用安装状态以及托管的 Google Play 应用的安装版本。 有关详细信息，请查看[如何监视应用保护策略](app-protection-policies-monitor.md)、[使用 Intune 管理 Android 工作配置文件设备](android-enterprise-overview.md)和[托管的 Google Play 应用类型](apps-add-android-for-work.md#managed-google-play-app-type)。

<!-- ***********************************************-->
## <a name="device-configuration"></a>设备配置

### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type----4886161----"></a>适用于 iOS 和 macOS 设置的设备功能、设备限制和扩展配置文件按注册类型显示 <!-- 4886161  -->

在 Intune 中, 你将为 iOS 和 macOS 设备创建配置文件 (**设备配置** > **文件** > 为平台 > 设备功能**创建配置文件** > **iOS**或**macOS**  、**设备限制**或配置文件类型的**扩展**。 当前列出了这些配置文件中的可用设置。 

在将来的更新中, Intune 门户中的可用设置将按照它们适用的注册类型进行分类:

- iOS
  - 所有注册类型
  - 设备注册和自动化设备注册
  - 自动设备注册

- macOS
  - 所有注册类型
  - 设备注册
  - 用户已批准和自动设备注册
  - 自动设备注册

适用于：

- iOS
  - [设备功能](ios-device-features-settings.md)
  - [设备限制](device-restrictions-ios.md)

- macOS
  - [设备功能](macos-device-features-settings.md)
  - [设备限制](device-restrictions-macos.md)
  - [扩展](kernel-extensions-settings-macos.md)

### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode----4892835----"></a>在展台模式下运行的受监督 iOS 设备的新语音控制设置 <!-- 4892835  -->

在 Intune 中, 你可以创建策略以将受监督的 iOS 设备作为展台或专用设备运行 (**设备配置** > **文件** > 创建适用于平台的**配置文件** > **iOS** >  配置文件类型 > 展台的设备限制 **(仅限监督模式)** 。 

在将来的更新中, 将有一些新设置可以控制:

- **语音控制**: 在展台模式下启用设备上的语音控制。
- **修改语音控件**: 允许用户在展台模式下更改设备上的语音控制设置。

若要查看当前设置, 请访问[IOS 展台 (仅限监控模式) 设置](device-restrictions-ios.md#kiosk-supervised-only)。

适用于：

- iOS 13.0 及更高版本

### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices----4893175----"></a>使用 iOS 和 macOS 设备上的应用程序和网站的单一登录 <!-- 4893175  -->
在将来的更新中, 将为 iOS 和 macOS 设备提供一些新的单一登录设置 (**设备配置** > **文件** > 为**macOS** **创建配置** > 文件**ios**或用于配置文件类型的平台 >**设备功能**)。

使用这些设置来配置单一登录体验, 特别是对于使用 Kerberos 身份验证的应用和网站。 你可以在通用凭据单一登录应用程序扩展和 Apple 的内置 Kerberos 扩展之间进行选择。

若要查看可配置的当前设备功能, 请访问[iOS 设备功能](ios-device-features-settings.md)和[macOS 设备功能](macos-device-features-settings.md)。

适用于：

- iOS 13.0 及更高版本
- macOS 10.15 及更高版本

### <a name="associate-domains-to-apps-on-macos-1015-devices----4898079----"></a>将域关联到 macOS 10.15 + 设备上的应用 <!-- 4898079  -->
在 macOS 设备上, 可以配置不同的功能, 并使用策略将这些功能推送到设备 (**设备配置** > **配置文件** > **Create profile** > **macOS**用于配置文件类型的平台 >**设备功能**)。 在将来的更新中, 你将能够将域关联到你的应用。 此功能可帮助与应用相关的网站共享凭据, 并可与 Apple 的单一登录扩展、通用链接和密码自动填充配合使用。 

若要查看可配置的当前功能, 请访问[Intune 中的 macOS 设备功能设置](macos-device-features-settings.md)。

适用于：

- macOS 10.15 及更高版本

### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices----4928474----"></a>显示或隐藏 iOS 监视设备上的应用时, 请使用 iTunes 应用商店 URL 中的 "itunes" 和 "应用" <!-- 4928474  --> 
在 Intune 中, 你可以创建策略以显示或隐藏受监督的 iOS 设备上的应用 (**设备配置** > **文件** > 为平台 > 设备**创建配置文件** > **iOS**  配置文件类型 >**显示或隐藏应用的限制 (仅限监督模式)** 。 

可以输入 iTunes 应用商店 URL, 如`https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`。 在将来的更新中, 你将可以在 URL 中`apps`使用`itunes`和, 如:

- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

有关这些设置的详细信息, 请参阅[显示或隐藏应用 (仅限监督模式)](device-restrictions-ios.md#show-or-hide-apps-supervised-only)。

适用于：

- iOS

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>支持适用于 iOS 的 IKEv2 VPN 配置文件 <!-- 1943438 -->
可以使用 IKEv2 协议为 iOS 本机 VPN 客户端创建 VPN 配置文件。 IKEv2 是以下位置中的新连接类型：  “设备配置” >   “配置文件” > “创建配置文件”   > 平台为“iOS”  >配置文件类型为“VPN”  >“设置”  。

这些 VPN 配置文件配置本机 VPN 客户端。 因此，没有 VPN 客户端应用安装或推送到托管设备。 此功能要求设备在 Intune （MDM 注册）中注册。

要查看当前可配置的 VPN 设置，请转到[在 iOS 设备上的 Microsoft Intune 中配置 VPN 设置](vpn-settings-ios.md)。

适用于：iOS


<!-- ***********************************************-->
## <a name="device-enrollment"></a>设备注册

### <a name="new-tenants-will-default-away-from-android-device-administrator-management----4869790----"></a>新租户将默认离开 Android 设备管理员管理 <!-- 4869790  -->
Android 企业版已取代 android 的设备管理员功能。 因此, 建议改为使用 Android Enterprise 进行新注册。 在将来的更新中, 新租户需要在 Android 注册中完成以下先决条件步骤, 才能使用设备管理员管理: 中转到**Intune** > **设备注册** > **Android 注册**具有设备 > **管理权限的个人和公司拥有的设备** **使用设备管理员来管理设备。**  > 

现有租户在其环境中将不会发生任何更改。 

有关 Intune 中 Android 设备管理员的详细信息, 请参阅[android 设备管理员注册](https://docs.microsoft.com/intune/android-enroll-device-administrator)。

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>对于 iOS 设备, 自定义公司门户的 "注册过程隐私" 屏幕 <!-- 4394993  -->
使用 markdown, 你可以自定义公司门户的隐私屏幕, 最终用户可以在 iOS 注册过程中看到这些屏幕。 具体而言, 你将能够自定义你的组织无法在设备上看到或执行的操作的列表。

<!-- ***********************************************-->
## <a name="device-management"></a>设备管理

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>将软件更新部署到 macOS 设备 <!-- 3194876 -->
你将能够将软件更新部署到 macOS 设备组。 此功能包括关键、固件、配置文件和其他更新。 你将能够在下一次设备签入时发送更新, 或选择每周计划, 以在你设置的时间内或在你设置的时间内部署更新。 当你想要在标准工作时间之外或在你的支持人员完全配备设备时, 这会很有帮助。 你还将获得已部署更新的所有 macOS 设备的详细报告。 您可以查看每个设备的报表, 以查看特定更新的状态。

### <a name="send-custom-notifications-to-a-device----4928910----"></a>向设备发送自定义通知 <!-- 4928910  -->
你将能够向安装了公司门户或 Intune 应用的特定设备发送自定义通知。 为此, 请在 " **Intune** > **设备** > " "**所有设备**" > 选择一个设备 >**更多** > **发送自定义通知**。 

### <a name="updates-to-android-enterprise-fully-managed-features----3464667-5227935-4062195-4631425-4631440---"></a>对 Android 企业完全托管功能的更新 <!-- 3464667, 5227935, 4062195, 4631425, 4631440 -->

我们将为 Android 完全托管设备添加以下支持:

- 用于完全托管 Android 的 SCEP 证书将可用于作为设备所有者管理的设备上的证书身份验证。 工作配置文件设备上已支持 SCEP 证书。  对于设备所有者的 SCEP 证书, 你将能够: <!-- 5227935 -->
    - 在 Android 企业的 "DO" 部分创建 SCEP 配置文件
    - 将 SCEP 证书链接到执行 Wi-fi 配置文件进行身份验证
    - 将 SCEP 证书链接到用于执行身份验证的 VPN 配置文件
    - 将 SCEP 证书链接到用于执行身份验证的电子邮件配置文件 (通过 AppConfig)
- Android 企业设备将支持系统应用。 在 Intune 中, 你将通过选择 "**客户端应用** > **应用** > " "**添加**" 来添加 Android 企业系统应用。 在 "**应用类型**" 列表中, 选择 " **Android 企业系统应用**"。 有关向 Intune 添加应用的详细信息，请参阅[向 Microsoft Intune 添加应用](apps-add.md)。 <!-- 4062195 -->
- 在**设备符合性** > **Android 企业** > **设备所有者**中, 你将能够创建设置 Google SafetyNet 证明级别的符合性策略。   <!-- 4631425 -->
- 在 Android 企业完全托管的设备上, 将支持移动威胁防御提供程序。 在 "**设备符合性** > **Android 企业** > **设备所有者**" 中, 可以选择可接受的威胁级别。 <!-- 4631440 --> [使用 Intune 将设备标记为符合或不符合的 Android Enterprise 设置](compliance-policy-create-android-for-work.md#device-owner)会列出当前设置。


适用于： 
- Android Enterprise 完全托管设备

<!-- ***********************************************-->
## <a name="monitor-and-troubleshoot"></a>监视和故障排除

### <a name="updated-support-experience-------5012398------"></a>更新的支持体验   <!--  5012398    -->
作为持续改进的一部分, 我们将更新 Intune 的控制台中支持体验。  我们将改进有关常见问题的控制台中搜索和反馈, 并简化工作流以联系支持人员。     

<!-- ***********************************************-->
## <a name="security"></a>安全

### <a name="tamper-protection-for-windows-defender-antivirus-----4705448---------"></a>Windows Defender 防病毒的篡改保护  <!-- 4705448       -->
我们会将*防篡改保护*添加到 Intune 可管理的 Windows Defender 防病毒设置。 你将能够使用适用于 Windows 10 endpoint protection 的设备配置文件来打开或关闭篡改保护。  有关防篡改保护的详细信息, 请参阅 Windows 文档中的[防止安全设置更改并篡改防篡改](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection)。 


<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。




