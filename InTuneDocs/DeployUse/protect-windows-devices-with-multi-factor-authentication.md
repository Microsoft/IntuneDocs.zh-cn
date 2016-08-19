---
title: "Windows 的多重身份验证 | Microsoft Intune"
description: "Intune 集成多重身份验证 (MFA) 来帮助你保护公司资源。"
keywords: 
author: Nbigman
manager: Arob98
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9b4f197d-bc10-4bee-91c9-19bcc8287d36
ms.reviewer: vinaybha
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 72288296d966b9b9fae4fd721b4460528213f626
ms.openlocfilehash: c2c1a35152dc0f9ec9464c056fed3300540bf33c


---

# Protect Windows devices with multi-factor authentication
Microsoft Intune 集成多重身份验证 (MFA) 来帮助你保护公司资源。 除用户名和密码外，MFA 需要身份验证因素，例如文本身份验证。 Intune 支持在注册 Windows 8.1 或更高版本、Windows Phone 8.1 或 Windows 10 桌面版和移动设备期间使用 MFA。 

## ADFS MFA 的本地基础结构要求
若要设置 Multi-Factor Authentication，你需要：

-   **ADFS 服务器所加入的 Active Directory 域。**

-   **配置 Active Directory 联合身份验证服务 (ADFS) 服务器，用于 MFA。** 运行 Windows Server 2012 R2 的服务器，将它设置为 ADFS 服务器。 有关详细信息，请参阅：[将 Azure Multi-Factor Authentication 服务器与 Windows Server 2012 R2 AD FS 配合使用来保护云和本地资源](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-adfs-w2k12/)

所有上面列出的服务器必须满足 [Windows Server 2012 R2 的系统要求和安装信息](http://technet.microsoft.com/library/dn303418.aspx)中提供的系统要求。

#### 使用 Intune 的 MFA
如果你的组织具有的本地 IT 基础结构包括 Active Directory 联合身份验证服务的 Active Directory 域，则可以在联合服务器上配置 MFA，然后启用 MFA 以进行 Intune 注册。 通过在 Intune 上配置 MFA，可以使用户在注册期间进行一次身份验证，然后便可以访问公司资源而无需每次重复 MFA 过程。

>[!NOTE]
>可以在 ADFS 服务器上基于每个用户或每个组要求进行 MFA。  

#### 未使用 Intune 的 MFA
如果你在联合身份验证服务器上配置 MFA，但未启用 MFA 以在 Intune 中注册，则用户将需要在其每次访问公司资源时（不仅在设备注册时）使用 MFA。

还可以使用 Azure Active Directory (AAD) MFA 在每次用户访问公司资源时基于每个用户要求 MFA。 AAD MFA 是云服务，它不需要任何本地 IT 基础结构。 若要了解如何设置 AAD MFA，请参阅[云中的 Azure Multi-Factor Authentication 入门](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-cloud/)。

## 在 Windows 设备注册过程中要求使用 ADFS MFA
有关如何启用 ADFS 中的 MFA 的信息，请参阅 [使用附加的 Multi-Factor Authentication 管理敏感应用程序的风险](http://technet.microsoft.com/library/dn280949.aspx)。

## 在 Intune 中设置设备注册 MFA
>[!Important]  
>在 Azure AD 租户或本地环境中启用 MFA，然后要求 Intune 在注册 Windows 设备时使用 MFA。 如果不执行此操作，用户在尝试注册其 Windows 设备或尝试将 Azure AD 加入其设备时（如果在 Azure AD 加入期间配置自动注册）将收到一条错误消息。

1.  在 Intune 管理控制台中，单击**管理员** &gt; **移动设备管理** &gt; **多重身份验证**。

2.  单击**配置多重身份验证**，然后单击**启用多重身份验证**。




<!--HONumber=Jul16_HO3-->


