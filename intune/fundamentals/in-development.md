---
title: 开发过程中 - Microsoft Intune
titleSuffix: ''
description: 开发过程中的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3720b0b9a67f0c3462993feef4162ef35f7f3f92
ms.sourcegitcommit: d1b36501186e867355843ddd67c795ade800b76a
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2019
ms.locfileid: "73182921"
---
# <a name="in-development-for-microsoft-intune---november-2019"></a>开发过程中的 Microsoft Intune 功能 - 2019 年 11 月

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

### <a name="smime-support-for-microsoft-outlook-mobile----2669398----"></a>Microsoft Outlook Mobile 的 S/MIME 支持 <!-- 2669398  -->
Intune 将支持提供 S/MIME 签名和加密证书，这些证书可用于 iOS 和 Android 上的 Outlook Mobile。 有关相关信息，请参阅适用于[iOS 设备的电子邮件设置](~/configuration/email-settings-ios.md)和[Android 设备的电子邮件设置](~/configuration/email-settings-android.md)。

### <a name="custom-settings-support-for-macos-applications----4736278----"></a>自定义设置对 macOS 应用程序的支持 <!-- 4736278  -->
Intune 将支持自定义设置，允许你将特定的键和值添加到现有的首选项属性列表（info.plist）文件，以配置 macOS 应用和设备。 并非所有应用都支持托管首选项，并且在某些情况下，只能管理特定设置。 仅通过设备通道部署设置。 只应上载属性列表文件或以设备通道设置为目标的 .xml 文件。

### <a name="assignment-type-value-in-windows-company-portal----5459950----"></a>Windows 公司门户中的分配类型值 <!-- 5459950  -->
将更新 Windows 公司门户应用程序的 "**已安装的应用**程序" 页。 已将 "**已安装的应用**" 页的 "**分配类型**" 列更新为 "组织要求"。 可能的值为 **"是" 或 "** **否**" 以指定所需的与可用的应用。 进行此更改是为了响应最终用户的一些混乱。 有关 Windows 公司门户的详细信息，请参阅[如何配置 Microsoft Intune 公司门户应用](~/apps/company-portal-app.md)。

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

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>为组织帐户配置应用通知内容 <!-- 2576686 -->
Android 和 iOS 设备上的 Intune 应用允许你为组织帐户控制应用通知内容。 此功能需要应用程序的支持，并可能不适用于所有启用应用的应用程序。 有关 APP 的详细信息，请参阅[什么是应用保护策略？](../apps/app-protection-policy.md)


<!-- ***********************************************-->
## <a name="device-configuration"></a>设备配置

### <a name="use-pkcs-certificates-with-wi-fi-profiles-on-windows-10-and-later-devices----3246388----"></a>在 Windows 10 和更高版本的设备上将 PKCS 证书与 Wi-fi 配置文件配合使用 <!-- 3246388  -->
目前，可以通过 SCEP 证书（**设备配置** > **配置文件** > **创建配置**文件 > **windows 10 和更高版本**的平台 > **wi-fi**配置文件类型 > **Enterprise** > **EAP 类型**）。 你将能够将 PKCS 证书用于 Windows Wi-fi 配置文件。 此功能允许用户使用租户中的新的或现有的 PKCS 证书配置文件对 Wi-fi 配置文件进行身份验证。 

有关 Wi-fi 配置文件的详细信息，请参阅[在 Intune 中添加适用于 Windows 10 及更高版本设备的 wi-fi 设置](../configuration/wi-fi-settings-windows.md)。

适用于：
- Windows 10 及更高版本

### <a name="new-exchangeactivesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices----4892824----"></a>在 iOS 设备上创建电子邮件设备配置文件时，新的 ExchangeActiveSync 设置 <!-- 4892824  --> 
在 iOS/iPadOS 设备上，你可以在设备配置文件中配置电子邮件连接（**设备配置** > **配置**文件 > **创建配置**文件 > 适用于平台的**ios/iPadOS** >**电子邮件**对于配置文件类型）。 

将提供新的 ExchangeActiveSync 设置，其中包括：
- 选择要同步的服务（或阻止同步），如电子邮件、日历和联系人。
- 允许（或阻止）用户在其设备上更改这些服务的同步设置。 

若要查看当前设置，请[在 Intune 中中转到 iOS 设备的电子邮件配置文件设置](../configuration/email-settings-ios.md)。

适用于：
- iOS 13.0 及更高版本
- iPadOS 13.0 及更高版本

### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-device-owner-and-dedicated-devices----5353228----"></a>阻止用户将个人 Google 帐户添加到 Android 企业设备所有者和专用设备 <!-- 5353228  -->
你将能够阻止用户在 Android 企业设备所有者和专用设备上创建个人 Google 帐户（**设备配置** > **配置文件** > **创建配置文件** > **Android 企业版**对于平台 >**设备所有者仅 >** 配置文件类型 >**用户和帐户设置**）的设备限制。

