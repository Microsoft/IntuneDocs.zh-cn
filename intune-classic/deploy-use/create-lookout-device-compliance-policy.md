---
title: "启用设备保护规则"
description: "在设备合规性策略中启用移动威胁保护规则。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c951692d-6538-46c0-a9f0-d607ded189ae
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 28ae825a9e33547a1987989d38667417214b97b2
ms.contentlocale: zh-cn
ms.lasthandoff: 06/08/2017


---

# <a name="create-lookout-device-compliance-policy-in-intune"></a>在 Intune 中创建 Lookout 设备符合性策略

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

具备 Lookout 移动威胁防御的 Intune 使你能够检测移动设备上的威胁并评估存在威胁的设备的风险。 可创建评估风险的合规性策略规则，确定设备是否合规。 然后可使用条件性访问策略，根据设备合规性阻止对服务的访问。

包含 Lookout 移动威胁防御的符合性策略的先决条件：

- [设置 Lookout 移动威胁防御订阅](setup-your-lookout-mtd-subscription.md)
- [在 Intune 中启用 Lookout 连接](enable-lookout-mtd-connection.md)
- [配置并部署 Lookout for Work 应用](configure-deploy-lookout-for-work-app.md)

作为 Lookout 移动威胁防御设置过程的一部分，需在 [Lookout 控制台](https://aad.lookout.com)中创建一个将各种威胁分类为高、中和低的策略。 在 Intune 合规性策略中，设置允许的最大威胁级别。

1. 在 [Intune 管理员控制台](https://manage.microsoft.com)中，转到“合规性策略”页。 可使用现有合规性策略或创建新策略。 转到“设备运行状况”并启用“设备威胁防护”。
  ![显示设备威胁保护规则设置的屏幕截图](../media/mtp/mtp-compliance-policy-rule.png)

2. 选择**允许的最大威胁级别**：
  * **无(安全)**：这是最安全的选项。  设备不能存在任何威胁，且仍可访问公司资源。  如果发现了任何威胁，设备都将被视为不合规。  
  * **低**：如果设备上仅存在低级威胁，则该设备为合规。 低级以上的任意威胁都将使设备不合规。
  * **中**：如果设备上发现的威胁为低级别或中等级别，设备为合规。 如果设备中检测到高级威胁，则视为不合格。
  * **高**：这是最不安全的选项。 此选项允许所有威胁级别，且仅将 Lookout 移动威胁防护用作报告目的。

![显示设备威胁保护规则设置威胁等级选项的屏幕截图](../media/mtp/mtp-compliance-policy-setting.png)

如果为 Office 365 或其他服务创建条件性访问策略，将考虑上述合规性评估，阻止不合规的设备访问这些服务，直到解决威胁。

## <a name="monitor-device-threats"></a>监视设备威胁
若要查看设备的合规性状态，请转到 [Intune 管理员控制台](https://manage.microsoft.com)，然后查看“所有设备”。

![Intune 管理员控制台“设备”页面的屏幕截图，其中显示了设备的合规性状态](../media/mtp/mtp-device-status-intune-console.png)

## <a name="next-steps"></a>后续步骤
* 创建条件访问策略
  * [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  * [Exchange 内部部署](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  * [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  * [Skype for Business Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
  * [Dynamics CRM](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)

