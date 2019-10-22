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
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ea5fae72f6e2057ef0b03a7bd295085ed1ac3bbd
ms.sourcegitcommit: 5807f4db4a45a093ce2fd6cb0c480bec384ec1ff
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601524"
---
# <a name="in-development-for-microsoft-intune---october-2019"></a>开发过程中的 Microsoft Intune 功能 - 2019 年 10 月

为了辅助就绪性和计划，此页面列出了正在开发但尚未发布的 Intune UI 更新和功能。 除了本页上的信息：

- 如果我们预计你需要在更改之前采取措施，我们将在 Office 消息中心发布补充性的文章。
- 当某个功能进入生产环境时，无论该功能是预览版还是正式发布，功能说明都将从此页面移动到[新增内容](whats-new.md)。
- 此页和[新增功能页](whats-new.md)会定期更新。 返回查看其他更新。
- 有关策略性可交付内容和时间线，请参阅 [Microsoft 365 路线图](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)。

> [!NOTE]
> 此页反映了未来版本中有关 Intune 功能的最新预期。 日期和各项功能可能会更改。 本页不介绍开发中的所有功能。

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

### <a name="apply-dark-mode-in-ios-company-portal----4911422----"></a>在 iOS 中应用暗色模式公司门户 <!-- 4911422  -->
为 iOS 公司门户规划了深色模式。 你将能够下载公司应用、管理你的设备，并在你选择的配色方案中获得支持。 有关 iOS 公司门户的详细信息，请参阅[如何配置 Microsoft Intune 公司门户应用](../apps/company-portal-app.md)。

### <a name="run-win32-apps-on-windows-10-s-mode-devices----3747604----"></a>在 Windows 10 S S 模式设备上运行 Win32 应用 <!-- 3747604  --> 
你将能够在 Windows 10 S 模式下管理的设备上安装和运行 Win32 应用。 使用 Windows Defender 应用程序控件（WDAC） PowerShell 工具为 S 模式创建一个或多个补充策略。 使用 Device Guard 签名门户对补充策略进行签名。 然后通过 Intune 上传和分发策略。 

在 Intune 中，可以通过选择 "**客户端应用**"  > **Windows 10 S 补充策略**来找到此功能。 

### <a name="set-app-availability-based-on-a-date-and-time----3510685----"></a>基于日期和时间设置应用可用性 <!-- 3510685  -->
作为管理员，你将能够配置所需应用的开始时间和截止时间。 在开始时，Intune 管理扩展将下载并缓存应用内容。 应用将在截止时间安装。 对于可用应用，开始时间将决定应用在公司门户中的可见性。 

若要设置基于日期和时间的应用可用性，请执行以下操作：

1. 在 Intune 中，选择“客户端应用” > “应用”   。 
1. 从列表中选择应用，或通过选择 "**添加**" 来添加新应用。 
1. 从 "应用" 边栏选项卡中，选择 "**分配**"  > **添加组**"。 
1. 将 "**分配类型**" 设置为 "**必需**"，然后选择 "**包含组**"。 
1. 设置 "**使所有用户都需要此应用** **" 是 "是"** 。 
1. 选择 "**编辑**" 以修改**最终用户体验**选项。 
1. 在 "**最终用户体验**" 边栏选项卡上，根据需要设置**软件可用时间**。 

有关详细信息，请参阅[将应用添加到 Microsoft Intune](../apps/apps-add.md)。

### <a name="require-win32-apps-to-restart----3136567----"></a>需要 Win32 应用重启 <!-- 3136567  -->
成功安装后，您将能够要求 Win32 应用程序重新启动。 你可以选择重启之前的时间量（宽限期）。

### <a name="display-notifications-for-the-company-portal-app-on-windows----1808082----"></a>显示 Windows 上公司门户应用的通知 <!-- 1808082  -->
我们将更新 Windows 设备上的公司门户应用程序，以便向用户显示 toast 通知，即使应用程序处于关闭状态也是如此。 仅当安装状态为 "已完成" 或 "失败" 时，更新才会显示可用应用的通知。 公司门户应用不会显示所需应用程序的通知。

### <a name="display-installation-status-messages-for-the-company-portal-app----2514416----"></a>显示公司门户应用的安装状态消息 <!-- 2514416  -->
公司门户应用会向最终用户显示其他应用安装状态消息。 以下条件适用于新的 Win32 依赖项功能：
- 应用安装失败。 不符合管理员定义的依赖关系。
- 应用已成功安装，但需要重新启动。
- 应用正在安装，但需要重新启动才能继续。

### <a name="assign-the-microsoft-edge-beta-for-macos----4678761----"></a>分配适用于 macOS 的 Microsoft Edge beta <!-- 4678761  -->
你将能够向 Intune for macOS 设备添加并分配最新版本的 Microsoft Edge beta 版。 

