---
title: "Microsoft Intune 的域名 | Microsoft Intune"
description: 
keywords: 
author: andredm7
manager: swadhwa
ms.date: 06/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c3c136f0-330d-432a-a91f-16f7dd097e55
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3d99669f90fe7ebec7854b7a800b09b0685c314e
ms.openlocfilehash: aaede1500f28c6eb8c2a21924d7c3b7f633eca26


---



# 使用 Microsoft Intune 管理自定义域

可以选择在 [Azure Active Directory 中执行](https://azure.microsoft.com/en-us/documentation/articles/active-directory-add-domain/)添加和验证自定义域的步骤。

当你的组织注册 Microsoft 提供的基于云的服务（如 Intune）时，你将获得一个 Azure Active Directory 中托管的初始域名，其形式如下所示：**yourdomain.onmicrosoft.com**。 在此示例中，**yourdomain** 是你在注册时选择的域名，**onmicrosoft.com** 是分配给你添加到订阅的帐户的后缀。

你无法重命名或删除该初始域名。 但是，你可以添加、验证或删除你自己的用于 Intune 的自定义域名，这对于想要保留业务标识非常有用。

## 添加和验证自定义域 

1. 转到 [Office 365 管理门户](https://portal.office.com/Admin/Default.aspx)并登录到你的管理员帐户。
    > [!IMPORTANT]
    > 查看     [Intune 帐户门户已与 Office 365 管理门户合并](https://docs.microsoft.com/en-us/intune/deploy-use/account-portal-merged-with-Office-365)公告，获取有关在何处管理 Microsoft Intune 用户、组和域的详细信息。
2. 在导航窗格中，选择“设置”&gt;“域”。
3. 选择“添加域”，然后键入你的自定义域名。
4. “验证域”对话框将打开，为你提供用于在 DNS 托管提供者中创建 TXT 记录的值。
    > [!TIP]
    > 使用 GoDaddy 域时，Office 365 管理门户会将你重定向到 GoDaddy 的登录页。 输入你的凭据并接受域更改权限协议后，将自动创建 TXT 记录。
    > 
    > 你还可以根据此步骤中提供的值，[在使用 GoDaddy 域时手动创建 TXT 记录](https://support.office.com/en-us/article/Create-DNS-records-at-GoDaddy-for-Office-365-f40a9185-b6d5-4a80-bb31-aa3bb0cab48a?ui=en-US&rs=en-US&ad=US)。

    > [!NOTE]
    > 根据此步骤中提供的值，在使用 Register.com 域时按照[分步说明](https://support.office.com/en-us/article/Create-DNS-records-at-Register-com-for-Office-365-55bd8c38-3316-48ae-a368-4959b2c1684e?ui=en-US&rs=en-US&ad=US#BKMK_verify)创建 TXT 记录。

5. 在 DNS 托管提供者中进行更改时，确保为 [Windows 设备注册](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune)创建 DNS 别名 (CNAME)。

在混合云方案中，添加自定义域名并验证你的组织拥有它后，你可以继续管理本地 Active Directory 中的用户帐户，然后将其与 Azure AD 同步。

## 将本地用户与 Azure AD 同步##

1. 在本地 Active Directory 中，为你的自定义域[添加 UPN 后缀](https://technet.microsoft.com/en-us/library/cc772007.aspx)。
2. 为计划导入的本地用户设置新的 UPN 后缀。
3. 运行 [Azure AD Connect 同步](https://azure.microsoft.com/en-us/documentation/articles/active-directory-aadconnect/)，以将本地用户与 Azure AD 集成。
4. 成功同步用户帐户信息后，你可以使用 [Office 365 管理门户](https://portal.office.com/Admin/Default.aspx)分配 Microsoft Intune 许可证。

### 另请参阅

[有关 Office 365 中的初始 onmicrosoft.com 域](https://support.office.com/en-us/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A?ui=en-US&rs=en-US&ad=US)

[开始使用 Microsoft Intune 前须知](what-to-know-before-you-start-microsoft-intune.md)



<!--HONumber=Jun16_HO5-->


