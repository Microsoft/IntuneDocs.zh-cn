---
title: 适用于 Windows Holographic for Business 的 Microsoft Intune 设备限制设置
titleSuffix: ''
description: 了解哪些 Intune 设置可用于控制运行 Windows Holographic for Business 的设备上的设备设置和功能。
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 694b81434a95f48abc98f5012460523420df58cc
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="microsoft-intune-windows-holographic-for-business-device-restriction-settings"></a>适用于 Windows Holographic for Business 的 Microsoft Intune 设备限制设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

运行 Windows Holographic for Business 的设备（如 Microsoft Hololens）支持以下设备限制设置。

## <a name="general"></a>常规

- **手动注销** - 允许用户手动从设备中删除工作区帐户。
- **Cortana** - 启用或禁用 Cortana 语音助手。
- **地理位置** - 指定设备是否可以使用位置服务信息。



## <a name="password"></a>Password
-   **密码** - 需要最终用户输入密码才能访问设备。
    -   **设备从空闲状态返回时需要输入密码** - 指定用户必须输入密码以解锁设备。



## <a name="app-store"></a>App Store

-   “自动更新应用商店的应用”- 允许自动更新从 Microsoft 应用商店安装的应用。
-   **受信任的应用安装** - 允许对使用受信任的证书签名的应用进行旁加载。
-   **开发人员解锁** - 允许 Windows 开发人员设置，如允许最终用户修改旁加载的应用。

## <a name="edge-browser"></a>Microsoft Edge 浏览器

-   **Microsoft Edge 浏览器** - 允许在设备上使用 Microsoft Edge Web 浏览器。
-   **Cookie** - 允许浏览器将 Internet Cookie 保存到设备。
-   **弹出窗口** - 阻止浏览器中的弹出窗口（仅适用于 Windows 10 桌面版）。
-   **搜索建议** - 允许搜索引擎在你键入搜索短语时建议站点。
-   **密码管理器** - 启用或禁用 Microsoft Edge 密码管理器功能。
- **发送 do-not-track 标头** - 配置 Microsoft Edge 浏览器，将“不跟踪”标头发送到用户访问的网站。

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen

- **Microsoft Edge SmartScreen** - 启用 Edge SmartScreen，以便访问网站和下载文件。

## <a name="search"></a>搜索
- **搜索位置** - 指定搜索是否可使用位置。 信息


## <a name="cloud-and-storage"></a>云和存储
-   **Microsoft 帐户** - 使用户可以将 Microsoft 帐户与设备关联。

## <a name="cellular-and-connectivity"></a>手机网络和连接性

-   **蓝牙** - 控制用户是否可以在设备上启用和配置蓝牙。
-   **蓝牙可发现性** - 允许其他已启用蓝牙的设备可发现此设备。
-   **蓝牙广告** - 允许设备通过蓝牙接收广告。

## <a name="control-panel-and-settings"></a>控制面板和设置

- **系统时间修改** - 阻止最终用户更改设备日期和时间。

## <a name="reporting-and-telemetry"></a>报告和遥测

- **共享使用情况数据** - 选择诊断数据提交级别。