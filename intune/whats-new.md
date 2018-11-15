---
title: Microsoft Intune 中的新增功能 - Azure | Microsoft Docs
titlesuffix: ''
description: 了解 Intune Azure 门户新增功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/09/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: 1180e085c0584f3da535947cad60c41d06a8026a
ms.sourcegitcommit: d8edd1c3d24123762dd6d14776836df4ff2a31dd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2018
ms.locfileid: "51576964"
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune 新增功能
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

了解 Microsoft Intune 每周新增功能。 此外，还可找到即将发生的更改、[重要说明](#notices)以及有关[过去版本](whats-new-archive.md)的信息。 某些功能可能会在数周内推出，第一周内可能不能供所有客户使用。

> [!Note]
> 有关混合移动设备管理 (MDM) 中新功能的信息，请参阅[混合新增功能页面](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。


<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->     
## <a name="week-of-november-5-2018"></a>2018 年 11 月 5 日当周

### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>支持 iOS 电子邮件配置文件中的 iOS 12 OAuth <!--2155106 -->

Intune 的 iOS 电子邮件配置文件支持 iOS 12 Open Authorization (OAuth)。 要查看此功能，请创建新配置文件（“设备配置” > “配置文件” > “创建配置文件” >  iOS 平台 >“电子邮件”配置文件类型），或更新现有的 iOS 电子邮件配置文件。 如果在已部署到用户的配置文件中启用 OAuth，则会提示用户重新进行身份验证，然后再次下载其电子邮件。

[iOS 电子邮件配置文件](email-settings-ios.md)提供了有关在电子邮件配置文件中使用 OAuth 的详细信息。

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview----1048100--"></a>已加入混合 Azure Active Directory 的设备支持 Autopilot（预览）<!-- 1048100-->
现在可以使用 Autopilot 对已加入混合 Azure Active Directory 的设备进行设置。 设备必须加入组织网络中，才能使用混合 Autopilot 功能。 有关详细信息，请参阅[使用 Intune 和 Windows Autopilot 部署已加入混合 Azure AD 的设备](windows-autopilot-hybrid.md)。
此功能将在未来几天内在整个用户群中推出。 因此，在推送到你的帐户之前，你可能无法执行这些步骤。

### <a name="app-protection-policy-app-settings-for-web-data----2662995----"></a>适用于 Web 数据的应用保护策略 (APP) 设置 <!-- 2662995  -->
已更新 Android 和 iOS 设备上适用于 Web 内容的应用策略设置，能更好地处理 http 和 https Web 链接，以及通过 iOS 通用链接和 Android 应用链接进行的数据传输。  

## <a name="week-of-october-29-2018"></a>2018 年 10 月 29 日当周


### <a name="app-management"></a>应用管理

#### <a name="require-non-biometric-pin-after-a-specified-timeout----1506985---"></a>在指定的超时后需要非生物识别 PIN <!-- 1506985 -->
在管理员指定的超时时长后要求输入非生物识别 PIN，Intune 会限制使用生物识别来访问公司数据，从而为启用了移动应用管理 (MAM) 的应用提升安全性。 这些设置会影响依靠 Touch ID (iOS)、Face ID (iOS)、Android Biometric 或其他未来生物识别身份验证方法访问启用了 APP/MAM 的应用程序的用户。 这些设置会使 Intune 管理员能够更精细地控制用户访问，让带有多个指纹或其他生物识别访问方法的设备只能向正确的用户显示公司数据。 在 Azure 门户中，打开“Microsoft Intune”。 选择“客户端应用” > “应用保护策略” > “添加策略” > “设置”。 找到特定设置的“访问”部分。 有关访问设置的信息，请参阅 [iOS 设置](app-protection-policy-settings-ios.md#access-settings)和 [Android 设置](app-protection-policy-settings-android.md#access-settings)。

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>iOS MDM 注册设备上的 Intune 应用数据传输设置<!-- 2244713 -->
可以将 iOS MDM 注册设备上的 Intune 应用数据传输设置控制与指定注册用户的身份（也称为用户主体名称 (UPN)）分开。 不使用 IntuneMAMUPN 的管理员不会观察到行为更改。 当此功能可用时，使用 IntuneMAMUPN 控制已注册设备上的数据传输行为的管理员应检查新设置，并根据需要更新其应用设置。

#### <a name="windows-10-win32-apps----2617325---"></a>Windows 10 Win32 应用 <!-- 2617325 -->
可以将 Win32 应用配置为在单个用户的用户上下文中安装，而不是为该设备的所有用户安装应用。

#### <a name="windows-win32-apps-and-powershell-scripts----2617330---"></a>Windows Win32 应用和 PowerShell 脚本 <!-- 2617330 -->
最终用户无需登录设备即可安装 Win32 应用或执行 PowerShell 脚本。 

#### <a name="troubleshooting-client-app-installation----1363711---"></a>客户端应用安装疑难解答 <!-- 1363711 -->
可以通过查看“故障排除”边栏选项卡中标有“应用安装”的列来解决客户端应用的安装问题。 要查看“故障排除”边栏选项卡，请在 Intune 门户中，选择“故障排除”下的“帮助和支持”。

### <a name="device-configuration"></a>设备配置

#### <a name="network-access-control-support-on-ios-vpn-clients----1333693-wnready---"></a>iOS VPN 客户端上的网络访问控制支持 <!-- 1333693 wnready -->
通过此更新，可以在为 Cisco AnyConnect、F5 Access 和 Citrix SSO for iOS 创建 VPN 配置文件时启用网络访问控制 (NAC)。 此设置允许将设备的 NAC ID 包含在 VPN 配置文件中。 目前，没有任何支持此新 NAC ID 的 VPN 客户端或 NAC 合作伙伴解决方案，但我们将通过[支持博客文章](ttps://aka.ms/iOS12_and_vpn)发送通知。

要使用 NAC，需要：
1. 选择加入以允许 Intune 在 VPN 配置文件中包含设备 ID
2. 使用直接来自 NAC 提供程序的指导更新 NAC 提供程序软件/固件

有关 iOS VPN 配置文件中此设置的信息，请参阅[在 Microsoft Intune 的 iOS 设备上添加 VPN 设置](vpn-settings-ios.md)。 有关网络访问控制的详细信息，请参阅[网络访问控制 (NAC) 与 Intune 集成](network-access-control-integrate.md)。 

适用于：iOS

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile----1818139---"></a>即使只有一个电子邮件配置文件，也可从设备删除电子邮件配置文件 <!-- 1818139 -->
以前，如果只有唯一一个电子邮件配置文件，则无法从设备删除该电子邮件配置文件。 有了此更新，该行为发生了变化。 现在，即使设备上只有唯一一个电子邮件配置文件，也可删除该电子邮件配置文件。 有关详细信息，请参阅[使用 Intune 向设备添加电子邮件设置](email-settings-configure.md)。

#### <a name="powershell-scripts-and-aad----2309469---"></a>PowerShell 脚本和 AAD <!-- 2309469 -->
Intune 中的 PowerShell 脚本可应用于 AAD 设备安全组。

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>适用于 Android、Android 企业版的新的“所需密码类型”默认设置 <!-- 2649963 -->
创建新的符合性策略时（“Intune” > “设备符合性” > “策略” > “创建策略” > > Android 或 Android Enterprise 平台 >“系统安全性”），所需密码类型的默认值会更改：

从“设备默认值”更改为“至少为数字”

适用对象：Android、Android Enterprise

要查看这些设置，请转到 [Android](compliance-policy-create-android.md) 和 [Android Enterprise](compliance-policy-create-android-for-work.md)。

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>在 Windows 10 Wi-Fi 配置文件中使用预共享密钥<!-- 2662938 -->
通过本次更新，用户能够使用预共享密钥 (PSK) 和 WPA/WPA2 个人安全协议对 Windows 10 的 Wi-Fi 配置的配置文件进行身份验证。 还可以在 Windows 10 的 2018 年 10 月更新中为设备指定按流量计费的网络的成本配置。

目前，必须导入 Wi-Fi 配置文件，或创建自定义配置文件才能使用预共享密钥。 [Windows 10 的 Wi-Fi 设置](wi-fi-settings-windows.md)列出了当前设置。 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices----3218390---"></a>从设备删除 PKCS 和 SCEP 证书 <!-- 3218390 -->
在某些情况下，即使从组中删除策略，删除配置或合规性部署，或是由管理员更新现有 SCEP 或 PKCS 配置文件，PKCS 和 SCEP 证书仍会存留在设备上。 此更新改变了这种情况。 在某些情况下，PKCS 和 SCEP 证书会从设备中删除，而在其他一些情况下，这些证书会存留在设备上。 请参阅[在 Microsoft Intune 中删除 SCEP 和 PKCS 证书](remove-certificates.md)了解这些情况。

#### <a name="use-gatekeeper-on-macos-devices-for-compliance----2504381---"></a>在 macOS 设备上使用网关守卫实现符合性 <!-- 2504381 -->
此更新包括 macOS 网关守卫，用于评估设备的符合性。 要设置网关守卫属性，请[为 macOS 设备添加设备符合性策略](compliance-policy-create-mac-os.md)。


### <a name="device-enrollment"></a>设备注册

#### <a name="enrollment-abandonment-report----1382924---"></a>注册放弃报告 <!-- 1382924 -->
我们在“设备注册” > “监视”下发布了新报表，其中提供了有关已放弃注册的详细信息。 有关详细信息，请参阅[公司门户放弃报表](enrollment-report-company-portal-abandon.md)。

#### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522---"></a>将 Autopilot 配置文件分配给所有设备虚拟组 <!--2715522 -->
可将 Autopilot 配置文件分配给所有设备虚拟组。 要执行此操作，请选择“设备注册” > “Windows 注册” > “部署配置文件”，然后选择一个配置文件，选择“分配”，接着在“分配给”下选择“所有设备”。 有关 Autopilot 配置文件的详细信息，请参阅[使用 Windows Autopilot 注册 Windows 设备](enrollment-autopilot.md)。

#### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>新的 Azure Active Directory 使用条款功能 <!-- 2870393 -->
Azure Active Directory 具备可供使用的使用条款功能，而不必再使用现有的 Intune 条款和条件。 Azure AD 使用条款功能在显示哪些条款以及何时显示这些条款方面更加灵活，并能更好地支持本地化，更好地控制条款的呈现方式以及改进报告。 Azure AD 使用条款功能需要 Azure Active Directory Premium P1，后者也是企业移动性 + 安全性 E3 套件的一部分。 要了解详情，请参阅[管理公司的用户访问条款和条件](terms-and-conditions-create.md)一文。

### <a name="android-device-owner-mode-support---3188762--"></a>Android 设备所有者模式支持 <!--3188762-->
对于 Samsung Knox 移动注册，Intune 现在支持将设备注册到 Android 设备所有者管理模式。 使用 WiFi 或移动电话网络的用户在第一次打开他们的设备时，只需几次点击即可进行注册。 有关详细信息，请参阅[使用 Samsung 的 Knox 移动注册自动注册 Android 设备](android-samsung-knox-mobile-enroll.md)。

### <a name="device-management"></a>设备管理

### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>按交换码 ID 对已注册 Windows Autopilot 的设备进行分组 <!-- 2075110 -->
通过 Configuration Manager [使用 Autopilot 为现有设备注册](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430)时，Intune 现已支持按交换码 ID 对 Windows 设备进行分组。 交换码 ID 是 Autopilot 配置文件的参数。 Intune 会自动将 [Azure AD 设备属性 enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) 设置为“OfflineAutopilotprofile - <correlator ID>”。 如此，即可通过离线 Autopilot 注册的 enrollmentprofileName 属性，根据交换码 ID 创建任意 Azure AD 动态组。 有关详细信息，请参阅[现有设备的 Windows Autopilot](enrollment-autopilot.md#windows-autopilot-for-existing-devices)。

### <a name="intune-app-protection-policies----2984657---"></a>Intune 应用保护策略 <!-- 2984657 -->
可使用 Intune 应用保护策略为受 Intune 保护的应用（如 Microsoft Outlook 和 Microsoft Word）配置各种数据保护设置。 我们为 [iOS](app-protection-policy-settings-ios.md) 和 [Android](app-protection-policy-settings-android.md) 更改了这些设置的外观，以便更轻松地查找单个设置。 策略设置分为三类：
- **数据重定位** - 此组包含数据丢失防护 (DLP) 控件，如剪切、复制、粘贴和另存为限制。 这些设置决定了用户与应用中的数据的交互方式。
- **访问要求** - 该组包含每个应用的 PIN 选项，用于确定最终用户在工作环境中访问应用的方式。  
- **条件启动** - 该组包含最低操作系统设置、已越狱和取得 Root 权限的设备检测以及脱机宽限期等设置。  
  
设置的功能不会更改，但在处理策略创作流程时会更容易找到它们。

### <a name="new-intune-device-subscription-sku---3312071--"></a>新的 Intune 设备订阅 SKU！--3312071-->
为了帮助降低企业中管理设备的成本，现在已提供基于设备的新订阅 SKU。 此 Intune 设备 SKU 按月按设备获取许可。 价格因许可计划而异。 可通过直接渠道、企业协议 (EA)、Microsoft 产品和服务计划 (MPSA) 以及开放和云解决方案提供商 (CSP) 获取。

### <a name="intune-apps"></a>Intune 应用

#### <a name="intune-will-support-a-maximum-package-size-of-8-gb-for-lob-apps----1727158---"></a>对于 LOB 应用，Intune 将支持最大为 8 GB 的包大小 <!-- 1727158 -->
Intune 将业务线 (LOB) 应用的最大包大小增加到 8 GB。 有关详细信息，请参阅[将应用添加到 Microsoft Intune](apps-add.md)。

#### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>为公司门户应用添加自定义品牌图像 <!-- 1916266 -->
Microsoft Intune 管理员可以上传自定义品牌图像，该图像将在 iOS 公司门户应用的用户配置文件页面上作为背景图像显示。 有关配置公司门户应用的详细信息，请参阅[如何配置 Microsoft Intune 公司门户应用](company-portal-app.md)。

#### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>在最终用户计算机上更新 Office 时，Intune 将维护维持 Office 本地化语言 <!-- 2971030 -->
Intune 在最终用户计算机上安装 Office 时，最终用户将自动获得与以前安装的 .MSI Office 相同的语言包。 有关详细信息，请参阅[使用 Microsoft Intune 将 Office 365 应用分配到 Windows 10 设备](apps-add-office365.md)。

### <a name="monitor-and-troubleshoot"></a>监视和故障排除

#### <a name="new-intune-support-experience-in-the-microsoft-365-device-management-portal----3076965---"></a>Microsoft 365 设备管理门户中的新 Intune 支持体验 <!-- 3076965 -->
我们正在 [Microsoft 365 设备管理门户]( http://devicemanagement.microsoft.com)中推出适用于 Intune 的新的“帮助和支持”体验。 通过新体验，可以用自己的语言描述问题，并获得故障排除见解和基于 Web 的修复内容。 这些解决方案通过基于规则的机器学习算法提供并依赖于用户查询。  

除特定于问题的指南之外，还可以使用新的案例创建工作流通过电子邮件或电话打开支持案例。  

对于参与部署的客户，此新体验取代了一组静态预选选项的当前“帮助和支持”体验，这些选项基于打开“帮助和支持”时所在控制台的区域。  

我们正在向部分租户（不是所有租户）推出此新的“帮助和支持”体验，你可在“设备管理”门户中进行找到。此新体验的参与者是在可用的 Intune 租户中随机选择的。在我们扩大推出时，将添加新租户。  

有关详细信息，请参阅“如何获取对 Microsoft Intune 的支持”中的[新的“帮助和支持”体验](get-support.md#new-help-and-support-experience)。  

### <a name="powershell-module-for-intune--preview-available----wnready-951068---"></a>适用于 Intune 的 PowerShell 模块 - 提供预览版 <!-- wnready 951068 -->
现在，[GitHub]( https://aka.ms/intunepowershell) 上提供了新 PowerShell 模块的预览版，该模块可通过 Microsoft Graph 提供对 Intune API 的支持。 有关如何使用此模块的详细信息，请参阅该处的自述文件。 


## <a name="week-of-october-15-2018"></a>2018 年 10 月 15 日当周

### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device-----2637704----"></a>在 iOS 设备上更改指纹或 Face ID 时，会提示输入 PIN <!-- 2637704  -->
在 iOS 设备上进行生物识别更改后，现在会提示用户输入 PIN。 这包括对已注册的指纹或 Face ID 的更改。 出现提示的时间取决于如何配置“以下时间(以分钟为单位)之后重新检查访问要求”超时。  未设置 PIN 时，会提示用户设置一个 PIN。 
 
此功能仅适用于 iOS，并且需要集成了 Intune APP SDK for iOS 版本 9.0.1 或更高版本的应用程序参与。 必须集成 SDK，以便可以在目标应用程序上强制执行行为。 此集成陆续进行，取决于特定应用程序团队。 参与的一些应用包括 WXP、Outlook、Managed Browser 和 Yammer。


## <a name="week-of-october-1-2018"></a>2018 年 10 月 1 日当周

### <a name="app-management"></a>应用管理

#### <a name="access-to-key-profile-properties-using-the-company-portal-app----772203---"></a>使用公司门户应用访问关键配置文件属性 <!-- 772203 -->
最终用户现在可以从公司门户应用访问关键帐户属性和操作，如密码重置。 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>可通过 iOS 上的 APP 设置阻止第三方键盘 <!-- 1248481 -->
在 iOS 设备上，Intune 管理员可以阻止使用第三方键盘在受策略保护的应用中访问组织数据。 当应用程序保护策略 (APP) 设置为阻止第三方键盘时，设备用户将在首次使用第三方键盘与公司数据交互时收到一条消息。 将阻止本地键盘以外的所有选项，设备用户不会看到它们。 设备用户只会看到一次对话消息。 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices----1248496---"></a>托管的 Android 和 iOS 设备上的 Intune 应用的用户帐户访问权限<!-- 1248496 -->
作为 Microsoft Intune 管理员，可控制将哪些用户帐户添加到托管设备上的 Microsoft Office 应用程序。 可以将访问权限限制为仅允许的组织用户帐户，并阻止已注册设备上的个人帐户。 

#### <a name="outlook-ios-and-android-app-configuration-policy---1828527---"></a>Outlook for iOS 和 Outlook for Android 应用配置策略 <!--1828527 -->
现在可以为通过 ActiveSync 协议进行基本身份验证的本地用户创建适用于 iOS 和 Android 的 Outlook for iOS 和 Outlook for Android 应用配置策略。 将为 Outlook for iOS 和 Outlook for Android 启用和添加其他配置设置。

#### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus 语言包 <!-- 1833450 -->
作为 Intune 管理员，你将能够为通过 Intune 管理的 Office 365 Pro Plus 应用部署其他语言。 可用语言列表包括语言包的“类型”（核心、部分和校对）。 在 Azure 门户中，选择“Microsoft Intune” > “客户端应用” > “应用” > “添加”。 在“添加应用”边栏选项卡的“应用类型”列表中，选择“Office 365 套件”下的“Windows 10”。 在“应用套件设置”边栏选项卡中选择“语言”。

####  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Windows 业务线 (LOB) 应用文件扩展名 <!-- 1884873 -->
Windows LOB 应用的文件扩展名现在包括 .msi、.appx、.appxbundle、.msix 和 .msixbundle。 可以在 Microsoft Intune 中添加应用，方法是通过选择“客户端应用” > “应用” > “添加”。 将显示“添加应用”窗格，可选择“应用类型”。 对于 Windows LOB 应用，选择“业务线”应用作为应用类型，选择“应用包文件”，然后输入带有扩展名的安装文件。

#### <a name="windows-10-app-deployment-using-intune----2309001---"></a>使用 Intune 部署 Windows 10 <!-- 2309001 -->
在业务线 (LOB) 应用和适用于企业的 Microsoft Store 应用的现有支持上进行构建时，管理员可以使用 Intune 将其组织的大部分现有应用程序部署到 Windows 10 设备上的最终用户。 管理员可以使用各种格式（例如 MSI、Setup.exe 或 MSP）为 Windows 10 用户添加、安装和卸载应用程序。 Intune 将在下载和安装、使用 Windows 10 操作中心通知最终用户状态或重新启动需求之前评估要求规则。 此功能将有效地清除对将此工作负荷转移到 Intune 和云感兴趣的组织所存在的阻碍。 此功能目前处于公共预览状态，我们预计在未来的几个月内为此功能添加重要的新功能。 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>最终用户设备和应用内容菜单 <!-- 2771453 -->
最终用户现在可以在设备和应用上使用上下文菜单触发常见操作，例如重命名设备或检查符合性。 

#### <a name="windows-company-portal-keyboard-shortcuts----2771518---"></a>Windows 公司门户键盘快捷方式 <!-- 2771518 -->
最终用户现在可以使用键盘快捷方式（快捷键）在 Windows 公司门户中触发应用和设备操作。

### <a name="device-configuration"></a>设备配置

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>在运行 Windows 10 的设备上的 VPN 配置文件中创建 DNS 后缀 <!-- 1333668 -->
在创建 VPN 设备配置的配置文件（“设备配置” > “配置文件” > “创建配置文件” > “Windows 10 及更高版本”平台>“VPN”配置文件类型）时，需要输入一些 DNS 设置。 通过此更新，还可以在 Intune 中输入多个 DNS 后缀。 使用 DNS 后缀时，可以使用其短名称而不是完全限定的域名 (FQDN) 搜索网络资源。 此更新还允许在 Intune 中更改 DNS 后缀的顺序。
[Windows 10 VPN 设置](vpn-settings-windows-10.md#dns-settings)列出了当前的 DNS 设置。
适用于：Windows 10 设备

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>支持 Android 企业工作配置文件的始终可用 VPN<!-- 1333705 -->
在此更新中，可以在具有托管工作配置文件的 Android 企业设备上使用始终可用的 VPN 连接。 始终可用 VPN 连接一直保持连接状态，或在用户解锁设备、设备重启或无线网络更改时立即重新连接。 还可以将连接置于“锁定”模式，该模式会阻止所有网络流量，直到 VPN 连接处于活动状态。
可以在“设备配置” > “配置文件” > “创建配置文件” >  适用于平台的“Android 企业版”>“设备限制” > “连接”设置中启用始终可用的 VPN。

#### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>向无用户设备颁发 SCEP 证书<!-- 1744554 -->
目前证书的颁发对象是用户。 通过此更新，SCEP 证书可以颁发给设备，包括无用户设备，例如网亭（“设备配置” > “配置文件” > “创建配置文件” >  适用于平台的“Windows 10 及更高版本”> 配置文件的“SCEP 证书”）。 其他更新包括：
- SCEP 配置文件中的“使用者”属性现在是自定义文本框，可以包含新的变量。 
- SCEP 配置文件中的“使用者可选名称(SAN)”属性现在是表格式，可以包含新的变量。 在表中，管理员可以添加属性并在自定义文本框中填写值。 SAN 将支持以下属性： 
  - DNS
  - 电子邮件地址
  - UPN

  可以在自定义值文本框中使用静态文本添加这些新变量。 例如，可以将 DNS 属性添加为 `DNS = {{AzureADDeviceId}}.domain.com`。

  > [!NOTE]
  > 在 SAN 的静态文本中无法使用大括号 ({ })、分号 (;) 和竖杠符号 (|)。 `Subject` 或 `Subject alternative name` 只接受大括号仅包含一个新设备证书变量的情况。 

新的设备证书变量：  

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

#### <a name="remotely-lock-uncompliant-devices----2064495---"></a>远程锁定不兼容的设备 <!-- 2064495 -->
如果设备不兼容，可以根据符合性策略创建一个可以远程锁定设备的操作。 在 Intune >“设备符合性”中，创建新的策略或选择现有策略 >“属性”。 选择“针对非符合性的操作” > “添加”，然后选择远程锁定设备。
在以下设备上受支持： 
- Android
- iOS
- macOS
- Windows 10 移动版 
- Windows Phone 8.1 及更高版本 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224---"></a>Azure 门户中的 Windows 10 和更高版本的网亭配置文件改进<!-- 2748224 -->
此更新包括对 Windows 10 网亭设备配置文件的以下改进（“设备配置” > “配置文件” > “创建配置文件” >  适用于平台的“Windows 10 及更高版本”> 配置文件类型的“网亭预览”）： 
- 目前，用户可以在同一设备上创建多个网亭配置文件。 利用此更新，Intune 将支持每台设备只有一个网亭配置文件。 如果你仍需要在单台设备上创建多个网亭配置文件，可以使用自定义 URI。
- 在“多应用网亭”配置文件中，可以在应用程序网格中对“开始菜单布局”选择应用程序磁贴大小和顺序。 如果需要更多自定义设置，可以继续上传 XML 文件。
- 网亭浏览器设置移入“网亭”设置。 目前，“网亭 Web 浏览器”设置在 Azure 门户中具有其自己的类别。
适用于：Windows 10 及更高版本




### <a name="device-enrollment"></a>设备注册

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>将 Autopilot 配置文件应用到尚未注册 Autopilot 的已注册 Win 10 设备<!-- 1558983 -->
可以将 Autopilot 配置文件应用到尚未注册 Autopilot 的已注册 Win 10 设备。 在 Autopilot 配置文件中，选择“将所有目标设备转换为 Autopilot”选项，以使用 Autopilot 部署服务自动注册非 Autopilot 设备。 等待 48 小时来处理注册。 取消注册设备并重置后，Autopilot 将对其进行配置。

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564---"></a>创建多个注册状态页配置文件并将其分配给 Azure AD 组<!-- 2526564 -->
现在可以[创建](windows-enrollment-status.md)多个注册状态页面配置文件并将其分配给 Azure AD 组。

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune---2748613--"></a>在 Intune 中从设备注册计划迁移到 Apple Business Manager <!--2748613-->
Apple Business Manager (ABM) 在 Intune 中工作，可以将你的帐户从设备注册计划 (DEP) 升级到 ABM。 Intune 中的过程是相同的。 若要将你的 Apple 帐户从 DEP 升级到 ABM，请转到 [ https://support.apple.com/en-us/HT208817]( https://support.apple.com/en-us/HT208817)。

### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page---2748656--"></a>“设备注册概述”页上的警报和注册状态选项卡 <!--2748656-->
警报和注册失败现在显示在“设备注册概述”页的单独选项卡上。

### <a name="device-management"></a>设备管理

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices----2451462----"></a>限制应用，并阻止对 Android 设备上公司资源的访问 <!-- 2451462  -->  
在“设备符合性” > “策略” > “创建策略” > “Android” > “系统安全”中，“设备安全”部分下有一个名为“受限制的应用”的新设置。 如果设备上安装了某些应用，“受限制的应用”设置将使用符合性策略来阻止对公司资源的访问。 除非从设备中删除受限制的应用，否则设备会一直被视为不符合要求。
适用于： 
- Android




## <a name="week-of-september-24-2018"></a>2018 年 9 月 24 日当周

### <a name="microsoft-365-device-management-administration-center----3078424---"></a>Microsoft 365 设备管理管理中心 <!-- 3078424 -->
Microsoft 365 的承诺之一是简化管理，多年来我们整合了后端 Microsoft 365 服务，以提供端到端方案（如 Intune 和 Azure AD 条件访问）。 新 [Microsoft 365 管理中心](http://devicemanagement.microsoft.com)整合、简化并集成了管理员体验。 借助设备管理的专家工作区，可轻松访问组织所需的所有设备和应用管理信息和任务。 我们希望这能成为企业最终用户计算团队的主要云工作区。

### <a name="support-for-more-third-party-certification-authorities-ca----3093107---"></a>为更多第三方证书颁发机构支持 (CA) 提供支持 <!-- 3093107 -->
通过简单证书注册协议 (SCEP)，现在可以使用 Windows、iOS、Android 和 macOS 在移动设备上发布新证书和续订证书。

### <a name="intune-moves-to-support-ios-10-and-later----2454656---"></a>Intune 转为支持 iOS 10 及更高版本 <!-- 2454656 -->  
Intune 注册、公司门户和托管浏览器现在仅支持运行 iOS 10 及更高版本的 iOS 设备。 若要查看组织中受影响的设备或用户，请转到 Azure 门户中的 Intune >“设备” > “所有设备”。 按 OS 进行筛选，然后单击“列”以显示 OS 版本详细信息。 请让这些用户将其设备升级到受支持的 OS 版本。  

如果拥有下面列出的任何设备，或者想要注册下面列出的任何设备，请注意，它们仅支持 iOS 9 及更早版本。  若要继续访问 Intune 公司门户，必须将这些设备升级到支持 iOS 10 或更高版本的设备：  

* iPhone 4S 
* iPod Touch  
* iPad 2 
* iPad（第 3 代） 
* iPad Mini（第 1 代）  

## <a name="week-of-september-17-2018"></a>2018 年 9 月 17 日当周

### <a name="app-management"></a>应用管理

### <a name="remove-duplication-of-app-protection-status-tiles----3083391---"></a>删除应用保护状态磁贴的副本 <!-- 3083391 -->
“iOS 用户状态”和“Android 用户状态”磁贴都会出现在“客户端应用 - 概述”页，以及“客户端应用 - 应用保护状态”页。 已从“客户端应用 - 概述”页删除状态磁贴，以避免重复。 

## <a name="week-of-august-27-2018"></a>2018 年 8 月 27 日当周

### <a name="app-management"></a>应用管理

#### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types----1520957---"></a>针对自定义和 Pulse Secure 连接类型的 iOS 每应用 VPN 配置文件的数据包隧道支持 <!-- 1520957 -->
如果使用 iOS 每应用 VPN 配置文件，可选择使用应用层隧道（应用-代理）或数据包级别隧道（数据包-隧道）。 这些选项适用于以下连接类型：
- 自定义 VPN
- Pulse Secure - 如果不确定使用哪个值，请查阅 VPN 提供商的文档。

#### <a name="delay-when-ios-software-updates-are-shown-on-the-device----1949583---"></a>延迟 iOS 软件更新在设备上的显示时间 <!-- 1949583 -->
在 Intune >“软件更新” > “适用于 iOS 的更新策略”中，可配置不希望设备安装任何更新的日期和时间段。 在未来的某个更新中，可延迟软件更新在设备上的显示时间（1-90 天）。 
[在 Microsoft Intune 中配置 iOS 更新策略](software-updates-ios.md)列出了当前设置。

#### <a name="office-365-proplus-version----2213968---"></a>Office 365 专业增强版 <!-- 2213968 -->
如果使用 Intune 将 Office 365 专业增强版应用分配到 Windows 10 设备，则可选择 Office 的版本。 在 Azure 门户中，选择“Microsoft Intune” > “应用” > “添加应用”。 然后，从“类型”下拉列表中选择“Office 365 专业增强版套件(Windows 10)”。 选择“应用套件设置”以显示关联的边栏选项卡。 将“更新通道”设置为一个值，如“每月”。 （可选）选择“是”，从最终用户设备中删除其他版本的 Office (msi)。 选择“特定”，在最终用户设备上为所选通道安装特定的 Office 版本。 此时，可选择要使用的“特定版本”的 Office。 可用版本会随时间发生变化。 因此，在创建新部署时，可用版本可能为更新的版本，而不再提供某些较旧版本。 当前部署会继续部署旧版本，但版本列表会持续按通道更新。 有关详细信息，请参阅 [Office 365 专业增强版的更新频道概述](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)。

#### <a name="support-for-register-dns-setting-for-windows-10-vpn----2282852---"></a>支持面向 Windows 10 VPN 的“注册 DNS”设置 <!-- 2282852 -->
通过此次更新，可将 Windows 10 VPN 配置文件配置为使用内部 DNS 动态注册分配给 VPN 接口的 IP 地址，而无需使用自定义配置文件。
有关当前可用的 VPN 配置文件设置的信息，请参阅 [Windows 10 VPN 设置](vpn-settings-windows-10.md)。 

#### <a name="the-macos-company-portal-installer-now-includes-the-version-number-in-the-installer-file-name---2652728--"></a>macOS 公司门户安装程序的安装程序文件名称中现在包含版本号 <!--2652728-->

#### <a name="ios-automatic-app-updates----2729759-wnready---"></a>iOS 自动应用更新 <!-- 2729759 wnready -->
自动应用更新适用于设备和用于 iOS 11.0 及更高版本的用户许可应用。




### <a name="device-configuration"></a>设备配置

#### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>Windows Hello 面向用户和设备 <!-- 1106609 -->
创建 [Windows hello 企业版](windows-hello.md)策略后，该策略会应用到组织中的所有用户（租户范围）。 进行此更新后，还可使用设备配置策略（“设备配置” > “配置文件” > “创建配置文件” > “标识保护” > “Windows Hello 企业版”），将此策略应用于特定用户或特定设备。
在 Intune Azure 门户中，Windows Hello 配置和设置现在同时存在于“设备注册”和“设备配置”中。 **设备注册**面向整个组织（租户范围内），并支持 Windows AutoPilot (OOBE)。 **设备配置**面向使用某种策略的设备和用户，该策略会在签入期间应用。
此功能适用于：  
- Windows 10 及更高版本
- Windows Holographic for Business

#### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858---"></a>Zscaler 是适用于 iOS 上 VPN 配置文件的可用连接 <!-- 1769858 -->
创建 iOS VPN 设备配置文件时（“设备配置” > “配置文件” > “创建配置文件” > “iOS”“平台”>“VPN 配置文件类型”），有几种连接类型，包括 Cisco、Citrix 等。 此次更新将 Zscaler 添加为一个连接类型。 
[运行 iOS 的设备的 VPN 设置](vpn-settings-ios.md)列出了可用的连接类型。

#### <a name="fips-mode-for-enterprise-wi-fi-profiles-for-windows-10----1879077---"></a>适用于 Windows 10 企业 Wi-Fi 配置文件的 FIPS 模式<!-- 1879077 -->
现在可在 Intune Azure 门户中启用适用于 Windows 10 企业 Wi-Fi 配置文件的美国联邦信息处理标准 (FIPS) 模式。 如果在 Wi-Fi 配置文件中启用 FIPS 模式，请确保 Wi-Fi 基础结构上已启用该模式。
有关如何创建 Wi-Fi 配置文件，请参阅 [Intune 中适用于 Windows 10 及更高版本设备的 Wi-Fi 设置](wi-fi-settings-windows.md)。

#### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>在 Windows 10 和更高版本的设备上控制 S 模式 - 公共预览版 <!-- 1958649 -->
利用该功能更新，可创建一个设备配置文件，用于将 Windows 10 设备从 S 模式下切换出来，或用于防止用户将设备从 S 模式下切换出来。 此功能的位置：Intune >“设备配置” > “配置文件” >  “Windows 10 及更高版本” > “版本升级和模式切换”。
[S 模式下的 Windows 10 简介](https://www.microsoft.com/windows/s-mode)提供了有关 S 模式的详细信息。
适用于：最新的 [Windows 预览体验](https://docs.microsoft.com/windows-insider/at-work-pro/)版本（预览版）。


#### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Windows Defender ATP 配置包自动添加到配置文件 <!-- 2144658 -->
在 Intune 中使用[高级威胁防护和加入](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile)设备时，需要提前下载配置包并将其添加到配置文件。 通过此次更新，Intune 可自动从 Windows Defender 安全中心获取该包，并将其添加到配置文件。
适用于 Windows 10 和更高版本。

#### <a name="require-users-to-connect-during-device-setup---2311457--"></a>要求用户在设备设置过程中进行连接<!--2311457-->
现在可以设置设备配置文件，要求设备在 Windows 10 设置过程中连接到网络，然后才能继续完成“网络”页面的操作。 虽然此功能处于预览状态，但 Windows 预览体验内部版本 1809 或更高版本需要使用此设置。
适用于：最新的 [Windows 预览体验](https://docs.microsoft.com/windows-insider/at-work-pro/)版本（预览版）。


#### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-enterprise-devices----2451462---"></a>限制应用，并阻止对 iOS 和 Android Enterprise 设备上公司资源的访问<!-- 2451462 -->
在“设备符合性” > “策略” > “创建策略” > “iOS” > “系统安全”中，有一个新的“受限制的应用程序”设置。 如果设备上安装了某些应用，此新设置会使用符合性策略来阻止对公司资源的访问。 除非从设备中删除受限制的应用，否则设备会一直被视为不符合要求。
适用于：iOS

#### <a name="modern-vpn-support-updates-for-ios----2459928-1819876-and-2650856---"></a>适用于 iOS 的新式 VPN 支持更新 <!-- 2459928, 1819876, and 2650856 -->
此次更新添加了对以下 iOS VPN 客户端的支持： 
- F5 Access（版本 3.0.1 及更高版本）
- Citrix SSO
- 此次更新还包含 Palo Alto Networks GlobalProtect 版本 5.0 及更高版本：
- iOS 的现有“F5 访问”连接类型已重命名为“旧版 F5 访问”。
- iOS 的现有“Palo Alto Networks GlobalProtect”连接类型已重命名为“旧版 Palo Alto Networks GlobalProtect”。
使用这些连接类型的现有配置文件将继续使用其各自的旧版 VPN 客户端。 如果要将 Cisco 旧式 AnyConnect、旧版 F5 访问、Citrix VPN 或 Palo Alto Networks GlobalProtect 4.1 及更早版本与 iOS 配合使用，则应改为使用新应用。 尽快执行此操作以确保可在更新到 iOS 12 的 iOS 设备上实现 VPN 访问。
有关 iOS 12 和 VPN 配置文件的详细信息，请参阅 [Microsoft Intune 支持团队博客](https://go.microsoft.com/fwlink/?linkid=2013806)。

#### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal----2469637---"></a>导出 Azure 经典门户的符合性策略，以在 Intune Azure 门户中重新创建这些策略<!-- 2469637 -->
将弃用 Azure 经典门户中创建的符合性策略。 可查看和删除任何现有符合性策略，但无法更新它们。 如果需要将任何符合性策略迁移到最新的 Intune Azure 门户，可将策略导出为逗号分隔的文件（.csv 文件）。 然后使用文件中的详细信息在 Intune Azure 门户中重新创建这些策略。

> [!IMPORTANT]
> Azure 经典门户停用后，将无法访问或查看符合性策略。 因此，在 Azure 经典门户停用之前，务必导出策略并在 Azure 门户中重新创建这些策略。

#### <a name="better-mobile---new-mobile-threat-defense-partner----22662717---"></a>Better Mobile - 新移动威胁防御合作伙伴<!-- 22662717 -->
可根据 Better Mobile 进行的风险评估，使用条件访问控制移动设备对公司资源的访问，Better Mobile 是与 Microsoft Intune 集成的移动威胁防御解决方案。

### <a name="device-enrollment"></a>设备注册

#### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in---1067692---"></a>将公司门户锁定在单应用模式下，直至用户登录 <!--1067692 --> 
如果在 DEP 注册过程中通过公司门户而非“设置助理”来对用户进行身份验证，那么现在可选择在单应用模式下运行公司门户。 此选项会在“设置助手”操作完成后立即锁定设备，这样用户须登录才能访问设备。 此过程可确保设备完成载入，且不会进入无任何用户绑定的孤立状态。

#### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device---1346521---"></a>为 Autopilot 设备分配一个用户和友好名称 <!--1346521 -->
现在可[将用户分配到单独的 Autopilot 设备](enrollment-autopilot.md)。 在使用 Autopilot 为用户设置设备时，管理员还可提供友好名称来问候用户。
适用于：最新的 [Windows 预览体验](https://docs.microsoft.com/windows-insider/at-work-pro/)版本（预览版）。

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>在 DEP 注册期间，使用 VPP 设备许可证预先设置公司门户 <!-- 1608345 -->
现可在设备注册计划 (DEP) 注册期间，使用批量采购计划 (VPP) 设备许可证预先设置公司门户。 若要完成此操作，在[创建或编辑注册配置文件](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile)时，指定要用于安装公司门户的 VPP 令牌。 请确保令牌没有过期，并且具有足够的公司门户应用许可证。 如果令牌过期或许可证用完，Intune 将改为推送 App Store 公司门户（这将提示输入 Apple ID）。

#### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>需要确认才能删除正用于公司门户预先设置的 VPP 令牌 <!-- 2237634 -->
如果在 DEP 注册期间正在使用批量购买计划 (VPP) 预先设置公司门户，则现在需要确认是否删除此令牌。

#### <a name="block-windows-personal-device-enrollments----1849498---"></a>阻止 Windows 个人设备注册 <!-- 1849498 -->
可通过 Intune 中的[移动设备管理](windows-enroll.md)[阻止 Windows 个人设备](enrollment-restrictions-set.md#set-device-type-restrictions)进行注册。 无法使用此功能阻止注册了 [Intune PC 代理](manage-windows-pcs-with-microsoft-intune.md)的设备。 这一功能将在随后几周内推出，因此你可能无法立即在用户界面中看到此功能。

#### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>在 Autopilot 配置文件中指定计算机名称模式 <!--1849855-->
可[指定一个计算机名称模板](enrollment-autopilot.md#create-an-autopilot-deployment-profile)，用于在 Autopilot 注册过程中生成和设置[计算机名](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp)。 适用于：最新的 [Windows 预览体验](https://docs.microsoft.com/windows-insider/at-work-pro/)版本（预览版）。


#### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>对于 Windows Autopilot 配置文件，隐藏公司登录页和域错误页上的“更改帐户”选项 <!--1901669 -->
提供[新的 Windows Autopilot 配置文件选项](enrollment-autopilot.md#create-an-autopilot-deployment-profile)，允许管理员隐藏公司登录页和域错误页上的更改帐户选项。 要隐藏这些选项，需在 Azure Active Directory 中配置公司品牌。 适用于：最新的 [Windows 预览体验](https://docs.microsoft.com/windows-insider/at-work-pro/)版本（预览版）。



### <a name="device-management"></a>设备管理

#### <a name="delete-jamf-devices----2653306--"></a>删除 Jamf 设备 <!-- 2653306-->
通过转到“设备”>“选择 Jamf 设备”>“删除”，可以删除 JAMF 托管的设备。

#### <a name="change-terminology-to-retire-and-wipe----2175759---"></a>将术语更改为“停用”和“擦除”<!-- 2175759 -->
为了与 Graph API 保持一致，Intune 用户界面和文档已更改以下术语：
- “删除公司数据”更改为“停用”
- “恢复出厂设置”将更改为“擦除”

#### <a name="confirmation-dialog-if-admin-tries-to-delete-mdm-push-certificate----297909500--"></a>管理员尝试删除 MDM 推送证书时出现的确认对话框 <!-- 297909500-->
如果有人尝试删除 Apple MDM 推送证书，确认对话框会显示相关的 iOS 和 macOS 设备数。 删除证书后，需要重新注册这些设备。

### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Windows Installer 的其他安全设置 <!-- 2282430 -->
可允许用户控制应用安装。 如果启用，则允许因安全冲突而停止的安装继续进行。 当 Windows Installer 在系统上安装任何程序时，可指示它使用提升的权限。 此外，还可以对 Windows 信息保护 (WIP) 项目编制索引，并将有关这些项目的元数据存储在未加密的位置。 禁用策略后，不会索引受 WIP 保护的项，也不会在 Cortana 或文件资源管理器的结果中显示这些项。 默认情况下禁用这些选项的功能。 

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>公司门户网站的新用户体验更新<!--2000968 -->
我们已根据客户反馈向公司门户网站添加新功能。 可从设备上体验到现有功能和可用性的重大改进。 该网站的各个区域（如设备详细信息、反馈与支持以及设备概述）都采用了全新的现代化快速响应设计。 你还会看到：

- 简化了所有设备平台上的工作流
- 改进了设备识别和注册流
- 提供了更多有用的错误消息
- 更友好的语言，减少了专业技术性术语
- 能够共享指向应用的直接链接
- 改善了大型应用目录的性能
- 为所有用户增加了辅助功能  

已更新 [Intune 公司门户网站文档](https://docs.microsoft.com/intune-user-help/using-the-intune-company-portal-website)以体现这些更改。 若要查看应用增强功能的示例，请参阅[Intune 最终用户应用的 UI 更新](whats-new-app-ui.md)。  

### <a name="monitor-and-troubleshoot"></a>监视和故障排除

#### <a name="enhanced-jailbreak-detection-in-compliance-reporting---2198738---"></a>符合性报告中的强化型越狱检测<!-- 2198738 -->
现在，强化型越狱检测设置状态将显示在管理员控制台中的所有符合性报告中。

### <a name="role-based-access-control"></a>基于角色的访问控制

#### <a name="scope-tags-for-policies---1081974---"></a>策略的作用域标记 <!--1081974 -->
可[创建作用域标记](scope-tags.md)来限制对 Intune 资源的访问。 将作用域标记添加到某个角色分配，然后将作用域标记添加到某个配置文件。 角色将仅有权访问符合后列条件的资源：其资源配置文件的作用域标记与角色标记匹配或无作用域标记。

## <a name="week-of-august-14-2018"></a>2018 年 8 月 14 日当周

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>Apple 设备注册计划支持注册 macOS 设备 <!-- 747651 -->
Intune 现支持将 macOS 设备注册到 Apple 设备注册计划 (DEP) 中。 有关详细信息，请参阅[通过 Apple 设备注册计划自动注册 macOS 设备](device-enrollment-program-enroll-macos.md)。

## <a name="week-of-july-23-2018"></a>2018 年 7 月 23 日的这一周

### <a name="app-management"></a>应用管理

#### <a name="line-of-business-lob-app-support-for-macos----1895847---"></a>对 macOS 的业务线 (LOB) 应用支持 <!-- 1895847 -->
Microsoft Intune 允许将 macOS LOB 应用部署为“必需”或“注册时可用”。 最终用户可通过适用于 macOS 公司门户或[公司门户网站](https://portal.manage.microsoft.com)获得部署为“可用”的应用。

#### <a name="ios-built-in-app-support-for-kiosk-mode----2051098---"></a>iOS 内置应用支持展台模式 <!-- 2051098 -->
除了应用商店应用和托管应用，现在可以选择在 iOS 设备上以展台模式运行的内置应用（例如 Safari）。

#### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>编辑 Office 365 Pro Plus 应用部署 <!-- 2150145 -->
作为 Microsoft Intune 管理员，现在可以对 Office 365 专业增强版应用部署进行更多编辑。 此外，不再需要删除部署以更改任何套件属性。 在 Azure 门户中，选择“Microsoft Intune” > “客户端应用” > “应用”。 从应用列表中选择你的 Office 365 Pro Plus 套件。  


#### <a name="updated-intune-app-sdk-for-android-is-now-available----2744271--"></a>现在提供更新的 Intune App SDK for Android <!-- 2744271-->

现在提供 Intune App SDK for Android 的更新版本，以支持 Android P 版本。 如果你是应用开发人员并使用 Intune SDK for Android，则必须安装 Intune app SDK 的更新版本，以确保 Android 应用中的 Intune 功能在 Android P 设备上运行正常。 此版本的 Intune App SDK 提供执行 SDK 更新的内置插件。 你无需重写集成的任何现有代码。 有关详细信息，请参阅 [Intune SDK for Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android)。 如果你使用的是 Intune 的旧标记样式，我们建议你使用公文包图标。 有关品牌打造的详细信息，请参阅[此 GitHub 存储库](https://github.com/msintuneappsdk/intune-app-partner-badge)。


### <a name="device-configuration"></a>设备配置

#### <a name="use-smime-to-encrypt-and-sign-a-users-multiple-devices-----1333642---"></a>使用 S/MIME 对用户的多个设备进行加密和签名 <!-- 1333642 -->
此更新包括使用新导入的证书配置文件进行 S/MIME 电子邮件加密（“设备配置” > “配置文件” > “创建配置文件”>“选择平台”>“PKCS 导入的证书”配置文件类型）。 在 Intune 中，可以 PFX 格式导入证书。 然后 Intune 可以将这些相同的证书传递给单个用户注册的多个设备。 还包括：

- 本机 iOS 电子邮件配置文件支持使用 PFX 格式的导入证书启用 S/MIME 加密。
- Windows Phone 10 设备上的本机电子邮件应用自动使用 S/MIME 证书。
- 可以跨多个平台传递私有证书。 但并非所有电子邮件应用都支持 S/MIME。
- 在其他平台上，可能需要手动配置电子邮件应用以启用 S/MIME。  
- 支持 S/MIME 加密的电子邮件应用可能以 MDM 不支持的方式（例如从发布者的证书存储读取）处理对 S/MIME 电子邮件加密的证书检索。

支持的设备：Windows、Windows Phone 10、macOS、iOS、Android

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>在 macOS 设备上使用防火墙设置创建设备符合性策略 <!-- 1497640 -->
创建新的 macOS 符合性策略（“设备符合性” > “策略” > “创建策略” > “平台: macOS” > “系统安全性”）时，有一些新的可用“防火墙”设置： 

- 防火墙：配置环境对传入连接的处理方式。
- 传入连接：阻止所有传入连接，DHCP、Bonjour 和 IPSec 等基本 Internet 服务需要的连接除外。 此设置还会阻止所有共享服务。
- 隐藏模式：启用隐藏模式以防止设备响应探测请求。 设备会继续回应已授权应用的传入请求。

适用于：macOS 10.12 及更高版本

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Windows 10 及更高版本的新 Wi-Fi 设备配置文件 <!-- 1879077 -->
目前，可以使用 XML 文件导入和导出 Wi-Fi 配置文件。 通过此次更新，能够直接在 Intune 中创建 Wi-Fi 设备配置文件，与在某些其他平台上的操作一样。

若要创建配置文件，打开“设备配置” > “配置文件” > “创建配置文件” > “Windows 10 及更高版本” > “Wi-Fi”。 

适用于 Windows 10 和更高版本。

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998---"></a>Kiosk - 已过时显示为灰色，无法更改 <!-- 2149998 -->
[展台功能](device-restrictions-windows-10.md#kiosk-preview---obsolete)（“设备配置” > “配置文件” > “创建配置文件” > “Windows 10 及更高版本” > “设备限制”）已过时，并替换为[适用于 Windows 10 和更高版本的展台设置](kiosk-settings.md)。 更新后，“展台 - 已过时”功能显示为灰色，并且无法更改或更新用户界面。 

若要启用展台模式，请参阅 [Windows 10 及更高版本的 Kiosk 设置](kiosk-settings.md)。

应用于 Windows 10 及更高版本、Windows Holographic for Business

#### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>使用第 3 方证书颁发机构的 API <!-- 2184013 -->
此更新中有一个 Java API，能实现第三方证书颁发机构与 Intune 和 SCEP 的集成。 然后用户可以将 SCEP 证书添加到配置文件，并使用 MDM 将其应用于设备。

目前 Intune 支持[使用 Active Directory 证书服务的 SCEP 请求](certificates-scep-configure.md)。

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>切换以显示或不显示 Kiosk 浏览器上的“结束会话”按钮 <!-- 2455253 -->
现可配置展台浏览器是否显示“结束会话”按钮。 可以在“设备配置” > “Kiosk（预览）” > “Kiosk Web 浏览器”中看到控件。 若关闭，用户单击按钮时，应用会提示是否结束会话。 确定结束时，浏览器清除所有浏览数据并导航回到默认 URL。

#### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>创建 eSIM 卡移动电话配置文件 <!-- 2564077 -->
在“设备配置”中，可创建 eSIM 手机网络配置文件。 可以导入包含移动运营商提供的移动电话激活码的文件。 然后，可以将这些配置文件部署到支持 eSIM LTE 的 Windows 10 设备，例如 Surface Pro LTE 和其他支持 eSIM 卡的设备。

检查[设备是否支持 eSIM 卡配置文件](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data)。

适用于 Windows 10 和更高版本。 




### <a name="device-enrollment"></a>设备注册

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>自动标记使用 Samsung Knox 移动注册为“公司”注册的 Android 设备。 <!-- 2404851 -->
默认情况下，使用 Samsung Knox 移动注册的 Android 设备现在标记为“设备所有权”下的“公司”。 使用 Knox 移动注册之前，不需要使用 IMEI 或序列号手动识别公司设备。

### <a name="device-management"></a>设备管理

#### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>在设备边栏选项卡上批量删除设备 <!-- 1793693 -->

现在可在“设备”边栏选项卡上一次删除多个设备。 选择“设备” > “所有设备”>“选择要删除的设备”>“删除”。 对于无法删除的设备，会出现警告。

## <a name="week-of-july-16-2018"></a>2018 年 7 月 16 日所在的一周  

### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>适用于 Windows 的公司门户应用中的更多同步机会  
适用于 Windows 的公司门户应用现在允许直接从 Windows 任务栏和“开始”菜单启动同步。 如果唯一任务是同步设备并访问公司资源，那么此功能特别有用。 要访问新功能，请右键单击固定到任务栏或“开始”菜单的公司门户图标。 在菜单选项（也称为跳转列表）中，选择“同步此设备”。 公司门户将打开“设置”页面并启动同步。若要了解新功能，请参阅 [UI 中的新增功能](whats-new-app-ui.md)。   

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>适用于 Windows 的公司门户应用中的新浏览体验  

现在，在适用于 Windows 的公司门户应用中浏览或搜索应用时，用户能在现有的“磁贴”视图和新添加的“详细信息”视图之间切换。 新视图列出应用程序详细信息，如名称、发布服务器、发布日期和安装状态。  

通过“应用”页的“已安装”视图可查看已完成和正在进行的应用安装的详细信息。 若要查看新视图的外观，请参阅 [UI 中的新增功能](whats-new-app-ui.md)。  
### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>针对设备注册管理员，改进了公司门户应用体验  
现在，当设备注册管理员 (DEM) 登录到适用于 Windows 的公司门户应用时，该应用将仅列出 DEM 当前正在运行的设备。 以前应用尝试显示所有 DEM 注册设备，会出现较长的超时，此改进则将减少超时时间。  


## <a name="week-of-july-9-2018"></a>2018 年 7 月 9 日所在的一周

### <a name="app-management"></a>应用管理

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>基于未批准的设备供应商和型号阻止应用的访问 <!-- 1425689 ! -->
Intune IT 管理员可通过 Intune 应用保护策略强制实施指定的 Android 制造商和/或 iOS 型号列表。 IT 管理员可以提供适用于 Android 策略的供应商列表和适用于 iOS 策略的设备型号列表，列表以分号分隔。 Intune App 保护策略仅适用于 Android 和 iOS。 可针对此指定列表执行两个单独的操作：
- 阻止应用访问未指定的设备。
- 或者，选择性地擦除未指定的设备上的企业数据。 

如果未满足策略要求，则用户将无法访问目标应用程序。 根据设置，用户可能会被阻止或选择性地删除应用中的用户企业数据。 在 iOS 设备上，需使用一些应用程序（例如 WXP、Outlook、Managed Browser 和 Yammer）与 Intune APP SDK 进行集成，才能在目标应用程序中强制实施此功能。 此集成陆续进行，取决于特定应用程序团队。 在 Android 上，此功能需要使用最新的公司门户。 

在最终用户设备上，Intune 客户端将根据 Intune 边栏选项卡中针对应用程序保护策略所指定的字符串的简单匹配来执行操作。 这完全取决于设备报告的值。 为此，建议 IT 管理员确保预期行为的准确性。 这可以通过根据面向较小规模用户组的各种设备制造商和型号对此设置进行测试来实现。 在 Microsoft Intune 中，选择“客户端应用” > “应用保护策略”，可查看和添加应用保护策略。 有关应用保护策略的详细信息，请参阅[什么是应用保护策略](app-protection-policy.md)和[在 Intune 中使用应用保护策略访问操作选择性地擦除数据](app-protection-policies-access-actions.md)。

### <a name="access-to-macos-company-portal-pre-release-build----1734766---"></a>访问 macOS 公司门户预发布版本 <!-- 1734766 -->
借助 Microsoft 自动更新，可通过加入预览体验计划注册抢先收到内部版本。 注册后，即可在公司门户更新版向最终用户推出前使用它。 有关详细信息，请参阅 [Microsoft Intune 博客](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/)。

## <a name="week-of-july-2-2018"></a>2018 年 7 月 2 日的这一周

### <a name="app-management"></a>应用管理

#### <a name="monitor-ios--app-configuration-status-per-device----880037---"></a>监控每个设备的 iOS 应用配置状态 <!-- 880037 -->
作为 Microsoft Intune 管理员，可监控每个受管理设备的 iOS 应用配置状态。 从 Azure 门户的“Microsoft Intune”中，选择“设备” > “所有设备”。 从受管理设备列表中选择特定设备，以显示该设备的边栏选项卡。 在该设备的边栏选项卡上，选择“应用配置”。

#### <a name="access-actions-for-app-protection-policies----1483510---"></a>应用保护策略操作的访问权限 <!-- 1483510 -->
可配置应用保护策略，显式擦除、阻止或警告不符合要求的设备。 “擦除”操作将从设备中删除贵公司的企业数据。 当出现擦除操作时，系统将会通知设备的用户擦除原因和修正步骤。 对于某些设置（例如，最低操作版本），你将能够应用多个操作，例如阻止和擦除。 注意，启动应用时会触发这些操作。

#### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>选择性擦除组织的应用数据 <!-- 1507030 -->
当不满足应用程序保护策略 (APP) 访问设置的条件时，管理员现可配置一项新操作，即选择性擦除组织数据配置。  此功能可帮助管理员根据预先配置的标准自动保护和删除应用程序中的敏感组织数据。

#### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>撤销通过 VPP 购买的 iOS 应用 <!-- 1777384 -->
作为 Microsoft Intune 管理员，可撤销通过批量采购计划 (VPP) 购买的选定 iOS 应用的所有许可证。 可在取消向用户分配用户许可的应用时向其发出通知。 撤销应用许可证将不会从设备中卸载相关的 VPP 应用。 若要卸载 VPP 应用，必须将分配操作更改为“卸载”。 回收的许可证计数将反映在 Intune“应用”工作负荷的“许可应用”节点中。 有关 iOS VPP 应用的详细信息，请参阅[如何使用 Microsoft Intune 管理通过批量采购计划购买的 iOS 应用](vpp-apps-ios.md)。

#### <a name="updates-to-out-of-compliance-messages-in-company-portal-app----1832222---"></a>公司门户应用中不合规消息的更新<!-- 1832222 -->
我们修改了设备用户在设备不合规时看到的消息。 消息保留其原始含义，但已使用更友好的语言和更少的技术术语进行了更新。 我们还刷新了文档和修正步骤的链接，使其保持最新状态。
以下修改前后的内容是将看到的消息改进的一个示例：
- 修改前：此设备未在 IT 管理员要求的指定时间内联系 Intune 服务。要解决此问题，请打开设备上的公司门户应用，单击“检查符合性”按钮。
- 修改后：设备在一段时间内未签入组织。要重新建立连接，请打开设备上的公司门户应用并点击设备的“检查设置”。

#### <a name="revoke-ios-vpp-app-license----1863797---"></a>撤消 iOS VPP 应用许可证 <!-- 1863797 -->
作为管理员，可回收分配给用户或设备的 iOS VPP 应用许可证。 也可通过卸载 iOS VPP 应用回收应用许可证。 卸载应用前，需要将用户或设备从应用的目标组中删除。 从该组中删除用户或设备可避免重新安装该应用。 完成这些步骤后，可选择将该应用许可证分配给其他用户或设备。 有关 iOS VPP 应用许可证的详细信息，请参阅[在 Microsoft Intune 中管理 iOS 批量购买的应用](vpp-apps-ios.md)。

### <a name="device-configuration"></a>设备配置

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eenotready---"></a>使用“访问工作或学校帐户”设置选择设备类别 <!-- 1058963 eenotready --> 
如果已启用[设备组映射](https://docs.microsoft.com/intune/device-group-mapping)，Windows 10 用户现将在通过“设置” > “帐户” > “访问工作或学校帐户”中的“连接”按钮注册后，看到选择设备类别的提示。 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>使用 sAMAccountName 作为电子邮件配置文件的帐户用户名 <!-- 1500307 -->
可使用本地“sAMAccountName”作为 Android、iOS 和 Windows 10 的电子邮件配置文件的帐户用户名。 还可从 Azure Active Directory (Azure AD) 中的 `domain` 或 `ntdomain` 属性获取域。 或者，输入自定义静态域。

若要使用此功能，必须将本地 Active Directory 环境中的 `sAMAccountName` 属性同步到 Azure AD。

适用于 [Android](email-settings-android.md)、[iOS](email-settings-ios.md)、[Windows 10 及更高版本](email-settings-windows-10.md)

#### <a name="see-device-configuration-profiles-in-conflict----1556983---"></a>查看冲突的设备配置文件<!-- 1556983 -->
“设备配置”中将显示现有配置文件列表。 此更新中添加了新列，用于提供有冲突的配置文件的详细信息。 可选中冲突的行以查看存在冲突的设置和配置文件。 

可在[管理配置文件](device-profile-monitor.md#view-conflicts)中查看详细信息。

#### <a name="new-status-for-devices-in-device-compliance----2308882---"></a>设备符合性中的设备新状态 <!-- 2308882 -->
在“设备符合性” > “策略”>“选择策略”>“概述”中，添加以下新状态：
- 成功
- 错误
- 冲突
- 挂起
- 不适用 还显示了图像，展示其他平台的设备计数。 例如，如果正在查看 iOS 配置文件，则新磁贴会显示同时分配给到配置文件的非 iOS 设备数。 请参阅[设备符合性策略](compliance-policy-monitor.md#view-status-of-device-policies)。

#### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>设备符合性支持第三方防病毒解决方案 <!-- 2325484 -->
当创建设备符合性策略（“设备符合性” > “策略” > “创建策略” > “平台: Windows 10 及更高版本” > “设置” > “系统安全”）时，会出现新的[设备安全性](compliance-policy-create-windows.md#windows-10-and-later-policy-settings)选项： 
- 防病毒：当设置为“需要”时，可使用在 Windows 安全中心注册的防病毒解决方案（如 Symantec 和 Windows Defender）来检查符合性。 
- 反间谍软件：当设置为“需要”时，可以使用在 Windows 安全中心注册的反间谍软件解决方案（如 Symantec 和 Windows Defender）来检查符合性。 

适用于：Windows 10 及更高版本 

### <a name="device-enrollment"></a>设备注册

####  <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens----1853904---"></a>注册计划令牌列表中没有配置文件列的设备 <!-- 1853904 -->
注册计划令牌列表中存在一个新列，显示未分配配置文件的设备数量。 这有助于管理员在将配置文件分发给用户之前，先为这些设备分配配置文件。 若要查看新列，请转到“设备注册” > “Apple 注册” > “注册计划令牌”。

### <a name="device-management"></a>设备管理

#### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>停用 Android for Work 和 Play for Work 以反映 Google 名称更改 <!--842873 -->
Intune 已更新“Android for Work”术语，以反映 Google 品牌的更改。 不再使用术语“Android for Work”和“Play for Work”。 根据上下文使用不同的术语：
- “Android 企业”指整个现代 Android 管理堆栈。
- “工作配置文件”或“配置文件所有者”指使用工作配置文件管理的 BYOD 设备。
- “托管的 Google Play”指 Google 应用商店。

#### <a name="rules-for-removing-devices----1609459---"></a>删除设备的规则<!-- 1609459 -->
提供新规则，用于自动删除未在设置天数内进行签入的设备。 要查看新规则，请转到“Intune”窗格，依次选择“设备”和“设备清理规则”。

#### <a name="corporate-owned-single-use-support-for-android-devices----1630973---"></a>支持公司拥有的单一用途 Android 设备 <!-- 1630973 -->

Intune 现支持受到高度管控的锁定展台式 Android 设备。 这使管理员可以将设备的使用进一步锁定到单个应用或一小组应用，并阻止用户在设备上启用其他应用或执行其他操作。 若要设置 Android 展台，请转到 Intune >“设备注册” > “Android 注册” > “展台和任务设备注册”。 有关详细信息，请参阅[设置 Android 企业展台设备的注册](android-kiosk-enroll.md)。

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794--"></a>逐行查看上传的重复公司设备标识符 <!-- 2203794-->
上传企业 ID 时，Intune 现提供重复项列表，你可以选择替换或保留现有信息。 选择“设备注册” > “公司设备标识符” > “添加标识符”后，如果有重复项，将显示报告。 

#### <a name="manually-add-corporate-device-identifiers----2203803---"></a>手动添加公司设备标识符 <!-- 2203803 -->
现在可以手动添加公司设备 ID。 选择“设备注册” > “公司设备标识符” > “添加”。 

## <a name="week-of-june-25-2018"></a>2018 年 6 月 25 日的这一周

### <a name="pradeo---new-mobile-threat-defense-partner----1169249---"></a>Pradeo - 新移动威胁防御合作伙伴<!-- 1169249 -->

可根据 Pradeo 给出的风险评估，使用条件访问控制移动设备对公司资源的访问，Pradeo 是与 Microsoft Intune 集成的移动威胁防御解决方案。

## <a name="week-of-june-18-2018"></a>2018 年 6 月 18 日的这一周

### <a name="microsoft-edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>针对 Intune 应用保护策略的 Microsoft Edge 移动设备支持 <!-- 1817882 -->

移动设备的 Microsoft Edge 浏览器现在支持在 Intune 中定义的应用保护策略。

## <a name="week-of-june-11-2018"></a>2018 年 6 月 11 日的这一周

### <a name="use-fips-mode-with-the-ndes-certificate-connector----1333688---"></a>将 FIPS 模式用于 NDES 证书连接器<!-- 1333688 -->
在已启用美国联邦信息处理标准 (FIPS) 模式的计算机上安装 NDES 证书连接器时，颁发和吊销证书不能按预期工作。 在此更新中，NDES 证书连接器中包含 FIPS 支持。 

此更新还包括：

- NDES 证书连接器需要 .NET 4.5 Framework，Windows Server 2016 和 Windows Server 2012 R2 中自动包含此内容。 以前，.NET 3.5 Framework 是最低要求版本。
- NDES 证书连接器中包含 TLS 1.2 支持。 因此，如果已安装 NDES 证书连接器的服务器支持 TLS 1.2，则使用 TLS 1.2。 如果服务器不支持 TLS 1.2，则使用 TLS 1.1。 目前，TLS 1.1 用于设备和服务器之间的身份验证。

有关详细信息，请参阅[配置和使用 SCEP 证书](certificates-scep-configure.md)和[配置和使用 PKCS 证书](certficates-pfx-configure.md)。

## <a name="week-of-june-4-2018"></a>2018 年 6 月 4 日的这一周

### <a name="app-management"></a>应用管理

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>在展台模式下检索适用于企业的 Microsoft Store 应用相关联的应用用户模型 ID (AUMID) <!-- 1560077 ! -->
Intune 现在可以检索适用于企业的 Microsoft Store (WSfB) 应用的应用用户模型 ID，以改进展台配置文件的配置。

有关适用于企业的 Microsoft Store 应用的详细信息，请参阅[管理来自适用于企业的 Microsoft Store 应用](windows-store-for-business.md)。

#### <a name="new-company-portal-branding-page----1916370---"></a>新的公司门户品牌页 <!-- 1916370 -->
公司门户品牌页拥有新的布局、消息和工具提示。


### <a name="device-configuration"></a>设备配置

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680----"></a>支持 Palo Alto Networks GlobalProtect VPN 配置文件<!-- 1333680 ! -->
通过此更新，可选择 Palo Alto Networks GlobalProtect 作为 Intune 中 VPN 配置文件的 VPN 连接类型（“设备配置” > “配置文件” > “创建配置文件” > “配置文件类型” > “VPN”）。 在此版本中，支持以下平台： 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings----1403702---"></a>新增本地设备安全选项设置<!-- 1403702 -->
现在可以配置适用于 Windows 10 设备的其他本地设备安全选项设置。 其他设置在 Microsoft 网络客户端、Microsoft 网络服务器、网络访问和安全性和交互式登录的区域内可用。 创建 Windows 10 设备配置策略时，可以在终结点保护类别中查找这些设置。

#### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>在 Windows 10 设备上启用展台模式 <!-- 1560072 ! -->
在 Windows 10 设备上，可以创建配置文件并启用展台模式（“设备配置” > “配置文件” > “创建配置文件” > “Windows 10” > “设备限制” > “展台”）。 在此更新中，“展台(预览版)”设置被重命名为“展台(旧版)”。 不再推荐使用“展台(旧版)”，但该版本在 7 月更新之前仍能正常使用。 “展台(旧版)”被替换为新的“展台”配置文件类型（“创建配置文件” > “Windows 10” > “展台(预览版)”），该类型将包含配置 Windows 10 RS4 和更高版本上的展台的设置。

适用于 Windows 10 和更高版本。

#### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>设备配置文件图形用户图表已恢复 <!-- 2160133 -->
为了改进设备配置文件图形图表上显示的计数（“设备配置” > “配置文件”> 选择现有配置文件 >“概述”），图形用户图表曾被暂时删除。

在此更新中，图形用户图表得到恢复，并显示在 Azure 门户中。

### <a name="device-enrollment"></a>设备注册

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication----1165118-wnready---"></a>支持无需用户身份验证的 Windows Autopilot 注册 <!-- 1165118 wnready -->
Intune 现在支持无需用户身份验证的 Windows Autopilot 注册。 这是 Windows Autopilot 部署配置文件中的新选项，“Autopilot 部署模式”设置为“自部署”。  设备必须运行 Windows 10 Insider Preview 内部版本 17672 或更高版本并且具有 TPM 2.0 芯片，才能成功完成此类型的注册。 由于不需要用户身份验证，因此应仅将此选项分配给你具有物理控制权限的设备。

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766---"></a>配置 Autopilot 的 OOBE 时的新语言/区域设置 <!-- 1821766 -->
在 Out of Box Experience 期间，会提供新的配置设置，以设置 Autopilot 配置文件的语言和区域。 要查看新设置，请选择“设备注册” > “Windows 注册” > “部署配置文件” > “创建配置文件” > “部署模式” = “自部署” > “默认配置”。

#### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>配置设备键盘的新设置 <!-- 1821768 -->
在 Out of Box Experience 期间，将提供新的设置，以配置 Autopilot 配置文件的键盘。 要查看新设置，请选择“设备注册” > “Windows 注册” > “部署配置文件” > “创建配置文件” > “部署模式” = “自部署” > “默认配置”。

#### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>将 AutoPilot 配置文件移动到组目标<!-- 1877935 -->
AutoPilot 部署配置文件可以分配给包含 AutoPilot 设备的 Azure AD 组。

### <a name="device-management"></a>设备管理

#### <a name="set-compliance-by-device-location----851881----"></a>按设备位置设置符合性 <!-- 851881 ! -->
在某些情况下，你可能想要将访问企业资源的权限限制到某个特定位置（该位置由网络连接定义）。 现在可以基于设备的 IP 地址来创建符合性策略（“设备符合性” > “位置”）。 如果设备移动到 IP 范围以外，则该设备将无法访问企业资源。

适用于：拥有更新的公司门户应用的 Android 设备 6.0 及更高版本

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>在 Windows 10 企业版 RS4 AutoPilot 设备上阻止使用者应用和体验<!-- 1621980 -->
你将能够阻止在 Windows 10 企业版 RS4 AutoPilot 设备上安装使用者应用和体验。 要查看此功能，请转到“Intune” > “设备配置” > “配置文件” > “创建配置文件” > “平台” = “Windows 10 或更高版本” > “配置文件类型” = “设备限制” > “配置” > “Windows 聚焦” > “使用者功能”。 

#### <a name="uninstall-the-latest-from-windows-10-software-updates----1732948---"></a>从 Windows 10 软件更新中卸载最新版本 <!-- 1732948 -->
如果发现 Windows 10 计算机上存在重大问题，则可以选择卸载（回滚）最新的功能更新或最新的质量更新。 卸载某功能或质量更新仅适用于设备所在的服务通道。 卸载将触发恢复 Windows 10 计算机上的先前更新的策略。 特别是对于功能更新，可以限制卸载最新版本的时间（2-60 天）。 要设置软件更新卸载选项，请从 Azure 门户中的“Microsoft Intune ”边栏选项卡中选择“软件更新”。 然后，从“软件更新”边栏选项卡中选择“Windows 10 更新通道”。 然后，可以从“概述”部分选择“卸载”选项。

#### <a name="search-all-devices-for-imei-and-serial-number----1793685---"></a>搜索所有设备以获取 IMEI 和序列号 <!-- 1793685 -->
现在可以在“所有设备”边栏选项卡上搜索 IMEI 和序列号（电子邮件、UPN、设备名称和管理名称仍然可用）。 在 Intune 中，选择“设备” > “所有设备”> 在搜索框中输入你的搜索。

#### <a name="management-name-field-will-be-editable----1875989---"></a>管理名称字段将可编辑 <!-- 1875989 -->
现在可以在设备的“属性”边栏选项卡上编辑管理名称字段。 若要编辑此字段，请选择“设备” > “所有设备”> 选择设备 >“属性”。 可以使用管理名称字段来唯一标识设备。

#### <a name="new-all-devices-filter-device-category----1878520---"></a>新建所有设备筛选器：设备类别 <!-- 1878520 -->
现在可以按设备类别筛选“所有设备”列表。 为此，请选择“设备” > “所有设备” > “筛选器” > “设备类别”。

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>使用 TeamViewer 共享 iOS 和 MacOS 设备的屏幕 <!-- 1985547 -->
管理员现在可以连接到 [TeamViewer](device-profile-android-teamviewer.md)，并启动与 iOS 和 macOS 设备之间的屏幕共享会话。 iPhone、iPad 和 macOS 用户可以与任何其他桌面或移动设备实时共享其屏幕。 

#### <a name="multiple-exchange-connector-support----2070451---"></a>多个 Exchange Connector 支持<!-- 2070451 -->
你不再受到每租户一个 Microsoft Intune Exchange Connector 的限制。 Intune 现在支持多个 Exchange Connector，你可以设置多个本地 Exchange 组织的 Intune 条件访问。

凭借 Intune 本地 Exchange 连接器，可以根据设备是否已在 Intune 中注册且是否符合 Intune 设备符合性策略来管理设备对本地 Exchange 邮箱的访问。 若要设置连接器，请从 Azure 门户下载 Intune 本地 Exchange 连接器，并将它安装在 Exchange 组织中的服务器上。 在 Microsoft Intune 仪表板上，选择“本地访问”，然后在“设置”下选择“Exchange ActiveSync 连接器”。 下载 Exchange 本地连接器，并将它安装在 Exchange 组织中的服务器上。 由于你已经不再受到每租户一个 Exchange 连接器的限制，因此，如果拥有其他的 Exchange 组织，则可以按照此相同的过程为其他每个 Exchange 组织下载并安装连接器。

#### <a name="new-device-hardware-detail-ccid----2156657---"></a>新的设备硬件详细信息：CCID <!-- 2156657 -->
现在每台设备均包含芯片卡接口设备 (CCID) 信息。 要查看该信息，请选择“设备” > “所有设备”> 选择一台设备 >“硬件”> 在“网络详情”下查看>

#### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>将所有用户和所有设备分配为范围组 <!-- 2196803 -->
现在可以分配所有用户、所有设备，以及范围组中的所有用户和所有设备。 要执行此操作，请选择“Intune 角色” > “所有角色” > “策略和配置文件管理器” > “分配”> 选择一项分配 >“范围(组)”。

#### <a name="udid-information-now-included-for-ios-and-macos-devices----2219806-wnready--"></a>现包括 iOS 和 macOS 设备的 UDID 信息 <!-- 2219806 wnready-->
要查看适用于 iOS 和 macOS 设备的唯一设备标识符 (UDID)，请转到“设备” > “所有设备”> 选择一台设备 >“硬件”。 UDID 仅适用于公司设备（如“设备” > “所有设备”> 选择一台设备 >“属性” > “设备所有权”下的设置）。

### <a name="intune-apps"></a>Intune 应用

#### <a name="improved-troubleshooting-for-app-installation----928990---"></a>改进了对应用安装的故障排除 <!-- 928990 -->
在 Microsoft Intune MDM 托管的设备上，有时应用安装可能会失败。 当这些应用安装失败时，可能难以了解失败原因或解决此问题。 我们将发布我们的应用疑难解答功能的公共预览版。 你将在每个设备下注意到名为“托管应用”的新节点。 该节点列出了通过 Intune MDM 提供的应用。 在该节点内，将看到应用安装状态的列表。 如果选择单个应用，将看到该特定应用的疑难解答视图。 在疑难解答视图中，将看到应用的端到端生命周期，例如，应用创建、修改、设为目标和提供给设备的时间。 此外，如果应用安装失败，将向你显示错误代码以及有有助于了解错误原因的消息。 

#### <a name="intune-app-protection-policies-and-microsoft-edge----1818968---"></a>Intune 应用保护策略和 Microsoft Edge <!-- 1818968 -->
移动设备（iOS 和 Android）的 Microsoft Edge 浏览器现在支持 Microsoft Intune 应用保护策略。 在 Microsoft Edge 应用程序中使用其企业 Azure AD 帐户登录的 iOS 和 Android 设备用户将受 Intune 保护。 在 iOS 设备上，“需要使用托管浏览器获取 Web 内容”的策略允许用户在托管的 Microsoft Edge 中打开链接。

## <a name="week-of-may-14-2018"></a>2018 年 5 月 14 日当周

### <a name="app-management"></a>应用管理

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>需要安装策略、应用、证书和网络配置文件<!-- 1553555 -->

除非 Intune 在 AutoPilot 设备预配期间安装策略、应用、证书和网络配置文件，否则管理员将能够阻止最终用户访问 Windows 10 RS4 桌面。 有关详细信息，请参阅[设置注册状态页](windows-enrollment-status.md)。

#### <a name="configuring-your-app-protection-policies----2144597-part-2---"></a>配置应用保护策略<!-- 2144597 Part 2 -->

在 Azure 门户中，现在只需转到 Intune，而不是转到 Intune 应用保护服务边栏选项卡。 Intune 中现在只有一个应用保护策略位置。 请注意，所有应用保护策略都位于 Intune 中“移动应用”边栏选项卡上的“应用保护策略”下。 此集成将有助于简化云管理。 请记住，Intune 中已具备所有应用保护策略，并且你可以修改先前配置的任何策略。 Intune 应用策略保护 (APP) 和条件访问 (CA) 策略现在位于“Microsoft Intune”边栏选项卡中“管理”部分的“条件访问”下，或“Azure Active Directory”边栏选项卡中“安全性”部分的“条件访问”下。 有关修改条件访问策略的详细信息，请参阅 [Azure Active Directory 中的条件性访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)。 有关其他信息，请参阅[什么是应用保护策略？](app-protection-policy.md)

## <a name="week-of-may-7-2018"></a>2018 年 5 月 7 日的这一周

### <a name="app-management"></a>应用管理

#### <a name="samsung-knox-mobile-enrollment-support---1112863--"></a>Samsung Knox 移动注册支持 <!--1112863-->

将 Intune 与 Samsung Knox 移动注册 (KME) 结合使用时，可以注册大量公司拥有的 Android 设备。 使用 WiFi 或移动电话网络的用户在第一次打开他们的设备时，只需几次点击即可进行注册。 在使用 Knox 部署应用时，可使用蓝牙或 NFC 注册设备。 有关详细信息，请参阅[使用 Samsung 的 Knox 移动注册自动注册 Android 设备](android-samsung-knox-mobile-enroll.md)。

#### <a name="requesting-help-in-the-company-portal-for-windows-10----1874137---"></a>在 Windows 10 公司门户上请求帮助<!-- 1874137 -->

当用户启动获取问题的帮助的工作流时，Windows 10 公司门户现在将直接向 Microsoft 发送应用日志。 这样一来，可以更为轻松地排除和解决向 Microsoft 提出的问题。

## <a name="week-of-april-23-2018"></a>2018 年 4 月 23 日当周

### <a name="app-management"></a>应用管理

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Android 上对 MAM PIN 的密码支持<!-- 1438086 -->

Intune 管理员能够设置应用程序启动要求以强制使用密码而不是数字 MAM PIN。 如果进行此配置，在访问启用 MAM 的应用程序前，用户需要在出现提示时设置并使用密码。 密码是至少包含一个特殊字符或大写/小写字母的数字 PIN。 Intune 对密码的支持与支持现有数字 PIN 类似，可通过管理员控制台设置最短长度并且允许重复字符和序列。 此功能需要最新版 Android 公司门户。 此功能已可应用于 iOS。

#### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>对 macOS 的业务线 (LOB) 应用支持 <!-- 1473977 -->
Microsoft Intune 将提供从 Azure 门户安装 macOS LOB 应用的功能。 使用 GitHub 中提供的工具对 macOS LOB 应用进行预处理后，可以将该应用添加到 Intune。 在 Azure 门户的“Intune”边栏选项卡中，选择“客户端应用”。 在“客户端应用”边栏选项卡上，选择“应用” > “添加”。 在“添加应用”边栏选项卡，选择“业务线应用”。 

#### <a name="built-in-all-users-and-all-devices-group-for-android-enterprise-work-profile-app-assignment----1813073---"></a>面向 Android Enterprise 工作配置文件应用分配的内置“所有用户”和“所有设备”组 <!-- 1813073 -->
可以利用面向 Android Enterprise 工作配置文件应用分配的内置“所有用户”和“所有设备”组。 有关详细信息，请参阅[在 Microsoft Intune 中包括和排除应用分配](apps-inc-exl-assignments.md)。

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>Intune 将重新安装用户卸载的所需应用 <!-- 1947010 -->
如果最终用户卸载所需应用，Intune 将在 24 小时内自动重新安装该应用，而不是等待 7 天的重新评估周期。

### <a name="device-configuration"></a>设备配置

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153---"></a>设备配置文件图表和状态列表将显示组中的所有设备<!-- 1449153 -->
配置设备配置文件（“设备配置” > “配置文件”）时，选择设备配置文件，如 iOS。 将此配置文件分配到包括 iOS 设备和非 iOS 设备的组。 图形图表显示应用到 iOS 和非 iOS 设备的配置文件计数（“设备配置” > “配置文件”> 选择一个现有配置文件 >“概述”）。 选择“概述”选项卡中的图形图表时，“设备状态”将列出组中的所有设备，而不仅仅是 iOS 设备。 

此次更新后，图形图表（“设备配置” > “配置文件”>选择一个现有配置文件>“概述”）将仅显示特定设备配置文件的计数。 例如，如果配置设备配置文件应用于 iOS 设备，则图表仅列出 iOS 设备的计数。 选中图形图表并打开“设备状态”后，将仅列出 iOS 设备。

当此更新正在进行时，用户图形图表将暂时删除。 

#### <a name="always-on-vpn-for-windows-10---1333666---"></a>适用于 Windows 10 的 Always On VPN<!--1333666 -->

目前，通过使用自定义虚拟专用网络 (VPN) 配置文件（使用 OMA-URI 创建），可在 Windows 10 设备上使用 [Always On](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on)。

此次更新后，管理员可以在 Azure 门户中的 Intune 中直接面向 Windows 10 VPN 配置文件启用 Always On。 Always On VPN 配置文件将在以下情况下自动连接：

- 用户登录其设备
- 设备上的网络发生更改
- 设备屏幕在关闭后重新打开

#### <a name="new-printer-settings-for-education-profiles----1308900---"></a>教育配置文件的新打印机设置 <!-- 1308900 -->

对于教育配置文件，新的设置在“打印机”类别下可用：“打印机”、“默认打印机”、“添加新的打印机”。

#### <a name="show-caller-id-in-personal-profile---android-enterprise-work-profile---1098984---"></a>在个人资料中显示呼叫方 ID - Android Enterprise 工作配置文件 <!--1098984 -->
在设备上使用个人资料时，最终用户可能不会看到工作联系人的呼叫方 ID 详细信息。 

进行此更新后，“Android Enterprise” > “设备限制” > “工作配置文件设置”中将出现新设置：
- 在个人资料中显示工作联系人呼叫方 ID

启用（不配置）后，工作联系人的呼叫方详细信息将显示在个人资料中。 阻止后，工作联系人的呼叫方号码不会显示在个人资料中。 

适用范围：Android OS v6.0 和更高版本的 Android 工作配置文件设备

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>添加到 Endpoint Protection 设置的新 Windows Defender Credential Guard 设置<!--1102252 --><!--from 1802 and 1804-->

此次更新后，[Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard)（“设备配置” > “配置文件” > “Endpoint Protection”）将包括以下设置： 

- Windows Defender Credential Guard：以基于虚拟化的安全性启用 Credential Guard。 启用此功能可帮助在下次同时启用“使用安全启动的平台安全级别”和“基于虚拟化的安全性”而重新启动时保护凭据。 选项包括：
  - 禁用：如果之前已使用“无锁启用”选项启用 Credential Guard，则会远程关闭 Credential Guard。

  - 使用 UEFI 锁启用：可确保 Credential Guard 不能使用注册表项或使用组策略禁用。 若要使用此设置来禁用 Credential Guard，必须将组策略设置为“禁用”。 然后，与实际存在的用户一起，从每台计算机中删除安全功能。 这些步骤清除保留在 UEFI 中的配置。 只要 UEFI 配置仍然存在，Credential Guard 就会保持启用状态。

  - 无锁启用：允许使用组策略远程禁用 Credential Guard。 使用此设置的设备必须至少在 Windows 10（版本 1511）上运行。

配置 Credential Guard 时，会自动启用以下相关技术： 

  - 启用基于虚拟化的安全性 (VBS)：在下次重新启动时启用基于虚拟化的安全性 (VBS)。 基于虚拟化的安全性使用 Windows 虚拟机监控程序提供对安全服务的支持，并要求“安全启动”。
  - 安全启动和直接内存访问 (DMA)：通过“安全启动”和直接内存访问启用 VBS。 DMA 保护需要硬件支持，并且仅在正确配置的设备上启用。 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>对 SCEP 证书使用自定义使用者名称<!-- 2064190 -->
可以使用“OnPremisesSamAccountName”作为 SCEP 证书配置文件中自定义使用者的公用名称。 例如，你可以使用 `CN={OnPremisesSamAccountName})`。

####  <a name="block-camera-and-screen-captures-on-android-enterprise-work-profiles----1098977---"></a>在 Android Enterprise 工作配置文件上阻止照相机和屏幕捕获 <!-- 1098977 -->
配置 Android 设备的设备限制时，可以阻止两个新属性： 
- 照相机：阻止访问设备上的所有照相机
- 屏幕捕获：阻止屏幕捕获，还会阻止在不具有安全视频输出的显示设备上显示内容

适用于 Android Enterprise 工作配置文件。


### <a name="device-enrollment"></a>设备注册

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>用户在使用 macOS High Sierra 10.13.2+ 的设备上的新注册步骤<!--1734567 -->
macOS High Sierra 10.13.2 引入了“用户批准的”MDM 注册的概念。 批准的注册将允许 Intune 管理某些安全敏感设置。 有关详细信息，请参阅此处的 Apple 支持文档： https://support.apple.com/HT208019。

如果最终用户未打开“系统首选项”并手动批准，使用 macOS 公司门户注册的设备将被视为“未经用户批准”。 为此，macOS 公司门户现直接在注册过程末尾指示使用 macOS 10.13.2 及以上版本的用户手动批准注册。 Intune 管理员控制台将就注册设备的用户批准情况进行报告。



### <a name="device-management"></a>设备管理

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----1629303---"></a>高级威胁防护 (ATP) 和 Intune 完全集成 <!-- 1629303 -->

[高级威胁防护 (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) 显示 Windows 10 设备的风险级别。 在 Windows Defender 安全中心（ATP 门户）中，可以创建到 Microsoft Intune 的连接。 创建后，将使用 Intune 符合性策略确定可接受的威胁级别。 如果超出威胁级别，则 Azure Active Directory (AD) 条件访问策略可以阻止访问组织内的不同应用。

此功能使 ATP 能够扫描文件、检测威胁并报告 Windows 10 设备上的任何风险。

请参阅[在 Intune 中启用具有条件访问的 ATP](advanced-threat-protection.md)。

#### <a name="support-for-user-less-devices----1637553---"></a>对无用户设备的支持<!-- 1637553 -->
Intune 支持在无用户设备（如 Microsoft Surface Hub）上评估符合性的功能。 符合性策略可以面向特定设备。 这样可以确定不具有关联用户的设备的符合性（和不符合性）。

#### <a name="delete-autopilot-devices----1713650---"></a>删除 AutoPilot 设备<!-- 1713650 -->
Intune 管理员可以[删除 AutoPilot 设备](enrollment-autopilot.md#delete-autopilot-devices)。

#### <a name="improved-device-deletion-experience---1832333---"></a>设备删除体验改进<!--1832333 -->
[删除 Intune 中的设备](devices-wipe.md#delete-devices-from-the-intune-portal)前，将不再需要删除公司数据或将设备恢复出厂设置。

要感受新体验，请登录 Intune，选择“设备” > “所有设备”> 设备的名称 >“删除”。

如果仍希望确认擦除/停用，可使用标准设备生命周期流程，即在“删除”前执行“删除公司数据”和“恢复出厂设置”。 

#### <a name="play-sounds-on-ios-when-in-lost-mode----1947769---"></a>“丢失”模式下在 iOS 上播放声音<!-- 1947769 -->
当受监督的 iOS 设备处于移动设备管理 (MDM)[丢失模式](device-lost-mode.md)时，可以[播放声音](device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device)（“设备” > “所有设备”>选择一个 iOS 设备 >“概述” > “更多”）。 声音将持续播放，直到将该设备移除“丢失”模式或用户在该设备上禁用声音。 适用于 iOS 9.3 和更高版本的设备。

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device---1972804--"></a>阻止或允许在 Intune 设备上所执行的搜索中出现 Web 结果 <!--1972804-->

管理员现在可以阻止在设备上所执行的搜索中出现 Web 结果。

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>针对 Apple MDM Push Certificate 上传失败的错误消息改进<!-- 2172331 -->

错误消息说明，续订现有 MDM 证书时必须使用相同 Apple ID。

#### <a name="test-the-company-portal-for-macos-on-virtual-machines----2216679---"></a>测试虚拟机上的 macOS 公司门户 <!-- 2216679 -->

我们已发布指南来帮助 IT 管理员在 Parallels Desktop 和 VMware Fusion 的虚拟机上测试 macOS 公司门户应用。 有关详细信息，请参阅[注册用于测试的虚拟 macOS 计算机](macos-enroll.md#enroll-virtual-macos-machines-for-testing)。


### <a name="user-interface"></a>用户界面

#### <a name="improved-device-tiles-in-the-windows-10-company-portal---2213364---"></a>改进了 Windows 10 公司门户中的设备磁贴 <!--2213364 -->

已对这些磁贴进行了更新，以便弱视用户更易于访问，并且可以更好地为屏幕阅读工具提供服务。

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>在 macOS 公司门户应用中发送诊断报告<!-- 2216677 -->
更新了适用于 macOS 设备的公司门户应用，以改进用户报告 Intune 相关错误的方式。 员工可从公司门户应用中：

- 将诊断报告直接上传给 Microsoft 开发人员团队。
- 通过电子邮件将事件 ID 发送给公司的 IT 支持团队。

有关详细信息，请参阅[发送 macOS 错误](/intune-user-help/send-errors-macos)。

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010-wnready---"></a>Intune 适用于 Windows 10 公司门户应用中的 Fluent 设计系统 <!-- 1195010 WNready -->
Windows 10 Intune 公司门户应用已更新 [Fluent 设计系统的导航视图](https://docs.microsoft.com/windows/uwp/design/basics/navigation-basics)。 在这款应用旁边，你会注意到一个静态、垂直的所有顶级页面列表。 单击任意链接，可以快速查看页面并在其之间进行切换。 这是你将看到的众多更新中的第一个更新，是我们持续不断努力成果的一部分，以便在 Intune 中创造更具适应性、更能感同身受且更为熟悉的体验。 若要查看更新后的外观，请转到[应用 UI 中的新增功能](whats-new-app-ui.md)。

## <a name="week-of-april-16-2018"></a>2018 年 4 月 16 日当周

#### <a name="use-cisco-anyconnect-client-for-ios----1333708---"></a>对 iOS 使用 Cisco AnyConnect 客户端 <!-- 1333708 -->

为 iOS 创建新的 VPN 配置文件时，现在提供两个选项：Cisco AnyConnect 和 Cisco Legacy AnyConnect。 Cisco AnyConnect 配置文件支持 4.0.7x 和更新版本。 现有 iOS Cisco AnyConnect VPN 配置文件将被标记为“Cisco Legacy AnyConnect”，并将继续适用于 Cisco AnyConnect 4.0.5x 和较旧版本，如现在一样。

> [!NOTE]
> 此更改仅适用于 iOS。 将继续只提供一个适用于 Android、Android Enterprise 工作配置文件和 macOS 平台的 Cisco AnyConnect 选项。

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>Jamf 注册的 macOS 设备现在可以向 Intune 注册<!-- 2370684 -->

macOS 公司门户版本 1.3 和 1.4 未成功向 Intune 注册 Jamf 设备。 macOS 门户版本 1.4.2 可修复此问题。


## <a name="week-of-april-9-2018"></a>2018 年 4 月 9 日当周  
#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>更新了 Android 适用的公司门户应用的帮助体验<!-- 1631531 -->

我们更新了 Android 适用的公司门户应用中的帮助体验，使其符合 Android 平台的最佳做法。 现在如果在使用应用时遇到问题，用户可以点击“菜单” > “帮助”，然后进行以下操作：
- 将诊断日志上传到 Microsoft。
- 向公司支持人员发送内含问题描述和事件 ID 的电子邮件。  

如需查看更新后的帮助体验，请转到[使用电子邮件发送日志](/intune-user-help/send-logs-to-your-it-admin-by-email-android)和[向 Microsoft 发送错误](/intune-user-help/send-logs-to-microsoft-android)。


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>新的注册失败趋势图表和失败原因表<!-- 1471783 -->

“注册概述”页中会显示注册失败趋势和前五个失败原因。 单击图表或表可查看详细信息，以查找故障排除建议和修正建议。

#### <a name="update-where-to-configure-your-app-protection-policies----2144597---"></a>更新配置应用保护策略的位置<!-- 2144597 -->

在 Microsoft Intune 服务的 Azure 门户中，我们会将“Intune 应用保护”服务边栏选项卡暂时重定向到“移动应用”边栏选项卡。 请注意，Intune 中“应用配置”下的“移动应用”边栏选项卡已包括所有应用保护策略。 直接转到 Intune 即可，无需转到“Intune 应用保护”。 在 2018 年 4 月，我们将停止重定向并将完全删除“Intune 应用保护服务”边栏选项卡，以便在 Intune 中只存在应用保护策略的一个位置。 

**这会对我产生哪些影响？**
此更改将同时影响 Intune 独立版客户和混合版（带 Configuration Manager 的 Intune）客户。 此集成将有助于简化云管理。

**我需要如何准备应对此项变化？**
请将 Intune 标记为收藏（而不是“Intune 应用保护”服务边栏选项卡），并确保熟悉 Intune 的“移动应用”边栏选项卡中的应用保护策略工作流。 我们将重定向一小段时间，然后删除“应用保护”边栏选项卡。 请记住，Intune 中已具备所有应用保护策略，并且你可以修改任何条件访问策略。 有关修改条件访问策略的详细信息，请参阅 [Azure Active Directory 中的条件性访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)。 有关其他信息，请参阅[什么是应用保护策略？](app-protection-policy.md) 


## <a name="week-of-april-2-2018"></a>2018 年 4 月 2 日当周

### <a name="intune-apps"></a>Intune 应用

#### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866---"></a>iOS 版公司门户应用的用户体验更新<!--1412866 -->
我们向 iOS 版公司门户应用发布了用户体验主要更新。 此更新具有经过完全重新设计的视觉效果，包括现代化的外观。 我们保留了应用的功能，但提高了其可用性和可访问性。  

你还会看到：
- 对 iPhone X 的支持。
- 应用启动速度和响应加载速度更快，可节省用户时间。
- 可为用户提供最新状态信息的附加进度条。
- 改进了用户上传日志的方式，因此可在出现问题时更轻松地报告该问题。  

若要查看更新后的外观，请转到[应用 UI 中的新增功能](whats-new-app-ui.md)。

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca----1056954---"></a>使用 Intune APP 和 CA 保护本地 Exchange 数据<!-- 1056954 -->
现在可以使用 Intune 应用策略保护 (APP) 和条件访问 (CA) 保护通过 Outlook Mobile 对本地 Exchange 数据的访问权限。 若要在 Azure 门户中添加或修改应用保护策略，请选择“Microsoft Intune” > “客户端应用” > “应用保护策略”。 使用此功能之前，请确保满足[适用于 iOS 和 Android 的 Outlook 要求](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx)。

## <a name="notices"></a>通知

### <a name="plan-for-change-performance-updates-to-intune-for-education---1750215--"></a>更改计划：Intune for Education 的性能更新 <!--1750215-->
我们将为 Intune for Education 添加一些更新，以便在为用户或设备分配设置时提高速度和可靠性。 作为此更改的一部分，到 11 月底，我们会将你的策略或设置分配移动到新组。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？

Intune for Education 客户有两个动态的 Azure Active Directory (Azure AD) 组：“所有用户”和“所有设备”。 进行这些更新之后，“所有用户”和“所有设备”Azure AD 组将不会在 Intune for Education 控制台中可见。 但是，它们仍将在 Azure 上的 Intune 控制台中可见，并将重命名为“所有用户(已过时，请勿使用)”和“所有设备(已过时，请勿使用)”。

更新推出后，将不再需要使用 Azure AD 组在 Intune 中分配应用和设置。 相反，我们会将设置分配移动到我们将为你创建的 Intune for Education 控制台中的新组，这些组仍将像以前一样显示为“所有用户”和“所有设备”。 这些更改在后端进行，因此你在 Intune for Education 控制台中看到的内容不会有任何变化。 最终用户或已注册设备不会受到任何影响。 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
在我们移动策略分配时，你无需执行任何操作。 如果你当前在 Intune for Education 控制台中分配策略，请继续执行此操作。

如果当前将策略分配给 Azure 上的 Intune 中提到的 Azure AD 组，请将这些策略分配给 Intune for Education 控制台中的“所有用户”和“所有设备”组。 当在控制台中看到 Azure AD 组已重命名为已过时时，请停止在 Azure AD 中分配策略。 如果当前没有将重命名的组用于任何其他目的，则应将其删除。


### <a name="plan-for-change-intune-will-move-to-support-macos-1012-and-higher-in-december---2970975--"></a>更改计划：Intune 将于 12 月支持 macOS 10.12 及更高版本 <!--2970975--> 

Apple 刚刚发布了 macOS 10.14。 随后，Intune 将于 2018 年 12 月支持 macOS 10.12 及更高版本。 

#### <a name="how-does-this-affect-me"></a>这对我有何影响？

从 12 月开始，使用 macOS 10.11 及更早版本的设备上的最终用户将无法使用公司门户注册 Intune。 他们需要将设备升级到 macOS 10.12 或更高版本，并将公司门户应用升级到最新版本，以继续获得支持和新功能。 

当前支持 macOS 10.12 和更高版本的设备有： 
- MacBook（2009 后期版本或更高版本）。 
- iMac（2009 后期版本或更高版本）
- MacBook Air（2010 后期版本或更高版本）。  
- MacBook Pro（2010 后期版本或更高版本）。 
- Mac Mini（2010 后期版本或更高版本）。 
- Mac Pro（2010 后期版本或更高版本）。 

12 月以后，未使用上述设备的最终用户将无法访问最新版本的 macOS 公司门户应用。 运行 macOS 10.12 以下不受支持版本的现有已注册设备将继续由 Intune 管理控制台进行管理并在其中列出。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？

- 要求最终用户在 2018 年 12 月前将其设备升级到支持的 OS 版本。 
- 检查 Azure 控制台上的 Intune 中的 Intune 报告，查看哪些设备或用户可能会受到影响。 转到“设备”>“所有设备”并按 OS 进行筛选。 可以添加其他列，帮助确定组织中哪些人员拥有运行 macOS 10.11 的设备。 
- 如果使用的是混合移动设备管理 (MDM)，请转到 Configuration Manager 控制台中的“资产和符合性”>“设备”，右键单击这些列以添加“操作系统”和“客户端版本”列，然后按 OS 排序。 请注意，混合 MDM 现已弃用，应尽快迁移到 Azure 上的 Intune。 
 
#### <a name="additional-information"></a>其他信息
有关详细信息，请参阅[使用公司门户应用在 Intune 中注册 macOS 设备](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos-cp)。
 

### <a name="plan-for-change-new-intune-support-experience-for-premier-customers"></a>更改计划：针对顶级客户的新 Intune 支持体验 
作为 Microsoft 顶级客户，你当前可以使用 Microsoft Premier Online (MPO) 门户 (premier.microsoft.com) 和 Intune on Azure (portal.azure.com) 为 Intune 创建支持请求。 从 2018 年 12 月 3 日起，为了继续增强顶级支持体验，你将仅能在 Intune on Azure 中创建支持请求。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
在 12 月 3 日后，你将无法在 MPO 中创建支持请求。  当你尝试执行此操作时，你将看到一个不能解除的提示，以重定向到 Intune on Azure。 在此处，你可以创建一个将被路由到 Intune 专用的 Microsoft 支持的支持请求，以及时诊断和解决你的问题。 无法在 Azure 门户中查看在 MPO 门户中创建的支持请求，因此，应停止在 MPO 中创建支持请求。  

如果你使用混合移动设备管理（混合 MDM）或使用共同管理，你可以继续使用 MPO 为 ConfigMgr 创建支持请求，但使用 Azure 门户为 Intune 创建支持请求。 提醒一下，混合 MDM 已被弃用，应计划尽快移动到 Intune on Azure。 有关详细信息，请参阅[从混合移动设备管理移动到 Azure 上的 Intune](https://aka.ms/hybrid_notification)。

请注意，只有具有全局管理员、Intune 服务管理员和服务支持管理员角色的用户才能在 Azure 门户中创建支持票证。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我能够针对此更改做什么准备？
- 停止使用 MPO，并使用 Intune on Azure 来创建和管理所有你的 Intune 支持请求。  
- 如有必要，请通知你的支持人员并更新文档。
- 如果你有用户（不具有全局管理员或 Intune 服务管理员角色）当前正在 MPO 中创建支持请求，则在 Azure Active Directory 中向其分配服务支持管理员角色，以使其能够在 Azure 门户中继续创建支持票证。
- 单击“其他信息”以获取详细信息和有用的链接。

#### <a name="additional-information"></a>其他信息
有关详细信息，请参阅 [Microsoft Intune 支持团队博客文章](https://aka.ms/IntuneSupport_MPO_to_Azure)。


### <a name="take-action-please-update-your-android-device-restriction-or-compliance-policy-password-settings-in-intune"></a>执行操作：请在 Intune 中更新 Android 设备限制或符合性策略密码设置
Intune 将删除 Android 4.4 及更高版本设备的可用密码类型“设备默认值”。 由于 Android 平台和设备默认值的差异，该策略通常被设备视为可选策略。 为了消除在 Android 上强制执行此设置时造成的混淆，我们会在即将发布的版本中将此设置从 UI 中删除。 
#### <a name="how-does-this-affect-me"></a>这对我有何影响？
- 如果要求必须在设备上输入密码，我们建议编辑 Android 平台配置文件来清楚表达所需的密码类型，而不是使用“设备默认值”。
- 如果打算让最终用户决定是否创建密码，请选择“未配置”按钮。 我们从 UI 删除此设置时，如果仍设置了该设置，系统会在下次编辑配置文件时提示选择“设备默认值”以外的值。
我需要针对此更改做什么准备？
查看 Android 和 Android 企业设备限制和符合性策略中的密码设置。 这些设置列于“符合性策略的系统安全性”下以及“设备密码”或“设备限制的工作配置文件设置”下。 其他信息包含一个链接，指向配置这些设置的位置的详细信息和屏幕截图。
#### <a name="additional-information"></a>其他信息
https://aka.ms/PasswordSettings 

### <a name="plan-for-change-change-password-at-next-auth-added-to-intune---1873216---"></a>更改计划：向 Intune 中添加“在下一次身份验证时更改密码”<!-- 1873216 -->
在 9 月服务版本中，Intune 计划纳入 Apple 新发布的“在下一次身份验证时更改密码”设置，该设置适用于运行 macOS 10.13 版和更高版本的设备。 在纳入此设置之前，MDM 提供商无法验证设备密码是否已更改为符合规定的密码。 Intune 的配置和符合性策略只验证在下一次更改设备密码后是否将其标记为符合规定。 添加此新的 Apple 功能后，macOS 用户会收到更新密码的请求，即使其密码已符合规定。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
这会影响使用 macOS 设备策略并使用 Intune 或混合 MDM 的环境。 现在 Apple 增添了此项“在下一次身份验证时更改密码”设置，Intune 可在推送密码策略时强制用户更新其密码。 如果设置为阻止访问公司资源直到访问设备被标记为符合规定为止，那么最终用户可能需要在重置密码以后才能访问公司资源，如电子邮件或 SharePoint 站点。 在将来，每当更新配置和符合性密码策略时，都会强制目标用户更新其密码。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
让支持人员知晓。 如果不想强制实施此 macOS 设备策略，建议取消分配或删除现有 macOS 策略。 客户研究表明，大多数客户不受此更改影响。 大多数最终用户在收到“使用密码进行注册或重置其密码以保持符合性”的请求后都会更新其密码。

### <a name="plan-for-change-intune-moving-to-tls-12"></a>更改计划：Intune 将移动到 TLS 1.2
从 2018 年 10 月 31 日 开始，Intune 将支持可提供同类最佳加密的传输层安全性 (TLS) 协议版本 1.2，以确保我们的服务在默认情况下更加安全，并与 Microsoft Office 365 等其他 Microsoft 服务保持一致。 Office 已在 MC128929 中传达了此更改。

公司门户也将于 2018 年 10 月 31 日支持 TLS 1.2。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
从 2018 年 10 月 31 日开始，Intune 将不再支持 TLS 协议版本 1.0 或 1.1。 所有客户端-服务器和浏览器-服务器组合应使用 TLS 版本 1.2，以确保顺利连接到 Intune。 请注意，此更改将影响不再受 Intune 支持但仍可通过 Intune 接收策略以及不能使用 TLS 版本 1.2 的最终用户设备。 其中包括运行 Android 4.3 及更低版本的设备。 有关受影响设备和浏览器的列表，请参阅下面的“其他信息”。

2018 年 10 月 31 日之后，如果遇到与使用旧版 TLS 相关的问题，将需要更新到 TLS 1.2，或使用支持 TLS 1.2 的设备才可解决。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
我们建议主动删除环境中的 TLS 1.0 和 1.1 依赖项，并尽量在操作系统级别禁用 TLS 1.0 和 1.1。 立即开始针对迁移到 TLS 1.2 进行规划。 请查看下面的支持博客文章，获取 Intune 现在不支持但仍可接收策略以及未来将无法使用 TLS 版本 1.2 进行通信的设备的列表。 可能需要通知那些最终用户，他们即将失去对公司资源的访问权限。

**其他信息**：[Intune moving to TLS 1.2 for encryption](https://blogs.technet.microsoft.com/intunesupport/2018/06/05/intune-moving-to-tls-1-2-for-encryption/)（将 Intune 移动到 TLS 1.2 以进行加密）


### <a name="plan-for-change-use-intune-on-azure-now-for-your-mdm-management----1227338---"></a>更改计划：立刻使用 Azure 上的 Intune 进行 MDM 管理<!-- 1227338 -->
一年前，我们推出了 [Azure 上 Intune 的公共预览版](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/)，六个月前，我们推出了 Intune [新管理员体验的正式版](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/)。 自 2018 年 8 月 31 日起，我们将面向使用 Intune 独立版的客户关闭经典 Silverlight 控制台中的移动设备管理 (MDM)。 但客户可以使用 [Azure 上的 Intune](https://aka.ms/Intune_on_Azure) 满足 MDM 需求。 如果仍在使用经典控制台进行 MDM，请停止此做法并开始熟悉 Azure 上的 Intune。 我们不希望任何最终用户受到此次更改的影响。 Silverlight 中将保留经典电脑管理。 可在[此处](https://aka.ms/Intune_on_Azure_mdm)详细了解此次更改及其带来的影响。

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 将要求更新应用传输安全<!--748318-->
Apple 宣布他们将强制对应用程序传输安全 (ATS) 实施特定要求。 使用 ATS 对所有通过 HTTPS 的应用通信实施更严格的安全措施。 此更改会影响使用 iOS 公司门户应用的 Intune 客户。 我们将在 [Intune 支持博客](https://aka.ms/compportalats)中介绍详细信息。



## <a name="see-also"></a>另请参阅
* [Microsoft Intune 博客](http://go.microsoft.com/fwlink/?LinkID=273882)
* [云平台路线图](https://www.microsoft.com/cloud-platform/roadmap)
* [What's new in the Company Portal UI](whats-new-app-ui.md)（公司门户 UI 新增功能）
* [前几个月的新增功能](whats-new-archive.md)
