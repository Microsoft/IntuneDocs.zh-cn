---
title: 在开发的 Microsoft Intune
titlesuffix: ''
description: 中开发的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/29/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3e068e2c9834290b705e8e7bc2f895636415f9ba
ms.sourcegitcommit: 69aaf89140f82f344404e75a69dc59d8a1585b10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675436"
---
# <a name="in-development-for-microsoft-intune---april-2019"></a>在开发中 Microsoft Intune-2019 年 4 月

以帮助你准备和规划，此页列出了 Intune UI 更新和功能正在开发中，但尚未释放。 此外：

- 如果我们希望，您将需要采取措施在更改前的，我们将发布免费的 Office 消息中心文章。
- 当作为预览功能启动在生产中，或已公开发布，功能说明将移动关闭此页和到上[新增功能页](whats-new.md)。
- 此页并[新增功能页](whats-new.md)会定期更新。 返回查看其他更新。
- 请参阅[M365 路线图](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)战略可交付结果和时间线。

> [!Note]
> 这些项反映 Microsoft 的有关 Intune 功能在将来版本中的当前预期。 日期和各项功能可能会更改。 在开发过程中的不是所有项都具有此页上的功能说明。

**RSS 源**：通过将以下 URL 复制并粘贴到源阅读器中，可以在页面更新时收到通知：`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure 门户中的 Intune

<!-- 1904 start-->

### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083---"></a>设置登录名设置和控制 macOS 设备上的重新启动选项 <!-- 1210083 -->
在 macOS 设备上可以创建设备配置文件 (**设备配置** > **配置文件** > **创建配置文件**>选择**macOS**平台 >**设备功能**配置文件类型)。 新的登录窗口设置将包括多个项，例如显示自定义横幅，选择用户登录、 显示或隐藏的电源设置，和的详细信息。

若要查看当前设置，请转到[macOS 设备功能设置](macos-device-features-settings.md)。

适用于： macOS

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Windows Defender 防火墙高级的设置 <!-- 1311949 -->
你将很快能够使用 Intune 来管理 Windows Defender 的客户端上的自定义防火墙规则。 规则可以指定应用程序、 网络地址和端口的入站和出站行为。 

### <a name="require-app-protection-conditional-access----1634317---"></a>需要应用保护条件性访问  <!--1634317 -->
你将能够使用*需要应用保护策略*，这可确认策略会在登录完成以防止用户访问使用条件性访问所保护的数据之前应用到用户的应用。 虽然策略保障可能会减慢第一次的使用体验，它有助于防止出现网络问题、 管理配置错误、 或有意的工作以避免受到应用程序保护策略。 

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----16726660---"></a>部署获得许可的适用于企业的 Microsoft Store 联机应用 <!-- 16726660 -->
你将能够在设备上下文中分配所需的适用于企业的 Microsoft Store 联机应用，这些应用已获得许可。 如果以这种方式部署适用于企业的 Microsoft Store 应用，则可在设备上为所有用户安装该应用。 这仅适用于 Windows 10 RS4+ 桌面版设备。 对于获得许可的适用于企业的 Microsoft Store 联机应用，可在客户端应用分配页面中选择安装在设备上下文中。

### <a name="include-and-exclude-mixture-of-user-groups-and-device-groups-when-assigning-policies-and-profiles----1807547---"></a>包括和排除各种用户组和设备组分配策略和配置文件时 <!-- 1807547 -->
如果将分配符合性策略或配置文件，可以直接将其分配给安全组，与用户或设备。 目前，你可以包括和排除仅用户组，*或*包括和排除仅设备组。 您不能包括和排除的混合组，如包括用户组*和*排除设备组。

您可以包括和排除多个用户组和设备组。 可包含一组用户，并排除设备组。 例如，可以分配或将设备配置文件部署到一组用户，但排除个人设备。

[分配设备配置配置文件](device-profile-assign.md)包括将配置文件分配给用户组和设备组的详细信息。

适用于： 所有平台

### <a name="retire-noncompliant-devices----1827291---"></a>停用不符合要求的设备 <!-- 1827291 -->
我们要添加新的符合性操作停用的不符合要求的设备。 正在停用不符合要求的设备，删除所有公司数据并也由 Intune 管理中都删除设备。 此操作运行时达到配置的值以天为单位。 最小值为 30 天。 

### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>在 macOS 设备上配置内核扩展插件的设置 <!-- 2043024 -->
在 macOS 设备上可以创建设备配置文件 (**设备配置** > **配置文件** > **创建配置文件**>选择**macOS**平台)。 一组新的设置将允许你配置并在设备上使用内核扩展。

适用于：10.13.2 及更高版本

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>将配置文件配置为在“设置助手”期间跳过某些屏幕 <!-- 2276470 -->
创建 macOS 注册配置文件时，可将其配置为在用户使用设置助手期间跳过以下任一屏幕：
- Android 迁移
- 显示基调
- 隐私
- iCloudStorage：如果你新建或编辑配置文件，选定跳过屏幕需要与 Apple MDM 服务器同步。 用户可以发起手动同步设备，这样在选取配置文件变更时就不会有任何延迟。
有关详细信息，请参阅[通过设备注册计划或 Apple School Manager 自动注册 macOS 设备](device-enrollment-program-enroll-macos.md)。

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>设备用户可以查看他们已安装或尝试安装的所有托管应用程序 <!-- 2352913 -->
对于 Windows 公司门户将列出所有托管应用程序&ndash;必需和可用&ndash;用户的设备上安装的。 用户将能尝试查看和修改挂起的应用安装和及其当前状态。 如果你的组织不会进行应用，必需或可用，则用户将看到一条消息说明，安装了任何公司应用。 用户还可以进行排序或筛选其应用程序的安装状态。

### <a name="scope-tags-for-apple-vpp-tokens---2371886---"></a>Apple VPP 令牌的作用域标记 <!--2371886 -->
您可以将作用域标记添加到 Apple VPP 令牌。 仅分配有相同的作用域标记的用户将有权访问带有该标记的 Apple VPP 令牌。 VPP 应用和使用该令牌购买的电子书将继承其作用域标记。 有关作用域标记的详细信息，请参阅[使用 RBAC 和作用域标记](scope-tags.md)。

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>当使用"适用性规则"创建配置文件的 Windows 10 设备 <!-- 2549910 -->
创建 Windows 10 设备配置文件 (**设备配置** > **配置文件** > **创建配置文件** > **Windows 10**平台)。 你将能够创建**适用性规则**因此配置文件仅适用于特定版本或特定版本。 例如，你创建的配置文件，将启用某些 BitLocker 设置。 一旦添加配置文件，请使用适用性规则，因此该配置文件仅适用于运行 Windows 10 企业版的设备。

适用于： 
- Windows 10 及更高版本

### <a name="enable-win32-app-dependencies----2617348---"></a>启用 Win32 应用程序依赖关系 <!-- 2617348 -->
公共预览版-作为管理员，你可以要求安装 Win32 应用程序之前，作为依赖项安装其他应用。 具体而言，设备必须先安装 Win32 应用程序安装依赖应用程序。 仅在 Intune 管理代理已升级到 1904年 （或更高版本 1.18.120.0） 这可能需要 1 或 2 个其他周后我们为 1904年升级服务后，将可以使用此功能。 在 Intune 中，选择**客户端应用** > **应用** > **添加**显示**添加应用**边栏选项卡。 选择**Windows 应用程序 (Win32)** 作为**应用类型**。 有关详细信息，请参阅[Intune 独立版的 Win32 应用管理](apps-win32-app-management.md)。

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-connect-to-wi-fi-networks-on-android-enterprise-dedicated-devices-running-multi-app-kiosk-mode---3041940---"></a>Android 企业版设备所有者的新设备限制设置： 让用户连接到 Wi-fi 网络上运行多应用展台模式的专用的 Android 企业版设备 <!--3041940 -->
管理员可以进行切换的新设置，允许用户在运行多应用展台模式下其专用的 Android 企业设备上配置蓝牙。 若要查看在 Intune 控制台中此设置，请选择**Intune** > **设备配置** > **配置文件** >  **创建配置文件**> 选择**Android 企业版**平台 >**仅限设备所有者、 设备限制**配置文件类型 >**设置**  > **专用设备**> 选择**多应用**从**展台模式**设置下拉列表。 一个选项调用**Wi-fi 配置**将可用于启用。 

适用范围： Android 企业版专用运行多应用展台模式的设备。 

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-configure-bluetooth-and-pairing-on-android-enterprise-dedicated-devices---3041941---"></a>Android 企业版设备所有者的新设备限制设置： 让用户配置蓝牙和上专用的 Android 企业设备配对 <!--3041941 -->
管理员可以进行切换的新设置，允许用户在运行多应用展台模式下其专用的 Android 企业设备上配置蓝牙。 若要查看在 Intune 控制台中此设置，请选择**Intune** > **设备配置** > **配置文件** >  **创建配置文件**> 选择**Android 企业版**平台 >**仅限设备所有者、 设备限制**配置文件类型 >**设置**  > **专用设备**> 选择**多应用**从**展台模式**设置下拉列表。 一个选项调用**蓝牙配置**将可用于启用。 

适用范围： Android 企业版专用运行多应用展台模式的设备。 

### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>监视安全基线状态 （公共预览版） <!-- 3082047 --> 
当监视*设备状态*为你的安全基准，视图将状态按类别对组织基线，如*上面锁*， *BitLocker*，并且*浏览器*。 将表示所有可用的基线类别。 对于每个类别，你将看到设备的数量不匹配特定基线类别、 配置错误，或不适用。

###  <a name="intune-security-tasks-for-defender-atp-in-public-preview----3208597---"></a>Defender atp 的 Intune 安全任务 （在公共预览版） <!-- 3208597 -->
即将作为公共预览版，Intune 将很快安全任务为添加新公布的 Microsoft Defender 威胁和漏洞管理。  通过这种集成，安全操作管理员在 Windows Defender ATP (WDATP) 可以更有效地交流的新兴威胁到 Intune 管理员建议的修正。 添加安全任务将添加一种基于风险的方法来发现、 设置优先级和修正终结点的漏洞和配置错误。

若要了解有关在 Intune 中的安全任务的详细信息，请参阅博客文章有关[使用 Intune 安全任务来扩展 Microsoft Defender ATP 的威胁和漏洞管理](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-security-tasks-extend-Microsoft-Defender-ATP-s/ba-p/369857)。 

### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883---"></a>创建并在 Intune 中使用 OEMConfig 设备配置文件 <!-- 3305883 -->
Intune 将支持具有 OEMConfig 配置 Android 企业设备。 具体而言，可以创建设备配置文件，并将设置应用于使用 OEMConfig Android 企业设备 (**设备配置** > **配置文件** > **创建配置文件** > **Android 企业版**平台)。

在每个 OEM 的基础上当前的 Oem 的支持。 如果您想的 OEMConfig 应用中不可用的 OEMConfig 应用列表，请联系`IntuneOEMConfig@microsoft.com`。

适用于： 
- Android Enterprise

### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254---"></a>适用于 Android 企业版设备所有者的新设备限制设置 <!-- 3574254 -->
在 Android 企业设备，可以创建设备限制配置文件，以允许或限制功能、 设置密码规则和的详细信息 (**设备配置** > **配置文件** > **创建配置文件**> 选择**Android 企业版**平台 >**仅限设备所有者 > 设备限制**配置文件类型)。 

对于完全托管的设备，在 Google Play 商店中应用新设置，包括密码设置，它允许完全访问，将提供更多。 

要查看设置的当前列表，请转到[用于允许或限制功能的 Android Enterprise 设备设置](device-restrictions-android-for-work.md)。 

适用范围： Android 企业版完全受管理设备

### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>检查了在 Windows 10 设备符合性策略中的 TPM 芯片集 <!-- 3617671 -->
许多 Windows 10 和更高版本设备都有受信任的平台模块 (TPM) 芯片集。 新的符合性设置将检查 TPM 是否在设备上。

[Windows 10 和更高版本的符合性策略设置](compliance-policy-create-windows.md#windows-10-and-later-policy-settings)列出了当前设置。

适用于： 
- Windows 10 及更高版本

### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227---"></a>将 Win32 应用安装在已注册 Intune 上配置 Azure AD 加入设备 <!-- 3695227 -->
你将能够的分配 Win32 应用程序以安装在 Intune 上注册 Azure AD 加入设备。 有关在 Intune 中的 Win32 应用程序的详细信息，请参阅[Win32 应用管理](apps-win32-app-management.md)。

### <a name="windows-defender-advanced-threat-protection-baseline----3754134---"></a>Windows Defender 高级威胁防护基线 <!-- 3754134 -->
我们要添加新的基线来帮助你配置 Windows Defender 高级威胁防护设置。

### <a name="device-overview-shows-primary-user---794259---"></a>设备概览显示主要用户 <!--794259 -->
设备概述页将显示主要用户，也称为用户设备关联用户 (UDA)。 若要查看设备的主要用户，请选择**Intune** > **设备** > **所有设备**> 选择一台设备。 主要用户将显示在顶部附近**概述**页。

### <a name="expanded-support-for-android-enterprise-fully-managed-devices----3903241-3903244-3903246---"></a>完全托管的 Android 企业设备的扩展的支持 <!-- 3903241, 3903244, 3903246 -->
我们将展开的完全托管的 Android 企业设备的支持 ([2019 年 1 月首次发布](whats-new.md#week-of-january-14-2019)包括以下：
- 合规性
- 条件性访问
- 新的最终用户应用程序

若要设置完全托管的 Android 设备，请转到“设备注册” > “Android 注册” > “公司拥有的完全托管的用户设备”。 完全托管的 Android 设备仍保留在预览版，支持以及某些 Intune 功能可能无法完全正常运行。 

### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925---"></a>更多适用于 Android 企业版工作配置文件设备报告的托管 Google Play 应用 <!-- 4105925 -->
对于托管 Google Play 应用程序部署到 Android 企业版工作配置文件设备，它将可以查看在设备上安装的应用程序的特定版本号。 这适用于仅限所需应用。 将在将来的版本中启用相同的功能来提供应用。

### <a name="ios-third-party-keyboards----4111843---"></a>iOS 第三方键盘 <!-- 4111843 -->
支持 Intune 应用保护策略 （应用）**第三方键盘**设置将结束由于 iOS 平台更改。 你将不能在 Intune 管理控制台中配置此设置，并不将 Intune App SDK 中的客户端上实施它。

<!-- 1903 start-->

### <a name="block-users-from-scanning-for-windows-updates----3316758---"></a>阻止用户从 Windows 更新扫描 <!-- 3316758 -->
我们添加了可用于阻止用户从 Windows 更新扫描的新 Windows 更新环设置。 此设置不会在门户中，从可用，但可以使用 Intune Graph API 进行配置。

### <a name="windows-update-notifications----3316782---"></a>Windows 更新通知 <!-- 3316782 -->
我们添加了支持与 Windows 更新环配置以便你将能够配置您的用户看到的 Windows 更新通知。 此设置不会在门户中，从可用，但可以使用 Intune Graph API 进行配置。

### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>将 12 个设备用户更改为适用于 iOS 的公司门户注册 <!--3448635 --> 
将更新适用于 iOS 的公司门户应用注册屏幕和步骤与在 Apple iOS 12.2 中发布的 MDM 注册更改保持一致。 更新的工作流现在将提示用户：

- 允许使用 Safari 打开公司门户网站 （通过 Safari) 并返回到公司门户应用之前下载的管理配置文件。
- 打开设置应用在其设备上安装管理配置文件。
- 返回到完成注册的公司门户应用。

有关如何准备这些更改的详细信息，请参阅[Microsoft 技术社区文章](https://aka.ms/CP_changes_iOS12)。 在此期间，若要在公司门户中支持新的 iOS 注册，我们已更新中的步骤[在 Intune 中的注册 iOS 设备](https://docs.microsoft.com/en-us/intune/ios-enroll)。 Apple 发布 iOS 版本 12.2 后，这些文档更改都将实时。 

### <a name="easier-access-to-diagnostic-settings----3804627---"></a>更轻松地访问诊断设置 <!-- 3804627 -->
我们将添加到一个新选项**审核日志**边栏选项卡中可用于直接打开在 Intune 控制台中每个审核日志工作负载*诊断设置*页。

## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。


