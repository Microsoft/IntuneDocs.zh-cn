---
title: 开发过程中 - Microsoft Intune
titleSuffix: ''
description: 开发过程中的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/03/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7113552e09a7c7fa145a452e56575bfaf5297c3e
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514552"
---
# <a name="in-development-for-microsoft-intune---february-2020"></a>Microsoft Intune 开发过程中的功能 - 2020 年 2 月

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

### <a name="retarget-web-clips-to-microsoft-edge-on-iosipados-devices---5455276---"></a>在 iOS/iPadOS 设备上将 Web 剪辑重定向到 Microsoft Edge<!-- 5455276 -->
Web 剪辑在 iOS/iPadOS 设备上充当已固定的 Web 应用，需要更新。 如果需要在受保护的浏览器中打开新部署的 Web 剪辑，将在 Microsoft Edge（而不是在 Intune Managed Browser 中）打开它们。 必须重定向现有 Web 剪辑，以确保它们在 Microsoft Edge 而不是 Managed Browser 中打开。

### <a name="macos-company-portal-user-experience-improvements---5568987---"></a>macOS 公司门户用户体验改进<!-- 5568987 -->
我们正在改进 macOS 设备注册体验和适用于 Mac 的公司门户应用。 预期会出现以下情况：
- 注册期间获得更好的 Microsoft AutoUpdate  体验，这可确保用户拥有最新版本的公司门户。
- 注册期间增强的符合性检查步骤。
- 支持复制的事件 ID，使用户可更快地将错误从其设备发送到公司支持团队。

有关注册和适用于 Mac 的公司门户应用的详细信息，请参阅使用公司门户应用注册 macOS 设备 (https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos-cp) )。 


