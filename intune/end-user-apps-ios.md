---
title: "iOS 用户如何获取其应用"
description: "使 iOS 应用可供最终用户使用的方法"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0061d4ecd8d71f8b7363193e36b838741aa56a92
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="how-your-ios-users-get-their-apps"></a>iOS 用户如何获取其应用

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

使用此信息可了解最终用户如何以及在何处获取你通过 Microsoft Intune 分发的应用。

**必需应用** -- 管理员所要求并且在用户参与程度最小的情况下安装在设备上的应用（具体取决于平台）。

**可用应用** -- 在公司门户应用列表中提供的应用和用户可以根据需要选择安装的应用。

**托管应用** -- 可以通过策略管理并且由 Intune“包装”或使用 Intune 移动应用管理 (MAM) 软件开发工具包 (SDK) 构建的应用。 这些应用可以由 Intune 进行管理，应用程序策略可以应用于它们。

**非托管应用** -- 可以通过策略管理并且未由 Intune 包装或未包含 Intune MAM SDK 的应用。 应用程序策略不能应用于这些应用。

Apple 限制禁止公司门户应用列出业务线应用和托管应用商店应用。 要解决这一问题，用户可根据 iOS 公司门户应用中磁贴的指示，在同一位置（公司门户网站）切换到其他视图，以查看所有应用。

在公司门户应用上的“应用”屏幕上，已注册用户可以通过点击以下磁贴获取他们的应用：

- **所有应用**指向[公司门户网站](https://portal.manage.microsoft.com)“全部”选项卡中所有应用的列表。

- **特色应用**使用户进入公司门户网站的“特别推荐”选项卡。

- **类别**指向公司门户网站的“类别”选项卡。


![iOS 公司门户应用屏幕](./media/ios-cp-app-main-apps-screen.png)

有关如何添加应用并将其放入这些磁贴的信息，请参阅[将已注册设备的应用添加到 Intune](/intune-classic/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune.md)。

### <a name="see-also"></a>另请参阅
[Android 用户如何获取其应用](end-user-apps-android.md)

[Windows 用户如何获取其应用](end-user-apps-windows.md)
