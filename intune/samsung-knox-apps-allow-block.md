---
title: "Intune 策略允许/阻止使用 Samsung KNOX 的应用"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：创建自定义配置文件以允许和阻止适用于 Samsung KNOX 标准版设备的应用。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: dea090e108d5ea023dc64d8d168b25d30b688cb2
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017



---
# <a name="use-custom-policies-to-allow-and-block-apps-for-samsung-knox-standard-devices-in-microsoft-intune"></a>在 Microsoft Intune 中使用自定义策略以允许和阻止适用于 Samsung KNOX 标准版设备的应用
[!INCLUDE[azure_preview](./includes/azure_preview.md)] 使用此主题中的过程创建 Microsoft Intune 自定义策略，该策略创建以下内容之一：

- 阻止在设备上运行的应用的列表。 阻止运行此列表中的应用，即使应用此策略时已安装这些应用也是如此。
- 允许设备用户从 Google Play 商店中安装的应用的列表。 仅可安装你列出的应用。 其他应用不能从应用商店安装。

仅运行 Samsung KNOX 标准版的设备可以使用这些设置。

## <a name="create-an-allowed-or-blocked-app-list"></a>创建允许或阻止的应用列表

1. 登录到 Azure 门户中。
2. 依次选择“更多服务” > “其他” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“设备配置”。
2. 在“设备配置”边栏选项卡上，选择“管理” > “配置文件”。
2. 在配置文件边栏选项卡列表中，选择“创建配置文件”。
3. 在“创建配置文件”边栏选项卡上，输入设备配置文件的“名称”和可选“描述”。
2. 选择“Android”“平台类型”，以及“自定义”“配置文件类型”。
3. 单击“设置”。
3. 在“自定义 OMA-URI 设置”边栏选项卡上，选择“添加”。
4. 在“添加或编辑 OMA-URI 设置”对话框中，指定以下内容：

### <a name="for-a-list-of-apps-that-are-blocked-from-running-on-the-device"></a>阻止在设备上运行的应用的列表：

- **名称** - 输入 **PreventStartPackages**。
- **描述** - 输入可选描述，如“阻止运行的应用列表”。
-     **数据类型** - 在下拉列表中，选择“字符串”。
-     **OMA-URI** - 输入 **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**
-     **值** - 输入你要允许的应用包名称的列表。 你可使用 **; : ,** 或 **|** 作为分隔符。 （示例：package1;package2;）

### <a name="for-a-list-of-apps-that-users-are-allowed-to-install-from-the-google-play-store-while-excluding-all-other-apps"></a>有关允许用户从 Google Play 商店中安装的应用（同时排除所有其他应用）的列表：
- **名称** - 输入 **AllowInstallPackages**。
- **描述** - 输入可选描述，如“用户可从 Google Play 安装的应用的列表”。
- **数据类型** - 在下拉列表中，选择“字符串”。
- **OMA-URI** - 输入 **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**
- **值** - 输入你要允许的应用包名称的列表。 你可使用 **; : ,** 或 **|** 作为分隔符。 （示例：package1;package2;）

4. 单击“确定”，然后在“创建配置文件”边栏选项卡上，选择“创建”。

>[!TIP]
> 可通过浏览 Google Play 商店上的应用找到应用的包 ID。 包 ID 包含在应用页面的 URL 中。 例如，Microsoft Word 应用的包 ID 是 **com.microsoft.office.word**。

每个目标设备下次签入时，将应用此应用设置。


<!---## Assign the custom profile--->

