---
title: "阻止没有新式身份验证的应用"
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
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: abfb3912ba6dfa6802e1321782afd155a96fbefc
ms.lasthandoff: 04/19/2017


---

# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>阻止不使用现代身份验证 (ADAL) 的应用

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

使用应用保护策略且基于应用的条件性访问依赖于使用[新式身份验证](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a)的应用程序，该验证是 OAuth2 的实现。 最新的 Office 移动和桌面应用程序使用现代身份验证，但是也有第三方应用和较旧 Office 应用使用其他身份验证方法（如基本身份验证和基于表单的身份验证）。

若要阻止对这些应用进行访问，我们建议执行以下操作：

* 安装 ADFS 声明规则以阻止非新式验证协议。 方案 3 中提供了详细的说明 - [阻止除了基于浏览器的应用程序之外的其他所有应用程序访问 O365](https://technet.microsoft.com/library/dn592182.aspx)。
* 对于 **SharePoint Online**，在 SharePoint Online 服务中使用 PowerShell commandlet [Set-SPOTenant](https://technet.microsoft.com/library/fp161390.aspx) 禁用非新式验证以将旧的身份验证协议属性设置为 false：

```
 Set-SPOTenant -LegacyAuthProtocolsEnabled $false
 
```


>[!IMPORTANT]
>基于应用的 CA 不得与基于 Azure Active Directory (Azure AD) 证书的身份验证一起使用。 一次只能配置其中一种。

### <a name="see-also"></a>另请参阅
[仅允许 Intune 支持的应用访问 O365 服务](allow-policy-managed-apps-access-to-o365.md)

