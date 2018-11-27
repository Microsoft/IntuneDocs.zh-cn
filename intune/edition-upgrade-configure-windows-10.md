---
title: 使用 Microsoft Intune 在 Windows 10 设备上升级或使用 S 模式 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中创建设备配置文件以将 Windows 10 设备升级到不同版本。 例如，可从 Windows 10 专业版升级到 Windows 10 企业版。 还可使用该配置文件在设备上启用或切出 S 模式。 另请参阅 Windows 10 专业版、N 版、教育版、云、企业版、核心版、全息版和移动版支持的升级路径。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: eb44647e50e406b9ef5052c576660c9b7eebf6dd
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189752"
---
# <a name="use-a-configuration-profile-to-upgrade-windows-10-or-switch-from-s-mode-in-intune"></a>使用配置文件升级 Windows 10 或在 Intune 中从 S 模式切换
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

在 Intune 中配置升级配置文件以自动将运行 Windows 10 版的设备升级到其他版本。 另请参阅支持的升级路径。

## <a name="before-you-begin"></a>在开始之前
将设备升级至最新版本之前，需要以下先决条件：

- 用于在该策略针对的所有设备上安装已更新 Windows 版本的有效产品密钥（适用于 Windows 10 桌面版）。 你可以使用多激活密钥 (MAK) 或密钥管理服务器 (KMS) 密钥。 对于 Windows 10 移动版和 Windows 10 全息版，可使用包含许可信息的 Microsoft 许可证文件以在该策略针对的所有设备上安装已更新 Windows 版本。
- 分配策略的 Windows 10 设备将在 Microsoft Intune 中注册。 无法将版本升级策略用于运行 Intune 电脑客户端软件的电脑。

## <a name="supported-upgrade-paths"></a>支持的升级路径
下表列出了 Windows 10 版本升级配置文件支持的升级路径。

| 从 | 升级到 |
|---|---|
| Windows 10 专业版 | Windows 10 教育版 <br/>Windows 10 企业版 <br/>Windows 10 专业教育版 |
| Windows 10 专业版 N | Windows 10 教育版 N <br/>Windows 10 企业版 N <br/>Windows 10 专业教育版 N | 
| Windows 10 专业教育版 | Windows 10 教育版 | 
| Windows 10 专业教育版 N | Windows 10 教育版 N |
| Windows 10 云端版 | Windows 10 教育版 <br/>Windows 10 企业版 <br/>Windows 10 专业版 <br/>Windows 10 专业教育版 | 
| Windows 10 云端版 N | Windows 10 教育版 N <br/>Windows 10 企业版 N <br/>Windows 10 专业版 N <br/>Windows 10 专业教育版 N | 
| Windows 10 企业版 | Windows 10 教育版 | 
| Windows 10 企业版 N | Windows 10 教育版 N | 
| Windows 10 核心版 | Windows 10 教育版 <br/>Windows 10 企业版 <br/>Windows 10 专业教育版 | 
| Windows 10 核心板 N | Windows 10 教育版 N <br/>Windows 10 企业版 N <br/>Windows 10 专业教育版 N | 
| Windows 10 全息版 | Windows 10 Holographic for Business |
| Windows 10 移动版 | Windows 10 移动企业版 |


<!-- Testing a new table on 3/5/18 

The following lists provide the supported upgrade paths for the Windows 10 edition upgrade profile. The Windows 10 edition to upgrade to is in bold followed by the list of supported editions that you can upgrade from:

**Windows 10 Education**
- Windows 10 Pro
- Windows 10 Pro Education
- Windows 10 Cloud
- Windows 10 Enterprise
- Windows 10 Core
    
**Windows 10 Education N edition**    
- Windows 10 Pro N edition
- Windows 10 Pro Education N edition
- Windows 10 Cloud N edition
- Windows 10 Enterprise N edition
- Windows 10 Core N edition
    
**Windows 10 Enterprise**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Windows 10 Enterprise N edition**
- Windows 10 Pro N edition
- Windows 10 Cloud N edition
- Windows 10 Core N edition
    
