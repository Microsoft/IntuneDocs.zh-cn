---
title: "收集设备日志| Microsoft Intune"
description: "了解如何收集托管设备中的日志。"
keywords: 
author: staciebarker
ms.author: staciebarker
manager: angrobe
ms.date: 11/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 19b0b502d2c8c261947c461f27a0e8153df5b186
ms.openlocfilehash: 1e65c1fa25e273ba03218f79ebeff611138e8013


---

# <a name="device-logs"></a>设备日志

作为故障诊断工作的一部分，你可能希望从用户设备中收集日志。 此处介绍了收集这些日志的说明。 通常，你可能需要访问设备，或者请求用户收集日志并将其发送给你。

### <a name="android-logs"></a>Android 日志
Android 日志位于 *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files*。 

有时不会显示这些文件，尤其是在较新的 Android 设备上。 如果发生这种情况，请让最终用户打开公司门户应用 Android 版，转到“设置”，选择“复制日志”，然后重启其设备。 

有关用户如何能够发送数据日志的详细信息，请参阅以下文章：

- [使用详细日志记录帮助 IT 管理员修复设备问题](/intune/enduser/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android) - 介绍用户如何打开详细日志记录（自动发送其所有数据日志）。 在默认情况下，详细日志记录处于启用状态。

- [使用电子邮件将 Android 诊断数据日志发送给 IT 管理员](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android) 

- [使用 USB 电缆将诊断数据日志发送给 IT 管理员](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)

### <a name="ios-logs"></a>iOS 日志

如[将 iOS 注册错误发送给 IT 管理员](/intune/enduser/send-errors-to-your-it-admin-ios)中所述，用户可向你发送注册错误。

### <a name="mac-os-x-logs"></a>Mac OS X 日志

1. 打开**控制台**应用。
2. 在**文件**下选择 **system.log**
3. 在顶部菜单栏中，选择**文件** > **另存副本为...** 并保存该文件。

### <a name="windows-phone"></a>Windows Phone

在 Windows Phone 公司门户应用中，用户必须选择“…” 以访问菜单，然后选择**发送日志**。 登录公司门户应用前后，此选项都可用。

### <a name="windows"></a>Windows

对于 Windows 公司门户，日志位于 *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*。



<!--HONumber=Nov16_HO2-->


