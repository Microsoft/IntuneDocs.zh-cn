---
title: 早期版本
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f3cbfad85e4a7a97d9bbf98e2ad239fda7cc29e4
ms.sourcegitcommit: d40bfb6af66f2ce7026c0151ace98ec23f1cf76e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="the-early-edition-for-microsoft-intune---may-2018"></a>Microsoft Intune 的早期版本 - 2018 年 5 月

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

<!-- 1805 start -->

### <a name="set-compliance-by-device-location----851881----"></a>按设备位置设置符合性 <!-- 851881 ! -->
在某些情况下，你可能想要将访问企业资源的权限限制到某个特定位置（该位置由网络连接定义）。 你将能够基于设备的 IP 地址来创建符合性策略（“设备合规性” > “位置”）。 如果设备移动到 IP 范围以外，则该设备将无法访问企业资源。

### <a name="improved-troubleshooting-for-app-installation----928990---"></a>改进了对应用安装的故障排除 <!-- 928990 -->
在 Microsoft Intune MDM 托管的设备上，有时应用安装可能会失败。 当这些应用安装失败时，可能难以了解失败原因或解决此问题。 我们将发布我们的应用疑难解答功能的公共预览版。 你将在每个设备下注意到名为“托管应用”的新节点。 该节点列出了通过 Intune MDM 提供的应用。 在该节点内，将看到应用安装状态的列表。 如果选择单个应用，将看到该特定应用的疑难解答视图。 在疑难解答视图中，将看到应用的端到端生命周期，例如，应用创建、修改、设为目标和提供给设备的时间。 此外，如果应用安装失败，将向你显示错误代码以及有有助于了解错误原因的消息。 

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
你将很快能够配置应用保护策略，以显式擦除、阻止或警告不符合要求的设备。 最新的操作“擦除”将从设备中删除贵公司的企业数据。 当出现擦除操作时，系统将会 通知设备用户擦除原因和修正步骤。 对于某些设置（例如，最低操作版本），你将能够应用多个操作，例如阻止和擦除。

### <a name="new-inventory-information-for-windows-devices----1333569-eeready---"></a>适用于 Windows 设备的新清单信息 <!-- 1333569 eeready -->

对于 Windows 设备，可在每个设备的“硬件”选项卡（“组” > “所有移动设备” > “设备” > 选择用户设备 >“查看属性” > “硬件”）中找到以下清单信息：
- TPM
- 防病毒
- 反间谍软件
- 防火墙
- UAC
- 电池
- 域名

