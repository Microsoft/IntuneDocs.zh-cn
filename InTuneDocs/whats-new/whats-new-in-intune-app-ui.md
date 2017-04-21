---
title: "Intune 最终用户应用的 UI 更新 | Microsoft Docs"
description: "了解 Intune 中针对最终用户设备上可用的应用所做的 UI 更改。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b782e382-8deb-48a7-a437-d7c5a17163f1
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 0a39abc7f19f4c2c8074de66a9cd5df9cef78ed5
ms.openlocfilehash: 81761af5ab5aebe6abb44ff43a7df5a337d38fc7
ms.lasthandoff: 04/13/2017


---
# <a name="ui-updates-for-intune-end-user-apps"></a>Intune 最终用户应用的 UI 更新
了解此版本的 Microsoft Intune 中，针对最终用户会看到的应用所做的 UI 更新。 这有助于与用户之间的通信以及用于支持部署的已创建的任何更新自定义文档。 还有助于了解如何在用户使用公司门户寻求支持人员的帮助和支持时更好地解决用户面临的任何问题。

> [!Note]
> 请注意，以下图像为预览版，发布的产品可能与当前版本有所不同。

## <a name="whats-coming-in-intune-app-ui"></a>Intune 应用 UI 中即将推出的内容

### <a name="april-2017"></a>2017 年 4 月

#### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Managed Browser 和公司门户的新图标 <!--918433, 918431-->

Managed Browser 正在接收 Android 和 iOS 版本应用的更新图标。 新图标将包含更新的 Intune 徽章，使其与企业移动性 + 安全性 (EM+S) 中的其他应用更加一致。

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

公司门户还接收 Android、iOS 和 Windows 版本应用的更新图标，以提高与 EM + S 中其他应用的一致性。 这些图标将在 4 月至 5 月下旬在所有平台中逐步发布。

#### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Android 公司门户中的登录进度指示器 <!--953374-->

用户启动或恢复应用时，Android 公司门户应用的更新会显示进度指示器。 该指示器将依次显示新的状态，从“正在连接...”开始，然后“正在登录...”，最后“正在检查安全性要求...”，完成后即允许用户访问该应用。

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

## <a name="whats-been-announced-for-ui-updates-for-end-user-apps"></a>针对最终用户应用的 UI 更新发布了什么内容

### <a name="february-2017"></a>2017 年 2 月

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622-announced-1702--"></a>Android 适用的公司门户应用的最新用户体验<!--621622, announced 1702-->
从 3 月开始，Android 适用的公司门户应用将按照[材料设计指南](https://material.io/guidelines/material-design/introduction.html)来打造更具现代感的外观。 这将改善以下用户体验：

* __颜色__：可以根据自定义调色板对选项卡标头着色。

![左侧为更新之前的 Android 适用的公司门户应用的图像。 右侧为更新之后的 Android 适用的公司门户应用的图像。 两张图像中都选定了“应用”、“设备”和“联系 IT”三个可用选项卡中的“设备”选项卡。](./media/CP_Android_DevicesTab_BeforeAfter.png)

* __界面__：“应用”选项卡上已更新了“特色应用”和“所有应用”按钮。 “搜索”按钮现在是浮动的操作按钮。

![左侧为更新之前的 Android 适用的公司门户应用的图像。 右侧为更新之后的 Android 适用的公司门户应用的图像。 两张图像中都选定了“应用”、“设备”和“联系 IT”三个可用选项卡中的“应用”选项卡。](./media/CP_Android_AppsTab_BeforeAfter.png)

* __导航__：“所有应用”以选项卡形式呈现出“特色”、“所有”和“分类”视图，便于导航。 “联系 IT”已经简化，改善了可读性。

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

### <a name="modernizing-the-company-portal-website---753980-announced-1701--"></a>公司门户网站现代化<!--753980, announced 1701-->
从 2 月开始，公司门户网站将支持针对不具有托管设备的用户的应用。 此网站将使用新的撞色配色方案、动态图和“汉堡菜单” ![（汉堡菜单的小图，该图片现已添加到公司门户网站左上角，](./media/CP_hamburger_menu.png) 它包括了支持人员详细联系信息和现有托管设备的信息），这与 Microsoft 其他产品和服务保持一致。 将重新排列登录页，强调可供用户使用的应用，登录页上具有针对特色应用和最近更新应用的传送。

![左侧是当前版本的公司门户网站的图像，其中包含之前版本的应用、“我的设备”以及“特别推荐”视图和“类别”视图。 右侧是更新版本的公司门户网站的图像，其中包含刷新的应用轮播、“最近发布”的应用列表和更新的“类别”视图。](./media/CP_Website_BeforeAfter_Feb2016.png)


### <a name="see-also"></a>另请参阅
* [Microsoft Intune 博客](http://go.microsoft.com/fwlink/?LinkID=273882)
* [云平台路线图](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Azure 预览版的新增功能](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [新增功能存档](whats-new-archive.md)

