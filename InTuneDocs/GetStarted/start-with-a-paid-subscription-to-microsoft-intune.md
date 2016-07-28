---
title: "Intune 快速入门指南 | Microsoft Intune"
description: "开始使用 Intune 订阅的要求和先决条件"
keywords: 
author: Staciebarker
manager: arob98
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d158503c-1276-422b-ab81-5f66c1cd7e7a
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 376e6c1ae229187ab8ec73390f091f1d534365dd
ms.openlocfilehash: e7ecf24c3fa678e68603f0e3523f2694a73e145c


---


# Intune 快速入门指南
此快速入门指南将引导你完成设置 Microsoft Intune 的付费订阅的步骤，以快速、轻松地管理你的组织使用的移动设备和 Windows 电脑。 你可以按顺序执行每个步骤，也可在某个步骤不适用于你的特定环境或业务需求时直接跳过。

>[!NOTE]
>本文重点介绍将 Intune 设置为独立服务。 或者，如果当前正在使用 Microsoft System Center Configuration Manager 管理计算机和服务器，则可以[扩展 Configuration Manager 以管理移动设备](https://technet.microsoft.com/library/jj884158.aspx)。 可以通过在混合的移动设备管理 (MDM) 部署中将 Intune 与 Configuration Manager 连接来执行此操作。

此快速入门指南中的步骤分享了许多与 [Intune 评估指南](/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune)中相同的步骤。 但是，在完成评估和准备好开始管理移动设备后，你需要满足几个其他要求：

-   使用 Intune 和 Azure Active Directory 同步本地 Active Directory 帐户。

-   更新公共域和域注册机构的 DNS 服务记录。

-   自定义生产用 Intune 功能。

>[!TIP]
>如果在符合条件的计划中购买至少 150 个 Microsoft Intune 的许可证，则可以使用 *FastTrack 中心权益*服务，通过该服务，Microsoft 专家可以和你一起为 Intune 准备好环境。 请参阅 [Microsoft Intune 服务权益说明](https://technet.microsoft.com/library/mt228265.aspx)。


## 在开始之前
请在开始使用付费订阅并已准备好部署 Intune 且对现有网络基础结构进行了更改后使用此指南。 这些任务可能包括上至只需添加或更新你的内部和外部 DNS 记录，下至将现有的 Active Directory 用户帐户同步到 Azure Active Directory 中。 无论决定使用何种 Intune 移动设备管理功能组合，都需要仔细规划将 Intune 与你现有的网络组件和服务进行交互的方式。 具体而言，应查看：

-   **如何管理用户身份**：对于大多数中型到大型组织，使用 Intune 管理用户身份的最佳和最方便的方法是通过 Azure Active Directory 将现有的目录服务连接到 Intune。 如果你已使用其他 Microsoft 云服务（如 Office 365 或 Exchange Online），则上述方法尤其方便实用。 使用 [Microsoft Azure Active Directory Connect](https://www.microsoft.com/download/details.aspx?id=47594) 同步现有的用户帐户是将本地 Active Directory 连接到 Azure Active Directory，并为你的用户配置单一登录身份验证体验的快速而简单的方法。

-   **将如何影响 DNS**：如果你想要使用自己的域名而不是初次注册 Intune 时获取的默认 onmicrosoft.com 域，将需要更新一些公用 DNS 记录。 需要更新 DNS 记录，以便移动设备能找到 Intune 服务并确保订阅的管理服务正确地管理你组织中使用的所有设备。

## 提供以下方便之处
是否已准备好开始？ 开始使用 Intune 的付费订阅时，需要以下各项：

### 一台具有启用 Silverlight 的 Web 浏览器的设备
你需要它来访问用于管理设备、应用和策略的 Intune 管理控制台。 当不从移动设备访问公司门户应用时，你也需要 Web 浏览器来访问基于 Web 的 Intune 公司门户。 为了简化操作，你可以在用于 Intune 管理的同一浏览器上使用“隐私模式”设置（例如：在 Internet Explorer 中，可以依次单击“工具”&gt;“InPrivate 浏览”）。

>[!TIP]
>鉴于此要求，Microsoft Edge 浏览器不支持访问 Intune 管理控制台。


### 移动设备的证书
如果使用 Intune 管理 iOS 或 Windows Phone 设备，你将需要证书和用于检索那些证书的帐户。 不需要任何其他证书即可管理 Android 设备。

- **Windows Phone 8.1** 用户不需要证书即可安装来自应用商店的公司门户应用。 但是，**Windows Phone 8.0** 或使用 Intune 将公司门户应用部署到 Windows Phone 8.1 设备都需要 [Symantec 代码签名证书](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do)。

>[!NOTE]
>本快速入门指南假定用户在 Windows Phone 8.1 或更高版本的设备上从应用商店获取公司门户应用。 有关 Windows Phone 8.0 支持的信息，请参阅[使用 Microsoft Intune 设置 Windows Phone 8.0 管理](/Intune/deploy-use/set-up-windows-phone-8.0-management-with-microsoft-intune)。

- 将 Windows 电脑注册为设备或[为 Microsoft Intune 安装 Windows 电脑客户端](/intune/deploy-use/install-the-windows-pc-client-with-microsoft-intune)时，**Windows 电脑**或 **Windows RT 设备**不需要证书。

- 对于 **iOS** 或 **Mac OS X** 设备，你将需要向 Apple 请求 Apple 推送通知服务证书，如在[使用 Microsoft Intune 设置 iOS 和 Mac 管理](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)的步骤 3 中所述。

## 后续步骤
现在是时候开始使用 Intune 快速入门指南了！

>[!div class="step-by-step"]
[**登录到 Intune** &rarr;](start-with-a-paid-subscription-to-microsoft-intune-step-1.md)



<!--HONumber=Jul16_HO3-->


