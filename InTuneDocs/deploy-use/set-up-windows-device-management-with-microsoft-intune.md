---
title: "使用 Microsoft Intune 设置 Windows 设备管理 | Microsoft Docs"
description: "使用 Microsoft Intune 为 Windows 设备启用移动设备管理 (MDM)。"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 03/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 771aed4e1c57171183b9a9ea7d9e0f702dc1859c
ms.openlocfilehash: f6014c5500b05762d123b2285ef859d67382e402
ms.lasthandoff: 04/06/2017


---

# <a name="set-up-windows-device-management"></a>设置 Windows 设备管理

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

使用下列方法之一为 Windows 设备设置注册：

- [**使用 Azure Active Directory Premium 自动注册 Windows 10**](#set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium)
 -  此方法仅适用于 Windows 10 设备。
 -  必须具有 Azure Active Directory Premium 才能使用此方法。
 -  如果选择不启用自动注册，请使用适用于 Windows 8.1 和 Windows Phone 8.1 的注册方法。

- [**不具备 Azure AD Premium 自动注册的注册**](#enable-windows-enrollment-without-azure-ad-premium)
 - 必须使用此方法注册 Windows 8.1 和 Windows Phone 8.1 设备。
 - 如果不想使用 Azure Active Directory (AD) Premium，可以将此方法用于 Windows 8.1 以及更高版本的设备。

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="enable-windows-enrollment-without-automatic-enrollment"></a>启用 Windows 注册（不使用自动注册）
可以让用户安装和注册其设备，而无需自动注册 Azure AD Premium。 将许可证分配给用户帐户后，用户可以将该帐户添加到 Windows 设备，并同意注册管理中的设备。 如果创建 DNS CNAME 资源记录，用户即可连接 Intune 并在其中进行注册，而无需输入服务器名称。

**步骤 1：创建 CNAME**（可选）<br>
为公司的域创建 CNAME DNS 资源记录。 例如，如果你的公司网站为 contoso.com，则你将在 DNS 中创建将 EnterpriseEnrollment.contoso.com 重定向到 enterpriseenrollment-s.manage.microsoft.com 的 CNAME。

尽管创建 CNAME DNS 条目是可选的，但 CNAME 记录能够使用户注册更加简便。 如果未找到注册 CNAME 记录，系统会提示用户手动输入 MDM 服务器名称 enrollment.manage.microsoft.com。

如果存在多个经过验证的域，则为每个域创建一个 CNAME 记录。 CNAME 资源记录必须包含以下信息：

CNAME 资源记录必须具有以下信息：

|类型：|主机名|指向|TTL|
|--------|-------------|-------------|-------|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 小时|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 小时|

`EnterpriseEnrollment-s.manage.microsoft.com` – 支持从电子邮件的域名重定向到具有域识别的 Intune 服务

如果你的公司对用户凭据使用多个域，则为每个域创建 CNAME 记录。

例如，如果你的公司网站为 contoso.com，则你将在 DNS 中创建将 EnterpriseEnrollment.contoso.com 重定向到 EnterpriseEnrollment-s.manage.microsoft.com 的 CNAME。 对 DNS 记录所做的更改可能最多需要 72 小时才能进行传播。 你无法在 Intune 中验证 DNS 更改，直到 DNS 记录开始进行传播。

**步骤 2：验证 CNAME**（可选）<br>
在 [Intune 管理员控制台](http://manage.microsoft.com)中，选择“管理员”&gt;“移动设备管理”&gt;“Windows”。 在“指定一个已验证的域名”框中输入公司网站经过验证的域的 URL，然后选择“测试自动检测”。

## <a name="tell-users-how-to-enroll-windows-devices"></a>告知用户如何注册 Windows 设备
告诉用户如何注册其 Windows 设备以及在纳入管理之后会出现的情况。
有关最终用户注册说明，请参阅[在 Intune 中注册 Windows 设备](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows)。 还可以将用户发送到 [IT 管理员可以在我的设备上看到什么](https://docs.microsoft.com/intune/enduser/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows)。

有关最终用户任务的详细信息，请参阅[有关 Microsoft Intune 最终用户体验的资源](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)。

### <a name="see-also"></a>另请参阅
[在 Microsoft Intune 中注册设备的先决条件](prerequisites-for-enrollment.md)

