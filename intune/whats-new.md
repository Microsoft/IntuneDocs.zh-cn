---
title: "Microsoft Intune 新增功能"
titleSuffix: Intune on Azure
description: "了解 Intune Azure 门户新增功能"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 06/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 73b43084c28436cb8a7e866dcee2d52694c60f5c
ms.openlocfilehash: 1a3069e128e25f4f0f5df7cc90392055729134fa
ms.contentlocale: zh-cn
ms.lasthandoff: 06/16/2017

---

# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune 新增功能

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

了解 Microsoft Intune 每周新增功能。 另外，你还可以找到[即将发生的更改](#whats-coming)、有关服务的[重要说明](#notices)，以及有关[过去版本](whats-new-archive.md)的信息。

> [!Note]
> 许多功能最终将支持带 Configuration Manager 的混合客户部署。 有关新的混合功能的详细信息，请查看[混合新增功能页](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。

## <a name="week-of-june-12-2017"></a>2017 年 6 月 12 日的这一周

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>新增可轻松删除公司门户的菜单操作 <!--1164569-->
根据用户反馈，适用于 Android 的公司门户应用新添加了一个菜单操作，可启动对设备中公司门户的删除。 此操作可将设备从 Intune 管理中删除，以便用户删除设备中的应用。 你可以在[应用 UI 中的新增功能](whats-new-app-ui.md)页和 [Android 最终用户文档](/intune-user-help/unenroll-your-device-from-intune-android)中查看这些更改。

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>与 Windows 10 创意者更新的应用同步改进 <!--676505-->

面向 Windows 10 的公司门户应用，现在将针对具有 Windows 10 创意者更新（版本 1703）的设备自动启动应用安装请求同步。 这将减少“正在挂起同步”状态下的应用安装停止问题。 此外，用户将可以从该应用内部手动启动同步。 

## <a name="week-of-june-5-2017"></a>2017 年 6 月 5 日的这一周

### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>Microsoft Intune 和条件性访问管理控制台正式发布

我们将宣布 Azure 管理控制台和条件性访问管理控制台上的新 Intune 正式发布。 通过 Azure 上的 Intune，你现在可以在一个统一的管理体验中管理所有 Intune MAM 和 MDM 功能，并利用 Azure AD 分组和定位。 Azure 中的条件性访问可以跨 Azure AD 和 Intune 在一个统一的控制台中集成丰富的功能。 而且，从管理体验上来看，移动到 Azure 平台还可让你用上现代浏览器。

Intune 现在 portal.azure.com 中可见，但在 Azure 控制台中没有“预览”标签。

此时，现有客户无需进行任何操作，除非你已在消息中心收到过系列消息之一，请求你采取操作，以便我们迁移组。 你可能还收到过一则消息中心通知，通知你由于我方的 bug，迁移将花费更长时间。 我们正在继续努力工作，以迁移任何受影响的客户。

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>对适用于 iOS 的公司门户应用中应用磁贴的改进
我们更新了主页上的应用磁贴设计，以反映你为公司门户设置的品牌颜色。 有关详细信息，请参阅[应用 UI 中的新增功能](whats-new-app-ui.md)。

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>适用于 iOS 的公司门户应用现在可使用帐户选取器
当 iOS 设备用户登录公司门户时，如果他们使用其工作或学校帐户登录其他 Microsoft 应用，则会看到新的帐户选取器。 有关详细信息，请参阅[应用 UI 中的新增功能](whats-new-app-ui.md)。

## <a name="week-of-may-29-2017"></a>2017 年 5 月 29 日的这一周

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>更改 MDM 颁发机构，而无需取消注册托管设备 <!--1103950-->

你现在可以更改 MDM 颁发机构，而无需联系 Microsoft 支持部门，并且无需取消注册并重新注册现有的受管理设备。 在 Configuration Manager 控制台中，可以通过“设置”将 [MDM 颁发机构](/sccm/mdm/deploy-use/change-mdm-authority)从“Configuration Manager (混合)”更改为“Microsoft Intune (独立)”，反之亦然。 


### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Samsung KNOX 启动 PIN 改进通知 <!--1087143-->
最终用户需要在 Samsung KNOX 设备上设置启动 PIN 以符合加密规定时，最终用户单击向他们显示的通知后，会将其转到“设置”应用中的确切位置。  以前，该通知会将最终用户转到密码更改屏幕。


### <a name="device-enrollment"></a>设备注册

#### <a name="apple-school-manager-asm-support-with-shared-ipad----748864-770395--"></a>共享 iPad 的 Apple School Manager (ASM) 支持<!-- 748864, 770395-->

Intune 现在支持使用 Apple School Manager (ASM) 来替换 Apple 设备注册计划，从而提供 iOS 设备开箱注册体验。 需要执行 ASM 载入才能将 Classroom 应用用于共享 iPad，并且需要执行此操作才会允许通过 Microsoft 学校数据同步 (SDS) 将数据从 ASM 同步到 Azure Active Directory。 有关详细信息，请参阅[通过 Apple School Manager 进行 iOS 设备注册](apple-school-manager-set-up-ios.md)。

> [!NOTE]
> 配置与课堂应用配合使用的共享 iPad 将需要在 Azure 中进行 iOS 教育版配置，这一功能尚未提供。  此功能将很快添加。

### <a name="device-management"></a>设备管理

#### <a name="provide-remote-assistance-to-android-devices-using-teamviewer----675418---"></a>使用 TeamViewer 为 Android 设备提供远程协助 <!-- 675418 -->

Intune 现在可使用 [TeamViewer](https://www.teamviewer.com) 软件（另行购买）为运行 Android 设备的用户提供远程协助。 有关详细信息，请参阅[向 Intune 托管的 Android 设备提供远程协助](device-profile-android-teamviewer.md)。

### <a name="app-management"></a>应用管理

#### <a name="new-app-protection-policies-conditions-for-mam----679864---"></a>MAM 的新应用保护策略条件 <!-- 679864 -->

你现在可以为没有注册用户的 MAM 设置强制执行以下策略的要求：

- 最低应用程序版本
- 最低操作系统版本
- 目标应用程序的最低 Intune APP SDK 版本（仅 iOS）

Android 和 iOS 上均提供此功能。 Intune 支持对 OS 平台版本、应用程序版本和 Intune APP SDK 的最低版本强制要求。 在 iOS 上，已集成 SDK 的应用程序还可在 SDK 级别设置最低版本强制要求。 如果上述三种不同级别中均未满足应用保护策略中的最低要求，用户将无法访问目标应用程序。 此时，用户可以删除其帐户（对于多重身份标识的应用程序）、关闭应用程序，或更新其 OS 或应用程序版本。

你还可以通过配置其他设置来提供建议进行 OS 或应用程序升级的非阻止型通知。 可以关闭此通知，并且应用程序可供正常使用。

有关详细信息，请参阅 [iOS 应用保护策略设置](app-protection-policy-settings-ios.md)和 [Android 应用保护策略设置](app-protection-policy-settings-android.md)。

#### <a name="configure-app-configurations-for-android-for-work----621621---"></a>配置适用于 Android for Work 的应用配置 <!-- 621621 -->
应用商店中的部分 Android 应用支持托管的配置选项，可让 IT 管理员控制应用在工作配置文件中的运行方式。 使用 Intune，你现在可以查看应用支持的 配置，并在 Intune 门户中使用配置设计器或 JSON 编辑器对其进行配置。 有关详细信息，请参阅[使用针对 Android for Work 的应用配置](app-configuration-policies-use-android.md)。

#### <a name="new-app-configuration-capability-for-mam-without-enrollment----677969---"></a>针对没有注册的 MAM 的新应用注册功能 <!-- 677969 -->

你现在可以通过没有注册通道的 MAM 创建应用配置策略。 此功能相当于移动设备管理 (MDM) 应用配置中提供的应用配置策略。 有关使用没有注册的 MAM 的应用配置示例，请参阅[使用 Microsoft Intune 的 Managed Browser 策略管理 Internet 访问](app-configuration-managed-browser.md)。

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser----682960---"></a>为 Managed Browser 配置允许和阻止的 URL 列表 <!-- 682960 -->

你现在可以使用 Azure 门户中的应用配置设置为 Intune Managed Browser 配置允许和阻止的域和 URL 列表。 无论是在受管还是不受管的设备上使用它，都可以配置这些设置。 有关详细信息，请参阅[使用 Microsoft Intune 的 Managed Browser 策略管理 Internet 访问](app-configuration-managed-browser.md)。

#### <a name="app-protection-policy-helpdesk-view----1069473---"></a>应用保护策略支持人员视图 <!-- 1069473 -->

IT 支持人员用户现在可以在“疑难解答”边栏选项卡中查看用户许可证状态和已分配给用户的应用保护策略应用的状态。 有关详细信息，请参阅[疑难解答](./help-desk-operators.md)。

### <a name="device-configuration"></a>设备配置

#### <a name="control-website-visits-on-ios-devices----723832---"></a>控制 iOS 设备上的网站访问 <!-- 723832 -->

你现在可以使用以下两种方法之一控制 iOS 设备的用户可以访问的网站：

- 使用 Apple 内置的 Web 内容筛选器添加允许和阻止的 URL。

- 只允许 Safari 浏览器访问指定的网站。 将在 Safari 中为你指定的每个站点创建书签。

有关详细信息，请参阅[适用于 iOS 设备的 Web 内容筛选器设置](web-content-filter-settings-ios.md)。

#### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>预配置 Android for Work 应用的设备权限 <!-- 621614 -->

对于已部署到 Android for Work 设备工作配置文件的应用，你现在可以针对各个应用配置权限状态。  默认情况下，要求位置或设备摄像头访问权限等设备权限的 Android 应用将提示用户接受或拒绝权限。  例如，如果应用要使用设备的麦克风，则将提示最终用户授予该应用使用麦克风的权限。 通过此功能，可让你代表最终用户定义权限。  你可以将权限配置为 a) 无需通知用户即自动拒绝；b) 无需通知用户即自动批准，或 c) 提示用户接受或拒绝。 有关详细信息，请参阅 [Microsoft Intune 中的 Android for Work 设备限制设置](device-restrictions-android-for-work.md)。

