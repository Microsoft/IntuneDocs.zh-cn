---
title: 屏蔽在 Intune 上不使用现代验证的应用
titleSuffix: Microsoft Intune
description: 了解如何屏蔽不使用新式身份验证 (ADAL) 的应用。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 0b74559eb0914d87daabaaad52902547ae7c08ac
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52182034"
---
# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>屏蔽不使用现代验证 (ADAL) 的应用

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

使用应用保护策略且基于应用的条件访问依赖使用[新式身份验证](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a)（即实现 OAuth2）的应用。 目前大部分 Office 移动和桌面应用都使用新式身份验证。 但也有第三方应用和旧版 Office 应用使用其他身份验证方法（如基本身份验证和基于窗体的身份验证）。

要阻止向这些应用授予访问权限，建议使用以下方法：

* 将 ADFS 声明规则设置为阻止非新式验证协议。 情形 3 [阻止所有对 O365 的访问（基于浏览器的应用除外）](https://technet.microsoft.com/library/dn592182.aspx)中提供了详细说明。
* 对于 Exchange 和 SharePoint Online，请使用 Azure Active Directory 条件访问并使用 PowerShell commandlet Set-SPOTenant for SharePoint Online。 有关详细说明，请参阅[为 Azure Active Directory 条件访问设置 SharePoint Online 和 Exchange Online](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication#legacy-authentication-protocols)。


>[!IMPORTANT]
>基于应用的 CA 不得与基于 Azure Active Directory (Azure AD) 证书的身份验证结合使用。 一次只能配置其中一种。

### <a name="see-also"></a>另请参阅
[使用 Intune 且基于应用的条件性访问](app-based-conditional-access-intune.md)
