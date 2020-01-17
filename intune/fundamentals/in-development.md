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
ms.openlocfilehash: 01ea2f75d166e5cc6aef4b890dba5722a74c1f61
ms.sourcegitcommit: 8f56220e7cafc5bc43135940575a9acb5afde730
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 01/09/2020
ms.locfileid: "75827813"
---
# <a name="in-development-for-microsoft-intune---january-2020"></a>Microsoft Intune 开发过程中的功能 - 2020 年 1 月

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

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>显示 Windows 上公司门户应用的通知<!-- 1808082  -->
我们将更新 Windows 设备上的公司门户应用程序，以便向用户显示 toast 通知，即使应用程序处于关闭状态也是如此。 仅当安装状态为 "已完成" 或 "失败" 时，更新才会显示可用应用的通知。 公司门户应用不会显示所需应用程序的通知。 

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>显示公司门户应用的安装状态消息<!-- 2514416  -->
公司门户应用会向最终用户显示其他应用安装状态消息。 以下条件适用于新的 Win32 依赖项功能：
- 应用安装失败。 不符合管理员定义的依赖关系。

### <a name="retarget-web-clips-to-microsoft-edge-on-ios-devices---5455276-idready---"></a>向 iOS 设备上的 Microsoft Edge 重定目标 web 剪辑<!-- 5455276 idready -->
在 iOS 设备上充当固定的 web 应用的 web 剪辑将需要更新。 新部署的 web 剪辑将在 Microsoft Edge 中打开，而不是在受保护的浏览器中打开的 Intune Managed Browser （如果需要）。 必须重定现有 web 剪辑的目标，以确保它们在 Microsoft Edge 而不是 Managed Browser 中打开。 

### <a name="user-experience-change-when-adding-apps-to-intune---4705829-idready---"></a>向 Intune 添加应用时的用户体验更改<!-- 4705829 idready -->
通过 Intune 添加应用时，你将看到新的用户体验。 此体验提供了以前使用过的相同设置和详细信息，但是，在将应用添加到 Intune 之前，新体验会按照类似于向导的过程进行。 这种新体验还会在添加应用之前提供 "审阅" 页。 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“应用”   > “所有应用”   > “添加”  。 有关详细信息，请参阅[将应用添加到 Microsoft Intune](~/apps/apps-add.md)。

#### <a name="require-win32-apps-to-restart----3136567--"></a>需要 Win32 应用重启 <!-- 3136567-->
可以要求 Win32 应用在成功安装后重启。 此外，还可以选择在必须重新启动之前的时间量（宽限期）。

<!-- ***********************************************-->
## <a name="device-configuration"></a>设备配置

### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-idready---"></a>向 Android 企业工作配置文件的 Wi-fi 配置文件添加自动代理设置<!-- 4490822 idready -->
在 Android 企业工作配置文件设备上，可以创建 Wi-fi 配置文件。 选择 Wi-fi 企业类型时，还可以输入 Wi-fi 网络上使用的可扩展身份验证协议（EAP）类型。

在将来的更新中，当你选择 "企业类型" 时，你将能够输入自动代理设置，包括代理服务器 URL，如 `proxy.contoso.com`。

若要查看可配置的当前 Wi-fi 设置，请参阅[在 Microsoft Intune 中为运行 Android 企业版和 android 展台的设备添加 wi-fi 设置](../configuration/wi-fi-settings-android-enterprise.md)。

适用于：
- Android Enterprise 工作配置文件

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>适用于 macOS 设备的有线网络设备配置文件<!-- 3508686  -->
将提供一个新的 macOS 设备配置文件，该配置**文件用于配置**有线网络（**设备配置** > **配置**文件 > **创建配置**文件 > 用于平台 >**有线网络**的配置文件类型）。 使用此功能创建 802.1 x 配置文件来管理有线网络，并将这些有线网络部署到 macOS 设备。

