---
title: 在 Windows 10 设备上升级版本或使用 S 模式 - Microsoft Intune - Azure | Microsoft Docs
description: 使用 Microsoft Intune 将 Windows 10 设备升级到其他版本，或切换 S 模式。 管理员可使用设备配置文件将 Windows 10 专业版升级到 Windows 10 企业版，并切出 S 模式。 请参阅支持的 Windows 10 专业版、N 版、教育版、云、企业版、核心版、全息版和移动版升级路径。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f5519429bae69fe277c72b12a2801a1875295824
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72493787"
---
# <a name="upgrade-windows-10-editions-or-switch-out-of-s-mode-on-devices-using-microsoft-intune"></a>使用 Microsoft Intune 在设备上升级 Windows 10 版本或切出 S 模式

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

作为移动设备管理 (MDM) 解决方案的一部分，不妨升级 Windows 10 设备。 例如，不妨将 Windows 10 专业版设备升级为 Windows 10 企业版。 或者，你希望设备切出 S 模式。

[Windows 10 S 模式](https://support.microsoft.com/help/4456067/windows-10-switch-out-of-s-mode)（打开另一个 Microsoft 网站）旨在实现安全性和性能。 你可以使用 Intune 切出 S 模式。 切出 S 模式是一种方法。 切出 S 模式后，无法返回 Windows 10 S 模式。

有关 S 模式，请参阅一些[常见问题](https://support.microsoft.com/help/4020089/windows-10-in-s-mode-faq)。

此功能适用于：

- Windows 10 及更高版本
- Windows 10 1809 或更高版本（适用于 S 模式）
- Windows Holographic for Business

这些功能在 Intune 中可用，并可供管理员进行配置。 Intune 使用“配置文件”创建和自定义这些设置，从而满足组织需求。 在配置文件中添加这些功能后，便能将此配置文件推送或部署到组织中的 Windows 10 设备。 在你部署此配置文件后，Intune 自动升级设备或切出 S 模式。

本文列出了支持的升级路径，并介绍了如何创建设备配置文件。 此外，还介绍了所有适用于 [Windows 10](edition-upgrade-windows-settings.md) 的升级设置和 S 模式设置。

> [!NOTE]
> 如果稍后撤消策略分配，设备上的 Windows 版本将不会还原。 设备将继续正常运行。

## <a name="prerequisites"></a>必备条件

升级设备前，请务必符合以下先决条件：

- 用于在该策略针对的所有设备上安装已更新 Windows 版本的有效产品密钥（适用于 Windows 10 桌面版）。 你可以使用多激活密钥 (MAK) 或密钥管理服务器 (KMS) 密钥。
- 对于 Windows 10 移动版和 Windows 10 全息版，可使用 Microsoft 许可证文件。 此许可证文件包含，在使用策略定目标到的所有设备上安装已更新版本所需的授权信息。
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

<!--The following table provides information about the supported upgrade paths for Windows 10 editions in this policy:

![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)  (X) = not supported    
![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)    (green checkmark) = supported    

|Upgrade from edition\Upgrade to edition|Education|Education N|Pro Education|Pro Education N|Enterprise|Enterprise N|Professional|Professional N|Mobile Enterprise|Holographic for Business|
|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|
|Pro|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Pro N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Pro Education|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Pro Education N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Cloud|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Cloud N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Enterprise|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Enterprise N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Core|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Core N|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Mobile|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|
|Holographic|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![unsupported](./media/edition-upgrade-configure-windows-10/x_blk.png)|![supported](./media/edition-upgrade-configure-windows-10/check_grn.png) -->

## <a name="create-the-profile"></a>创建配置文件

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“设备配置”   > “配置文件”   > “创建配置文件”  。
3. 输入以下属性：

    - **名称**：输入新配置文件的描述性名称。 例如，输入 `Windows 10 edition upgrade profile` 或 `Windows 10 switch off S mode` 等名称。
    - **说明**：输入配置文件的说明。 此设置是可选的，但建议进行。
    - **平台**：选择平台：  

        - **Windows 10 及更高版本**

    - **配置文件类型**：选择“版本升级”  。
    - **设置**：输入要配置的设置。 有关所有设置及其用途的列表，请参阅：

        - [Windows 10 升级和 S 模式](edition-upgrade-windows-settings.md)
        - [Windows Holographic for Business](holographic-upgrade.md)

4. 选择“确定”   > “创建”  以保存所做的更改。

此时，配置文件创建完成，并出现在列表中。 请务必[分配配置文件](device-profile-assign.md)，并[监视配置文件状态](device-profile-monitor.md)。

## <a name="next-steps"></a>后续步骤

创建配置文件后，即可进行分配。 下一步，[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

查看适用于 [Windows 10](edition-upgrade-windows-settings.md) 和 [Windows Holographic for Business](holographic-upgrade.md) 设备的升级设置和 S 模式设置。
