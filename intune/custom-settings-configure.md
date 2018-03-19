---
title: "在 Microsoft Intune 中使用自定义设备设置 - Azure | Microsoft Docs"
description: "添加或创建配置文件，以便使用 Microsoft Intune 为 Windows、Android 和 iOS 设备使用自定义设置"
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: adecb332c91f17cf92362295b6b0c81445f5acaf
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2018
---
# <a name="create-a-profile-with-custom-settings-in-intune"></a>使用 Intune 中的自定义设置创建配置文件

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune 可能不含所需的所有内置设置。 或者你可能想要使用其他设备配置文件中的可用设置。 要添加这些设置，请创建设备配置文件，然后使用自定义设备设置来配置配置文件。

本文列出了使用自定义设置创建配置文件的基本步骤。 它还包括一些链接，可以深入了解如何创建不同平台上的自定义设置。

## <a name="custom-settings-on-different-platforms"></a>不同平台上的自定义设置
每个平台的自定义设置配置都不相同。 例如，要控制 Android 和 Windows 设备上的功能，可输入开放移动联盟统一资源标识符 (OMA-URI) 值。 对于 Apple 设备，则可以导入使用 [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) 创建的文件。

## <a name="create-the-profile"></a>创建配置文件

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 依次选择“设备配置”、“配置文件”和“创建配置文件”。
4. 输入自定义配置文件的“名称”和“描述”。
5. 从“平台”下拉列表中，选择要应用自定义设置的设备平台。 可选择以下任何平台：

    - **Outlook Web Access (OWA)**
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 及更高版本**
    - **Windows 10 及更高版本**

6. 从“配置文件”类型下拉列表中，选择“自定义”。
7. 根据所选择的平台，可配置的设置有所不同。 以下链接提供了有关每个平台的自定义设置的更多详细信息：

    - [Android 设置](custom-settings-android.md)
    - [iOS 设置](custom-settings-ios.md)
    - [macOS 设置](custom-settings-macos.md)
    - [Windows Phone 8.1 设置](custom-settings-windows-phone-8-1.md)
    - [Windows 10 设置](custom-settings-windows-10.md)
    - [Windows Holographic for Business 设置](custom-settings-windows-holographic.md)
    - [Android for Work 设置](custom-settings-android-for-work.md)

8. 完成后，选择“创建”。

配置文件随即创建并显示在配置文件列表中。 要向组分配此配置文件，请参阅[如何分配设备配置文件](device-profile-assign.md)。