要查看可以配置的当前设置，请转到[使用 Intune 允许或限制功能的 Android Enterprise 设备设置](../configuration/device-restrictions-android-for-work.md)。

适用于：
- Android Enterprise 设备所有者
- Android Enterprise 专用设备

### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-ios-device-restrictions-profile----5468501----"></a>IOS 设备限制配置文件中删除了 Siri 命令的服务器端日志记录设置 <!-- 5468501  -->
在 iOS 设备上，你可以创建一个设备限制配置文件，用于为 Siri 命令配置服务器端日志记录（**设备配置** > **配置文件** > **创建配置文件** > **iOS/iPadOS**用于平台>**内置应用程序**的配置文件类型 >**设备限制**。 将删除**Siri 命令的服务器端日志记录**设置。

此设置将从 Intune 管理控制台中删除。 即使配置了此设置的现有策略将继续显示此设置，此设置在设备上也不起作用。 如果要从现有策略中删除此设置，请执行策略，进行次要编辑，保存，并更新策略。

要查看可以配置的设置，请参阅[使用 Intune 允许或限制功能的 iOS 和 iPadOS 设备设置](../configuration/device-restrictions-ios.md)。

适用于：
- iOS


<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
## <a name="device-management"></a>设备管理

### <a name="edit-device-name-value-for-autopilot-devices---2640074----"></a>编辑 Autopilot 设备的设备名称值<!-- 2640074  -->
你将能够编辑 Azure AD 联接的 Autopilot 设备的设备名称值。 为此，请转到**Intune** > **设备注册** > **windows 注册** > **windows Autopilot** > **设备**> 选择设备 > 在右窗格中更改 "**设备名称**" 值>**保存**。


### <a name="edit-the-group-tag-value-for-autopilot-devices---4816775---"></a>编辑 Autopilot 设备的组标记值<!-- 4816775 -->
你将能够编辑 Autopilot 设备的**组标记**值：

1. 选择**Intune**  > **设备注册** > **windows 注册** > **windows Autopilot**  > **设备**。
1. 选择设备。
1. 在右侧窗格中，更改 "**组标记**" 值。
1. 选择“保存”  。

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>需要 Jamf 管理的目标 macOS 用户组 <!-- 4061739 -->
你将能够面向特定的用户组，以要求 Jamf 管理其 macOS 设备。 通过此目标，你可以将 Jamf 符合性集成应用到 macOS 设备的子集，而其他设备仍由 Intune 管理。 通过目标，还可以将用户设备从一个移动设备管理（MDM）系统逐步迁移到另一台移动设备管理（MDM）系统。

<!-- ***********************************************-->
## <a name="intune-apps"></a>Intune 应用

### <a name="improved-macos-enrollment-experience-in-company-portal----5074349----"></a>公司门户中改进了 macOS 注册体验 <!-- 5074349  -->
MacOS 注册体验的公司门户将有一个更简单的注册过程，该过程将更密切地与 iOS 注册体验公司门户相匹配。 设备用户将看到：  

* 轻巧的用户界面。  
* 改进的注册清单。  
* 更清楚地说明如何注册其设备。  
* 改进了疑难解答选项。  

### <a name="improved-checklist-design-in-company-portal-app-for-android---5550857----"></a>公司门户适用于 Android 的应用程序中改进了清单设计<!-- 5550857  -->
适用于 Android 的公司门户应用程序中的设置清单将更新为轻型设计和新图标。 所做的更改将与针对 iOS 的公司门户应用程序的最新更新进行对齐。

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>监视和故障排除

### <a name="updated-support-experience-------5012398------"></a>更新的支持体验   <!--  5012398    -->
作为持续改进的一部分，我们将更新 Intune 的控制台中支持体验。  我们将为常见问题改善控制台内搜索和反馈，并简化工作流以联系支持人员。     

<!-- ***********************************************-->
## <a name="role-based-access-control"></a>基于角色的访问控制

### <a name="duplicate-custom-or-built-in-roles----1081938---"></a>复制自定义或内置角色 <!-- 1081938 -->
你将能够复制内置和自定义角色。 为此，请参阅**Intune** > **角色** > **所有角色**> 在列表中选择一个角色 > "**重复**"。 请确保输入唯一的名称。

<!-- ***********************************************-->

## <a name="security"></a>安全

### <a name="bitlocker-key-rotation--------2564951--------"></a>BitLocker 密钥轮换     <!-- 2564951      -->
你将能够使用 Intune 为运行 Windows 版本1909或更高版本的受管理设备旋转 BitLocker 恢复密钥。 

<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。
