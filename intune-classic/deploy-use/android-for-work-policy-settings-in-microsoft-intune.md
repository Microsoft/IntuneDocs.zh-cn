---
title: "Android for Work 策略设置"
description: "创建控制通过 Intune 管理的 Android for Work 设备上的设置及功能的策略。"
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 02/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 35a53076-74d6-486d-b201-e0da2e170008
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0938e4b788ef11a773854531f570e63809389fad
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/12/2017
---
# <a name="android-for-work-policy-settings-in-microsoft-intune"></a>Microsoft Intune 中的 Android for Work 策略设置

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune 提供了一系列内置常规设置，你可以在 [Android for Work 设备](android-for-work.md)上进行配置。

## <a name="general-configuration-policy"></a>常规配置策略

使用 Intune **Android for Work 常规配置策略**可为 Android for Work 设备配置安全性和工作配置文件设置。

如果你寻找的设置没有在本主题中出现，你可能能够使用 Android 自定义策略创建它，该自定义策略允许你使用 OMA-URI 设置来控制设备。 有关详细信息，请参阅本主题后面的“[自定义策略设置](#custom-policy-settings)”。

> [!TIP]
> 设置工作配置文件时，设备会自动进行加密。 无法更改此设置。

### <a name="password-settings"></a>密码设置

|设置名|详细信息|
|----------------|-|
|**需要密码才可解锁移动设备**|指定在托管设备上是否需要密码。 选择：<br><br>- **复杂** - 至少需要一个字母、数字和符号<br>- **字母数字** - 至少需要一个数字和一个字母字符<br>- **字母** - 至少需要字母或符号<br>- **复杂数字** - 需要不重复或连续的数字字符<br>- **数字**<br><br>如果未启用此设置，则没有复杂性要求。|
|**最短密码长度**|指定密码中所需的最少字符或数字数。|
|**设备锁定之前须经历的不活动分钟数**|指定设备自动锁定之前没有进行用户活动的分钟数。|
|**允许 Smart Lock 和其他信任代理**<br>（Android 6 及更高版本）|让你控制兼容 Android 设备上的 Smart Lock 功能。 如果设备处于可信位置（例如当它连接到特定蓝牙设备时，或者在 NFC 标记附近时），则此手机功能（有时称为信任代理）使你可以禁用或绕过设备锁屏界面密码。可以使用此设置防止用户配置 Smart Lock。|
|**删除工作配置文件之前的重复登录失败次数**|指定在删除设备上的工作配置文件之前允许的登录失败次数。 这不会执行完整设备擦除。|
|**记住密码历史记录**|防止重复使用以前用过的密码。|
|**“记住密码历史记录”** - **“防止重用以前的密码”**|指定要记住的以前所用密码的数量。|
|**密码过期（天数）**|指定必须更改设备密码前的天数。|
|**允许指纹解锁**<br>（Android 6 及更高版本）|允许使用指纹解锁具有此功能的设备。|


### <a name="work-profile-settings"></a>工作配置文件设置

|设置名|详细信息|
|----------------|-|
|**允许在工作和个人配置文件之间共享数据**|允许工作配置文件中的应用与用户个人配置文件中的应用共享数据。 选择：<br><br>- **阻止任何跨边界的共享**<br>- **工作配置文件中的应用可处理来自个人配置文件的共享请求**<br>- **无共享限制**|
|**设备锁定时隐藏工作配置文件通知**<br>（Android 6 及更高版本）|控制是否在设备锁定时显示来自工作配置文件的任何通知。|
|**设置默认应用权限策略**<br>（Android 6 及更高版本）|为工作配置文件中的所有应用设置默认权限策略。 自 Android 6 起，系统在运行时将向最终用户提示应用所需的一些权限。  此策略设置可让 IT 部门决定：用户是否会收到以及以何种方式收到为工作配置文件中的应用授予权限的提示。 <br/><br/>例如，IT 可能将应用推送到需要位置访问权限的工作配置文件。  通常，应用将弹出一个对话框，询问用户是否要授予应用的位置访问权限，用户可允许也可拒绝。  此策略使 IT 部门能决定：在无提示的情况下自动授予所有权限、在无提示的情况下自动拒绝，还是让最终用户决定。|


## <a name="custom-policy-settings"></a>自定义策略设置
使用 Microsoft Intune 的 **Android for Work 自定义配置策略**来部署可用于控制 Android for Work 设备功能的 OMA URI 设置。 这些设置是许多移动设备制造商用来控制设备功能的标准设置。

此功能旨在使你能够部署不能使用 Intune 策略配置的 Android 设置。
Intune 目前支持有限数量的 Android 自定义策略。 请参阅本主题的示例，查找可配置的策略。

### <a name="general-settings"></a>常规设置

|设置名|详细信息|
    |----------------|--------------------|
    |**Name**|输入 Android 自定义策略的唯一名称，以帮助你在 Intune 控制台中识别它。|
    |**描述**|提供对 Android 自定义策略的概述以及可帮助你查找它的其他相关信息。|

### <a name="oma-uri-settings"></a>OMA-URI 设置

   |设置名|详细信息|
    |--------|--------------------|
    |**设置名称**|输入 OMA-URI 设置的唯一名称，以帮助你在设置列表中识别它。|
    |**设置描述**|提供对设置进行概述的说明以及帮助你找到该设置的其他相关信息。|
    |**数据类型**|选择将在其中指定此 OMA-URI 设置的日期类型。 从“字符串、字符串 (XML)、日期和时间、整数、浮点”，或者“布尔值”中进行选择。|
    |**OMA-URI（区分大小写）**|指定需为其提供设置的 OMA-URI。|
    |**值**|指定要与之前指定的 OMA-URI 关联的值。|

### <a name="examples"></a>示例

- [创建具有预共享密钥的 Wi-Fi 配置文件](pre-shared-key-wi-fi-profile.md)
- [使用自定义策略创建适用于 Android 设备的 per-app VPN 配置文件](per-app-vpn-for-android-pulse-secure.md)

### <a name="see-also"></a>另请参阅
[使用 Microsoft Intune 策略管理设备上的设置和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
