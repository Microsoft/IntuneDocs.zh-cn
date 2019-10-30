---
title: 将 Microsoft Edge for Windows 10 添加到 Microsoft Intune
titleSuffix: ''
description: 了解如何将 Microsoft Edge for Windows 添加到 Microsoft Intune。
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
ms.openlocfilehash: 492feb3f2ef5f5bbbc1537d4c60ac12d5fd6bdcd
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585600"
---
# <a name="add-microsoft-edge-for-windows-10-to-microsoft-intune"></a>将 Microsoft Edge for Windows 10 添加到 Microsoft Intune

必须首先将应用添加到 Intune 中，才可以部署、配置、监视或保护它们。 可用的[应用类型](~/apps/apps-add.md#app-types-in-microsoft-intune)之一是 Microsoft Edge 版本 77 和更高版本  。 通过在 Intune 中选择此应用类型，可以将 Microsoft Edge 版本 77 和更高版本分配并安装到由你管理的运行 Windows 10 的设备  。

> [!IMPORTANT]
> 此应用类型处于“公共预览”阶段，提供适用于 Windows 10 的开发人员和 beta 版本通道  。 部署仅使用英语 (EN)，但最终用户可以在“设置” > “语言”下更改浏览器中的显示语言   。 Microsoft Edge 是一款安装在系统上下文和类似体系结构中的 Win32 应用（在 x86 OS 上安装为 x86 应用，在 x64 OS 上安装为 x64 应用）。 另外，默认“启用”Edge 的自动更新，且无法卸载 Edge  。

> [!NOTE]
> Microsoft Edge 版本 77 和更高版本也同样适用于 macOS  。
> 
> 不能将 Microsoft Edge 的内置应用程序部署用于工作区加入计算机。 内置应用程序部署需要 Intune 管理扩展，只有已加入 AAD 的设备才有此扩展。 仍可使用上传到“客户端应用”的 .msi 部署 Microsoft Edge 77 及更高版本，请参阅[将 Windows 业务线应用添加到 Microsoft Intune](~/apps/lob-apps-windows.md)    。

## <a name="prerequisites"></a>必备条件
- 需要 Windows 10 RS2 及更高版本。
- 用户上下文中预安装的任何“开发人员”和“beta 版本”通道 Microsoft Edge 版本 77 及更高版本都将被系统上下文中安装的 Edge 覆盖    。

## <a name="configure-the-app-in-intune"></a>在 Intune 中配置应用
可以使用以下步骤将 Microsoft Edge 版本 77 和更高版本添加到 Intune：

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 在“Intune”窗格中，选择“客户端应用” > “应用” > “添加”     。
3. 在 Microsoft Edge 版本 77 和更高版本下的“应用类型”列表中，选择“Windows 10”    。

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

## <a name="configure-app-settings"></a>配置应用设置
在此步骤中，配置应用的安装选项。

1. 在“添加应用”边栏选项卡中，选择“应用设置”   。
2. 在“应用设置”边栏选项卡中，从“通道”列表中选择“Beta”或“开发”，以确定要从哪个 Edge 通道部署应用     。
    - “Beta”通道是最稳定的 Microsoft Edge 预览体验，也是在组织内全面试用的最佳选择  。 每六周发布一次重大更新，每个版本中都会加入开发人员通道的经验和改进。
    - “开发”通道适用于在 Windows、Windows Server 和 macOS 上提供反馈的企业  。 它每周更新，包含最新的改进和修复。

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
完成应用配置后，从“添加应用”边栏选项卡中选择“添加”   。 

此时，已创建的应用显示在应用列表中，可在此列表中将其分配到选择的组。 

> [!NOTE]
> 目前，如果取消分配 Microsoft Edge 的部署，它将保留在设备上。

## <a name="troubleshooting"></a>疑难解答
**适用于 Windows 10 的 Microsoft Edge 77 及更高版本：**<br>
Intune 使用 Intune 管理扩展下载 Microsoft Edge 安装程序并将其部署到指定的 Windows 10 设备，然后将部署设置发送到 Microsoft Edge 安装程序，后者直接从 CDN 下载并安装 Microsoft Edge 浏览器。 请参考 [Intune 管理扩展的先决条件](~/apps/intune-management-extension.md#prerequisites)以及“访问 Azure 更新服务”和 CDN 中概述的最佳做法，以确保你的网络配置允许 Windows 10 设备访问这些位置。

## <a name="next-steps"></a>后续步骤
- [将应用分配给组](~/apps/apps-deploy.md)
