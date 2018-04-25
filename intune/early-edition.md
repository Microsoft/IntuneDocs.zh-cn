---
title: 早期版本
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b6ca8108924c6c062da0d0ef56ab5b68635dd9ca
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="the-early-edition-for-microsoft-intune---april-2018"></a>Microsoft Intune 的早期版本 - 2018 年 4 月

早期版本提供了一份即将发布的 Microsoft Intune 版本中将出现的功能列表。 此信息的提供具有条件限制，并且会不断变化。 请不要与公司外部共享此信息。 此处列出的某些功能有无法按期发布的风险并可能推迟到以后的版本。 正在以试验模式（外部测试）测试其他功能，以确保它们可立即供客户使用。 如果有任何问题或顾虑，请与 Microsoft 产品组联系人联系。

本页将定期更新。 返回查看其他更新。

> [!Note]
>下面的更改依据 Intune 开发。 有关新的混合功能的详细信息，请查看[混合新增功能页](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure 门户中的 Intune

<!-- 1804 start -->

### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802--"></a>添加到 Endpoint Protection 设置的新 Windows Defender Credential Guard 设置<!--1102252 --><!--from 1802-->

新 [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) 设置将添加到“设备配置” > “配置文件” > “Endpoint Protection”。 将添加以下设置：

- 平台安全级别：指定平台安全级别是否在下次重启时启用。 基于虚拟化的安全性需要安全启动。 可以选择使用直接内存访问 (DMA) 保护启用基于虚拟化的安全性。 DMA 保护需要硬盘支持并且将仅在正确配置的设备上启用。
- 基于虚拟化的安全性：指定基于虚拟化的安全性是否在下次重启时启用。
- Windows Defender Credential Guard：当具有安全启动的平台安全级别和基于虚拟化的安全性同时启用时，在下次重启时通过基于虚拟化的安全性打开 Credential Guard 以帮助保护凭据。 可用选项包括“禁用”、“使用 UEFI 锁启用”、“无锁启用”和“未配置”。
  - “禁用”选项将远程关闭 Credential Guard（如果之前已使用“无锁启用”选项启用）。

  - “使用 UEFI 锁启用”选项可确保 Credential Guard 不能通过注册表项或通过使用组策略禁用。 若要在使用此设置后禁用 Credential Guard，必须将组策略设置为“禁用”，并通过真实存在的用户从每台计算机中删除安全功能，以清除 UEFI 中保留的配置。 只要 UEFI 配置仍然存在，Credential Guard 则会保持启用状态。

  - “无锁启用”选项允许通过使用组策略远程禁用 Credential Guard。 使用此设置的设备必须至少在 Windows 10（版本 1511）上运行。

  - “未配置”选项将策略设置保留为未定义状态。 组策略不会将策略设置写到注册表，所以它不会对计算机或用户造成影响。 如果注册表中存在当前设置，它将不会被修改。

### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Android 上对 MAM PIN 的密码支持<!-- 1438086 -->

Intune 管理员将能够设置应用程序启动要求以强制使用密码而不是数字 MAM PIN。 如果进行此配置，在访问启用 MAM 的应用程序前，用户需要在出现提示时设置并使用密码。 密码是至少包含一个特殊字符或大写/小写字母的数字 PIN。 Intune 对密码的支持与支持现有数字 PIN 类似，可通过管理员控制台设置最短长度并且允许重复字符和序列。 此功能需要最新版 Android 公司门户。 此功能已可应用于 iOS。

###  <a name="block-camera-and-screen-captures-on-android-for-work----1098977-eeready--"></a>在 Android for Work 上阻止照相机和屏幕捕获<!-- 1098977 eeready-->
配置 Android 设备的设备限制时，将可以阻止两个新属性： 
- 照相机：阻止访问设备上的所有照相机
- 屏幕捕获：阻止屏幕捕获，还会阻止在不具有安全视频输出的显示设备上显示内容

适用于 Android for Work。

### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>对 macOS 的业务线 (LOB) 应用支持 <!-- 1473977 -->
Microsoft Intune 将提供从 Azure 门户安装 macOS LOB 应用的功能。 使用 GitHub 中提供的工具对 macOS LOB 应用进行预处理后，可以将该应用添加到 Intune。 在 Azure 门户的“Intune”边栏选项卡中，选择“移动应用”。 在“移动应用”边栏选项卡，选择“应用” > “添加”。 在“添加应用”边栏选项卡，选择“业务线应用”。 

### <a name="support-for-user-less-devices----1637553---"></a>对无用户设备的支持<!-- 1637553 -->
Intune 将支持在无用户设备（如 Microsoft Surface Hub）上评估符合性的功能。 符合性策略可以面向特定设备。 这样可以确定不具有关联用户的设备的符合性（和不符合性）。

### <a name="additions-to-local-device-security-options-settings----1403702---"></a>新增本地设备安全选项设置<!-- 1403702 -->
你将能够配置适用于 Windows 10 设备的其他本地设备安全选项设置。 其他设置将在 Microsoft 网络客户端、Microsoft 网络服务器、网络访问和安全性和交互式登录的区域内可用。 创建 Windows 10 设备配置策略时，可以在终结点保护类别中查找这些设置。

### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>需要安装策略、应用、证书和网络配置文件<!-- 1553555 -->
除非 Intune 在 AutoPilot 设备预配期间安装策略、应用、证书和网络配置文件，否则管理员将能够阻止最终用户访问 Windows 10 RS4 桌面。

### <a name="rules-for-removing-devices----1609459---"></a>删除设备的规则<!-- 1609459 -->
将提供新规则，用于自动删除未在设置天数内进行签入的设备。 要查看新规则，请转到“Intune”窗格，依次选择“设备”和“设备删除规则”。

### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>在 Windows 10 企业版 RS4 AutoPilot 设备上阻止使用者应用和体验<!-- 1621980 -->
你将能够阻止在 Windows 10 企业版 RS4 AutoPilot 设备上安装使用者应用和体验。 要查看此功能，请转到“Intune” > “设备注册” > “Windows 注册” > “Windows AutoPilot 配置文件” > “新建” > “注册设置”。 

### <a name="advanced-threat-protection-integrated-with-intune----1629303---"></a>与 Intune 集成的高级威胁防护<!-- 1629303 -->
[高级威胁防护 (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) 显示 Windows 10 设备的风险级别。 Intune 评估 Windows 10 设备的符合性时，ATP 风险评分包括在此评估中。 可以配合使用 ATP 和条件访问来保护网络。

### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>用户在使用 macOS High Sierra 10.13.2+ 的设备上的新注册步骤<!--1734567 -->
macOS High Sierra 10.13.2 引入了“用户批准的”MDM 注册的概念。 未来，批准的注册将允许 Intune 管理某些安全敏感设置。 有关详细信息，请参阅此处的 Apple 支持文档：https://support.apple.com/HT208019。

如果最终用户未打开“系统首选项”并手动批准，使用 macOS 公司门户的设备将被视为“未经用户批准”。 为此，macOS 公司门户现直接在注册过程末尾指示使用 macOS 10.13.2 及以上版本的用户手动批准注册。 Intune 管理员控制台将就注册设备的用户批准情况进行报告。

### <a name="delete-autopilot-devices----1713650---"></a>删除 AutoPilot 设备<!-- 1713650 -->
Intune 管理员将能够删除 AutoPilot 设备。

### <a name="built-in-all-users-and-all-devices-group-for-android-for-work-afw-app-assignment----1813073---"></a>面向 Android for Work (AFW) 应用分配的内置“所有用户”和“所有设备”组<!-- 1813073 -->
你将能够利用面向 AFW 应用分配的内置“所有用户”和“所有设备”。 有关详细信息，请参阅[在 Microsoft Intune 中包括和排除应用分配](apps-inc-exl-assignments.md)。

### <a name="improved-device-deletion-experience---1832333---"></a>设备删除体验改进<!--1832333 -->
删除 Intune 中的设备前，将不再需要删除公司数据或将设备恢复出厂设置。

要感受新体验，请登录 Intune，选择“设备” > “所有设备”> 设备的名称 >“删除”。

 如果仍希望确认擦除/停用，可使用标准设备生命周期流程，即在“删除”前执行“删除公司数据”和“恢复出厂设置”。 

### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>将 AutoPilot 配置文件移动到组目标<!-- 1877935 -->
目前，可向所选设备分配 AutoPilot 部署配置文件。 到四月底，将可以按如下方式分配这些配置文件：
- 创建包含 AutoPilot 设备的 (Azure AD) 组
- 向 Azure AD 组分配所需配置文件。 现在，AutoPilot 配置文件将分配到该组中的 AutoPilot 设备。

### <a name="play-sounds-on-ios-when-in-lost-mode----1629303---"></a>“丢失”模式下在 iOS 上播放声音<!-- 1629303 -->
当受监督 iOS 设备处于移动设备管理 (MDM)[“丢失”模式](device-lost-mode.md)时，你可以播放声音（“设备” > “所有设备”> 选择一个 iOS 设备 >“概述” > “更多”）。 声音将持续播放，直到将该设备移除“丢失”模式或用户在该设备上禁用声音。 适用于 iOS 9.3 和更高版本的设备。

### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>对 SCEP 证书使用自定义使用者名称<!-- 2064190 -->
你将能够使用“OnPremisesSamAccountName”作为 SCEP 证书配置文件中自定义使用者的公用名称。 例如，你可以使用 `CN={OnPremisesSamAccountName})`。

### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>在 macOS 公司门户应用中发送诊断报告<!-- 2216677 -->
将更新适用于 macOS 设备的公司门户应用，以改进用户报告 Intune 相关错误的方式。 在公司门户应用中，员工将能够：
- 直接将诊断报告上传到 Microsoft 开发人员团队。
- 通过电子邮件将事件 ID 发送给公司的 IT 支持团队。

### <a name="always-on-vpn-for-windows-10---1333666---"></a>适用于 Windows 10 的 Always On VPN<!--1333666 -->

目前，通过使用自定义虚拟专用网络 (VPN) 配置文件（使用 OMA-URI 创建），可在 Windows 10 设备上使用 [Always On](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on)。

此次更新后，管理员将能够在 Azure 门户中的 Intune 中直接面向 Windows 10 VPN 配置文件启用 Always On。 Always On VPN 配置文件将在以下情况下自动连接：

- 用户登录其设备
- 设备上的网络发生更改
- 设备屏幕在关闭后重新打开

### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>针对 Apple MDM Push Certificate 上传失败的错误消息改进<!-- 2172331 -->

错误消息将说明，续订现有 MDM 证书时必须使用相同 Apple ID。

###  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153-eeready---"></a>设备配置文件图表和状态列表将显示组中的所有设备<!-- 1449153 eeready -->
配置设备配置文件（“设备配置” > “配置文件”）时，选择设备配置文件，如 iOS。 将此配置文件分配到包括 iOS 设备和非 iOS 设备的组。 图形图表显示应用到 iOS 和非 iOS 设备的配置文件计数（“设备配置” > “配置文件”> 选择一个现有配置文件 >“概述”）。 选择“概述”选项卡中的图形图表时，“设备状态”将列出组中的所有设备，而不仅仅是 iOS 设备。 

此次更新后，图形图表（“设备配置” > “配置文件”> 选择一个现有配置文件 >“概述”）将仅显示特定设备配置文件的计数。 例如，如果配置设备配置文件应用于 iOS 设备，则图表仅列出 iOS 设备的计数。 选中图形图表并打开“设备状态”后，将仅列出 iOS 设备。

当此更新正在进行时，用户图形图表将暂时删除。 


<!-- 1803 start -->

#### <a name="multiple-exchange-connector-support----2070451---"></a>多个 Exchange Connector 支持<!-- 2070451 -->

你将不再受到每租户一个 Microsoft Intune Exchange Connector 的限制。 Intune 将支持多个 Exchange Connector，使你可以设置多个本地 Exchange 组织的 Intune 条件访问。

凭借 Intune 本地 Exchange 连接器，可以根据设备是否已在 Intune 中注册且是否符合 Intune 设备符合性策略来管理设备对本地 Exchange 邮箱的访问。 若要设置连接器，请从 Azure 门户下载 Intune 本地 Exchange 连接器，并将它安装在 Exchange 组织中的服务器上。 在 Microsoft Intune 仪表板上，选择“本地访问”，然后在“设置”下选择“Exchange ActiveSync 连接器”。 下载 Exchange 本地连接器，并将它安装在 Exchange 组织中的服务器上。 由于你已经不再受到每租户一个 Exchange 连接器的限制，因此，如果拥有其他的 Exchange 组织，则可以按照此相同的过程为其他每个 Exchange 组织下载并安装连接器。

### <a name="support-coming-for-new-cisco-anyconnect-client-for-ios----1333708---"></a>即将为适用于 iOS 的新 Cisco AnyConnect 客户端提供支持 <!-- 1333708 -->

为适用于 iOS 的 Cisco AnyConnect 创建的新 VPN 配置文件将适用于 Cisco AnyConnect 4.0.7x 和更高版本。 现有 iOS Cisco AnyConnect VPN 配置文件将被标记为“Cisco Legacy AnyConnect”，并将继续适用于 Cisco AnyConnect 4.0.5x，如现在一样。

> [!NOTE]
> 此更改仅适用于 iOS；将继续只提供一个适用于 Android、Android for Work 和 macOS 的 Cisco AnyConnect 选项。

#### <a name="more-information"></a>详细信息

需要创建新的 iOS Cisco AnyConnect VPN 配置文件以支持新应用，因为新的 Cisco AnyConnect 应用和 Cisco Legacy AnyConnect 应用是单独的应用。 如果是在环境中管理 AnyConnect 客户端的，还需要部署新的 Cisco AnyConnect 应用。 若要完成升级，还需要删除 Cisco Legacy AnyConnect 配置文件，并删除 Cisco Legacy AnyConnect 应用。

在初始版本中，网络访问控制 (NAC) 集成将不适用于新的 AnyConnect 客户端。 我们正在与 Cisco 合作，以在未来的 Intune 版本中提供 NAC 集成。

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>可以将所需的业务线 (LOB) 应用部署到 Windows 10 桌面版设备上的所有用户 <!-- 1627835 RS4 -->
客户将能够部署所需的业务线 Windows 10 应用以安装在设备上下文中。 这将使这些应用可供此设备上的所有用户可用。 这仅适用于 Windows 10 桌面版设备。

### <a name="company-portal-enrollment-improved----1874230--"></a>改进的公司门户注册 <!-- 1874230-->
通过在 Windows 10 内部版本 1703 和更高版本上使用公司门户注册设备的用户将能够在不退出应用的情况下完成注册的第一步。

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>更新适用于 Android 的公司门户应用上的“帮助和反馈”体验 <!--1631531 -->

我们将更新适用于 Android 的公司门户应用上的“帮助和反馈”体验以符合 Android 应用的最佳做法。 我们将在未来的几个月里更新适用于 Android 的公司门户应用，将“帮助和反馈”菜单项分为不同的“帮助”和“发送反馈”菜单项。 “帮助”页面将包含“常见问题”部分和“电子邮件支持”按钮，引导最终用户向 Microsoft 上传日志并向公司支持部门发送电子邮件以描述问题。 “发送反馈”将引导用户完成标准的 Microsoft 反馈提交，这将提示用户选择“我喜欢一些内容”、“我不喜欢一些内容”还是“我有个主意”。

<!-- 1802 start -->

### <a name="new-printer-settings-for-education-profiles----1308900---"></a>教育配置文件的新打印机设置 <!-- 1308900 -->

对于教育配置文件，新的设置将提供在“打印机”类别下：“打印机”、“默认打印机”、“添加新的打印机”。

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>应用保护策略<!-- 679615 -->
Intune 应用保护策略将提供创建默认全局策略的功能，以便快速对整个租户中所有用户启用保护。

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory 网站可能需要 Intune Managed Browser 应用，并且支持 Managed Browser（公共预览版）的单一登录<!-- 710595 -->   
利用 Azure Active Directory (Azure AD)，可在移动设备上将对网站的访问限于 Intune Managed Browser 应用。 在 Managed Browser 中，网站数据可保持安全并且独立于最终用户的个人数据。 此外，Managed Browser 支持受 Azure AD 保护的站点的单一登录功能。 通过登录 Managed Browser，或在设备上将 Managed Browser 与由 Intune 管理的其他应用配合使用，用户无需输入凭据，Managed Browser 即可访问受 Azure AD 保护的公司站点。 此功能适用于 Outlook Web Access (OWA) 和 SharePoint Online 等站点，以及通过 Azure 应用代理访问的 Intranet 资源等其他公司站点。




## <a name="notices"></a>通知

此时没有任何活动通知。


### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。


