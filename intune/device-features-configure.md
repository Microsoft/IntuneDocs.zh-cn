---
title: "配置 Microsoft Intune 设备功能设置"
titleSuffix: 
description: "了解如何使用 Microsoft Intune 来配置所管理的设备上的功能。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6cd646976deb1599c4cbc9154b6f2a487029dd79
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2018
---
#<a name="configure-device-feature-settings-in-microsoft-intune"></a>在 Microsoft Intune 中配置设备功能设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

借助设备功能，你能够在 iOS 和 macOS 设备上控制 AirPrint、通知，和共享设备配置等功能。

使用本文中的信息了解有关配置设备功能配置文件的基础知识，然后阅读针对每个平台的其他文章以了解设备规范。

## <a name="create-a-device-profile-containing-device-feature-settings"></a>创建包含设备功能设置的设备配置文件

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分。
3. 在“Intune”页，选择“设备配置”。
2. 在“管理”部分下的“设备配置”页上，选择“配置文件”。
3. 在“配置文件”页，选择“创建配置文件”。
4. 在“创建配置文件”页，输入设备功能配置文件的“名称”和“说明”。
5. 从“平台”下拉列表中，选择要应用设置的设备平台。 目前，可以为设备功能选择以下平台之一：
    - **iOS**
    - **macOS**
6. 在“配置文件类型”下拉列表中，选择“设备功能”。 
7. 根据所选择的平台，可配置的设置有所不同。 有关每个平台的详细设置，请转到以下文章之一：
    - [适用于 iOS 和 MacOS 的 AirPrint 设置](air-print-settings-ios-macos.md)
    - [适用于 iOS 的 AirPlay 设置](airplay-settings-ios.md)
    - [适用于 iOS 的主屏幕布局设置](home-screen-settings-ios.md)
    - [适用于 iOS 的应用通知设置](app-notification-settings-ios.md)
    - [适用于 iOS 的共享设备配置设置](shared-device-settings-ios.md)
    - [配置 Intune for iOS 设备 SSO](sso-ios.md)
    - [适用于 iOS 的 Web 内容筛选器设置](web-content-filter-settings-ios.md)

8. 完成后，选择“确定”，返回“创建配置文件”页，然后选择“创建”。

配置文件随即创建并显示在“配置文件列表”页中。
## <a name="next-steps"></a>后续步骤

如果希望将此配置文件分配到组，请参阅[如何分配设备配置文件](device-profile-assign.md)。



