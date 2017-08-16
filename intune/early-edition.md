---
title: "早期版本"
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 08/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5d5d8e0500a0ee928b1037a978f6d4dadab71495
ms.sourcegitcommit: 2ed8d1c39d4b3e3282111f1d758afb3a50f19f8f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2017
---
# <a name="the-early-edition-for-microsoft-intune---august-2017"></a>Microsoft Intune 的早期版本 - 2017 年 8 月

早期版本提供了一份即将发布的 Microsoft Intune 版本中将出现的功能列表。 此信息的提供具有条件限制，并且会不断变化。 请不要与公司外部共享此信息。 此处列出的某些功能有无法按期发布的风险并可能推迟到以后的版本。 正在以试验模式（外部测试）测试其他功能，以确保它们可立即供客户使用。 如果有任何问题或顾虑，请与 Microsoft 产品组联系人联系。

本页将定期更新。 返回查看其他更新。

> [!Note]
>下面的更改依据 Intune 开发。 有关新的混合功能的详细信息，请查看[混合新增功能页](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。

<!--

## What's coming to Intune on the Azure portal  
## What's coming to Intune apps
## Notices

-->



## <a name="intune-on-the-azure-portal"></a>Azure 门户上的 Intune

### <a name="actions-for-non-compliance----730266--"></a>针对不合规的操作<!--730266-->     
“针对不合规的操作”是合规性策略的新功能，允许在不合规的设备上执行操作。 可指定单个或多个操作，并指定这些操作必然会发生的时间段。 例如，可在设备变为不合规后，立即通过电子邮件通知该不合规设备的用户，或可在 3 天宽限期后，通过条件性访问阻止不合规设备访问公司资源。

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>列出使用较旧 iOS 版本的 iOS 设备的新报表   <!-- 1352223 -->
可在“软件更新”工作区中获取“过期 iOS 设备”报表。 在报表中，可以查看已应用 iOS 更新策略且具有可用更新的受监督 iOS 设备的列表。 可以查看每个设备的状态，了解该设备未自动更新的原因。 

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices-----822899--1305423--"></a>用于允许和阻止适用于 Samsung KNOX 标准版设备的应用的新设置<!-- 822899,  1305423-->   
将添加新的[设备限制设置](device-restrictions-android.md)，以便用户能够指定以下应用列表：
  - 允许用户安装的应用
  - 已阻止用户运行的应用
  - 设备上对用户隐藏的应用  

可以通过 URL、包名称或从管理的应用列表中指定应用。

### <a name="new-settings-for-windows-10-device-restriction-profile"></a>Windows 10 设备限制配置文件的新设置
<!--- 978575, 1308849, 1308850 -->
我们将向 Windows Defender SmartScreen 类别中的 Windows 10 设备限制配置文件中添加新设置。

有关 Windows 10 设备限制配置文件的详细信息，请参阅 [Windows 10 和更高版本的设备限制设置]( device-restrictions-windows-10.md)。

### <a name="new-device-restriction-settings-for-windows-10------1063965---"></a>适用于 Windows 10 的 Intune 设备限制设置   <!-- 1063965 -->
我们将向以下类别中的 [Windows 10 设备限制配置文件](/intune/device-restrictions-windows-10)添加新设置：
- Windows Defender SmartScreen
- App Store


### <a name="android-for-work-support-for-lookout----1087312---"></a>Lookout 的 Android for Work 支持<!-- 1087312 -->   
在使用 Lookout for Work 应用时，Lookout 的 Intune 连接器将支持 Android for Work 设备。 可以在容器内部或外部部署 Lookout 应用。


### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Intune 应用保护和 Citrix MDX 开发工具 <!-- 709185 -->
可以同时使用 Citrix XenMobile MDX 和 Microsoft Intune 来管理设备和应用。 通过使用此方法，可在使用 Citrix mVPN 技术的同时通过 Intune 应用保护策略管理应用。

能够查找包含适用于iOS 和 Android 的 App Wrapping Tool 和 Intune App SDK 的代码存储库，同时还能集成 Citrix MDX mVPN 技术。


### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium - 新移动威胁防御合作伙伴<!-- 954681 -->
能够根据 Zimperium 给出的风险评估，使用条件访问控制移动设备对公司资源的访问，Zimperium 是与 Microsoft Intune 集成的移动威胁防御解决方案。

#### <a name="how-integration-with-intune-works"></a>与 Intune 的集成是如何发挥作用的？
基于从运行 Zimperium 的设备收集的遥测评估风险。 可以基于通过 Intune 设备符合性策略启动的 Zimperium 风险评估配置 EMS 条件访问策略，从而根据检测到的威胁允许或阻止不符合要求的设备访问公司资源。

### <a name="new-azure-ad-conditional-access-policy-ui-link-from-intune-----1016201---"></a>Intune 中的新 Azure AD 条件访问策略用户界面链接 <!-- 1016201 -->
IT 管理员可以通过 Azure AD 工作负荷中的新条件访问策略设置基于应用的条件性策略。 位于 Azure Intune 应用保护部分的基于应用的条件访问策略只是暂时保持现状，未来将逐步强制实施。 Intune 工作负荷与 Azure AD 中的新条件访问策略用户界面存在便捷的链接。


### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>本地 Exchange 连接器高可用性支持 <!-- 676614 -->   
能够拥有用于本地 Exchange 连接器的多个客户端访问服务器 (CAS) 角色。 例如，如果主 CAS 失败，Exchange 连接器会收到一个用于回退到其他 CAS 的查询。 此功能可确保服务不中断。

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>适用于 Exchange 连接器的 System Center Operations Manager 管理包<!-- 885457 -->   
将会提供适用于 Exchange 连接器的 System Center Operations Manager 管理包帮助你分析 Exchange 连接器日志。 此管理包将在需要进行问题故障排除时为你提供监控 Intune 的多种方式。

### <a name="end-of-support-for-ios-80----1164477---"></a>停止对 iOS 8.0 的支持<!---1164477--->
适用于 iOS 的托管应用和公司门户应用需要使用 iOS 9.0 和更高版本才能访问公司资源。 今年 9 月之前不更新的设备将不再能够访问公司门户应用或这些应用。 截至 12 月底，将阻止对包括电子邮件在内的公司资源的任何访问。 

### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>停止对 Android 4.3 及更低版本的支持 <!---1171127, 1326920 --->
Android 托管的应用和公司门户应用需要使用 Android 4.4 和更高版本访问公司资源。 在 10 月初之前还未更新的设备将不再能够访问公司门户应用或这些应用。 截至 12 月，所有已注册的设备将在 12 月强制停用，从而导致无法访问公司资源。 如果使用应用保护策略而不使用 MDM，应用将不会收到更新，并且随着时间推移其体验质量将会降低。


### <a name="platform-support-reminder-windows-phone-81-mainstream-support-will-end-july-11-2017----1327781---"></a>平台支持提醒：Windows Phone 8.1 主流支持将于 2017 年 7 月 11 日结束 <!-- 1327781 -->  
2017 年 7 月 11 日，Windows Phone 8.1 平台的主流支持将迎来结束。 Windows 8.1 电脑支持不受影响。

不会对任何由 Intune 服务管理的 Windows Phone 8.1 设备产生即时影响。 注册的设备将继续工作，并且所有策略、配置和应用都将继续按预期方式工作。 请注意，对于 Intune 服务中的 Windows Phone 8.1 平台以及 Windows Phone 8.1 公司门户应用，不推出任何功能改进。

建议尽早将符合条件的 Windows Phone 8.1 设备升级到 Windows 10 移动版。 

## <a name="intune-apps"></a>Intune 应用

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>iOS 和 Android 的 Intune Managed Browser 支持<!---1374196--->

自 2017 年 10 月起，Android 版 Intune Managed Browser 应用将仅支持运行 Android 4.4 及更高版本的设备。 iOS 上的 Intune Managed Browser 应用将仅支持运行 iOS 9.0 及更高版本的设备。 早期版本的 Android 和 iOS 将能够继续使用 Managed Browser，但不能安装新版本的应用，并且可能无法访问所有应用功能。 建议将这些设备更新为受支持的操作系统版本。

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>允许最终用户无需进行注册便可访问适用于 Android 的公司门户应用 <!---1169910--->  
最终用户很快将无需注册其设备就能访问 Android 公司门户应用。 使用应用保护策略的组织中的最终用户在打开公司门户应用时将不再收到指示其注册设备的提示。 最终用户也将能够从公司门户安装应用而无需注册其设备。 

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>改进了用户达到允许注册的最大设备数时提示的错误消息 <!-- 1270370 -->
最终用户将不再看到普通错误消息，而将看到一条友好且可操作的错误消息：“注册设备数已达到 IT 管理员允许的最大数量。 请删除已注册的设备，或者向 IT 管理员寻求帮助。”

### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Android 公司门户用户和应用保护策略用户的新登录体验 <!-- 621669 -->
最终用户将能够在不注册 Android 设备的情况下，使用 Android 公司门户应用浏览应用、管理设备以及查看 IT 联系人信息。 此外，如果最终用户已使用受 Intune 应用保护策略保护的应用，并启动了 Android 公司门户，最终用户将不再会接收到注册设备的提示。 

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>通知最终用户可查看哪些 iOS 设备信息 <!--739894-->
我们将在 iOS 公司门户应用的“设备详细信息”屏幕上添加“所有权类型”。 这样，用户便可直接在 Intune 最终用户文档的此页中发现详细隐私信息。 用户还将能在“关于”屏幕中找到此信息。

### <a name="apps-details-pages-display-new-information-for-android-devices---1287476--"></a>应用详细信息页显示 Android 设备的新信息 <!--1287476-->
Android 公司门户应用的应用详细信息页将显示 IT 管理员为该应用定义的应用类别。

### <a name="intune-mobile-application-management-mam-dialog-boxes-now-have-a-modern-interface----1199015---"></a>“Intune 移动应用管理”(MAM) 对话框现在具有现代界面 <!-- 1199015 -->
经过更新，“Intune 移动应用管理”(MAM) 对话框现已具有现代外观和体验。 对话框功能与以前相同。

在现代 Android 设备上， Intune 现在显示的错误或通知对话框也将呈现出更新的外观和体验。

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Android 公司门户应用中用于切换电池优化的新设置 <!--1405990-->
Android 公司门户应用的“设置”页将添加新设置，该设置可使用户轻松关闭公司门户和 Microsoft Authenticator 应用的电池优化。 设置中显示的应用名称将有所区别，具体取决于使用哪一应用管理工作帐户。 我们建议用户关闭电池优化，以提高用于同步电子邮件和数据的工作应用的性能。 




## <a name="notices"></a>通知

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 将要求更新应用传输安全<!--748318-->   
自 2017 年春季开始，Apple 宣布他们将强制对应用程序传输安全 (ATS) 实施特定要求。 使用 ATS 对所有通过 HTTPS 的应用通信实施更严格的安全措施。 此更改会影响使用 iOS 公司门户应用的 Intune 客户。 请查看 [Intune 支持博客](https://aka.ms/compportalats)，了解更多详细信息。

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接访问 Apple 注册方案<!--951869-->   
对于在 2017 年 1 月之后创建的 Intune 帐户，Intune 支持在 Azure 预览门户中使用注册设备工作负荷直接访问 Apple 注册方案。 以前，仅能通过经典 Intune 门户中的链接访问 Apple 注册预览版。 2017 年 1 月之前创建的 Intune 帐户需要进行一次性迁移，然后才能使用 Azure 中的这些功能。 迁移的计划目前尚未公布，但详细信息将尽快发布。 强烈建议创建一个试用帐户，在现有帐户无法访问预览版时测试新体验。

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>做好应对更改的计划：Intune 将更改 Intune 合作伙伴门户体验<!-- 1050016 -->
自 2017 年 5 月中旬起，我们将从 manage.microsoft.com 中删除 Intune 合作伙伴页面（从服务更新入手）。  

如果你是合作伙伴管理员，将无法再代表客户在 Intune 合作伙伴页面中查看内容和执行操作，而是需要在 Microsoft 的其他两个合作伙伴门户之一进行登录。

使用 [Microsoft 合作伙伴中心](https://partnercenter.microsoft.com/)和 [Microsoft Office 365 合作伙伴管理中心](https://portal.office.com/)，可以登录所管理的客户帐户。 作为合作伙伴，未来请使用其中一个网站管理客户。



### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。
