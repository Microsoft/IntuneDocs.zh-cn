---
title: "Exchange ActiveSync 策略设置"
description: "使用 Intune Exchange ActiveSync 策略来配置设置，这些设置可让你控制 Exchange ActiveSync 托管设备上的特性和功能。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9cbb826-b155-4df6-abf3-60c6f05b2783
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d2abab78eed4788baff71f7f5c690dc3d73b2098
ms.sourcegitcommit: cf7f7e7c9e9cde5b030cf5fae26a5e8f4d269b0d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2017
---
# <a name="exchange-activesync-policy-settings-in-microsoft-intune"></a>Microsoft Intune 中的 Exchange ActiveSync 策略设置

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

使用 Microsoft Intune“Exchange ActiveSync”策略配置设置，这些设置可控制 Exchange ActiveSync 托管设备上的一系列特性和功能。


## <a name="password-settings"></a>密码设置

|设置名|详细信息
|----------------|---|
|**需要密码才可解锁移动设备**|指定是否必须使用密码锁定设备。<br>（不适用于运行 Windows RT 的设备）。|
|**所需的密码类型**|指定需要的密码类型，例如仅限数字或字母数字。|
|**最短密码长度**|指定设备密码中所需的最少字符数。|
|**允许简单密码**|指定是否可以使用简单密码（包括 "0000" 和 "1234"）。|
|**擦除设备前允许的重复登录失败次数**|指定在擦除设备之前用户可以输入不正确密码的次数。|
|**密码过期（天数）**|指定必须更改设备密码前的天数。
|**记住密码历史记录**|指定是否允许用户使用以前用过的密码。|
|**“记住密码历史记录”** – **“防止重用以前的密码”**|指定不能重复使用的以前所用密码的数量。|
|**需要提供密码之前处于非活动状态的分钟数**|指定锁定屏幕之前，设备必须保持空闲的时间量。

## <a name="encryption-settings"></a>加密设置

|设置名|详细信息|
|----------------|---|
|**需要对移动设备加密**<sup>1</sup>|需要对设备上的数据进行加密（受支持时）。<br><br>对于 Windows Phone 8 设备，必须将其设置为 **“是”**。<br /><br />若要在 iOS 设备上启用加密，请启用设置“需要密码以解锁移动设备”。|
|**需要对存储卡进行加密**|需要对存储在外部存储（如 SD 卡）上的数据进行加密（在支持的设备上）。
<sup>1</sup>运行 Windows 8.1 的设备的其他信息

-   若要在运行 Windows 8.1 的设备上强制加密，必须在每台设备上安装 [用于 Windows 的 December 2014 MDM 客户端更新](https://support.microsoft.com/kb/3013816)。

-   如果对 Windows 8.1 设备启用此设置，则该设备的所有用户必须都具有 Microsoft 帐户。

-   若要使 Windows 8.1 设备的加密正常工作，该设备必须满足 Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) 硬件认证要求。

-   在 Windows 8.1 设备上强制加密时，恢复密钥仅可从用户的 Microsoft 帐户（从用户的 OneDrive 帐户访问）进行访问。 无法代表用户恢复此密钥。

## <a name="email-settings"></a>电子邮件设置

|设置名|详细信息
|----------------|---|
|**允许用户下载电子邮件附件**|指定是否可以将电子邮件附件下载到设备。|
|**电子邮件同步时间段**|指定将同步到设备的已接收电子邮件的天数。
|**允许不完全支持 Exchange ActiveSync 设置的移动设备使用 Exchange 进行同步**|指定是否在不支持一个或多个 Exchange ActiveSync 设置的设备上允许仅当 Exchange 访问。

## <a name="browser-settings"></a>浏览器设置

|设置名|详细信息
|----------------|---|
|**允许 Web 浏览器**|指定是否可以使用设备上的 Web 浏览器。<br>（不可用于 Windows RT 或 Windows Phone）。

## <a name="hardware-settings"></a>硬件设置

|设置名|详细信息
|----------------|---|
|**允许照相机**|指定是否可以使用设备上的照相机。<br>（不可用于 Windows RT 或 Windows Phone）。



### <a name="see-also"></a>另请参阅
[使用 Microsoft Intune 策略管理设备上的设置和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
