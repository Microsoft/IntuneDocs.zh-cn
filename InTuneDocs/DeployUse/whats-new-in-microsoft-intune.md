---
title: "新增功能 | Microsoft Intune"
description: "了解 Microsoft Intune 的当月新增功能和过去版本"
keywords: 
author: Lindavr
manager: jeffgilb
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b8bff8951c8ced7656f007787d614fd277401fd0
ms.openlocfilehash: 35612b07cf18d8038af51cdfac5146b9e8a876fc


---

# Microsoft Intune 新增功能
了解此版本 Microsoft Intune 中的新增功能。 你还可以发现需要计划的即将发生的更改，以及有关过去版本的信息。

下面的更改依据 Intune 开发。 所有这些功能最终将支持混合客户部署（带 Intune 的 Configuration Manager）。 有关新的混合功能的详细信息，请查看[混合新增功能页](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx)。


## 2016 年 7 月
## 应用管理
### 改善应用预配配置文件更新体验
Apple iOS 业务线移动应用附带预配配置文件和证书签名的代码。 当应用在 iOS 设备上运行时，iOS 会确认 iOS 应用的完整性，并强制实施由预配配置文件定义的策略。

用于签署应用的企业签名证书通常持续 3 年。 但是，预配配置文件将在 1 年后过期。 利用此更新，Intune 会为你提供一些工具，用于主动地将新预配配置文件策略部署到安装了即将到期的应用而证书仍有效的设备。 有关详细信息，请参阅[使用 iOS 移动预配配置文件策略以保持你的业务线应用最新](/intune/deploy-use/ios-mobile-app-provisioning-profiles)。
<!--- TFS 1280247--->
### 用于 Intune 应用的 Xamarin SDK 已推出
Intune 应用 SDK Xamarin 组件允许你在使用 Xamarin 生成的移动 iOS 和 Android 应用中启用 Intune 移动应用管理功能。 你可以在 [Xamarin 应用商店](https://components.xamarin.com/view/Microsoft.Intune.MAM)中或在 [Microsoft Intune Github 页面](https://github.com/msintuneappsdk)上找到该组件。
<!--- TFS 1061478 --->

## 设备管理
### 提高了设备注册限制
Intune 将每个用户的设备的最大可配置设备注册限制从 5 提高到了 15。
<!---TFS 1289896 --->



## 公司门户更新
### 公司门户网站
- **改善了注册 Windows 设备时的最终用户体验**<br/>
使用条件访问时，Windows 8.1、Windows 10 桌面版和 Windows 10 移动版的注册步骤已在公司门户网站中阐明。 用户现在将看到单独的“设备注册”和“工作区加入”步骤，从而在他们遇到工作区加入 (WPJ) 失败时更易于看到设备的状态以及完成此过程。 执行单独的步骤还可以简化 IT 管理员排除故障的过程。 以前，当最终用户尝试注册并且 WPJ 除外的所有注册步骤都成功时，已注册的设备将不出现在用户要标识的设备列表中，因而使用户感到困惑。

### Android
- **Android 公司门户应用**<br/>
如果 Android 最终用户看到一条错误消息，指出其设备缺少所需的证书，用户可以点击“如何解决此问题”按钮以获取安装缺少的证书的[步骤](/intune/enduser/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator)。 如果用户完成这些步骤，但看到另一条“缺少证书”的错误消息，系统会要求用户联系其 IT 管理员，并提供此[链接](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues)，其中包含 IT 管理员可以用于解决证书问题的步骤。

- **限制旁加载的应用安装到注册的设备**<br/>
Android 设备不能再通过公司门户网站安装应用程序，除非使用适用于 Android 的 Intune 公司门户应用已在 Intune 中注册设备。
<!---TFS 1299082--->

### iOS
- **对 iOS 公司门户应用中设备注册管理器帐户的更改**<br/>
若要提高性能和可扩展性，Intune 不再在 iOS 公司门户应用的“**我的设备**”窗格中显示所有设备注册管理器 (DEM) 设备。 仅显示运行该应用的本地设备，且仅限该设备通过公司门户应用注册的情况下。

    DEM 用户可能会在本地设备上执行操作，但只能从 Intune 管理员控制台远程管理其他已注册设备。 此外，Intune 将不支持通过 Apple 设备注册计划或 Apple 配置器工具使用 DEM 帐户。 这两种注册方法已支持共享的 iOS 设备的无用户注册。

    当共享设备的无用户注册不可用时，仅使用 DEM 帐户。 有关详细信息，请参阅[使用 Microsoft Intune 中的“设备注册管理器”注册企业自有设备](https://docs.microsoft.com/en-us/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)。
<!---TFS 1233681--->

## 对 Windows 功能名称的更改
- [Microsoft Passport for Work](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune) 现在称为 **Windows Hello 企业版**。
- [企业数据保护](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune)现在称为 **Windows 信息保护**。

## 即将推出
### Intune 组将于 2016 年 8 月初过渡到 Azure Active Directory 组
Intune 正在创建使用 Azure Active Directory (AAD) 安全组的新组管理体验。 基于这些 Azure AD 的安全组可以包含用户和设备，并且当我们介绍新的基于 Azure 的 Intune 管理门户时，将用于所有组管理、策略部署和配置文件部署。

此新体验将：
- 使你无需在服务之间重复组。
- 允许你访问某些新的 Azure Active Directory Premium (AADP) 组功能。
- 提供使用 PowerShell 和图表的可扩展性。
- 跨企业移动性管理统一组管理体验。

若要启用移动到安全组，当前管理控制台中的体验将进行一些修改。 这些更改和 Azure AD 安全组的使用情况将记录在 Intune 文档中。

Intune 的新客户将看到当前租户执行操作之前的一些安全组更改。

除了组管理中的更改，还将弃用以下功能：
- 在创建新组的过程中排除成员或组
- “**未分组的用户**”和“**未分组的设备**”组
- 服务管理员角色中的“**管理组**”
- 对通知规则的基于组的自定义警报
- 利用报表中的组进行透视

有关缓解这些弃用功能的方式的详细信息，将于 8 月发布。

### 向 Android 公司门户添加“通知”
我们即将于 8 月发布 Android 公司门户的更新，这将在主页上引入一个新的“**通知**”图标。 点击此图标将访问“**通知**”页，该页将向你的最终用户显示在公司门户应用中需要注意的所有项，例如，设备非合规性、注册更新和注册激活。 如果还使用 iOS 公司门户应用，你将已看到通知体验。 通过引入“**通知**”页，只要设备已经注册，每次启动或恢复 Android 公司门户时，你将不会看到“**公司访问设置**”页。 我们听说你们中的许多人都已创建最终用户指南，而且非常感谢你们在指南/屏幕快照可能需要更新时提前通知我们。 请更新你的文档，以反映体验中即将发生的更改。 在此查找更新的屏幕快照：https://aka.ms/androidcpupdate。  



### 云路线图
通过[云平台路线图](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)实时了解 Intune 即将推出的开发内容。

### 服务弃用
- **iOS 公司门户应用的支持更改**<br/>
在 7 月，要求适用于 iOS 的 Microsoft Intune 公司门户应用的所有用户都使用最新版本。 新用户将只能够下载最新版本，而当前用户必须更新到最新版本。 最新版本需要 iOS 8.0 或更高版本，因此运行较旧的 iOS 版本的设备将无法使用公司门户或者进行注册，直到将其设备更新为 iOS 8.0 或更高版本，并且将公司门户应用更新到最新版本。 运行 iOS 8.0 以下版本的已注册设备将继续受管理，并将列在 Intune 管理员控制台中。  

- **最低 iOS 托管浏览器版本已更新为 8.0**<br/>
Intune 将于 8 月发布适用于 iOS 的更新的 Microsoft Intune 托管浏览器应用，该应用将仅支持运行 iOS 8.0 或更高版本的设备。 iOS 7.1 设备仍将能够使用现有的托管浏览器应用，请鼓励你的用户更新为 iOS 8.0 或更高版本，以访问和充分利用新的托管浏览器功能。  
<!---TFS 1313253--->

- **适用于 Windows 8 和 Windows Phone 8 的公司门户应用将从 2016 年 9 月起弃用** <br/>
从 2016 年 9 月开始，Microsoft Intune 将结束为适用于 Windows Phone 8 和 Windows 8 平台的 Microsoft Intune 公司门户应用提供支持。 将设备更新到 Windows 8.1 和 Windows Phone 8.1，并使用相应的 Windows 8.1 和 Windows Phone 8.1 公司门户应用继续向这些设备分发应用。
<!---TFS 1255391--->

- **Intune 查看器应用** <br/>
随着新的 RMS 共享应用的发布，我们将从 2016 年 8 月起删除以下 Intune 查看器应用：
    - Intune AV 查看器
    - Intune PDF 查看器
    - Google Play 中适用于 Android 的 Intune 图像查看器

  建议使用[适用于 Android 的 Rights Management 应用（RMS 共享）](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app)而不是使用 Intune 查看器应用，前者只需部署一个应用而不是三个单独的应用便可安全地查看 Android 设备上的公司文件。 如果不再支持 Intune 查看器应用，则将其从 Google 应用商店中删除并且不可供将来使用。

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



## 早期 Intune 发行版本
如果想要查看在过去六个月内发布在 Intune 中的内容，它们已在[早期 Intune 发行版本](previous-intune-releases.md)文章中列出。

### 另请参阅
* [Microsoft Intune 博客](http://go.microsoft.com/fwlink/?LinkID=273882)
* [云平台路线图](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)



<!--HONumber=Jul16_HO3-->


