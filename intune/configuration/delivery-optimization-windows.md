---
title: Microsoft Intune 中适用于 Windows 10 的传递优化设置 - Azure | Microsoft Docs
description: 配置通过 Intune 管理的 Windows 10 设备如何使用传递优化。 在 Intune 中，创建设备配置文件以从 Internet 安装更新。 此外，请参阅如何使用传递优化配置文件替换现有的更新通道。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: kerimh
ms.openlocfilehash: 7d94a2c7e47b3cfcc9f4592faf0a4c2a09a24ac4
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72495242"
---
# <a name="delivery-optimization-settings-in-microsoft-intune"></a>Microsoft Intune 中的传递优化设置

借助 Intune，可使用 Windows 10 设备的传递优化设置来减少这些设备下载应用程序和更新时的带宽消耗。 传递优化被配置为设备配置文件的一部分。  

本文介绍如何将传递优化设置配置为设备配置文件的一部分。 创建配置文件后，可将它分配或部署到 Windows 10 设备。 

有关 Intune 支持的传递优化设置的列表，请参阅 [Intune 的传递优化设置](../delivery-optimization-settings.md)。  

要了解 Windows 10 上的传递优化，请参阅 Windows 文档中的[传递优化更新](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization)。  


> [!NOTE]
> 软件更新 – Windows 10 更新通道  替换为“传递优化”  设置。 可以将现有更新通道更改为使用“传递优化”  设置。 [将现有更新通道迁移为传递优化](#move-existing-update-rings-to-delivery-optimization)（见本文） 
## <a name="create-the-profile"></a>创建配置文件

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。

2. 选择“设备配置”   > “配置文件”   > “创建配置文件”  。

3. 输入以下属性：

    - **名称**：输入新配置文件的描述性名称。
    - **说明**：输入配置文件的说明。 此设置是可选的，但建议进行。
    - **平台**：选择平台：  

        - **Windows 10 及更高版本**

    - **配置文件类型**：选择“传递优化”  。
    - **设置**：配置用于定义希望如何下载更新和应用的设置。 要了解可用设置，请参阅 [Intune 的传递优化设置](../delivery-optimization-settings.md)。

4. 完成后，选择“确定” > “创建”，保存所做更改   。

配置文件随即创建并显示在列表中。 接下来，[分配配置文件](device-profile-assign.md)，然后[监视其状态](device-profile-monitor.md)。

## <a name="move-existing-update-rings-to-delivery-optimization"></a>将现有更新通道迁移为传递优化

将“软件更新 - Windows 10 更新通道”替换为“传递优化”设置   。 可以轻松更改现有的更新通道以使用“传递优化”  设置。 要在创建传递优化配置文件时保持设置不变，请使用同一传递优化下载模式，然后设置已使用的相同设置  。 但是，可选择重新配置传递优化设置，以利用传递优化配置文件能够管理的所有附加设置。

1. 创建传递优化配置文件：

    1. 在 Intune 中，选择“设备配置”   > “配置文件”   > “创建配置文件”  。
    2. 输入以下属性：

        - **名称**：输入新配置文件的描述性名称。
        - **说明**：输入配置文件的说明。 此设置是可选的，但建议进行。
        - **平台**：选择“Windows 10 及更高版本”  。
        - **配置文件类型**：选择“传递优化”  。
        - **设置**：对于传递优化下载模式，除非要更改应用于设备的设置，否则请选择现有软件更新通道所用的同一模式  。 选项包括：
            - 未配置 
            - **仅 HTTP，无对等互连**
            - **在相同 NAT 后面与对等互连混合的 HTTP**
            - **跨专用组与对等互连混合的 HTTP**
            - **与 Internet 对等互连混合的 HTTP**
            - **无对等互连的简单下载模式**
            - **Bypass 模式**
    3. 配置可能想要管理的任何其他设置。
1. 将此新配置文件分配给与现有软件更新通道相同的设备和用户。 [分配配置文件](device-profile-assign.md)列出了具体步骤。

3. 取消配置现有的软件通道：
    1. 在 Intune 中，转到“软件更新”  > Windows 10 更新通道。
    2. 在列表中，选择更新通道。
    3. 在设置中，将“传递优化下载模式”  设置为“未配置”  。
    4. 依次单击“确定”   > “保存”  更改。

## <a name="next-steps"></a>后续步骤

[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。  
查看 Intune 的[传递优化设置](../delivery-optimization-settings.md)。
