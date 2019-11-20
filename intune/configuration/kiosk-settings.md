---
title: Microsoft Intune 中适用于 Windows 和 Holographic 设备的展台设置 - Azure | Microsoft Docs
description: 使用 Microsoft Intune 将 Windows 10（及更高版本）和 Windows Holographic for Business 设备配置为单应用和多应用展台、自定义开始菜单、添加应用、显示任务栏，以及配置 Web 浏览器。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: b2dede228aadac2981c38d2842f5da1369933f86
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059873"
---
# <a name="windows-10-and-windows-holographic-for-business-device-settings-to-run-as-a-dedicated-kiosk-using-intune"></a>使用 Intune 将 Windows 10 和 Windows Holographic for Business 设备作为专用展台运行的设置

在 Windows 10 设备上，使用 Intune 将设备作为展台（有时也称为专用设备）运行。 展台模式下的设备可以运行一个应用，也可以运行多个应用。 可以显示和自定义开始菜单、添加不同的应用（包括 Win32 应用）、向 Web 浏览器添加特定主页等。 

此功能适用于运行以下程序的设备：

- Windows 10 及更高版本
- Windows Holographic for Business

Intune 支持每台设备一个展台配置文件。 如果在单台设备上需要多个展台配置文件，可以使用[自定义 OMA-URI](custom-settings-windows-10.md)。

Intune 使用“配置文件”创建和自定义这些设置，从而满足组织需求。 在配置文件中添加这些功能后，将这些设置推送或部署到组织中的组。

本文介绍了如何创建设备配置文件。 有关所有设置及其用途的列表，请参阅 [Windows 10 展台设置](kiosk-settings-windows.md)和 [Windows Holographic for Business 展台设置](kiosk-settings-holographic.md)。

## <a name="create-the-profile"></a>创建配置文件

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“设备”   > “配置文件”   > “创建配置文件”  。
3. 输入以下属性：

   - **名称**：输入新配置文件的描述性名称。
   - **说明**：输入配置文件的说明。 此设置是可选的，但建议进行。
   - **平台**：选择“Windows 10 及更高版本” 
   - **配置文件类型**：选择“展台” 

4. 选择“设置”  中的“展台模式”  。 “展台模式”标识策略支持的展台模式类型  。 选项包括：

    - **未配置**（默认）：策略不会启用展台模式。
    - **单个应用、全屏展台**：设备以单个用户帐户的身份运行，并锁定到单个应用商店应用。 所以，用户登录时，将启动一个特定应用。 此模式还会限制用户打开新应用或更改正在运行的应用。
    - **多应用展台**：设备通过使用应用程序用户模型 ID (AUMID) 运行多个应用商店应用、Win32 应用或收件箱 Windows 应用。 设备上仅可使用你添加的应用。

        多应用展台或固定目标设备的优势在于，让用户仅访问其所需应用，提供易于理解的体验。 同时从其视图中删除他们不需要的应用。

    有关所有设置及其用途的列表，请参阅：
      - [Windows 10 展台设置](kiosk-settings-windows.md)
      - [Windows Holographic for Business 展台设置](kiosk-settings-holographic.md)

5. 完成后，选择“确定”   > “创建”  以保存所做的更改。

此时，配置文件创建完成，并出现在配置文件列表中。 下一步是[分配](device-profile-assign.md)配置文件。

## <a name="next-steps"></a>后续步骤

[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。

可以为运行下列平台的设备创建展台配置文件：
- [Android](device-restrictions-android.md#kiosk)
- [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings)
- [Windows 10 及更高版本](kiosk-settings-windows.md)
- [Windows Holographic for Business](kiosk-settings-holographic.md)
