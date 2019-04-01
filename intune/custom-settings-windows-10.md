---
title: 在 Microsoft Intune 中添加适用于 Windows 10 设备的自定义设置 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中为运行 Windows 10 的设备添加或创建自定义配置文件，以使用 OMA-URI 设置。 使用自定义配置文件添加自定义设置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 44be460ee910818d52179da55151d1bceeb8b306
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565904"
---
# <a name="use-custom-settings-for-windows-10-devices-in-intune"></a>在 Intune 中使用适用于 Windows 10 设备的自定义设置

借助 Microsoft Intune，可以使用“自定义配置文件”添加或创建适用于 Windows 10 设备的自定义设置。 自定义配置文件是 Intune 中的一项功能。 这项功能用于添加未内置到 Intune 的设备设置和功能。

Windows 10 自定义配置文件使用开放移动联盟统一资源标识符 (OMA-URI) 设置配置不同的功能。 移动设备制造商通常使用这些设置来控制设备上的功能。 

Windows 10 提供了许多配置服务提供程序 (CSP) 设置，例如，[策略配置服务提供程序（策略 CSP）](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers)。

如果正在寻找特定设置，请记住 [Windows 10 设备限制配置文件](device-restrictions-windows-10.md)包含许多内置设置。 因此，可能不需要输入自定义值。

本文介绍：

- 如何创建适用于 Windows 10 设备的自定义配置文件
- 建议的 OMA-URI 设置列表
- 提供打开 VPN 连接的自定义配置文件的示例

## <a name="create-the-profile"></a>创建配置文件

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
2. 选择“设备配置” > “配置文件” > “创建配置文件”。
3. 输入以下设置：

    - **名称**：输入配置文件的名称，例如 `windows 10 custom profile`。
    - **说明**：输入配置文件的说明。
    - **平台**：选择“Windows 10 及更高版本”。
    - **配置文件类型**：选择“自定义”。

4. 在“自定义 OMA-URI 设置”中，选择“添加”。 输入以下设置：

    - **名称**：输入 OMA-URI 设置的唯一名称，以帮助你在设置列表中识别它。
    - **说明**：输入设置的简要说明以及其他重要详细信息。
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

## <a name="example"></a>示例

下面的示例中启用了 Connectivity/AllowVPNOverCellular 设置。 此设置可允许 Windows 10 设备在处于移动电话网络中时打开 VPN 连接。

![包含 VPN 设置的自定义策略的示例](./media/custom-policy-example.png)

## <a name="find-the-policies-you-can-configure"></a>查找可以配置的策略

可以在[配置服务提供程序参考](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)中找到 Windows 10 支持的所有配置服务提供程序 (CSP) 的完整列表。

并非所有设置均兼容所有 Windows 10 版本。 [配置服务提供程序参考](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)中介绍每个 CSP 所支持的版本。

此外，Intune 并不支持[配置服务提供程序参考](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)中列出的所有设置。 若要查明 Intune 是否支持所需的设置，请打开针对该设置的文章。 每个设置页面都将显示其支持的操作。 若要使用 Intune，设置必须支持“添加”、“替换”和“获取”操作。 如果返回的值**获取**操作与提供的值不匹配**添加**或**替换**操作，那么 Intune 将报告符合性错误。

## <a name="next-steps"></a>后续步骤

配置文件已创建，但它尚未起到任何作用。 下一步需要[分配配置文件](device-profile-assign.md)。
