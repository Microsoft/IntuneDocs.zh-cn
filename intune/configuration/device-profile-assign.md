---
title: 在 Microsoft Intune 中分配设备配置文件 - Azure | Microsoft Docs
description: 使用 Microsoft 终结点管理器管理中心向用户和设备分配设备配置文件和策略。 了解如何在 Microsoft InTune 中从配置文件分配中排除组。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/28/2020
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
ms.openlocfilehash: 5b61c333f41054194b44c7517e508fe1ef6d28d4
ms.sourcegitcommit: b0d683917af83170f85022b270270d8ced8e301c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2020
ms.locfileid: "76812370"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>在 Microsoft Intune 中分配用户和设备配置文件

创建一个配置文件，其中包含你输入的所有设置。 下一步是部署配置文件或将其“分配”给 Azure Active Directory (Azure AD) 用户或设备组。 分配后，用户和设备会收到你的配置文件，并且会应用你输入的设置。

本文演示如何分配配置文件，并介绍有关对配置文件使用作用域标记的一些信息。

> [!NOTE]  
> 当配置文件被删除或不再分配给设备时，根据配置文件中设置的不同，可能会执行不同的操作。 这些设置基于 CSP，并且每个 CSP 可以不同地处理配置文件删除。 例如，设置可能会保留现有值，而不会恢复为默认值。 该行为由操作系统中的每个 CSP 控制。 有关 Windows CSP 的列表，请参阅[配置服务提供程序 (CSP) 参考](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference)。
>
> 要将设置更改为其他值，请创建新的配置文件，将设置配置为“未配置”  ，然后分配配置文件。 应用于设备后，用户应该可控制将设置更改为其首选值。
>
> 在配置这些设置时，我们建议部署到试验组。 有关 Intune 推出建议的更多信息，请参阅[创建推出计划](../fundamentals/planning-guide-rollout-plan.md)。

## <a name="before-you-begin"></a>在开始之前

确保你拥有适当的角色来分配配置文件。 有关详细信息，请参阅 [Microsoft Intune 的基于角色的访问控制 (RBAC)](../fundamentals/role-based-access-control.md)。

## <a name="assign-a-device-profile"></a>分配设备配置文件

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“设备”   > “配置文件”  。 此时会列出所有配置文件。
3. 选择要分配的配置文件，单击“分配”  。
4. 选择“包含”组或“排除”组，然后选择组   。 选择组时，会选择 Azure AD 组。 若要选择多个组，请按住 Ctrl，然后选择组  。

    ![在配置文件分配中包括或排除组选项的屏幕截图](./media/device-profile-assign/group-include-exclude.png)

5. 单击“保存”以保存更改  。

### <a name="evaluate-how-many-users-are-targeted"></a>评估所面向的用户数

分配配置文件后，还可以评估  受影响的用户数。 此功能计算用户数，不计算设备数。

1. 在管理中心，选择“设备”   > “配置文件”  。
2. 选择一个配置文件，依次单击“分配”   >   “评估”。 随即出现一条消息，显示此配置文件所面向的用户数。

如果“评估”按钮呈灰显状态，请确保配置文件已分配到一个或多个组  。

## <a name="use-scope-tags-or-applicability-rules"></a>使用作用域标记或适用性规则

创建或更新配置文件时，还可以向配置文件添加作用域标记和适用性规则。

“作用域标记”非常适合用于将配置文件筛选到特定组（例如 `US-NC IT Team` 或 `JohnGlenn_ITDepartment`）  。 [将 RBAC 和作用域标记用于分布式 IT](../fundamentals/scope-tags.md) 提供了详细信息。

