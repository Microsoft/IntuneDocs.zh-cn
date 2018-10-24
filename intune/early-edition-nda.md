---
title: 早期版本
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 72585982cd27962981f581a99f0ea361642df0ee
ms.sourcegitcommit: ba0699cc351954960b222223c60c4ecd50edc829
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49652132"
---
# <a name="the-early-edition-for-microsoft-intune---october-2018"></a>Microsoft Intune 的早期版本 - 2018 年 10 月

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

<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>将 Microsoft 推荐的设置与安全基线结合使用 <!-- 2055484 -->
Intune 可与其他专注于安全性的服务集成，包括 Windows Defender ATP 和 Office 365 ATP。 客户要求能在各项 Microsoft 365 服务中采用通用策略和一组统一的端到端安全工作流。 我们的目标是实现策略一致，构建连接安全操作和常见管理员任务的解决方案。 在 Intune 中，我们旨在通过发布一组 Microsoft 推荐的“安全基线”（“Intune” > “安全基线”）来实现这一目标。  管理员将能够直接通过这些基线创建安全策略，然后将其部署到用户。 他们还可以自定义最佳做法建议，满足组织需求。 Intune 可确保设备始终符合这些基线，并通知不符合的用户管理员或设备。

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices----1048100---"></a>加入混合 Azure Active Directory 的设备支持 Autopilot <!-- 1048100 -->
将能使用 Autopilot 对已加入混合 Azure Active Directory 的设备进行设置。 设备必须加入组织网络中，才能使用混合 Autopilot 功能。

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

### <a name="enrollment-abandonment-report----1382924---"></a>注册放弃报告 <!-- 1382924 -->
我们将在“设备注册” > “监视”下发布新报告，其中提供了有关已放弃注册的详细信息。

### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>无需用户注册，即可部署 WIP 政策 <!-- 1434452 -->
无需要求 MDM 用户注册其 Windows 10 设备，即可部署Windows 信息保护 (WIP) 策略。 此配置允许公司基于 WIP 配置保护其企业文档，同时允许用户管理自己的 Windows 设备。 使用 WIP 策略保护文档后，Intune 管理员可以选择性擦除受保护的数据。 通过选择用户和设备，并发送擦除请求，所有通过 WIP 策略保护的数据都将不可用。 从 Azure 门户中的 Intune，选择“移动应用” > “应用选择性擦除”。


### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>为公司门户应用添加自定义品牌图像 <!-- 1916266 -->
作为 Microsoft Intune 管理员，可以上传自定义品牌图像，该图像将在公司门户应用的用户配置文件页面上作为背景图像显示。 有关配置公司门户应用的详细信息，请参阅[如何配置 Microsoft Intune 公司门户应用](company-portal-app.md)。

### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>按交换码 ID 对已注册 Windows Autopilot 的设备进行分组 <!-- 2075110 -->
通过 Configuration Manager [使用 Autopilot 为现有设备注册](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430)时，Intune 将支持按交换码 ID 对 Windows 设备进行分组。 交换码 ID 是 Autopilot 配置文件的参数。 Intune 会自动将 [Azure AD 设备属性 enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects)设置为“OfflineAutopilotprofile - \<交换码 ID\>”。 如此，即可通过离线 Autopilot 注册的 enrollmentprofileName 属性，根据交换码 ID 创建任意 Azure AD 动态组。 


### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>支持 iOS 电子邮件配置文件中的 iOS 12 OAuth <!--2155106 -->
Intune 的 iOS 电子邮件配置文件将支持 iOS 12 OAuth。 要查看此功能，请选择“Intune” > “设备配置” > “配置文件” > “创建配置文件” > “OAuth”。 如果启用此设置，将发生两种情况：
1. 已指定的设备将发布新的配置文件。
2. 系统会再次提示最终用户输入其凭据。

### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>适用于 Android、Android 企业版的新的“所需密码类型”默认设置 <!-- 2649963 -->
创建新的符合性策略时（“Intune” > “设备符合性” > “策略” > “创建策略” > “Android”或“Android 企业版”平台 > 系统安全性），“所需密码类型”的默认值将更改：当前默认值为设备默认；新的默认值为最小数值；应用于：Android、Android 企业版

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522---"></a>将 Autopilot 配置文件分配给所有设备虚拟组 <!--2715522 -->
可将 Autopilot 配置文件分配给所有设备虚拟组。 要执行此操作，请选择“设备注册” > “Windows 注册” > “部署配置文件”，然后选择一个配置文件，选择“分配”，接着在“分配给”下选择“所有设备”。

### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>新的 Azure Active Directory 使用条款功能 <!-- 2870393 -->
Azure Active Directory 将具备可供使用的使用条款功能，而不必再使用现有的 Intune 条款和条件。 Azure AD 使用条款功能在显示哪些条款以及何时显示这些条款方面更加灵活，并能更好地支持本地化，更好地控制条款的呈现方式以及改进报告。 Azure AD 使用条款功能需要 Azure Active Directory Premium P1，后者也是企业移动性 + 安全性 E3 套件的一部分。


### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>在最终用户计算机上更新 Office 时，Intune 将维护维持 Office 本地化语言 <!-- 2971030 -->
Intune 在最终用户计算机上安装 Office 时，最终用户将自动获得与以前安装的 .MSI Office 相同的语言包。 

<!-- 1809 start -->  

### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>iOS MDM 注册设备上的 Intune 应用数据传输设置<!-- 2244713 -->
用户能够将 iOS MDM 注册设备上的 Intune 应用数据传输设置控制与指定注册用户的身份分开。 不使用 IntuneMAMUPN 的管理员不会观察到行为更改。 当此功能可用时，使用 IntuneMAMUPN 控制已注册设备上的数据传输行为的管理员应检查新设置，并根据需要更新其应用设置。

### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>在 Windows 10 Wi-Fi 配置文件中使用预共享密钥<!-- 2662938 -->
用户将能够使用预共享密钥 (PSK) 和 WPA/WPA2-个人安全协议对 Windows 10 的 Wi-Fi 配置的配置文件进行身份验证。
目前，必须导入 Wi-Fi 配置文件，或创建自定义配置文件才能使用预共享密钥。 [Windows 10 的 Wi-Fi 设置](wi-fi-settings-windows.md)列出了当前设置。 

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>适用于 Web 数据的应用保护策略 (APP) 设置 <!-- 2662995 -->
将更新 Android 和 iOS 设备上适用于 Web 内容的应用策略设置，以更好地处理 http 和 https Web 链接，以及通过 iOS 通用链接和 Android 应用链接进行的数据传输。  

### <a name="autopilot-device-sync-frequency-increasing-to-every-12-hours----2753673---"></a>Autopilot 设备同步频率增加到每隔 12 小时<!-- 2753673 -->
Autopilot 设备将每 12 小时同步一次，而不是每 24 小时同步一次。

### <a name="intune-landing-page-updates-and-node-rename---2867309---"></a>Intune 登录页更新和节点重命名<!--2867309 -->
对 Intune 登录页的更新将包括新的和更改的监视磁贴和图表，以便更好地进行数据可视化处理。 “移动应用”节点将变为“客户端应用”。

### <a name="increased-end-user-access-using-the-company-portal-app----772203---"></a>借助公司门户应用提升了最终用户的访问权限<!-- 772203 -->
最终用户将能够从公司门户应用访问密钥帐户操作，例如密码重置和他们的 AAD 配置文件。  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>另一个 MDM 使用的 Apple VPP 令牌 <!-- 1488946 -->
Intune 会检测是否 Intune 和另一个 MDM 同时在使用同一个 Apple 批量采购计划 (VPP) 令牌，并显示相关详细信息。

