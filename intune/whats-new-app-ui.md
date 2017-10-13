---
title: "Intune 最终用户应用的 UI 更新"
description: "了解 Intune 中针对最终用户设备上可用的应用所做的 UI 更改。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b782e382-8deb-48a7-a437-d7c5a17163f1
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 11a3c96046a194e10d952508669b7e8fac0d1ee8
ms.sourcegitcommit: 53a1f5226d1e1172f013a1b192321dde610b2d6c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/06/2017
---
# <a name="ui-updates-for-intune-end-user-apps"></a>Intune 最终用户应用的 UI 更新
了解此版本的 Microsoft Intune 中，针对最终用户会看到的应用所做的 UI 更新。 这有助于与用户之间的通信以及用于支持部署的已创建的任何更新自定义文档。 还有助于了解如何在用户使用公司门户寻求支持人员的帮助和支持时更好地解决用户面临的任何问题。

## <a name="week-of-october-2-2017"></a>2017 年 10 月 2 日那周

#### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>对公司门户中的设备设置工作流的改进<!--1490692-->
我们改进了适用于 Android 的公司门户应用中的设备设置工作流。 语言更贴近你公司的用语习惯，在可能的情况下我们还对屏幕进行了合并。 

|以前|完成|
|---|---|
|![01](./media/android_cp_enroll_01_post_1709.png)|![01](./media/android_cp_enroll_01_1709_new.png)|
|![01a](./media/android_cp_enroll_01_before_1710.png)| *与上一步结合使用* |
|![02](./media/android_cp_enroll_02_before_1710.png)|![02](./media/android_cp_enroll_02_after_1710.png)|
|![03](./media/android_cp_enroll_03_before_1710.png)|![03](./media/android_cp_enroll_03_after_1710.png)|

其他步骤已在 Android for Work 设备上进行了改进。

|以前|完成|
|---|---|
|![04](./media/android_work_cp_enroll_01_before_1710.png)|![04](./media/android_work_cp_enroll_01_after_1710.png)|
|![05](./media/android_work_cp_enroll_02_before_1710.png)| *与上一步结合使用* |
|![06](./media/android_work_cp_enroll_03_before_1710.png)|![06](./media/android_work_cp_enroll_03_after_1710.png)|
|![07](./media/android_work_cp_enroll_04_before_1710.png)|![07](./media/android_work_cp_enroll_04_after_1710.png)|
|![08](./media/android_work_cp_enroll_05_before_1710.png)| *与上一步结合使用* |


我们已更新条件访问电子邮件激活屏幕。

|以前|完成|
|---|---|
|![06](./media/android_conditional_access_email_before_1710.png)|![06](./media/android_conditional_access_email_after_1710.png)

## <a name="week-of-september-11-2017"></a>含 2017 年 9 月 11 日的那周

### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Android 公司门户应用的表述更容易理解 <!---1396349--->  

为了让最终用户能够更轻松地注册，Android 公司门户应用的注册流程已使用新文本进行了简化。 如果有自定义注册文档，则需要更新该文档，反映新的屏幕。 可找到如下所示示例图片：

|以前|完成|
|---|---|
|![01](./media/android_cp_enroll_01_before_1709.png)|![01](./media/android_cp_enroll_01_post_1709.png)|
|![02](./media/android_cp_enroll_02_before_1709.png)|![02](./media/android_cp_enroll_02_post_1709.png)|
|![03](./media/android_cp_enroll_03_before_1709.png)|![03](./media/android_cp_enroll_03_post_1709.png)|
|![04](./media/android_cp_enroll_04_before_1709.png)|![04](./media/android_cp_enroll_04_post_1709.png)|
|![05](./media/android_cp_enroll_05_before_1709.png)|![05](./media/android_cp_enroll_05_post_1709.png)|


## <a name="week-of-august-28-2017"></a>含 2017 年 8 月 28 日的那周

### <a name="ios-11-mail-app-will-support-oauth----1196951---"></a>iOS 11 邮件应用将支持 OAuth<!---1196951--->

在使用 OAuth 的 iOS 设备上，使用 Intune 的条件访问支持更安全的身份验证。 为支持此功能，适用于 iOS 的公司门户应用上现在有一个不同的流，允许更安全的身份验证。 如果最终用户在邮件应用中尝试登录新的 Exchange 帐户，将会看到一个 Web 视图提示。 在 Intune 中注册后，用户会看到提示，要求允许本机邮件应用访问证书。 大多数最终用户不会再看到隔离电子邮件。 现有邮件帐户会继续使用基本身份验证协议，因此仍会收到隔离电子邮件。 最终用户的这种登录体验与 Office 移动应用的登录体验类似。

