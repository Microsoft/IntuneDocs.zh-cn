---
title: "支持的设备 - Microsoft Intune"
description: "列出用于 Intune 设备管理支持的设备平台和浏览器"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/06/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b168cbf5282b4e016133d071c56c8abd54c2e23b
ms.sourcegitcommit: dc2595bec05206a826cd10cb834bf6043145c917
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/14/2017
---
# <a name="supported-devices-and-browsers"></a>支持的设备和浏览器

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

本文适用于负责企业中的设备管理的系统管理员。 有关在手机上安装 Intune 的帮助，请参阅[使用托管设备来完成工作](/intune-user-help/company-portal-frequently-asked-questions)。

开始设置 Microsoft Intune 之前，请查看以下要求：

- [支持的设备和计算机](#intune-supported-devices)
- [支持 Intune 的 Web 浏览器列表](#intune-supported-web-browsers)

还应熟悉 [Intune 网络带宽使用情况](network-bandwidth-use.md)（[经典门户](/intune-classic/get-started/network-bandwidth-use)）。

## <a name="intune-supported-devices"></a>支持 Intune 的设备

使用 Intune 移动设备管理，可管理以下设备：

[!INCLUDE[mdm-supported-devices](./includes/mdm-supported-devices.md)]

### <a name="supported-samsung-knox-standard-devices"></a>受支持的 Samsung KNOX Standard 标准版设备

在 MDM 注册期间，仅当设备显示在[受支持的 KNOX 设备列表](https://www.samsungknox.com/knox-supported-devices/knox-workspace)中时，公司门户应用才会尝试 Samsung KNOX 激活。 这有助于避免出现会阻止 MDM 注册的 KNOX 激活错误。 不支持 Samsung KNOX 激活的设备将作为标准 Android 设备进行注册。 Samsung 设备可能有一些支持 KNOX 的型号，其他设备则不具备。 购买并部署 Samsung 设备前，请与设备经销商确认 KNOX 兼容性。

下面列出的 Samsung 设备型号不支持 KNOX，并且由适用于 Android 的公司门户应用作为本机 Android 设备进行注册：

| **设备名** | **设备型号** |
| --- | --- |
| Galaxy Avant | SM-G386T |
| Galaxy Core 2/Core 2 Duos | SM-G355H<br>SM-G355M |
| Galaxy Core Lite | SM-G3588V |
| Galaxy Core Prime | SM-G360H |
| Galaxy Core LTE | SM-G386F<br>SM-G386W |
| Galaxy Grand | GT-I9082L<br>GT-I9082<br>GT-I9080L |
| Galaxy Grand 3 | SM-G7200 |
| Galaxy Grand Neo | GT-I9060I |
| Galaxy Grand Prime 超值版 | SM-G531H |
| Galaxy J Max | SM-T285YD |
| Galaxy J1 | SM-J100H<br>SM-J100M<br>SM-J100ML |
| Galaxy J1 Ace | SM-J110F<br>SM-J110H |
| Galaxy J1 Mini | SM-J105M |
| Galaxy J2/J2 Pro | SM-J200H<br>SM-J210F |
| Galaxy J3 | SM-J320F<br>SM-J320FN<br>SM-J320H<br>SM-J320M |
| Galaxy K Zoom | SM-C115 |
| Galaxy Light | SGH-T399N |
| Galaxy Note 3 | SM-N9002<br>SM-N9009 |
| Galaxy Note 7/Note 7 Duos | SM-N930S<br>SM-N9300<br>SM-N930F<br>SM-N930T<br>SM-N9300<br>SM-N930F<br>SM-N930S<br>SM-N930T |
| Galaxy Note 10.1 3G | SM-P602 |
| Galaxy S2 Plus | GT-I9105P |
| Galaxy S3 Mini | SM-G730A<br>SM-G730V |
| Galaxy S3 Neo | GT-I9300<br>GT-I9300I |
| Galaxy S4 | SM-S975L |
| Galaxy S4 Neo | SM-G318ML |
| Galaxy S5 | SM-G9006W |
| Galaxy S6 Edge | 404SC |
| Galaxy Tab A 7.0&quot; | SM T280<br>SM-T285 |
| Galaxy Tab 3 7&quot;/Tab 3 Lite 7&quot; | SM-T116<br>SM-T210<br>SM-T211 |
| Galaxy Tab 3 8.0&quot; | SM-T311 |
| Galaxy Tab 3 10.1&quot; | GT-P5200<br>GT-P5210<br>GT-P5220 |
| Galaxy Trend 2 Lite | SM-G318H |
| Galaxy V Plus | SM-G318HZ |
| Galaxy Young 2 Duos | SM-G130BU |

Intune 不能用于管理 Windows Server 操作系统。

### <a name="windows-pc-software-client"></a>Windows 电脑软件客户端

作为一种备用注册方法，可在 Windows 电脑上部署和安装 [Intune 软件客户端](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune)。 使用 Intune 经典门户时，此功能才可用。 可使用 Intune 软件客户端管理 Windows 7 和更高版本的电脑，Windows 10 家庭版除外。

<!--  ### Exchange ActiveSync management

You can manage [Exchange ActiveSync devices](/intune-classic/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune) from the Intune console. This option provides a limited set of management capabilities when compared to the other methods. See [Capabilities of built-in Mobile Device Management in Office 365](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0) for a list of supported devices.  -->

## <a name="intune-supported-web-browsers"></a>受 Intune 支持的 Web 浏览器

不同的管理任务要求使用以下管理网站之一。

- [Office 365 门户](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Azure 门户](https://portal.azure.com/)

此类门户支持以下浏览器：
- Microsoft Edge（最新版本）
- Microsoft Internet Explorer 11
- Safari（最新版本，仅限 Mac）
- Chrome（最新版本）
- Firefox（最新版本）

### <a name="intune-classic-portal"></a>Intune 经典门户

Intune 经典功能（例如 Intune 电脑软件客户端和与 Mobile Threat Defense 合作伙伴的集成）仅适用于 Intune 经典门户 (https://manage.microsoft.com)。 Intune 经典门户需要 Silverlight 浏览器支持。

以下 Silverlight 浏览器支持 Intune 控制台：
- Internet Explorer 10 或更高版本
- Google Chrome（42 版之前的版本）
- 启用了 Silverlight 的 Mozilla Firefox [了解详细信息](https://go.microsoft.com/fwlink/?linkid=836872)

> [!Note]
> Intune 经典门户不支持 Microsoft Edge 浏览器和移动浏览器，因为这些浏览器不支持 [Microsoft Silverlight](https://msdn.microsoft.com/library/cc838158(v=vs.95).aspx)。

只有拥有服务管理员权限或者身份是具有全局管理员角色的租户管理员的用户才能登录到此门户。 要访问管理控制台，你的帐户必须具有使用 Intune 的许可证，并且登录状态为“已允许”。
