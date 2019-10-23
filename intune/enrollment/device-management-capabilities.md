---
title: Microsoft Intune 中的设备管理功能
description: 阅读本主题以了解 Intune 如何帮助你管理注册的设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 64df7ccad203109c201b0e18c3d20023690e31aa
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503226"
---
# <a name="enrolled-device-management-capabilities-of-microsoft-intune"></a>Microsoft Intune 已注册设备管理功能

通过在 Microsoft Intune 服务中*注册*设备，你可以使用 Microsoft Intune 管理各种设备。 你可自己注册一些设备类型，或者用户可使用公司门户  应用注册。 注册可以让他们浏览和安装应用，确保他们的设备符合公司策略，并可联系 IT 支持人员。

本文提供注册设备后可获得的功能的完整列表。

管理、盘存、应用部署、预配和停用操作均可通过 Azure 门户中 Intune 来执行。

用户获取公司门户的访问权限，这使他们可以安装应用、注册和删除设备以及与其 IT 部门或支持人员联系。



## <a name="device-security-and-configuration"></a>设备安全性和配置

|功能|详细信息|更多信息|
|--------------|-----------|--------------------|
|配置策略<br><br>自定义策略| 让你可在组织中管理移动设备上多个设置和功能。 例如，你可以申请密码、限制失败尝试次数、限制屏幕锁定前的时间量、设置密码过期时间，以及阻止使用以前用过的密码。 你还可以控制硬件和软件功能的使用，例如设备的摄像头或 Web 浏览器。<br><br>配置策略不包含所需设置时，请使用自定义策略。 对于 iOS 设备，你可以导入你从 Apple 配置工具中导出的设置。 对于其他设备，你可以使用开放移动联盟统一资源标识符 (OMA-URI) 设置配置设备上的设置和功能。|[使用 Microsoft Intune 策略管理设备上的设置和功能](../protect/device-compliance-get-started.md)|
|远程擦除、远程锁定和密码重置|在设备丢失或被盗时，清除敏感数据。 例如，你可以远程锁定设备、将其还原为出厂设置或仅擦除企业数据。<br><br>你可以在用户无法访问其设备时重置密码，锁定遗失或被盗的设备，甚至擦除遗失或被盗设备的数据。|使用[远程锁定](../remote-actions/device-remote-lock.md)和[密码重置](../remote-actions/device-passcode-reset.md)功能帮助保护设备|
|展台模式|允许你锁定移动设备的某些功能，如屏幕捕捉和电源开关。 此外允许您限制设备运行您指定的单个应用程序。 |[Microsoft Intune 中的 iOS 配置策略设置](../configuration/device-restrictions-ios.md)|
|Autopilot 重置|将任务发送到设备以远程启动重置过程，从而使 IT 员工或其他管理员无需访问每台计算机即可启动该过程。 如果设备使用 Autopilot 重置，设备的主要用户将会遭删除。 在重置后登录的下一个用户将被设置为主要用户。|[远程 Windows Autopilot 重置](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset#reset-devices-with-remote-windows-autopilot-reset)|

## <a name="app-management"></a>应用管理

|功能|详细信息|更多信息|
|--------------|-----------|--------------------|
|应用部署和管理|提供了一系列的工具以帮助你在移动应用的整个生命周期中对其进行管理，包括部署来自安装文件和应用商店的应用、对应用状态的详细监视以及应用删除。|[在 Microsoft Intune 中部署应用](../apps/apps-deploy.md)|
|符合和不符合要求的应用程序|你可以指定符合（即允许用户安装）和不符合要求的应用程序（不允许用户安装）的列表。|[Microsoft Intune 中的 iOS 策略设置](../configuration/device-restrictions-ios.md)|
|移动应用程序管理|使用针对所有设备（无论是否由 Intune 托管）的移动应用程序管理配置应用的限制。 你可以通过限制数据的复制粘贴、外部备份和应用之间的数据传输等操作来提高公司数据的安全性。|[在 Microsoft Intune 控制台中配置和部署移动应用程序管理策略](../developer/app-wrapper-prepare-android.md)|
|iOS 移动应用配置|使用移动应用配置策略可提供用户在运行 iOS 应用时可能需要的设置。 例如，某一个应用可能要求用户指定端口号或登录信息。 你可以简化应用配置并减少支持呼叫次数。|[使用 Microsoft Intune 中的移动应用配置策略配置 iOS 应用](../apps/app-configuration-policies-use-ios.md)|
|iOS 移动应用预配配置文件|帮助你将预配配置文件部署到即将到期的 iOS 应用。 |[使用 iOS 移动预配配置文件策略防止应用过期](../apps/app-provisioning-profile-ios.md)|
|托管浏览器|配置托管浏览器策略以控制设备用户可访问的网站。 此外，您可以将移动应用程序管理策略应用到托管浏览器。|[使用 Microsoft Intune 的 Managed Browser 策略管理 Internet 访问](../apps/app-configuration-managed-browser.md)|
|Windows Hello 企业版|让你可以与 Windows Hello 企业版集成，这是一种适用于 Windows 10 的替代登录方法，它使用本地 Active Directory 或 Azure Active Directory 来取代密码、智能卡或虚拟智能卡。|[使用 Microsoft Intune 控制设备上的 Windows Hello 企业版设置](../protect/windows-hello.md)|
|批量购买应用程序|帮助你通过以下操作管理通过批量购买计划购买的应用：从应用商店中导入许可证信息、跟踪已使用的许可证的数量，以及阻止安装超出你所拥有的应用的更多副本。|[使用 Microsoft Intune 管理批量购买的应用](../apps/vpp-apps.md)|

## <a name="company-resource-access"></a>公司资源访问

|功能|详细信息|更多信息|
|--------------|-----------|--------------------|
|证书配置文件|创建和部署受信任的证书配置文件和简单证书注册协议 (SCEP) 证书，这些文件和证书可对 Wi-Fi、VPN 和电子邮件配置文件进行保护和身份验证。|[使用 Microsoft Intune 中的证书配置文件确保资源访问的安全性](../protect/certificates-configure.md)|
|Wi-Fi 配置文件|将无线网络设置部署到你的用户。 通过部署这些设置，你可最小化用户连接到公司网络时所需的工作。|[Microsoft Intune 中的 Wi-Fi 连接](../configuration/wi-fi-settings-configure.md)|
|电子邮件配置文件|创建并将电子邮件设置部署到设备上，以便用户可以在个人设备上访问公司电子邮件，而无需进行任何特殊设置。|[使用 Microsoft Intune 的电子邮件配置文件配置对公司电子邮件的访问](../configuration/email-settings-configure.md)|
|VPN 配置文件|将 VPN 设置部署到用户和你的组织中的设备。 通过部署这些设置，你可以最大限度减少用户连接到公司网络资源需要进行的工作。|[Microsoft Intune 中的 VPN 连接](../configuration/device-profiles.md#vpn)|
|条件访问策略|管理从非 Intune 托管设备对 Microsoft Exchange 电子邮件和 SharePoint Online 进行的访问。|[使用 Microsoft Intune 限制对电子邮件和 SharePoint 的访问](../protect/app-based-conditional-access-intune.md)|

## <a name="next-steps"></a>后续步骤

[查看可管理的设备列表](../remote-actions/device-management.md)。