![选择本机邮件应用中的帐户类型。](./media/ios-11-ca-email-after-1708-01.png)

![选择 Exchange 后，iOS 设备提示输入电子邮件地址和帐户名。](./media/ios-11-ca-email-after-1708-02.png)

![提供电子邮件地址和帐户名。](./media/ios-11-ca-email-after-1708-03.png)

![已发送到外部 Microsoft 登录页。](./media/ios-11-ca-email-after-1708-04.png)

![在 Microsoft 页提供密码。](./media/ios-11-ca-email-after-1708-05.png)

![Microsoft 提示用户向管理系统注册设备。](./media/ios-11-ca-email-after-1708-06.png)

![系统会提示用户从公司门户网站进行注册。](./media/ios-11-ca-email-after-1708-07.png)

## <a name="week-of-august-21-2017"></a>含 2017 年 8 月 21 日的那周

### <a name="intune-mobile-application-management-mam-dialog-boxes-will-have-a-modern-interface----1199015---"></a>“Intune 移动应用管理”(MAM) 对话框将具有新式界面<!-- 1199015 -->

更新后，“Intune 移动应用管理”(MAM) 对话框将具有新式外观和体验。 对话框功能与以前相同。

之前的体验

![旧界面](./media/NewUI_Old_AttachFileHandler.jpg)

新式体验

![新式界面](./media/NewUI_Modern_AttachFileHandler.jpg)


## <a name="week-of-august-14-2017"></a>含 2017 年 8 月 14 日的那周

### <a name="updates-to-the-device-details-page-on-the-company-portal-app-for-windows-10----1287448---"></a>适用于 Windows 10 的公司门户应用上“设备详细信息”页的更新<!---1287448--->

适用于 Windows 10 的公司门户应用将标题下的“类别”标签移动至“设备详细信息”页上的一个属性。

![适用于 Windows 的公司门户应用的“设备详细信息”屏幕，现在“类别”字段显示为一个属性，而不是直接显示在屏幕标题的下方。](./media/cp_win10_category_tag_move_after_1708.png)

## <a name="week-of-july-31-2017"></a>2017 年 7 月 31 日的这一周

### <a name="apps-details-pages-will-display-new-information-for-android-devices---1287476--"></a>应用详细信息页显示 Android 设备的新信息<!--1287476-->

Android 版“公司门户”应用的应用详细信息页现在会显示 IT 管理员为该应用定义的应用类别。

![新的应用详细信息页](./media/cp_android_appdetails_after_1708.png)

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>改进了所有平台上跨公司门户应用的登录体验<!--User Story 1132123-->

我们宣布将在接下来的几个月内推出一项更新，该更新将提升适用于 Android、iOS 和 Windows 的 Intune 公司门户应用的登录体验。 当 Azure AD 进行此更改时，新的用户体验将自动在公司门户应用的所有平台上显现。 此外，用户可以使用生成的一次性验证码从其他设备立即登录到公司门户。 当用户需要在没有凭据的情况下登录时，这尤为有用。  

下面，将向你介绍使用凭据进行登录的以前的登录体验和新登录体验，以及从其他设备进行登录的新登录体验。

__以前的登录体验__

![公司门户登录页，网站的图形表示形式前面显示一个人形图标。 下面是“登录”按钮。 底部的链接指向 Microsoft 隐私和 Cookie 信息。](./media/cp_ios_aad_signin_before_1704_001.png)

![点击“登录”后，用户在此页上输入其凭据，系统要求输入用户的电子邮件和密码，还提供其他方法以解决密码出错的情况。](./media/cp_ios_aad_signin_before_1704_002.png)

![提供密码后，公司门户应用登录，并通过加载栏进行提示。](./media/cp_ios_aad_signin_before_1704_003.png)

__新的登录体验__

![公司门户登录页，网站的图形表示形式前面显示一个人形图标。 下面是“登录”按钮。 底部的链接指向 Microsoft 隐私和 Cookie 信息。](./media/cp_ios_aad_signin_after_1704_001.png)

![提示用户只提供电子邮件地址，而不是在同一屏幕上同时提供电子邮件和密码。](./media/cp_ios_aad_signin_after_1704_002.png)