**Windows 10 Pro**
- Windows 10 Cloud
    
**Windows 10 Pro N edition**
- Windows 10 Cloud N edition
    
**Windows 10 Pro Education**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Windows 10 Pro Education N edition**
- Windows 10 Pro N edition
- Windows 10 Cloud N edition
- Windows 10 Core N edition

**Windows 10 Holographic for Business**
- Windows 10 Holographic

**Windows 10 Mobile Enterprise**
- Windows 10 Mobile -->

<!--The following table provides information about the supported upgrade paths for Windows 10 editions in this policy:

![supported](./media/check_grn.png)  (X) = not supported    
![unsupported](./media/x_blk.png)    (green checkmark) = supported    

|Upgrade from edition\Upgrade to edition|Education|Education N|Pro Education|Pro Education N|Enterprise|Enterprise N|Professional|Professional N|Mobile Enterprise|Holographic for Business|
|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|
|Pro|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro Education|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro Education N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Cloud|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Cloud N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Enterprise|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Enterprise N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Core|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)   |![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Core N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Mobile|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|
|Holographic|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png) -->

## <a name="upgrade-the-edition"></a>升级版本

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
2. 选择“设备配置” > “配置文件” > “创建配置文件”。
3. 输入配置文件的“名称”和“描述”。 例如，输入类似于 `Windows 10 edition upgrade` 的内容
4. 在“平台”中，选择“Windows 10 及更高版本”。
5. 在“配置文件类型”中，选择“版本升级”。
6. 在“版本升级”属性中，输入以下设置：

   - **要升级到的版本**：选择要升级到的 Windows 10 版本。 将该策略针对的设备升级到所选版本。
   - **产品密钥**：输入从 Microsoft 接收的产品密钥。 创建包含产品密钥的策略后，无法更新该密钥，并出于安全原因隐藏该密钥。 要更改产品密钥，请再次输入完整密钥。
   - **许可证文件**：对于 Windows 10 Holographic for Business 或 Windows 10 移动版，请选择“浏览”以选择从 Microsoft 接收的许可证文件。 此许可证文件包含要将目标设备升级到的版本的许可证信息。

7. 选择“确定”，保存所做更改。 选择“创建”以创建配置文件。

## <a name="switch-out-of-s-mode"></a>切出 S 模式

[Windows 10 S 模式](https://support.microsoft.com/help/4456067/windows-10-switch-out-of-s-mode)旨在提高安全性和性能。 若设备仅运行来自 Microsoft Store 的应用，则可使用 S 模式帮助确保设备安全。 若设备需要 Microsoft Store 中不可用的应用，则切出 S 模式。 切出 S 模式是一种方法。 切出 S 模式后，无法返回 Windows 10 S 模式。

以下步骤说明如何在 Windows 10（1809 或更高版本）设备上创建控制 S 模式的配置文件。

1. 在 [Azure 门户](https://portal.azure.com)中，选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
2. 选择“设备配置” > “配置文件” > “创建配置文件”。
3. 输入配置文件的“名称”和“描述”。 例如，输入类似于 `Windows 10 switch off S mode` 的内容
4. 在“平台”中，选择“Windows 10 及更高版本”。
5. 在“配置文件类型”中，选择“版本升级”。
6. 选择“模式切换(仅 Windows 预览体验)”，然后设置“切出 S 模式”属性。 选项包括：

    - **无设置**：S 模式设备将保持 S 模式。 最终用户可将设备切出 S 模式。
    - **保持 S 模式**：禁止最终用户将设备切出 S 模式。
    - **切换**：将设备切出 S 模式。

7. 选择“确定”，保存所做更改。 选择“创建”以创建配置文件。

配置文件随即创建并在配置文件中列出。

## <a name="next-steps"></a>后续步骤

[分配此配置文件](device-profile-assign.md)到组。

>[!NOTE]
>如果稍后删除分配的策略，设备上的 Windows 版本将不会还原，并继续正常运行。
