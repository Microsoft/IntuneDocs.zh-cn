---
title: "Microsoft Intune 新增功能"
titleSuffix: Intune on Azure
description: "了解 Intune Azure 门户新增功能"
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 08/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f28ce989b5907f7e7474543c364508424dc0c9cf
ms.sourcegitcommit: 0b164f806165d312acfc88815a60e325e3d02672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2017
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune 新增功能

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

了解 Microsoft Intune 每周新增功能。 另外，你还可以找到[即将发生的更改](#whats-coming)、有关服务的[重要说明](#notices)，以及有关[过去版本](whats-new-archive.md)的信息。

> [!Note]
> 许多功能最终将支持带 Configuration Manager 的混合客户部署。 有关新的混合功能的详细信息，请查看[混合新增功能页](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。


<!-- Common categories:  
  ### Role-based access control
  ### Device enrollment
  ### Device management
  ### App management
  ### Device configuration
  ### Intune apps
-->   


## <a name="week-of-august-21-2017"></a>含 2017 年 8 月 21 日的那周
### <a name="app-management"></a>应用管理
#### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Android 公司门户用户和应用保护策略用户的新登录体验 <!-- 621669 -->

最终用户现在可以在不注册 Android 设备的情况下，使用 Android 公司门户应用浏览应用、管理设备以及查看 IT 联系人信息。 此外，如果最终用户已使用受 Intune 应用保护策略保护的应用，并启动了 Android 公司门户，最终用户不会再接收到注册设备的提示。

## <a name="week-of-july-31-2017"></a>2017 年 7 月 31 日的这一周
### <a name="device-enrollment"></a>设备注册  

#### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version------1333256--1245463----"></a>按 OS 版本限制 Android 和 iOS 设备注册 <!--- 1333256,  1245463 --->
Intune 现在支持按操作系统版本号限制 iOS 和 Android 注册。 在“设备类型限制”下，IT 管理员现可设置平台配置，限制最低和最高操作系统值之间的注册。 Android 操作系统版本必须指定为 Major.Minor.Build.Rev，其中 Minor、Build 和 Rev 是可选的。 iOS 版本必须指定为 Major.Minor.Build，其中 Minor 和 Build 是可选的。 详细了解[设备注册限制](enrollment-restrictions-set.md)。

>[!NOTE]
>请勿通过 Apple 注册计划或 Apple Configurator 限制注册。

#### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment------1333272--1333275-1245709----"></a>限制 Android、iOS 和 macOS 设备的个人私有设备注册<!--- 1333272,  1333275, 1245709 --->
Intune 可通过将企业设备 IMEI 号码列入允许列表来限制个人设备注册。 Intune 现已使用设备序列号将此功能扩展到 iOS、Android 和 macOS。 通过将序列号上传到 Intune，可将设备预声明为企业所有的设备。 使用注册限制，可以阻止私人拥有的设备 (BYOD)，仅允许企业所有的设备进行注册。 详细了解[设备注册限制](enrollment-restrictions-set.md)。

若要导入序列号，请转至“设备注册” > “公司设备标识符”，单击“添加”，然后上传一个 CSV 文件（无标头，含两列，分别是序列号和详细信息，如 IMEI 号）。  若要限制私人拥有的设备，请转到“设备注册” > “注册限制”。 在“设备类型限制”下，选择“默认”，然后选择“平台配置”。 可以针对 iOS、Android 和 macOS“允许”或“阻止”私人拥有的设备。 


### <a name="device-management"></a>设备管理   

#### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>用于强制设备与 Intune 同步的新设备操作 <!-- 711369 -->
在此版本中，我们添加了一个新的设备操作，可强制所选设备立即通过 Intune 签入。 当设备签入时，该设备会立即收到已分配给自己的任何挂起的操作或策略。  此操作可帮助立即验证和对已分配的策略进行故障排除，而无需等待下一个安排的签入。
有关详细信息，请参阅[同步设备](device-sync.md)

#### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>强制受监视的 iOS 设备自动安装可用的最新软件更新 <!-- 777100 -->
软件更新工作区推出了一项新策略，可在该工作区中强制受监视的 iOS 设备自动安装可用的最新软件更新。 有关详细信息，请参阅[配置 iOS 更新策略](/intune/software-updates-ios)

#### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner-----954651-1172027---"></a>Check Point SandBlast Mobile - 新移动威胁防御伙伴<!-- 954651, 1172027 -->
可根据 Check Point SandBlast Mobile 给出的风险评估，使用条件访问控制移动设备对公司资源的访问，Check Point SandBlast Mobile 是与 Microsoft Intune 集成的移动威胁防御解决方案。

##### <a name="how-integration-with-intune-works"></a>与 Intune 的集成是如何发挥作用的？
基于从运行 Check Point SandBlast Mobile 的设备收集的遥测评估风险。 可基于通过 Intune 设备符合性策略启用的 Check Point SandBlast Mobile 风险评估配置 EMS 条件访问策略。 根据检测到的威胁，可允许或阻止不符合的设备访问企业资源。


### <a name="app-management"></a>应用管理

#### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business----748101---"></a>将应用部署为在适用于企业的 Microsoft 应用商店中可用<!-- 748101 -->
通过此版本，管理员现可将适用于企业的 Microsoft 应用商店分配为可用。 设置为可用时，最终用户可安装来自公司门户应用或网站的应用，而无需重定向到 Microsoft 应用商店。


### <a name="intune-apps"></a>Intune 应用  

#### <a name="ui-updates-to-the-company-portal-website---1313244-part-1--"></a>公司门户网站的用户界面更新 <!--1313244 part 1-->
我们对[公司门户网站](https://portal.manage.microsoft.com)的用户界面进行了几项更新，目的是增强最终用户体验。

- __对应用磁贴的改进__：应用图标现在显示时将具有基于图标主导颜色（如果可检测到）自动生成的背景色。 适用时，此背景会替代以前应用磁贴上显示的灰色边框。

    在即将发布的版本中，公司门户网站会尽可能显示大图标。 建议 IT 管理员使用像素大小不低于 120 x120 的高分辨率图标发布应用。 

- __导航更改__：导航栏项已移至左上角的汉堡菜单。 已删除“类别”页面。 用户现在可在浏览时按类别筛选内容。

- __对精选应用的更新__：我们在网站中添加了一个专用页面，用户可在其中浏览精选的应用，还可以对主页的“精选”部分做出一些用户界面调整。

#### <a name="ibooks-support-for-the-company-portal-website---1231841--"></a>针对公司门户网站的 iBooks 支持<!--1231841-->
我们已向公司门户网站添加了一个专用页面，允许用户浏览和下载 iBooks。 

### <a name="monitor-and-troubleshoot"></a>监视和故障排除

#### <a name="additional-help-desk-troubleshooting-details------applies-to-1263399-1326964-1341642----"></a>有关支持人员故障排除的其他详细信息 <!---  Applies to 1263399, 1326964, 1341642 --->
 
Intune 更新了故障排除的显示内容，并添加了提供给管理人员和支持人员的信息。 现在用户可以看到一个“分配”表，表中按组成员身份汇总了针对用户的所有分配。 此列表包括：
- 移动应用
- 相容性策略
- 配置文件
 
此外，“设备”表格现包括“Azure AD 联接类型”和“Azure AD 符合性”列。 有关详细信息，请参阅[帮助用户解决问题](help-desk-operators.md)。

### <a name="reporting"></a>报表

#### <a name="intune-data-warehouse-public-preview"></a>Intune 数据仓库（公共预览版）

Intune 数据仓库每天对数据进行采样，提供租户的历史视图。 可使用 Power BI 文件 (PBIX) 访问数据，该文件是一个 OData 链接，可与许多分析工具兼容或与 REST API 交互。 有关详细信息，请参阅[使用 Intune 数据仓库](reports-nav-create-intune-reports.md)。

## <a name="week-of-july-23rd-2017"></a>2017 年 7 月 23 日的这一周

### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>适用于 Windows 10 公司门户应用的浅色和深色模式<!---676547--->
最终用户将能够为 Windows 10 公司门户应用自定义颜色模式。 用户能够在公司门户应用的“设置”部分进行更改。 更改将在用户重启应用后显示。 对于 Windows 10 版本 1607 及更高版本，应用模式将默认为系统设置。 对于 Windows 10 版本 1511 及更早版本，应用模式将默认为浅色模式。

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>让最终用户能够在 Windows 10 公司门户应用中标记其设备组<!---807046-->
最终用户现在能够选择其设备所属的组，方法是直接从 Windows 10 公司门户应用中标记该组。




## <a name="notices"></a>通知

### <a name="ip-addresses-for-intune-updated----1175274---"></a>更新了 Intune 的 IP 地址 <!-- 1175274 -->
[更新后的 DNS 名称和 IP 地址列表](/intune/network-bandwidth-use)可用于防火墙代理设置。

### <a name="use-azure-active-directory-for-conditional-access----967947---"></a>使用 Azure Active Directory 进行条件性访问 <!-- 967947 -->
条件性访问位于 Azure 控制台的 Azure Active Directory 部分，可为云应用（例如 Office 365 Exchange Online 和 SharePoint Online ）的设置策略提供更强大和更灵活的框架。  使用“Azure Active Directory 中的条件访问”边栏选项卡（而非经典 Intune 控制台）配置策略。 需要在 Azure 控制台中重新创建经典 Intune 控制台中的现有策略。 有关详细信息，请参阅[创建 Azure AD 条件性访问策略](/intune/conditional-access-exchange-create.md#create-azure-ad-conditional-access-policies-in-intune-azure-preview)

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接访问 Apple 注册方案<!--951869-->
对于在 2017 年 1 月之后创建的 Intune 帐户，Intune 支持在 Azure 门户中使用注册设备工作负荷直接访问 Apple 注册方案。 以前，仅能通过经典 Intune 门户中的链接访问 Apple 注册预览版。 2017 年 1 月之前创建的 Intune 帐户需要进行一次性迁移，然后才能使用 Azure 中的这些功能。 迁移的计划目前尚未公布，但详细信息将尽快发布。 强烈建议创建一个试用帐户，在现有帐户无法访问 Azure 门户时测试新体验。

### <a name="administration-roles-being-replaced-in-azure-portal"></a>在 Azure 门户中被替换的管理角色
在 Intune 经典门户 (Silverlight) 中使用的现有移动应用程序管理 (MAM) 管理角色（参与者、所有者和只读）被替换为 Intune Azure 门户中一套完整的基于角色的新的管理控制方法 (RBAC)。 在迁移到 Azure 门户后，需要将管理员重新分配到这些新的管理角色。 有关 RBAC 和新角色的详细信息，请参阅 [Microsoft Intune 基于角色的访问控制](/intune/role-based-access-control)。



## <a name="whats-coming"></a>即将推出

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

在 Azure 门户上转到 Intune，然后查看“设备”>“所有设备”，并按 iOS 版本进行筛选以查看任何操作系统早于 iOS 9 的当前设备。


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 将要求更新应用传输安全<!--748318-->
Apple 宣布他们将强制对应用程序传输安全 (ATS) 实施特定要求。 使用 ATS 对所有通过 HTTPS 的应用通信实施更严格的安全措施。 此更改会影响使用 iOS 公司门户应用的 Intune 客户。

我们通过强制实施新的 ATS 要求的 Apple TestFlight 计划提供了适用于 iOS 的公司门户应用的可用版本。 如果你想要试用以测试你的 ATS 符合性，请发送电子邮件至 <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a>，并提供你的名字、姓氏、电子邮件地址和公司名称。 请查看 [Intune 支持博客](https://aka.ms/compportalats)，了解更多详细信息。

### <a name="see-also"></a>另请参阅
* [Microsoft Intune 博客](http://go.microsoft.com/fwlink/?LinkID=273882)
* [云平台路线图](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [What's new in the Company Portal UI](whats-new-app-ui.md)（公司门户 UI 新增功能）
* [前几个月的新增功能](whats-new-archive.md)
