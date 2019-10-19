---
title: 在 Microsoft Intune 中向 Android 设备添加自定义设置 - Azure | Microsoft Docs
description: 添加或创建适用于 Android 设备的自定义配置文件，进而创建具有预共享密钥的 WiFi 配置文件、按每个应用创建 VPN 配置文件，或在 Microsoft Intune 中允许/阻止适用于 Samsung Knox 标准设备的应用
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 17f0b30d0a8c706a7fdff1c7da722eeccdf097eb
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72495793"
---
# <a name="use-custom-settings-for-android-devices-in-microsoft-intune"></a>在 Microsoft Intune 中使用适用于 Android 设备的自定义设置

借助 Microsoft Intune，可以使用“自定义配置文件”添加或创建适用于 Android 设备的自定义设置。 自定义配置文件是 Intune 中的一项功能。 这项功能用于添加未内置到 Intune 的设备设置和功能。

Android 自定义配置文件使用开放移动联盟统一资源标识符 (OMA-URI) 设置配置 Android 设备上的不同功能。 移动设备制造商通常使用这些设置来控制这些功能。

通过自定义配置文件，可配置和分配以下 Android 设置。 以下设置未内置于 Intune：

- [创建具有预共享密钥的 Wi-Fi 配置文件](/intune/wi-fi-profile-shared-key)
- [创建每应用 VPN 配置文件](/intune/android-pulse-secure-per-app-vpn)
- [允许和阻止适用于 Samsung Knox 标准版设备的应用](/intune/samsung-knox-apps-allow-block)

>[!IMPORTANT]
> 自定义配置文件中仅可配置列出的设置。 Android 设备不公开可配置的 OMA-URI 设置的完整列表。 如需查看更多设置，请在 [Intune Uservoice 网站](https://microsoftintune.uservoice.com/forums/291681-ideas)投票支持其他设置。

本文介绍如何创建适用于 Android 设备的自定义配置文件。

## <a name="create-the-profile"></a>创建配置文件

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“设备配置” > “配置文件” > “创建配置文件”    。
3. 输入以下设置：

    - **名称**：输入配置文件的名称，例如 `android custom profile`。
    - **说明**：输入配置文件的说明。
    - **平台**：选择“Android”  。
    - **配置文件类型**：选择“自定义”  。

4. 在“自定义 OMA-URI 设置”中，选择“添加”   。 输入以下设置：

    - **名称**：输入 OMA-URI 设置的唯一名称，便于轻松查找。
    - **说明**：输入设置的简要说明以及其他重要详细信息。
    - **OMA-URI**：输入要作为设置使用的 OMA-URI。
    - **数据类型**：选择用于此 OMA-URI 设置的数据类型。 选项包括：

      - 字符串
      - 字符串（XML 文件）
      - 日期和时间
      - 整数
      - 浮点
      - 布尔值
      - Base64（文件）

    - **值**：输入要与已输入的 OMA-URI 关联的数据值。 值取决于所选的数据类型。 例如，如果选择了“日期和时间”，则从日期选取器中选择值  。

    添加一些设置后，可以选择“导出”  。 “导出”将创建逗号分隔值 (.csv) 文件中添加的所有值的列表  。

5. 选择“确定”，保存所做更改  。 根据需要继续添加更多设置。 
6. 完成后，选择“确定” > “创建”，以创建 Intune 配置文件   。 完成后，配置文件将显示在“设备配置 - 配置文件”列表中  。

## <a name="next-steps"></a>后续步骤

配置文件已创建，但它尚未起到任何作用。 下一步需要[分配配置文件](device-profile-assign.md)。

请参阅如何[在 Android Enterprise 设备上创建配置文件](custom-settings-android-for-work.md)。
