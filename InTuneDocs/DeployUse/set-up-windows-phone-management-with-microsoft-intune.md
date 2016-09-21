---
title: "设置 Windows 10 移动版和 Windows Phone 管理 | Microsoft Intune"
description: "使用 Microsoft Intune 为 Windows 10 移动版或 Windows Phone 设备启用移动设备管理 (MDM)。"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5615051-2dd1-453b-9872-d3fdcefb2cb8
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ebb1648ab13d31a2ba1ab17615814be8dda8a08c
ms.openlocfilehash: 76aaa33832dc1b765e248f85f739a4955ca90e2d


---


# 使用 Microsoft Intune 设置 Windows Phone 和 Windows 10 移动版管理

作为 Intune 管理员，你可以通过两种方式为 Windows 10 移动版和 Windows Phone 设备启用注册和管理：

- **[使用 Azure AD 自动注册](#azure-active-directory-enrollment)** - Windows 10 和 Windows 10 移动版用户通过向设备添加工作或学校帐户来注册设备
- **[公司门户注册](#company-portal-app-enrollment)** - Windows Phone 8.1 和更高版本设备通过下载和安装公司门户应用，然后在应用中输入其工作或学校帐户凭据进行注册。


[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## 公司门户应用注册
可以让用户使用 Intune 公司门户应用安装和注册设备，从而注册他们的设备。 创建 DNS CNAME 可帮助用户进行连接 Intune 并在其中进行注册，而无需输入服务器名称。 如果你管理 Windows Phone 8.0 设备或需要将公司门户部署到 Windows Phone 设备，则必须下载公司门户应用并对其进行签名。 请参阅[设置 Windows Phone 8.0 管理](set-up-windows-phone-8.0-management-with-microsoft-intune.md)。

1.  **设置 Intune**<br>如果你尚未设置，请通过[将移动设备管理机构设置](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority)为“Microsoft Intune”并设置 MDM，为管理移动设备做好准备。

2.  **创建 CNAME**（可选）<br>为公司的域创建 **CNAME** DNS 资源记录。 例如，你的公司网站为 contoso.com，则你将在 DNS 中创建将 EnterpriseEnrollment.contoso.com 重定向到 manage.microsoft.com 的 CNAME。 如果存在多个经过验证的域，则为每个域创建一个 CNAME 记录。 CNAME 资源记录必须包含以下信息：

  |类型：|主机名|指向|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 小时|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 小时|
  DNS 记录更改可能最多需要 72 小时才能进行传播。 你无法在 Intune 中验证 DNS 更改，直到 DNS 记录开始进行传播。

  `EnterpriseEnrollment-s.manage.microsoft.com` – 支持从电子邮件的域名重定向到具有域识别的 Intune 服务

  `EnterpriseRegistration.windows.net` – 支持将使用其工作或学校帐户向 Azure Active Directory 注册的 Windows 8.1 和 Windows 10 移动版设备

  如果你的公司对用户凭据使用多个域，则为每个域创建 CNAME 记录。

  例如，如果你的公司网站为 contoso.com，则你将在 DNS 中创建将 EnterpriseEnrollment.contoso.com 重定向到 EnterpriseEnrollment-s.manage.microsoft.com 的 CNAME。 DNS 记录更改可能最多需要 72 小时才能进行传播。 你无法在 Intune 中验证 DNS 更改，直到 DNS 记录开始进行传播。

3.  **验证 CNAME**<br>在 [Intune 管理控制台](http://manage.microsoft.com)中，单击**管理** &gt; **移动设备管理** &gt; **Windows Phone**。 在**指定一个已验证的域名**框中键入公司网站结果验证的域的 URL，然后单击**测试自动检测**。

    ![设置 Windows 的移动设备管理对话框](../media/windows-phone-enrollment.png)

4.  **可选步骤**<br>在 Windows 10 中无需执行**添加旁加载密钥**步骤。 只有在向 Windows 应用商店中未提供的设备分配业务线 (LOB) 应用时才需要执行**上载代码签名证书**步骤。 [了解详细信息](set-up-windows-phone-8.0-management-with-microsoft-intune.md)

5.  **通知用户**<br>你的用户将需要了解注册其设备的方式以及他们纳入管理之后会出现的情况。
    - [最终用户需要了解的有关 Microsoft Intune 使用的内容](what-to-tell-your-end-users-about-using-microsoft-intune.md)
    - [适用于 Windows 设备的最终用户指南](../enduser/using-your-windows-device-with-intune.md)

无需任何额外的工作，除非你要将公司门户部署到设备。  可以安全地忽略管理控制台中的步骤 2 和 3。



<!--HONumber=Aug16_HO5-->


