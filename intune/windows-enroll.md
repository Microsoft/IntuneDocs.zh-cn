---
title: 使用 Microsoft Intune 设置 Windows 设备的注册
titlesuffix: ''
description: 设置 Windows 设备的注册。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 896c984cb5831dc84a041d4ad39e4cdf6819f0f8
ms.sourcegitcommit: 820f950d1fc80b1eb5db1b0cf77f44d92a969951
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2018
---
# <a name="set-up-enrollment-for-windows-devices"></a>设置 Windows 设备的注册

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

此主题可帮助 IT 管理员为用户简化 Windows 注册过程。 [设置 Intune](setup-steps.md) 之后，用户便可立即使用其工作或学校帐户进行[登录](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows)并注册 Windows 设备。  

Intune 管理员可通过以下方式简化注册：
- [启用自动注册](#enable-windows-10-automatic-enrollment)（需要 Azure AD Premium）
- [CNAME 注册](#simplify-windows-enrollment-without-azure-ad-premium)
- [启用批量注册](windows-bulk-enroll.md)（需要 Azure AD Premium 和 Windows 配置设计器）
- 当用户注册并查看策略设置的应用进度时，可[添加自定义消息](windows-enrollment-status.md)来问候用户

两个因素决定你简化 Windows 设备注册的方式：

- **是否使用 Azure Active Directory Premium？** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) 随附企业移动性 + 安全性和其他许可计划。
- **用户将注册什么版本的 Windows 客户端？** <br>可通过添加工作或学校帐户自动注册 Windows 10 设备。 早期版本必须使用公司门户应用进行注册。

||**Azure AD Premium**|**其他 AD**|
|----------|---------------|---------------|  
|**Windows 10**|[自动注册](#enable-windows-10-automatic-enrollment) |[用户注册](#enable-windows-enrollment-without-azure-ad-premium)|
|**早期 Windows 版本**|[用户注册](#enable-windows-enrollment-without-azure-ad-premium)|[用户注册](#enable-windows-enrollment-without-azure-ad-premium)|

能够使用自动注册的组织还可通过使用 Windows 配置设计器应用来配置[批量注册设备](windows-bulk-enroll.md)。

**多用户支持**<br>
运行 Windows 10 创意者更新并加入了 Azure Active Directory 域的设备现在支持 Intune 的多用户管理。 当标准用户使用其 Azure AD 凭据登录时，将接收到分配给其用户名的应用和策略。 用户当前无法将公司门户用于自助服务方案，如安装应用。

[!INCLUDE[AAD-enrollment](./includes/win10-automatic-enrollment-aad.md)]

## <a name="simplify-windows-enrollment-without-azure-ad-premium"></a>简化 Windows 注册（不使用 Azure AD Premium）
可以创建自动将注册请求重定向到 Intune 服务器的域名服务器 (DNS) 别名（CNAME 记录类型），从而简化用户注册。 如果不创建 DNS CNAME 资源记录，则尝试连接到 Intune 的用户必须在注册过程中输入 Intune 服务器名称。

**步骤 1：创建 CNAME**（可选）<br>
为公司的域创建 CNAME DNS 资源记录。 例如，如果你的公司网站为 contoso.com，则你将在 DNS 中创建将 EnterpriseEnrollment.contoso.com 重定向到 enterpriseenrollment-s.manage.microsoft.com 的 CNAME。

尽管创建 CNAME DNS 条目是可选的，但 CNAME 记录能够使用户注册更加简便。 如果找不到注册 CNAME 记录，系统会提示用户手动输入 MDM 服务器名称 enrollment.manage.microsoft.com。

|类型|主机名|指向|TTL|
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 小时|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 小时|

如果具有多个 UPN 后缀，你需要为每个域名创建一个 CNAME，并将每个 CNAME 指向 EnterpriseEnrollment-s.manage.microsoft.com。如果 Contoso 的用户使用 name@contoso.com，同时也使用 name@us.contoso.com 和 name@eu.constoso.com 作为其电子邮件或 UPN，则 Contoso DNS 管理员应创建以下 CNAME：

|类型|主机名|指向|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 小时|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 小时|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 小时|

`EnterpriseEnrollment-s.manage.microsoft.com` – 支持从电子邮件的域名重定向到具有域识别的 Intune 服务

对 DNS 记录所做的更改可能最多需要 72 小时才能进行传播。 你无法在 Intune 中验证 DNS 更改，直到 DNS 记录开始进行传播。

**步骤 2：验证 CNAME**（可选）<br>
在 Azure 门户中，选择“更多服务” > “监视 + 管理” > “Intune”。 在 Intune 边栏选项卡上，选择“**注册设备**” > “**Windows 注册**”。 在“指定一个已验证的域名”框中键入公司网站 URL，然后选择“测试自动检测”。

## <a name="tell-users-how-to-enroll-windows-devices"></a>告知用户如何注册 Windows 设备
告诉用户如何注册其 Windows 设备以及在纳入管理之后会出现的情况。

> [!NOTE]
> 最终用户必须通过 Microsoft Edge 访问公司门户网站，才能查看为特定版本的 Windows 分配的 Windows 应用。 Google Chrome、Mozilla Firefox 和 Internet Explorer 等其他浏览器不支持该类型的筛选。

有关最终用户注册说明，请参阅[在 Intune 中注册 Windows 设备](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows)。 还可让用户查看 [IT 管理员可以在我的设备上看的什么](https://docs.microsoft.com/intune-user-help/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows)。

>[!IMPORTANT]
> 如果尚未启用自动 MDM 注册，但是具有已加入到 Azure AD 的 Windows 10 设备，则注册后可在 Intune 控制台中看到两条记录。 确保具有已加入 Azure AD 的设备的用户使用相同的帐户转到“帐户” > “访问工作或学校”和“连接”后，即可停止此操作。 

有关最终用户任务的详细信息，请参阅[有关 Microsoft Intune 最终用户体验的资源](end-user-educate.md)。

## <a name="next-steps"></a>后续步骤

- [在 Azure 上使用 Intune 管理 Windows 设备时的注意事项](/intune-classic/deploy-use/intune-on-azure)。
