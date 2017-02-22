---
title: "注册 Windows 设备 | Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：启用适用于 Windows 设备的 Intune 移动设备管理 (MDM)。"
keywords: 
author: staciebarker
manager: stabar
ms.date: 02/15/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a4103a4cef393df585b9b9daa92ab63dd7805e9e
ms.openlocfilehash: a55118e60750616f8b058846148364cbeccb5784


---

# <a name="enroll-windows-devices"></a>注册 Windows 设备 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

使用下列方法之一为 Windows 设备设置注册：

- [**使用 Azure Active Directory Premium 自动注册 Windows 10 和 Windows 10 移动版**](#set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium)
 -  此方法仅适用于 Windows 10 和 Windows 10 移动版设备。
 -  必须具有 Azure Active Directory Premium 才能使用此方法。 否则，请使用适用于 Windows 8.1 和 Windows Phone 8.1 的注册方法。
 -  如果选择不启用自动注册，请使用适用于 Windows 8.1 和 Windows Phone 8.1 的注册方法。

- [**通过配置 CNAME 注册 Windows 8.1 和 Windows Phone 8.1**](#set-up-windows-81-and-windows-phone-81-enrollment-by-configuring-cname)
 - 必须使用此方法注册 Windows 8.1 和 Windows Phone 8.1 设备。


## <a name="prerequisites"></a>先决条件

如果 Intune Azure 预览版中尚不具备以下某些先决条件，则需要从经典 Intune 管理控制台执行此操作。

- [配置自定义域名](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [将移动设备管理 (MDM) 机构设置](set-mdm-authority.md)为 **Microsoft Intune**
- [配置公司门户应用](/intune-azure/manage-apps/company-portal-app.md)
- 向用户分配许可证

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="set-up-windows-81-and-windows-phone-81-enrollment-by-configuring-cname"></a>通过配置 CNAME 设置 Windows 8.1 和 Windows Phone 8.1 注册

可以让用户使用 Intune 公司门户安装和注册其设备。 如果创建 DNS CNAME 资源记录，用户即可连接 Intune 并在其中进行注册，而无需输入服务器名称。

1. **创建 CNAME**（可选）<br>
 为公司的域创建 **CNAME** DNS 资源记录。 例如，如果你的公司网站为 contoso.com，则你将在 DNS 中创建将 EnterpriseEnrollment.contoso.com 重定向到 enterpriseenrollment-s.manage.microsoft.com 的 CNAME。

    尽管创建 CNAME DNS 条目是可选的，但 CNAME 记录能够使用户注册更加简便。 如果未找到注册 CNAME 记录，系统会提示用户手动输入 MDM 服务器名称 enrollment.manage.microsoft.com。

    如果存在多个经过验证的域，则为每个域创建一个 CNAME 记录。 CNAME 资源记录必须包含以下信息：

    CNAME 资源记录必须具有以下信息：

  |类型：|主机名|指向|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 小时|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 小时|

  `EnterpriseEnrollment-s.manage.microsoft.com` – 支持从电子邮件的域名重定向到具有域识别的 Intune 服务

  `EnterpriseRegistration.windows.net` – 支持将使用其工作或学校帐户向 Azure Active Directory 注册的 Windows 8.1 和 Windows 10 移动版设备

  如果你的公司对用户凭据使用多个域，则为每个域创建 CNAME 记录。

  例如，如果你的公司网站为 contoso.com，则你将在 DNS 中创建将 EnterpriseEnrollment.contoso.com 重定向到 EnterpriseEnrollment-s.manage.microsoft.com 的 CNAME。 对 DNS 记录所做的更改可能最多需要 72 小时才能进行传播。 你无法在 Intune 中验证 DNS 更改，直到 DNS 记录开始进行传播。

2.  **验证 CNAME**<br>在 [Intune 管理控制台](http://manage.microsoft.com)中，选择“管理”&gt;“移动设备管理”&gt;“Windows Phone”。 在“指定一个已验证的域名”框中输入公司网站经过验证的域的 URL，然后选择“测试自动检测”。

3.  **可选步骤**<br>在 Windows 10 中无需执行**添加旁加载密钥**步骤。 <br>只有在向设备分发 Windows 应用商店中未提供的业务线 (LOB) 应用时才需要执行“上传代码签名证书”步骤。

4.  **告诉用户如何注册其设备以及在纳入管理之后会出现的情况。**

    有关最终用户注册说明，请参阅[在 Intune 中注册 Windows 设备](https://docs.microsoft.com/en-us/intune/enduser/enroll-your-device-in-intune-windows)。 还可以将用户发送到 [IT 管理员可以在我的设备上看到什么](https://docs.microsoft.com/intune/enduser/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows)。

    有关最终用户任务的详细信息，请参阅[有关 Microsoft Intune 最终用户体验的资源](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)。

无需任何额外的工作，除非你要将公司门户部署到设备。  可以安全地忽略管理控制台中的步骤 2 和 3。



<!--HONumber=Feb17_HO3-->


