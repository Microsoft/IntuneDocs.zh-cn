---
title: 注册或登录到 Microsoft Intune
description: 如何注册 Microsoft Intune 订阅或登录以开始你的订阅。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f3ce07a-b718-42a9-bace-f99a8b8abd94
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 78d38b72c9853a9eadaf71fcdff7567fc66d35ca
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "73414673"
---
# <a name="sign-up-or-sign-in-to-microsoft-intune"></a>注册或登录到 Microsoft Intune

本主题指导系统管理员如何注册 Intune 帐户。

注册 Intune 之前，请确定是否已有 Microsoft Online Services 帐户、企业协议或等效的批量许可协议。 Microsoft 批量许可协议或其他 Microsoft 云服务订阅（如 Office 365）通常包含工作或学校帐户。

如果已有工作或学校帐户，请使用该帐户进行“登录”，并将 Intune 添加到订阅中  。 否则，也可通过“注册”创建新帐户，以便为组织使用 Intune  。

>[!WARNING]
>注册新帐户后，不能合并现有的工作或学校帐户。

## <a name="how-to-sign-up-for-intune"></a>如何注册 Intune

1. 请访问 [Intune 注册页](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20)。

   ![Microsoft Intune 试用版帐户注册网页的屏幕截图](./media/account-sign-up/account-sign-up-site.png)

2. 在“注册”页上登录或注册以管理 Intune 的新订阅。

## <a name="post-sign-up-considerations"></a>注册后的注意事项

注册新订阅后，在注册过程中提供的电子邮件地址将收到一封含有帐户信息的电子邮件。 这封电子邮件将确认你的订阅处于活动状态。

完成注册过程后，系统会定向到 Microsoft 365 管理中心，在此处可添加用户并为其分配许可证。 如果只有使用默认 onmicrosoft.com 域名的基于云的帐户，此时就可以继续操作，并添加用户和分配许可证。 但是，如果要使用组织的[自定义域名](custom-domain-name-configure.md)，或者从本地 Active Directory [同步用户帐户信息](users-add.md#sync-active-directory-and-add-users-to-intune)，则可关闭该浏览器窗口。

## <a name="sign-in-to-microsoft-intune"></a>登录 Microsoft Intune

注册 Intune 后，可以使用任何装有[受支持的浏览器](supported-devices-browsers.md#intune-supported-web-browsers)设备登录 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)，以管理服务。

默认情况下，你的帐户必须在 Azure AD 中具有下列权限之一：

- 全局管理员
- Intune 服务管理员（也称为 Intune 管理员）

若要为具有其他权限的用户授予管理服务的访问权限，请参阅[基于角色的访问控制](role-based-access-control.md)

### <a name="intune-admin-portal-url"></a>Intune 管理门户 URL

Microsoft 365 管理中心： https://devicemanagement.microsoft.com

Intune Azure 门户： https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade

Intune for Education： https://intuneeducation.portal.azure.com

Intune 经典门户： https://manage.microsoft.com Intune 经典门户仅用于管理向 Intune PC 软件客户端注册的设备

### <a name="urls-for-intune-services-provided-by-office-365"></a>Office 365 提供的 Intune 服务的 URL

Microsoft 365 商业版： https://portal.microsoft.com/adminportal

Office 365 移动设备管理： https://portal.office.com/adminportal/home#/MifoDevices

## <a name="see-also"></a>另请参阅

[无法登录 Office 365、Azure 或 Intune](https://support.microsoft.com/help/2412085)
