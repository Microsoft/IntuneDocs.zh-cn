---
title: "早期版本 | Microsoft Docs"
description: 
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 249a902e6e10f799dcff4e1c46da90cd62f2c125
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="the-early-edition-for-microsoft-intune---may-2017"></a>Microsoft Intune 的早期版本 - 2017 年 5 月

**早期版本**提供了一份即将发布的 Microsoft Intune 版本中将出现的功能的列表。 此信息在非常有限的情况下依据保密协议 (NDA) 提供，并不断变化。 此处列出的某些功能有无法按期发布的风险并可能推迟到以后的版本。 正在以试验模式（外部测试）测试其他功能，以确保它们可立即供客户使用。 如果有任何问题或顾虑，请联系 Intune/PM 好友。

本页将定期更新。 返回查看其他更新。

> [!Note]
> 下面的更改依据 Intune 开发。 所有这些功能最终将支持混合客户部署（带 Intune 的 Configuration Manager）。 有关新的混合功能的详细信息，请查看[混合新增功能页](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。

## <a name="new-capabilities"></a>新功能

### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>从适用于 iOS 的企业门户到 Outlook for iOS 的单一登录支持 <!--834012-->

如果用户在同一设备上使用同一帐户登录到适用于 iOS 的公司门户应用，则将不再需要登录 Outlook 应用。 用户启动 Outlook 应用时，他们将能够选择自己的帐户并自动登录。 我们也正在致力于为其他 Microsoft 应用添加此功能。

### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Samsung KNOX 启动 PIN 改进通知 <!--1087143-->

最终用户需要在 Samsung KNOX 设备上设置启动 PIN 以符合加密时，最终用户点击向他们显示的通知后，此通知会将其转到“设置”应用中的确切位置。  以前，该通知会将最终用户转到密码更改屏幕。

### <a name="promoting-the-most-current-version-of-the-company-portal-for-android---1098661--"></a>提示安装面向 Android 的公司门户的最新版本 <!--1098661-->

当应用的“通知”屏幕中已发布面向 Android 的公司门户应用的新推荐版本时，最终用户将看到应用内通知。 该通知将告诉用户某个“公司门户更新可用”。 点击此通知将打开一个网页，并显示可以从其中下载更新版本的可用应用商店列表。 

### <a name="improvements-to-app-syncing-with-windows-10-creators-update----676505---"></a>与 Windows 10 创意者更新的应用同步改进 <!-- 676505 -->

面向 Windows 10 的公司门户将自动启动与 Windows 10 创意者更新 (1704) 的设备应用安装请求同步。 这将减少“正在挂起同步”状态下的应用安装停止问题。 此外，用户将可以从该应用内部手动启动同步。 

面向 Windows 10 的公司门户还将公开一个刷新按钮，用户可以通过它在必要时刷新应用中的内容。 

## <a name="notices"></a>通知

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 将要求更新应用传输安全<!--748318-->

自 2017 年春季开始，Apple 宣布他们将强制对应用程序传输安全 (ATS) 实施特定要求。 使用 ATS 对所有通过 HTTPS 的应用通信实施更严格的安全措施。 此更改会影响使用 iOS 公司门户应用的 Intune 客户。 请查看 [Intune 支持博客](https://aka.ms/compportalats)，了解更多详细信息。

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接访问 Apple 注册方案<!--951869-->

对于在 2017 年 1 月之后创建的 Intune 帐户，Intune 支持在 Azure 预览门户中使用注册设备工作负荷直接访问 Apple 注册方案。 以前，仅能通过经典 Intune 门户中的链接访问 Apple 注册预览版。 2017 年 1 月之前创建的 Intune 帐户需要进行一次性迁移，然后才能使用 Azure 中的这些功能。 迁移的计划目前尚未公布，但详细信息将尽快发布。 强烈建议创建一个试用帐户，在现有帐户无法访问预览版时测试新体验。

### <a name="whats-coming-for-appx-in-intune-on-azure----1000270---"></a>Azure 上 Intune 的 Appx 的新增功能 <!-- 1000270 -->

在迁移到 Azure 上的 Intune 的过程中，我们做出了 3 个 appx 更改：

1. 在仅能部署到 MDM 注册的设备的经典 Intune 控制台中添加新的 appx 应用类型。
2. 重用现有的 appx 应用类型，以仅面向通过 Intune PC 代理托管的 PC。
3. 通过迁移将所有现有的 appxs 转换为 MDM appx。

这不会影响通过 Intune PC 代理管理的设备的任何现有部署。 但是，迁移后将无法将这些已迁移的 appx 部署到由先前未面向的 Intune PC 代理托管的任何新设备。

迁移后，如果要进行新的 PC 部署，则需要将 appx 作为电脑 appx 再次上传。 若要了解详细信息，请参阅 [Intune 支持团队博客上的 ](https://aka.ms/appxchange)Azure 上 Intune 中的 Appx 更改。  


## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Azure 上新的 Intune 管理体验公开预览版<!--736542-->

在 2017 年初，我们会将完整管理体验迁移到 Azure 上，以便能够在可使用图形 API 进行扩展的新式服务平台上对核心 EMS 工作流进行强大且集成的管理。

新的试用租户将于本月开始在 Azure 门户中看到新管理体验的公开预览版。 在预览状态下，将以迭代方式交付现有 Intune 控制台的功能和奇偶校验。

Azure 门户中的管理体验将使用已公布的新分组和定向功能；当现有租户迁移到新的分组体验时，也会将你迁移，以预览租户上的新管理体验。 在此期间，如果想要在租户迁移之前测试或查看任何新功能，请注册新的 Intune 试用帐户或查阅[新文档](https://docs.microsoft.com/intune/what-is-intune)。

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>支持 Android 应用的托管配置选项 <!-- 621621 -->

将可以配置 Play Store 中支持托管配置选项的 Android 应用。  通过此功能，你 可查看应用支持的配置值列表，并提供优质的引导式 UI，以便配置这些值。

### <a name="remote-assistance-for-android-devices----675418---"></a>Android 设备的远程协助 <!-- 675418 -->

Intune 将使用 [TeamViewer](https://www.teamviewer.com) 软件（单独购买）使运行 Android 设备的用户获得远程协助。

### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>预配置 Android for Work 应用的设备权限 <!-- 621614 -->

对于已部署到 Android for Work 设备工作配置文件的应用，你将可以配置单个应用的权限状态。 默认情况下，要求位置或设备摄像头访问权限等设备权限的 Android 应用将提示用户接受或拒绝权限。  例如，如果应用要使用设备的麦克风，则将提示最终用户授予该应用使用麦克风的权限。 可以通过此功能代表最终用户定义权限。  管理员可以配置权限，以

- 无需通知用户即自动拒绝
- 无需通知用户即自动批准
- 提示用户接受或拒绝。

### <a name="define-app-specific-pin-for-android-for-work-devices---728976--"></a>为 Android for Work 设备定义特定于应用的 PIN <!--728976-->

你将可以定义密码策略，其仅适用于托管为 Android for Work 设备的 Android 7.0 及更高版本设备的工作配置文件中的应用。  选项包括：

- 定义仅设备范围的密码策略 - 这是最终用户解锁整个设备时必须使用的密码
- 仅定义工作配置文件密码策略 - 只要打开工作配置文件中的任何应用，均提示最终用户输入密码。
- 同时定义设备和工作配置文件策略 - IT 人员可以选择同时以不同的长度定义设备密码策略和工作配置文件密码策略（例如使用 4 位数的 PIN 来解锁设备，而使用 6 位数的 PIN 来打开任意工作应用）

>[!NOTE]
> 此选项仅适用于 Android 7.0 及更高版本。  默认情况下，最终用户将可以选择使用两个单独定义的 PIN 或者他们可以选择将两个已定义的 PIN 合并为二者中较强大的一个 PIN。

### <a name="manage-password-and-other-android-for-work-settings---1102534--"></a>管理密码和其他 Android for Work 设置 <!--1102534-->

我们将添加一个新的 Android for Work 设备限制策略，可让你在 Android for Work 设备上管理密码和工作配置文件设置。

###  <a name="new-web-content-filter-policy-for-ios-devices----723832---"></a>适用于 iOS 设备的新 Web 内容筛选器策略 <!-- 723832 -->

你将可以使用以下两种方法之一控制 iOS 设备的用户可以访问的网站：

  - 使用 Apple 内置的 Web 内容筛选器添加允许和阻止的 URL。
  - 只允许 Safari 浏览器访问指定的网站。 将在 Safari 中为你指定的每个站点创建书签。

### <a name="apple-school-manager-asm-support---748864--"></a>Apple School Manager (ASM) 支持<!--748864-->

Intune 将支持使用 Apple School Manager (ASM) 来替换 Apple 设备注册计划，从而提供 iOS 设备开箱注册体验。 需要执行 ASM 载入才能将 Classroom 应用用于共享 iPad，并且需要执行此操作才会允许通过 Microsoft 学校数据同步 (SDS) 将数据从 ASM 同步到 Azure Active Directory。  

### <a name="shared-ipad-support---770395-1044681---"></a>共享 iPad 支持 <!--770395, 1044681 -->

Intune 将支持在 Apple 的设备注册计划或 Apple School Manager 的注册配置文件中配置共享 iPad 模式。 此设置将允许多个托管的 Apple ID 登录到同一个设备。

我们还将扩展对管理 iOS Classroom 应用的支持，以便为使用托管 Apple ID 登录共享 iPad 的学生提供支持。

### <a name="new-windows-device-restriction-settings---978585--"></a>新 Windows 设备限制设置 <!--978585-->

我们将向 Windows 设备限制配置文件添加控制无线显示、设备发现、任务切换和 SIM 卡错误消息等功能的设置。

### <a name="office-365-proplus-app-available-for-windows-10-devices---1121362--"></a>适用于 Windows 10 设备的 Office 365 ProPlus 应用 <!--1121362-->

我们将添加可以让你轻松地将 Office 365 ProPlus 应用分配到 Windows 10 设备的新 Office 365 ProPlus 应用类型。 此外，如果你拥有 Microsoft Project 和 Microsoft Visio 的许可证，你还可以安装它们。 所需的应用将被捆绑在一起，并且将显示为 Intune 控制台的应用列表中的一个应用。

### <a name="new-allowblock-list-for-the-managed-browser---682960--"></a>Managed Browser 的新允许或阻止列表 <!--682960-->

你将可以使用 Azure 门户中的“Intune 应用程序配置”设置配置 Managed Browser 的域和 URL 的允许/阻止列表。 无论是在托管的还是未经托管的设备上使用它，都可以为 Managed Browser 配置此列表。

### <a name="new-app-configuration-capabilities----677969---"></a>新应用配置功能 <!-- 677969 -->

此功能将等效于移动设备管理 (MDM) 应用配置。 管理员可以通过它应用更多应用配置值，即通过没有注册渠道的 MAM 中的应用保护策略可用的应用配置值。

### <a name="new-app-protection-policies-conditions-for-mam---679864--"></a>MAM 的新应用保护策略条件 <!--679864-->

你将可以通过“管理控制台”为没有注册用户的 MAM 设置强制具备以下内容的要求：

- 最低应用程序版本
- 最低操作系统版本
- 目标应用程序的最低 Intune APP SDK 版本（仅 iOS）

此功能将同时适用于 Android 和 iOS。 Intune 支持对 OS 平台版本、应用程序版本和 Intune APP SDK 的最低版本强制要求。 在 iOS 上，已集成 SDK 的应用程序还可在 SDK 级别设置最低版本强制要求。

如果上述三种不同级别中均未满足应用保护策略中的最低要求，用户将无法访问目标应用程序。 此时，用户可以删除其帐户（对于多身份标识应用程序）、关闭应用程序和/或更新其 OS 或应用程序版本来满足此要求。

此外，你还将可以通过“管理控制台”配置其他设置来提供建议进行 OS 或应用程序升级的非阻止型通知。 可以关闭此通知，并且应用程序可供正常使用。

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>更改 MDM 颁发机构，而无需取消注册托管设备 <!--1103950-->

你将可以更改 MDM 颁发机构，而无需联系 Microsoft 支持部门，并且无需取消注册并重新注册现有的托管设备。 在“Configuration Manager”控制台中，可以通过“设置”将 MDM 颁发机构从“Configuration Manager (混合)”更改为“Microsoft Intune (独立)”，反之亦然。


### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new-in-microsoft-intune.md)。

