---
title: "配置 Intune 设备功能设置"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解如何使用 Intune 来配置你管理的设备上的功能。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: f584d76a498264f8ab1cf883f5ee95d52d3446d3
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-configure-device-feature-settings-in-microsoft-intune"></a>如何在 Microsoft Intune 中配置设备功能设置

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

设备限制使你能够在 iOS 和 macOS 设备上控制 AirPrint、通知，和共享设备配置等功能。

使用本主题中的信息了解有关配置设备功能配置文件的基础知识，然后深入阅读每个平台的主题以了解设备详情。

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>创建包含设备限制设置的设备配置文件

1. 登录到 Azure 门户中。
2. 依次选择“更多服务” > “其他” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“设备配置”。
2. 在“设备配置”边栏选项卡上，依次选择“管理” > “配置文件”。
3. 在配置文件边栏选项卡上，选择“创建配置文件”。
4. 在“创建配置文件”边栏选项卡上，输入设备功能配置文件的“名称”和“说明”。
5. 从“平台”下拉列表中，选择要应用设置的设备平台。 目前，可以为设备功能选择以下平台之一：
    - **iOS**
    - **macOS**
6. 在“配置文件类型”类型下拉列表中，选择“设备功能”。 
7. 根据所选择的平台，可配置的设置将有所不同。 有关每个平台的详细设置，请转到以下主题之一：
    - [适用于 iOS 和 MacOS 的 AirPrint 设置](air-print-settings-ios-macos.md)
     - [适用于 iOS 的 AirPlay 设置](airplay-settings-ios.md)
    - [适用于 iOS 的主屏幕布局设置](home-screen-settings-ios.md)
    - [适用于 iOS 的应用通知设置](app-notification-settings-ios.md)
    - [适用于 iOS 的共享设备配置设置](shared-device-settings-ios.md)

8. 完成后，返回“创建配置文件”边栏选项卡，然后点击“创建”。

将创建配置文件并在“配置文件列表”边栏选项卡上显示。
如果想要继续操作并将此配置文件分配到组，请参阅[如何分配设备配置文件](device-profile-assign.md)。




