---
title: "配置 Intune 设备功能设置"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解如何使用 Intune 在管理的设备上配置功能。"
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
ms.sourcegitcommit: c8715f96f532ee6bacda231e1147d03226ecbb48
ms.openlocfilehash: fddd4963ceea09b37ad4d8c739f437dbcf3b053e
ms.contentlocale: zh-cn
ms.lasthandoff: 04/26/2017


---

# <a name="how-to-configure-device-feature-settings-in-microsoft-intune"></a>如何在 Microsoft Intune 中配置设备功能设置

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

通过设备限制，可以控制 iOS 和 macOS 设备上的功能，如 AirPrint、通知和共享设备配置。

请参阅本主题，了解有关如何配置设备功能配置文件的基础知识，然后进一步阅读每个平台的主题，了解各个设备平台的具体设置。

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>创建包含设备限制设置的设备配置文件

1. 登录 Azure 门户。
2. 依次选择“更多服务” > “其他” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“设备配置”。
2. 在“设备配置”边栏选项卡上，依次选择“管理” > “配置文件”。
3. 在“配置文件”边栏选项卡上，选择“创建配置文件”。
4. 在“创建配置文件”边栏选项卡上，输入设备功能配置文件的“名称”和“说明”。
5. 在“平台”下拉列表中，选择要向其应用设置的设备平台。 目前，可以选择向下列平台之一应用设备功能设置：
    - **Android**
    - **macOS**
6. 在“配置文件类型”下拉列表中，选择“设备功能”。 
7. 可配置的设置因所选平台而异。 若要详细了解每个平台的具体设置，请参阅下列主题之一：
    - [适用于 iOS 和 MacOS 的 AirPrint 设置](air-print-settings-for-ios-and-macos.md)
     - [适用于 iOS 的 AirPlay 设置](airplay-settings-for-ios-devices.md)
    - [适用于 iOS 的主屏幕布局设置](home-screen-settings-for-ios.md)
    - [适用于 iOS 的应用通知设置](app-notification-settings-for-ios.md)
    - [适用于 iOS 的共享设备配置设置](shared-device-settings-for-ios.md)

8. 完成后，返回“创建配置文件”边栏选项卡，然后点击“创建”。

此时，配置文件会进行创建，并显示在配置文件列表边栏选项卡上。
若要将此配置文件分配给组，请参阅[如何分配设备配置文件](how-to-assign-device-profiles.md)。




