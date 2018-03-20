---
title: "如何将 Android 应用商店应用添加到 Microsoft Intune"
titleSuffix: 
description: "了解如何将 Android 应用商店应用添加到 Microsoft Intune。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 87fea551dea1f80ee071fe6b477b84729e000874
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-add-android-store-apps-to-microsoft-intune"></a>如何将 Android 应用商店应用添加到 Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

将应用分配给一个设备或一组用户之前，必须先将应用添加到 Microsoft Intune。 可按以下步骤，从 Azure 门户将 Android 应用商店应用添加到 Intune。

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分。
3. 在 Intune 窗格中，选择“移动应用”。
4. 在“移动应用”工作负载中，选择“管理”部分下的“应用”。
5. 在应用列表的上方，选择“添加”。
6. 在“添加应用”窗格上，在可用的“应用商店应用”类型下选择“Android”。
7. 选择“配置”，为应用配置以下信息，注意：根据所选应用，此窗格中的一些值可能已自动填入：
    - **名称** — 输入应用的名称，该名称将显示在公司门户中。 请确保使用的所有应用名称都是唯一的。 如果同一应用名称存在两次，则在公司门户中将仅向用户显示其中一个应用。
    - **描述** — 为应用输入描述。 将在公司门户中向用户显示此描述。
    - **发行者** — 输入应用的发行者名称。
    - **应用商店 URL** - 输入要创建的应用的应用商店 URL。
    - **最低操作系统** - 从列表中选择可安装应用的最低操作系统版本。 如果将应用分配到具有较低操作系统的设备，则不会安装该应用。
    - **类别**（可选）- 选择一个或多个内置应用类别或你创建的类别。 这可让用户在浏览公司门户时更轻松地查找应用。
    - **在公司门户中将此应用显示为特色应用** - 当用户浏览应用时，在公司门户的主页上突出显示此应用。
    - **信息 URL**（可选）- 输入包含此应用相关信息的网站 URL。 将在公司门户中向用户显示该 URL。
    - **隐私 URL**（可选）- 输入包含此应用相关隐私信息的网站的 URL。 将在公司门户中向用户显示该 URL。
    - **开发者**（可选）- 输入应用开发者的名称。
    - **所有者**（可选）- 输入此应用的所有者的名称，例如，HR 部门。
    - **说明**（可选）- 输入要与此应用关联的任何备注。
    - **徽标**（可选）- 上传将与应用关联的图标。 用户浏览公司门户时，此图标将与应用一同显示。
8. 设置完应用信息后，单击“确定”。
9. 单击“添加”，以添加应用。

此时，已创建的应用显示在应用列表中，可供分配到选定组。 

##<a name="next-steps"></a>后续步骤

- [如何将应用分配到组](apps-deploy.md)