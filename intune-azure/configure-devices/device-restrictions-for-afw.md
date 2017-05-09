---
title: "适用于 Android for Work 的 Intune 设备限制设置"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：了解可用于控制 Android for Work 设备上的设备设置和功能的 Intune 设置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1830720b-16cb-4f2f-a71a-62967f882563
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 03fec9d22e705ccb27f4eb1f8f82c7ace95e841e
ms.openlocfilehash: c5cff131e7bcedadbad42fe6ab8bf00017f933ff
ms.contentlocale: zh-cn
ms.lasthandoff: 04/26/2017


---

# <a name="android-for-work-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune 中的 Android for Work 设备限制设置

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="work-profile-settings"></a>工作配置文件设置
-     工作和个人配置文件之间的数据共享 - 使用此设置可控制工作配置文件中的应用能否与个人配置文件中的应用共享数据。 选择：
    - 默认共享限制 - 这是设备的默认共享行为，因运行的 Android 版本而异。 默认情况下，允许从个人配置文件向工作配置文件共享数据。 默认情况下，也会阻止工作配置文件和个人配置文件之间的数据共享。 这样可以防止从工作配置文件向个人配置文件共享数据时发生数据泄漏。 在版本低于 6.0 的设备上，Google 未提供阻止从个人配置文件向工作配置文件共享数据的方法。  
    - 工作配置文件中的应用可以处理个人配置文件发出的共享请求 - 使用此选项可以启用允许从个人配置文件向工作配置文件共享数据的内置 Android 功能。 启用此功能后，工作配置文件中的应用可以处理个人配置文件中的应用发出的共享请求。 这是版本低于 6.0 的 Android 设备的默认行为。
    - 个人配置文件中的应用可以处理工作配置文件发出的共享请求 - 允许跨工作配置文件边界进行双向共享。 选择此设置后，工作配置文件中的应用可以与个人配置文件中的非托管应用共享数据。  请谨慎使用此设置，因为这会允许将工作配置文件中的托管数据传输到设备的非托管端。


-     设备锁定时显示的工作配置文件通知 - 控制工作配置文件中的应用能否在设备锁定时显示屏幕通知。
-     默认应用权限 - 设置适用于工作配置文件中所有应用的默认权限策略。 自 Android 6 起，将在运行时向最终用户提示授予应用所需的一些权限。 使用此策略设置，可以确定如何或是否提示用户授予工作配置文件中的应用所需的权限。
例如，将应用推送到要求访问位置的工作配置文件。 此应用通常会向用户弹出对话框，询问其是否要向此应用授予位置访问权限，用户可以批准或拒绝。 使用此策略，可以确定所有权限是否都应不经提示自动授予、不经提示自动拒绝还是都应由最终用户自行决定。 选择：
    -     设备默认值
    -     提示
    -     自动授予
    -     自动拒绝

## <a name="password"></a>Password

- 最短密码长度 - 输入用户密码至少必须包含的字符数（介于 **4**-**14** 之间）
- 屏幕锁定前的最长闲置分钟数 - 选择设备在闲置多长时间后自动锁定。
- 擦除设备前的登录失败次数 - 输入在输入密码不正确多少次后擦除设备中的所有数据。
- 密码到期(天) - 输入多少天后最终用户必须更改密码（介于 **1**-**255** 之间）。
- 所需的密码类型 - 选择必须在设备上设置的密码类型。 选择：
    - 设备默认值
    - 低安全性生物识别
    - **必需**
    - 至少为数字
    - 复杂数字 -（不允许使用重复或连续数字，如“1111”或“1234”）
    - 至少为字母
    - 至少为字母数字
    - 至少为字母数字与符号
- 防止重用以前的密码 - 输入必须使用多少个新密码后才能重用旧密码（介于 **1**-**24** 之间）。
- 指纹解锁 - 防止最终用户使用设备指纹扫描仪解锁设备。
- Smart Lock 和其他信任代理 - 可用于控制兼容设备上的 Smart Lock 功能。 使用此手机功能（有时称为“信任代理”），可以在设备处于可信位置时（例如，当设备与特定蓝牙设备相连或在 NFC 标记附近时）禁用或绕过设备锁屏界面密码。此设置可用于防止用户配置 Smart Lock。

## <a name="custom-policy-settings"></a>自定义策略设置
使用 Microsoft Intune **Android for Work 自定义配置策略**可以部署用于控制 Android for Work 设备上功能的 OMA-URI 设置。 这些设置是许多移动设备制造商用来控制设备功能的标准设置。

此功能旨在方便你部署无法通过 Intune 策略配置的 Android 设置。
目前，Intune 支持的 Android 自定义策略数量有限。 请参阅本主题中的示例，了解可以配置哪些策略。

### <a name="general-settings"></a>常规设置

|设置名|详细信息|
    |----------------|--------------------|
    |**Name** |输入 Android 自定义策略的唯一名称，以帮助你在 Intune 控制台中识别它。|
    |**描述** |提供对 Android 自定义策略的概述以及可帮助你查找它的其他相关信息。|

### <a name="oma-uri-settings"></a>OMA-URI 设置

  |设置名|详细信息|
  |--------|--------------------|
  |**Name** |输入 OMA-URI 设置的唯一名称，以帮助你在设置列表中识别它。|
  |**描述** |提供对设置进行概述的说明以及帮助你找到该设置的其他相关信息。|
    |OMA-URI (区分大小写) |指定需为其提供设置的 OMA-URI。|
  |数据类型 |选择指定此 OMA-URI 设置时使用的数据类型。 可从“字符串”、“字符串(XML)”、“日期和时间”、“整数”、“浮点”或“布尔”中进行选择。|
  |**值** |指定要与之前指定的 OMA-URI 关联的值。|

