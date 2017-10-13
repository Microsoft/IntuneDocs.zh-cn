---
title: "在 Intune 中注册 macOS 设备 | Microsoft Docs"
description: "介绍如何在 Intune 中注册 macOS 设备"
keywords: "Mac OS X、macOS、OS X"
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 58eb0e7a-1321-4c66-a281-88fb01e72c1c
searchScope: User help
ROBOTS: 
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 04009fa3fea401e3093a444b0fdbbbe12bd31c84
ms.sourcegitcommit: db7a7bbead3a3fa78c4d643607f709a2909eb608
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/28/2017
---
# <a name="enroll-your-macos-device-in-intune"></a>在 Intune 中注册 macOS 设备

需要获取对你组织的应用、数据和资源的访问权限才能完成工作。 如果在工作中使用的是 macOS 设备，这意味着需要安装“管理配置文件”。 这只是一个由公司支持人员设置的文件，用于将设置和访问信息加载到 Mac 上。 想要了解更多信息？ 了解[安装公司门户应用并在 Intune 中注册设备会发生什么情况](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios.md)

  > [!NOTE]
  > 如果你确实想要注册 iOS 设备（如 iPhone 或 iPad），请[改为尝试使用这些说明](enroll-your-device-in-intune-ios.md)。

1. 在你的“Dock”上找到“Safari”并打开一个新窗口，然后打开[公司门户网站](https://portal.manage.microsoft.com)。
2. 使用工作或学校帐户登录到公司门户网站。

  [!INCLUDE[wit_nextref](includes/end-user-password-guidance.md)]

3. 登录时将看到可用的“主页”、“应用”和“类别”选项卡。 此页将显示可安装的所有应用。 如果尚未注册任何设备，将看到通知“无法显示任何应用”。 可以通过选择“我的设备”继续下一步操作。

 ![Web 门户登录页面的屏幕截图，Web 门户显示没有可安装的应用，下方有“我的设备”按钮。](./media/macOS_enroll_001_landing_page.png)

4. 在“我的设备”页上，显示已注册的设备列表或仅显示横幅。 这取决于是否已注册设备（macOS 或其他设备）。 若要注册未列出的设备，请选择显示“如果设备已列出，请点击此处进行识别。如果设备未列出，请点击此处注册设备”的横幅。

  ![“我的设备”页的屏幕截图，横幅上方显示一些未识别的设备，提示注册未列出的设备或识别未识别的设备。](./media/macOS_enroll_002_tap_here_banner.png)

5. 将显示一个弹出窗口，并简要说明为何需要__标识或注册此设备__。 查看此内容，然后单击“注册”以继续。

 ![标识或注册此设备 macOS](./media/macOS_enroll_003_IDenroll_popup.png)

6. 系统会显示第二个弹出窗口，并简要说明__注册此设备__会发生什么情况。 查看此内容，然后单击“安装”以继续。

 ![注册此设备 macOS](./media/macOS_enroll_004_enroll_popup.png)

  > [!NOTE]
  > Intune 需要访问你的计算机，以确保设备足够安全以访问你组织的资源。 了解[在 Intune 中注册设备会发生什么情况](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-ios.md)。

7. 将打开“系统偏好设置”，并询问是否要__安装“管理配置文件”？__ 单击“安装”以继续，或单击“显示配置文件”获取更多详细信息。

 ![安装管理配置文件](./media/macOS_enroll_005_sysprefs_mgmt_profile.png)

8. 将出现一个 macOS 弹出窗口。 通过提供计算机的“用户名”和“密码”，然后单击“确定”，确认要进行更改。 这会将管理配置文件安装到你的 Mac 上。

 ![macOS 配置文件安装弹出窗口](./media/macOS_enroll_006_sysprefs_admin_login.png)

9. 你可能会在 Mac 中看到有关配置文件详细信息或是否确定要“安装”的额外消息。 单击“继续”和“安装”以继续。 安装完成后，便可以在“设备配置文件”列表中查看新安装的“管理配置文件”。

 ![macOS 配置文件已安装](./media/macOS_enroll_007_sysprefs_installed_profile.png)

仍需要帮助？ 请与公司支持人员联系。 可以在[公司门户网站](https://portal.manage.microsoft.com)中查找他们的联系信息。
