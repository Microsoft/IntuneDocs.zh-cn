---
title: 早期版本 - Microsoft Intune
titlesuffix: ''
description: Microsoft Intune 的早期版本
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/3/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 21d89d97355430f071763391d69fe332cf3ef369
ms.sourcegitcommit: 4e69a8664c289263490daa4c02bc6b81c33196e5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2018
ms.locfileid: "53642891"
---
# <a name="the-early-edition-for-microsoft-intune---december-2018"></a>Microsoft Intune 的早期版本 - 2018 年 12 月

> [!Note]
> NDA 通知：下面的更改依据 Intune 开发。 此信息在 NDA 下共享，但具有严格限制。 请勿在 Twitter、UserVoice、Reddit 等社交媒体或公共网站上发布此信息。 

早期版本提供了一份即将发布的 Microsoft Intune 版本中将出现的功能列表（在 NDA 下共享）。 此信息的提供具有条件限制，并且会不断变化。 请勿发布推文、在 UserVoice 上发帖，或者以其他方式在公司外部共享此信息。 此处列出的某些功能有无法按期发布的风险并可能推迟到以后的版本。 正在以试验模式（外部测试）测试其他功能，以确保它们可立即供客户使用。 如果有任何问题或顾虑，请与 Microsoft 产品组联系人联系。

本页将定期更新。 返回查看其他更新。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure 门户中的 Intune

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android Enterprise APP-WE 应用部署 <!-- 1171203 -->
对于没有注册 (APP-WE) 部署方案的未注册应用保护策略中的 Android 设备，能够使用托管的 Google Play 将应用商店应用和 LOB 应用部署到用户。 具体而言，IT 管理员可以向最终用户提供应用目录以及不再需要最终用户通过允许从未知源进行安装来放宽其设备的安全状况的安装体验。 此外，此部署方案将改进最终用户体验。

### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>用于在 Windows 10 及更高版本设备上使用 DNS 设置时自动连接并保留规则的新选项 <!-- 1333665, 2999078 -->
在 Windows 10 及更高版本设备上，你将能够创建包含 DNS 服务器列表的 VPN 配置文件来解析域，如 contoso.com。 这将包括名称解析的新设置（“设备配置” > “配置文件” > “创建配置文件”> 选择“Windows 10 及更高版本”作为平台 > 选择“VPN”作为配置文件类型 >“DNS 设置” >“添加”）： 

- **自动连接**：如果为“已启用”，则当设备与所输入的域（如 contoso.com）通信时，会自动连接到 VPN。
- **永久性**：默认情况下，只要使用此 VPN 配置文件连接设备，所有名称解析策略表 (NRPT) 规则就会处于活动状态。 当 NRPT 规则的此设置为“已启用”时，该规则将在设备上保持活动状态，即使 VPN 断开连接也是如此。 该规则会保持活动状态，直到删除 VPN 配置文件或手动删除该规则，删除操作可以使用 PowerShell 完成。

[Windows 10 VPN 设置](vpn-settings-windows-10.md)介绍了设置的当前列表。 

### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user----1333642-eeready---"></a>使用 S/MIME 对用户的多个设备进行加密和签名 <!-- 1333642 eeready -->
将支持使用新导入的证书配置文件进行 S/MIME 电子邮件加密（“设备配置” > “配置文件” > “创建配置文件”>“选择平台”>“PKCS 导入的证书”配置文件类型）。 在 Intune 中，可以 PFX 格式导入证书。 然后 Intune 可以将这些相同的证书传递给单个用户注册的多个设备。 还包括：

- 本机 iOS 电子邮件配置文件支持使用 PFX 格式的导入证书启用 S/MIME 加密。
- Windows Phone 10 设备上的本机电子邮件应用自动使用 S/MIME 证书。
- 可以跨多个平台传递私有证书。 但并非所有电子邮件应用都支持 S/MIME。
- 在其他平台上，可能需要手动配置电子邮件应用以启用 S/MIME。  
- 支持 S/MIME 加密的电子邮件应用可能以 MDM 不支持的方式（例如从发布者的证书存储读取）处理对 S/MIME 电子邮件加密的证书检索。

