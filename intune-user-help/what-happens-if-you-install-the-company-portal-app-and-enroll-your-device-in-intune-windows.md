---
title: 安装 Windows 适用的公司门户应用 | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/23/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d65e3452-5bbf-4d26-a06e-401ddcc47f39
searchScope:
- User help
ROBOTS: ''
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 85ccfb526ada4d6851fb32b077d07d3538f90361
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "55846836"
---
# <a name="what-happens-if-you-install-the-company-portal-app-and-enroll-your-windows-device-in-intune"></a>安装公司门户应用并在 Intune 中注册 Windows 设备后会发生什么情况？

安装公司门户应用，然后使用该应用注册 Windows 或 Windows Phone 设备，即表示你允许公司支持人员管理你的设备以保护公司或学校数据的安全。 本主题介绍设备版本低于 Windows 10 时会发生的情况。 对于 Windows 10 设备，请参阅[相关主题](about-cp-app-for-windows-10.md)。  

## <a name="what-happens-to-all-windows-devices-after-enrollment"></a>注册后，所有 Windows 设备会发生什么情况
在 Intune 中注册 Windows 或 Windows Phone 设备，可实现以下操作：

-   访问公司网络、你的电子邮件和工作文件。

-   从公司门户网站获取公司应用。 （__注意__：对于 Windows 7 和 Windows Vista，仅可以从公司门户网站获取公司应用。）

-   自动设置公司或学校电子邮件帐户。

-   在手机丢失或被盗时将它重置为出厂设置。

注册设备时，会向公司支持人员授予执行以下操作的权限：

-   将设备重置回制造商的默认设置。 如果设备丢失或被盗，这非常有用。

-   仅删除公司相关文件和业务应用。 *不会删除个人数据和设置。*

-   公司支持人员可看到设备上安装的软件，包括个人安装的软件。

-   对设备设置要求，例如要求使用设备密码或 PIN 以帮助保护公司数据。 公司支持人员还可以限制可输入错误密码的次数，并可在尝试次数过多时锁定设备。

-   要求用户加密其设备上的公司数据，以便在设备丢失或被盗时帮助保护公司数据。

-   要求你接受条款和条件。

-   阻止用户拍摄公司相关数据。

## <a name="what-happens-to-all-windows-pcs-after-enrollment"></a>注册后，所有 Windows 电脑会发生什么情况

-  将在计算机上安装某个软件，使公司支持人员能够管理计算机，并使你能够访问公司资源（如应用和支持信息）。 公司支持人员可能会自动更新此软件。

-  可能会在计算机上安装 Intune Endpoint Protection。 此软件用于检查病毒和恶意软件。

-  公司支持人员可从计算机硬盘中收集或删除数据。

-  公司支持人员可在计算机上安装应用和更新。

## <a name="what-happens-every-eight-hours-after-device-enrollment"></a>设备注册之后每 8 小时会发生什么情况

已注册的设备将以约 8 小时的间隔执行以下操作：

-   下载公司支持人员已提供的任何策略或应用更新。

-   发送任何硬件清单更新。

-   发送任何公司应用清单更新。

如有疑问，请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)。
