---
title: 适用于 macOS 的 Microsoft Intune 设备限制设置
titlesuffix: ''
description: 了解可用于控制运行 macOS 的设备中设备设置和功能的 Intune 设置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 51b1df246c23f2e1571b3bccc3f4f26ae91e26dd
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52178346"
---
# <a name="microsoft-intune-macos-device-restriction-settings"></a>Microsoft Intune macOS 设备限制设置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文介绍可为运行 macOS 的设备配置的 Microsoft Intune 设备限制设置。

## <a name="password"></a>密码
-   **密码** - 需要最终用户输入密码才能访问设备。
    -   **所需密码类型** - 指定密码是否可以仅由数值组成，还是必须为字母数字（包含字母和数字）。 仅在 Mac OS X 10.10.3 及更高版本上支持此设置。
    -   **密码中的非字母数字字符数** - 指定密码中必须包含的复杂字符数（**0** 至 **4**）。<br>复杂字符是一个符号，例如“?”。
    -   **最短密码长度** - 输入用户必须配置的最短密码长度（介于 **4** 到 **16** 个字符之间）。
    -   **简单密码** - 允许使用简单密码，如 **0000** 或 **1234**。
    -   **要求提供密码前，屏幕锁定后的最大分钟数** - 指定在需要密码来进行解锁之前，计算机必须保持非活动状态的时间。
    -   **屏幕锁定前的最大非活动状态分钟数** - 指定锁定屏幕前，计算机必须处于空闲状态的时间长度。
    -   **密码过期（天数）** - 指定用户在多少天之后必须更改密码（**1** 到 **255** 天）。
    -   **防止重用以前的密码** - 指定以前用过的不能重复使用的密码数（**1** 到 **24**）。

## <a name="restricted-apps"></a>受限制的应用

在受限制的应用列表中，可以配置以下列表之一：

- **禁止的应用**列表 - 列出用户不得安装和运行的应用（未由 Intune 托管）。 不阻止用户安装已禁止的应用，但如果用户这样做，系统会向你报告。
- **批准的应用**列表 - 列出允许用户安装的应用。 用户不得安装未列出的应用。 自动允许由 Intune 托管的应用。 不阻止用户安装不在已批准列表的应用，但如果用户这样做，系统会向你报告。

若要配置列表，请单击“添加”，然后指定你选择的名称、应用发布者（可选）和该应用的捆绑 ID（例如 *com.apple.calculator*）。

## <a name="domains"></a>Domains

### <a name="unmarked-email-domains"></a>未标记的电子邮件域

在“电子邮件域 URL”字段中，向列表添加一个或多个 URL。 当用户从所配置的域以外的域接收电子邮件时，该电子邮件在 MacOS 邮件应用中被标记为不受信任。

