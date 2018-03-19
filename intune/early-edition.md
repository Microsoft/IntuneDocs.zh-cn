---
title: "早期版本"
description: 
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9a2c104200518af31fd05e6b8abe853377767aa9
ms.sourcegitcommit: 9cf05d3cb8099e4a238dae9b561920801ad5cdc6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/09/2018
---
# <a name="the-early-edition-for-microsoft-intune---march-2018"></a>Microsoft Intune 的早期版本 - 2018 年 3 月

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

### <a name="enhanced-jailbreak-detection----846515---"></a>增强的越狱检测 <!-- 846515 -->

增强的越狱检测是一个新的符合性设置，将改善 Intune 评估已越狱设备的方式。 此设置将导致设备更频繁地与 Intune 进行确认，这将使用设备的位置服务并将影响电池使用情况。

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>可以将所需的业务线 (LOB) 应用部署到 Windows 10 桌面版设备上的所有用户 <!-- 1627835 RS4 -->
客户将能够部署所需的业务线 Windows 10 应用以安装在设备上下文中。 这将使这些应用可供此设备上的所有用户可用。 这仅适用于 Windows 10 桌面版设备。 

### <a name="expiring-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>即将过期的适用于 Microsoft Intune 的业务线 (LOB) 应用 <!-- 748789 -->
在 Azure 门户中，Intune 将向你发出警报，通知你即将过期的业务线应用。 上传新版本的业务线应用后，Intune 将从应用列表删除过期通知。

### <a name="company-portal-enrollment-improved----1874230--"></a>改进的公司门户注册 <!-- 1874230-->
通过在 Windows 10 内部版本 1703 和更高版本上使用公司门户注册设备的用户将能够在不退出应用的情况下完成注册的第一步。

### <a name="new-management-name-column----1333586---"></a>新的管理名称列 <!-- 1333586 -->
一个名为“管理名称”的新列将添加到设备边栏选项卡上。 这是基于以下公式按每设备分配的自动生成、不可编辑的名称： 
- 所有设备的默认名称：<username>_<devicetype>_<enrollmenttimestamp>
- 对于批量添加的设备：<PackageId/ProfileId>_<DeviceType>_<EnrollmentTime> 
 
在设备边栏选项卡中，这是可选列。 默认情况下将不提供此列，只能通过列选择器进行访问。 设备名称不受此新列的影响。

### <a name="new-settings-for-windows-defender-security-center-notifications-device-configuration-profile----1631906---"></a>适用于 Windows Defender 安全中心通知设备配置文件的新设置 <!-- 1631906 -->

三个新设置将添加到 Windows Defender 安全中心 (WDSC) 通知设备配置文件。

管理员将能够：

- 隐藏“标识”支柱
- 隐藏“硬件”支柱及其子设置
- 隐藏“勒索软件”支柱（Onedrive for Business 文件还原）

从 WDSC 应用隐藏这些支柱后，最终用户将无法配置这些设置，并且将不会生成与已隐藏组件相关的所有通知。

### <a name="mam-policies-targeted-based-on-management-state----1665993---"></a>根据管理状态面向的 MAM 策略 <!-- 1665993 -->

你将能够根据设备的管理状态面向 MAM 策略：

- **iOS 设备** - 你将能够以非托管设备（仅限 MAM）或 Intune 托管设备为目标。
- **Android 设备** - 你将能够以非托管设备、Intune 托管设备和 Intune 托管的 Android Enterprise 配置文件为目标（以前称为 Android for Work）。

### <a name="configure-gatekeeper-to-control-macos-app-download-source----1690459--"></a>配置网关守卫以控制 macOS 应用下载源 <!-- 1690459-->

你将能够配置网关守卫，通过控制可以下载应用的位置以保护设备免受应用侵害。 你将能够配置以下下载源：Mac 应用商店、Mac 应用商店和标识的开发人员或任意位置。 还能够配置用户是否可以通过按住 Ctrl 并单击以替代这些网关守卫控件来安装应用。

可以在“设备配置” -> “创建配置文件” -> “macOS” -> “终结点保护”下找到这些设置。

