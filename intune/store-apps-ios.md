---
title: "如何将 iOS 应用商店应用添加到 Intune"
titleSuffix: Intune on Azure
description: "了解如何将 iOS 应用商店应用添加到 Intune。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/11/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3d6a12a21c156a45974e096da852f749f19bd330
ms.sourcegitcommit: 4034ac474bfed358270a32459a2cf2fe02f44e45
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2017
---
# <a name="how-to-add-ios-store-apps-to-microsoft-intune"></a>如何将 iOS 应用商店应用添加到 Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


本主题提供的信息有助于向 Intune 添加 iOS 应用商店应用。

>[!NOTE]
>尽管 iOS 设备用户可删除部分内置 iOS 应用（如 Stocks 和地图），但无法使用 Intune 重新部署这些应用。 如果最终用户删除这些应用，则必须前往 App Store，并手动重新安装它们。

## <a name="before-you-start"></a>开始之前

如果应用在应用商店中是免费的，则只能使用此方法分配应用。 如果要使用 Intune 分配付费应用，请考虑使用 [iOS 批量购买计划](vpp-apps-ios.md)。


## <a name="step-1---search-for-the-app-in-the-store"></a>步骤 1 - 在应用商店中搜索应用

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“管理应用”。
4. 在“移动应用”工作负荷中，选择“管理”>“应用”。
5. 在应用列表的上方，选择“添加”。
6. 在“添加应用”边栏选项卡中，选择“搜索应用商店”。
7. 在“Apple 应用商店”边栏选项卡的搜索框中输入名称（或名称的一部分）。 Intune 将搜索应用商店并返回相关结果的列表。
8. 从列表中，选择所需应用，然后单击“确定”。

## <a name="step-2---configure-app-information"></a>步骤 2 - 配置应用信息

1. 在“添加应用”边栏选项卡中，选择“应用信息”。
2. 在“编辑应用”边栏选项卡中，配置以下信息。 完成后，单击“添加”。 根据所选择的应用，此边栏选项卡中的某些值可能已自动填充：
- **应用名称** - 输入应用的名称，该名称将显示在公司门户中。 请确保使用的所有应用名称都是唯一的。 如果同一应用名称存在两次，则在公司门户中将仅向用户显示其中一个应用。
    - **应用描述** - 为应用输入描述。 这将在公司门户中向用户显示。
- **发行者** — 输入应用的发行者名称。
- **应用商店 URL** - 输入要创建的应用的应用商店 URL。
- **最低操作系统** - 从列表中选择可安装应用的最低操作系统版本。 如果将应用分配到具有较低操作系统的设备，则不会安装该应用。
- **类别**（可选）。 选择一个或多个内置应用类别或你创建的类别。 这可让用户在浏览公司门户时更轻松地查找应用。
- **在公司门户中将此应用显示为特色应用** - 当用户浏览应用时，在公司门户的主页上突出显示此应用。
- **信息 URL** -（可选）输入包含此应用相关信息的网站 URL。 将在公司门户中向用户显示该 URL。
- **隐私 URL** -（可选）输入包含此应用相关隐私信息的网站 URL。 将在公司门户中向用户显示该 URL。
- **开发者** -（可选）输入应用开发者的名称。
- **所有者** -（可选）输入此应用的所有者的名称，例如，**HR 部门**。
- **说明** - 输入要与此应用关联的任何备注。
- **上传图标** - 上传将与应用关联的图标。 用户浏览公司门户时，此图标将与应用一同显示。
3. 完成后，在“添加应用”边栏选项卡上，选择“保存”。

创建的应用将显示在应用列表中，可在该列表中将其分配到所选择的组。 如需帮助，请参阅[如何将应用分配到组](apps-deploy.md)。
