---
title: "包括和排除应用分配"
titlesuffix: Microsoft Intune
description: "了解如何使用 Intune 包括和排除应用分配。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/29/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c59f6df5-3317-4dff-8f19-fdeec33faedf
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ca1f45c3203645dc474fcb6411a8ad598ff83714
ms.sourcegitcommit: a6fd6b3df8e96673bc2ea48a2b9bda0cf0a875ae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2018
---
# <a name="include-and-exclude-app-assignments-in-microsoft-intune"></a>在 Microsoft Intune 中包括和排除应用分配

使用 Intune 可以分配要包括的组和要排除的组，从而决定哪些用户有权访问应用。 通过结合使用包括组分配和排除组分配，可针对一组用户或设备包括和排除应用分配。 选择某应用后，即可选择如何分配该应用。 在包括一个较大的组来提供应用，然后排除一个较小的组来缩小选定用户时，此功能非常有用。 较小的组可以是测试组或管理组。 

从分配中排除组时，必须仅排除用户组或仅排除设备组，而非用户和设备的混合组。 排除组时，Intune 不会考虑用户与设备之间的关联。 在排除设备组的同时包括用户组，是不大可能产生所需结果的，因为包括的优先等级高于排除。 例如，如果让某 iOS 应用面向“所有用户”，并排除“所有 iPad”，最终结果将是使用 iPad 的任何用户仍可获得该应用。 但是，如果让该 iOS 应用面向“所有设备”，并排除“所有 iPad”，则部署会成功。  

>[!NOTE]
>为应用设置组分配时，已弃用“不适用”类型，代之以排除组功能。 
>
>为方便起见，Intune 在具有内置优化的控制台中提供了预先创建的“所有用户”和“所有设备”组。 强烈建议针对所有用户和所有设备使用这些组，而不要使用你自己创建的任何“所有用户”或“所有设备”组。  

## <a name="including-and-excluding-groups-when-assigning-apps"></a>分配应用时包括和排除组 
若要使用包括和排除分配将应用分配给组，请执行以下操作：
1. 从“Microsoft Intune”边栏选项卡中选择“移动应用”。
2. 从“移动应用”边栏选项卡中选择“应用”。 随即显示已添加应用的列表。
3. 选择要分配的应用。 随即显示与该应用相关的仪表板。 
4. 选择“管理”部分下的“分配”。 

    ![Intune 应用分配](./media/apps-inc-exl-01.png)
5. 选择“添加组”，添加分配有该应用的那些用户组。 
6. 选择“添加组”边栏选项卡上可用分配类型中的某个“分配类型”。
7. 选择“不论是否注册均可使用”作为分配类型。

    ![Intune 应用分配 - 添加组](./media/apps-inc-exl-02.png)
8. 选择“包含的组”，然后选择你想要其使用此应用的用户组。

    >[!NOTE]
    >添加组时，如果给定的分配类型中已包括任何其他组，则在其他包括分配类型中，该组会被预先选定且无法更改。 因此，已被使用的组无法用作包括组。

9. 选择“是”，使此应用可供所有用户使用。

    ![Intune 应用分配 - 包括组](./media/apps-inc-exl-03.png)
10. 单击“确定”，设置要包括的组。
11. 选择“排除的组”，然后选择你想要其无法使用此应用的用户组。 
12. 选择要排除的组，不提供此应用。

    ![Intune 应用分配 - 排除组](./media/apps-inc-exl-04.png)
13. 单击“选择”，完成组选择操作。
14. 单击“添加组”边栏选项卡上的“确定”。 应用“分配”列表随即显示。
15. 单击“保存”，使应用的组分配处于活动状态。

进行组分配时，会禁用已分配或已选择的组。 若想选择当前禁用的组，请将其从应用的已分配列表中删除。 在应用“分配”列表中，选择包含想要更改的特定分配的行即可编辑分配。 此外，单击行尾的省略号 (…) 并选择“删除”即可删除分配。 而且选择按“分配类型”或按“包括/排除”分类还可以更改“分配”列表的视图。

![Intune 应用分配 - 完成](./media/apps-inc-exl-05.png)

## <a name="next-steps"></a>后续步骤

* 有关为应用包括和排除组分配的详细信息，请参阅 [Microsoft Intune 博客](https://aka.ms/new_app_assignment_process)。
