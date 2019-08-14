---
title: 开发过程中 - Microsoft Intune
titleSuffix: ''
description: 开发过程中的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 95eede7c62e728aa0dbade4478eb87f31c252558
ms.sourcegitcommit: a6775522df49d17a4125ccb31be395f2343bdae8
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2019
ms.locfileid: "68833551"
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

### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment----3504144---"></a>控制设备取消注册时的 iOS 应用卸载行为 <!-- 3504144 -->
当设备在用户或设备组级别上取消注册时, 管理员将能够管理是否在设备上删除或保留应用。 

### <a name="categorize-microsoft-store-for-business-apps----3926922---"></a>为适用于企业的 Microsoft Store 应用分类 <!-- 3926922 -->
你将能够为业务应用 Microsoft Store 分类。 为此, 请选择 **"**  > Intune  客户端应用 > 应用  >选择适用于企业应用 > 应用的 Microsoft Store信息   > 类别。  在下拉菜单中, 分配一个类别。
### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>为组织帐户配置应用通知内容 <!-- 2576686 -->
Android 和 iOS 设备上的 Intune 应用保护策略 (应用) 允许您控制组织帐户的应用通知内容。 此功能需要应用程序的支持, 可能无法用于所有启用应用的应用程序。 有关 APP 的详细信息，请参阅[什么是应用保护策略？](app-protection-policy.md)。

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>用于 Android 工作配置文件的可用 Google Play 应用报告 <!-- 3041956  -->
对于 Android 工作配置文件设备上的可用应用安装，可以查看应用安装状态以及托管的 Google Play 应用的安装版本。 有关详细信息，请查看[如何监视应用保护策略](app-protection-policies-monitor.md)、[使用 Intune 管理 Android 工作配置文件设备](android-enterprise-overview.md)和[托管的 Google Play 应用类型](apps-add-android-for-work.md#managed-google-play-app-type)。

<!-- ***********************************************-->
## <a name="device-configuration"></a>设备配置

### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release----4867809----"></a>某些无人监督的 iOS 设备限制将仅在 iOS 13.0 版本中受到监督 <!-- 4867809  -->
某些设置将适用于从 iOS 13.0 版开始的监督设备。 这些设置包括：

- App Store、文档查看和游戏
  - App Store
  - 显式 iTunes、音乐、播客或新闻内容
  - 添加 Game Center 好友
  - 多玩家游戏
- 内置应用
  - 照相机
    - FaceTime
  - Safari
    - 自动填充
- 云和存储
  - 备份到 iCloud
  - 阻止 iCloud 文档同步
  - 阻止 iCloud 密钥链同步

如果在 iOS 13.0 版本之前配置这些设置并将其分配给无人监督设备, 则这些设置仍适用于这些无人监督设备。 在设备升级到 iOS 13.0 后, 它们仍适用。 备份和还原的无人监督设备上会删除这些限制。 

要查看最新设置，请转到[使用 Intune 允许或限制功能的 iOS 设备设置](device-restrictions-ios.md)。

适用于：  
- iOS 13.0 及更高版本

### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices----4867699-4867709----"></a>新设置以及对现有设置的更改以限制 iOS 和 macOS 设备上的功能 <!-- 4867699 4867709  -->
你将能够创建配置文件以限制运行 iOS 和 macOS 的设备上的设置 **(设备**配置 >   文件 > **创建配置文件** > iOS  或macOS  的平台**类型 > 设备限制**)。 将添加以下功能：

- 在**macOS** > 设备限制   >   云和存储**中, 使用新的 "移交** " 设置来阻止用户在一个 macOS 设备上启动工作, 并继续在另一个 macOS 或 iOS 设备上工作。
  要查看最新设置，请转到[使用 Intune 允许或限制功能的 macOS 设备设置](device-restrictions-macos.md)。
- 在**iOS** > **设备限制**中, 有一些更改:
  - **内置**应用程序 >   查找我的 iPhone (仅限监督模式): 在 "查找我的应用" 功能中阻止此功能的新设置。 
  -  内置应用 >   查找朋友 (仅限监督的设备): 在 "查找我的应用" 功能中阻止此功能的新设置。 
  - **Wi-fi**状态的无线 > **修改 (仅限被监督的**设备): 阻止用户在设备上打开或关闭 wi-fi 的新设置。
  - **键盘和字典** >   QuickPath (仅限被监督的设备): 阻止 QuickPath 功能的新设置。
  - **云和存储**: **活动延续**会重命名**为**"提交"。

  要查看最新设置，请转到[使用 Intune 允许或限制功能的 iOS 设备设置](device-restrictions-ios.md)。

适用于：  
- macOS 10.15 和更高版本
- iOS 13 和更高版本

### <a name="control-the-apps-files-documents-and-folders-that-open-when-user-signs-in-to-macos-devices---3914202----"></a>控制用户登录 macOS 设备时打开的应用、文件、文档和文件夹 <!--3914202  -->
你将**能够在 macOS 设备上启用和配置功能 (设备配置** >    > 文件**创建配置文件**  > 配置文件类型的**平台 >** 设备功能的 macOS  )。 

将有新的登录项设置, 用于控制用户登录已注册设备时打开的应用、文件、文档和文件夹。 

若要查看当前设置，请转到 [Intune 中的 macOS 设备功能设置](macos-device-features-settings.md)。

适用于：  
- macOS

### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode----3755304-3041943-3041946----"></a>多应用模式下 Android 企业专用设备的新增功能 <!-- 3755304 3041943 3041946  -->
你将能够在 Android 企业专用设备上控制展台样式体验中的功能和设置。 为此, 请选择 **"设备** > **配置**文件" > "创建配置文件   > Android企业  "仅适用于  平台 > 设备所有者, 配置文件类型的设备限制。

将添加以下功能：
- **专用设备** > 多应用  :可通过在设备  上向上轻扫, 或在屏幕上浮动, 使用户可以移动虚拟主页按钮。
- **专用设备** > 多应用  :闪光灯访问  权限允许用户使用闪光灯。 
- **专用设备** > 多应用  :媒体音量  控制允许用户使用滑块控制设备的媒体音量。 
- **专用设备** >   多应用: 启用屏幕保护程序、上传自定义映像, 并控制何时显示屏幕保护程序。

要查看当前设置，请转到[便于使用 Intune 允许或限制功能的 Android Enterprise 设备设置](device-restrictions-android-for-work.md#dedicated-device-settings)。

适用于：  
- Android Enterprise 专用设备

### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices----3574215----"></a>适用于 Android 企业完全托管设备的新应用和配置文件 <!-- 3574215  -->
使用配置文件, 可以将设置应用于 Android 企业完全托管设备的 VPN、电子邮件和 Wi-fi 设置。 你将能够:
- 使用应用配置文件来部署 Outlook、Gmail 和9个工作电子邮件设置。
- 使用设备配置文件来部署受信任的根证书设置。
- 使用设备配置文件来部署 VPN 和 Wi-fi 设置。

用户将通过其用于 VPN、Wi-fi 和电子邮件配置文件的用户名和密码进行身份验证。 目前, 无法使用基于证书的身份验证。 

适用于：  
- Android Enterprise 完全托管设备

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>支持适用于 iOS 的 IKEv2 VPN 配置文件 <!-- 1943438 -->
可以使用 IKEv2 协议为 iOS 本机 VPN 客户端创建 VPN 配置文件。 IKEv2 是以下位置中的新连接类型：  “设备配置” >   “配置文件” > “创建配置文件”   > 平台为“iOS”  >配置文件类型为“VPN”  >“设置”  。

这些 VPN 配置文件配置本机 VPN 客户端。 因此，没有 VPN 客户端应用安装或推送到托管设备。 此功能要求设备在 Intune （MDM 注册）中注册。

要查看当前可配置的 VPN 设置，请转到[在 iOS 设备上的 Microsoft Intune 中配置 VPN 设置](vpn-settings-ios.md)。

适用于：iOS

<!-- ***********************************************-->
## <a name="device-enrollment"></a>设备注册

### <a name="skip-more-screens-in-setup-assistant---4877451---"></a>在设置助理中跳过更多屏幕 <!--4877451 -->
你将能够设置设备注册计划配置文件, 以跳过以下设置助理屏幕: 
- 屏幕时间
- Touch ID 设置

为此, 请使用 " **设备注册** >   " "Apple注册  >   " "注册计划令牌" > 选择令牌 >配置  文件 > 选择配置文件 **>** 属性 > "自**定义" 旁边**的 "编辑  "。
有关设置助理自定义的详细信息, [请参阅创建 Apple 注册](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile)配置文件。

### <a name="android-enrollment-device-administrator-support----4869749----"></a>Android 注册设备管理员支持 <!-- 4869749  -->
Android 设备管理员注册选项将添加到 android  注册页面 (Intune > **设备注册** > Android注册  )。 默认情况下, 将为所有租户启用 Android 设备管理员。  

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>对于 iOS 设备, 自定义公司门户的 "注册过程隐私" 屏幕 <!-- 4394993  -->
使用 markdown, 你可以自定义公司门户的隐私屏幕, 最终用户可以在 iOS 注册过程中看到这些屏幕。 具体而言, 你将能够自定义你的组织无法在设备上看到或执行的操作的列表。

<!-- ***********************************************-->
## <a name="device-management"></a>设备管理

### <a name="build-number-included-on-android-device-hardware-page----4461910----"></a>Android 设备硬件页面上包含的生成号 <!-- 4461910  -->
每个 Android 设备的 "硬件" 页上的新条目将包括设备的操作系统内部版本号。

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>将自动设备清理时间限制为减少到30天 <!--4231059  -->
在上次登录后, 你将能够将自动设备清理时间限制设置为短于30天 (而非当前限制为90天)。 为此, 请参阅 Intune > 设备 > 设置 > 设备清理规则。    

<!-- ***********************************************-->
## <a name="role-based-access-control"></a>基于角色的访问控制

### <a name="default-scope-tag----3702875---"></a>默认范围标记 <!-- 3702875 -->
新的内置默认范围标记将可用。 支持作用域标记的所有未标记的 Intune 对象将自动分配给默认作用域标记。 **默认**作用域标记将被添加到所有现有的角色分配, 以使与目前的管理体验保持一致。 如果你不希望管理员查看具有默认作用域标记的 Intune 对象, 请从角色分配中删除默认作用域标记。 此功能类似于 System Center Configuration Manager 中的安全作用域功能。

<!-- ***********************************************-->
## <a name="security"></a>安全

### <a name="import-and-export-security-baselines------3408610------------"></a>导入和导出安全基线    <!--3408610          -->  
我们添加的功能是导出和导入安全基线。 此功能可让你进行自定义并在 Intune 环境之间共享。

<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。




