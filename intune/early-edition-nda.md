---
title: 早期版本
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0f6447f4a5cfb2638278a59414e83f744adb8c81
ms.sourcegitcommit: ed97b68f08c1a8469f0b45bc1c839a0b5f5c71e0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "45978257"
---
# <a name="the-early-edition-for-microsoft-intune---september-2018"></a>Microsoft Intune 的早期版本 - 2018 年 9 月

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

<!-- 1809 start -->

### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices-----1248496----"></a>托管的 Android 和 iOS 设备上的 Intune 应用的用户帐户访问权限<!-- ! 1248496  -->

作为 Microsoft Intune 管理员，可以控制将哪些用户帐户添加到托管设备上的 Microsoft Office 应用程序。 能够限制仅允许组织用户帐户的访问权限，并阻止已注册设备上的个人帐户。 

### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10----1333668---"></a>在运行 Windows 10 的设备上的 VPN 配置配置文件中创建 DNS 后缀<!-- 1333668 -->
在创建 VPN 设备配置的配置文件（“设备配置” > “配置文件” > “创建配置文件” > “Windows 10 及更高版本”平台>“VPN”配置文件类型）时，需要输入一些 DNS 设置。 还可以在 Intune 中输入多个 DNS 后缀。 使用 DNS 后缀时，可以使用其短名称而不是完全限定的域名 (FQDN) 搜索网络资源。 此更新还允许在 Intune 中更改 DNS 后缀的顺序。
[Windows 10 VPN 设置](vpn-settings-windows-10.md#dns-settings)列出了当前的 DNS 设置。
适用于：Windows 10 设备

### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>支持 Android 企业工作配置文件的始终可用 VPN<!-- 1333705 -->
用户将能够在具有托管工作配置文件的 Android 企业设备上使用始终可用 VPN 连接。 始终可用 VPN 连接一直保持连接状态，或在用户解锁设备、设备重启或无线网络更改时立即重新连接。 还可以将连接置于“锁定”模式，该模式会阻止所有网络流量，直到 VPN 连接处于活动状态。
始终可用 VPN 设置位于“设备配置” > “配置文件” > “创建配置文件” > “Android Enterprise”平台>“配置文件类型”的“仅工作配置文件”下的“设备限制”>“连接”设置中。 

### <a name="outlook-for-ios-and-android-app-configuration-policy---1828527---"></a>Outlook for iOS 和 Outlook for Android 应用配置策略<!--1828527 -->
可以为 iOS 创建 Outlook for iOS 和 Outlook for Android 应用配置策略。 将为 Outlook for iOS 和 Outlook for Android 启用和添加其他配置设置。

###  <a name="windows-line-of-business-lob-app-file-extensions----1884873---"></a>Windows 业务线 (LOB) 应用文件扩展名 <!-- 1884873 -->
Windows LOB 应用的文件扩展名包括 .msi、appx、appxbundle、.msix 和 .msixbundle。 可以在 Microsoft Intune 中添加应用，方法是通过选择“客户端应用” > “应用” > “添加”。 将显示可以选择“应用类型”的“添加应用”窗格。 对于 Windows LOB 应用，选择“业务线”应用作为应用类型，选择“应用包文件”，然后输入带有相应扩展名的安装文件。

### <a name="remotely-lock-noncompliant-devices----2064495---"></a>远程锁定不符合要求的设备<!-- 2064495 -->
如果设备不符合要求，将能够根据符合性策略创建一个可远程锁定设备的操作。 在 Intune 中，转到“设备符合性”，创建新的策略，或选择现有策略。 选择“针对非符合性的操作” > “添加”，然后选择远程锁定设备。
在以下设备上受支持： 
- Android
- iOS
- macOS
- Windows 10 移动版 
- Windows Phone 8.1 及更高版本 

### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>iOS MDM 注册设备上的 Intune 应用数据传输设置<!-- 2244713 -->
用户能够将 iOS MDM 注册设备上的 Intune 应用数据传输设置控制与指定注册用户的身份分开。 不使用 IntuneMAMUPN 的管理员不会观察到行为更改。 当此功能可用时，使用 IntuneMAMUPN 控制已注册设备上的数据传输行为的管理员应检查新设置，并根据需要更新其应用设置。

### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>在 Windows 10 Wi-Fi 配置文件中使用预共享密钥<!-- 2662938 -->
用户将能够使用预共享密钥 (PSK) 和 WPA/WPA2-个人安全协议对 Windows 10 的 Wi-Fi 配置的配置文件进行身份验证。
目前，必须导入 Wi-Fi 配置文件，或创建自定义配置文件才能使用预共享密钥。 [Windows 10 的 Wi-Fi 设置](wi-fi-settings-windows.md)列出了当前设置。 

### <a name="app-protection-policy-app-settings-for-web-data----2662995-eeready---"></a>适用于 Web 数据的应用保护策略 (APP) 设置 <!-- 2662995 eeready -->
将更新 Android 和 iOS 设备上适用于 Web 内容的应用策略设置，以更好地处理 http 和 https Web 链接，以及通过 iOS 通用链接和 Android 应用链接进行的数据传输。  

### <a name="autopilot-device-sync-frequency-increasing-to-every-12-hours----2753673---"></a>Autopilot 设备同步频率增加到每隔 12 小时<!-- 2753673 -->
Autopilot 设备将每 12 小时同步一次，而不是每 24 小时同步一次。

### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>将 Autopilot 配置文件应用到尚未注册 Autopilot 的已注册 Win 10 设备<!-- 1558983 -->
可以将 Autopilot 配置文件应用到尚未注册 Autopilot 的已注册 Win 10 设备。 在 Autopilot 配置文件中，选择“将所有目标设备转换为 Autopilot”选项，以使用 Autopilot 部署服务自动注册非 Autopilot 设备。 等待 48 小时来处理注册。 取消注册设备并重置后，Autopilot 将对其进行配置。 

### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564--"></a>创建多个注册状态页配置文件并将其分配给 Azure AD 组<!-- 2526564-->
用户将能够创建多个注册状态页配置文件并将其分配给 Azure AAD 用户组。

### <a name="intune-landing-page-updates-and-node-rename---2867309---"></a>Intune 登录页更新和节点重命名<!--2867309 -->
对 Intune 登录页的更新将包括新的和更改的监视磁贴和图表，以便更好地进行数据可视化处理。 “移动应用”节点将变为“客户端应用”。

### <a name="increased-end-user-access-using-the-company-portal-app----772203---"></a>增加了最终用户使用公司门户应用的访问权限<!-- 772203 -->
最终用户将能够从公司门户应用访问密钥帐户操作，例如密码重置和他们的 AAD 配置文件。

### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>向无用户设备颁发 SCEP 证书<!-- 1744554 -->
目前证书的颁发对象是用户。 用户将能够向设备（包括无用户设备，如网亭）颁发 SCEP 证书（“设备配置” > “配置文件” > “创建配置文件” > “Windows 10 及更高版本”平台>“配置文件”的“SCEP 证书”）。 其他更新将包括：
- SCEP 配置文件中的“使用者”属性现在是自定义文本框，可以包含新的变量。 
- SCEP 配置文件中的“使用者可选名称(SAN)”属性现在是表格式，可以包含新的变量。 在表中，管理员可以添加属性并在自定义文本框中填写值。 SAN 将支持以下属性： 
  - DNS
  - 电子邮件地址
  - UPN 可以在自定义值文本框中使用静态文本添加这些新变量。 例如，可以将 DNS 属性添加为 `DNS = {{AzureADDeviceId}}.domain.com`。
  > [!NOTE]
  > 在 SAN 的静态文本中无法使用大括号 ({ })、分号 (;) 和竖杠符号 (|)。 `Subject` 或 `Subject alternative name` 只接受大括号仅包含一个新设备证书变量的情况。 新的设备证书变量：  
```
"{{AAD_Device_ID}}",
"{{Device_Serial}}",
"{{Device_IMEI}}",
"{{SerialNumber}}",
"{{IMEINumber}}",
"{{AzureADDeviceId}}",
"{{WiFiMacAddress}}",
"{{IMEI}}",
"{{DeviceName}}",
"{{FullyQualifiedDomainName}}",
"{{MEID}}",
```

> [!NOTE]
>  - `{{FullyQualifiedDomainName}}` 仅适用于 Windows 和已加入域的设备。 
>  -  在使用者或 SAN 中为设备证书指定设备属性（如 IMEI、序列号和完全限定的域名）时，请注意这些属性可能被有权访问设备的人员模仿。 

[创建 SCEP 证书配置文件](certificates-scep-configure.md#create-a-scep-certificate-profile)列出了创建 SCEP 配置的配置文件时的当前变量。 

适用于：Windows 10 及更高版本和 iOS，支持用于 Wi-fi



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

### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224-eeready---"></a>Azure 门户中的 Windows 10 和更高版本的网亭配置文件改进<!-- 2748224 eeready -->
Windows 10 网亭设备配置文件（“设备配置” > “配置文件” > “创建配置文件” > “Windows 10 及更高版本”平台>“配置文件类型”的“网亭预览”）将得到改进： 
- 目前，用户可以在同一设备上创建多个网亭配置文件。 利用此更新，Intune 将支持每台设备只有一个网亭配置文件。 如果你仍需要在单台设备上创建多个网亭配置文件，可以使用自定义 URI。
-在“多应用网亭”配置文件中，可以在应用程序网格中对“开始菜单布局”选择应用程序磁贴大小和顺序。 如果需要更多自定义设置，可以继续上传 XML 文件。
- 网亭浏览器设置移入“网亭”设置。 目前，“网亭 Web 浏览器”设置在 Azure 门户中具有其自己的类别。
适用于：Windows 10 及更高版本

<!-- 1807 start -->

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>针对设备注册管理员用户，改进了公司门户应用体验 <!-- 675800 -->
当设备注册管理员 (DEM) 登录到适用于 Windows 的公司门户应用时，该应用将仅列出 DEM 的当前正在运行的设备。 此改进将减少以前应用尝试加载所有 DEM 注册设备时出现的超时。  

### <a name="check-for-configuration-manager-compliance----2192052---"></a>检查 Configuration Manager 符合性<!-- 2192052 -->
未来的更新将包括新的 System Center Configuration Manager 符合性设置（“设备符合性”“策略” >  > “创建策略” > “Windows 10”）。 Configuration Manager 向 Intune 符合性发送信号。 使用 Intune 设置，可以要求所有 Configuration Manager 信号都返回“符合”。

例如，要求所有软件更新都安装在设备上。 在 Configuration Manager 中，此要求具有“已安装”状态。 如果设备上的任何计划都处于未知状态，则此设备在 Intune 中不兼容。

适用于 Windows 10 及更高版本

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>针对即将过期的 VPP 令牌或公司门户许可证不足的警报 <!-- 2237572 -->
如果在 DEP 注册期间使用批量采购计划 (VPP) 预先设置公司门户，则在 VPP 令牌即将过期以及公司门户的许可证不足的情况下，Intune 将发出警报。

### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Windows Installer 的其他安全设置 <!-- 2282430 -->
可允许用户控制应用安装。 如果启用，则允许因安全冲突而停止的安装继续进行。 当 Windows Installer 在系统上安装任何程序时，可指示它使用提升的权限。 此外，将能够对 Windows 信息保护 (WIP) 项目编制索引，并将有关这些项目的元数据存储在未加密的位置。 禁用策略后，将不会对受 WIP 保护的项编制索引，也不会在 Cortana 或文件资源管理器的结果中显示这些项。 默认情况下将禁用这些选项的功能。 

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>可通过 iOS 上的 APP 设置阻止第三方键盘 <!-- 1248481 -->
在 iOS 设备上，Intune 管理员可以阻止使用第三方键盘在受策略保护的应用中访问组织数据。 当应用程序保护策略 (APP) 设置为阻止第三方键盘时，设备用户将在首次使用第三方键盘与公司数据交互时收到一条消息。 将阻止本地键盘以外的所有选项都，设备用户不会看到它们。 设备用户只会看到一次对话消息。 

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus 语言包 <!-- 1833450 -->
作为 Intune 管理员，将能够为通过 Intune 管理的 Office 365 Pro Plus 应用部署其他语言。 可用语言列表包括语言包的“类型”（核心、部分和校对）。 在 Azure 门户中，选择“Microsoft Intune” > “移动应用” > “应用” > “添加”。 在“添加应用”边栏选项卡的“应用类型”列表中，选择“Office 365 套件”下的“Windows 10”。 在“应用套件设置”边栏选项卡中选择“语言”。

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



