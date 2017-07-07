---
title: "适用于 macOS 设备的 Intune 自定义设置"
titleSuffix: Intune on Azure
description: "了解可在 macOS 自定义配置文件中使用的设置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 68100ea5-7d9b-4c0b-8df7-b9a24b2442c8
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 57c4ec3621ffaef5c1aaffd55c87baac91e50154
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="custom-settings-for-macos-devices-in-microsoft-intune"></a>Microsoft Intune 中适用于 macOS 设备的自定义设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用 Microsoft Intune 的“macOS 自定义配置文件”将使用 [Apple Configurator 工具](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)创建的设置分配到 macOS 设备。 使用此工具可以创建控制这些设备的操作的许多设置，并将其导出到配置描述文件中。 然后可将此配置描述文件导入到 Intune macOS 自定义配置文件，并将这些设置部署到组织中的用户和设备。

此功能允许你分配不能使用其他 Intune 配置文件类型配置的 macOS 设置。


1. 按照[如何在 Microsoft Intune 中配置自定义设备设置](custom-settings-configure.md)中的说明进行操作。
2. 在“创建配置文件”边栏选项卡上，指定下列信息：

- **自定义配置描述文件名称** - 提供策略的名称，该名称将显示在设备上以及 Intune 状态中。
- **配置描述文件** - 浏览到使用 Apple Configurator 创建的配置文件。
确保在要分配 macOS 自定义策略的设备上从 Apple Configurator 工具导出的设置与 macOS 版本兼容。 有关如何解析不兼容的设置的信息，可搜索 [Apple 开发人员](https://developer.apple.com/)网站上的“配置描述文件参考”和“移动设备管理协议参考”。

你已导入的文件将在边栏选项卡的“文件内容”区域显示。
