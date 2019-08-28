---
title: 在 Microsoft Intune 中包括和排除应用分配
titleSuffix: ''
description: 了解如何使用 Microsoft Intune 包括和排除应用分配。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c59f6df5-3317-4dff-8f19-fdeec33faedf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e32b40283410a53a9cbb65a27d0d614da0169d6c
ms.sourcegitcommit: c8cb314256c4896e838918f015ffaefb8f00ace5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/23/2019
ms.locfileid: "70001792"
---
# <a name="include-and-exclude-app-assignments-in-microsoft-intune"></a>在 Microsoft Intune 中包括和排除应用分配

在 Intune 中，可以通过分配要包括的组和要排除的组来决定哪些用户有权访问应用。 在将组分配到应用之前，必须设置应用的分配类型。 分配类型使应用可用、成为所需应用，或者卸载应用。 

要设置应用的可用性，可以通过结合使用包括组分配和排除组分配，针对一组用户或设备包括和排除应用分配。 在包括一个较大的组来提供应用，然后排除一个较小的组来缩小选定用户时，此功能非常有用。 较小的组可能是测试组或管理组。 

从应用分配中排除组时，必须排除仅用户组或仅设备组。 不能排除用户和设备的混合组。 

Intune 排除组时不会考虑用户与设备的关联。 在排除设备组的同时含入用户组，是不大可能产生所需结果的。 包含将优先于排除。 例如，如果让某 iOS 应用面向“所有用户”，并排除“所有 iPad”，最终结果将是使用 iPad 的任何用户仍可获得该应用   。 但是，如果让该 iOS 应用面向“所有设备”，并排除“所有 iPad”，则部署会成功   。  

> [!NOTE]
> 为应用设置组分配时，已弃用“不适用”类型，代之以排除组功能  。 
>
> Intune 在控制台中提供了预先创建的“所有用户”和“所有设备”组   。 为了方便起见，这些组已内置优化。 强烈建议针对所有用户和所有设备使用这些组，而不要使用可能是你自己创建的任何“所有用户”或“所有设备”组。  
>
> Android 企业支持包括和排除组。 可利用内置的“所有用户”和“所有设备”组进行 Android 企业应用分配   。 


## <a name="include-and-exclude-groups-when-assigning-apps"></a>分配应用时包括和排除组 
若要使用包括和排除分配将应用分配给组，请执行以下操作：
1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在“Intune”窗格中，选择“客户端应用”   。
4. 在“客户端应用”窗格中，选择“应用”   。 随即显示已添加应用的列表。
5. 选择要分配的应用。 仪表板显示有关应用的信息。 
6. 在菜单的“管理”部分中选择“分配”   。 

    ![分配应用时包括应用分配](./media/apps-inc-exl-01.png)
7. 选择“添加组”，添加分配有该应用的那些用户组  。 
8. 在“添加组”窗格中，从可用的分配类型中选择某个“分配类型”   。
9. 对于分配类型，请选择“不论是否注册均可使用”  。

    ![Intune 应用分配 - 添加组](./media/apps-inc-exl-02.png)
10. 选择“包含的组”，然后选择你想要其使用此应用的用户组  。

    > [!NOTE]
    > 添加组时，如果给定的分配类型中已包括任何其他组，则在其他包括分配类型中，会预先选定该组且无法修改。 已被使用的组无法用作包括组。

11. 选择“是”，使此应用可供所有用户使用  。

    ![Intune 应用分配 - 包括组](./media/apps-inc-exl-03.png)
12. 选择“确定”，设置要包括的组  。
13. 选择“排除的组”，然后选择你想要其无法使用此应用的用户组  。 
14. 选择要排除的组。 这使该应用对这些组不可用。

    ![Intune 应用分配 - 排除组](./media/apps-inc-exl-04.png)
15. 选择“选择”，完成组选择操作  。
16. 在“添加组”  窗格中，选择“确定”  。 应用“分配”列表随即显示  。
17. 单击“保存”，使应用的组分配处于活动状态  。

在进行组分配时，已分配的组不可修改。 若想选择当前不可用的组，先从应用的已分配列表中删除应用。 

要编辑分配，请在应用的“分配”列表中，选择包含想要更改的特定分配的行即可编辑分配  。 还可以选择行尾的省略号 (…) 并选择“删除”即可删除分配   。 要更改“分配”列表的视图，请按“分配类型”或按“包括/排除”分组    。

![Intune 应用分配 - 完成](./media/apps-inc-exl-05.png)

## <a name="next-steps"></a>后续步骤

- 有关为应用包括和排除组分配的详细信息，请参阅 [Microsoft Intune 博客](https://aka.ms/new_app_assignment_process)。
- 了解如何[监视应用信息和分配](apps-monitor.md)。
