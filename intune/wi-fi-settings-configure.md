---
title: 在 Microsoft Intune 中为设备创建 Wi-Fi 配置文件 - Azure | Microsoft Docs
description: 请参阅具体步骤以在 Microsoft Intune 中创建 Wi-Fi 设备配置文件。 创建适用于 Android、Android Enterprise、Android 展台、iOS、macOS、Windows 10 及更高版本以及 Windows Holographic for Business 的配置文件。 使用这些配置文件创建 WiFi 连接以使用证书、选择 EAP 类型、选择身份验证方法和启用代理等。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 16273910220dae238e15910af0557dd8b73646b9
ms.sourcegitcommit: cff65435df070940da390609d6376af6ccdf0140
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2018
ms.locfileid: "49425251"
---
# <a name="add-and-use-wi-fi-settings-on-your-devices-in-microsoft-intune"></a>在 Microsoft Intune 中添加和使用设备上的 Wi-Fi 设置

使用 Microsoft Intune Wi-Fi 配置文件将无线网络设置分配到组织中的用户和设备。 分配 Wi-Fi 配置文件后，你的用户将有权访问贵公司的 Wi-Fi 网络，而无需自行配置。

例如，安装名为“Contoso Wi-Fi”的新 Wi-Fi 网络。 然后你要将所有 iOS 设备设置为连接到此网络。 过程如下：

1. 创建包含连接到 Contoso Wi-Fi 无线网络所需的设置的 Wi-Fi 配置文件。
2. 将该配置文件分配到包含所有 iOS 设备用户的组。
3. 用户在其设备上的无线网络列表中找到新的 Contoso Wi-Fi 网络。 然后，他们可以使用所选的身份验证方法连接到该网络。

使用本文中的步骤创建 Wi-Fi 配置文件。 然后，查看有关平台特定设置和详细信息的主题。

## <a name="supported-device-platforms"></a>支持的设备平台

Wi-Fi 配置文件支持以下设备平台：

- Android 4 及更高版本
- Android Enterprise 和展台
- iOS 8.0 及更高版本
- macOS（Mac OS X 10.11 及更高版本）
- Windows 10 及更高版本、Windows 10 移动版和 Windows Holographic for Business

> [!NOTE]
> 对于运行 Windows 8.1 的设备，你可以导入之前从另一台设备导出的 Wi-Fi 配置。

## <a name="create-a-wi-fi-device-profile"></a>创建 Wi-Fi 设备配置文件

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。 
2. 选择“设备配置” > “配置文件” > “创建配置文件”。
3. 为 Wi-Fi 配置文件输入“名称”和“说明”。
4. 从“平台”下拉列表中，选择要应用 Wi-Fi 设置的设备平台。 选项包括：

    - **Outlook Web Access (OWA)**
    - **Android 企业**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 及更高版本**
    - **Windows 10 及更高版本**

5. 在“配置文件类型”中，选择“Wi-Fi”。

    - 对于作为展台运行的 Android Enterprise 设备，可以选择“仅设备所有者” > “Wi-Fi”。
    - 对于 Windows 8.1 及更高版本，可以选择“Wi-Fi 导入”。 此选项允许你以之前从其他设备导出的 XML 文件形式导入 Wi-Fi 设置。

6. 某些 Wi-Fi 设置针对每个平台会有所不同。 若要查看特定平台的设置，可选择：

    - [Outlook Web Access (OWA)](wi-fi-settings-android.md)
    - [Android Enterprise 和展台](wi-fi-settings-android-enterprise.md)
    - [iOS](wi-fi-settings-ios.md)
    - [macOS](wi-fi-settings-macos.md)
    - [Windows 10 及更高版本](wi-fi-settings-windows.md)
    - [Windows 8.1 及更高版本](wi-fi-settings-import-windows-8-1.md)，包括 Windows Holographic for Business

    大多数平台都具有“基本”和“企业”设置。 “基本”包括功能，如网络名称和 SSID。 “企业”可提供更高级的信息，如可扩展身份验证协议 (EAP)。

7. 添加 Wi-Fi 设置完成后，选择“创建配置文件” > “创建”以添加配置文件。 配置文件随即创建并显示在配置文件列表中（“设备配置” > “配置文件”）。

## <a name="next-steps"></a>后续步骤

配置文件已创建，但未执行任何操作。 下一步，[分配此配置文件](device-profile-assign.md)。
