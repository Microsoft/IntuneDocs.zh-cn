---
title: "屏蔽不使用新式验证的应用"
description: 
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 098b652c-01e0-45d1-a731-620b0d3dc7c1
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: e10453155343bb7fd91a4fd3874d393ef78d0b1a
ms.openlocfilehash: 0f192c0e41cf3b639cbfdac3f8c4fc3b8167266d
ms.contentlocale: zh-cn
ms.lasthandoff: 04/25/2017


---

# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>屏蔽不使用新式验证 (ADAL) 的应用

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

使用应用保护策略且基于应用的条件访问依赖使用[新式验证](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a)（即实现 OAuth2）的应用。 虽然目前大部分 Office 移动和桌面应用都使用新式验证，但也有第三方应用和旧版 Office 应用使用其他验证方法（如基本身份验证和基于表单的身份验证）。

若要阻止向这些应用授予访问权限，我们建议执行以下操作：

* 将 ADFS 声明规则设置为阻止非新式验证协议。 情形 3 [阻止所有对 O365 的访问（基于浏览器的应用除外）](https://technet.microsoft.com/library/dn592182.aspx)中提供了详细说明。
* 对于 **SharePoint Online**，在 SharePoint Online 服务中使用 PowerShell commandlet [Set-SPOTenant](https://technet.microsoft.com/library/fp161390.aspx) 禁用非新式验证，从而将旧身份验证协议属性设置为 false：

```
 Set-SPOTenant -LegacyAuthProtocolsEnabled $false

```


>[!IMPORTANT]
>基于应用的 CA 不得与基于 Azure Active Directory (Azure AD) 证书的身份验证结合使用。 一次只能配置其中一种。

### <a name="see-also"></a>另请参阅
[仅允许 Intune 支持的应用访问 O365 服务](allow-policy-managed-apps-access-to-o365.md)

