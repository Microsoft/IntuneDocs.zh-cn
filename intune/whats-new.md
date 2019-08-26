---
title: Microsoft Intune 中的新增功能 - Azure | Microsoft Docs
titleSuffix: ''
description: 了解 Intune Azure 门户新增功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 267eb630b962893d5ab32530a095fe2fd3f7102e
ms.sourcegitcommit: cbd406e3c6ab8c9a29d58dfda4a18e34277a1594
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/19/2019
ms.locfileid: "69620214"
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune 新增功能

了解 Microsoft Intune 每周新增功能。 还可以找到[重要通知](#notices)、[过去版本](whats-new-archive.md)，以及有关[如何发布 Intune 服务更新](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728)的信息。 

> [!Note]
> 每个[每月更新](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728)可能需要长达三天才能推出，顺序如下：
> - 第 1 天：亚太地区 (APAC)
> - 第 2 天：欧洲、中东和非洲 (EMEA)
> - 第 3 天：北美
> 
> 某些功能可能会在数周内推出，第一周内可能不能供所有客户使用。
>
> 有关版本中即将推出的功能的列表，请查看[开发过程中页面](in-development.md)。

**RSS 源**：通过将以下 URL 复制并粘贴到源阅读器中，可以在页面更新时收到通知：`https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Device security
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->  

<!-- ########################## -->

## <a name="week-of-august-12-2019"></a>2019 年 8 月 12 日当周

### <a name="app-management"></a>应用管理

#### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment----3504144-----"></a>控制设备取消注册时的 iOS 应用卸载行为 <!-- 3504144   -->
管理员可以管理当设备在用户或设备组级别取消注册时，应用是被删除还是保留在设备上。 

#### <a name="categorize-microsoft-store-for-business-apps----3926922---"></a>为适用于企业的 Microsoft Store 应用分类 <!-- 3926922 -->
可以对适用于企业的 Microsoft Store 应用进行分类。 为此，请依次选择“Intune” > “客户端应用” > “应用”，选择适用于企业的 Microsoft Store 应用，再依次选择“应用信息” > “类别”。 在下拉菜单上，分配类别。

#### <a name="customized-notifications-for-microsoft-intune-app-users----4843354----"></a>面向 Microsoft Intune 应用用户的自定义通知 <!-- 4843354  -->
适用于 Android 的 Microsoft Intune 应用现在支持显示自定义推送通知，这与适用于 iOS 和 Android 的公司门户应用中最近新增的支持保持一致。 有关详细信息，请参阅[使用 Intune 发送自定义通知](custom-notifications.md)。

### <a name="device-configuration"></a>设备配置

#### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode----3755304-3041943-3041946-----"></a>新增了适用于多应用模式下 Android Enterprise 专用设备的功能 <!-- 3755304 3041943 3041946   -->
在 Intune 中，可以在 Android Enterprise 专用设备上通过展台样式体验来控制功能和设置（依次选择“设备配置” > “配置文件” > “创建配置文件” > “Android Enterprise”（作为平台）>“仅限设备所有者，设备限制”（作为配置文件类型））。

在此更新中，新增了以下功能：

- “专用设备” > “多应用”：虚拟主页按钮可以通过在设备上向上轻扫来显示，也可以悬浮在屏幕上，这样用户就可以移动它。
- “专用设备” > “多应用”：“闪光灯访问”允许用户使用闪光灯。 
- “专用设备” > “多应用”：“媒体音量控制”允许用户使用滑块控制设备的媒体音量。 
- “专用设备” > “多应用”：允许用户启用屏幕保护程序，上传自定义图像，并控制屏幕保护程序的显示时间。

要查看当前设置，请转到[便于使用 Intune 允许或限制功能的 Android Enterprise 设备设置](device-restrictions-android-for-work.md#dedicated-device-settings)。

适用于：  
- Android Enterprise 专用设备

#### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices----3574215-3574238-3574235-3574232-----"></a>新增了适用于 Android Enterprise 完全托管设备的应用配置文件 <!-- 3574215 3574238 3574235 3574232   -->
使用配置文件，可以配置设置，从而将 VPN、电子邮件和 Wi-Fi 设置应用于 Android Enterprise 设备所有者（完全托管）设备。 在此更新中，可以：

- 使用[应用配置策略](app-configuration-policies-use-android.md)来部署 Outlook、Gmail 和 Nine Work 电子邮件设置。
- 使用设备配置文件来部署[受信任的根证书设置](certificates-configure.md)。
- 使用设备配置文件来部署 [VPN](vpn-settings-android-enterprise.md) 和 [Wi-Fi](wi-fi-settings-android-enterprise.md) 设置。

> [!IMPORTANT]
> 利用此功能，用户可以使用 VPN、Wi-Fi 和电子邮件配置文件的用户名和密码进行身份验证。 目前，无法使用基于证书的身份验证。 

适用于：  
- Android Enterprise 设备所有者（完全托管）

#### <a name="control-the-apps-files-documents-and-folders-that-open-when-users-sign-in-to-macos-devices---3914202-----"></a>控制在用户登录 macOS 设备后打开哪些应用、文件、文档和文件夹 <!--3914202   -->
可以在 macOS 设备上启用和配置功能（依次选择“设备配置” > “配置文件” > “创建配置文件” > “macOS”（作为平台）>“设备功能”（作为配置文件类型））。 

在此更新中，新增了“登录项”设置，用于控制在用户登录注册的设备后打开哪些应用、文件、文档和文件夹。 

若要查看当前设置，请转到 [Intune 中的 macOS 设备功能设置](macos-device-features-settings.md)。

适用于：  
- macOS

#### <a name="deadlines-replace-engaged-restart-settings-for-windows-update-rings------4464404----------"></a>Windows 更新通道的“预定重启”设置替换为“截止时间”   <!-- 4464404        -->
为了与最近的 [Windows 服务变更](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1903#servicing)保持一致，Intune 的 Windows 10 更新通道现在[支持“截止时间”设置](windows-update-settings.md)。 “截止时间”确定设备何时安装功能和安全更新程序。  在运行 Windows 10 1903 或更高版本的设备上，“截止时间”取代“预定重启”配置。  未来在旧版 Windows 10 上，“截止时间”也会取代“预定重启”。  

如果你未配置“截止时间”，设备会继续使用“预定重启”设置，但在将来的更新中 [Intune 将会不支持“预定重启”设置](whats-new.md#plan-for-change-new-windows-updates-settings-in-intune-)。  

请计划对所有 Windows 10 设备使用“截止时间”。 在“截止时间”设置就位后，可以将 Intune 配置“预定重启”更改为“未配置”。 设置为“未配置”后，Intune 会停止管理设备上的这些设置，但不会从设备中删除上次配置的这些设置。 因此，上次配置的“预定重启”设置会继续处于活动状态并用于设备，直到这些设置被除 Intune 以外的其他方法修改。 稍后，当设备 Windows 版本发生更改时，或当 Intune 对“截止时间”的支持扩展到设备 Windows 版本时，设备就会开始使用已就位的新设置。

#### <a name="support-for-multiple-microsoft-intune-certificate-connectors--------4704642--------"></a>支持多个 Microsoft Intune 证书连接器   <!--   4704642      -->
Intune 现在支持安装和使用多个 [Microsoft Intune 证书连接器来执行 PKCS 操作](certficates-pfx-configure.md)。 此变更支持连接器的负载均衡和高可用性。 每个连接器实例都可以处理来自 Intune 的证书请求。  如果一个连接器不可用，其他连接器将继续处理请求。 

无需升级到最新版连接器软件，即可使用多个连接器。  

#### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices----4867699-4867709-----"></a>限制 iOS 和 macOS 设备上功能的新设置和现有设置变更 <!-- 4867699 4867709   -->
可以在运行 iOS 和 macOS 的设备上创建限制设置的配置文件（依次选择“设备配置” > “配置文件” > “创建配置文件” > “iOS”或“macOS”（作为平台）>“设备限制”）。 此更新包括以下功能：

- 依次转到“macOS” > “设备限制” > “云和存储”，使用新设置“移交”来阻止用户在一台 macOS 设备上启动工作，并继续在另一台 macOS 或 iOS 设备上工作。

  要查看最新设置，请转到[使用 Intune 允许或限制功能的 macOS 设备设置](device-restrictions-macos.md)。

- 依次转到“iOS” > “设备限制”，有下面的一些变更：

  - “内置应用” > “查找我的 iPhone (仅限受监督)”：“查找我的应用”功能中新增阻止此功能的设置。 
  - “内置应用” > “查找我的好友(仅限受监督)”：“查找我的应用”功能中新增阻止此功能的设置。 
  - “无线” > “修改 Wi-Fi 状态(仅限受监督)”：新增阻止用户在设备上打开或关闭 Wi-Fi 的设置。
  - “键盘和字典” > “QuickPath (仅限受监督)”：新增阻止 QuickPath 功能的设置。
  - “云和存储”：“活动延续”重命名为“移交”。

  要查看最新设置，请转到[使用 Intune 允许或限制功能的 iOS 设备设置](device-restrictions-ios.md)。

适用于：  
- macOS 10.15 及更高版本
- iOS 13 及更高版本

#### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release----4867809-----"></a>随着 iOS 13.0 版本推出，一些适用于不受监督的 iOS 设备的限制将适用于仅限受监督的设备 <!-- 4867809   -->
在此更新中，随着 iOS 13.0 版本推出，一些设置适用于仅限受监督的设备。 如果这些设置是在 iOS 13.0 版本推出前配置并分配到不受监督的设备，它们仍适用于不受监督的设备。 在设备升级到 iOS 13.0 后，它们仍适用。 这些限制不适用于已备份和还原的不受监督的设备。 

这些设置包括：

- App Store、文档查看和游戏
  - App Store
  - iTunes 限制级音乐、播客或新闻内容
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

要查看最新设置，请转到[使用 Intune 允许或限制功能的 iOS 设备设置](device-restrictions-ios.md)。

适用于：  
- iOS 13.0 及更高版本

#### <a name="improved-device-status-for-macos-filevault-encryption-----4944983-----------"></a>针对 macOS FileVault 加密改进了设备状态  <!-- 4944983         -->
我们针对 macOS 设备上的 FileVault 加密更新了[多个设备状态消息](encryption-monitor.md#device-encryption-status)。

#### <a name="some-windows-defender-antivirus-scan-settings-in-the-reporting-show-a-failed-status----5119229---"></a>报告中的一些 Windows Defender 防病毒扫描设置显示“失败”状态 <!-- 5119229 -->
在 Intune 中，可以创建使用 Windows Defender 防病毒来扫描 Windows 10 设备的策略（依次选择“设备配置” > “配置文件” > “创建配置文件” > “Windows 10 及更高版本”（作为平台）“设备限制”（作为配置文件类型）>“Windows Defender 防病毒”）。 “执行每日快速扫描的时间”和“要执行的系统扫描类型”报告显示“失败”状态（实际为“成功”状态）。 

在此更新中，这种行为得到了修复。 因此，“执行每日快速扫描的时间”和“要执行的系统扫描类型”设置在扫描成功完成后显示“成功”状态，并在无法应用设置时显示“失败”状态。 

若要详细了解 Windows Defender 防病毒设置，请参阅[使用 Intune 允许或限制功能的 Windows 10（及更高版本）设备设置](device-restrictions-windows-10.md#windows-defender-antivirus)。 

### <a name="device-enrollment"></a>设备注册

#### <a name="default-scope-tags----3702875----"></a>默认作用域标记 <!-- 3702875  -->
新增了内置默认作用域标记。 所有支持作用域标记的未标记 Intune 对象都会自动分配到默认作用域标记。 默认作用域标记添加到所有现有角色分配中，以与目前的管理员体验保持一致。 如果不想让管理员看到有默认作用域标记的 Intune 对象，请从角色分配中删除默认作用域标记。 此功能类似于 System Center Configuration Manager 中的安全作用域功能。 有关详细信息，请参阅[将 RBAC 和作用域标记用于分布式 IT](scope-tags.md)。

#### <a name="android-enrollment-device-administrator-support----4869749-----"></a>Android 注册设备管理员支持 <!-- 4869749   -->
Android 设备管理员注册选项已添加到“Android 注册”页（依次转到“Intune” > “设备注册” > “Android 注册”）。 默认情况下，所有租户仍将启用 Android 设备管理员。  有关详细信息，请参阅 [Android 设备管理员注册](android-enroll-device-administrator.md)。

#### <a name="skip-more-screens-in-setup-assistant---4877451----"></a>跳过设置助理中的更多屏幕 <!--4877451  -->
可以将设备注册计划配置文件设置为，跳过以下设置助理屏幕：
- 适用于 iOS
    - 外观
    - Express 语言
    - 首选语言
    - 设备间迁移
- 对于 macOS
    - 屏幕时间
    - Touch ID 设置

若要详细了解设置助理的自定义项，请参阅[创建适用于 iOS 的 Apple 注册配置文件](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile)和[创建适用于 macOS 的 Apple 注册配置文件](device-enrollment-program-enroll-macos.md#create-an-apple-enrollment-profile)。

#### <a name="add-a-user-column-to-the-autopilot-device-csv-upload-process----3823054---"></a>将用户列添加到 Autopilot 设备 CSV 上传过程 <!-- 3823054 -->
现在可以将用户列添加到 Autopilot 设备 CSV 上传内容中。 这样一来，就能在导入 CSV 时批量分配用户。 CSV 中行的新格式如下所示：序列号、Windows 产品 ID、硬件哈希、组标记（可选）、分配的用户（可选）。 有关详细信息，请参阅[在 Intune 中使用 Windows AutoPilot 注册 Windows 设备](enrollment-autopilot.md)。


### <a name="device-management"></a>设备管理

#### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>将自动设备清理时间限制配置缩短到 30 天 <!--4231059  -->
可以将自动设备清理时间限制设置为，上次登录后 30 天（而不是之前的 90 天限制）。 为此，请依次转到“Intune” > “设备” > “设置” > “设备清理规则”。

#### <a name="build-number-included-on-android-device-hardware-page----4461910-----"></a>Android 设备“硬件”页上包含生成号 <!-- 4461910   -->
每个 Android 设备的“硬件”页上都新增了包括设备操作系统生成号的条目。 有关详细信息，请参阅[使用 Intune 查看设备详细信息](device-inventory.md)。


<!-- ########################## -->

## <a name="week-of-august-5-2019"></a>2019 年 8 月 5 日当周

### <a name="zebra-technologies-is-a-supported-oem-for-oemconfig-on-android-enterprise-devices-----4843713---"></a>Zebra Technologies 是 Android Enterprise 设备上受支持的 OEMConfig OEM  <!-- 4843713 -->

在 Intune 中，可以创建设备配置文件，并使用 OEMConfig 将设置应用于 Android Enterprise 设备（依次选择“设备配置” > “配置文件” > “创建配置文件” > “Android Enterprise”（作为平台）>“OEMConfig”（作为配置文件类型））。

在此更新中，Zebra Technologies 是受支持的 OEMConfig 原始设备制造商 (OEM)。 若要详细了解 OEMConfig，请参阅[通过 OEMConfig 使用和管理 Android Enterprise 设备](android-oem-configuration-overview.md)。

适用于：  
- Android Enterprise

<!-- ########################## -->

## <a name="week-of-july-22-2019"></a>2019 年 7 月 22 日当周 

### <a name="app-management"></a>应用管理

#### <a name="customized-notifications-for-users-and-groups-------16766574------------"></a>发送给用户和组的自定义通知    <!-- 16766574          -->
从公司门户应用向使用 Intune 管理的 iOS 和 Android 设备上的用户发送自定义推送通知。 这些移动推送通知是高度可自定义的免费文本，可以用于任何目的。 可以将它们定目标到组织中的不同用户组。 有关详细信息，请参阅[自定义通知](custom-notifications.md)。

#### <a name="googles-device-policy-controller-app----3041950----"></a>Google 的 Device Policy Controller 应用 <!-- 3041950  -->
托管主屏幕应用现在可以访问 Google 的 Android 设备策略应用。 托管主屏幕应用是一种自定义启动器，用于使用多应用展台模式在 Intune 中注册为 Android Enterprise (AE) 专用设备的设备。 你可以访问 Android 设备策略应用，或引导用户访问 Android 设备策略应用，以获取支持和进行调试。 此启动功能在设备注册并锁定到托管主屏幕时可用。 无需其他安装项，即可使用此功能。

#### <a name="outlook-protection-settings-for-ios-and-android-devices----3212619---"></a>适用于 iOS 和 Android 设备的 Outlook 保护设置 <!-- 3212619 -->
现在可以使用简单的 Intune 管理控件，配置用于 Outlook for iOS 和 Outlook for Android 的常规应用配置设置和数据保护配置设置，而无需注册设备。 常规应用配置设置等同于，管理员在管理已注册设备上的 Outlook for iOS 和 Outlook for Android 时可以启用的设置。 若要详细了解 Outlook 设置，请参阅[部署 Outlook for iOS 和 Outlook for Android 应用配置设置](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)。

### <a name="device-configuration"></a>设备配置

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910-eeready---idstaged---"></a>在创建 Windows 10 设备配置配置文件时使用“适用性规则” <!-- 2549910 eeready   idstaged -->

可以创建 Windows 10 设备配置文件，具体方法为依次单击“设备配置” > “配置文件” > “创建配置文件” > “Windows 10”（作为平台）>“适用性规则”。 在此次更新中，可以创建适用性规则，让配置文件仅应用于特定版本。 例如，创建一个启用某些 BitLocker 设置的配置文件。 添加配置文件后，请使用适用性规则，使配置文件仅适用于运行 Windows 10 企业版的设备。

若要添加适用性规则，请参阅[适用性规则](device-profile-create.md#applicability-rules)。

适用于：Windows 10 及更高版本

#### <a name="use-tokens-to-add-device-specific-information-in-custom-profiles-for-ios-and-macos-devices----3330008----"></a>使用标记在 iOS 和 macOS 设备的自定义配置文件中添加设备专用信息 <!-- 3330008  -->
可以使用 iOS 和 macOS 设备上的自定义配置文件，配置没有内置到 Intune 中的设置和功能，具体方法为依次单击“设备配置” > “配置文件” > “创建配置文件” > “iOS”或“macOS”（作为平台）>“自定义”（作为配置文件类型）。 在此次更新中，你可以向 `.mobileconfig` 文件添加标记，用于添加设备专用信息。 例如，可以将 `Serial Number: {{serialnumber}}` 添加到配置文件，用于显示设备序列号。

若要创建自定义配置文件，请参阅 [iOS 自定义设置](custom-settings-ios.md)或 [macOS 自定义设置](custom-settings-macos.md)。

适用于：
- iOS
- macOS

#### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise----3712769-----"></a>在创建 Android Enterprise 的 OEMConfig 配置文件时使用新配置设计器 <!-- 3712769   -->
在 Intune 中，可以创建使用 OEMConfig 应用的设备配置文件，具体方法为依次单击“设备配置”>“配置文件”>“创建配置文件”>“Android Enterprise”（作为平台）>“OEMConfig”（作为配置文件类型）。 当你这样做时，系统会打开 JSON 编辑器，其中包含模板和值以供你更改。 

在此次更新中，我们新增了配置设计器，它的用户体验更佳，显示应用中嵌入的详细信息，包括标题、说明等。 JSON 编辑器仍可用，并显示你在配置设计器中所做的任何更改。

若要查看当前设置，请转到[通过 OEMConfig 使用和管理 Android Enterprise 设备](android-oem-configuration-overview.md)。

适用于：Android Enterprise

#### <a name="updated-ui-for-configuring-windows-hello-----4089576--------------"></a>更新了用于配置 Windows Hello 的 UI  <!-- 4089576            -->
我们更新了用于[将 Intune 配置为使用 Windows Hello 企业版](windows-hello.md)的控制台。 所有配置设置现在都位于用于启用支持 Windows Hello 的控制台的同一个窗格中。 


#### <a name="intune-powershell-sdk----4924113---"></a>Intune PowerShell SDK <!-- 4924113 --> 
通过 Microsoft Graph 支持 Intune API 的 Intune PowerShell SDK 已更新到版本 6.1907.1.0。 SDK 现在支持以下功能：
- 用于 Azure 自动化。
- 支持仅限应用的身份验证读取操作。 
- 支持将易记的缩短名称用作别名。
- 符合 PowerShell 命名约定。 具体而言，`Connect-MSGraph` cmdlet 上的 `PSCredential` 参数已重命名为 `Credential`。
- 支持在使用 `Invoke-MSGraphRequest` cmdlet 时手动指定 `Content-Type` 标头的值。

有关详细信息，请参阅[用于 Microsoft Intune Graph API 的 PowerShell SDK](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune)。


### <a name="device-enrollment"></a>设备注册

#### <a name="updates-for-enrollment-restrictions-----2871968---"></a>更新了注册限制  <!-- 2871968 -->
新租户的注册限制已更新为，默认允许 Android Enterprise 工作配置文件。 现有租户不会有任何变化。 若要使用 Android Enterprise 工作配置文件，仍需[将 Intune 帐户连接到托管的 Google Play 帐户](https://docs.microsoft.com/intune/connect-intune-android-enterprise)。

#### <a name="ui-updates-for-apple-enrollment-and-enrollment-restrictions---4089575-4089579----"></a>更新了用于 Apple 注册和注册限制的 UI <!--4089575, 4089579  -->
以下两个过程都使用向导样式的用户界面：
- Apple 设备注册。 有关详细信息，请参阅[通过 Apple 设备注册计划自动注册 iOS 设备](device-enrollment-program-enroll-ios.md)。
- 注册限制创建。 有关详细信息，请参阅[创建注册限制](enrollment-restrictions-set.md)。

#### <a name="handling-pre-configuration-of-corporate-device-identifiers-for-android-q-devices----4711509--idmiss---"></a>处理如何预配置 Android Q 设备的企业设备标识符 <!-- 4711509  idmiss -->
在 Android Q (v10) 中，Google 将撤消旧版托管（设备管理员）Android 设备上的 MDM 代理收集设备标识符信息的功能。  Intune 有一项功能，可便于 IT 管理员[预配置设备序列号或 IMEI 列表](https://docs.microsoft.com/intune/corporate-identifiers-add#identify-corporate-owned-devices-with-imei-or-serial-number)，以便自动将这些设备标记为企业所有。 此功能不适用于由设备管理员托管的 Android Q 设备。  无论设备的序列号或 IMEI 是否已上传，设备在 Intune 注册过程中始终被视为个人设备。  注册后，可以手动将所有权切换给企业。  这只影响新注册，而现有已注册设备则不受影响。  使用工作配置文件托管的 Android 设备不受此更改的影响，并将继续按目前的方式运行。  另外，注册为设备管理员的 Android Q 设备无法再将 Intune 控制台中的序列号或 IMEI 作为设备属性进行报告。

#### <a name="icons-have-changed-for-android-enterprise-enrollments-work-profile-dedicated-devices-and-fully-managed-devices----4977730---"></a>更改了用于 Android Enterprise 注册（工作配置文件、专用设备和完全托管设备）的图标 <!-- 4977730 -->
Android Enterprise 注册配置文件的图标已更改。 若要查看新图标，请先依次转到“Intune” > “注册” > “Android 注册”，再查看“注册配置文件”下。


#### <a name="windows-diagnostic-data-collection-change----4113859---"></a>更改了 Windows 诊断数据收集 <!-- 4113859 -->
对于运行 Windows 10 版本 1903 及更高版本的设备，用于诊断数据收集的默认值已更改。 自 Windows 10 1903 起，诊断数据收集默认启用。 Windows 诊断数据是来自 Windows 设备的至关重要技术数据，包含设备相关信息以及 Windows 和相关软件的性能。 有关详细信息，请参阅[配置组织中的 Windows 诊断数据](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization)。 Autopilot 设备也选择启用“全”遥测，除非在 Autopilot 配置文件中使用 [System/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry) 进行了其他设置。

### <a name="device-management"></a>设备管理

#### <a name="improve-device-location---3855417----"></a>改进了设备位置<!-- 3855417  -->
可以使用“定位设备”操作来放大到设备的确切坐标。 若要详细了解如何定位丢失的 iOS 设备，请参阅[查找丢失的 iOS 设备](device-locate.md)。


### <a name="device-security"></a>设备安全性

#### <a name="advanced-settings-for-windows-defender-firewall--public-preview------1311949-------"></a>Windows Defender 防火墙（公共预览版）的高级设置  <!--  1311949     -->  
使用 Intune 管理[作为设备配置文件一部分的自定义防火墙规则](endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices)，以在 Windows 10 设备上实现终结点保护。 规则可以指定应用程序、网络地址和端口的入站和出站行为。 

#### <a name="updated-ui-for-managing-security-baselines------4091125-------"></a>更新了用于管理安全基线的 UI   <!-- 4091125     -->
我们在 Intune 控制台中更新了安全基线的[创建和编辑体验](security-baselines.md#create-the-profile)。 具体更改包括：

简化了向导样式格式，已压缩为一个边栏选项卡 。 这项新设计杜绝了边栏选项卡扩张，IT 专业人员不再需要向下钻取多个单独的窗格。  
现在可以在创建和编辑基线的过程中创建分配，而不必稍后返回来分配基线。 我们添加了设置摘要，你可以在新建基线和编辑现有基线前查看。 编辑时，摘要只显示正在编辑的一个属性类别中设置的项列表。



<!-- ########################## -->

## <a name="week-of-july-15-2019"></a>2019 年 7 月 15 日当周 

### <a name="app-management"></a>应用管理

#### <a name="managed-home-screen-and-managed-settings-icons----4918107---"></a>Managed Home Screen 应用图标和“托管设置”图标 <!-- 4918107 -->
Managed Home Screen 应用图标和“托管设置”图标已更新。 Managed Home Screen 应用仅用于，在 Intune 中注册为 Android Enterprise (AE) 的专用设备，且在多应用展台模式下运行的设备。 若要详细了解 Managed Home Screen 应用，请参阅[配置用于 Android Enterprise 的 Microsoft Managed Home Screen 应用](app-configuration-managed-home-screen-app.md)。

#### <a name="android-device-policy-on-android-enterprise-dedicated-devices----4918136---"></a>Android Enterprise 专用设备上的 Android Device Policy <!-- 4918136 -->
可以从 Managed Home Screen 应用的调试屏幕访问 Android Device Policy 应用。 Managed Home Screen 应用仅用于，在 Intune 中注册为 Android Enterprise (AE) 的专用设备，且在多应用展台模式下运行的设备。 有关详细信息，请参阅[配置用于 Android Enterprise 的 Microsoft Managed Home Screen 应用](app-configuration-managed-home-screen-app.md)。

#### <a name="ios-company-portal-updates----3902931---"></a>更新了 iOS 公司门户 <!-- 3902931 -->
iOS 应用管理提示中的公司名称将替换当前的“i.manage.microsoft.com”文本。 例如，当尝试从公司门户安装 iOS 应用或允许管理应用时，用户将看到公司名称，而不是“i.manage.microsoft.com”。 这将在未来几天内向所有客户推出。

### <a name="device-configuration"></a>设备配置

#### <a name="manage-filevault-for-macos-------3858502--4557986--1210104----"></a>管理用于 macOS 的 FileVault   <!--  3858502 + 4557986 + 1210104  -->
可以使用 Intune [管理用于 macOS 设备的 FileVault 密钥加密](encrypt-devices.md)。 若要加密设备，请使用终结点保护设备配置文件。

我们对 FileVault 的支持包括，加密未加密设备、托管设备个人恢复密钥、自动或手动轮换个人加密密钥，以及检索企业设备密钥。 最终用户还可以使用公司门户网站来获取加密设备的个人恢复密钥。 

我们还扩展了加密报告，增加了 [FileVault 相关信息](encryption-monitor.md)以及 BitLocker 相关信息，这样你就可以在一个地方集中查看所有设备加密详细信息了。 

### <a name="device-enrollment"></a>设备注册

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user----4156123---"></a>Windows Autopilot 重置导致设备的主要用户遭删除 <!-- 4156123 -->
如果设备使用 Autopilot 重置，设备的主要用户将会遭删除。 在重置后登录的下一个用户将被设置为主要用户。 此功能将在未来几天内向所有客户推出。

## <a name="week-of-july-8-2019"></a>2019 年 7 月 8 日当周

### <a name="new-office-windows-and-onedrive-settings-in-windows-10-administrative-templates----3510695---"></a>Windows 10 管理模板中新增 Office、Windows 和 OneDrive 设置 <!-- 3510695 -->

可以在 Intune 中创建模拟本地组策略管理的管理模板，具体方法为依次单击“设备管理” > “配置文件” > “创建配置文件” > “Windows 10 及更高版本”（作为平台）>“管理模板”（作为配置文件类型）。

在此次更新中，我们新增了更多可添加到模板中的 Office、Windows 和 OneDrive 设置。 现在，利用这些新设置，可以配置超过 2500 项完全基于云的设置。

若要详细了解此功能，请参阅[使用 Windows 10 模板在 Intune 中配置组策略设置](administrative-templates-windows.md)。

适用于：Windows 10 及更高版本

## <a name="week-of-july-1-2019"></a>2019 年 7 月 1 日当周 

### <a name="app-management"></a>应用管理

#### <a name="aad-and-app-on-android-enterprise-devices----3574267---"></a>Android Enterprise 设备上的 AAD 和 APP <!-- 3574267 -->
上手使用完全托管 Android Enterprise 设备时，用户现在初始设置新设备或恢复出厂设置的设备期间向 Azure Active Directory (AAD) 注册。 之前，对于完全托管设备，在设置完成后，用户必须手动启动 Microsoft Intune 应用，才能启动 AAD 注册过程。 现在，当用户在初始设置后登陆设备主页时，设备就已注册。

除了更新了 AAD 之外，现在还支持在完全托管 Android Enterprise 设备上运行 Intune 应用保护策略 (APP)。 此功能将在我们推出后可用。有关详细信息，请参阅[使用 Intune 将托管 Google Play 应用添加到 Android Enterprise 设备](apps-add-android-for-work.md)。

## <a name="week-of-june-24-2019"></a>2019 年 6 月 24 日的这一周 

### <a name="app-management"></a>应用管理

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data----3145939---"></a>配置允许哪种浏览器链接到组织数据 <!-- 3145939 -->
现在，借助 Android 和 iOS 设备上的 Intune 应用保护策略 (APP)，可以将 Org web 链接转移到特定浏览器，而不仅仅是 Intune Managed Browser 和 Microsoft Edge。  有关 APP 的详细信息，请参阅[什么是应用保护策略？](app-protection-policy.md)。

#### <a name="all-apps-page-identifies-onlineoffline-microsoft-store-for-business-apps--4089647---"></a>“所有应用”页标识适用于企业的 Microsoft Store 联机/脱机应用<!--4089647 -->
“所有应用”页现在包含标签，用于将适用于企业的 Microsoft Store (MSFB) 应用识别为联机或脱机应用。 每个 MSFB 应用现在都包含“Online”或“Offline”后缀。 应用详细信息页还包含“许可证类型”和“支持设备上下文安装”（仅限脱机许可应用）信息。

#### <a name="company-portal-app-on-windows-shared-devices---4393553---"></a>Windows 共享设备上的公司门户应用 <!--4393553 -->
用户现在可以在 Windows 共享设备上访问公司门户应用。 最终用户会在设备磁贴上看到“共享”标签。 这适用于 Windows 公司门户应用版本 10.3.45609.0 及更高版本。

#### <a name="view-all-installed-apps-from-new-company-portal-web-page----4224326---"></a>从新版公司门户网页查看所有已安装应用 <!-- 4224326 -->
公司门户网站的新增“已安装应用”页面将列出用户设备上安装的所有（要求安装和允许安装的）托管应用。 除了分配类型，用户还可以看到应用的发布者、发布日期和当前安装状态。 如果你并未要求或允许用户安装任何应用，则用户将看到一条消息，说明尚未安装任何公司应用。 若要在 Web 上查看新页面，请转到[公司门户网站](https://portal.manage.microsoft.com)，并单击“已安装应用”。  

#### <a name="new-view-lets-app-users-see-all-managed-apps-installed-on-device----2352913---"></a>新增视图，可相应用用户显示设备上安装的所有托管应用 <!-- 2352913 -->  
现在，适用于 Windows 的公司门户应用将列出用户设备上安装的所有（要求安装和允许安装的）托管应用。 用户还可以看到已尝试和待处理的应用安装及其当前状态。 如果你并未要求或允许用户安装应用，则用户将看到一条消息，说明尚未安装任何公司应用。 若要查看新视图，请转到公司门户的导航窗格，并选择“应用” > “已安装应用”。    

### <a name="device-configuration"></a>设备配置

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>在 macOS 设备上配置内核扩展的设置 <!-- 2043024 -->
在 macOS 设备上，可以创建设备配置文件（依次选择“设备配置” > “配置文件” > “创建配置文件”> 针对平台选择“macOS”）。 在此次更新中，我们新增了一组设置，可便于你在设备上配置和使用内核扩展。 你可以添加特定扩展，也可以允许来自特定合作伙伴或开发人员的所有扩展。

若要详细了解此功能，请参阅[内核扩展概述](kernel-extensions-overview-macos.md)和[内核扩展设置](kernel-extensions-settings-macos.md)。

适用于：10.13.2 及更高版本

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options----2697002---"></a>来自 Windows 10 设备的“仅 Store”设置的应用包括更多配置选项。 <!-- 2697002 -->
为 Windows 设备创建设备限制配置文件时，可以使用“仅来自 Store 的应用”设置，使用户仅从 Windows 应用商店安装应用（“设备配置” > “配置文件” > “创建配置文件” > 平台为“Windows 10 和更高版本”>配置文件类型为“设备限制”）。 在此次更新中，我们扩展了这项设置，以支持更多选项。 

若要查看新设置，请转到[允许或限制功能的 Windows 10（及更高版本）设备设置](device-restrictions-windows-10.md#app-store)。

适用于：Windows 10 及更高版本

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group----4089955---"></a>将多个 Zebra 移动扩展设备配置文件部署到一台设备、同一用户组或同一设备组 <!-- 4089955 -->
在 Intune 中，可以使用设备配置文件中的 Zebra 移动性扩展 (MX)，为 Zebra 设备自定义没有内置到 Intune 中的设置。 目前，可以将一个配置文件部署到一台设备。 在此次更新中，你可以将多个配置文件部署到：
- 同一用户组
- 同一设备组
- 一台设备

[通过 Microsoft Intune 中的 Zebra 移动扩展来使用和管理 Zebra 设备](android-zebra-mx-overview.md)显示了如何在 Intune 中使用 MX。

适用于：Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow----4404075----"></a>iOS 设备上的一些展台设置是使用“阻止”（替代“允许”）设置的 <!-- 4404075  -->
在 iOS 设备上创建设备限制配置文件时（“设备配置” > “配置文件” > “创建配置文件” > 平台为“iOS”>配置文件类型为“设备限制”>“展台”），可以设置“自动锁定”、“响铃切换”、“屏幕旋转”、“屏幕睡眠按钮”和“音量按钮”。 

在此次更新中，值是“阻止”（阻止此功能）或“未配置”（允许此功能）。 若要查看设置，请转到[允许或限制功能的 iOS 设备设置](device-restrictions-ios.md#kiosk-supervised-only)。 

适用于：iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices----4490704---"></a>在 iOS 设备上使用人脸 ID 进行密码身份验证 <!-- 4490704 -->
创建用于 iOS 设备的设备限制配置文件时，可将指纹用作密码。 在此次更新中，指纹密码设置还允许面部识别，具体方法为依次单击“设备配置” > “配置文件” > “创建配置文件” > “iOS”（作为平台）>“设备限制”（作为配置文件类型）>“密码”。 因此，更改了以下设置：

- “指纹解锁”现在更改为“Touch ID 和 Face ID 解锁”。
- 指纹修改（仅限监管模式）现在更改为“Touch ID 和 Face ID 修改（仅限监管模式）”。

Face ID 可在 iOS 11.0 和更高版本中使用。 若要查看设置，请转到[使用 Intune 允许或限制功能的 iOS 设备设置](device-restrictions-ios.md#password)。

适用于：iOS

#### <a name="restricting-gaming-and-app-store-features-on-ios-devices-is-now-dependent-on-ratings-region----4593948---"></a>限制 iOS 设备上的游戏和应用商店功能现在取决于分级区域 <!-- 4593948 -->
在 iOS 设备上，可以允许或限制与游戏、应用商店和查看文档相关的功能（“设备配置” > “配置文件” > “创建配置文件” >  平台为“iOS”> 配置文件类型为“设备限制”>“应用商店、文档查看、游戏”）。 此外还可以选择分级区域，例如美国。 

在此次更新中，“应用”功能更改为“分级区域”的子级，且依赖“分级区域”。 若要查看设置，请转到[使用 Intune 允许或限制功能的 iOS 设备设置](device-restrictions-ios.md#app-store-doc-viewing-gaming)。

适用于：iOS

### <a name="device-enrollment"></a>设备注册

#### <a name="windows-autopilot-support-for-hybrid-azure-ad-join----4809146--"></a>Windows Autopilot 支持混合 Azure AD 联接 <!-- 4809146-->
除了现有的 Azure AD 联接支持之外，现有设备的 Windows Autopilot 现在还支持混合 Azure AD 联接。 适用于运行 Windows 10 版本 1809 及更高版本的设备。 有关详细信息，请参阅[现有设备的 Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices)。



### <a name="device-management"></a>设备管理

#### <a name="see-the-security-patch-level-for-android-devices----4461911---"></a>查看 Android 设备的安全修补程序级别 <!-- 4461911 -->
现在可以查看 Android 设备的安全修补程序级别。 为此，请先依次选择“Intune” > “设备” > “所有设备”，再选择设备和“硬件”。
此时，“操作系统”部分列出了修补程序级别。

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group----3173810---"></a>将范围标记分配给安全组中的所有托管设备 <!-- 3173810 -->
现在可以将范围标记分配给安全组，安全组中的所有设备也会与这些范围标记关联。 这些组中的所有设备也将分配有范围标记。 使用此功能设置的范围标记将覆盖使用当前设备范围标记流设置的范围标记。 有关详细信息，请参阅[将 RBAC 和范围标记用于分布式 IT](scope-tags.md)。

### <a name="device-security"></a>设备安全性

#### <a name="use-keyword-search-with-security-baselines-------"></a>对安全基线使用关键字搜索 <!--  -->
创建或编辑[安全基线配置文件](security-baselines.md#create-the-profile)时，可以在新“搜索”栏中指定关键字，以从可用设置组中筛选出与搜索条件匹配的设置组。 

#### <a name="the-security-baselines-feature-is-now-generally-available-----3785395---"></a>安全基线功能现已推出正式版  <!-- 3785395 -->
安全基线功能已不再处于预览阶段，现已推出正式版 (GA)。  也就是说，此功能可供在生产中使用。 不过，各个基线模板可能仍处于预览阶段，并按自己的计划接受评估并推出正式版。

#### <a name="the-mdm-security-baseline-template-is-now-generally-available------3794072-4217151--3534649---"></a>MDM 安全基线模板现已推出正式版   <!-- 3794072, 4217151,  3534649 -->
MDM 安全基线模板已不再处于预览阶段，现已推出正式版 (GA)。 此 GA 模板的标识为“2019 年 5 月 MDM 安全基线”。  这是新模板，而不是从预览版升级的模板。  由于它是新模板，你需要先审阅[它包含的设置](security-baseline-settings-windows.md)，再新建将此模板部署到设备的配置文件。 其他安全基线模板可能仍处于预览阶段。 有关可用基线的列表，请参阅[可用安全基线](security-baselines.md#available-security-baselines)。  

“2019 年 5 月 MDM 安全基线”除了是新模板之外，还包含我们最近在开发文章中公布的两项设置：  
- 越过锁定：语音激活屏幕锁定的应用  
- DeviceGuard：在下次重启设备时使用基于虚拟化的安全性 (VBS)。  

“2019 年 5 月 MDM 安全基线”还新增了几项新设置，删除了其他一些设置，并修订了一项设置的默认值。 有关从预览版到 GA 的更改的详细列表，请参阅“新模板中发生了什么变化”。

#### <a name="security-baseline-versioning-----3194322---"></a>安全基线版本控制  <!-- 3194322 -->
用于 Intune 的安全基线支持版本控制。 借助此支持，在每个安全基线的新版本发布时，可以将现有安全基线配置文件更新为使用更高版本的基线，而无需从头开始重新创建和部署新基线。 此外，在 Intune 控制台中，还可以查看每个基线的相关信息，如使用基线的各个配置文件的数量、配置文件使用的不同基线版本的数量，以及特定安全基线的最新版本的发布时间。  有关详细信息，请参阅**安全基线**。

#### <a name="the-use-security-keys-for-sign-in-setting-has-moved-----4501151---"></a>“使用安全密钥登录”设置已移动  <!-- 4501151 -->
用于标识保护的设备配置设置“使用安全密钥登录”不再是“配置 Windows Hello 企业版”的子设置。 它现在是始终可用的顶级设置，即使你没有启用 Windows Hello 企业版，也不例外。 有关详细信息，请参阅[标识保护](identity-protection-windows-settings.md)。

### <a name="role-based-access-control"></a>基于角色的访问控制

#### <a name="new-permissions-for-assigned-group-admins------4504437-----"></a>新增了已分配的组管理员的权限   <!-- 4504437   -->
Intune 的内置学校管理员角色现在对托管应用拥有创建、读取、更新和删除 (CRUD) 权限。 也就是说，在此次更新中，如果你在 Intune for Education 中被分配为组管理员，现在可以创建、查看、更新和删除 iOS MDM Push Certificate、iOS MDM 服务器令牌和 iOS VPP 令牌，此外还拥有[所有现有权限](https://docs.microsoft.com/intune-education/group-admin-delegate#group-admin-permissions)。 若要执行其中任何一项操作，请依次转到“租户设置” > “iOS 设备管理”。  

#### <a name="applications-can-use-the-graph-api-to-call-read-operations-without-user-credentials----4655885---"></a>应用可以使用 Graph API 来调用读取操作，而无需使用用户凭据 <!-- 4655885 -->
应用可以通过应用标识来调用 Intune Graph API 读取操作，而无需使用用户凭据。 若要详细了解如何访问用于 Intune 的 Microsoft Graph API，请参阅[在 Microsoft Graph 中使用 Intune](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)。

#### <a name="apply-scope-tags-to-microsoft-store-for-business-apps----4392555---"></a>将范围标记应用于适用于企业的 Microsoft Store 应用 <!-- 4392555 -->
现在可以将范围标记应用于适用于企业的 Microsoft Store 应用。 若要详细了解范围标记，请参阅[将基于角色的访问控制 (RBAC) 和范围标记用于分布式 IT](scope-tags.md)。

## <a name="week-of-june-17-2019"></a>2019 年 6 月 17 日当周 

### <a name="app-management"></a>应用管理

#### <a name="new-features-in-microsoft-intune-app"></a>Microsoft Intune 应用中的新功能
我们已向适用于 Android 的 Microsoft Intune 应用（预览版）添加新功能。 完全托管的 Android 设备上的用户现在可以：  

* 查看和管理通过 Intune 公司门户或 Microsoft Intune 应用注册的设备。    
* 联系他们的组织以获取支持。    
* 向 Microsoft 发送反馈。    
* 如果组织已制定相关条款和条件，请进行查阅。    

## <a name="week-of-june-10-2019"></a>2019 年 6 月 10 日当周 

### <a name="app-management"></a>应用管理

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github----2653471---"></a>显示 GitHub 上提供的 Intune SDK 集成的新示例应用 <!-- 2653471 -->
msintuneappsdk GitHub 帐户新增了适用于 iOS (Swift)、Android、Xamarin.iOS、Xamarin Forms 和 Xamarin.Android 的示例应用。 这些应用旨在补充现有文档并演示如何将 Intune APP SDK 集成到自己的移动应用中。 如果你是需要其他 Intune SDK 指南的应用开发人员，请参阅以下链接示例：
- [Chatr](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App) - 使用 Azure Active Directory 身份验证库 (ADAL) 进行中转身份验证的本机 iOS (Swift) 即时消息应用。
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App) - 使用 ADAL 进行中转身份验证的本机 Android 待办事项列表应用。
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps) - 使用 ADAL 进行代理身份验证的 Xamarin.Android 待办事项列表应用，此存储库还具有 Xamarin.Forms 应用。
- [Xamarin.iOS 示例应用](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) - 基本 Xamarin.iOS 示例应用。

## <a name="week-of-may-27-2019"></a>2019 年 5 月 27 日当周 

### <a name="app-management"></a>应用管理

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices----4223162---"></a>报告 Android 设备上可能有害的应用 <!-- 4223162 -->
Intune 现在提供有关 Android 设备上可能有害的应用的其他报告信息。 

## <a name="week-of-may-20-2019"></a>2019 年 5 月 20 日当周 

### <a name="app-management"></a>应用管理

#### <a name="windows-company-portal-app----3316993---"></a>Windows 公司门户应用 <!-- 3316993 -->
Windows 公司门户应用将具有一个标记为“设备”的新页面。 “设备”页面将显示最终用户已注册的所有设备。 在用户使用 10.3.4291.0 或更高版本时，公司门户中将显示此更改。 要了解如何配置公司门户，请参阅[如何配置 Microsoft Intune 公司门户应用](company-portal-app.md)。

### <a name="device-enrollment"></a>设备注册

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Autopilot 设备的 OrderID 属性名称已更改为“组标记” <!-- 4659453 -->

为更直观地显示，Autopilot 设备上的 OrderID 属性名称已更改“组标记”。 在使用 CSV 上传 Autopilot 设备信息时，必须使用“组标记”而不是 OrderID 作为列标题。  

## <a name="week-of-may-13-2019"></a>2019 年 5 月 13 日当周 

### <a name="app-management"></a>应用管理

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359----"></a>Intune 策略更新身份验证方法和公司门户应用安装  <!-- 1927359  -->
在已通过 Apple 公司设备注册方法之一经由“设置助理”注册的设备上，Intune 将不再支持由最终用户从应用商店手动安装的公司门户。 仅当在注册过程中使用 Apple 设置助理进行身份验证时，此更改才适用。 此更改也只会影响通过以下方式注册的 iOS 设备：  
* Apple 配置器

* Apple Business Manager

* Apple School Manager

* Apple 设备注册计划 (DEP)

如果用户从应用商店安装公司门户应用，然后尝试通过该应用注册这些设备，则他们将收到错误。 在注册过程中由 Intune 自动推送公司门户时，这些设备应仅使用公司门户。 将更新 Azure 门户中的 Intune 注册配置文件，以便你可以指定设备的身份验证方式以及是否收到公司门户应用。 如果希望 DEP 设备用户具有公司门户，则需要在注册配置文件中指定你的首选项。 

此外，iOS 公司门户中的“标识设备”屏幕将被删除。 因此，想要启用条件访问或部署公司应用的管理员必须更新 DEP 注册配置文件。 仅当使用设置助理对 DEP 注册进行身份验证时，此要求才适用。 在这种情况下，必须将公司门户推送到设备上。 为此，请选择“Intune” > “设备注册” > “Apple 注册” > “注册计划令牌”，依次选择令牌和“配置文件”，选择配置文件，再选择“属性”，然后将“安装公司门户”设置为“是”。

若要在已注册的 DEP 设备上安装公司门户，需要转到“Intune”>“客户端应用”，并将其作为具有应用配置策略的托管应用进行推送。 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy----3568384---"></a>配置最终用户使用应用保护策略更新业务线 (LOB) 应用的方式 <!-- 3568384 -->
用户现在可以配置最终用户可获取业务线 (LOB) 应用的更新版本的位置。 最终用户将在“最低应用版本”条件启动对话框中看到此功能，系统将提示最终用户更新到 LOB 应用的最低版本。 必须提供这些更新详细信息作为 LOB 应用保护策略（应用）的一部分。 此功能在 iOS 和 Android 中可用。 在 iOS 上，此功能要求应用与 Intune SDK for iOS v. 10.0.7 或更高版本集成（或使用包装工具包装）。 在 Android 上，此功能需要使用最新的公司门户。 若要配置最终用户更新 LOB 应用的方式，应用需要使用键 `com.microsoft.intune.myappstore` 发送给它的托管应用配置策略。 发送的值将定义最终用户从哪个应用商店中下载应用。 如果应用是通过公司门户部署的，则值必须为 `CompanyPortal`。 对于任何其他应用商店，必须输入完整的 URL。

#### <a name="intune-management-extension-powershell-scripts-----3734186----"></a>Intune 管理扩展 PowerShell 脚本  <!-- 3734186  -->
用户可以在设备上配置使用用户的管理员权限运行的 PowerShell 脚本。 有关详细信息，请参阅[在 Intune 中的 Windows 10 设备上使用 PowerShell 脚本](intune-management-extension.md)和 [Win32 应用管理](apps-win32-app-management.md)。

#### <a name="android-enterprise-app-management----4459905---"></a>Android Enterprise 应用管理 <!-- 4459905 -->
Intune 将自动向 Intune 管理控制台添加四个常见的与 Android Enterprise 相关的应用，以便 IT 管理员可以轻松配置和使用 Android Enterprise 管理。 这四个 Android Enterprise 应用如下所示：

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - 用于 Android Enterprise 完全托管方案。
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** - 帮助你使用双因素身份验证登录帐户。
- **[Intune 公司门户](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - 用于应用保护策略 (APP) 和 Android Enterprise 工作配置文件方案。
- [托管的主屏幕](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) - 用于 Android Enterprise 专用/展台方案。

在过去，IT 管理员需要在设置过程中从[托管的 Google Play 商店](https://play.google.com/store/apps)手动查找并批准这些应用。 此更改消除了这些以前的手动步骤，客户可以更轻松快速地使用 Android Enterprise 管理。

当管理员首次将 Intune 租户连接到托管的 Google Play 时，他们将看到已自动添加到其 Intune 应用列表的这四个应用。 有关详细信息，请参阅[如何将 Intune 帐户连接到托管的 Google Play 帐户](connect-intune-android-enterprise.md)。 对于已连接其租户或已使用 Android Enterprise 的租户，管理员无需执行任何操作。 这四个应用将在 2019 年 5 月服务推出结束后的 7 天内自动显示。

### <a name="device-configuration"></a>设备配置

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune-----1533038---"></a>更新了 Microsoft Intune 的 PFX 证书连接器  <!-- 1533038 -->
我们已发布[用于 Microsoft Intune 的 PFX 证书连接器](certficates-pfx-configure.md#whats-new-for-connectors)的更新，该更新解决了以下问题：因现有 PFX 证书持续重新处理而导致连接器停止处理新请求。

#### <a name="intune-security-tasks-for-defender-atp-in-public-preview--------3208597---"></a>适用于 Defender ATP 的 Intune 安全任务（公共预览版）     <!-- 3208597 -->
在公共预览版中，可以使用 Intune 管理 [Microsoft Defender 高级威胁防护 (ATP) 的安全任务](atp-manage-vulnerabilities.md)。 这与 ATP 集成，并增加了基于风险的方法来发现终结点漏洞和配置错误，并对其设置优先级和进行修正，同时缩短了从发现到缓解的时间。

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---idstaged--"></a>了解 Windows 10 设备合规性策略中的 TPM 芯片组 <!-- 3617671   idstaged-->
许多 Windows 10 及更高版本设备都具有受信任的平台模块 (TPM) 芯片组。 此更新包含一个新符合性设置，它将检查设备上的 TPM 芯片版本。 

[Windows 10 及更高版本的符合性策略设置](compliance-policy-create-windows.md#device-security)介绍了此设置。

适用于：Windows 10 及更高版本

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices----4097904-----"></a>防止最终用户修改其个人热点，并禁止 Siri 服务器登录 iOS 设备 <!-- 4097904   -->  
为 iOS 设备创建设备限制配置文件（在“设备配置” > “配置文件” > “创建配置文件” >  针对平台选择“iOS”> 针对配置文件类型选择“设备限制”）。 此更新包括可配置的新设置：

- **内置应用**：Siri 命令的服务器端日志记录
- **无线**：个人热点的用户修改（仅限监管模式）

若要查看这些设置，请转到[适用于 iOS 的内置应用设置](device-restrictions-ios.md#built-in-apps)和[适用于 iOS 的无线设置](device-restrictions-ios.md#wireless)。

适用于：iOS 12.2 及更新版本

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices----4097905-----"></a>macOS 设备的新 Classroom 应用设备限制设置 <!-- 4097905   --> 
可以为 macOS 设备创建设备配置文件（依次选择“设备配置” > “配置文件” > “创建配置文件” >  针对平台选择“macOS”> 针对配置文件类型选择“设备限制”）。 在此次更新中，我们新增了教室应用设置、用于阻止屏幕截图的选项，以及用于禁用 iCloud 照片库的选项。

要查看最新设置，请转到[使用 Intune 允许或限制功能的 macOS 设备设置](device-restrictions-macos.md)。

适用范围：macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>已重命名用于访问应用商店设置的 iOS 密码<!-- 4557891  -->
“用于访问应用商店的密码”设置已重命名为“要求所有购买都输入 iTunes Store 密码”（“设备配置” > “配置文件” > “创建配置文件” > “iOS”(针对平台) > 配置文件类型的“设备限制”>“App Store、文档查看和游戏”）。

若要查看可用设置，请转到 [App Store、文档查看和游戏 iOS 设置](device-restrictions-ios.md#app-store-doc-viewing-gaming)。

适用于：iOS

#### <a name="microsoft-defender-advanced-threat-protection--baseline--preview------3754134---"></a>Microsoft Defender 高级威胁防护基线（预览版）  <!--  3754134 -->
已添加用于 [Microsoft Defender 高级威胁防护](security-baseline-settings-defender-atp.md)设置的安全基线（预览版）。 当环境满足使用 [Microsoft Defender 高级威胁防护](advanced-threat-protection.md#prerequisites)的先决条件时，此基线才可用。

### <a name="device-enrollment"></a>设备注册

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available----3605348---"></a>Windows 注册状态页 (ESP) 现已正式发布 <!-- 3605348 -->
注册状态页现在没有预览版。 有关详细信息，请参阅[设置注册状态页](windows-enrollment-status.md)。


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation-----4593669---"></a>Intune 用户界面更新 - Autopilot 注册配置文件创建  <!-- 4593669 -->
用于创建 Autopilot 注册配置文件的用户界面已更新为与 Azure 用户界面样式保持一致。 有关详细信息，请参阅[创建 Autopilot 注册配置文件](https://docs.microsoft.com/intune/enrollment-autopilot#create-an-autopilot-deployment-profile)。 接下来，其他 Intune 方案将更新为此新 UI 样式。

#### <a name="enable-autopilot-reset-for-all-windows-devices----4225665---"></a>为所有 Windows 设备启用 Autopilot 重置 <!-- 4225665 -->
Autopilot 重置现在适用于所有 Windows 设备，甚至包括那些未配置为使用注册状态页的设备。 如果在初始设备注册过程中未为设备配置注册状态页，则设备将在登录后直接转到桌面。 可能最多需要 8 小时才能同步并在 Intune 中显示符合。 有关详细信息，请参阅[使用远程 Windows Autopilot 重置功能重置设备](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote)。

#### <a name="exact-imei-format-not-required-when-searching-all-devices---30407680---"></a>搜索所有设备时不需要确切的 IMEI 格式 <!--30407680 -->
搜索“所有设备”时，无需在 IMEI 号码中包含空格。

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>从 Apple 门户删除设备时，Intune 门户将反映此操作 <!--2489996 -->
如果从 Apple 的设备注册计划或 Apple Business Manager 门户删除设备，下次同步时将自动从 Intune 删除该设备。

### <a name="the-enrollment-status-page-now-tracks-win32-apps----2714451---"></a>注册状态页现在跟踪 Win32 应用 <!-- 2714451 -->
这仅适用于运行 Windows 10 版本 1903 及更高版本的设备。 有关详细信息，请参阅[设置注册状态页](windows-enrollment-status.md)。

### <a name="device-management"></a>设备管理

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>使用图形 API 批量重置和擦除设备 <!-- 3295288 -->
用户现在可以使用图形 API 批量重置和擦除多达 100 台设备。


### <a name="monitor-and-troubleshoot"></a>监视和故障排除

#### <a name="the-encryption-report-is-out-of-public-preview------4587546--------"></a>加密报表没有公共预览版   <!-- 4587546      -->
[BitLocker 和设备加密的报表](encryption-monitor.md)现已正式发布，并且不再是公共预览版的一部分。 

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices----4050557---"></a>适用于 iOS 和 Android 设备的 Outlook 签名和生物识别设置 <!-- 4050557 -->
现在可以指定是否在 iOS 和 Android 设备上的 Outlook 中启用了默认签名。 此外，还可以选择允许用户更改 iOS 上的 Outlook 中的生物识别设置。

## <a name="week-of-may-6-2019"></a>2019 年 5 月 6 日当周 

### <a name="device-configuration"></a>设备配置

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices----4500808---"></a>面向 iOS 设备针对 F5 Access 的网络访问控制 (NAC) 支持 <!-- 4500808 -->

F5 发布了针对 BIG-IP 13 的更新，在 Intune 中实现了针对 iOS 上的 F5 Access 的 NAC 功能支持。 使用此功能需要：

- 将 BIG-IP 更新为 13.1.1.5 版。 不支持 BIG-IP 14。
- 将 BIG-IP 与 Intune 相集成以配置 NAC。 [概述：使用终结点管理系统配置 APM 以进行设备状态检查](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html)中列出了相关步骤。
- 在 Intune 中的 VPN 配置文件中选择“启用网络访问控制(NAC)”设置。

若要查看可用设置，请转至[在 iOS 设备上配置 VPN](vpn-settings-ios.md)。

适用于：iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune----doc-vso-1521237----"></a>更新了 Microsoft Intune 的 PFX 证书连接器 <!-- doc-vso 1521237  -->  
我们发布了针对 [Microsoft Intune 的 PFX 证书连接器](certficates-pfx-configure.md#whats-new-for-connectors)的更新，将轮询间隔从 5 分钟降到了 30 秒。

## <a name="week-of-april-22-2019"></a>2019 年 4 月 22 日当周

### <a name="use-compliance-manager-to-create-assessments-for-microsoft-intune---4404750---"></a>使用合规性管理器为 Microsoft Intune 创建评估<!-- 4404750 -->

[合规性管理器](https://servicetrust.microsoft.com/ComplianceManager)（打开另一个 Microsoft 站点）是 Microsoft 服务信任门户中基于工作流的风险评估工具。 它使你能够跟踪、分配和验证组织的与 Microsoft 服务相关的法规遵从性活动。 可以使用 Office 365、Azure、Dynamics、专业服务和 Intune 创建自己的合规性评估。 Intune 提供两种评估：FFIEC 和 GDPR。

合规性管理器可将控件分类（由 Microsoft 管理的控件和由组织管理的控件），从而帮助你节省精力。 你可以完成评估，然后导出并打印评估。

[联邦金融机构检查委员会 (FFIEC)](https://www.microsoft.com/trustcenter/compliance/FFIEC)（打开另一个 Microsoft 站点）合规性是 FFIEC 发布的一套网上银行标准。 对于使用 Intune 的金融机构来说，这是最必不可少的评估。 它诠释了 Intune 如何帮助遵循与公有云工作负载相关的 FFIEC 网络安全指南。 Intune 的 FFIEC 评估是合规性管理器中的第二种 FFIEC 评估。

以下示例介绍 FFIEC 控件的明细。 Microsoft 负责 64 个控件。 你负责其余 12 个控件。

![请参阅 FFIEC 的 Intune 评估示例，其中包括客户操作和 Microsoft 操作](./media/intune-ffiec-assessment-status.png)

[一般数据保护条例 (GDPR)](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-overview)（打开另一个 Microsoft 站点）是欧盟 (EU) 法律，用于帮助保护个人及其数据的权利。 GDPR 是帮助遵守隐私法规的必不可少的评估。 

以下示例介绍 GDPR 控件的明细。 Microsoft 负责 49 个控件。 你负责其余 66 个控件。

![请参阅 GDPR 的 Intune 评估示例，其中包括客户操作和 Microsoft 操作](./media/intune-assessment-status.png)

## <a name="week-of-april-15-2019"></a>2019 年 4 月 15 日当周

### <a name="app-management"></a>应用管理

#### <a name="openssl-encryption-for-android-app-protection-policies----3747362---"></a>Android 应用保护策略的 OpenSSL 加密 <!-- 3747362 -->
Android 设备上的 Intune 应用保护策略 (APP) 现在使用符合 FIPS 140-2 标准的 OpenSSL 加密库。 有关详细信息，请参阅 [Microsoft Intune 中的 Android 应用保护策略设置](app-protection-policy-settings-android.md)的[加密](app-protection-policy-settings-android.md#encryption)部分。

#### <a name="enable-win32-app-dependencies----2617348----"></a>启用 Win32 应用依赖项 <!-- 2617348  -->
管理员可以要求在安装 Win32 应用之前，将其他应用作为依赖项进行安装。 具体来说，设备必须先安装相关应用，再安装 Win32 应用。 在 Intune 中，选择“客户端应用” > “应用” > “添加”，以显示“添加应用”边栏选项卡。 选择“Windows 应用(Win32)”作为“应用类型”。 添加应用后，可以选择“依赖项”，添加在安装 Win32 应用之前必须安装的相关应用。 有关详细信息，请参阅 [Intune 独立版 - Win32 应用管理](apps-win32-app-management.md)。 

#### <a name="app-version-installation-information-for-microsoft-store-for-business-apps----3537391-----"></a>适用于企业的 Microsoft Store 应用的应用版本安装信息 <!-- 3537391   -->
应用安装报告包括适用于企业的 Microsoft Store 应用的应用版本信息。 在 Intune 中，选择“客户端应用” > “应用”。 选择“适用于企业的 Microsoft Store 应用”，然后在“监视”部分下选择“设备安装状态”。

#### <a name="additions-to-win32-apps-requirement-rules----3676883-----"></a>Win32 应用要求规则的新增内容 <!-- 3676883   -->
可以基于 PowerShell 脚本、注册表值和文件系统信息创建要求规则。 在 Intune 中，选择“客户端应用” > “应用” > “添加”。 然后，在“添加应用”边栏选项卡中选择“Windows 应用(Win32)”作为“应用类型”。  选择“要求” > “添加”，以配置其他要求规则。 然后，选择“文件类型”、“注册表”或“脚本”作为“要求类型”。 有关详细信息，请参阅 [Win32 应用管理](apps-win32-app-management.md)。

#### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227----"></a>配置要在已注册到 Intune 并且已加入 Azure AD 的设备上安装的 Win32 应用 <!-- 3695227  -->
可以分配要在已注册到 Intune 并且已加入 Azure AD 的设备上安装的 Win32 应用。 有关 Intune 中 Win32 应用的详细信息，请参阅 [Win32 应用管理](apps-win32-app-management.md)。

#### <a name="device-overview-shows-primary-user---3794259----"></a>设备概述显示主要用户 <!--3794259  -->
“设备概述”页将显示主要用户，也称为用户设备相关性用户 (UDA)。 要查看设备的主要用户，请选择“Intune” > “设备” > “所有设备”> 选择一个设备。 主要用户将显示在靠近“概述”页顶部的位置。

#### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925----"></a>Android Enterprise 工作配置文件设备的其他托管 Google Play 应用报告 <!-- 4105925  -->
对于部署到 Android Enterprise 工作配置文件设备的托管 Google Play 应用，可以查看设备上安装的应用的特定版本号。 这仅适用于所需的应用。  

#### <a name="ios-third-party-keyboards----4111843-----"></a>iOS 第三方键盘 <!-- 4111843   -->
由于 iOS 平台更改，不再支持适用于针对 iOS 的“第三方键盘”设置的 Intune 应用保护策略 (APP) 的支持。 你将无法在 Intune 管理控制台中配置此设置，并且此设置将不会在 Intune App SDK 中的客户端上强制执行。

### <a name="device-configuration"></a>设备配置

#### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083----"></a>在 macOS 设备上设置登录设置和控制重启选项 <!-- 1210083  -->
在 macOS 设备上，可以创建设备配置文件（依次选择“设备配置” > “配置文件” > “创建配置文件” > 针对平台选择“macOS”> 针对配置文件类型选择“设备功能”）。 此更新包括新的登录窗口设置，例如显示自定义横幅、选择用户登录方式、显示或隐藏电源设置等。

要查看这些设置，请转到 [macOS 设备功能设置](macos-device-features-settings.md)。

#### <a name="configure-wifi-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode---3041940----"></a>在以多应用展台模式运行的 Android Enterprise 和设备所有者专用设备上配置 WiFi <!--3041940  -->
可以在以多应用展台模式运行的 Android Enterprise 和设备所有者专用设备上启用设置。 在此更新中，可让用户配置和连接到 WiFi 网络（依次选择“Intune” > “设备配置” > “配置文件” > “创建配置文件” >  针对平台选择“Android Enterprise”> 针对配置文件类型选择“仅限设备所有者”>“设备限制”>“专用设备” > “展台模式”：“多应用” > “WiFi 配置”。 

要查看可以配置的所有设置，请转到[用于允许或限制功能的 Android Enterprise 设备设置](device-restrictions-android-for-work.md)。

适用于：以多应用展台模式运行的 Android Enterprise 专用设备


#### <a name="configure-bluetooth-and-pairing-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode----3041941----"></a>在以多应用展台模式运行的 Android Enterprise 和设备所有者专用设备上配置蓝牙和配对 <!-- 3041941  -->
可以在以多应用展台模式运行的 Android Enterprise 和设备所有者专用设备上启用设置。 在此更新中，你可以允许最终用户启用蓝牙并通过蓝牙进行设备配对（依次选择“Intune” > “设备配置” > “配置文件” > “创建配置文件” >  针对平台选择“Android Enterprise”> 针对配置文件类型选择“仅限设备所有者”>“设备限制”>“专用设备” > “展台模式”：“多应用” > “蓝牙配置”。 

要查看可以配置的所有设置，请转到[用于允许或限制功能的 Android Enterprise 设备设置](device-restrictions-android-for-work.md)。

适用于：以多应用展台模式运行的 Android Enterprise 专用设备

#### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883----"></a>在 Intune 中创建和使用 OEMConfig 设备配置文件 <!-- 3305883  -->
在此更新中，Intune 支持使用 OEMConfig 配置 Android Enterprise 设备。 具体来说，可以使用 OEMConfig 创建设备配置文件并将设置应用于 Android Enterprise 设备（依次选择“设备配置” > “配置文件” > “创建配置文件” >  针对平台选择“Android Enterprise”）。

对 OEM 的支持目前基于每个 OEM。 如果 OEMConfig 应用列表中未包含所需 OEMConfig 应用，请联系 `IntuneOEMConfig@microsoft.com`。

要了解有关此功能的详细信息，请转到[在 Microsoft Intune 中通过 OEMConfig 使用和管理 Android Enterprise 设备](android-oem-configuration-overview.md)。

适用于：Android Enterprise

#### <a name="windows-update-notifications-----3316758-3316782----"></a>Windows 更新通知  <!-- 3316758, 3316782  -->
我们已将两个“用户体验设置”添加到了你可以在 Intune 控制台中管理的 Windows 更新通道配置中。 现在可以执行以下操作：
- 阻止或允许用户[扫描 Windows 更新](windows-update-settings.md)。
- 管理向用户显示的 [Windows 更新通知级别](windows-update-settings.md)。

#### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254----"></a>针对 Android Enterprise 和设备所有者的新设备限制设置 <!-- 3574254  -->
在 Android Enterprise 设备上，可以创建设备限制配置文件，以允许或限制功能和设置密码规则等（依次选择“设备配置” > “配置文件” > “创建配置文件”> 针对平台选择“Android Enterprise”> 针对配置文件类型选择“仅限设备所有者”>“设备限制”）。 

此更新包括新密码设置，允许完全托管设备对 Google Play 商店中应用的完全访问权限，等等。 要查看设置的当前列表，请转到[用于允许或限制功能的 Android Enterprise 设备设置](device-restrictions-android-for-work.md)。 

适用于：Android Enterprise 完全托管设备

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>了解 Windows 10 设备合规性策略中的 TPM 芯片组 <!-- 3617671 -->

此功能已推迟，并计划稍后发布。

#### <a name="updated-ui-changes-for-microsoft-edge-browser-on-windows-10-and-later-devices----3775833-----"></a>更新了 Windows 10 及更高版本设备上 Microsoft Edge 浏览器的 UI 更改 <!-- 3775833   -->
创建设备配置文件时，可以允许或限制 Windows 10 及更高版本设备上的 Microsoft Edge 功能（依次选择“设备配置” > “配置文件” > “创建配置文件”> 针对平台选择“Windows 10 和更高版本”> 针对配置文件类型选择“设备限制”>“Microsoft Edge 浏览器” > ）。 在此更新中，Microsoft Edge 设置的描述更具体，更易于理解。 

要查看这些功能，请转到 [Microsoft Edge 浏览器设备限制设置](device-restrictions-windows-10.md#microsoft-edge-browser)。

适用于：Windows 10 及更高版本

#### <a name="expanded-support-for-android-enterprise-fully-managed-devices--preview-------3903241-3903244-3903246-----"></a>扩展了对 Android Enterprise 完全托管设备（预览版）的支持  <!--   3903241, 3903244, 3903246   -->
我们继续在公开预览版中扩展了对 Android Enterprise 完全托管设备的支持（[于 2019 年 1 月首次发布](whats-new.md#week-of-january-14-2019)，包括以下内容： 

- 在完全托管设备和专用设备上，可以创建[合规性策略](compliance-policy-create-android-for-work.md)以包括密码规则和操作系统要求（依次选择“设备合规性” > “策略” > “创建策略”> 针对平台选择“Android Enterprise”> 针对配置文件类型选择“设备所有者” > ）。 

  在专用设备上，设备可能显示为“不合规”。 在专用设备上无法进行条件访问。 请务必完成使专用设备符合分配的策略的任何任务或操作。

- [条件访问](conditional-access.md) - 适用于 Android 的条件访问策略也适用于 Android Enterprise 完全托管设备。 用户现在可以使用 Microsoft Intune 应用在 Azure Active Directory 中注册其完全托管设备。 然后，查看并解决任何合规性问题，以访问组织资源。

- 新最终用户应用（Microsoft Intune 应用）- 有一种用于 Android 完全托管设备的新最终用户应用，名为 Microsoft Intune。 此新应用质轻、现代，可提供与公司门户应用类似的功能，但适用于完全托管设备。 有关详细信息，请参阅 [Google Play 上的 Microsoft Intune 应用](https://play.google.com/store/apps/details?id=com.microsoft.intune)。

若要设置完全托管的 Android 设备，请转到“设备注册” > “Android 注册” > “公司拥有的完全托管的用户设备”。 完全托管的 Android 设备的支持仍为预览版，某些 Intune 功能可能无法完全正常运行。  

要详细了解此预览版，请参阅我们的博客 [Microsoft Intune - Preview 2 for Android Enterprise Fully Managed devices](https://aka.ms/preview2_AE_fullymanaged)（适用于 Android Enterprise 完全托管设备的 Microsoft Intune - 预览版 2）。


### <a name="device-enrollment"></a>设备注册

#### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470----"></a>将配置文件配置为在“设置助手”期间跳过某些屏幕 <!-- 2276470  -->
创建 macOS 注册配置文件时，可将其配置为在用户使用设置助手期间跳过以下任一屏幕：
- 外观
- 显示基调
- iCloudStorage：如果你新建或编辑配置文件，选定跳过屏幕需要与 Apple MDM 服务器同步。  用户可以发起手动同步设备，这样在选取配置文件变更时就不会有任何延迟。
有关详细信息，请参阅[通过设备注册计划或 Apple School Manager 自动注册 macOS 设备](device-enrollment-program-enroll-macos.md)。

#### <a name="bulk-device-naming-when-enrolling-corporate-ios-devices--3566569----"></a>注册企业 iOS 设备时批量命名设备<!--3566569  -->
使用 Apple 的任一企业注册方法 (DEP/ABM/ASM) 时，可以设置设备名格式，以自动命名传入的 iOS 设备。 可以在模板中指定包含设备类型和序列号的格式。 为此，请选择“Intune” > “设备注册” > “Apple 注册” > “注册程序令牌” > “选择令牌” >“创建配置文件” > “设备命名格式”。 可以编辑现有配置文件，但只有新同步的设备才会应用该名称。

#### <a name="updated-default-timeout-message-on-enrollment-status-page----3959331---"></a>更新了“注册状态”页上的默认超时消息 <!-- 3959331 -->
我们更新了在“注册状态”页 (ESP) 超过 ESP 配置文件中指定的超时值时用户看到的默认超时消息。 新的默认消息是用户看到的内容，可帮助他们了解 ESP 部署的下一步操作。  

### <a name="device-management"></a>设备管理

#### <a name="retire-noncompliant-devices-----1827291-----"></a>停用不合规的设备  <!-- 1827291   -->
此功能已推迟，并计划在将来版本中发布。


### <a name="monitor-and-troubleshoot"></a>监视和故障排除

#### <a name="intune-data-warehouse-v10-changes-reflecting-back-to-beta----4403765---"></a>Intune 数据仓库 V1.0 更改在 beta 版本中体现 <!-- 4403765 -->
V1.0 在 1808 版本首次引入后，它在某些重要方面与 beta 版 API 有所不同。 在 1903 版本中，这些更改将在 beta 版 API 中体现。 如果有使用 beta 版 API 的重要报表，我们强烈建议将这些报表切换到 V1.0 以避免中断性变更。 有关详细信息，请参阅 [Intune 数据仓库 API 的更改日志](reports-changelog.md#1903-part-2)。

#### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>监控安全基线状态（公共预览版） <!-- 3082047 --> 
我们向安全基线的监控添加了[每个类别的视图](security-baselines-monitor.md#per-category-view)。 （安全基线仍为预览版）。 每个类别的视图显示基线中的每个类别以及属于该类别的每个状态组的设备百分比。 现可查看与各个类别不匹配、配置错误或不适用的设备数量。

### <a name="role-based-access-control"></a>基于角色的访问控制

#### <a name="scope-tags-for-apple-vpp-tokens---2371886----"></a>Apple VPP 令牌的范围标记 <!--2371886  -->
现可将范围标记添加到 Apple VPP 令牌。 只有分配有相同范围标记的用户才能访问带有该标记的 Apple VPP 令牌。 使用该令牌购买的 VPP 应用和电子书会继承其范围标记。 有关范围标记的详细信息，请参阅[使用 RBAC 和范围标记](scope-tags.md)。







## <a name="week-of-april-1-2019"></a>2019 年 4 月 1 日当周

### <a name="device-configuration"></a>设备配置

#### <a name="updated-certificate-connectors-----icm-113304612---"></a>更新了证书连接器  <!-- ICM 113304612 -->
我们已经发布了针对 [Microsoft Intune 的 Intune 证书连接器和 PFX 证书连接器](certficates-pfx-configure.md#whats-new-for-connectors)的更新。 新版本修复了几个已知问题。  

### <a name="app-management"></a>应用管理

#### <a name="user-experience-update-for-the-company-portal-app-for-ios----2536024---"></a>iOS 版公司门户应用的用户体验更新 <!-- 2536024 -->
适用于 iOS 设备的公司门户应用的主页已经过重新设计。 经此更改后，主页将更好地遵循 iOS UI 模式，更易于查找应用和电子书。

#### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>对 iOS 12 设备用户的公司门户注册的更改 <!--3448635 -->  
适用于 iOS 的公司门户的注册屏幕和步骤已更新，以与 Apple iOS 12.2 中发布的 MDM 注册更改保持一致。 更新的工作流提示用户执行以下操作：  

* 允许 Safari 在返回公司门户应用之前打开公司门户网站并下载管理配置文件。  
* 打开“设置”应用以在其设备上安装管理配置文件。
* 返回公司门户应用以完成注册。  

要了解更新的注册步骤和屏幕，请参阅[在 Intune 中注册 iOS 设备](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)。  

## <a name="week-of-march-25-2019"></a>2019 年 3 月 25 日当周

### <a name="monitor-and-troubleshoot"></a>监视和故障排除

### <a name="support-for-the-power-bi-compliance-app-from-the-data-warehouse-blade-in-microsoft-intune----4260871---"></a>Microsoft Intune 中的“数据仓库”边栏选项卡中对 Power BI 合规性应用的支持 <!-- 4260871 -->
以前，“Intune 数据仓库”边栏选项卡中的“下载 Power BI 文件”链接会下载 Intune 数据仓库报表（.pbix 文件）。 此报表已替换为 Power BI 合规性应用。 Power BI 合规性应用无需特殊加载或设置。 它将直接在 Power BI 在线门户中打开，并根据凭据专门向 Intune 租户显示数据。 在 Intune 中，选择“Intune”边栏选项卡右侧的“设置 Intune 数据仓库”链接。 然后，单击“获取 Power BI 应用”。 有关详细信息，请参阅[使用 Power BI 连接到数据仓库](reports-proc-get-a-link-powerbi.md)。

## <a name="week-of-march-18-2019"></a>2019 年 3 月 18 日当周

### <a name="app-management"></a>应用管理

#### <a name="deploy-microsoft-visio-and-microsoft-project----3725386----"></a>部署 Microsoft Visio 和 Microsoft Project <!-- 3725386  -->
现可使用 Microsoft Intune，将 Microsoft Visio Pro for Office 365 和 Microsoft Project Online 桌面客户端作为独立应用部署到 Windows 10 设备（如果拥有这些应用的许可证）。 在 Intune 中，选择“客户端应用” > “应用” > “添加”，以显示“添加应用”边栏选项卡。 在“添加应用”边栏选项卡上，选择“Windows 10”作为“应用类型”。 然后，选择“配置应用套件”，以选择要安装的应用。 有关适用于 Windows 10 设备的 Office 365 应用的详细信息，请参阅[使用 Microsoft Intune 将 Office 365 应用分配给 Windows 10 设备](apps-add-office365.md)。

#### <a name="microsoft-visio-pro-for-office-365-product-name-change----3593653----"></a>Microsoft Visio Pro for Office 365 产品名称更改 <!-- 3593653  -->
Microsoft Visio Pro for Office 365 现在称为 Microsoft Visio Online 计划 2。  有关 Microsoft Visio 的详细信息，请参阅 [Visio Online 计划 2](https://products.office.com/visio/visio-online-plan-2)。 有关适用于 Windows 10 设备的 Office 365 应用的详细信息，请参阅[使用 Microsoft Intune 将 Office 365 应用分配给 Windows 10 设备](apps-add-office365.md)。

#### <a name="intune-app-protection-policy-app-character-limit-setting----3291302----"></a>Intune 应用保护策略 (APP) 字符限制设置 <!-- 3291302  -->
Intune 管理员可以指定 Intune APP“限制使用其他应用剪切、复制和粘贴”策略设置的例外情况。  管理员可以指定可能会从托管应用中剪切或复制的字符数。 此设置允许将指定数量的字符共享到任何应用，而不受“限制使用其他应用剪切、复制和粘贴”设置的限制。 请注意，适用于 Android 的 Intune 公司门户应用版本需要 5.0.4364.0 或更高版本。 有关详细信息，请参阅 [iOS 数据保护](app-protection-policy-settings-ios.md#data-protection)、[Android 数据保护](app-protection-policy-settings-android.md#data-protection)和[查看客户端应用保护日志](app-protection-policy-settings-log.md#app-protection-policy-settings)。

#### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477-----"></a>用于进行 Office ProPlus 部署的 Office 部署工具 (ODT) XML <!-- 3192477   -->
在 Intune 管理控制台中创建 Office Pro Plus 实例时，将能够提供 Office 部署工具 (ODT) XML。 如果现有的 Intune UI 选项无法满足需求，这将允许进行更多自定义。 有关详细信息，请参阅[使用 Microsoft Intune 将 Office 365 应用分配到 Windows 10 设备](https://docs.microsoft.com/intune/apps-add-office365)以及 [Office 部署工具的配置选项](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool)。

#### <a name="app-icons-will-now-be-displayed-with-an-automatically-generated-background----1429026----"></a>现在将显示自动生成背景的应用图标 <!-- 1429026  -->
在 Windows 公司门户应用中，现在将显示应用图标，其中的背景根据图标主色（如果可检测到）自动生成。 如果适用，此背景将替换以前应用磁贴上显示的灰色边框。 用户将在 10.3.3451.0 之后的公司门户版本中看到此更改。

#### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523-----"></a>在 Windows 批量注册后，使用公司门户应用安装可用的应用 <!-- 2751523   -->
使用 [Windows 批量注册](windows-bulk-enroll.md)（预配包）注册到 Intune 的 Windows 设备将能够使用公司门户应用安装可用的应用。 有关公司门户应用的详细信息，请参阅[手动添加 Windows 10 公司门户](store-apps-company-portal-app.md)和[如何配置 Microsoft Intune 公司门户应用](company-portal-app.md)。

#### <a name="the-microsoft-teams-app-can-be-selected-as-part-of-the-office-app-suite----3828932----"></a>可以选择 Microsoft Teams 应用作为 Office 应用套件的一部分 <!-- 3828932  -->
在安装 Office Pro Plus 应用套件的过程中，可以包含或排除 Microsoft Teams 应用。 此功能适用于 Office Pro Plus 内部版本号 16.0.11328.20116+。 用户必须先注销，然后登录设备，才能完成安装。 在 Intune 中，选择“客户端应用” > “应用” > “添加”。 选择一种“Office 365 套件”应用类型，然后选择“配置应用套件”。

### <a name="device-configuration"></a>设备配置

#### <a name="automatically-start-an-app-when-running-multiple-apps-in-kiosk-mode-on-windows-10-and-later-devices----2351390---"></a>在 Windows 10 及更高版本的设备上以展台模式运行多个应用时自动启动应用 <!-- 2351390 -->

在 Windows 10 及更高版本的设备上，能够以展台模式运行设备，并运行许多应用。 在此更新中，可以进行自动启动设置（依次选择“设备配置” > “配置文件” > “创建配置文件” >  针对平台选择“Windows 10 和更高版本”> 针对配置文件类型选择“展台”>“多应用展台”）。 使用此设置可在用户登录设备时自动启动应用。

要查看所有展台设置的列表和说明，请参阅 [Intune 中作为展台运行的 Windows 10 和更高版本设备的设置](kiosk-settings-windows.md)。

适用于：Windows 10 及更高版本

#### <a name="operational-logs-also-show-details-on-non-compliant-devices----4063755----"></a>操作日志还显示有关不合规设备的详细信息 <!-- 4063755  -->
将 Intune 日志路由到 Azure 监视器功能时，还可以路由操作日志。 在此更新中，操作日志还提供有关不合规设备的信息。 

有关此功能的详细信息，请参阅[在 Intune 中将日志数据发送到存储、事件中心或日志分析](review-logs-using-azure-monitor.md)。

#### <a name="route-logs-to-azure-monitor-in-more-intune-workloads----3804627---"></a>在更多 Intune 工作负载中，将日志路由到 Azure Monitor <!-- 3804627 -->
在 Intune 中，可以将审核和操作日志路由到 Azure Monitor 中的事件中心、存储和日志分析（依次选择“Intune” > “监视” > “诊断设置”）。 在此更新中，可以路由更多 Intune 工作负载中的这些日志，包括合规性、配置、客户端应用等。 

要了解有关将日志路由到 Azure Monitor 的详细信息，请参阅[将日志数据发送到存储、事件中心或日志分析](review-logs-using-azure-monitor.md)。

#### <a name="create-and-use-mobility-extensions-on-android-zebra-devices-in-intune----3305880-----"></a>使用 Android Zebra 设备在 Intune 中创建和使用移动扩展 <!-- 3305880   -->
在此更新中，Intune 支持配置 Android Zebra 设备。 具体来说，可以创建设备配置文件，并使用 StageNow 生成的移动扩展 (MX) 配置文件将设置应用于 Android Zebra 设备（依次选择“设备配置” > “配置文件” > “创建配置文件” >  针对平台选择“Android”> 针对配置文件类型选择“MX 配置文件(仅限 Zebra)”）。

有关此功能的详细信息，请参阅[通过 Intune 中的移动扩展使用和管理 Zebra 设备](android-zebra-mx-overview.md)。

适用于：Android

### <a name="device-management"></a>设备管理

#### <a name="encryption-report-for-windows-10-devices-in-public-preview---2351538---"></a>Windows 10 设备的加密报表（公共预览版）<!-- 2351538 -->  
使用新的[加密报表（预览版）](encryption-monitor.md)查看关于 Windows 10 设备加密状态的详细信息。 可用的详细信息包括设备 TPM 版本、加密准备和状态、错误报告等。  

#### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-in-public-preview----2351547-----"></a>从 Intune 门户访问 BitLocker 恢复密钥（公共预览版） <!-- 2351547   -->  
现在可以使用 Intune 从 Azure Active Directory [查看有关 BitLocker 密钥 ID 和 BitLocker 恢复密钥的详细信息](encryption-monitor.md)。

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Microsoft Edge 支持 iOS 和 Android 设备上的 Intune 方案 <!-- 3411007 -->
Microsoft Edge 支持与 Intune Managed Browser 相同的所有管理方案，并新增了对最终用户体验的改进。 Intune 策略启用的 Microsoft Edge 企业功能包括双重标识、应用保护策略集成、Azure 应用程序代理集成、托管收藏夹和主页快捷方式。 有关详细信息，请参阅 [Microsoft Edge 支持](app-configuration-managed-browser.md#microsoft-edge-support)。

#### <a name="exchange-onlineintune-connector-deprecate-support-for-eas-only-devices---3105122----"></a>Exchange Online/Intune 连接器不再支持只有 EAS 的设备 <!--3105122  -->
Intune 控制台不再支持查看和管理使用 Intune 连接器连接到 Exchange Online 的只有 EAS 的设备。 但你有以下选项：
- 在移动设备管理 (MDM) 中注册设备
- 使用 Intune 应用保护策略管理设备
- 使用 [Exchange Online 中的客户端和移动设备](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online)中所述的 Exchange 控件

### <a name="search-the-all-devices-page-for-an-exact-device-by-using-name---4254930---"></a>使用[名称]在“所有设备”页中精确搜索设备 <!--4254930 -->
现在可以精确搜索的设备名。 转到“Intune” > “设备” > “所有设备”> 在搜索框中，使用 {} 将设备名括起来，以精确搜索匹配项。 例如，{Device12345}。

### <a name="monitor-and-troubleshoot"></a>监视和故障排除

#### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202----"></a>支持“租户状态”页上的其他连接器 <!-- 3617202  -->
[“租户状态”页](tenant-status.md)现可显示其他连接器的状态信息，包括 Windows Defender 高级威胁防护 (ATP) 和其他 Mobile Threat Defense 连接器。

### <a name="role-based-access-control"></a>基于角色的访问控制

#### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917----"></a>向某些 Azure Active Directory 角色授予 Intune 只读访问权限 <!-- 3637917  -->
已向以下 Azure AD 角色授予 Intune 只读访问权限。 通过 Azure AD 角色授予的权限取代了通过 Intune 基于角色的访问控制 (RBAC) 授予的权限。

对 Intune 审核数据的只读访问权限：

- 合规性管理员
- 符合性数据管理员

对所有 Intune 数据的只读访问权限：

- 安全管理员
- 安全操作员
- 安全性读者

有关详细信息，请参阅[基于角色的访问控制](role-based-access-control.md)。

#### <a name="scope-tags-for-ios-app-provisioning-profiles---2934430-----"></a>iOS 应用预配配置文件的范围标记 <!--2934430   -->
可以向 iOS 应用预配配置文件添加范围标记，以便只有角色也分配有该范围标记的人员才能够访问 iOS 应用预配配置文件。 有关详细信息，请参阅[使用 RBAC 和范围标记](scope-tags.md)。

#### <a name="scope-tags-for-app-configuration-policies---2371891-----"></a>应用配置策略的范围标记 <!--2371891   -->
可以向应用配置策略添加范围标记，以便只有角色也分配有该范围标记的人员才能够访问应用配置策略。 应用配置策略仅针对或关联到分配有相同范围标记的应用。 有关详细信息，请参阅[使用 RBAC 和范围标记](scope-tags.md)。

### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Microsoft Edge 支持 iOS 和 Android 设备上的 Intune 方案 <!-- 3411007 -->
Microsoft Edge 将增加对最终用户体验的改进，支持与 Intune 托管浏览器相同的所有管理方案。 Intune 策略启用的 Microsoft Edge 企业功能包括双重标识、应用保护策略集成、Azure 应用程序代理集成、托管收藏夹和主页快捷方式。 有关详细信息，请参阅 [Microsoft Edge 支持](app-configuration-managed-browser.md#microsoft-edge-support)。

## <a name="week-of-february-25-2019"></a>2019 年 2 月 25 日当周

### <a name="device-configuration"></a>设备配置

#### <a name="intune-powershell-module----951068----"></a>Intune PowerShell 模块 <!-- 951068  -->
现在，[Microsoft PowerShell 库](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune/6.1902.1.10)中提供了 Intune PowerShell 模块，该模块可通过 Microsoft Graph 提供对 Intune API 的支持。

- [有关如何使用此模块的详细信息](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/README.md)
- [使用此模块的方案示例](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/Samples/README.md)

#### <a name="improved-support-for-delivery-optimization----3183757----"></a>改进了对传递优化的支持  <!--3183757  -->
我们扩展了 Intune 中对配置传递优化的支持。 现在可以配置[传递优化设置](delivery-optimization-settings.md)的扩展列表，并直接从 Intune 控制台将其定向到设备。


## <a name="week-of-february-18-2019"></a>2019 年 2 月 18 日当周

### <a name="app-management"></a>应用管理

#### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355-----"></a>Intune 将在 Android 设备上使用 Google Play 保护 API <!-- 2577355   -->
某些 IT 管理员面临着 BYOD 情况，最终用户可能会使他们的手机获取 root 权限或越狱。 此行为虽然有时并非恶意，但会导致绕过许多 Intune 策略，这些策略是为了保护组织在最终用户设备上的数据而设置的。 因此，Intune 为已注册和未注册的设备提供 root 权限和越狱检测。 在此版本中，Intune 现在将利用 Google Play 保护 API 添加到我们对未注册设备的现有 root 权限检测检查。 虽然 Google 不会共享发生的所有 root 权限检测检查，但我们预期这些 API 能够检测出因设备自定义而导致设备获取 root 权限的用户，以及能够在旧设备上获得较新 OS 更新的用户。 然后，可以阻止这些用户访问公司数据，或者可以从其启用策略的应用中删除其公司帐户。 为了获得额外价值，IT 管理员现在将在 Intune 应用保护边栏选项卡中进行多次报告更新 -“已标记的用户”报告将显示通过 Google Play 保护的 SafetyNet API 扫描检测到的用户，“潜在有害应用”报告将显示通过 Google 的验证应用 API 扫描检测到的应用。 此功能在 Android 中可用。

#### <a name="win32-app-information-available-in-troubleshooting-blade----2617342-----"></a>“故障排除”边栏选项卡显示的 Win32 应用信息 <!-- 2617342   -->
现在可以从 Intune 应用“排除故障”边栏选项卡收集 Win32 应用安装的失败日志文件。 有关应用安装排除故障的详细信息，请参阅[排查应用安装问题](troubleshoot-app-install.md)和[排查 Win32 应用问题](apps-win32-app-management.md#troubleshoot-win32-app-issues)。

#### <a name="app-status-details-for-ios-apps----3761235-----"></a>iOS 应用的应用状态详细信息 <!-- 3761235   -->
将出现与以下内容相关的新应用安装错误消息：
- 在共享 iPad 上安装 VPP 应用失败
- 禁用 App Store 失败
- 未能找到应用的 VPP 许可证
- 无法使用 MDM 提供程序安装系统应用
- 设备处于丢失模式或展台模式时无法安装应用
- 用户未登录 App Store 时无法安装应用

在 Intune 中，选择“客户端应用” > “应用”>“应用名称”>“设备安装状态”。 “状态详细信息”列中将提供新的错误消息。

#### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780----"></a>适用于 Windows 10 的公司门户应用中的全新应用类别屏幕<!-- 3834780  -->
添加了名为“应用类别”的新屏幕，以改善适用于 Windows 10 的公司门户中的应用浏览和选择体验。 用户现在可以看到他们的应用按照“特别推荐”、“教育”和“工作效率”等类别进行排序。 此更改将出现在公司门户 10.3.3451.0 版及更高版本中。 要查看新屏幕，请参阅[应用 UI 中的新增功能](https://docs.microsoft.com/intune/whats-new-app-ui)。 有关公司门户中应用的详细信息，请参阅[在设备上安装和共享应用](/intune-user-help/install-apps-cpapp-windows)。  

#### <a name="power-bi-compliance-app----1455231-doc-work-item---"></a>Power BI 合规性应用 <!-- 1455231 doc-work-item -->
使用 [Intune 合规性（数据仓库）](https://aka.ms/intune/datawarehouseapi/getpowerbiapp)应用访问 Power BI Online 中的 Intune 数据仓库。 使用此 Power BI 应用，可立即访问和共享预创建的报表，无需任何设置，也无需离开 Web 浏览器。 有关详细信息，请参阅[更改日志 - Power BI 合规性应用](reports-changelog.md#power-bi-compliance-app)。


### <a name="device-configuration"></a>设备配置

#### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675-----"></a>PowerShell 脚本可以在 64 位设备上的 64 位主机上运行 <!-- 1862675   -->
将 PowerShell 脚本添加到设备配置概要文件时，该脚本始终以 32 位执行，即使在 64 位操作系统上也是如此。 通过此更新，管理员可以在 64 位设备上的 64 位 PowerShell 主机中运行该脚本（“设备配置” > “PowerShell 脚本” > “添加” > “配置” > “在 64 位 PowerShell 主机中运行脚本”）。

有关使用 PowerShell 的更多详细信息，请参阅 [Intune 中的 PowerShell 脚本](intune-management-extension.md)。

适用于：Windows 10 及更高版本

#### <a name="macos-users-are-prompted-to-update-their-password----1873216---"></a>系统会提示 macOS 用户更新密码 <!-- 1873216 -->
Intune 会在 macOS 设备上强制实施 ChangeAtNextAuth 设置。 此设置会影响具有合规性密码策略或设备限制密码配置文件的最终用户和设备。 系统会提示一次最终用户更新其密码。 每当用户首次运行需要身份验证的任务（例如，登录设备）时，就会出现此提示。 在执行需要管理权限的任何操作（例如，请求密钥链访问权限）时，系统也会提示用户更新密码。 

管理员更改任何新的或现有的密码策略时，系统会再次提示最终用户更新密码。

适用于：  
macOS

#### <a name="assign-scep-certificates-to-a-userless-macos-device-----2340521----"></a>将 SCEP 证书分配给无用户的 macOS 设备  <!-- 2340521  -->
可以使用设备属性将简单证书注册协议 (SCEP) 证书分配给 macOS 设备（包括没有用户关联的设备），并将证书配置文件与 Wi-Fi 或 VPN 配置文件相关联。 此操作扩展了现有的支持，可向[运行 Windows、iOS 和 Android 的具有和没有用户关联的设备分配 SCEP 证书](certificates-scep-configure.md#create-a-scep-certificate-profile)。  此更新添加了一个选项，可在配置 macOS 的 SCEP 证书配置文件时，选择设备的证书类型。

适用于： 
- macOS

#### <a name="intune-conditional-access-ui-update------2432313-----"></a>Intune 条件访问 UI 更新   <!-- 2432313   -->
我们已对 Intune 控制台中条件访问的 UI 进行了改进。 这些地方包括：
- 使用 Azure Active Directory 中的边栏选项卡替换了 Intune“条件访问”边栏选项卡。 这将确保可在 Intune 控制台中访问[条件访问](conditional-access.md)的所有设置和配置，这仍是 Azure AD 技术。 
- 我们已将“本地访问”边栏选项卡重命名为“Exchange 访问”，并将 Exchange 服务连接器设置重定位到此重命名的边栏选项卡。  此更改合并了[配置和监视与 Exchange Online 和 Exchange 本地相关的详细信息](exchange-connector-install.md)的位置。  

#### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135-----"></a>展台浏览器和 Microsoft Edge 浏览器应用能够在 Windows 10 设备上以展台模式运行 <!-- 2935135   -->
可以在展台模式下使用 Windows 10 设备运行一个应用或多个应用。 此更新包括在展台模式下使用浏览器应用的若干更改，包括：

- 添加 Microsoft Edge 浏览器或 Kiosk Browser 以在展台设备上作为应用程序运行（“设备配置” > “配置文件” > “新配置文件” > “Windows 10 及更高版本”（针对平台）>“展台”（针对配置文件类型））。
- 可以允许或限制新的功能和设置（依次选择“设备配置” > “配置文件” > “新配置文件” >  针对平台选择“Windows 10 和更高版本”> 针对配置文件类型选择“设备限制”），包括：

- Microsoft Edge 浏览器：
  - 使用 Microsoft Edge 展台模式
  - 空闲时间后刷新浏览器

- 收藏夹和搜索：
  - 允许更改搜索引擎

有关这些设置的列表，请参阅：

- [将 Windows 10 及更高版本设备作为展台运行的设置](kiosk-settings-windows.md)
- [Microsoft Edge 浏览器的设备限制](device-restrictions-windows-10.md#microsoft-edge-browser)
- [收藏夹和搜索设备限制](device-restrictions-windows-10.md##favorites-and-search)

适用于：Windows 10 及更高版本

#### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774-----"></a>适用于 iOS 和 macOS 设备的新设备限制设置 <!-- 3448774   -->
你可以在运行 iOS 和 macOS 的设备上限制某些设置和功能（“设备配置” > “配置文件” > “新配置文件” > “iOS”或“macOS”（针对平台）>“设备限制”（针对配置文件类型））。 此更新添加了可以控制的更多功能和设置，包括在 iOS 设备上设置屏幕时间、更改 eSIM 设置更改和蜂窝计划等。 此外，还包括在 macOS 设备上延迟用户见到软件更新的时间和阻止内容缓存。 

要查看可以限制的功能和设置，请参阅：

- [iOS 设备限制设置](device-restrictions-ios.md)
- [macOS 设备限制设置](device-restrictions-macos.md)

适用于：

- iOS
- macOS

#### <a name="kiosk-devices-are-now-called-dedicated-devices-on-android-enterprise-devices----3598402-----"></a>在 Android Enterprise 设备上，“展台”设备现在称为“专用设备” <!-- 3598402   -->
为了与 Android 术语保持一致，“展台”将更改为适用于 Android Enterprise 设备的“专用设备”（依次选择“设备配置” > “配置文件” > “创建配置文件”> 针对平台选择“Android Enterprise”>“仅限设备所有者” > “设备限制” > “专用设备”）。

要查看可用设置，请转到[允许或限制功能的设备设置](device-restrictions-android-for-work.md#dedicated-device-settings)。

适用于：  
Android Enterprise

#### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850-3803313-----"></a>Safari 和“延迟用户软件更新可见性”iOS 设置将移至 Intune UI <!-- 3640850, 3803313   -->
对于 iOS 设备，可以设置 Safari 设置并配置软件更新。 在此更新中，这些设置将移至 Intune UI 的不同部分：

- Safari 设置已从“Safari”（“设备配置” > “配置文件” > “新配置文件” > “iOS”（针对平台）>“设备限制”（针对配置文件类型））移动到[内置应用](device-restrictions-ios.md#built-in-apps)。
- 受监督的 iOS 设备的“延迟用户软件更新可见性”设置（“软件更新” > “iOS 的更新策略”）将移至“设备限制” >  [常规](device-restrictions-ios.md#general)。  有关对现有策略的影响的详细信息，请参阅 [iOS 软件更新](software-updates-ios.md#configure-the-policy)。 

有关设置列表，请参阅：

- [iOS 设备限制](device-restrictions-ios.md) 
- [iOS 软件更新](software-updates-ios.md)

此功能适用于： 

- iOS

#### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164-----"></a>在 iOS 设备上将设备设置中的启用限制重命名为屏幕时间 <!-- 3699164   -->
可以在受监管的 iOS 设备上配置“设备设置中的启用限制”（“设备配置” > “配置文件” > “新配置文件” > “iOS”（针对平台）>“设备限制”（针对配置文件类型）>“常规”）。 在此更新中，此设置将重命名为“屏幕时间(仅监管模式)”。 

操作是相同的。 具体而言： 

- iOS 11.4.1 及更早版本：“阻止”阻止最终用户在设备设置中设置自己的限制。 
- iOS 12.0 及更高版本：“阻止”阻止最终用户在设备设置中设置自己的“屏幕时间”，包括内容和隐私限制。 升级到 iOS 12.0 的设备将不再在设备设置中看到限制选项卡。 这些设置位于“屏幕时间”。 

有关设置列表，请参阅 [iOS 设备限制](device-restrictions-ios.md#general)。

适用于： 
- iOS


### <a name="device-management"></a>设备管理

#### <a name="rename-an-enrolled-windows-device----1911112----"></a>重命名已注册的 Windows 设备 <!-- 1911112  -->
现在可以重命名已注册的 Windows 10 设备（RS4 或更高版本）。 若要执行此操作，请选择“Intune” > “设备” > “所有设备”> 选择设备 >“重命名设备”。 此功能当前不支持重命名混合 Azure AD Windows 设备。

#### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>将范围标记自动分配给具有该范围的管理员创建的资源 <!-- 3173823  -->
管理员创建资源时，分配给管理员的任何范围标记都将自动分配给这些新资源。

### <a name="monitor-and-troubleshoot"></a>监视和故障排除

#### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202----"></a>“失败注册”报表将移至“设备注册”边栏选项卡 <!-- 3560202  -->
“失败注册”报表已迁移到“设备注册”边栏选项卡的“监视”部分。 已添加两个新列（“注册方法”和“OS 版本”）。

#### <a name="company-portal-abandonment-report-renamed-to-incomplete-user-enrollments---3815076-eemiss---"></a>“公司门户放弃报表”已重命名为“部分用户注册” <!--3815076 eemiss -->
“公司门户放弃报表”已重命名为“部分用户注册”。


<!-- ########################## -->
## <a name="week-of-february-4-2019"></a>2019 年 2 月 4 日当周

### <a name="app-management"></a>应用管理

#### <a name="intune-macos-company-portal-dark-mode----3300524----"></a>Intune macOS 公司门户深色模式 <!-- 3300524  -->
Intune macOS 公司门户现在支持 macOS 的深色模式。 在 macOS 10.14+ 设备上启用深色模式时，公司门户将调整其外观以反映该模式的颜色。

<!-- ########################## -->
## <a name="week-of-january-21-2019"></a>2019 年 1 月 21 日当周

### <a name="app-management"></a>应用管理

#### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Win32 应用的 Toast 通知 <!-- 3136566   -->
可以取消显示每个应用分配的最终用户 Toast 通知。 在 Intune 中，依次选择“客户端应用” > “应用”> 应用 >“分配” > “包括组”。 

#### <a name="intune-app-protection-policies-ui-update----3251427----"></a>Intune 应用保护策略用户界面更新 <!-- 3251427  -->
我们已更改 Intune 应用保护的设置和按钮的标签，以使用户更容易理解每个选项。 一些更改包括：  
- 控件从“是” / “否”控件更改为主要“阻止” / “允许”和“禁用” / “启用”控件。 标签也会更新。  
- 将对设置重新设置格式，以在控件中并排显示设置及其标签，从而提供更好的浏览。   

默认设置和设置数目将保持不变，但此更改可使用户更轻松地了解、浏览以及利用设置，以应用所选的应用保护策略。 有关信息，请参阅 [iOS 设置](app-protection-policy-settings-ios.md)和 [Android 设置](app-protection-policy-settings-android.md)。

### <a name="additional-settings-for-outlook----3301182----"></a>Outlook 的其他设置 <!-- 3301182  -->
现在可以使用 Intune 为 iOS 和 Android 配置 Outlook 以下其他设置：

- 仅允许在 iOS 和 Android 的 Outlook 中使用工作或学校帐户
- 部署适用于 Office 365 和混合新式身份验证本地帐户的新式身份验证
- 选择基本身份验证时，请使用 `SAMAccountName` 作为电子邮件配置文件中的用户名字段
- 允许保存联系人
- 配置外部收件人邮件提示
- 配置“重点收件箱”
- 需要进行生物识别来访问适用于 iOS 的 Outlook
- 阻止外部图像

> [!NOTE]
> 如果使用 Intune 应用保护策略来管理公司标识的访问权限，则应考虑不启用“需要生物识别”。 有关详细信息，请参阅 [iOS 访问设置](app-protection-policy-settings-ios.md#access-requirements)和 [Android 访问设置](app-protection-policy-settings-android.md#access-requirements)的“必须有公司凭据才能访问”。

有关详细信息，请参阅 [Microsoft Outlook 配置设置](app-configuration-policies-outlook.md)。

#### <a name="delete-android-enterprise-apps----1352553---"></a>删除 Android Enterprise 应用 <!-- 1352553 -->
可以从 Microsoft Intune 中删除托管 Google Play 应用。 若要删除托管 Google Play 应用，请在 Azure 门户中打开“Microsoft Intune”，并依次选择“客户端应用” > “应用”。 在应用列表中，选择托管 Google Play 应用右侧的省略号 (...)，再从随即显示的列表中选择“删除”。 从应用列表删除托管的 Google Play 应用时，托管的 Google Play 应用会自动变为未批准状态。

#### <a name="managed-google-play-app-type----1352580---"></a>“托管 Google Play”应用类型 <!-- 1352580 -->
“托管的 Google Play”应用类型让你可以专门将[托管的 Google Play 应用](https://play.google.com/work/search?q=microsoft&c=apps)添加到 Intune。 作为 Intune 管理员，现在可以在 Intune 中浏览、搜索、批准、同步和分配已批准的托管 Google Play 应用。  不再需要单独转到托管 Google Play 控制台，也不再需要重新进行身份验证。  在 Intune 中，选择“客户端应用” > “应用” > “添加”。 在“应用类型”列表中，将应用类型选择为“托管的 Google Play”。

### <a name="default-android-pin-keyboard----3802457---"></a>默认为 Android PIN 键盘 <!-- 3802457 -->
对于在 Android 设备上使用“数字”PIN 类型设置 Intune 应用保护策略 (App) PIN 的最终用户来说，他们将看到默认的 Android 键盘，而不是之前设计的固定 Android 键盘 UI。 在 Android 和 iOS 上使用默认键盘时，此更改对于“数字”和/或“密码”这两种 PIN 类型是一致的。 有关 Android 上最终用户访问设置的详细信息，如应用 PIN，请参阅 [Android 访问要求](app-protection-policy-settings-android.md#access-requirements)。

### <a name="device-configuration"></a>设备配置

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview----2055484-----"></a>结合使用 Microsoft 建议设置与安全基线（公共预览版） <!-- 2055484   -->

Intune 可与其他专注于安全性的服务集成，包括 Windows Defender ATP 和 Office 365 ATP。 客户要求能在各项 Microsoft 365 服务中采用通用策略和一组统一的端到端安全工作流。 我们的目标是实现策略一致，构建连接安全操作和常见管理员任务的解决方案。 在 Intune 中，我们旨在通过发布一组 Microsoft 推荐的“安全基线”（“Intune” > “安全基线”）来实现这一目标。  管理员可以直接通过这些基线创建安全策略，再将它们部署到用户。 还可以自定义最佳做法建议，以满足组织需求。 Intune 可确保设备始终符合这些基线，并通知不符合的用户管理员或设备。

此功能存在于公共预览版，因此现在创建的任何配置文件都不会转移到通用 (GA) 的安全基线模板。 不应计划在生产环境中使用这些预览模板。

若要详细了解安全基线，请参阅[在 Intune 中创建 Windows 10 安全基线](security-baselines-monitor.md)。

此功能适用于：Windows 10 及更高版本

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>非管理员可以在已加入 Azure AD 的 Windows 10 设备上启用 BitLocker<!-- 2147379   -->
在 Windows 10 设备上启用 BitLocker 设置时（“设备配置” > “配置文件” > “创建配置文件” > “Windows 10 及更高版本”作为平台 >“Endpoint protection”作为配置文件类型 >“Windows 加密”），将添加 BitLocker 设置。 

此更新包括新的 BitLocker 设置，以允许标准用户（非管理员）启用加密。 

若要查看设置，请转到[适用于 Windows 10 的 Endpoint Protection 设置](endpoint-protection-windows-10.md#windows-encryption)。

#### <a name="check-for-configuration-manager-compliance----2192052--eepublished----"></a>检查 Configuration Manager 合规性 <!-- 2192052  eepublished  -->
此更新包括新的 System Center Configuration Manager 符合性设置（“设备符合性” > “策略” > “创建策略” > “Windows 10 及更高版本” > “Configuration Manager 符合性）。 Configuration Manager 向 Intune 符合性发送信号。 使用此设置，可以要求所有 Configuration Manager 信号都返回“符合”。

例如，要求所有软件更新都安装在设备上。 在 Configuration Manager 中，此要求具有“已安装”状态。 如果设备上的任意计划处于未知状态，此设备在 Intune 中不符合要求。

[Configuration Manager 符合性](compliance-policy-create-windows.md#configuration-manager-compliance)介绍了此设置。

适用于：Windows 10 及更高版本

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324-----"></a>使用设备配置配置文件在受监管的 iOS 设备上自定义壁纸 <!-- 2809324   -->
为 iOS 设备创建设备配置文件时，可以自定义一些功能（“设置配置” > “配置文件” > “创建配置文件” > “iOS”（作为平台）>“设备功能”（作为配置文件类型））。 此更新包括新的墙纸设置，可便于管理员在主屏幕或锁定屏幕上使用 .png、.jpg 或 .jpeg 格式图像。 这些壁纸设置仅适用于受监督的设备。 

有关这些设置的列表，请参阅 [iOS 设备功能设置](ios-device-features-settings.md)。

#### <a name="windows-10-kiosk-is-generally-available----3594661----"></a>Windows 10 展台已全面推出 <!-- 3594661  -->
在此更新中，Windows 10 及更高版本设备上的展台功能已全面推出（正式版）。 若要查看可以添加和配置的所有设置，请参阅[适用于 Windows 10（及更高版本）的展台设置](kiosk-settings.md)。

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396-----"></a>在“设备限制”>“Android Enterprise 的设备所有者”中删除“通过蓝牙共享联系人” <!-- 3598396   -->
在创建 Android Enterprise 设备的设备限制配置文件时，会有一个“通过蓝牙共享联系人”设置。 在此更新中，“通过蓝牙共享联系人”设置遭删除（“设备配置” > “配置文件” > “创建配置文件” > “Android Enterprise”（作为平台）>“设备限制”>“设备所有者”（作为配置文件类型）>“常规”）。 

Android Enterprise 设备所有者管理不支持“通过蓝牙共享联系人”设置。 因此，在删除此设置时，即使在环境中启用并配置了此设置，此更改也不会影响任何设备或租户。

要查看设置的当前列表，请转到[用于允许或限制功能的 Android Enterprise 设备设置](device-restrictions-android-for-work.md)。

适用于：Android Enterprise 设备所有者

### <a name="device-management"></a>设备管理

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>对未注册的 WIP 设备的选择性擦除支持 <!-- 1434452 -->
未注册的 Windows 信息保护 (WIP-WE) 允许客户保护其在 Windows 10 设备上的公司数据，而不需要完整的 MDM 注册。 使用 WIP-WE 策略保护文档后，Intune 管理员可以选择性擦除受保护的数据。 通过选择用户和设备，并发送擦除请求，所有通过 WIP-WE 策略保护的数据都将不可用。 从 Azure 门户中的 Intune，选择“移动应用” > “应用选择性擦除”。

### <a name="monitor-and-troubleshoot"></a>监视和故障排除

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services----3762211----"></a>新推出运行日志，以及向 Azure Monitor 服务发送日志的功能 <!-- 3762211  -->
Intune 有内置审核日志，可以在事件变更时跟踪事件。 此更新包含新日志功能，包括： 
- 运行日志（预览版）显示已注册用户和设备的详细信息，其中包括成功和失败尝试次数。
- 可将审核日志和运行日志发送到 Azure Monitor，包括存储帐户、事件中心和 Log Analytics。 借助这些服务，可以存储数据、使用分析工具（如 Splunk 和 QRadar），并能获取日志数据的可视化效果。

[使用 Intune 将日志数据发送到存储、事件中心或 Log Analytics](review-logs-using-azure-monitor.md) 详细介绍了此功能。

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509----"></a>在 iOS DEP 设备上跳过更多设置助理屏幕 <!-- 2687509  -->
除了当前可以跳过的屏幕之外，还可以将 iOS DEP 设备设置为在用户注册设备时跳过设置助理中的以下屏幕：显示色调、隐私、Android 迁移、主页按钮、iMessage 和 FaceTime、载入、监视迁移、外观、屏幕时间、软件更新、SIM 安装程序。
若要选择要跳过的屏幕，请转到“设备注册” > “Apple 注册” > “注册计划令牌”> 选择令牌 >“配置文件”> 选择配置文件 >“属性” > “设置助理的自定义项”> 对于要跳过的任何屏幕选择“隐藏”>“确定”。
如果你新建或编辑配置文件，选定跳过屏幕需要与 Apple MDM 服务器同步。 用户可以发起手动同步设备，这样在选取配置文件变更时就不会有任何延迟。

#### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android Enterprise APP-WE 应用部署 <!-- 1171203 -->
对于没有注册 (APP-WE) 部署方案的未注册应用保护策略中的 Android 设备，现在可以使用托管的 Google Play 将应用商店应用和 LOB 应用部署到用户。 具体而言，可以向最终用户提供应用目录以及不再需要最终用户通过允许从未知源进行安装来放宽其设备的安全状况的安装体验。 此外，此部署方案将改进最终用户体验。

<!-- ########################## -->
## <a name="week-of-january-14-2019"></a>2019 年 1 月 14 日当周

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>对 Android 公司拥有的完全托管设备的支持（预览版） <!-- 1574342  -->
Intune 现支持完全托管的 Android 设备，这是公司拥有的“设备所有者”方案，其中设备由 IT 管理员严格管理并与各个用户关联。 这样，管理员便可以管理整个设备、强制扩展不可用于工作配置文件的策略控制的范围并限制用户仅从托管的 Google Play 安装应用。 有关详细信息，请参阅[设置 Android 完全托管的设备的 Intune 注册](android-fully-managed-enroll.md)和[注册专用设备或完全托管的设备](android-dedicated-devices-fully-managed-enroll.md)。  请注意，此功能处于预览状态。 Android 完全托管的用户设备目前无法使用部分 Intune 功能，例如证书、符合性以及条件访问。

<!-- ########################## -->
## <a name="week-of-january-7-2019"></a>2019 年 1 月 7 日当周

### <a name="app-management"></a>应用管理

#### <a name="intune-app-pin----2298397---"></a>Intune 应用 PIN <!-- 2298397 -->
作为 IT 管理员，你现在可以配置在最终用户必须更改其 Intune 应用 PIN 之前可以等待的天数。 新设置是在该等待天数之后重置的 PIN，同时，通过选择“Intune”“客户端应用” > “应用保护策略” > “创建策略” > “设置” > “访问要求” > ，便会在 Azure 门户中提供新设置。 可用于 [iOS](app-protection-policy-settings-ios.md) 和 [Android](app-protection-policy-settings-android.md) 设备，此功能支持正整数。


#### <a name="intune-device-reporting-fields----2748738---"></a>Intune 设备报告字段 <!-- 2748738 -->
Intune 提供其他设备报告字段，包括 Android 注册 ID、Android 制造商、模型和安全修补程序版本以及 iOS 型号。 在 Intune 中，通过选择“客户端应用” > “应用保护状态”并选择“应用保护报告: iOS、Android”来获取这些字段。 此外，这些参数将帮助你配置设备制造商“允许”列表 (Android)、设备型号的“允许”列表（Android 和 iOS）和最低 Android 安全修补程序版本设置。 


### <a name="device-configuration"></a>设备配置

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>管理模板为公共预览版，并移动到其自己的配置文件 <!-- 3322847 -->

Intune 中的管理模板（“设备配置” > “管理模板”）当前为公共预览版。 借助此更新：

- 管理模板包括可在 Intune 中托管的大约 300 个设置。 以前，这些设置仅存在于组策略编辑器中。
- 管理模板现已推出公共预览版。
- 管理模板从“设备配置” > “管理模板”移动到“设备配置” > “配置文件” > “创建配置文件”> 在“平台”中，选择“Windows 10 及更高版本”，在“配置文件类型”中，选择“管理模板”。
- 已启用报告

有关此功能的更多信息，请转到[用于配置组策略设置的 Windows 10 模板](administrative-templates-windows.md)。

适用于：Windows 10 及更高版本

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user-----1333642---"></a>使用 S/MIME 对用户的多个设备进行加密和签名  <!-- 1333642 -->
此更新包括使用新导入的证书配置文件进行 S/MIME 电子邮件加密（“设备配置” > “配置文件” > “创建配置文件”>“选择平台”>“PKCS 导入的证书”配置文件类型）。 在 Intune 中，可以 PFX 格式导入证书。 然后 Intune 可以将这些相同的证书传递给单个用户注册的多个设备。 还包括：
- 本机 iOS 电子邮件配置文件支持使用 PFX 格式的导入证书启用 S/MIME 加密。
- Windows Phone 10 设备上的本机电子邮件应用自动使用 S/MIME 证书。
- 可以跨多个平台传递私有证书。 但并非所有电子邮件应用都支持 S/MIME。
- 在其他平台上，可能需要手动配置电子邮件应用以启用 S/MIME。  
- 支持 S/MIME 加密的电子邮件应用可能以 MDM 不支持的方式（例如从发布者的证书存储读取）处理对 S/MIME 电子邮件加密的证书检索。
有关此功能的详细信息，请参阅[对电子邮件进行签名和加密的 S/MIME 概述](certificates-s-mime-encryption-sign.md)。
在以下设备上受支持：Windows、Windows Phone 10、macOS、iOS、Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>用于在 Windows 10 及更高版本设备上使用 DNS 设置时自动连接并保留规则的新选项 <!-- 1333665, 2999078 -->
在 Windows 10 及更高版本设备上，可以创建包含 DNS 服务器列表的 VPN 配置文件来解析域，如 contoso.com。 这一升级包括名称解析的新设置（“设备配置” > “配置文件” > “创建配置文件”> 选择“Windows 10 及更高版本”作为平台 > 选择“VPN”作为配置文件类型 >“DNS 设置” >“添加”）： 
- **自动连接**：如果为“已启用”，则当设备与所输入的域（如 contoso.com）通信时，会自动连接到 VPN。
- **永久性**：默认情况下，只要使用此 VPN 配置文件连接设备，所有名称解析策略表 (NRPT) 规则就会处于活动状态。 当 NRPT 规则的此设置为“已启用”时，该规则将在设备上保持活动状态，即使 VPN 断开连接也是如此。 该规则会保持活动状态，直到删除 VPN 配置文件或手动删除该规则，删除操作可以使用 PowerShell 完成。
[Windows 10 VPN 设置](vpn-settings-windows-10.md)介绍了设置。 

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>在 Windows 10 设备上使用 VPN 配置文件的受信任网络检测 <!-- 1500165 -->
使用受信任的网络检测时，可以在用户已使用受信任的网络时阻止 VPN 配置文件自动创建 VPN 连接。 通过此更新，可以添加 DNS 后缀，以便在运行 Windows 10 及更高版本的设备上启用受信任的网络检测（“设备配置” > “配置文件” > “创建配置文件” > “Windows 10 及更高版本”作为平台 >“VPN”作为配置文件类型）。
[Windows 10 VPN 设置](vpn-settings-windows-10.md)列出了当前的 VPN 设置。

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users----1907917-1063203---"></a>管理多个用户使用的 Windows Holographic for Business 设备 <!-- 1907917, 1063203 -->
目前，你可以在使用自定义 OMA-URI 设置的 Windows 10 和 Windows Holographic for Business 设备上配置共享电脑设置。 通过此更新，会添加新的配置文件以配置共享设备设置（“设备配置” > “配置文件” > “创建配置文件” > “Windows 10 及更高版本” > “共享多用户设备”）。
若要了解关于此功能的更多信息，请转到[用于托管共享设备的 Intune 设置](shared-user-device-settings.md)。
适用于：Windows 10 及更高版本、Windows Holographic for Business

#### <a name="new-windows-10-update-settings---2626030--2512994----"></a>新的 Windows 10 更新设置 <!--2626030  2512994  -->
对于 [Windows 10 更新通道](windows-update-for-business-configure.md)，可以配置：
- **自动更新行为** - 使用新选项“重置为默认值”，在运行“2018 年 10 月更新”的 Windows 10 计算机上还原初始的自动更新设置
- **阻止用户暂停 Windows 更新** - 配置新的软件更新设置，使你能够阻止或允许用户通过其计算机的“设置”暂停更新安装。 

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>iOS 电子邮件配置文件可以使用 S/MIME 签名和加密 <!-- 2662949 -->
你可以创建包含不同设置的电子邮件配置文件。 此更新包括可用于在 iOS 设备上对电子邮件通信进行签名和加密的 S/MIME 设置（“设备配置” > “配置文件” > “创建配置文件”> 选择“iOS”作为平台 >“电子邮件”作为配置文件类型）。
[iOS 电子邮件配置设置](email-settings-ios.md)列出了设置。

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>某些 BitLocker 设置支持 Windows 10 专业版<!-- 2727036 -->
你可以创建在 Windows 10 设备上设置 Endpoint Protection 设置的配置文件，包括 BitLocker。 此更新会为某些 BitLocker 设置添加对 Windows 10 专业版的支持。 若要查看这些保护设置，请转到[适用于 Windows 10 的 Endpoint protection 设置](endpoint-protection-windows-10.md#windows-encryption)。

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>Azure 门户中的共享设备配置将重命名为适用于 iOS 设备的“锁屏消息”<!-- 2809362 -->
创建适用于 iOS 设备的配置文件时，你可以添加“共享设备配置”设置以在锁屏上显示特定文本。 此更新包括以下更改： 
- Azure 门户中的“共享设备配置”设置将重命名为“锁定屏幕消息(仅限受监督的设备)”（“设备配置” > “配置文件” > “创建配置文件”> 选择“iOS”作为平台 > 选择“设备功能”作为配置文件类型 >“锁定屏幕消息”）。
- 添加锁屏消息时，可以插入序列号、设备名称或另一个特定于设备的值作为“资产标记信息”和“锁屏脚注”中的变量。 例如，可以使用大括号输入 `Device name: {{devicename}}` 或 `Serial number is {{serialnumber}}`。 [iOS 令牌](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list)列出了可用的令牌。
[用于在锁屏上显示消息的设置](shared-device-settings-ios.md)列出了设置。

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices----2827760--"></a>添加到 iOS 设备的新 App Store、文档查看和游戏设备限制设置 <!-- 2827760-->
在“设备配置” > “配置文件” > “创建配置文件” > 平台选择“iOS”> 配置文件类型选择“设备限制”>“App Store、文档查看和游戏”中，添加了以下设置：允许托管应用将联系人写入非托管联系人帐户。允许非托管应用从托管联系人帐户中读取联系人。要查看这些设置，请转到 [iOS 设备限制](device-restrictions-ios.md#app-store-doc-viewing-gaming)。

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Android Enterprise 设备所有者设备的新通知、提示和锁屏设置 <!-- 3201839 3201843 -->
以设备所有者身份运行时，此更新包括 Android Enterprise 设备上的多项新功能。 若要使用这些功能，请转到“设备配置” > “配置文件” > “创建配置文件”> 在“平台”中，选择“Android Enterprise” > 在“配置文件类型”中，选择“仅设备所有者” > “设备限制”。

新的功能包括： 

- 禁止显示系统通知，包括传入呼叫、系统警报、系统错误等。
- 建议跳过首次打开的应用的启动教程和提示。
- 禁用高级锁屏设置，例如照相机、通知、指纹解锁等。


若要查看这些设置，请转到 [Android Enterprise 设备限制设置](device-restrictions-android-for-work.md)。

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Android Enterprise 设备所有者设备可以使用 Always On VPN 连接 <!-- 3202194 -->
在此更新中，可以在 Android Enterprise 设备所有者设备上使用始终可用的 VPN 连接。 始终可用 VPN 连接一直保持连接状态，或在用户解锁设备、设备重启或无线网络更改时立即重新连接。 还可以将连接置于“锁定”模式，该模式会阻止所有网络流量，直到 VPN 连接处于活动状态。
可以在“设备配置” > “配置文件” > “创建配置文件” >  适用于平台的“Android 企业版”>“仅设备所有者”的“设备限制”>“连接”设置中启用始终可用的 VPN。 若要查看这些设置，请转到 [Android Enterprise 设备限制设置](device-restrictions-android-for-work.md)。

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Windows 10 设备上的任务管理器中的结束进程的新设置 <!-- 3285177 --> 
此更新包括使用 Windows 10 设备上的任务管理器的结束进程的新设置。 使用设备配置文件（“设备配置” > “配置文件” > “创建配置文件”> 在“平台”中，选择“Windows 10”> 在“配置文件类型”中，选择“设备限制” > “常规”设置），选择允许或阻止此设置。
若要查看这些设置，请转到 [Windows 10 设备限制设置](device-restrictions-windows-10.md)。
适用于：Windows 10 及更高版本


### <a name="device-enrollment"></a>设备注册

#### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564---"></a>更详细的注册限制失败消息传送 <!-- 3111564 -->
不满足注册限制时，会收到更详细的错误消息。 若要查看这些消息，请转到“Intune” > “故障排除”> 并检查“注册故障”表。 有关详细信息，请参阅[注册失败列表](help-desk-operators.md#enrollment-failure-reference)。

### <a name="monitor-and-troubleshoot"></a>监视和故障排除

#### <a name="tenant-status-dashboard-----1124854---"></a>租户状态仪表板  <!-- 1124854 -->
新[租户状态页](tenant-status.md)会提供一个位置，可以在其中查看租户状态和相关详情。  该仪表板分为 4 个区域：
- **租户详细信息** - 显示租户姓名和位置、MDM 机构、租户中的注册设备总数以及许可证计数等信息。 此部分还为租户列出当前服务版本。
- **连接器状态** - 显示有关已配置的可用连接器的信息，还可以列出尚未启用的连接器。  
   根据每个连接器的当前状态，将其标记为“正常”、“警告”或“不正常”。 选择要了解的连接器，并查看其详细信息或为其配置其他信息。
- **Intune 服务运行状况** - 显示租户活动事件或服务中断情况的详细信息。 该部分信息直接检索自 Office 消息中心。
- **Intune 新闻** - 显示租户的活动信息。 消息包括在租户收到最新 Intune 功能时的通知等。  该部分信息直接检索自 Office 消息中心。

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10----1488939--"></a>适用于 Windows 10 的公司门户的新“帮助和支持”体验 <!-- 1488939-->
新的公司门户“帮助和支持”页有助于用户针对应用和访问问题进行故障排除和请求帮助。 在新页面中，用户可以通过电子邮件发送错误和诊断日志的详细信息，并查找其组织的支持人员详细信息。 用户还可以查找常见问题解答部分，其中带有相关 Intune 文档的链接。 

#### <a name="new-help-and-support-experience-for-intune------3307080---"></a>Intune 的新的“帮助和支持”体验   <!-- #3307080 -->
我们将在未来几天向所有租户推出新的“帮助和支持”体验。 可以在 Intune 上进行此新体验，并且可以在使用 [Azure 门户](https://portal.azure.com/)中的“Intune”边栏选项卡时对其进行访问。
通过新体验，可以用自己的语言描述问题，并获得故障排除见解和基于 Web 的修复内容。 这些解决方案通过基于规则的机器学习算法提供并依赖于用户查询。 除特定于问题的指南之外，还会使用新的案例创建工作流通过电子邮件或电话打开支持案例。 此新体验取代了一组静态预选选项的先前的“帮助和支持”体验，这些选项基于打开“帮助和支持”时所在控制台的区域。 有关详细信息，请参阅[如何获取对 Microsoft Intune 的支持](get-support.md)。

### <a name="role-based-access-control"></a>基于角色的访问控制

#### <a name="scope-tags-for-apps----1081941---"></a>应用的作用域标记 <!-- 1081941 -->
可创建作用域标记来限制对角色和应用的访问。 可向应用添加作用域标记，以便只有具有特定角色（该角色也分配有该作用域标记）的人员才可以访问该应用。 目前，无法向从托管 Google Play 添加到 Intune 的应用或使用 Apple Volume Purchase Program (VPP) 购买的应用分配作用域标记（但计划在将来提供此支持）。 有关详细信息，请参阅[使用作用域标记筛选策略](scope-tags.md)。

## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]
