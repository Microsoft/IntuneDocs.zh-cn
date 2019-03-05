---
title: 在 Microsoft Intune 中配置设备限制设置 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中向 Android、macOS、iOS、Windows Phone 和 Windows 10 上的限制功能添加设备配置文件
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/20/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 460b9b89f6bec42bf7ad0c1abadfc0625295a5a8
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/02/2019
ms.locfileid: "57236121"
---
# <a name="configure-device-restriction-settings-in-microsoft-intune"></a>在 Microsoft Intune 中配置设备限制设置

通过设备限制可以跨众多类别控制所管理的各种设置和功能，例如：
- 安全
- 浏览器
- 硬件
- 数据共享设置

例如，可以创建一个设备限制配置文件，用于阻止 iOS 设备用户访问设备相机。

了解设备限制配置文件基础知识，然后阅读针对每个平台的深入文章以了解设备规范。

## <a name="create-the-profile"></a>创建配置文件

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”，筛选“Intune”，然后选择“Intune”。
2. 选择“设备配置” > “配置文件” > “创建配置文件”。
3. 输入设备限制配置文件的“名称”和“描述”。
4. 从“平台”下拉列表中，选择要应用自定义设置的设备平台。 目前，可以为设备限制设置选择以下平台之一：

    - **Outlook Web Access (OWA)**
    - **Android 企业**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 及更高版本**
    - **Windows 10 及更高版本**

5. 在“配置文件类型”下拉列表中，选择“设备限制”。 若要为 Windows 10 协同版设备（如 Surface Hub）创建设备限制配置文件，请选择“设备限制(Windows 10 协同版)”。
6. 根据所选择的平台，可配置的设置有所不同。 选择平台，以了解详细设置：

    - [Android 设置](device-restrictions-android.md)
    - [Android Enterprise 设置](device-restrictions-android-for-work.md)
    - [iOS 设置](device-restrictions-ios.md)
    - [macOS 设置](device-restrictions-macos.md)
    - [Windows Phone 8.1 设置](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Windows 10 设置](device-restrictions-windows-10.md)
    - [Windows 10 协同版设置](device-restrictions-windows-10-teams.md)
    - [Windows Holographic for Business 设置](device-restrictions-windows-holographic.md)

7. 完成后，选择“确定” > “创建”以保存所做的更改。

此时，配置文件创建完成，并出现在配置文件列表中。

## <a name="next-steps"></a>后续步骤

创建配置文件后，即可进行分配。 下一步，[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