### <a name="configure-the-mac-application-firewall----1690461---"></a>配置 Mac 应用程序防火墙 <!-- 1690461 -->

你将能够配置 Mac 应用程序防火墙。 可以使用此操作以基于每个应用程序来控制连接，而不是基于每个端口来进行控制。 这样一来，可以更轻松地获得防火墙保护的优势，还有助于防止不良应用控制为合法应用打开的网络端口。
 
可以在“设备配置” -> “创建配置文件” -> “macOS” -> “终结点保护”下找到此功能。

启用防火墙设置后，即可使用两种策略来配置防火墙：

- 阻止所有传入连接

   可以阻止目标设备的所有传入连接。 如果选择进行此操作，将阻止所有应用的传入连接。 

- 允许或阻止特定应用

   可以允许或阻止特定应用接收传入连接。 还可以启用隐藏模式，阻止对探测请求做出响应。
 
#### <a name="more-information"></a>更多信息

- 阻止所有传入连接

   这将阻止所有共享服务（例如文件共享和屏幕共享）接收传入连接。 仍然允许接收传入连接的系统服务包括：
   - configd - 实现 DHCP 和其他网络配置服务
   - mDNSResponder - 实现 Bonjour
   - racoon - 实现 IPSec

   若要使用共享服务，请确保将“传入连接”设置为“未配置”（不“阻止”）。

- 隐藏模式

   启用此选项可防止计算机对探测请求做出响应。 计算机仍然会响应授权应用的传入请求。 意外的请求将被忽略，如 ICMP (ping)。
 

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>更新适用于 Android 的公司门户应用上的“帮助和反馈”体验 <!--1631531 -->

我们将更新适用于 Android 的公司门户应用上的“帮助和反馈”体验以符合 Android 应用的最佳做法。 我们将在未来的几个月里更新适用于 Android 的公司门户应用，将“帮助和反馈”菜单项分为不同的“帮助”和“发送反馈”菜单项。 “帮助”页面将包含“常见问题”部分和“电子邮件支持”按钮，引导最终用户向 Microsoft 上传日志并向公司支持部门发送电子邮件以描述问题。 “发送反馈”将引导用户完成标准的 Microsoft 反馈提交，这将提示用户选择“我喜欢一些内容”、“我不喜欢一些内容”还是“我有个主意”。

### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks----1488911---"></a>批量采购计划 (VPP) 电子书的自定义书籍类别 <!-- 1488911 -->
你将能够创建自定义电子书类别，然后将 VPP 电子书分配到自定义电子书类别。 最终用户即可以看到新建的电子书类别以及分配给该类别的书籍。

#### <a name="company-portal-for-android-visual-updates---976944---"></a>适用于 Android 的公司门户的视觉更新 <!--976944 -->

