---
title: "早期发行版本 | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ffbb26f30c7801789a47d57ffed00696f5e6d81a
ms.openlocfilehash: 11e90ce994d17d9dcc62edba775dd0ab8110414e


---

# 早期 Intune 发行版本
## 2016 年 8 月
## 2016 年 8 月
## 应用管理
<!---@Barry, I created the buckets of App management, Device management, etc but am not tied to them. Just wanted to break up and organize the feature list. If you're going to take over the Company Portal section, please talk to Stacie about how she's been organizing it. --->

### iOS 9.3 隐藏和显示的应用
对于运行 iOS 9.3 或更高版本的受监管设备，可将 iOS 常规配置策略中的隐藏和显示的应用列表用于：
- 指定对用户隐藏的应用列表。 用户无法查看，或启动这些应用。
- 指定用户可以查看和启动的应用列表。 无法查看或启动其他应用。

你可以指定的应用包括已部署的应用，以及内置的 iOS 应用，如“信息”和“备忘录”。 有关详细信息，请参阅 [Microsoft Intune 中的 iOS 策略设置]( /intune/deploy-use/ios-policy-settings-in-microsoft-intune)
<!---TFS 1279009 checked--->
### Samsung KNOX 设备允许和阻止的应用策略
你现在可以配置适用于 Samsung KNOX 设备的自定义策略，该策略允许你创建以下项之一：
- 阻止在设备上运行的应用的列表。 即使安装了阻止列表中定义的应用，该应用也不能在设备上激活。
- 允许设备用户从 Google Play 商店中安装的应用的列表。 其他应用不能从应用商店安装。

仅运行 Samsung KNOX 的设备可以使用这些设置。
有关详细信息，请参阅[使用自定义策略允许和阻止适用于 Samsung KNOX 设备的应用](/intune/deploy-use/custom-policy-to-allow-and-block-samsung-knox-apps)。
<!---TFS 1311629 checked --->
### 与移动应用程序管理 (MAM) 兼容的新应用
无论设备是否注册，适用于 [iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) 和 [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) 的 Yammer 应用现在与 [Intune 移动应用程序管理 (MAM) 策略](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)兼容。

有关 MAM 兼容应用的完整列表，请参阅 [Microsoft Intune 应用程序合作伙伴](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners)站点。
<!--- TFS 1252335 & 1252336 checked--->


<!--- I started putting TFS numbers in the What's Coming topic and found it helpful when updating the What's New. Up to you if you want to continue. --->

### Intune 查看器应用
随着新的 RMS 共享应用的发布，我们将从 2016 年 8 月起删除以下 Intune 查看器应用：
- Intune AV 查看器
- Intune PDF 查看器
- Google Play 中适用于 Android 的 Intune 图像查看器

建议使用[适用于 Android 的 Rights Management 应用（RMS 共享）](/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app)而不是使用 Intune 查看器应用，前者只需部署一个应用而不是三个单独的应用便可安全地查看 Android 设备上的公司文件。 如果不再支持 Intune 查看器应用，则将其从 Google 应用商店中删除并且不可供将来使用。

## 设备管理
### Android 7.0 支持
Intune 为移动设备即将推出的 Android 7.0 操作系统提供“day 0”支持。
<!---TFS 1262053--->
### Google 删除了 Android 7.0 设备上的远程密码重置功能
Google 正在删除 Android 7.0 设备的 IT 管理员和最终用户远程重置密码功能。 以前，IT 管理员可以远程重置用户的密码，而且最终用户可以从公司门户网站重置其密码。



## 公司门户更新
### 公司门户网站
- **从公司门户到 Microsoft 的反馈链接** <br/>
公司门户网站使最终用户能够点击位于页面底部的新的“反馈”链接，以便向 Microsoft 发送有关他们对站点的体验的反馈。 收集的匿名信息反馈将帮助 Microsoft 改进用户的公司门户网站体验。
<!--- TFS 1313657 checked--->

### iOS
- **最低 iOS 托管浏览器版本已更新为 8.0**<br/>
已更新用于 iOS 的 Microsoft Intune Managed Browser 应用以支持运行 iOS 8.0 或更高版本的设备。 虽然 iOS 7.1 设备仍可使用现有的 Managed Browser 应用，但最好鼓励你的用户更新为 iOS 8.0 或更高版本，以访问和充分利用新的 Managed Browser 功能。  
<!---TFS 1313253 checked--->

## 即将推出

### iOS 10 支持
Intune 完全支持 iOS 10。 详细信息将紧随 iOS 10 公开发行版。

### Intune 组将于 2016 年 9 月初过渡到 Azure Active Directory 组
Intune 正在创建将 Azure Active Directory (AAD) 安全组用作 Intune 中的用户和设备组的新组管理体验。 **当我们介绍新的基于 Azure 的 Intune 管理门户时**，这些组将用于所有组管理、策略部署和配置文件部署。

此新体验将会使你无需在服务之间重复组，**允许你访问某些新的 Azure Active Directory Premium (AADP) 组功能**，并提供使用 PowerShell 和图表的可扩展性。 这还将跨企业移动性管理统一组管理体验。

若要启用移动到安全组，**当前管理控制台**中的体验将进行一些修改。 **这些更改和 AAD 安全组的使用情况将记录在 Intune 文档中**。

Intune 的新客户将看到**当前租户执行操作之前的一些安全组更改**。

除了组管理中的更改，**还将弃用以下功能**：
- 在创建新组的过程中排除成员或组
- “**未分组的用户**”和“**未分组的设备**”组
- 服务管理员角色中的“**管理组**”
- 对通知规则的基于组的自定义警报
- 利用报表中的组进行透视
<!--- TFS 1295329--->

