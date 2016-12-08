---
title: "Windows 的多重身份验证 | Microsoft Intune"
description: "Intune 集成多重身份验证 (MFA) 来帮助你保护公司资源。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 09/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9b4f197d-bc10-4bee-91c9-19bcc8287d36
ms.reviewer: vinaybha
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ab9ad1fb42176f2fc2babaa6fa3c91cea40b4ca5
ms.openlocfilehash: 1bfd17f9fcc73049254bc77351eae48da874fb4c


---

# <a name="protect-windows-devices-with-multifactor-authentication"></a>Protect Windows devices with multi-factor authentication
Microsoft Intune 集成多重身份验证 (MFA) 来帮助你保护公司资源。 除用户名和密码外，MFA 需要身份验证因素，例如文本身份验证。 Intune 支持在注册 Windows 8.1 或更高版本、Windows Phone 8.1 或 Windows 10 桌面版和移动设备期间使用 MFA。

## <a name="onpremises-infrastructure-requirements-for-adfs-mfa"></a>ADFS MFA 的本地基础结构要求
若要设置 Multi-Factor Authentication，你需要：

-   自动注册，如[设置 Windows 设备管理](set-up-windows-device-management-with-microsoft-intune.md)所述。
-   **ADFS 服务器所加入的 Active Directory 域。**

-   **为 MFA 配置的 Active Directory 联合身份验证服务 (ADFS) 服务器。** 运行 Windows Server 2012 R2 且设置为 ADFS 服务器的服务器。 有关详细信息，请参阅：[将 Azure Multi-Factor Authentication 服务器与 Windows Server 2012 R2 AD FS 配合使用来保护云和本地资源](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-adfs-w2k12/)

服务器必须满足 [Windows Server 2012 R2 的系统要求和安装信息](http://technet.microsoft.com/library/dn303418.aspx)中的系统要求。

 


#### <a name="mfa-with-intune"></a>使用 Intune 的 MFA
如果你的组织具有的本地 IT 基础结构，其中包括 Active Directory 联合身份验证服务 (ADFS) 的 Active Directory 域，则可以在联合服务器上设置 MFA，然后启用 MFA 进行 Intune 注册。 通过在 Intune 上配置 MFA，用户可在注册期间进行一次身份验证，然后便可以使用公司资源而无需每次重复 MFA 过程。

>[!NOTE]
>可以在 ADFS 服务器上基于每个用户或每个组要求进行 MFA。  

#### <a name="mfa-without-intune"></a>未使用 Intune 的 MFA
如果在联合身份验证服务器上设置 MFA，但未启用 MFA 以在 Intune 中注册，则用户需要在每次访问公司资源时（不仅在设备注册时）使用 MFA。

还可以使用 Azure Active Directory (Azure AD) MFA 在用户每次访问公司资源时基于每个用户要求进行 MFA。 Azure AD MFA 是云服务，不需要任何本地 IT 基础结构。 若要了解如何设置 Azure AD MFA，请参阅 [Getting started with Azure Multi-Factor Authentication in the cloud](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-cloud/)（云中的 Azure Multi-Factor Authentication 入门）。

## <a name="requiring-adfs-mfa-during-enrollment-of-windows-devices"></a>在 Windows 设备注册过程中要求使用 ADFS MFA
有关如何启用 ADFS 中的 MFA 的信息，请参阅 [使用附加的 Multi-Factor Authentication 管理敏感应用程序的风险](http://technet.microsoft.com/library/dn280949.aspx)。

## <a name="set-up-device-enrollment-mfa-in-intune"></a>在 Intune 中设置设备注册 MFA
>[!Important]  
>在 Azure AD 租户或本地环境中启用 MFA，然后要求 Intune 在注册 Windows 设备时使用 MFA。 如果不执行此操作，尝试注册其 Windows 设备或尝试将 Azure AD 加入其设备的用户将在 Azure AD 加入期间设置自动注册时收到一条错误消息。

1.  在 Intune 管理控制台中，选择“管理员” &gt;“移动设备管理” &gt;“多重身份验证”。

2.  选择“配置多重身份验证”，然后选择“启用多重身份验证”。



<!--HONumber=Nov16_HO1-->


