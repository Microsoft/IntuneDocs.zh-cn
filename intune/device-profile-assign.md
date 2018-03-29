---
title: 在 Microsoft Intune 中分配设备配置文件 - Azure | Microsoft Docs
description: 使用 Azure 门户将设备配置文件和策略分配给用户和设备。 了解如何在 Microsoft InTune 中从配置文件分配中排除组。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9840298df981bee6c33d3cb36ec5e4ada46d11bd
ms.sourcegitcommit: e6319ff186d969da34bd19c9730ba003d6cce353
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/20/2018
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>在 Microsoft Intune 中分配用户和设备配置文件

创建配置文件后，可将配置文件分配给 Azure Active Directory (Azure AD) 组。

## <a name="assign-a-device-profile"></a>分配设备配置文件

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”，然后搜索“Microsoft Intune”。
2. 在 Microsoft Intune 中，依次选择“设备配置”、“配置文件”。
3. 在配置文件列表中，选择要分配的配置文件，然后选择“分配”。
4. 选择“包括”组或“排除”组，然后选择组  

    ![在配置文件分配中包括或排除组选项的屏幕截图](./media/group-include-exclude.png)

5. 选择组时，会选择 Azure AD 组。 按住 Ctrl 可选择多个组。
6. 完成后，选择“保存”。

## <a name="exclude-groups-from-a-profile-assignment"></a>从配置文件分配中排除组

通过使用 Intune 设备配置文件，可将组从策略分配中排除。 例如，可将设备配置文件分配到“所有企业用户”组，但排除“高级管理人员”组中的任何成员。

从分配中排除组时，仅排除用户或仅排除设备组（不是混合组），Intune 不会考虑任何用户到设备的关系。 如果在排除设备组的同时包括用户组，可能不会产生所需结果。 如果使用混合组或存在其他冲突，则包含优先于排除。

例如，需要向组织中除网亭设备外的所有设备分配设备配置文件。 于是含入“所有用户”组，而排除“所有设备”组。 在这种情况下，所有用户及其设备均会获得策略，即使用户设备属于“所有设备”组也是如此。

排除操作仅查看组的直接成员，而不包括与用户关联的设备。 但是，没有用户的设备不会获得策略。 出现这种情况是因为这些设备与“所有用户”组没有任何关系。

如果包括“所有设备”，而排除“所有用户”，则所有设备均接收策略。 在这种情况下，其目的是将与用户关联的设备从策略中排除。 但是，这样并不会排除设备，因为排除功能只比较直接组成员。

>[!TIP]
>排除操作不适用于符合性策略或应用分配。 若要从分配中排除成员，可使用“可用”和“不适用”分配。 例如，通过“可用”意图向“所有企业用户”分配应用，通过“不适用”意图向“高级管理人员”分配应用。 将向所有用户分配应用，“高级管理人员”组中的用户除外。 如果通过“必需”意图向“所有企业用户”分配应用，则不排除“高级管理人员”组中的用户。

## <a name="next-steps"></a>后续步骤
有关监视设备配置文件分配的指南，请参阅[如何监视设备配置文件](device-profile-monitor.md)。
