---
title: 早期版本
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6cc33bc6e03d2e0370c9e2c2dd9d3462296710e6
ms.sourcegitcommit: e814cfbbefe818be3254ef6f859a7bf5f5b99123
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2018
ms.locfileid: "43329678"
---
# <a name="the-early-edition-for-microsoft-intune---august-2018"></a>Microsoft Intune 的早期版本 - 2018 年 8 月

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

<!-- 1808 start -->



### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>另一个 MDM 使用的 Apple VPP 令牌 <!-- 1488946 -->
Intune 会检测是否 Intune 和另一个 MDM 同时在使用同一个 Apple 批量采购计划 (VPP) 令牌，并显示相关详细信息。

### <a name="ios-version-number-and-build-number-are-shown----1892471---"></a>显示 iOS 版本号和生成号 <!-- 1892471 -->
在“设备符合性” > “设备符合性”中，会显示 iOS 操作系统版本。 在未来的某个更新中，会显示生成号。
Apple 每次发布安全更新时，会保留版本号，更新生成号。 通过所显示的生成号，可轻松确认是否已安装漏洞更新。

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>“设备符合性仪表板”中的停用设备 <!-- 1981119 -->
未来的某个更新将从设备符合性仪表板中删除已停用的设备。 这会改变符合性数字。

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>公司门户网站的新用户体验更新<!--2000968 -->
将根据客户的反馈向公司门户网站添加新功能。 可从 Android、iOS 和 Windows 设备上体验到现有功能和可用性方面的重大改进。 该网站的各个区域（如设备详细信息、反馈与支持以及设备概述）都采用了全新的现代化快速响应设计。 你还会看到：
- 简化了所有设备平台上的工作流
- 改进了设备识别和注册流
- 提供了更多有用的错误消息
- 语言更加友好，减少了技术术语的使用
- 共享指向应用的直接链接的功能
- 改善了大型应用目录的性能
- 为所有用户增加了辅助功能

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>将配置文件配置为在“设置助手”期间跳过某些屏幕 <!-- 2276470 -->
创建 macOS 注册配置文件时，可将其配置为在用户使用设置助手期间跳过以下任一屏幕：
- Android 迁移
- 显示基调
- 隐私
- iCloudStorage

### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>本地连接器更新过程的更改 <!-- 2277554 -->
将根据客户反馈更改本地连接器的更新方式。 初次安装本地连接器之后，会自动对其进行更新。 此更改首先应用于适用于 Microsoft Intune 的全新 PFX 证书连接器，随后会推广至其他类型的本地连接器。 



<!-- 1807 start -->

### <a name="more-sync-opportunities-in-the-company-portal-app-for-windows----2683177---"></a>适用于 Windows 的公司门户应用中的更多同步机会 <!-- 2683177 -->
适用于 Windows 的公司门户应用即将向 Windows 任务栏和“开始”菜单跳转列表添加设备同步操作。 单击两个位置之一，即可快速同步设备，并获取对公司资源的访问权限。  

### <a name="reset-device-passcodes-from-company-portal-app-for-windows-10----2101282---"></a>从适用于 Windows 10 的公司门户重置设备密码 <!-- 2101282 --> 
员工很快就可以直接从 Windows 10 的公司门户应用重置其设备的 PIN 或密码。 此功能将在支持重置密码的远程和本地 Intune 管理的设备上提供。 根据设备类型，对远程设备的请求将删除设备的当前密码或创建临时密码。 请求重置本地设备的用户将重定向到设备的“设置”应用。  

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows----2317227---"></a>适用于 Windows 的公司门户应用中的新浏览体验<!-- 2317227 -->  
在适用于 Windows 的公司门户应用中浏览或搜索应用时，用户将能在现有的“磁贴”视图和新添加的“详细信息”视图之间切换。 新视图列出应用程序详细信息，如名称、发布服务器、发布日期和安装状态。  

“应用”页将介绍“已安装的”视图，通过该视图可查看已完成和正在进行的应用安装的详细信息。 想分享有关新变化的反馈或想法吗？ 请在公司门户应用中向我们发送反馈。

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>针对设备注册管理员用户，改进了公司门户应用体验 <!-- 675800 -->
当设备注册管理员 (DEM) 登录到适用于 Windows 的公司门户应用时，该应用将仅列出 DEM 的当前正在运行的设备。 此改进将减少以前应用尝试加载所有 DEM 注册设备时出现的超时。  

### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>在 DEP 注册期间，使用 VPP 设备许可证预先设置公司门户 <!-- 1608345 -->
在设备注册计划 (DEP) 注册期间，可以使用批量采购计划 (VPP) 设备许可证预先设置公司门户。 若要完成此操作，在创建或编辑注册配置文件时，指定要用于安装公司门户的 VPP 令牌。 请确保令牌没有过期，并且具有足够的公司门户应用许可证。 如果令牌过期或许可证用完，Intune 将改为推送 App Store 公司门户（这将提示输入 Apple ID）。