### <a name="ios-version-number-and-build-number-are-shown----1892471---"></a>显示 iOS 版本号和生成号 <!-- 1892471 -->
在“设备符合性” > “设备符合性”中，会显示 iOS 操作系统版本。 在未来的某个更新中，会显示生成号。
Apple 每次发布安全更新时，会保留版本号，更新生成号。 通过所显示的生成号，可轻松确认是否已安装漏洞更新。

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>“设备符合性仪表板”中的停用设备 <!-- 1981119 -->
未来的某个更新将从设备符合性仪表板中删除已停用的设备。 这会改变符合性数字。


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>本地连接器更新过程的更改 <!-- 2277554 -->
将根据客户反馈更改本地连接器的更新方式。 初次安装本地连接器之后，会自动对其进行更新。 此更改首先应用于适用于 Microsoft Intune 的全新 PFX 证书连接器，随后会推广至其他类型的本地连接器。 

<!-- 1807 start -->

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>针对设备注册管理员用户，改进了公司门户应用体验 <!-- 675800 -->
当设备注册管理员 (DEM) 登录到适用于 Windows 的公司门户应用时，该应用将仅列出 DEM 的当前正在运行的设备。 此改进将减少以前应用尝试加载所有 DEM 注册设备时出现的超时。  

### <a name="check-for-configuration-manager-compliance----2192052---"></a>检查 Configuration Manager 符合性<!-- 2192052 -->
未来的更新将包括新的 System Center Configuration Manager 符合性设置（“设备符合性”“策略” >  > “创建策略” > “Windows 10”）。 Configuration Manager 向 Intune 符合性发送信号。 使用 Intune 设置，可以要求所有 Configuration Manager 信号都返回“符合”。

例如，要求所有软件更新都安装在设备上。 在 Configuration Manager 中，此要求具有“已安装”状态。 如果设备上的任何计划都处于未知状态，则此设备在 Intune 中不兼容。

适用于 Windows 10 及更高版本

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>针对即将过期的 VPP 令牌或公司门户许可证不足的警报 <!-- 2237572 -->
如果在 DEP 注册期间使用批量采购计划 (VPP) 预先设置公司门户，则在 VPP 令牌即将过期以及公司门户的许可证不足的情况下，Intune 将发出警报。

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>可通过 iOS 上的 APP 设置阻止第三方键盘 <!-- 1248481 -->
在 iOS 设备上，Intune 管理员可以阻止使用第三方键盘在受策略保护的应用中访问组织数据。 当应用程序保护策略 (APP) 设置为阻止第三方键盘时，设备用户将在首次使用第三方键盘与公司数据交互时收到一条消息。 将阻止本地键盘以外的所有选项都，设备用户不会看到它们。 设备用户只会看到一次对话消息。 

<!-- 1805 start -->

### <a name="require-non-biometric-after-specified-timeout----1506985---"></a>在指定的超时时长后需要非生物识别<!-- 1506985 --> 

在管理员指定的超时时长后要求输入非生物识别 PIN，Intune 会限制使用生物识别来访问公司数据，从而为启用了移动应用程序管理 (MAM) 的应用提升安全性。 这些设置将影响依靠 Touch ID (iOS)、Face ID (iOS)、Android Biometric 或其他未来生物识别身份验证方法访问启用了 APP/MAM 的应用程序的用户。 这些设置将使 Intune 管理员能够更精细地控制用户访问，让带有多个指纹或其他生物识别访问方法的设备只能向正确的用户显示公司数据。 在 Azure 门户中，打开“Microsoft Intune”。 选择“移动应用” > “应用保护策略” > “添加策略” > “设置”。 找到特定设置的“访问”部分。

<!-- 1803 start -->

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>更新适用于 Android 的公司门户应用上的“帮助和反馈”体验 <!--1631531 -->

将更新适用于 Android 的公司门户应用上的“帮助和反馈”体验以符合 Android 应用的最佳做法。 在未来的几个月里将更新适用于 Android 的公司门户应用，将“帮助和反馈”菜单项分为不同的“帮助”和“发送反馈”菜单项。 “帮助”页面将包含“常见问题”部分和“电子邮件支持”按钮，引导最终用户向 Microsoft 上传日志并向公司支持部门发送电子邮件以描述问题。 “发送反馈”将引导用户完成标准的 Microsoft 反馈提交，这将提示用户选择“我喜欢一些内容”、“我不喜欢一些内容”还是“我有个主意”。



<!-- the following are present prior to 1711 -->

## <a name="notices"></a>通知

此时没有任何活动通知。

### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。



