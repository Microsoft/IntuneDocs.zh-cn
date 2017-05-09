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
ms.translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: f1291d6eec32ad834d33fcbfff320ce173521a25
ms.contentlocale: zh-cn
ms.lasthandoff: 04/24/2017


---

# <a name="set-up-windows-device-management"></a>设置 Windows 设备管理

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本主题可帮助 IT 管理员为用户提供经过简化的 Windows 注册过程。  无需执行其他任何步骤，即可注册 Windows 设备，为用户提供更简单的注册过程。

两个因素决定了简化 Windows 设备注册的方式：
- **是否使用 Azure Active Directory Premium？** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) 随附企业移动性 + 安全性和其他许可计划。
- **将注册什么版本的 Windows？** <br>可通过添加工作或学校帐户自动注册 Windows 10 设备。 早期版本必须使用公司门户应用进行注册。

||**Azure AD Premium**|**其他 AD**|
|----------|---------------|---------------|  
|**Windows 10**|[自动注册](#enable-windows-10-automatic-enrollment) |[用户注册](#enable-windows-enrollment-without-azure-ad-premium)|
|**早期 Windows 版本**|[用户注册](#enable-windows-enrollment-without-azure-ad-premium)|[用户注册](#enable-windows-enrollment-without-azure-ad-premium)|

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="enable-windows-enrollment-without-automatic-enrollment"></a>在不使用自动注册的情况下启用 Windows 注册
可以让用户在不使用 Azure AD Premium 自动注册的情况下注册其设备。 分配许可证后，用户可以在将其工作帐户添加到其个人拥有的设备或将其公司拥有的设备加入你的 Azure AD 后进行注册。 创建 DNS 别名（CNAME 记录类型）可以简化用户注册其设备的过程。 如果创建 DNS CNAME 资源记录，用户即可连接 Intune 并在其中进行注册，而无需输入 Intune 服务器名称。

**第 1 步：创建 CNAME**（可选）<br>
为公司的域创建 CNAME DNS 资源记录。 例如，如果你的公司网站为 contoso.com，则你将在 DNS 中创建将 EnterpriseEnrollment.contoso.com 重定向到 enterpriseenrollment-s.manage.microsoft.com 的 CNAME。

虽然可选择性创建 CNAME DNS 条目，但 CNAME 记录可简化用户的注册。 如果找不到注册 CNAME 记录，系统会提示用户手动输入 MDM 服务器名称 enrollment.manage.microsoft.com。

如果存在多个经过验证的域，则为每个域创建一个 CNAME 记录。 CNAME 资源记录必须包含以下信息：

CNAME 资源记录必须包含以下信息：

|类型：|主机名|指向|TTL|
|--------|-------------|-------------|-------|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 小时|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 小时|

`EnterpriseEnrollment-s.manage.microsoft.com` – 支持从电子邮件的域名重定向到具有域识别的 Intune 服务

如果公司对用户凭据使用多个域，请为每个域创建 CNAME 记录。

例如，如果公司网站为 contoso.com，则需要在 DNS 中创建将 EnterpriseEnrollment.contoso.com 重定向到 EnterpriseEnrollments.manage.microsoft.com 的 CNAME。 对 DNS 记录所做的更改可能最多需要 72 小时才能进行传播。 你无法在 Intune 中验证 DNS 更改，直到 DNS 记录开始进行传播。

**第 2 步：验证 CNAME**（可选）<br>
在 [Intune 管理控制台](https://manage.microsoft.com)中，依次选择“管理”&gt;“移动设备管理”&gt;“Windows”。 在“指定验证域名”框中输入公司网站的验证域的 URL，然后选择“测试自动检测”。

## <a name="tell-users-how-to-enroll-windows-devices"></a>告诉用户如何注册 Windows 设备
告诉用户如何注册 Windows 设备以及在纳入管理之后会出现的情况。
有关最终用户注册说明，请参阅[在 Intune 中注册 Windows 设备](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows)。 还可以将用户定向到[我的 IT 管理员可以在我的设备上看到的内容](https://docs.microsoft.com/intune/enduser/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows)。

若要详细了解最终用户任务，请参阅 [Microsoft Intune 最终用户体验的相关资源](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)。

### <a name="see-also"></a>另请参阅
[在 Microsoft Intune 中注册设备的先决条件](prerequisites-for-enrollment.md)

