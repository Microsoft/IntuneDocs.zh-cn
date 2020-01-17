---
title: 用于允许/阻止在 Samsung Knox 设备上运行应用的 Microsoft Intune 策略
titleSuffix: ''
description: 创建自定义配置文件，以允许和阻止在 Samsung Knox 标准设备上运行应用。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4b83a0339d87375502159467af323fceae5eb6e2
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207071"
---
# <a name="use-custom-policies-in-microsoft-intune-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>在 Microsoft Intune 中使用自定义策略以允许和阻止在 Samsung Knox 标准设备上运行应用 

使用此本文中的过程创建 Microsoft Intune 自定义策略，该策略创建以下内容之一：

- 阻止在设备上运行的应用的列表。 阻止运行此列表中的应用，即使应用此策略时已安装这些应用也是如此。
- 允许设备用户从 Google Play 商店安装的应用列表。 仅可安装你列出的应用。 其他应用不能从应用商店安装。

这些设置只可供运行 Samsung Knox Standard 的设备使用。

## <a name="create-an-allowed-or-blocked-app-list"></a>创建允许或阻止的应用列表

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“设备”   > “配置文件”   > “创建配置文件”  。
3. 输入以下设置：

    - **名称**：输入配置文件的描述性名称。 为配置文件命名，以便稍后可以轻松地识别它们。 例如，有效的配置文件名称为**Windows phone 自定义配置文件**。
    - **描述**：输入包含设置概述以及其他所有重要详细信息的说明。
    - **平台**：选择“Android”  。
    - **配置文件类型**：选择 "**自定义**"。

4. 在“自定义 OMA-URI 设置”中，选择“添加”   。 输入以下设置：

    阻止在设备上运行的应用的列表：

    - **名称**：输入 **PreventStartPackages**。
    - **描述**：输入设置的简要说明以及有助于找到该配置文件的其他所有相关信息。 例如，输入**阻止运行的应用列表**。
    - **OMA-URI**（区分大小写）：输入“./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages”  。
    - **数据类型**：选择 "**字符串**"。
    - **值**：输入你要允许的应用包名称的列表。 可使用 `;`、`:` 或 `|` 作为分隔符。 例如，输入 `package1;package2;`。

   有关允许用户从 Google Play 商店中安装的应用（同时排除所有其他应用）的列表：

    - **名称**：输入 **AllowInstallPackages**。
    - **说明**：输入设置的简要说明以及有助于找到该配置文件的其他所有相关信息。 例如，输入**用户可以从 Google Play 安装的应用列表**。
    - **OMA-URI**（区分大小写）：输入“./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages”  。
    - **数据类型**：选择 "**字符串**"。
    - **值**：输入你要允许的应用包名称的列表。 可使用 `;`、`:` 或 `|` 作为分隔符。 例如，输入 `package1;package2;`。

5. 选择“确定”，保存所做更改  。
6. 完成后，选择“确定” > “创建”，以创建 Intune 配置文件   。 完成后，配置文件将显示在“设备 - 配置文件”列表中  。

>[!TIP]
> 可通过浏览 Google Play 商店上的应用找到应用的包 ID。 包 ID 包含在应用页面的 URL 中。 例如，Microsoft Word 应用的包 ID 是 **com.microsoft.office.word**。

每个目标设备下次签入时，将应用此应用设置。

## <a name="next-steps"></a>后续步骤

配置文件已创建，但它尚未起到任何作用。 下一步，[分配配置文件](../device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。
