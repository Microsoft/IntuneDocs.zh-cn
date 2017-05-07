---
title: "对 O365 进行基于应用的条件性访问"
description: "了解 MAM CA 如何帮助控制有权访问 O365 服务的应用的概念。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/05/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bd6bee60-5e39-42c8-a2e9-f5865ac3573f
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: 8fc53e8717277a4075bc7ecde31fd60c3539a5f7
ms.lasthandoff: 04/19/2017


---

# <a name="allow-only-mobile-apps-that-support-intune-app-protection-policies-to-access-office-365-services"></a>仅允许支持 Intune 应用保护策略的移动应用访问 Office 365 服务

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

[Intune 应用保护策略](protect-apps-and-data-with-microsoft-intune.md)可帮助保护在 Intune 中注册进行管理的设备上的公司数据。 还可在 **Intune 中注册进行管理的员工自有设备**上使用应用保护策略。  在这种情况下，即使不管理该设备，仍需要确保公司数据和资源受保护。 使用基于应用的 MAM 条件性访问，可创建相应策略，仅允许支持 Intune 应用保护策略的移动应用访问 O365 服务（如 Exchange Online）。

例如，通过仅允许 **Microsoft Outlook 应用**访问 Exchange Online，可以**阻止 iOS 和 Android 上的内置邮件应用**，这些应用不具有 Intune MAM 策略提供的数据保护，从而无法从 **Exchange Online** 获取电子邮件。 或者可以阻止不受 Intune MAM 支持的移动应用访问 **SharePoint Online**。

下图说明了基于应用的条件性访问策略采用何种流程来确定何时允许或阻止访问：![显示是否允许访问时的各种必备条件的图表](../media/mam-ca-decision-flow_simple.png)。

图表中使用的缩写的说明：
* **CP**：公司门户应用
* **AA**：Azure Authenticator 应用
* **AAD**：Azure Active Directory
* **EAS**：Exchange Active Sync

## <a name="prerequisites"></a>先决条件
创建基于应用的条件性访问策略**之前**，必须具有**“企业移动性 + 安全性”或 Azure Active Directory Premium 订阅**，且用户必须获得 EMS 或 Azure AD 许可。 有关详细信息，请参阅[企业移动性定价页](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing)或 [Azure Active Directory 定价页](https://azure.microsoft.com/pricing/details/active-directory/)。


## <a name="supported-apps"></a>受支持的应用
**Exchange Online**：
* 适用于 Android 和 iOS **Microsoft Outlook**。

**SharePoint Online**
* 适用于 iOS 和 Android 的 Microsoft Word
* 适用于 iOS 和 Android 的 Microsoft Excel
* 适用于 iOS 和 Android 的 Microsoft PowerPoint
* 适用于 iOS 和 Android 的 Microsoft OneDrive for Business
* 适用于 iOS 的 Microsoft OneNote

>[!IMPORTANT]
>对于 Android 设备，必须通过登录到 OneDrive 应用或 Outlook 应用完成初始设备注册。 在没有注册的情况下，适用于 Android 的 OneNote 应用尚不支持 MAM。

若要了解应用具有基于应用的条件性访问策略时的用户使用体验如何，请参阅[将应用与 MAM CA 结合使用时预期会出现的情况](use-apps-with-mam-ca.md)。


## <a name="next-steps"></a>后续步骤
[为 MAM 应用创建 Exchange Online 策略](mam-ca-for-exchange-online.md)

[为 MAM 应用创建 SharePoint Online 策略](mam-ca-for-sharepoint-online.md)

[阻止不具有新式验证的应用](block-apps-with-no-modern-authentication.md)

### <a name="see-also"></a>另请参阅

[使用应用保护策略保护应用数据](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

