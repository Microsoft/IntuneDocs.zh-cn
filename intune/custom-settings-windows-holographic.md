---
title: "Windows Holographic for Business 设备的 Intune 自定义设置"
titlesuffix: Azure portal
description: "了解可以在 Windows Holographic for Business 自定义配置文件中使用的设置。"
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 1/24/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ae46aef10ca294637a4d433ce273d3c53e695d64
ms.sourcegitcommit: 93622d740cbd12043eedc25a9699cc4256e23e7e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2018
---
# <a name="custom-device-settings-for-windows-holographic-for-business-devices-in-microsoft-intune"></a>Microsoft Intune 中的 Windows Holographic for Business 设备的自定义设备设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

 使用 Windows Holographic for Business 的 Microsoft Intune 自定义配置文件部署可用于控制设备功能的 OMA-URI（开放移动联盟统一资源标识符）设置。 通过 Windows Holographic for Business 可以进行很多配置服务提供程序 (CSP) 设置。 有关 CSP 的概述，请参阅[面向 IT 专业人员的配置服务提供程序 (CSP) 简介](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers)。 如需了解 Windows Holographic 支持的具体 CSP，请参阅 [Windows Holographic 中支持的 CSP](https://docs.microsoft.com/en-us/windows/client-management/mdm/configuration-service-provider-reference#hololens)。

如果正在寻找特定设置，请牢记 [Windows Holographic for Business 设备限制配置文件](device-restrictions-windows-holographic.md)包含许多内置设置，无需指定自定义值。

1. 按照[如何在 Microsoft Intune 中配置自定义设备设置](custom-settings-configure.md)中的说明进行操作。
2. 在“创建配置文件”边栏选项卡上，选择“设置”添加 1 个或多个 OMA-URI 设置。
3. 在“自定义 OMA-URI 设置”边栏选项卡上，单击“添加”可添加新值。 还可以单击“导出”创建逗号分隔值 (.csv) 文件中配置的所有值的列表。
4. 对于想要添加的每个 OMA URI 设置，请输入以下信息。 使用本主题中的列表了解可以使用的设置：
    - **设置名称** - 输入 OMA-URI 设置的唯一名称，以帮助你在设置列表中识别它。
    - **设置描述** -（可选）输入设置的描述。
    - **数据类型** -从以下各项选择：
        - **字符串**
        - **字符串 (XML)**
        - **日期和时间**
        - **整数**
        - **浮点**
        - **布尔值**
    - **OMA-URI（区分大小写）** - 指定想要为其提供设置的 OMA-URI。
    - **值** - 指定要与输入的 OMA-URI 关联的值。
5. 完成后，返回“创建配置文件”边栏选项卡，然后单击“创建”。
系统将创建配置文件并在“配置文件列表”边栏选项卡上显示出来。

## <a name="supported-custom-settings"></a>支持的自定义设置

Windows Holographic for Business 支持下列自定义设置：


|设置名|OMA-URI|数据类型  |
|---------|---------|---------|
|AllowFastReconnect     |./Vendor/MSFT/Policy/Config/Authentication/AllowFastReconnect|整数（0 - 不允许，1 - 允许）|
|AllowVPN     |./Vendor/MSFT/Policy/Config/Settings/AllowVPN|整数（0 - 不允许，1 - 允许）|



## <a name="how-to-find-the-policies-you-can-configure"></a>如何查找可以配置的策略

在 [Windows Holographic 中支持的 CSP](https://docs.microsoft.com/en-us/windows/client-management/mdm/configuration-service-provider-reference#hololens) 中，可以找到 Windows Holographic 支持的所有配置服务提供程序 (CSP) 的完整列表。 并非所有设置都与所有 Windows Holographic 版本兼容。 Windows 主题中的表将告诉你各个 CSP 支持的版本。

此外，Intune 并不支持本主题中列出的所有设置。 若要查明 Intune 是否支持所需的设置，请打开适用于该设置的主题。 每个设置页面将显示其支持的操作。 若要使用 Intune，设置必须支持“添加”或“替换”操作。