在 Windows 10 设备上，可以添加适用性规则  ，以便配置文件仅适用于特定 OS 版本或特定 Windows 版本。 [适用性规则](device-profile-create.md#applicability-rules)包含详细信息。

## <a name="user-groups-vs-device-groups"></a>用户组与设备组

许多用户询问何时使用用户组以及何时使用设备组。 答案取决于你的目标。 下面是一些入门指南。

### <a name="device-groups"></a>设备组

如果要在设备上应用设置，而不考虑登录的用户，请将配置文件分配给设备组。 应用于设备组的设置始终随附于设备（而不是用户）。

例如：

- 设备组适用于管理没有专用用户的设备。 例如，你的设备将打印票证、扫描清单、由换班工作人员共享、将其分配到特定仓库等。 将这些设备放在设备组中，并将配置文件分配给此设备组。

- 创建一个[设备固件配置接口 (DFCI) Intune 配置文件](device-firmware-configuration-interface-windows.md)，用于更新 BIOS 中的设置。 例如，你将此配置文件配置为禁用设备照相机，或锁定启动选项以防止用户启动其他操作系统。 此配置文件是分配给设备组的良好方案。

- 在某些特定的 Windows 设备上，你始终需要控制某些 Microsoft Edge 设置，而不考虑使用该设备的用户。 例如，你想要阻止所有下载，将所有 cookie 限制为当前浏览会话，并删除浏览历史记录。 对于这种情况，请将这些特定 Windows 设备放在设备组中。 然后，[在 Intune 中创建管理模板](administrative-templates-windows.md)，添加这些设备设置，然后将此配置文件分配到设备组。

总而言之，当你不关心登录设备的用户或是否有任何人登录时，请使用设备组。 你希望设置始终位于设备上。

### <a name="user-groups"></a>用户组

应用于用户组的配置文件设置始终随附于用户，并在登录到多个设备时随附于用户。 通常用户有很多设备，如 Surface Pro 用于办公，iOS 设备用于私事。 而且，通常人们可以从这些设备访问电子邮件和其他组织资源。

例如：

- 你需要为所有设备上的所有用户提供一个技术支持图标。 在此情况下，将这些用户放在用户组中，并将你的技术支持图标配置文件分配给此用户组。
- 用户将收到一个新的组织拥有的设备。 用户通过其域帐户登录到设备。 设备在 Azure AD 中自动注册，并由 Intune 自动管理。 此配置文件是分配给用户组的良好方案。
- 每当用户登录到设备时，你都需要控制 OneDrive 或 Office 等应用中的功能。 在这种情况下，将 OneDrive 或 Office 配置文件设置分配给用户组。

  例如，你想要在 Office 应用中阻止不受信任的 ActiveX 控件。 你可以[在 Intune 中创建管理模板](administrative-templates-windows.md)，配置这些设置，然后将此配置文件分配到用户组。

总而言之，当你希望设置和规则始终随附于用户而不考虑使用的设备时，请使用用户组。

## <a name="exclude-groups-from-a-profile-assignment"></a>从配置文件分配中排除组

通过使用 Intune 设备配置文件，可在配置文件分配中包括和排除组。

最佳做法是专门为用户组创建和分配配置文件。 并且，专门为设备组创建和分配其他配置文件。 有关组的详细信息，请参阅[添加用于组织用户和设备的组](../fundamentals/groups-add.md)。

如果分配配置文件，请在包括和排除组时使用下表。 复选标记表示支持分配：

![支持的选项在配置文件分配中包括或排除组](./media/device-profile-assign/include-exclude-user-device-groups.png)

### <a name="what-you-should-know"></a>应了解的内容

- 在以下相同的组类型方案中，排除优先于包含：

  - 包括用户组和排除用户组
  - 包括设备组和排除设备组

  例如，可将设备配置文件分配到“所有公司用户”  用户组，但排除“高级管理人员”  用户组中的成员。 由于这两个组都是用户组，因此除“高级管理人员”  之外的“所有公司用户”  获取配置文件。

- Intune 不会评估用户到设备组的关系。 如果将配置文件分配到混合组，则结果可能不是你所预期的。

  例如，将设备配置文件分配到“所有用户”用户组，但排除“所有个人设备”设备组   。 在此混合组配置文件分配中，“所有用户”  获取配置文件。 排除不适用。

  因此，建议不要将配置文件分配到混合组。

## <a name="next-steps"></a>后续步骤

有关监视配置文件以及运行配置文件的设备的指南，请参阅[监视设备配置文件](device-profile-monitor.md)。