### <a name="check-for-sccm-compliance----2192052---"></a>检查 SCCM 符合性 <!-- 2192052 -->
未来的更新将包括新的 System Center Configuration Manager (SCCM) 符合性设置（“设备符合性” > “策略” > “创建策略” > “Windows 10”。 SCCM 向 Intune 符合性发送信号。 使用 Intune 设置，可以要求所有 SCCM 信号都返回“符合”。

例如，要求所有软件更新都安装在设备上。 在 SCCM, 中，此要求具有“已安装”状态。 如果设备上的任何计划都处于未知状态，则此设备在 Intune 中不兼容。

适用于 Windows 10 及更高版本

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>针对即将过期的 VPP 令牌或公司门户许可证不足的警报 <!-- 2237572 -->
如果在 DEP 注册期间使用批量采购计划 (VPP) 预先设置公司门户，则在 VPP 令牌即将过期以及公司门户的许可证不足的情况下，Intune 将发出警报。

### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>需要确认才能删除正用于公司门户预先设置的 VPP 令牌 <!-- 2237634 -->
如果在 DEP 注册期间正在使用批量购买计划 (VPP) 预先设置公司门户，则需要确认是否删除此令牌。

#### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Windows Installer 的其他安全设置 <!-- 2282430 -->
可允许用户控制应用安装。 如果启用，则允许因安全冲突而停止的安装继续进行。 当 Windows Installer 在系统上安装任何程序时，可指示它使用提升的权限。 此外，将能够对 Windows 信息保护 (WIP) 项目编制索引，并将有关这些项目的元数据存储在未加密的位置。 禁用策略后，将不会对受 WIP 保护的项编制索引，也不会在 Cortana 或文件资源管理器的结果中显示这些项。 默认情况下将禁用这些选项的功能。 

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>可通过 iOS 上的 APP 设置阻止第三方键盘 <!-- 1248481 -->
在 iOS 设备上，Intune 管理员可以阻止使用第三方键盘在受策略保护的应用中访问组织数据。 当应用程序保护策略 (APP) 设置为阻止第三方键盘时，设备用户将在首次使用第三方键盘与公司数据交互时收到一条消息。 将阻止本地键盘以外的所有选项都，设备用户不会看到它们。 设备用户只会看到一次对话消息。 

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>在应用启动和超时时要求输入非生物识别密码 <!-- 1506985 -->

在应用启动时和管理员指定的超时时长后要求输入非生物识别密码，Intune 会限制使用生物识别来访问公司数据，从而为启用了移动应用程序管理 (MAM) 的应用提升安全性。 这些设置将影响依靠 Touch ID (iOS)、Face ID (iOS)、Android Biometric 或其他未来生物识别身份验证方法访问启用了 APP/MAM 的应用程序的用户。 这些设置将使 Intune 管理员能够更精细地控制用户访问，让带有多个指纹或其他生物识别访问方法的设备只能向正确的用户显示公司数据。 在 Azure 门户中，打开“Microsoft Intune”。 选择“客户端应用” > “应用保护策略” > “添加策略” > “设置”。 找到特定设置的“访问”部分。

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus 语言包 <!-- 1833450 -->
作为 Intune 管理员，你将能够为通过 Intune 管理的 Office 365 Pro Plus 应用部署其他语言。 可用语言列表包括语言包的“类型”（核心、部分和校对）。 在 Azure 门户中，选择“Microsoft Intune” > “客户端应用” > “应用” > “添加”。 在“添加应用”边栏选项卡的“应用类型”列表中，选择“Office 365 套件”下的“Windows 10”。 在“应用套件设置”边栏选项卡中选择“语言”。

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

<!-- 1805 start -->

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>在冷应用启动和超时时要求非生物识别密码 <!-- 1506985 --> 

在冷应用启动时和管理员指定的超时时长后要求输入非生物识别密码，Intune 会限制使用生物识别来访问公司数据，从而为启用了移动应用程序管理 (MAM) 的应用提升安全性。 这些设置将影响依靠 Touch ID (iOS)、Face ID (iOS)、Android Biometric 或其他未来生物识别身份验证方法访问启用了 APP/MAM 的应用程序的用户。 这些设置将使 Intune 管理员能够更精细地控制用户访问，让带有多个指纹或其他生物识别访问方法的设备只能向正确的用户显示公司数据。 在 Azure 门户中，打开“Microsoft Intune”。 选择“客户端应用” > “应用保护策略” > “添加策略” > “设置”。 找到特定设置的“访问”部分。

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



