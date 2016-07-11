---
experiment_id: lindavr-abtest-20160527
title: "新增功能 | Microsoft Intune"
description: "了解 Microsoft Intune 的当月新增功能和过去版本"
keywords: 
author: Lindavr
manager: jeffgilb
ms.date: 06/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
ms.sourcegitcommit: d1fb04dbb8746637bf72c1e227f36fe589594ca0
ms.openlocfilehash: ae524a989e236e84a6ce9d8266fc648dd683a825


---

# Microsoft Intune 新增功能
了解此版本 Microsoft Intune 中的新增功能。 你还可以发现需要计划的即将发生的更改，以及有关过去版本的信息。

以下是此版本中的新增功能。 除了 Windows Defender 策略设置更新，所有这些功能还受混合客户部署（Configuration Manager 与 Intune）支持。 有关新的混合功能的详细信息，请查看[混合新增功能页](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx)。

## 2016 年 6 月
### Intune 服务运行状况
Intune 服务运行状态信息已随同其他 Microsoft 服务一起移到一个中心位置。 现在，你可在服务运行状态下的 Office 365 管理门户中找到此信息。 有关详细信息，请参阅[此博客文章](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/)。

## 应用管理
- **增强的 Windows 10 企业数据策略配置体验。** 我们围绕创建应用规则、指定网络边界定义和其他企业数据保护设置增强了 Windows 10 企业数据保护策略配置体验。 若要了解详细信息，请参阅 [Create an enterprise data protection (EDP) policy using Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune)（使用 Microsoft Intune 创建企业数据保护 (EDP) 策略）。


