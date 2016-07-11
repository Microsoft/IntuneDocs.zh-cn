---
title: "Android 用户如何获取其应用 | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d3bcf89636f9da8fd8bfa5cc52391742a9ce9f92
ms.openlocfilehash: 25571ce1b214c927f3dc2ea3968d00970621e474


---


# Android 用户如何获取其应用
使用此信息可了解最终用户如何以及在何处获取你通过 Microsoft Intune 分发的应用。 

**必需应用** - 管理员所要求并且在用户参与程度最小的情况下安装在设备上的应用（具体取决于平台）。
 
- **Samsung Knox 设备**：如果你将所需的应用部署到 Samsung Knox 设备，它将自动以无提示方式在设备上安装。
- **本机（非 Samsung Knox 设备）**：如果你将所需的应用部署到非 Samsung Knox 设备，它不会在用户设备上自动安装。 相反，用户会收到安装应用的提示。 用户接受提示后，会下载该应用，然后用户会收到一个提示需要进行安装的通知。 

**可用应用** - 在公司门户应用列表中提供的应用和用户可以根据需要选择安装的应用。

**托管应用** - 可以通过策略管理并且由 Intune“包装”或使用 Intune 移动应用管理 (MAM) 软件开发工具包 (SDK) 构建的应用。 这些应用可以由 Intune 进行管理，应用程序策略可以应用于它们。

**非托管应用** - 可以通过策略管理并且未由 Intune 包装或未包含 Intune MAM SDK 的应用。 应用程序策略不能应用于这些应用。

###另请参阅
[使用 Microsoft Intune 添加应用](/intune/deploy-use/add-apps)
[iOS 用户如何获取应用](how-your-ios-users-get-their-apps.md)
[Windows 用户如何获取应用](how-your-windows-users-get-their-apps.md)


<!--HONumber=Jul16_HO1-->


