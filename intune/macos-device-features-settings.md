---
title: Microsoft Intune 中的 macOS 设备功能设置 - Azure | Microsoft Docs
description: 查看 Microsoft Intune 中所有用于为 macOS 设备配置 AirPrint 的设置。 还逐步介绍了如何获取网络中 AirPrint 服务器的 IP 地址、路径和端口设置。 在设备配置文件中使用这些设置，将 macOS 设备配置为使用网络中的 AirPrint 服务器。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/05/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e0707226412d314ac1d44ba339b4c9151b394919
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/02/2019
ms.locfileid: "57233893"
---
# <a name="macos-device-feature-settings-in-intune"></a>Intune 中的 macOS 设备功能设置

Intune 包括一些内置设置，可便于 macOS 用户使用网络中的 AirPrint 打印机进行打印。 本文列出了这些设置，并介绍了每个设置的用途。 它还列出了使用“终端”应用（仿真器）获取 AirPrint 打印机的 IP 地址、路径和端口的步骤。

## <a name="before-you-begin"></a>在开始之前

[创建 macOS 设备配置文件](device-features-configure.md)。

## <a name="airprint-settings"></a>AirPrint 设置

1. 选择“设置”中的“AirPrint”。 输入 AirPrint 服务器的以下属性：

    - **IP 地址**：输入打印机的 IPv4 或 IPv6 地址。 如果使用主机名标识打印机，可以通过在“终端”应用中对打印机执行 ping 操作来获取 IP 地址。 （本文中的）[获取 IP 地址和路径](#get-the-ip-address-and-path)提供了更多详细信息。
    - **路径**：输入打印机的路径。 网络中打印机的路径通常是 `ipp/print`。 （本文中的）[获取 IP 地址和路径](#get-the-ip-address-and-path)提供了更多详细信息。
    - **端口**：输入 AirPrint 目标的侦听端口。 如果将此属性留空，AirPrint 使用默认端口。 适用于 iOS 11.0 及更高版本。
    - **TLS**：选择“启用”可使用传输层安全性 (TLS) 确保 AirPrint 连接安全。 适用于 iOS 11.0 及更高版本。

2. 选择“添加”。 此时，AirPrint 服务器添加到列表中。 可以添加多个 AirPrint 服务器。

    还可以导入包含 AirPrint 打印机列表的逗号分隔文件 (.csv)。 此外，在 Intune 中添加 AirPrint 打印机后，还可以导出此列表。

3. 完成后，选择“确定”，以保存列表。

## <a name="get-the-ip-address-and-path"></a>获取 IP 地址和路径

必须有打印机的 IP 地址、资源路径和端口，才能添加 AirPrinter 服务器。 下面逐步介绍了如何获取此类信息。

1. 在作为 AirPrint 打印机连接到同一本地网络（子网）的 Mac 上，打开“终端”（路径为“/Applications/Utilities”）。
2. 在“终端”应用中，键入“`ippfind`”，再按 Enter。

    记下打印机信息。 例如，可能会返回类似于 `ipp://myprinter.local.:631/ipp/port1` 的内容。 第一部分是打印机名称。 最后一部分 (`ipp/port1`) 是资源路径。

3. 在“终端”中，键入“`ping myprinter.local`”，再按 Enter。

   记下 IP 地址。 例如，可能会返回类似于 `PING myprinter.local (10.50.25.21)` 的内容。

4. 使用 IP 地址和资源路径值。 在此示例中，IP 地址为 `10.50.25.21`，资源路径为 `/ipp/port1`。

## <a name="next-steps"></a>后续步骤

- 查看所有适用于 [iOS 设备](ios-device-features-settings.md)的设置。
- 将此配置文件分配到组；请参阅[分配设备配置文件](device-profile-assign.md)。
