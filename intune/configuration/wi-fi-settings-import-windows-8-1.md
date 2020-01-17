---
title: 在 Microsoft Intune 中导入适用于 Windows 设备的 Wi-Fi 设置 - Azure | Microsoft Docs
description: 使用 netsh wlan 将 Windows 设备中的 Wi-Fi 设置导出为 XML 文件。 然后，在 Intune 中导入此文件，为运行 Windows 8.1、Windows 10 和 Windows Holographic for Business 的设备创建 Wi-Fi 配置文件。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f79ccdc71ddbfa3f25daef629515fb612de01852
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207003"
---
# <a name="import-wi-fi-settings-for-windows-devices-in-intune"></a>在 Intune 中导入适用于 Windows 设备的 Wi-Fi 设置

对于运行 Windows 的设备，可以导入之前导出到文件的 Wi-Fi 配置文件。 对于 Windows 10 及更高版本的设备，还可以直接在 Intune 中[创建 Wi-Fi 配置文件](wi-fi-settings-windows.md)  。

适用于：  
- Windows 8.1 及更高版本
- Windows 10 及更高版本
- Windows 10 桌面版或移动版
- Windows Holographic for Business

## <a name="export-wi-fi-settings-from-a-windows-device"></a>从 Windows 设备导出 Wi-Fi 设置

在 Windows 中，使用 `netsh wlan` 将现有的 Wi-Fi 配置文件导出为 Intune 可读取的 XML 文件。 必须将密钥导出为纯文本才能成功使用配置文件。

如果 Windows 计算机上已安装了所需的 WiFi 配置文件，请按照以下步骤进行操作：

1. 为导出的 Wi-Fi 配置文件创建本地文件夹，如 c:\WiFi  。
2. 以管理员身份打开命令提示符。
3. 运行 `netsh wlan show profiles` 命令。 记下要导出的配置文件的名称。 在此示例中，配置文件的名称是 **WiFiName**。
4. 运行 `netsh wlan export profile name="ProfileName" folder=c:\Wifi` 命令。 此命令会在目标文件夹中创建一个名为“Wi-Fi-WiFiName.xml”  的 Wi-Fi 配置文件。

## <a name="import-the-wi-fi-settings-into-intune"></a>将 Wi-Fi 设置导入 Intune

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“设备”   > “配置文件”   > “创建配置文件”  。
3. 输入以下设置：

    - **名称**：输入配置文件的描述性名称。 该名称必须与 Wi-Fi 配置文件 xml 中的名称属性相同  。 否则操作会失败。
    - **描述**：输入包含设置概述以及其他所有重要详细信息的说明。
    - **平台**：选择“Windows 8.1 及更高版本”  。
    - **配置文件类型**：选择“Wi-Fi 导入”  。

    > [!IMPORTANT]
    > - 如果要导出的 Wi-Fi 配置文件中包含预共享密钥，则必须在命令中添加 `key=clear`  。 例如，输入 `netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi`
    > - 在 Windows 10 中使用预共享的密钥会导致 Intune 中出现修正错误。 出现这种情况时，Wi-Fi 配置文件已正确分配给设备，并且该配置文件可以正常工作。
    > - 如果导出的 Wi-Fi 配置文件含有预共享密钥，请务必保管好该文件。 密钥为纯文本格式，你需负责保管好该密钥。

4. 输入以下设置：

    - **连接名称**：为此 Wi-Fi 连接输入名称。 用户浏览可用 Wi-fi 网络时向用户显示此名称。
    - **配置文件 XML**：选择浏览按钮，然后选择包含想要导入的 Wi-Fi 配置文件设置的 XML 文件。
    - **文件内容**：显示你选择的配置文件的 XML 代码。

5. 选择“确定”，保存所做更改  。
6. 完成后，选择“确定”   > “创建”  ，以创建 Intune 配置文件。 完成后，配置文件将显示在“设备 - 配置文件”  列表中。

## <a name="next-steps"></a>后续步骤

配置文件已创建，但未执行任何操作。 下一步，[分配配置文件](../device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

请参阅 [Wi-Fi 设置概述](wi-fi-settings-configure.md)，其中包括了其他可用平台。
