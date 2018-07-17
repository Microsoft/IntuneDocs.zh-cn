---
title: 早期版本
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 609e142551344a1ce39761280031463c8e34f1f0
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2018
ms.locfileid: "37906016"
---
# <a name="the-early-edition-for-microsoft-intune---july-2018"></a>Microsoft Intune 的早期版本 - 2018 年 7 月

> [!Note]
> NDA 通知：下面的 Intune 更改仍处于开发阶段。 此信息在 NDA 下共享，但具有严格限制。 请勿在 Twitter、UserVoice、Reddit 等社交媒体或公共网站上发布此信息。 

早期版本提供了一份即将发布的 Microsoft Intune 版本中将出现的功能列表（在 NDA 下共享）。 此信息的提供具有条件限制，并且会不断变化。 请勿发布推文、在 UserVoice 上发帖，或者以其他方式在公司外部共享此信息。 此处列出的某些功能有无法按期发布的风险并可能推迟到以后的版本。 正在以试验模式（外部测试）测试其他功能，以确保它们可立即供客户使用。 如果有任何问题或顾虑，请与 Microsoft 产品组联系人联系。

本页将定期更新。 返回查看其他更新。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure 门户中的 Intune

<!-- 1807 start -->

### <a name="reset-device-passcodes-from-company-portal-app-for-windows-10----2101282---"></a>从适用于 Windows 10 的公司门户重置设备密码 <!-- 2101282 --> 
员工很快就可以直接从 Windows 10 的公司门户应用重置其设备的 PIN 或密码。 此功能将在支持重置密码的远程和本地 Intune 管理的设备上提供。 根据设备类型，对远程设备的请求将删除设备的当前密码或创建临时密码。 请求重置本地设备的用户将重定向到设备的“设置”应用。  

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows----2317227---"></a>适用于 Windows 的公司门户应用中的新浏览体验<!-- 2317227 -->  
在适用于 Windows 的公司门户应用中浏览或搜索应用时，用户将能在现有的“磁贴”视图和新添加的“详细信息”视图之间切换。 新视图列出应用程序详细信息，如名称、发布服务器、发布日期和安装状态。  

“应用”页将介绍“已安装的”视图，通过该视图可查看已完成和正在进行的应用安装的详细信息。 想分享有关新变化的反馈或想法吗？ 请在公司门户应用中向我们发送反馈。

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>针对设备注册管理员用户，改进了公司门户应用体验 <!-- 675800 -->
当设备注册管理员 (DEM) 登录到适用于 Windows 的公司门户应用时，该应用将仅列出 DEM 的当前正在运行的设备。 此改进将减少以前应用尝试加载所有 DEM 注册设备时出现的超时。  

### <a name="use-smime-to-encrypt-and-sign-a-users-multiple-devices-----1333642---"></a>使用 S/MIME 对用户的多个设备进行加密和签名 <!-- 1333642 -->
未来的更新将包括使用新导入的证书配置文件进行 S/MIME 电子邮件加密（“设备配置” > “配置文件” > “创建配置文件”>“选择平台”>“PKCS 导入的证书”配置文件类型）。 在 Intune 中，可以 PFX 格式导入证书。 然后 Intune 可以将这些相同的证书传递给单个用户注册的多个设备。 还包括：

- 本机 iOS 电子邮件配置文件支持使用 PFX 格式的导入证书启用 S/MIME 加密。
- Windows Phone 10 设备上的本机电子邮件应用自动使用 S/MIME 证书。
- 可以跨多个平台传递私有证书。 但并非所有电子邮件应用都支持 S/MIME。
- 在其他平台上，可能需要手动配置电子邮件应用以启用 S/MIME。  
- 支持 S/MIME 加密的电子邮件应用可能以 MDM 不支持的方式（例如从发布者的证书存储读取）处理对 S/MIME 电子邮件加密的证书检索。

支持的设备：Windows、Windows Phone 10、macOS、iOS、Android

### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>在 DEP 注册期间，使用 VPP 设备许可证预先设置公司门户 <!-- 1608345 -->
在设备注册计划 (DEP) 注册期间，可以使用批量采购计划 (VPP) 设备许可证预先设置公司门户。 若要完成此操作，在创建或编辑注册配置文件时，指定要用于安装公司门户的 VPP 令牌。 请确保令牌没有过期，并且具有足够的公司门户应用许可证。 如果令牌过期或许可证用完，Intune 将改为推送 App Store 公司门户（这将提示输入 Apple ID）。

### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>在设备边栏选项卡上批量删除设备 <!-- 1793693 -->
可在设备边栏选项卡一次删除多个设备。 选择“设备” > “所有设备”>“选择要删除的设备”>“删除”。 对于无法删除的设备，会出现警告。

### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Windows 10 及更高版本的新 Wi-Fi 设备配置文件 <!-- 1879077 -->
目前，可以使用 XML 文件导入和导出 Wi-Fi 配置文件。 将能够直接在 Intune 中创建 Wi-Fi 配置文件，就与在某些其他平台上的操作一样。

若要创建配置文件，打开“设备配置” > “配置文件” > “创建配置文件” > “Windows 10 及更高版本” > “Wi-Fi”。 

适用于 Windows 10 和更高版本。

###  <a name="windows-line-of-business-lob-apps-file-extension-rename----1884873---"></a>Windows 业务线 (LOB) 应用文件扩展名重命名 <!-- 1884873 -->
Windows LOB 应用的文件扩展名将从 .appx 和 .appxbundle 重命名为 .msix 和 .msixbundle。 可以在 Microsoft Intune 中添加应用，方法是通过选择“移动应用” > “应用” > “添加”。 将显示“添加应用”窗格，可选择“应用类型”。 对于 Windows LOB 应用，选择“业务线”应用作为应用类型，选择“应用包文件”，然后输入带有扩展名的安装文件。

### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Windows Defender ATP 配置包自动添加到配置文件 <!-- 2144658 -->
在 Intune 中使用[高级威胁防护和加入](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile)设备时，下载配置包，并将其添加到配置文件。 在未来的更新中，Intune 自动从 Windows Defender 安全中心获取包，并将其添加到配置文件。

适用于 Windows 10 和更高版本。

### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998---"></a>Kiosk - 已过时显示为灰色，无法更改 <!-- 2149998 -->
[Kiosk 功能](device-restrictions-windows-10.md#kiosk-preview---obsolete)“设备配置” > “配置文件” > “创建配置文件” > “Windows 10 及更高版本” > “设备限制”将过时，并替换为 [Windows 10 和更高版本的 Kiosk 设置](kiosk-settings.md)。 “Kiosk - 已过时”功能将显示为灰色，并且无法更改或更新用户界面。 

若要启用展台模式，请参阅 [Windows 10 及更高版本的 Kiosk 设置](kiosk-settings.md)。

应用于 Windows 10 及更高版本、Windows Holographic for Business

### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>使用第 3 方证书颁发机构的 API <!-- 2184013 -->
将有一个 Java API，使第三方证书颁发机构能与 Intune 和 SCEP 集成。 然后用户可以将 SCEP 证书添加到配置文件，并使用 MDM 将其应用于设备。

目前 Intune 支持[使用 Active Directory 证书服务的 SCEP 请求](certificates-scep-configure.md)。

### <a name="check-for-sccm-compliance----2192052---"></a>检查 SCCM 符合性 <!-- 2192052 -->
未来的更新将包括新的 System Center Configuration Manager (SCCM) 符合性设置（“设备符合性” > “策略” > “创建策略” > “Windows 10”。 SCCM 向 Intune 符合性发送信号。 使用 Intune 设置，可以要求所有 SCCM 信号都返回“符合”。

例如，要求所有软件更新都安装在设备上。 在 SCCM, 中，此要求具有“已安装”状态。 如果设备上的任何计划都处于未知状态，则此设备在 Intune 中不兼容。

适用于 Windows 10 及更高版本

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>针对即将过期的 VPP 令牌或公司门户许可证不足的警报 <!-- 2237572 -->
如果在 DEP 注册期间使用批量采购计划 (VPP) 预先设置公司门户，则在 VPP 令牌即将过期以及公司门户的许可证不足的情况下，Intune 将发出警报。

### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>需要确认才能删除正用于公司门户预先设置的 VPP 令牌 <!-- 2237634 -->
如果在 DEP 注册期间正在使用批量购买计划 (VPP) 预先设置公司门户，则需要确认是否删除此令牌。

### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>自动标记使用 Samsung Knox 移动注册为“公司”注册的 Android 设备 <!-- 2404851 -->
默认情况下，使用 Samsung Knox 移动注册的 Android 设备将标记为“设备所有权”下的“公司”。 使用 Knox 移动注册之前，将不需要使用 IMEI 或序列号手动识别公司设备。

### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>切换以显示或不显示 Kiosk 浏览器上的“结束会话”按钮 <!-- 2455253 -->
将可以配置以决定 Kiosk 浏览器是否显示“结束会话”按钮。 可以在“设备配置” > “Kiosk（预览）” > “Kiosk Web 浏览器”中看到控件。 若关闭，用户单击按钮时，应用会提示是否结束会话。 确定结束时，浏览器清除所有浏览数据并导航回到默认 URL。

### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>创建 eSIM 卡移动电话配置文件 <!-- 2564077 -->
在“设备配置”中，将能够创建 eSIM 卡移动电话配置文件。 可以导入包含移动运营商提供的移动电话激活码的文件。 然后，可以将这些配置文件部署到支持 eSIM LTE 的 Windows 10 设备，例如 Surface Pro LTE 和其他支持 eSIM 卡的设备。

检查[设备是否支持 eSIM 卡配置文件](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data)。

适用于 Windows 10 和更高版本。 




<!-- 1806 start -->


### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>可通过 iOS 上的 APP 设置阻止第三方键盘 <!-- 1248481 -->
在 iOS 设备上，Intune 管理员可以阻止使用第三方键盘在受策略保护的应用中访问组织数据。 当应用程序保护策略 (APP) 设置为阻止第三方键盘时，设备用户将在首次使用第三方键盘与公司数据交互时收到一条消息。 将阻止本地键盘以外的所有选项都，设备用户不会看到它们。 设备用户只会看到一次对话消息。 

### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>在 macOS 设备上使用防火墙设置创建设备符合性策略 <!-- 1497640 -->
创建新的 macOS 符合性策略（“设备符合性” > “策略” > “创建策略” > “平台: macOS” > “系统安全”）时，会有一些新的可用“防火墙”设置： 
- 防火墙：配置环境对传入连接的处理方式。
- 传入连接：阻止所有传入连接，DHCP、Bonjour 和 IPSec 等基本 Internet 服务需要的连接除外。 此设置还会阻止所有共享服务。
- 隐藏模式：启用隐藏模式以防止设备响应探测请求。 设备会继续回应已授权应用的传入请求。

适用于：macOS 10.12 及更高版本

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>在应用启动和超时时要求输入非生物识别密码 <!-- 1506985 -->

在应用启动时和管理员指定的超时时长后要求输入非生物识别密码，Intune 会限制使用生物识别来访问公司数据，从而为启用了移动应用程序管理 (MAM) 的应用提升安全性。 这些设置将影响依靠 Touch ID (iOS)、Face ID (iOS)、Android Biometric 或其他未来生物识别身份验证方法访问启用了 APP/MAM 的应用程序的用户。 这些设置将使 Intune 管理员能够更精细地控制用户访问，让带有多个指纹或其他生物识别访问方法的设备只能向正确的用户显示公司数据。 在 Azure 门户中，打开“Microsoft Intune”。 选择“移动应用” > “应用保护策略” > “添加策略” > “设置”。 找到特定设置的“访问”部分。

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus 语言包 <!-- 1833450 -->
作为 Intune 管理员，你将能够为通过 Intune 管理的 Office 365 Pro Plus 应用部署其他语言。 可用语言列表包括语言包的“类型”（核心、部分和校对）。 在 Azure 门户中，选择“Microsoft Intune” > “移动应用” > “应用” > “添加”。 在“添加应用”边栏选项卡的“应用类型”列表中，选择“Office 365 套件”下的“Windows 10”。 在“应用套件设置”边栏选项卡中选择“语言”。

### <a name="preview-a-new-user-experience-update-for-the-company-portal-website---2000968---"></a>预览公司门户网站的新用户体验更新<!--2000968 -->
我们根据客户的反馈向公司门户网站/iOS 应用目录添加新功能。 可从 Android、iOS 和 Windows 设备上体验到现有功能和可用性方面的重大改进。 该网站的各个区域（如设备详细信息、反馈与支持以及设备概述）都采用了全新的现代化快速响应设计。 你还会看到：

- 简化了所有设备平台上的工作流
- 改进了设备识别和注册流
- 提供了更多有用的错误消息
- 语言更加友好，减少了技术术语的使用
- 共享指向应用的直接链接的功能
- 改善了大型应用目录的性能
- 为所有用户增加了辅助功能

更新当前处于预览状态。 可以在 http://aka.ms/webcpflighting 注册以加入预览


### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>编辑 Office 365 Pro Plus 应用部署 <!-- 2150145 -->
作为 Microsoft Intune 管理员，你现在可以对 Office 365 Pro Plus 应用部署进行更多编辑。 在 Azure 门户中，选择“Microsoft Intune” > “移动应用” > “应用”。 从应用列表中选择你的 Office 365 Pro Plus 套件。  

<!-- 1805 start -->

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>在冷应用启动和超时时要求非生物识别密码 <!-- 1506985 --> 

在冷应用启动时和管理员指定的超时时长后要求输入非生物识别密码，Intune 会限制使用生物识别来访问公司数据，从而为启用了移动应用程序管理 (MAM) 的应用提升安全性。 这些设置将影响依靠 Touch ID (iOS)、Face ID (iOS)、Android Biometric 或其他未来生物识别身份验证方法访问启用了 APP/MAM 的应用程序的用户。 这些设置将使 Intune 管理员能够更精细地控制用户访问，让带有多个指纹或其他生物识别访问方法的设备只能向正确的用户显示公司数据。 在 Azure 门户中，打开“Microsoft Intune”。 选择“移动应用” > “应用保护策略” > “添加策略” > “设置”。 找到特定设置的“访问”部分。

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>基于未批准的设备供应商和型号阻止应用的访问 <!-- 1425689 ! -->
Intune IT 管理员将能够通过 Intune 应用保护策略来强制实施指定的 Android 制造商和/或 iOS 型号列表。 IT 管理员可以提供适用于 Android 策略的供应商列表和适用于 iOS 策略的设备型号列表，列表以分号分隔。 Intune App 保护策略仅适用于 Android 和 iOS。 针对这一指定的列表，可以执行两个单独的操作：
- 阻止应用访问未指定的设备。
- 或者，选择性地擦除未指定的设备上的企业数据。 

如果未满足策略要求，则用户将无法访问目标应用程序。 根据设置，用户可能会被阻止或选择性地删除应用中的用户企业数据。 在 iOS 设备上，此功能需要应用程序的参与（例如， WXP、Outlook、Managed Browser、Yammer）以便为最低版本设置集成 Intune APP SDK，以针对目标应用程序强制执行。 此集成陆续进行，取决于特定应用程序团队。 在 Android 上，此功能需要使用最新的公司门户。 

在最终用户设备上，Intune 客户端将根据 Intune 边栏选项卡中针对应用程序保护策略所指定的字符串的简单匹配来执行操作。 这完全取决于设备报告的值。 为此，建议 IT 管理员确保预期行为的准确性。 这可以通过根据面向较小规模用户组的各种设备制造商和型号对此设置进行测试来实现。 在 Microsoft Intune 中，选择“移动应用” > “应用保护策略”以查看和添加应用保护策略。 有关应用保护策略的详细信息，请参阅[什么是应用保护策略](app-protection-policy.md)。


<!-- 1803 start -->

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>可以将所需的业务线 (LOB) 应用部署到 Windows 10 桌面版设备上的所有用户 <!-- 1627835 RS4 -->
客户将能够部署所需的业务线 Windows 10 应用以安装在设备上下文中。 这将使这些应用可供此设备上的所有用户可用。 这仅适用于 Windows 10 桌面版设备。

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
