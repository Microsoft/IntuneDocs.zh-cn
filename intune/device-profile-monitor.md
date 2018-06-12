---
title: 使用 Microsoft Intune 查看设备配置文件 - Azure | Microsoft Docs
description: 查看和管理 Microsoft Intune 中设备配置的配置文件详细信息，查看分配给配置文件的设备数量的图形图表，并查看哪些设备已分配或部署配置文件。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9deaed87-fb4b-4689-ba88-067bc61686d7
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bffb6832200379fca0221d8718afdebe06163980
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34744782"
---
# <a name="monitor-device-profiles-in-microsoft-intune"></a>在 Microsoft Intune 中监视设备配置文件

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 包含 Azure 门户中的一些功能，可帮助监视和管理设备配置的配置文件。 例如，可以检查配置文件的状态，查看分配的设备并更新配置文件的属性。

## <a name="view-existing-profiles"></a>查看现有配置文件

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 选择“设备配置” > “配置文件”。

列出现有的全部配置文件，并包含诸如平台之类的详细信息，以及配置文件是否分配给任何设备。

## <a name="view-details-on-a-profile"></a>查看配置文件中的详细信息

创建设备配置文件后，Intune 会提供图形图表。 这些图表显示配置文件的状态，例如成功分配给设备，或配置文件是否显示冲突。

1. 选择现有的配置文件。 例如，选择一个 macOS 配置文件。
2. 单击“概述”选项卡。

    顶部的图形图表显示分配给特定设备配置文件的设备数量。 例如，如果配置设备配置文件应用于 macOS 设备，则图表列出 macOS 设备的计数。

    它还显示分配了相同设备配置文件的其他平台的设备数量。 例如，它显示非 macOS 设备的计数。

    ![查看分配给设备配置文件的设备数量](./media/device-configuration-profile-graphical-chart.png)

    底部的图形图表显示分配给特定设备配置文件的用户数量。 例如，如果配置设备配置文件应用于 macOS 用户，则图表列出 macOS 用户的计数。

3. 选择顶部图形图表中的圆圈。 “设备状态”随即打开。

    列出分配给配置文件的设备，并显示配置文件是否成功部署。 另请注意，它只列出了具有特定平台的设备（例如 macOS）。

    关闭“设备状态”详细信息。

4. 选择底部图形图表中的圆圈。 “用户状态”随即打开。 

    列出分配给配置文件的用户，并显示配置文件是否成功部署。 另请注意，它只列出了具有特定平台的用户（例如 macOS）。

    关闭“用户状态”详细信息。

5. 返回“配置文件”列表，选择特定的配置文件。 也可以更改现有属性：
  - 属性：更改名称或更新任何现有设置。
  - 分配：包括或排除策略应该应用的设备。 选择“所选组”以选择特定的组。
  - 设备状态：列出分配给配置文件的设备，并显示配置文件是否成功部署。 可以选择特定设备以获取更多详细信息，包括已安装的应用。
  - 用户状态：列出受此配置文件影响的设备的用户名，以及配置文件是否成功部署。 可以选择特定用户以获取更多详细信息。
  - 每个设置状态：通过显示配置文件中的各个设置来筛选输出，并显示设置是否成功应用。

## <a name="next-steps"></a>后续步骤
[分配用户和设备配置文件](device-profile-assign.md)  
[设备配置文件的常见问题和解决方法](device-profile-troubleshoot.md)