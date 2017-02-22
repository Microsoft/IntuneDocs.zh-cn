---
title: "适用于 macOS 设备的 Intune 自定义设置 | Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：了解可以在 macOS 自定义配置文件中使用的设置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 68100ea5-7d9b-4c0b-8df7-b9a24b2442c8
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5ab494a3dd1e1bdea9703ab314574b192c5208ee
ms.openlocfilehash: 113572430f0ef82c9a6fa533e3d6fc17b86119cb


---

# <a name="custom-settings-for-macos-devices-in-intune-azure-preview"></a>Intune Azure 预览版中适用于 macOS 设备的自定义设置

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

使用 Microsoft Intune 的“macOS 自定义配置文件”将使用 [Apple Configurator 工具](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)创建的设置部署到 macOS 设备。 使用此工具可以创建控制这些设备的操作的许多设置，并将其导出到配置描述文件中。 然后可将此配置描述文件导入到 Intune macOS 自定义配置文件，并将这些设置部署到组织中的用户和设备。

此功能允许你部署不能与其他 Intune 配置文件策略一起配置的 macOS 设置。


1. 按照[如何在 Microsoft Intune 中配置自定义设备设置](how-to-configure-custom-settings.md)中的说明进行操作。
2. 在“创建配置文件”边栏选项卡上，指定下列信息：

- **自定义配置描述文件名称** - 提供策略的名称，该名称将显示在设备上以及 Intune 状态中。
- **配置描述文件** - 浏览到使用 Apple Configurator 创建的配置文件。
确保在要部署 macOS 自定义策略的设备上从 Apple Configurator 工具导出的设置与 macOS 版本兼容。 有关如何解析不兼容的设置的信息，可搜索 [Apple 开发人员](https://developer.apple.com/)网站上的“配置描述文件参考”和“移动设备管理协议参考”。

你已导入的文件将在边栏选项卡的“文件内容”区域显示。



<!--HONumber=Feb17_HO1-->


