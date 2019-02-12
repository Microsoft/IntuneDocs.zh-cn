---
title: 升级到 Windows Holographic for Business
titleSuffix: Microsoft Intune
description: 了解如何将运行 Windows Holographic 的设备升级到 Windows Holographic for Business
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: bfca0cb5b02fdf77fa9a0bab42af05fd04b5c140
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55838880"
---
# <a name="upgrade-devices-running-windows-holographic-to-windows-holographic-for-business"></a>将运行 Windows Holographic 的设备升级到 Windows Holographic for Business

Microsoft Intune 包含许多有助于管理和保护设备的设置。 本文列出并介绍了用于将 Windows Holographic 设备升级为 Windows Holographic for Business 的设置。 这些设置是在 Intune 中的升级配置文件中创建，随后被推送或部署到设备。

作为移动设备管理 (MDM) 解决方案的一部分，请使用这些设置升级 Windows Holographic 设备。 对于 Microsoft HoloLens，可以通过购买商业套件来获得升级所需的许可证。 有关详细信息，请参阅[解锁 Windows Holographic for Business 功能](https://docs.microsoft.com/hololens/hololens-upgrade-enterprise)。

若要详细了解此功能，请参阅[升级 Windows 10 版本或启用 S 模式](edition-upgrade-configure-windows-10.md)。

## <a name="before-you-begin"></a>在开始之前

[创建设备配置文件](edition-upgrade-configure-windows-10.md#create-the-profile)。

## <a name="edition-upgrade"></a>版本升级

- **要升级到的版本**：选择“Windows 10 Holographic for Business”。
- **许可证文件**：转到并选择系统提供的 XML 许可证文件。

  ![输入包含 Holographic for Business 许可证信息的 XML 文件名](media/Holographic-edition-upgrade.png)
 
## <a name="next-steps"></a>后续步骤

此时，配置文件创建完成，但它可能尚未执行任何操作。 请务必[分配配置文件](device-profile-assign.md)，并[监视配置文件状态](device-profile-monitor.md)。

还可以为 [Windows 10 及更高版本](edition-upgrade-windows-settings.md)设备创建版本升级配置文件。