### <a name="screen-removed-from-company-portal-android-work-profile-enrollment--6103987---"></a>从公司门户的 Android 工作配置文件注册中删除了屏幕<!--6103987 -->
从公司门户中的 Android 工作配置文件注册流中删除“下一步是什么?”  屏幕，简化用户体验。 请转到[使用 Android 工作配置文件注册]( https://docs.microsoft.com/intune-user-help/enroll-device-android-work-profile)，查看当前的 Android 工作配置文件注册流。

### <a name="microsoft-defender-advanced-threat-protection-atp-app-for-macos---5424518-idready---"></a>适用于 macOS 的 Microsoft Defender 高级威胁防护 (ATP) 应用<!-- 5424518 idready -->
Intune 将提供一种简单的方法，将适用于 macOS 的 Microsoft Defender 高级威胁防护 (ATP) 应用部署到托管 Mac 设备。 有关详细信息，请参阅[适用于 macOS 的 Microsoft Defender 高级威胁防护](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac)。 

<!-- ***********************************************-->
## <a name="device-configuration"></a>设备配置

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>macOS 设备的有线网络设备配置文件<!-- 3508686  -->
可使用新的 macOS 设备配置文件来配置有线网络（“设备配置” > “配置文件” > “创建配置文件” > 选择“macOS”作为平台 > 选择“有线网络”作为配置文件类型      ）。 使用此功能创建 802.1x 配置文件来管理有线网络，并将这些有线网络部署到 macOS 设备。

适用于：
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-iosipados-devices----1947932-idready---"></a>具有 IKEv2 VPN 连接的 VPN 配置文件可将“始终可用”用于 iOS/iPadOS 设备 <!-- 1947932 idready -->
在 iOS/iPadOS 设备上，可创建使用 IKEv2 连接的 VPN 配置文件（“设备配置” > “配置文件” > 创建配置文件 >  选择“iOS/iPadOS”作为平台 > 选择“VPN”作为配置文件类型      ）。 在未来的更新中，可为 IKEv2 配置“始终可用”。 配置后，IKEv2 VPN 配置文件会自动连接并保持连接（或快速重新连接）到 VPN。 即使切换网络或重启设备，它仍会保持连接。

在 iOS/iPadOS 上，始终可用 VPN 仅限于 IKEv2 配置文件。

要查看当前可配置的 IKEv2 设置，请转到[在 iOS/iPadOS 设备上的 Microsoft Intune 中添加 VPN 设置](../configuration/vpn-settings-ios.md#ikev2-settings)。

适用于：
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-iosipados-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>改善了在 iOS/iPadOS 和 macOS 设备上创建配置文件时的用户界面体验<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
为 iOS/iPadOS 或 macOS 设备创建配置文件时，将更新“终结点管理”管理中心中的体验。 此更改会影响以下设备配置文件（“设备” > “配置文件” > “创建配置文件” >  选择“iOS”或“macOS”作为平台      ）：

- 自定义：iOS/iPadOS、macOS
- 设备功能：iOS/iPadOS、macOS
- 设备限制：iOS/iPadOS、macOS
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
## <a name="device-management"></a>设备管理

### <a name="change-primary-user-for-windows-devices----3794742---"></a>更改 Windows 设备的主要用户 <!-- 3794742 -->
你能够更改 Windows 混合设备和 Azure AD 联接设备的主要用户。 为此，请转到“Intune”   > “设备”   > “所有设备”  > 选择设备 >“属性”   > “主要用户”  。 

### <a name="serial-number-on-the-apple-mdm-push-certificate-page--5947765---"></a>Apple MDM Push 证书页上的序列号<!--5947765 -->
Apple MDM Push 证书页将显示序列号。 如果对创建该证书的 Apple ID 的访问权限丢失，则需要该序列号以重新获得对 Apple MDM Push 证书的访问权限。 若要查看序列号，请转到“设备”   > “iOS”   > “iOS 注册”   > “Apple MDM Push 证书”  。

### <a name="choose-which-iosipados-updates-to-push-to-enrolled-devices--5879689---"></a>选择要推送到已注册设备的 iOS/iPadOS 更新<!--5879689 -->
你能够选择特定的 iOS/iPadOS 更新，将更新推送至已使用 Apple Business Manager 或 Apple School Manager 注册的设备。 此类设备必须设置设备配置策略，将软件更新可见性延迟数天。 若要查看此功能，请转到 MEM >“设备”   > “iOS”   > “更新 iOS/iPadOS 的策略”   > “创建配置文件”  。

### <a name="new-update-schedule-options-for-pushing-os-updates-to-enrolled-iosipados-devices--5879689--"></a>用于将 OS 更新推送到已注册 iOS/iPadOS 设备的新更新计划选项<!--5879689-->
在为 iOS/iPadOS 设备计划操作系统更新时，你能够从以下选项中进行选择。 这适用于使用 Apple Business Manager 或 Apple School Manager 注册类型的设备。
- 下次签入时更新
- 在计划时间内更新
- 在计划时间外更新

对于后两个选项，可创建多个时间窗口。

若要查看新选项，请转到 MEM >“设备”   > “iOS”   > “更新 iOS/iPadOS 的策略”   > “创建配置文件”  。


<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>监视和故障排除

### <a name="improved-intune-reporting-experience---3791418-idready---"></a>改进了 Intune 报表体验<!-- 3791418 idready -->
Intune 现在提供了改进的报表体验，包括新的报表类型、更好的报表组织、更集中的视图、改进的报表功能以及更一致和更及时的数据。 报告体验将从公共预览版迁移到 GA 版（正式版）。 此外，GA 版本还将提供本地化支持、bug 修复、设计改进，并在 [Microsoft终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)的磁贴上聚合设备符合性数据。

新的报表类型侧重于以下内容：
- **操作** - 提供具有负面运行状况的全新记录。 
- **组织** - 提供总体状态的更广泛汇总。
- **历史** - 提供一段时间内的模式和趋势。
- **专业** - 允许使用原始数据创建自己的自定义报表。

第一组新报表侧重于设备符合性。 有关详细信息，请参阅[博客 - Microsoft Intune 报表框架](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553)和 [Intune 报表](~/fundamentals/reports.md)。



<!-- ***********************************************-->
## <a name="role-based-access-control"></a>基于角色的访问控制

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>即将更改“Intune 角色”用户界面<!--5801612 idready-->
[Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)的用户界面  > “租户管理” > “角色”将更改为更易用的直观设计   。 此体验提供的设置和详细信息与你现在使用的相同，但是新体验采用类似于向导的过程。


<!-- ***********************************************-->
## <a name="security"></a>安全

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Android COBO 设备上的派生凭据支持<!--4839592-->
你将能够在 Android 企业版完全托管设备上使用派生凭据。 将添加有关为 Entrust Datacard、Intercede 和 DISA Purebred 检索派生凭据的支持。 你将能够使用派生凭据进行应用身份验证、Wi-Fi、VPN 或 S/MIME 签名，并/或通过支持该凭据的应用进行加密。

### <a name="use-antivirus-policy-to-manage-settings-for-microsoft-defender-antivirus-and-the-windows-security-experience--6131401---"></a>使用防病毒策略管理 Microsoft Defender 防病毒和 Windows 安全体验的设置<!--6131401 -->
在“终结点安全”  节点中，你能够配置防病毒设置  。 配置防病毒策略时，需通过两种配置文件类型来定义 Windows 10 设备的设置：

- Microsoft Defender 防病毒：管理云保护、防病毒排除项、修正、扫描选项等设置。
- Windows 安全体验：管理用户在其设备上体验 Windows 安全设置的方式。 你可配置最终用户可在 Microsoft Defender 安全中心查看的内容以及他们收到的通知。 

<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。


