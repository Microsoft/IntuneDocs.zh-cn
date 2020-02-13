---
title: Microsoft Intune 中适用于 Windows 10 的传递优化设置 - Azure | Microsoft Docs
description: 配置通过 Intune 管理的 Windows 10 设备如何使用传递优化。 在 Intune 中，创建设备配置文件以从 Internet 安装更新。 此外，请参阅如何使用传递优化配置文件替换现有的更新通道。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/10/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: kerimh
ms.openlocfilehash: 9fb4aab6b02c6ad6a5d2f18ca9d15beafc12d58a
ms.sourcegitcommit: e1ff157f692983b49bdd6e20cc9d0f93c3b3733c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124803"
---
# <a name="delivery-optimization-settings-in-microsoft-intune"></a>Microsoft Intune 中的传递优化设置

借助 Intune，可使用 Windows 10 设备的传递优化设置来减少这些设备下载应用程序和更新时的带宽消耗。 在设备配置文件配置传递优化。  

本文介绍如何将传递优化设置配置为设备配置文件的一部分。 创建配置文件后，可将它分配或部署到 Windows 10 设备。 

若要查看 Intune 支持的传递优化设置的列表，请参阅 [Intune 的传递优化设置](../delivery-optimization-settings.md)。  

要了解 Windows 10 上的传递优化，请参阅 Windows 文档中的[传递优化更新](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization)。  

## <a name="create-the-profile"></a>创建配置文件

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 选择“设备” > “配置文件” > “创建配置文件”。

3. 输入以下属性：

    - **名称**：输入新配置文件的描述性名称。
    - **描述**：输入配置文件的说明。 此设置是可选的，但建议进行。
    - **平台**：选择“Windows 10 及更高版本”。
    - **配置文件类型**：选择“传递优化”。

4. 选择“设置” > “配置”然后定义希望如何下载更新和应用。 要了解可用设置，请参阅 [Intune 的传递优化设置](../delivery-optimization-settings.md)。

5. 完成后，选择“确定” > “创建”，保存所做更改。

配置文件随即创建并显示在列表中。 接下来，[分配配置文件](device-profile-assign.md)，然后[监视其状态](device-profile-monitor.md)。

<!-- ## Move existing update rings to delivery optimization

**Delivery optimization** settings replace **Software updates – Windows 10 Update Rings**. Your existing update rings can be easily changed to use the **Delivery optimization** settings. To maintain the same settings when you create a delivery optimization profile, use the same *Delivery optimization download mode* and then set the same settings as you already use. However, you can choose to reconfigure delivery optimization settings to take advantage of the full range of addition settings that the Delivery Optimization profile can manage. 
-->

## <a name="remove-delivery-optimization-from-windows-10-update-rings"></a>从 Windows 10 更新通道中删除传递优化

以前在软件更新通道中配置传递优化。 从 2019 年 2 月开始，在设备配置文件中配置传递优化设置。该配置文件包括其他设置，其影响不限于向备传递软件更新。 如果尚未从更通道中删除传递优化设置，请将其设置为“未配置”以将其删除，然后使用“传递优化”配置文件来管理更大范围的可用选项。

1. 创建“传递优化”设备配置文件：

    1. 在 Microsoft 终结点管理器管理中心中，选择“设备” > “配置文件” > “创建配置文件”。
    2. 输入以下属性：

        - **名称**：输入新配置文件的描述性名称。
        - **描述**：输入配置文件的说明。 此设置是可选的，但建议进行。
        - **平台**：选择“Windows 10 及更高版本”。
        - **配置文件类型**：选择“传递优化”。
        - **设置**：对于传递优化下载模式，除非要更改应用于设备的设置，否则请选择现有软件更新通道所用的同一模式。 选项包括：
            - 未配置
            - **仅 HTTP，无对等互连**
            - **在相同 NAT 后面与对等互连混合的 HTTP**
            - **跨专用组与对等互连混合的 HTTP**
            - **与 Internet 对等互连混合的 HTTP**
            - **无对等互连的简单下载模式**
            - **Bypass 模式**
    3. 配置可能想要管理的任何其他设置。

2. 将此新配置文件分配给与现有软件更新通道相同的设备和用户。 [分配配置文件](device-profile-assign.md)列出了具体步骤。

3. 取消配置现有的软件通道：
    1. 在 Microsoft 终结点管理器管理中心，转到“软件更新”>“Windows 10 更新圈”。
    2. 在列表中，选择更新通道。
    3. 在设置中，将“传递优化下载模式”设置为“未配置”。
    4. 依次单击“确定” > “保存”更改。

## <a name="next-steps"></a>后续步骤

[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。  
查看 Intune 的[传递优化设置](../delivery-optimization-settings.md)。
