---
title: 在 iOS 设备上使用托管应用 | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/09/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3232c5c1-cb9f-45ca-806f-7e74eeb3533e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 35d77c9aa739096f36f4dbf4b75a4186e55a3381
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "55835057"
---
# <a name="use-managed-apps-on-your-ios-device"></a>在 iOS 设备上使用托管应用

公司支持人员可对托管应用进行配置，以帮助保护在该应用中可访问的公司数据。 在 iOS 设备上的托管应用中访问公司数据时，可能会注意到此应用与预期的运作方式有些许不同。 例如，你可能无法复制和粘贴受保护的公司数据，或者你可能无法将该数据保存到特定位置。

不同的托管应用也可以在设备上协同工作，使你能在处理日常任务的同时始终保护公司数据。 例如，如果你在一托管应用中打开了一份公司文件，但是需打开另一托管应用才能查看该文件，则系统会自动打开后者以允许你查看该文件。 如果所需应用不可用，则某些特定操作（如打开文档或从托管文档中访问 Web 链接）可能不可用。

在托管应用中访问公司数据时，你会看到如下所示的消息，告知你将打开的应用是托管应用。

![managed-apps-message-ios](./media/managed-apps-message.png)

## <a name="how-do-i-get-managed-apps"></a>如何获取托管应用？  
你可通过以下几种不同的方式获取托管应用：

-   如果已在 Microsoft Intune 中注册设备，则你可以从公司门户应用或公司门户网站安装应用，或者可由公司支持人员将其安装到你的设备。 若要了解相关注册信息，请参阅[在 Intune 中注册 iOS 设备](enroll-your-device-in-intune-ios.md)或[在 Intune 中注册 macOS 设备](enroll-your-device-in-intune-macos.md)。

-   从 App Store 安装应用，然后使用由 Intune 管理的公司用户帐户登录该应用。

公司支持人员有时可能会为你安装的应用购买多个许可证。 如果你看到一条消息，要求你接受 Apple Volume Purchase Program 协议，这是正常现象，可以接受该协议。 如果不接受，你将无法安装该应用。

## <a name="available-apps"></a>可用应用   
 贵组织会选择适合在工作中或学校里使用的应用。 这些应用是在公司门户中仅能找到的应用。   

 也可以根据设备类型使用应用。 例如，如果使用适用于 iOS 的公司门户应用，则可以访问 iOS 应用，但不能访问 Android 应用。   

## <a name="request-an-app-for-work-or-school"></a>请求用于工作或用于学校的应用   
 如果未在公司门户中找到需要的应用，则可以请求该应用。 在公司门户应用的“支持”选项卡中查找“支持人员”的联系人详细信息。可以在[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)中找到相同的联系详情。   
 

## <a name="what-can-my-company-support-manage-in-an-app"></a>我的公司支持人员可管理应用中的哪些内容？  
以下是公司支持人员可在应用中管理的一些选项示例，它们可影响用户在其设备上与公司数据的交互：

-   对特定网站的访问

-   应用程序之间的数据传输

-   保存文件

-   复制和粘贴操作

-   PIN 访问要求

-   使用公司凭据登录

-   将数据备份到云的能力

-   截取屏幕截图的能力

-   数据加密要求

有关设备上的托管应用的详细信息，请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)。