### 向 Android 公司门户添加“通知”
我们即将于 9 月发布 Android 公司门户的更新，这将在主页上引入一个新的“通知”图标。 点击此图标将访问“**通知**”页，该页将向你的最终用户显示在公司门户应用中需要注意的所有项，例如，设备非合规性、注册更新和注册激活。 如果还使用 iOS 公司门户应用，你将已看到通知体验。 通过引入“**通知**”页，只要设备已经注册，每次启动或恢复 Android 公司门户时，你将不会看到“**公司访问设置**”页。 我们听说你们中的许多人都已创建最终用户指南，而且非常感谢你们在指南/屏幕快照可能需要更新时提前通知我们。 请更新你的文档，以反映体验中即将发生的更改。 在此查找更新的屏幕快照：https://aka.ms/androidcpupdate。  

### iOS 最终用户如何获取应用方面的改进
于九月份在 iOS 的公司门户应用的应用磁贴中进行以下更改，从一个位置（公司门户网站中）即可将用户指向其所有应用的不同视图。 目前，Apple 限制禁止业务线和托管应用商店应用列于公司门户应用中，并要求用户访问不同视图来查找自己所有的应用。

- **公司应用**磁贴目前指向公司门户网站“全部”选项卡中的所有应用的列表，此行为将继续以同种方式运作。 磁贴名称将更改为“**全部应用**”。
- **其他应用**磁贴目前指向公司门户应用内部的一个视图，其中列出了 Apple 允许公司门户应用显示的所有应用。 磁贴名称将更改为“**特别推荐的应用**”，点击该磁贴会将用户转到公司门户网站的“特别推荐”选项卡。
-  **类别**磁贴目前指向公司门户应用内部的一个视图，其中列出了应用类别。 磁贴名称不会更改，但是目前它将指向公司门户网站的“类别”选项卡。 你可以在[此处](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186)查看更新的屏幕截图。
<!---TFS 1317133--->

### 云路线图
通过[云平台路线图](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)实时了解 Intune 即将推出的开发内容。

### 服务弃用
<!---@Barry, we started listing service deprecations earlier this summer. --->
- **iOS 公司门户应用的支持更改**<br/>
在 9 月，要求适用于 iOS 的 Microsoft Intune 公司门户应用的所有用户都使用最新版本。 新用户将只能够下载最新版本，而当前用户必须更新到最新版本。 最新版本需要 iOS 8.0 或更高版本，因此运行较旧的 iOS 版本的设备将无法使用公司门户或者进行注册，直到将其设备更新为 iOS 8.0 或更高版本，并且将公司门户应用更新到最新版本。 运行 iOS 8.0 以下版本的已注册设备将继续受管理，并将列在 Intune 管理员控制台中。  

- **最低 iOS 托管浏览器版本已更新为 8.0**<br/>
Intune 将于 8 月发布适用于 iOS 的更新的 Microsoft Intune 托管浏览器应用，该应用将仅支持运行 iOS 8.0 或更高版本的设备。 iOS 7.1 设备仍将能够使用现有的托管浏览器应用，请鼓励你的用户更新为 iOS 8.0 或更高版本，以访问和充分利用新的托管浏览器功能。  
<!---TFS 1313253--->

- **适用于 Windows 8 和 Windows Phone 8 的公司门户应用将弃用** <br/>
从 2016 年 10 月开始，Microsoft Intune 将终止对 Windows 8 和 Windows Phone 8 公司门户应用的支持。 另外，Microsoft Intune 还将终止对 Windows Phone 8 平台的支持。 因此，你将无法注册或更新任何 Windows Phone 8 设备。 你可以继续管理已注册的 Windows Phone 8 和 Windows 8 设备。 将 Windows Phone 8 和 Windows 8 设备更新到 Windows 8.1 和 Windows Phone 8.1，并使用相应的 Windows 8.1 和 Windows Phone 8.1 公司门户应用在不中断的情况下继续向这些设备分发应用。
<!---TFS 1255391--->

<!--- - **Custom Group Targeting of Notification Rules Removal.**<br/>
Intune notification rules define who an email alert will be sent to from Intune. Currently, you can configure notification rules to send emails to all users of devices in an Intune device group that you created. From around June 1st 2016 moving forward, targeting user-created groups will no longer be supported.

    Today, to target a notification rule to a group you created from the Microsoft Intune administration console, you would take the following steps:

    In the **Admin** workspace, click **Notification Rules** > **Create New Rule**

    In step two of the Create Notification Rule Wizard, select the device groups which the rule will target. This step, “select device groups”, is being removed from the Intune Console.

    The preliminary timeline for this change is as follows:
    - In August, 2016, new tenants will not see step two of the Create Notification Rule Wizard. Exiting tenants are unaffected.
    - Around September, 2016, some existing tenants will not see the “select device groups” in the wizard.
    - Around November, 2016, we expect that all tenants will not see the “select device groups” in the wizard.

--->

## 2016 年 7 月
### 应用管理
#### 改善应用预配配置文件更新体验
Apple iOS 业务线移动应用附带预配配置文件和证书签名的代码。 当应用在 iOS 设备上运行时，iOS 会确认 iOS 应用的完整性，并强制实施由预配配置文件定义的策略。

