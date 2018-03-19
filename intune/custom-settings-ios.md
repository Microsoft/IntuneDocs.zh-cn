---
title: "适用于运行 iOS 的设备的 Microsoft Intune 自定义设置"
titleSuffix: Azure portal
description: "了解可以在 iOS 自定义配置文件中使用的设置。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 40e34a2e22c9349cad63d813b892863e0e8a2933
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-ios"></a>适用于运行 iOS 的设备的 Microsoft Intune 自定义设备设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用 Microsoft Intune 的“iOS 自定义配置文件”将使用 [Apple Configurator 工具](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)创建的设置分配到 iOS 设备。 使用此工具可以创建控制这些设备的操作的许多设置，并将其导出到配置描述文件中。 然后可将此配置描述文件导入到 Intune iOS 自定义配置文件，并将这些设置部署到组织中的用户和设备。

此功能允许你分配不能使用其他 Intune 配置文件类型配置的 iOS 设置。


1. 按照[如何在 Microsoft Intune 中配置自定义设备设置](custom-settings-configure.md)中的说明进行操作。
2. 在“自定义配置文件”窗格上，配置以下每个设置：

- **自定义配置文件名称** - 提供策略的名称，该名称在设备上以及 Intune 状态中显示。
- **配置描述文件** - 浏览到使用 Apple Configurator 创建的配置文件。
确保在要分配 iOS 自定义策略的设备上从 Apple Configurator 工具导出的设置与 iOS 版本兼容。 有关如何解析不兼容的设置的信息，可搜索 [Apple 开发人员](https://developer.apple.com/)网站上的“配置描述文件参考”和“移动设备管理协议参考”。

已导入的文件在窗格的“文件内容”区域中显示。
