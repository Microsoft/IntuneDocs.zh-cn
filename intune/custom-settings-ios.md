---
title: 在 Microsoft Intune 中向 iOS 设备添加自定义设置 - Azure | Microsoft Docs
titleSuffix: ''
description: 从 Apple Configurator 或 Apple 配置文件管理器工具导出 iOS 设置，然后将这些设置导入 Microsoft Intune。 这些设置可以创建、使用和控制 iOS 设备上的自定义设置和功能。 之后，可以将此自定义配置文件分配或分发到组织中的 iOS 设备，以创建基线或标准。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9637cc36d6ee901b5da0ffbe44180cd7dbdaffee
ms.sourcegitcommit: 78ae22b1a7cb221648fc7346db751269d9c898b1
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "66373990"
---
# <a name="use-custom-settings-for-ios-devices-in-microsoft-intune"></a>在 Microsoft Intune 中使用适用于 iOS 设备的自定义设置

借助 Microsoft Intune，可以使用“自定义配置文件”添加或创建适用于 iOS 设备的自定义设置。 自定义配置文件是 Intune 中的一项功能。 这项功能用于添加未内置到 Intune 的设备设置和功能。

使用 iOS 设备时，可以通过两种方法将自定义设置引入 Intune：

- [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)
- [Apple 配置文件管理器](https://support.apple.com/profile-manager)

这些工具可用于将设置导出到配置文件。 在 Intune 中，导入此文件，然后将该配置文件分配给 iOS 用户和设备。 分配后便会分发设置，并在组织中为 iOS 创建基线或标准。

本文介绍如何创建适用于 iOS 设备的自定义配置文件。 文中还对如何使用 Apple Configurator 和 Apple 配置文件管理器提供了一些指导。

## <a name="before-you-begin"></a>在开始之前

- 使用 Apple Configurator 创建配置文件时，请确保导出的设置与正在使用的设备上的 iOS 版本兼容  。 有关如何解决不兼容设置的信息，请在 [Apple 开发人员](https://developer.apple.com/)网站上搜索“配置文件参考”和“移动设备管理协议参考”   。

- 使用 Apple 配置文件管理器时，请务必  ：

  - 在配置文件管理器中启用[移动设备管理](https://help.apple.com/serverapp/mac/5.7/#/apd05B9B761-D390-4A75-9251-E9AD29A61D0C)。
  - 在配置文件管理器中添加 [iOS 设备](https://help.apple.com/profilemanager/mac/5.7/#/pm9onzap1984)。
  - 在配置文件管理器中添加设备后，转到“在库之下” > “设备”>“选择设备”>“设置”    。 输入设备的常规设置。

    下载并保存此文件。 需在 Intune 配置文件中输入此文件。

  - 请确保从 Apple 配置文件管理器导出的设置与正在使用的设备上的 iOS 版本兼容。 有关如何解决不兼容设置的信息，请在 [Apple 开发人员](https://developer.apple.com/)网站上搜索“配置文件参考”和“移动设备管理协议参考”   。

## <a name="create-the-profile"></a>创建配置文件

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“设备配置” > “配置文件” > “创建配置文件”    。
3. 输入以下设置：

    - **名称**：输入配置文件的名称，例如 `ios custom profile`。
    - **说明**：输入配置文件的说明。
    - **平台**：选择“iOS”  。
    - **配置文件类型**：选择“自定义”  。

4. 在“自定义配置”中，请输入以下设置  ：

    - **自定义配置文件名称**：输入策略的名称。 此名称将在设备上和 Intune 状态中显示。
    - **配置文件**：浏览到使用 Apple Configurator 或 Apple 配置文件管理器创建的配置文件。 已导入的文件显示在“文件内容”区域中  。

5. 选择“确定” > “创建”，以创建 Intune 配置文件   。 完成后，配置文件将显示在“设备配置 - 配置文件”列表中  。

## <a name="next-steps"></a>后续步骤

配置文件已创建，但它尚未起到任何作用。 下一步需要[分配配置文件](device-profile-assign.md)。

请参阅如何[在 macOS 设备上创建配置文件](custom-settings-macos.md)。 
