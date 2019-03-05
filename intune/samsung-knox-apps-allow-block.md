---
title: 用于允许/阻止在 Samsung Knox 设备上运行应用的 Microsoft Intune 策略
titlesuffix: ''
description: 创建自定义配置文件，以允许和阻止在 Samsung Knox 标准设备上运行应用。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/5/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 38f78d17d0c5e9c12ee02b3644f7fa78fe676d86
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/02/2019
ms.locfileid: "57235457"
---
# <a name="use-custom-policies-in-microsoft-intune-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>在 Microsoft Intune 中使用自定义策略以允许和阻止在 Samsung Knox 标准设备上运行应用 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

使用此本文中的过程创建 Microsoft Intune 自定义策略，该策略创建以下内容之一：

- 阻止在设备上运行的应用的列表。 阻止运行此列表中的应用，即使应用此策略时已安装这些应用也是如此。
- 允许设备用户从 Google Play 商店中安装的应用的列表。 仅可安装你列出的应用。 其他应用不能从应用商店安装。

这些设置只可供运行 Samsung Knox Standard 的设备使用。

## <a name="create-an-allowed-or-blocked-app-list"></a>创建允许或阻止的应用列表

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 在“Intune”窗格上，选择“设备配置”。
2. 在“设备配置”窗格上，选择“管理” > “配置文件”。
2. 在配置文件窗格列表中，选择“创建配置文件”。
3. 在“创建配置文件”窗格上，输入设备配置文件的“名称”和可选“描述”。
2. 对于“平台”选择“Android”，对于“配置文件类型”选择“自定义”。
3. 单击“设置”。
3. 在“自定义 OMA-URI 设置”窗格上，选择“添加”。
4. 在“添加或编辑 OMA-URI 设置”对话框中，指定以下设置：

   阻止在设备上运行的应用的列表：

   - **名称** - 输入 **PreventStartPackages**。
   - **描述** - 输入可选描述，如“阻止运行的应用列表”。
   -    **数据类型** - 在下拉列表中，选择“字符串”。
   -    **OMA-URI** - 输入 **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**
   -    **值** - 输入你要允许的应用包名称的列表。 你可使用 **; : ,** 或 **|** 作为分隔符。 （示例：package1;package2;）

   有关允许用户从 Google Play 商店中安装的应用（同时排除所有其他应用）的列表：
   - **名称** - 输入 **AllowInstallPackages**。
   - **描述** - 输入可选描述，如“用户可从 Google Play 安装的应用的列表”。
   - **数据类型** - 在下拉列表中，选择“字符串”。
   - **OMA-URI** - 输入 **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**
   - **值** - 输入你要允许的应用包名称的列表。 你可使用 **; : ,** 或 **|** 作为分隔符。 （示例：package1;package2;）

4. 单击“确定”，然后在“创建配置文件”窗格上，选择“创建”。

>[!TIP]
> 可通过浏览 Google Play 商店上的应用找到应用的包 ID。 包 ID 包含在应用页面的 URL 中。 例如，Microsoft Word 应用的包 ID 是 **com.microsoft.office.word**。

每个目标设备下次签入时，将应用此应用设置。


<!---## Assign the custom profile--->