## 设备管理
- **Windows Defender 策略设置，可以避免可能不需要的应用。** 名为“**可能不需要的应用程序检测**”的新 Windows Defender 设置已被添加到 Windows 10 桌面版和移动版的常规配置。 你可以使用此设置以防止已注册的 Windows 台式计算机运行被 Windows Defender 分类为可能不需要的软件。 你可以防止这些应用程序运行，或使用审核模式在安装了不需要的应用程序时进行报告。 有关详细信息，请参阅 [Microsoft Intune 中的 Windows 10 策略设置](https://docs.microsoft.com/en-us/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune)。
<!---TFS 1244478--->

## 条件性访问
- **Intune 的 Cisco ISE 网络访问控制策略。**  使用 Cisco 标识服务引擎 (ISE) 2.1 并使用 Microsoft Intune 的客户可以在 ISE 中设置网络访问控制策略。

    此策略下，需要使用 WiFi 或 VPN 连接到网络的设备必须在符合以下条件后才被允许访问：

    * 必须由 Intune 进行管理
    * 必须符合任何已部署的 Intune 合规性策略

 非合规设备的最终用户将被提示注册和修正任何合规性问题以获取访问权限。
- **浏览器的条件性访问。** 可以为 [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md) 和 [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md) 设置条件访问策略，以便仅允许通过托管且合规的 iOS 和 Android 设备上受支持的 Web 浏览器对其进行访问。 尝试通过 iOS 和 Android 设备登录到 Outlook Web Access (OWA) 和 SharePoint 站点的最终用户，系统将提示通过 Intune 注册其设备以及在完成登录前解决任何非合规性问题。
<!---TFS 1175844--->

- **Dynamics CRM Online 支持条件性访问。** 可以为 [Dynamics CRM Online](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md) 设置条件访问策略，以便仅允许托管且合规的 iOS 和 Android 设备对其进行访问。 系统将提示尝试登录到 iOS 和 Android 设备上的 Dynamics CRM 移动应用的最终用户注册 Intune 并在登录完成前修正任何非合规性问题。
<!---TFS1295358--->


## 公司门户更新

### Android 公司门户应用

- 当 IT 管理员应用了新的“要求设备不允许安装来自未知源的应用 (Android 4.0 +)”策略时，Android 4.0 或更高版本设备的最终用户将看到消息“必须禁用来自未知来源的安装”。 用户将需要转到“设置” > “安全”，然后关闭“未知源”。 通过合规性消息中的链接，用户可获取有关该消息和为什么需要禁用该设置的详细[信息](/Intune/EndUser/you-are-asked-to-turn-off-unknown-sources-android)。

- 当 IT 管理员应用了新的“要求设备已启用扫描应用的安全威胁 (Android 4.0 +)”策略时，Android 4.0 或更高版本设备的最终用户将看到消息“扫描设备的安全威胁”。 用户将需要转到“设置” > “Google” > “安全”，然后打开“扫描设备的安全威胁”。 通过合规性消息中的链接，用户可获取有关该消息和为什么需要启用该设置的详细[信息](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android)。

- 当 IT 管理员应用了新的“要求禁用 USB 调试 (Android 4.2 +)”策略时，Android 4.2 或更高版本设备的最终用户将看到消息“必须禁用 USB 调试”。 用户将需要转到“设置” > “开发人员”选项，然后关闭“USB 调试”。 通过合规性消息中的链接，用户可获取有关该消息和为什么需要禁用该设置的详细[信息](/Intune/EndUser/you-are-asked-to-turn-off-usb-debugging-android)。

- 当 IT 管理员应用新的“最低 Android 安全修补程序级别 (Android 6.0+)”策略时，Android 6.0 或更高版本设备用户会看到消息“此设备不符合最低 Android 安全修补程序级别”。 用户将需要安装所需的安全修补程序。 通过合规性消息中的链接，用户可获取有关如何安装所需安全修补程序并查看当前已安装的安全修补程序的[信息](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android)。

### iOS 公司门户应用

- 当最终用户安装业务线应用时，现在它们将看到改进的应用安装体验。 如果应用安装要花很长时间，用户可以手动同步设备以强制继续同步过程。 若要查看最终用户说明，请参阅[手动同步 iOS 设备](/Intune/EndUser/sync-your-device-manually-ios.md)。

- 适用于 iOS 的 Microsoft Intune 公司门户应用已更新，可支持 iOS 8.0 和更高版本。 此更新意味着，仅当设备正在运行 iOS 8.0 或更高版本时，最终用户才可在 Intune 中安装公司门户应用并注册新设备。 如果用户已注册运行不受支持的 iOS 版本的设备，则这些用户可以继续使用其设备上的公司门户应用。


## 即将推出

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
    - 2016 年 8 月，新租户将看不到创建通知规则向导的步骤二。 正在退出的租户不受影响。
    - 2016 年 9 月左右，某些现有租户将看不到向导中的“选择设备组”。
    - 2016 年 11 月左右，我们期望所有租户将不会看到向导中的“选择设备组”。


- **iOS 公司门户应用的支持更改**。 在 7 月，要求适用于 iOS 的 Microsoft Intune 公司门户应用的所有用户都使用最新版本。 新用户将只能够下载最新版本，而当前用户必须更新到最新版本。 最新版本需要 iOS 8.0 或更高版本，因此运行较旧的 iOS 版本的设备将无法使用公司门户或者进行注册，直到将其设备更新为 iOS 8.0 或更高版本，并且将公司门户应用更新到最新版本。 运行 iOS 8.0 以下版本的已注册设备将继续受管理，并将列在 Intune 管理员控制台中。





## 早期 Intune 发行版本
如果想要查看在过去六个月内发布在 Intune 中的内容，它们已在[早期 Intune 发行版本](previous-intune-releases.md)文章中列出。
> [!div class="op_single_selector"]
- [2016 年 4 月](previous-intune-releases.md)
- [2016 年 3 月](previous-intune-releases.md)
- [2016 年 2 月](previous-intune-releases.md)
- [2016 年 1 月](previous-intune-releases.md)
- [2015 年 12 月](previous-intune-releases.md)
- [2015 年 11 月](previous-intune-releases.md)




### 另请参阅
* [Microsoft Intune 博客](http://go.microsoft.com/fwlink/?LinkID=273882)
* [云平台路线图](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)



<!--HONumber=Jun16_HO4-->


