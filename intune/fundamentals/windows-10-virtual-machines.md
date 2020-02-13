---
title: 将 Windows 10 虚拟机与 Microsoft Intune 配合使用
titleSuffix: ''
description: 将 Windows 10 虚拟机与 Microsoft Intune 配合使用的准则
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 486ca7eae1b1e8b016f44c735ec04a23145421a8
ms.sourcegitcommit: e1ff157f692983b49bdd6e20cc9d0f93c3b3733c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124973"
---
# <a name="using-windows-10-virtual-machines-with-intune"></a>将 Windows 10 虚拟机与 Intune 配合使用

Intune 支持管理运行 Windows 10 企业版的虚拟机，但存在某些限制。 Intune 管理不依赖于或干扰同一虚拟机的 Windows 虚拟桌面管理。

使用 Intune 管理 Windows 10 VM 时，请记住以下几点：

## <a name="enrollment"></a>注册
- 建议不要使用 Intune 管理按需会话主机虚拟机。 在创建每个 VM 后都必须进行注册。 此外，定期删除 VM 会使孤立的设备记录保留在 Intune 中，直到它们[被清理](../remote-actions/devices-wipe.md#automatically-delete-devices-with-cleanup-rules)。 
- Windows Autopilot 自部署和白色手套部署类型不受支持，因为它们需要受信任的平台模块 (TPM) 实体。 
- 只能使用 RDP 访问的 VM（如托管在 Azure 上的 VM）不支持全新体验 (OOBE) 注册。 此限制意味着：
    - 不支持 Windows Autopilot 和商用 OOBE。
    - 不支持设备上下文策略的“注册状态页”选项。

## <a name="configuration"></a>配置
Intune 不支持任何利用受信任的平台模块或硬件管理的配置，包括：
- [BitLocker 设置](../configuration/device-profiles.md#endpoint-protection)
- [设备固件配置接口设置](../configuration/device-profiles.md#device-firmware-configuration-interface)

## <a name="reporting"></a>报表
Intune 会自动检测虚拟机，并将其报告为“设备” > “所有设备”>“选择设备”>“概述” > >“模型”字段中的“虚拟机”。 

已解除分配的虚拟机可能会导致不合规的设备报告，因为它们无法[使用 Intune 服务签入](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned)。

## <a name="retirement"></a>停用
如果只有 RDP 访问权限，请不要使用[擦除操作](../remote-actions/devices-wipe.md#wipe)。 擦除操作将删除虚拟机的 RDP 设置，并阻止再次连接。


