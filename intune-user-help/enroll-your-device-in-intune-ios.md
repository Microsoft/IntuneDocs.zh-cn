---
title: 设置 iOS 设备对公司资源的访问 | Microsoft Docs
description: 介绍如何获取 Intune 管理的 iOS 设备
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 50fc19410b280e984c8dc3abe620baad7c3267de
ms.sourcegitcommit: 604b29c480b24270b5debc3e5f3141c8149ee6ed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2018
ms.locfileid: "49959530"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>设置 iOS 设备对公司资源的访问

通过 Intune 公司门户应用注册 iOS 设备，以便获取对组织的电子邮件、文件和应用的安全访问权限。

必须先托管企业或个人设备，随后才能从该设备访问专有数据。 托管设备完成后，组织将通过移动设备管理 (MDM) 提供程序为该设备分配策略和应用。 

若要持续拥有从设备访问工作或学校信息的权限，必须配置设备以匹配组织的首选设置。 本文介绍公司门户如歌帮助注册、配置和维护设备，以满足这些需求。

> [!NOTE]
> 如果想要在邮件应用中访问公司电子邮件，但收到托管设备的提示，那么通过本文你将了解如何解决该问题。 按照下面的说明，获取对 iOS 设备上的电子邮件和其他公司资源的访问权限。

## <a name="what-to-expect-from-the-company-portal-app"></a>公司门户应用的作用

### <a name="security"></a>安全
初始设置期间，应用要求你向组织验证自己的身份。 然后，它将告知你必须更新的所有设备设置。 例如，组织通常会设置密码的最小或最大字符数要求，必须满足此要求。    

### <a name="protection"></a>保护
注册设备后，公司门户应用将继续确保设备受到保护。 例如，如果安装的应用来自于不受信任的源，应用将发出警报，且有时会撤销对公司数据的访问权限。 与此类似的应用保护策略在组织中很常见。 它们通常要求先卸载不受信任的应用，然后才能重新获得访问权限。

### <a name="setting-notifications"></a>设置通知
如果注册后组织强制使用新的安全要求（如多重身份验证），公司门户应用将对此作出通知。 可调整设置，以便可以继续通过该设备开展工作。  

要了解有关注册的详细信息，请参阅[安装公司门户应用并注册设备后会发生什么情况？](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios)。 

## <a name="before-you-start"></a>开始之前

- 请确保在注册开始后完成整个过程。 如果暂停超过几分钟时间，安装可能结束，并且需要重新开始。  
- 如果该过程失败，请返回到公司门户应用并重试。  
- 请检查 Wi-Fi 是否正常及设备上的 Safari 是否运行正常。
- 下载并安装 [Intune 公司门户应用](install-and-sign-in-to-the-intune-company-portal-app-ios.md)。  


## <a name="using-the-company-portal-app-to-set-up-access-to-company-resources"></a>使用公司门户应用程序设置对公司资源的访问

