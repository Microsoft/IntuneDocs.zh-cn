---
title: 使用 Microsoft Intune 将 Office 365 安装到 macOS 设备
titleSuffix: ''
description: 了解如何使用 Microsoft Intune 在 macOS 设备上安装 Office 365 应用。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2ae63fa19bb24381580a206481a9ac2e3684314a
ms.sourcegitcommit: 063177c6c365fef3642edd7c455790958469aad9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/30/2019
ms.locfileid: "66412375"
---
# <a name="assign-office-365-to-macos-devices-with-microsoft-intune"></a>使用 Microsoft Intune 将 Office 365 分配给 macOS 设备

借助此应用类型，可以轻松地将 Office 365 2016 应用分配给 macOS 设备。 使用此应用类型，可以安装 Word、Excel、PowerPoint、Outlook 和 OneNote。 为帮助保护和不断更新应用，这些应用随附 Microsoft AutoUpdate (MAU)。 所需的应用将显示为 Intune 控制台的应用列表中的一个应用。


## <a name="before-you-start"></a>开始之前

开始将 Office 365 添加到 macOS 设备前，请了解以下详细信息：

- 部署这些应用的设备必须运行 macOS 10.10 或更高版本。
- Intune 仅支持添加 Office 2016 for Mac 套件随附的 Office 应用。
- 当 Intune 安装应用套件时，如果任何 Office 应用处于打开状态，用户可能会丢失未保存文件中的数据。

## <a name="create-and-configure-the-app-suite"></a>创建和配置应用套件

从“应用”  窗格添加 Office 365。
1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在“Intune”窗格中，选择“客户端应用”   。
4. 在“客户端应用”工作负载窗格的“管理”下，选择“应用”    。 
5. 选择“添加”  。
6. 在“应用类型”  列表中，选择“Office 365 套件”  组中的“macOS”  。
7. 要获取有关应用套件的信息，请选择“应用套件信息”  。  
    此信息有助于在 Intune 中识别应用套件，也有助于用户在公司门户中找到应用套件。
8. 输入以下信息：
    - **套件名称**：输入应用套件的名称，该名称将显示在公司门户中。 请确保使用的所有套件名称都是唯一的。 如果同一应用套件名称存在两次，则在公司门户中将仅向用户显示其中一个应用。
    - **套件描述**：输入应用套件的描述。
    - **发布者**：Microsoft 显示为发布者。
    - **类别**：选择一个或多个内置应用类别或你创建的类别。 该设置可让用户在浏览公司门户时更轻松地查找应用套件。
    - **在公司门户中将此应用显示为特色应用**：当用户浏览应用时，选择此选项以在公司门户的主页上突出显示应用套件。
    - **信息 URL**：（可选）输入包含此应用相关信息的网站的 URL。 在公司门户中向用户显示该 URL。
    - **隐私 URL**：（可选）输入包含此应用相关隐私信息的网站的 URL。 在公司门户中向用户显示该 URL。
    - **开发者**：Microsoft 显示为开发者。
    - **所有者**：Microsoft 显示为所有者。
    - **备注**：（可选）输入要与此应用关联的任何备注。
    - **徽标**：用户浏览公司门户时，Office 365 徽标与应用一同显示。
9. 选择“确定”  。
10. 在“添加应用”  窗格上，选择“添加”  。  
    应用套件在应用列表中显示为各个条目。

## <a name="configure-app-assignments"></a>配置应用分配

在这一步中，配置应用套件分配。 

1. 在应用列表中选择“Office 365”  应用套件，以显示“Office 365”  概述窗格。
2. 在“Office 365”  窗格中，选择“分配”  。
3. 若要添加将使用应用套件的组，请选择“添加组”  。  
    随即将显示“添加组”  窗格。
4. 将“分配类型”设置为“必需”或“可用”    。
5. 将应用套件分配给选定组。 有关详细信息，请参阅[使用 Microsoft Intune 将应用分配到组](apps-deploy.md)。

    >[!Note]
    > 无法通过 Intune 卸载 Office 365 应用套件。

5. 在“分配”  窗格中，选择“确定”  。
6. 在“添加组”  窗格中，选择“确定”  。
7. 要提交应用分配，选择“保存”  。

## <a name="next-steps"></a>后续步骤

- 若要了解如何将 Office 365 应用添加到 Windows 10 设备，请参阅[使用 Microsoft Intune 将 Office 365 专业增强版 2016 应用分配给 Windows 10 设备](apps-add-office365.md)。
- 要了解从用户组添加和排除应用分配，请参阅[添加和排除应用分配](apps-inc-exl-assignments.md)。
