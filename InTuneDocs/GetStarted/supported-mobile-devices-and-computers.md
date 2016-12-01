---
title: "支持的移动设备和浏览器 | Microsoft Intune"
description: "Intune 支持的移动设备和计算机"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: aeeccfa4-0f14-447e-a3df-c8435c8a4bb2
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 149f3a3310907d131affeaad4bd372aa60be9206
ms.openlocfilehash: 80541567c535cfeb7fca3eda3c9143f4b11d7abb


---

# <a name="supported-mobile-devices-and-computers"></a>支持的移动设备和计算机

可注册并管理以下设备类型：

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

注册设备后可使用[这些功能](/Intune/get-started/choose-how-to-manage-devices)。

或者，可以使用 Intune 电脑客户端软件管理 Windows 电脑。 Intune 电脑客户端软件支持 Windows 7 及更高版本，Windows 10 家庭版除外。 使用可提供[这些功能](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune)的客户端软件管理电脑。

拥有企业管理套件的客户还可以使用 Azure Active Directory (Azure AD) 注册 Windows 10 设备。

## <a name="microsoft-intune-supported-web-browsers"></a>Microsoft Intune 支持的 Web 浏览器

不同的管理任务要求你使用以下管理网站之一。

- [Office 365 门户](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Microsoft Intune 管理员控制台](https://admin.manage.microsoft.com/)

> [!Note]
> 管理控制台不支持 Microsoft Edge 浏览器和移动浏览器，因为它们不支持 [Microsoft Silverlight](https://msdn.microsoft.com/en-us/library/cc838158(v=vs.95).aspx)。 Intune 控制台会在一段时间内脱离 Silverlight 体验；最终，所有 Intune 的移动设备和应用程序管理功能将[提供在新的 Microsoft Azure 门户中](https://blogs.technet.microsoft.com/enterprisemobility/2015/11/17/enhancing-managed-mobile-productivity/)。

|Intune 功能 |支持的浏览器|
|---------|---------|
|Intune 管理控制台     |  Internet Explorer 10 或更高版本<br /><br />Google Chrome（42 版之前的版本）<br /><br />启用了 Silverlight 的 Mozilla Firefox<br /><br />**注意：**管理控制台不支持 Microsoft Edge 和移动浏览器。                      
|Office 365 管理门户     |所有浏览器，包括移动浏览器和托管浏览器  |
|公司门户网站     |**在移动设备上：**使用每个受支持平台的默认 Web 浏览器   <br /><br />**在 Windows 电脑上：**使用 Internet Explorer 10 或更高版本，或 Microsoft Edge<br /><br />**在 Mac OS X 10.9 或更高版操作系统的计算机上：**使用 Apple Safari    |

> [!Note]
> 管理控制台不支持 Microsoft Edge 浏览器和移动浏览器，因为它们不支持 [Microsoft Silverlight](https://msdn.microsoft.com/en-us/library/cc838158(v=vs.95).aspx)。 Intune 控制台会在一段时间内脱离 Silverlight 体验；最终，所有 Intune 的移动设备和应用程序管理功能将[提供在新的 Microsoft Azure 门户中](https://blogs.technet.microsoft.com/enterprisemobility/2015/11/17/enhancing-managed-mobile-productivity/)。

### <a name="office-365-portalhttpgomicrosoftcomfwlinkplinkid698854"></a>[Office 365 门户](http://go.microsoft.com/fwlink/p/?LinkId=698854)

**作为租户管理员，请使用此门户来管理你的订阅**，包括下列任务（如果你的管理员角色允许）：

- 管理订阅的用户帐户，并配置从本地 Active Directory 进行的目录同步。
- 管理用户的组（称为安全组）。
- 将使用 Intune 的许可证分配给用户。
- 配置用于订阅的域名。 域名定义用户登录所使用的帐户。
- 管理订阅的帐单和采购详细信息，包括你拥有的许可证的数量，或者可使用的云存储空间量。
- 查找链接以查看 Intune 服务的运行状况。
- 作为租户管理员，你可以登录到 Office 365 门户来管理订阅（即使没有为你的帐户分配使用 Intune 的许可证）。
- 拥有 Intune 许可证但不是管理员的任何用户都可使用此门户重置其帐户密码和编辑其配置文件。
- 若要访问 Office 365 门户，帐户的登录状态必须为“已允许”。 此状态与拥有订阅许可证不同。 默认情况下，所有用户帐户均为“已允许”。


### <a name="microsoft-intune-administrator-consolehttpsmanagemicrosoftcom"></a>[Microsoft Intune 管理员控制台](https://manage.microsoft.com/)

**作为服务管理员，使用此门户来管理日常操作**，其中包括：

- 为计算机和移动设备设置策略。
- 上载和部署软件（如软件更新和应用）。
- 管理计算机上的 Endpoint Protection。
- 查看设备状态和运行报表。
- 登录到此门户。 你必须拥有服务管理员权限或者是具有全局管理员角色的租户管理员，才能登录到此门户。


只有拥有服务管理员权限或者身份是具有全局管理员角色的租户管理员的用户才能登录到此门户。 要访问管理控制台，你的帐户必须具有使用 Intune 的许可证，并且登录状态为“已允许”。



<!--HONumber=Nov16_HO4-->


