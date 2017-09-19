---
title: "适用于 iOS 和 macOS 设备的 Intune AirPrint 设置"
titlesuffix: Azure portal
description: "了解如何使用 Intune 来帮助自动将 iOS 和 macOS 设备连接到与 AirPrint 兼容的打印机。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 712a79fb-14ef-4f6b-aba5-1dfca900afd2
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bf8e076ff5ff4266f36d0a86697558b309a7fc36
ms.sourcegitcommit: cf7f7e7c9e9cde5b030cf5fae26a5e8f4d269b0d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2017
---
# <a name="airprint-settings-for-ios-and-macos-devices"></a>适用于 iOS 和 macOS 设备的 AirPrint 设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用这些设置来配置 iOS 或 macOS 设备以自动连接到网络上与 AirPrint 兼容的打印机。 需要打印机的 IP 地址和资源路径才能继续执行操作。

## <a name="find-airprint-printer-information"></a>查找 AirPrint 打印机信息

使用此过程将 AirPrint 信息添加到 AirPrint 负载，以便 iOS 设备用户可以打印到已知的 AirPrint 打印机。

1. 在连接到同一本地网络（子网）作为 AirPrint 打印机的 Mac 上，打开终端（从“/应用程序/实用程序”）
2. 在终端中，键入“ippfind”，然后按 Enter 键。
3. 记下该命令返回的任何打印机信息，例如：**ipp://myprinter.local.:631/ipp/port1**。 该信息的第一部分是你的打印机的名称，最后一部分是资源路径。
4. 在终端中，键入“ping myprinter.local”，然后按 Enter 键。
5. 记下该命令返回的 IP 地址信息，例如，**PING myprinter.local (10.50.25.21)**。
6. 最后，使用 AirPrint 负载设置中的 IP 地址和资源路径。 示例 IP 地址可以是 **10.50.25.21**，示例资源路径可以是 **/ipp/port1**。

## <a name="configure-an-airprint-profile"></a>配置 AirPrint 配置文件

1. 在“设备功能”边栏选项卡上，选择“AirPrint”。
2. 在“AirPrint”边栏选项卡上，若要添加 AirPrint 目标，输入其“IP 地址” 和“资源路径”，然后单击“添加”。
3. 继续添加所需的目标。 完成后，请选择“确定”。

此外，还可以从逗号分隔值 (.csv) 文件导入打印机列表或导出该列表。


## <a name="next-steps"></a>后续步骤

现在可将设备配置文件分配到所选择的组。 有关详细信息，请参阅[如何分配设备配置文件](device-profile-assign.md)。