---
title: "Microsoft Intune 的发行说明 | Microsoft Docs"
description: "Intune 发行说明"
keywords: 
author: Staciebarker
ms.author: stabar
manager: angrobe
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: db9479b2-582d-4a1a-9fbc-fbfc6c680e6f
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: fd300a5dfe6d6976491988453ec69e99668889fb


---

# <a name="release-notes-for-microsoft-intune"></a>Microsoft Intune 的发行说明

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune 是基于云的综合性客户端管理解决方案，它向最新版本的 Windows 提供工具、报告和升级许可证。 它还有助于保持你的计算机使用最新程序且安全可靠。 此外，利用 Intune，你可以通过 Exchange ActiveSync 或直接通过 Intune 管理网络上的移动设备。 以下发行说明描述了 Microsoft Intune 中的重要信息和已知问题。


## <a name="android-users-cant-send-email-when-conditional-access-for-exchange-online-is-implemented"></a>当执行对 Exchange Online 的条件性访问时，Android 用户无法发送电子邮件

**问题：**设置了 Exchange Online 的条件访问时，在设备上运行 Samsung Android 5.1.1 及更改版本的用户无法发送电子邮件。 Samsung 承认其 Android 5.1.1 及更高版本的内置电子邮件客户端中存在此问题，且正在研究修复程序。

**解决方法 1：**建终用户使用适用于 Android 的 Outlook 应用。

**解决方法 2：**要让受影响用户能够发送电子邮件，可以遵循下列步骤：

1. 将受影响用户加入在 Exchange Online 条件访问策略的“免除组”部分中的安全组。
2. 允许用户在内置电子邮件客户端上临时同步电子邮件。
3. 将受影响用户从免除组中移出，并确认用户现在可以发送电子邮件。

Microsoft 将继续与 Samsung 紧密合作，共同研究出修复程序和其他解决方法。



## <a name="changing-resource-access-profiles-between-groups-for-ios-and-android-might-fail"></a>更改 iOS 和 Android 组之间的资源访问配置文件可能会失败
**问题：**更改组之间的电子邮件或简单证书注册协议 (SCEP) 资源访问配置文件时，配置文件可能会发生冲突且失败。 例如，假设你拥有一个指向本地 Exchange Server 并针对组 A 的现有电子邮件配置文件。然后创建了一个指向 Exchange Online 并针对组 B 的新电子邮件配置文件。当你将用户从组 A 移动到组 B 时，设备将保留该本地 Exchange 电子邮件配置文件并尝试安装针对组 B 的 Exchange Online 电子邮件配置文件。

此时，将发生以下一种情况： 
* 如果电子邮件配置文件 A 和 B 相同，则设备会拒绝电子邮件配置文件 B，因为它已经包含电子邮件配置文件 A。
* 如果电子邮件配置文件 A 和 B 不同，如示例中所述，设备最终会接受两个电子邮件配置文件。

> [!NOTE]
> 系统将检查主机名和用于用户名的属性，从而区分电子邮件配置文件。

在这两种情况下，为了防止无意删除用户对电子邮件的访问或客户端的 SCEP 证书，未从设备中删除资源访问配置文件（电子邮件配置文件）。

**解决方法：** 无。

## <a name="when-you-enroll-a-windows-81-device-that-must-authenticate-to-a-proxy-server-the-enrollment-process-fails-with-no-visible-cause"></a>在注册必须向代理服务器进行身份验证的 Windows 8.1 设备时，注册进程将失败，并且没有明显原因
**问题：** 当你注册 Windows 8.1 设备时，如果在注册过程中设备必须向代理服务器进行身份验证，但设备尚未缓存代理服务器凭据，则注册将失败。 如果设备上未缓存代理服务器的凭据，则注册进程必须等待用户输入凭据。 但是，在注册进程期间不会提示你提供代理服务器凭据。 结果是注册进程无法向代理服务器进行身份验证。 不会向用户呈现此失败的明显指示。

**解决方法：**对于必须在需要使用已验证代理服务器的网络上注册的 Windows 8.1 设备，在注册设备之前，请为代理服务器设置并保存凭据。 在 Windows 8.1 设备上设置和保存凭据：

1.  在 Windows 8.1 设备上，打开 Internet Explorer。
2.  提示输入代理服务器凭据时，请输入凭据，然后选择“记住我的凭据”选项。
3.  注册该设备。

## <a name="windows-phone-81-devices-fail-to-enroll-with-microsoft-intune-when-device-authentication-is-enabled-in-ad-fs"></a>当在 AD FS 中启用设备身份验证时，Windows Phone 8.1 设备无法注册 Microsoft Intune。
**问题：**当你注册 Windows Phone 8.1 设备时，如果设备身份验证的可选设置作为 Active Directory 联合身份验证服务 (AD FS) 中的全局身份验证策略的一部分启用，则无法注册。

**解决方法：**在“编辑全局身份验证策略”中取消选中“启用设备身份验证”，以便在 AD FS 服务器上禁用设备身份验证。 有关详细信息，请参阅[配置身份验证策略](http://technet.microsoft.com/library/dn486781.aspx)。


## <a name="microsoft-intune-app-wrapping-tool-for-android-has-no-built-in-uninstall-capability"></a>适用于 Android 的 Microsoft Intune 应用包装工具没有内置卸载功能
**问题：****适用于 Android 的 Microsoft 应用包装工具**没有用于卸载该工具的内置功能。

**解决方法：** 浏览到安装工具的位置，并删除该目录。 默认安装位置为：**C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool**。 有关应用包装工具的详细信息，请参阅[使用应用包装工具准备管理 Android 应用](/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)。

## <a name="remote-assistance-is-not-available-on-computers-that-run-windows-8-or-windows-81"></a>远程协助在运行 Windows 8 或 Windows 8.1 的计算机上不可用
**问题：** 在此版本中，远程协助功能在运行 Windows 8 或 Windows 8.1 的计算机上不可用。

**解决方法：** 无。

## <a name="alert-notifications-for-recipients-that-are-automatically-added-might-not-work"></a>自动添加的接收者的警报通知可能无法工作
**问题：**如果将接收者自动添加到警报通知中，他们可能不一定会收到通知。

**解决方法：**若要确保接收者收到消息通知，应将接收者手动添加到警报通知中。

## <a name="language-support-in-the-azure-portal"></a>Azure 门户中的语言支持
Azure 门户支持以下这些语言：中文（简体）、中文（繁体）、捷克语、荷兰语、英语、德语、匈牙利语、意大利语、日语、葡萄牙语（巴西）、葡萄牙语（葡萄牙）、俄语、西班牙语、英语、法语、朝鲜语、波兰语、瑞典语和土耳其语。

Intune 管理控制台和面向用户的移动体验除了 Azure 门户中支持的所有语言外，还支持丹麦语、希腊语、芬兰语、挪威语和罗马尼亚语。



<!--HONumber=Dec16_HO2-->


