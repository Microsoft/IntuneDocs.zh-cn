---
title: 在 Microsoft Intune 中分配设备配置文件 - Azure | Microsoft Docs
description: 使用 Azure 门户将设备配置文件和策略分配给用户和设备。 了解如何在 Microsoft InTune 中从配置文件分配中排除组。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: altsou
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a19515e859f5e78f7611bbd10088aea5f7c44650
ms.sourcegitcommit: f12bd2ce10b6241715bae2d2857f33c474287166
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72892639"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>在 Microsoft Intune 中分配用户和设备配置文件

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

创建一个配置文件，其中包含你输入的所有设置。 下一步是部署配置文件或将其“分配”给 Azure Active Directory (Azure AD) 用户或设备组。 分配后，用户和设备会收到你的配置文件，并且会应用你输入的设置。

本文演示如何分配配置文件，并介绍有关对配置文件使用作用域标记的一些信息。

> [!NOTE]  
> 当策略被删除或不再分配到设备时，此设置可能会保留现有值。 此设置不会还原到默认值。 若要将设置更改为其他值，请创建新策略并进行分配。

## <a name="before-you-begin"></a>在开始之前

确保你拥有适当的角色来分配策略。 有关详细信息，请参阅 [Microsoft Intune 的基于角色的访问控制 (RBAC)](../fundamentals/role-based-access-control.md)。

## <a name="assign-a-device-profile"></a>分配设备配置文件

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“设备配置” > “配置文件”   。 此时会列出所有配置文件。
3. 选择要分配的配置文件，单击“分配”  。
4. 选择“包含”组或“排除”组，然后选择组   。 选择组时，会选择 Azure AD 组。 若要选择多个组，请按住 Ctrl，然后选择组  。

    ![在配置文件分配中包括或排除组选项的屏幕截图](./media/device-profile-assign/group-include-exclude.png)

5. 单击“保存”以保存更改  。

### <a name="evaluate-how-many-users-are-targeted"></a>评估所面向的用户数

分配配置文件后，还可以评估  受影响的用户数。 此功能计算用户数，不计算设备数。

1. 在 Intune 中，选择“设备配置” > “配置文件”   。
2. 选择一个配置文件，依次单击“分配”   >   “评估”。 随即出现一条消息，显示此配置文件所面向的用户数。

如果“评估”按钮呈灰显状态，请确保配置文件已分配到一个或多个组  。

## <a name="use-scope-tags-or-applicability-rules"></a>使用作用域标记或适用性规则

创建或更新配置文件时，还可以向配置文件添加作用域标记和适用性规则。

 作用域标记非常适合用于筛选策略并将其分配给特定组（如“人力资源”或“所有 US-NC 员工”）。 [将 RBAC 和作用域标记用于分布式 IT](../fundamentals/scope-tags.md) 提供了详细信息。

在 Windows 10 设备上，可以添加适用性规则  ，以便配置文件仅适用于特定 OS 版本或特定 Windows 版本。 [适用性规则](device-profile-create.md#applicability-rules)包含详细信息。

## <a name="exclude-groups-from-a-profile-assignment"></a>从配置文件分配中排除组

通过使用 Intune 设备配置文件，可在策略分配中包括和排除组。

最佳做法是专门为用户组创建和分配策略。 并且，专门为设备组创建和分配其他策略。 有关组的详细信息，请参阅[添加用于组织用户和设备的组](../fundamentals/groups-add.md)。

如果分配策略，请在包括和排除组时使用下表。 复选标记表示支持分配：

![支持的选项在配置文件分配中包括或排除组](./media/device-profile-assign/include-exclude-user-device-groups.png)

### <a name="what-you-should-know"></a>应了解的内容

- 在以下相同的组类型方案中，排除优先于包含：

  - 包括用户组和排除用户组
  - 包括设备组和排除设备组

  例如，可将设备配置文件分配到“所有公司用户”  用户组，但排除“高级管理人员”  用户组中的成员。 由于这两个组都是用户组，因此除“高级管理人员”之外的“所有公司用户”获取策略   。

- Intune 不会评估用户到设备组的关系。 如果将策略分配到混合组，则结果可能不是你所预期的。

  例如，将设备配置文件分配到“所有用户”用户组，但排除“所有个人设备”设备组   。 在此混合组策略分配中，  “所有用户”获取策略。 排除不适用。

  因此，建议不要将策略分配到混合组。

## <a name="next-steps"></a>后续步骤

有关监视配置文件以及运行配置文件的设备的指南，请参阅[监视设备配置文件](device-profile-monitor.md)。
