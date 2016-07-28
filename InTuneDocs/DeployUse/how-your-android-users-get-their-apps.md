---
title: "Android 用户如何获取其应用 | Microsoft Intune"
description: "使 Android 应用可供最终用户使用的方法"
keywords: 
author: Staciebarker
manager: arob98
ms.date: 7/7/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 376e6c1ae229187ab8ec73390f091f1d534365dd
ms.openlocfilehash: 43b7eb3378d9977b9d19196c91a812d9411752b9


---


# Android 用户如何获取其应用
使用此信息可了解 Android 最终用户如何以及在何处获取你通过 Microsoft Intune 分发的应用。 该信息在本机 Android 设备与 Samsung Knox 设备上可能有所不同。

## 本机（非 Samsung Knox）Android 设备

| 应用类型 | 业务线 (LOB) 应用 | Play Store 应用  |
| ------------- |-------------| -----|
| 可用应用      | 用户在公司门户中点击“**安装**”。 此时将出现一条通知，用户需要点击该通知以开始安装。 安装成功后，通知即会消失。 | 用户在公司门户中点击应用，并转到 Play Store中的应用页，他们可以在那里开始安装。|
| Required apps      | 用户将看到一条通知（用户无法关闭此通知），指示他们需要安装应用。 用户点击通知以开始安装。 安装成功后，通知即会消失。    | 用户将看到一条通知（用户无法关闭此通知），指示他们需要安装应用。 用户点击该通知，并转到 Play Store 中的应用页，他们可以在那里开始安装。 安装成功后，通知即会消失。 |

## Samsung Knox Android 设备

| 应用类型 | 业务线 (LOB) 应用 | Play Store 应用  |
| ------------- |-------------| -----|
| 可用应用      | 用户在公司门户中点击“**安装**”。 应用安装无需进一步的用户干预。 | 用户在公司门户中点击应用，并转到 Play Store中的应用页，他们可以在那里开始安装。|
| Required apps      | 应用安装无需任何用户干预。    | 用户将看到一条通知（用户无法关闭此通知），指示他们需要安装应用。 用户点击该通知，并转到 Play Store 中的应用页，他们可以在那里开始安装。 安装成功后，通知即会消失。 |

应用可以是托管应用，也可以是非托管应用，如下所述。 托管应用的过程对于所有类型的 Android 设备都是相同的。

**托管应用** - 可以通过策略管理并且由 Intune“包装”或使用 Intune 移动应用管理 (MAM) 软件开发工具包 (SDK) 构建的应用。 这些应用可以由 Intune 进行管理，应用程序策略可以应用于它们。

**非托管应用** - 可以通过策略管理并且未由 Intune 包装或未包含 Intune MAM SDK 的应用。 应用程序策略不能应用于这些应用。

### 另请参阅
[使用 Microsoft Intune 添加应用](/intune/deploy-use/add-apps)
[iOS 用户如何获取应用](how-your-ios-users-get-their-apps.md)
[Windows 用户如何获取应用](how-your-windows-users-get-their-apps.md)



<!--HONumber=Jul16_HO3-->