适用于：
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-ios-devices----1947932-idready---"></a>具有 IKEv2 VPN 连接的 VPN 配置文件可对 iOS 设备使用 always on <!-- 1947932 idready -->
在 iOS 设备上，你可以创建一个 VPN 配置文件，该配置文件使用 IKEv2 连接（**设备配置** > **配置**文件 > **创建配置** **文件 > 用于**平台 > **VPN**的配置文件类型）。 在将来的更新中，可以使用 IKEv2 配置 always on。 配置后，IKEv2 VPN 配置文件会自动连接，并保持连接（或快速重新连接）到 VPN。 即使在网络之间移动或重新启动设备，它仍保持连接状态。

在 iOS 上，始终启用的 VPN 仅限 IKEv2 配置文件。

要查看当前可配置的 IKEv2 设置，请转到[在 iOS 设备上的 Microsoft Intune 中添加 VPN 设置](../configuration/vpn-settings-ios.md#ikev2-settings)。

适用于：
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-ios-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>改善了在 iOS 和 macOS 设备上创建配置文件时的用户界面体验<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
为 iOS 或 macOS 设备创建配置文件时，将更新终结点管理管理中心中的体验。 此更改会影响以下设备配置文件（**设备** > **配置文件** > **创建配置**文件 > **iOS**或平台的**macOS** ）：

- 自定义： iOS、macOS
- 设备功能： iOS、macOS
- 设备限制：iOS、macOS
- 终结点保护：macOS
- 扩展： macOS
- 首选项文件： macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-idready----"></a>改善了在 Android 企业设备上创建 OEMConfig 配置文件时的用户界面体验<!-- 5568645 idready  -->
当你创建或编辑适用于 Android 企业设备的 OEMConfig 配置文件时，会更新终结点管理管理中心中的体验。 更新的体验将提供已配置的设置的摘要。 此更改会影响 OEMConfig 设备配置文件（**设备** > **配置**文件 > **创建**配置文件 > **Android Enterprise** for platform > **OEMConfig**的配置文件类型）。

此功能适用于：
- Android Enterprise 

<!-- ***********************************************-->
## <a name="device-enrollment"></a>设备注册

### <a name="block-android-enrollments-by-device-manufacturer--5197392-idready--"></a>阻止设备制造商进行 Android 注册<!--5197392 idready-->
你将能够阻止设备根据设备制造商进行注册。 这适用于 Android 设备管理员和 Android 企业工作配置文件设备。 若要查看注册限制，请访问[Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)> **设备** > **注册限制**。



<!-- ***********************************************-->
## <a name="device-management"></a>设备管理


### <a name="new-information-in-device-details---4471759-5604099----"></a>设备详细信息中的新信息<!-- 4471759 5604099  -->
以下信息将添加到设备的 "**概述**" 页中：
- 内存容量（设备上的物理内存量）
- 存储容量（设备上的物理存储量） 
- CPU 处理器类型和速度
- RAM 和处理器数据

<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->

<!--
## Monitoring and troubleshooting
-->


<!-- ***********************************************-->
## <a name="role-based-access-control"></a>基于角色的访问控制

### <a name="new-intune-built-in-role-endpoint-security-manager--4253397-idready--"></a>新 Intune 内置角色终结点安全管理器<!--4253397 idready-->
新的 Intune 内置角色将可用：端点安全管理器。 此新角色使管理员能够完全访问 Intune 中的终结点管理器节点，并且仅可访问其他区域。 角色是 Azure AD 的 "安全管理员" 角色的扩展。 如果目前只有全局管理员角色，则无需进行任何更改。 如果你使用角色，并且想要终结点安全管理器提供的粒度，则在该角色可用时分配该角色。 有关内置角色的详细信息，请参阅[基于角色的访问控制](role-based-access-control.md)。

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Intune 角色用户界面更改即将发生<!--5801612 idready-->
用于[Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431) > **租户管理** > **角色**的用户界面将更改为用户友好和直观的设计。 此体验提供的设置和详细信息与你现在使用的相同，但是新体验采用类似于向导的过程。


<!-- ***********************************************-->
## <a name="security"></a>安全

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Android COBO 设备上的派生凭据支持<!--4839592-->
你将能够在 Android 企业完全托管的设备上使用派生凭据。 将包括支持，以便为 Entrust Datacard、调解和 DISA Purebred 检索派生凭据。 你将能够使用派生凭据进行应用身份验证、Wi-fi、VPN 或 S/MIME 签名，并/或对支持它的应用加密。 

<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。


