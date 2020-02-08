---
title: 开发过程中 - Microsoft Intune
titleSuffix: ''
description: 开发过程中的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/07/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d71ae3c15dddedd5d9ebfaf06fcae25af89f6b82
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912619"
---
# <a name="in-development-for-microsoft-intune---january-2020"></a>Microsoft Intune 开发过程中的功能 - 2020 年 1 月

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

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>在 Windows 上显示来自“公司门户”应用的通知<!-- 1808082  -->
我们将更新 Windows 设备上的“公司门户”应用，以便向用户显示 toast 通知（即使应用程序处于关闭状态）。 仅当安装状态为“已完成”或“失败”时，更新才会显示有关可用应用的通知。 “公司门户”应用不会显示必需应用程序的通知。 

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>显示“公司门户”应用的安装状态消息<!-- 2514416  -->
“公司门户”应用会向最终用户显示其他应用安装状态消息。 以下条件适用于新的 Win32 依赖项功能：
- 应用安装失败。 不符合管理员定义的依赖项。

### <a name="retarget-web-clips-to-microsoft-edge-on-ios-devices---5455276---"></a>在 iOS 设备上将 Web 剪辑重定向到 Microsoft Edge<!-- 5455276 -->
Web 剪辑在 iOS 设备上充当已固定的 Web 应用，需要更新。 如果需要在受保护的浏览器中打开新部署的 Web 剪辑，将在 Microsoft Edge（而不是在 Intune Managed Browser 中）打开它们。 必须重定向现有 Web 剪辑，以确保它们在 Microsoft Edge 而不是 Managed Browser 中打开。 


<!-- ***********************************************-->
## <a name="device-configuration"></a>设备配置

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>macOS 设备的有线网络设备配置文件<!-- 3508686  -->
可使用新的 macOS 设备配置文件来配置有线网络（“设备配置” > “配置文件” > “创建配置文件” > 选择“macOS”作为平台 > 选择“有线网络”作为配置文件类型      ）。 使用此功能创建 802.1x 配置文件来管理有线网络，并将这些有线网络部署到 macOS 设备。

适用于：
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-ios-devices----1947932-idready---"></a>具有 IKEv2 VPN 连接的 VPN 配置文件可将“始终可用”用于 iOS 设备 <!-- 1947932 idready -->
在 iOS 设备上，可创建使用 IKEv2 连接的 VPN 配置文件（“设备配置” > “配置文件” > 创建配置文件 >  选择“iOS/iPadOS”作为平台 > 选择“VPN”作为配置文件类型      ）。 在未来的更新中，可为 IKEv2 配置“始终可用”。 配置后，IKEv2 VPN 配置文件会自动连接并保持连接（或快速重新连接）到 VPN。 即使切换网络或重启设备，它仍会保持连接。

在 iOS 上，始终可用 VPN 仅限于 IKEv2 配置文件。

要查看当前可配置的 IKEv2 设置，请转到[在 iOS 设备上的 Microsoft Intune 中添加 VPN 设置](../configuration/vpn-settings-ios.md#ikev2-settings)。

适用于：
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-ios-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>改善了在 iOS 和 macOS 设备上创建配置文件时的用户界面体验<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
为 iOS 或 macOS 设备创建配置文件时，将更新“终结点管理”管理中心中的体验。 此更改会影响以下设备配置文件（“设备” > “配置文件” > “创建配置文件” >  选择“iOS”或“macOS”作为平台      ）：

- 自定义：iOS、macOS
- 设备功能：iOS、macOS
- 设备限制：iOS、macOS
- 终结点保护：macOS
- 扩展：macOS
- 首选项文件：macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-idready----"></a>改善了在 Android 企业版设备上创建 OEMConfig 配置文件时的用户界面体验<!-- 5568645 idready  -->
创建或编辑适用于 Android 企业版设备的 OEMConfig 配置文件时，将更新“终结点管理”管理中心中的体验。 更新的体验将提供已配置设置的摘要的概览。 此更改会影响 OEMConfig 设备配置文件（“设备” > “配置文件” > “创建配置文件” >  选择“Android 企业版”作为平台 > 选择“OEMConfig”作为配置文件类型      ）。

此功能适用于：
- Android Enterprise 

<!-- ***********************************************-->
<!--## Device enrollment-->



<!-- ***********************************************-->
<!--## Device management-->



<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->

<!--
## Monitoring and troubleshooting
-->


<!-- ***********************************************-->
## <a name="role-based-access-control"></a>基于角色的访问控制

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>即将更改“Intune 角色”用户界面<!--5801612 idready-->
[Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)的用户界面  > “租户管理” > “角色”将更改为更易用的直观设计   。 此体验提供的设置和详细信息与你现在使用的相同，但是新体验采用类似于向导的过程。


<!-- ***********************************************-->
## <a name="security"></a>安全

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Android COBO 设备上的派生凭据支持<!--4839592-->
你将能够在 Android 企业版完全托管设备上使用派生凭据。 将添加有关为 Entrust Datacard、Intercede 和 DISA Purebred 检索派生凭据的支持。 你将能够使用派生凭据进行应用身份验证、Wi-Fi、VPN 或 S/MIME 签名，并/或通过支持该凭据的应用进行加密。 

<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。


