---
title: 如何配置 Intune Wi-Fi 设置
titleSuffix: Microsoft Intune
description: 了解如何使用 Microsoft Intune 来配置所管理设备上的 Wi-Fi 连接。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e2dba6e0d1c50790c8c2c2bf287695ab67fdb972
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905319"
---
# <a name="how-to-configure-wi-fi-settings-in-microsoft-intune"></a>如何在 Microsoft Intune 中配置 Wi-Fi 设置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

使用 Microsoft Intune Wi-Fi 配置文件将无线网络设置分配到组织中的用户和设备。 分配 Wi-Fi 配置文件后，你的用户将有权访问你公司的 Wi-Fi 网络，而无需自行配置。

例如，安装名为 Contoso Wi-Fi 的新 Wi-Fi 网络，并且想要将所有 iOS 设备设置为连接到此网络。 过程如下：

1. 创建包含连接到 Contoso Wi-Fi 无线网络所必需的设置的 Wi-Fi 配置文件。
2. 将该配置文件分配到包含所有 iOS 设备用户的组。
3. 用户在其设备上的无线网络列表中找到新的 Contoso Wi-Fi 网络，然后即可轻松连接到它。

## <a name="supported-device-platforms"></a>支持的设备平台

Wi-Fi 配置文件支持以下设备平台：

- Android 4 及更高版本
- Android 工作配置文件
- iOS 8.0 及更高版本
- macOS（Mac OS X 10.11 及更高版本）

对于运行 Windows 8.1、Windows 10、Windows 10 移动版和 Windows Holographic for Business 的设备，可以导入之前从另一台设备导出的 Wi-Fi 配置。

使用本主题中的信息了解有关配置 Wi-Fi 配置文件的基础知识，然后深入阅读有关每个平台的主题以了解设备详情。

## <a name="create-a-device-profile-containing-wi-fi-settings"></a>创建包含 Wi-Fi 设置的设备配置文件

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 在“Intune”窗格上，选择“设备配置”。
2. 在“管理”部分的“设备配置”窗格上，选择“配置文件”。
3. 在“配置文件”窗格上，选择“创建配置文件”。
4. 在“创建配置文件”窗格上，输入 Wi-Fi 配置文件的“名称”和“说明”。
5. 从“平台”下拉列表中，选择要应用 Wi-Fi 设置的设备平台。 目前，可以为 Wi-Fi 设置选择以下平台之一：
    - **Outlook Web Access (OWA)**
    - **Android 企业**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 及更高版本**
    - **Windows 10 及更高版本**

   > [!IMPORTANT]
   > 如果要为运行 Windows 10（包括 Windows Holographic for Business）的设备创建配置文件，必须选择“Windows 8.1 及更高版本”平台。 “Windows 10 及更高版本”平台不包含 Wi-Fi 配置文件类型。 

6. 对于 Apple 或 Android 设备，请在“WiFi 类型”下拉列表中，选择“基本”或“企业”。 可使用“基本”来提供基本功能，如网络名称和 SSID。 “企业”允许提供更高级的信息，如可扩展身份验证协议 (EAP)（如果 Wi-Fi 网络使用此协议）。 

   “Wi-Fi 导入”（适用于 Windows 8.1 及更高版本）允许以之前从其他设备导出的 XML 文件形式导入 Wi-Fi 设置。
1. 根据所选择的平台，可配置的设置有所不同。 有关每个平台的详细设置，请转到以下主题之一：
    - [Android 和 Android 工作配置文件设置](wi-fi-settings-android.md)
    - [iOS 设置](wi-fi-settings-ios.md)
    - [macOS 设置](wi-fi-settings-macos.md)
    - [Windows 8.1 及更高版本设置](wi-fi-settings-import-windows-8-1.md)（包括 Windows Holographic for Business）
1. 完成后，返回“创建配置文件”窗格，然后点击“创建”。

配置文件随即创建并显示在“配置文件列表”窗格中。

## <a name="next-steps"></a>后续步骤

如果想要继续操作并将此配置文件分配到组，请参阅[如何分配设备配置文件](device-profile-assign.md)。
