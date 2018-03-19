---
title: "使用 Microsoft Intune 将 Office 365 安装到 macOS 设备"
titlesuffix: 
description: "了解如何使用 Microsoft Intune 在 macOS 设备上安装 Office 365 应用。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8de14184c4d23adc79d5b519fdcf272f0d7f6804
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-assign-office-365-to-macos-devices-with-microsoft-intune"></a>如何使用 Microsoft Intune 将 Office 365 分配给 macOS 设备

借助此“应用商店应用”类型，可以轻松地将 Office 365 应用分配给 macOS 设备。 使用此应用类型，可以安装 Word、Excel、PowerPoint、Outlook 和 OneNote。 这些应用还随附 Microsoft AutoUpdate (MAU)，有助于保护和不断更新应用。 所需的应用将显示为 Intune 控制台的应用列表中的一个应用。


## <a name="before-you-start"></a>开始之前

开始将 Office 365 添加到 macOS 设备前，必须了解以下详细信息：

- 部署这些应用的设备必须运行 macOS 10.10 或更高版本。
- Intune 仅支持添加 Office 2016 for Mac 套件随附的 Office 应用。
- 如果任何 Office 应用在 Intune 安装应用套件时处于打开状态，最终用户可能会丢失未保存文件中的数据。

## <a name="create-and-configure-the-app-suite"></a>创建和配置应用套件

使用“应用”边栏选项卡添加 Office 365。
1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “监视 + 管理” > “Intune”。
3. 从“Intune”边栏选项卡中，选择“移动应用”。
4. 在“移动应用”工作负载中，选择“管理”部分中的“应用”。 
5. 选择“添加”以显示“添加应用”边栏选项卡。
6. 在“应用类型”列表中，选择“Office 365 套件”组中的“macOS”。
7. 选择“应用套件信息”以提供有关应用套件的信息。 此信息有助于在 Intune 中识别应用套件，也有助于用户在公司门户应用中找到它。
8.  指定下列信息：
    - **套件名称** - 输入应用套件的名称，该名称将显示在公司门户中。 请确保使用的所有套件名称都是唯一的。 如果同一应用套件名称存在两次，则在公司门户中将仅向用户显示其中一个应用。
    - **套件描述** - 为应用套件输入描述。
    - **发布者** - Microsoft 显示为发布者。
    - **类别** - 选择一个或多个内置应用类别或你创建的类别。 该设置可让用户在浏览公司门户时更轻松地查找应用套件。
    - **在“公司门户”中将此显示为特别推荐的应用** - 当用户浏览应用时，此设置会在“公司门户”的主页上突出显示应用套件。
    - **信息 URL**（可选）- 输入包含此应用相关信息的网站 URL。 在公司门户中向用户显示该 URL。
    - **隐私 URL**（可选）- 输入包含此应用相关隐私信息的网站的 URL。 在公司门户中向用户显示该 URL。
    - **开发人员** - Microsoft 显示为开发人员。
    - **所有者** - Microsoft 显示为所有者。
    - **说明**（可选）- 输入要与此应用关联的任何备注。
    - **徽标** - 用户浏览公司门户时，Office 365 徽标与应用一同显示。
9.  单击“应用信息”边栏选项卡上的“确定”。
10. 在“添加应用”边栏选项卡中，单击“添加”。
    应用套件在应用列表中显示为各个条目。

## <a name="configure-app-assignments"></a>配置应用分配

在这一步中，配置应用套件分配。 

1. 在应用列表中选择“Office 365”应用套件，以显示“Office 365”概述边栏选项卡。
2. 单击“Office 365”边栏选项卡中的“分配”。
3. 单击“添加组”来添加组以使用应用套件。 此时，显示“添加组”边栏选项卡。
3. 将“分配类型”设置为“必需”。
4. 将应用套件分配给选定组。 有关详细信息，请参阅[如何使用 Microsoft Intune 将应用分配到组](apps-deploy.md)。

    >[!Note]
    > 对于任何需要 Office 365 应用套件的组，无法通过 Microsoft Intune 卸载它。

5. 在“分配”边栏选项卡上选择“确定”。
6. 选择“添加组”边栏选项卡上的“确定”。
7. 选择“保存”，提交应用分配。

## <a name="next-steps"></a>后续步骤

- 若要了解如何将 Office 365 应用添加到 Windows 10 设备，请参阅[如何使用 Microsoft Intune 将 Office 365 专业增强版 2016 应用分配给 Windows 10 设备](apps-add-office365.md)。
- 要了解为用户组添加和排除应用分配，请参阅[添加和排除应用分配](apps-inc-exl-assignments.md)。