有关 SCP 如何检索此数据的详细信息，请参阅 [DeviceStatus CSP](https://docs.microsoft.com/en-us/windows/client-management/mdm/devicestatus-csp) 文章中的 DeviceGuard 条目。

### <a name="intune-and-the-microsoft-edge-browser----1818969---"></a>Intune 和 Microsoft Edge 浏览器 <!-- 1818969 -->
移动设备（iOS 和 Android）的 Microsoft Edge 浏览器现在支持 Intune 应用保护策略。 在 Edge 浏览器应用程序中使用其企业 Azure AD 帐户登录的用户将受 Intune 保护。 

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
你将能够分配所有用户、所有设备，以及范围组中的所有用户和所有设备。

### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>将 AutoPilot 配置文件移动到组目标<!-- 1877935 -->
目前，可向所选设备分配 AutoPilot 部署配置文件。 此功能发布后，以下是分配这些配置文件要执行的操作：
- 创建包含 AutoPilot 设备的 (Azure AD) 组
- 向 Azure AD 组分配所需配置文件。 现在，AutoPilot 配置文件将分配到该组中的 AutoPilot 设备。

### <a name="management-name-field-will-be-editable----1875989---"></a>管理名称字段将可编辑 <!-- 1875989 -->
你将能够编辑设备的“属性”边栏选项卡上的管理名称字段。 若要编辑此字段，请选择“设备” > “所有设备”> 选择设备 >“属性”。 可以使用管理名称字段来唯一标识设备。

<!-- 1804 start -->


### <a name="additions-to-local-device-security-options-settings----1403702---"></a>新增本地设备安全选项设置<!-- 1403702 -->
你将能够配置适用于 Windows 10 设备的其他本地设备安全选项设置。 其他设置将在 Microsoft 网络客户端、Microsoft 网络服务器、网络访问和安全性和交互式登录的区域内可用。 创建 Windows 10 设备配置策略时，可以在终结点保护类别中查找这些设置。

### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>需要安装策略、应用、证书和网络配置文件<!-- 1553555 -->
除非 Intune 在 AutoPilot 设备预配期间安装策略、应用、证书和网络配置文件，否则管理员将能够阻止最终用户访问 Windows 10 RS4 桌面。

### <a name="rules-for-removing-devices----1609459---"></a>删除设备的规则<!-- 1609459 -->
将提供新规则，用于自动删除未在设置天数内进行签入的设备。 要查看新规则，请转到“Intune”窗格，依次选择“设备”和“设备删除规则”。

### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>在 Windows 10 企业版 RS4 AutoPilot 设备上阻止使用者应用和体验<!-- 1621980 -->
你将能够阻止在 Windows 10 企业版 RS4 AutoPilot 设备上安装使用者应用和体验。 要查看此功能，请转到“Intune” > “设备注册” > “Windows 注册” > “Windows AutoPilot 配置文件” > “新建” > “注册设置”。 

<!-- 1803 start -->

#### <a name="multiple-exchange-connector-support----2070451---"></a>多个 Exchange Connector 支持<!-- 2070451 -->

你将不再受到每租户一个 Microsoft Intune Exchange Connector 的限制。 Intune 将支持多个 Exchange Connector，使你可以设置多个本地 Exchange 组织的 Intune 条件访问。

凭借 Intune 本地 Exchange 连接器，可以根据设备是否已在 Intune 中注册且是否符合 Intune 设备符合性策略来管理设备对本地 Exchange 邮箱的访问。 若要设置连接器，请从 Azure 门户下载 Intune 本地 Exchange 连接器，并将它安装在 Exchange 组织中的服务器上。 在 Microsoft Intune 仪表板上，选择“本地访问”，然后在“设置”下选择“Exchange ActiveSync 连接器”。 下载 Exchange 本地连接器，并将它安装在 Exchange 组织中的服务器上。 由于你已经不再受到每租户一个 Exchange 连接器的限制，因此，如果拥有其他的 Exchange 组织，则可以按照此相同的过程为其他每个 Exchange 组织下载并安装连接器。

### <a name="support-coming-for-new-cisco-anyconnect-client-for-ios----1333708---"></a>即将为适用于 iOS 的新 Cisco AnyConnect 客户端提供支持 <!-- 1333708 -->

为适用于 iOS 的 Cisco AnyConnect 创建的新 VPN 配置文件将适用于 Cisco AnyConnect 4.0.7x 和更高版本。 现有 iOS Cisco AnyConnect VPN 配置文件将被标记为“Cisco Legacy AnyConnect”，并将继续适用于 Cisco AnyConnect 4.0.5x，如现在一样。

> [!NOTE]
> 此更改仅适用于 iOS；将继续只提供一个适用于 Android、Android for Work 和 macOS 的 Cisco AnyConnect 选项。

#### <a name="more-information"></a>更多信息

需要创建新的 iOS Cisco AnyConnect VPN 配置文件以支持新应用，因为新的 Cisco AnyConnect 应用和 Cisco Legacy AnyConnect 应用是单独的应用。 如果是在环境中管理 AnyConnect 客户端的，还需要部署新的 Cisco AnyConnect 应用。 若要完成升级，还需要删除 Cisco Legacy AnyConnect 配置文件，并删除 Cisco Legacy AnyConnect 应用。

在初始版本中，网络访问控制 (NAC) 集成将不适用于新的 AnyConnect 客户端。 我们正在与 Cisco 合作，以在未来的 Intune 版本中提供 NAC 集成。

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>可以将所需的业务线 (LOB) 应用部署到 Windows 10 桌面版设备上的所有用户 <!-- 1627835 RS4 -->
客户将能够部署所需的业务线 Windows 10 应用以安装在设备上下文中。 这将使这些应用可供此设备上的所有用户可用。 这仅适用于 Windows 10 桌面版设备。

### <a name="company-portal-enrollment-improved----1874230--"></a>改进的公司门户注册 <!-- 1874230-->
通过在 Windows 10 内部版本 1703 和更高版本上使用公司门户注册设备的用户将能够在不退出应用的情况下完成注册的第一步。

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>更新适用于 Android 的公司门户应用上的“帮助和反馈”体验 <!--1631531 -->

我们将更新适用于 Android 的公司门户应用上的“帮助和反馈”体验以符合 Android 应用的最佳做法。 我们将在未来的几个月里更新适用于 Android 的公司门户应用，将“帮助和反馈”菜单项分为不同的“帮助”和“发送反馈”菜单项。 “帮助”页面将包含“常见问题”部分和“电子邮件支持”按钮，引导最终用户向 Microsoft 上传日志并向公司支持部门发送电子邮件以描述问题。 “发送反馈”将引导用户完成标准的 Microsoft 反馈提交，这将提示用户选择“我喜欢一些内容”、“我不喜欢一些内容”还是“我有个主意”。

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