我们将更新适用于 Android 的公司门户应用以遵循 Android 的 [Material Design](https://material.io/)（材料设计）准则。 应用发布时，我们会将新图标的图像发布到[应用 UI 中的新增内容](whats-new-app-ui.md)一文。 


<!-- 1802 start -->

### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>新的注册失败趋势图表和失败原因表<!-- 1471783 -->

在“注册概述”页，你将能够查看注册失败趋势和前五个失败原因。 单击图表或表可查看详细信息，以查找故障排除建议和修正建议。

### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>使用十六进制代码自定义公司门户主题 <!--1049561 -->

可以使用十六进制代码自定义公司门户应用中的主题颜色。 输入十六进制代码时，Intune 将按照 [WCAG 2.0 标准](http://www.w3.org/TR/WCAG20)确定在文本颜色和背景色之间提供最高级别对比度的文本颜色。 可以在“移动应用” > “公司门户”中预览文本颜色和公司徽标之间的颜色对比。 

### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252---"></a>添加到终结点保护设置的新 Windows Defender Credential Guard 设置 <!--1102252 --> 

新 [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard] 设置将添加到“设备配置” > “配置文件” > “终结点保护”。 将添加以下设置： 

- 平台安全级别：指定平台安全级别是否在下次重启时启用。 基于虚拟化的安全性需要安全启动。 可以选择使用直接内存访问 (DMA) 保护启用基于虚拟化的安全性。 DMA 保护需要硬盘支持并且将仅在正确配置的设备上启用。
- 基于虚拟化的安全性：指定基于虚拟化的安全性是否在下次重启时启用。 
- Windows Defender Credential Guard：当具有安全启动的平台安全级别和基于虚拟化的安全性同时启用时，在下次重启时通过基于虚拟化的安全性打开 Credential Guard 以帮助保护凭据。 可用选项包括“禁用”、“使用 UEFI 锁启用”、“无锁启用”和“未配置”。 
  - “禁用”选项将远程关闭 Credential Guard（如果之前已使用“无锁启用”选项启用）。

  - “使用 UEFI 锁启用”选项可确保 Credential Guard 不能通过注册表项或通过使用组策略禁用。 若要在使用此设置后禁用 Credential Guard，必须将组策略设置为“禁用”，并通过真实存在的用户从每台计算机中删除安全功能，以清除 UEFI 中保留的配置。 只要 UEFI 配置仍然存在，Credential Guard 则会保持启用状态。

  - “无锁启用”选项允许通过使用组策略远程禁用 Credential Guard。 使用此设置的设备必须至少在 Windows 10（版本 1511）上运行。

  - “未配置”选项将策略设置保留为未定义状态。 组策略不会将策略设置写到注册表，所以它不会对计算机或用户造成影响。 如果注册表中存在当前设置，它将不会被修改。

### <a name="reset-passwords-for-android-o-devices----1238299---"></a>重置 Android O 设备的密码 <!-- 1238299 -->
可以重置已注册的 Android O 设备的密码。 将“重置密码”请求发送到 Android O 设备时，它将针对当前用户设置新的设备解锁密码或托管的配置文件质询。 密码或质询是根据设备拥有配置文件所有者还是设备所有者发送的，并且会立即生效。

### <a name="local-device-security-option-settings----1251887---"></a>本地设备安全选项设置 <!-- 1251887 -->
可以使用新的“本地设备安全选项”设置在 Windows 10 设备上启用安全设置。 创建 Windows 10 设备配置策略时，可以在终结点保护类别中查找这些设置。

### <a name="new-printer-settings-for-education-profiles----1308900---"></a>教育配置文件的新打印机设置 <!-- 1308900 -->

对于教育配置文件，新的设置将提供在“打印机”类别下：“打印机”、“默认打印机”、“添加新的打印机”。 

### <a name="ios-app-provisioning-configuration----1581650---"></a>iOS 应用预配配置 <!-- 1581650 -->
可以分配 iOS 应用预配配置文件以通过包括或排除安全组来防止应用过期。

### <a name="new-windows-defender-exploit-guard-settings----631893---"></a>新 Windows Defender 攻击防护设置 <!-- 631893 -->

将提供六个新的“攻击面减少”设置和扩展的“受控文件夹访问权限: 文件夹保护”功能。 这些设置可以在 Device configuration\Profiles\
Create profile\Endpoint protection\Windows Defender Exploit Guard 中找到。

#### <a name="attack-surface-reduction"></a>攻击面减少

|设置名  |设置选项  |描述  |
|---------|---------|---------|
|高级勒索软件防护|启用、审核、未配置|使用激进的勒索软件防护。|
|标记从 Windows 本地安全机构子系统窃取的凭据|启用、审核、未配置|标记从 Windows 本地安全机构子系统 (lsass.exe) 窃取的凭据。|
|来自 PSExec 和 WMI 命令的进程创建|阻止、审核、未配置|阻止来自 PSExec 和 WMI 命令的进程创建。|
|从 USB 运行的不受信任和未签名的进程|阻止、审核、未配置|阻止从 USB 运行的不受信任和未签名的进程。|
|不符合普及程度、年龄或信任列表条件的可执行文件|阻止、审核、未配置|阻止可执行文件的运行，除非这些文件符合普及程度、年龄或信任列表条件。|

#### <a name="controlled-folder-access"></a>受控文件夹访问权限

|设置名  |设置选项  |描述  |
|---------|---------|---------|
|文件夹保护（已实现）|未配置、启用、仅审核（已实现）<br><br> **新建**<br>阻止磁盘修改、审核磁盘修改|
阻止不友好应用对文件和文件夹进行未经授权的更改。<br><br>**启用**：阻止不受信任的应用修改或删除受保护文件夹中的文件，以及阻止写入到磁盘扇区。<br><br>
**仅阻止磁盘修改**：<br>阻止不受信任的应用写入到磁盘扇区。 不受信任的应用仍可以修改或删除受保护文件夹中的文件。|

### <a name="new-windows-defender-application-guard-settings----1631890---"></a>新 Windows Defender 应用程序防护设置 <!-- 1631890 -->

- **启用图形加速**

管理员将可以为 Windows Defender 应用程序防护启用虚拟图形处理器。 此设置使 CPU 可以将图形呈现卸载到 vGPU。 这可以提升使用图形密集型网站或在容器中观看视频时的性能。

- **SaveFilestoHost**

管理员将可以使文件从在容器中运行的 Microsoft Edge 传递到主机文件系统。 打开此选项将使用户可以从容器中的 Microsoft Edge 将文件下载到主机文件系统。

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>根据 Android Enterprise 组包括和排除应用分配 <!-- 1813081 -->
在应用分配期间以及选择分配类型后，Android Enterprise（以前称为 Android for Work）将支持排除功能。

<!-- the following are present prior to 1802 -->

### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>将符合性策略定目标到设备组中的设备 <!--1307012 -->

将可以把符合性策略定目标到用户组中的用户。 将可以把符合性策略定目标到设备组中的设备。

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>应用保护策略<!-- 679615 -->
Intune 应用保护策略将提供创建默认全局策略的功能，以便快速对整个租户中所有用户启用保护。

### <a name="configure-an-ios-app-pin----1586774---"></a>配置 iOS 应用 PIN <!-- 1586774 -->
很快，便能要求目标 iOS 应用使用 PIN。 几天后，还可通过 Azure 门户配置 PIN 需求和到期日期。 需要时，用户必须设置并使用新的 PIN 才有权访问 iOS 应用。 只有使用 Intune App SDK 启用应用保护的 iOS 应用才支持此功能。

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory 网站可能需要 Intune Managed Browser 应用，并且支持 Managed Browser（公共预览版）的单一登录<!-- 710595 -->   
利用 Azure Active Directory (Azure AD)，可在移动设备上将对网站的访问限于 Intune Managed Browser 应用。 在 Managed Browser 中，网站数据可保持安全并且独立于最终用户的个人数据。 此外，Managed Browser 支持受 Azure AD 保护的站点的单一登录功能。 通过登录 Managed Browser，或在设备上将 Managed Browser 与由 Intune 管理的其他应用配合使用，用户无需输入凭据，Managed Browser 即可访问受 Azure AD 保护的公司站点。 此功能适用于 Outlook Web Access (OWA) 和 SharePoint Online 等站点，以及通过 Azure 应用代理访问的 Intranet 资源等其他公司站点。

<!-- the following are present prior to 1711 -->

### <a name="redirecting-macos-users-to-the-new-company-portal-app---1380728--"></a>将 macOS 用户重定向到新公司门户应用 <!--1380728-->   
当最终用户登录公司门户网站注册其 macOS 设备时，系统会将其定向到下载 macOS 版新公司门户应用的页面，以便完成此过程。 使用 OS X El Capitan 10.11 或更高版本的 macOS 设备会出现这种情况。 

<!-- the following are present prior to 1709 -->

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>改进了用户达到允许注册的最大设备数时提示的错误消息 <!-- 1270370 -->
使用 Android 设备的最终用户将不再看到通用错误消息，而将看到下面可操作的友好错误消息：“注册设备数已达到 IT 管理员允许的数量上限。请删除已注册的设备，或者向 IT 管理员寻求帮助。”



## <a name="notices"></a>通知

此时没有任何活动通知。



### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。


