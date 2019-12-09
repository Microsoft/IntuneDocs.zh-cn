---
title: 使用 Microsoft Intune 将内置应用添加到移动设备
titleSuffix: ''
description: 了解如何使用 Intune 更轻松地在移动设备上安装内置应用。
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
ms.assetid: 0ec8de66-5a0f-4c8d-afbf-c2becc7d6eec
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a92699ccce4f0b2590e526b3442cd45bfda6407c
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563606"
---
# <a name="add-built-in-apps-to-microsoft-intune"></a>将内置应用添加到 Microsoft Intune

通过使用内置的应用类型，可以轻松地将特选的托管应用（例如 Office 365 应用）分配给 iOS 和 Android 设备  。 可以为此应用类型分配特定的应用，例如 Excel、OneDrive、Outlook、Skype 等。 添加应用后，应用类型将显示为“内置 iOS 应用”  或“内置 Android 应用”  。 通过使用内置应用类型，可以选择将其中哪些应用发布给设备用户。

在早期版本的 Intune 控制台中，Intune 提供了几个默认的托管 Office 365 应用，如 Outlook 和 OneDrive。 这些托管应用的应用类型被标记为“托管 iOS 应用商店应用”  或“托管 Android 应用”  。 我们建议使用内置应用类型，而不是使用这些应用类型。 通过使用内置应用类型，用户在编辑和删除 Office 365 应用方面将具有更多灵活性。

>[!NOTE]
>删除所有分配时，也会从应用列表中删除被标记为“托管 iOS 应用商店”  和“托管 Android 应用”  的默认 Office 365 应用。

## <a name="add-a-built-in-app"></a>添加内置应用

若要将内置应用添加到 Microsoft Intune 中的可用应用中，请执行以下步骤：
1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“应用”   > “所有应用”   > “添加”  。
3. 在“应用类型”  列表中的“添加”  应用窗格中，选择“内置应用”  。
4. 选择“选择应用”  。
5. 在“内置应用”  窗格中，选择想要添加的应用。
6. 在“添加应用”  窗格中，选择“添加”  。


## <a name="configure-app-information"></a>配置应用信息

可以修改有关内置应用的信息。 此信息有助于在 Intune 中识别应用，也有助于用户在公司门户中找到该应用。
1. 选择“应用” > “所有应用”，然后选择想要修改的内置应用   。  
   随即显示该内置应用的窗格。
2. 选择“属性”   > “配置”  。
4. 在“应用信息”  窗格中可以修改以下信息：
    - **名称**：输入内置应用的名称，该名称将在公司门户中显示。 请确保使用的所有名称都是唯一的。 如果同一应用名称存在两次，则在公司门户中将仅向用户显示其中一个应用。
    - **说明**：输入应用的描述。 
    - **发布者**：输入应用发布者的名称。
    - **类别**：（可选）选择一个或多个内置应用类别。 设置此选项可让用户在浏览公司门户时更轻松地查找应用。
    - **在公司门户中将此应用显示为特色应用**：当用户浏览应用时，在公司门户的主页上突出显示应用。
    - **信息 URL**：（可选）输入包含此应用相关信息的网站的 URL。 在公司门户中向用户显示该 URL。
    - **隐私 URL**：（可选）输入包含此应用相关隐私信息的网站的 URL。 在公司门户中向用户显示该 URL。
    - **开发者**：（可选）输入应用开发者的名称。
    - **所有者**：（可选）输入此应用的所有者的名称（例如，HR 部门  ）。
    - **备注**：输入想与此应用关联的任何备注。
    - **上传图标**：上传用户浏览公司门户时与应用一同显示的图标。
4. 选择“确定”  。
5. 在“属性”  窗格中，选择“保存”  。

## <a name="next-steps"></a>后续步骤

- 现在，可将应用分配到所选组。 有关详细信息，请参阅[将应用分配到组](apps-deploy.md)。
