---
title: "使用 Microsoft Intune 设置 Windows 设备管理 | Microsoft Docs"
description: "使用 Microsoft Intune 为 Windows 设备启用移动设备管理 (MDM)。"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 02/26/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 255c3e47464ac7670a971881cf399e8e2bb17044
ms.openlocfilehash: 4acbae2aba4cff21286d45cb7cb1691864c281dc
ms.lasthandoff: 02/28/2017


---

# <a name="set-up-windows-device-management"></a>设置 Windows 设备管理

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

使用下列方法之一为 Windows 设备设置注册：

- [**使用 Azure Active Directory Premium 自动注册 Windows 10 和 Windows 10 移动版**](#set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium)
 -  此方法仅适用于 Windows 10 和 Windows 10 移动版设备。
 -  必须具有 Azure Active Directory Premium 才能使用此方法。 否则，请使用适用于 Windows 8.1 和 Windows Phone 8.1 的注册方法。
 -  如果选择不启用自动注册，请使用适用于 Windows 8.1 和 Windows Phone 8.1 的注册方法。


- [**通过配置 CNAME 注册 Windows 8.1 和 Windows Phone 8.1**](#set-up-windows-81-and-windows-phone-81-enrollment-by-configuring-cname)
 - 必须使用此方法注册 Windows 8.1 和 Windows Phone 8.1 设备。

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="set-up-windows-81-and-windows-phone-81-enrollment-by-configuring-cname"></a>通过配置 CNAME 设置 Windows 8.1 和 Windows Phone 8.1 注册
可以让用户使用 Intune 公司门户安装和注册其设备。 如果创建 DNS CNAME 资源记录，用户即可连接 Intune 并在其中进行注册，而无需输入服务器名称。

### <a name="step-1-set-up-intune"></a>步骤 1：设置 Intune

如果尚未设置，请通过[将移动设备管理 (MDM) 机构设置](prerequisites-for-enrollment.md#step-2-set-mdm-authority)为“Microsoft Intune”，然后设置 MDM，为管理移动设备做好准备。

### <a name="step-2-create-cnames-optional"></a>步骤 2：创建 CNAME（可选）

为公司的域创建 **CNAME** DNS 资源记录。 例如，如果你的公司网站为 contoso.com，则你将在 DNS 中创建将 EnterpriseEnrollment.contoso.com 重定向到 enterpriseenrollment-s.manage.microsoft.com 的 CNAME。


   尽管创建 CNAME DNS 条目是可选的，但 CNAME 记录能够使用户注册更加简便。 如果未找到注册 CNAME 记录，系统会提示用户手动输入 MDM 服务器名称 enrollment.manage.microsoft.com。

   CNAME 资源记录必须具有以下信息：

  |类型：|主机名|指向|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 小时|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 小时|

  `EnterpriseEnrollment-s.manage.microsoft.com` – 支持从电子邮件的域名重定向到具有域识别的 Intune 服务

  `EnterpriseRegistration.windows.net` – 支持将使用其工作或学校帐户向 Azure Active Directory 注册的 Windows 8.1 和 Windows 10 移动版设备

  如果你的公司对用户凭据使用多个域，则为每个域创建 CNAME 记录。

  例如，如果你的公司网站为 contoso.com，则你将在 DNS 中创建将 EnterpriseEnrollment.contoso.com 重定向到 EnterpriseEnrollment-s.manage.microsoft.com 的 CNAME。 对 DNS 记录所做的更改可能最多需要 72 小时才能进行传播。 你无法在 Intune 中验证 DNS 更改，直到 DNS 记录开始进行传播。

### <a name="step-3-verify-cname"></a>步骤 3：验证 CNAME

在 [Intune 管理员控制台](http://manage.microsoft.com)中，选择“管理员”&gt;“移动设备管理”&gt;“Windows”。 在“指定一个已验证的域名”框中输入公司网站经过验证的域的 URL，然后选择“测试自动检测”。

### <a name="step-4-tell-your-users-how-to-enroll-their-devices-and-what-to-expect-after-theyre-brought-into-management"></a>步骤 4：告诉用户如何注册其设备以及在纳入管理之后会出现的情况。

   有关最终用户注册说明，请参阅[在 Intune 中注册 Windows 设备](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows)。

   有关最终用户任务的详细信息，请参阅[如何使最终用户了解 Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune) 和[适用于 Windows 设备的最终用户指南](../enduser/using-your-windows-device-with-intune.md)。

### <a name="see-also"></a>另请参阅
[在 Microsoft Intune 中注册设备的先决条件](prerequisites-for-enrollment.md)

