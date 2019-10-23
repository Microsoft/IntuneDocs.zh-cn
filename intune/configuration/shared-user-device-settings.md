---
title: Microsoft Intune 中的共享或多用户设备设置 - Azure | Microsoft Docs
description: 添加并使用由 Microsoft Intune 中多个用户共享或使用的 Windows 10 和 Windows Holographic for Business 设备。 查看所有设置的列表以及这些设置对设备（包括 Microsoft HoloLens）的效果。 控制来宾帐户、管理帐户和删除非活动帐户、允许或阻止保存到本地存储、设置电源和睡眠选项、选择安装更新的时间，并在设备配置文件的教育环境中使用设备。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: b8dfab31d770c012acf88eb3775313634c3c14cc
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72492296"
---
# <a name="control-access-accounts-and-power-features-on-shared-pc-or-multi-user-devices-using-intune"></a>使用 Intune 控制共享电脑或多用户设备上的访问权限、帐户和电源功能

具有多个用户的设备称为共享设备，是移动设备管理 (MDM) 解决方案的常见部分。 使用 Microsoft Intune，可以自定义运行以下平台的共享设备：

- Windows 10 专业版和更高版本
- Windows 10 企业版和更高版本
- Windows Holographic for Business，例如 HoloLens

例如，学校拥有许多通常由学生使用的设备。 使用此设置，学校 Intune 管理员可启用共享电脑功能，一次允许一个用户。 学生在设备上不能在不同登录帐户之间切换。 如果学生注销，你还可以选择删除所有用户特定的设置。

最终用户可以使用来宾帐户登录到这些共享设备。 用户登录后，系统会缓存凭据。 最终用户使用设备时，只能访问你允许访问的功能。 例如，你可以进行如下设置：选择设备何时进入睡眠模式，用户是否可以在本地查看和保存文件，启用或禁用电源管理设置等。 此外，还可控制用户注销时是否删除来宾帐户，或达到阈值时是否删除非活动帐户。

本文介绍如何创建配置文件，并包括指向可用设置及其说明的链接。

在 Intune 中创建配置文件时，可以将配置文件部署或分配到贵组织中的设备组。 还可以将此配置文件分配给具有混合设备类型和操作系统 (OS) 版本的设备组。

## <a name="create-the-profile"></a>创建配置文件

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“设备配置”   > “配置文件”   > “创建配置文件”  。
3. 输入以下属性：

   - **名称**：输入新配置文件的描述性名称。
   - **说明**：输入配置文件的说明。 此设置是可选的，但建议进行。
   - **平台**：选择“Windows 10 及更高版本”  。
   - **配置文件类型**：选择“共享的多用户设备”  。

4. 配置 [Windows 10 及更高版本](shared-user-device-settings-windows.md)和 [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md) 的设置。

5. 选择“确定”   > “创建”  以保存所做的更改。

配置文件已创建并在列表中显示，但它尚未起到任何作用。 请务必向组织中的设备组[分配配置文件](device-profile-assign.md)。

## <a name="next-steps"></a>后续步骤

- 请参阅 [Windows 10 及更高版本](shared-user-device-settings-windows.md)和 [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md) 的所有设置。
- [分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。
