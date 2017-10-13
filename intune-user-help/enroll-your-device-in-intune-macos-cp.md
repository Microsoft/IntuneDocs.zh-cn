---
title: "通过公司门户在 Intune 中注册 macOS 设备 | Microsoft Docs"
description: "介绍如何通过公司门户应用在 Intune 中注册 macOS 设备"
keywords: "Mac OS X、macOS、OS X"
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 09/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope: User help
ROBOTS: 
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: b40801633a130ac79b0ae5b4e1669320c70909e2
ms.sourcegitcommit: db7a7bbead3a3fa78c4d643607f709a2909eb608
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/28/2017
---
# <a name="enroll-your-macos-device-in-intune-with-the-company-portal-app"></a>通过公司门户应用在 Intune 中注册 macOS 设备

[!INCLUDE[macos-preview-1708](./includes/macos-preview-1708.md)]

获取对组织的应用、数据和资源的访问权限可使工作更加轻松。 你的组织使用 Intune [管理对这些资源的访问权限](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-ios.md)，你需要下载适用于 macOS 的公司门户应用。 这些说明适用于使用 OS X El Capitan 10.11+ 的 macOS 设备。

  > [!NOTE]
  > 如果要注册 iPhone 或 iPad 等 iOS 设备，请[改为尝试以下说明](enroll-your-device-in-intune-ios.md)。

1.  在 Dock 上，查找 Safari，并转到 [aka.ms/macoscompanyportal](https://aka.ms/macoscompanyportal)。 

2. 下载应用。 Mac 将进行检查，确认下载的 CompanyPortal.dmg 可以安全打开。 从“下载”文件夹将其打开后，将“CompanyPortal”应用拖动到“应用程序”文件夹。

3. 打开“应用程序”文件夹或“Launchpad”，然后打开“公司门户”。

4. Mac 会显示一条消息：“CompanyPortal”是从 Internet 下载的应用程序。是否确认要打开? 单击“打开”。

  > [!NOTE]
  > Intune 需要访问你的计算机，以确保设备足够安全以访问你组织的资源。 如果计算机拒绝打开“公司门户”应用，请尝试[关闭 Gatekeeper](https://support.apple.com/HT202491)，然后打开该应用。

6. “公司门户”应用中的第一个屏幕会提示你使用登录公司门户网站时所用的相同工作帐户或学校帐户登录。

7. 公司门户确认帐户信息后会显示“设备注册”和“设备符合性”状态。 黄色三角形可让你知道，需要执行一些操作，确保可在工作时安全使用 Mac。 单击“开始”，开始[向管理系统注册设备](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)。

8. Mac 随即开始注册到管理系统。 在此期间，系统可能会提示提供计算机的登录信息。 注册需要几分钟时间。 在此期间，可在计算机上执行其他操作。 完成公司访问设置后，会显示一条消息，通知操作已完成。

仍需要帮助？ 请与公司支持人员联系。 可以在[公司门户网站](https://portal.manage.microsoft.com)中查找他们的联系信息。
