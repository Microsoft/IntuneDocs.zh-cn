---
title: "安装公司门户应用并在 Intune 中注册 Windows 设备后会发生什么情况？ | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 09/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d65e3452-5bbf-4d26-a06e-401ddcc47f39
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4881d765a6a79d380ab6d3facdb55d9f0c81bf97
ms.openlocfilehash: ac4fdc73122fb5dc82771f174d9bd783c186bf9d


---


# 安装公司门户应用并在 Intune 中注册 Windows 设备后会发生什么情况？

在安装公司门户应用，然后使用该应用注册 Windows 或 Windows Phone 设备，即表示你允许 IT 管理员管理你的设备以保护公司或学校数据的安全，如下所述（适用于操作系统版本低于 Windows 10 的设备）。 请参阅[本页](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows10.md)以了解 Windows 10 设备的情况。

## 注册后，所有 Windows 设备会发生什么情况
在 Intune 中注册 Windows 或 Windows Phone 设备，可实现以下操作：

-   访问公司网络、你的电子邮件和工作文件

-   从公司门户网站中获取公司应用（对于 Windows 7 和 Vista，你只能从公司门户网站获取公司应用）

-   自动设置公司或学校电子邮件帐户

-   在手机丢失或被盗时将它重置为出厂设置

注册设备时，将向 IT 管理员授予执行以下操作的权限：

-   将你的设备重置回制造商的默认设置。 如果设备丢失或被盗，这非常有用。

-   仅删除公司相关文件和业务应用。 **不会删除你的个人数据和设置。**

-   IT 管理员可看到设备上安装的软件，包括你个人安装的软件。

-   对你的设备设置要求，例如要求使用密码或 PIN 保护公司数据。 IT 管理员还可限制可输入错误密码的次数，并可在尝试次数过多时锁定设备。

-   要求用户加密其设备上的公司数据，以便在设备丢失或被盗时帮助保护公司数据。 

-   要求你接受条款和条件。

-   阻止用户拍摄公司相关数据。

## 注册后，所有 Windows 电脑会发生什么情况

-  将在计算机上安装某个软件，使 IT 管理员能够管理计算机，并使你能够获取公司资源（如应用和支持信息）。 你的 IT 管理员可能会自动更新此软件。

-  可能会在计算机上安装 Intune Endpoint Protection。 此软件用于检查病毒和恶意软件。

-  你的 IT 管理员可从你的计算机的硬盘中收集或删除数据。

-  你的 IT 管理员可在你的计算机上安装应用和更新。

## 设备注册之后每 8 小时会发生什么情况
已注册的设备将以约 8 小时的间隔执行以下操作：

-   下载 IT 管理员已提供的任何策略或应用更新。

-   发送任何硬件清单更新。

-   发送任何公司应用清单更新。

如有疑问，请与你的 IT 管理员联系。 有关他们的联系信息，请查看[公司门户网站](http://portal.manage.microsoft.com)。




<!--HONumber=Sep16_HO4-->


