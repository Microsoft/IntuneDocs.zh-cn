---
title: 将 Android 应用商店应用添加到 Microsoft Intune
titleSuffix: ''
description: 了解如何将 Google Play 商店的 Android 应用商店应用添加到 Microsoft Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e6b9f6a9303e53652959639193633cdcc00dfb99
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755079"
---
# <a name="add-android-store-apps-to-microsoft-intune"></a>将 Android 应用商店应用添加到 Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

将应用分配给一个设备或一组用户之前，必须先将应用添加到 Microsoft Intune。 

## <a name="add-an-app"></a>添加应用程序

通过执行以下步骤，从 Azure 门户将 Android 应用商店应用添加到 Intune：

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“应用”   > “所有应用”   > “添加”  。
3. 在“选择应用类型”  窗格中的可用“应用商店应用”  类型下，选择“Android 应用商店应用”  。
4. 单击“选择”  。<br>
   将显示“添加应用”  步骤。
5. 若要为 Android 应用配置“应用信息”  ，请导航到 [Google Play 商店](https://play.google.com/store) 并搜索要部署的应用。 显示应用页并记下应用详细信息。 
6. 在“应用信息”  页中，添加应用详细信息：
    - **名称**：输入要在公司门户中显示的应用名称。 请确保使用唯一的应用名称。 如果应用名称重复，则在公司门户中仅向用户显示一个名称。
    - **描述**：输入应用的描述。 在公司门户中向用户显示该描述。
    - **发布者**：输入应用发布者的名称。
    - **应用商店 URL**：输入要创建的应用的应用商店 URL。 当应用详细信息在应用商店中显示时，请使用应用页面的 URL。 
    - **最低操作系统**：在列表中选择可安装应用的最低操作系统版本。 如果将应用分配到具有较低操作系统的设备，则不会安装该应用。
    - **类别**：（可选）选择一个或多个内置应用类别或所创建的类别。 此操作可让用户在浏览公司门户时更轻松地查找应用。
    - **在公司门户中将此应用显示为特色应用**：当用户浏览应用时，选择此选项以在公司门户的主页上突出显示应用套件。 适用于基于可用意图部署的应用。
    - **信息 URL**：（可选）输入包含此应用相关信息的网站的 URL。 在公司门户中向用户显示该 URL。
    - **隐私 URL**：（可选）输入包含此应用相关隐私信息的网站的 URL。 在公司门户中向用户显示该 URL。
    - **开发者**：（可选）输入应用开发者的名称。
    - **所有者**：（可选）输入此应用的所有者的名称（例如，HR 部门  ）。
    - **备注**：（可选）输入要与此应用关联的任何备注。
    - **徽标**：（可选）：上传将与应用关联的图标。 用户浏览公司门户时，此图标将与应用一同显示。
7. 单击“下一步”  以显示“作用域标记”  页面。
8. 单击“选择作用域标记”  可以选择为应用添加作用域标记。 有关详细信息，请参阅[对分布式 IT 使用基于角色的访问控制 (RBAC) 和作用域标记](~/fundamentals/scope-tags.md)。
9. 单击“下一步”以显示“分配”页面   。
10. 为应用选择组分配。 有关详细信息，请参阅[添加用于组织用户和设备的组](~/fundamentals/groups-add.md)。 
11. 单击“下一步”  以显示“查看 + 创建”页  。 查看为应用输入的值和设置。
12. 完成后，单击“创建”  将应用添加到 Intune。

随即显示创建的应用的“概述”  边栏选项卡。

## <a name="next-steps"></a>后续步骤

- [将应用分配给组](apps-deploy.md)
