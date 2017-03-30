---
title: "如何配置 Intune Wi-Fi 设置"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解如何使用 Intune 来配置你管理的设备上的 Wi-Fi 连接。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1fadb488-9c6c-43c1-ba23-8c69db633b96
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: ca4f1adc5704ecd66d2af7823f95ca63ec20469e
ms.openlocfilehash: 34b906301fca2e91f2c014b9959c305a39f46af1
ms.lasthandoff: 03/17/2017


---

# <a name="how-to-configure-wi-fi-settings-in-microsoft-intune"></a>如何在 Microsoft Intune 中配置 Wi-Fi 设置

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

使用 Microsoft Intune Wi-Fi 配置文件将无线网络设置部署到组织中的用户和设备。 部署 Wi-Fi 配置文件后，你的用户将有权访问你公司的 Wi-Fi 网络，而无需自行配置。

例如，安装名为 Contoso Wi-Fi 的新 Wi-Fi 网络，并且想要将所有 iOS 设备设置为连接到此网络。 过程如下：

1. 创建包含连接到 Contoso Wi-Fi 无线网络所必需的设置的 Wi-Fi 配置文件。
2. 将该配置文件分配到包含所有 iOS 设备用户的组。
3. 用户在其设备上的无线网络列表中找到新的 Contoso Wi-Fi 网络，然后即可轻松连接到它。

Wi-Fi 配置文件支持以下设备平台：

- Android 4 及更高版本
- iOS 8.0 及更高版本
- macOS（Mac OS X 10.9 及更高版本）

对于运行 Windows 8.1、Windows 10 和 Windows 10 移动版的设备，你可以导入之前从另一台设备导出的 Wi-Fi 配置。

使用本主题中的信息了解有关配置 Wi-Fi 配置文件的基础知识，然后深入阅读有关每个平台的主题以了解设备详情。

## <a name="create-a-device-profile-containing-wi-fi-settings"></a>创建包含 Wi-Fi 设置的设备配置文件

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “其他” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“设备配置”。
2. 在“设备配置”边栏选项卡上，选择“管理” > “配置文件”。
3. 在配置文件边栏选项卡上，选择“创建配置文件”。
4. 在“创建配置文件”边栏选项卡上，输入 Wi-Fi 配置文件的“名称”和“说明”。
5. 从“平台”下拉列表中，选择要应用 Wi-Fi 设置的设备平台。 目前，可以为 Wi-Fi 设置选择以下平台之一：
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows 8.1 及更高版本（导入配置文件）**
6. 从“配置文件类型”下拉列表中，选择“Wi-Fi 基本”或“Wi-Fi 企业”。
    >[!TIP]
    >使用“Wi-fi 基本”可提供基本功能，如网络名称和 SSID。 “Wi-Fi 企业”允许你提供更高级的信息，如可扩展身份验证协议 (EAP)（如果你的 Wi-Fi 网络使用此协议）。 “Wi-Fi 导入”（适用于 Windows 8.1 和 Windows 10）允许你以之前从其他设备导出的 XML 文件形式导入 Wi-Fi 设置。
7. 根据所选择的平台，可配置的设置将有所不同。 有关每个平台的详细设置，请转到以下主题之一：
    - [Android 设置](wi-fi-for-android.md)
    - [iOS 设置](wi-fi-for-ios.md)
    - [macOS 设置](wi-fi-for-macos.md)
    - [Windows Phone 8.1 设置](wi-fi-import-for-windows-8-1.md)
8. 完成后，返回“创建配置文件”边栏选项卡，然后点击“创建”。

将创建配置文件并在“配置文件列表”边栏选项卡上显示。
如果想要继续操作并将此配置文件分配到组，请参阅[如何分配设备配置文件](how-to-assign-device-profiles.md)。


