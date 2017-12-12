---
title: "早期版本"
description: 
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 11/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 35bf193563deb34ac59df245c622bbc011d80b76
ms.sourcegitcommit: 67ec0606c5440cffa7734f4eefeb7121e9d4f94f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/08/2017
---
# <a name="the-early-edition-for-microsoft-intune---december-2017"></a>Microsoft Intune 的早期版本 - 2017 年 12 月

早期版本提供了一份即将发布的 Microsoft Intune 版本中将出现的功能列表。 此信息的提供具有条件限制，并且会不断变化。 请不要与公司外部共享此信息。 此处列出的某些功能有无法按期发布的风险并可能推迟到以后的版本。 正在以试验模式（外部测试）测试其他功能，以确保它们可立即供客户使用。 如果有任何问题或顾虑，请与 Microsoft 产品组联系人联系。

本页将定期更新。 返回查看其他更新。

> [!Note]
>下面的更改依据 Intune 开发。 有关新的混合功能的详细信息，请查看[混合新增功能页](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->


## <a name="intune-in-the-azure-portal"></a>Azure 门户中的 Intune

### <a name="app-protection-policies-----679615---"></a>应用保护策略<!-- 679615 -->
Intune 应用保护策略将提供创建默认全局策略的功能，以便快速对整个租户中所有用户启用保护。

### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>撤销 iOS 批量采购计划应用<!-- 820863 -->
对于具有一个或多个 iOS 批量采购计划 (VPP) 应用的给定设备，你将能够撤销相关的基于设备的应用许可证。 撤销应用许可证将不会从设备中卸载相关的 VPP 应用。 若要卸载 VPP 应用，必须将分配操作更改为“卸载”。 有关详细信息，请参阅[如何使用 Microsoft Intune 管理通过批量采购计划购买的 iOS 应用](vpp-apps-ios.md)。

### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>撤销 iOS 批量采购计划令牌的许可证<!-- 820870 -->
你将能够撤销给定 VPP 令牌的所有 iOS 批量采购计划 (VPP) 应用的许可证。

### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>删除 iOS 批量采购计划令牌<!-- 820879 -->
你将能够使用控制台删除 iOS 批量采购计划 (VPP) 令牌。 当你有重复的 VPP 令牌实例时，可能需要执行此操作。

### <a name="network-access-control-nac-device-check-in-reporting-----1232250---"></a>网络访问控制 (NAC) 设备签入报告<!-- 1232250 -->
在此次更改之前，IT 管理员无法从 Intune 方面确定 NAC 管理的设备是否与其 NAC 解决方案进行通信。 当 NAC 管理的设备没有与其 NAC 解决方案进行通信时，该设备被 NAC 解决方案视为不合规，因此被 NAC 解决方案自身阻止，随后又被依赖于设备合规状态的条件访问策略阻止。

通过此次更改，IT 管理员可以看到哪些 NAC 管理的设备已经成功地与它们的 NAC 解决方案进行通信。 这项新功能包括两个新的监控功能（位于 Intune 内的设备合规工作负载中），统计信息如下所示：
- 过去一小时内的平均 NAC 调用
- 上次 NAC 传入请求（日期/时间）

### <a name="new-ios-device-action------1244701---"></a>新的 iOS 设备操作<!-- 1244701 -->
你可以关闭 iOS 10.3 监督的设备。 此操作会立即关闭设备，而不会向最终用户发出警告。 当你在“设备”工作负载中选择设备时，可以在设备属性中找到“关闭（仅监督）”操作。

### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling----1361755-eeready---"></a>SCEP 和 PFX 证书处理的多个连接器支持<!-- 1361755 eeready -->
使用本地 NDES 连接器为设备提供证书的客户将能够在单个租户中配置多个连接器。

这项新功能支持以下方案：

- 高可用性

    每个 NDES 连接器从 Intune 中拉取证书请求。  如果一个 NDES 连接器脱机，另一个连接器可以继续处理请求。

### <a name="new-automatic-redeployment-setting----1469168---"></a>新的自动重新部署设置<!-- 1469168 -->
此设置允许具有管理权限的用户在设备锁定屏幕上使用“CTRL + Win + R”删除所有用户数据和设置。 将自动重新配置该设备并将其重新注册到管理体系中。

该设置可以在“Windows 10”->“设备限制”->“常规”->“自动重新部署”中找到。

### <a name="install-office-apps-on-macos-devices----1494311---"></a>在 macOS 设备上安装 Office 应用<!-- 1494311 -->
你将能够在 macOS 设备上安装 Office 应用。 这个新的应用类型将允许你安装 Word、Excel、PowerPoint、Outlook 和 OneNote。 这些应用也随 Microsoft AutoUpdater (MAU) 一起提供，以帮助保持应用处于安全和最新状态。

### <a name="surface-hub-resource-account-supported----1566442-eeready---"></a>支持的 Surface Hub 资源帐户<!-- 1566442 eeready -->
将添加新的设备操作，以便管理员可以定义和更新与 Surface Hub 关联的资源帐户。

资源帐户由 Surface Hub 用于通过 Skype/Exchange 进行身份验证，以便它可以加入会议。 可以创建一个唯一的资源帐户，以使 Surface Hub 作为会议室出现在会议中。 例如，资源帐户可能会显示为“会议室 B41/6233”。 通常需要针对会议室位置以及何时需要更改其他资源帐户参数来配置 Surface Hub 的资源帐户（称为设备帐户）。

如果管理员需要更新设备上的资源帐户，他们必须提供与该设备关联的当前 Active Directory/Azure Active Directory 凭据。 如果为设备启用了密码轮换，则管理员必须转到 Azure Active Directory 以查找密码。

> [!NOTE]
> 所有字段都会向下发送到一个包中，覆盖之前配置的所有字段。 空字段也会覆盖现有字段。

以下是管理员可以配置的设置：

- 资源帐户  

   -  Active Directory 用户  
   域名\用户名或用户主体名称 (UPN)：user@domainname.com
   - **密码**


- 可选的资源帐户参数（必须使用指定的资源帐户设置）
   -  密码轮换期间  
     出于安全原因，确保帐户密码每周由 Surface Hub 自动更新。 在启用此功能之后，要配置任何参数，Azure Active Directory 中的帐户必须先进行密码重置。

   - SIP（会话初始协议）地址    
     仅在自动发现失败时使用。

   - 电子邮件    
     设备/资源帐户的电子邮件地址。

   - Exchange Server    
     仅在自动发现失败时需要。

   - 日历同步    
     指定是否启用日历同步和其他 Exchange Server 服务。 例如：会议同步。

### <a name="intune-now-provides-the-account-move-operation-----1573558-1579830---"></a>Intune 现在提供帐户移动操作<!-- 1573558, 1579830 -->
“帐户移动”将租户从一个 Azure 扩展单元 (ASU) 迁移到另一个。 “帐户移动”可用于两种由客户启动的情景，当你调用请求它的 Intune 支持团队时，也可以是 Microsoft 驱动的情景，其中 Microsoft 需要对后端服务进行调整。 在“帐户移动”期间，租户进入只读模式 (ROM)。 在 ROM 期间，注册、重命名设备、更新符合性状态等服务操作将失败。

### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>新的 Windows Defender 安全中心 (WDSC) 设备配置文件设置<!-- 1335507 -->
Intune 在名为“Windows Defender 安全中心”的端点保护下添加了一个新的设备配置文件设置部分。 IT 管理员可以配置最终用户能访问 Windows Defender 安全中心应用的哪些支柱。 如果 IT 管理员在 Windows Defender 安全中心应用中隐藏支柱，则与隐藏支柱相关的所有通知都不会显示在用户设备上。

以下是管理员可以在 Windows Defender 安全中心设备配置文件设置中隐藏的支柱：
- 病毒和威胁防护
- 设备性能和运行状况
- 防火墙和网络保护
- 应用和浏览器控制
- 产品系列选项

IT 管理员还可以自定义用户接收的通知。 例如，你可以配置用户是接收由 WDSC 中的可见支柱生成的所有通知还是仅接收关键通知。 非关键通知包括 Windows Defender 防病毒活动的周期性摘要以及扫描完成时的通知。 所有其他通知被视为是关键通知。 另外，还可以自定义通知内容，例如，可以提供 IT 联系信息以嵌入用户设备上显示的通知。




<!-- the following are present prior to 1712 -->
### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>使用内置应用类型将 Office 365 移动应用分配到 iOS 和 Android 设备<!-- 1332318 -->
借助内置应用类型，可更轻松地创建 Office 365 应用并将其分配到管理的 iOS 和 Android 设备。 这些应用包括 Word、Excel、PowerPoint 和 OneDrive 等 Office 365 应用。 可将特定应用分配到应用类型并编辑应用信息配置。

### <a name="single-sign-on-support-for-ios----1333645---"></a>iOS 的单一登录支持 <!-- 1333645 -->  
可对 iOS 用户使用单一登录。 编码为在单一登录有效负载中查找用户凭据的 iOS 应用可使用此有效负载配置更新。 还可使用 UPN 和 Intune 设备 ID 配置主体名称和领域。

### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>允许受管理应用发送文本协议 <!-- 1414050  -->
受 Intune App SDK 管理的应用可发送短信。

### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>使用 Intune 远程锁定受管理的 macOS 设备 <!-- 1437691 -->
可锁定丢失的 macOS 设备并设置 6 位数的恢复 PIN。 锁定时，“设备概述”边栏选项卡会显示 PIN，直到发送另一个设备操作。

有关详细信息，请参阅[使用 Intune 远程锁定受管理设备](device-remote-lock.md)。


### <a name="assignment-conflict-resolution-has-changed-for-ios-store-apps----1480316---"></a>iOS 应用商店应用的分配冲突解决方法已发生更改 <!-- 1480316 -->
最终用户可能发现 iOS 应用商店应用可用性已发生更改。 目前，如果某个应用被分配到两个组并且在“必需和可用”和“不适用”之间存在冲突，则该应用会被解析为“必需和可用”。 更改后，遇到此冲突的应用会被解析为“不适用”。

对于某个应用被分配到多个组（具有不同应用意向）的情况，这项更改有助于避免混淆。

如果希望在 11 月服务发布前，在信息工作者门户和公司门户中使用应用，你有两个选择：

1. 删除组的“不适用”分配。
2. 创建一个新组，该组不包括已分配“必需和可用”意向的成员，然后将该组分配为“不适用”。

有关详细信息，请参阅[如何使用 Microsoft Intune 将应用分配到组](apps-deploy.md)。

> [!Note]
> 发布后，无法在 Intune 经典控制台中查看或修改移动设备管理 (MDM) 应用分配。 但是，可使用 Azure 控制台或 Intune 图形 API 分配应用。

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731---"></a>独立于 Android 设备管理 Android for Work 设备 <!-- 1490731 -->
Intune 支持独立于 Android 平台管理 Android for Work 设备的注册。 这些设置位于“设备注册” > “注册限制” > “设备类型限制”下。 （这些设置之前位于“设备注册” > “Android for Work 注册” > “Android for Work 注册设置”下。）

默认情况下，Android for Work 设备的设置与 Android 设备的设置相同。 但是，更改 Android for Work 设置后则不再相同。
 
如果阻止个人 Android for Work 注册，那么仅公司 Android 设备可注册为 Android for Work。

使用新设置时，请考虑下列各项：

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>如果之前从未载入 Android for Work 注册
默认设备类型限制将阻止新的 Android for Work 平台。 载入该功能后，可允许设备注册 Android for Work。 为此，请更改默认值或新建一个设备类型限制，取代默认设备类型限制。

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>如果已载入 Android for Work 注册
如果之前已载入，那么情况取决于所选设置：

| Setting | 默认设备类型限制中的 Android for Work 状态 | 注意 |
| --- | --- | --- |
| **将所有设备作为 Android 管理** | 已阻止 | 所有 Android 设备均不注册 Android for Work。 |
| 将受支持设备作为 Android for Work 管理 | ，然后用户才能访问 | 所有支持 Android for Work 的 Android 设备均须注册 Android for Work。 |
| **仅为这些组中的用户将受支持设备作为 Android for Work 管理** | 已阻止 | 创建单独的设备类型限制策略替代默认值。 此策略将之前选择的组定义为允许 Android for Work 注册。 允许所选组中的用户继续注册 Android for Work 设备。 所有其他用户则不能注册 Android for Work。 |

所有情况下都将保留预期规则。 对你来说，无需任何操作即可维护环境中的 Android for Work 全局或按组允许。

这些更改随 11 月更新一起推出，但可能需要一些时间才能在你的帐户上执行。 当帐户可使用这些更改时，你会在 Office 365 门户中收到确认通知。


### <a name="configure-an-ios-app-pin----1586774---"></a>配置 iOS 应用 PIN <!-- 1586774 -->
很快，便能要求目标 iOS 应用使用 PIN。 几天后，还可通过 Azure 门户配置 PIN 需求和到期日期。 需要时，用户必须设置并使用新的 PIN 才有权访问 iOS 应用。 只有使用 Intune App SDK 启用应用保护的 iOS 应用才支持此功能。

### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>为个人设备添加“查找我的 iPhone” <!--1427287-->
将可查看 iOS 设备是否已开启“激活锁”。 经典门户中的 Intune 之前并不提供此功能。

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory 网站可能需要 Intune Managed Browser 应用，并且支持 Managed Browser（公共预览版）的单一登录<!-- 710595 -->   
利用 Azure Active Directory (Azure AD)，可在移动设备上将对网站的访问限于 Intune Managed Browser 应用。 在 Managed Browser 中，网站数据可保持安全并且独立于最终用户的个人数据。 此外，Managed Browser 支持受 Azure AD 保护的站点的单一登录功能。 通过登录 Managed Browser，或在设备上将 Managed Browser 与由 Intune 管理的其他应用配合使用，用户无需输入凭据，Managed Browser 即可访问受 Azure AD 保护的公司站点。 此功能适用于 Outlook Web Access (OWA) 和 SharePoint Online 等站点，以及通过 Azure 应用代理访问的 Intranet 资源等其他公司站点。


<!-- the following are present prior to 1710 -->



### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>支持 Windows 10 版本升级策略 <!-- 903672(archived), 1119689 -->  
可以创建 Windows 10 版本升级策略，将 Windows 10 设备升级到 Windows 10 教育版、Windows 10 教育版 N、Windows 10 专业版、Windows 10 专业版 N、Windows 10 专业教育版和 Windows 10 专业教育版 N。有关 Windows 10 版本升级的详细信息，请参阅[如何配置 Windows 10 版本升级](edition-upgrade-configure-windows-10.md)。




<!-- the following are present prior to 1709 -->



### <a name="android-for-work-support-for-lookout----1087312---"></a>Lookout 的 Android for Work 支持<!-- 1087312 -->   
在使用 Lookout for Work 应用时，Lookout 的 Intune 连接器将支持 Android for Work 设备。 可以在容器内部或外部部署 Lookout 应用。

### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Intune 应用保护和 Citrix MDX 开发工具 <!-- 709185 -->
可以同时使用 Citrix XenMobile MDX 和 Microsoft Intune 来管理设备和应用。 通过使用此方法，可在使用 Citrix mVPN 技术的同时通过 Intune 应用保护策略管理应用。

能够查找包含适用于iOS 和 Android 的 App Wrapping Tool 和 Intune App SDK 的代码存储库，同时还能集成 Citrix MDX mVPN 技术。


### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>本地 Exchange 连接器高可用性支持 <!-- 676614 -->   
能够拥有用于本地 Exchange 连接器的多个客户端访问服务器 (CAS) 角色。 例如，如果主 CAS 失败，Exchange 连接器会收到一个用于回退到其他 CAS 的查询。 此功能可确保服务不中断。

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>适用于 Exchange 连接器的 System Center Operations Manager 管理包<!-- 885457 -->   
将会提供适用于 Exchange 连接器的 System Center Operations Manager 管理包帮助你分析 Exchange 连接器日志。 此管理包将在需要进行问题故障排除时为你提供监控 Intune 的多种方式。





## <a name="intune-apps"></a>Intune 应用

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>利用 Android 版公司门户应用帮助用户自助 <!---1573324, 1573150, 1558616, 1564878--->
Android 版公司门户应用为最终用户添加了说明，帮助他们了解并自行解决（如果可能）新用例。 

- 系统会显示新消息，说明已部署加密符合性策略，但根据 [Google 推荐准则](https://developer.android.com/reference/android/app/admin/DevicePolicyManager.html#setStorageEncryption(android.content.ComponentName, boolean)，[设备制造商未对设备加密](/intune-user-help/your-device-appears-encrypted-but-cp-says-otherwise-android)。
- 如果最终用户达到允许添加的最大设备数，他们将被引导至 (Azure Active Directory 门户)[https://account.activedirectory.windowsazure.com/r/#/profile]，以删除设备。 
- 最终用户会得到可遵循的步骤，帮助他们[修复 Samsung KNOX 设备上的激活错误](https://go.microsoft.com/fwlink/?linkid=859718)或[关闭节能模式](/intune-user-help/power-saving-mode-android)。 如果这些解决方案均无法解决问题，请查看[将日志提交给 Microsoft](/intune-user-help/send-logs-to-microsoft-ios) 的相关说明。 


### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>适用于 Android 设备的新“解决”操作<!---1583480--->
Android 版公司门户应用在“更新设备设置”页中引入了“解决”操作。 选择此选项会将最终用户直接转至导致其设备不符合的设置。 Android 版公司门户应用当前为以下设置提供此操作：[设备密码](/intune-user-help/set-your-pin-or-password-android)、[设备加密](/intune-user-help/encrypt-your-device-android)、[USB 调试](/intune-user-help/you-need-to-turn-off-usb-debugging-android)和[未知源](/intune-user-help/you-need-to-turn-off-unknown-sources-android)。 




<!-- the following are present prior to 1711 -->


### <a name="redirecting-macos-users-to-our-new-company-portal-app---1380728--"></a>将 macOS 用户重定向到新公司门户应用<!--1380728-->   
当最终用户登录公司门户网站注册其 macOS 设备时，系统会将其定向到下载 macOS 版新公司门户应用的页面，以便完成此过程。 使用 OS X El Capitan 10.11 或更高版本的 macOS 设备会出现这种情况。 


<!-- the following are present prior to 1710 -->



### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>现在可以在没有注册提示的情况下，安装可注册或不可注册的应用。 <!-- 1334712 -->
在 Android 公司门户应用中，可以在没有注册提示的情况下，安装可注册或不可注册的公司应用。


<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>iOS 和 Android 的 Intune Managed Browser 支持<!-- 1374196 -->
自 2017 年 10 月起，Android 版 Intune Managed Browser 应用将仅支持运行 Android 4.4 及更高版本的设备。 iOS 上的 Intune Managed Browser 应用将仅支持运行 iOS 9.0 及更高版本的设备。 早期版本的 Android 和 iOS 将能够继续使用 Managed Browser，但不能安装新版本的应用，并且可能无法访问所有应用功能。 建议将这些设备更新为受支持的操作系统版本。


### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>改进了用户达到允许注册的最大设备数时提示的错误消息 <!-- 1270370 -->
最终用户将不再看到普通错误消息，而将看到一条友好且可操作的错误消息：“注册设备数已达到 IT 管理员允许的最大数量。请删除已注册的设备，或者向 IT 管理员寻求帮助。”




## <a name="notices"></a>通知

此时没有任何活动通知。




### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。
