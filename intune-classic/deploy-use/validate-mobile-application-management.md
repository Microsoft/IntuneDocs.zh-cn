---
title: "验证 MAM 设置 | Microsoft Docs"
description: "本主题介绍如何测试和验证是否已正确设置 MAM 策略并按预期方式工作。"
keywords: 
author: andredm7
ms.author: andredm
manager: angerobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 41d82597-e13e-4c3e-9151-e71392236ca0
ms.reviewer: joglocke
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: ab04c85d6704d7011cc5d4ea2a9f83d78b5b73e3
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="validating-your-mobile-application-management-setup"></a>验证移动应用管理设置

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本主题提供有关设置移动应用管理 (MAM) 后检查问题的相关信息。 本指南适用于 Azure 门户中的 MAM 策略。

### <a name="checking-for-symptoms"></a>检查症状
由于 MAM 是数据保护工具，因此用户不太可能报告问题。 如果 MAM 配置出现问题，用户将具有不受限制的访问权限，因为在没有 MAM 时他们也会具有不受限制的访问权限，所以也不会意识到出现了问题。 因此，建议让一小组可以专门测试 MAM 限制的用户试验 MAM 策略，从而验证 MAM 配置。


### <a name="what-to-check"></a>要检查的内容

如果测试显示 MAM 策略行为与预期不符，建议检查以下各项：

- 用户是否已获得 MAM 授权？
- 用户是否已获得 O365 授权？
- 每个用户的 MAM 应用的状态。 可能的应用状态为“**已签入**”和“**未签入**”。

#### <a name="user-mam-status"></a>用户 MAM 状态
1. 在 Azure 门户中，依次选择“**Intune 移动应用管理**” > “**设置**” > “**应用管理**” > “**所有设置**” > “**应用报告(按用户)**” > “**用户**”。

2. 从列表中选择用户或搜索并选择一个用户，然后选择“**选择用户**”。 在“**应用报告**”列顶部，将看到用户是否已获得 MAM 授权。 你可以从下面看到该用户是否已获得 O365 授权，以及所有用户设备的应用状态。

![MAM 的应用状态](..\media\ts-mam-user-apps.png)

### <a name="what-to-do"></a>要执行的操作
下面是要根据用户状态采取的操作：

- 如果用户未获得 MAM 授权，则按“[管理 Intune 许可证](..\get-started\start-with-a-paid-subscription-to-microsoft-intune.md)”中所述向用户分配 Intune 许可证。
- 如果用户未获得 O365 授权，则为该用户获取许可证。
- 如果用户的应用被列为“**未签入**”，请检查是否已为该应用正确配置 MAM 策略。
- 确保这些条件适用于要应用 MAM 策略的所有用户。

### <a name="see-also"></a>另请参阅
[准备好使用 Microsoft Intune 配置移动应用管理策略](..\deploy-use\get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)

[通过 Microsoft Intune 使用移动应用管理策略保护应用数据](..\deploy-use\protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

