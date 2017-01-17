---
title: "先决条件 | Microsoft Docs"
description: "指向 Intune 先决条件和要求的链接"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/19/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: angrobe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e13a9c426e07ebb2443bd403d1a5c7274afd387e
ms.openlocfilehash: d07c7e667dbb5c01a9dcd8b2f69e7d930c27f25a


---

# <a name="prerequisites-to-getting-started-with-intune"></a>开始使用 Intune 的先决条件

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

开始设置 Microsoft Intune 之前，请查看以下要求：

- [支持的设备和计算机](#intune-supported-devices)
- [支持 Intune 的 Web 浏览器列表](#intune-supported-web-browsers)

还应熟悉 [Intune 网络带宽使用限制](network-bandwidth-use.md)。

## <a name="intune-supported-devices"></a>支持 Intune 的设备

使用 Intune 移动设备管理，可管理以下设备：

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

Intune 不能用于管理 Windows Server 操作系统。

Intune 设备管理提供[这些功能](mobile-device-management-capabilities-in-microsoft-intune.md)。

### <a name="windows-pc-software-client"></a>Windows 电脑软件客户端

作为一种备用注册方法，可在 Windows 电脑上部署和安装 [Intune 软件客户端](/intune/deploy-use/manage-windows-pcs-with-microsoft-intune)。 可使用 Intune 软件客户端管理 Windows 7 和更高版本的电脑，Windows 10 家庭版除外。 使用可提供[这些功能](windows-pc-management-capabilities-in-microsoft-intune.md)的客户端软件管理电脑。

### <a name="exchange-activesync-management"></a>Exchange ActiveSync 管理

可通过 Intune 控制台管理 [Exchange ActiveSync 设备](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune)。 与其他方法相比，该选项提供有限的一组管理功能。 有关支持的设备的列表，请参阅 [Office 365 中内置移动设备管理的功能](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0)。

## <a name="intune-supported-web-browsers"></a>受 Intune 支持的 Web 浏览器

不同的管理任务要求使用以下管理网站之一。

- [Office 365 门户](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Microsoft Intune 管理员控制台](https://admin.manage.microsoft.com/)

|Intune 功能 |支持的浏览器|
|---------|---------|
|**Intune 管理控制台**     |  Internet Explorer 10 或更高版本<br /><br />Google Chrome（42 版之前的版本）<br /><br />启用了 Silverlight 的 Mozilla Firefox<br />**注意：**自 2017 年 3 月起，Mozilla 将不再支持 Silverlight。 [了解详细信息](https://go.microsoft.com/fwlink/?linkid=836872)。 |
|**Office 365 管理门户**     |所有浏览器，包括移动浏览器和托管浏览器  |
|**公司门户网站**     |**在移动设备上：**使用每个受支持平台的默认 Web 浏览器   <br /><br />**在 Windows 电脑上：**使用 Internet Explorer 10 或更高版本，或 Microsoft Edge<br /><br />**在 Mac OS X 10.9 或更高版操作系统的计算机上：**使用 Apple Safari    |

> [!Note]
> 管理控制台不支持 Microsoft Edge 浏览器和移动浏览器，因为它们不支持 [Microsoft Silverlight](https://msdn.microsoft.com/en-us/library/cc838158(v=vs.95).aspx)。 Intune 控制台会在一段时间内脱离 Silverlight 体验；最终，所有 Intune 的移动设备和应用程序管理功能将[提供在新的 Microsoft Azure 门户中](https://blogs.technet.microsoft.com/enterprisemobility/2015/11/17/enhancing-managed-mobile-productivity/)。


只有拥有服务管理员权限或者身份是具有全局管理员角色的租户管理员的用户才能登录到此门户。 要访问管理控制台，你的帐户必须具有使用 Intune 的许可证，并且登录状态为“已允许”。

>[!div class="step-by-step"]

>[**网络**&rarr;](network-bandwidth-use.md)  



<!--HONumber=Dec16_HO3-->


