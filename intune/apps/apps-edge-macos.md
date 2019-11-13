---
title: 使用 Microsoft Intune 将 Microsoft Edge 添加到 macOS 设备
titleSuffix: ''
description: 了解如何使用 Microsoft Intune 将 Microsoft Edge 添加到 macOS 设备。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: kellieei
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: c6726f731fba5bc41893f999ac627bff9a8aca1e
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "73754834"
---
# <a name="add-microsoft-edge-to-macos-devices-using-microsoft-intune"></a>使用 Microsoft Intune 将 Microsoft Edge 添加到 macOS 设备

必须首先将应用添加到 Intune 中，才可以部署、配置、监视或保护它们。 可用的[应用类型](~/apps/apps-add.md#app-types-in-microsoft-intune)之一是 Microsoft Edge 版本 77 和更高版本  。 通过在 Intune 中选择此应用类型，可以将 Microsoft Edge 版本 77 和更高版本分配并安装到你管理的运行 macOS 的设备  。 此应用类型使你可以轻松地将 Microsoft Edge 分配到 MacOS 设备，而无需使用 MacOS 应用包装工具。 为帮助保护和不断更新应用，这些应用随附 Microsoft AutoUpdate (MAU)。

> [!IMPORTANT]
> 此应用类型处于“公共预览”阶段，提供适用于 macOS 的开发人员和 beta 版本通道  。 部署仅使用英语 (EN) ，但最终用户可以在“设置” > “语言”下更改浏览器中的显示语言   。 

> [!NOTE]
> Microsoft Edge 版本 77 和更高版本也同样适用于 Windows 10  。

## <a name="prerequisites"></a>必备条件
- 在安装 Microsoft Edge 之前，macOS 设备必须运行 macOS 10.12 或更高版本。

## <a name="add-microsoft-edge-to-intune"></a>将 Microsoft Edge 添加到 Intune
可以使用以下步骤将 Microsoft Edge 版本 77 和更高版本添加到 Intune：

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 在“Intune”窗格中，选择“客户端应用” > “应用” > “添加”     。
3. 在 Microsoft Edge 版本 77 和更高版本下的“应用类型”中，选择“macOS”    。

## <a name="configure-app-information"></a>配置应用信息
在此步骤中，提供有关此应用部署的信息。 此信息可帮助你在 Intune 中标识应用，还可帮助用户在公司门户中找到该应用。

1. 单击“应用信息”以显示“应用信息”边栏选项卡   。
2. 在“应用信息”边栏选项卡中，提供有关此应用部署的信息  。 此信息可帮助你在 Intune 中标识应用，还可帮助用户在公司门户中找到该应用。
    - **名称**：输入应用的名称，该名称将显示在公司门户中。 请确保所有名称都是唯一的。 如果同一应用名称存在两次，则在公司门户中将仅向用户显示其中一个应用。
    - **说明**：输入应用的描述。 例如，可以在描述中列出目标用户。
    - **发布者**：Microsoft 显示为发布者。
    - **类别**：（可选）选择一个或多个内置应用类别或所创建的类别。 此设置可让用户在浏览公司门户时更轻松地找到该应用。
    - **在公司门户中将此应用显示为特色应用**：选择此选项，用户在公司门户中浏览应用时，将在主页上突出显示该应用。
    - **信息 URL**：（可选）输入包含此应用相关信息的网站的 URL。 在公司门户中向用户显示该 URL。
    - **隐私 URL**：（可选）输入包含此应用相关隐私信息的网站的 URL。 在公司门户中向用户显示该 URL。
    - **开发者**：Microsoft 显示为开发者。
    - **所有者**：Microsoft 显示为所有者。
    - **备注**：（可选）输入要与此应用关联的任何备注。
3. 选择“确定”  。

## <a name="configure-microsoft-edge-settings"></a>配置 Microsoft Edge 设置
在此步骤中，配置应用的安装选项。

1. 在“添加应用”边栏选项卡中，选择“应用设置”   。
2. 在“应用设置”边栏选项卡中，自动选择了“Beta”通道，且无法更改   。
    - “Beta”通道是最稳定的 Microsoft Edge 预览体验，也是组织内全面试用的最佳选择  。 每六周发布一次重大更新。

    > [!NOTE]
    > 用户浏览公司门户时，Microsoft Edge 浏览器徽标与应用一同显示。
3.  选择“确定”  。

## <a name="select-scope-tags-optional"></a>选择作用域标记（可选）。
可以使用作用域标记来确定谁可以在 Intune 中查看客户端应用信息。 若要详细了解作用域标记，请参阅将基于角色的访问控制和作用域标记用于分布式 IT。
1.  选择“作用域(标记)”   >   “添加”。
2.  使用“选择”  框搜索作用域标记。
3.  选中要分配到此应用的作用域标记旁边的复选框。
4.  单击“选择” > “确认”   。

## <a name="add-the-app"></a>添加应用
完成配置后，从“应用”边栏选项卡中选择“添加”   。 

此时，已创建的应用显示在应用列表中，可在此列表中将其分配到选择的组。 

> [!NOTE]
> 当前，Apple 没有提供通过 Intune 在 macOS 设备上卸载 Microsoft Edge 的方法。

## <a name="next-steps"></a>后续步骤
- 若要了解如何在 macOS 设备上配置 Microsoft Edge，请参阅[在 macOS 设备上配置 Microsoft Edge](https://docs.microsoft.com/deployedge/configure-microsoft-edge-on-mac)。
- 要了解从用户组添加和排除应用分配，请参阅[添加和排除应用分配](~/apps/apps-inc-exl-assignments.md)。
- [将应用分配给组](~/apps/apps-deploy.md)

