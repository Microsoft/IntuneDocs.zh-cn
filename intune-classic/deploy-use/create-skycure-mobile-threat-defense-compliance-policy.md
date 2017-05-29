---
title: "创建 Skycure 移动威胁防御符合性策略 | Microsoft Docs"
description: "在 Intune 经典控制台中创建 Skycure 移动威胁防御符合性策略。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 56ff1728-1119-4e8a-aae6-ed5c7fafa052
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 54c36ffaee24ed7643bf8d64c52084d66550b240
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="create-skycure-mobile-threat-defense-compliance-policy"></a>创建 Skycure 移动威胁防御符合性策略

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

具备 Skycure 移动威胁防御的 Intune 使你能够检测移动设备上的威胁并评估存在威胁的设备的风险。 可创建评估风险的 Intune 符合性策略规则，确定设备是否符合。 然后可使用条件性访问策略，根据设备合规性阻止对服务的访问。

## <a name="before-you-begin"></a>在开始之前

包含 Skycure 设备威胁防护的符合性策略的先决条件：

-   [使用 Intune 设置 Skycure 集成](/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune)

-   [在 Intune 中启用 Skycure 连接](/intune-classic/deploy-use/enable-skycure-mobile-threat-defense-in-intune)

作为 Skycure 移动威胁防御设置过程的一部分，需在 Skycure 控制台中创建一个将各种威胁分类为高、中和低的策略。 现在需要在 Intune 符合性策略中设置允许的最大威胁级别。

## <a name="to-create-skycure-compliance-policy"></a>创建 Skycure 符合性策略

1.  转到“[Intune 经典控制台](https://manage.microsoft.com/)”，然后输入你的凭据。

2.  选择“策略”&gt;“符合性策略”。 可使用现有合规性策略或创建新策略。

3.  选择“添加”&gt;“设备运行状况”，然后启用“设备威胁防护”。

4.  选择**允许的最大威胁级别**：

    a.  **无(安全)**：这是最安全的选项。 设备不能存在任何威胁，且仍可访问公司资源。 如果发现了任何威胁，设备都将被视为不合规。

    b。  **低**：如果设备上仅存在低级威胁，则该设备为合规。 低级以上的任意威胁都将使设备不合规。

    c.  **中**：如果设备上发现的威胁为低级别或中等级别，设备为合规。 如果设备中检测到高级威胁，则视为不合格。

    d.  **高**：这是最不安全的选项。 此选项允许所有威胁级别，且仅将 Skycure 移动威胁防御用作报告目的。

> [!IMPORTANT]
> 如果为 Office 365 或其他服务创建条件性访问策略，将考虑上述合规性评估，阻止不合规的设备访问这些服务，直到解决威胁。

## <a name="span-idmonitor-device-threats-classanchorspan-idnext-steps-classanchorspan-idtoc477360344-classanchorspanspanspannext-steps"></a><span id="monitor-device-threats" class="anchor"><span id="next-steps" class="anchor"><span id="_Toc477360344" class="anchor"></span></span></span>后续步骤

-   为以下各项创建条件访问策略：

    -   [Exchange Online](/intune-classic/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
    -   [Exchange 内部部署](/intune-classic/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
    -   [SharePoint Online](/intune-classic/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)
    -   [Skype for Business Online](/intune-classic/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune)
    -   [Dynamics CRM](/intune-classic/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune)

