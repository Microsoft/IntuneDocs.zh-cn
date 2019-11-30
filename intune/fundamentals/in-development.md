---
title: 开发过程中 - Microsoft Intune
titleSuffix: ''
description: 开发过程中的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04b284a62076122cec70b6b455151a0377470521
ms.sourcegitcommit: 16a9109b4028589c17695d41271ca4fee8b1d697
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74540740"
---
# <a name="in-development-for-microsoft-intune---december-2019"></a>开发过程中的 Microsoft Intune 功能 - 2019 年 12 月

为了辅助就绪性和计划，此页面列出了正在开发但尚未发布的 Intune UI 更新和功能。 除了本页上的信息：

- 如果我们预计你需要在更改之前采取措施，我们将在 Office 消息中心发布补充性的文章。
- 当某个功能进入生产环境时，无论该功能是预览版还是正式发布，功能说明都将从此页面移动到[新增内容](whats-new.md)。
- 此页和[新增功能页](whats-new.md)会定期更新。 返回查看其他更新。
- 有关策略性可交付内容和时间线，请参阅 [Microsoft 365 路线图](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)。

> [!NOTE]
> 此页反映了未来版本中有关 Intune 功能的最新预期。 日期和各项功能可能会更改。 本页不介绍开发中的所有功能。

