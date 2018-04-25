---
title: 导入适用于 Windows 8.1 和更高版本的 Wi-Fi 设置
titleSuffix: Microsoft Intune
description: 如何将 Wi-Fi 设置从 Windows 导入 Intune Wi-Fi 配置文件。
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 033b60fded23f5a1dac5c8ff93716dac77c56fe2
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="import-wi-fi-settings-for-windows-81-and-later-devices-in-microsoft-intune"></a>在 Microsoft Intune 中导入适用于 Windows 8.1 及更高版本设备的 Wi-Fi 设置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

对于运行 Windows 8.1、Windows 10 桌面版或移动版或 Windows Holographic for Business 的设备，可以导入之前导出到文件的 Wi-Fi 配置文件。

## <a name="export-wi-fi-settings-from-a-windows-device"></a>从 Windows 设备导出 Wi-Fi 设置

在 Windows 中，使用 **netsh wlan** 实用程序将现有的 Wi-Fi 配置文件导出为 Intune 可读取的 XML 文件。 必须将密钥导出为纯文本才能成功使用配置文件。

如果 Windows 计算机上已安装了所需的 WiFi 配置文件，请按照以下步骤进行操作：

1. 为导出的 W-Fi-配置文件创建本地文件夹，如 **c:\WiFi**。
2. 以管理员身份打开命令提示符。
3. 运行 `netsh wlan show profiles` 命令，并记下想导出的配置文件的名称。 在此示例中，配置文件的名称是 **WiFiName**。
4. 运行 `netsh wlan export profile name="ProfileName" folder=c:\Wifi` 命令。此操作会在目标文件夹中创建一个名为“Wi-Fi-WiFiName.xml”的 Wi-Fi 配置文件。

## <a name="import-the-wi-fi-settings-into-intune"></a>将 Wi-Fi 设置导入 Intune

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 选择“设备配置” > “配置文件” > “创建配置文件”。
4. 输入设备限制配置文件的“名称”和“描述”。

    > [!IMPORTANT]
    > - 该名称必须与 Wi-Fi 配置文件 xml 中的名称属性相同。 否则操作会失败。
    > - 如果要导出的 Wi-Fi 配置文件中包含预共享密钥，则必须在命令中添加 `key=clear`。 例如，输入 `netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi`
    > - 在 Windows 10 中使用预共享的密钥会导致 Intune 中出现修正错误。 出现这种情况时，Wi-Fi 配置文件已正确分配给设备，并且该配置文件可以正常工作。
    > - 如果导出的 Wi-Fi 配置文件含有预共享密钥，请务必保管好该文件。 密钥为纯文本格式，你需负责保管好该密钥。

5. 在“平台”中，选择“Windows 8.1 及更高版本”。
6. 在“配置文件类型”中，选择“Wi-Fi 导入”。
7. 配置下列设置：
  - **连接名称**：输入 Wi-Fi 连接的名称。 最终用户浏览可用 Wi-Fi 网络时，会显示此名称。
  - **配置文件 XML**：选择浏览器按钮以选择包含想要导入 Intune 的 Wi-Fi 配置文件设置的 XML 文件。
  - **文件内容**：显示你选择的配置文件的 XML 代码。
8. 完成后，选择“确定”，然后选择“创建”创建配置文件。

配置文件随即创建并在配置文件列表中列出。
