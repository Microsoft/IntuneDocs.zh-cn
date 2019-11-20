---
title: 使用 Microsoft Intune 查看设备配置文件 - Azure | Microsoft Docs
description: 查看和管理 Microsoft Intune 中设备配置的配置文件详细信息，查看分配给配置文件的设备数量的图形图表，并查看哪些设备已分配或部署配置文件。 也可对具有冲突设置的配置文件进行故障排除。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9deaed87-fb4b-4689-ba88-067bc61686d7
ms.reviewer: karthib
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 85ba34cfec8ebe78d2574034967bd7ed76f3304e
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059548"
---
# <a name="monitor-device-profiles-in-microsoft-intune"></a>在 Microsoft Intune 中监视设备配置文件

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune 包含一些功能，可帮助监视和管理设备配置文件。 例如，可以检查配置文件的状态，查看分配的设备并更新配置文件的属性。

## <a name="view-existing-profiles"></a>查看现有配置文件

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“设备”   > “配置文件”  。

列出了现有的全部配置文件，包含诸如平台之类的详细信息，并显示配置文件是否分配给任何设备。

## <a name="view-details-on-a-profile"></a>查看配置文件中的详细信息

创建设备配置文件后，Intune 会提供图形图表。 这些图表显示配置文件的状态，例如成功分配给设备，或配置文件是否显示冲突。

1. 选择现有的配置文件。 例如，选择一个 macOS 配置文件。
2. 单击“概述”  选项卡。

    顶部的图形图表显示分配到设备配置文件的设备数量。 例如，如果配置设备配置文件应用于 macOS 设备，则图表列出 macOS 设备的计数。

    它还显示分配了相同设备配置文件的其他平台的设备数量。 例如，它显示非 macOS 设备的计数。

    ![查看分配给设备配置文件的设备数量](./media/device-profile-monitor/device-configuration-profile-graphical-chart.png)

    底部的图形图表显示分配到设备配置文件的用户数量。 例如，如果配置设备配置文件应用于 macOS 用户，则图表列出 macOS 用户的计数。

3. 选择顶部图形图表中的圆圈。  “设备状态”随即打开。

    列出分配给配置文件的设备，并显示配置文件是否成功部署。 另请注意，它只列出了具有特定平台的设备（例如 macOS）。

    关闭“设备状态”详细信息  。

4. 选择底部图形图表中的圆圈。 “用户状态”随即打开  。 

    列出分配给配置文件的用户，并显示配置文件是否成功部署。 另请注意，它只列出了具有特定平台的用户（例如 macOS）。

    关闭“用户状态”详细信息  。

5. 返回“配置文件”列表，选择特定的配置文件  。 也可以更改现有属性：
    - **属性**：更改名称或更新任何现有设置。
    - **分配**：包含或排除应该应用策略的设备。 选择  “所选组”以选择特定的组。
    - **设备状态**：列出分配给配置文件的设备，并显示配置文件是否成功部署。 可以选择特定设备以获取更多详细信息，包括已安装的应用。
    - **用户状态**：列出受此配置文件影响的用户的名称及设备，以及配置文件是否已成功部署。 可以选择特定用户以获取更多详细信息。
    - **每个设置状态**：通过显示配置文件中的各个设置来筛选输出，并显示设置是否成功应用。

## <a name="view-conflicts"></a>查看冲突

在“设备” > “所有设备”中，可看到导致冲突的任何设置   。 出现冲突时，你还会看到包含此设置的所有配置文件。 管理员可使用此功能来帮助排除故障，并修复配置文件中的任何差异。

1. 在 Intune 中，选择“设备” > “所有设备”> 选择列表中的现有设备   。 最终用户可从公司门户应用获取设备名。
2. 选择“设备配置”  。 列出了适用于该设备的所有配置策略。
3. 选择策略。 它会显示该策略中适用于该设备的所有设置。 如果设备具有“冲突”状态，请选择该行  。 在新窗口中，将看到所有配置文件，以及具有导致冲突的设置的配置文件名称。

既然知道了冲突的设置以及包含该设置的策略，应该较容易解决冲突。 

## <a name="device-firmware-configuration-interface-profile-reporting"></a>设备固件配置接口配置文件报告

> [!WARNING]
> 正在创建监视 DFCI 配置文件。 当 DFCI 处于公共预览版时，监视数据可能丢失或不完整。

与其他设备配置文件一样，DFCI 配置文件按设置进行报告。 根据制造商对 DFCI 的支持，某些设置可能不适用。

通过 DFCI 配置文件设置，你可能会看到以下状态：

- **符合**：当配置文件中的设置值与设备上的设置匹配时，将显示此状态。 在下列情况下，可能出现此状态：

  - DFCI 配置文件成功配置了配置文件中的设置。
  - 设备没有由设置控制的硬件功能，并且配置文件设置为“已禁用”  。
  - UEFI 不允许 DFCI 禁用此功能，并且配置文件设置为“已启用”  。
  - 该设备缺少禁用该功能的硬件，并且配置文件设置为“已启用”  。

- **不适用**：当配置文件中的设置值为“已启用”，并且在设备上找不到匹配的设置时，将显示此状态  。 如果设备硬件不具有此功能，可能会出现此状态。

- **不符合**：当配置文件中的设置值与设备上的设置不匹配时，将显示此状态。 在下列情况下，可能出现此状态：

  - UEFI 不允许 DFCI 禁用设置，并且配置文件设置为“已禁用”  。
  - 该设备缺少禁用该功能的硬件，并且配置文件设置为“已禁用”  。
  - 该设备没有最新的 DFCI 固件版本。
  - 在使用 UEFI 菜单中的本地“退出”控件注册到 Intune 之前，DFCI 是禁用的。
  - 设备在 Autopilot 注册之外注册到 Intune。
  - 该设备未由 Microsoft CSP 注册到 Autopilot，也未由 OEM 直接注册。

## <a name="next-steps"></a>后续步骤

[设备配置文件的常见疑问、问题和解决方案](device-profile-troubleshoot.md)  
[在 Intune 中对策略和配置文件进行故障排除](troubleshoot-policies-in-microsoft-intune.md)
