---
title: Microsoft Intune 中的 macOS 设备功能设置 - Azure | Microsoft Docs
description: 查看用于为 macOS 设备配置 AirPrint 的设置，自定义“登录”窗口以显示或隐藏 Microsoft Intune 中的电源按钮。 请参阅获取网络中 AirPrint 服务器的 IP 地址、路径和端口设置的步骤。 在设备配置配置文件中使用这些设置来配置 macOS 设备功能。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 63f2832dd321425efe8092f1bb12dd0d479ef71b
ms.sourcegitcommit: b78793ccbef2a644a759ca3110ea73e7ed6ceb8f
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 08/16/2019
ms.locfileid: "69549936"
---
# <a name="macos-device-feature-settings-in-intune"></a>Intune 中的 macOS 设备功能设置

Intune 包含一些内置设置，用于自定义 macOS 设备上的功能。 本文列出了这些设置，并介绍了每个设置的用途。 它还列出了使用“终端”应用（仿真器）获取 AirPrint 打印机的 IP 地址、路径和端口的步骤。

此功能适用于：

- macOS

使用这些设置创建横幅、选择用户登录方式、添加 AirPrint 服务器等，这是移动设备管理 (MDM) 解决方案的一部分内容。

我们将这些设置添加到 Intune 中的设备配置配置文件中，然后分配或部署到 macOS 设备。

## <a name="before-you-begin"></a>在开始之前

[创建 macOS 设备配置文件](device-features-configure.md)。

## <a name="airprint"></a>AirPrint