用于签署应用的企业签名证书通常持续 3 年。 但是，预配配置文件将在 1 年后过期。 利用此更新，Intune 会为你提供一些工具，用于主动地将新预配配置文件策略部署到安装了即将到期的应用而证书仍有效的设备。 有关详细信息，请参阅[使用 iOS 移动预配配置文件策略以保持你的业务线应用最新](/intune/deploy-use/ios-mobile-app-provisioning-profiles)。
<!--- TFS 1280247--->
#### 用于 Intune 应用的 Xamarin SDK 已推出
Intune 应用 SDK Xamarin 组件允许你在使用 Xamarin 生成的移动 iOS 和 Android 应用中启用 Intune 移动应用管理功能。 你可以在 [Xamarin 应用商店](https://components.xamarin.com/view/Microsoft.Intune.MAM)中或在 [Microsoft Intune Github 页面](https://github.com/msintuneappsdk)上找到该组件。
<!--- TFS 1061478 --->

### 设备管理
#### 提高了设备注册限制
Intune 将每个用户的设备的最大可配置设备注册限制从 5 提高到了 15。
<!---TFS 1289896 --->

#### 运行 Intune 客户端软件的 Windows 电脑的 TeamViewer 集成
运行 Intune 客户端的 Windows 电脑的 [TeamViewer](https://www.teamviewer.com) 集成让你可以与 Windows 电脑建立远程协助会话，从而帮助支持最终用户支持部门。 这包括 Windows 7、Windows 8、Windows 8.1 和 Windows 10。 有关详细信息，请参阅[使用 Microsoft Intune 计算机客户端的常见 Windows 电脑管理任务](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client)。
<!---TFS 1284856--->

### 公司门户更新
#### 公司门户网站
- **改善了注册 Windows 设备时的最终用户体验**<br/>
使用条件访问时，Windows 8.1、Windows 10 桌面版和 Windows 10 移动版的注册步骤已在公司门户网站中阐明。 用户现在将看到单独的“设备注册”和“工作区加入”步骤，从而在他们遇到工作区加入 (WPJ) 失败时更易于看到设备的状态以及完成此过程。 执行单独的步骤还可以简化 IT 管理员排除故障的过程。 以前，当最终用户尝试注册并且 WPJ 除外的所有注册步骤都成功时，已注册的设备将不出现在用户要标识的设备列表中，因而使用户感到困惑。

#### Android
- **Android 公司门户应用**<br/>
如果 Android 最终用户看到一条错误消息，指出其设备缺少所需的证书，用户可以点击“如何解决此问题”按钮以获取安装缺少的证书的[步骤](/intune/enduser/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator)。 如果用户完成这些步骤，但看到另一条“缺少证书”的错误消息，系统会要求用户联系其 IT 管理员，并提供此[链接](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues)，其中包含 IT 管理员可以用于解决证书问题的步骤。

- **限制旁加载的应用安装到注册的设备**<br/>
Android 设备不能再通过公司门户网站安装应用程序，除非使用适用于 Android 的 Intune 公司门户应用已在 Intune 中注册设备。
<!---TFS 1299082--->

#### iOS
- **对 iOS 公司门户应用中设备注册管理器帐户的更改**<br/>
若要提高性能和可扩展性，Intune 不再在 iOS 公司门户应用的“**我的设备**”窗格中显示所有设备注册管理器 (DEM) 设备。 仅显示运行该应用的本地设备，且仅限该设备通过公司门户应用注册的情况下。

DEM 用户可能会在本地设备上执行操作，但只能从 Intune 管理员控制台远程管理其他已注册设备。 此外，Intune 将不支持通过 Apple 设备注册计划或 Apple 配置器工具使用 DEM 帐户。 这两种注册方法已支持共享的 iOS 设备的无用户注册。

当共享设备的无用户注册不可用时，仅使用 DEM 帐户。 有关详细信息，请参阅[使用 Microsoft Intune 中的“设备注册管理器”注册企业自有设备](https://docs.microsoft.com/en-us/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)。
<!---TFS 1233681--->

### 对 Windows 功能名称的更改
- [Microsoft Passport for Windows](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune) 现在称为 **Windows Hello 企业版**。
- [企业数据保护](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune)现在称为 **Windows 信息保护**。

## 2016 年 6 月
### Intune 服务运行状况
Intune 服务运行状态信息已随同其他 Microsoft 服务一起移到一个中心位置。 现在，你可在服务运行状态下的 Office 365 管理门户中找到此信息。 有关详细信息，请参阅[此博客文章](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/)。

### 应用管理
- **增强的 Windows 10 企业数据策略配置体验。** 我们围绕创建应用规则、指定网络边界定义和其他企业数据保护设置增强了 Windows 10 企业数据保护策略配置体验。 若要了解详细信息，请参阅 [Create an enterprise data protection (EDP) policy using Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune)（使用 Microsoft Intune 创建企业数据保护 (EDP) 策略）。


### 设备管理
- **Windows Defender 策略设置，可以避免可能不需要的应用。** 名为“**可能不需要的应用程序检测**”的新 Windows Defender 设置已被添加到 Windows 10 桌面版和移动版的常规配置。 你可以使用此设置以防止已注册的 Windows 台式计算机运行被 Windows Defender 分类为可能不需要的软件。 你可以防止这些应用程序运行，或使用审核模式在安装了不需要的应用程序时进行报告。 有关详细信息，请参阅 [Microsoft Intune 中的 Windows 10 策略设置](https://docs.microsoft.com/en-us/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune)。
<!---TFS 1244478--->

### 条件性访问
- **Intune 的 Cisco ISE 网络访问控制策略。**  使用 Cisco 标识服务引擎 (ISE) 2.1 并使用 Microsoft Intune 的客户可以在 ISE 中设置网络访问控制策略。

    此策略下，需要使用 WiFi 或 VPN 连接到网络的设备必须在符合以下条件后才被允许访问：

    * 必须由 Intune 进行管理
    * 必须符合任何已部署的 Intune 合规性策略

 非合规设备的最终用户将被提示注册和修正任何合规性问题以获取访问权限。
- **浏览器的条件性访问。** 可以为 [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) 和 [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune) 设置条件访问策略，以便仅允许通过托管且合规的 iOS 和 Android 设备上受支持的 Web 浏览器对其进行访问。 尝试通过 iOS 和 Android 设备登录到 Outlook Web Access (OWA) 和 SharePoint 站点的最终用户，系统将提示通过 Intune 注册其设备以及在完成登录前解决任何非合规性问题。
<!---TFS 1175844--->

- **Dynamics CRM Online 支持条件性访问。** 可以为 [Dynamics CRM Online](/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune) 设置条件访问策略，以便仅允许托管且合规的 iOS 和 Android 设备对其进行访问。 系统将提示尝试登录到 iOS 和 Android 设备上的 Dynamics CRM 移动应用的最终用户注册 Intune 并在登录完成前修正任何非合规性问题。
<!---TFS1295358--->

##E 公司门户更新

#### Android 公司门户应用

- 当 IT 管理员应用了新的“要求设备不允许安装来自未知源的应用 (Android 4.0 +)”策略时，Android 4.0 或更高版本设备的最终用户将看到消息“必须禁用来自未知来源的安装”。 用户将需要转到“设置” > “安全”，然后关闭“未知源”。 通过合规性消息中的链接，用户可获取有关该消息和为什么需要禁用该设置的详细[信息](/Intune/EndUser/you-are-asked-to-turn-off-unknown-sources-android)。

- 当 IT 管理员应用了新的“要求设备已启用扫描应用的安全威胁 (Android 4.0 +)”策略时，Android 4.0 或更高版本设备的最终用户将看到消息“扫描设备的安全威胁”。 用户将需要转到“设置” > “Google” > “安全”，然后打开“扫描设备的安全威胁”。 通过合规性消息中的链接，用户可获取有关该消息和为什么需要启用该设置的详细[信息](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android)。

- 当 IT 管理员应用了新的“要求禁用 USB 调试 (Android 4.2 +)”策略时，Android 4.2 或更高版本设备的最终用户将看到消息“必须禁用 USB 调试”。 用户将需要转到“设置” > “开发人员”选项，然后关闭“USB 调试”。 通过合规性消息中的链接，用户可获取有关该消息和为什么需要禁用该设置的详细[信息](/Intune/EndUser/you-are-asked-to-turn-off-usb-debugging-android)。

- 当 IT 管理员应用新的“最低 Android 安全修补程序级别 (Android 6.0+)”策略时，Android 6.0 或更高版本设备用户会看到消息“此设备不符合最低 Android 安全修补程序级别”。 用户将需要安装所需的安全修补程序。 通过合规性消息中的链接，用户可获取有关如何安装所需安全修补程序并查看当前已安装的安全修补程序的[信息](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android)。

#### iOS 公司门户应用

- 当最终用户安装业务线应用时，现在它们将看到改进的应用安装体验。 如果应用安装要花很长时间，用户可以手动同步设备以强制继续同步过程。 若要查看最终用户说明，请参阅[手动同步 iOS 设备](/Intune/EndUser/sync-your-device-manually-ios)。

- 适用于 iOS 的 Microsoft Intune 公司门户应用已更新，可支持 iOS 8.0 和更高版本。 此更新意味着，仅当设备正在运行 iOS 8.0 或更高版本时，最终用户才可在 Intune 中安装公司门户应用并注册新设备。 如果用户已注册运行不受支持的 iOS 版本的设备，则这些用户可以继续使用其设备上的公司门户应用。


## 2016 年 5 月

所有这些功能也受混合部署 (Configuration Manager with Intune) 支持。 有关新的混合功能的详细信息，请查看[混合新增功能](https://technet.microsoft.com/en-us/library/mt718155.aspx)页。

### 文档
欢迎使用 [docs.microsoft.com](https://docs.microsoft.com/en-us/intune) 预览版本！
这是一个全新的新式内容平台，旨在使作为我们客户的你能更容易地理解和使用 Intune。
若要了解所有新增功能，请参阅 [Introducing docs.microsoft.com](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/)（docs.microsoft.com 简介）

### Intune 服务运行状况
Intune 服务运行状态信息已随同其他 Microsoft 服务一起移到一个中心位置。 现在你可在**服务运行状态**下的 [Office 365 管理门户](https://portal.office.com/Admin/Default.aspx)中找到此信息。
有关详细信息，请参阅[此博客文章](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/)。


### 应用管理
- **MAM SDK：支持 PIN 长度配置。** 你将能够指定类似于设备 PIN 的 MAM 应用的 PIN 的长度。 这将要求最终用户符合你设置的新限制。 他们将看到一个稍经修改的 PIN 屏幕来解释较长输入。 有关详细信息，请参阅[适用于 Android 的 MAM 策略设置](/intune/deploy-use/android-mam-policy-settings)和[适用于 iOS 的 MAM 策略设置](/intune/deploy-use/ios-mam-policy-settings)。

- **Skype for Business iOS 版和 Android 版。** 你现在可以通过 [MAM 以 Skype for Business 为目标，而不需要注册策略](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)。 用户登录后，将应用 MAM 策略。

- **可通过 MAM 策略管理的新应用。** 适用于 Android 的 Microsoft Word、Excel 和 PowerPoint 应用现在可与未向 Intune 注册的设备上的 MAM 策略相关联。 有关支持的应用的完整列表，请转到 [Microsoft Intune application partners](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)（Microsoft Intune 应用程序合作伙伴）页上的 Microsoft Intune mobile application gallery（Microsoft Intune 移动应用程序库）。


### 公司门户更新

#### Android 公司门户应用
- **最终用户 toast 通知**：当最终用户从公司门户注册设备或删除设备时，现在他们将会看到来自 Andoid 公司门户应用的 toast 通知。

- **对 Android 公司门户应用中设备注册管理器帐户的更改。** 若要提高性能和可扩展性，Intune 不再在 Android 公司门户应用的“我的设备”窗格中显示所有设备注册管理器 (DEM) 设备。 仅显示运行该应用的本地设备，且仅限该设备通过公司门户应用注册的情况下。 DEM 用户可能会在本地设备上执行操作，但只能从 Intune 管理员控制台远程管理其他已注册设备。

#### 公司门户网站
- **公司门户网站：设备标识横幅将向最终用户提供详细信息。** 最终用户现在能够更轻松地标识他们在使用公司门户网站时所选的设备。 如果选择了错误的设备，他们将能够通过点击主页标题栏中的**点击此处**链接选择正确的设备。

## 即将推出
- **消息中心 UI 载入**。 作为 Intune 迁移到 [Office 365 管理门户](https://portal.office.com/)的一部分，我们将开始利用其消息中心以沟通新功能和其他通知。 另外，通过安装随附的 Office 365 管理员移动应用，可在移动电话上收到通知，并轻松地将任何消息转发到用户或分发别名。
我们将开始通过五月发行版本使用消息中心，以在更新完成时通知你，并且将包括有关新的和改进的 Intune 功能的信息。 现在可以通过登录到 [Office 365 管理门户](https://portal.office.com/)，然后选择左导航窗格中的“消息中心”选项来查看消息中心。

- **对设备注册管理器帐户的更改**。 为了提高性能和可扩展性，Intune 不再在 iOS 公司门户应用的**我的设备**窗格中显示**所有**设备注册管理器 (DEM) 设备。 仅显示运行该应用的本地设备，且仅限该设备通过公司门户应用注册的情况下。 DEM 用户可能会在本地设备上执行操作，但只能从 Intune 管理员控制台远程管理其他已注册设备。 此外，Intune 将不支持通过 Apple 设备注册计划或 Apple 配置器工具使用 DEM 帐户。 这两种注册方法已支持共享的 iOS 设备的无用户注册。 当共享设备的无用户注册不可用时，仅使用 DEM 帐户。

### 云路线图
通过[云平台路线图](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)实时了解 Intune 即将推出的开发内容。

### 服务弃用
- **Intune 查看器应用。** 随着新的 RMS 共享应用的发布，我们将从 2016 年 8 月起删除以下 Intune 查看器应用：
    - Intune AV 查看器
    - Intune PDF 查看器
    - Google Play 中适用于 Android 的 Intune 图像查看器

  建议使用适用于 Android 的 Rights Management 应用（RMS 共享）而不是使用 Intune 查看器应用，前者只需部署一个应用而不是三个单独的应用便可安全地查看 Android 设备上的公司文件。 了解有关 RMS 共享应用（具有指向文档的链接）的详细信息。

- **通知规则删除的自定义组目标。**
Intune 通知规则定义将从 Intune 向其发送电子邮件警报的人员。 当前，你可将通知规则配置为向你创建的 Intune 设备组中的设备所有用户发送电子邮件。 约从 2016 年 6 月 1 日起，已不再支持目标用户创建组。

    当前，若要为从 Microsoft Intune 管理控制台创建的组指定通知规则，应采用以下步骤：

    在**管理员**工作区，单击**通知规则**  >  **创建新规则**

    在创建通知规则向导的步骤二中，选择此规则所针对的设备组。 将从 Intune 控制台中删除“选择设备组”这一步骤。

    此更改的初步时间线如下：
    - 2016 年 6 月，新租户将看不到创建通知规则向导的步骤二。 正在退出的租户不受影响。
    - 2016 年 8 月左右，某些正在退出的租户将看不到向导中的“选择设备组”。
    - 2016 年 10 月左右，我们期望所有租户将不会看到向导中的“选择设备组”。


- **iOS 公司门户应用的支持更改**。 未来数月中，Microsoft Intune 公司门户应用 iOS 版将会更新，更新后仅支持运行 iOS 8.0 或更高版本的设备。 用户将无法注册运行 iOS 8.0 以下版本的新设备。 已注册的运行 iOS 8.0 以下版本的设备将继续受管理，且在有限时间内，能够继续使用公司门户应用。 但是，只有 iOS 8.0 或更高版本的设备才能访问最新版本的公司门户应用。 我们鼓励你通知用户更新到 iOS 8.0 或更高版本以充分利用 Intune 的新功能。  


## 2016 年 4 月
所有这些功能也支持混合客户（与 Intune 集成的 Configuration Manager）。
### 应用管理
- **MAM 用户合规性。**
现在，你可以查看 Azure Active Directory (AAD) 租户中的任何用户的应用程序管理策略的[状态](/intune/deploy-use/monitor-mobile-app-management-policies-with-Microsoft-Intune)。 这包括：
   - 设备
   - 在设备上的应用

   状态值：

   **已签入**：指示该策略已部署到用户，以及应用已用在工作环境中且已成功接收到该策略。

    **未签入**：指示策略已部署到用户，但应用从那时起尚未在工作环境中使用。


- **防止 Outlook 联系人同步的 MAM 控件 (Android)。**
适用于[移动应用程序管理](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)而无需注册设备的新设置。 此设置可以防止应用程序将联系人同步到 Android 设备的本机通讯簿。 启用此设置后，目标应用程序将不能再将联系人保存到本机通讯簿。 禁用此设置后，目标应用程序将能够将联系人保存到本机通讯簿。 [远程擦除设备或应用](/intune/deploy-use/wipe-managed-company-app-data-with-Microsoft-Intune)后，将删除已保存到本机通讯簿的所有联系人。 最初，Android 设备上的 Outlook 应用程序支持此新设置。

### 设备管理
- **公司拥有的设备的电话号码标识。** 例如，当运行移动设备清单报表时，现在使用其完整的电话号码标识归类为“企业”的手机。 BYOD 电话号码将继续使用 **** 屏蔽，仅显示最后 4 位数字。


### 公司门户更新
**Android 公司门户应用**未在 Intune 注册其设备和未安装正确证书的用户将不能登录到 Android 公司门户应用，并且会看到以下消息：“无法登录，因为设备缺少必需的证书”。 该消息包含“如何解决此问题”的链接，用户可以点击以查看关于安装证书的说明。 若要查看最终用户解决此问题的步骤，请参阅[设备缺少必需的证书](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing)。

**iOS 公司门户应用**已添加“下拉刷新”操作支持以刷新主页上的内容，其中包括列出的应用、设备以及 IT 联络信息。 “下列刷新”操作不会检查合规性或策略信息，这可以通过选择当前设备的磁贴，然后点击“同步”按钮来实现。

**Windows 10 移动版和 Windows Phone 8.1 公司门户应用**当最终用户安装业务线应用时，他们现在将了解到改进后的应用安装体验。 如果应用安装要花很长时间，用户可以手动同步设备以强制继续同步过程。 若要查看最终用户说明，请参阅[手动同步设备以加速应用安装](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually)。

**公司门户网站**当 Windows 10 移动版和 Windows Phone 8.1 用户正在安装业务线应用时，现在他们将看到以下新状态，向他们提供有关安装状态的详细信息：

* **等待设备进行同步** – 用户已点击“安装”，并且设备现在尝试与 Intune 基础结构进行同步。 必须先同步，然后才能完成安装。 “正在等待设备进行同步”消息也是一个链接，用户可以点击以查看[说明](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually)，了解如果同步过程需要很长时间或已停止，如何手动将设备与 Intune 同步。
* **正在下载** – 正在处理用户的下载请求，且设备正在下载并安装应用。

添加这些状态之前，如果应用安装需要很长时间，用户将感到困惑，因为他们只能看到“正在安装”状态，而这可能会在屏幕上保持数个小时。 添加新的状态意味着，现在用户可以点击“正在等待设备进行同步”链接，并按照说明进行操作以强制继续同步过程，而不是呼叫支持部门。


## 2016 年 3 月
### 自 2016 年 3 月 29 日起新增的功能
除了更新到 Windows 10 常规配置策略之外，2016 年 3 月 29 日发布的所有功能还支持混合客户（与 Intune 集成的 Configuration Manager）。 即将推出对 Windows 10 常规配置策略更新的混合支持。 请注意，其中某些功能可能需要使用 Configuration Manager 的最新版本。

### 应用管理
- **防止 Outlook 联系人同步的 MAM 控件 (iOS)。** 适用于移动应用程序管理而无需注册设备的新设置。 此设置可以防止应用程序将联系人同步到 iOS 设备的本机通讯簿。 启用此设置后，应用将不再能够将联系人保存到本机通讯簿。 禁用此设置后，应用就可以将联系人保存到本机通讯簿。 选择性擦除设备时，将删除已保存到本机通讯簿的所有联系人。 iOS 设备上的 Outlook 应用程序支持此新设置。 有关此设置和其他设置的详细信息，请参阅[创建和部署 MAM 策略](https://technet.microsoft.com/en-us/library/dn292747.aspx)。

### 访问控制
- **Skype for Business Online 支持条件性访问。** 可以为 Skype for Business Online 设置条件性访问策略，使仅托管且合规的 iOS 和 Android 设备可对其进行访问。 系统将提示尝试登录到 iOS 和 Android 设备上的 Skype for Business 移动应用的最终用户注册 Intune 并在登录完成前修复任何非合规性问题。 有关详细信息，请参阅[管理对 Skype for Business Online 的访问权限](https://technet.microsoft.com/en-us/library/mt695297.aspx)。

### 设备管理
- **适用于 iOS 9.3 的 Intune 支持。** 3 月 21 日星期一，Apple 宣布推出 iOS 9.3。 我们致力于确保 Microsoft Intune 与 Apple 最新版本的移动操作系统兼容，并且[我们很高兴地宣布 Intune 支持管理 iOS 9.3 设备](https://blogs.technet.microsoft.com/microsoftintune/2016/03/23/microsoft-intune-provides-support-for-ios-9-3/)。

  在用户将设备升级到 iOS 9.3 时，当前可用于管理 iOS 设备的所有现有 Intune 功能都将继续无缝工作。 此外，iOS 9.3 现在也支持混合客户（与 Intune 集成的 Configuration Manager）。

- **Windows 10 常规配置策略现包含用于管理已注册 Windows 10 电脑上的 Windows Defender 的设置。** 有关详细信息，请参阅 [Microsoft Intune 中的 Windows 10 配置策略设置](https://technet.microsoft.com/en-us/library/mt404697.aspx)。


### 公司门户

- **Windows 应用包可以直接从公司门户网站安装。** 使用 Windows 8、Windows 8.1 和 Windows RT 电脑的用户现可直接从公司门户网站安装 Windows 应用包（扩展名为.appx）。 以前，用户必须在设备上部署或安装公司门户应用才能安装应用。

- **用户可以从公司门户网站远程锁定其设备。** 公司门户网站新增了远程锁定选项，让用户在设备丢失或被盗时可以从门户网站远程锁定其设备。 请参阅[最终用户说明](https://technet.microsoft.com/library/mt590895.aspx/?wt.mc_id=ui#BKMK_iwp_remote_lock)。 下表列出了适用于独立 Intune 和带 Configuration Manager 的 Intune 的远程锁定平台支持。

|平台 | 支持详细信息|
|---------|----------------|
|Android |支持|
|iOS |支持|
|Windows 10 移动版 |仅在手机设置了密码时支持|
|Windows 10 桌面版 |不支持|
|Windows Phone 8.1 |仅在手机设置了密码时支持|
|Windows Phone 8。0 |不支持|
|电脑（Windows 8.0 及更早版本） |不支持|
|电脑 (Windows 8.1) |不支持|

### 自 2016 年 3 月 10 日起新增的功能

### 应用管理

- **利用在第三方 MDM 解决方案中注册的设备的 iOS“Open in”管理**可通过第三方移动设备管理 (MDM) 供应商利用 iOS“Open-In”管理功能。 可以在配置文件设置中设置限制，并使用[管理 iOS 应用之间的数据传输](/intune/deploy-use/manage-data-transfer-between-ios-apps-with-microsoft-intune)部署应用。

     此方法有两个主要优点：

     1. 用户必须先使用工作帐户登录才能从云服务或其他应用中访问任何公司数据。 这可确保访问数据时移动应用管理 (MAM) 策略已到位。

     2. 通过第三方 MDM 解决方案部署的托管电子邮件配置文件和其他托管应用可以与具有 Intune MAM 策略的应用共享文件和数据。

- **使用未在 Intune 中注册的设备的 MAM 策略管理 Microsoft Outlook 应用**现在你可以使用 Intune 移动应用程序管理策略管理未在 Intune 中注册的设备上的 Microsoft Outlook 应用。 具有 MAM 功能的已更新 Microsoft Outlook 应用适用于 [iOS](https://itunes.apple.com/us/app/microsoft-outlook-email-calendar/id951937596?mt=8) 和 [Android](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook) 设备。 使用[创建和部署移动应用管理策略](https://technet.microsoft.com/library/mt627829.aspx)主题中的说明来创建 MAM 策略。  


- **移动应用配置策略使你能更灵活地为 iOS 应用指定用户详细信息**你可以提供打开 iOS 应用时可能需要的用户设置。 例如，你可以提供网络端口或用户名。 有关详细信息，请参阅[使用 Microsoft Intune 中的移动应用配置策略配置 iOS 应用](/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)。


- **将适用于 Microsoft Intune 的 Adobe Reader 部署到企业中 Intune 托管的 iOS 设备**现在可以使用 Intune 移动应用程序管理策略在已注册的设备上对适用于 iOS 的 Adobe Reader 应用进行管理。

- **确保部署的 Web 剪辑在托管浏览器中打开**可以部署仅可在 iOS 和 Android 设备上使用托管浏览器打开的目标 Web 剪辑。 例如，你通过公司门户将链接部署到企业资源，当用户导航到该链接时，他们便可直接打开到在其中能受到 MAM 策略保护的托管浏览器中。 有关详细信息，请参阅[部署应用](/intune/deploy-use/deploy-apps)。


- **从 Intune 管理员控制台为 Windows 10 设备查找、管理和分配适用于企业的 Windows 应用商店应用**Intune 支持适用于企业的 Windows 应用商店，可帮助查找、管理和分配应用到你正在管理的 Windows 10 设备。 适用于企业的 Windows 应用商店可用于管理从 Intune 管理员控制台（管理其他应用时所用的同一控制台）部署和监视这些应用的进程。 具体来说，适用于企业的 Windows 应用商店管理“在线授权应用”的内容和授权。 有关详细信息，请参阅[管理从适用于企业的 Windows 应用商店购买的应用](/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune)。


### 设备管理
- **针对 iOS 设备的 PFX 证书分发**Intune 管理员可以为 iOS 设备上的 Wi-Fi、电子邮件和 VPN 身份验证创建和部署 iOS PFX 证书。 此功能已可用于 Android 和 Windows 10 设备。 有关详细信息，请参阅[启用对使用证书配置文件的公司资源的访问](/intune/deploy-use/secure-resource-access-with-certificate-profiles)。


- **将应用和策略应用到基于用户类别选择的不同设备组** Intune 管理员现在可以定义自定义设备类别，以让用户在注册过程中从中进行选择。 例如，管理员可能想要用户指定是否要注册用于“收银机”或“送货车”或“库存间”的设备。 所选类别将使该设备成为 Intune 设备组的成员，这可用于将不同的应用和策略部署到已注册的设备。 有关详细信息，请参阅[使用设备组映射对设备进行分类](/intune/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune)。

### Microsoft 公司门户的更改和更新
此版本已针对公司门户进行了如下更改：

**Android 公司门户应用**

* 当你的用户发布一个由移动应用程序管理 (MAM) 管理的应用时，他们将看到一条消息，通知他们该应用由他们的公司管理。 用户现在可以点击“了解详细信息”链接以在此处获取有关“托管应用”意义的[详细信息](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_use_mgd_apps)。 他们还可以点击“不再显示”以便他们启动应用时不再显示该消息。
* 添加了新屏幕以指导用户完成注册过程，并提供有关用户应该注册的原因和 IT 管理员能够和不能够在他们的已注册设备上看到的内容的详细信息。 请参阅[注册说明](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc)以获取详细信息。
* 注册错误消息现在会显示在公司门户应用中。 以前，这些消息显示在公司门户网站上。 进行此更改意味着所有的错误消息现在只显示在一个位置而不是两个不同的位置。


**iOS 公司门户应用**
* 当你的用户发布一个由移动应用程序管理 (MAM) 管理的应用时，他们将看到一条消息，通知他们该应用由他们的公司管理。 用户现在可以点击“了解详细信息”链接以在此处获取有关“托管应用”意义的[详细信息](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_use_mgd_apps)。 他们还可以点击“不再显示”以便他们启动应用时不再显示该消息。
* 添加了新屏幕以指导用户完成注册过程，并提供有关用户应该注册的原因和 IT 管理员能够和不能够在他们的已注册设备上看到的内容的详细信息。 请参阅[注册说明](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device)以获取详细信息。
* 注册错误消息现在会显示在公司门户应用中。 以前，这些消息显示在公司门户网站上。 进行此更改意味着所有的错误消息现在只显示在一个位置而不是两个不同的位置。




## 2016 年 2 月
### Microsoft 公司门户的更改和更新

此版本已针对公司门户进行了如下更改：

#### Android 公司门户应用
- 添加了新屏幕以指导用户完成注册过程，并提供有关用户应该注册的原因和 IT 管理员能够和不能够在他们的已注册设备上看到的内容的详细信息。 请参阅[注册说明](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc)以获取详细信息。
- 注册错误消息现在会显示在公司门户应用中。 以前，这些消息显示在公司门户网站上。 进行此更改意味着所有的错误消息现在只显示在一个位置而不是两个不同的位置。

#### iOS 公司门户应用
 - 添加了新屏幕以指导用户完成注册过程，并提供有关用户应该注册的原因和 IT 管理员能够和不能够在他们的已注册设备上看到的内容的详细信息。 请参阅[注册说明](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device)以获取详细信息。

 - 注册错误消息现在会显示在公司门户应用中。 以前，这些消息显示在公司门户网站上。 进行此更改意味着所有的错误消息现在只显示在一个位置而不是两个不同的位置。


## 2016 年 1 月

### 利用 Windows 10 功能
* **运行状况证明服务的条件性访问** Intune 管理员现在可以在 Intune 管理控制台中查看 Windows 10 设备运行状况证明的状态。 设备运行状况证明让管理员能够确保客户端计算机具有可信 BIOS、TPM 和启动软件配置。 为了支持设备运行状况证明，客户端设备必须运行 Windows 10 并启用 TPM 2。 设备运行状况证明显示为以下各项启用的设备数：
    * 开机初期启动的反恶意软件
    * BitLocker
    * 安全启动
    * 代码完整性

    阅读 [Microsoft Intune 的设备合规性策略简介](/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune)以获取有关设备运行状况设置、收集的数据点和运行状况证明报告的详细信息。 [HAS 服务详细信息](https://msdn.microsoft.com/en-us/library/dn934876.aspx)深入解释了该服务。

* **Windows 10 Passport for Work 策略和证书管理**利用 Intune，可以[与 Microsoft Passport for Work 集成](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune)，这是使用 Active Directory 或 Azure Active Directory 帐户替代密码、智能卡或虚拟智能卡的一种适用于 Windows 10 的替代登录方法。 通过 Passport，你可以使用用户手势取代密码进行登录。 用户手势可以是简单 PIN、Windows Hello 等生物识别身份验证或指纹读取器等外部设备。

* **特定应用的 VPN**你可以选择通过 VPN 自动连接到企业网络的应用。 设置 VPN 配置文件时创建应用列表，如“通过 Microsoft Intune 使用 VPN 配置文件帮助用户连接到其工作”中所述。

* **Windows 10 完全擦除支持**你现在可以发起通过 Intune 管理控制台已在 Intune 中注册的 Windows 10 桌面设备的远程完全擦除。 Windows 10 完全擦除会对设备进行出厂重置。


### Apple 批量采购计划 (VPP) 更新
Intune 现在可以帮助你[管理通过适用于企业的 Apple 批量采购计划 (VPP) 购买的应用](/intune/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune)。 这包括同步 Apple 和 Intune 之间的许可证信息，和跟踪你已部署的每个应用的副本数量。

### 使用 IMEI 号码识别企业拥有的设备
现在可以对具有 IMEI 号码的移动设备平台[导入国际移动设备标识 (IMEI) 号码](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)，以帮助识别企业拥有的移动设备。 在 Intune 中注册后，带有导入的 IMEI 号码的设备就会被标记为“企业”，这些设备可用于应用与应用到个人拥有设备的策略不同的策略。

### 更多应用现在与 Intune MAM 策略相兼容
来自 Microsoft 合作伙伴的其他应用现在与 Intune 移动应用程序管理 (MAM) 策略（针对由 Intune 管理的设备）兼容：
* Box for EMM（来自 Box Inc）- 仅限 iOS
* Adobe Reader（来自 Adobe）- 仅限 Android
* Foxit PDF Reader（来自 Foxit Corporation）- iOS 和 Android


### 于 1 月结束 IE9 支持
从 2016 年 2 月开始，将不再支持 Internet Explorer 9 作为用于访问 Microsoft Intune 公司门户网站、Intune 帐户门户和 Intune 管理控制台的官方浏览器。 你将需要迁移到 Internet Explorer 10 或更高版本。


>[!div class="step-by-step"]

>[&larr; **Intune 中的新增功能**](whats-new-in-microsoft-intune.md)    



<!--HONumber=Oct16_HO1-->


