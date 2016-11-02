---
title: "收集设备日志| Microsoft Intune"
description: "了解如何收集托管设备中的日志。"
keywords: 
author: staciebarker
ms.author: staciebarker
manager: angrobe
ms.date: 10/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3a081109cd499d3bdda75cb6c8a4dab9d9d28fab
ms.openlocfilehash: ec7d522e8dcff66d1b84fed3c4c0cc708e555e67


---

# <a name="device-logs"></a>设备日志

作为故障诊断工作的一部分，你可能希望从用户设备中收集日志。 此处介绍了收集这些日志的说明。 通常，你可能需要访问设备，或者请求用户收集日志并将其发送给你。

### <a name="android-log-location"></a>Android 日志位置
Android 日志位于 *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files*。 如[使用电子邮件将 Android 诊断数据日志发送给 IT 管理员](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)中所述，用户还可以使用电子邮件向你发送日志文件。

### <a name="ios-logs"></a>iOS 日志

如[将 iOS 注册错误发送给 IT 管理员](/intune/enduser/send-errors-to-your-it-admin-ios)中所述，用户可向你发送注册错误。

### <a name="mac-os-x-devices"></a>Mac OS X 设备

1. 打开**控制台**应用。
2. 在**文件**下选择 **system.log**
3. 在顶部菜单栏中，选择**文件** > **另存副本为...** 并保存该文件。

### <a name="windows-phone"></a>Windows Phone

在 **Windows Phone 公司门户**中，用户必须选择 **...** 以访问菜单，然后选择**发送日志**。 登录门户前后此选项都可用。

### <a name="windows"></a>Windows

对于 Windows 公司门户，日志位于 *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*。



<!--HONumber=Oct16_HO3-->


