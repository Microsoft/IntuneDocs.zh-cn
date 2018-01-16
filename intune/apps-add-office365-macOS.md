---
title: "使用 Intune 将 Office 365 安装到 macOS 设备"
titlesuffix: Azure portal
description: "了解如何使用 Intune 更轻松地在 macOS 设备上安装 Office 365 应用。"
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 12/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5e0ad0b99a2c8a602b5e542530a1d437065461b2
ms.sourcegitcommit: 22ab1c6a6bfeb4fef9850d12b29829c3fecbbeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/12/2018
---
# <a name="how-to-assign-office-365-to-macos-devices-with-microsoft-intune"></a>如何使用 Microsoft Intune 将 Office 365 分配给 macOS 设备

借助此应用类型，可以轻松地将 Office 365 应用分配给 macOS 设备。 使用此新应用类型，可以安装 Word、Excel、PowerPoint、Outlook 和 OneNote。 这些应用还随附 Microsoft AutoUpdate (MAU)，有助于保护和不断更新应用。 所需的应用将显示为 Intune 控制台的应用列表中的一个应用。


## <a name="before-you-start"></a>开始之前

- 部署这些应用的设备必须运行 macOS 10.10 或更高版本。
- Intune 仅支持添加 Office 2016 for Mac 套件随附的 Office 应用。
- 如果任何 Office 应用在 Intune 安装应用套件时处于打开状态，最终用户可能会丢失未保存文件中的数据。


## <a name="get-started"></a>入门
使用“应用”边栏选项卡添加 Office 365。
1.  登录 Azure 门户。
2.  选择“更多服务” > “监视 + 管理” > “Intune”。
3.  在 Intune 边栏选项卡上，选择“移动应用”。
4.  在“移动应用”工作负载中，选择“管理”组中的“应用”。 选择“添加”。
5.  在“添加应用”边栏选项卡上，依次选择“Office 365” > “macOS”。
6.  选择“添加”。

## <a name="configure-the-app-suite"></a>配置应用套件

提供应用套件的相关信息。 此信息有助于在 Intune 中识别它，也有助于用户在公司门户应用中找到它。

1.  在“添加应用”边栏选项卡上，选择“应用套件信息”。
2.  指定下列信息：
    - **套件名称** - 输入应用套件的名称，该名称将显示在公司门户中。 请确保使用的所有套件名称都是唯一的。 如果同一应用套件名称存在两次，则在公司门户中将仅向用户显示其中一个应用。
    - **套件描述** - 为应用套件输入描述。
    - **发布者** - Microsoft 显示为发布者。
    - **类别** -（可选）选择一个或多个内置应用类别或所创建的类别。 这样，可让用户在浏览公司门户时更轻松地查找应用套件。
    - **在“公司门户”中将此显示为特别推荐的应用** - 当用户浏览应用时，此设置会在“公司门户”的主页上突出显示应用套件。
    - **信息 URL** -（可选）输入包含此应用相关信息的网站 URL。 在公司门户中向用户显示该 URL。
    - **隐私 URL** -（可选）输入包含此应用相关隐私信息的网站 URL。 在公司门户中向用户显示该 URL。
    - **开发人员** - Microsoft 显示为开发人员。
    - **所有者** - Microsoft 显示为所有者。
    - **说明** - 输入要与此应用关联的任何备注。
    - **上传图标** - 用户浏览公司门户时，上传与应用一同显示的图标。
3.  选择“确定”。 应用套件在应用列表中显示为各个条目。

## <a name="configure-app-assignments"></a>配置应用分配

在这一步中，配置应用套件分配。 请注意，可用的应用类型即将推出。

1.  依次选择应用列表中的应用套件和“分配”。
2.  选择“选择组”。
3.  将应用套件分配给选定组。 有关详细信息，请参阅[如何使用 Microsoft Intune 将应用分配到组](/intune/apps-deploy)。
4.  对于每个组，选择“需要安装”。
        >[!Note]
        > You cannot uninstall Office 365 through Intune.

5. 选择“保存”，提交应用分配。

## <a name="next-steps"></a>后续步骤

若要了解如何将 Office 365 应用添加到 Windows 10 设备，请参阅[如何使用 Microsoft Intune 将 Office 365 专业增强版 2016 应用分配给 Windows 10 设备](/intune/apps-add-office365)。
