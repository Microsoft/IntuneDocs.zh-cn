---
title: 注册你的设备时，你的公司可以看到哪些信息？
description: 介绍 IT 人员在托管设备上能看到和不能看到的内容。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 12655728-a1af-4d89-97bc-925fe36c0dc4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.collection: M365-identity-device-management
ms.openlocfilehash: fc50f48afbd527f3c6d82cc0c71a166b0356ab9e
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "73801481"
---
# <a name="what-information-can-my-organization-see-when-i-enroll-my-device"></a>在我注册自己的设备时，我的组织可以看到哪些信息？

向 Microsoft Intune 注册设备时，组织看不到你的个人信息。 注册设备时，将为组织授予查看设备上特定信息的权限，如设备型号和序列号。 组织可使用此信息来帮助保护设备上的公司数据。

**你的组织永远看不到的内容：**

- 调用和 Web 浏览历史记录
- 电子邮件和短信
- 联系人
- 日历
- 密码
- 图片，包括照片应用中的照片或本机照片
- 文件

**你的组织始终可以看到的内容：**

- 设备型号（如 Google Pixel）
- 设备制造商（如 Microsoft）
- 操作系统和版本，如 iOS 12.0.1
- 应用清单和应用名称（如 Microsoft Word）。 在个人设备上，组织只能看到托管应用清单。 在公司拥有的设备上，组织可以查看所有应用广告资源。
- 设备所有者
- 设备名称
- 设备序列号
- IMEI

**组织可能会看到的信息：**

- 电话号码：对于公司拥有的设备，公司可看到完整的电话号码。 对于个人拥有的设备，组织只能看到电话号码的最后四位数字。 可以在设备的 "**详细信息**" 页上查看每个设备的所有权类型。
- 设备存储空间：如果无法安装所需的应用，组织可以查看设备的存储空间，以确定空间是否不足。  
- 位置：你的组织永远不会看到你的设备的位置，除非你需要恢复丢失、受监督的 iOS 设备。 访问 [Apple iOS 文档](https://go.microsoft.com/fwlink/?linkid=853816)以详细了解受监督的设备。  
- 应用清单详细信息：如果组织使用 Mobile Threat Defense，则可以查看 iOS 设备中应用的相关详细信息。 了解[移动威胁防御](you-are-prompted-to-install-mtd-ios.md)的详细信息。 如果你有个人设备，则组织只能看到托管应用清单。 如果你有公司拥有的设备，则组织可查看所有应用广告资源。
- 网络信息：可能向组织支持人员提供有关 Android 设备网络连接信息。 例如，如果组织要求设备在某个建筑物内使用，则设备将标识所连接的网络。 
