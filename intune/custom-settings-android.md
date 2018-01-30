---
title: "适用于 Android 设备的 Intune 自定义设置"
titleSuffix: Azure portal
description: "了解可以在 Android 自定义配置文件中使用的设置。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 09/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 293137705fc8d5a37ac0dd7101a7ce80c9f7e917
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="custom-settings-for-android-devices-in-microsoft-intune"></a>Microsoft Intune 中适用于 Android 设备的自定义设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用 Microsoft Intune 的 Android **自定义**配置文件来分配可用于控制 Android 设备功能的 OMA-URI 设置。 这些设置是许多移动设备制造商用来控制设备功能的标准设置。

此功能旨在使你能够分配不能使用 Intune 策略配置的以下 Android 设置：

- [使用 Microsoft Intune 自定义设备配置文件，创建具有预共享密钥的 Wi-Fi 配置文件](/intune/wi-fi-profile-shared-key)
- [使用 Microsoft Intune 自定义配置文件为 Android 设备创建每应用 VPN 配置文件](/intune/android-pulse-secure-per-app-vpn)
- [在 Microsoft Intune 中使用自定义策略允许和阻止在 Samsung Knox Standard 设备上运行应用](/intune/samsung-knox-apps-allow-block)

>[!IMPORTANT]
>当前，仅上述设置可通过此配置文件类型配置。 Android 设备不公开可配置的 OMA-URI 设置的完整列表。 若要查看添加的更多设置，请在 [Intune Uservoice 网站](https://microsoftintune.uservoice.com/forums/291681-ideas)上请求这些设置。

## <a name="custom-profile-settings-for-android-devices"></a>适用于 Android 设备的自定义配置文件设置

1. 按照[如何在 Microsoft Intune 中配置自定义设备设置](custom-settings-configure.md)中的说明进行操作。
2. 在“创建配置文件”边栏选项卡上，选择“设置”添加 1 个或多个 OMA-URI 设置。
3. 在“编辑行”边栏选项卡上，为每个设置配置以下值：
    - **名称** - 输入 OMA-URI 设置的唯一名称，以帮助你在设置列表中识别它。
    - **说明** - 提供对设置进行概述的说明以及帮助你找到该设置的其他相关信息。
    - **数据类型** - 选择将在其中指定此 OMA-URI 设置的数据类型。 从“字符串”、“字符串 (XML)”、“日期和时间”、“整数”、“浮点”或者“布尔值”中进行选择。
    - **OMA-URI** 指定需为其提供设置的 OMA-URI。
    - **值** - 输入要与已输入的 OMA-URI 关联的值。
4. 完成后，单击“确定”，根据需要继续添加其他设置。

## <a name="next-steps"></a>后续步骤

完成设置后，将创建配置文件，并显示在配置文件列表边栏选项卡上。 如果想要继续操作并将此配置文件分配到组，请参阅[如何分配设备配置文件](device-profile-assign.md)。




