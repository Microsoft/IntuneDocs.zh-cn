---
title: 在 Microsoft Intune 中配置设备限制设置 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中向 Android、macOS、iOS、Windows Phone 和 Windows 10 上的限制功能添加设备配置文件
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 13f93f9fcf813c2e86809d2cc20991d2fd635187
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
ms.locfileid: "31024611"
---
# <a name="configure-device-restriction-settings-in-microsoft-intune"></a>在 Microsoft Intune 中配置设备限制设置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

通过设备限制可以跨众多类别控制所管理的各种设置和功能，例如：
- 安全
- 浏览器
- 硬件
- 数据共享设置

例如，可以创建一个设备限制配置文件，用于阻止 iOS 设备用户访问设备相机。

了解设备限制配置文件基础知识，然后阅读针对每个平台的深入文章以了解设备规范。

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>创建包含设备限制设置的设备配置文件

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 选择“设备配置” > “配置文件” > “创建配置文件”。
4. 输入设备限制配置文件的“名称”和“描述”。
5. 从“平台”下拉列表中，选择要应用自定义设置的设备平台。 目前，可以为设备限制设置选择以下平台之一：
    - **Outlook Web Access (OWA)**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 及更高版本**
    - **Windows 10 及更高版本**
6. 在“配置文件类型”下拉列表中，选择“设备限制”。 如果想要为 Windows 10 协同版设备（如 Surface Hub）创建设备限制配置文件，请选择“设备限制( Windows 10 协同版)”。
7. 根据所选择的平台，可配置的设置有所不同。 有关每个平台的详细设置，请转到以下主题之一：
    - [Android 设置](device-restrictions-android.md)
    - [iOS 设置](device-restrictions-ios.md)
    - [macOS 设置](device-restrictions-macos.md)
    - [Windows Phone 8.1 设置](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Windows 10 设置](device-restrictions-windows-10.md)
    - [Windows 10 协同版设置](device-restrictions-windows-10-teams.md)
    - [Windows Holographic for Business 设置](device-restrictions-windows-holographic.md)
    - [Android for Work 设置](device-restrictions-android-for-work.md)
8. 完成后，返回“创建配置文件”页，然后单击“创建”。

配置文件随即创建并显示在“配置文件列表”页中。
如果想要继续操作并将此配置文件分配到组，请参阅[如何分配设备配置文件](device-profile-assign.md)。

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
