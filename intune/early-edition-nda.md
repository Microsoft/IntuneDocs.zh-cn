---
title: 早期版本 - Microsoft Intune
titlesuffix: ''
description: Microsoft Intune 的早期版本
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/09/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 0efc84da6a9efb594600b9ca33aa5eb7622c8101
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203427"
---
# <a name="the-early-edition-for-microsoft-intune---january-2019"></a>Microsoft Intune 的早期版本 - 2019 年 1 月

> [!Note]
> NDA 通知：下面的更改依据 Intune 开发。 此信息在 NDA 下共享，但具有严格限制。 请勿在 Twitter、UserVoice、Reddit 等社交媒体或公共网站上发布此信息。 

早期版本提供了一份即将发布的 Microsoft Intune 版本中将出现的功能列表（在 NDA 下共享）。 此信息的提供具有条件限制，并且会不断变化。 请勿发布推文、在 UserVoice 上发帖，或者以其他方式在公司外部共享此信息。 此处列出的某些功能有无法按期发布的风险并可能推迟到以后的版本。 正在以试验模式（外部测试）测试其他功能，以确保它们可立即供客户使用。 如果有任何问题或顾虑，请与 Microsoft 产品组联系人联系。

本页将定期更新。 返回查看其他更新。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure 门户中的 Intune

<!-- 1901 start -->

### <a name="android-enterprise-apps----1352553----"></a>Android Enterprise 应用 <!-- 1352553  -->
将能从 Microsoft Intune 中删除托管的 Google Play 应用。 要删除托管的 Google Play 应用，请在 Azure 门户中打开 Microsoft Intune 并选择“客户端应用” > “应用”。 在应用列表中，选择托管的 Google Play 应用右侧的省略号 (...)，并在显示的列表中选择“删除”。 从应用列表删除托管的 Google Play 应用时，托管的 Google Play 应用会自动变为未批准状态。