|您看到的内容|说明|
|---|---|
|![公司门户登录屏幕，底部有“登录”按钮。](./media/ios-01-cp-enroll-1802.PNG)|打开公司门户应用程序并点击“登录”。|
|![Azure AD 登录提示符。](./media/ios-02-cp-enroll-1802.PNG)|输入公司电子邮件地址，然后点击“下一步”。|
|![Azure AD 密码提示符。](./media/ios-03-cp-enroll-1802.PNG)|输入你的密码，然后点击“登录”。|
|![正在加载公司资源初始屏幕。](./media/ios-04-cp-enroll-1802.PNG)|等待此屏幕加载完成。|
|![条款和条件页。](./media/ios-05-cp-enroll-1802.PNG)|阅读并接受所有条款和条件。|
|![设置公司访问屏幕。 当前，管理和设置都需要解决方案。](./media/ios-06-cp-enroll-1802.PNG)|点击“开始”以开始执行使你的设备能够访问公司资源的过程。 如果现在无法执行这一过程，可以“推迟”此过程，但这也意味着将无法获取电子邮件、文档等资源。|
|![“我的公司可以看到什么信息”屏幕。](./media/ios-07-cp-enroll-1802.PNG)|通过点击底部的链接，可以详细了解你的公司可以看到的信息。 否则，点击“继续”。|
|![“下一步是什么”屏幕。](./media/ios-08-cp-enroll-1802.PNG)|此屏幕介绍安装中的操作。 将用到 Safari、设置应用和公司门户应用。 点击“继续”。|
|![在点击“下一步是什么”上的“下一步”后加载屏幕。](./media/ios-09-cp-enroll-1802.PNG)|等待此屏幕加载完成。|
|![切换到 Safari 进行注册。](./media/ios-cp-sent-to-safari-1808.png)|你将被转到 Safari 以获取设备的管理信息。|
|![系统提示打开设置应用。](./media/ios-8-cp-enroll-1711.PNG)|点击“允许”打开设置应用，下载配置的配置文件。 安装该文件，让公司管理你设备上的公司信息。|
|![设备设置中“安装配置文件”屏幕的屏幕截图。](./media/ios-9-cp-enroll-1711.PNG)|点击“安装”。|
|![安装屏幕底部的配置文件模式对话框。](./media/ios-10-cp-enroll-1711.PNG)|点击“安装”。|
|![配置文件正在安装加载屏幕。](./media/ios-11-cp-enroll-1711.PNG)|等待此屏幕加载完成。|
|![配置文件管理警告屏幕。](./media/ios-12-cp-enroll-1711.PNG)|该警告由 Apple 编写，可让你详细了解可以对受管理的设备执行什么类型的操作。 详细了解[你的公司可以看到什么信息](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)。|
|![系统提示询问是否信任远程管理。](./media/ios-13-cp-enroll-1711.PNG)|点击“信任”允许公司管理你设备上的公司信息和设置。|
|![配置文件完成安装加载屏幕。](./media/ios-14-cp-enroll-1711.PNG)|等待此屏幕加载完成。|
|![配置文件已安装屏幕。](./media/ios-15-cp-enroll-1711.PNG)|配置文件已安装，即将对你设备上的公司信息和设置进行管理。|
|![切换到 Safari 进行注册。](./media/ios-16-cp-enroll-1711.PNG)|将返回到 Safari 以完成获取你设备上的管理信息的过程。 |
|![系统提示打开公司门户。](./media/ios-17-cp-enroll-1711.PNG)|点击“打开”。|
|![正在加载公司资源屏幕。](./media/ios-21-cp-enroll-1802.PNG)|等待此屏幕加载完成。|
|![选择公司门户应用中的设备类别。](./media/ios-22-cp-enroll-1802.PNG)|为你的设备选择最适合的类别。 这通常与拥有设备的用户以及该设备大部分时间所在的位置有关。|
|![已选择类别。](./media/ios-23-cp-enroll-1802.PNG)||
|![设备管理成功，现在需要更新设置。](./media/ios-24-cp-enroll-1802.PNG)|你已成功管理你的设备。 公司可能还需要你更新一些其他设置，例如，密码长度。 点击“继续”以继续。|
|![确认设备设置。](./media/ios-25-cp-enroll-1802.PNG)|公司门户将检查是否需要更新任何设置。|
|![设置检查已完成，具有错误的 OS 版本](./media/ios-26-cp-enroll-1802.PNG)|公司门户将提供如何能够修复设置中存在的任何问题的说明。 修复完成后，点击“检查设置”。|
|![确认设备设置加载屏幕](./media/ios-27-cp-enroll-1802.PNG)|你的设备将检查你的设置是否能够足够安全地访问公司资源。|
|![已成功注册和更新设置](./media/ios-28-cp-enroll-1802.PNG)|祝贺你！ 你的设备现已在 Intune 中注册。|

> [!Note]
> 在完全实现设备管理前，还需完成几个步骤。 了解关于[使用电信费用管理注册设备](enroll-your-device-with-telecom-expense-management-ios.md)的详细信息。 如果组织正在使用 Apple 的设备注册计划，请在[此处](enroll-your-device-dep-ios.md)了解详细信息。

仍需帮助？ 请与公司支持人员联系。 可以在[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)中查找他们的联系信息。  
