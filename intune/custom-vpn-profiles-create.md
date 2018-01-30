---
title: "如何使用 Microsoft Intune 创建自定义 VPN 配置文件"
titleSuffix: Azure portal
description: "使用自定义配置在 Intune 中创建 VPN 配置文件。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 70af9ce41efa7f52987e1103b89493b4cf200091
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-create-custom-vpn-profiles-in-microsoft-intune"></a>如何在 Microsoft Intune 中创建自定义 VPN 配置文件

## <a name="create-a-custom-configuration"></a>创建自定义配置
可使用 Intune 自定义配置策略为以下设备创建 VPN 配置文件：

* 运行 Android 4 和更高版本的设备
* 运行 Windows 8.1 和更高版本的已注册设备
* 运行 Windows Phone 8.1 和更高版本的设备
* 运行 Windows 10 桌面版的已注册设备 
* 运行 Windows 10 移动版的设备

此类型的策略在标准 Intune VPN 策略不包含要使用的设置时很有用。

## <a name="to-create-a-custom-configuration-policy"></a>创建自定义配置策略：

1. 登录 Azure 门户。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“设备配置”。
4. 在“设备配置”边栏选项卡上，依次选择“管理” > “配置文件”。
5. 在配置文件边栏选项卡上，选择“创建配置文件”。
6. 在“创建配置文件”边栏选项卡上，输入 VPN 配置文件的“名称”和“说明”。
7. 从“平台”下拉列表中，选择要应用 VPN 设置的设备平台。 目前，可以为自定义设备设置选择以下平台之一：
    - **Outlook Web Access (OWA)**
    - **iOS**（使用从 Apple Configurator 导出的文件配置）。
    - **macOS**（使用从 Apple Configurator 导出的文件配置）。
    - **Windows Phone 8.1**
    - **Windows 10 及更高版本**
6. 从“配置文件”类型下拉列表中，选择“自定义”。
7. 在“自定义 OMA-URI 设置”边栏选项卡上，对于要指定的每个 URI 设置，选择“添加”，提供所需的信息，然后选择“确定”。 下面是一个示例：

   ![VPN 配置文件自定义配置对话框](./media/Intune_Add_VPN_URI.png)

4.  输入所需的所有 URI 设置后，选择“确定”，然后在“创建配置文件”边栏选项卡上，选择“创建”。

此时，配置文件会进行创建，并显示在配置文件列表边栏选项卡上。
如果想要继续操作并将此配置文件分配到组，请参阅[如何分配设备配置文件](device-profile-assign.md)。




