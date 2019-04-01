---
title: 在开发的 Microsoft Intune
titlesuffix: ''
description: 中开发的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/04/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c377a8558b1f318b4ddad735b6368a291e34516
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57756813"
---
# <a name="in-development-for-microsoft-intune---march-2019"></a>在开发中 Microsoft Intune-2019 年 3 月

以帮助你准备和规划，此页列出了 Intune UI 更新和功能正在开发中，但尚未释放。 此外：

- 如果我们希望，您将需要采取措施在更改前的，我们将发布免费的 Office 消息中心文章。
- 当作为预览功能启动在生产中，或已公开发布，功能说明将移动关闭此页和到上[新增功能页](whats-new.md)。
- 此页并[新增功能页](whats-new.md)会定期更新。 返回查看其他更新。
- 请参阅[M365 路线图](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)战略可交付结果和时间线。

> [!Note]
> 这些项反映 Microsoft 的有关 Intune 功能在将来版本中的当前预期。 日期和各项功能可能会更改。 在开发过程中的不是所有项都具有此页上的功能说明。

**RSS 源**：通过将以下 URL 复制并粘贴到源阅读器中，可以在页面更新时收到通知：`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`


<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure 门户中的 Intune


<!-- 1903 start-->

### <a name="encryption-report-----2351538---"></a>加密报表  <!-- 2351538 -->
您可以使用新的加密报表来查看有关你的设备的加密状态的详细信息。 可用的详细信息将包括设备 TPM 版本、 加密就绪状态和状态、 错误报告，和的详细信息。  

### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-----2351547----"></a>从 Intune 门户中访问 BitLocker 恢复密钥  <!-- 2351547  -->
我们添加了新的入口点中的设备，你可以在其中查看从 Azure Active Directory (AAD) 有关 BitLocker 密钥 ID 和 BitLocker 恢复密钥的详细信息。

### <a name="scope-tags-for-app-configuration-policies---2371891---"></a>应用配置策略的作用域标记 <!--2371891 -->
您可以将作用域标记添加到应用配置策略，以便只有具有角色还分配该作用域标记的人员有权访问应用配置策略。 应用配置策略可以仅针对或与应用分配相同的作用域标记相关联。

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522---"></a>将 Autopilot 配置文件分配给所有设备虚拟组 <!--2715522 -->
可将 Autopilot 配置文件分配给所有设备虚拟组。 要执行此操作，请选择“设备注册” > “Windows 注册” > “部署配置文件”，然后选择一个配置文件，选择“分配”，接着在“分配给”下选择“所有设备”。 有关 Autopilot 配置文件的详细信息，请参阅[使用 Windows Autopilot 注册 Windows 设备](enrollment-autopilot.md)。

### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523----"></a>安装 Windows 批量注册后，使用公司门户应用可用的应用 <!-- 2751523  -->
在使用 Intune 中注册的 Windows 设备[Windows 批量注册](windows-bulk-enroll.md)（预配包） 将能够使用公司门户应用安装可用的应用程序。 有关公司门户应用的详细信息，请参阅[手动添加 Windows 10 公司门户](store-apps-company-portal-app.md)并[如何配置 Microsoft Intune 公司门户应用](company-portal-app.md)。

### <a name="scope-tags-for-ios-app-provisioning-profiles---2934430---"></a>IOS 应用预配配置文件的作用域标记 <!--2934430 -->
您可以将作用域标记添加到 iOS 应用预配配置文件，以便只有具有角色还分配该作用域标记的人员有权访问 iOS 应用预配配置文件。 

### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477----"></a>Office 部署工具 (ODT) 的 Office 专业增强版部署 XML <!-- 3192477  -->
你将能够在 Intune 管理控制台中创建的 Office Pro Plus 实例时提供 Office 部署工具 (ODT) XML。 如果现有的 Intune 用户界面选项不能满足你的需求，这将允许更大的可自定义性。 

###  <a name="block-users-from-scanning-for-windows-updates-------3316758------"></a>阻止用户从 Windows 更新扫描    <!-- 3316758    -->
我们添加了新 Windows 更新通道设置，可以使用将阻止用户从 Windows 更新扫描。 此设置不会在门户中，从可用，但可以使用 Intune Graph API 进行配置。

### <a name="windows-update-notifications-----3316782---"></a>Windows 更新通知  <!-- 3316782 -->
我们添加了支持与 Windows 更新环配置以便你将能够配置您的用户看到的 Windows 更新通知。 此设置不会在门户中，从可用，但可以使用 Intune Graph API 进行配置。

### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>将 12 个设备用户更改为适用于 iOS 的公司门户注册 <!--3448635 -->  
将更新适用于 iOS 的公司门户，应用程序的注册屏幕和步骤与在 Apple iOS 12.2 中发布的 MDM 注册更改保持一致。 更新的工作流现在将提示用户：

- 允许使用 Safari 打开公司门户网站 （通过 Safari) 并返回到公司门户应用之前下载的管理配置文件。 
- 打开设置应用在其设备上安装管理配置文件。
- 返回到完成注册的公司门户应用。  

有关如何准备这些更改的详细信息，请参阅[Microsoft 技术社区文章](https://techcommunity.microsoft.com/)。 在此期间，若要在公司门户中支持新的 iOS 注册，我们已更新中的步骤[在 Intune 中的注册 iOS 设备](https://docs.microsoft.com/en-us/intune/ios-enroll)。 Apple 发布 iOS 版本 12.2 后，这些文档更改都将实时。 

### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202-------"></a>租户状态页上的其他连接器的支持 <!-- 3617202     -->
租户状态页将显示状态信息包括的附加连接器*Windows Defender 高级威胁防护*(ATP) 和其他移动威胁防御连接器。

### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917---"></a>授予 Intune 读取仅对某些 Azure Active Directory 角色的访问 <!-- 3637917 -->
我们将会向 Intune 只读到以下 Azure AD 角色的访问。 使用 Azure AD 角色授予的权限优先于使用 Intune 基于角色的访问控制 (RBAC) 授予的权限。

只读 Intune 审核数据的访问：

- 合规性管理员
- 符合性数据管理器

只读访问权限的所有 Intune 数据：

- 安全管理员
- 安全运算符
- 安全性读者
- 全局读取器

### <a name="easier-access-to-diagnostic-settings------3804627-----"></a>更轻松地访问诊断设置   <!-- 3804627   -->
我们将添加到一个新选项**审核日志**边栏选项卡中的每个可用于直接打开在 Intune 控制台中每个审核日志工作负荷*诊断设置*页。

### <a name="create-and-use-device-configuration-profiles-on-android-zebra-devices-in-intune----3895244----"></a>创建并在 Intune 中 Android 斑马设备上使用设备配置文件 <!-- 3895244  -->
Intune 将支持 Android 斑马设备配置。 具体而言，你将能够： 

- 创建设备配置文件，并将设置应用到 Android 斑马设备使用移动扩展 (MX) 配置文件生成的 StageNow (**设备配置** > **配置文件** > **创建配置文件** > **Android**平台)。

适用于：  
- Android

<!-- 1901 start -->

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>部署获得许可的适用于企业的 Microsoft Store 联机应用 <!-- 1672660  -->
你将能够在设备上下文中分配所需的适用于企业的 Microsoft Store 联机应用，这些应用已获得许可。 如果以这种方式部署适用于企业的 Microsoft Store 应用，则可在设备上为所有用户安装该应用。 这仅适用于 Windows 10 RS4+ 桌面版设备。 对于获得许可的适用于企业的 Microsoft Store 联机应用，可在客户端应用分配页面中选择安装在设备上下文中。

## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。
