---
# required metadata

title: 收集设备日志| Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 06/01/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 设备日志

作为故障诊断工作的一部分，你可能希望从用户设备中收集日志。 此处介绍了收集这些日志的说明。 通常，你可能需要访问设备，或者请求用户收集日志并将其发送给你。 

### Android 日志位置
Android 日志位于 *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files*。 如[使用电子邮件将 Android 诊断数据日志发送给 IT 管理员](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)中所述，用户还可以使用电子邮件向你发送日志文件。

### iOS 日志

如[将 iOS 注册错误发送给 IT 管理员](/intune/enduser/send-errors-to-your-it-admin-ios)中所述，用户可向你发送注册错误。

### Mac OS X 设备

1. 打开**控制台**应用。
2. 在**文件**下选择 **system.log**
3. 在顶部菜单栏中，选择**文件** > **另存副本为...** 并保存该文件。

### Windows Phone

在 **Windows Phone 公司门户**中，用户必须选择 **...** 以访问菜单，然后选择**发送日志**。 登录门户前后此选项都可用。

### Windows

对于 Windows 公司门户，日志位于 *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*。


<!--HONumber=Jun16_HO1-->


