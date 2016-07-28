---
title: "配置策略参考 | Microsoft Intune"
description: "通过本主题中的信息可帮助你确定管理设备所需要使用的 Microsoft Intune 策略。"
keywords: 
author: robstackmsft
manager: arob98
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d27f2739-9791-4aae-a9db-01a4e59ccfe5
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a409d36c1c5fcfd3d81ce0cbdf1f69af4747157a
ms.openlocfilehash: cce19141ef25a8cca785d6ae80d1fe03ab352a8e


---

# Microsoft Intune 策略参考

通过本主题中的信息可帮助你确定管理设备所需要使用的 Microsoft Intune 配置策略。

> [!TIP]
> 有关如何使用策略的详细信息，请参阅[使用 Microsoft Intune 策略管理设备上的设置和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)。


## Android 配置策略

|策略名称|在你想要完成以下事项时使用:|
|---------------|------------------------|
|**自定义配置（Android 4 及更高版本，Samsung KNOX 标准版 4.0 及更高版本）**|部署 OMA-URI 设置，例如可用于控制设备功能的 Wi-Fi 设置。 这在配置策略不提供你需要的设置时十分有用。<br /><br />有关详细信息，请参阅[Microsoft Intune 中的 Android 策略设置](android-policy-settings-in-microsoft-intune.md)。|
|**电子邮件配置文件（Samsung KNOX 标准版 4.0 及更高版本）**|创建、部署和监视托管设备上的 Exchange Active Sync 电子邮件设置。 这样一来，用户无需进行特殊设置，就能通过个人设备访问企业电子邮件。<br /><br />有关详细信息，请参阅[使用 Microsoft Intune 的电子邮件配置文件配置对公司电子邮件的访问](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)。|
|**常规配置（Android 4 及更高版本、Samsung KNOX 标准版 4.0 及更高版本）**|配置移动设备安全设置和功能设置。<br />指定相容或不相容的应用，并在使用这些应用时进行报告。<br />配置锁定设备为只允许某些功能运行的展台模式，例如，允许设备只运行一个应用或禁用音量按钮。<br /><br />有关详细信息，请参阅[Microsoft Intune 中的 Android 策略设置](android-policy-settings-in-microsoft-intune.md)。|
|**PKCS #12 (.PFX) 证书配置文件（Android 4 及更高版本）**|使用此配置文件以建立和部署针对设备证书请求的 PFX 设置。<br /><br />有关详细信息，请参阅[使用 Microsoft Intune 中的证书配置文件确保资源访问的安全性](secure-resource-access-with-certificate-profiles.md)。|
|**SCEP 证书配置文件（Android 4 及更高版本）**|可以配置简单证书注册协议证书，该证书可与受信任的移动设备证书一起用于对移动设备进行身份验证，以允许它们访问 Wi-Fi 和 VPN 配置文件等配置的网络资源。<br /><br />有关详细信息，请参阅[使用 Microsoft Intune 中的证书配置文件确保资源访问的安全性](secure-resource-access-with-certificate-profiles.md)。|
|**受信任的证书配置文件（Android 4 及更高版本）**|可以配置受信任的移动设备证书，该证书可用于对移动设备进行身份验证，以允许它们访问 Wi-Fi 和 VPN 配置文件等配置的网络资源。<br /><br />有关详细信息，请参阅[使用 Microsoft Intune 中的证书配置文件确保资源访问的安全性](secure-resource-access-with-certificate-profiles.md)。|
|**VPN 配置文件（Android 4 及更高版本）**|配置和部署授权用户从其移动设备安全访问您公司网络的设置。 通过部署这些设置，你可最大程度减少最终用户连接到其作业所需的工作。<br /><br />有关详细信息，请参阅 [Microsoft Intune.md 中的 VPN 连接](vpn-connections-in-microsoft-intune.md)。|
|**Wi-fi 配置文件（Android 4 及更高版本）**|配置和部署到您的组织中的用户的无线网络设置。 通过部署这些设置，你可最大程度减少最终用户连接到无线网络所需的工作。<br /><br />有关详细信息，请参阅 [Microsoft Intune 中的 Wi-Fi 连接](wi-fi-connections-in-microsoft-intune.md)。|

## iOS 配置策略

