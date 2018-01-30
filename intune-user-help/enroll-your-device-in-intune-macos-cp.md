---
title: "通过公司门户在 Intune 中注册 macOS 设备 | Microsoft Docs"
description: "介绍如何通过公司门户应用在 Intune 中注册 macOS 设备"
keywords: "Mac OS X、macOS、OS X"
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 11/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: 
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 0da2ba5d842a004f167a4bbeca62d4b00f756612
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="enroll-your-macos-device-in-intune-with-the-company-portal-app"></a>通过公司门户应用在 Intune 中注册 macOS 设备

获取对组织的应用、数据和资源的访问权限可使工作更加轻松。 你的组织使用 Intune [管理对这些资源的访问权限](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md)，你需要下载适用于 macOS 的公司门户应用。 这些说明适用于使用 OS X El Capitan 10.11+ 的 macOS 设备。

> [!NOTE]
> 可在[此处](enroll-your-device-in-intune-macos-legacy.md)查找有关在 macOS 早期版本上注册 macOS 设备的说明。

1. 在你的“Dock”上找到“Safari”并打开一个新窗口，然后打开[公司门户网站](https://portal.manage.microsoft.com#HelpDeskDialog)。

2. 使用工作或学校帐户登录到公司门户网站。

[!INCLUDE[wit_nextref](includes/end-user-password-guidance.md)]

3. 登录后，单击页面左上角的“菜单”，选择“我的设备”。

   ![Web 门户登录页面的屏幕截图，Web 门户显示没有可安装的应用，下方有“我的设备”按钮。](./media/macOS_enroll_001_landing_page.png)

4. 在“我的设备”页上，显示已注册的设备列表或仅显示横幅。 这取决于是否已注册设备（macOS 或其他设备）。 若要注册未列出的设备，请选择显示“如果设备已列出，请点击此处进行识别。如果设备未列出，请点击此处注册设备”的横幅。 如果没有任何已注册设备，横幅上将显示“未注册任何设备。请点击此处注册此设备。”

    ![“我的设备”页的屏幕截图，横幅上方显示一些未识别的设备，提示注册未列出的设备或识别未识别的设备。](./media/macOS_enroll_002_tap_here_banner.png)

5. 将公司门户应用下载到 macOS 设备以继续注册。

    ![提示用户下载 macOS 公司门户应用的通知。 此通知包含上述步骤中所列的文本，并在右下角显示“下载”按钮。](./media/macOS_enroll_IWP_CP_app_notice.png)

6. Mac 将进行检查，确认下载的 CompanyPortal.pkg 可以安全打开。 打开安装程序并完成安装过程。

7. 完成安装后，打开“应用程序”文件夹或“Launchpad”，然后打开“公司门户”。

8. Mac 会显示一条消息：“CompanyPortal”是从 Internet 下载的应用程序。是否确认要打开? 单击“打开” 。

  > [!NOTE]
  > Intune 需要访问你的计算机，以确保设备足够安全以访问你组织的资源。 如果计算机拒绝打开“公司门户”应用，请尝试[关闭 Gatekeeper](https://support.apple.com/HT202491)，然后打开该应用。

9. “公司门户”应用中的第一个屏幕会提示你使用登录公司门户网站时所用的相同工作帐户或学校帐户登录。

10. 公司门户确认帐户信息后会显示“设备注册”和“设备符合性”状态。 黄色三角形可让你知道，需要执行一些操作，确保可在工作时安全使用 Mac。 单击“开始”，开始[向管理系统注册设备](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)。

11. Mac 随即开始注册到管理系统。 在此期间，系统可能会提示提供计算机的登录信息。 注册需要几分钟时间。 在此期间，可在计算机上执行其他操作。 完成公司访问设置后，会显示一条消息，通知操作已完成。

仍需帮助？ 请与公司支持人员联系。 可以在[公司门户网站](https://portal.manage.microsoft.com#HelpDeskDialog)中查找他们的联系信息。
