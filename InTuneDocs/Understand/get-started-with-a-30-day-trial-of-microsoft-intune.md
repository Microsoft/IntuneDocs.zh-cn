---
# required metadata

title: Intune 评估指南 | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 619a1d11-3d22-4635-8f70-770eba3e1712

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Intune 评估指南
可快速简单地设置 Intune 的免费 30 天评估，以便管理你的移动设备和计算机。 在评估中只需几个简单的步骤，便可以添加多达 100 个用户和设备、设置组、配置法规遵从性策略并注册和管理移动设备及计算机。

在本主题中，你将学习启动和运行 Intune 评估的基础知识，同时获得服务概述，便于你评估 Intune 的特性和功能。

观看这段五分钟的演示视频，了解如何轻松地开始使用 Microsoft Intune 的免费评估并管理自己的设备：

<iframe width="675" height="480" src="https://www.youtube.com/embed/ltcZvm4VOFU" frameborder="0" allowfullscreen></iframe>

## 在开始之前
开始使用 Intune 之前，你将需要以下各项：

-   一台已启用 Silverlight Web 浏览器的设备，你可以用它来访问你创建 Intune 用户帐户（“Office 365 管理中心”）的网站以及管理设备、组和策略的网站（“Intune 管理控制台”）

-   另一台带有 Web 浏览器的设备，将用它来测试 Intune 用户将如何使用公司门户注册和管理他们的设备。 还将测试用户如何查找和安装应用并向管理员请求帮助。 如果没有另一台设备，则可以在用于 Intune 管理的同一浏览器中使用“隐私模式”设置（例如：在 Internet Explorer 中，可以选择“工具” &gt; “InPrivate 浏览”）

-   如果你有现成的 Microsoft Online Services 帐户，则需要该帐户的管理员凭据。 如果你没有此类帐户或者只是想将此 Intune 租户用于评估目的，则不需要这些管理员凭据。

-   如果使用 Intune 评估管理 iOS 或 Windows Phone 设备，你将需要证书（或密钥）和用于检索那些证书的帐户（请参阅下表）。 Android 设备不需要任何其他证书。

    |平台|证书要求|更多信息|
    |------------|----------------------------|--------------------|
    |Windows Phone 8.1 和 Windows Phone 8 |从商店安装公司门户应用的 Windows Phone 8.1 用户不需要证书。 Windows Phone 8.0 或使用 Intune 将公司门户应用部署到 Windows Phone 8.1 设备都需要 Symantec 证书。|本指南假定用户从 Windows Phone 8.1 或更高版本的设备上的商店获取公司门户应用。 有关 Windows Phone 8.0 支持的信息，请参阅[使用 Microsoft Intune 设置 Windows Phone 管理](/Intune/DeployUse/set-up-windows-phone-management-with-microsoft-intune)|
    |Windows 10、Windows RT 8.1、Windows RT 或 Windows 8.1 设备|注册 Windows RT 和 Windows 设备没有相关的证书要求。|使用 Microsoft Intune 安装 Windows PC 客户端|
    |iOS 7.1 或更高版本|获取 Apple 推送通知服务证书。|向 Apple 请求 Apple Push Notification 服务证书，如下所述：[使用 Microsoft Intune 设置 iOS 和 Mac 管理](/Intune/DeployUse/set-up-ios-and-mac-management-with-microsoft-intune)|

## 用于完成 Intune 的 30 天评估的步骤
- [步骤 1：登录或注册 30 天评估](get-started-with-a-30-day-trial-of-microsoft-intune-step-1.md)。 注册或登录 Intune 之前，应考虑是使用现有帐户登录还是创建仅用于 Microsoft Intune 的 30 天评估的临时帐户。
- [步骤 2：添加用户](get-started-with-a-30-day-trial-of-microsoft-intune-step-2.md)。 完成帐户设置后，会将单个用户帐户添加到 Intune，或批量添加用户（请参阅本部分中的说明）。 开始使用之前，了解 Intune 对管理员帐户的处理方式非常重要。
- [步骤 3：创建用于组织用户和设备的组](get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md)。 Intune 中的组使你能非常灵活地管理设备和用户。 你可以将组设置为适应组织需要（例如，按地理位置、部门或硬件特性）并将其广泛用于执行各种管理任务，上至为一组用户设置策略，下至将应用程序部署到一组设备。
- [步骤 4：创建策略并发布应用](get-started-with-a-30-day-trial-of-microsoft-intune-step-4.md)。 Intune 策略提供的设置有助于控制移动设备上的安全设置、维护计算机的 Windows 防火墙和 Endpoint Protection 设置以及部署应用程序。
- [步骤 5：注册移动设备并安装应用](get-started-with-a-30-day-trial-of-microsoft-intune-step-5.md)。 若要使用 Intune 设置移动设备管理，必须设置移动设备管理机构，为特定设备平台启用管理，然后使用公司门户应用注册设备。 然后，你可以部署自己发布的 Microsoft Skype 应用。
- [步骤 6：其他选项和其他功能](get-started-with-a-30-day-trial-of-microsoft-intune-step-6.md)。 选择如何使用警报、报告和其他 Intune 功能以满足业务需求。
- [步骤 7：后续步骤](get-started-with-a-30-day-trial-of-microsoft-intune-step-7.md)。 准备移动到 Intune 付费订阅并利用 Intune FastTrack 中心权益。


### 后续步骤
现在可以开始使用 30 天评估订阅！

>[!div class="step-by-step"]

### 注册 Intune
[另请参阅](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune)


<!--HONumber=May16_HO2-->


