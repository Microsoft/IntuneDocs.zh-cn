---
title: Microsoft Intune 中的新增功能 - Azure | Microsoft Docs
titleSuffix: ''
description: 了解 Intune Azure 门户新增功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/07/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7018e2ab4290219c752f44b4b391822438461e8e
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415088"
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune 新增功能

了解 Microsoft Intune 每周新增功能。 还可以找到[重要通知](#notices)、[过去版本](whats-new-archive.md)，以及有关[如何发布 Intune 服务更新](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728)的信息。 

> [!Note]
> 每个[每月更新](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728)可能需要长达三天才能推出，顺序如下：
>
> - 第 1 天：亚太地区 (APAC)
> - 第 2 天：欧洲、中东和非洲 (EMEA)
> - 第 3 天：北美
> - 第 4 天之后：Intune for Government
>
> 某些功能可能会在数周内推出，第一周内可能不能供所有客户使用。
>
> 有关版本中即将推出的功能的列表，请查看[开发过程中页面](in-development.md)。

**RSS 源**：通过将以下 URL 复制并粘贴到源阅读器中，可以在页面更新时收到通知：`https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Device security
### Intune apps
### Monitor and troubleshoot
### Role-based access control
-->  

<!-- ########################## -->
## <a name="week-of-february-10-2020"></a>2020 年 2 月 10 日当周

### <a name="windows-7-ends-extended-support---3042987--"></a>Windows 7 终止扩展支持 <!--3042987-->
Windows 7 已于 2020 年 1 月 14 日终止扩展支持。 Intune 已弃用对同时运行 Windows 7 的设备的支持。 帮助保护 PC 的技术协助和自动更新将不再可用。 应升级到 Windows 10。 有关详细信息，请参阅[变更计划博客文章](https://aka.ms/Windows7_Intune)。


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>应用管理

#### <a name="microsoft-edge-version-77-and-later-on-windows-10-devices---5843584---"></a>Windows 10 设备上的 Microsoft Edge 77 及更高版本<!-- 5843584 -->
Intune 现在支持卸载 Windows 10 设备上的 Microsoft Edge 版本 77 及更高版本。 有关详细信息，请参阅[将适用于 Windows 10 的 Microsoft Edge 添加到 Microsoft Intune](~/apps/apps-windows-edge.md)。

#### <a name="screen-removed-from-company-portal-android-work-profile-enrollment--6103987---"></a>从公司门户的 Android 工作配置文件注册中删除了屏幕<!--6103987 -->
从公司门户中的 Android 工作配置文件注册流中删除了“下一步是什么?”  屏幕，简化用户体验。 请转到[使用 Android 工作配置文件注册](/intune-user-help/enroll-device-android-work-profile)，查看更新后的 Android 工作配置文件注册流。  

#### <a name="company-portal-app-improved-performance---6178652---"></a>公司门户应用提高了性能<!-- 6178652 -->
公司门户应用已更新，以支持使用 ARM64 处理器的设备（例如 Surface Pro X）的更高性能。以前，公司门户以仿真 ARM32 模式运行。 现在，在版本 10.4.7080.0 及更高版本中，公司门户应用已针对 ARM64 进行了本地编译。 有关公司门户应用的详细信息，请参阅[如何配置 Microsoft Intune 公司门户应用](~/apps/company-portal-app.md)。

<!-- ########################## -->
## <a name="week-of-january-27-2020"></a>2020 年 1 月 27 日当周

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>应用管理

#### <a name="intune-support-for-additional-microsoft-edge-version-77-deployment-channel-for-macos---5983950----"></a>对适用于 macOS 的其他 Microsoft Edge 版本 77 部署通道的 Intune 支持<!-- 5983950  -->
Microsoft Intune 现在支持适用于 macOS 的 Microsoft Edge 应用的其他稳定  部署通道。 “稳定”  通道是用于在企业环境中广泛部署 Microsoft Edge 的建议通道。 它每六周更新一次，每个版本中都会加入“Beta”通道的改进  。 除了“稳定”通道  和“Beta”  通道之外，Intune 还支持“开发”  通道。 公共预览版为适用于 macOS 的 Microsoft Edge 版本 77 及更高版本提供“稳定”通道和“开发”通道。 默认情况下启用浏览器的自动更新。 有关详细信息，请参阅[使用 Microsoft Intune 添加适用于 macOS 设备的 Microsoft Edge](~/apps/apps-edge-macos.md)。

#### <a name="retirement-of-intune-managed-browser--5728447---"></a>停用 Intune Managed Browser<!--5728447 -->
Intune Managed Browser 将停用。 使用 Microsoft Edge 获取受保护的 Intune 浏览器体验。 有关详细信息，请参阅“[采取措施：使用 Microsoft Edge 获得受保护的 Intune 浏览器体验](~/fundamentals/whats-new.md#take-action-use-microsoft-edge-for-your-protected-intune-browser-experience)”条目（下面的[通知](~/fundamentals/whats-new.md#notices)一节中）。

<!-- ########################## -->
## <a name="week-of-january-20-2020-2001-service-release"></a>2020 年 1 月 20 日当周（2001 服务版本）

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>应用管理

#### <a name="user-experience-change-when-adding-apps-to-intune---4705829-----"></a>向 Intune 添加应用时的用户体验更改<!-- 4705829   -->
向 Intune 添加应用时，你将获得全新的用户体验。 此体验提供的设置和详细信息与你之前使用的相同，但是，在向 Intune 添加应用时，新体验采用类似于向导的过程。 这种新体验还会在添加应用之前提供“审阅”页。 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“应用”   > “所有应用”   > “添加”  。 有关详细信息，请参阅[将应用添加到 Microsoft Intune](~/apps/apps-add.md)。

#### <a name="require-win32-apps-to-restart----5622282-----"></a>需要重启 Win32 应用 <!-- 5622282   -->
可以要求必须在成功安装 Win32 应用后重启。 此外，还可以选择必须重启之前的时间（宽限期）。

#### <a name="user-experience-change-when-configuring-apps-in-intune---4207990-----"></a>在 Intune 中配置应用时的用户体验变化<!-- 4207990   -->
在 Intune 中创建应用配置策略时，你将获得全新的用户体验。 此体验提供的设置和详细信息与你之前使用的相同，但是，在向 Intune 添加策略时，新体验采用类似于向导的过程。 在 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，选择“应用”   > “应用配置策略”   > “添加”  。 有关详细信息，请参阅 [Microsoft Intune 的应用配置策略](~/apps/app-configuration-policies-overview.md)。 

#### <a name="intune-support-for-additional-microsoft-edge-for-windows-10-deployment-channel---5861774---"></a>对适用于 Windows 10 的其他 Microsoft Edge 部署通道的 Intune 支持<!-- 5861774 -->
Microsoft Intune 现在支持适用于 Windows 10 的 Microsoft Edge（版本 77 或更高版本）应用的其他稳定  部署通道。 “稳定”  通道是用于在企业环境中广泛部署适用于 Windows 10 的 Microsoft Edge 的建议通道。 此通道每六周更新一次，每个版本中都会加入“Beta”通道的改进  。 除了“稳定”通道  和“Beta”  通道之外，Intune 还支持“开发”  通道。 有关详细信息，请参阅[适用于 Windows 10 的 Microsoft Edge - 配置应用设置](~/apps/apps-windows-edge.md#configure-app-settings)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>设备配置

#### <a name="improved-user-interface-experience-when-configuring-exchange-activesync-on-premises-connector-ui---5695492-----"></a>改进了配置 Exchange ActiveSync 本地连接器 UI 时的用户界面体验<!-- 5695492   -->
我们更新了[配置 Exchange ActiveSync 本地连接器](../protect/exchange-connector-install.md)的体验。 更新的体验使用单个窗格来配置、编辑和汇总本地连接器的详细信息。 

#### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-----"></a>向 Android Enterprise 工作配置文件的 Wi-Fi 配置文件添加自动代理设置<!-- 4490822   -->
在 Android Enterprise 工作配置文件设备上，可以创建 Wi-Fi 配置文件。 选择 Wi-Fi“企业”类型时，还可以输入 Wi-Fi 网络上使用的可扩展身份验证协议 (EAP) 类型。

现在，选择“企业”类型时，还可以输入自动代理设置，包括代理服务器 URL，如 `proxy.contoso.com`。

若要查看可配置的现有 Wi-Fi 设置，请参阅[在 Microsoft Intune 中为运行 Android Enterprise 和 Android 展台的设备添加 Wi-Fi 设置](../configuration/wi-fi-settings-android-enterprise.md)。

适用于：
- Android Enterprise 工作配置文件

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>设备注册

#### <a name="block-android-enrollments-by-device-manufacturer--5197392----"></a>阻止设备制造商进行 Android 注册<!--5197392  -->
可以阻止设备按设备制造商进行注册。 这适用于 Android 设备管理员和 Android Enterprise 工作配置文件设备。 若要查看注册限制，请转到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)“设备” >   “注册限制” > “设备限制”  。

#### <a name="improvements-to-the-iosipados-create-enrollment-type-profile-ui---6055005---"></a>对 iOS/iPadOS 创建注册类型配置文件 UI 的改进<!-- 6055005 -->
对于 iOS/iPadOS 用户注册，已简化“创建注册类型配置文件设置”页，   改进“注册类型”  选项进程，同时保持功能不变。 若要查看新 UI，请转到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431) > “设备”   > “iOS”   > “iOS 注册”   > “注册类型”   > “创建配置文件”   > “设置”页  。 有关详细信息，请参阅[在 Intune 中创建用户注册配置文件](../enrollment/ios-user-enrollment.md#create-a-user-enrollment-profile-in-intune)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>设备管理

#### <a name="new-information-in-device-details---4471759-5604099----"></a>设备详细信息中的新信息<!-- 4471759 5604099  -->
以下信息现在位于设备的“概述”  页上：
- 内存容量（设备上的物理内存量）
- 存储容量（设备上的物理存储量） 
- CPU 体系结构


#### <a name="ios-bypass-activation-lock-remote-action-renamed-to-disable-activation-lock---5904591----"></a>iOS“绕过激活锁”远程操作已重命名为“禁用激活锁” <!--5904591  -->
远程操作“绕过激活锁”  已重命名为“禁用激活锁”  。 有关详细信息，请参阅[通过 Intune 禁用 iOS 激活锁](../remote-actions/device-activation-lock-bypass.md)。

#### <a name="windows-10-feature-update-deployment-support-for-autopilot-devices---5948137-----"></a>对 Autopilot 设备的 Windows 10 功能更新部署支持<!-- 5948137   -->
Intune 现在支持使用 [Windows 10 功能更新部署](../protect/windows-update-for-business-configure.md#windows-10-feature-updates)来定位 Autopilot 注册的设备。

在 Autopilot 开箱即用体验 (OOBE) 期间，不能应用 Windows 10 功能更新策略，这些策略仅在设备完成预配（通常为一天）后第一次进行 Windows 更新扫描时应用。


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>监视和故障排除

#### <a name="windows-autopilot-deployment-reports-preview----3856172-----"></a>Windows Autopilot 部署报表（预览） <!-- 3856172   -->
新报告说明了通过 Windows Autopilot 部署的每个设备的详细信息。 有关详细信息，请参阅 [Autopilot 部署报告](../enrollment/enrollment-autopilot.md#autopilot-deployments-report)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>基于角色的访问控制

#### <a name="new-intune-built-in-role-endpoint-security-manager--4253397-----"></a>新的 Intune 内置角色终结点安全管理器<!--4253397   -->
提供新的 Intune 内置角色：终结点安全管理器。 这个新角色使管理员能够在 Intune 中完全访问终结点管理器节点，并具有对其他区域的只读访问权限。 该角色是 Azure AD 中“安全管理员”角色的扩展。 如果目前只有全局管理员角色，则无需进行任何更改。 如果你使用角色，并且想要终结点安全管理器提供的粒度，则在该角色可用时分配该角色。 有关内置角色的详细信息，请参阅[基于角色的访问控制](role-based-access-control.md)。

<!-- ########################## -->
## <a name="week-of-january-6-2020"></a>2020 年 1 月 6 日当周

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>应用管理

#### <a name="smime-support-for-microsoft-outlook-for-ios---2669398---"></a>对 Microsoft Outlook for iOS 提供 S/MIME 支持<!-- 2669398 -->
Intune 支持提供 S/MIME 签名和加密证书，适用于 iOS 设备上的 Outlook for iOS。 有关详细信息，请参阅[适用于 iOS 和 Android 的敏感度标签和保护](https://aka.ms/omsmime)。

#### <a name="cache-win32-app-content-using-microsoft-connected-cache-server---6030314---"></a>使用 Microsoft Connected Cache 服务器缓存 Win32 应用内容<!-- 6030314 -->
可以在 Configuration Manager 分发点上安装 Microsoft Connected Cache 服务器，用于缓存 Intune Win32 应用内容。 有关详细信息，请参阅 [Configuration Manager 中的 Microsoft Connected Cache - 对 Intune Win32 应用的支持](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/microsoft-connected-cache#bkmk_intune)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>基于角色的访问控制

#### <a name="windows-10-administrative-templates-admx-profiles-now-support-scope-tags---5137390---"></a>Windows 10 管理模板 (ADMX) 配置文件现支持范围标记 <!--5137390 -->
现在可以将范围标记分配给管理模板配置文件 (ADMX)。 为此，请前往“Intune”   > “设备”   > “配置文件”  >“在列表中选择管理模板配置文件”>“属性”   > “范围标记”  。 有关范围标记的详细信息，请参阅[向其他对象分配范围标记](../fundamentals/scope-tags.md#assign-scope-tags-to-other-objects)。

<!-- ########################## -->
## <a name="week-of-december-30-2019"></a>2019 年 12 月 30 日当周

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>应用管理

#### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices---4851745---"></a>从 MEM 加密的 macOS 设备检索个人恢复密钥<!-- 4851745 -->
借助 iOS 公司门户应用，最终用户可以检索其个人恢复密钥（FileVault 密钥）。 拥有个人恢复密钥的设备必须已注册 Intune，并且通过 Intune 使用 FileVault 加密。 借助 iOS 公司门户应用，最终用户单击“获取恢复密钥”，即可以在加密的 macOS 设备中检索个人恢复密钥。  此外，还可以通过选择“设备” > “已加密和已注册的 macOS 设备” > “获取恢复密钥”，来从 Intune 检索恢复密钥。    有关 FileVault 的详细信息，请参阅[用于 macOS 的 FileVault 加密](~/protect/encrypt-devices.md#filevault-encryption-for-macos)。

#### <a name="ios-and-ipados-user-licensed-vpp-apps---5619268---"></a>iOS 和 iPadOS 用户许可的 VPP 应用<!-- 5619268 -->
对于用户注册的 iOS 和 iPadOS 设备，将不再向最终用户显示部署为可用的新创建的设备许可的 VPP 应用程序。 不过，最终用户会继续看到公司门户中的所有用户许可的 VPP 应用。 有关 VPP 应用的详细信息，请参阅[如何使用 Microsoft Intune 管理通过 Apple Volume Purchase Program 购买的 iOS and macOS 应用](~/apps/vpp-apps-ios.md)。

<!-- ########################## -->
## <a name="week-of-december-23-2019"></a>2019 年 12 月 23 日当周

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>应用管理

#### <a name="notice---windows-10-1703-rs2-will-be-moving-out-of-support----5026679---"></a>通知 - 不再支持 Windows 10 1703 (RS2) <!-- 5026679 -->
自 2018 年 10 月 9 日起，家庭版、专业版和专业工作站版的 Microsoft 平台支持不再包含 Windows 10 1703 (RS2)。 在 2019 年 10 月 8 日，Windows 10 企业版和教育版平台支持不再包含 Windows 10 1703 (RS2)。 自 2019 年 12 月 26 日起，我们会将 Windows 公司门户应用程序最低版本更新到 Windows 10 1709 (RS3)。 运行 1709 之前版本的计算机将不再从 Microsoft Store 收到此应用程序的更新版。 之前我们已通过消息中心将此变更告知使用 Windows 10 早期版本的客户。 有关详细信息，请参阅 [Windows 生命周期简报](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)。

<!-- ########################## -->

## <a name="week-of-december-16-2019"></a>2019 年 12 月 16 日当周

### <a name="device-configuration"></a>设备配置

#### <a name="updates-to-administrative-templates-for-windows-10-devices----5941568---"></a>Windows 10 设备管理模板更新 <!-- 5941568 -->

可以使用 Microsoft Intune 中的 ADMX 模板控制和管理用于 Microsoft Edge、Office 和 Windows 的设置。 Intune 中的管理模板做出以下策略设置更新：

- 添加了对 Microsoft Edge 版本 78 和 79 的支持。
- 包括[管理模板文件 (ADMX/ADML) 和适用于 Office 365 专业增强版、Office 2019 和 Office 2016 的 Office 自定义工具](https://www.microsoft.com/download/details.aspx?id=49030)中的 ADMX（2019 年 11 月 11 日）文件。

有关 Intune 中的 ADMX 模板的详细信息，请参阅[使用 Windows 10 模板在 Microsoft Intune 中配置组策略设置](../configuration/administrative-templates-windows.md)。

适用于：

- Windows 10 及更高版本

## <a name="week-of-december-9-2019-1912-service-release"></a>2019 年 12 月 9 日当周（1912 服务版本）

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>应用管理

#### <a name="migrating-to-microsoft-edge-for-managed-browsing-scenarios---5173762---"></a>迁移到适用于托管浏览方案的 Microsoft Edge<!-- 5173762 -->
由于即将停用 Intune Managed Browser，我们对应用保护策略进行了更改，以简化将用户转移到 Edge 所需的步骤。 我们将应用保护策略设置的选项“限制使用其他应用传输 Web 内容”更新为以下之一  ：

- 任何应用
- Intune 托管浏览器
- Microsoft Edge
- 非托管浏览器 

选择“Microsoft Edge”时，最终用户将看到条件访问消息，该消息通知他们托管浏览方案需要 Microsoft Edge  。 如果尚未下载，系统将提示他们下载 Microsoft Edge 并使用其 AAD 帐户登录 Microsoft Edge。  这等同于将目标设置为应用配置设置 `com.microsoft.intune.useEdge` 设为 True 的启用了 MAM 的应用  。 使用“策略托管浏览器”设置的现有应用保护策略现已选中“Intune Managed Browser”，你将看不到任何行为更改   。 这意味着，如果你将 useEdge 应用配置设置设为 True，则用户将看到一条要求使用 Microsoft Edge 的消息   。 我们鼓励所有使用托管浏览方案的客户通过“限制使用其他应用传输 Web 内容”来更新其应用保护策略，以确保用户无论从哪个应用启动链接，都可以看到过渡到 Microsoft Edge 的合适指南  。 

#### <a name="configure-app-notification-content-for-organization-accounts---2576686----"></a>配置组织帐户的应用通知内容<!-- 2576686  -->
借助 Android 和 iOS 设备上的 Intune 应用保护策略 (APP)，可以控制组织帐户的应用通知内容。 可以选择一个选项（“允许”、“组织组织数据”、或“阻止”），以指定如何为选定的应用显示组织帐户的通知。此功能需要应用程序的支持，可能并非在所有启用 APP 的应用程序中可用。 Outlook for iOS 版本 4.15.0（或更高版本）和 Outlook for Android 4.83.0（或更高版本）将支持此设置。 可从控制台获取此设置，但此功能将从 2019 年 12 月 16 日之后开始生效。 有关 APP 的详细信息，请参阅[什么是应用保护策略？](../apps/app-protection-policy.md)。

#### <a name="microsoft-app-icons-update--4677605----"></a>Microsoft 应用图标更新<!--4677605  -->
应用保护策略和应用配置策略的应用目标窗格中用于 Microsoft 应用的图标已更新。

#### <a name="require-use-of-approved-keyboards-on-android--4761794----"></a>要求在 Android 上使用经过批准的键盘<!--4761794  -->
在应用保护策略中，可以指定设置[“批准的键盘”  ](../apps/app-protection-policy-settings-android.md#data-protection)，以管理可以将哪些 Android 键盘用于托管的 Android 应用。 当用户打开此托管应用并且尚未将批准的键盘用于该应用时，将提示他们切换到设备上已安装的一个经过批准的键盘。 必要时，会为用户提供从 Google Play Store 下载批准的键盘的链接，以便他们可以进行安装和设置。 如果用户的活动键盘不是经过批准的键盘，则用户只能够编辑托管应用中的文本字段。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>设备配置

#### <a name="updated-single-sign-on-experience-for-apps-and-websites-on-your-ios-ipados-and-macos-devices---4999578----"></a>更新了 iOS、iPadOS 和 macOS 设备上的应用和网站的单一登录体验<!-- 4999578  -->
Intune 添加了更多适用于 iOS、iPadOS 和 macOS 设备的单一登录 (SSO) 设置。 现在可以配置组织或标志提供者编写的重定向 SSO 应用扩展。 使用这些设置来为使用新式身份验证方法（如 OAuth 和 SAML2）的应用和网站配置无缝单一登录体验。 

这些新设置扩展了 SSO 应用扩展和 Apple 内置 Kerberos 扩展的旧设置（“设备”   > “设备配置”   > “配置文件”   > “创建配置文件”   >  为平台类型选择“iOS/iPadOS”或“macOS”> 为配置文件类型选择“设备功能”）。    

转到 [iOS 上的 SSO](../configuration/ios-device-features-settings.md#single-sign-on-app-extension) 和 [macOS 上的 SSO](../configuration/macos-device-features-settings.md#single-sign-on-app-extension)，可查看可配置的 SSO 应用扩展设置的完整范围。

适用于：

- iOS/iPadOS
- macOS

#### <a name="we-have-updated-two-device-restriction-settings-for-ios-and-ipados-devices-to-correct-their-behavior---5701352------"></a>我们更新了针对 iOS 和 iPadOS 设备的两个设备限制设置，以更正这些设备的行为<!-- 5701352    -->
对于 iOS 设备，你可以创建设备限制配置文件来“允许无线 PKI 更新”和“阻止 USB 受限模式”   （“设备”   > “设备配置”   > “配置文件”   > “创建配置文件”   >  为平台选择“iOS/iPadOS”> 为配置文件类型选择“设备限制”）。   在此版本之前，以下设置的 UI 设置和说明均不正确，现已更正。 自此版本开始，这些设置的行为如下所示：

**阻止无线 PKI 更新**：**阻止**：若设备未连接计算机，将阻止用户收到软件更新。 **未配置**（默认设置）：设备无需连接计算机，即可收到软件更新。
- 之前，你可以将此设置配置如下：**允许**：你的用户无需将设备连接到计算机，即可收到软件更新。
**在设备锁定时允许使用 USB 附件**：**允许**：允许 USB 附件与锁定超过一个小时的设备交换数据。 **未配置**（默认设置）：未更新设备的 USB 受限模式，若设备锁定时间超过一个小时，将阻止 USB 附件从设备传输数据。
- 之前，你可以将此设置配置如下：**阻止**：可禁用受监管设备上的 USB 受限模式。

有关可以配置的设置的详细信息，请参阅[使用 Intune 允许或限制功能的 iOS 和 iPadOS 设备设置](../configuration/device-restrictions-ios.md)。

此功能适用于：

- iOS/iPadOS

#### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>macOS 设备的有线网络设备配置文件<!-- 3508686  -->
   > [!NOTE]
   > 此功能推迟到稍后发布。

#### <a name="block-users-from-configuring-certificate-credentials-in-the-managed-keystore-on-android-enterprise-device-owner-devices---3311998---"></a>阻止用户在 Android Enterprise 设备所有者设备的托管密钥存储中配置证书凭据<!-- 3311998 -->
在 Android Enterprise 设备所有者上，你可以配置一个新设置，来阻止用户在托管密钥存储中配置证书凭据（“设备配置”   > “配置文件”   > “创建配置文件”   > “Android Enterprise”（针对平台）>“仅设备所有者”>“设备限制”（针对配置文件类型）>“用户和帐户”）。   

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>设备管理

#### <a name="protected-wipe-action-now-available--51150000---"></a>受保护的擦除操作现已可用<!--51150000 -->
现在可以选择使用擦除设备操作对设备执行受保护的擦除。 除了受保护的擦除无法通过关闭设备规避，它与标准擦除相同。 受保护的擦除将继续尝试重置设备，直到成功为止。 在一些配置中，此操作可能会使设备无法重启。 有关详细信息，请参阅[停用或擦除设备](../remote-actions/devices-wipe.md)。

#### <a name="device-ethernet-mac-address-added-to-devices-overview-page--5562275---"></a>将设备以太网 MAC 地址添加到了设备的“概述”页<!--5562275 -->
现在可以从设备详细信息页看到设备的以太网 MAC 地址（“设备”   > “所有设备”  > 选择一个设备 > “概述”。 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>设备安全性

#### <a name="improved-experience-on-a-shared-device-when-device-based-conditional-access-policies-are-enabled---1734096----"></a>改进了启用基于设备的条件访问策略时共享设备中的体验<!-- 1734096  -->
通过在执行策略时选中针对用户的最新符合性评估具有多个用户（针对基于设备的条件访问策略）的共享设备中的体验。 有关详细信息，请参阅下列概述文章：
- [Azure 条件访问概述](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)
- [Intune 设备符合性概述](../protect/device-compliance-get-started.md)

#### <a name="use-pkcs-certificate-profiles-to-provision-devices-with-certificates---2317124-2317130-2317139-2340517-2340528-2340529----"></a>使用 PKCS 证书配置文件为设备预配证书<!-- 2317124, 2317130, 2317139, 2340517, 2340528, 2340529  -->
现在，当运行 Android for Work、iOS 和 Windows 的设备与 PKCS 证书配置文件关联时，可以使用配置文件向其颁发证书，例如用于 Wi-Fi 和 VPN 的配置文件  。 之前，这三个平台仅支持基于用户的证书，基于设备的支持仅限于 macOS。

> [!NOTE]
> Wi-Fi 配置文件不支持 PKCS 证书配置文件。 而是在使用 [EAP 类型](../configuration/wi-fi-settings-windows.md#enterprise-profile)时使用 SCEP 证书配置文件。

若要使用基于设备的证书，在为支持的平台[创建 PKCS 证书配置文件](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile)时选择“设置”。  现在将显示“证书类型”设置，它支持“设备”或“用户”选项。 



<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>监视和故障排除

#### <a name="centralized-audit-logs--5603185-5697164---"></a>集中式化审核日志<!--5603185, 5697164 -->
现在全新的集中式审核日志体验可将各种类别的审核日志收集到一个页面。 可以通过筛选日志来获得你所寻找的数据。 若要查看审核日志，可转到“租户管理”   > “审核日志”。  

#### <a name="scope-tag-information-included-in-audit-log-activity-details--5763534---"></a>将范围标记信息包含在审核日志活动详细信息中<!--5763534 -->
现在审核日志活动详细信息包含范围标记信息（针对支持范围标记的 Intune 对象）。 有关审核日志的详细信息，请参阅[使用审核日志跟踪和监视事件](monitor-audit-logs.md)。


<!-- ########################## -->
## <a name="week-of-december-2-2019"></a>2019 年 12 月 2 日当周

#### <a name="new-microsoft-endpoint-configuration-manager-co-management-licensing--5027281--"></a>新的 Microsoft Endpoint Configuration Manager 共同管理许可<!--5027281-->
拥有软件保障的 Configuration Manager 客户在不购买额外的 Intune 共同管理许可证的情况下可获得适用于 Windows 10 电脑的 Intune 共同管理。 客户不再需要为其最终用户分配单独的 Intune/EMS 许可证以共同管理 Windows 10。
- 由 Configuration Manager 管理并注册加入共同管理的设备拥有与 Intune 独立 MDM 托管的电脑几乎相同的权限。 但在重置后，不能使用 Autopilot 重新预配它们。
- 通过使用其他方式注册到 Intune 的 Windows 10 设备需要完整的 Intune 许可证。
- 其他平台上的设备仍需要完整的 Intune 许可证。

有关详细信息，请参阅[许可条款](https://www.microsoft.com/en-us/Licensing/product-licensing/products)。


<!-- ########################## -->
## <a name="week-of-november-18-2019-1911-service-release"></a>2019 年 11 月 18 日当周（1911 服务版本）

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>应用管理

#### <a name="ui-update-when-selectively-wiping-app-data---4102028---"></a>针对何时选择性擦除应用数据更新了 UI<!-- 4102028 -->
更新了 Intune 中用于选择性擦除应用数据的 UI。 UI 更改包括：
- 简化了体验，可使用压缩在一个窗格中的向导式格式。
- 对创建流进行了更新，使其包含分配。
- 在创建新策略前查看属性时，或在编辑属性时，将显示包含已设置的所有内容的摘要页。 此外，编辑属性时，摘要将仅显示正在编辑的属性类别的项目列表。

有关详细信息，请参阅[如何仅擦除 Intune 托管应用中的企业数据](~/apps/apps-selective-wipe.md)。

#### <a name="ios-and-ipados-third-party-keyboard-support---4922950---"></a>iOS 和 iPadOS 第三方键盘支持<!-- 4922950 -->
2019 年 3 月，我们宣布不再支持 iOS 应用保护策略设置“第三方键盘”。 此功能将返回到支持 iOS 和 iPadOS 的 Intune。 若要启用此设置，请访问新的或现有的 iOS/iPadOS 应用保护策略的“数据保护”  选项卡，并在“数据传输”  下查找“第三方键盘”  设置。

此策略设置的行为与以前的实现略有不同。 在使用 SDK 版本 12.0.16 及更高版本的多标识应用中，如果应用保护策略的目标是将此设置配置为“阻止”  ，则最终用户将无法在其组织和个人帐户中选择第三方键盘。 使用 SDK 版本 12.0.12 及更早版本的应用将继续显示以下博客文章标题中所述的行为：[已知问题：个人帐户的 iOS 中不阻止第三方键盘](https://aka.ms/3rdparty_iOS_Intune)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>设备配置

#### <a name="target-macos-user-groups-to-require-jamf-management---4061739----"></a>需要 Jamf 管理的目标 macOS 用户组<!-- 4061739  --> 
可以面向特定的用户组，这些用户将获得[由 Jamf 管理的 macOS 设备](../protect/conditional-access-integrate-jamf.md)。 这使你可以将 Jamf 符合性集成应用于 macOS 设备的子集，而其他设备由 Intune 管理。 如果已在使用 Jamf 集成，则默认情况下，所有用户都将作为集成目标。

#### <a name="new-exchange-activesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices---4892824-----"></a>在 iOS 设备上创建电子邮件设备配置文件时的新 Exchange ActiveSync 设置<!-- 4892824   --> 
在 iOS/iPadOS 设备上，可以在设备配置文件中创建电子邮件连接（“设备配置”   > “配置文件”   > “创建配置文件”   > “iOS/iPadOS”  (针对平台) >“电子邮件”  (针对配置文件类型)）。 

提供了新的 Exchange ActiveSync 设置，包括：
- **要同步的 Exchange 数据**：为日历、联系人、提醒、备注和电子邮件选择要同步（或阻止同步）的 Exchange 服务。
- **允许用户更改同步设置**：允许（或阻止）用户在其设备上更改这些服务的同步设置。  

有关这些设置的详细信息，请参阅 [Intune 中适用于 iOS 设备的 电子邮件配置文件设置](../configuration/email-settings-ios.md)。 

适用于：

- iOS 13.0 及更高版本
- iPadOS 13.0 及更高版本

#### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-fully-managed-and-dedicated-devices---5353228-----"></a>阻止用户将个人 Google 帐户添加到 Android Enterprise 完全托管的专用设备<!-- 5353228   -->
在 Android Enterprise 完全托管的专用设备上，提供了一个新设置以阻止用户创建个人 Google 帐户（“设备配置”   > “配置文件”   > “创建配置文件”   > “Android Enterprise”  (针对平台) >“仅设备所有者”>“设备限制”  (针对配置文件类型) >“用户和帐户设置”   > “个人 Google 帐户”  ）。

要查看可以配置的设置，请转到[便于使用 Intune 允许或限制功能的 Android Enterprise 设备设置](../configuration/device-restrictions-android-for-work.md)。

适用于：

- Android Enterprise 完全托管设备
- Android Enterprise 专用设备

#### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-iosipados-device-restrictions-profile----5468501-----"></a>iOS/iPadOS 设备限制配置文件中删除了“Siri 命令的服务器端日志记录”设置 <!-- 5468501   -->
在 iOS 和 iPadOS 设备上，从 Microsoft 终结点管理器管理控制台中删除了“Siri 命令的服务器端日志记录”  设置（“设备配置”   > “配置文件”   > “创建配置文件”   > “iOS/iPadOS”  (针对平台) >“设备限制”  (针对配置文件类型) >“内置应用”  ）。 

此设置对设备不起作用。 若要从现有配置文件中删除此设置，请打开该配置文件，进行更改，然后保存该配置文件。 配置文件已更新，并从设备中删除了该设置。

若要查看可以配置的设置，请参阅[使用 Intune 允许或限制功能的 iOS 和 iPadOS 设备设置](../configuration/device-restrictions-ios.md)。

适用于：

- iOS/iPadOS

#### <a name="windows-10-feature-updates-public-preview---2384877---"></a>Windows 10 功能更新（公开预览版）<!-- 2384877 -->
你现在可以将 [Windows 10 功能更新](../protect/windows-update-for-business-configure.md#windows-10-feature-updates)部署到 Windows 10 设备。 Windows 10 功能更新是一个新的软件更新策略，该策略用于设置你想要在设备中安装和保留的 Windows 10 版本。 可以将此新策略类型和现有的 Windows 10 更新通道一起使用。

接收 Windows 10 功能更新策略的设备将安装指定版本的 Windows，然后一直保留该版本，直到策略被编辑或删除。 运行更高版本 Windows 的设备仍保持其当前版本。 保持在特定 Windows 版本的设备仍可以在 Windows 10 更新通道中安装该版本的质量和安全更新。

此新类型的策略在本周开始向租户推出。 如果你的租户尚未能使用此策略，敬请期待，很快就可以使用。

#### <a name="add-and-change-key-information-in-plist-files-for-macos-applications---4736278---"></a>为 macOS 应用程序添加和更改 plist 文件中的关键信息<!-- 4736278 -->
在 macOS 设备上，你现在可以创建设备配置文件，该配置文件将上传与应用或设备关联的属性列表文件 (.plist)（“设备”   > “配置文件”   > “创建配置文件”   > “macOS”  (针对平台) >“首选项文件”  (针对配置文件类型)）。

只有某些应用支持托管首选项，并且这些应用可能不允许管理所有设置。 请确保上传的属性列表文件可配置设备通道设置，而不是用户通道设置。

有关此功能的详细信息，请参阅[使用 Microsoft Intune 向 macOS 设备添加属性列表文件](../configuration/preference-file-settings-macos.md)。

适用于：

- 运行 10.7 及更高版本的 macOS 设备

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>设备管理

#### <a name="edit-device-name-value-for-autopilot-devices---2640074---"></a>编辑 Autopilot 设备的设备名称值<!-- 2640074 -->
可以编辑 Azure AD 联接的 Autopilot 设备的设备名称值。  有关详细信息，请参阅[编辑 Autopilot 设备属性](../enrollment/enrollment-autopilot.md#edit-autopilot-device-attributes)。

#### <a name="edit-group-tag-value-for-autopilot-devices---4816775-----"></a>编辑 Autopilot 设备的组标记值<!-- 4816775   -->
可以编辑 Autopilot 设备的组标记值。 有关详细信息，请参阅[编辑 Autopilot 设备属性](../enrollment/enrollment-autopilot.md#edit-autopilot-device-attributes)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>监视和故障排除

#### <a name="updated-support-experience---5012398---"></a>更新的支持体验<!-- 5012398 -->

从现在开始，针对[获取 Intune 的帮助和支持](get-support.md)将向租户推出已更新且简化的控制台内体验。 如果你尚未能感受此新体验，敬请期待，很快就会推出。

我们改进了针对常见问题的控制台内搜索和反馈，以及用于联系支持人员的工作流。 打开支持问题时，你将看到需要回拨或电子邮件答复的实时估计，并且顶级和统一支持客户可以轻松地为其问题指定严重性，以帮助更快地获得支持。

#### <a name="improved-intune-reporting-experience-public-preview----3791418---"></a>改进了 Intune 报表体验（公共预览版） <!-- 3791418 -->
Intune 现在提供了改进的报表体验，包括新的报表类型、更好的报表组织、更集中的视图、改进的报表功能以及更一致和更及时的数据。 新的报表类型侧重于以下内容：
- **操作** - 提供具有负面运行状况的全新记录。 
- **组织** - 提供总体状态的更广泛汇总。
- **历史** - 提供一段时间内的模式和趋势。
- **专业** - 允许使用原始数据创建自己的自定义报表。

第一组新报表侧重于设备符合性。 有关详细信息，请参阅[博客 - Microsoft Intune 报表框架](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553)和 [Intune 报表](~/fundamentals/reports.md)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>基于角色的访问控制

#### <a name="duplicate-custom-or-built-in-roles----1081938-----"></a>复制自定义或内置角色 <!-- 1081938   -->
现在可以复制内置和自定义角色。 有关详细信息，请参阅[复制角色](../fundamentals/create-custom-role.md#copy-a-role)。

#### <a name="new-permissions-for-school-administrator-role----5621805----"></a>学校管理员角色的新权限 <!-- 5621805  -->  
已将两个新权限（“分配配置文件”  和“同步设备”  ）添加到了学校管理员角色 >“权限”   > “注册计划”  。 同步配置文件权限允许组管理员同步 Windows Autopilot 设备。 分配配置文件权限允许他们删除用户启动的 Apple 注册配置文件。 它还提供了相关权限以允许他们管理 Autopilot 设备分配和 Autopilot 部署配置文件分配。 有关所有学校管理员/组管理员权限的列表，请参阅[分配组管理员](https://docs.microsoft.com/intune-education/group-admin-delegate)。 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="security"></a>安全

#### <a name="bitlocker-key-rotation---2564951----"></a>BitLocker 密钥轮换<!-- 2564951  -->
对于运行 Windows 1909 或更高版本的托管设备，你可以使用 Intune 设备操作远程[轮换 BitLocker 恢复密钥](../protect/encrypt-devices.md#rotate-bitlocker-recovery-keys)。 若要获取相关资格以轮换恢复密钥，设备必须配置为支持恢复密钥轮换。  

#### <a name="updates-to-dedicated-device-enrollment-to-support-scep-device-certificate-deployment----5198878----"></a>更新了专用设备注册以支持 SCEP 设备证书部署 <!-- 5198878  -->
Intune 现在支持 SCEP 设备证书部署到 Android Enterprise 专用设备，以实现对 Wi-Fi 配置文件的基于证书的访问。 若要使部署正常工作，设备上必须存在 Microsoft Intune 应用。 因此，我们更新了 Android Enterprise 专用设备的注册体验。 新注册仍将以相同的方式（QR、NFC、零接触或设备标识符）启动，但现在需要用户安装 Intune 应用。 现有设备将开始以滚动的方式自动安装应用。

#### <a name="intune-audit-logs-for-business-to-business-collaboration--5670211---"></a>面向企业到企业协作的 Intune 审核日志<!--5670211 -->
企业到企业 (B2B) 协作可以安全地将公司的应用程序和服务与来自任何其他组织的来宾用户共享，同时保持对自己公司数据的控制。 Intune 现在支持 B2B 来宾用户的审核日志。 例如，当来宾用户进行更改时，Intune 将能够通过审核日志捕获此数据。 有关详细信息，请参阅[什么是 Azure Active Directory B2B 中的来宾用户访问权限？](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b)


<!-- ########################## -->
## <a name="week-of-november-11-2019"></a>2019 年 11 月 11 日当周  

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>应用管理  

#### <a name="improved-macos-enrollment-experience-in-company-portal----5074349----"></a>在公司门户中改进了 macOS 注册体验 <!-- 5074349  -->  
用于 macOS 注册的公司门户提供的注册过程更简单，与用于 iOS 注册的公司门户高度一致。 设备用户现在可以看到：  

* 流畅的用户界面。  
* 改进的注册清单。  
* 更清晰的设备注册说明。  
* 改进的疑难解答选项。  

#### <a name="web-apps-launched-from-the-windows-company-portal-app---5030972---"></a>从 Windows 公司门户应用启动的 Web 应用<!-- 5030972 -->
最终用户现在可以直接从 Windows 公司门户应用启动 Web 应用。 最终用户可以选择 Web 应用，然后选择选项“在浏览器中打开”  。 已发布的 Web URL 直接在 Web 浏览器中打开。 此功能将在下周推出。 有关 Web 应用的详细信息，请参阅[向 Microsoft Intune 添加 Web 应用](~/apps/web-app.md)。  


#### <a name="new-assignment-type-column-in-company-portal-for-windows-10----5459950----"></a>适用于 Windows 10 的公司门户中的”新建分配类型”列 <!-- 5459950  -->
“公司门户”>“安装的应用” > “分配类型”列已重命名为“你的组织需要”    。  在该列下，用户将看到“是”或“否”值，以指示应用是其组织必需的还是可选的   。 之所以做出这些更改是因为设备用户对可用应用的概念感到困惑。 用户可以参阅[在设备上安装和共享应用](/intune-user-help/install-apps-cpapp-windows)以获取从公司门户安装应用的详细信息。 有关为用户配置公司门户应用的详细信息，请参阅[如何配置 Microsoft Intune 公司门户应用](~/apps/company-portal-app.md)。  

<!-- ########################## -->
## <a name="week-of-november-4-2019"></a>2019 年 11 月 4 日当周

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>设备安全性

#### <a name="security-baselines-are-supported-on-microsoft-azure-government---4062552---"></a>Microsoft Azure 政府支持安全基线<!-- 4062552 -->

Microsoft Azure 政府  上托管的 Intune 实例现在可以使用[安全基线](../protect/security-baselines.md)来帮助保护用户和设备的安全。

## <a name="whats-new-archive"></a>新增功能存档
若要了解前几个月的新增功能，请参阅[新增功能存档](whats-new-archive.md)。

## <a name="notices"></a>通知

[!INCLUDE [Intune notices](../includes/intune-notices.md)]
