---
title: "验证应用保护策略"
titleSuffix: Intune on Azure
description: "本主题介绍如何测试和验证应用保护策略是否已正确设置并按预期方式工作。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angerobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 28fcd15d2d2e11e4aa2ba6982fc3cb8567e56a31
ms.sourcegitcommit: 2ee1e8248814d74cef80b609a8e43f59fa0b2618
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2017
---
# <a name="how-to-validate-your-app-protection-policy-setup"></a>如何验证应用保护策略设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


本主题提供设置应用保护策略后如何检查问题的相关信息。 本指南适用于 Azure 门户中的应用保护策略。

### <a name="checking-for-symptoms"></a>检查症状
由于应用保护是数据保护工具，因此用户不太可能报告问题。 如果应用保护配置出现问题，用户将具有不受限制的访问权限，因为在没有应用保护时他们也会具有不受限制的访问权限，所以也不会意识到出现了问题。 因此，建议让一小组可专门测试应用保护限制的用户试验应用保护策略，从而验证应用保护配置。


### <a name="what-to-check"></a>要检查的内容

如果测试显示应用保护策略行为与预期不符，建议检查以下各项：

- 用户是否已获得应用保护授权？
- 用户是否已获得 O365 授权？
- 每个用户的应用保护应用的状态。 可能的应用状态为“**已签入**”和“**未签入**”。

#### <a name="user-app-protection-status"></a>用户应用保护状态
1. 在 Azure 门户中选择“管理应用” > “监视” >  “应用保护用户状态” > “用户”。

2. 从列表中选择用户或搜索并选择一个用户，然后选择“选择用户”。 在“应用报告”列顶部，将看到用户是否已获得应用保护授权。 你可以从下面看到该用户是否已获得 O365 授权，以及所有用户设备的应用状态。



### <a name="what-to-do"></a>要执行的操作
下面是要根据用户状态采取的操作：

- 如果用户未获得应用保护授权，请为用户分配 Intune 许可证。
- 如果用户未获得 O365 授权，则为该用户获取许可证。
- 如果用户的应用被列为“未签入”，请检查是否已为该应用正确配置应用保护策略。
- 确保这些条件适用于要应用应用保护策略的所有用户。

### <a name="see-also"></a>另请参阅

[什么是 Intune 应用保护策略？](app-protection-policies.md)
