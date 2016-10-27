---
title: "新增功能存档 | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ec77bc20bf429c804cb502bb46fc549d080a94ac
ms.openlocfilehash: 14698e5f40e76e370e178aeb6187d89fbc5cb2bd


---
## 2016 年 9 月
## 新增功能、公告和信息
* [Windows 条件访问](#windows-conditional-access)
* [iOS 10 支持](#ios-10-support)
* [App Wrapping Tool 支持 MAM，且无需进行设备注册（针对 Android 和 iOS）](#app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios)
* [Intune 组将于 9 月过渡到 Azure Active Directory](#intune-groups-begin-transitioning-to-azure-active-directory-in-september)
* [集成 Lookout 以保护 Android 设备](#lookout-integration-to-protect-android-devices)
* [Android、iOS 和 Windows 公司门户更新](#company-portal-updates)
* [Intune 术语表](#intune-glossary)
* [即将推出](#whats-coming)

## Windows 条件访问
现在可通过 Intune 管理控制台创建条件访问策略，阻止 Windows 电脑访问 Exchange Online 和 SharePoint Oline。 还可以创建条件访问策略，阻止访问 Office 桌面和通用应用程序。

## iOS 10 支持
现有的 Intune MDM 和 MAM 方案与 iOS 10 兼容。 有关提示，请参阅 [Intune Support Team Blog](https://blogs.technet.microsoft.com/intunesupport/2016/09/13/support-tip-intune-support-for-ios-10/)（Intune 支持团队博客）。

## App Wrapping Tool 支持 MAM，且无需进行设备注册（针对 Android 和 iOS）
Intune App Wrapping Tool 是一种命令行工具，用于在适用于 iOS 和 Android 的业务线 (LOB) 应用上启用 Intune MAM。 借助该工具，能够以最简单的方法将 Intune MAM SDK 整合到应用中，以便应用可执行通过 Intune 部署的 MAM 策略。 使用 MAM 策略，可以：

1. 加密应用数据。
2. 要求信息工作者在启动应用时输入 PIN。
3. 允许应用仅将数据传输到其他托管应用。
4. 防止应用将数据备份到 Android、iTunes 和 iCloud。
5. 仅允许剪切、复制和粘贴到其他托管应用，以及剪切、复制和粘贴自其他托管应用。

已更新的 Intune App Wrapping Tool 的公共预览版现支持 MAM，且无需在 Android 和 iOS 上对内部 LOB 应用进行设备注册。 这意味着最终用户不需要让其设备注册 Intune，便可使用启用了 MAM 的 LOB 应用。

任何人都可以测试该公共预览版软件，并参阅帮助文档，该文档位于 msintuneappsdk 的 GitHub：

http://www.github.com/msintuneappsdk/intune-app-wrapper-ios-preview

http://www.github.com/msintuneappsdk/intune-app-wrapper-android-preview

安装和使用适用于 Android 和 iOS 预发行版的 Microsoft Intune 应用包装之前，必须：

* 查看适用于 Android 和 iOS 预发行版的 Microsoft Intune App Wrapping Tool 的 Microsoft 许可条款
* 打印并保留一份许可条款，以留作记录。 下载和使用适用于 Android 预发行版的 Microsoft Intune App Wrapping Tool 表示你同意这些许可条款。 如果不接受这些条款，请不要使用此软件。
<!---TFS 1235607--->

## Intune 组将于 9 月过渡到 Azure Active Directory
某些新的 Intune 帐户将使用 Azure Active Directory 安全组，而不是 Intune 用户组。 你将知道自己使用的是安全组，因为 Intune 门户组页上会有一个定向到 Azure 管理门户的链接。

## 集成 Lookout 以保护 Android 设备
Microsoft 将与 Lookout 的移动威胁防护解决方案集成，以通过检测设备上的恶意软件、危险应用等来保护 Android 移动设备。 Lookout 的解决方案有助于确定威胁级别，可对该功能进行配置。 可以在 Intune 中创建合规性策略规则，以根据 Lookout 的风险评估来确定设备合规性。 使用条件访问策略，你可以基于设备合规性状态允许或阻止访问公司资源。

将提示非合规性设备的最终用户进行注册，并要求其在 Android 设备上安装 Lookout for Work 应用程序，激活该应用并修正 Lookout for Work 应用程序中报告的威胁，以便获得访问权限。 若要了解详细信息，请参阅[根据设备、网络和应用程序风险限制访问权限](restrict-access-based-on-device-network-app-risk.md)。


## 公司门户更新

### Android

**向 Android 公司门户添加“通知”**<br/>
已将新的“通知”图标添加到 Android 公司门户的主页上。 点击此图标将访问“通知”页，该页将向你的最终用户显示在公司门户应用中需要注意的所有项，例如，设备非合规性、注册更新和注册激活。 iOS 公司门户应用已经有此通知体验。 拥有此新的“通知”页意味着，只要设备已注册，每次启动或恢复公司门户时，你将不会看到“公司访问设置”页。 如果你创建自己的最终用户指南，可能需要更新你的文档来反映此更改。 在[此处](https://aka.ms/androidcpupdate)查看更新的屏幕截图。  
<!---TFS 1095560--->

**在 Android 公司门户中提供反馈**</br>
已向 Android 公司门户菜单添加了新项。 点击“帮助和反馈”会显示三个操作：
* 使用“获取帮助” 向 IT 部门报告有关公司门户的问题。 IT 将使用电子邮件客户端创建电子邮件并在其中附加公司门户日志。 “获取帮助”替代了“设置”页上的“发送数据”功能。
* 使用“提供反馈”可向公司门户团队提供反馈。
* 使用“评价我们的应用”可在 Google Play 上留下对公司门户应用的评级或评价。

### iOS
**iOS 公司门户应用的支持更改**<br/>
现要求适用于 iOS 的 Microsoft Intune 公司门户应用的所有用户都使用最新版本。 新用户只能下载最新版本，而当前用户必须更新到最新版本。 最新版本需要 iOS 8.0 或更高版本，因此运行较旧的 iOS 版本的设备将无法使用公司门户或者进行注册，直到将其设备更新为 iOS 8.0 或更高版本，并且将公司门户应用更新到最新版本。 运行 iOS 8.0 以下版本的已注册设备将继续受管理，并将列在 Intune 管理员控制台中。
<!---TFS 1283165--->

**iOS 最终用户如何获取应用方面的改进**<br/>
在 iOS 的公司门户应用的应用磁贴中已进行了以下更改，从一个位置（公司门户网站中）即可将用户指向其所有应用的不同视图。 Apple 限制禁止业务线和托管应用商店应用列于公司门户应用中，并要求用户访问不同视图来查找自己所有的应用。

- “公司应用”磁贴之前指向公司门户网站“全部”选项卡中的所有应用的列表，此行为将继续以同种方式运作。 磁贴名称已更改为“全部应用”。
- “其他应用”磁贴之前指向公司门户应用内部的一个视图，其中列出了 Apple 允许公司门户应用显示的所有应用。 磁贴名称已更改为“特别推荐的应用”，点击该磁贴会将用户转到公司门户网站的“特别推荐”选项卡。
-  “类别”磁贴之前指向公司门户应用内部的一个视图，其中列出了应用类别。 磁贴名称未改变，但它现指向公司门户网站的“类别”选项卡。
你可以在[此处](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186)查看更新的屏幕截图。
<!---TFS 1317133--->

**如果 IT 专业人员为应用设置该要求，则提示安装 iOS 托管浏览器应用**<br/>
如果你已经将 Web Clip 配置为仅在托管的浏览器中打开，且托管浏览器未在设备上安装，则设备上的公司门户应用将提示用户安装托管浏览器后才能安装 Web Clip。
<!---TFS 1228570--->

### Windows
**添加到 Windows Phone 8.1 公司门户应用的反馈按钮**<br/>
Windows Phone 8.1 公司门户应用让最终用户能够通过使用新的“发送反馈”按钮发送有关应用的反馈。 要找到该按钮，用户需点击公司门户应用屏幕右下方的的“三个点”菜单，然后点击“发送反馈”。 收集的匿名信息反馈将帮助 Microsoft 改进用户的公司门户应用体验。
<!---TFS 1317806--->

## Intune 术语表</br>
我们在库中添加了一个新的[术语表主题](https://docs.microsoft.com/intune/understand-explore/intune-glossary)，帮助你了解 Intune 产品中使用的一些术语。



<!--HONumber=Oct16_HO2-->


