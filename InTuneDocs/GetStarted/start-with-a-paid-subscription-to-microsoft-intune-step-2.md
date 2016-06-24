---
# required metadata

title: 配置自定义域名 | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# 配置自定义域名

默认情况下，Intune 使用你第一次订阅该服务时创建的 **<domain>onmicrosoft.com** 域名。 如果你的组织拥有自定义域，你可以配置 Intune 的实例来使用该域，而不是使用订阅提供的域名。

在创建新用户帐户或从本地 Active Directory 同步帐户之前，我们强烈建议你决定是仅使用 .onmicrosoft.com 域还是添加一个或多个自定义域名。 添加用户之前配置自定义域使用户能够使用他们用于访问其他域资源的凭据登录，从而帮助简化你的订阅的用户身份管理。

在向 Microsoft 订阅基于云的服务时，该服务的实例将成为为你基于的云服务提供身份和目录服务的 Microsoft [Azure AD 租户](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant)。 由于将 Intune 配置为使用组织自定义域名的任务对于其他 Azure AD 租户都相同，因此你可以使用[添加你的域](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/)中的信息和过程

> 有关将自定义域用于 Microsoft 基于云的服务的详细信息，请参阅 [Conceptual overview of custom domain names in Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/)（Azure Active Directory 中自定义域名的概念性概述）

### 后续步骤
祝贺你！ 你刚刚完成了 *Intune 快速入门指南*的步骤 2

>[!div class="step-by-step"]

>[&larr; **登录到 Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-1.md)     [**将用户添加到 Intune** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-3.md)  


<!--HONumber=May16_HO2-->


