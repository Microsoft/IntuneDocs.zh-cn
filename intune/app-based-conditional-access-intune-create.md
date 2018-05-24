---
title: 使用 Intune 设置基于应用的条件性访问策略
description: 了解如何使用 Intune 创建基于应用的条件性访问策略。
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 05/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c505e881fe06d6f4da217533d0507731ac22a29f
ms.sourcegitcommit: 698bd1488be3a269bb88c077eb8d99df6e552a9a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>使用 Intune 设置基于应用的条件性访问策略

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文介绍如何为已批准应用列表中的一部分应用设置基于应用的条件性访问策略。 已批准应用列表包含经由 Microsoft 测试过的应用。

> [!IMPORTANT]
> 本文介绍了添加基于应用的条件访问策略的步骤。 请注意，从批准的应用列表添加应用（如 SharePoint Online、Microsoft Teams 和 Microsoft Exchange Online）时，可使用相同步骤。

## <a name="create-app-based-conditional-access-policies-in-azure-ad-workload"></a>在 Azure AD 工作负载中创建基于应用的条件访问策略

IT 管理员可从 Azure AD 工作负载中创建基于应用的条件访问策略。 这样就无需在 Azure 和 Intune 工作负载之间进行切换，简化了操作。

> [!IMPORTANT]
> 需要具备 Azure AD Premium 许可证才能从 Intune Azure 门户创建 Azure AD 条件性访问策略。

### <a name="to-create-an-app-based-conditional-access-policy"></a>创建基于应用的条件性访问策略

> [!IMPORTANT]
> 使用基于应用的条件访问策略前，需要将 [Intune 应用保护策略](app-protection-policies.md)应用于应用。

1. 在“Intune 仪表板”中，选择“条件访问”。

2. 在“策略”窗格中，选择“新建策略”以创建基于应用的新条件性访问策略。

4. 输入策略名称并配置“分配”部分中可用的设置后，在“访问控制”部分下选择“授予”。

5. 选择“需要已批准的客户端应用”>“选择”>“创建”，保存新策略。

## <a name="next-steps"></a>后续步骤
[阻止不具有新式验证的应用](app-modern-authentication-block.md)

### <a name="see-also"></a>另请参阅

[使用应用保护策略保护应用数据](app-protection-policies.md)
[Azure Active Directory 中的条件访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
