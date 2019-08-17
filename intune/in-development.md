---
title: 开发过程中 - Microsoft Intune
titleSuffix: ''
description: 开发过程中的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3c2b9429bf5b50ac5e416c4a7b356627e9cc9fb1
ms.sourcegitcommit: f75386986d24e7d5dd63a3f1a0a014cb52056063
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 08/16/2019
ms.locfileid: "69560107"
---
# <a name="in-development-for-microsoft-intune---august-2019"></a>开发过程中的 Microsoft Intune 功能 - 2019 年 8 月

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

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>为组织帐户配置应用通知内容 <!-- 2576686 -->
Android 和 iOS 设备上的 Intune 应用保护策略 (应用) 允许您控制组织帐户的应用通知内容。 此功能需要应用程序的支持, 可能无法用于所有启用应用的应用程序。 有关 APP 的详细信息，请参阅[什么是应用保护策略？](app-protection-policy.md)。

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>用于 Android 工作配置文件的可用 Google Play 应用报告 <!-- 3041956  -->
对于 Android 工作配置文件设备上的可用应用安装，可以查看应用安装状态以及托管的 Google Play 应用的安装版本。 有关详细信息，请查看[如何监视应用保护策略](app-protection-policies-monitor.md)、[使用 Intune 管理 Android 工作配置文件设备](android-enterprise-overview.md)和[托管的 Google Play 应用类型](apps-add-android-for-work.md#managed-google-play-app-type)。

<!-- ***********************************************-->
## <a name="device-configuration"></a>设备配置

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>支持适用于 iOS 的 IKEv2 VPN 配置文件 <!-- 1943438 -->
可以使用 IKEv2 协议为 iOS 本机 VPN 客户端创建 VPN 配置文件。 IKEv2 是以下位置中的新连接类型：  “设备配置” >   “配置文件” > “创建配置文件”   > 平台为“iOS”  >配置文件类型为“VPN”  >“设置”  。

这些 VPN 配置文件配置本机 VPN 客户端。 因此，没有 VPN 客户端应用安装或推送到托管设备。 此功能要求设备在 Intune （MDM 注册）中注册。

要查看当前可配置的 VPN 设置，请转到[在 iOS 设备上的 Microsoft Intune 中配置 VPN 设置](vpn-settings-ios.md)。

适用于：iOS

<!-- ***********************************************-->
## <a name="device-enrollment"></a>设备注册

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>对于 iOS 设备, 自定义公司门户的 "注册过程隐私" 屏幕 <!-- 4394993  -->
使用 markdown, 你可以自定义公司门户的隐私屏幕, 最终用户可以在 iOS 注册过程中看到这些屏幕。 具体而言, 你将能够自定义你的组织无法在设备上看到或执行的操作的列表。

<!-- ***********************************************-->
## <a name="security"></a>安全

### <a name="import-and-export-security-baselines------3408610------------"></a>导入和导出安全基线    <!--3408610          -->  
我们添加的功能是导出和导入安全基线。 此功能可让你进行自定义并在 Intune 环境之间共享。

<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。