- **IP 地址**：输入打印机的 IPv4 或 IPv6 地址。 如果使用主机名标识打印机，可以通过在“终端”应用中对打印机执行 ping 操作来获取 IP 地址。 （本文中的）[获取 IP 地址和路径](#get-the-ip-address-and-path)提供了更多详细信息。
- **路径**：输入打印机的路径。 网络中打印机的路径通常是 `ipp/print`。 （本文中的）[获取 IP 地址和路径](#get-the-ip-address-and-path)提供了更多详细信息。
- **端口**（iOS 11.0 及更高版本）：输入 AirPrint 目标的侦听端口。 如果将此属性留空，AirPrint 使用默认端口。
- **TLS**（iOS 11.0 及更高版本）：选择“启用”可使用传输层安全性 (TLS) 确保 AirPrint 连接安全  。

**添加**：AirPrint 服务器。 可以添加多个 AirPrint 服务器。

- **导入**（可选）：还可以导入包含 AirPrint 打印机列表的以逗号分隔的文件 (.csv)  。 此外，在 Intune 中添加 AirPrint 打印机后，还可以导出  此列表。

选择“确定”保存设置  。

### <a name="get-the-ip-address-and-path"></a>获取 IP 地址和路径

必须有打印机的 IP 地址、资源路径和端口，才能添加 AirPrinter 服务器。 下面逐步介绍了如何获取此类信息。

1. 在作为 AirPrint 打印机连接到同一本地网络（子网）的 Mac 上，打开“终端”  （路径为“/Applications/Utilities”  ）。
2. 在“终端”应用中，键入“`ippfind`”，再按 Enter。

    记下打印机信息。 例如，可能会返回类似于 `ipp://myprinter.local.:631/ipp/port1` 的内容。 第一部分是打印机名称。 最后一部分 (`ipp/port1`) 是资源路径。

3. 在“终端”中，键入“`ping myprinter.local`”，再按 Enter。

   记下 IP 地址。 例如，可能会返回类似于 `PING myprinter.local (10.50.25.21)` 的内容。

4. 使用 IP 地址和资源路径值。 在此示例中，IP 地址为 `10.50.25.21`，资源路径为 `/ipp/port1`。

## <a name="login-items"></a>登录项

- **文件、文件夹和自定义应用**: 在用户登录到设备时,**添加**要打开的文件、文件夹、自定义应用或系统应用的路径。 系统应用或为组织生成或自定义的应用通常位于`Applications`文件夹中, 路径类似于。 `/Applications/AppName.app` 

  可以添加多个文件、文件夹和应用。 例如，输入：  
  
  - `/Applications/Calculator.app`
  - `/Applications`
  - `/Applications/Microsoft Office/root/Office16/winword.exe`
  - `/Users/UserName/music/itunes.app`
  
  添加任何应用、文件夹或文件时, 请确保输入正确的路径。 并非所有项都位于`Applications`文件夹中。 如果用户将项从一个位置移到另一个位置, 则路径会更改。 当用户登录时, 此移动的项目将不会打开。

## <a name="login-window"></a>登录窗口

### <a name="window-layout"></a>Window 布局

- **在菜单栏中显示其他信息**：选中菜单栏上的时间区域时，选择“允许”可显示主机名和 macOS 版本  。 如果选择“未配置”（默认），则菜单栏上不会显示此信息  。
- **横幅**：输入一条在设备登录屏幕上显示的消息。 例如，输入组织信息、欢迎消息、失物招领信息等。
- **选择登录格式**：选择用户登录设备的方式。 选项包括：
  - **提示输入用户名和密码**（默认）：要求用户输入用户名和密码。
  - **列出所有用户，提示输入密码**：要求用户从用户列表中选择其用户名，然后输入其密码。 还需配置：

    - **本地用户**：选择“隐藏”则不会在用户列表中显示本地用户帐户，其中可能包含标准帐户和管理员帐户  。 仅显示网络和系统用户帐户。 如果选择“未配置”（默认），会显示用户列表中的本地用户帐户  。
    - **移动帐户**：选择“隐藏”则不会在用户列表中显示移动帐户  。 如果选择“未配置”（默认），会显示用户列表中的移动帐户  。 一些移动帐户可能会显示为网络用户。
    - **网络用户**：选择“显示”会在用户列表中显示网络用户  。 如果选择“未配置”（默认），则不显示用户列表中的网络用户帐户  。
    - **管理员用户**：选择“隐藏”则不在用户列表中显示管理员用户帐户  。 选择“未配置”（默认）则显示用户列表中的管理员用户帐户  。
    - **其他用户**：选择“显示”则列出用户列表中的“其他...”用户   。 选择“未配置”（默认）则不显示用户列表中的其他用户帐户  。

### <a name="login-screen-power-settings"></a>登录屏幕电源设置

- **关闭按钮**：选择“隐藏”则不会在登录屏幕上显示关机按钮  。 选择“未配置”（默认）则显示关闭按钮  。
- **重启按钮**：选择“隐藏”则不会在登录屏幕上显示重启按钮  。 选择“未配置”（默认）则显示重启按钮  。
- **睡眠按钮**：选择“隐藏”则不会在登录屏幕上显示睡眠按钮  。 选择“未配置”（默认）则显示睡眠按钮  。

### <a name="other"></a>其他

- **禁止用户从控制台登录**：“禁用”会隐藏用于登录的 macOS 命令行  。 对一般用户“禁用”此设置  。 选择“未配置”（默认）则允许高级用户使用 macOS 命令行登录  。 要进入控制台模式，用户必须在“用户名”字段中输入 `>console`，并且必须在控制台窗口中进行身份验证。

### <a name="apple-menu"></a>Apple 菜单

用户登录设备后，以下设置会影响他们的操作。

- **禁用关机**：选择“禁用”会阻止用户在其登录后选择“关机”选项   。 选择“未配置”（默认）则允许用户选择设备上的“关机”菜单项   。
- **禁用重启**：选择“禁用”则阻止用户在其登录后选择“重启”选项   。 选择“未配置”（默认）则允许用户选择设备上的“重启”菜单项   。
- **禁用关闭电源**：选择“禁用”则阻止用户在其登录后选择“关闭电源”选项   。 选择“未配置”（默认）则允许用户选择设备上的“关闭电源”菜单项   。
- **禁用注销**（macOS 10.13 及更高版本）：选择“禁用”则阻止用户在其登录后选择“注销”选项   。 选择“未配置”（默认）则允许用户选择设备上的“注销”菜单项   。
- **禁用锁屏**（macOS 10.13 及更高版本）：选择“禁用”则阻止用户在其登录后选择“锁屏”选项   。 选择“未配置”（默认）则允许用户选择设备上的“锁屏”菜单项   。

选择“确定”以保存设置  。

## <a name="next-steps"></a>后续步骤

- 查看所有适用于 [iOS 设备](ios-device-features-settings.md)的设置。
- [将此配置文件分配](device-profile-assign.md)给组，并[监视配置文件状态](device-profile-monitor.md)。
