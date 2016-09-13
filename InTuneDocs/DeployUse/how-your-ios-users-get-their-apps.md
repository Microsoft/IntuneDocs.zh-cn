---
title: "iOS 用户如何获取其应用 | Microsoft Intune"
description: "使 iOS 应用可供最终用户使用的方法"
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9f1946c02c6267a22844106e8f72555ec5e9cabb
ms.openlocfilehash: 212dcd31697180dae61569dda13b56704a079bf4


---


# iOS 用户如何获取其应用

使用此信息可了解最终用户如何以及在何处获取你通过 Microsoft Intune 分发的应用。

**必需应用** - 管理员所要求并且在用户参与程度最小的情况下安装在设备上的应用（具体取决于平台）。

**可用应用** - 在公司门户应用列表中提供的应用和用户可以根据需要选择安装的应用。

**托管应用** - 可以通过策略管理并且由 Intune“包装”或使用 Intune 移动应用管理 (MAM) 软件开发工具包 (SDK) 构建的应用。 这些应用可以由 Intune 进行管理，应用程序策略可以应用于它们。

**非托管应用** - 可以通过策略管理并且未由 Intune 包装或未包含 Intune MAM SDK 的应用。 应用程序策略不能应用于这些应用。

Apple 限制禁止业务线和托管应用商店应用列于公司门户应用中，这意味着用户必须访问不同视图才能找到自己所有的应用。 公司门户应用的“应用”页上显示的各个磁贴代表的应用可用情况如下：

- **公司应用**磁贴指向[公司门户网站](http://portal.manage.microsoft.com)“**全部**”选项卡中所有应用的列表。

- **其他应用**磁贴目前指向公司门户应用内部的一个视图，其中列出了 Apple 允许公司门户应用显示的所有应用。 其中包括除业务线和托管应用商店应用之外的所有应用。

- **类别**磁贴目前指向公司门户应用内部的一个视图，其中列出了应用类别。

    ![ios-how-to-sync-device-with-intune](./media/ios-sync-comp-portal-apps.png)


###另请参阅
[Android 用户如何获取其应用](how-your-android-users-get-their-apps.md)</br>
[Windows 用户如何获取其应用](how-your-windows-users-get-their-apps.md)



<!--HONumber=Aug16_HO4-->


