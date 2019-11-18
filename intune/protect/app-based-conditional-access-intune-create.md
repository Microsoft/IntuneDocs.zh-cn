---
title: 使用 Intune 设置基于应用的条件访问策略
titleSuffix: Microsoft Intune
description: 了解如何使用 Intune 创建基于应用的条件访问策略。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 465f8b0001e5e2a049a3ffe12469bdb5057854ec
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "73712848"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>使用 Intune 设置基于应用的条件访问策略

为已批准应用列表中的一部分应用设置基于应用的条件访问策略。 已批准应用列表包含经由 Microsoft 测试过的应用。

可以使用基于应用的条件访问策略前，需要将 [Intune 应用保护策略](../apps/app-protection-policies.md)应用于应用。

> [!IMPORTANT]
> 本文介绍了添加基于应用的条件访问策略的步骤。 从批准的应用列表添加应用（如 SharePoint Online、Microsoft Teams 和 Microsoft Exchange Online）时，可使用相同步骤。

## <a name="create-app-based-conditional-access-policies"></a>创建基于应用的条件访问策略

条件访问是一项 Azure Active Directory (Azure AD) 技术。 从 Intune  访问的条件访问节点与从 Azure AD  访问的节点相同。 因为节点相同，无需在 Intune 和 Azure AD 之间切换即可配置策略。

你必须具有 Azure AD Premium 许可证，然后才能从 Microsoft 终结点管理器管理中心创建条件访问策略。

### <a name="to-create-an-app-based-conditional-access-policy"></a>创建基于应用的条件访问策略

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)

2. 选择“终结点安全”   > “条件访问”   > “新策略”  。

3. 输入策略“名称”  ，然后在“分配”  下，选择“用户和组”  。 使用“包括”或“排除”选项来添加策略的组，然后选择“完成”  。

4. 选择“云应用或操作”  ，然后选择要保护的应用。 例如，选取“选择应用”  ，然后选择“Office 365 SharePoint Online”  和“Office 365 Exchange Online”  。

   选择“完成”  ，保存所做的更改。

5. 选择“条件”   > “客户端应用”  ，将策略应用到应用和浏览器。 例如，选择“是”  ，然后启用“浏览器”  和“移动应用和桌面客户端”  。

   选择“完成”  ，保存所做的更改。

6. 在“访问控制”  下，选择“授予”  以应用基于设备符合性的条件访问。 例如，选择“授予访问权限”   > “要求设备标记为符合策略”  。

   选取“选择”  ，保存所做的更改。

7. 对于“启用策略”  ，选择“启用”  ，然后选择“创建”  以保存所做的更改。





## <a name="next-steps"></a>后续步骤
[阻止不使用新式验证的应用](app-modern-authentication-block.md)

## <a name="see-also"></a>另请参阅

[使用应用保护策略保护应用数据](../apps/app-protection-policies.md)
[Azure Active Directory 中的条件访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
