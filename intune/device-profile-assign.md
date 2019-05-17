---
title: 在 Microsoft Intune 中分配设备配置文件 - Azure | Microsoft Docs
description: 使用 Azure 门户将设备配置文件和策略分配给用户和设备。 了解如何在 Microsoft InTune 中从配置文件分配中排除组。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0c950efdd95fd8d856ec677385712a022dead870
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "59570502"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>在 Microsoft Intune 中分配用户和设备配置文件

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

创建一个配置文件，其中包含你输入的所有设置。 下一步是部署配置文件或将其“分配”给 Azure Active Directory (Azure AD) 用户或设备组。 分配后，用户和设备会收到你的配置文件，并且会应用你输入的设置。

本文演示如何分配配置文件，并介绍有关对配置文件使用作用域标记的一些信息。

## <a name="assign-a-device-profile"></a>分配设备配置文件

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”> 筛选“Intune”> 选择“Intune”。
2. 选择“设备配置” > “配置文件”。 此时会列出所有配置文件。
3. 选择要分配的配置文件，单击“分配”。
4. 选择“包含”组或“排除”组，然后选择组。 选择组时，会选择 Azure AD 组。 若要选择多个组，请按住 Ctrl，然后选择组。

    ![在配置文件分配中包括或排除组选项的屏幕截图](./media/group-include-exclude.png)

5. 单击“保存”以保存更改。

### <a name="evaluate-how-many-users-are-targeted"></a>评估所面向的用户数

分配配置文件后，还可以评估受影响的用户数。 此功能计算用户数，不计算设备数。

1. 在 Intune 中，选择“设备配置” > “配置文件”。
2. 选择一个配置文件，依次单击“分配” > “评估”。 随即出现一条消息，显示此配置文件所面向的用户数。

如果“评估”按钮呈灰显状态，请确保配置文件已分配到一个或多个组。


## <a name="use-scope-tags"></a>使用作用域标记

创建或更新配置文件时，还可以向配置文件添加作用域标记。

作用域标记非常适合用于筛选策略并将其分配给特定组（如“人力资源”或“所有 US-NC 员工”）。 [将 RBAC 和作用域标记用于分布式 IT](scope-tags.md) 提供了详细信息。

## <a name="exclude-groups-from-a-profile-assignment"></a>从配置文件分配中排除组

通过使用 Intune 设备配置文件，可将组从策略分配中排除。 例如，可将设备配置文件分配到“所有企业用户”组，但排除“高级管理人员”组中的成员。

从分配中排除组，仅排除用户或仅排除设备组（不是混合组）时，Intune 不会考虑用户与设备的关系。 如果在排除设备组的同时包含用户组，可能不会获得预期结果。 如果使用混合组或存在其他冲突，则包含优先于排除。

例如，需要向组织中除网亭设备外的所有设备分配设备配置文件。 于是含入“所有用户”组，而排除“所有设备”组。 在这种情况下，所有用户及其设备均会获得策略，即使用户设备属于“所有设备”组也是如此。

排除仅考虑组的直接成员。 它不包含与用户关联的设备。 但是，没有用户的设备不会获得策略。 出现这种情况是因为这些设备与“所有用户”组没有任何关系。

如果包括“所有设备”，而排除“所有用户”，则所有设备均接收策略。 在这种情况下，其目的是将与用户关联的设备从策略中排除。 但是，这样并不会排除设备，因为排除功能只比较直接组成员。

## <a name="next-steps"></a>后续步骤

有关监视配置文件以及运行配置文件的设备的指南，请参阅[监视设备配置文件](device-profile-monitor.md)。