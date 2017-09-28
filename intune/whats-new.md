---
title: "Microsoft Intune 新增功能"
titlesuffix: Azure portal
description: "了解 Intune Azure 门户新增功能"
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 09/18/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 08a22a1fa6829807860b6278181dd638f1049770
ms.sourcegitcommit: 0d9bfd92bf5958261ed83b1f150bf207b7ba7e56
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/21/2017
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune 新增功能

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

了解 Microsoft Intune 每周新增功能。 另外，你还可以找到[即将发生的更改](#whats-coming)、有关服务的[重要说明](#notices)，以及有关[过去版本](whats-new-archive.md)的信息。

> [!Note]
> 许多功能最终将支持带 Configuration Manager 的混合客户部署。 有关新的混合功能的详细信息，请查看[混合新增功能页](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。


<!-- Common categories:  
  ### Device enrollment
  ### Device management
  ### App management
  ### Device configuration
  ### Role-based access control
  ### Intune apps
  ### Monitor and troubleshoot

-->   

## <a name="week-of-september-11-2017"></a>含 2017 年 9 月 11 日的那周

### <a name="device-enrollment"></a>设备注册

#### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo----1475932---"></a>向最终用户额外发送有关 Android Oreo 公司门户应用的推送通知 <!---1475932--->

最终用户可以看到其他通知，其中指明了 Android Oreo 公司门户应用何时执行后台任务，如从 Intune 服务检索策略。 最终用户可以更加清楚地了解公司门户何时在设备上执行管理任务。 这是 Android Oreo 公司门户应用的全部[公司门户 UI 优化](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune)中的一部分。 

#### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>通知最终用户可查看哪些 iOS 设备信息 <!--739894--> 

我们已在适用于 iOS 的公司门户应用的“设备详细信息”屏幕上添加“所有权类型”。 这样，用户便可直接在 Intune 最终用户文档的此页中发现详细隐私信息。用户还将能在“关于”屏幕中找到此信息。 

#### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>允许最终用户无需进行注册便可访问适用于 Android 的公司门户应用 <!---1169910--->

最终用户很快将无需注册其设备就能访问 Android 公司门户应用。 使用应用保护策略的组织中的最终用户在打开公司门户应用时将不再收到指示其注册设备的提示。 最终用户也将能够从公司门户安装应用而无需注册其设备。 


#### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Android 公司门户应用的表述更容易理解 <!---1396349--->  

为了让最终用户能够更轻松地注册，Android 公司门户应用的注册流程已使用新文本进行了简化。 如果有自定义注册文档，则需要更新该文档，反映新的屏幕。 可以在 [Intune 最终用户应用的 UI 更新](whats-new-app-ui.md#week-of-september-11-2017)页面找到示例图片。

#### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>Windows 10 公司门户应用被添加到 Windows 信息保护允许策略 <!-- 677129 -->

Windows 10 公司门户应用已更新为支持 Windows 信息保护 (WIP)。 此类应用将可以被添加到 WIP 允许策略。 此更改生效后，便无需再将应用添加到“豁免”列表。 


## <a name="week-of-august-21-2017"></a>含 2017 年 8 月 21 日的那周

### <a name="device-enrollment"></a>设备注册
#### <a name="improvements-to-device-overview----1404453---"></a>设备概述改进<!-- 1404453 -->  
设备概述改进现在显示已注册设备，但不包含由 Exchange ActiveSync 管理的设备。 Exchange ActiveSync 设备没有与已注册设备相同的管理选项。 要在 Azure 门户的 Intune 中查看已注册设备数和各平台的已注册设备数，请转到“设备” > “概述”。

### <a name="device-management"></a>设备管理
#### <a name="improvements-to-device-inventory-collected-by-intune"></a>Intune 所收集设备清单的改进
<!-- 961134, 1104426, 1281327, 1333543 -->
此版本中，我们对由你管理的设备收集的清单信息做出了以下改进：
 
-   对于 Android 设备，现在可向设备清单添加一列，显示每个设备的最新修补程序级别。 将“安全修补程序级别”列添加到设备列表可查看此项。
-   筛选设备视图时，现在可按设备注册日期筛选设备。 例如，可仅显示于指定日期后注册的设备。
-   我们已对“上次签入日期”项所用的筛选器做出了一些改进。
-   在设备列表中，现在可显示公司拥有设备的电话号码。
此外，还可使用筛选器窗格按电话号码搜索设备。
 
有关设备清单的详细信息，请参阅[如何查看 Intune 设备清单](device-inventory.md)。

#### <a name="conditional-access-support-for-macos-devices"></a>对 macOS 设备的条件访问支持 
<!-- 720172 -->
现在可设置一个条件访问策略，要求 Mac 设备注册 Intune 且符合其设备符合性策略。 例如，用户可以下载适用于 macOS 的 Intune 公司门户应用并向 Intune 注册其 Mac 设备。 Intune 会评估 Mac 设备是否符合 PIN、加密、OS 版本和系统完整性等要求。

- 深入了解[对 macOS 设备的条件访问支持](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)。

#### <a name="company-portal-app-for-macos-is-in-public-preview----1484796---"></a>适用于 macOS 的公司门户应用当前为公共预览版<!---1484796--->
适用于 macOS 的公司门户应用目前作为企业移动性 + 安全性中条件访问公共预览版的一部分提供。 此版本支持 macOS 10.11 及更高版本。 在 [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal) 获取该应用。 


#### <a name="new-device-restriction-settings-for-windows-10"></a>适用于 Windows 10 的 Intune 新设备限制设置    
<!--1063965, 1308850  -->
在此版本中，我们为 [Windows 10 设备限制配置文件](/intune/device-restrictions-windows-10)添加了新设置，类别如下：

-   Windows Defender SmartScreen
-   App Store

#### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>更新至 Windows 10 终结点保护设备配置文件以应用 BitLocker 设置
<!--1459533 -->    
此版本中，我们已对 BitLocker 设置在 Windows 10 终结点保护设备配置文件中的作用方式做出如下改进：
 
在“Bitlocker OS 驱动器设置”下，对于“包含非兼容 TPM 芯片的 BitLocker”设置，选择“阻止”后，以前这会导致实际上允许 BitLocker 的问题。 我们已修复此问题，在选中“阻止”后会阻止 BitLocker。
在“Bitlocker OS 驱动器设置”下，对于“基于证书的数据恢复代理”设置，现在可显式阻止基于证书的数据恢复代理。 但是，默认情况下允许此代理。
在“BitLocker 固定数据驱动器设置”下，对于“数据恢复代理”设置，现在可显式阻止数据恢复代理。
有关详细信息，请参阅[适用于 Windows 10 及更高版本的 Endpoint Protection 设置](endpoint-protection-windows-10.md)。


### <a name="app-management"></a>应用管理
#### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Android 公司门户用户和应用保护策略用户的新登录体验 <!-- 621669 -->
最终用户现在可以使用 Android 公司门户应用浏览应用、管理设备和查看 IT 联系人信息，而无需注册其 Android 设备。 此外，如果最终用户已使用受 Intune 应用保护策略保护的应用，并启动了 Android 公司门户，最终用户不会再接收到注册设备的提示。

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Android 公司门户应用中用于切换电池优化的新设置 <!--1405990-->
适用于 Android 的公司门户应用的“设置”页添加了新设置，该设置可使用户轻松关闭公司门户和 Microsoft Authenticator 应用的电池优化。 设置中显示的应用名称将有所区别，具体取决于使用哪一应用管理工作帐户。 我们建议用户关闭电池优化，以提高用于同步电子邮件和数据的工作应用的性能。 

#### <a name="multi-identity-support-for-onenote-for-ios---------1234281---"></a>对适用于 iOS 的 OneNote 的多身份支持<!-- 1234281 -->
最终用户现在可对适用于 iOS 的 Microsoft OneNote 使用不同的帐户（工作帐户和个人帐户）。 应用保护策略可应用于工作笔记本中的公司数据，而不会影响个人笔记本。 例如，可通过应用策略允许用户查找工作笔记本中的信息，但阻止用户将工作笔记本中的公司数据复制粘贴到个人笔记本。
 
- 详细了解支持 Intune 的[应用保护和多身份](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)的应用。

#### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>用于允许和阻止适用于 Samsung KNOX 标准版设备的应用的新设置
<!-- 1305423 822899-->  
在此版本中，将添加新的[设备限制设置](device-restrictions-android.md)，以便用户能够指定以下应用列表：
 
- 允许用户安装的应用
- 已阻止用户运行的应用
- 设备上对用户隐藏的应用
 
可以通过 URL、包名称或从管理的应用列表中指定应用。

#### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>Intune 中新 Azure AD 基于应用的条件访问策略用户界面链接
<!-- 1016201 -->
IT 管理员现可通过 Azure AD 工作负荷中的新条件访问策略 UI 设置基于应用的条件策略。 位于 Azure 门户中 Intune 应用保护部分的基于应用的条件访问策略只是暂时保持现状，未来将逐步强制实施。 此外，还有指向 Intune 工作负荷中新条件访问策略 UI 的便捷链接。

- 深入了解 [Azure AD 中基于应用的条件访问](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference)。


## <a name="notices"></a>通知

### <a name="ip-addresses-for-intune-updated----1175274---"></a>更新了 Intune 的 IP 地址 <!-- 1175274 -->
[更新后的 DNS 名称和 IP 地址列表](/intune/network-bandwidth-use)可用于防火墙代理设置。

### <a name="use-azure-active-directory-for-conditional-access----967947---"></a>使用 Azure Active Directory 进行条件性访问 <!-- 967947 -->
条件访问位于 Azure 门户的“Azure Active Directory”部分，可为云应用（如 Office 365 Exchange Online 和 SharePoint Online）的设置策略提供更强大和更灵活的框架。  使用“Azure Active Directory 中的条件访问”边栏选项卡（而非 Intune 控制台）配置策略。 需要在 Azure 门户中重新创建 Intune 控制台中的现有策略。 有关详细信息，请参阅[创建 Azure AD 条件访问策略](/intune/conditional-access-exchange-create.md#create-azure-ad-conditional-access-policies-in-intune-azure-preview)。

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接访问 Apple 注册方案<!--951869-->
对于在 2017 年 1 月之后创建的 Intune 帐户，Intune 支持在 Azure 门户中使用注册设备工作负荷直接访问 Apple 注册方案。 以前，只能通过 Intune 经典门户中的链接访问 Apple 注册预览版。 2017 年 1 月之前创建的 Intune 帐户需要进行一次性迁移，然后才能使用 Azure 中的这些功能。 迁移的计划目前尚未公布，但详细信息将尽快发布。 强烈建议创建一个试用帐户，在现有帐户无法访问 Azure 门户时测试新体验。

### <a name="administration-roles-being-replaced-in-azure-portal"></a>在 Azure 门户中被替换的管理角色
在 Intune 经典门户 (Silverlight) 中使用的现有移动应用程序管理 (MAM) 管理角色（参与者、所有者和只读）被替换为 Intune Azure 门户中一套完整的基于角色的新的管理控制方法 (RBAC)。 在迁移到 Azure 门户后，需要将管理员重新分配到这些新的管理角色。 有关 RBAC 和新角色的详细信息，请参阅 [Microsoft Intune 基于角色的访问控制](/intune/role-based-access-control)。



## <a name="whats-coming"></a>即将推出

#### <a name="ios-11-mail-app-will-support-oauth----1196951---"></a>iOS 11 邮件应用将支持 OAuth<!---1196951--->
在使用 OAuth 的 iOS 设备上，使用 Intune 的条件访问支持更安全的身份验证。 为支持此功能，适用于 iOS 的公司门户应用上现在有一个不同的流，允许更安全的身份验证。 如果最终用户在邮件应用中尝试登录新的 Exchange 帐户，将会看到一个 Web 视图提示。 在 Intune 中注册后，用户会看到提示，要求允许本机邮件应用访问证书。 大多数最终用户不会再看到隔离电子邮件。 现有邮件帐户会继续使用基本身份验证协议，因此仍会收到隔离电子邮件。 最终用户的这种登录体验与 Office 移动应用的登录体验类似。

### <a name="end-of-support-for-ios-80----1164477---"></a>停止对 iOS 8.0 的支持<!---1164477--->
适用于 iOS 的托管应用和公司门户应用需要使用 iOS 9.0 和更高版本才能访问公司资源。 今年 9 月之前不更新的设备将不再能够访问公司门户应用或这些应用。 

### <a name="ui-updates-to-the-company-portal-website---1313244-part-2--"></a>公司门户网站的用户界面更新 <!--1313244 part 2-->
__对精选应用的更新__  
我们在网站中添加了一个专用页面，用户可在其中浏览精选的应用，还可以对主页的“精选”部分做出一些用户界面调整。 可以在[应用用户界面更新](whats-new-app-ui.md)页中查看这些更改效果。


### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>停止对 Android 4.3 及更低版本的支持 <!---1171127, 1326920 --->
Android 托管的应用和公司门户应用需要使用 Android 4.4 和更高版本访问公司资源。 在 10 月初之前还未更新的设备将不再能够访问公司门户应用或这些应用。 截至 12 月，所有已注册的设备将在 12 月强制停用，从而导致无法访问公司资源。 如果使用应用保护策略而不使用 MDM，应用将不会收到更新，并且随着时间推移其体验质量将会降低。


### <a name="platform-support-reminder-windows-phone-81-mainstream-support-ended-july-11-2017"></a>平台支持提醒：Windows Phone 8.1 主流支持将于 2017 年 7 月 11 日终止
<!-- 1327781 -->
2017 年 7 月 11 日，Windows Phone 8.1 平台的主流支持终止。 Windows 8.1 电脑支持不受影响。

不会对任何由 Intune 服务管理的 Windows Phone 8.1 设备产生即时影响。 注册的设备将继续工作，并且所有策略、配置和应用都将继续按预期方式工作。 请注意，对于 Intune 服务中的 Windows Phone 8.1 平台以及 Windows Phone 8.1 公司门户应用，不推出任何功能改进。

建议尽早将符合条件的 Windows Phone 8.1 设备升级到 Windows 10 移动版。 

### <a name="changes-in-support-for-the-intune-ios-company-portal-app-----1164474----"></a>Intune iOS 公司门户应用的支持更改 <!-- 1164474  -->
Microsoft Intune 公司门户应用 iOS 版即将会有新的版本，该版本仅支持运行 iOS 9.0 或更高版本的设备。 支持 iOS 8 的公司门户版本在未来短时间内仍将可用。 但是请注意，如果还使用启用了 MAM 的 iOS 应用（支持 iOS 9.0 和更高版本），需确保最终用户更新到最新 OS。 

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
虽然我们无法提供具体日期，但我们仍将此提前告知于你，以便你有时间做出计划。 请确保你的用户更新到 iOS 9+，且当公司门户应用发布后，请求最终用户更新其公司门户应用。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
鼓励用户更新到 iOS 9.0 或更高版本以充分利用 Intune 的新功能。  鼓励用户安装公司门户的新版本，从而利用它将提供的新功能。

转到 Azure 门户中 Intune，依次查看“设备”>“所有设备”，并按 iOS 版本进行筛选，以确定当前是否有任何设备的操作系统低于 iOS 9。


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 将要求更新应用传输安全<!--748318-->
Apple 宣布他们将强制对应用程序传输安全 (ATS) 实施特定要求。 使用 ATS 对所有通过 HTTPS 的应用通信实施更严格的安全措施。 此更改会影响使用 iOS 公司门户应用的 Intune 客户。

我们通过强制实施新的 ATS 要求的 Apple TestFlight 计划提供了适用于 iOS 的公司门户应用的可用版本。 如果你想要试用以测试你的 ATS 符合性，请发送电子邮件至 <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a>，并提供你的名字、姓氏、电子邮件地址和公司名称。 请查看 [Intune 支持博客](https://aka.ms/compportalats)，了解更多详细信息。

### <a name="see-also"></a>另请参阅
* [Microsoft Intune 博客](http://go.microsoft.com/fwlink/?LinkID=273882)
* [云平台路线图](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [What's new in the Company Portal UI](whats-new-app-ui.md)（公司门户 UI 新增功能）
* [前几个月的新增功能](whats-new-archive.md)
