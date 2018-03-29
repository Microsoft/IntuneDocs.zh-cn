---
title: "如何使用 Microsoft Intune 创建自定义 VPN 配置文件"
titleSuffix: 
description: "使用自定义配置在 Intune 中创建 VPN 配置文件。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ec9b959d086051985287a62f7d10fe8d4cbad7e9
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-create-custom-vpn-profiles-in-microsoft-intune"></a>如何在 Microsoft Intune 中创建自定义 VPN 配置文件

可使用 Intune 自定义配置策略为以下平台创建 VPN 配置文件：

* Android 4 及更高版本
* 运行 Windows 8.1 和更高版本的已注册设备
* Windows Phone 8.1 及更高版本
* 运行 Windows 10 桌面版的已注册设备 
* Windows 10 移动版

此类型的策略在标准 Intune VPN 策略不包含要使用的设置时很有用。

## <a name="to-create-a-custom-configuration-policy"></a>创建自定义配置策略：

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 在“Intune”窗格上，选择“设备配置”。
2. 在“管理”部分的“设备配置”窗格上，选择“配置文件”。
5. 在“配置文件”窗格上，选择“创建配置文件”。
6. 在“创建配置文件”窗格上，输入 VPN 配置文件的“名称”和“说明”。
7. 从“平台”下拉列表中，选择要应用 VPN 设置的设备平台。 目前，可以为自定义设备设置选择以下平台之一：
    - **Outlook Web Access (OWA)**
    - **Android for Work**
    - **iOS**（使用从 Apple Configurator 导出的文件配置）。
    - **macOS**（使用从 Apple Configurator 导出的文件配置）。
    - **Windows Phone 8.1**
    - **Windows 8.1 及更高版本**
    - **Windows 10 及更高版本**
6. 从“配置文件”类型下拉列表中，选择“自定义”。
7. 在“自定义 OMA-URI 设置”窗格上，对于要指定的每个 URI 设置，选择“添加”，提供所需的信息，然后选择“确定”。 下面是一个示例：

   ![VPN 配置文件自定义配置对话框](./media/Intune_Add_VPN_URI.png)

4.  输入所需的所有 URI 设置后，选择“确定”，然后在“创建配置文件”窗格上，选择“创建”。

随即创建配置文件并在“配置文件列表”窗格上显示。
如果想要继续操作并将此配置文件分配到组，请参阅[如何分配设备配置文件](device-profile-assign.md)。




