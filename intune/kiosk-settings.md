---
title: Microsoft Intune 中适用于 Windows 10 的展台设置 - Azure | Microsoft Docs
description: 了解可用来控制运行 Windows 10 的设备上的设备设置和功能的 Microsoft Intune 设置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 5/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 897ff48253961d6e1aa83bf36113c362d4548fbf
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745114"
---
# <a name="kiosk-settings-for-windows-10-and-later-in-intune"></a>Intune 中适用于 Windows 10 （及更高版本）的展台设置

可使用展台配置文件配置 Windows 10 设备以运行一个或多个应用。 配置展台配置文件时，还可以选择是否显示开始菜单、是否安装 Web 浏览器以及更多选项。

## <a name="kiosk-settings"></a>展台设置

1. 选择“添加”以创建展台环境。
2. 为展台输入“展台配置名称”。 此名称标识一组应用程序、这些应用在开始菜单上的布局以及分配给此展台配置的用户。
3. 选择“展台模式”。 “展台模式”标识策略支持的展台模式类型。 选项包括：

  - 未配置（默认设置）：策略不启用展台模式。
  - 单个全屏应用展台：该配置文件允许设备作为单个用户帐户运行，并将其锁定到单个通用 Windows 平台 (UWP) 应用。 所以，用户登录时，将启动一个特定应用。 此模式还会限制用户打开新应用或更改正在运行的应用。
  - 多应用展台：该配置文件允许设备运行多个通用 Windows 平台 (UWP) 应用或 Win32 应用。 还可以将不同的应用分配给不同的用户帐户。 用户仅可使用你添加的应用。 多应用展台或固定目标设备的优势在于，让用户仅访问其所需应用，提供易于理解的体验。 同时从其视图中删除他们不需要的应用。

#### <a name="single-full-screen-app-kiosks"></a>单个全屏应用展台
输入以下设置：

- 通用 Windows 平台 (UWP) 应用标识符：输入展台应用的应用程序用户模型 ID (AUMID)。 或者选择使用[移动应用](apps-add.md)添加的现有托管应用。

    请参阅 [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app)（查找已安装应用的应用程序用户模型 ID）。

- 用户帐户类型：选项：

  - 自动登录：对于启用了自动登录的面向公众的环境中的展台，应使用具有最低权限的用户（如本地标准用户帐户）。 若要针对展台模式配置 Azure Active Directory (AD) 帐户，请使用 `AzureAD\user@contoso.com` 格式。
  - 本地用户帐户：输入与展台应用相关联的本地（对设备而言）用户帐户或 Azure AD 帐户登录名。 对于加入 Azure AD 域的帐户，请使用 `domain\username@tenant.org` 格式输入帐户。

#### <a name="multi-app-kiosks"></a>多应用展台
在此模式下，可从“开始”菜单使用应用。 其中仅包含用户可以打开的应用。 

[多应用展台](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#configure-a-kiosk-in-microsoft-intune)使用可列出允许的应用和其他设置的展台配置。

输入以下设置：

- 添加 Win32 应用：Win32 应用是传统的桌面应用。 输入“应用名称”和“标识符”。 就设备而言，标识符是可执行文件的完全限定的路径名。
- 添加托管应用：选择使用 [Intune 中的“移动应用”](apps-add.md)添加的现有托管应用。
- 通过 AUMID 添加应用：输入[应用的 AUMID](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app)（UWP 应用）。
- **任务栏**：在展台上选择“启用”（显示）任务栏，或将其保持为“未配置”（隐藏）。
- “开始”菜单布局：输入一个 XML 文件，用于描述应用在“开始”菜单上的显示方式，包括应用的顺序。 相关指导和示例 XML，请参阅[自定义和导出“开始”布局](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout)。

  有关使用和创建 XML 文件的更多详细信息，请参阅[创建运行多个应用的 Windows 10 展台](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#create-xml-file)。

- 用户帐户类型：添加一个或多个可以使用你添加的应用的用户帐户。 帐户登录后，仅可使用在配置中定义的应用。 该帐户可以是设备的本地帐户，也可以是与展台应用相关联的 Azure AD 帐户登录。

    对于启用了自动登录功能的面向公众的环境中的展台，应使用具有最低权限的用户类型（例如本地标准用户帐户）。 若要针对展台模式配置 Azure Active Directory (AD) 帐户，请使用 `domain\user@tenant.com` 格式。

## <a name="kiosk-web-browser-settings"></a>展台 Web 浏览器设置

这些设置控制展台上的 Web 浏览器应用。 请确保使用“[移动应用](apps-add.md)”向展台设备部署 Web 浏览器应用。

1. 输入以下设置：

  - 默认主页 URL：输入展台浏览器在打开或重新启动浏览器时打开的默认 URL。

  - 显示主页按钮：显示（“需要”）或隐藏（“未配置”）展台浏览器的主页按钮。 默认情况下，“未配置”该按钮。

  - 显示导航按钮：显示（“需要”）或隐藏（“未配置”）前进和后退按钮。 默认情况下，“未配置”导航按钮。

  - 当用户超出空闲时间限制时刷新浏览器：以分钟为单位，输入展台浏览器以刷新状态重新启动之前的会话空闲时长。 该值为 1-1440 分钟之内的整数。 默认情况下，该值为空，这意味着未设置空闲超时时长。

  - 已阻止的网站：已阻止的网站 URL 列表（支持使用通配符）。 使用此设置来防止浏览器打开特定网站。 还可以“导入”包含列表的 .csv 文件。 或者，创建包含你添加的网站的 .csv 文件（“导出”）。

  - 网站例外：已阻止网站 URL 的例外列表（支持使用通配符）。 使用此设置允许浏览器打开特定网站。 这些例外是已阻止 URL 的子集。 如果某个 URL 位于已阻止的网站列表和网站例外列表中，则该例外生效。

    还可以“导入”包含列表的 .csv 文件。 或者，创建包含你添加的网站的 .csv 文件（“导出”）。

2. 选择“确定”，保存所做更改。

## <a name="next-steps"></a>后续步骤
[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。