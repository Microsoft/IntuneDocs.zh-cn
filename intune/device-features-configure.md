---
title: 使用 Microsoft Intune 创建 iOS 或 macOS 设备配置文件 - Azure | Microsoft Docs
description: 添加或创建 iOS 或 macOS 设备配置文件，再配置 Microsoft Intune 中用于为设备配置 AirPrint、主屏幕布局、应用通知、共享设备、单一登录和 Web 内容筛选器的设置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8483e036e270744daa5e36bf9375da6e11c25746
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2019
ms.locfileid: "66048305"
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>在 Intune 中添加 iOS 或 macOS 设备功能设置

Intune 包含许多有助于管理员控制 iOS 和 macOS 设备的功能和设置。 例如，管理员可以：

- 允许用户有权在网络中访问 AirPrint 打印机
- 将应用和文件夹添加到主屏幕，包括添加新页面
- 选择是否以及如何显示应用通知
- 将锁定屏幕配置为显示消息或资产标记，特别是对于共享设备
- 为用户提供安全的单一登录体验，以在应用间共用凭据
- 筛选使用成人语言的网站，并允许或屏蔽特定网站

这些功能在 Intune 中可用，并可供管理员进行配置。 Intune 使用“配置文件”创建和自定义这些设置，从而满足组织需求。 在配置文件中添加这些功能后，便能将此配置文件推送或部署到组织中的 iOS 和 macOS 设备。

本文介绍了如何创建设备配置文件。 还可以查看所有适用于 [iOS](ios-device-features-settings.md) 和 [macOS](macos-device-features-settings.md) 设备的设置。

## <a name="create-a-device-profile"></a>创建设备配置文件

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”> 筛选“Intune”> 选择“Intune”。
2. 选择“设备配置” > “配置文件” > “创建配置文件”。
3. 输入以下属性：

    - **名称**：输入新配置文件的描述性名称。
    - **说明**：输入配置文件的说明。 此设置是可选的，但建议进行。
    - **平台**：选择平台：
        - **iOS**
        - **macOS**
    - **配置文件类型**：选择“设备功能”。
    - **设置**：输入要配置的设置。 有关所有设置及其用途的列表，请参阅：

        - [iOS](ios-device-features-settings.md)
        - [macOS](macos-device-features-settings.md)

4. 完成后，依次选择“确定”、“创建”以保存所做更改。

此时，配置文件创建完成，并出现在列表中。 请务必[分配配置文件](device-profile-assign.md)，并[监视配置文件状态](device-profile-monitor.md)。

## <a name="next-steps"></a>后续步骤

创建配置文件后，即可进行分配。 下一步，[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

查看所有适用于 [iOS](ios-device-features-settings.md) 和 [macOS](macos-device-features-settings.md) 设备的设备功能设置。
