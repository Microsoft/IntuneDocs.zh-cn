---
title: "新增功能存档 | Microsoft Intune"
description: 
keywords: 
author: Lindavr
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: 051d06afb0f29f2a97c1f06dc1102138e5f2be8f


---


## 2015 年 9 月
### 移动设备和应用管理更新
**所有 Intune iOS 管理功能现在均支持 iOS 9**有关 iOS 9 管理功能的详细信息，请参阅[此博客文章](http://blogs.technet.com/b/microsoftintune/archive/2015/09/09/day-zero-support-for-ios-9-with-intune.aspx)。

**适用于 iOS 的新移动应用配置策略**使用新的移动应用配置策略来自动提供 iOS 应用运行时可能需要的设置。 例如，你可以提供网络端口或用户名。 有关详细信息，请参阅[使用 Microsoft Intune 中的移动应用配置策略配置应用](https://technet.microsoft.com/library/mt481447.aspx)。

**为 iOS 9 用户简化应用管理**
在此版本中，你可以为 iOS 9 用户将已部署的应用交由 Intune 管理。 对于 iOS 的早期版本，在部署应用时，即使已在一个设备上安装了非托管版本的该应用，你仍须让用户手动卸载该应用后，Intune 才能安装托管应用。

 但从这个版本的 Intune 开始，你现在可以提示 iOS 9 设备的用户允许 Intune 接管该应用的管理并应用任何相关的移动应用程序管理策略。

 **Windows 10 管理** 使用新的 [Windows 10 常规配置策略](https://technet.microsoft.com/library/mt404697.aspx)为运行 Windows 10 和 Windows 10 移动版的已注册设备配置密码、设备、浏览器和其他设置。

 **创建应用并将其部署到已注册的 Windows 10 设备**新的软件安装程序类型，通过 MDM 的 Windows Installer (&#42;.msi)，允许你创建 Windows Installer 应用，并将其部署到运行 Windows 10 的已注册设备中。 有关详细信息，请参阅[开始在 Microsoft Intune 中部署应用](https://technet.microsoft.com/library/dn646955.aspx)。

### Microsoft 公司门户应用的更改和更新
此版本已针对公司门户应用进行了如下更改：

**iOS**
* Microsoft 会自动收集有关性能和公司门户使用情况的匿名数据以改进 Microsoft 产品和服务。 最终用户可以使用设备上的“数据使用情况”设置关闭数据收集，但管理员无法控制数据收集，并且无法更改最终用户对此设置的选择。
* iPhone 6 和 iPhone 6 Plus 上支持全屏分辨率
* 修复 bug 以提高安全性

### Intune 文档新增内容 — 2015 年 9 月
**新主题**

|Name|详细信息|
|----|--------|
|[Microsoft Intune 中的 Windows 10 配置策略设置](https://technet.microsoft.com/library/mt404697.aspx)|这是一个新的配置策略，允许你管理运行 Windows 10 和 Windows 10 移动版的设备上的设置和功能。
| [使用 Microsoft Intune 中的移动应用配置策略配置应用](https://technet.microsoft.com/library/mt481447.aspx)|这是一种新的策略类型，允许你自动提供用户运行 iOS 应用时可能需要的设置。 |

**更新的主题**

|Name|详细信息|
|----|-------|
|[通过 Microsoft Intune 使用策略来管理计算机和移动设备](https://technet.microsoft.com/library/dn743712.aspx)|已更新为包含帮助你了解和创建策略的最新信息。|

## 2015 年 8 月
### 移动设备和应用管理更新
* Intune 注册和公司访问的“条款和条件”[现在使用策略进行管理](https://technet.microsoft.com/library/mt405893.aspx)。 可以指定不同的条款和条件来满足特定用户组的要求。 例如，你可以将条款和条件以不同语言部署到按地理位置定义的用户组。 还可以 [编辑你的条款和条件](https://technet.microsoft.com/library/mt405893.aspx#BKMK_TCVers) 并指定是否递增版本号，这要求用户在使用公司门户前首先需同意新的条款和条件。
* “已重命名多个 Intune 策略” 以增强跨产品一致性和方便轻松查找。 有关所有可用的 Intune 策略列表，请参阅[通过 Microsoft Intune 使用策略来管理计算机和移动设备](https://technet.microsoft.com/library/dn743712.aspx)。
* “PKCS #12 (.PFX) 证书配置文件”可以用于 Android 4.0 或更高版本，以及 Windows 10（桌面版和移动版）和更高版本。 使用 .PFX 不需要 NDES 服务器。 在[通过 Microsoft Intune 使用证书配置文件启用对公司资源的访问](http://technet.microsoft.com/library/dn818904.aspx)中了解如何使用 .PFX 证书配置文件
* 如[通过 Microsoft Intune 使用 VPN 配置文件帮助用户连接到其工作](https://technet.microsoft.com/library/dn818905.aspx)中所述，**Windows 10 桌面版和移动版的企业边界设置**启用了粒度 VPN 设置
* **适用于 Android 的 OneDrive 应用现支持多身份**。 在 [可以管理的 Microsoft 应用程序列表](https://technet.microsoft.com/library/dn708489.aspx)中描述了对移动应用管理策略的此项和其他更新。
* **绕过 iOS 激活锁定**。 如果公司拥有的 iOS 设备受激活锁定保护，则必须先输入用户的 Apple ID 和密码，才能擦除或重新激活该设备。 当用户在不关闭激活锁定的情况下离开公司，然后返回使用公司拥有的设备时，则将面临一项巨大的挑战。 若要帮助解决此问题，可以使用 [Intune 绕过激活锁定](https://technet.microsoft.com/library/mt414176.aspx)

### PC 的条件性访问
现在，你可以配置 PC 的条件访问策略。 这将允许 Office 桌面应用访问 Exchange Online 和 SharePoint Online 服务。
若要启用 PC 的条件性访问策略，此 PC 必须已加入域或必须合规。
* 有关启用电脑的条件性访问的要求的完整列表，请参阅[使用 Microsoft Intune 管理对电子邮件和 SharePoint 的访问](http://technet.microsoft.com/library/dn818907).aspx) 中的**入门**部分。
* 请参阅[使用 Microsoft Intune 管理电子邮件访问](https://technet.microsoft.com/library/dn705841.aspx)，了解可设置为启用电子邮件访问的条件性访问的选项。
* 请参阅[使用 Microsoft Intune 管理 SharePoint Online 访问](https://technet.microsoft.com/library/dn705844.aspx)，了解可设置为启用 SharePoint Online 的条件性访问的选项。

### Microsoft 公司门户应用的更改和更新
此版本已针对公司门户应用进行了如下更改：

**Android**

如果用户尚未注册其设备以进行管理，则该用户现将在登录后看到设备注册说明。

### Intune 文档新增内容 - 2015 年 8 月
**新主题**

|标题|详细信息|
|-----|-------|
|[通过 Microsoft Intune 的绕过激活锁定帮助保护 iOS 设备](https://technet.microsoft.com/library/mt414176.aspx)|了解有关在用户离开公司并返还已锁定设备时如何使用 Intune 绕过 iOS 激活锁定的信息。|

**更新的主题**

|标题|详细信息|
|-----|-------|
|[可配合 Microsoft Intune 移动应用程序管理策略使用的 Microsoft 应用](https://technet.microsoft.com/library/dn708489.aspx)|更新了有关可使用移动应用程序管理策略管理的应用的最新信息。
|[通过 Microsoft Intune 使用策略来管理计算机和移动设备](http://technet.microsoft.com/library/dn743712.aspx)|更新了 Intune 新增的最新策略。|
<!---
## July 2015
July updates for Intune are limited to behind-the-scenes enhancements that allow us to continue providing you with a high-quality service experience. New features are not included in this service update.

### Intune Onboarding benefit
Microsoft offers the Intune Onboarding benefit for eligible plans. The Onboarding benefit lets you work remotely with Microsoft specialists to get your Intune environment ready for use. For more information, see [Microsoft Intune Onboarding benefit description](https://technet.microsoft.com/library/mt228266.aspx)
### Changes and updates to Microsoft Company Portal apps
The following changes have been made to the company portal apps in this release.

**Android**

Microsoft automatically collects anonymous data about the performance and use of the company portal to improve Microsoft products and services. End users can turn off data collection by using the Usage Data setting on their device, but administrators have no control over the data collection and cannot change the end user’s selection for this setting.--->



<!--HONumber=Jun16_HO4-->


