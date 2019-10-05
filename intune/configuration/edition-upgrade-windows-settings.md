---
title: Microsoft Intune 中的 Windows 10 升级设置和 S 模式设置 - Azure | Microsoft Docs
description: 查看在设备上使用 Microsoft Intune 中的设备配置文件升级 Windows 10 版本或启用 S 模式时所有设置及其用途的列表。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c34f683bfd16362dfb9af9a69c6f7d9b04860c7
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734760"
---
# <a name="windows-10-and-newer-device-settings-to-upgrade-editions-or-enable-s-mode-in-intune"></a>Intune 中用于升级版本或启用 S 模式的 Windows 10（及更高版本）设备设置

Microsoft Intune 包含许多有助于管理和保护设备的设置。 本文列出并介绍了用于在 Windows 10 设备上升级版本或启用 S 模式的设置。 这些设置是在 Intune 中的升级配置文件中创建，随后被推送或部署到设备。

作为移动设备管理 (MDM) 解决方案的一部分，请使用这些设置控制 Windows 10 设备的版本选项和 S 模式选项。

若要详细了解此功能，请参阅[升级 Windows 10 版本或启用 S 模式](edition-upgrade-configure-windows-10.md)。

## <a name="before-you-begin"></a>在开始之前

[创建配置文件](edition-upgrade-configure-windows-10.md#create-the-profile)。

## <a name="edition-upgrade"></a>版本升级

- **要升级到的版本**：选择要升级到的 Windows 10 版本。 将该策略针对的设备升级到所选版本。
- **产品密钥**：输入从 Microsoft 接收的产品密钥。 创建包含产品密钥的策略后，无法更新该密钥，并出于安全原因隐藏该密钥。 要更改产品密钥，请再次输入完整密钥。
- **许可证文件**：对于 Windows 10 Holographic for Business 或 Windows 10 移动版，请选择“浏览”以选择从 Microsoft 接收的许可证文件    。 此许可证文件包含要将设备升级到的版本的许可证信息。

## <a name="mode-switch"></a>模式切换

- **无设置**：S 模式设备保持 S 模式。 最终用户可将设备切出 S 模式。
- **保持 S 模式**：禁止最终用户将设备切出 S 模式。
- **切换**：将设备切出 S 模式。

## <a name="next-steps"></a>后续步骤

此时，配置文件创建完成，但它可能尚未执行任何操作。 请务必[分配配置文件](device-profile-assign.md)，并[监视配置文件状态](device-profile-monitor.md)。

还可以为 [Windows Holographic for Business](holographic-upgrade.md) 设备创建版本升级配置文件。
