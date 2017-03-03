---
title: "阻止没有新式验证的应用 | Microsoft Docs"
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
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 0e1fa2341c0f74492a0ef80d0054922052bbe561


---

# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>阻止不使用现代身份验证 (ADAL) 的应用

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

具有 MAM 策略的应用的条件访问 (MAM CA) 依赖于使用作为 OAuth2 实现的[现代身份验证](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a)的应用程序。 最新的 Office 移动和桌面应用程序使用现代身份验证，但是也有第三方应用和较旧 Office 应用使用其他身份验证方法（如基本身份验证和基于表单的身份验证）。

若要阻止对这些应用进行访问，我们建议执行以下操作：

* 安装 ADFS 声明规则以阻止非新式验证协议。 方案 3 中提供了详细的说明 - [阻止除了基于浏览器的应用程序之外的其他所有应用程序访问 O365](https://technet.microsoft.com/library/dn592182.aspx)。

>[!IMPORTANT]
>MAM CA 不得与基于 Azure Active Directory (Azure AD) 证书的身份验证结合使用。 一次只能配置其中一种。



### <a name="see-also"></a>另请参阅
[仅允许 Intune 支持的应用访问 O365 服务](allow-policy-managed-apps-access-to-o365.md)



<!--HONumber=Dec16_HO2-->


