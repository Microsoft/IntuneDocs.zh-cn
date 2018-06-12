---
title: 早期版本
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/30/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 95ad588b084319cd8a0f5f5c5d92da0e892eed50
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745037"
---
# <a name="the-early-edition-for-microsoft-intune---june-2018"></a>Microsoft Intune 的早期版本 - 2018 年 6 月

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

<!-- 1806 start -->

### <a name="corporate-owned-single-use-cosu-support-for-android-devices----1630973---"></a>支持公司拥有的单一用途 (COSU) Android 设备 <!-- 1630973 -->

Intune 将支持受到高度管控的锁定展台式 Android 设备。 这使管理员可以将设备的使用进一步锁定到单个应用或一小组应用，并阻止用户在设备上启用其他应用或执行其他操作。

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>Apple 设备注册计划支持注册 macOS 设备 <!-- 747651 -->

Intune 支持将 macOS 设备注册到 Apple 设备注册计划 (DEP) 中。 为此，请执行以下操作：

1. 在 deploy.apple.com，将 macOS 序列号分配给 MDM 服务器。
2. 将序列号导入 Intune。
3. 创建特定于 macOS 设备的注册计划配置文件。

### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>停用 Android for Work 和 Play for Work 以反映 Google 名称更改 <!--842873 -->
Intune 将更新“Android for Work”术语，以反映 Google 品牌的更改。  我们将不再使用术语“Android for Work”和“Play for Work”。 将根据上下文，会使用不同的术语：

- “Android 企业”指整个现代 Android 管理堆栈。
- “工作配置文件”或“配置文件所有者”指使用工作配置文件管理的 BYOD 设备。
- “托管的 Google Play”指 Google 应用商店。

### <a name="monitor-ios--app-configuration-status-per-device----880037-eeready-eestaged---"></a>监控每个设备的 iOS 应用配置状态 <!-- 880037 eeready eestaged -->

作为 Microsoft Intune 管理员，你将能够监控每个受管理设备的 iOS 应用配置状态。 从 Azure 门户的“Microsoft Intune”中，选择“设备” > “所有设备”。 从受管理设备列表中选择特定设备，以显示该设备的边栏选项卡。 在该设备的边栏选项卡上，选择“应用配置”。  

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>可通过 iOS 上的 APP 设置阻止第三方键盘 <!-- 1248481 -->
在 iOS 设备上，Intune 管理员可以阻止使用第三方键盘在受策略保护的应用中访问组织数据。 当应用程序保护策略 (APP) 设置为阻止第三方键盘时，设备用户将在首次使用第三方键盘与公司数据交互时收到一条消息。 将阻止本地键盘以外的所有选项都，设备用户不会看到它们。 设备用户只会看到一次对话消息。 

### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>在 macOS 设备上使用防火墙设置创建设备符合性策略 <!-- 1497640 -->
创建新的 macOS 符合性策略（“设备符合性” > “策略” > “创建策略” > “平台: macOS” > “系统安全”）时，会有一些新的可用“防火墙”设置： 
- 防火墙：配置环境对传入连接的处理方式。
- 传入连接：阻止所有传入连接，DHCP、Bonjour 和 IPSec 等基本 Internet 服务需要的连接除外。 此设置还会阻止所有共享服务。
- 隐藏模式：启用隐藏模式以防止设备响应探测请求。 设备会继续回应已授权应用的传入请求。

适用于：macOS 10.12 及更高版本

### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>使用 sAMAccountName 作为电子邮件配置文件的帐户用户名 <!-- 1500307 -->

你将能够使用本地“sAMAccountName”作为 Android、iOS 和 Windows 10 的电子邮件配置文件的帐户用户名。 还可以从 Azure Active Directory (Azure AD) 中的 `domain` 或 `ntdomain` 属性获取域。 或者，输入自定义静态域。

若要使用此功能，必须将本地 Active Directory 环境中的 `sAMAccountName` 属性同步到 Azure AD。

适用于：Android、iOS、Windows 10 及更高版本

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>在应用启动和超时时要求输入非生物识别密码 <!-- 1506985 -->

在应用启动时和管理员指定的超时时长后要求输入非生物识别密码，Intune 会限制使用生物识别来访问公司数据，从而为启用了移动应用程序管理 (MAM) 的应用提升安全性。 这些设置将影响依靠 Touch ID (iOS)、Face ID (iOS)、Android Biometric 或其他未来生物识别身份验证方法访问启用了 APP/MAM 的应用程序的用户。 这些设置将使 Intune 管理员能够更精细地控制用户访问，让带有多个指纹或其他生物识别访问方法的设备只能向正确的用户显示公司数据。 在 Azure 门户中，打开“Microsoft Intune”。 选择“移动应用” > “应用保护策略” > “添加策略” > “设置”。 找到特定设置的“访问”部分。

### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>选择性擦除组织的应用数据 <!-- 1507030 -->
当不满足应用程序保护策略 (APP) 访问设置的条件时，管理员可配置一项新操作，即选择性擦除组织数据配置。  此功能可帮助管理员根据预先配置的标准自动保护和删除应用程序中的敏感组织数据。

### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>撤销通过 VPP 购买的 iOS 应用 <!-- 1777384 -->
作为 Microsoft Intune 管理员，你可以撤销通过批量采购计划 (VPP) 购买的选定 iOS 应用的许可证。 可在取消向用户分配应用时向其发出通知。 撤销应用许可证将不会从设备中卸载相关的 VPP 应用。 若要卸载 VPP 应用，必须将分配操作更改为“卸载”。 回收的许可证计数将反映在 Intune“应用”工作负荷的“许可应用”节点中。 有关 iOS VPP 应用的详细信息，请参阅[如何使用 Microsoft Intune 管理通过批量采购计划购买的 iOS 应用](vpp-apps-ios.md)。

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus 语言包 <!-- 1833450 -->
作为 Intune 管理员，你将能够为通过 Intune 管理的 Office 365 Pro Plus 应用部署其他语言。 可用语言列表包括语言包的“类型”（核心、部分和校对）。 在 Azure 门户中，选择“Microsoft Intune” > “移动应用” > “应用” > “添加”。 在“添加应用”边栏选项卡的“应用类型”列表中，选择“Office 365 套件”下的“Windows 10”。 在“应用套件设置”边栏选项卡中选择“语言”。

### <a name="revoke-ios-vpp-app-license----1863797---"></a>撤消 iOS VPP 应用许可证 <!-- 1863797 -->
作为管理员，你将能够回收分配给用户或设备的 iOS VPP 应用许可证。 也可通过卸载 iOS VPP 应用回收应用许可证。 然后，可以选择将该应用许可证分配给其他用户或设备。 有关 iOS VPP 应用许可证的详细信息，请参阅[在 Microsoft Intune 中管理 iOS 批量购买的应用](vpp-apps-ios.md)。

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>公司门户网站的新用户体验更新<!--2000968 -->
我们根据客户的反馈向公司门户网站添加新功能。 可从 Android、iOS 和 Windows 设备上体验到现有功能和可用性方面的重大改进。 该网站的各个区域（如设备详细信息、反馈与支持以及设备概述）都采用了全新的现代化快速响应设计。 你还会看到：

- 简化了所有设备平台上的工作流
- 改进了设备识别和注册流
- 提供了更多有用的错误消息
- 语言更加友好，减少了技术术语的使用
- 共享指向应用的直接链接的功能
- 改善了大型应用目录的性能
- 为所有用户增加了辅助功能

### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>编辑 Office 365 Pro Plus 应用部署 <!-- 2150145 -->
作为 Microsoft Intune 管理员，你现在可以对 Office 365 Pro Plus 应用部署进行更多编辑。 在 Azure 门户中，选择“Microsoft Intune” > “移动应用” > “应用”。 从应用列表中选择你的 Office 365 Pro Plus 套件。  

### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794---"></a>逐行查看上传的重复公司设备标识符 <!-- 2203794 -->
上传企业 ID 时，Intune 将提供重复项列表，你可以选择替换或保留现有信息。 选择“设备注册” > “公司设备标识符” > “添加标识符”后，如果有重复项，将显示报告。 

### <a name="manually-add-corporate-device-identifiers----2203803---"></a>手动添加公司设备标识符 <!-- 2203803 -->
你将可以手动添加公司设备 ID。 选择“设备注册” > “公司设备标识符” > “添加”。

### <a name="new-status-for-devices-in-device-configuration----2308882---"></a>可在设备配置中为设备设置新状态 <!-- 2308882 -->
在“设备配置” > “概述”中，将添加以下新状态：
- 成功
- 错误
- 冲突
- 挂起
- 不适用 还显示了图像，展示其他平台的设备计数。 例如，如果正在查看 iOS 配置文件，则新磁贴会显示同时分配给到配置文件的非 iOS 设备数。 

### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>设备符合性支持第三方防病毒解决方案 <!-- 2325484 -->
当创建设备符合性策略（“设备符合性” > “策略” > “创建策略” > “平台: Windows 10 及更高版本” > “设置” > “系统安全”）时，会出现新的“设备安全性”选项： 
- 防病毒：当设置为“需要”时，可以使用在 Windows 安全中心注册的防病毒解决方案（如 Symantec）来检查符合性。 
- 反间谍软件：当设置为“需要”时，可以使用在 Windows 安全中心注册的反间谍软件解决方案（如 Symantec）来检查符合性。 

适用于：Windows 10 及更高版本 

<!-- 1805 start -->

### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680-eeready----"></a>支持 Palo Alto Networks GlobalProtect VPN 配置文件<!-- 1333680 eeready ! -->

通过此更新，可选择 Palo Alto Networks GlobalProtect 作为 Intune 中 VPN 配置文件的 VPN 连接类型（“设备配置” > “配置文件” > “创建配置文件” > “配置文件类型” > “VPN”）。 在此版本中，支持以下平台： 

- iOS
- Windows 10

### <a name="set-compliance-by-device-location----851881----"></a>按设备位置设置符合性 <!-- 851881 ! -->
在某些情况下，你可能想要将访问企业资源的权限限制到某个特定位置（该位置由网络连接定义）。 你将能够基于设备的 IP 地址来创建符合性策略（“设备合规性” > “位置”）。 如果设备移动到 IP 范围以外，则该设备将无法访问企业资源。

适用于：拥有更新的公司门户应用的 Android 设备 6.0 及更高版本

### <a name="improved-troubleshooting-for-app-installation----928990---"></a>改进了对应用安装的故障排除 <!-- 928990 -->
在 Microsoft Intune MDM 托管的设备上，有时应用安装可能会失败。 当这些应用安装失败时，可能难以了解失败原因或解决此问题。 我们将发布我们的应用疑难解答功能的公共预览版。 你将在每个设备下注意到名为“托管应用”的新节点。 该节点列出了通过 Intune MDM 提供的应用。 在该节点内，将看到应用安装状态的列表。 如果选择单个应用，将看到该特定应用的疑难解答视图。 在疑难解答视图中，将看到应用的端到端生命周期，例如，应用创建、修改、设为目标和提供给设备的时间。 此外，如果应用安装失败，将向你显示错误代码以及有有助于了解错误原因的消息。

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>在冷应用启动和超时时要求非生物识别密码 <!-- 1506985 --> 

在冷应用启动时和管理员指定的超时时长后要求输入非生物识别密码，Intune 会限制使用生物识别来访问公司数据，从而为启用了移动应用程序管理 (MAM) 的应用提升安全性。 这些设置将影响依靠 Touch ID (iOS)、Face ID (iOS)、Android Biometric 或其他未来生物识别身份验证方法访问启用了 APP/MAM 的应用程序的用户。 这些设置将使 Intune 管理员能够更精细地控制用户访问，让带有多个指纹或其他生物识别访问方法的设备只能向正确的用户显示公司数据。 在 Azure 门户中，打开“Microsoft Intune”。 选择“移动应用” > “应用保护策略” > “添加策略” > “设置”。 找到特定设置的“访问”部分。

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>基于未批准的设备供应商和型号阻止应用的访问 <!-- 1425689 ! -->
Intune IT 管理员将能够通过 Intune 应用保护策略来强制实施指定的 Android 制造商和/或 iOS 型号列表。 IT 管理员可以提供适用于 Android 策略的供应商列表和适用于 iOS 策略的设备型号列表，列表以分号分隔。 Intune App 保护策略仅适用于 Android 和 iOS。 针对这一指定的列表，可以执行两个单独的操作：
- 阻止应用访问未指定的设备。
- 或者，选择性地擦除未指定的设备上的企业数据。 

如果未满足策略要求，则用户将无法访问目标应用程序。 根据设置，用户可能会被阻止或选择性地删除应用中的用户企业数据。 在 iOS 设备上，此功能需要应用程序的参与（例如， WXP、Outlook、Managed Browser、Yammer）以便为最低版本设置集成 Intune APP SDK，以针对目标应用程序强制执行。 此集成陆续进行，取决于特定应用程序团队。 在 Android 上，此功能需要使用最新的公司门户。 

在最终用户设备上，Intune 客户端将根据 Intune 边栏选项卡中针对应用程序保护策略所指定的字符串的简单匹配来执行操作。 这完全取决于设备报告的值。 为此，建议 IT 管理员确保预期行为的准确性。 这可以通过根据面向较小规模用户组的各种设备制造商和型号对此设置进行测试来实现。 在 Microsoft Intune 中，选择“移动应用” > “应用保护策略”以查看和添加应用保护策略。 有关应用保护策略的详细信息，请参阅[什么是应用保护策略](app-protection-policy.md)。

### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>在 Windows 10 设备上启用展台模式 <!-- 1560072 ! -->
在 Windows 10 设备上，可以创建配置文件并启用展台模式（“设备配置” > “配置文件” > “创建配置文件” > “Windows 10” > “设备限制” > “展台”）。 在此更新中，“展台(预览版)”设置被重命名为“展台(旧版)”。 不再推荐使用“展台(旧版)”，但该版本在 7 月更新之前仍能正常使用。 “展台(旧版)”被替换为新的“展台”配置文件类型（“创建配置文件” > “Windows 10” > “展台(预览版)”），该类型将包含配置 Windows 10 RS4 和更高版本上的展台的设置。

适用于 Windows 10 和更高版本。

### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>在展台模式下检索适用于企业的 Microsoft Store 应用相关联的应用用户模型 ID (AUMID) <!-- 1560077 ! -->
Intune 将能够检索适用于企业的 Microsoft Store (WSfB) 应用的应用用户模型 ID，以改进展台配置文件的配置。

有关适用于企业的 Microsoft Store 应用的详细信息，请参阅[管理来自适用于企业的 Microsoft Store 应用](windows-store-for-business.md)。

### <a name="access-actions-for-app-protection-policies----1483510-eeready---"></a>应用保护策略操作的访问权限 <!-- 1483510 EEready -->
你将很快能够配置应用保护策略，以显式擦除、阻止或警告不符合要求的设备。 最新的操作“擦除”将从设备中删除贵公司的企业数据。 当出现擦除操作时，系统将会 通知设备用户擦除原因和修正步骤。 对于某些设置（例如，最低操作版本），你将能够应用多个操作，例如阻止和擦除。 在启动应用时，会触发这些操作。

### <a name="new-inventory-information-for-windows-devices----1333569-eeready---"></a>适用于 Windows 设备的新清单信息 <!-- 1333569 eeready -->

对于 Windows 设备，可在每个设备的“硬件”选项卡（“组” > “所有移动设备” > “设备” > 选择用户设备 >“查看属性” > “硬件”）中找到以下清单信息：
- TPM
- 防病毒
- 反间谍软件
- 防火墙
- UAC
- 电池
- 域名

