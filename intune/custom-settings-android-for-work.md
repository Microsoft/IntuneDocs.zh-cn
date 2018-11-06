---
title: 在 Microsoft Intune 中向 Android Enterprise 设备添加自定义设置 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中添加或创建适用于 Android Enterprise 设备的自定义配置文件
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a622264ed7cc091849bacbd02f8ae7bdb33603fe
ms.sourcegitcommit: c969b596ec0fec227484c50f210ba4e159e2e533
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2018
ms.locfileid: "49983136"
---
# <a name="use-custom-settings-for-android-enterprise-devices-in-microsoft-intune"></a>在 Microsoft Intune 中使用适用于 Android Enterprise 设备的自定义设置

借助 Microsoft Intune，可以使用“自定义配置文件”添加或创建适用于 Android Enterprise 设备的自定义设置。 自定义配置文件是 Intune 中的一项功能。 这项功能用于添加未内置到 Intune 的设备设置和功能。

Android Enterprise 自定义配置文件使用开放移动联盟统一资源标识符 (OMA-URI) 设置控制 Android Enterprise 设备上的功能。 移动设备制造商通常使用这些设置来控制这些功能。

Intune 支持有限数量的 Android 自定义配置文件。

本文介绍如何创建适用于 Android Enterprise 设备的自定义配置文件。 文中还提供了可阻止复制粘贴操作的自定义配置文件的示例。

## <a name="create-the-profile"></a>创建配置文件

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
2. 选择“设备配置” > “配置文件” > “创建配置文件”。
3. 输入以下设置：

    - **名称**：输入配置文件的名称，例如 `android enterprise custom profile`
    - **说明**：输入配置文件的说明
    - **平台**：选择“Android Enterprise”
    - **配置文件类型**：选择“自定义”

4. 在“自定义 OMA-URI 设置”中，选择“添加”。 输入以下设置：

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

    - **值**：输入要与已输入的 OMA-URI 关联的数据值。 值取决于所选的数据类型。 例如，如果选择了“日期和时间”，则从日期选取器中选择值。

    添加一些设置后，可以选择“导出”。 “导出”将创建逗号分隔值 (.csv) 文件中添加的所有值的列表。

5. 选择“确定”，保存所做更改。 根据需要继续添加更多设置。
6. 完成后，选择“确定” > “创建”，以创建 Intune 配置文件。 完成后，配置文件将显示在“设备配置 - 配置文件”列表中。

## <a name="example"></a>示例

本此示例中将创建一个自定义配置文件，可用于限制在 Android Enterprise 设备上的工作和个人应用之间执行复制和粘贴操作。

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
2. 选择“设备配置” > “配置文件” > “创建配置文件”。
3. 输入以下设置：

    - **名称**：输入配置文件的名称，例如 `android ent block copy paste custom profile`。
    - **说明**：输入配置文件的说明。
    - **平台**：选择“Android Enterprise”。
    - **配置文件类型**：选择“自定义”。

4. 在“自定义 OMA-URI 设置”中，选择“添加”。 输入以下设置：

    - **名称**：输入类似于 `Block copy and paste` 的内容。
    - **说明**：输入类似于 `Blocks copy/paste between work and personal apps` 的内容。
    - **OMA-URI**：输入 `./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste`.
    - **数据类型**：选择“布尔”，使此 OMA-URI 的值为 True 或 False。
    - **值**：选择“True”。

5. 输入设置后，环境应类似于下图：

    ![阻止 Android 工作配置文件的复制和粘贴。](./media/custom-policy-afw-copy-paste.png)

向你管理的 Android Enterprise 设备分配此配置文件后，将阻止工作和个人配置文件中应用之间的复制和粘贴操作。

## <a name="next-steps"></a>后续步骤

配置文件已创建，但它尚未起到任何作用。 下一步需要[分配配置文件](device-profile-assign.md)。

请参阅如何[在 Android 设备上创建配置文件](custom-settings-android.md)。