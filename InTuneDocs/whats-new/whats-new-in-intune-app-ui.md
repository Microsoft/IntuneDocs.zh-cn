---
title: "Intune 最终用户应用的 UI 更新 | Microsoft Docs"
description: "了解最终用户设备上运行的 Intune 应用的 UI 变化。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 04/26/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b782e382-8deb-48a7-a437-d7c5a17163f1
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 5f172290d493717308446c4f9e2313a03ba8f3aa
ms.openlocfilehash: 84c6c9ddeeff3570d0b00364063e43105141de0f
ms.contentlocale: zh-cn
ms.lasthandoff: 04/27/2017


---
# <a name="ui-updates-for-intune-end-user-apps"></a>Intune 最终用户应用的 UI 更新
了解最终用户将会在这一版 Microsoft Intune 中看到的应用 UI 更新。 这有助于与用户进行通信，并更新为了支持部署而创建的自定义文档。 此外，还有助于了解如何更好地排除用户遇到的任何问题（如果用户使用公司门户致电支持人员以寻求支持的话）。

> [!Note]
> 请注意，下面展示的是预览版图像，发布的产品可能与展示的版本有所不同。

## <a name="april-2017"></a>2017 年 4 月

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>改进了适用于所有平台的公司门户应用的登录体验 <!--User Story 1132123-->

我们一直在不断改进适用于 Android、iOS 和 Windows 的 Intune 公司门户应用的登录体验。  在 Azure AD 执行此更改后，适用于所有平台的公司门户应用的用户体验都会自动焕然一新。 此外，用户现在还可以使用生成的一次性代码从其他设备登录公司门户。 当用户需要在不使用凭据的情况下登录时，此功能就特别有用。  

下面展示了旧登录体验、使用凭据时的新登录体验以及从其他设备登录时的新登录体验。

__旧登录体验__

![公司门户登录页，在网站图形化表示形式前方显示人员图标。 下方显示“登录”按钮。 底部链接指向 Microsoft 隐私和 Cookie 信息。](./media/cp_ios_aad_signin_before_1704_001.png)

![点击“登录”后，用户需要在此页上输入凭据，系统会要求用户输入电子邮件地址和密码，并且还会提供密码错误解决方案。](./media/cp_ios_aad_signin_before_1704_002.png)

![输入密码后，用户即可登录公司门户应用。请注意，此时页面上会显示加载进度栏。](./media/cp_ios_aad_signin_before_1704_003.png)

__新登录体验__

![公司门户登录页，在网站图形化表示形式前方显示人员图标。 下方显示“登录”按钮。 底部链接指向 Microsoft 隐私和 Cookie 信息。](./media/cp_ios_aad_signin_after_1704_001.png)

![系统会提示用户只输入电子邮件地址，而无需在同一屏幕上同时输入电子邮件地址和密码。](./media/cp_ios_aad_signin_after_1704_002.png)

![接受用户输入的电子邮件地址后，系统会提示用户输入密码。](./media/cp_ios_aad_signin_after_1704_003.png)

__从其他设备登录时的新登录体验__

![公司门户登录页，在网站图形化表示形式前方显示人员图标。 下方显示“登录”按钮。 底部链接指向 Microsoft 隐私和 Cookie 信息。](./media/cp_ios_aad_signin_from_another_device_after_1704_001.png)

点击“从其他设备登录”链接。

![系统会提示用户只输入电子邮件地址，而无需在同一屏幕上同时输入电子邮件地址和密码。 电子邮件地址字段下方的链接为“从其他设备登录”。](./media/cp_ios_aad_signin_from_another_device_after_1704_002.png)

![页面上提供了说明，指示用户在工作计算机上转到 aka.ms/devicelogin 页，然后使用唯一密码进行登录。](./media/cp_ios_aad_signin_from_another_device_after_1704_003.png)

