---
title: 在 Microsoft Intune 中使用策略限制设备功能 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中添加设备配置文件以限制 Android、macOS、iOS、iPadOS、Windows Phone 和 Windows 10 设备上的功能
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cfa640d5858479b5f98009e92f005312966f536a
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "73755279"
---
# <a name="configure-device-restriction-settings-in-microsoft-intune"></a>在 Microsoft Intune 中配置设备限制设置

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune 包含帮助管理员控制 Android、iOS、macOS 和 Windows 设备的设备限制策略。 这些限制允许控制各种设置和功能，以保护组织的资源。 例如，管理员可以：

- 允许或阻止设备照相机
- 控制对 Google Play、应用商店、查看文档和游戏的访问
- 阻止内置应用，或创建允许或禁止的应用列表
- 允许或阻止将文件备份到云和存储帐户
- 设置最小密码长度和阻止简单密码

这些功能在 Intune 中可用，并可供管理员进行配置。 Intune 使用“配置文件”创建和自定义这些设置，从而满足组织需求。 在配置文件中添加这些功能后，就可以将配置文件推送或部署到组织中的设备上。

本文介绍了如何创建设备限制配置文件。 还可以查看所有适用于不同平台的可用设置。

## <a name="create-the-profile"></a>创建配置文件

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“设备”   > “配置文件”   > “创建配置文件”  。
3. 输入以下属性：

    - **名称**：输入策略的描述性名称。 为策略命名，以便稍后可以轻松地识别它们。 例如，策略名称最好是“iOS：阻止设备上的照相机”  。
    - **说明**：输入策略的说明。 此设置是可选的，但建议进行。
    - **平台**：选择设备平台。 选项包括：  

        - **Android
**
        - **Android 企业**
        - **iOS/iPadOS**
        - **macOS**
        - **Windows Phone 8.1**
        - **Windows 8.1 及更高版本**
        - **Windows 10 及更高版本**

    - **配置文件类型**：选择“设备限制”  。

        若要为 Windows 10 协同版设备（如 Surface Hub）创建设备限制配置文件，请选择“设备限制(Windows 10 协同版)”  。

4. 根据所选择的平台，可配置的设置有所不同。 选择平台，以了解详细设置：

    - [Android 设置](../device-restrictions-android.md)
    - [Android Enterprise 设置](../device-restrictions-android-for-work.md)
    - [iOS/iPadOS 设置](device-restrictions-ios.md)
    - [macOS 设置](device-restrictions-macos.md)
    - [Windows Phone 8.1 设置](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Windows 10 设置](device-restrictions-windows-10.md)
    - [Windows 10 协同版设置](device-restrictions-windows-10-teams.md)
    - [Windows Holographic for Business 设置](device-restrictions-windows-holographic.md)

5. 完成后，选择“确定”   > “创建”  以保存所做的更改。

此时，配置文件创建完成，并出现在配置文件列表中。

## <a name="next-steps"></a>后续步骤

创建配置文件后，即可进行分配。 下一步，[分配配置文件](../device-profile-assign.md)并[监视其状态](../device-profile-monitor.md)。

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/device-restrictions-configure/disable-android-camera.png)

-->
