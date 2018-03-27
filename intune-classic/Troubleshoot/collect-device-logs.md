---
title: 收集设备日志
description: 了解如何收集托管设备中的日志。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/07/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 979b1317adbb23f9ace27f15c49072798b67bb95
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="device-logs"></a>设备日志

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

在进行故障诊断工作的过程中，可能希望从用户设备中收集日志。 此处介绍了收集这些日志的说明。 通常需要访问设备获取日志，也可请求用户收集日志并发送。

### <a name="android-logs"></a>Android 日志
Android 日志位于 *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files*。

有时不会显示这些文件，尤其是在较新的 Android 设备上。 如果请求用户收集日志，请让用户打开 Android 版公司门户应用。 然后选择“设置”>“复制日志”并重启设备。

有关用户如何能够发送数据日志的详细信息，请参阅以下文章：

- [使用详细日志记录帮助 IT 管理员修复设备问题](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android) - 介绍用户如何启用详细日志记录（自动发送其所有数据日志）。 在默认情况下，详细日志记录处于启用状态。

- [使用电子邮件将 Android 诊断数据日志发送给 IT 管理员](/intune-user-help/send-logs-to-your-it-admin-by-email-android)

- [使用 USB 电缆将诊断数据日志发送给 IT 管理员](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)

### <a name="ios-logs"></a>iOS 日志

如[将 iOS 注册错误发送给 IT 管理员](/intune-user-help/send-errors-to-your-it-admin-ios)中所述，用户可向你发送注册错误。

用户可发送设备日志，如[发送 iOS 设备日志](/intune-user-help/send-logs-to-microsoft-ios)所述。

### <a name="mac-os-x-logs"></a>Mac OS X 日志

1. 打开**控制台**应用。
2. 在“文件”下，选择 **system.log**。
3. 在顶部的菜单栏中，选择“文件” > “另存副本为...”。 然后保存该文件。

### <a name="windows-phone"></a>Windows Phone

在 Windows Phone 公司门户应用中，用户可选择三个点（“...”）访问菜单，然后选择“发送日志”。 登录公司门户应用前后，此选项都可用。

### <a name="windows"></a>Windows

对于 Windows 公司门户，日志位于 *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*。
