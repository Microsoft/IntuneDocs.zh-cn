---
title: "保护电子邮件和 Office 365 | Microsoft Docs"
description: "本主题介绍如何使用条件性访问只允许合规设备在 SharePoint Online 和其他服务上访问公司电子邮件和公司数据。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c564d292-b83b-440d-bf08-3f5b299b7a5e
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 9f05e516723976dcf6862475dbb78f9dce2913be
ms.openlocfilehash: 399c6260a98d51417a067d001c0fd42c926c1513
ms.lasthandoff: 01/24/2017


---

# <a name="protect-access-to-email-office-365-and-other-services-with-microsoft-intune"></a>使用 Microsoft Intune 保护对电子邮件、Office 365 和其他服务的访问

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

通过使用企业移动性 + 安全性 (EMS) 条件访问，可保护对公司电子邮件、Office 365 服务（如 **Exchange 内部部署**、**Exchange Online**、**Exchange Online Dedicated**、**SharePoint Online**、**Skype for Business Online**）以及其他服务的访问。 该功能可确保只有符合在 Intune 管理控制台或 Azure 经典门户中设置的条件性访问规则的设备，才能访问公司电子邮件和 Office 365 服务。
## <a name="how-does-conditional-access-work"></a>条件性访问如何工作？
可使用合规性策略设置评估设备的合规性。 条件性访问策略通过该评估来限制或允许对特定服务的访问。 结合使用条件性访问策略与设备合规性策略时，仅允许合规的设备访问该服务。 将合规性策略和条件访问策略部署到用户。 检查用户用于访问服务的任何设备是否符合策略。

> [!IMPORTANT] 
> 记住，必须向使用该设备的用户部署合规性策略，才能评估设备的合规性。
> 如果未向用户部署合规性策略，该设备将被视为合规且不会对其应用任何访问限制。

当设备不满足策略中设置的条件时，将指导最终用户完成注册设备并修复导致设备不合规问题的过程。

条件性访问的典型工作流：

![图示显示了用于确定是允许还是阻止设备访问服务的决策点](../media/ConditionalAccess4.png)

## <a name="setup-considerations"></a>安装注意事项

### <a name="licensing"></a>许可

Microsoft Intune 与 Azure Active Directory (Azure AD) Premium 无缝地配合工作以便通过 EMS 条件性访问提供多层控制，如果想要使用 Intune部署条件性访问策略，必须先具有这两个产品的许可证。

可以单独购买 **Azure AD Premium 许可证**，也可以作为企业版协议的一部分（与 Intune 一起）购买。 如果使用 Intune 部署条件性访问策略，请确保获得正确的 Azure AD Azure AD Premium 或**EMS 许可证**。

- 了解有关[企业移动性定价页](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility-pricing)或 [Azure Active Directory 定价页](https://azure.microsoft.com/en-us/pricing/details/active-directory/)的详细信息。

此外，请确保将 [Azure AD Premium 或 EMS 许可证](/Intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-4.md)分配给计划应用条件性访问策略的用户。

### <a name="device-compliance-settings"></a>设备合规性设置

若要设置条件性访问，请配置设备合规性策略和条件性访问策略。 合规性策略包括密码、加密以及设备是否已越狱等设置。 设备必须满足这些规则才能视为合规。

- 了解[设备合规性策略及其工作原理](introduction-to-device-compliance-policies-in-microsoft-intune.md)的详细信息。

### <a name="conditional-access-policy"></a>条件性访问策略

可以基于以下内容设置条件性访问策略以保护访问：
- 设备合规性状态。
- 在设备上运行的平台。
- 用于访问服务的应用类型。

与其他 Intune 策略不同，条件性访问策略无需部署。 配置策略并选择应该具有该策略的用户后，将向所有目标用户应用该策略。 如果将某个用户设定为策略的目标，则其使用的每个设备必须合规才能访问资源。


## <a name="next-steps"></a>后续步骤


2. [创建设备合规性策略](create-a-device-compliance-policy-in-microsoft-intune.md)。

2.  为以下任一项 Microsoft 云服务/产品创建条件性访问策略：
> [!div class="op_single_selector"]
  - [为 Exchange Online 创建条件性访问策略](restrict-access-to-exchange-online-with-microsoft-intune.md)
  - [为 Exchange 内部部署创建条件性访问策略](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  - [为新版 Exchange Online Dedicated 创建条件性访问策略](restrict-access-to-exchange-online-with-microsoft-intune.md)
  - [为旧版 Exchange Online Dedicated 创建条件性访问策略](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  - [为 SharePoint Online 创建条件性访问策略](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  - [为 Skype for Business Online 创建条件性访问策略](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
  - [为 Dynamics CRM Online 创建条件性访问策略](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)

