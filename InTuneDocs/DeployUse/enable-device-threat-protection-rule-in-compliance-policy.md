---
title: "在合规性策略中启用设备保护规则 | Microsoft Intune"
description: "在设备合规性策略中启用移动威胁保护规则。"
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c951692d-6538-46c0-a9f0-d607ded189ae
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9bf5764d1e1bd73fd62e5033b2309fc8d5a912e4
ms.openlocfilehash: ec287d49910a72c22122f45a01850bcbd3a7d203


---

# <a name="enable-device-threat-protection-rule-in-the-compliance-policy"></a>在合规性策略中启用设备威胁保护规则
通过附带 Lookout 移动威胁保护的 Intune，可检测设备上的移动威胁并进行风险评估。 可以创建合规性策略规则，使其包含风险评估，以便确定设备是否合规。 然后可通过条件访问策略，根据设备合规性允许或阻止访问 Exchange、SharePoint 及其他服务。

要使 Lookout 设备威胁检测影响设备的合规性策略，请执行以下操作：

* 必须在在合规性策略中启用“设备威胁保护”规则。

* “Intune 管理员控制台”中的“Lookout 状态”页必须显示“活动”。 请参阅[在 Intune 中启用 Lookout MTP 连接](enable-lookout-mtp-connection-in-intune.md)主题，了解有关如何激活 Lookout 集成的更多详细信息和介绍。


在合规性策略中创建设备威胁防护规则前，建议[为订阅设置 Lookout 设备威胁保护](set-up-your-subscription-with-lookout-mtp.md)、[在 Intune 中启用 Lookout 连接](enable-lookout-mtp-connection-in-intune.md)并[配置 Lookout for Work 应用](configure-and-deploy-lookout-for-work-apps.md)。 仅在设置完成后才会执行合规性规则。

若要启用设备威胁保护规则，可使用现有合规性策略或创建新策略。

作为 Lookout 设备威胁保护设置的一部分，需在 [Lookout 控制台](https://aad.lookout.com)中创建将各种威胁分为高级、中级和低级的策略。 在 Intune 合规性策略中，将用威胁等级设置允许的最高威胁等级。

在“Intune 管理员控制台”的“合规性策略”页面，转到“设备运行状况”，并使用切换选项启用“设备威胁防护”规则。 然后从以下选项选择允许的最高威胁等级：
* **无(安全)**：这是最安全的选项。  这意味着该设备不能具有任何威胁。  如果设备中存在所有级别的威胁，则会被视为不合规。  
* **低**：如果设备上仅存在低级威胁，则该设备视为合规。 低级以上的任意威胁都将使设备不合规。
* **中**：如果设备上存在的威胁为低级或中级，也被视为合规。 如果设备中检测到高级威胁，则视为不合格。
* **高**：这是最不安全的选项。 本质上而言，此选项允许所有威胁等级，可能仅在将此解决方案用于报告时有用。

![显示设备威胁保护规则设置的屏幕截图 ](../media/mtp/mtp-compliance-policy-rule.png)

![显示设备威胁保护规则设置威胁等级选项的屏幕截图](../media/mtp/mtp-compliance-policy-setting.png)

如果为 Office 365 或其他设备创建条件访问策略，请考虑上述合规性评估，如果设备不合规，将阻止其访问公司资源，直到解决威胁。

可在“Intune 管理员控制台”的“所有设备”页查看设备的合规性状态。

![Intune 管理员控制台“设备”页面的屏幕截图，其中显示了设备的合规性状态](../media/mtp/mtp-device-status-intune-console.png)

## <a name="next-steps"></a>后续步骤
* 创建条件访问策略
  * [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  * [Exchange 内部部署](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  * [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  * [Skype for Business Online](restrict-access-to-skype-for-business-online-with-microsoft-intune,md)
  * [Dynamics CRM](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)



<!--HONumber=Nov16_HO2-->


