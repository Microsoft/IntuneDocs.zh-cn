---
title: Android 用户如何获取其应用
description: 使 Android 应用可供最终用户使用的方法
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/21/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 878e4d0854722d82eab0545cf3a1ba743f2c52db
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
ms.locfileid: "31023132"
---
# <a name="how-your-android-users-get-their-apps"></a>Android 用户如何获取其应用

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

使用此信息可了解 Android 最终用户如何以及在何处获取你通过 Microsoft Intune 分发的应用。 该信息可能因设备类型（本机 Android 设备或 Samsung Knox 标准版设备）而异。

## <a name="native-non-samsung-knox-standard-android-devices"></a>本机（非 Samsung Knox 标准）Android 设备

| 应用类型 | 业务线 (LOB) 应用 | Play Store 应用  |
| ------------- |-------------| -----|
| 可用应用      | 用户在公司门户中点击“**安装**”。 此时将出现一条通知，用户需要点击该通知以开始安装。 安装成功后，通知即会消失。 | 用户在公司门户中点击应用，并转到 Play Store中的应用页，他们可以在那里开始安装。|
| Required apps      | 用户将看到一条通知（用户无法关闭此通知），指示他们需要安装应用。 用户点击通知以开始安装。 安装成功后，通知即会消失。    | 用户将看到一条通知（用户无法关闭此通知），指示他们需要安装应用。 用户点击该通知，并转到 Play Store 中的应用页，他们可以在那里开始安装。 安装成功后，通知即会消失。 |

最终用户需要允许来自未知源的安装才能安装 [LOB 应用](lob-apps-android.md)。 这些应用通常位于两个位置：

* Android 7.1.2 及更低版本：“设置” > “安全性” > “未知源”
* Android 8.0 及更高版本：“设置” > “应用和通知” > “特殊应用访问” > “安装未知应用” > “公司门户” > “允许来自此源”

在这种情况下，公司门户应用将通知最终用户，并将最终用户直接引导至相应设置。 


## <a name="samsung-knox-standard-android-devices"></a>Samsung Knox 标准版 Android 设备

| 应用类型 | 业务线 (LOB) 应用 | Play Store 应用  |
| ------------- |-------------| -----|
| 可用应用      | 用户在公司门户中点击“**安装**”。 应用安装无需进一步的用户干预。 | 用户在公司门户中点击应用，并转到 Play Store中的应用页，他们可以在那里开始安装。|
| Required apps      | 应用安装无需任何用户干预。    | 用户将看到一条通知（用户无法关闭此通知），指示他们需要安装应用。 用户点击该通知，并转到 Play Store 中的应用页，他们可以在那里开始安装。 安装成功后，通知即会消失。 |

应用可以是托管应用，也可以是非托管应用，如下所述。 托管应用的过程对于所有类型的 Android 设备都是相同的。

**托管应用** - 这些是可以通过策略管理的应用。 它们已由 Intune“包装”或通过 Intune App SDK 生成。 这些应用可以由 Intune 进行管理，应用程序策略可以应用于它们。

**非托管应用** - 这些是无法通过策略管理的应用。 它们未由 Intune 包装或不包含 Intune App SDK。 应用程序策略不能应用于这些应用。

### <a name="see-also"></a>另请参阅
[使用 Microsoft Intune 添加应用](apps-add.md)

[iOS 用户如何获取其应用](end-user-apps-ios.md)

[Windows 用户如何获取其应用](end-user-apps-windows.md)
