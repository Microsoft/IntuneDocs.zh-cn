---
title: 发现的应用
titleSuffix: Microsoft Intune
description: 了解有关 Intune 在设备上发现的被检测到的应用的详细信息。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 07dd262f-13e7-4cb2-9cc2-b755d1c276cf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 53555a01899cfec15c319e790620b2bfeaa302bc
ms.sourcegitcommit: 948ff8f56639e6dc7091134a0efd8d44efca63f2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2019
ms.locfileid: "68590904"
---
# <a name="intune-discovered-apps"></a>Intune 发现的应用

Intune 发现的应用是租户中在 Intune 注册相关设备上检测到的应用的列表  。 它充当租户的软件清单。 发现的应用是[应用安装](apps-monitor.md)报表中的单独报表  。 对于个人设备，Intune 从不收集有关非管理应用程序的信息。 在公司设备上，任何应用无论是否为受管理应用，此报表都将收集其相关信息。 下面是映射预期行为的表。 通常，报表从注册时间起每隔 7 天刷新一次（不是整个租户每周刷新一次）。 此刷新周期的唯一例外是通过 Win32 应用的 Intune 管理扩展收集的应用程序信息，该信息每隔 24 小时收集一次。

## <a name="monitor-discovered-apps-with-intune"></a>使用 Intune 监视发现的应用

Intune 提供有关在租户的 Intune 注册设备上检测到的应用的聚合列表。

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 在“Intune”窗格中，选择“客户端应用” > “发现的应用”    。

>[!NOTE]
>从“发现的应用”边栏选项卡中选择“导出”，可以将发现的应用列表导出为 .csv 文件   。
>
>对于发现的 Win32 应用，当前没有聚合计数。 此类数据只能在每台设备上查看。

Intune 还提供租户中单个设备的已发现应用的列表。 

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 在“Intune”窗格中，选择“设备” > “所有设备”   。
3. 选择设备。
4. 要查看此设备的检测到的应用，请在“监视器”部分中选择“已发现的应用”   。 

## <a name="details-of-discovered-apps"></a>发现的应用的详细信息

以下列表提供了应用平台类型、针对个人设备监视的应用、针对公司拥有的设备监视的应用以及刷新周期。 如需深入了解 Intune 支持的应用类型，请参阅 [Microsoft Intune 中的应用类型](apps-add.md#app-types-in-microsoft-intune)。

| 平台 | 个人拥有的设备 | 公司拥有的设备 | 刷新周期 |
|------------------------------------------------------------------------|----------------------------------|--------------------------------------------------|---------------------------------------|
| Windows 10（Win32 应用）注意事项：[必须在设备上安装 Intune 管理扩展](intune-management-extension.md) | 不适用 | “添加删除程序”列表中的所有 Win32 应用 | 自设备注册时间起每隔 24 小时刷新一次 |
| Windows 10（现代应用） | 仅限托管现代应用 | 设备上安装的所有现代应用 | 自设备注册时间起每隔 7 天刷新一次 |
| Windows 8.1 | 仅托管应用 | 仅托管应用 | 自设备注册时间起每隔 7 天刷新一次 |
| Windows Phone 8 | 仅托管应用 | 仅托管应用 | 自设备注册时间起每隔 7 天刷新一次 |
| Windows RT | 仅托管应用 | 仅托管应用 | 自设备注册时间起每隔 7 天刷新一次 |
| iOS | 仅托管应用 | 设备上安装的所有应用 | 自设备注册时间起每隔 7 天刷新一次 |
| macOS | 设备上安装的所有应用 | 设备上安装的所有应用 | 自设备注册时间起每隔 7 天刷新一次 |
| Android | 仅托管应用 | 设备上安装的所有应用 | 自设备注册时间起每隔 7 天刷新一次 |
| Android Enterprise | 仅托管应用 | 仅工作配置文件中安装的应用 | 自设备注册时间起每隔 7 天刷新一次 |

发现的应用数可能与应用安装状态计数不一致。 导致不一致的可能原因包括：
- 已安装的托管应用的定位更改可能会导致状态边栏选项卡中的安装计数减少，但仍会在检测到的应用中报告。
- 由于用户或设备可能重叠，在租户中定位同一应用的多个实例将导致不同的计数。 应用的每个实例都会计算重叠用户，但发现的应用将会有重复计数。
- 发现的应用和应用状态会以不同的时间间隔收集，这可能会导致应用计数出现差异。

## <a name="next-steps"></a>后续步骤

- [Microsoft Intune 中的应用类型](apps-add.md#app-types-in-microsoft-intune)
- [使用 Microsoft Intune 监视应用信息和分配](apps-monitor.md)