### <a name="managed-google-play-app-type----1352580---"></a>托管的 Google Play 应用类型 <!-- 1352580 -->
“托管的 Google Play”应用类型让你可以专门将[托管的 Google Play 应用](https://play.google.com/work/search?q=microsoft&c=apps)添加到 Intune。 Intune 管理员现在可以在 Intune 中浏览、搜索、批准、同步和分配已批准的托管的 Google Play 应用。 无需单独浏览到托管的 Google Play 控制台，也无需重新进行身份验证。 在 Intune 中，选择“客户端应用” > “应用” > “添加”。 在“应用类型”列表中，将应用类型选择为“托管的 Google Play”。

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>对 Android 公司拥有的完全托管设备的支持（预览版）<!-- 1574342  -->
Intune 将支持完全托管的 Android 设备，这是公司拥有的“设备所有者”方案，其中设备由 IT 管理员紧密管理并与各个用户关联。 这样，管理员便可以管理整个设备、强制扩展不可用于工作配置文件的策略控制的范围并限制用户仅从托管的 Google Play 安装应用。 要设置完全托管的 Android 设备，请转到“设备注册” > “Android 注册” > “公司拥有的完全托管的用户设备”。 请注意，此功能处于预览状态。 Android 完全托管的用户设备目前无法使用部分 Intune 功能，例如证书、符合性以及条件访问。

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>部署获得许可的适用于企业的 Microsoft Store 联机应用 <!-- 1672660  -->
你将能够在设备上下文中分配所需的适用于企业的 Microsoft Store 联机应用，这些应用已获得许可。 如果以这种方式部署适用于企业的 Microsoft Store 应用，则可在设备上为所有用户安装该应用。 这仅适用于 Windows 10 RS4+ 桌面版设备。 对于获得许可的适用于企业的 Microsoft Store 联机应用，可在客户端应用分配页面中选择安装在设备上下文中。

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470----"></a>将配置文件配置为在“设置助手”期间跳过某些屏幕 <!-- 2276470  -->
创建 macOS 注册配置文件时，可将其配置为在用户使用设置助手期间跳过以下任一屏幕：
- Android 迁移
- 显示基调
- 隐私
- iCloudStorage

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522----"></a>将 Autopilot 配置文件分配给所有设备虚拟组 <!--2715522  -->
可将 Autopilot 配置文件分配给所有设备虚拟组。 要执行此操作，请选择“设备注册” > “Windows 注册” > “部署配置文件”，然后选择一个配置文件，选择“分配”，接着在“分配给”下选择“所有设备”。 有关 Autopilot 配置文件的详细信息，请参阅[使用 Windows Autopilot 注册 Windows 设备](enrollment-autopilot.md)。

### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324----"></a>使用设备配置配置文件在受监管的 iOS 设备上自定义壁纸 <!-- 2809324  -->
在为 iOS 设备创建设备配置配置文件时，可以允许或限制“设备配置” > “配置文件” > “创建配置文件” > “iOS”（作为平台）>“设备限制”（作为配置文件类型）中的一些设置。 此更新包括新的“壁纸”设置，管理员可以通过此设置将 .png、.jpg 或 .jpeg 图像用作壁纸、预览图像以及阻止用户更改壁纸。 壁纸设置仅应用于受监管的设备。 要获取当前设置的列表，请参阅 [iOS 设备限制设置](device-restrictions-ios.md)。

### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Win 32 应用的 Toast 通知 <!-- 3136566   -->
你将能够隐藏每个应用分配的最终用户 Toast 通知。 在 Intune 中，选择“客户端应用” > “应用”> 选择该应用 >“分配” > “包括组”。 

### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396---"></a>在“设备限制”>“Android Enterprise 的设备所有者”中删除“通过蓝牙共享联系人”<!-- 3598396 -->
在创建 Android Enterprise 设备的设备限制配置文件时，会有一个“通过蓝牙共享联系人”设置。 在此更新中，“通过蓝牙共享联系人”设置将被删除（“设备配置” > “配置文件” > “创建配置文件” > “Android Enterprise”（作为平台）>“设备限制”>“设备所有者”（作为配置文件类型）>“常规”）。 

Android Enterprise 设备所有者管理不支持“通过蓝牙共享联系人”设置。 因此，在删除此设置时，即使在环境中启用并配置了此设置，此更改也不会影响任何设备或租户。

要查看设置的当前列表，请转到[用于允许或限制功能的 Android Enterprise 设备设置](device-restrictions-android-for-work.md)。

适用于：Android Enterprise 设备所有者

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android Enterprise APP-WE 应用部署 <!-- 1171203 -->
对于没有注册 (APP-WE) 部署方案的未注册应用保护策略中的 Android 设备，能够使用托管的 Google Play 将应用商店应用和 LOB 应用部署到用户。 具体而言，IT 管理员可以向最终用户提供应用目录以及不再需要最终用户通过允许从未知源进行安装来放宽其设备的安全状况的安装体验。 此外，此部署方案将改进最终用户体验。

### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Intune App SDK 将支持 256 位加密密钥 <!-- 1832174 -->
应用保护策略启用加密时，适用于 Android 的 Intune App SDK 将使用 256 位加密密钥。 SDK 将继续提供 128 位密钥支持以与使用旧版 SDK 的内容和应用兼容。


### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Intune 策略更新身份验证方法和公司门户应用安装  <!-- 1927359 -->
在已通过 Apple 公司设备注册方法之一经由“设置助理”注册的设备上，Intune 将不再支持由最终用户从应用商店手动安装的公司门户。 仅当在注册过程中使用 Apple 设置助理进行身份验证时，此更改才适用。 此更改也只会影响通过以下方式注册的 iOS 设备：  
* Apple 配置器
* Apple Business Manager
* Apple School Manager
* Apple 设备注册计划 (DEP)

如果用户从应用商店安装公司门户应用，然后尝试通过该应用注册这些设备，则他们将收到错误。 在注册过程中由 Intune 自动推送公司门户时，这些设备应仅使用公司门户。 将更新 Azure 门户中的 Intune 注册配置文件，以便你可以指定设备的身份验证方式以及是否收到公司门户应用。 如果希望 DEP 设备用户具有公司门户，则需要在注册配置文件中指定你的首选项。 此外，公司门户应用中的“标识设备”屏幕很快就会过时。  
若要在已注册的 DEP 设备上安装公司门户，需要转到“Intune”>“客户端应用”，并将其作为具有应用配置策略的托管应用进行推送。 未来的文档中将详细概述执行这些步骤的方式。

### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379---"></a>非管理员可以在已加入 Azure AD 的 Windows 10 设备上启用 BitLocker<!-- 2147379 -->
在 Windows 10 设备上启用 BitLocker 设置时（“设备配置” > “配置文件” > “创建配置文件” > “Windows 10 及更高版本”作为平台 >“Endpoint protection”作为配置文件类型 >“Windows 加密”），将添加 BitLocker 设置。 此更新包括新的 BitLocker 设置，以允许标准用户（非管理员）启用加密。 若要查看当前设置，请参阅[适用于 Windows 10 的 Endpoint protection 设置](endpoint-protection-windows-10.md#windows-encryption)。


### <a name="additional-settings-for-outlook----3301182---"></a>Outlook 的其他设置 <!-- 3301182 -->
现在可以使用 Intune 为 iOS 和 Android 配置 Outlook 其他设置。  设置包括以下内容：
- 仅允许在 iOS 和 Android 的 Outlook 中使用工作或学校帐户
- 部署适用于 Office 365 和混合新式身份验证本地帐户的新式身份验证
- 选择基本身份验证时，请使用 `SAMAccountName` 作为电子邮件配置文件中的用户名字段
- 允许保存联系人
- 配置外部收件人邮件提示
- 配置“重点收件箱”
- 需要进行生物识别来访问适用于 iOS 的 Outlook 
- 阻止外部图像

> [!NOTE]
> 如果使用 Intune 应用保护策略来管理公司标识的访问权限，则应考虑不启用“需要生物识别”。 有关详细信息，请参阅 [iOS 访问要求](app-protection-policy-settings-ios.md#access-settings)和 [Android 访问要求](app-protection-policy-settings-android.md#access-settings)的“访问需要的公司凭据”。

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>管理模板为公共预览版，并移动到其自己的配置文件 <!-- 3322847 -->
Intune 中的管理模板（“设备配置” > “管理模板”）目前为个人预览版。 借助此更新：管理模板包括可在 Intune 中管理的大约 300 个设置。 以前，这些设置仅存在于组策略编辑器中。
管理模板现已推出公共预览版，管理模板从“设备配置” > “管理模板”移动到“设备配置” > “配置文件” >“创建配置文件”> 在“平台”中，选择“Windows 10 及更高版本”，在“配置文件类型”中，选择“管理模板”。
“已启用报告”适用于：Windows 10 及更高版本

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>Intune macOS 公司门户深色模式 <!-- 3300524 -->
Intune macOS 公司门户现在支持 macOS 的深色模式。 如果在 macOS 10.14+ 设备上启用了深色模式，公司门户会将其外观调整为能反映该模式的颜色。

<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>将 Microsoft 推荐的设置与安全基线结合使用 <!-- 2055484 -->
Intune 可与其他专注于安全性的服务集成，包括 Windows Defender ATP 和 Office 365 ATP。 客户要求能在各项 Microsoft 365 服务中采用通用策略和一组统一的端到端安全工作流。 我们的目标是实现策略一致，构建连接安全操作和常见管理员任务的解决方案。 在 Intune 中，我们旨在通过发布一组 Microsoft 推荐的“安全基线”（“Intune” > “安全基线”）来实现这一目标。  管理员将能够直接通过这些基线创建安全策略，然后将其部署到用户。 他们还可以自定义最佳做法建议，满足组织需求。 Intune 可确保设备始终符合这些基线，并通知不符合的用户管理员或设备。

### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>无需用户注册，即可部署 WIP 政策 <!-- 1434452 -->
无需要求 MDM 用户注册其 Windows 10 设备，即可部署Windows 信息保护 (WIP) 策略。 此配置允许公司基于 WIP 配置保护其企业文档，同时允许用户管理自己的 Windows 设备。 使用 WIP 策略保护文档后，Intune 管理员可以选择性擦除受保护的数据。 通过选择用户和设备，并发送擦除请求，所有通过 WIP 策略保护的数据都将不可用。 从 Azure 门户中的 Intune，选择“移动应用” > “应用选择性擦除”。


<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>适用于 Web 数据的应用保护策略 (APP) 设置 <!-- 2662995 -->
将更新 Android 和 iOS 设备上适用于 Web 内容的应用策略设置，以更好地处理 http 和 https Web 链接，以及通过 iOS 通用链接和 Android 应用链接进行的数据传输。  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>另一个 MDM 使用的 Apple VPP 令牌 <!-- 1488946 -->
Intune 会检测是否 Intune 和另一个 MDM 同时在使用同一个 Apple 批量采购计划 (VPP) 令牌，并显示相关详细信息。

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>“设备符合性仪表板”中的停用设备 <!-- 1981119 -->
未来的某个更新将从设备符合性仪表板中删除已停用的设备。 这会改变符合性数字。



<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>检查 Configuration Manager 符合性<!-- 2192052 -->
未来的更新将包括新的 System Center Configuration Manager 符合性设置（“设备符合性”“策略” >  > “创建策略” > “Windows 10”）。 Configuration Manager 向 Intune 符合性发送信号。 使用 Intune 设置，可以要求所有 Configuration Manager 信号都返回“符合”。

例如，要求所有软件更新都安装在设备上。 在 Configuration Manager 中，此要求具有“已安装”状态。 如果设备上的任何计划都处于未知状态，则此设备在 Intune 中不兼容。

适用于 Windows 10 及更高版本



## <a name="notices"></a>通知

此时没有任何活动通知。

### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。



