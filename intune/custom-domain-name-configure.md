---
title: "配置自定义域名"
description: "向你的 Intune 订阅添加自定义域名"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/07/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3
ms.reviewer: angerobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d75292ce60eb1db232aed12fc80a7cbccc063fb4
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="configure-a-custom-domain-name"></a>配置自定义域名

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

本主题指导管理员如何创建 DNS CNAME 以简化和自定义其登录体验。

当你的组织注册 Microsoft 提供的基于云的服务（如 Intune）时，你将获得一个 Azure Active Directory (AD) 中托管的初始域名，其形式如下所示：**yourdomain.onmicrosoft.com**。 在此示例中，**yourdomain** 是你在注册时选择的域名，**onmicrosoft.com** 是分配给你添加到订阅的帐户的后缀。 如果你的组织拥有自定义域，你可以配置 Intune 的实例来使用该域，而不是使用订阅提供的域名。

在创建用户帐户或同步本地 Active Directory 之前，我们强烈建议你决定是仅使用 .onmicrosoft.com 域还是添加一个或多个自定义域名。 添加用户之前配置自定义域使用户能够使用他们用于访问其他域资源的凭据登录，从而帮助简化你的订阅的用户身份管理。

在向 Microsoft 订阅基于云的服务时，该服务的实例将成为为你基于的云服务提供身份和目录服务的 Microsoft [Azure AD 租户](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant)。 由于将 Intune 配置为使用组织自定义域名的任务对于其他 Azure AD 租户都相同，因此你可以使用[添加你的域](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/)中的信息和过程。

> [!TIP]
> 有关将自定义域用于 Microsoft 基于云的服务的详细信息，请参阅 [Conceptual overview of custom domain names in Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/)（Azure Active Directory 中自定义域名的概念性概述）。

你无法重命名或删除该初始域名。 但是，你可以添加、验证或删除你自己的用于 Intune 的自定义域名，这对于想要保留业务标识非常有用。

## <a name="to-add-and-verify-your-custom-domain"></a>添加和验证自定义域

1. 转到 [Office 365 管理门户](https://portal.office.com/Admin/Default.aspx)并登录到你的管理员帐户。

2. 在导航窗格中，选择“设置”&gt;“域”。

3. 选择“添加域”，然后键入你的自定义域名。

4. “验证域”对话框将打开，为你提供用于在 DNS 托管提供者中创建 TXT 记录的值。
    - **GoDaddy 用户**：Office 365 管理门户会将你重定向到 GoDaddy 的登录页。 输入你的凭据并接受域更改权限协议后，自动创建 TXT 记录。 你还可以[创建 TXT 记录](https://support.office.com/article/Create-DNS-records-at-GoDaddy-for-Office-365-f40a9185-b6d5-4a80-bb31-aa3bb0cab48a)。
    - **Register.com 用户**：按照[分步说明](https://support.office.com/article/Create-DNS-records-at-Register-com-for-Office-365-55bd8c38-3316-48ae-a368-4959b2c1684e#BKMK_verify)创建 TXT 记录。

也可在 [Azure Active Directory 中执行](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/)添加和验证自定义域的步骤。

可了解更多[关于 Office 365 中的初始 onmicrosoft.com 域](https://support.office.com/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A)的信息
