---
title: "在合规性策略中启用设备保护规则 | Microsoft Intune"
description: "在设备合规性策略中启用移动威胁保护规则。"
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: c951692d-6538-46c0-a9f0-d607ded189ae
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9c2ffb5fe497d56d8250fe3dec7db606c2067a1c
ms.openlocfilehash: 761372b2c8b81699bc2584ab1ef8d0f9d523abe9


---

# 在合规性策略中启用设备威胁保护规则
通过附带 Lookout 移动威胁保护的 Intune，可检测设备上的移动威胁并进行风险评估。  
合规性策略规则允许通过此风险评估确定设备是否符合策略。 然后可通过条件访问策略，根据设备合规性允许或阻止 Exchange、SharePoint 及其他服务。

要使 Lookout MTP 威胁保护影响设备的合规性策略，请执行以下操作：

1.  必须在在合规性策略中启用“设备威胁保护”规则。

2.  Intune 管理员控制台中的“Lookout 状态”页必须显示“活动”。 请参阅[在 Intune 中启用 Lookout MTP 连接](enable-lookout-mtp-connection-in-intune.md)主题，了解有关如何激活 Lookout 集成的更多详细信息和介绍。


## 配置设备威胁保护规则

在合规性策略中创建设备威胁保护前，建议[为订阅设置 Lookout MTP](set-up-your-subscription-with-lookout-mtp.md)、[在 Intune 中启用 Lookout 连接](enable-lookout-mtp-connection-in-intune.md)并[配置 Lookout for Work 应用](configure-and-deploy-lookout-for-work-apps.md)。 仅在设置完成后才会执行合规性规则。

若要启用设备威胁保护规则，可使用现有合规性策略或创建新策略。

Lookout MTP 设置过程中，需在 [Lookout MTP 控制台](https://aad.lookout.com)中创建将各种威胁分为高级、中级和低级的策略。 在 Intune 合规性策略中，将用威胁等级设置允许的最高威胁等级。

在 Intune 管理员控制台的合规性策略页面，转到“设备运行状况”，并使用切换选项启用“设备威胁保护”规则。 然后从以下选项选择允许的最高威胁等级：
* **无(安全)**：这是最安全的选项。  这意味着该设备不能具有任何威胁。  若检测到设备具有任一等级的威胁，则将其评为不合规。  
* **低**：若设备上仅存在低级威胁，则将其评为合规。 低级以上的任意威胁都将使设备不合规。
* **中**：若设备设备上存在的威胁为低级或中级，则将其评为合规。 如果检测到高级威胁，则将其确定为不合规。
* **高**：这是最不安全的选项。 本质上而言，此选项允许所有威胁等级，可能仅在将此解决方案用于报告时有用。

![显示设备威胁保护规则设置的屏幕截图 ](../media/mtp/mtp-compliance-policy-rule.png)

![显示设备威胁保护规则设置威胁等级选项的屏幕截图](../media/mtp/mtp-compliance-policy-setting.png)

若为 O365 或其他设备创建条件访问策略，请考虑上述合规性评估，且解决威胁前将阻止不合规设备进行访问。

可在 Intune 管理员控制台的“设备”页查看设备的合规性状态。

![Intune 管理员控制台“设备”页面的屏幕截图，其中显示了设备的合规性状态](../media/mtp/mtp-device-status-intune-console.png)

## 后续步骤
* 创建条件访问策略
  * [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  * [Exchange 内部部署](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  * [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  * [Skype for Business Online](restrict-access-to-skype-for-business-online-with-microsoft-intune,md)
  * [动态 CRM](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)



<!--HONumber=Sep16_HO2-->


