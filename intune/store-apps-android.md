---
title: 将 Android 应用商店应用添加到 Microsoft Intune
titleSuffix: ''
description: 了解如何将 Android 应用商店应用添加到 Microsoft Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f62cb3a99a9cfd328cc041f095b0980eacc99852
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34224691"
---
# <a name="add-android-store-apps-to-microsoft-intune"></a>将 Android 应用商店应用添加到 Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

将应用分配给一个设备或一组用户之前，必须先将应用添加到 Microsoft Intune。 通过执行以下步骤，从 Azure 门户将 Android 应用商店应用添加到 Intune：

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。  
    Intune 位于“监视 + 管理”部分中。
1. 在“Intune”窗格中，选择“移动应用”。
2. 在“移动应用”工作负载窗格的“管理”下，选择“应用”。
3. 选择“添加”。
4. 在“添加应用”窗格中的“应用商店应用”类型下，选择“Android”。
5. 若要配置应用信息，请选择“配置”，然后提供以下信息。  
    某些值可能已自动填充（具体取决于所选应用）。
    - **名称**：输入要在公司门户中显示的应用名称。 请确保使用唯一的应用名称。 如果应用名称重复，则在公司门户中仅向用户显示一个名称。
    - 描述：为应用输入描述。 在公司门户中向用户显示该描述。
    - 发布者：输入应用的发布者名称。
    - **应用商店 URL**：输入要创建的应用的应用商店 URL。
    - **最低操作系统**：在列表中选择可安装应用的最低操作系统版本。 如果将应用分配到具有较低操作系统的设备，则不会安装该应用。
    - **类别**（可选）：选择一个或多个内置应用类别或你创建的类别。 此操作可让用户在浏览公司门户时更轻松地查找应用。
    - 在“公司门户”中将此显示为特别推荐的应用：选择此选项可在用户浏览应用时，在“公司门户”的主页上突出显示应用套件。
    - 信息 URL：（可选）输入包含此应用相关信息的网站 URL。 在公司门户中向用户显示该 URL。
    - 隐私 URL：（可选）输入包含此应用相关隐私信息的网站 URL。 在公司门户中向用户显示该 URL。
    - 开发人员：（可选）输入应用开发人员的名称。
    - 所有者：（可选）输入此应用的所有者的名称（例如，HR 部门）。
    - 备注：（可选）输入要与此应用关联的任何备注。
    - **徽标**（可选）：上传将与应用关联的图标。 用户浏览公司门户时，此图标将与应用一同显示。
1. 选择“确定”。
2. 选择“添加”。

此时，已创建的应用显示在应用列表中，可在此列表中将其分配到选择的组。 

## <a name="next-steps"></a>后续步骤

- [将应用分配给组](apps-deploy.md)