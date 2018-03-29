---
title: 使用 Microsoft Intune 创建 iOS 或 macOS 设备配置文件 - Azure | Microsoft Docs
description: 添加或创建 iOS 或 macOS 设备配置文件，然后在 Microsoft Intune 中配置 AirPrint、AirPlay、主屏幕布局、应用通知、共享设备、单一登录的设置以及 Web 内容筛选器设置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 291ad9cb8b07893f538171c365110618ea376388
ms.sourcegitcommit: e6319ff186d969da34bd19c9730ba003d6cce353
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/20/2018
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>在 Intune 中添加 iOS 或 macOS 设备功能设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用设备功能，可以控制 iOS 和 macOS 设备上的一系列设置和功能，例如：

- AirPrint 和 AirPlay 设置
- 主屏幕布局
- 应用的通知
- 共享设备配置
- 设置单一登录
- 筛选 Web 内容

本文介绍有关配置 iOS 设备功能配置文件的基础知识。 然后，你可以逐步浏览其他文章，以为设备配置平台特定的设置。

## <a name="create-a-device-profile"></a>创建设备配置文件

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 选择“设备配置” > “配置文件” > “创建配置文件”。
4. 输入以下属性：

   - **名称**：输入新配置文件的描述性名称。
   - **说明**：输入配置文件的说明。 （这是可选的，但建议使用它。）
   - **平台**：选择平台类型：
     - **iOS**
     - **macOS**
   - **配置文件类型**：选择“设备功能”。
   - **设置**：设置取决于你选择的平台。 以下文章介绍了每种配置文件类型的设置：

     - [适用于 iOS 和 MacOS 的 AirPrint 设置](air-print-settings-ios-macos.md)
     - [适用于 iOS 的 AirPlay 设置](airplay-settings-ios.md)
     - [适用于 iOS 的主屏幕布局设置](home-screen-settings-ios.md)
     - [适用于 iOS 的应用通知设置](app-notification-settings-ios.md)
     - [适用于 iOS 的共享设备配置设置](shared-device-settings-ios.md)
     - [配置 Intune for iOS 设备 SSO](sso-ios.md)
     - [适用于 iOS 的 Web 内容筛选器设置](web-content-filter-settings-ios.md)

5. 完成后，依次选择“确定”、“创建”以保存所做更改。

配置文件随即创建并显示在列表中。

## <a name="next-step"></a>下一步

要向组分配此配置文件，请参阅[如何分配设备配置文件](device-profile-assign.md)。