|策略名称|在你想要完成以下事项时使用:|
|---------------|------------------------|
|**自定义配置（iOS 7.1 和更高版本）**|将配置文件部署到使用 Apple 配置器工具创建的 iOS 设备上。 这在配置策略不提供你需要的设置时十分有用。<br /><br />有关详细信息，请参阅 [Microsoft Intune 中的 iOS 策略设置](ios-policy-settings-in-microsoft-intune.md)。|
|**电子邮件配置文件（iOS 7.1 及更高版本）**|创建、部署和监视托管设备上的 Exchange Active Sync 电子邮件设置。 这样一来，用户无需进行特殊设置，就能通过个人设备访问企业电子邮件。<br /><br />有关详细信息，请参阅[使用 Microsoft Intune 的电子邮件配置文件配置对公司电子邮件的访问](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)。|
|**常规配置（iOS 7.1 及更高版本）**|配置移动设备安全设置和功能设置。<br />-   指定相容或不相容的应用，并在使用这些应用时进行报告。<br />配置锁定设备为只允许某些功能运行的展台模式，例如，允许设备只运行一个应用或禁用音量按钮。<br /><br />有关详细信息，请参阅 [Microsoft Intune 中的 iOS 策略设置](ios-policy-settings-in-microsoft-intune.md)。|
|**移动应用配置策略（iOS 7.1 及更高版本）**|移动应用配置策略可自动提供用户在运行 iOS 应用时可能需要的设置。<br /><br />有关详细信息，请参阅[使用 Microsoft Intune 中的移动应用配置策略配置 iOS 应用](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md)。|
|**移动预配配置文件策略（iOS 7.1 及更高版本）**|Apple iOS 业务线移动应用附带预配配置文件和证书签名的代码。 当应用在 iOS 设备上运行时，iOS 会确认 iOS 应用的完整性，并强制实施由预配配置文件定义的策略。<br><br>用于签署应用的企业签名证书通常持续 3 年。 但是，预配配置文件将在 1 年后过期。 使用此策略对拥有即将过期（但证书仍然有效）应用的设备主动部署新的预配配置文件策略。<br><br>有关详细信息，请参阅[使用 iOS 移动预配配置文件策略防止你的应用过期](ios-mobile-app-provisioning-profiles.md)。|
|**PKCS #12 (.PFX) 证书配置文件（iOS 7.1 及更高版本）**|使用此配置文件以建立和部署针对设备证书请求的 PFX 设置。<br /><br />有关详细信息，请参阅[使用 Microsoft Intune 中的证书配置文件确保资源访问的安全性](secure-resource-access-with-certificate-profiles.md)。|
|**SCEP 证书配置文件（iOS 7.1 及更高版本）**|可以配置简单证书注册协议证书，该证书可与受信任的移动设备证书一起用于对移动设备进行身份验证，以允许它们访问 Wi-Fi 和 VPN 配置文件等配置的网络资源。<br /><br />有关详细信息，请参阅[使用 Microsoft Intune 中的证书配置文件确保资源访问的安全性](secure-resource-access-with-certificate-profiles.md)。|
|**受信任证书配置文件（iOS 7.1 及更高版本）**|可以配置受信任的移动设备证书，该证书可用于对移动设备进行身份验证，以允许它们访问 Wi-Fi 和 VPN 配置文件等配置的网络资源。<br /><br />有关详细信息，请参阅[使用 Microsoft Intune 中的证书配置文件确保资源访问的安全性](secure-resource-access-with-certificate-profiles.md)。|
|**VPN 配置文件（iOS 7.1 及更高版本）**|配置和部署授权用户从其移动设备安全访问您公司网络的设置。 通过部署这些设置，你可最大程度减少最终用户连接到其作业所需的工作。<br /><br />有关详细信息，请参阅 [Microsoft Intune.md 中的 VPN 连接](vpn-connections-in-microsoft-intune.md)。|
|**Wi-Fi 配置文件（iOS 7.1 及更高版本）**|配置和部署到您的组织中的用户的无线网络设置。 通过部署这些设置，你可最大程度减少最终用户连接到无线网络所需的工作。<br /><br />有关详细信息，请参阅 [Microsoft Intune 中的 Wi-Fi 连接](wi-fi-connections-in-microsoft-intune.md)。|


## Mac OS X 配置策略

