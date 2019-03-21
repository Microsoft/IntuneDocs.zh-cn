---
title: 开启 Windows Defender | Microsoft Docs
description: 了解如何打开 Windows Defender 以访问公司资源。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/08/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d16dd2de-3ed5-474f-a04b-36dcd350162c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: shburbid
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8d51e9db367925442c7b6c735b1de86891e05856
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "55845272"
---
# <a name="turn-on-windows-defender-to-access-company-resources"></a>打开 Windows Defender 以访问公司资源

你的单位或学校希望确保访问其资源的设备受到保护。 他们有多种可使用 [Windows Defender](https://www.microsoft.com/safety/pc-security/windows-defender.aspx)（Windows 的针对恶意软件的内置保护）的方式。

若要修复任何访问问题，可能需要更改 Windows Defender 中的某些设置。 这些步骤可能需要在计算机的不同位置进行操作。

## <a name="turn-on-windows-defender"></a>打开 Windows Defender

1. 在“开始”中，打开“控制面板”。
2. 打开“管理工具” > “编辑组策略”。 这将在一个新窗口中打开“本地组策略编辑器”。
3. 打开“计算机配置” > “管理模板” > “Windows 组件” > “Windows Defender 防病毒”。 “关闭 Windows Defender 防病毒”设置位于其他设置文件夹下方。 
4. 打开“关闭 Windows Defender 防病毒”，并确保将其设置为“禁用”或“未配置”。

## <a name="turn-on-real-time-protection"></a>启用实时保护

要确保实时保护已开启，请转到“开始”并搜索“Windows Defender 安全中心”以进行检查。 选择“病毒和威胁防护设置”，并确认“实时保护”和“云提供的保护”都已切换到“开”。 如果未显示这些选项，请执行以下操作启用它们：

1. 在“开始”中，打开“控制面板”。
2. 打开“管理工具” > “编辑组策略”。 这将在一个新窗口中打开“本地组策略编辑器”。
3. 打开“计算机配置” > “管理模板” > “Windows 组件” > “Windows Defender 安全中心” > “病毒和威胁防护”。
4. 打开“病毒和威胁防护区域”设置，并将其设置为“禁用”。

## <a name="update-your-antivirus-definitions"></a>更新防病毒定义

要确保防病毒定义是最新的，请转到“开始”并搜索“Windows Defender 安全中心”以进行检查。 选择“保护更新”和“检查更新”，确保设备针对病毒具有最新保护。 如果未显示此选项，请按照[启用实时保护](turn-on-defender-windows.md#turn-on-real-time-protection)中的步骤进行操作

仍需帮助？ 请与公司支持人员联系。 有关他们的联系信息，请查看[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)。
