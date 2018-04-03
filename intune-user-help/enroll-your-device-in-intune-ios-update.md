---
title: "设置对公司资源的访问 | Microsoft Docs"
description: "介绍如何获取 Intune 管理的 iOS 设备"
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 02/20/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
searchScope:
- User help
ROBOTS: 
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 6474688a09c4063c55eff07f3cf84ebcb1911c65
ms.sourcegitcommit: eac89306d1391a6d3ae1179612b0820b19c2baa6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="set-up-access-to-your-company-resources"></a>设置对公司资源的访问

你的公司拥有大量专有信息：从电子邮件到文件、网络等。 从你的 iOS 设备访问信息时，公司使用 Microsoft Intune 帮助保护该信息。 这使公司能够在管理这些资源并使其更为安全的同时，使你能够自由地使用首选设备来完成工作。

> [!NOTE]
> 如果正在邮件应用中尝试访问公司电子邮件，很可能已收到提示，要求管理设备以确保其安全。 按照下面的说明，获取对 iOS 设备上的电子邮件和其他公司资源的访问权限。

## <a name="before-you-start"></a>开始之前

- 请确保在启动后完成整个过程。 暂停超过几分钟后，该过程通常会停止，并需要重新开始。
- 如果该过程失败，需要返回到公司门户应用程序以重试。
- 请确保 Wi-Fi 正常及设备上的 Safari 运行正常。
- 下载并安装 [Intune 公司门户应用](install-and-sign-in-to-the-intune-company-portal-app-ios.md)。


## <a name="using-the-company-portal-app-to-set-up-access-to-company-resources"></a>使用公司门户应用程序设置对公司资源的访问

|您看到的内容|说明|
|---|---|
|![公司门户登录屏幕，底部有“登录”按钮。](./media/ios-01-cp-enroll-1802.png)|打开公司门户应用程序并点击“登录”。|
|![Azure AD 登录提示符。](./media/ios-02-cp-enroll-1802.png)|输入公司电子邮件地址，然后点击“下一步”。|
|![Azure AD 密码提示符。](./media/ios-03-cp-enroll-1802.png)|输入你的密码，然后点击“登录”。|
|![正在加载公司资源初始屏幕。](./media/ios-04-cp-enroll-1802.png)|等待加载完成。|
|![条款和条件页。](./media/ios-05-cp-enroll-1802.png)|阅读并接受所有条款和条件。|
|![设置公司访问屏幕。 当前，管理和设置都需要解决方案。](./media/ios-06-cp-enroll-1802.png)|点击“开始”以开始执行使你的设备能够访问公司资源的过程。 如果现在无法执行这一过程，可以“推迟”此过程，但这也意味着将无法获取电子邮件、文档等资源。|
|![“我的公司可以看到什么信息”屏幕。](./media/ios-07-cp-enroll-1802.png)|通过点击底部的链接，可以详细了解你的公司可以看到的信息。 否则，点击“继续”。|
|![“下一步是什么”屏幕。](./media/ios-08-cp-enroll-1802.png)|此屏幕介绍安装中的操作。 要完成此过程，将需要用到 Safari、设置应用和公司门户应用。 点击“继续”。|
|![在点击“下一步是什么”上的“下一步”后加载屏幕。](./media/ios-09-cp-enroll-1802.png)|等待加载完成。|
|![切换到 Safari 进行注册。](./media/ios-7-cp-enroll-1711.png)|你将被转到 Safari 以获取设备的管理信息。|
|![系统提示打开设置应用。](./media/ios-8-cp-enroll-1711.png)|点击“允许”打开设置应用，下载配置的配置文件。 安装该文件，让公司管理你设备上的公司信息。|
|![配置文件会在设置中打开。](./media/ios-9-cp-enroll-1711.png)|点击“安装”。|
|![安装屏幕底部的配置文件模式对话框。](./media/ios-10-cp-enroll-1711.png)|点击“安装”。|
|![配置文件正在安装加载屏幕。](./media/ios-11-cp-enroll-1711.png)|等待加载完成。|
|![配置文件管理警告屏幕。](./media/ios-12-cp-enroll-1711.png)|该警告由 Apple 编写，可让你详细了解可以对受管理的设备执行什么类型的操作。 详细了解[你的公司可以看到什么信息](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)。|
|![系统提示询问是否信任远程管理。](./media/ios-13-cp-enroll-1711.png)|点击“信任”允许公司管理你设备上的公司信息和设置。|
|![配置文件完成安装加载屏幕。](./media/ios-14-cp-enroll-1711.png)|等待加载完成。|
|![配置文件已安装屏幕。](./media/ios-15-cp-enroll-1711.png)|配置文件已安装，即将对你设备上的公司信息和设置进行管理。|
|![切换到 Safari 进行注册。](./media/ios-16-cp-enroll-1711.png)|将返回到 Safari 以完成获取你设备上的管理信息的过程。 |
|![系统提示打开公司门户。](./media/ios-17-cp-enroll-1711.png)|点击“打开”。|
|![正在加载公司资源屏幕。](./media/ios-21-cp-enroll-1802.png)|等待加载完成。|
|![选择公司门户应用中的设备类别。](./media/ios-22-cp-enroll-1802.png)|为你的设备选择最适合的类别。 这通常与拥有设备的用户以及该设备大部分时间所在的位置有关。|
|![已选择类别。](./media/ios-23-cp-enroll-1802.png)||
|![设备管理成功，现在需要更新设置。](./media/ios-24-cp-enroll-1802.png)|你已成功管理你的设备。 公司可能还需要你更新一些其他设置，例如，密码长度。 点击“继续”以继续。|
|![确认设备设置。](./media/ios-25-cp-enroll-1802.png)|公司门户将检查是否需要更新任何设置。|
|![设置检查已完成，具有错误的 OS 版本](./media/ios-26-cp-enroll-1802.png)|公司门户将提供如何能够修复设置中存在的任何问题的说明。 修复完成后，点击“检查设置”。|
|![确认设备设置加载屏幕](./media/ios-27-cp-enroll-1802.png)|你的设备将检查你的设置是否能够足够安全地访问公司资源。|
|![已成功注册和更新设置](./media/ios-28-cp-enroll-1802.png)|祝贺你！ 你的设备现已在 Intune 中注册。|

> [!Note]
> 在完全实现设备管理前，还需完成几个步骤。 了解关于[使用电信费用管理注册设备](enroll-your-device-with-telecom-expense-management-ios.md)的详细信息。 如果组织正在使用 Apple 的设备注册计划，请在[此处](enroll-your-device-dep-ios.md)了解详细信息。

仍需帮助？ 请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://portal.manage.microsoft.com#HelpDeskDialog)。
