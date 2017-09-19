---
title: "如何使用 Intune 分配设备配置文件"
titlesuffix: Azure portal
description: "创建 Intune 设备配置文件后，请使用此主题了解如何将其分配给设备。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ba1438fe9227e0c7933fda7e9a2b60c8d4a5dca4
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2017
---
# <a name="how-to-assign-microsoft-intune-device-profiles"></a>如何分配 Microsoft Intune 设备配置文件

## <a name="assign-a-device-profile"></a>分配设备配置文件

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“设备配置”。
1. 在“设备配置”边栏选项卡上，选择“管理” > “配置文件”。
2. 在“配置文件列表”边栏选项卡上，选择要管理的配置文件，然后在“<配置文件名称> 报表”边栏选项卡上，选择“管理” > “分配”。
3. 在下一个边栏选项卡上，选择“包括”（包括组） 或“排除”（排除组），然后选择“选择组”。
![在配置文件分配中含入和排除组。](./media/group-include-exclude.png)
4. 在“选择组”边栏选项卡上，选择要在分配中含入或排除的 Azure AD 组。 可以按住 Ctrl 键以选择多个组。
4. 完成后，在“选择组”边栏选项卡上，选择“选择”。



## <a name="how-to-exclude-groups-from-a-device-profile-assignment"></a>如何从设备配置文件分配中排除组

通过使用 Intune 设备配置文件，可将组从策略分配中排除。 例如，可将设备配置文件分配到“所有企业用户”组，但排除“高级管理人员”组中的任何成员。

将组从分配中排除时，仅排除用户组或仅排除设备组，而非用户和设备的混合组。 排除组时，Intune 不会考虑用户与设备之间的关联。 在排除设备组的同时含入用户组，是不大可能产生所需结果的。 如果使用混合组或存在其他冲突，则包含优先于排除。

例如，需要向组织中除网亭设备外的所有设备分配设备配置文件。 于是含入“所有用户”组，而排除“所有设备”组。

在这种情况下，所有用户及其设备均会获得策略，即使用户设备属于“所有设备”组也是如此。 

排除操作仅评估组的直接成员，而不包括与用户关联的设备。 但是，与用户无关联的设备不会获得策略，因为它们与“所有用户”组无关联。 

如果含入“所有设备”，而排除“所有用户”，则所有设备均接收策略。 在这种情况下，目的是将与用户关联的设备从策略中排除。 但是，这并不是因为排除功能只比较直接组成员。 

>[!Tip]
>排除操作当前不适用于合规性政策或应用分配。 若要从分配中排除成员，可使用“可用”分配意图和“不适用”分配意图。 例如，通过“可用”意图向“所有企业用户”分配应用，通过“不适用”意图向“高级管理人员”分配应用。 将向所有用户分配应用，“高级管理人员”组中的用户*除外*。 如果通过“必需”意图向“所有企业用户”分配应用，则不排除“高级管理人员”组中的用户。
 
    
## <a name="next-steps"></a>后续步骤
有关可帮助你监视设备配置文件分配的信息，请参阅[如何监视设备配置文件](device-profile-monitor.md)。
