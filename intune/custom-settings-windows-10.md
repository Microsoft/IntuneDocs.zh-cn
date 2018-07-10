---
title: Microsoft Intune 中适用于 Windows 10 设备的自定义设置 - Azure | Microsoft Docs
description: 使用 Microsoft Intune 中的自定义配置文件，在运行 Windows 10 的设备上配置 OMA-URI 自定义设置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bdbb6643a4ee8aace0db22cd7f9189f7ac6445f0
ms.sourcegitcommit: ada99fefe9a612ed753420116f8c801ac4bf0934
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2018
ms.locfileid: "36232820"
---
# <a name="custom-oma-uri-settings-for-windows-10-devices---intune"></a>适用于 Windows 10 设备的自定义 OMA-URI 设置 - Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

使用适用于 Windows 10 和 Windows 10 移动版的 Microsoft Intune 自定义配置文件部署 OMA-URI（开放移动联盟统一资源标识符）设置。 这些设置用于控制设备功能。 Windows 10 提供了许多配置服务提供程序 (CSP) 设置，例如，[策略配置服务提供程序（策略 CSP）](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers)。

如果你正在寻找特定设置，请牢记 [Windows 10 设备限制配置文件](device-restrictions-windows-10.md)包含许多已内置到 Intune 且不需要自定义值的设置。

## <a name="configure-custom-settings"></a>配置自定义设置

1. 使用自定义配置文件类型创建新的配置文件。 [如何配置自定义设备设置](custom-settings-configure.md)中列出了操作步骤。
2. 在“自定义 OMA-URI 设置”中，选择“添加”来创建新设置。 还可以单击“导出”创建逗号分隔值 (.csv) 文件中配置的所有值的列表。
3. 对于要添加的每个 OMA URI 设置，请输入以下信息：

- **名称**：输入 OMA-URI 设置的唯一名称，以帮助你在设置列表中识别它。
- **说明**：（可选）输入设置的说明。
- **OMA-URI（区分大小写）**：输入想要为其提供设置的 OMA-URI。
- **数据类型**：从以下各项选择：
  - **字符串**
  - **字符串 (XML)**
  - **日期和时间**
  - **整数**
  - **浮点**
  - **布尔值**
  - **Base64**
- **值**：输入要与已输入的 OMA-URI 关联的值或文件。

4. 完成后，选择“确定”。 在“创建配置文件”中，选择“创建”。 配置文件随即创建并出现在配置文件列表中。

## <a name="example"></a>示例
下面的示例中启用了 Connectivity/AllowVPNOverCellular 设置。 此设置可允许 Windows 10 设备在处于移动电话网络中时打开 VPN 连接。

![包含 VPN 设置的自定义策略的示例](./media/custom-policy-example.png)

## <a name="find-the-policies-you-can-configure"></a>查找可以配置的策略

可以在[配置服务提供程序参考](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)中找到 Windows 10 支持的所有配置服务提供程序 (CSP) 的完整列表。

并非所有设置均兼容所有 Windows 10 版本。 [配置服务提供程序参考](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)中介绍每个 CSP 所支持的版本。

此外，Intune 并不支持列出的所有设置。 若要查明 Intune 是否支持所需的设置，请打开针对该设置的文章。 每个设置页面将显示其支持的操作。 若要使用 Intune，设置必须支持“添加”或“替换”操作。
