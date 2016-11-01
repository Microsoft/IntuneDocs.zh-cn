---
title: "使用 Microsoft Intune 设置 Windows 设备管理 | Microsoft Intune"
description: "使用 Microsoft Intune 为 Windows 电脑（包括 Windows 10 设备）启用移动设备管理 (MDM)。"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: dfc5241376033471a232b059ac07fa4488f05514
ms.openlocfilehash: c405408bd6a1e2b0743566e413436aefbaa7018b


---

# 设置 Windows 设备管理

作为 Intune 管理员，可以通过两种方式为 Windows 电脑启用注册和管理：

- **[使用 Azure Active Directory 自动注册](#azure-active-directory-enrollment)** - Windows 10 和 Windows 10 移动版用户通过向设备添加工作或学校帐户来注册设备
- **[公司门户注册](#company-portal-app-enrollment)** - Windows 8.1 和更高版本的用户通过下载和安装公司门户应用，然后在应用中输入其工作或学校帐户凭据对设备进行注册。

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## 设置公司门户应用注册
可以让用户使用 Intune 公司门户应用安装和注册设备。 如果创建 DNS CNAME 资源记录，用户即可连接 Intune 并在其中进行注册，而无需输入服务器名称。

1. **设置 Intune**<br>
如果尚未设置，请通过[将移动设备管理 (MDM) 机构设置](prerequisites-for-enrollment.md#set-mobile-device-management-authority)为“Microsoft Intune”，然后设置 MDM，为管理移动设备做好准备。

2. **创建 CNAME**（可选）<br>为公司的域创建 **CNAME** DNS 资源记录以简化注册。 尽管创建 CNAME DNS 条目是可选的，但 CNAME 记录能够使用户注册更加简便。 如果未找到注册 CNAME 记录，系统会提示用户手动输入 MDM 服务器名称，`https://manage.microsoft.com`。 CNAME 资源记录必须具有以下信息：

  |类型：|主机名|指向|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 小时|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 小时|

  `EnterpriseEnrollment-s.manage.microsoft.com` – 支持从电子邮件的域名重定向到具有域识别的 Intune 服务

  `EnterpriseRegistration.windows.net` – 支持将使用其工作或学校帐户向 Azure Active Directory 注册的 Windows 8.1 和 Windows 10 移动版设备

  如果你的公司对用户凭据使用多个域，则为每个域创建 CNAME 记录。

  例如，如果你的公司网站为 contoso.com，则你将在 DNS 中创建将 EnterpriseEnrollment.contoso.com 重定向到 EnterpriseEnrollment-s.manage.microsoft.com 的 CNAME。 对 DNS 记录所做的更改可能最多需要 72 小时才能进行传播。 你无法在 Intune 中验证 DNS 更改，直到 DNS 记录开始进行传播。

3.  **验证 CNAME**<br>在 [Intune 管理员控制台](http://manage.microsoft.com)中，选择“管理员”&gt;“移动设备管理”&gt;“Windows”。 在“指定一个已验证的域名”框中输入公司网站经过验证的域的 URL，然后选择“测试自动检测”。

  ![Windows 设备管理对话框](../media/enroll-intune-winenr.png)

4.  **可选步骤**<br>在 Windows 10 中无需执行**添加旁加载密钥**步骤。 只有在向设备分配 Windows 应用商店中未提供的业务线 (LOB) 应用时才需要执行“上传代码签名证书”步骤。 [了解详细信息](set-up-windows-phone-8.0-management-with-microsoft-intune.md)。

6.  **通知用户**<br>需要告诉用户如何注册其设备以及在设备纳入管理之后会出现的情况：
      - [最终用户需要了解的有关 Microsoft Intune 使用的内容](what-to-tell-your-end-users-about-using-microsoft-intune.md)
      - [适用于 Windows 设备的最终用户指南](../enduser/using-your-windows-device-with-intune.md)

### 另请参阅
[在 Microsoft Intune 中注册设备的先决条件](prerequisites-for-enrollment.md)



<!--HONumber=Oct16_HO3-->


