---
title: "如何将 iOS 应用商店应用添加到 Microsoft Intune"
titlesuffix: 
description: "了解如何将 iOS 应用商店应用添加到 Microsoft Intune。"
keywords: Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4bd10c4f05204d0e911a7538f5d5133e4a336320
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-ios-store-apps-to-microsoft-intune"></a>如何将 iOS 应用商店应用添加到 Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


本文中提供的信息可帮助向 Microsoft Intune 添加 iOS 应用商店应用。 iOS 应用商店应用是 Intune 在用户设备上安装的应用。 用户是公司员工的一部分。 iOS 应用商店应用会自动更新。

>[!NOTE]
>尽管 iOS 设备用户可删除部分内置 iOS 应用（如“股市”和“地图”），但无法使用 Intune 重新部署这些应用。 如果最终用户删除这些应用，则必须前往 App Store，并手动重新安装它们。

## <a name="before-you-start"></a>开始之前

如果应用在应用商店中是免费的，则只能使用此方法分配应用。 如果要使用 Intune 分配付费应用，请考虑使用 [iOS 批量购买计划](vpp-apps-ios.md)。

>[!NOTE]
>使用 Microsoft Intune 时建议使用 Chrome 和 Microsoft Edge 浏览器。

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分。
3. 在 Intune 边栏选项卡上，选择“移动应用”。
4. 在“移动应用”工作负载中，选择“管理”部分下的“应用”。
5. 选择“应用”窗格右侧的“添加”。
6. 在“应用类型”列表中，选择可用“应用商店应用”类型下的“iOS”。
7. 选择“搜索 App Store”。
8. 在“搜索 App Store”边栏选项卡中，选择 App Store 国家/地区的区域设置。
9. 在搜索框中键入名称（或名称的一部分）。 Intune 将搜索应用商店并返回相关结果的列表。
10. 从列表中选择所需应用，然后单击“选择”。
11. 在“添加应用”边栏选项卡中，选择“应用信息”以配置应用。
12. 在“应用信息”边栏选项卡中，添加应用信息。 根据所选择的应用，此边栏选项卡中的某些值可能已自动填充：
    - **名称** - 键入要在公司门户中显示的应用名称。 请确保使用的所有应用名称都是唯一的。 如果同一应用名称存在两次，则在公司门户中将仅向用户显示其中一个应用。
    - **描述** - 键入要在公司门户中向用户显示的应用描述。
    - **发布者** - 键入应用发布者名称。
    - **应用商店 URL** - 键入要创建的应用的 App Store URL。
    - **最低操作系统** - 从列表中选择可安装应用的最低操作系统版本。 应用将不会安装在具有更早操作系统的设备上。
    - **适用的设备类型** - 从列表中选择应用所使用的设备。
    - **类别**（可选）。 选择一个或多个内置应用类别或你创建的类别。 “类别”可让用户在浏览公司门户时更轻松地查找应用。
    - **在公司门户中将此应用显示为特色应用** - 当用户浏览应用时，在公司门户的主页上突出显示此应用。
    - **信息 URL** -（可选）键入包含此应用相关信息的网站 URL。 将在公司门户中向用户显示该 URL。
    - **隐私 URL** -（可选）键入包含此应用相关隐私信息的网站 URL。 将在公司门户中向用户显示该 URL。
    - **开发者** -（可选）键入应用开发者的名称。 此字段仅对管理员可见，对最终用户不可见。
    - **所有者** -（可选）键入此应用的所有者的名称，例如，HR 部门。  此字段仅对管理员可见，对最终用户不可见。
    - **备注** - 键入要与此应用关联的任何备注。 此字段仅对管理员可见，对最终用户不可见。
    - **徽标** - 上传与应用关联的图标。 用户浏览公司门户时，此图标将与应用一同显示。
13. 完成后，单击“添加信息”边栏选项卡上的“确定”。
14. 在“添加应用”边栏选项卡中，单击“添加”。

创建的应用显示在应用列表中，可在该列表中将其分配到选择的组。

## <a name="next-steps"></a>后续步骤

- [如何将应用分配到组](apps-deploy.md)
