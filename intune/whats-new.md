---
title: "Microsoft Intune 新增功能"
titlesuffix: Azure portal
description: "了解 Intune Azure 门户新增功能"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/01/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5058428dca9212d8b20364f58ac463939a699221
ms.sourcegitcommit: 6d69403266dbcb31c879432719798935c94917fa
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2018
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune 新增功能

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

了解 Microsoft Intune 每周新增功能。 另外，你还可以找到[即将发生的更改](#whats-coming)、有关服务的[重要说明](#notices)，以及有关[过去版本](whats-new-archive.md)的信息。

> [!Note]
> 有关混合移动设备管理 (MDM) 中新功能的信息，请参阅[混合新增功能页面](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。


<!-- Common categories:  
  ### Device enrollment
  ### Device management
  ### App management
  ### Device configuration
  ### Role-based access control
  ### Intune apps
  ### Monitor and troubleshoot

-->   

## <a name="week-of-february-5-2018"></a>2018 年 2 月 5 日开始的这一周

### <a name="device-enrollment"></a>设备注册

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625-eeready---"></a>新增了 Apple 批量注册所需的用户身份验证选项 <!-- 747625 eeready -->

> [!NOTE]
> 新租户可立即查看此功能。 对于现有租户，此功能将于四月推出。 此次推出完成之前，你可能无权访问这些新功能。

对于以下注册方法，Intune 现支持使用“公司门户”应用验证设备：

- Apple 设备注册计划
- Apple School Manager
- Apple Configurator 注册

使用“公司门户”选项时，可以强制执行 Azure Active Directory 多重身份验证，而不会屏蔽这些注册方法。

使用“公司门户”选项时，Intune 会跳过 iOS 设置助理中用于用户关联注册的用户身份验证。 也就是说，设备最初注册为无用户设备，因此不会接收用户组的配置或策略。 只会接收设备组的配置和策略。 不过，Intune 会在设备上自动安装“公司门户”应用。 首个启动并登录“公司门户”应用的用户将与 Intune 中的设备相关联。 此时，用户将会接收用户组的配置和策略。 只有重新注册，才能更改用户关联。

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685-eeready---"></a>Intune 支持多个 Apple DEP/Apple School Manager 帐户 <!-- 747685 eeready -->

Intune 现支持最多通过 100 个不同的 Apple 设备注册计划 (DEP) 或 Apple School Manager 帐户注册设备。 可以单独管理注册配置文件和设备的每个已上传令牌。 可以根据已上传的 DEP/ School Manager 令牌自动分配不同的注册配置文件。 如果上传了多个 School Manager 令牌，一次只能与 Microsoft 学校数据同步共享一个令牌。

迁移后，通过 Graph 管理 Apple DEP 或 ASM 的 beta 版本 Graph API 和已发布脚本将不再有效。 新的 beta 版本 Graph API 正在进行开发，将在迁移后发布。

### <a name="remote-printing-over-a-secure-network----1709994----"></a>通过安全网络远程打印 <!-- 1709994  -->
使用 PrinterOn 的无线移动打印解决方案，用户将可以随时随地通过安全网络进行远程打印。 PrinterOn 将集成适用于 iOS 和 Android 的 Intune APP SDK。 将可以通过管理控制台中的 Intune“应用保护策略”边栏选项卡，将应用保护策略定目标到此应用。 最终用户将能够通过 Play 商店或 iTunes 下载“PrinterOn for Microsoft”应用，以便在 Intune 生态系统内使用。

## <a name="week-of-january-29-2018"></a>2018 年 1 月 29 日当周

### <a name="device-enrollment"></a>设备注册

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>已到期令牌和即将到期令牌的警报 <!-- 1639263 -->
概述页现在显示已到期令牌和即将到期令牌的警报。 单击一个令牌的警报后，将转到令牌的详细信息页。  如果单击多个令牌的警报，将转到所有令牌及其状态的列表。 管理员应在到期日期之前续订令牌。

### <a name="device-management"></a>设备管理

#### <a name="remote-erase-command-support-for-macos-devices----1438084---"></a>macOS 设备的远程“清除”命令支持<!-- 1438084 -->

管理员可以对 macOS 设备远程发出清除命令。

> [!IMPORTANT]
> 由于清除命令无法撤消，因此应谨慎使用。

清除命令不仅会从设备中删除所有数据（包括操作系统）， 还会从 Intune 管理范围中删除设备。 不过，并不会向用户发出警告，而是在命令发出后立即执行清除操作。

必须配置 6 位恢复 PIN。 此 PIN 可用于解锁已清除的设备，此时将开始重新安装操作系统。 开始清除后，PIN 便会显示在 Intune 中设备概述边栏选项卡上的状态栏中。 只要清除正在进行中，PIN 就会一直显示。 清除完成后，设备便会从 Intune 管理范围中完全消失。 请务必记录恢复 PIN。这样一来，无论是谁恢复设备，都可以使用它。

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>撤销 iOS 批量采购计划令牌的许可证<!-- 820870 --> 
可以撤销给定 VPP 令牌的所有 iOS 批量采购计划 (VPP) 应用的许可证。

### <a name="app-management"></a>应用管理

#### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>撤销 iOS 批量采购计划应用<!-- 820863 -->
对于具有一个或多个 iOS 批量采购计划 (VPP) 应用的给定设备，可以撤销相关的基于设备的应用许可证。 撤销应用许可证将不会从设备中卸载相关的 VPP 应用。 若要卸载 VPP 应用，必须将分配操作更改为“卸载”。 有关详细信息，请参阅[如何使用 Microsoft Intune 管理通过批量采购计划购买的 iOS 应用](vpp-apps-ios.md)。

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>使用内置应用类型将 Office 365 移动应用分配到 iOS 和 Android 设备<!-- 1332318 -->
借助内置应用类型，可更轻松地创建 Office 365 应用并将其分配到管理的 iOS 和 Android 设备。 这些应用包括 Word、Excel、PowerPoint 和 OneDrive 等 Office 365 应用。 可将特定应用分配到应用类型并编辑应用信息配置。

#### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>根据组添加和排除应用分配 <!-- 1406920 -->

在应用分配期间以及在选择分配类型后，可以选择要包括和排除的组。

#### <a name="website-learning-mode----1631908---"></a>网站学习模式 <!-- 1631908 -->

Intune 现在具有 Windows 信息保护 (WIP) 学习模式扩展。 除了查看已启用 WIP 的应用的相关信息外，还可以查看与网站共享工作数据的设备的摘要。 通过此信息，可以确定应将哪些网站添加到组和用户 WIP 策略中。

#### <a name="approve-the-company-portal-app-for-android-for-work---1797090---"></a>审核适用于 Android for Work 的“公司门户”应用 <!--1797090 -->
如果组织使用 Android for Work，将需要手动审核适用于 Android 的“公司门户”应用，以便它能够继续从托管的 Google Play 商店接收自动更新。

#### <a name="faceid-on-ios-devices----1807377---"></a>iOS 设备上的 FaceID<!-- 1807377 -->
Intune 应用保护策略现在支持用于在 iOS 设备上控制 FaceID 的设置。 此设置适用于支持 FaceID 功能的设备（目前仅限 iPhone X）。 此设置与当前支持的 TouchID 控件相互独立。 组织可以选择是否信任 FaceID 作为有效的 PIN 提示，以将其作为 TouchID 控件的替代方式。

### <a name="device-configuration"></a>设备配置

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments-----1480316---"></a>可通过包括和排除分配来向组分配应用程序配置策略  <!-- 1480316 --> 

可通过结合使用包括分配和排除分配来向一组用户和设备分配应用程序配置策略。 可通过自定义选择组或虚拟组的方式来选择分配。 虚拟组包括“所有用户”、“所有设备”或“所有用户 + 所有设备”。

#### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>支持 Windows 10 版本升级策略 <!-- 903672(archived), 1119689 -->  
可以创建 Windows 10 版本升级策略，将 Windows 10 设备升级到 Windows 10 教育版、Windows 10 教育版 N、Windows 10 专业版、Windows 10 专业版 N、Windows 10 专业教育版和 Windows 10 专业教育版 N。有关 Windows 10 版本升级的详细信息，请参阅[如何配置 Windows 10 版本升级](edition-upgrade-configure-windows-10.md)。

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>适用于 Intune 的条件访问策略只能通过 Azure 门户访问 <!-- 1737088 1634311 -->

从本次发布开始，必须在 [Azure 门户](https://portal.azure.com)中通过“Azure Active Directory” > “条件访问”配置和管理“条件访问”策略。 为方便起见，还可在 Azure 门户中通过“Intune” > “条件访问”，从 Intune 访问此边栏选项卡。

#### <a name="updates-to-compliance-emails---1637547---"></a>更新了符合性电子邮件 <!--1637547 -->

通过发送电子邮件来报告不符合设备时，将包括不符合设备的详细信息。 


## <a name="week-of-january-22-2018"></a>2018 年 1 月 22 日当周

### <a name="intune-apps"></a>Intune 应用

#### <a name="new-functionality-for-the-resolve-action-for-android-devices---1583480--"></a>Android 设备的“解决”操作的新功能 <!--1583480-->

适用于 Android 的公司门户应用正在展开更新设备设置的“解决”操作，从而解决[设备加密问题](/intune-user-help/encrypt-your-device-android)。

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>适用于 Windows 10 的公司门户应用中提供远程锁定 <!--676506-->
最终用户现在可以从适用于 Windows 10 的公司门户应用远程锁定他们的设备。 此功能将不会为他们当前使用的本地设备显示。

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>可以更轻松地解决适用于 Windows 10 的“公司门户”应用的符合性问题 <!--676546-->
使用 Windows 设备的最终用户将能够点击“公司门户”应用中的不符合原因。 在可能的情况下，此操作会使用户直接转到“设置”应用中的适当位置，以修复问题。

## <a name="week-of-december-11-2017"></a>2017 年 12 月 11 日当周

### <a name="device-configuration"></a>设备配置

#### <a name="new-automatic-redeployment-setting----1469168---"></a>新的自动重新部署设置<!-- 1469168 -->
使用“自动重新部署”设置，具有管理权限的用户可在设备锁定屏幕上使用 CTRL+Win+R 删除所有用户数据和设置。 设备会自动进行重新配置并重新注册到管理。 此设置可在“Windows 10”>“设备限制”>“常规”>“自动重新部署”中找到。 有关详细信息，请参阅[适用于 Windows 10 的 Intune 设备限制设置](device-restrictions-windows-10.md#general)。

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy-----903672--1119689---"></a>支持在 Windows 10 版本升级策略中指定其他源版本  <!-- 903672,  1119689 -->
现在可以使用 Windows 10 版本升级策略从其他 Windows 10 版本（Windows 10 专业版、Windows 10 专业教育版、Windows 10 云端版等）升级。 在此版本发布前，支持的版本升级路径更加受限。 有关详细信息，请参阅[如何配置 Windows 10 版本升级](edition-upgrade-configure-windows-10.md)。

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>新的 Windows Defender 安全中心 (WDSC) 设备配置文件设置<!-- 1335507 -->

Intune 在名为“Windows Defender 安全中心”的端点保护下添加了一个新的设备配置文件设置部分。 IT 管理员可以配置最终用户能访问 Windows Defender 安全中心应用的支柱类型。 如果 IT 管理员在 Windows Defender 安全中心应用中隐藏支柱，则与隐藏支柱相关的所有通知都不会显示在用户设备上。

以下是管理员可以在 Windows Defender 安全中心设备配置文件设置中隐藏的支柱：
- 病毒和威胁防护
- 设备性能和运行状况
- 防火墙和网络保护
- 应用和浏览器控制
- 产品系列选项

IT 管理员还可以自定义用户接收的通知。 例如，你可以配置用户是接收由 WDSC 中的可见支柱生成的所有通知还是仅接收关键通知。 非关键通知包括 Windows Defender 防病毒活动的周期性摘要以及扫描完成时的通知。 所有其他通知被视为是关键通知。 另外，还可以自定义通知内容，例如，可以提供 IT 联系信息以嵌入用户设备上显示的通知。

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling----1361755---"></a>SCEP 和 PFX 证书处理的多个连接器支持<!-- 1361755 -->

使用本地 NDES 连接器向设备提供证书的客户现在可以在一个租户中配置多个连接器。

这项新功能支持以下方案：

- 高可用性

每个 NDES 连接器从 Intune 中拉取证书请求。  如果一个 NDES 连接器脱机，另一个连接器可以继续处理请求。

#### <a name="customer-subject-name-can-use-aaddeviceid-variable-----1468599---"></a>客户的使用者名称可以使用 AAD_DEVICE_ID 变量  <!-- 1468599 -->

在 Intune 中创建 SCEP 证书配置文件时，现在可以使用 AAD_DEVICE_ID 变量生成自定义使用者名称。   如果使用此 SCEP 配置文件请求获取证书，这个变量会被替换为发出证书请求的设备的 AAD 设备 ID。


### <a name="device-management"></a>设备管理

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747---"></a>使用 Intune 的设备符合性引擎管理 Jamf 注册的 macOS 设备<!-- 1592747 -->
现在可以使用 Jamf 将 macOS 设备状态信息发送到 Intune。然后，Intune 会评估它与 Intune 控制台中定义的策略的符合性。 基于设备符合性状态以及其他条件（如位置、用户风险等），条件访问将强制实现 macOS 设备访问云和与 Azure AD 连接的本地应用程序（包括 Office 365）的符合性。 详细了解如何[设置 Jamf 集成](conditional-access-integrate-jamf.md)和[强制 Jamf 托管设备遵守策略](conditional-access-assign-jamf.md)。

#### <a name="new-ios-device-action------1424701---"></a>新的 iOS 设备操作<!-- 1424701 -->

现在可以关闭 iOS 10.3 监管的设备。 此操作会立即关闭设备，而不会向最终用户发出警告。 当你在“设备”工作负载中选择设备时，可以在设备属性中找到“关闭（仅监督）”操作。

#### <a name="disallow-datetime-changes-to-samsung-knox-devices----1468103---"></a>禁止对 Samsung Knox 设备更改日期/时间 <!-- 1468103 -->

现在可在 Samsung Knox 设备上阻止日期和时间更改。 此功能位于“设备配置文件” > “设备限制(Android)” > “常规”中。

#### <a name="surface-hub-resource-account-supported----1566442----"></a>支持的 Surface Hub 资源帐户<!-- 1566442  -->

我们新增了一项设备操作，以便管理员能够定义和更新与 Surface Hub 关联的资源帐户。

资源帐户由 Surface Hub 用于通过 Skype/Exchange 进行身份验证，以便它可以加入会议。 可以创建一个唯一的资源帐户，以使 Surface Hub 作为会议室出现在会议中。 例如，资源帐户可能会显示为“会议室 B41/6233”。 通常需要针对会议室位置以及何时需要更改其他资源帐户参数来配置 Surface Hub 的资源帐户（称为设备帐户）。

如果管理员需要更新设备上的资源帐户，他们必须提供与该设备关联的当前 Active Directory/Azure Active Directory 凭据。 如果为设备启用了密码轮换，则管理员必须转到 Azure Active Directory 以查找密码。

> [!NOTE]
> 所有字段都会向下发送到一个包中，覆盖之前配置的所有字段。 空字段也会覆盖现有字段。

以下是管理员可以配置的设置：

- 资源帐户
   - **Active Directory 用户**

      域名\用户名或用户主体名称 (UPN)：user@domainname.com

   - **密码**

- 可选的资源帐户参数（必须使用指定的资源帐户设置）

   - **密码轮转周期**

     出于安全原因，确保帐户密码每周由 Surface Hub 自动更新。 在启用此功能之后，要配置任何参数，Azure Active Directory 中的帐户必须先进行密码重置。

   - **SIP (会话初始协议)地址**

     仅在自动发现失败时使用。

   - **Email**

     设备/资源帐户的电子邮件地址。

   - **Exchange Server**

     仅在自动发现失败时需要。

   - **日历同步**

     指定是否启用日历同步和其他 Exchange Server 服务。 例如：会议同步。

#### <a name="install-office-apps-on-macos-devices----1494311---"></a>在 macOS 设备上安装 Office 应用<!-- 1494311 -->
现在可以在 macOS 设备上安装 Office 应用。 使用此新应用类型，可以安装 Word、Excel、PowerPoint、Outlook 和 OneNote。 这些应用还随附 Microsoft AutoUpdate (MAU)，有助于保护和不断更新应用。

### <a name="app-management"></a>应用管理

#### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>删除 iOS 批量采购计划令牌<!-- 820879 -->
可以使用控制台删除 iOS Volume Purchase Program (VPP) 令牌。 当你有重复的 VPP 令牌实例时，可能需要执行此操作。

### <a name="intune-apps"></a>Intune 应用

#### <a name="end-user-messaging-for-accounts---1573558-for-1712--"></a>最终用户因帐户看到的消息 <!--1573558 for 1712-->

“公司门户”网站的用户被禁止执行必须对租户拥有写权限的操作。 他们会看到相应错误消息，指明其帐户处于维护状态。 适用于 Android、iOS、macOS 和 Windows 的“公司门户”应用即将发生类似更改。 可以在[应用 UI 最近更新](whats-new-app-ui.md)页中看到此错误。



### <a name="role-based-access-control"></a>基于角色的访问控制

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1667026---"></a>名为“当前用户”的新实体集合仅限于当前活动的用户数据<!-- 1667026 -->

User 实体集合包含企业中分配有许可证的所有 Azure Active Directory (Azure AD) 用户。 例如，在上个月期间，可能将某个用户添加到 Intune 然后又将其删除。 尽管在提交报告时该用户已不存在，但在数据中仍然会显示该用户及其状态。 可以创建一个报告，该报告将显示用户的历史记录在你的数据中存在的持续时间。

相比之下，新的“当前用户”实体集合只包含尚未被删除的用户。 “当前用户”实体集合仅包含当前活动的用户。 有关“当前用户”实体集合的信息，请参阅[引用当前用户实体](reports-ref-current-user.md)。


### <a name="updated-graph-apis----1736360---"></a>更新了 Graph API <!-- 1736360 -->

我们更新了一些适用于 Intune 且处于 beta 阶段的图形 API。 有关详细信息，请查看每月的[图形 API 更改日志](https://developer.microsoft.com/graph/docs/concepts/changelog)。


## <a name="week-of-december-4-2017"></a>2017 年 12 月 4 日当周

### <a name="monitor-and-troubleshoot"></a>监视和故障排除

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>Intune 支持 Windows 信息保护 (WIP) 拒绝的应用<!-- 1479103 -->
可在 Intune 中指定已拒绝的应用。 如果某个应用被拒，它会被阻止访问公司信息，允许的应用列表则与此相反。 有关详细信息，请参阅 [Recommended deny list for Windows Information Protection](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection)（Windows 信息保护的推荐拒绝列表）。


## <a name="week-of-november-27-2017"></a>2017 年 11 月 27 日当周

### <a name="device-enrollment"></a>设备注册

#### <a name="troubleshoot-enrollment-issues-----746324---"></a>排查注册问题<!-- 746324 -->

“疑难解答”工作区现在显示用户注册问题。 问题的相关详细信息和建议的修正步骤可帮助管理员和支持人员排查问题。 某些注册问题可能无法捕获，还有某些错误可能没有修正建议。

#### <a name="group-assigned-enrollment-restrictions----747598---"></a>组分配注册限制 <!-- 747598 -->

作为 Intune 管理员，现在可[为用户组创建自定义设备类型和设备限制注册限制](enrollment-restrictions-set.md)。

使用 Intune Azure 门户，每种限制类型最多可创建 25 个实例，然后这些实例可分配给用户组。 组分配限制会替代默认限制。

所有限制类型实例均保存在严格有序的列表中。 此顺序定义冲突解决的优先级值。 受多个限制实例影响的用户仅受优先级值最高的实例限制。 通过将给定实例拖至列表中其他位置，可更改其优先级。

将 Android for Work 设置从 Android For Work 注册菜单迁移到注册限制菜单时，会随之发布此功能。 由于这种迁移可能需要几天时间，帐户可能会在 11 月版本的其他部分中升级，然后才能看到已为注册限制启用组分配。

#### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>支持多个网络设备注册服务 (NDES) 连接器 <!-- 1528104 -->

NDES 允许无域凭据运行的移动设备基于简单证书注册协议 (SCEP) 获取证书。
利用此更新可支持多个 NDES 连接器。

#### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>独立于 Android 设备管理 Android for Work 设备 <!-- 1490731 EEready-->

注意：以下更改随 11 月更新一起推出，但可能需要一些时间才能在你的帐户上执行。 当帐户可使用这些更改时，你会在 Office 365 门户中收到确认通知。 推出后，你将拥有其他可管理性选项。 在推出期间，最终用户体验未作任何更改。

Intune 支持独立于 Android 平台管理 Android for Work 设备的注册。 这些设置位于“设备注册” > “注册限制” > “设备类型限制”下。 （这些设置之前位于“设备注册” > “Android for Work 注册” > “Android for Work 注册设置”下。）

默认情况下，Android for Work 设备的设置与 Android 设备的设置相同。 但是，更改 Android for Work 设置后则不再相同。

如果阻止个人 Android for Work 注册，那么仅公司 Android 设备可注册为 Android for Work。

使用新设置时，请考虑下列几点：

##### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>如果之前从未载入 Android for Work 注册

默认设备类型限制将阻止新的 Android for Work 平台。 载入该功能后，可允许设备注册 Android for Work。 为此，请更改默认值或新建一个设备类型限制，取代默认设备类型限制。

##### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>如果已载入 Android for Work 注册

如果之前已载入，那么情况取决于所选设置：

| Setting | 默认设备类型限制中的 Android for Work 状态 | 注意 |
| --- | --- | --- |
| **将所有设备作为 Android 管理** | 已阻止 | 所有 Android 设备均不注册 Android for Work。 |
| 将受支持设备作为 Android for Work 管理 | ，然后用户才能访问 | 所有支持 Android for Work 的 Android 设备均须注册 Android for Work。 |
| **仅为这些组中的用户将受支持设备作为 Android for Work 管理** | 已阻止 | 创建单独的设备类型限制策略替代默认值。 此策略将之前选择的组定义为允许 Android for Work 注册。 允许所选组中的用户继续注册 Android for Work 设备。 所有其他用户则不能注册 Android for Work。 |

所有情况下都将保留预期规则。 对你来说，无需任何操作即可维护环境中的 Android for Work 全局或按组允许。

### <a name="app-management"></a>应用管理

#### <a name="app-install-report-updated-to-include-install-pending-status----1249446---"></a>应用安装报表已更新以包括安装挂起状态 <!-- 1249446 -->  

通过“移动应用”工作负荷中的“应用”列表，可获取每个应用的“应用安装状态”报表，该报表现在包括用户和设备的“安装挂起”计数。

#### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>移动威胁检测的 iOS 11 应用清单 API <!-- 1391759 -->

Intune 从个人和公司所有的设备收集应用清单信息，这些信息可供移动威胁检测 (MTD) 提取，例如 Lookout for Work。 可通过 iOS 11+ 设备的用户收集应用清单。

**应用清单**  
清单（来自公司所有的 iOS 11+ 和个人所有的设备）将发送给 MTD 服务提供程序。 应用清单中的数据包括：

 - 应用 ID
 - 应用版本
 - 应用内部版本号
 - 应用程序名称
 - 应用程序包大小
 - 应用动态大小
 - 应用是否经过验证
 - 应用是否受管理


### <a name="device-management"></a>设备管理

#### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone----1463747-wnready---"></a>将混合 MDM 用户及其设备迁移至 Intune 独立版<!-- 1463747 wnready -->
现有新的流程和工具可用于将混合 MDM 的用户及其设备迁移至 Azure 门户中的 Intune，这可让你执行以下任务：
- 将 Configuration Manager 控制台中的策略和配置文件复制到 Azure 门户中的 Intune
- 将一部分用户移至 Azure 门户中的 Intune，同时将剩余用户保留在混合 MDM 中
- 将设备迁移至 Azure 门户中的 Intune，而无需重新注册这些设备

有关详细信息，请参阅[将混合 MDM 用户及其设备迁移至 Intune 独立版](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)。

#### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>本地 Exchange 连接器高可用性支持 <!-- 676614 -->
使用指定的 CAS 建立与 Exchange 的连接后，Exchange 连接器现在可以发现其他 CAS。 如果主 CAS 不可用，在主 CAS 的故障修复前，连接器会先故障转移到其他可用的 CAS。 有关详细信息，请参阅[本地 Exchange 连接器高可用性支持](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support)。

#### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>远程重启 iOS 设备（仅限被监督的设备）<!-- 1424595 -->

可使用设备操作触发受监督的 iOS 10.3+ 设备重启。 要详细了解如何使用设备重启操作，请参阅[使用 Intune 远程重启设备](device-restart.md)。

> [!Note]
> 此命令需要受监督的设备和“设备锁定”访问权限。 设备会立即重启。 密码锁定的 iOS 设备重启后不会重新加入 Wi-Fi 网络；重启后，它们可能无法与服务器进行通信。

#### <a name="single-sign-on-support-for-ios----1333645---"></a>iOS 的单一登录支持 <!-- 1333645 -->  

可对 iOS 用户使用 SSO。 编码为在单一登录有效负载中查找用户凭据的 iOS 应用可使用此有效负载配置更新。 还可使用 UPN 和 Intune 设备 ID 配置主体名称和领域。 有关详细信息，请参阅[配置 Intune for iOS 设备 SSO](sso-ios.md)。

#### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>为个人设备添加“查找我的 iPhone” <!--1427287-->
现可查看 iOS 设备是否已开启“激活锁”。 经典门户中的 Intune 之前并不提供此功能。


#### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>使用 Intune 远程锁定受管理的 macOS 设备 <!-- 1437691 -->

可锁定丢失的 macOS 设备并设置 6 位数的恢复 PIN。 锁定时，“设备概述”边栏选项卡会显示 PIN，直到发送另一个设备操作。

有关详细信息，请参阅[使用 Intune 远程锁定受管理设备](device-remote-lock.md)。

#### <a name="new-scep-profile-details-supported----1559808---"></a>支持新的 SCEP 配置文件详细信息 <!-- 1559808 -->

在 Windows、iOS、macOS 和 Android 平台上创建 SCEP 配置文件时，管理员现可设置其他设置。  管理员可设置 IMEI、序列号或公用名，包括采用使用者名称格式的电子邮件。

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

#### <a name="retain-data-during-a-factory-reset----1588489---"></a>在恢复出厂设置过程中保留数据 <!--1588489 -->
将 Windows 10 版本 1709 及更高版本重置为出厂设置时，可使用新功能。 管理员可指定在恢复出厂设置过程中，是否将设备注册和其他配置数据保留在设备上。

恢复出厂设置过程中保留以下数据：
- 与设备关联的用户帐户
- 计算机状态（域加入，已加入 Azure Active Directory）
- MDM 注册
- OEM 安装的应用（存储和 Win32 应用）
- 用户配置文件
- 用户配置文件以外的用户数据
- 用户自动登录

不保留以下数据：
- 用户文件
- 用户安装的应用（存储和 Win32 应用）
- 非默认设备设置

### <a name="monitor-and-troubleshoot"></a>监视和故障排除
#### <a name="window-10-update-ring-assignments-are-displayed----1621837---"></a>显示 Windows 10 更新通道分配<!-- 1621837 -->
进行故障排除时，对于正在查看的用户，可看到任何 Windows 10 更新通道分配。  

#### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings-----1455974----"></a>Windows Defender 高级威胁防护报告频率设置 <!-- 1455974  -->
Windows Defender 高级威胁防护 (WDATP) 服务允许管理员对受管理设备的报告频率进行管理。 借助新的“提高遥测报告频率”选项，WDATP 可提高收集数据和评估风险的频率。 报告的默认值可优化速度和性能。 提高报告频率十分适合高风险设备。 在“设备配置”的“Windows Defender ATP”配置文件中可找到此设置。

#### <a name="audit-updates----1412961---"></a>审核更新 <!-- 1412961 -->  
Intune 审核提供与 Intune 相关的更改操作记录。  捕获所有创建、更新、删除和远程任务操作，并保留一年。  通过 Azure 门户，可查看每个工作负荷中过去 30 天的审核数据，还可对这些数据进行筛选。  利用相应的图形 API，可检索过去一年存储的审核数据。

“审核”位于“监视”组下。 每个工作负荷都有一个“审核日志”菜单项。




## <a name="week-of-november-20-2017"></a>2017 年 11 月 20 日当周

### <a name="app-management"></a>应用管理

#### <a name="google-play-protect-support-on-android----908720---"></a>Android 上的 Google Play Protect 支持 <!-- 908720 -->

随着 Android Oreo 的发布，Google 引入了一系列名为 Google Play Protect 的安全功能，以便用户和组织可以运行安全的应用和 Android 映像。 Intune 现支持 Google Play Protect 功能，包括 SafetyNet 远程认证。 管理员可以设置符合性策略要求，要求配置和正常运行 Google Play Protect。
“SafetyNet 设备认证”设置要求设备连接到 Google 服务，以验证设备是否正常运行且未遭到入侵。 管理员还可以对 Android for Work 设置配置文件设置，以要求 Google Play 服务对已安装的应用进行验证。 如果设备不符合 Google Play Protect 要求，条件访问可能会阻止用户访问公司资源。

- 了解[如何创建用于启用 Google Play 保护的设备符合性策略](https://docs.microsoft.com/intune/compliance-policy-create-google-play-protect)。

#### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>允许受管理应用发送文本协议 <!-- 1414050  -->

由 Intune App SDK 管理的应用可发送短信。

## <a name="week-of-november-13-2017"></a>2017 年 11 月 13 日当周

### <a name="intune-apps"></a>Intune 应用
#### <a name="company-portal-app-for-macos-is-available---1541700--"></a>现已提供适用于 macOS 的公司门户应用 <!--1541700-->
macOS 上的 Intune 公司门户提供了经过优化的更新体验，可以清楚地显示用户所需要的针对已注册的所有设备的所有信息和符合性通知。 而且，Intune 公司门户部署到设备后，Microsoft AutoUpdate for macOS 将为其提供更新。 从 macOS 设备登录到 Intune 公司门户网站，可以下载适用于 macOS 的新 Intune 公司门户。

#### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps-----1248473---"></a>Microsoft Planner 现在属于已批准应用的移动应用管理 (MAM) 列表的一部分<!-- 1248473 -->
适用于 iOS 和 Android 的 Microsoft Planner 应用现在属于已批准应用的移动应用管理 (MAM) 列表的一部分。 可以通过 Azure 门户中的“Intune 应用保护”边栏选项卡为所有租户配置应用。
- 了解有关[已批准应用的 MAM 列表](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)的详细信息。

#### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices------1547061---"></a>iOS 设备上的每个应用程序 VPN 要求更新频率<!-- 1547061 -->  
管理员现在可以删除 iOS 设备上应用程序的每个应用程序 VPN 要求；受影响的设备将在下一次 Intune 签入后更新，通常在 15 分钟内发生。  

### <a name="monitor-and-troubleshoot"></a>监视和故障排除
#### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>支持适用于 Exchange 连接器的 System Center Operations Manager 管理包<!-- 885457 -->
现已提供适用于 Exchange 连接器的 System Center Operations Manager (SCOM) 管理包帮助你分析 Exchange 连接器日志。 在你需要进行故障排除时，此功能可提供多种监视该服务的方式。

## <a name="week-of-november-6-2017"></a>2017 年 11 月 6 日当周

### <a name="device-enrollment"></a>设备注册
#### <a name="co-management-for-windows-10-devices-----1243445---"></a>适用于 Windows 10 设备的共同管理<!-- 1243445 -->
共同管理是一种解决方案，可在传统管理与现代管理之间架起一座桥梁，为你提供利用分阶段的方法实现转换的途径。 共同管理本质上是一种解决方案，其中 Configuration Manager 和 Microsoft Intune 同时管理 Windows 10 设备，并且这些设备可联接到 Active Directory (AD) 和 Azure Active Directory (Azure AD)。  此配置提供以适合组织的步调（如果无法即刻完成所有迁移）逐步实现现代化的方式。  

#### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>通过 OS 版本限制 Windows 注册<!-- 245498 -->
作为 Intune 管理员，现在可为设备注册指定 Windows 10 的最低和最高版本。 可以在“平台配置”边栏选项卡中设置这些限制。

Intune 将继续支持 Windows 8.1 电脑和手机注册。 但只有对 Windows 10 才可设置最高和最低版本限制。 若要允许注册 8.1 设备，请将最低限制留空。

#### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Windows AutoPilot 未分配设备警报<!-- 1631236 -->
在“Microsoft Intune” > “设备注册” > “概述”页中，为 Windows AutoPilot 未分配设备提供了一个新警报。 此警报显示有多少来自 AutoPilot 计划的设备尚未分配 AutoPilot 部署配置文件。 使用警报中的信息可创建配置文件，并将其分配到未分配的设备。 单击警报时，会看到 Windows AutoPilot 设备的完整列表，以及与之相关的详细信息。 有关详细信息，请参阅[使用 Windows AutoPilot Deployment 计划注册 Windows 设备](https://docs.microsoft.com/intune/enrollment-autopilot)。

### <a name="device-management"></a>设备管理

#### <a name="refresh-button-for-devices-list-------1333581---"></a>设备列表的刷新按钮 <!-- 1333581 -->
由于设备列表不会自动刷新，可使用新的“刷新”按钮来更新列表中显示的设备。

#### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>对 Symantec 云证书颁发机构 (CA) 的支持<!-- 1333638 -->    
Intune 现在支持 Symantec 云 CA，允许 Intune 证书连接器从 Symantec 云 CA 向 Intune 受管理设备颁发 PKCS 证书。 如果现已将 Intune 证书连接器和 Microsoft 证书颁发机构 (CA) 配合使用，则可以利用现有 Intune 证书连接器设置添加 Symantec CA 支持。

#### <a name="new-items-added-to-device-inventory-----1404455---"></a>添加到设备清单的新项目<!--1404455 -->
以下新项目现在适用于[由已注册设备获取的清单](device-inventory.md)：

- Wi-Fi MAC 地址
- 总存储空间
- 总可用空间
- MEID
- 订阅者运营商


### <a name="app-management"></a>应用管理
#### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>通过在设备上定义最低 Android 安全修补程序版本设置对应用的访问权限<!-- 1278463 -->   
管理员可定义最低 Android 安全修补程序版本，必须在设备上安装该修补程序才能访问托管帐户下的托管应用程序。

> [!Note]  
> 此功能仅适用于在安装了 Android 6.0 及更高版本的设备上限制由 Google 发布的安全修补程序。

#### <a name="app-conditional-launch-support----1193313---"></a>应用条件启动支持<!-- 1193313 -->
IT 管理员现可通过 Azure 管理门户设置要求，通过移动应用管理 (MAM) 强制要求在应用程序启动时输入密码，而不是输入数字 PIN。 如果进行此配置，在访问启用 MAM 的应用程序前，用户需要在出现提示时设置并使用密码。 密码是至少包含一个特殊字符或大写/小写字母的数字 PIN。 此版本的 Intune 仅在 iOS 上支持此功能。 Intune 对密码的支持与支持数字 PIN 类似，设置了最短长度并且允许重复字符和序列。 该功能需要一些应用程序（例如 WXP、Outlook、Managed Browser、Yammer）的参与，将 Intune APP SDK 与代码集成，以便此功能准备就绪并在目标应用程序中强制实施密码设置。

#### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>设备安装状态报告中业务线应用的应用版本号<!-- 1233999 -->
在此版本中，设备安装状态报告显示适用于 iOS 和 Android 的业务线应用的应用版本号。 可使用此信息对应用进行故障排除，或者查找正在运行过时应用版本的设备。


### <a name="device-configuration"></a>设备配置
#### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>管理员现在可以使用设备配置文件在设备上配置防火墙设置<!-- 951708 -->   
管理员可以启用防火墙，还可以为域、专用网络和公用网络配置多种协议。  可在“Endpoint Protection”配置文件中找到这些防火墙设置。

#### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>Windows Defender 应用程序防护根据组织的定义，帮助阻止设备访问不受信任的网站<!-- 958257 -->   
利用 Windows 信息保护工作流或设备配置下的新“网络边界”配置文件，管理员可将站点定义为“受信任站点”或“公司站点”。 如果使用 Microsoft Edge 访问未在 64 位 Windows 10 设备的受信任网络边界中列出的站点，这些站点将转为在 Hyper-V 虚拟计算机内的浏览器中打开。

可在设备配置文件“Endpoint Protection”中找到应用程序防护。 管理员可在其中配置虚拟化浏览器与主机，以及非受信任站点与受信任站点之间的交互，同时存储虚拟化浏览器中生成的数据。 要在设备上使用应用程序防护，首先必须配置网络边界。 仅可为每个设备定义一个网络边界，这一点非常重要。  

#### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>Windows 10 企业版上的 Windows Defender 应用程序控制提供仅信任经授权应用的模式<!-- 1031096 -->    
由于每天都有成千上万个新恶意文件生成，因此使用基于签名的防病毒检测来抵御恶意软件可能无法再针对新型攻击提供足够的防御。 通过在 Windows 10 企业版上使用 Windows Defender 应用程序控制，可以更改设备配置，从信任防病毒软件或其他安全解决方案未阻止的所有应用的模式，更改为操作系统仅信任经企业授权的应用的模式。 可在 Windows Defender 应用程序控制中将信任分配给应用。

利用 Intune，可以在“仅审核”模式或强制执行模式下配置应用程序控制策略。 在“仅审核”模式下运行的应用不会受到阻止。 “仅审核”模式在本地客户端日志中记录所有事件。 还可以配置是仅允许运行 Windows 组件和 Microsoft Store 应用，还是允许运行 Intelligent Security Graph 定义的信誉良好的其他应用。

#### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>Windows Defender 攻击防护是面向 Windows 10 的一组新入侵防护功能<!-- 1063615 -->   
Windows Defender 攻击防护内含自定义规则，可降低应用程序受到攻击的可能性、预防宏和脚本威胁、自动阻止网络连接到可信度较低的 IP 地址，以及保护数据免受勒索软件和未知威胁的攻击。 Windows Defender 攻击防护包含以下组成部分：

- “攻击面减少(ASR)”提供用于预防宏、脚本和电子邮件威胁的规则。
- “控制文件夹访问”可自动阻止访问受保护文件夹中的内容。
- “网络筛选器”可阻止从任何应用到低可信度 IP/域的出站连接
- “攻击防护”提供内存、控制流和策略限制，可用于保护应用程序免受攻击。


#### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices----790537---"></a>在 Intune 中管理 PowerShell 脚本以供 Windows 10 设备使用<!-- 790537 -->

Intune 管理扩展允许你在 Intune 中上传 PowerShell 脚本以在 Windows 10 设备上运行。 扩展对 Windows 10 移动设备管理 (MDM) 功能进行了补充，使你可更轻松地采用新式管理。 有关详细信息，请参阅[在 Intune 中管理 PowerShell 脚本以供 Windows 10 设备使用](intune-management-extension.md)。

#### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>适用于 Windows 10 的 Intune 新设备限制设置<!-- 1308850 -->
-    消息传送（仅限移动设备）- 禁用测试或 MMS 消息
-    密码 - 此设置用于启用 FIPS，并且支持使用 Windows Hello 设备辅助设备进行身份验证 
-    显示 - 此设置用于打开或关闭旧版应用的 GDI 缩放

#### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Windows 10 设备的展台模式限制<!-- 1308872 -->   
可将 Windows 10 设备的用户限制为使用展台模式，从而限制这些用户仅使用一组预定义的应用。  为此，需创建 Windows 10 设备限制配置文件并设置展台设置。

展台模式支持两种模式：“单应用”模式（仅允许用户运行一个应用）或“多应用”模式（允许访问多个应用）。  可定义用户帐户和设备名，确定受支持的应用。  用户登录时，仅可访问定义的应用。  有关详细信息，请参阅 [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)。 

展台模式要求：

- MDM 机构必须是 Intune。
- 必须已在目标设备上安装应用。
- 设备必须[正确预配](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions)。

#### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>用于创建网络边界的新设备配置文件<!-- 1311967 -->   
名为“网络边界”的新设备配置文件与其他设备配置文件可以位于同一位置。 使用此配置文件定义要视为公司资源和受信任资源的在线资源。 必须先为设备定义网络边界，然后才能在设备上使用 Windows Defender 应用程序防护和 Windows 信息保护等功能。 仅可为每个设备定义一个网络边界，这一点非常重要。

可以定义可信任的企业云资源、IP 地址范围和内部代理服务器。 定义后，Windows Defender 应用程序防护和 Windows 信息保护等功能即可使用网络边界。

####  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Windows Defender 防病毒软件的两个其他设置<!-- 1338409 -->  
**文件阻止级别**

| | |
|---|---|
| 未配置 | “未配置”使用 Windows Defender 防病毒软件的默认阻止级别，并提供强大的检测功能而不会增加检测出合法文件的风险。 |
| 高 | “高”级别执行级别较高的检测。
| 高 +  | “高 +”级别执行“高”级别检测，同时采取额外的保护措施，但可能会影响客户端性能。
| 零容差  | “零容差”可阻止所有未知的可执行文件。 |

级别设置为“高”可能导致检测出一些合法文件，但出现此情况的可能性不大。
建议将文件阻止级别设置为默认级别，即“未配置”。

**云扫描文件的超时延长**  

| | |
|--|--|
| 秒数 (0 - 50) | 指定等待云返回结果时，Windows Defender 防病毒软件应阻止文件的最长时间。 默认值为 10 秒：此处指定的任意额外时间（最多 50 秒）都将与这 10 秒相加。 大多数情况下，扫描所需的时间远少于最大值。 延长时间可使云对可疑文件进行全面调查。 建议启用此设置，并至少指定 20 秒的延长时间。 |

#### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>添加了适用于 Windows 10 设备的 Citrix VPN<!-- 1512457 -->  
可为 Windows 10 设备配置 Citrix VPN。 为 Windows 10 或更高版本配置 VPN 时，可在“基础 VPN”边栏选项卡中的“选择连接类型”列表中选择“Citrix VPN”。

> [!Note]
> 适用于 iOS 和 Android 的 Citrix 配置已存在。

#### <a name="wi-fi-connections-support-pre-shared-keys-on-ios----1550823---"></a>iOS 上的 Wi-Fi 连接支持预共享密钥<!-- 1550823 -->
客户可配置 Wi-Fi 配置文件，以便在 iOS 设备上为“WPA/WPA2 个人”连接使用预共享密钥 (PSK)。 当设备在 Intune 中注册时，这些配置文件将被推送至用户的设备。

当配置文件推送到设备时，下一步采取何种操作取决于配置文件的配置。  如果设置为自动连接，则它将在下一次需要网络时执行自动连接。  如果手动连接配置文件，则用户必须手动激活连接。  

### <a name="intune-apps"></a>Intune 应用

#### <a name="access-to-managed-app-logs-for-ios----1469920---"></a>访问 iOS 的托管应用日志<!-- 1469920 -->
安装了 Managed Browser 的最终用户现在可查看所有 Microsoft 已发布应用的管理状态，并可针对托管 iOS 应用的疑难问题发送日志。

若要了解如何在运行于 iOS 设备上的 Managed Browser 中启用疑难解答模式，请参阅[如何在 iOS 上使用 Managed Browser 访问托管应用日志](app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios)。

#### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>在适用于 iOS 的公司门户（版本 2.9.0）中对设备设置工作流的改进<!-- 1417174 -->

改进了适用于 iOS 的公司门户应用中的设备设置工作流。 语言对用户更加友好，在可能的情况下我们还对屏幕进行了合并。 通过在整个设置文本中使用公司名称使语言特定于你的公司。 可以在 [应用 UI 的新增功能](whats-new-app-ui.md)页上看到此更新的工作流。

### <a name="monitor-and-troubleshoot"></a>监视和故障排除

#### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>用户实体包含数据仓库数据模型中的最新用户数据 <!-- 1544273 -->
Intune 数据库仓库数据模型的第一个版本只包含 Intune 的最近历史数据。 报表制作者无法捕获用户的当前状态。 在此更新中，用户实体将包含最新用户数据。


## <a name="notices"></a>通知

### <a name="plan-for-change-update-where-you-configure-your-app-protection-policies"></a>更改计划：更新配置应用保护策略的位置

从 2018 年 3 月开始，我们将从 Azure 门户的“Intune 应用保护服务”边栏选项卡暂时重定向到 Azure 门户中 Intune 内的“移动应用”边栏选项卡。 请注意，Intune 中“应用配置”下的“移动应用”边栏选项卡已包括所有应用保护策略。 直接转到 Intune 即可，而无需转到“Intune 应用保护”。 我们将在 4 月停止该重定向并完全删除“Intune 应用保护服务”边栏选项卡，它将再次复制当前内置于 Intune 的功能。 

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
此更改将同时影响 Intune 独立版客户和混合版（带 Configuration Manager 的 Intune）客户。 此集成将有助于简化云管理。 当前在 Azure 中，只可转到一个边栏选项卡（Intune 边栏选项卡）来管理组、策略、应用以及任何移动设备管理。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
请将 Intune 标记为收藏（而不是“Intune 应用保护服务”边栏选项卡），并确保熟悉 Intune 的“移动应用”边栏选项卡中的应用保护策略工作流。 我们将重定向一小段时间，然后删除“应用保护”边栏选项卡。 请记住，所有应用保护策略都已转到 Intune，可按照此处的文档操作，修改任何条件访问策略：[https://aka.ms/azuread_ca](https://aka.ms/azuread_ca)。

**其他信息**：[https://aka.ms/intuneapppolicy](https://aka.ms/intuneapppolicy)

### <a name="updated-new-security-enhancements-in-the-intune-service-----1637539---"></a>已更新：Intune 服务中新的安全性增强功能<!-- 1637539 -->   

我们将在 Intune 服务中推出安全性增强功能。 作为此更改的一部分，Intune 服务的三月版更新中将在 Azure 控制台的 Intune 中添加一个切换键，以启用或关闭此安全性功能。 启用该功能后，未分配符合性策略的设备将标记为“不符合”。

**混合版客户**：暂时不会向混合版客户引入此更改。 用户无需采取任何操作。 但是，强烈建议确保设备分配有至少 1 个符合性策略。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？

在三月版更新中推出此更改时，此功能将为你带来不同的影响，具体取决于你是否已分配符合性策略。

- 如果你是新租户或现有租户，且设备未分配任何符合性策略，切换键将自动设置为“符合”。 该功能在控制台中的默认设置为“关闭”。 对最终用户没有任何影响。
- 如果你是现有租户，且具有已分配符合性策略的设备，切换键将自动设置为“不符合”。 三月版更新推出后，此功能的默认设置为“启用”。 

如果通过条件访问 (CA) 使用符合性策略，且该功能已启用，CA 现在将阻止所有未分配到至少 1 个符合性策略的设备。 除非向所有设备分配至少 1 个符合性策略，否则与这些设备关联的最终用户（以前允许访问电子邮件）将失去访问权限。   
 
#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？  

如果使用条件访问，建议启用此功能并将切换键设置为“不符合”。 为避免最终用户失去电子邮件访问权限，请确保所有设备分配有至少 1 个符合性策略。 以下是帮助你执行此操作所做的一些更改：   

- 我们在 Intune 门户中引入了一个报表，称为“没有符合性策略的设备”，可用于确定环境中没有分配到符合性策略的所有设备。 
- 有一个“所有用户”选项，可轻松向所有用户分配符合性策略。

如果选择关闭此切换键，则不需要任何后续操作。

**其他信息**：[https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

### <a name="plan-for-change-change-in-support-for-the-microsoft-intune-app-sdk-for-cordova-plugin"></a>计划更改：更改对 Microsoft Intune App SDK for Cordova 插件的支持
Intune 对 [Microsoft Intune App SDK Cordova](app-sdk-cordova.md) 插件的支持于 2018 年 5 月 1 日结束。 建议改为使用 Intune App Wrapping Tool 准备基于 Cordova 的应用，以实现 Intune 中的可管理性和可用性。 此更改生效时，将不再维护 Microsoft Intune APP SDK for Cordova 插件，也不接收更新。 应用开发者将不能使用此插件。 Intune 计划继续支持使用 Cordova 构建的应用。 但使用 Microsoft Intune APP SDK for Cordova 插件构建的任何应用在 Intune 中都会减少功能。 使用 Intune App Wrapping Tool 包装后，应用可以照常部署给最终用户。 针对基于 Cordova 且发布到 Google Play 商店的 Android 应用：
- 最终用户首次启动时，系统会提示其输入凭据以接收 Intune 策略。
- 应用应被发布到面向 Intune 用户的应用商店，例如“Contoso App for Intune”。 

有关 App Wrapping Tool 的详细信息，请参阅 [App Wrapping Tool for iOS](app-wrapper-prepare-ios.md) 和 [App Wrapping Tool for Android](app-wrapper-prepare-android.md)。 如有任何问题或疑问，请联系 [msintuneappsdk@microsoft.com](mailto:msintuneappsdk@microsoft.com)。 

### <a name="plan-for-change-use-intune-on-azure-now-for-your-mdm-management----1227338---"></a>更改计划：立刻使用 Azure 上的 Intune 进行 MDM 管理<!-- 1227338 -->
一年前，我们推出了 [Azure 上 Intune 的公共预览版](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/)，六个月前，我们推出了 Intune [新管理员体验的正式版](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/)。 自 2018 年 4 月 2 日起，我们将面向使用 Intune 独立版的客户关闭经典 Silverlight 控制台中的移动设备管理 (MDM)。 但客户可以使用 [Azure 上的 Intune](https://aka.ms/Intune_on_Azure) 满足 MDM 需求。 如果仍在使用经典控制台进行 MDM，请停止此做法并开始熟悉 Azure 上的 Intune。 我们不希望任何最终用户受到此次更改的影响。 Silverlight 中将保留经典电脑管理。 可在[此处](https://aka.ms/Intune_on_Azure_mdm)详细了解此次更改及其带来的影响。


### <a name="plan-for-change-easy-assist-end-of-life----1556480---"></a>计划更改：Easy Assist 服务终止 <!-- 1556480 -->
Intune 使用 Microsoft Easy Assist 提供 PC 管理远程协助。 可能不知道的一件事是，Microsoft Easy Assist 所属的 Office Live Meeting 即将于 2017 年 12 月 31 日遭弃用。 因此，Intune 使用的 Easy Assist 产品/服务同样也将于 2017 年 12 月 31日服务终止。

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>独立于 Android 设备管理 Android for Work 设备 <!-- 1490731 EEready-->    
注意：以下更改随 11 月更新一起推出，但可能需要一些时间才能在你的帐户上执行。 当帐户可使用这些更改时，你会在 Office 365 门户中收到确认通知。 推出后，你将拥有其他可管理性选项。 在推出期间，最终用户体验未作任何更改。

Intune 支持独立于 Android 平台管理 Android for Work 设备的注册。 这些设置位于“设备注册” > “注册限制” > “设备类型限制”下。 （这些设置之前位于“设备注册” > “Android for Work 注册” > “Android for Work 注册设置”下。）

默认情况下，Android for Work 设备的设置与 Android 设备的设置相同。 但是，更改 Android for Work 设置后则不再相同。

如果阻止个人 Android for Work 注册，那么仅公司 Android 设备可注册为 Android for Work。

使用新设置时，请考虑下列几点：

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>如果之前从未载入 Android for Work 注册

默认设备类型限制将阻止新的 Android for Work 平台。 载入该功能后，可允许设备注册 Android for Work。 为此，请更改默认值或新建一个设备类型限制，取代默认设备类型限制。

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>如果已载入 Android for Work 注册

如果之前已载入，那么情况取决于所选设置：

| Setting | 默认设备类型限制中的 Android for Work 状态 | 注意 |
| --- | --- | --- |
| **将所有设备作为 Android 管理** | 已阻止 | 所有 Android 设备均不注册 Android for Work。 |
| 将受支持设备作为 Android for Work 管理 | ，然后用户才能访问 | 所有支持 Android for Work 的 Android 设备均须注册 Android for Work。 |
| **仅为这些组中的用户将受支持设备作为 Android for Work 管理** | 已阻止 | 创建单独的设备类型限制策略替代默认值。 此策略将之前选择的组定义为允许 Android for Work 注册。 允许所选组中的用户继续注册 Android for Work 设备。 所有其他用户则不能注册 Android for Work。 |

所有情况下都将保留预期规则。 对你来说，无需任何操作即可维护环境中的 Android for Work 全局或按组允许。

### <a name="deprecating-support-for-os-x-mavericks-1010-and-previous-versions-of-macos---1489263-plan-for-change-for-1802--"></a>正在弃用对 OS X Mavericks 10.10 及 macOS 早期版本的支持<!--1489263, plan for change for 1802-->
自 2018 年 2 月起，将开始停止对运行 OS X Yosemite 10.10 及 macOS 早期版本的设备的注册。 Intune 完全支持 OS X Capitan 10.11 和更高版本。

### <a name="new-path-for-managed-devices-in-graph-api----1586728---"></a>在图形 API 中访问受管理设备的新路径<!-- 1586728 -->
用于在 beta 版本图形 API 中访问托管设备的路径正在发生更改。 

| | |
|--|--|
| 当前路径 |  https://graph.microsoft.com/beta/managedDevices |
| 新路径 | https://graph.microsoft.com/beta/deviceManagement/managedDevices |

这两个路径在 10 月均可使用。 10 月服务发布后，仅可使用新路径。  如果目前使用图形 API 受管理设备，请使用新路径更新和验证脚本和应用程序。 有关其他更改，请查看每月[图形 API 更改日志](https://developer.microsoft.com/graph/docs/concepts/changelog)。


### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接访问 Apple 注册方案<!--951869-->
对于在 2017 年 1 月之后创建的 Intune 帐户，Intune 支持在 Azure 门户中使用注册设备工作负荷直接访问 Apple 注册方案。 以前，只能通过 Intune 经典门户中的链接访问 Apple 注册预览版。 2017 年 1 月之前创建的 Intune 帐户需要进行一次性迁移，然后才能使用 Azure 中的这些功能。 迁移的计划目前尚未公布，但详细信息将尽快发布。 如果现有帐户无法访问 Azure 门户，强烈建议创建一个试用帐户测试新体验。

### <a name="administration-roles-being-replaced-in-azure-portal"></a>在 Azure 门户中被替换的管理角色
在 Intune 经典门户 (Silverlight) 中使用的现有移动应用程序管理 (MAM) 管理角色（参与者、所有者和只读）被替换为 Intune Azure 门户中一套完整的基于角色的新的管理控制方法 (RBAC)。 在迁移到 Azure 门户后，需要将管理员重新分配到这些新的管理角色。 有关 RBAC 和新角色的详细信息，请参阅 [Microsoft Intune 基于角色的访问控制](/intune/role-based-access-control)。

## <a name="whats-coming"></a>即将推出

### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866--"></a>iOS 版公司门户应用的用户体验更新<!--1412866-->

我们将向 iOS 版公司门户应用发布用户体验主要更新。 此更新具有经过完全重新设计的视觉效果，包括现代化的外观和经提升的可用性和可访问性感受。 iOS 公司门户当前的所有功能都将保留。

我们将通过 Apple TestFlight 计划推出更新版 iOS 公司门户应用的预发布版本，用户可以使用并提供反馈。 若想参与 TestFlight，请在 https://aka.ms/intune_ios_cp_testflight 注册。

### <a name="conditional-access-policies-for-intune-will-only-be-available-from-the-azure-portal-----1737088---"></a>适用于 Intune 的条件访问策略仅可从 Azure 门户访问<!-- 1737088 -->
我们正在简化配置和管理条件访问的位置。 目前，可从“Intune 应用保护(MAM)”边栏选项卡管理条件访问，还可通过 [Microsoft Azure 门户](https://manage.windowsazure.com)中的经典版 Azure AD 进行管理。 从 1 月开始，只能在 [Azure 门户](https://portal.azure.com)中通过“Azure Active Directory” > “条件访问”配置和管理策略。 为方便起见，还可在 Azure 门户中通过“Intune” > “条件访问”，从 Intune 访问此边栏选项卡。

### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine---1592747--"></a>使用 Intune 的设备符合性引擎管理 Jamf 注册的 macOS 设备<!--1592747-->
从 2018 年初开始，Jamf 将把 macOS 设备状态信息发送给 Intune，然后由 Intune 评估它是否符合 Intune 控制台中定义的策略。 基于设备符合性状态以及其他条件（如位置、用户风险等），条件访问将强制实现 macOS 设备访问云和与 Azure AD 连接的本地应用程序（包括 Office 365）的符合性。

### <a name="changes-in-support-for-the-intune-ios-company-portal-app-----1164474----"></a>Intune iOS 公司门户应用的支持更改 <!-- 1164474  -->
Microsoft Intune 公司门户应用 iOS 版即将会有新的版本，该版本仅支持运行 iOS 9.0 或更高版本的设备。 支持 iOS 8 的公司门户版本在未来较短时间内仍将可用。 但是，如果还使用启用了 MAM 的 iOS 应用（支持 iOS 9.0 和更高版本），需确保最终用户更新到最新 OS。 

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
虽然我们无法提供具体日期，但我们仍将此提前告知于你，以便你有时间做出计划。 请确保你的用户更新到 iOS 9+，且当公司门户应用发布后，请求最终用户更新其公司门户应用。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
鼓励用户更新到 iOS 9.0 或更高版本以充分利用 Intune 的新功能。  鼓励用户安装公司门户的新版本，从而利用它将提供的新功能。

转到 Azure 门户中 Intune，依次查看“设备”>“所有设备”，并按 iOS 版本进行筛选，以确定当前是否有任何设备的操作系统低于 iOS 9。


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 将要求更新应用传输安全<!--748318-->
Apple 宣布他们将强制对应用程序传输安全 (ATS) 实施特定要求。 使用 ATS 对所有通过 HTTPS 的应用通信实施更严格的安全措施。 此更改会影响使用 iOS 公司门户应用的 Intune 客户。

我们通过强制实施新的 ATS 要求的 Apple TestFlight 计划提供了适用于 iOS 的公司门户应用的可用版本。 如果你想要试用以测试你的 ATS 符合性，请发送电子邮件至 <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a>，并提供你的名字、姓氏、电子邮件地址和公司名称。 请查看 [Intune 支持博客](https://aka.ms/compportalats)，了解更多详细信息。

## <a name="see-also"></a>另请参阅
* [Microsoft Intune 博客](http://go.microsoft.com/fwlink/?LinkID=273882)
* [云平台路线图](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [What's new in the Company Portal UI](whats-new-app-ui.md)（公司门户 UI 新增功能）
* [前几个月的新增功能](whats-new-archive.md)
