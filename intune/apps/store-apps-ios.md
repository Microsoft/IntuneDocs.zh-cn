---
title: 将 iOS 应用商店应用添加到 Microsoft Intune
titleSuffix: ''
description: 了解如何将 iOS 应用商店应用添加到 Microsoft Intune。 如果应用在 App Store 中是免费的，则可以使用此方法分配应用。
keywords: Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f2baf60fed2c6010e5ae0784cda166ac4fabfd57
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511729"
---
# <a name="add-ios-store-apps-to-microsoft-intune"></a>将 iOS 应用商店应用添加到 Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

本文中提供的信息可帮助向 Microsoft Intune 添加 iOS 应用商店应用。 iOS 应用商店应用是 Intune 在用户设备上安装的应用。 用户是公司员工的一部分。 iOS 应用商店应用会自动更新。

>[!NOTE]
>尽管 iOS/iPadOS 设备用户可删除部分内置 iOS/iPadOS 应用（如“股市”和“地图”），但无法使用 Intune 重新部署这些应用。 如果用户删除这些应用，则必须前往 App Store，手动重新进行安装。

## <a name="before-you-start"></a>开始之前

只有当应用在应用商店中免费提供时，才使用此方法分配应用。 如果要使用 Intune 分配付费应用，请考虑使用 [iOS/iPadOS 批量购买计划](vpp-apps-ios.md)。

>[!NOTE]
>在使用 Microsoft Intune 时，我们建议使用 Microsoft Edge 或 Google Chrome 浏览器。

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“应用”   > “所有应用”   > “添加”  。
3. 在“选择应用类型”  窗格中的可用“应用商店应用”  类型下，选择“iOS 应用商店应用”  。
4. 单击“选择”  。<br>
   将显示“添加应用”  步骤。
5. 选择“搜索 App Store”  。
6. 在“搜索 App Store”  窗格中，选择 App Store 国家/地区的区域设置。
7. 在“搜索”  框中，键入应用的名称（或名称的一部分）。  
    Intune 将搜索应用商店并返回相关结果的列表。
8. 在结果列表中，选择想要使用的应用，然后选择“选择”  。<br>

   “应用信息”  页面将显示在“添加应用”  窗格中。 如果可能，将基于你从应用商店中选择的应用添加应用信息。

9. 在“应用信息”  页中，添加应用的详细信息。 此窗格中的某些值可能已自动填充（具体取决于所选应用）：
    - **名称**：输入要在公司门户中显示的应用名称。 请确保使用唯一的应用名称。 如果应用名称重复，则在公司门户中仅向用户显示一个名称。
    - **描述**：输入应用的描述。 在公司门户中向用户显示该描述。
    - **发布者**：输入应用发布者的名称。
    - **应用商店 URL**：键入要创建的应用的应用商店 URL。
    - **最低操作系统**：在列表中选择可安装应用的最低操作系统版本。 如果将应用分配到具有较低操作系统的设备，则不会安装该应用。
    - **适用的设备类型**：在列表中，选择应用使用的设备。
    - **类别**：（可选）选择一个或多个内置应用类别或所创建的类别。 此操作可让用户在浏览公司门户时更轻松地查找应用。
    - **在公司门户中将此应用显示为特色应用**：当用户浏览应用时，选择此选项以在公司门户的主页上突出显示应用套件。
    - **信息 URL**：（可选）输入包含此应用相关信息的网站的 URL。 在公司门户中向用户显示该 URL。
    - **隐私 URL**：（可选）输入包含此应用相关隐私信息的网站的 URL。 在公司门户中向用户显示该 URL。
    - **开发者**：（可选）输入应用开发者的名称。 此字段仅对管理员可见，对用户不可见。
    - **所有者**：（可选）输入此应用的所有者的名称（例如，HR 部门  ）。 此字段仅对管理员可见，对用户不可见。
    - **备注**：（可选）输入要与此应用关联的任何备注。 此字段仅对管理员可见，对最终用户不可见。
    - **徽标**：（可选）：上传将与应用关联的图标。 用户浏览公司门户时，此图标将与应用一同显示。
10. 单击“下一步”  以显示“作用域标记”  页面。
11. 单击“选择作用域标记”  可以选择为应用添加作用域标记。 有关详细信息，请参阅[对分布式 IT 使用基于角色的访问控制 (RBAC) 和作用域标记](~/fundamentals/scope-tags.md)。
12. 单击“下一步”以显示“分配”页面   。
13. 为应用选择组分配。 有关详细信息，请参阅[添加用于组织用户和设备的组](~/fundamentals/groups-add.md)。 
14. 单击“下一步”  以显示“查看 + 创建”页  。 查看为应用输入的值和设置。
15. 完成后，单击“创建”  将应用添加到 Intune。

随即显示创建的应用的“概述”  边栏选项卡。

## <a name="next-steps"></a>后续步骤

- [将应用分配给组](apps-deploy.md)
