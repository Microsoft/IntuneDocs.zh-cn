---
title: 使用 Microsoft Intune 重命名设备 - Azure | Microsoft Docs
description: 使用 Microsoft Intune 重命名设备。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b286e095613c56f2d6fdfa5a2cf2cd1398611f12
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/28/2020
ms.locfileid: "77781834"
---
# <a name="rename-a-device-in-intune"></a>在 Intune 中重命名设备

 通过“重命名设备”操作可以重命名在 Intune 中注册的设备。 设备的名称将在 Intune 和设备中更改。

可以重命名下列类型的设备：
- 公司拥有的 Windows 
- 受监督的 iOS/iPadOS
- 公司拥有的 MacOS 10

此功能暂不支持重命名混合 Azure AD Windows 设备。

## <a name="rename-a-device"></a>重命名设备

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
3. 选择“设备” > “所有设备”> 选择设备 >“…” > “重命名设备”     。
4. 在“重命名设备”  边栏选项卡的文本框中键入新名称。 可以使用字母、数字及连字符。 名称必须至少包含一个字母或连字符。
5. 如果要在重命名设备后重新启动该设备，请选择“重命名后重新启动”旁边的“是”   。
6. 选择“重命名”  。

## <a name="windows-device-rename-rules"></a>Windows 设备重命名规则
重命名 Windows 设备时，新名称必须遵循以下规则：
- 小于或等于 15 个字符（必须小于或等于 63 个字节，不包括尾随 NULL）
- 非 Null 或空字符串
- 允许的 ASCII：字母（a-z、A-Z），数字 (0-9) 和连字符
- 允许的 Unicode：0x80 及以后的字符，必须是有效的 UTF8，必须是可映射到 IDN（即 RtlIdnToNameprepUnicode 成功；请参阅 RFC 3492）
- 名称不得只包含数字
- 名称中不能包含空格
- 不允许的字符：{ | } ~ [ \ ] ^ ' : ; < = > ? & @ ! " # $ % ` ( ) + / , . _ *)


## <a name="next-steps"></a>后续步骤

若要查看“重命名”设备操作的状态  ，请查看设备的“概述”  页。