#### <a name="define-app-specific-pin-for-android-for-work-devices----728976-1102534---"></a>为 Android for Work 设备定义特定于应用的 PIN <!-- 728976, 1102534 -->

具有作为 Android for Work 设备管理的工作配置文件的 Android 7.0 及更高版本的设备，可让管理员定义仅适用于工作配置文件中应用于各应用的密码策略。  选项包括：

- 定义仅设备范围的密码策略 - 这是用户解锁整个设备时必须使用的密码。
 仅定义工作配置文件密码策略 - 只要打开工作配置文件中的任何应用，系统均会提示用户输入密码。
- 同时定义设备和工作配置文件策略 - IT 管理员可以选择同时以不同的长度定义设备密码策略和工作配置文件密码策略（例如，使用四位数的 PIN 来解锁设备，使用六位数的 PIN 来打开任意工作应用）。

有关详细信息，请参阅 [Microsoft Intune 中的 Android for Work 设备限制设置](device-restrictions-android-for-work.md)。

> [!NOTE]
> 此选项仅适用于 Android 7.0 及更高版本。  默认情况下，最终用户可以使用两个单独定义的 PIN，或者他们可以选择将两个已定义的 PIN 合并为二者中较强大的一个 PIN。

#### <a name="new-settings-for-windows-10-devices----978585---"></a>适用于 Windows 10 设备的新设置 <!-- 978585 -->

