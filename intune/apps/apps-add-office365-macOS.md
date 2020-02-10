---
title: 使用 Microsoft Intune 将 Office 365 安装到 macOS 设备
titleSuffix: ''
description: 了解如何使用 Microsoft Intune 在 macOS 设备上安装 Office 365 应用。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3cf4c2abb5506f297af8a4e77145abea5360381b
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755351"
---
# <a name="assign-office-365-to-macos-devices-with-microsoft-intune"></a>使用 Microsoft Intune 将 Office 365 分配给 macOS 设备

借助此应用类型，可以轻松地将 Office 365 2016 应用分配给 macOS 设备。 使用此应用类型，可以安装 Word、Excel、PowerPoint、Outlook 和 OneNote。 为帮助保护和不断更新应用，这些应用随附 Microsoft AutoUpdate (MAU)。 所需的应用将显示为 Intune 控制台的应用列表中的一个应用。


## <a name="before-you-start"></a>开始之前

开始将 Office 365 添加到 macOS 设备前，请了解以下详细信息：

- 部署这些应用的设备必须运行 macOS 10.10 或更高版本。
- Intune 仅支持添加 Office 2016 for Mac 套件随附的 Office 应用。
- 当 Intune 安装应用套件时，如果任何 Office 应用处于打开状态，用户可能会丢失未保存文件中的数据。

## <a name="select-the-office-365-suite-app-type"></a>选择 Office 365 套件应用类型

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“应用”   > “所有应用”   > “添加”  。
3. 在“选择应用类型”  窗格的“Office 365 套件”  部分中选择“macOS”  。
4. 单击“选择”  。 将显示“添加 Office 365 套件”  步骤。

## <a name="step-1---app-suite-information"></a>步骤 1 - 应用套件信息

在此步骤中，提供有关该应用套件的信息。 此信息有助于在 Intune 中识别应用套件，也有助于用户在公司门户中找到应用套件。

1. 在“应用套件信息”  页中，可以确认或修改默认值：
    - **套件名称**：输入应用套件的名称，该名称将显示在公司门户中。 请确保使用的所有套件名称都是唯一的。 如果同一应用套件名称存在两次，则在公司门户中将仅向用户显示其中一个应用。
    - **套件描述**：输入应用套件的描述。 例如，可以列出已选择要包括的应用。
    - **发布者**：Microsoft 显示为发布者。
    - **类别**：（可选）选择一个或多个内置应用类别或所创建的类别。 该设置可让用户在浏览公司门户时更轻松地查找应用套件。
    - **在公司门户中将此应用显示为特色应用**：当用户浏览应用时，选择此选项以在公司门户的主页上突出显示应用套件。
    - **信息 URL**：（可选）输入包含此应用相关信息的网站的 URL。 在公司门户中向用户显示该 URL。
    - **隐私 URL**：（可选）输入包含此应用相关隐私信息的网站的 URL。 在公司门户中向用户显示该 URL。
    - **开发者**：Microsoft 显示为开发者。
    - **所有者**：Microsoft 显示为所有者。
    - **备注**：输入想与此应用关联的任何备注。
    - **徽标**：用户浏览公司门户时，Office 365 徽标与应用一同显示。
2. 单击“下一步”  以显示“作用域标记”  页面。

## <a name="step-2---select-scope-tags-optional"></a>步骤 2 - 选择作用域标记（可选）
可以使用作用域标记来确定谁可以在 Intune 中查看客户端应用信息。 若要详细了解作用域标记，请参阅[将基于角色的访问控制和作用域标记用于分布式 IT](../fundamentals/scope-tags.md)。

1. 单击“选择作用域标记”  可以选择为应用套件添加作用域标记。 
2. 单击“下一步”以显示“分配”页面   。

## <a name="step-3---assignments"></a>步骤 3 - 分配

1. 为应用套件选择“必需”  或“适用于已注册的设备”  组分配。 有关详细信息，请参阅[添加用于组织用户和设备的组](~/fundamentals/groups-add.md)和[使用 Microsoft Intune 将应用分配到组](apps-deploy.md)。

    >[!Note]
    > 无法通过 Intune 卸载 Office 365 for macOS 应用套件。

2. 单击“下一步”  以显示“查看 + 创建”页  。 

## <a name="step-4---review--create"></a>步骤 4 - 查看 + 创建

1. 查看为应用套件输入的值和设置。
2. 完成后，单击“创建”  将应用添加到 Intune。

    随即显示创建的 Office 365 Window 10 应用套件的“概述”  边栏选项卡。 应用套件在应用列表中显示为各个条目。

## <a name="next-steps"></a>后续步骤

- 若要了解如何将 Office 365 应用添加到 Windows 10 设备，请参阅[使用 Microsoft Intune 将 Office 365 专业增强版 2016 应用分配给 Windows 10 设备](apps-add-office365.md)。
- 要了解从用户组添加和排除应用分配，请参阅[添加和排除应用分配](apps-inc-exl-assignments.md)。
