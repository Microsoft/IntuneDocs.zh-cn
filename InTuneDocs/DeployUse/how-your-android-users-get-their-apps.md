---
title: "Android 用户如何获取其应用 | Microsoft Intune"
description: "使 Android 应用可供最终用户使用的方法"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 7/7/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 738b6bedcefbfd8bf0fa7bde5b86c79293af527e
ms.openlocfilehash: 64b42d25815946122d0be0d031ab7cc4b3ac6a8a


---


# <a name="how-your-android-users-get-their-apps"></a>Android 用户如何获取其应用
使用此信息可了解 Android 最终用户如何以及在何处获取你通过 Microsoft Intune 分发的应用。 该信息可能因设备类型（本机 Android 设备或 Samsung Knox 标准版设备）而异。

## <a name="native-nonsamsung-knox-android-devices"></a>本机（非 Samsung Knox）Android 设备

| 应用类型 | 业务线 (LOB) 应用 | Play Store 应用  |
| ------------- |-------------| -----|
| 可用应用      | 用户在公司门户中点击“**安装**”。 此时将出现一条通知，用户需要点击该通知以开始安装。 安装成功后，通知即会消失。 | 用户在公司门户中点击应用，并转到 Play Store中的应用页，他们可以在那里开始安装。|
| Required apps      | 用户将看到一条通知（用户无法关闭此通知），指示他们需要安装应用。 用户点击通知以开始安装。 安装成功后，通知即会消失。    | 用户将看到一条通知（用户无法关闭此通知），指示他们需要安装应用。 用户点击该通知，并转到 Play Store 中的应用页，他们可以在那里开始安装。 安装成功后，通知即会消失。 |

## <a name="samsung-knox-standard-android-devices"></a>Samsung Knox 标准版 Android 设备

| 应用类型 | 业务线 (LOB) 应用 | Play Store 应用  |
| ------------- |-------------| -----|
| 可用应用      | 用户在公司门户中点击“**安装**”。 应用安装无需进一步的用户干预。 | 用户在公司门户中点击应用，并转到 Play Store中的应用页，他们可以在那里开始安装。|
| Required apps      | 应用安装无需任何用户干预。    | 用户将看到一条通知（用户无法关闭此通知），指示他们需要安装应用。 用户点击该通知，并转到 Play Store 中的应用页，他们可以在那里开始安装。 安装成功后，通知即会消失。 |

应用可以是托管应用，也可以是非托管应用，如下所述。 托管应用的过程对于所有类型的 Android 设备都是相同的。

**托管应用** - 这些是可以通过策略管理的应用。 它们由 Intune“包装”或使用 Intune 移动应用程序管理 (MAM) 软件开发工具包 (SDK) 构建。 这些应用可以由 Intune 进行管理，应用程序策略可以应用于它们。

**非托管应用** - 这些是无法通过策略管理的应用。 它们未由 Intune 包装或未包含 Intune MAM SDK。 应用程序策略不能应用于这些应用。

### <a name="see-also"></a>另请参阅
[使用 Microsoft Intune 添加应用](/intune/deploy-use/add-apps)

[iOS 用户如何获取其应用](how-your-ios-users-get-their-apps.md)

[Windows 用户如何获取其应用](how-your-windows-users-get-their-apps.md)



<!--HONumber=Nov16_HO1-->