|策略名称|在你想要完成以下事项时使用:|
|---------------|------------------------|
|**自定义配置（Mac OS X 10.9 及更高版本）**|将配置文件部署到使用 Apple Configurator 工具创建的 Mac 计算机上。 这在配置策略不提供你需要的设置时十分有用。<br /><br />有关详细信息，请参阅 [Microsoft Intune 中的 Mac OS X 策略设置](mac-os-x-policy-settings-in-microsoft-intune.md)。|
|**常规配置（Mac OS X 10.9 及更高版本）**|配置移动设备安全设置和功能设置。<br />指定相容或不相容的应用，并在使用这些应用时进行报告。<br /><br />有关详细信息，请参阅 [Microsoft Intune 中的 Mac OS X 策略设置](mac-os-x-policy-settings-in-microsoft-intune.md)。|
|**SCEP 证书配置文件（Mac OS X 10.9 及更高版本）**|可以配置简单证书注册协议证书，该证书可与受信任的移动设备证书一起用于对移动设备进行身份验证，以允许它们访问 Wi-Fi 和 VPN 配置文件等配置的网络资源。<br /><br />有关详细信息，请参阅[使用 Microsoft Intune 中的证书配置文件确保资源访问的安全性](secure-resource-access-with-certificate-profiles.md)。|
|**受信任的证书配置文件（Mac OS X 10.9 及更高版本）**|可以配置受信任的移动设备证书，该证书可用于对移动设备进行身份验证，以允许它们访问 Wi-Fi 和 VPN 配置文件等配置的网络资源。<br /><br />有关详细信息，请参阅[使用 Microsoft Intune 中的证书配置文件确保资源访问的安全性](secure-resource-access-with-certificate-profiles.md)。|
|**VPN 配置文件（Mac OS X 10.9 及更高版本）**|配置和部署授权用户从其移动设备安全访问您公司网络的设置。 通过部署这些设置，你可最大程度减少最终用户连接到其作业所需的工作。<br /><br />有关详细信息，请参阅 [Microsoft Intune.md 中的 VPN 连接](vpn-connections-in-microsoft-intune.md)。|
|**Wi-Fi 配置文件（Mac OS X 10.9 及更高版本）**|配置和部署到您的组织中的用户的无线网络设置。 通过部署这些设置，你可最大程度减少最终用户连接到无线网络所需的工作。<br /><br />有关详细信息，请参阅 [Microsoft Intune 中的 Wi-Fi 连接](wi-fi-connections-in-microsoft-intune.md)。|

## Windows 配置策略
仅适用于 Windows Phone 和注册的 Windows 设备。

