---
title: 早期版本
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2f21df636ab429969429c6dbdf540daaa67a8f88
ms.sourcegitcommit: d8edd1c3d24123762dd6d14776836df4ff2a31dd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2018
ms.locfileid: "51576760"
---
# <a name="the-early-edition-for-microsoft-intune---november-2018"></a>Microsoft Intune 的早期版本 - 2018 年 11 月

> [!Note]
> NDA 通知：下面的 Intune 更改仍处于开发阶段。 此信息在 NDA 下共享，但具有严格限制。 请勿在 Twitter、UserVoice、Reddit 等社交媒体或公共网站上发布此信息。 

早期版本提供了一份即将发布的 Microsoft Intune 版本中将出现的功能列表（在 NDA 下共享）。 此信息的提供具有条件限制，并且会不断变化。 请勿发布推文、在 UserVoice 上发帖，或者以其他方式在公司外部共享此信息。 此处列出的某些功能有无法按期发布的风险并可能推迟到以后的版本。 正在以试验模式（外部测试）测试其他功能，以确保它们可立即供客户使用。 如果有任何问题或顾虑，请与 Microsoft 产品组联系人联系。

本页将定期更新。 返回查看其他更新。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure 门户中的 Intune

<!-- 1811 start -->

### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>卸载公司拥有的受监督 iOS 设备上的应用 <!-- 1281677 -->
你将能够删除公司拥有的受监督 iOS 设备上的应用。 可以通过以“卸载”分配类型的用户或设备组为目标来删除任何应用。 对于个人或无监督的 iOS 设备，你将继续只能删除使用 Intune 安装的应用。

### <a name="track-installation-of-office-proplus---2620217--"></a>跟踪 Office 专业增强版的安装过程<!--2620217-->
你将能够使用[注册状态页面](windows-enrollment-status.md)来跟踪 [Office 专业增强版](apps-add-office365.md)的安装进度。

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133--"></a>macOS 设备注册计划支持 Apple School Manager 帐户 <!--3006133-->
Intune 将支持对 Apple School Manager 帐户使用 macOS 设备上的设备注册计划。

### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>暂时暂停 Android 设备上的展台模式以进行更改 <!-- 3041935 -->
在多应用展台模式下使用 Android 设备时，IT 管理员可能需要对设备进行更改。 新的多应用展台设置将允许 IT 管理员使用 PIN 临时暂停展台模式，并有权访问整个设备。
要查看当前展台设置，请参阅 [Android 展台设置](android-kiosk-settings.md)。

### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>在托管的主屏幕应用中设置自定义背景 <!-- 3041945 -->
我们将添加一种设置，使你可自定义 Android Enterprise、多应用和展台模式设备上托管的主屏幕应用的背景外观。  要配置“自定义 URL 背景”，请转到的 Azure 门户中的 Intune >“设备配置”。 选择当前设备配置文件或创建新配置文件以编辑其展台设置。

### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>启用 Android Enterprise 展台设备上的虚拟主页按钮 <!-- 3042021 -->
新的设置将允许用户点击其设备上的软键按钮，以在其多应用展台设备上托管的主屏幕应用和其他已分配的应用之间进行切换。 此设置在用户的展台应用未对“后退”按钮及时做出响应的情况下特别有用。 可为公司拥有的一次性 Android 设备配置此设置。 要启用或禁用“虚拟主页”按钮，请转至 Azure 门户中的 Intune >“设备配置”。 选择当前设备配置文件或创建新配置文件以编辑其展台设置。

### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>应用保护策略分配将保存并应用 <!-- 3104570 -->
可以更好地控制应用保护政策分配。 通过保存并应用应用保护策略分配，仅目标用户会受到应用保护分配策略的直接影响。

### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>适用于 Windows 10 及更高版本的新 Microsoft Edge 浏览器设置 <!-- 3174639 -->
将添加新的设置，以帮助控制和管理设备上的 Microsoft Edge 浏览器。 有关当前设置的列表，请参阅[适用于 Windows 10（及更高版本）的设备限制](device-restrictions-windows-10.md#microsoft-edge-browser)。

### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>选择注册状态页上跟踪的应用<!-- 2531007 -->
可以选择在“注册状态”页面上跟踪的应用。

### <a name="intune-app-protection-policies-ui-update----3251427---"></a>Intune 应用保护策略用户界面更新 <!-- 3251427 -->

Intune 应用保护策略可以为 Intune 受保护的应用（如 Microsoft Outlook 和 Word）配置各种数据保护设置。 我们正在更改设置和按钮标签，以使用户更容易理解每个选项。 这些控件将从“是”/“否”控件改为主要的“阻止”/“允许”和“禁用”/“启用”控件，同时还将更新标签以提高清晰度。 将对设置重新设置格式，以在控件中并排显示设置及其标签，从而提供更好的浏览。 默认设置和设置数目将保持不变，但此更改可使用户更轻松地了解、浏览以及利用设置，以应用所选的应用保护策略。



<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>将 Microsoft 推荐的设置与安全基线结合使用 <!-- 2055484 -->
Intune 可与其他专注于安全性的服务集成，包括 Windows Defender ATP 和 Office 365 ATP。 客户要求能在各项 Microsoft 365 服务中采用通用策略和一组统一的端到端安全工作流。 我们的目标是实现策略一致，构建连接安全操作和常见管理员任务的解决方案。 在 Intune 中，我们旨在通过发布一组 Microsoft 推荐的“安全基线”（“Intune” > “安全基线”）来实现这一目标。  管理员将能够直接通过这些基线创建安全策略，然后将其部署到用户。 他们还可以自定义最佳做法建议，满足组织需求。 Intune 可确保设备始终符合这些基线，并通知不符合的用户管理员或设备。

### <a name="scope-tags-for-apps---1081941---"></a>应用的作用域标记 <!--1081941 -->
可创建作用域标记来限制对 Intune 资源的访问。 将作用域标记添加到某个角色分配，然后将作用域标记添加到某个配置文件。 角色将仅有权访问符合后列条件的资源：其资源配置文件的作用域标记与角色标记匹配或无作用域标记。
若要创建作用域标记，选择“Intune 角色” > “作用域(标记)” > “创建”。
要向角色分配添加作用域标记，选择“Intune 角色” > “所有角色” > “策略和配置文件管理器” > “分配” > “作用域(标记)”。
要向配置文件添加作用域标记，选择“设备配置” > “配置文件”>“选择配置文件”>“属性” > “作用域(标记)”。

### <a name="tenant-health-dashboard----1124854---"></a>租户运行状况仪表板 <!-- 1124854 -->
Intune 中的“租户状态”页面将在一个位置提供租户状态信息。 该页面分为 4 个部分：  
- **租户详细信息**：包含 MDM 机构、租户中的注册设备总数以及许可证计数等信息。 此部分还为租户提供当前服务版本。
- **连接器状态**：包含 Apple VPP、适用于企业的 Windows 应用商店和证书连接器等已配置连接器的信息。 根据连接器的当前状态，将其标记为“正常”、“警告”或“不正常”。
- **Intune 服务运行状况**：包含租户的活动事件或服务中断情况。 该部分信息直接检索自 Office 消息中心 ([https://portal.office.com](https://portal.office.com))。
- **Intune 新闻**：包含租户的活动消息，其中包括租户已收到最新 Intune 功能的通知等内容。 该部分信息直接检索自 Office 消息中心 ([https://portal.office.com](https://portal.office.com))。


### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>无需用户注册，即可部署 WIP 政策 <!-- 1434452 -->
无需要求 MDM 用户注册其 Windows 10 设备，即可部署Windows 信息保护 (WIP) 策略。 此配置允许公司基于 WIP 配置保护其企业文档，同时允许用户管理自己的 Windows 设备。 使用 WIP 策略保护文档后，Intune 管理员可以选择性擦除受保护的数据。 通过选择用户和设备，并发送擦除请求，所有通过 WIP 策略保护的数据都将不可用。 从 Azure 门户中的 Intune，选择“移动应用” > “应用选择性擦除”。


<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>适用于 Web 数据的应用保护策略 (APP) 设置 <!-- 2662995 -->
将更新 Android 和 iOS 设备上适用于 Web 内容的应用策略设置，以更好地处理 http 和 https Web 链接，以及通过 iOS 通用链接和 Android 应用链接进行的数据传输。  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>另一个 MDM 使用的 Apple VPP 令牌 <!-- 1488946 -->
Intune 会检测是否 Intune 和另一个 MDM 同时在使用同一个 Apple 批量采购计划 (VPP) 令牌，并显示相关详细信息。

### <a name="ios-and-macos-version-numbers-and-build-numbers-are-available-in-compliance-policies----1892471---"></a>符合性策略中提供了 iOS 和 macOS 的版本号和生成号 <!-- 1892471 -->
在“设备符合性” > “设备符合性”中，iOS 和 macOS 操作系统版本都会显示，并且可在符合性策略中使用。 在未来的更新中，还可以为这两个平台配置生成号。

Apple 每次发布安全更新时，会保留版本号，更新生成号。 通过在符合性策略中使用生成号，可轻松地检查是否已安装漏洞更新。

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>“设备符合性仪表板”中的停用设备 <!-- 1981119 -->
未来的某个更新将从设备符合性仪表板中删除已停用的设备。 这会改变符合性数字。


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>本地连接器更新过程的更改 <!-- 2277554 -->
将根据客户反馈更改本地连接器的更新方式。 初次安装本地连接器之后，会自动对其进行更新。 此更改首先应用于适用于 Microsoft Intune 的全新 PFX 证书连接器，随后会推广至其他类型的本地连接器。 

<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>检查 Configuration Manager 符合性<!-- 2192052 -->
未来的更新将包括新的 System Center Configuration Manager 符合性设置（“设备符合性”“策略” >  > “创建策略” > “Windows 10”）。 Configuration Manager 向 Intune 符合性发送信号。 使用 Intune 设置，可以要求所有 Configuration Manager 信号都返回“符合”。

例如，要求所有软件更新都安装在设备上。 在 Configuration Manager 中，此要求具有“已安装”状态。 如果设备上的任何计划都处于未知状态，则此设备在 Intune 中不兼容。

适用于 Windows 10 及更高版本

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>针对即将过期的 VPP 令牌或公司门户许可证不足的警报 <!-- 2237572 -->
如果在 DEP 注册期间使用批量采购计划 (VPP) 预先设置公司门户，则在 VPP 令牌即将过期以及公司门户的许可证不足的情况下，Intune 将发出警报。



<!-- the following are present prior to 1711 -->

## <a name="notices"></a>通知

此时没有任何活动通知。

### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。