**RSS 源**：通过将以下 URL 复制并粘贴到源阅读器中，可以在页面更新时收到通知：`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>应用管理

### <a name="ios-user-licensed-vpp-apps---5619268-idready---"></a>iOS 用户许可的 VPP 应用<!-- 5619268 idready -->
对于用户注册 iOS 设备，最终用户将不再显示部署为 "可用" 的设备许可 VPP 应用程序。 但是，最终用户将继续在公司门户中看到所有用户许可的 VPP 应用。 有关 VPP 应用的详细信息，请参阅[如何使用 Microsoft Intune 管理通过 Apple Volume Purchase Program 购买的 iOS and macOS 应用](~/apps/vpp-apps-ios.md)。

### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices---4851745-idready---"></a>从 MEM encrypted macOS 设备检索个人恢复密钥<!-- 4851745 idready -->
最终用户将能够使用 iOS 公司门户应用检索其个人恢复密钥（FileVault 密钥）。 具有个人恢复密钥的设备必须向 Intune 注册，并通过 Intune 使用 FileVault 进行加密。 使用 iOS 公司门户应用，最终用户可以打开 Safari web 视图，并检索其个人恢复密钥。 在 Intune 中，选择 "**设备**" > 已*加密和已注册的 MacOS 设备* > **获取恢复密钥**"。 有关 FileVault 的详细信息，请参阅[FileVault encryption For macOS](~/protect/encrypt-devices.md#filevault-encryption-for-macos)。

### <a name="microsoft-app-icons-update--4677605--"></a>Microsoft 应用图标更新<!--4677605-->
应用保护策略和应用配置策略的应用目标窗格中用于 Microsoft 应用的图标将会更新。

### <a name="smime-support-for-microsoft-outlook-mobile---2669398----"></a>Microsoft Outlook Mobile 的 S/MIME 支持<!-- 2669398  -->
Intune 将支持提供 S/MIME 签名和加密证书，这些证书可用于 iOS 和 Android 上的 Outlook Mobile。 有关相关信息，请参阅适用于[iOS 设备的电子邮件设置](~/configuration/email-settings-ios.md)和[Android 设备的电子邮件设置](~/configuration/email-settings-android.md)。

### <a name="custom-settings-support-for-macos-applications---4736278----"></a>自定义设置对 macOS 应用程序的支持<!-- 4736278  -->
Intune 将支持自定义设置，允许你将特定的键和值添加到现有的首选项属性列表（info.plist）文件，以配置 macOS 应用和设备。 并非所有应用都支持托管首选项，并且在某些情况下，只能管理特定设置。 仅通过设备通道部署设置。 只应上载属性列表文件或以设备通道设置为目标的 .xml 文件。

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>显示 Windows 上公司门户应用的通知<!-- 1808082  -->
我们将更新 Windows 设备上的公司门户应用程序，以便向用户显示 toast 通知，即使应用程序处于关闭状态也是如此。 仅当安装状态为 "已完成" 或 "失败" 时，更新才会显示可用应用的通知。 公司门户应用不会显示所需应用程序的通知。

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>显示公司门户应用的安装状态消息<!-- 2514416  -->
公司门户应用会向最终用户显示其他应用安装状态消息。 以下条件适用于新的 Win32 依赖项功能：
- 应用安装失败。 不符合管理员定义的依赖关系。

### <a name="configure-app-notification-content-for-organization-accounts---2576686---"></a>为组织帐户配置应用通知内容<!-- 2576686 -->
Android 和 iOS 设备上的 Intune 应用允许你为组织帐户控制应用通知内容。 此功能需要应用程序的支持，并可能不适用于所有启用应用的应用程序。 有关 APP 的详细信息，请参阅[什么是应用保护策略？](../apps/app-protection-policy.md)

<!-- ***********************************************-->
## <a name="device-configuration"></a>设备配置

### <a name="block-users-from-configuring-certificate-credentials-in-the-managed-keystore-on-android-enterprise-device-owner-devices---3311998-idready---"></a>阻止用户在 Android 企业设备所有者设备上的托管密钥存储中配置证书凭据<!-- 3311998 idready -->
在 Android 企业设备所有者设备上，会有一个新设置阻止用户在托管密钥存储中配置其证书凭据（**设备配置** > **配置文件** > **创建配置**文件 > **Android Enterprise** for Platform >**设备所有者仅 >** **用户 + 帐户**的配置文件类型 > 设备限制。

要查看当前设置，请转到[便于使用 Intune 允许或限制功能的 Android Enterprise 设备设置](../configuration/device-restrictions-android-for-work.md)。

适用于：
- Android 企业设备所有者，包括专用和完全托管的设备

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686-idready---"></a>适用于 macOS 设备的有线网络设备配置文件<!-- 3508686 idready -->
在 macOS 设备上，未来更新将包括一个新的设备配置文件，该配置**文件用于配置**有线网络（**设备配置** > **配置**文件 > **创建配置**文件 > 用于平台 >**有线网络**的配置文件类型）。 使用此功能创建 802.1 x 配置文件来管理有线网络，并将这些有线网络部署到 macOS 设备。

适用于：
- macOS

### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-idready---"></a>向 Android 企业工作配置文件的 Wi-fi 配置文件添加自动代理设置<!-- 4490822 idready -->
在 Android 企业工作配置文件设备上，可以创建 Wi-fi 配置文件。 选择 Wi-fi 企业类型时，还可以输入 Wi-fi 网络上使用的可扩展身份验证协议（EAP）类型。

在将来的更新中，当你选择 "企业类型" 时，你将能够输入自动代理设置，包括代理服务器 URL，如 `proxy.contoso.com`。

若要查看可配置的当前 Wi-fi 设置，请参阅[在 Microsoft Intune 中为运行 Android 企业版和 android 展台的设备添加 wi-fi 设置](../configuration/wi-fi-settings-android-enterprise.md)。

适用于：
- Android Enterprise 工作配置文件

### <a name="enable-network-access-control-nac-with-cisco-anyconnect-vpn-on-ios-devices---4860111-idready---"></a>在 iOS 设备上使用 Cisco AnyConnect VPN 启用网络访问控制（NAC）<!-- 4860111 idready -->
在 iOS 设备上，你可以创建一个 VPN 配置文件，并使用不同的连接类型，包括 Cisco AnyConnect （**设备配置** > **配置文件** > **创建配置**文件的配置文件**类型的 > > ** 配置**文件类型**的配置文件类型 > **cisco AnyConnect**的连接类型）。 

在将来的更新中，你将能够使用 Cisco AnyConnect 启用网络访问控制（NAC）。 使用此功能需要：

1. 在[Cisco 标识服务引擎管理员指南](https://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html)中，请按照将**MICROSOFT INTUNE 配置为 MDM Server**中的步骤在 Azure 中配置 Cisco 标识服务引擎（ISE）。
2. 在 Intune 设备配置文件中，选择 "**启用网络访问控制（NAC）** " 设置。

若要查看所有可用的 VPN 设置，请参阅[在 iOS 设备上配置 VPN 设置](../configuration/vpn-settings-ios.md)。

适用于：
- iOS

### <a name="updated-single-sign-on-experience-for-apps-and-websites-on-your-ios-ipados-and-macos-devices---4999578-idready---"></a>针对 iOS、iPadOS 和 macOS 设备上的应用和网站更新了单一登录体验<!-- 4999578 idready -->
Intune 正在为 iOS、iPadOS 和 macOS 设备添加更多单一登录设置。 目前，可以在 Intune 中配置凭据 SSO 应用扩展和 Apple 的内置 Kerberos 扩展。 在将来的更新中，你将能够配置由你的组织或你的标识提供者编写的重定向 SSO 应用扩展。 

使用这些设置为使用新式身份验证方法（例如 OAuth 和 SAML2）的应用程序和网站配置无缝单一登录体验。 

若要查看可配置的 SSO 应用扩展设置，请[在 macOS](../configuration/macos-device-features-settings.md#single-sign-on-app-extension)上的[iOS](../configuration/ios-device-features-settings.md#single-sign-on-app-extension)和 sso 上访问 sso。

适用于：
- iOS/iPadOS
- macOS

### <a name="require-use-of-approved-keyboards-on-android--4761794-idready---"></a>需要在 Android 上使用已批准的键盘<!--4761794 IDready -->
可以指定要在托管 Android 应用中使用的已批准键盘的列表。 在托管应用程序中，系统将提示用户切换到设备上已安装的已批准键盘之一，或者，如果需要，系统会将其定向到 Google Play 商店下载并设置一个已批准的键盘。 如果用户的活动键盘是已批准的键盘之一，则该用户将只能编辑托管应用中的文本字段。

### <a name="use-pkcs-certificates-with-wi-fi-profiles-on-windows-10-and-later-devices---3246388----"></a>在 Windows 10 和更高版本的设备上将 PKCS 证书与 Wi-fi 配置文件配合使用<!-- 3246388  -->
目前，可以通过 SCEP 证书（**设备配置** > **配置文件** > **创建配置**文件 > **windows 10 和更高版本**的平台 > **wi-fi**配置文件类型 > **Enterprise** > **EAP 类型**）。 你将能够将 PKCS 证书用于 Windows Wi-fi 配置文件。 此功能允许用户使用租户中的新的或现有的 PKCS 证书配置文件对 Wi-fi 配置文件进行身份验证。 

有关 Wi-fi 配置文件的详细信息，请参阅[在 Intune 中添加适用于 Windows 10 及更高版本设备的 wi-fi 设置](../configuration/wi-fi-settings-windows.md)。

适用于：
- Windows 10 及更高版本

### <a name="new-exchangeactivesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices---4892824----"></a>在 iOS 设备上创建电子邮件设备配置文件时，新的 ExchangeActiveSync 设置<!-- 4892824  --> 
在 iOS/iPadOS 设备上，你可以在设备配置文件中配置电子邮件连接（**设备配置** > **配置**文件 > **创建配置**文件 > 适用于平台的**ios/iPadOS** >**电子邮件**对于配置文件类型）。 

将提供新的 ExchangeActiveSync 设置，其中包括：
- 选择要同步的服务（或阻止同步），如电子邮件、日历和联系人。
- 允许（或阻止）用户在其设备上更改这些服务的同步设置。 

若要查看当前设置，请[在 Intune 中中转到 iOS 设备的电子邮件配置文件设置](../configuration/email-settings-ios.md)。

适用于：
- iOS 13.0 及更高版本
- iPadOS 13.0 及更高版本

### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-device-owner-and-dedicated-devices---5353228----"></a>阻止用户将个人 Google 帐户添加到 Android 企业设备所有者和专用设备<!-- 5353228  -->
你将能够阻止用户在 Android 企业设备所有者和专用设备上创建个人 Google 帐户（**设备配置** > **配置文件** > **创建配置文件** > **Android 企业版**对于平台 >**设备所有者仅 >** 配置文件类型 >**用户和帐户设置**）的设备限制。

要查看可以配置的当前设置，请转到[使用 Intune 允许或限制功能的 Android Enterprise 设备设置](../configuration/device-restrictions-android-for-work.md)。

适用于：
- Android Enterprise 设备所有者
- Android Enterprise 专用设备

### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-ios-device-restrictions-profile---5468501----"></a>IOS 设备限制配置文件中删除了 Siri 命令的服务器端日志记录设置<!-- 5468501  -->
在 iOS 设备上，你可以创建一个设备限制配置文件，用于为 Siri 命令配置服务器端日志记录（**设备配置** > **配置文件** > **创建配置文件** > **iOS/iPadOS**用于平台>**内置应用程序**的配置文件类型 >**设备限制**。 将删除**Siri 命令的服务器端日志记录**设置。

此设置将从 Intune 管理控制台中删除。 即使配置了此设置的现有策略将继续显示此设置，此设置在设备上也不起作用。 如果要从现有策略中删除此设置，请执行策略，进行次要编辑，保存，并更新策略。

要查看可以配置的设置，请参阅[使用 Intune 允许或限制功能的 iOS 和 iPadOS 设备设置](../configuration/device-restrictions-ios.md)。

适用于：
- iOS

<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
<!--## Device management-->


<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>监视和故障排除

### <a name="centralized-audit-logs--5603185-5697164--"></a>集中式审核日志<!--5603185, 5697164-->
新的集中审核日志体验会将所有类别的审核日志收集到一个页面中。 You'l 可以筛选日志以获取所需数据。 若要查看审核日志，请参阅**租户管理** > **审核日志**。 有关详细信息，请参阅[Intune 中的审核日志即将发生的更改](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Upcoming-change-to-Audit-logs-in-Intune/ba-p/1015858)。

<!-- ***********************************************-->
<!--## Role-based access control-->


<!-- ***********************************************-->

## <a name="security"></a>安全

### <a name="use-pkcs-certificate-profiles-to-provision-devices-with-certificates---2317124-2317130-2317139-2340517-2340528-2340529-idready---"></a>使用 PKCS 证书配置文件设置具有证书的设备<!-- 2317124, 2317130, 2317139, 2340517, 2340528, 2340529 IDready -->
你将能够使用 PKCS 证书配置文件向设备颁发证书，并扩展当前对基于用户的证书的支持。 基于设备的证书将支持 Android、iOS 和 Windows 平台，并且可用于 Wi-fi 和 VPN 配置文件。

<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。