|策略名称|在你想要完成以下事项时使用:|
|---------------|------------------------|
|**自定义配置（Windows 10 桌面版和移动版及更高版本）**|部署可用于控制设备功能的 OMA-URI 设置。 这在配置策略不提供你需要的设置时十分有用。<br />    有关详细信息，请参阅 [Microsoft Intune 中的 Windows 10 策略设置](windows-10-policy-settings-in-microsoft-intune.md)。|
|**自定义配置（Windows Phone 8.1 及更高版本）**|部署可用于控制设备功能的 OMA-URI 设置。 这在配置策略不提供你需要的设置时十分有用。<br /><br />有关详细信息，请参阅 [Microsoft Intune 中的 Windows Phone 8.1 设置](windows-phone-8-1-policy-settings-in-microsoft-intune.md)。|
|**版本升级策略（Windows 10 桌面版及更高版本）**<br><br>**版本升级策略（Windows 10 全息版及更高版本）**|配置并部署包含用于将 Windows 10 设备更新到较新版本的许可证或产品密钥信息的策略<br><br>有关详细信息，请参阅 [Microsoft Intune 中的版本升级策略设置](edition-upgrade-policy-settings-in-microsoft-intune.md)。|  
|**电子邮件配置文件（Windows Phone 8 及更高版本）**<br /><br />**电子邮件配置文件（Windows 10 桌面版和移动版及更高版本）**|创建、部署和监视托管设备上的 Exchange Active Sync 电子邮件设置。 这样一来，用户无需进行特殊设置，就能通过个人设备访问企业电子邮件。<br /><br />有关详细信息，请参阅[使用 Microsoft Intune 的电子邮件配置文件配置对公司电子邮件的访问](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)。|
|**常规配置（Windows 10 桌面版和移动版及更高版本）**|为注册的 Windows 10 桌面版和移动版设备配置移动设备安全和功能设置。<br /><br />有关详细信息，请参阅 [Microsoft Intune 中的 Windows 10 策略设置](windows-10-policy-settings-in-microsoft-intune.md)。|
|**常规配置（Windows 10 协同版及更高版本）**|为已注册的 Windows 10 协同版设备（例如 Surface Hub 设备）配置设备安全性和功能设置。<br /><br />有关详细信息，请参阅 [Microsoft Intune 中的 Windows Team 配置策略设置](windows-team-configuration-policy-settings-in-microsoft-intune.md)。|
|**常规配置（Windows 8.1 及更高版本）**|为注册的 Windows 设备配置移动设备安全设置和功能设置。<br /><br />有关详细信息，请参阅 [Microsoft Intune 中的 Windows 策略设置](windows-configuration-policy-settings-in-microsoft-intune.md)。|
|**常规配置（Windows Phone 8.1 及更高版本）**|配置移动设备安全设置和功能设置。<br />指定用户可以使用或不能使用的应用，并阻止安装和使用不符合要求的应用。<br /><br />有关详细信息，请参阅 [Microsoft Intune 中的 Windows Phone 8.1 设置](windows-phone-8-1-policy-settings-in-microsoft-intune.md)。|
|**PKCS #12 (.PFX) 证书配置文件（Windows 10 桌面版和移动版及更高版本）**|使用此配置文件以建立和部署针对设备证书请求的 PFX 设置。<br /><br />有关详细信息，请参阅[使用 Microsoft Intune 中的证书配置文件确保资源访问的安全性](secure-resource-access-with-certificate-profiles.md)。|
|**SCEP 证书配置文件（Windows 8.1 及更高版本）**<br /><br />**SCEP 证书配置文件（Windows Phone 8.1 及更高版本）**|可以配置简单证书注册协议证书，该证书可与受信任的移动设备证书一起用于对移动设备进行身份验证，以允许它们访问 Wi-Fi 和 VPN 配置文件等配置的网络资源。<br /><br />有关详细信息，请参阅[使用 Microsoft Intune 中的证书配置文件确保资源访问的安全性](secure-resource-access-with-certificate-profiles.md)。|
|**受信任的证书配置文件（Windows 8.1 及更高版本）**<br /><br />**受信任的证书配置文件（Windows Phone 8.1 及更高版本）**|可以配置受信任的移动设备证书，该证书可用于对移动设备进行身份验证，以允许它们访问 Wi-Fi 和 VPN 配置文件等配置的网络资源。<br /><br />有关详细信息，请参阅[使用 Microsoft Intune 中的证书配置文件确保资源访问的安全性](secure-resource-access-with-certificate-profiles.md)。|
|**VPN 配置文件（Windows 10 桌面版和移动版及更高版本）**<br /><br />**VPN 配置文件（Windows 8.1 及更高版本）**<br /><br />**VPN 配置文件（Windows Phone 8.1 及更高版本）**|配置和部署授权用户从其移动设备安全访问您公司网络的设置。 通过部署这些设置，你可最大程度减少最终用户连接到其作业所需的工作。<br /><br />有关详细信息，请参阅 [Microsoft Intune 中的 VPN 连接](vpn-connections-in-microsoft-intune.md)。|
|**Wi-Fi 导入**|导入和部署你之前导出到文件的 Windows Wi-Fi 配置。<br /><br />有关详细信息，请参阅 [Microsoft Intune 中的 Wi-Fi 连接](wi-fi-connections-in-microsoft-intune.md)。|
|**Windows 信息保护**<br>（以前称为企业数据保护）|随着企业中员工拥有的设备的增加，通过应用和服务（如电子邮件、社交媒体和公共云）发生的意外数据泄露的风险也在增加，这是不受企业控制的。 例如，某位员工从其个人电子邮件帐户发送最新的工程图片、将产品信息复制并粘贴到推文，或将正在进行的销售报表保存到他的公有云存储。<br><br>Windows 信息保护有助于防范潜在的数据泄露，而不会干扰员工体验。 它还有助于防范企业应用和数据在企业自有设备和员工带到工作中的个人设备上的意外数据泄露，而无需对你的环境或其他应用进行更改。<br><br>此 Intune 策略管理由 Windows 信息保护的应用、企业网络位置、保护级别和加密设置的列表。<br><br>有关详细信息，请参阅 [Protect your enterprise data using Windows Information Protection](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-edp)（使用 Windows 信息保护来保护你的企业数据）。|


## 软件策略

|策略名称|在你想要完成以下事项时使用:|
|---------------|------------------------|
|**托管浏览器策略 （Android 4 和更高版本）**<br /><br />**托管浏览器策略（iOS 7.1 及更高版本）**|指定用户在使用托管浏览器应用程序时，他们能或不能访问的网站。<br /><br />有关详细信息，请参阅[使用 Microsoft Intune 的托管浏览器策略管理 Internet 访问](manage-internet-access-using-managed-browser-policies.md)。|
|**移动应用程序管理策略 （Android 4 和更高版本）**<br /><br />**移动应用程序管理策略（iOS 7.1 及更高版本）**|修改您部署的应用程序的功能，以帮助使其符合您的公司的遵从性和安全策略。 例如，您可以限制在受限制的应用程序内的剪切、复制和粘贴操作，或配置应用程序以打开托管浏览器内的所有 web 链接。<br /><br />有关详细信息，请参阅 [Configure and deploy mobile application management policies in the Microsoft Intune console（在 Microsoft Intune 控制台中配置和部署移动应用程序管理策略）](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)。|

