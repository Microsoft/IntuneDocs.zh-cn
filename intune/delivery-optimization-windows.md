---
title: Microsoft Intune 中适用于 Windows 10 的传递优化设置 - Azure | Microsoft Docs
description: 使用 Windows 10 及更高版本设备提供的传递优化云服务，配置将软件更新传递到设备的具体方式。 在 Intune 中，创建设备配置文件以从 Internet 安装更新。 此外，请参阅如何使用传递优化配置文件替换现有的更新通道。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0a59cab5f709897e064b315193b292cb46dc2f2e
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831541"
---
# <a name="windows-10-and-newer-delivery-optimization-settings-in-microsoft-intune"></a>Microsoft Intune 中的 Windows 10（和更高版本）传递优化设置

> [!NOTE]
> 软件更新 – Windows 10 更新通道替换为“传递优化”设置。 可以将现有更新通道更改为使用“传递优化”设置。 （本文中的）[将现有更新通道迁移为传递优化](#move-existing-update-rings-to-delivery-optimization)列出了相关步骤。 


此功能适用于以下平台：

- Windows 10 及更高版本

本文列举并介绍了可以为 Windows 10 设备配置的所有传递优化设置。 将这些设置添加到设备配置文件，然后使用 Microsoft Intune 将其分配或部署到设备中。

[传递优化更新](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization)是一个不错的资源，可用于了解有关 Windows 10 上的传递优化的详细信息。

## <a name="create-the-profile"></a>创建配置文件

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”> 筛选“Intune”> 选择“Intune”。

2. 选择“设备配置” > “配置文件” > “创建配置文件”。

3. 输入以下属性：

    - **名称**：输入新配置文件的描述性名称。
    - **说明**：输入配置文件的说明。 此设置是可选的，但建议进行。
    - **平台**：选择平台：  

        - **Windows 10 及更高版本**

    - **配置文件类型**：选择“传递优化”。
    - **设置**：选择更新下载方式。 选项包括： 

        - **未配置**：最终用户使用自己的方法更新其设备，可能使用的是 Windows 更新或操作系统提供的“传递优化”设置。
        - **仅 HTTP，无对等互连**：仅从 Internet 获取更新。 不从网络上的其他计算机（称为对等互连或对等）获取更新。
        - **在相同 NAT 后面与对等互连混合的 HTTP**：从 Internet 和网络上的其他计算机获取更新。 
        - **跨专用组与对等互连混合的 HTTP**：对等互连在同一 Active Directory 站点（如果存在）或同一域中的设备上发生。 在选中此选项后，在整个网络地址转换 (NAT) IP 地址中进行对等互连。
        - **与 Internet 对等互连混合的 HTTP**：从 Internet 和网络上的其他计算机获取更新。
        - **无对等互连的简单下载模式**：直接从更新所有者（如 Microsoft）通过 Internet 获取更新。 它不会联系传递优化云服务。
        - **Bypass 模式**：使用后台智能传送服务 (BITS) 获取更新。 请勿使用传递优化。

4. 完成后，选择“确定” > “创建”，保存所做更改。

此时，配置文件创建完成，并出现在列表中。 下一步，[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

## <a name="move-existing-update-rings-to-delivery-optimization"></a>将现有更新通道迁移为传递优化

软件更新 – Windows 10 更新通道替换为“传递优化”设置。 可以轻松更改现有的更新通道以使用“传递优化”设置。 步骤：

1. 创建传递优化配置文件：

    1. 在 Intune 中，选择“设备配置” > “配置文件” > “创建配置文件”。
    2. 输入以下属性：

        - **名称**：输入新配置文件的描述性名称。
        - **说明**：输入配置文件的说明。 此设置是可选的，但建议进行。
        - **平台**：选择“Windows 10 及更高版本”。
        - **配置文件类型**：选择“传递优化”。
        - **设置**：对于“传递优化下载模式”，选择现有软件更新通道所使用的同一模式。 选项包括：
            - 未配置
            - **仅 HTTP，无对等互连**
            - **在相同 NAT 后面与对等互连混合的 HTTP**
            - **跨专用组与对等互连混合的 HTTP**
            - **与 Internet 对等互连混合的 HTTP**
            - **无对等互连的简单下载模式**
            - **Bypass 模式**

2. 将此新配置文件分配给与现有软件更新通道相同的设备和用户。 [分配配置文件](device-profile-assign.md)列出了具体步骤。

3. 取消配置现有的软件通道：
    1. 在 Intune 中，转到“软件更新”> Windows 10 更新通道。
    2. 在列表中，选择更新通道。
    3. 在设置中，将“传递优化下载模式”设置为“未配置”。
    4. 依次单击“确定” > “保存”更改。

## <a name="next-steps"></a>后续步骤

[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。
