---
title: 将 Android 应用商店应用添加到 Microsoft Intune
titleSuffix: ''
description: 了解如何将 Google Play 商店的 Android 应用商店应用添加到 Microsoft Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
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
ms.openlocfilehash: ec800064d109cca42878c79ade6777de9b782015
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563506"
---
# <a name="add-android-store-apps-to-microsoft-intune"></a>将 Android 应用商店应用添加到 Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

将应用分配给一个设备或一组用户之前，必须先将应用添加到 Microsoft Intune。 

## <a name="add-an-app"></a>添加应用程序

通过执行以下步骤，从 Azure 门户将 Android 应用商店应用添加到 Intune：

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“应用”   > “所有应用”   > “添加”  。
3. 在“添加应用”窗格中的“应用商店应用”类型下，选择“Android”    。
4. 若要配置应用信息，请选择“配置”，然后提供以下信息  。 对于 Android 应用，导航到 [Google Play 应用商店](https://play.google.com/store) 并搜索要部署的应用。 选择应用，并记下应用的详细信息。 某些值可能已自动填充（具体取决于所选应用）。
    - **名称**：输入要在公司门户中显示的应用名称。 请确保使用唯一的应用名称。 如果应用名称重复，则在公司门户中仅向用户显示一个名称。
    - **说明**：输入应用的描述。 在公司门户中向用户显示该描述。
    - **发布者**：输入应用发布者的名称。
    - **应用商店 URL**：输入要创建的应用的应用商店 URL。
    - **最低操作系统**：在列表中选择可安装应用的最低操作系统版本。 如果将应用分配到具有较低操作系统的设备，则不会安装该应用。
    - **类别**：（可选）选择一个或多个内置应用类别或所创建的类别。 此操作可让用户在浏览公司门户时更轻松地查找应用。
    - **在公司门户中将此应用显示为特色应用**：当用户浏览应用时，选择此选项以在公司门户的主页上突出显示应用套件。 适用于基于可用意图部署的应用。
    - **信息 URL**：（可选）输入包含此应用相关信息的网站的 URL。 在公司门户中向用户显示该 URL。
    - **隐私 URL**：（可选）输入包含此应用相关隐私信息的网站的 URL。 在公司门户中向用户显示该 URL。
    - **开发者**：（可选）输入应用开发者的名称。
    - **所有者**：（可选）输入此应用的所有者的名称（例如，HR 部门  ）。
    - **备注**：（可选）输入要与此应用关联的任何备注。
    - **徽标**：（可选）：上传将与应用关联的图标。 用户浏览公司门户时，此图标将与应用一同显示。
5. 选择“确定”  。
6. 选择“添加”  。

此时，已创建的应用显示在应用列表中，可在此列表中将其分配到选择的组。 

## <a name="next-steps"></a>后续步骤

- [将应用分配给组](apps-deploy.md)
