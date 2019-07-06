---
title: 开发过程中 - Microsoft Intune
titleSuffix: ''
description: 开发过程中的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f7dd6f62cb53dd0cc373fb3f2ffa7d9434b135cd
ms.sourcegitcommit: 116ef72b9da4d114782d4b8dd9f57556c9b01511
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2019
ms.locfileid: "67494247"
---
# <a name="in-development-for-microsoft-intune---july-2019"></a>Microsoft Intune 开发过程中的功能 - 2019 年 7 月

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


### <a name="customized-notifications-for-users-and-groups-------16766574-----"></a>自定义的通知的用户和组    <!-- 16766574   -->
你将很快能够从公司门户应用程序到 iOS 和使用 Intune 管理的 Android 设备上的用户发送自定义的临时推送通知。 这些自定义通知不受限于特定 Intune 功能和可用于任何目的需要，包括常规通知你想要将发送到某些或所有员工。  

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>配置组织帐户的应用通知的内容 <!-- 2576686 -->
在 Android 和 iOS 设备上的 Intune 应用保护策略 （应用） 将允许您对控件应用通知内容为组织帐户。 此功能将需要从应用程序的支持，并且可能不可用的所有应用程序启用应用程序。 有关 APP 的详细信息，请参阅[什么是应用保护策略？](app-protection-policy.md)。

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>用于 Android 工作配置文件的可用 Google Play 应用报告 <!-- 3041956  -->
对于 Android 工作配置文件设备上的可用应用安装，可以查看应用安装状态以及托管的 Google Play 应用的安装版本。 有关详细信息，请查看[如何监视应用保护策略](app-protection-policies-monitor.md)、[使用 Intune 管理 Android 工作配置文件设备](android-enterprise-overview.md)和[托管的 Google Play 应用类型](apps-add-android-for-work.md#managed-google-play-app-type)。

<!-- ***********************************************-->
## <a name="device-configuration"></a>设备配置


### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>支持适用于 iOS 的 IKEv2 VPN 配置文件 <!-- 1943438 -->
可以使用 IKEv2 协议为 iOS 本机 VPN 客户端创建 VPN 配置文件。 IKEv2 是以下位置中的新连接类型：  “设备配置” >   “配置文件” > “创建配置文件”   > 平台为“iOS”  >配置文件类型为“VPN”  >“设置”  。

这些 VPN 配置文件配置本机 VPN 客户端。 因此，没有 VPN 客户端应用安装或推送到托管设备。 此功能要求设备在 Intune （MDM 注册）中注册。

要查看当前可配置的 VPN 设置，请转到[在 iOS 设备上的 Microsoft Intune 中配置 VPN 设置](vpn-settings-ios.md)。

适用于：iOS

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>在创建 Windows 10 设备配置配置文件时使用“适用性规则” <!-- 2549910 -->
创建 Windows 10 设备配置配置文件（“设备配置” > “配置文件” > “创建配置文件” > 适用于平台的“Windows 10”）     。 你将能够创建“适用性规则”，使配置文件仅应用于特定版本  。 例如，创建一个启用某些 BitLocker 设置的配置文件。 添加配置文件后，请使用适用性规则，使配置文件仅适用于运行 Windows 10 企业版的设备。

适用于： 
- Windows 10 及更高版本

### <a name="administrative-templates-for-group-policy---------3510695---"></a>用于组策略的管理模板     <!--  3510695 -->
为提高云端设备安全性，我们将发布管理模板，让用户使用 Intune 为 Windows 电脑配置精选的组策略设置。  这些模板使用策略配置服务提供商 (CSP) 来提供 Office、Windows 和 OneDrive 中的多达 2500 个其他设置。

### <a name="manage-filevault-for-macos-------3858502--1210104-----"></a>管理适用于 macOS 的 FileVault   <!--  3858502 + 1210104   -->
您可以使用 Intune 终结点保护设备配置文件来管理 FileVault 适用于 macOS 设备的密钥加密。 这包括托管的查看和旋转公司设备的加密密钥。 最终用户将能够检索这些密钥通过公司门户网站。

### <a name="advanced-settings-for-windows-defender-firewall-------1311949-------"></a>Windows Defender 防火墙的高级设置   <!--  1311949     -->
作为公共预览版，你很快就可以使用 Intune 在客户端上管理 Windows Defender 的自定义防火墙规则。  

### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise----3712769----"></a>新配置设计器创建 Android 企业版 OEMConfig 配置文件时 <!-- 3712769  -->
在 Intune 中，您可以创建使用 OEMConfig 应用的设备配置配置文件 (设备配置 > 配置文件 > 创建配置文件 > Android 企业版为平台 > OEMConfig 配置文件类型)。 如果执行此操作时，JSON 编辑器会使用的模板和值以更改打开。 此更新包括配置设计器使用改进的用户体验，可以显示嵌入在应用中，包括标题、 说明和详细信息的详细信息。 JSON 编辑器仍然可用，并显示你在配置设计器中进行任何更改。

若要查看当前设置，请转到[使用和管理 Android 企业设备与 OEMConfig](android-oem-configuration-overview.md)。

适用对象：Android Enterprise


<!-- ***********************************************-->
## <a name="device-management"></a>设备管理

### <a name="improve-device-location---3855417---"></a>提高设备位置<!-- 3855417 -->
你将能够缩放到的设备使用的确切坐标**定位设备**操作。 有关查找丢失的 iOS 设备的详细信息，请参阅[查找丢失的 iOS 设备](device-locate.md)。

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>配置自动设备清理时间限制减少到 30 天 <!--4231059  -->
您可以设置自动设备清理时间限制短短的上次登录后的 30 天 （而不是当前限制为 90 天）。 若要执行此操作，请转到**Intune** > **设备** > **安装** > **设备清理了规则**。


<!-- ***********************************************-->
## <a name="security"></a>安全

### <a name="import-and-export-security-baselines------3408610------------"></a>导入和导出安全基准    <!--3408610          -->  
我们添加了导出和导入安全基准，以便您可以执行你与你的自定义和共享 Intune 环境之间的功能。



<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。