有关 CSP 如何检索此数据的详细信息，请参阅 [DeviceStatus CSP](https://docs.microsoft.com/en-us/windows/client-management/mdm/devicestatus-csp) 文章中的 DeviceStatus 条目。

### <a name="intune-and-the-microsoft-edge-browser----1818969---"></a>Intune 和 Microsoft Edge 浏览器 <!-- 1818969 -->
移动设备（iOS 和 Android）的 Microsoft Edge 浏览器现在支持 Intune 应用保护策略。 在 Microsoft Edge 浏览器应用程序中使用其企业 Azure AD 帐户登录的用户将受 Intune 保护。 

### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766---"></a>配置 Autopilot 的 OOBE 时的新语言/区域设置 <!-- 1821766 -->
在 Out of Box Experience 期间，将提供新的配置设置，以设置 Autopilot 配置文件的语言和区域。

### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>配置设备键盘的新设置 <!-- 1821768 -->
在 Out of Box Experience 期间，将提供新的设置，以配置 Autopilot 配置文件的键盘。

### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>使用 TeamViewer 共享 iOS 和 MacOS 设备的屏幕 <!-- 1985547 -->
当前，可以使用 TeamViewer 来远程管理 [Intune 管理的 Android 和 Windows 设备](device-profile-android-teamviewer.md)。

管理员将能够连接到 TeamViewer，并启动与 iOS 和 macOS 设备之间的屏幕共享会话。 iPhone、iPad 和 macOS 用户可以与任何其他桌面或移动设备实时共享其屏幕。 

### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>设备配置文件图形用户图表已恢复 <!-- 2160133 -->
为了改进设备配置文件图形图表上显示的计数（“设备配置” > “配置文件”> 选择现有配置文件 >“概述”），图形用户图表曾被暂时删除。

在此更新中，图形用户图表得到恢复，并显示在 Azure 门户中。

### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>将所有用户和所有设备分配为范围组 <!-- 2196803 -->
你将能够分配所有用户、所有设备，以及范围组中的所有用户和所有设备。 要执行此操作，请选择“Intune 角色” > “所有角色” > “策略和配置文件管理器” > “分配”> 选择一项分配 >“范围(组)”。

### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>将 AutoPilot 配置文件移动到组目标<!-- 1877935 -->
目前，可向所选设备分配 AutoPilot 部署配置文件。 此功能发布后，以下是分配这些配置文件要执行的操作：
- 创建包含 AutoPilot 设备的 (Azure AD) 组
- 向 Azure AD 组分配所需配置文件。 现在，AutoPilot 配置文件将分配到该组中的 AutoPilot 设备。

### <a name="management-name-field-will-be-editable----1875989---"></a>管理名称字段将可编辑 <!-- 1875989 -->
你将能够编辑设备的“属性”边栏选项卡上的管理名称字段。 若要编辑此字段，请选择“设备” > “所有设备”> 选择设备 >“属性”。 可以使用管理名称字段来唯一标识设备。

<!-- 1804 start -->

### <a name="additions-to-local-device-security-options-settings----1403702---"></a>新增本地设备安全选项设置<!-- 1403702 -->
你将能够配置适用于 Windows 10 设备的其他本地设备安全选项设置。 其他设置将在 Microsoft 网络客户端、Microsoft 网络服务器、网络访问和安全性和交互式登录的区域内可用。 创建 Windows 10 设备配置策略时，可以在终结点保护类别中查找这些设置。

### <a name="rules-for-removing-devices----1609459---"></a>删除设备的规则<!-- 1609459 -->
将提供新规则，用于自动删除未在设置天数内进行签入的设备。 要查看新规则，请转到“Intune”窗格，依次选择“设备”和“设备删除规则”。

### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>在 Windows 10 企业版 RS4 AutoPilot 设备上阻止使用者应用和体验<!-- 1621980 -->
你将能够阻止在 Windows 10 企业版 RS4 AutoPilot 设备上安装使用者应用和体验。 要查看此功能，请转到“Intune” > “设备注册” > “Windows 注册” > “Windows AutoPilot 配置文件” > “新建” > “注册设置”。 

<!-- 1803 start -->

#### <a name="multiple-exchange-connector-support----2070451---"></a>多个 Exchange Connector 支持<!-- 2070451 -->

你将不再受到每租户一个 Microsoft Intune Exchange Connector 的限制。 Intune 将支持多个 Exchange Connector，使你可以设置多个本地 Exchange 组织的 Intune 条件访问。

凭借 Intune 本地 Exchange 连接器，可以根据设备是否已在 Intune 中注册且是否符合 Intune 设备符合性策略来管理设备对本地 Exchange 邮箱的访问。 若要设置连接器，请从 Azure 门户下载 Intune 本地 Exchange 连接器，并将它安装在 Exchange 组织中的服务器上。 在 Microsoft Intune 仪表板上，选择“本地访问”，然后在“设置”下选择“Exchange ActiveSync 连接器”。 下载 Exchange 本地连接器，并将它安装在 Exchange 组织中的服务器上。 由于你已经不再受到每租户一个 Exchange 连接器的限制，因此，如果拥有其他的 Exchange 组织，则可以按照此相同的过程为其他每个 Exchange 组织下载并安装连接器。

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>可以将所需的业务线 (LOB) 应用部署到 Windows 10 桌面版设备上的所有用户 <!-- 1627835 RS4 -->
客户将能够部署所需的业务线 Windows 10 应用以安装在设备上下文中。 这将使这些应用可供此设备上的所有用户可用。 这仅适用于 Windows 10 桌面版设备。

### <a name="company-portal-enrollment-improved----1874230--"></a>改进的公司门户注册 <!-- 1874230-->
通过在 Windows 10 内部版本 1703 和更高版本上使用公司门户注册设备的用户将能够在不退出应用的情况下完成注册的第一步。

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>更新适用于 Android 的公司门户应用上的“帮助和反馈”体验 <!--1631531 -->

将更新适用于 Android 的公司门户应用上的“帮助和反馈”体验以符合 Android 应用的最佳做法。 在未来的几个月里将更新适用于 Android 的公司门户应用，将“帮助和反馈”菜单项分为不同的“帮助”和“发送反馈”菜单项。 “帮助”页面将包含“常见问题”部分和“电子邮件支持”按钮，引导最终用户向 Microsoft 上传日志并向公司支持部门发送电子邮件以描述问题。 “发送反馈”将引导用户完成标准的 Microsoft 反馈提交，这将提示用户选择“我喜欢一些内容”、“我不喜欢一些内容”还是“我有个主意”。

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>应用保护策略<!-- 679615 -->
Intune 应用保护策略将提供创建默认全局策略的功能，以便快速对整个租户中所有用户启用保护。

<!-- the following are present prior to 1711 -->

## <a name="notices"></a>通知

此时没有任何活动通知。

### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。



