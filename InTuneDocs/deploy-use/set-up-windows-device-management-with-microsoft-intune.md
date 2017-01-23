---
title: "使用 Microsoft Intune 设置 Windows 设备管理 | Microsoft Docs"
description: "使用 Microsoft Intune 为 Windows 电脑（包括 Windows 10 设备）启用移动设备管理 (MDM)。"
keywords: 
author: staciebarker
manager: stabar
ms.date: 11/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 31d58d9973cca4023186731a5411c9c9e830e32a
ms.openlocfilehash: e24251a066349e23beb94b75a66c5710ba7e41f1


---

# <a name="set-up-windows-device-management"></a>设置 Windows 设备管理

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

作为 Intune 管理员，可以通过两种方式为 Windows 电脑启用注册和管理：

- **[使用 Azure Active Directory 自动注册](#azure-active-directory-enrollment)** - Windows 10 和 Windows 10 移动版用户通过向设备添加工作或学校帐户来注册设备。

- **[公司门户注册](#set-up-company-portal-app-enrollment)** - Windows 8.1 和更高版本的用户通过下载和安装公司门户应用，然后在应用中输入其工作或学校帐户凭据对设备进行注册。

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="set-up-company-portal-app-enrollment"></a>设置公司门户应用注册
可以让用户使用 Intune 公司门户应用安装和注册设备。 如果创建 DNS CNAME 资源记录，用户即可连接 Intune 并在其中进行注册，而无需输入服务器名称。

1. **设置 Intune**<br>
如果尚未设置，请通过[将移动设备管理 (MDM) 机构设置](prerequisites-for-enrollment.md#step-2-set-mdm-authority)为“Microsoft Intune”，然后设置 MDM，为管理移动设备做好准备。

2. **创建 CNAME**（可选）<br>为公司的域创建 **CNAME** DNS 资源记录。 例如，如果公司网站为 contoso.com，则将在 DNS 中创建将 EnterpriseEnrollment.contoso.com 重定向到 enterpriseenrollment-s.manage.microsoft.com 的 CNAME。

    如果你当前在 DNS 中有将 EnterpriseEnrollment.contoso.com 重定向到 manage.microsoft.com 的 CNAME，则我们建议将它替换为 DNS 中将 EnterpriseEnrollment.contoso.com 重定向到 enterpriseenrollment-s.manage.microsoft.com 的 CNAME。 建议进行此更改，因为将针对未来版本中的注册弃用 manage.microsoft.com 终结点。

    CNAME 资源记录必须具有以下信息：

  |类型：|主机名|指向|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 小时|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 小时|

  `EnterpriseEnrollment-s.manage.microsoft.com` – 支持从电子邮件的域名重定向到具有域识别的 Intune 服务

  `EnterpriseRegistration.windows.net` – 支持将使用其工作或学校帐户向 Azure Active Directory 注册的 Windows 8.1 和 Windows 10 移动版设备

  如果你的公司对用户凭据使用多个域，则为每个域创建 CNAME 记录。

  例如，如果你的公司网站为 contoso.com，则你将在 DNS 中创建将 EnterpriseEnrollment.contoso.com 重定向到 EnterpriseEnrollment-s.manage.microsoft.com 的 CNAME。 对 DNS 记录所做的更改可能最多需要 72 小时才能进行传播。 你无法在 Intune 中验证 DNS 更改，直到 DNS 记录开始进行传播。

3.  **验证 CNAME**<br>在 [Intune 管理员控制台](http://manage.microsoft.com)中，选择“管理员”&gt;“移动设备管理”&gt;“Windows”。 在“指定一个已验证的域名”框中输入公司网站经过验证的域的 URL，然后选择“测试自动检测”。

4.  **可选步骤**<br>在 Windows 10 中无需执行**添加旁加载密钥**步骤。 只有在向设备分配 Windows 应用商店中未提供的业务线 (LOB) 应用时才需要执行“上传代码签名证书”步骤。

6.  **告诉用户如何注册其设备以及在纳入管理之后会出现的情况。**

    有关最终用户注册说明，请参阅[在 Intune 中注册 Windows 设备](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows)。

    有关最终用户任务的详细信息，请参阅[有关 Microsoft Intune 最终用户体验的资源](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)。


### <a name="see-also"></a>另请参阅
[在 Microsoft Intune 中注册设备的先决条件](prerequisites-for-enrollment.md)



<!--HONumber=Dec16_HO3-->


