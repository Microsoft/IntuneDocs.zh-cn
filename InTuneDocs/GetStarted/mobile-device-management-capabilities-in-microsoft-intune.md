---
# required metadata

title: Microsoft Intune 的移动设备管理功能 | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f23b3ee7-78da-4e53-9fc2-78e58401bcf9

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
# Microsoft Intune 的移动设备管理功能

通过在 Microsoft Intune 服务中*注册*设备，你可以使用 Microsoft Intune 管理各种设备。 然后，用户可以使用*公司门户*来执行一系列操作，例如注册其设备，浏览和安装应用，确保其设备符合公司策略，以及联系其 IT 支持。
本主题介绍了注册设备可为你提供的功能的完整列表。

管理、清单、应用部署、设置和停用都可通过 Intune 管理控制台进行处理。 用户获取公司门户的访问权限，这使他们可以安装应用、注册和删除设备以及帮助他们与其 IT 部门或支持人员联系。



## 设备安全性和配置

|功能|详细信息|更多信息|
|--------------|-----------|--------------------|
|配置策略<br><br>自定义策略|移动设备配置策略让你能够在组织中管理移动设备上多个设置和功能。 例如，你可以申请密码、限制失败尝试次数、限制在屏幕锁定前的分钟数、设置密码过期时间，以及阻止使用以前用过的密码。 你还可以控制硬件和软件功能的使用，例如设备的摄像头或 Web 浏览器。<br><br>在配置策略不包含你需要的设置时使用自定义策略。 对于 iOS 设备，你可以导入你从 Apple 配置工具中导出的设置。 对于其他设备，你可以使用 OMA-URI 设置配置设备上的设置和功能。|[使用 Microsoft Intune 策略管理设备上的设置和功能](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)<br />|
|远程擦除、远程锁定和密码重置|在设备丢失或被盗时，请清除敏感数据。 例如，你可以远程锁定设备、将其还原为出厂设置或仅擦除企业数据。<br>你可以在用户无法访问其设备时重置密码，锁定遗失或被盗的设备，甚至擦除遗失或被盗设备的数据。|[通过远程锁定和密码重置帮助保护你的设备](/intune/deploy-use/use-remote-lock-and-passcode-reset-in-microsoft-intune)和[从 Intune 管理中停用设备](/intune/deploy-use/retire-devices-from-microsoft-intune-management)|
|展台模式|允许您锁定移动设备的某些功能，如屏幕捕捉和电源开关。 此外允许您限制设备运行您指定的单个应用程序。|[Microsoft Intune 中的 iOS 配置策略设置](/intune/deploy-use/ios-policy-settings-in-microsoft-intune)|

## 应用管理

|功能|详细信息|更多信息|
|--------------|-----------|--------------------|
|应用部署和管理|提供了一系列的工具以帮助你在移动应用的整个生命周期中对其进行管理，包括部署来自安装文件和应用商店的应用、对应用状态的详细监视以及应用删除。|[在 Microsoft Intune 中部署应用](/intune/deploy-use/deploy-apps)|
|符合和不符合要求的应用程序|你可以指定符合（即允许用户安装）和不符合要求的应用程序（禁止用户安装）的列表。|[Microsoft Intune 中的 iOS 策略设置](/intune/deploy-use/ios-policy-settings-in-microsoft-intune)|
|移动应用程序管理|针对使用 Intune 进行管理设备和不使用 Intune 进行管理的设备，使用移动应用程序管理配置应用程序的限制。 这可以帮助您通过限制数据的复制和粘贴、外部备份和应用程序之间的数据传输等操作来提高您公司的数据的安全性。|[Configure and deploy mobile application management policies in the Microsoft Intune console](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console)<br><br>[使用 Microsoft Intune 创建和部署移动应用管理策略](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)<br /><br />[使用 Microsoft Intune 应用包装工具为移动应用程序管理准备 iOS 应用](/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)<br /><br />[使用 Microsoft Intune 应用包装工具为移动应用程序管理准备 Android 应用](/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)|
|移动应用配置|使用移动应用配置策略可提供用户在运行 iOS 应用时可能需要的设置。 例如，某一个应用可能要求用户指定登录信息的端口号。 这可以帮助简化应用程序的配置并减少技术支持呼叫次数。|[使用 Microsoft Intune 中的移动应用配置策略配置 iOS 应用](/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)|
|托管浏览器|在把托管浏览器部署到您的用户后，您可以配置托管浏览器策略控制他们可以访问的网站。 此外，您可以将移动应用程序管理策略应用到托管浏览器。|[使用 Microsoft Intune 的托管浏览器策略管理 Internet 访问](/intune/deploy-use/manage-internet-access-using-managed-browser-policies)|
|Microsoft Passport|通过 Intune 可以与 Microsoft Passport for Work 集成，这是一种适用于 Windows 10 的替代登录方法，它使用 Active Directory 或 Azure Active Directory 帐户来取代密码、智能卡或虚拟智能卡。|[通过 Microsoft Intune 控制设备上的 Microsoft Passport 设置](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune)|

## 公司资源访问

|功能|详细信息|更多信息|
|--------------|-----------|--------------------|
|证书配置文件|创建和部署受信任的证书配置文件和简单证书注册协议 (SCEP) 证书，这些文件和证书有助于对 Wi-Fi、VPN 和电子邮件配置文件进行保护和身份验证。|[使用 Microsoft Intune 中的证书配置文件确保资源访问的安全性](/intune/deploy-use/secure-resource-access-with-certificate-profiles)|
|Wi-Fi 配置文件|将无线网络设置部署到你的用户。 通过部署这些设置，你可最小化最终用户连接到公司网络时所需的工作。|[Microsoft Intune 中的 Wi-Fi 连接](/intune/deploy-use/wi-fi-connections-in-microsoft-intune)|
|电子邮件配置文件|创建电子邮件设置并将其部署到设备。 这样一来，用户无需进行特殊设置，就能通过个人设备访问企业电子邮件。|[使用 Microsoft Intune 的电子邮件配置文件配置对公司电子邮件的访问](/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)|
|VPN 配置文件|将 VPN 设置部署到用户和你的组织中的设备。 通过部署这些设置，你可以最大限度减少最终用户连接到公司网络资源需要进行的工作。|[Microsoft Intune 中的 VPN 连接](/intune/deploy-use/vpn-connections-in-microsoft-intune)|
|条件性访问策略|管理从非 Intune 托管设备对 Microsoft Exchange 电子邮件和 SharePoint Online 进行的访问。|[使用 Microsoft Intune 限制对电子邮件和 SharePoint 的访问](/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)|

## 清单和报告

|功能|详细信息|更多信息|
|--------------|-----------|--------------------|
|清单和报告|查找有关你管理的设备和它们所使用的软件的信息。<br /><br />你可以通过多种方式筛选这些报告，如设备平台以及设备是否符合公司标准。|[通过使用报表了解 Microsoft Intune 操作](/intune/understand-explore/understand-microsoft-intune-operations-by-using-reports)|

### 另请参阅
[Microsoft Intune 中的 Windows PC 管理功能](/intune/understand-explore/windows-pc-management-capabilities-in-microsoft-intune)


<!--HONumber=May16_HO1-->


