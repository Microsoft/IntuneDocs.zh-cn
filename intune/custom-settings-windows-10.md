---
title: 适用于运行 Windows 10 的设备的 Microsoft Intune 自定义设置
titlesuffix: ''
description: 了解可以在 Windows 10 自定义配置文件中配置的自定义设置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 36705c49a55c88c41470feaad14520e900dcb3dd
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
ms.locfileid: "31837007"
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-windows-10"></a>适用于运行 Windows 10 的设备的 Microsoft Intune 自定义设备设置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

 使用适用于 Windows 10 和 Windows 10 移动版的 Microsoft Intune **自定义**配置文件来部署可用于控制设备功能的 OMA-URI（开放移动联盟统一资源标识符）设置。 Windows 10 提供了许多配置服务提供程序 (CSP) 设置，例如，[策略配置服务提供程序 (策略 CSP)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers)。
如果你正在寻找特定设置，请牢记 [Windows 10 设备限制配置文件](device-restrictions-windows-10.md)包含许多已内置到 Intune 且无需你指定自定义值的设置。

## <a name="configure-custom-settings"></a>配置自定义设置

1. 按照[如何在 Microsoft Intune 中配置自定义设备设置](custom-settings-configure.md)中的说明进行操作。
1. 在“自定义 OMA-URI 设置”窗格上，单击“添加”可添加新值。 还可以单击“导出”创建逗号分隔值 (.csv) 文件中配置的所有值的列表。
1. 对于想要添加的每个 OMA URI 设置，请输入以下信息。 使用本文中的列表了解可以使用的设置：
    - **名称** - 输入 OMA-URI 设置的唯一名称，以帮助你在设置列表中识别它。
    - **描述** -（可选）输入设置的描述。
    - **OMA-URI（区分大小写）** - 指定想要为其提供设置的 OMA-URI。
    - **数据类型** -从以下各项选择：
        - **字符串**
        - **字符串 (XML)**
        - **日期和时间**
        - **整数**
        - **浮点**
        - **布尔值**
        - **Base64**
    - **值** - 指定要与输入的 OMA-URI 关联的值或文件。
1. 完成后，选择“确定”，返回“创建配置文件”窗格，然后选择“创建”。
配置文件随即创建并显示在“配置文件列表”窗格中。

## <a name="example"></a>示例
在以下屏幕截图中，已启用设置 **Connectivity/AllowVPNOverCellular**。 这样一来，Windows 10 设备在处于移动电话网络中时会打开 VPN 连接。

> ![包含 VPN 设置的自定义策略的示例](./media/custom-policy-example.png)


## <a name="how-to-find-the-policies-you-can-configure"></a>如何查找可以配置的策略

可以在 Windows 文档库中的[配置服务提供程序参考](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)中找到 Windows 10 支持的所有配置服务提供程序 (CSP) 的完整列表。

并非所有设置均兼容所有 Windows 10 版本。 Windows 文章中的表将说明各个 CSP 支持的版本。

此外，Intune 并不支持本文中列出的所有设置。 若要查明 Intune 是否支持所需的设置，请打开针对该设置的文章。 每个设置页面将显示其支持的操作。 若要使用 Intune，设置必须支持“添加”或“替换”操作。
