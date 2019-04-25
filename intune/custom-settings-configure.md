---
title: 在 Microsoft Intune 中使用自定义设备设置 - Azure | Microsoft Docs
description: 添加或创建配置文件，以便通过 Microsoft Intune 使用适用于 Windows Phone、Windows 8.1、Windows 10 及更高版本、Android、Android Enterprise、macOS 和 iOS 设备的自定义设置
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/23/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 923570324dba89efdc9e314f18307ea7310bb252
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61508100"
---
# <a name="create-a-profile-with-custom-settings-in-intune"></a>使用 Intune 中的自定义设置创建配置文件

## <a name="what-are-custom-profiles"></a>什么是自定义配置文件

Microsoft Intune 含有许多内置设置，用于控制设备上的不同功能。 你还可以创建自定义配置文件。 希望使用未内置于 Intune 中的设备设置和功能时，自定义配置文件非常有用。 这些配置文件包含用于控制组织中设备的功能和设置。 例如，你可以创建自定义配置文件，为每台 iOS 设备设置相同的功能。

有关配置文件的详细信息，请参阅[什么是 Microsoft Intune 设备配置文件？](device-profiles.md)。 

本文包含指向创建适用于 Android、Android Enterprise、iOS、macOS 和 Windows 的自定义配置文件的链接。

## <a name="available-platforms"></a>可用平台

每个平台的自定义设置配置都不相同。 例如，要控制 Android 和 Windows 设备上的功能，可输入开放移动联盟统一资源标识符 (OMA-URI) 值。 对于 Apple 设备，则可以导入使用 [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) 或 [Apple 配置文件管理器](https://support.apple.com/profile-manager)创建的文件。

自定义配置文件创建方式类似于内置配置文件，并可用于以下平台：

- [Outlook Web Access (OWA)](custom-settings-android.md)
- [Android Enterprise](custom-settings-android-for-work.md)
- [iOS](custom-settings-ios.md)
- [macOS](custom-settings-macos.md)
- [Windows 10](custom-settings-windows-10.md)
- [Windows Holographic for Business](custom-settings-windows-holographic.md)
- [Windows Phone 8.1](custom-settings-windows-phone-8-1.md)

## <a name="next-steps"></a>后续步骤

选择平台，并开始：

- [Outlook Web Access (OWA)](custom-settings-android.md)
- [Android Enterprise](custom-settings-android-for-work.md)
- [iOS](custom-settings-ios.md)
- [macOS](custom-settings-macos.md)
- [Windows 10](custom-settings-windows-10.md)
- [Windows Holographic for Business](custom-settings-windows-holographic.md)
- [Windows Phone 8.1](custom-settings-windows-phone-8-1.md)
