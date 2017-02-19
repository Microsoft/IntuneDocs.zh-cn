---
title: "取消注册 Windows 设备会造成什么结果？ |Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47e03edb-0c57-4e25-8e89-4a1069267b8c
searchScope:
- Company Portal
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: a87fe0cf9591040f1455d71b1f40cd0705ba8abf
ms.openlocfilehash: 7d41dc09c36684bd30263cfc0519cdacb3ab321b


---


# <a name="what-happens-if-you-unenroll-your-windows-device-from-intune"></a>从 Intune 取消注册 Windows 设备会发生什么情况？

使用此页面右侧“本文内容”下的链接，找到所使用设备类型的相关信息。


## <a name="windows-10-windows-81-windows-8-windows-7-windows-vista"></a>Windows 10，Windows 8.1，Windows 8，Windows 7，Windows Vista

-   设备将不再显示在公司门户中，并且你不能再从公司门户安装应用。

-   如果安装了 Intune 客户端软件，则会从计算机中删除该软件。

-   从计算机中删除 Intune Endpoint Protection 软件。 如果计算机安装了其他病毒防护软件，并且该软件处于禁用状态，则在删除 Intune Endpoint Protection 后可重新启用该软件。 从公司门户中将计算机删除之后，请对其进行检查。

    > [!IMPORTANT]
    > 如果未重新启用其他病毒保护软件或未安装其他病毒保护软件，你的计算机可能容易受到病毒和恶意软件的攻击。

-   将不再应用当添加设备时在设备上更改的任何设置（例如禁用相机）。

-   计算机不再从 Intune 服务接收自动软件更新或防病毒软件更新。 但是，根据计算机的设置情况，计算机可能仍会从 Windows Server Update Services、Windows 更新或 Microsoft 更新接收更新。

此外，对于 Windows 8.1：

-   你不再能使用设备上的公司应用和公司数据。

-   某些邮件应用（例如 Windows 邮件）无法再访问设备上所存储的公司电子邮件。

-   可能无法再使用 Wi-Fi 或虚拟专用网连接到公司网络。

-   可能无法再访问设备上的某些公司资源（例如文件共享或内部网站）。

## <a name="windows-10-mobile-and-windows-phone-81"></a>Windows 10 移动版和 Windows Phone 8.1

-   从设备中卸载公司门户应用。 这意味着设备不再显示在公司门户中，且不能从公司门户应用或公司门户网站安装应用。

-   你不再能使用设备上的公司应用和公司数据。

-   将不再应用当添加设备时在设备上更改的任何设置（例如禁用相机，或需要一定的密码长度）。

    > [!IMPORTANT]
    > 唯一例外的是加密策略，这些策略仍适用。 如果公司策略要求对 Windows Phone 进行加密，则解密电话的唯一方式是使用“设置”菜单对其进行重置。

## <a name="windows-rt-running-windows-81"></a>运行 Windows 8.1 的 Windows RT

-   从设备中卸载公司门户应用。 这意味着设备不再显示于公司门户中，且不能从公司门户安装应用。

-   你不再能使用设备上的公司应用和公司数据。

-   将不再应用当添加设备时在设备上更改的任何设置（例如禁用相机，或需要一定的密码长度）。

-   可能无法再使用 Wi-Fi 或虚拟专用网连接到公司网络。

-   可能无法再访问设备上的某些公司资源（例如文件共享或内部网站）。

-   某些邮件应用（例如 Windows 邮件）无法再访问设备上所存储的公司电子邮件。

在删除 Windows RT 设备时，将发生下列情况：

-   从设备中卸载公司门户应用。 这意味着设备不再显示在公司门户中，并且你不能再从公司门户安装应用。

-   你不再能使用设备上的公司应用和公司数据。

-   将不再应用当添加设备时在设备上更改的任何设置（例如禁用相机，或需要一定的密码长度）。

如有疑问，请与 IT 管理员联系。 有关联系信息，请查看[公司门户网站](http://portal.manage.microsoft.com)。



<!--HONumber=Jan17_HO4-->