## 常用的移动设备设置

|策略名称|在你想要完成以下事项时使用:|
|---------------|------------------------|
|**Exchange ActiveSync 策略**|为 Exchange ActiveSync 托管设备配置移动设备安全设置和功能设置。<br /><br />有关详细信息，请参阅 [Microsoft Intune 中的 Exchange ActiveSync 策略设置](exchange-activesync-policy-settings-in-microsoft-intune.md)。|
|**移动设备安全策略**|<ul><li>为移动设备(所有平台)配置设置，包括:<br /><br /><ul><li>安全</li><li>加密</li><li>系统</li><li>Email</li><li>应用程序</li></ul></li></ul> **重要提示：**Microsoft Intune 现在拥有针对每个设备平台的单独**配置策略**，这些策略包含你可以使用的最新设置。 你可以继续使用移动设备安全策略，任何现有部署仍将起作用，但你应计划尽快迁移到新配置策略。<br />有关详细信息，请参阅 [Microsoft Intune 中的移动设备安全策略设置](mobile-device-security-policy-settings-in-microsoft-intune.md)。|

## 条件访问和相容性策略

### 条件性访问

|策略名称|在你想要完成以下事项时使用:|
|---------------|------------------------|
|**Exchange Online 策略**<br /><br />**Exchange 本地策略**|管理从非 Intune 托管设备或不符合你创建的合规性策略的设备对 Microsoft Exchange 电子邮件进行的访问。<br /><br />有关详细信息，请参阅[使用 Intune 限制对 Exchange Online 和新版 Exchange Online Dedicated 的电子邮件访问](restrict-access-to-exchange-online-with-microsoft-intune.md)。|
|**SharePoint Online 策略**|管理从非 Intune 托管设备或不符合你创建的合规性策略的设备对 SharePoint Online 进行的访问。<br /><br />有关详细信息，请参阅[使用 Microsoft Intune 限制对 SharePoint Online 的访问](restrict-access-to-sharepoint-online-with-microsoft-intune.md)。|
|**Skype for Business**|管理从非 Intune 托管设备或不符合你创建的合规性策略的设备对 Skype for Business 进行的访问。<br /><br />有关详细信息，请参阅[使用 Microsoft Intune 限制对 Skype for Business 的访问](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)。|
> [!NOTE]
> 你不向用户和设备部署条件访问策略。 相反，你配置所需的策略，然后它会应用于策略针对的所有组。

### 符合性策略

|策略名称|在你想要完成以下事项时使用:|
|---------------|------------------------|
|**相容性策略**|定义设备的相容性级别，然后报告不相容的设备。 这些策略与条件访问一起使用，帮助评估应从服务阻止的设备。<br /><br />有关详细信息，请参阅 [Microsoft Intune 中的设备合规性策略](introduction-to-device-compliance-policies-in-microsoft-intune.md)。|

## Windows PC 管理

|策略名称|在你想要完成以下事项时使用:|
|---------------|------------------------|
|**Microsoft Intune 代理设置**|在计算机上配置 Intune PC 客户端，包括下列各项的设置：<br /><br />-   Endpoint Protection<br />-   软件更新<br />-   策略检查计划<br /><br />这种策略仅可以部署到设备组。<br /><br />Intune 客户端根据“更新和应用程序检测频率”设置下载新的和更新的策略，该设置的默认值为 8 小时。 不过，你可以随时在计算机上强制刷新策略。<br /><br />有关详细信息，请参阅[在 Microsoft Intune 中利用软件更新使 Windows 电脑保持最新版本](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)。|
|**Microsoft Intune 中心设置**|配置在 Microsoft Intune 中心内出现的托管计算机的详细信息。<br /><br />这种策略仅可以部署到设备组。<br /><br />有关详细信息，请参阅[使用 Microsoft Intune 计算机客户端的常见 Windows 电脑管理任务](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)。|
|**Windows 防火墙设置**|在计算机上为常见网络通信配置 Windows 防火墙设置和例外，包括：<br /><br />-   BranchCache<br />-   远程协助<br />-   媒体共享<br /><br />这种策略仅可以部署到设备组。<br /><br />有关详细信息，请参阅[使用 Microsoft Intune 的 Endpoint Protection 帮助保障 Windows 电脑的安全](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)。|

### 另请参阅

[使用 Microsoft Intune 策略管理设备上的设置和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Jul16_HO3-->


