---
title: "在 iOS 设备上使用托管应用 | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3232c5c1-cb9f-45ca-806f-7e74eeb3533e
searchScope:
- Company Portal
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 6da5f6a3b017a93446011f8d59e73a4ea7730196


---


# <a name="use-managed-apps-on-your-ios-device"></a>在 iOS 设备上使用托管应用

IT 管理员可对托管应用进行配置，以帮助保护在该应用中可访问的公司数据。 在 iOS 设备上的托管应用中访问公司数据时，可能会注意到此应用与预期的运作方式有些许不同。 例如，你可能无法复制和粘贴受保护的公司数据，或者你可能无法将该数据保存到特定位置。

不同的托管应用也可以在设备上协同工作，使你能在处理日常任务的同时始终保护公司数据。 例如，如果你在一托管应用中打开了一份公司文件，但是需打开另一托管应用才能查看该文件，则系统会自动打开后者以允许你查看该文件。 如果所需应用不可用，则某些特定操作（如打开文档或从托管文档中访问 Web 链接）可能不可用。

在托管应用中访问公司数据时，你会看到如下所示的消息，告知你将打开的应用是托管应用。

![managed-apps-message-ios](./media/managed-apps-message.png)

### <a name="how-do-i-get-managed-apps"></a>如何获取托管应用？
你可通过以下几种不同的方式获取托管应用：

-   如果已在 Microsoft Intune 中注册设备，则你可以从公司门户应用或公司门户网站安装应用，或者可由 IT 管理员将其安装到你的设备。 若要了解相关注册信息，请参阅[在 Intune 中注册 iOS 设备](enroll-your-device-in-intune-ios.md)或[在 Intune 中注册 macOS 设备](enroll-your-device-in-intune-macos.md)。

-   从 App Store 安装应用，然后使用由 Intune 管理的公司用户帐户登录该应用。

### <a name="what-can-my-it-admin-manage-in-an-app"></a>IT 管理员可以管理应用中的哪些内容？
以下是 IT 管理员可在应用中管理的一些选项示例，它们可影响用户在其设备上与公司数据的交互：

-   对特定网站的访问

-   应用程序之间的数据传输

-   保存文件

-   复制和粘贴操作

-   PIN 访问要求

-   使用公司凭据登录

-   将数据备份到云的能力

-   截取屏幕截图的能力

-   数据加密要求


有关设备上的托管应用的详细信息，请联系你的 IT 部门。 有关联系信息，请查看[公司门户网站](http://portal.manage.microsoft.com)。



<!--HONumber=Dec16_HO2-->


