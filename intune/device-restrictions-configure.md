---
title: "配置 Intune 设备限制设置"
titleSuffix: Azure portal
description: "了解如何使用 Intune 配置你管理的设备上的设置和功能。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4cd21d6e87dfa142fe9e3ef4d9bbbc0be87eca9b
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-configure-device-restriction-settings-in-microsoft-intune"></a>如何在 Microsoft Intune 中配置设备限制设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

设备限制让你可以跨众多类别控制你所管理的各种设置和功能，包括安全性、浏览器、硬件和数据共享设置。 例如，可以创建一个设备限制配置文件，用于阻止 iOS 设备用户访问设备相机。

使用本主题中的信息了解有关配置设备限制配置文件的基础知识，然后深入阅读每个平台的主题以了解设备详情。

创建包含设备限制设置的设备配置文件：

1. 登录 Azure 门户。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“配置设备”。
2. 在“设备配置”边栏选项卡上，依次选择“管理” > “配置文件”。
3. 在配置文件边栏选项卡上，选择“创建配置文件”。
4. 在“创建配置文件”边栏选项卡上，输入设备限制配置文件的“名称”和“说明”。
5. 从“平台”下拉列表中，选择要应用自定义设置的设备平台。 目前，可以为设备限制设置选择以下平台之一：
    - **Outlook Web Access (OWA)**
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

此时，配置文件会进行创建，并显示在配置文件列表边栏选项卡上。
如果想要继续操作并将此配置文件分配到组，请参阅[如何分配设备配置文件](device-profile-assign.md)。

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->