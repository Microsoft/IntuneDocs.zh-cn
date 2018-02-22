---
title: "导入适用于 Windows 8.1 和更高版本的 Wi-Fi 设置"
titleSuffix: Azure portal
description: "如何将 Wi-Fi 设置从 Windows 导入 Intune Wi-Fi 配置文件。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 1/25/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5b4b77f9c9c1c957e3332c20e010a5e8e8ec2b56
ms.sourcegitcommit: 93622d740cbd12043eedc25a9699cc4256e23e7e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-import-wi-fi-settings-for-windows-81-and-later-devices-in-microsoft-intune"></a>如何在 Microsoft Intune 中导入适用于 Windows 8.1 及更高版本设备的 Wi-Fi 设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

对于运行 Windows 8.1、Windows 10 桌面版或移动版或 Windows Holographic for Business 的设备，可以导入之前导出到文件的 Wi-Fi 配置文件。

## <a name="export-wi-fi-settings-from-a-windows-device"></a>从 Windows 设备导出 Wi-Fi 设置

在 Windows 中，使用 **netsh wlan** 实用程序将现有的 Wi-Fi 配置文件导出为 Intune 可读取的 XML 文件。 如果 Windows 计算机上已安装了所需的 WiFi 配置文件，请遵循以下过程。
1. 为导出的 W-Fi-配置文件创建本地文件夹，如 **c:\WiFi**。
1. 以管理员身份打开命令提示符。
1. 运行 **netsh wlan show profiles** 命令，并记下想导出的配置文件的名称。 在此示例中，配置文件的名称是 **WiFiName**。
1. 运行以下命令：netsh wlan export profile name="ProfileName" folder=c:\Wifi。这会在目标文件夹中创建一个名为 Wi-Fi-WiFiName.xml 的 Wi-Fi 配置文件。

## <a name="import-the-wi-fi-settings-into-intune"></a>将 Wi-Fi 设置导入 Intune

1. 登录 Azure 门户。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“设备配置”。
2. 在“设备配置”边栏选项卡上，依次选择“管理” > “配置文件”。
3. 在“配置文件”边栏选项卡上，单击“创建配置文件”。
4. 在“创建配置文件”边栏选项卡上，输入设备限制配置文件的“名称”和“说明”。

   > [!WARNING]
   > 该名称必须与 Wi-fi 配置文件 xml 中的名称属性相同，否则操作会失败。

5. 从“平台”下拉列表中，选择“Windows 8.1 及更高版本”。
6. 在“配置文件”类型下拉列表中，选择“Wi-Fi 导入”。
7. 在“Wi-Fi 基本选项”边栏选项卡上，配置以下设置：
    - **连接名称** 输入 Wi-Fi 连接的名称。 最终用户浏览可用 Wi-Fi 网络时，会显示此名称。
    - **配置文件 XML** 单击浏览器按钮以选择包含想要导入 Intune 的 Wi-Fi 配置文件设置的 XML 文件。
    - **文件内容** 显示你选择的配置描述文件的 XML 代码。
8. 完成后，返回“创建配置文件”边栏选项卡，然后点击“创建”。

系统将创建配置文件并在“配置文件列表”边栏选项卡上显示出来。