在以下设备上受支持：Windows、Windows Phone 10、macOS、iOS、Android

### <a name="help-and-support-page-in-the-windows-company-portal-app----1488939---"></a>Windows 公司门户应用中的帮助和支持页 <!-- 1488939 -->
将向 Windows 公司门户应用添加一个新页。 帮助和支持页将提供支持人员联系信息。 此外，最终用户将能够在出现问题时发送公司门户日志。 此页面还提供“常见问题解答”部分来帮助最终用户。

### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>在 Windows 10 设备上使用 VPN 配置文件的受信任网络检测 <!-- 1500165 -->
使用受信任的网络检测时，能够在用户已使用受信任的网络时阻止 VPN 配置文件自动创建 VPN 连接。 能够添加 DNS 后缀，以便在运行 Windows 10 及更高版本的设备上启用受信任的网络检测（“设备配置” > “配置文件” > “创建配置文件” > “Windows 10 及更高版本”作为平台 >“VPN”作为配置文件类型）。
[Windows 10 VPN 设置](vpn-settings-windows-10.md)列出了当前的 VPN 设置。

### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Intune App SDK 将支持 256 位加密密钥 <!-- 1832174 -->
应用保护策略启用加密时，适用于 Android 的 Intune App SDK 将使用 256 位加密密钥。 SDK 将继续提供 128 位密钥支持以与使用旧版 SDK 的内容和应用兼容。

### <a name="enabled-shared-pc-settings-in-intune-profile----1907917---"></a>在 Intune 配置文件中已启用共享 PC 设置 <!-- 1907917 -->
目前，你可以在使用自定义 OMA-URI 设置的 Windows 10 桌面设备上配置共享 PC 设置。 将添加新的配置文件以配置共享 PC 设置（“设备配置” > “配置文件” > “创建配置文件” > “Windows 10 及更高版本” > “共享多用户设备”）。
适用于：Windows 10 及更高版本、Windows Holographic for Business

### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Intune 策略更新身份验证方法和公司门户应用安装  <!-- 1927359 -->
在已通过 Apple 公司设备注册方法之一经由“设置助理”注册的设备上，Intune 将不再支持由最终用户从应用商店手动安装的公司门户。 仅当在注册过程中使用 Apple 设置助理进行身份验证时，此更改才适用。 此更改也只会影响通过以下方式注册的 iOS 设备：  
* Apple 配置器
* Apple Business Manager
* Apple School Manager
* Apple 设备注册计划 (DEP)

如果用户从应用商店安装公司门户应用，然后尝试通过该应用注册这些设备，则他们将收到错误。 在注册过程中由 Intune 自动推送公司门户时，这些设备应仅使用公司门户。 将更新 Azure 门户中的 Intune 注册配置文件，以便你可以指定设备的身份验证方式以及是否收到公司门户应用。 如果希望 DEP 设备用户具有公司门户，则需要在注册配置文件中指定你的首选项。 此外，公司门户应用中的“标识设备”屏幕很快就会过时。  
若要在已注册的 DEP 设备上安装公司门户，需要转到“Intune”>“客户端应用”，并将其作为具有应用配置策略的托管应用进行推送。 未来的文档中将详细概述执行这些步骤的方式。

### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379---"></a>非管理员可以在已加入 Azure AD 的 Windows 10 设备上启用 BitLocker<!-- 2147379 -->
在 Windows 10 设备上启用 BitLocker 设置时（“设备配置” > “配置文件” > “创建配置文件” > “Windows 10 及更高版本”作为平台 >“Endpoint protection”作为配置文件类型 >“Windows 加密”），将添加 BitLocker 设置。 此更新包括新的 BitLocker 设置，以允许标准用户（非管理员）启用加密。 若要查看当前设置，请参阅[适用于 Windows 10 的 Endpoint protection 设置](endpoint-protection-windows-10.md#windows-encryption)。

### <a name="intune-app-pin----2298397---"></a>Intune 应用 PIN <!-- 2298397 -->
作为 IT 管理员，你将能够配置在最终用户必须更改其 Intune 应用 PIN 之前可以等待的天数。 通过选择“Intune” > “客户端应用” > “应用保护策略” > “创建策略” > “设置” > “访问要求”将在 Azure 门户中提供新设置。 此功能将适用于 iOS 和 Android 设备。 此设置支持正整数值。

### <a name="new-windows-10-update-settings----2626030-2512994---"></a>新的 Windows 10 更新设置 <!-- 2626030 2512994 -->
对于 Windows 10 更新通道，你将能够：
- 在运行“2018 年 10 月更新”的 Windows 10 计算机上还原原始的自动更新设置
- 配置新的软件更新设置，使你能够阻止或允许用户通过其计算机的“设置”暂停更新安装。 



### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>iOS 电子邮件配置文件可以使用 S/MIME 签名和加密 <!-- 2662949 -->
你将能够创建包含不同设置的电子邮件配置文件。 这包括可用于在 iOS 设备上对电子邮件通信进行签名和加密的 S/MIME 设置（“设备配置” > “配置文件” > “创建配置文件”> 选择“iOS”作为平台 >“电子邮件”作为配置文件类型）。

[iOS 电子邮件配置设置](email-settings-ios.md)列出了当前设置。

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509---"></a>在 iOS DEP 设备上跳过更多设置助理屏幕 <!-- 2687509 -->
除了当前可以跳过的屏幕之外，你还能够将 iOS DEP 设备设置为在用户注册设备时跳过设置助理中的以下屏幕：显示色调、隐私、Android 迁移、主页按钮、iMessage 和 FaceTime、载入、监视迁移、外观、屏幕时间、软件更新、SIM 安装程序。
若要选择要跳过的屏幕，请转到“设备注册” > “Apple 注册” > “注册计划令牌”> 选择令牌 >“配置文件”> 选择配置文件 >“属性” > “设置助理的自定义项”> 对于要跳过的任何屏幕选择“隐藏”>“确定”。

### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>某些 BitLocker 设置支持 Windows 10 专业版<!-- 2727036 -->
你将能够创建在 Windows 10 设备上设置 Endpoint Protection 设置的配置文件，包括 BitLocker。 这会为某些 BitLocker 设置添加对 Windows 10 专业版的支持。 若要查看当前 Windows 10 版本设置，请参阅[适用于 Windows 10 的 Endpoint protection 设置](endpoint-protection-windows-10.md#windows-encryption)。


### <a name="intune-device-reporting-fields----2748738---"></a>Intune 设备报告字段 <!-- 2748738 -->
Intune 将提供其他设备报告字段，包括 Android 制造商、模型和安全修补程序版本以及 iOS 型号。 在 Intune 中，将通过选择“客户端应用” > “应用保护状态”并选择“应用保护报告: iOS、Android”来获取这些字段。 此外，这些参数将帮助你配置设备制造商“允许”列表 (Android)、设备型号的“允许”列表（Android 和 iOS）和最低 Android 安全修补程序版本设置。 

### <a name="intune-device-reporting-fields----2748738---"></a>Intune 设备报告字段 <!-- 2748738 -->
Intune 将提供其他设备报告字段，包括 Android 制造商、模型和安全修补程序版本以及 iOS 型号。 在 Intune 中，将通过选择“客户端应用” > “应用保护状态”并选择“应用保护报告: iOS、Android”来获取这些字段。 此外，这些参数将帮助你配置设备制造商“允许”列表 (Android)、设备型号的“允许”列表（Android 和 iOS）和最低 Android 安全修补程序版本设置。 

### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal----2809362---"></a>Azure 门户中的共享设备配置将重命名为适用于 iOS 设备的“锁定屏幕消息”<!-- 2809362 -->
创建适用于 iOS 设备的配置文件时，你将能够添加“共享设备配置”设置以在锁定屏幕上显示特定文本。 这包括以下更改： 

- Azure 门户中的“共享设备配置”设置将重命名为“锁定屏幕消息(仅限受监督的设备)”（“设备配置” > “配置文件” > “创建配置文件”> 选择“iOS”作为平台 > 选择“设备功能”作为配置文件类型 >“锁定屏幕消息”）。
- 添加锁定屏幕消息时，可以插入序列号、设备名称或另一个特定于设备的值作为“资产标记信息”中的变量。 例如，可以使用大括号输入 `Device name: {{device name}}` 或 `Serial number is {{serial number}}`。 [iOS 令牌](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list)列出了可用的令牌。

[用于在锁定屏幕上显示消息的设置](shared-device-settings-ios.md)列出了当前设置。

### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564--"></a>更详细的注册限制失败消息传送 <!-- 3111564-->
不满足注册限制时，将收到更详细的错误消息。 若要查看这些消息，请转到“Intune” > “故障排除”> 并检查“注册故障”表。

### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Android Enterprise 设备所有者设备的新通知、提示和锁屏设置 <!-- 3201839 3201843 -->
以设备所有者身份运行时，此更新包括 Android Enterprise 设备上的多项新功能。 若要使用这些功能，请转到“设备配置” > “配置文件” > “创建配置文件”> 在“平台”中，选择“Android Enterprise” > 在“配置文件类型”中，选择“仅设备所有者” > “设备限制”。
新功能包括： 
- 禁止显示系统通知，包括传入呼叫、系统警报、系统错误等
- 建议跳过首次打开的应用的启动教程和提示
- 禁用高级锁屏设置，例如照相机、通知、指纹解锁等

若要查看当前设置，请转到 [Android Enterprise 设备限制设置](device-restrictions-android-for-work.md)。

### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Android Enterprise 设备所有者设备可以使用 Always On VPN 连接 <!-- 3202194 -->
在此更新中，可以在 Android Enterprise 设备所有者设备上使用始终可用的 VPN 连接。 始终可用 VPN 连接一直保持连接状态，或在用户解锁设备、设备重启或无线网络更改时立即重新连接。 还可以将连接置于“锁定”模式，该模式会阻止所有网络流量，直到 VPN 连接处于活动状态。
可以在“设备配置” > “配置文件” > “创建配置文件” >  适用于平台的“Android 企业版”>“仅设备所有者”的“设备限制”>“连接”设置中启用始终可用的 VPN。 若要查看当前设置，请转到 [Android Enterprise 设备限制设置](device-restrictions-android-for-work.md)。

### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Windows 10 设备上的任务管理器中的结束进程的新设置 <!-- 3285177 --> 
此更新包括使用 Windows 10 设备上的任务管理器的结束进程的新设置。 使用设备配置文件（“设备配置” > “配置文件” > “创建配置文件”> 在“平台”中，选择“Windows 10”> 在“配置文件类型”中，选择“设备限制” > “常规”设置），选择允许或阻止此设置。
若要查看当前设置，请转到 [Windows 10 设备限制设置](device-restrictions-windows-10.md)。
适用于：Windows 10 及更高版本

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>管理模板为公共预览版，并移动到其自己的配置文件 <!-- 3322847 -->
Intune 中的管理模板（“设备配置” > “管理模板”）目前为个人预览版。 借助此更新：管理模板包括可在 Intune 中管理的大约 300 个设置。 以前，这些设置仅存在于组策略编辑器中。
管理模板现已推出公共预览版，管理模板从“设备配置” > “管理模板”移动到“设备配置” > “配置文件” >“创建配置文件”> 在“平台”中，选择“Windows 10 及更高版本”，在“配置文件类型”中，选择“管理模板”。
“已启用报告”适用于：Windows 10 及更高版本


<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>将 Microsoft 推荐的设置与安全基线结合使用 <!-- 2055484 -->
Intune 可与其他专注于安全性的服务集成，包括 Windows Defender ATP 和 Office 365 ATP。 客户要求能在各项 Microsoft 365 服务中采用通用策略和一组统一的端到端安全工作流。 我们的目标是实现策略一致，构建连接安全操作和常见管理员任务的解决方案。 在 Intune 中，我们旨在通过发布一组 Microsoft 推荐的“安全基线”（“Intune” > “安全基线”）来实现这一目标。  管理员将能够直接通过这些基线创建安全策略，然后将其部署到用户。 他们还可以自定义最佳做法建议，满足组织需求。 Intune 可确保设备始终符合这些基线，并通知不符合的用户管理员或设备。

### <a name="scope-tags-for-apps---1081941---"></a>应用的作用域标记 <!--1081941 -->
可创建作用域标记来限制对 Intune 资源的访问。 将作用域标记添加到某个角色分配，然后将作用域标记添加到某个配置文件。 角色将仅有权访问符合后列条件的资源：其资源配置文件的作用域标记与角色标记匹配或无作用域标记。
若要创建作用域标记，选择“Intune 角色” > “作用域(标记)” > “创建”。
要向角色分配添加作用域标记，选择“Intune 角色” > “所有角色” > “策略和配置文件管理器” > “分配” > “作用域(标记)”。
要向配置文件添加作用域标记，选择“设备配置” > “配置文件”>“选择配置文件”>“属性” > “作用域(标记)”。

### <a name="tenant-health-dashboard----1124854---"></a>租户运行状况仪表板 <!-- 1124854 -->
Intune 中的“租户状态”页面将在一个位置提供租户状态信息。 该页面分为 4 个部分：  
- **租户详细信息**：包含 MDM 机构、租户中的注册设备总数以及许可证计数等信息。 此部分还为租户提供当前服务版本。
- **连接器状态**：包含 Apple VPP、适用于企业的 Windows 应用商店和证书连接器等已配置连接器的信息。 根据连接器的当前状态，将其标记为“正常”、“警告”或“不正常”。
- **Intune 服务运行状况**：包含租户的活动事件或服务中断情况。 该部分信息直接检索自 Office 消息中心 ([https://portal.office.com](https://portal.office.com))。
- **Intune 新闻**：包含租户的活动消息，其中包括租户已收到最新 Intune 功能的通知等内容。 该部分信息直接检索自 Office 消息中心 ([https://portal.office.com](https://portal.office.com))。


### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>无需用户注册，即可部署 WIP 政策 <!-- 1434452 -->
无需要求 MDM 用户注册其 Windows 10 设备，即可部署Windows 信息保护 (WIP) 策略。 此配置允许公司基于 WIP 配置保护其企业文档，同时允许用户管理自己的 Windows 设备。 使用 WIP 策略保护文档后，Intune 管理员可以选择性擦除受保护的数据。 通过选择用户和设备，并发送擦除请求，所有通过 WIP 策略保护的数据都将不可用。 从 Azure 门户中的 Intune，选择“移动应用” > “应用选择性擦除”。


<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>适用于 Web 数据的应用保护策略 (APP) 设置 <!-- 2662995 -->
将更新 Android 和 iOS 设备上适用于 Web 内容的应用策略设置，以更好地处理 http 和 https Web 链接，以及通过 iOS 通用链接和 Android 应用链接进行的数据传输。  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>另一个 MDM 使用的 Apple VPP 令牌 <!-- 1488946 -->
Intune 会检测是否 Intune 和另一个 MDM 同时在使用同一个 Apple 批量采购计划 (VPP) 令牌，并显示相关详细信息。

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>“设备符合性仪表板”中的停用设备 <!-- 1981119 -->
未来的某个更新将从设备符合性仪表板中删除已停用的设备。 这会改变符合性数字。


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>本地连接器更新过程的更改 <!-- 2277554 -->
将根据客户反馈更改本地连接器的更新方式。 初次安装本地连接器之后，会自动对其进行更新。 此更改首先应用于适用于 Microsoft Intune 的全新 PFX 证书连接器，随后会推广至其他类型的本地连接器。 

<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>检查 Configuration Manager 符合性<!-- 2192052 -->
未来的更新将包括新的 System Center Configuration Manager 符合性设置（“设备符合性”“策略” >  > “创建策略” > “Windows 10”）。 Configuration Manager 向 Intune 符合性发送信号。 使用 Intune 设置，可以要求所有 Configuration Manager 信号都返回“符合”。

例如，要求所有软件更新都安装在设备上。 在 Configuration Manager 中，此要求具有“已安装”状态。 如果设备上的任何计划都处于未知状态，则此设备在 Intune 中不兼容。

适用于 Windows 10 及更高版本



## <a name="notices"></a>通知

此时没有任何活动通知。

### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。



