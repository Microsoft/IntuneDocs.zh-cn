---
title: "配置 Intune 设备限制设置"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解如何使用 Intune 来配置你管理的设备上的设置和功能。"
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
ms.openlocfilehash: 600ff92bf1b53800712fc2e77fef7158ab765970
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-configure-device-restriction-settings-in-microsoft-intune"></a>如何在 Microsoft Intune 中配置设备限制设置

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

设备限制让你可以跨众多类别控制你所管理的各种设置和功能，包括安全性、浏览器、硬件和数据共享设置。 例如，可以创建一个设备限制配置文件，用于阻止 iOS 设备用户访问设备相机。

使用本主题中的信息了解有关配置设备限制配置文件的基础知识，然后深入阅读每个平台的主题以了解设备详情。

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>创建包含设备限制设置的设备配置文件

1. 登录到 Azure 门户中。
2. 依次选择“更多服务” > “其他” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“配置设备”。
2. 在“设备配置”边栏选项卡上，选择“管理” > “配置文件”。
3. 在配置文件边栏选项卡上，选择“创建配置文件”。
4. 在“创建配置文件”边栏选项卡上，输入设备限制配置文件的“名称”和“说明”。
5. 从“平台”下拉列表中，选择要应用自定义设置的设备平台。 目前，可以为设备限制设置选择以下平台之一：
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 及更高版本**
    - **Windows 10 及更高版本**
6. 在“配置文件类型”类型下拉列表中，选择“设备限制”。 如果想要为 Windows 10 协同版设备（如 Surface Hub）创建设备限制配置文件，请选择“设备限制( Windows 10 协同版)”。
7. 根据所选择的平台，可配置的设置将有所不同。 有关每个平台的详细设置，请转到以下主题之一：
    - [Android 设置](device-restrictions-android.md)
    - [iOS 设置](device-restrictions-ios.md)
    - [macOS 设置](device-restrictions-macos.md)
    - [Windows Phone 8.1 设置](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Windows 10 设置](device-restrictions-windows-10.md)
    - [Windows 10 协同版设置](device-restrictions-windows-10-teams.md)
    - [Android for Work 设置](device-restrictions-android-for-work.md)
8. 完成后，返回“创建配置文件”边栏选项卡，然后点击“创建”。

将创建配置文件并在“配置文件列表”边栏选项卡上显示。
如果想要继续操作并将此配置文件分配到组，请参阅[如何分配设备配置文件](device-profile-assign.md)。

## <a name="example-of-device-restriction-settings"></a>设备限制设置示例

在此高级示例中，将创建设备限制政策，阻止在 Android 设备上使用内置相机应用。

![如何在 Android 设备上禁用相机](./media/disable-android-camera.png)


