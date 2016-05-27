---
# required metadata

title: Microsoft Intune 的域名 | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: c3c136f0-330d-432a-a91f-16f7dd097e55

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---



# Microsoft Intune 的域名

设置 Microsoft Intune 之前，请查看本主题以及[启动 Microsoft Intune 前须知](what-to-know-before-you-start-microsoft-intune.md)中列出的其他要求

当你的组织注册 Microsoft 提供的基于云的服务（如 Intune）时，将向你提供一个如下所示的初始域名：**contoso.onmicrosoft.com**。 在此示例中， **contoso** 是你在注册时选择的域名，**onmicrosoft.com** 是分配给你添加到订阅的帐户的后缀。 完成注册过程后，将无法更改该域名。 不过，作为全局管理员，你可以添加自己的自定义域名供组织用于服务，或者可以删除你以前添加的域。

默认情况下，当你使用 onmicrosoft 域时，你导入的每个用户都将为其用户主体名称 (UPN) 收到 **onmicrosoft.com** 后缀。

若要使用你拥有的域名，而不使用在注册时提供的域名，你可以将域名添加到 Active Directory。 添加了域并且经过验证你拥有该域后，你可通过在 DNS 托管提供者处更改 DNS 资源记录来创建包括域名的帐户和组。 要在你计划使用自定义域时简化用户帐户管理，请在开始从本地 Active Directory 同步用户之前，将自定义域名配置到你的订阅。

为 Intune 配置域名和 DNS 资源记录与为 Azure Active Directory 租户进行的配置相同。 有关说明，请参阅[添加自定义域名以简化使用 Azure Active Directory 进行的登录](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/)。

### 另请参阅
[启动 Microsoft Intune 前须知](what-to-know-before-you-start-microsoft-intune.md)


<!--HONumber=May16_HO2-->


