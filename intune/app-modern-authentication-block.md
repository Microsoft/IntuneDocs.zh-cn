---
title: "屏蔽在 Intune 上不使用现代验证的应用"
description: 
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a6a7cf3b73f4be195b4e07c8c72edeae9fbc9073
ms.sourcegitcommit: 94d3d86f8ae9f82a9872384bbaae53580036a4ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2017
---
# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>屏蔽不使用现代验证 (ADAL) 的应用

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用应用保护策略且基于应用的条件访问依赖使用[现代验证](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a)（即实现 OAuth2）的应用。 虽然目前大部分 Office 移动和桌面应用都使用新式验证，但也有第三方应用和旧版 Office 应用使用其他验证方法（如基本身份验证和基于表单的身份验证）。

若要阻止向这些应用授予访问权限，我们建议执行以下操作：

* 将 ADFS 声明规则设置为阻止非新式验证协议。 情形 3 [阻止所有对 O365 的访问（基于浏览器的应用除外）](https://technet.microsoft.com/library/dn592182.aspx)中提供了详细说明。
* 对于 **SharePoint Online**，在 SharePoint Online 服务中使用 PowerShell commandlet [Set-SPOTenant](https://technet.microsoft.com/library/fp161390.aspx) 禁用非新式验证，从而将旧身份验证协议属性设置为 false：

```
 Set-SPOTenant -LegacyAuthProtocolsEnabled $false

```


>[!IMPORTANT]
>基于应用的 CA 不得与基于 Azure Active Directory (Azure AD) 证书的身份验证结合使用。 一次只能配置其中一种。

### <a name="see-also"></a>另请参阅
[使用 Intune 且基于应用的条件性访问](app-based-conditional-access-intune.md)
