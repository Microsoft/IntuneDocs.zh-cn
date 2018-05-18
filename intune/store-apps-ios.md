---
title: 将 iOS 应用商店应用添加到 Microsoft Intune
titlesuffix: ''
description: 了解如何将 iOS 应用商店应用添加到 Microsoft Intune。
keywords: Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5a9bc97356174ce331099f7f59a28fe6be700c41
ms.sourcegitcommit: b0ad42fe5b5627e5555b2f9e5bb81bb44dbff078
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/09/2018
---
# <a name="add-ios-store-apps-to-microsoft-intune"></a>将 iOS 应用商店应用添加到 Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文中提供的信息可帮助向 Microsoft Intune 添加 iOS 应用商店应用。 iOS 应用商店应用是 Intune 在用户设备上安装的应用。 用户是公司员工的一部分。 iOS 应用商店应用会自动更新。

>[!NOTE]
>尽管 iOS 设备用户可删除部分内置 iOS 应用（如“股市”和“地图”），但无法使用 Intune 重新部署这些应用。 如果用户删除这些应用，则必须前往 App Store，手动重新进行安装。

## <a name="before-you-start"></a>开始之前

只有当应用在应用商店中免费提供时，才使用此方法分配应用。 如果要使用 Intune 分配付费应用，请考虑使用 [iOS 批量购买计划](vpp-apps-ios.md)。

>[!NOTE]
>在使用 Microsoft Intune 时，我们建议使用 Microsoft Edge 或 Google Chrome 浏览器。

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。  
    Intune 位于“监视 + 管理”部分中。
3. 在“Intune”窗格中，选择“移动应用”。
4. 在“移动应用”工作负载窗格的“管理”下，选择“应用”。
5. 在“应用”窗格中，选择“添加”。
6. 在“应用类型”列表中，选择“应用商店应用”类型下的“iOS”。
7. 选择“搜索 App Store”。
8. 在“搜索 App Store”窗格中，选择 App Store 国家/地区的区域设置。
9. 在“搜索”框中，键入应用的名称（或名称的一部分）。  
    Intune 将搜索应用商店并返回相关结果的列表。
10. 在结果列表中，选择想要使用的应用，然后选择“选择”。
11. 在“添加应用”窗格中，选择“应用信息”以配置应用。
12. 在“应用信息”窗格中，添加应用信息。 此窗格中的某些值可能已自动填充（具体取决于所选应用）：
    - **名称**：输入要在公司门户中显示的应用名称。 请确保使用唯一的应用名称。 如果应用名称重复，则在公司门户中仅向用户显示一个名称。
    - 描述：为应用输入描述。 在公司门户中向用户显示该描述。
    - 发布者：输入应用的发布者名称。
    - **应用商店 URL**：键入要创建的应用的应用商店 URL。
    - **最低操作系统**：在列表中选择可安装应用的最低操作系统版本。 如果将应用分配到具有较低操作系统的设备，则不会安装该应用。
    - 适用的设备类型：在列表中，选择应用使用的设备。
    - **类别**（可选）：选择一个或多个内置应用类别或你创建的类别。 此操作可让用户在浏览公司门户时更轻松地查找应用。
    - 在“公司门户”中将此显示为特别推荐的应用：选择此选项可在用户浏览应用时，在“公司门户”的主页上突出显示应用套件。
    - 信息 URL：（可选）输入包含此应用相关信息的网站 URL。 在公司门户中向用户显示该 URL。
    - 隐私 URL：（可选）输入包含此应用相关隐私信息的网站 URL。 在公司门户中向用户显示该 URL。
    - 开发人员：（可选）输入应用开发人员的名称。 此字段仅对管理员可见，对用户不可见。
    - 所有者：（可选）输入此应用的所有者的名称（例如，HR 部门）。 此字段仅对管理员可见，对用户不可见。
    - 备注：（可选）输入要与此应用关联的任何备注。 此字段仅对管理员可见，对最终用户不可见。
    - **徽标**（可选）：上传将与应用关联的图标。 用户浏览公司门户时，此图标将与应用一同显示。
13. 选择“确定”。
14. 选择“添加”。

此时，已创建的应用显示在应用列表中，可在此列表中将其分配到选择的组。

## <a name="next-steps"></a>后续步骤

- [将应用分配给组](apps-deploy.md)
