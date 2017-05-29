---
title: "推动最终用户采用条件访问 | Microsoft Docs"
description: "本文旨在提供有关如何利用条件访问推动 Intune 注册的见解。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c2d7ce3f-fe97-4044-ad9e-25ac8fa301c9
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 55e437fa33af9d27223798cbac9f541b0bc1be2d
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="phase-2-drive-end-user-adoption-with-conditional-access"></a>阶段 2：推动最终用户采用条件访问

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

通过 Intune 启用条件访问功能（例如，阻止未注册设备的电子邮件）有助于推动注册和符合性，但成功迁移不需要这些功能。 迁移采用目标和安全要求应指示成功。

## <a name="migration-campaign-with-conditional-access"></a>使用条件访问的迁移活动

下面是使用条件访问促进迁移活动的典型方法：

1.  设置条件访问规则，对所有用户强制实施，但明确排除需要从旧的 MDM 提供程序迁移的用户。 可以为条件访问排除的所有用户创建 Azure AD 用户组。

2.  用户迁移时，将他们从条件访问排除组中删除。

3.  迁移完成后，将所有条件访问策略配置为默认阻止，除非 Intune 允许访问。

### <a name="advantages"></a>优点

-   为新用户帐户或不受此前解决方案管理的用户帐户提供访问控制。

-   为此前解决方案的用户提供宽限期以进行迁移。

-   尽量避免降低工作效率

### <a name="disadvantages"></a>缺点

-   在对此前解决方案的用户启用条件访问之前，他们可能无法使用非管理设备访问资源。

> [!TIP]
> 这是众多方法之一。 你可以选择一个更简单的过程来延迟所有条件访问，直到指示每个阶段进行注册，也可以选择一个更为严格的过程，从一开始就强制实施条件访问并要求所有访问完全具备符合性。

-   了解有关[条件性访问](https://docs.microsoft.com/intune/conditional-access)的详细信息。

## <a name="task-list-for-conditional-access"></a>条件访问的任务列表

### <a name="task-1-get-ready-for-intune-conditional-access"></a>任务 1：准备好进行 Intune 条件访问

-   了解[如何配置条件访问](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)。

### <a name="task-2-set-up-intune-conditional-access"></a>任务 2：设置 Intune 条件访问

选择以下任一条件访问策略类型并了解详细信息：

-   [Exchange Online 和新的 Exchange Online 专用](/intune-classic/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)

-   [本地 Exchange 和旧版 Exchange Online专用](/intune-classic/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)

-   [SharePoint Online](/intune-classic/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)

-   [Skype for Business Online](/intune-classic/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune)

-   [Dynamics CRM Online](/intune-classic/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune)

-   [示例电子邮件访问情形](/intune-classic/deploy-use/restrict-email-access-example-scenarios)

## <a name="next-steps"></a>后续步骤

[阶段 2：典型迁移周期](/intune-classic/plan-design/migration-phase2-typical-migration-cycle)