启动浏览器，然后转到 [https://aka.ms/devicelogin](https://aka.ms/devicelogin)。

![用户工作计算机上用户浏览器的图像，而不是公司门户应用的图像。 随即显示的“设备登录”页提示用户输入他们在公司门户应用中看到的代码。](./media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

输入在公司门户应用中看到的代码。 选择“继续”后，将能够使用贵公司支持的任意一种方法（如智能卡）进行身份验证。

![用户已在字段中输入唯一代码，且“设备登录”网站已请求确认 Intune 公司门户是否是接收登录授权的正确应用。](./media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

![声明用户现已在设备上登录公司门户应用的确认页，此页可以关闭。](./media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

此时，将开始登录公司门户应用。

![通过身份验证后，即可登录公司门户应用。请注意，此时页面上会显示加载进度栏。](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Managed Browser 和公司门户的新图标 <!--918433, 918431-->

Managed Browser 将获得该应用的 Android 和 iOS 版的更新图标。 新图标将包含更新的 Intune 徽章，使其与企业移动性 + 安全性 (EM+S) 中的其他应用更为一致。

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_manbro_before_042017.png" alt="The previous version of the Managed Browser app icon." width=200 height=366 align=center>
          </td>
          <td>
             <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_manbro_after_042017.png" alt="The updated version of the Managed Browser app icon." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

公司门户还将获得该应用的 Android、iOS 和 Windows 版的更新图标，以改进与 EM+S 中的其他应用的一致性。 这些图标将于四月至五月底逐步在平台上发布。

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Android 公司门户中的登录进度指示器 <!--953374-->

用户启动或重启应用时，Android 公司门户应用的更新程序将显示登录进度指示器。 允许用户访问应用前，指示器将经历以下新状态：开始是“正在连接...”，然后是“正在登录...”，接下来是“正在查看安全要求...”。

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_signing_in_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Connecting' underneath it." width=200 height=366 align=center>
          </td>
          <td>
             <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_checking_security_reqs_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Signing in' underneath it." width=200 height=366 align=center>
           </td>
           <td>
              <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_connecting_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Checking for security requirements' underneath it." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>改进了 Windows 10 公司门户应用的应用安装状态 <!--676495-->
现在，在 Windows 10 公司门户应用中开始安装所有新式应用时，都可以看到应用安装进度栏。

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_win10_install_status_before_1704.png" alt="An image of the previous version of the loading screen, where the status simply said 'installing.'" width=200 height=366 align=center>
          </td>
          <td>
             <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_win10_install_status_after_1704.png" alt="An image of the updated version of the loading screen, which now shows an install progress bar." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

## <a name="february-2017"></a>2017 年 2 月

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622-announced-1702--"></a>Android 公司门户应用的新用户体验 <!--621622, announced 1702-->
自 3 月起，Android 公司门户应用将根据 [Material Design 指南](https://material.io/guidelines/material-design/introduction.html)打造更加新式的外观。 改进的用户体验包括：

* __颜色__：可以根据自定义调色板对选项卡标题进行着色。

![左侧为更新前的 Android 公司门户应用图像。 右侧为更新后的 Android 公司门户应用图像。 在两张图像中，选定的选项卡都是“应用”、“设备”和“联系 IT 部门”三个选项卡中的“设备”。](./media/CP_Android_DevicesTab_BeforeAfter.png)

* __界面__：更新了“应用”选项卡中的“特别推荐的应用”和“所有应用”按钮。 “搜索”按钮现在是浮动操作按钮。

![左侧为更新前的 Android 公司门户应用图像。 右侧为更新后的 Android 公司门户应用图像。 在两张图像中，选定的选项卡都是“应用”、“设备”和“联系 IT 部门”三个选项卡中的“应用”。](./media/CP_Android_AppsTab_BeforeAfter.png)

* __导航__：“所有应用”中显示“特别推荐”、“所有”和“类别”选项卡式视图，以便用户能够轻松进行导航。 “联系 IT 部门”已经过精简，更加清晰易辨。

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_contactit_after.png" alt="The Company Portal app for Android displaying an updated version of the Contact IT tab. The tab shows available contact information for IT, including phone number, email address, IT website, and IT contact information." width=200 height=366 align=center>
          </td>
      </tr>
   </table>
</body>
</html>

## <a name="january-2017"></a>2017 年 1 月

### <a name="modernizing-the-company-portal-website---753980-announced-1701--"></a>新式公司门户网站 <!--753980, announced 1701-->
自 2 月起，公司门户网站将支持面向不使用受管理设备的用户的应用。 为了与其他 Microsoft 产品和服务保持一致，此网站将采用新的对比色配色方案、动态插图和“汉堡”菜单 ![现已添加到公司门户网站左上角的“汉堡”菜单的小图像](./media/CP_hamburger_menu.png) （其中包含支持人员详细联系信息和现有受管理设备的信息）。 登录页将重新进行排列，以突出显示用户可使用的应用，同时包含特别推荐的应用和最近更新的应用的传送视图。

![左侧是当前版本的公司门户网站的图像，其中包含旧版“应用”、“我的设备”、“特别推荐”和“类别”视图。 右侧是更新版的公司门户网站的图像，其中包含更新后的应用传送视图、“最近发布的应用”列表和“类别”视图。](./media/CP_Website_BeforeAfter_Feb2016.png)


### <a name="see-also"></a>另请参阅
* [Microsoft Intune 博客](http://go.microsoft.com/fwlink/?LinkID=273882)
* [云平台路线图](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Azure 预览版中的新增功能](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [新增功能存档](whats-new-archive.md)

