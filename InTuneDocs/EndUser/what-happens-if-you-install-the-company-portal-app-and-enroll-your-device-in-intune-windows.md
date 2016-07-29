---
title: "安装公司门户应用并在 Intune 中注册 Windows 设备后会发生什么情况？ | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 7/8/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d65e3452-5bbf-4d26-a06e-401ddcc47f39
ROBOTS: noindex,nofollow
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 618e2abda642c3b9b2e813824dfd4235c9309faa
ms.openlocfilehash: 8b6e9b1bbf2d870b57dfcd7cdefefa2550d07d14


---


# 安装公司门户应用并在 Intune 中注册 Windows 设备后会发生什么情况？

在安装公司门户应用，然后使用该应用注册 Windows 或 Windows Phone 设备后，你要启用你的 IT 管理员来管理你的设备以保护公司或学校数据的安全，对于早于 Windows 10 的设备，如下所述。 有关 Windows 10 设备的信息，请参阅[本页](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows10.md)。

## 注册后，所有 Windows 设备会发生什么情况
当你在 Intune 中注册 Windows 或 Windows Phone 设备时，你可以：

-   访问公司网络、你的电子邮件和工作文件

-   从公司门户网站中获取公司应用（对于 Windows 7 和 Vista，你只能从公司门户网站获取公司应用）

-   自动配置公司或学校电子邮件帐户

-   在手机丢失或被盗时将它重置为出厂设置

注册设备时，将向 IT 管理员授予执行以下操作的权限：

-   将你的设备重置回制造商的默认设置。 如果设备丢失或被盗，这非常有用。

-   删除公司相关的所有数据以及安装的业务应用。 不会删除你的个人数据和设置。

-   你的 IT 管理员可清点计算机上安装的所有软件，包括你个人安装的软件。

-   强制你在设备上设置密码或 PIN，如果尝试输入太多次不正确的密码，设备可能会被锁定，使你无法访问设备，或者将你的设备重置回制造商的默认设置（可能包括删除数据）。

-   强制对设备上的所有数据进行加密，这在设备丢失或被盗时有助于保护数据。

-   要求你接受条款和条件。

-   你的 IT 管理员可能会在计算机上强制实施策略。 例如，可能会要求你在计算机上设置密码或 PIN，如果尝试输入太多次不正确的密码，你可能会被锁定，无法访问计算机，或者会从计算机的硬盘驱动器上删除所有数据。

-   禁用 SD 卡。

## 注册后，所有 Windows 电脑会发生什么情况

-  将在计算机上安装某个软件，使 IT 管理员能够管理计算机，并使你能够获取公司资源（如应用和支持信息）。 你的 IT 管理员可能会自动更新此软件。

-  可能会在计算机上安装 Intune Endpoint Protection。 此软件用于检查病毒和恶意软件。

-  你的 IT 管理员可清点计算机上安装的所有软件，包括你个人安装的软件。

-  可能要求你接受条款和条件。

-  你的 IT 管理员可从你的计算机的硬盘中收集或删除数据。 你的 IT 管理员还可以删除整个硬盘。

-  你的 IT 管理员可在你的计算机上安装应用和更新。

-  你的 IT 管理员可能会在计算机上强制实施策略。 例如，可能会要求你在计算机上设置密码或 PIN，如果尝试输入太多次不正确的密码，计算机可能会被锁定，使你无法访问计算机，或者会从计算机的硬盘中删除所有数据。


## 设备注册之后每 8 小时会发生什么情况
大约每 8 小时，注册的设备将：

-   下载 IT 管理员已提供的任何策略或应用更新。

-   发送任何硬件清单更新。

-   发送任何公司应用清单更新。

有关注册的步骤，请参阅[在 Intune 中注册 Windows 设备](enroll-your-device-in-intune-windows.md)。 若要了解 IT 管理员可以在你的设备上看到的内容，请参阅[当我在 Intune 中注册设备后，IT 管理员可以看到哪些内容？](what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md)。

如有疑问，请与你的 IT 管理员联系。 有关他们的联系信息，请查看[公司门户网站](http://portal.manage.microsoft.com)。

### 另请参阅
[通过 Intune 使用 Windows 设备](using-your-windows-device-with-intune.md)



<!--HONumber=Jul16_HO4-->


