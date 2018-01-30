---
title: "如何配置 Intune 自定义设备设置"
titleSuffix: Azure portal
description: "了解如何使用 Intune 配置你所管理设备上的自定义设置。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6e3821f40cdf1c36f020bf807eed5c6fbd83a9aa
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-configure-custom-device-settings-in-microsoft-intune"></a>如何在 Microsoft Intune 中配置自定义设备设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="when-to-use-custom-settings"></a>何时使用自定义设置

当 Intune 没有你想要配置的内置设置时，自定义设备设置会非常有用，并且可从其他设备配置文件获得这些设置。
每个平台的自定义设置配置都不相同。 例如，对于 Android 和 Windows 设备，可以指定开放移动联盟统一资源标识符 (OMA-URI) 值来控制设备功能。 对于 Apple 设备，则可以导入使用 [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) 创建的文件。

使用本主题中的信息了解有关配置自定义设置配置文件的基础知识，然后深入阅读每个平台的主题以了解设备详情。

## <a name="create-a-device-profile-containing-custom-settings"></a>创建包含自定义设置的设备配置文件

1. 登录 Azure 门户。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“设备配置”。
2. 在“设备配置”边栏选项卡上，依次选择“管理” > “配置文件”。
3. 在配置文件边栏选项卡上，选择“创建配置文件”。
4. 在“创建配置文件”边栏选项卡上，输入自定义配置文件的“名称”和“说明”。
5. 从“平台”下拉列表中，选择要应用自定义设置的设备平台。 目前，可以为自定义设备设置选择以下平台之一：
    - **Outlook Web Access (OWA)**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 10 及更高版本**
6. 从“配置文件”类型下拉列表中，选择“自定义”。
7. 根据所选择的平台，可配置的设置将有所不同。 有关每个平台的详细设置，请转到以下主题之一：
    - [Android 设置](custom-settings-android.md)
    - [iOS 设置](custom-settings-ios.md)
    - [macOS 设置](custom-settings-macos.md)
    - [Windows Phone 8.1 设置](custom-settings-windows-phone-8-1.md)
    - [Windows 10 设置](custom-settings-windows-10.md)
    - [Android for Work 设置](custom-settings-android-for-work.md)
8. 完成后，返回“创建配置文件”边栏选项卡，然后点击“创建”。

此时，配置文件会进行创建，并显示在配置文件列表边栏选项卡上。
如果想要继续操作并将此配置文件分配到组，请参阅[如何分配设备配置文件](device-profile-assign.md)。
