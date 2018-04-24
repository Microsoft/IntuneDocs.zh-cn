---
title: 使用 Microsoft Intune 设置 Windows 设备管理
description: 使用 Microsoft Intune 为 Windows 设备启用移动设备管理 (MDM)。
keywords: ''
author: NathBarn
manager: angrobe
ms.date: 03/20/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: fb2d724cc87ffdc506eda8d5ea2330ab9aacd3e9
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="set-up-windows-device-management"></a>设置 Windows 设备管理

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

本主题可帮助 IT 管理员为用户提供经过简化的 Windows 注册过程。  无需任何其他步骤即可注册 Windows 设备，但你还可为用户简化注册过程。

两个因素决定你简化 Windows 设备注册的方式：
- **是否使用 Azure Active Directory Premium？** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) 随附企业移动性 + 安全性和其他许可计划。
- **将注册什么版本的 Windows？** <br>可通过添加工作或学校帐户自动注册 Windows 10 设备。 早期版本必须使用公司门户应用进行注册。

||**Azure AD Premium**|**其他 AD**|
|----------|---------------|---------------|  
|**Windows 10**|[自动注册](#enable-windows-10-automatic-enrollment) |[用户注册](#enable-windows-enrollment-without-automatic-enrollment)|
|**早期 Windows 版本**|[用户注册](#enable-windows-enrollment-without-automatic-enrollment)|[用户注册](#enable-windows-enrollment-without-automatic-enrollment)|

[!INCLUDE [AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="enable-windows-enrollment-without-automatic-enrollment"></a>在不使用自动注册的情况下启用 Windows 注册
无需 Azure AD Premium 自动注册即可让用户注册其设备。 分配许可证后，用户即可在将他们的工作帐户添加到其个人拥有的设备后或在将其企业拥有的设备加入到你的 Azure AD 后进行注册。 创建 DNS 别名（CNAME 记录类型）可以简化用户注册其设备的过程。 如果创建 DNS CNAME 资源记录，用户即可连接 Intune 并在其中进行注册，而无需输入 Intune 服务器名称。

**第 1 步：创建 CNAME**（可选）<br>
为公司的域创建 CNAME DNS 资源记录。 例如，如果你的公司网站为 contoso.com，则你将在 DNS 中创建将 EnterpriseEnrollment.contoso.com 重定向到 enterpriseenrollment-s.manage.microsoft.com 的 CNAME。

尽管创建 CNAME DNS 条目是可选的，但 CNAME 记录能够使用户注册更加简便。 如果找不到注册 CNAME 记录，系统会提示用户手动输入 MDM 服务器名称 enrollment.manage.microsoft.com。

如果存在多个经过验证的域，则为每个域创建一个 CNAME 记录。 CNAME 资源记录必须包含以下信息：

CNAME 资源记录必须包含以下信息：

|类型：|主机名|指向|TTL|
|--------|-------------|-------------|-------|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 小时|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 小时|

`EnterpriseEnrollment-s.manage.microsoft.com` – 支持从电子邮件的域名重定向到具有域识别的 Intune 服务

如果公司对用户凭据使用多个域，请为每个域创建 CNAME 记录。

例如，如果公司网站为 contoso.com，则需要在 DNS 中创建将 EnterpriseEnrollment.contoso.com 重定向到 EnterpriseEnrollments.manage.microsoft.com 的 CNAME。对 DNS 记录所做的更改可能最多需要 72 小时才能进行传播。 你无法在 Intune 中验证 DNS 更改，直到 DNS 记录开始进行传播。

**步骤 2：验证 CNAME**（可选）<br>
在 [Intune 管理控制台](https://manage.microsoft.com)中，依次选择“管理”&gt;“移动设备管理”&gt;“Windows”。 在“指定验证域名”框中输入公司网站的验证域的 URL，然后选择“测试自动检测”。

## <a name="tell-users-how-to-enroll-windows-devices"></a>告诉用户如何注册 Windows 设备
告诉用户如何注册其 Windows 设备以及在纳入管理之后会出现的情况。
有关最终用户注册说明，请参阅[在 Intune 中注册 Windows 设备](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows)。 还可以将用户发送到 [IT 管理员可以在我的设备上看到什么](https://docs.microsoft.com/intune-user-help/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows)。

若要详细了解最终用户任务，请参阅 [Microsoft Intune 最终用户体验的相关资源](/intune/end-user-educate)。

### <a name="see-also"></a>另请参阅
[在 Microsoft Intune 中注册设备的先决条件](prerequisites-for-enrollment.md)