分配适用于 macOS 设备的 Microsoft Edge beta：
1. 在 Intune 中，选择 "**客户端应用**"  > **应用**" > **添加应用** > **Microsoft Edge-macOS**。 
1. 将 Microsoft Edge beta 分配给目标组。 Microsoft 自动更新（MAU）将 Microsoft Edge 保持最新状态。 
 
有关 Microsoft Edge 的详细信息，请参阅[使用 Microsoft Intune 的 Microsoft Edge 管理 web 访问](../apps/manage-microsoft-edge.md)。

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>为组织帐户配置应用通知内容 <!-- 2576686 -->
Android 和 iOS 设备上的 Intune 应用允许你为组织帐户控制应用通知内容。 此功能需要应用程序的支持，并可能不适用于所有启用应用的应用程序。 有关 APP 的详细信息，请参阅[什么是应用保护策略？](../apps/app-protection-policy.md)


<!-- ***********************************************-->
## <a name="device-configuration"></a>设备配置

### <a name="new-device-firmware-configuration-interface-profile-for-devices-that-run-windows-10-and-later----2266073----"></a>用于运行 Windows 10 和更高版本的设备的新设备固件配置接口配置文件 <!-- 2266073  -->
在 Windows 10 和更高版本中，可以创建设备配置文件来控制设置和功能： 

1. 选择“设备配置” > “配置文件” > “创建配置文件”    。
1. 在“平台”中，选择“Windows 10 及更高版本”  。 
 
新的设备固件配置接口配置文件类型将允许 Intune 管理 UEFI （BIOS）设置。

有关可以配置的当前设置的信息，请参阅[在 Microsoft Intune 中使用设备配置文件在设备上应用功能和设置](../configuration/device-profiles.md)。

此功能适用于 Windows 10 RS5 （1809）及更高版本（在选择设备上）。
 

<!-- ***********************************************-->
## <a name="device-enrollment"></a>设备注册

### <a name="for-ios-devices-customize-the-enrollment-privacy-window-of-company-portal----4394993----"></a>对于 iOS 设备，自定义公司门户的 "注册隐私" 窗口 <!-- 4394993  -->
使用 Markdown，能够自定义最终用户在 iOS 注册期间看到的公司门户隐私窗口。 具体来说，将能够自定义组织无法在设备上查看或执行的操作列表。

<!-- ***********************************************-->
## <a name="device-management"></a>设备管理


### <a name="edit-the-group-tag-value-for-autopilot-devices---4816775---"></a>编辑 Autopilot 设备的组标记值<!-- 4816775 -->
你将能够编辑 Autopilot 设备的**组标记**值：

1. 选择**Intune**  > **设备注册** > **windows 注册** > **windows Autopilot**  > **设备**。
1. 选择设备。
1. 在右侧窗格中，更改 "**组标记**" 值。
1. 选择“保存”  。

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>需要 Jamf 管理的目标 macOS 用户组 <!-- 4061739 -->
你将能够面向特定的用户组，以要求 Jamf 管理其 macOS 设备。 通过此目标，你可以将 Jamf 符合性集成应用到 macOS 设备的子集，而其他设备仍由 Intune 管理。 通过目标，还可以将用户设备从一个移动设备管理（MDM）系统逐步迁移到另一台移动设备管理（MDM）系统。

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>将软件更新部署到 macOS 设备 <!-- 3194876 -->
你将能够将软件更新部署到 macOS 设备组。 此功能包括关键、固件、配置文件和其他更新。 你可以在下一个设备签入中发送更新。 或者，你可以选择每周计划，以将更新部署在你设置的或时间段内。 

如果你想要在标准工作时间之外或在你的支持人员完全配备时在非工作时间更新设备，则可以使用此功能。 你还将获得已部署更新的所有 macOS 设备的详细报告。 您可以按设备钻取到报表以查看特定更新的状态。

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>监视和故障排除

### <a name="android-report-on-the-devices-overview-page----2984353----"></a>"设备概述" 页上的 Android 报表 <!-- 2984353  -->
我们会将新报表添加到 "**设备概述**" 页。 此报表显示每个设备管理解决方案中已注册的 Android 设备的数目。 该图表显示了工作配置文件的设备计数、完全托管、专用和设备管理员注册。 

若要查看报告，请选择 " **Intune** > **设备**"  > **概述**。

### <a name="updated-support-experience-------5012398------"></a>更新的支持体验   <!--  5012398    -->
作为持续改进的一部分，我们将更新 Intune 的控制台中支持体验。  我们将为常见问题改善控制台内搜索和反馈，并简化工作流以联系支持人员。     

<!-- ***********************************************-->
<!--## Security-->


<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。
