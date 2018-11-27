---
title: 在 Microsoft Intune 中向 Windows Phone 8.1 设备添加自定义设置 - Azure | Microsoft Docs
titleSuffix: ''
description: 在 Microsoft Intune 中为运行 Windows Phone 8.1 的设备添加或创建自定义配置文件，以使用 OMA-URI 设置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: a876cf430952aa99957af4bc9a66f4bc29d65df9
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184669"
---
# <a name="use-custom-settings-for-windows-phone-81-devices-in-intune"></a>在 Intune 中使用适用于 Windows Phone 8.1 设备的自定义设置

借助 Microsoft Intune，可以使用“自定义配置文件”添加或创建适用于 Windows Phone 8.1 设备的自定义设置。 自定义配置文件是 Intune 中的一项功能。 这项功能用于添加未内置到 Intune 的设备设置和功能。

Windows Phone 8.1 自定义配置文件使用开放移动联盟统一资源标识符 (OMA-URI) 设置配置不同的功能。 移动设备制造商通常使用这些设置来控制设备上的功能。

本文介绍如何创建适用于 Windows Phone 8.1 设备的自定义配置文件。 

## <a name="create-the-profile"></a>创建配置文件

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
2. 选择“设备配置” > “配置文件” > “创建配置文件”。
3. 输入以下设置：

    - **名称**：输入配置文件的名称，例如 `windows phone custom profile`。
    - **说明**：输入配置文件的说明。
    - **平台**：选择“Windows Phone 8.1”。
    - **配置文件类型**：选择“自定义”。

4. 在“自定义 OMA-URI 设置”中，选择“添加”。 输入以下设置：

    - **名称**：输入 OMA-URI 设置的唯一名称，以帮助你在设置列表中识别它。
    - **说明**：输入设置的简要说明以及有助于找到该配置文件的其他所有相关信息。
    - **OMA-URI**（区分大小写）：输入想要作为设置使用的 OMA-URI。
    - **数据类型**：选择用于此 OMA-URI 设置的数据类型。 选项包括：

        - 字符串
        - 字符串（XML 文件）
        - 日期和时间
        - 整数
        - 浮点
        - 布尔值
        - Base64（文件）

    - **值**：输入要与已输入的 OMA-URI 关联的数据值。 值取决于所选的数据类型。 例如，如果选择了“日期和时间”，则从日期选取器中选择值。

    添加一些设置后，可以选择“导出”。 “导出”将创建逗号分隔值 (.csv) 文件中添加的所有值的列表。

5. 选择“确定”，保存所做更改。 根据需要继续添加更多设置。
6. 完成后，选择“确定” > “创建”，以创建 Intune 配置文件。 完成后，配置文件将显示在“设备配置 - 配置文件”列表中。

## <a name="next-steps"></a>后续步骤

配置文件已创建，但它尚未起到任何作用。 下一步需要[分配配置文件](device-profile-assign.md)。

请参阅如何在 [Windows 10 设备](custom-settings-windows-10.md)上创建自定义配置文件。