---
title: "注册 Windows 设备"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：启用适用于 Windows 设备的 Intune 移动设备管理 (MDM)。"
keywords: 
author: nathbarn
manager: nathbarn
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 687be18cedd063b3c2701937f2522e801e51644b
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="enroll-windows-devices"></a>注册 Windows 设备

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

此主题可帮助 IT 管理员为用户简化 Windows 注册过程。  无需任何其他步骤即可注册 Windows 设备，但你还可为用户简化注册过程。

运行 Windows 10 创意者更新并加入了 Azure Active Directory 域的设备现在支持 Intune 的多用户管理。 这意味着当不同的标准用户使用其 Azure AD 凭据登录设备时，他们将收到分配给其用户名的所有应用和策略。 用户当前无法将公司门户用于自助服务方案，如安装应用。

两个因素决定你简化 Windows 设备注册的方式：

- **是否使用 Azure Active Directory Premium？** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) 随附企业移动性 + 安全性和其他许可计划。
- **将注册什么版本的 Windows？** <br>可通过添加工作或学校帐户自动注册 Windows 10 设备。 早期版本必须使用公司门户应用进行注册。

||**Azure AD Premium**|**其他 AD**|
|----------|---------------|---------------|  
|**Windows 10**|[自动注册](#enable-windows-10-automatic-enrollment) |[用户注册](#enable-windows-enrollment-without-azure-ad-premium)|
|**早期 Windows 版本**|[用户注册](#enable-windows-enrollment-without-azure-ad-premium)|[用户注册](#enable-windows-enrollment-without-azure-ad-premium)|

[!INCLUDE[AAD-enrollment](./includes/win10-automatic-enrollment-aad.md)]

## <a name="enable-windows-enrollment-without-azure-ad-premium"></a>启用 Windows 注册（不使用 Azure AD Premium）
无需 Azure AD Premium 自动注册即可让用户注册其设备。 分配许可证后，用户即可在将他们的工作帐户添加到其个人拥有的设备后或在将其企业拥有的设备加入到你的 Azure AD 后进行注册。 创建 DNS 别名（CNAME 记录类型）使用户能更轻松地注册其设备。 如果创建 DNS CNAME 资源记录，用户即可连接 Intune 并在其中进行注册，而无需输入 Intune 服务器名称。

**步骤 1：创建 CNAME**（可选）<br>
为公司的域创建 CNAME DNS 资源记录。 例如，如果你的公司网站为 contoso.com，则你将在 DNS 中创建将 EnterpriseEnrollment.contoso.com 重定向到 enterpriseenrollment-s.manage.microsoft.com 的 CNAME。

尽管创建 CNAME DNS 条目是可选的，但 CNAME 记录能够使用户注册更加简便。 如果找不到注册 CNAME 记录，系统会提示用户手动输入 MDM 服务器名称 enrollment.manage.microsoft.com。

|类型|主机名|指向|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 小时|

如果具有多个 UPN 后缀，你需要为每个域名创建一个 CNAME，并将每个 CNAME 指向 EnterpriseEnrollment-s.manage.microsoft.com。 例如，如果 Contoso 的用户使用 name@contoso.com，但也使用 name@us.contoso.com 和 name@eu.constoso.com 作为其电子邮件/UPN，则 Contoso DNS 管理员需要创建以下 CNAME。

|类型|主机名|指向|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 小时|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 小时|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 小时|

`EnterpriseEnrollment-s.manage.microsoft.com` – 支持从电子邮件的域名重定向到具有域识别的 Intune 服务

对 DNS 记录所做的更改可能最多需要 72 小时才能进行传播。 你无法在 Intune 中验证 DNS 更改，直到 DNS 记录开始进行传播。

**步骤 2：验证 CNAME**（可选）<br>
在 Azure Intune 门户中，选择“更多服务” > “监视 + 管理” > “Intune”。 在 Intune 边栏选项卡上，选择“**注册设备**” > “**Windows 注册**”。 在“指定一个已验证的域名”框中输入公司网站经过验证的域的 URL，然后选择“测试自动检测”。

## <a name="tell-users-how-to-enroll-windows-devices"></a>告知用户如何注册 Windows 设备
告诉用户如何注册其 Windows 设备以及在纳入管理之后会出现的情况。 有关最终用户注册说明，请参阅[在 Intune 中注册 Windows 设备](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows)。 还可以告诉用户 [IT 管理员可以在我的设备上看到什么](https://docs.microsoft.com/intune-user-help/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows)。

有关最终用户任务的详细信息，请参阅[有关 Microsoft Intune 最终用户体验的资源](https://docs.microsoft.com/intune-classic/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)。

