---
title: 基于应用的 Intune 条件访问
titleSuffix: Microsoft Intune
description: 了解基于应用的条件访问如何与 Intune 协作。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b399fba0-5dd4-4777-bc9b-856af038ec41
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f0b5e67c433f2d3633219650f48307dccae196e9
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "73713291"
---
# <a name="app-based-conditional-access-with-intune"></a>基于应用的 Intune 条件访问

[Intune 应用保护策略](../apps/app-protection-policy.md)可帮助保护在 Intune 中已注册设备上的公司数据。 另外，应用保护策略还可用在没有注册 Intune 进行管理的员工自有设备上。 在这种情况下，即使你的公司不管理该设备，仍需要确保公司数据和资源受保护。

通过确保仅支持 Intune 应用保护策略的客户端应用可以访问 Exchange Online 和其他 Office 365 服务，基于应用的条件访问和客户端应用管理增加了一个安全层。

> [!NOTE]
> 受管理应用是一种自身执行应用保护策略的应用，可由 Intune 管理。

仅允许 Microsoft Outlook 应用访问 Exchange Online 时，可阻止 iOS 和 Android 上的内置邮件应用。 此外，你还可以阻止未执行 Intune 应用保护策略的应用访问 SharePoint Online。

## <a name="prerequisites"></a>必备条件

在创建基于应用的条件访问策略之前，必须具有：

- 企业移动性 + 安全性 (EMS) 或 Azure Active Directory (AD) 高级订阅  
- 必须向用户授予 EMS 或 Azure AD 许可

有关详细信息，请参阅[企业移动性定价](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing)或 [Azure Active Directory 定价](https://azure.microsoft.com/pricing/details/active-directory/)。

## <a name="supported-apps"></a>受支持的应用

可以在 [Azure Active Directory 条件访问技术参考文档](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference)中找到支持基于应用的条件访问的应用列表。

基于应用的条件访问[还支持业务线 (LOB) 应用](app-modern-authentication-block.md)，但这些应用需要使用 [Office 365 现代身份验证](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a)。 

## <a name="how-app-based-conditional-access-works"></a>基于应用的条件访问的工作方式

在此示例中，管理员将应用保护策略应用到 Outlook 应用，然后应用条件访问规则，将 Outlook 应用添加到可在访问公司电子邮件时使用的已批准的应用列表。

> [!NOTE]
> 以下流程图可用于其他托管的应用。

![流程图中所示的基于应用的条件访问过程](./media/app-based-conditional-access-intune/ca-intune-common-ways-3.png)

1. 用户尝试从 Outlook 应用对 Azure AD 进行身份验证。

2. 首次尝试身份验证时，用户将被重定向到应用商店来安装代理应用。 代理应用可以是适用于 iOS 的 Microsoft Authenticator，也可以是适用于 Android 设备的 Microsoft 公司门户。

   如果用户尝试使用本机电子邮件应用，则将被重定向到应用商店，然后安装 Outlook 应用。

3. 在设备上安装代理应用。

4. 代理应用将启动 Azure AD 注册进程，在 Azure AD 中创建一个设备记录。 这与移动设备管理 (MDM) 注册过程不同，但此记录是必需的，用于在设备上强制执行条件访问策略。

5. 代理应用将验证应用程序的身份。 有一个安全层，以便代理应用可验证该应用是否授权用户使用。

6. 代理应用将应用客户端 ID 作为用户身份验证过程的一部分发送到 Azure AD，以查看其是否存在于策略批准列表中。

7. Azure AD 允许用户根据策略批准列表验证并使用应用。 如果列表中没有此应用，Azure AD 将拒绝对其进行访问。

8. Outlook 应用与 Outlook 云服务通信，启动与 Exchange Online 的通信。

9. Outlook 云服务与 Azure AD 通信，以为用户检索 Exchange Online 服务访问令牌。

10. Outlook 应用与 Exchange Online 通信，检索用户的公司电子邮件。

11. 将企业电子邮件发送到用户的邮箱。

## <a name="next-steps"></a>后续步骤
[创建基于应用的条件访问策略](app-based-conditional-access-intune-create.md)

[阻止不具有新式验证的应用](app-modern-authentication-block.md)
