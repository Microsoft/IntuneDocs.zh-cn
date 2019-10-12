---
title: 开发过程中 - Microsoft Intune
titleSuffix: ''
description: 开发过程中的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0e7c4e5ed45455dda941fb0c61c989c12c57135d
ms.sourcegitcommit: 29b1113dc04534c4c87c33c773c5a0e24266e042
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71999326"
---
# <a name="in-development-for-microsoft-intune---october-2019"></a>开发过程中的 Microsoft Intune 功能 - 2019 年 10 月

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

### <a name="additional-app-configuration-variable-available----4969237----"></a>其他可用的应用配置变量 <!-- 4969237  -->
创建应用配置策略时，可以在配置设置中包含 `AAD Device ID` 配置变量。 在 Intune 中，选择“客户端应用”   > “应用配置策略”   > “添加”  。 输入配置策略详细信息，然后选择 "**配置设置**"，查看 "**配置设置**" 边栏选项卡。

### <a name="dark-mode-for-ios-company-portal----4911422----"></a>适用于 iOS 的深色模式公司门户 <!-- 4911422  -->
为 iOS 公司门户规划了深色模式。 下载公司应用、管理你的设备，并在你选择的配色方案中获得支持。 有关 iOS 公司门户的详细信息，请参阅[如何配置 Microsoft Intune 公司门户应用](../apps/company-portal-app.md)。

### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-devices----4760025----"></a>禁止在 Android 企业设备上安装未知源的应用 <!-- 4760025  -->
对于 Android 企业工作配置文件设备，最终用户永远不能将来自未知源的应用安装到工作配置文件中。 你还可以选择将此限制扩展到个人配置文件。 如果启用此限制，则还会阻止 Android 企业工作配置文件设备上的最终用户将来自未知源的应用程序旁加载到其设备的个人端。 

### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui----4102027-4102029----"></a>应用保护 UI 和 iOS 应用预配 UI 更新 <!-- 4102027, 4102029  -->
将更新用于创建和编辑 Intune 中的应用保护策略和 iOS 应用预配配置文件的 UI。 UI 更改包括：
- 使用在一个边栏选项卡中压缩的向导样式格式简化了体验。 
- 用于包含分配的创建流的更新。
- 在创建新策略或编辑属性时，在查看属性时设置的所有项的汇总页。 此外，在编辑属性时，摘要将仅显示正在编辑的属性类别中的项目列表。

### <a name="create-groups-of-management-objects-called-policy-sets----3762880----"></a>创建称为策略集的管理对象组 <!-- 3762880  -->
策略集允许你创建对现有管理实体的引用的绑定，这些实体需要标识、定位，并作为单个概念单元监视。 策略集不会替换现有概念或对象。 管理员可以继续按原样分配各个对象。 策略集引用单个对象。 因此，对这些单独的对象所做的任何更改将反映在策略集中。  在 Intune 中，你将选择  > **创建**的**策略集**来创建新的策略集。 

### <a name="win32-apps-on-windows-10-s-mode-devices----3747604----"></a>Windows 10 S S 模式设备上的 Win32 应用 <!-- 3747604  --> 
你将能够在 Windows 10 S 模式托管的设备上安装和运行 Win32 应用。 你将能够使用 Windows Defender 应用程序控制（WDAC） PowerShell 工具为 S 模式创建一个或多个补充策略。 用 Device Guard 签名门户为补充策略签名，然后通过 Intune 上传和分发策略。 在 Intune 中，你将通过选择 "**客户端应用**"  > **个 Windows 10 S 补充策略**来找到此功能。 

### <a name="set-app-availability-based-on-a-date-and-time----3510685----"></a>基于日期和时间设置应用可用性 <!-- 3510685  -->
作为管理员，你可以为所需的应用配置开始时间和截止时间。 开始时，Intune 管理扩展将启动应用内容下载并将其缓存。 应用将在截止时间安装。 对于可用应用，开始时间将指示应用在公司门户中的可见性。 在 Intune 中，选择“客户端应用” > “应用”   。 然后从列表中选择特定的应用，或选择 "**添加**" 以添加新的应用。 从 "应用" 边栏选项卡中，选择 "**分配**"  > **添加组**"。 将 "**分配类型**" 设置为 "**必需**"，然后选择 "**包含组**"。 选中 "**使所有用户都需要此应用程序** **是"** ，并选择 "**编辑**" 以修改**最终用户体验**选项。 在 "**最终用户体验**" 边栏选项卡中，根据需要设置**软件可用时间**。 有关添加应用的详细信息，请参阅[向 Microsoft Intune 添加应用](../apps/apps-add.md)。

