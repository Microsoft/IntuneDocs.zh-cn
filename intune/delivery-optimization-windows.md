---
title: Microsoft Intune 中适用于 Windows 10 的传递优化设置 - Azure | Microsoft Docs
description: 使用 Windows 10 及更高版本设备提供的传递优化云服务，配置将软件更新传递到设备的具体方式。 在 Intune 中，创建设备配置文件以从 Internet 安装更新。 此外，请参阅如何使用传递优化配置文件替换现有的更新通道。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 36cfb5ac05b2d69b5c7349f4ebc6054848a08fc8
ms.sourcegitcommit: ecd6aebe50b1440a282dfdda771e37fbb8750d42
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/01/2018
ms.locfileid: "52730395"
---
# <a name="windows-10-and-newer-delivery-optimization-settings-in-microsoft-intune"></a>Microsoft Intune 中的 Windows 10（和更高版本）传递优化设置

本文列举并介绍了可以为 Windows 10 设备配置的所有传递优化设置。 将这些设置添加到设备配置文件，然后使用 Microsoft Intune 将其分配或部署到设备中。

## <a name="settings"></a>设置

**传递优化下载模式**：选择将更新传递到设备的方式。 选项包括：

- **未配置**：最终用户使用自己的方法更新其设备，可能使用的是 Windows 更新或操作系统提供的“传递优化”设置。
- **仅 HTTP，无对等互连**：仅从 Internet 获取更新。 不从网络上的其他计算机（称为对等互连或对等）获取更新。
- **与跨专用组的对等互连混合的同一 NAT HTTP 后面与对等互连混合的 HTTP**：从 Internet 和网络上的其他计算机获取更新。 对等互连在同一 Active Directory 站点（如果存在）或同一域中的设备上发生。 在选中此选项后，在整个网络地址转换 (NAT) IP 地址中进行对等互连。
- **与 Internet 对等互连混合的 HTTP**：从 Internet 和网络上的其他计算机获取更新。
- **无对等互连的简单下载模式**：直接从更新所有者（如 Microsoft）通过 Internet 获取更新。 它不会联系传递优化云服务。
- **Bypass 模式**：使用后台智能传送服务 (BITS) 获取更新。 请勿使用传递优化。

## <a name="move-from-existing-update-rings-to-delivery-optimization"></a>从现有的更新通道移动到传递优化

软件更新 – Windows 10 更新通道替换为“传递优化”设置。 可以轻松更改现有的更新通道以使用“传递优化”设置。 步骤：

1. 创建传递优化配置文件：

    1. 在 Intune 中，选择“设备配置” > “配置文件” > “创建配置文件”。
    2. 输入配置文件的“名称”和“描述”。
    3. 对于“平台”，选择“Windows 10 及更高版本”。 对于“配置文件类型”，选择“传递优化”。
    4. 选择“设置”。 对于“传递优化下载模式”，选择现有软件更新通道所使用的同一模式。 选项包括：
        - 未配置
        - **仅 HTTP，无对等互连**
        - **与跨专用组的对等互连混合的同一 NAT HTTP 后面与对等互连混合的 HTTP**
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