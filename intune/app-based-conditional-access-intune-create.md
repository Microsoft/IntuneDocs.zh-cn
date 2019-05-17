---
title: 使用 Intune 设置基于应用的条件性访问策略
titleSuffix: Microsoft Intune
description: 了解如何使用 Intune 创建基于应用的条件性访问策略。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2019
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1514fe9dfcd09e2b77967b0fed8c36fb7a06634f
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567486"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>使用 Intune 设置基于应用的条件性访问策略

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

为已批准应用列表中的一部分应用设置基于应用的条件访问策略。 已批准应用列表包含经由 Microsoft 测试过的应用。

> [!IMPORTANT]
> 本文介绍了添加基于应用的条件访问策略的步骤。 从批准的应用列表添加应用（如 SharePoint Online、Microsoft Teams 和 Microsoft Exchange Online）时，可使用相同步骤。

## <a name="create-app-based-conditional-access-policies"></a>创建基于应用的条件访问策略
条件访问是一项 Azure Active Directory (Azure AD) 技术。 从 Intune 访问的条件访问节点与从 Azure AD 访问的节点相同。 这意味着无需在 Intune 和 Azure AD 之间切换即可配置策略。

> [!IMPORTANT]
> 需要具备 Azure AD Premium 许可证才能从 Intune 门户创建条件访问策略。

### <a name="to-create-an-app-based-conditional-access-policy"></a>创建基于应用的条件性访问策略

> [!IMPORTANT]
> 使用基于应用的条件访问策略前，需要将 [Intune 应用保护策略](app-protection-policies.md)应用于应用。

1. 在“Intune 仪表板”中，选择“条件访问”。

2. 在“策略”窗格中，选择“新建策略”以创建基于应用的新条件性访问策略。

4. 输入策略名称并配置“分配”部分中可用的设置后，在“访问控制”部分下选择“授予”。

5. 选择“需要已批准的客户端应用”>“选择”>“创建”，保存新策略。

## <a name="next-steps"></a>后续步骤
[阻止不使用新式验证的应用](app-modern-authentication-block.md)

### <a name="see-also"></a>另请参阅

[使用应用保护策略保护应用数据](app-protection-policies.md)
[Azure Active Directory 中的条件访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