### <a name="require-win32-apps-to-restart----3136567----"></a>需要 Win32 应用重启 <!-- 3136567  -->
你将能够要求在安装成功后必须重启 Win32 应用程序。 此外，还可以选择在必须重新启动之前的时间量（宽限期）。

### <a name="company-portal-app-on-windows----1808082----"></a>在 Windows 上公司门户应用 <!-- 1808082  -->
Windows 设备上的公司门户应用将更新为向用户显示 toast 通知，即使应用程序已关闭也是如此。 仅当安装状态为 "已完成" 或 "失败" 时，更新才会显示可用应用的通知。 公司门户应用将不会显示所需应用程序的通知。

### <a name="company-portal-app-installation-status-messages----2514416----"></a>公司门户应用安装状态消息 <!-- 2514416  -->
公司门户应用会向最终用户显示其他应用安装状态消息。 以下条件适用于新的 Win32 依赖项功能：
- 应用安装失败。 不符合管理员定义的依赖关系。
- 应用已成功安装，但需要重新启动。
- 应用正在安装，但需要重新启动才能继续。

#### <a name="assign-microsoft-edge-beta-for-macos----4678761----"></a>为 macOS 分配 Microsoft Edge beta <!-- 4678761  -->
你将能够将最新版本的 Microsoft Edge beta 添加到 Intune for macOS 设备。 在 Intune 中，选择 "**客户端应用**"  >  个**应用**， >  "**添加应用** > **Microsoft Edge-macOS**"。 然后，将 Microsoft Edge beta 分配给目标组。 Microsoft 自动更新（MAU）将 Microsoft Edge 保持最新状态。 有关 Microsoft Edge 的详细信息，请参阅[使用 Microsoft Intune 的 Microsoft Edge 管理 web 访问](../apps/manage-microsoft-edge.md)。

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>为组织帐户配置应用通知内容 <!-- 2576686 -->
Android 和 iOS 设备上的 Intune 应用保护策略（应用）允许您控制组织帐户的应用通知内容。 此功能需要应用程序的支持，可能无法用于所有启用应用的应用程序。 有关 APP 的详细信息，请参阅[什么是应用保护策略？](../apps/app-protection-policy.md)。

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>用于 Android 工作配置文件的可用 Google Play 应用报告 <!-- 3041956  -->
对于 Android 工作配置文件设备上的可用应用安装，可以查看应用安装状态以及托管的 Google Play 应用的安装版本。 有关详细信息，请查看[如何监视应用保护策略](../apps/app-protection-policies-monitor.md)、[使用 Intune 管理 Android 工作配置文件设备](../enrollment/android-enterprise-overview.md)和[托管的 Google Play 应用类型](../apps/apps-add-android-for-work.md#managed-google-play-app-types)。

<!-- ***********************************************-->
## <a name="device-configuration"></a>设备配置


### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices----5199328----"></a>受监督的 iOS 和 iPadOS 设备的新设备配置设置 <!-- 5199328  -->
在 iOS 和 iPadOS 设备上，你可以创建一个配置文件以限制设备上的功能和设置（**设备配置** > **配置文件** > **创建配置文件** > **iOS/iPadOS**用于平台 >**设备**配置文件类型的限制）。 将有一些新设置可以控制： 
- 在文件应用中访问网络驱动器  
- 在文件应用中访问 USB 驱动器 
- Wi-fi 始终打开 

要查看最新设置，请转到[使用 Intune 允许或限制功能的 iOS 设备设置](../configuration/device-restrictions-ios.md)。

适用于：
- iOS 13.0 及更高版本
- iPadOS 13.0 及更高版本

### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-and-android-enterprise----5021055----"></a>Android 和 Android 企业版 Wi-fi 配置文件中的 "自动连接" 设置已删除 <!-- 5021055  -->
在 Android 和 Android 企业设备上，你可以创建一个 Wi-fi**配置文件来**配置不同的设置（**设备配置** > **配置文件** >  >    对于适用于配置文件类型的平台 > **wi-fi** ）。 将删除 "**自动连接**" 设置，因为它[不受 Android 支持](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29)。 

如果在 Wi-fi 配置文件中使用此设置，可能会注意**到自动连接**不起作用。 不需要执行任何操作，但请注意，在 Intune 用户界面中会删除此设置。

若要查看当前设置，请参阅[Android wi-fi 设置](../configuration/wi-fi-settings-android.md)或[android 企业 wi-fi 设置](../configuration/wi-fi-settings-android-enterprise.md)。

适用于：
- Android
- Android Enterprise

### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices----4816339----"></a>在 Android 企业设备所有者设备上创建全局 HTTP 代理 <!-- 4816339  -->
在 Android 企业设备上，可以配置全局 HTTP 代理，以满足组织的 web 浏览标准（**设备配置** > **配置文件** > **创建配置文件** > **Android Enterprise**平台 >**设备所有者 >** 配置文件类型的设备限制 >**连接**）。 配置后，所有 HTTP 流量都将使用此代理。

适用于：
- Android Enterprise 设备所有者

### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices----2266073----"></a>适用于 Windows 10 及更高版本设备的新设备固件配置接口配置文件 <!-- 2266073  -->
在 Windows 10 和更高版本中，你可以创建设备配置文件来控制设置和功能（**设备配置** > **配置**文件  > **Create profile** > **Windows 10 和更高版本**的平台）。 将有一个新的设备固件配置接口配置文件类型，该类型允许 Intune 管理 UEFI （BIOS）设置。

若要查看可配置的所有当前设置的概述，请参阅[在 Microsoft Intune 中使用设备配置文件应用设备上的功能和设置](../configuration/device-profiles.md)。

适用于：
- Windows 10 RS5 （1809）及更高版本（选择设备）

### <a name="pkcs-certificates-for-macos-----1333650------------------"></a>MacOS 的 PKCS 证书  <!-- 1333650                -->
我们会在运行 macOS 的设备上添加对 PKCS 证书的完全支持。 用户将能够使用 "自定义使用者" 和 "使用者可选名称" 字段部署用户和设备证书。 我们还将有一个新设置 "允许所有应用访问"，这是通过启用使所有关联的应用访问私钥。 有关此设置的更多详细信息，请访问以下 Apple 文档： https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf 。

###   <a name="derived-credentials-to-provision-mobile-devices-with-certificates----------1736036-1736037-1772050--------"></a>用证书设置移动设备的派生凭据      <!--  1736036, 1736037, 1772050      --> 
我们将添加对派生凭据的支持，支持用于将证书部署到设备的*美国国家标准与技术研究院（NIST） 800-157*标准。  派生凭据依赖于使用个人身份验证（PIV）或公用访问卡（CAC）卡，如智能卡。 用户在计算机上使用其智能卡进行身份验证，然后按照派生凭据提供程序所需的过程为其托管设备提交证书请求。   

使用派生凭据获取证书的过程不同于使用 SCEP 或 PKCS 证书配置文件，但最终结果相同–带有用于身份验证的证书的移动设备，可用于应用身份验证、VPN、Wi-fi 或电子邮件储存.   

有关详细信息，请参阅 www.nccoe.nist.gov 上的[派生 PIV 凭据](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials)。

派生凭据的初始版本将支持 iOS 上的 Entrust Datacard、调解和 DISA Purebred。 以后的版本将支持其他平台和派生的凭据提供程序。   

<!-- ***********************************************-->
## <a name="device-enrollment"></a>设备注册

### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment----4350697---"></a>指定使用工作配置文件或设备管理员注册注册的 Android 设备操作系统版本 <!-- 4350697 -->
使用 Intune 设备类型限制，你将能够使用设备的操作系统版本来指定哪些用户设备将使用 Android 企业工作配置文件注册或 Android 设备管理员注册。 为此，请跳到**Intune** > **设备注册** > **注册限制** > **创建限制** > **设备类型限制** > **平台设置**。

### <a name="edit-device-name-value-for-autopilot-devices----4816775---"></a>编辑 Autopilot 设备的设备名称值 <!-- 4816775 -->
你将能够编辑 Azure AD 联接的 Autopilot 设备的设备名称值。 为此，请转到**Intune** > **设备注册** > **Windows 注册** > **windows Autopilot** > **设备**> 选择设备 > 在右窗格中更改 "设备名称" 值 >**保存**.

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>对于 iOS 设备，自定义公司门户的“注册过程隐私”屏幕 <!-- 4394993  -->
使用 Markdown，能够自定义最终用户在 iOS 注册期间看到的公司门户的隐私屏幕。 具体来说，将能够自定义组织无法在设备上查看或执行的操作列表。

<!-- ***********************************************-->
## <a name="device-management"></a>设备管理


### <a name="edit-group-tag-value-for-autopilot-devices---4816775---"></a>编辑 Autopilot 设备的组标记值<!-- 4816775 -->
你将能够编辑 Autopilot 设备的组标记值。 为此，请转到**Intune** > **设备注册** > **Windows 注册** > **windows Autopilot** > **设备**> 选择设备 > 在右窗格中更改 "组标记" 值 >**保存**.

### <a name="ui-update-for-creating-and-editing-windows-10-update-rings-----4099089------------"></a>用于创建和编辑 Windows 10 更新环的 UI 更新  <!-- 4099089          -->   
我们将为 Intune 推出适用于 Windows 10 更新环的已更新创建和编辑 UI 体验。  对 UI 的更改将包括：  
- 使用在一个边栏选项卡中压缩的向导样式格式简化现有体验。 此 UI 更新将不再出现边栏增加，需要 IT 专业人员向下钻取到深层刀片旅程。   
- 修改创建流以包含分配。  
- 在创建新的更新环之前以及编辑属性时，会添加在查看属性时设置的所有项目的汇总页面。 编辑时，摘要将只显示正在编辑的一个属性类别中设置的项列表。

### <a name="ui-update-for-creating-and-editing-ios-software-updates-----4099090----------"></a>用于创建和编辑 iOS 软件更新的 UI 更新  <!-- 4099090        -->   
我们将推出适用于 Intune 软件更新的已更新创建和编辑 UI 体验。 对 UI 的更改将包括：
- 使用在一个边栏选项卡中压缩的向导样式格式简化现有体验。 此 UI 更新将不再出现边栏增加，需要 IT 专业人员向下钻取到深层刀片旅程。  
- IOS 软件更新策略 create flow 将更新为包含分配 
- 在创建新策略和编辑属性时，iOS 软件更新策略将包含在查看属性时设置的所有项目的汇总页。 编辑时，摘要将只显示正在编辑的一个属性类别中设置的项列表。

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>需要 Jamf 管理的目标 macOS 用户组 <!-- 4061739 -->
你将能够面向特定的用户组，以要求其 macOS 设备由 Jamf 管理。 通过此目标，你可以将 Jamf 符合性集成应用到 macOS 设备的子集，而其他设备仍由 Intune 管理。 它还允许你将用户的设备从一个 MDM 逐渐迁移到另一个 MDM。

### <a name="new-restrictions-for-renaming-windows-devices----3478938---"></a>重命名 Windows 设备的新限制 <!-- 3478938 -->
设备名称必须遵循以下规则：
- 15个字符或更少（必须小于或等于63字节，不包括尾随 NULL）
- 非 Null 或空字符串
- 允许的 ASCII：字母（a-z、a-z）、数字（0-9）和连字符
- 允许的 Unicode：字符 > = 0x80，必须是有效的 UTF8，必须为 IDN-可映射（RtlIdnToNameprepUnicode 成功; 请参阅 RFC 3492）
- 名称不能仅包含数字，也不能以数字开头
- 名称中不能包含空格
- 不允许的字符： {|} ~ [\] ^ '：;< = >？ &AMP; @！ " # $ % ` ( ) + / , . _ *)

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>将软件更新部署到 macOS 设备 <!-- 3194876 -->
你将能够将软件更新部署到 macOS 设备组。 此功能包括关键、固件、配置文件和其他更新。 你将能够在下一次设备签入时发送更新，或选择每周计划，以在你设置的时间内或在你设置的时间内部署更新。 当你想要在标准工作时间之外或在你的支持人员完全配备设备时，此功能可帮助你进行更新。 你还将获得已部署更新的所有 macOS 设备的详细报告。 您可以查看每个设备的报表，以查看特定更新的状态。

<!-- ***********************************************-->
## <a name="monitor-and-troubleshoot"></a>监视和故障排除

### <a name="new-android-report-on-devices-overview-page----2984353----"></a>"新建 Android 报表设备" 概述页 <!-- 2984353  -->
我们会将新报表添加到 "设备概述" 页，其中显示了每个设备管理解决方案中已注册的 Android 设备的数目。 此图表将显示工作配置文件、完全托管、专用和设备管理员注册的设备计数。 若要查看报告，请选择 " **Intune** > **设备**"  > **概述**。

### <a name="windows-autopilot-deployment-reports----3856172----"></a>Windows Autopilot 部署报表 <!-- 3856172  -->
新报表将详细说明通过 Windows Autopilot 部署的每个设备。 此数据将在部署后30天内可用。 若要查看报告，请访问**Intune** > **设备注册** > **监视器** > **Autopilot 部署**。

### <a name="updated-support-experience-------5012398------"></a>更新的支持体验   <!--  5012398    -->
作为持续改进的一部分，我们将更新 Intune 的控制台中支持体验。  我们将改进有关常见问题的控制台中搜索和反馈，并简化工作流以联系支持人员。     

<!-- ***********************************************-->
<!--## Security-->


<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。