我们已添加新的 [Windows 设备限制设置](device-restrictions-windows-10.md)，可控制无线显示、设备发现、任务切换和 SIM 卡错误消息等功能。

#### <a name="updates-to-certificate-configuration----918991-and-823198---"></a>证书配置更新 <!-- 918991 and 823198 -->

创建 SCEP 证书配置文件时，对于“使用者名称格式”，可以使用适用于 iOS、 Android 和 Windows 设备的“自定义”选项。 在本次更新之前，“自定义”字段仅适用于 iOS 设备。 有关详细信息，请参阅[如何创建 SCEP 证书配置文件] (certificates-scep-configure.md#how-to-create-a-scep-certificate-profile)。

创建 PKCS 证书配置文件时，对于“使用者可选名称”，可以选择“自定义 Azure AD 属性”。 当选择“自定义 Azure AD 属性”时，将出现“部门”选项。 有关详细信息，请参阅[如何创建 PKCS 证书配置文件] (certficates-pfx-configure.md#how-to-create-a-pkcs-certificate-profile)。

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode----662059---"></a>配置多个当 Android 设备处于展台模式时可以运行的应用 <!-- 662059 -->

当 Android 设备处于展台模式时，你之前仅能配置一个允许运行的应用。 现在，你可以使用应用 ID、应用商店 URL，或通过选择一个已经管理的 Android 应用配置多个应用。 有关详细信息，请参阅[展台模式设置](device-restrictions-android.md#kiosk)。


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

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>改进了所有平台上跨公司门户应用的登录体验<!--User Story 1132123-->

我们宣布将在接下来的几个月内推出一项更新，用以提升适用于 Android、iOS 和 Windows 的 Intune 公司门户应用的登录体验。 当 Azure AD 进行此更改时，新的用户体验将自动在公司门户应用的所有平台上显现。 此外，用户可以使用生成的一次性验证码从其他设备立即登录到公司门户。 当用户需要在没有凭据的情况下登录时，这尤为有用。

若要查看使用凭据进行登录的以前的登录体验和新登录体验，以及从其他设备进行登录的新登录体验的屏幕快照，请参阅[应用 UI 中的新增功能](/intune/whats-new-app-ui)。

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>做好应对更改的计划：Intune 将更改 Intune 合作伙伴门户体验<!-- 1050016 -->

自 2017 年 5 月中旬起，我们将从 manage.microsoft.com 中删除 Intune 合作伙伴页面（从服务更新入手）。  

如果你是合作伙伴管理员，将无法再代表客户在 Intune 合作伙伴页面中查看内容和执行操作，而是需要在 Microsoft 的其他两个合作伙伴门户之一进行登录。

使用 [Microsoft 合作伙伴中心](https://partnercenter.microsoft.com/)和 [Microsoft Office 365 合作伙伴管理中心](https://portal.office.com/)，可以登录所管理的客户帐户。 作为合作伙伴，未来请使用其中一个网站管理客户。


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 将要求更新应用传输安全<!--748318-->

Apple 宣布他们将强制对应用程序传输安全 (ATS) 实施特定要求。 使用 ATS 对所有通过 HTTPS 的应用通信实施更严格的安全措施。 此更改会影响使用 iOS 公司门户应用的 Intune 客户。

我们通过强制实施新的 ATS 要求的 Apple TestFlight 计划提供了适用于 iOS 的公司门户应用的可用版本。 如果你想要试用以测试你的 ATS 符合性，请发送电子邮件至 <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a>，并提供你的名字、姓氏、电子邮件地址和公司名称。 请查看 [Intune 支持博客](https://aka.ms/compportalats)，了解更多详细信息。

### <a name="see-also"></a>另请参阅
* [Microsoft Intune 博客](http://go.microsoft.com/fwlink/?LinkID=273882)
* [云平台路线图](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [What's new in the Company Portal UI](whats-new-app-ui.md)（公司门户 UI 新增功能）
* [前几个月的新增功能](whats-new-archive.md)