![在接受其电子邮件地址之后，提示用户输入密码。](./media/cp_ios_aad_signin_after_1704_003.png)

![在经过身份验证过程后，公司门户应用进行登录，并通过加载栏进行提示。](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

__从其他设备登录时的新登录体验__

![公司门户登录页，网站的图形表示形式前面显示一个人形图标。 下面是“登录”按钮。 底部的链接指向 Microsoft 隐私和 Cookie 信息。](./media/cp_ios_aad_signin_from_another_device_after_1704_001.png)

点击“从其他设备登录”链接。

![通过使用工作计算机的唯一密码访问 aka.ms/devicelogin 页面，然后使用验证码进行登录可获得说明。](./media/cp_ios_aad_signin_from_another_device_after_1704_003.png)

启动浏览器，然后转到 [https://aka.ms/devicelogin](https://aka.ms/devicelogin)。

![用户工作计算机上用户浏览器的图像，而不是公司门户应用的图像。 显示的“设备登录”页将提示用户输入他们在公司门户应用中收到的验证码。](./media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

输入在公司门户应用中看到的验证码。 选择“继续”，你将能够使用受贵公司支持的任意方法进行身份验证，如智能卡。

![用户已将唯一代码输入到字段中，“设备登录”站点要求确认 Intune 公司门户是接收授权以进行登录的正确应用。](./media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

![确认页显示用户现在已登录其设备上的公司门户应用，可以关闭此页。](./media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

公司门户应用将开始进行登录。

![在经过身份验证过程后，公司门户应用进行登录，并通过加载栏进行提示。](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

## <a name="week-of-june-12-2017"></a>2017 年 6 月 12 日的这一周

### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>适用于 Android 的公司门户应用现推出了全新的应用保护政策最终用户体验 <!--1305217-->
根据客户反馈，已修改适用于 Android 的公司门户应用，以便显示“访问公司内容”按钮。 其目的在于，使最终用户在仅需要访问支持应用保护策略（Intune 移动应用程序管理的一项功能）的应用时，无需完成不必要的注册过程。

用户只需点击“访问公司内容”按钮，而不是开始注册设备。

![一个 Android 公司门户应用的图像，图像正中以较大文字显示“访问公司内容”，而不是按照标准情况提供立即注册选项](./media/and_access_company_content_after_1706.png)

然后，用户转到公司门户网站，以获得在其设备上使用应用的权限，此时公司门户网站将验证其凭据。

![一个公司门户网站的图像，其中显示确认登录的画面。](./media/and_iwp_sign_in_auth_page_after_1706.png)

仍可通过点击“操作”菜单，让设备注册为完全管理。

![另一个 Android 公司门户应用的图像，其中显示了屏幕右上角的菜单，含有一个用于继续注册设备的选项。](./media/and_sign_in_menu_after_app_protection_policy_enrolled_after_1706.png)

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>与 Windows 10 创意者更新的应用同步改进 <!--676505-->

面向 Windows 10 的公司门户应用，现在将针对具有 Windows 10 创意者更新（版本 1703）的设备自动启动应用安装请求同步。 这将减少“正在挂起同步”状态下的应用安装停止问题。 此外，用户将可以从该应用内部手动启动同步。

![一个 Windows 10 公司门户应用的图像，其中显示从公司门户应用商店下载 Microsoft Word 时的下载状态为待处理状态。](./media/w10_download_pending_after_1706.png)

![一个 Windows 10 公司门户应用的图像，其中显示新的自动同步状态，同时显示一个状态消息，指示设备正在同步并尝试下载该应用。](./media/w10_download_pending_syncing_after_1706.png)

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Windows 10 公司门户新的引导式体验<!---1058938--->
适用于 Windows 10 的公司门户应用将为尚未被标识或注册的设备提供引导式的 Intune 演练体验。 新体验提供了循序渐进的说明，引导用户完成 AAD 注册（条件性访问功能所需）和 MDM 注册（设备管理功能所需）。 引导式体验可从公司门户主页获取。 如果用户未完成注册和登记，可以继续使用应用，但能够体验的功能将很有限。

此更新仅在运行 Windows 10 周年更新（内部版本 1607）或更高版本的设备上可见。

![一个 Windows 10 公司门户应用“登录”页面的图像，其中在“设备”列表中间显示了一个状态消息，告知用户其所用设备尚未针对公司用途进行设置，应选中该消息以开始设置。](./media/win10_guided_enroll_select_setup_after_1706.png)

![一个 Windows 10 公司门户应用“设置”页面的图像，该页面向用户发出警告，指示其需要向设备添加公司账号，然后才能注册应用管理。](./media/win10_guided_enroll_we_help_setup_after_1706.png)

![Windows 10 公司门户应用“向此设备添加公司帐户”页面的图像，其中指示用户需转至“设置应用”并选择“连接”以完成注册。 执行此操作后，屏幕将指示用户需返回公司门户应用，以完成注册。](./media/win10_guided_enroll_leaving_for_iwp_after_1706.png)

![Windows 10 公司门户应用“注册管理”屏幕的图像，其中显示一条“已完成状态”的消息，提示用户现已完成设备注册，应点击“下一步”按钮以继续操作。](./media/win10_guided_enroll_youre_now_enrolled_after_1706.png)

![一个 Windows 10 公司门户应用“完成”屏幕的图像，其中告知用户已完成所有设置，且已通过正确添加的公司帐户完成了设备注册。](./media/win10_guided_enroll_youre_all_set_after_1706.png)

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>新增可轻松删除公司门户的菜单操作 <!--1164569-->
根据用户反馈，适用于 Android 的公司门户应用新添加了一个菜单操作，可启动对设备中公司门户的删除。 此操作可将设备从 Intune 管理中删除，以便用户删除设备中的应用。

![Android 公司门户应用的图像和操作菜单将在右上角打开。 新的“删除公司门户”选项是第三个选项，位于“我的配置文件“和“设置”的下方，以及“条款和条件”、“帮助和反馈”和“关于”的上方。](./media/android_remove_cp_menu_action_after_1705.png)

![在操作菜单中选择新的“删除公司门户”选项后，将出现一个确认对话图像。 该对话将通知用户“删除公司门户，设备将不再由 IT 管理员管理，并且可能删除对公司数据、公司应用和公司电子邮件的访问权限。” 然后，它会要求用户通过选择“是”确认删除“公司门户”应用。](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="week-of-june-5-2017"></a>2017 年 6 月 5 日的这一周

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios---1230777--"></a>对适用于 iOS 的公司门户应用中应用磁贴的改进<!--1230777-->
我们更新了主页上的应用磁贴设计，以反映你为公司门户设置的品牌颜色。

**之前**

![更新前适用于 iOS 的公司门户应用图像，显示了“所有应用”、“特别推荐的应用”和“类别”的预设填充符图像。](./media/cp_ios_homepage_before_1705.png)

**之后**

![更新后适用于 iOS 的公司门户应用图像，现在反映了选择任意与组织相关的颜色的功能。](./media/cp_ios_homepage_after_1705.png)

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>适用于 iOS 的公司门户应用现在可使用帐户选取器
如果用户使用工作或学校帐户在其 iOS 设备上登录其他 Microsoft 应用，则他们可能会在首次登录公司门户时看到我们的新帐户选取器。

![帐户选取器图像，显示了测试用户“Robin Swanson”在他的两个电子邮件地址之间选择。 两个地址下有一个按钮，让用户可以使用不同帐户登录。](./media/cp_ios_multi-account-selector-after-1705.png)

## <a name="april-2017"></a>2017 年 4 月

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Managed Browser 和公司门户的新图标 <!--918433, 918431-->

托管浏览器正在接收 Android 和 iOS 版本应用的更新图标。 新图标将包含更新的 Intune 徽章，使其与企业移动性 + 安全性 (EM+S) 中的其他应用更加一致。

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_manbro_before_042017.png" alt="The previous version of the Managed Browser app icon." width=200 height=366 align=center>
          </td>
          <td>
             <img src="/intune/media/cp_manbro_after_042017.png" alt="The updated version of the Managed Browser app icon." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

公司门户还接收 Android、iOS 和 Windows 版本应用的更新图标，以提高与 EM + S 中其他应用的一致性。 这些图标将在 4 月至 5 月下旬在所有平台中逐步发布。

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Android 公司门户中的登录进度指示器 <!--953374-->

用户启动或恢复应用时，Android 公司门户应用的更新会显示进度指示器。 允许用户访问应用前，指示器将经历以下新状态：开始是“正在连接...”，然后是“正在登录...”，接下来是“正在查看安全要求...”。

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_android_connecting_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Connecting' underneath it." width=200 height=366 align=center>
          </td>
          <td>
             <img src="/intune/media/cp_android_signing_in_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Signing in' underneath it." width=200 height=366 align=center>
           </td>
           <td>
              <img src="/intune/media/cp_android_checking_security_reqs_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Checking for security requirements' underneath it." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>改进 Windows 10 公司门户应用的应用安装状态 <!--676495-->
现在，Windows 10 公司门户应用在应用详细信息页上提供安装进度栏。 运行 Windows 10 周年更新和更高版本的设备上的现代应用支持此功能。

__之前__![以前版本加载页面的图像，其状态消息仅显示“正在安装”。](./media/cp_win10_install_status_before_1704.png)

__之后__![现已更新版本加载页面的图像，其状态消息会显示安装进度条。](./media/cp_win10_install_status_after_1704.png)

## <a name="february-2017"></a>2017 年 2 月

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622-announced-1702--"></a>Android 适用的公司门户应用的最新用户体验<!--621622, announced 1702-->
从 3 月开始，Android 适用的公司门户应用将按照[材料设计指南](https://material.io/guidelines/material-design/introduction.html)来打造更具现代感的外观。 这将改善以下用户体验：

* __颜色__：可以根据自定义调色板对选项卡标头着色。

![左侧为更新之前的 Android 适用的公司门户应用的图像。 右侧为更新之后的 Android 适用的公司门户应用的图像。 两张图像中都选定了“应用”、“设备”和“联系 IT”三个可用选项卡中的“设备”选项卡。](./media/CP_Android_DevicesTab_BeforeAfter.png)

* __界面__：“应用”选项卡上已更新了“特色应用”和“所有应用”按钮。“搜索”按钮现在是浮动的操作按钮。

![左侧为更新之前的 Android 适用的公司门户应用的图像。 右侧为更新之后的 Android 适用的公司门户应用的图像。 两张图像中都选定了“应用”、“设备”和“联系 IT”三个可用选项卡中的“应用”选项卡。](./media/CP_Android_AppsTab_BeforeAfter.png)

* __导航__：“所有应用”以选项卡形式呈现出“特色”、“所有”和“分类”视图，便于导航。 “联系 IT”已经简化，改善了可读性。

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_android_contactit_after.png" alt="The Company Portal app for Android displaying an updated version of the Contact IT tab. The tab shows available contact information for IT, including phone number, email address, IT website, and IT contact information." width=200 height=366 align=center>
          </td>
      </tr>
   </table>
</body>
</html>

## <a name="january-2017"></a>2017 年 1 月

### <a name="modernizing-the-company-portal-website---753980-announced-1701--"></a>公司门户网站现代化<!--753980, announced 1701-->
从 2 月开始，公司门户网站将支持针对不具有托管设备的用户的应用。 此网站将使用新的撞色配色方案、动态图和“汉堡菜单” ![（汉堡菜单的小图，该图片现已添加到公司门户网站左上角，](./media/CP_hamburger_menu.png) 它包括了支持人员详细联系信息和现有托管设备的信息），这与 Microsoft 其他产品和服务保持一致。 将重新排列登录页，强调可供用户使用的应用，登录页上具有针对特色应用和最近更新应用的传送。

![左侧是当前版本的公司门户网站的图像，其中包含之前版本的应用、“我的设备”以及“特别推荐”视图和“类别”视图。 右侧是更新版本的公司门户网站的图像，其中包含刷新的应用轮播、“最近发布”的应用列表和更新的“类别”视图。](./media/CP_Website_BeforeAfter_Feb2016.png)

## <a name="coming-soon-in-the-ui"></a>即将在 UI 中推出的内容
以下是我们通过更新用户界面提升用户体验的各种方法的计划。

> [!Note]
> 请注意，以下图像可能是预览版，发布的产品可能与当前版本有所不同。

### <a name="ui-updates-to-the-company-portal-website---1313244-part-2--"></a>公司门户网站的用户界面更新 <!--1313244 part 2-->

__对精选应用的更新__ 我们在网站中添加了一个专用页面，用户可在其中浏览精选的应用，还可以对主页的“精选”部分做出一些用户界面调整。

![显示应用的彩色磁贴。 它们是每个应用下方的较大方形，填充颜色取决于应用徽标的主体颜色。 “精选应用”部分在公司门户应用的顶部单独显示。](./media/cp_win10_colorful_tiles_after_1708.png)

### <a name="see-also"></a>另请参阅
* [Microsoft Intune 博客](http://go.microsoft.com/fwlink/?LinkID=273882)
* [云平台路线图](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Intune 中的新增功能](https://docs.microsoft.com/intune/whats-new)
