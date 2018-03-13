---
title: "早期版本"
description: 
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/24/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d7c2ec47a163c16de91d3004a6204c1c00feb801
ms.sourcegitcommit: eac89306d1391a6d3ae1179612b0820b19c2baa6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="the-early-edition-for-microsoft-intune---february-2018"></a>Microsoft Intune 的早期版本 - 2018 年 2 月

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


<!-- 1802 start -->

### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>新的注册失败趋势图表和失败原因表<!-- 1471783 -->

在“注册概述”页，你将能够查看注册失败趋势和前五个失败原因。 单击图表或表可查看详细信息，以查找故障排除建议和修正建议。

### <a name="prevent-end-users-from-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>防止最终用户添加或删除工作配置文件中的帐户 <!-- 1728700 -->    
将 Gmail 应用部署到 Android for Work 配置文件中后，能够防止最终用户通过使用 Android for Work 设备限制配置文件中的“添加和删除帐户”设置添加或删除工作配置文件中的帐户。

### <a name="app-protection-policies-----679615---"></a>应用保护策略<!-- 679615 -->
Intune 应用保护策略将提供创建默认全局策略的功能，以便快速对整个租户中所有用户启用保护。

### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Intune 支持多个 Apple DEP/Apple School Manager 帐户 <!-- 747685 -->

Intune 将支持最多通过 100 个不同的 Apple 设备注册计划 (DEP) 或 Apple School Manager 帐户注册设备。 可以单独管理注册配置文件和设备的每个已上传令牌。 可以根据已上传的 DEP/ School Manager 令牌自动分配不同的注册配置文件。 如果上传了多个 School Manager 令牌，一次只能与 Microsoft 学校数据同步共享一个令牌。

迁移后，通过 Graph 管理 Apple DEP 或 ASM 的 beta 版本 Graph API 和已发布脚本将不再有效。 新的 beta 版本 Graph API 正在进行开发，将在迁移后发布。

### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Windows Defender 运行状况状态和威胁状态报告 <!--854704 -->

了解 Windows Defender 的运行状况和状态是管理 Windows 电脑的关键。  Intune 将向 Windows Defender 代理的状态和运行状况添加新的报告和操作。 通过使用设备符合性工作负载中的状态汇总报告，可以看到需要以下任一项的设备：

- 签名更新
- 重新启动
- 手动干预
- 完全扫描
- 需要干预的其他代理状态

在某些情况下，可以采取远程更正操作，例如触发签名更新。  此报告中还显示了报告为“清理”的电脑数量。

每个状态类别的深入报告列出需要注意的各个电脑，或者报告为“清理”的电脑。

### <a name="protocol-exceptions-for-applications---1035509-eeready--"></a>应用程序的协议异常 <!--1035509 eeready-->

可以将异常创建到 Intune 移动应用程序管理 (MAM) 数据传输策略以打开特定的非托管应用程序。 此类应用程序必须受到 IT 的信任。 除创建的异常外，当数据传输策略设置为“仅限托管应用”时，数据传输仍将仅限于由 Intune 托管的应用程序。 可以使用协议 (iOS) 或包 (Android) 创建限制。

例如，可以将 Webex 包作为异常添加到 MAM 数据传输策略。 这样使托管 Outlook 电子邮件消息中的 Webex 链接可以直接在 Webex 应用程序中打开。 其他非托管的应用程序中将继续限制数据传输。

### <a name="customize-your-company-portal-themes-with-hex-codes---1049561-eeready--"></a>使用十六进制代码自定义公司门户主题 <!--1049561 eeready-->

可以使用十六进制代码自定义公司门户应用中的主题颜色。 输入十六进制代码时，Intune 将按照 [WCAG 2.0 标准](http://www.w3.org/TR/WCAG20)确定在文本颜色和背景色之间提供最高级别对比度的文本颜色。 可以在“移动应用” > “公司门户”中预览文本颜色和公司徽标之间的颜色对比。 

### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252---"></a>添加到终结点保护设置的新 Windows Defender Credential Guard 设置 <!--1102252 --> 

新 [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard] 设置将添加到“设备配置” > “配置文件” > “终结点保护”。 将添加以下设置： 

- 平台安全级别：指定平台安全级别是否在下次重启时启用。 基于虚拟化的安全性需要安全启动。 可以选择使用直接内存访问 (DMA) 保护启用基于虚拟化的安全性。 DMA 保护需要硬盘支持并且将仅在正确配置的设备上启用。
- 基于虚拟化的安全性：指定基于虚拟化的安全性是否在下次重启时启用。 
- Windows Defender Credential Guard：当具有安全启动的平台安全级别和基于虚拟化的安全性同时启用时，在下次重启时通过基于虚拟化的安全性打开 Credential Guard 以帮助保护凭据。 可用选项包括“禁用”、“使用 UEFI 锁启用”、“无锁启用”和“未配置”。 
  - “禁用”选项将远程关闭 Credential Guard（如果之前已使用“无锁启用”选项启用）。

  - “使用 UEFI 锁启用”选项可确保 Credential Guard 不能通过注册表项或通过使用组策略禁用。 若要在使用此设置后禁用 Credential Guard，必须将组策略设置为“禁用”，并通过真实存在的用户从每台计算机中删除安全功能，以清除 UEFI 中保留的配置。 只要 UEFI 配置仍然存在，Credential Guard 则会保持启用状态。

  - “无锁启用”选项允许通过使用组策略远程禁用 Credential Guard。 使用此设置的设备必须至少在 Windows 10（版本 1511）上运行。

  - “未配置”选项将策略设置保留为未定义状态。 组策略不会将策略设置写到注册表，所以它不会对计算机或用户造成影响。 如果注册表中存在当前设置，它将不会被修改。

### <a name="synchronize-and-deploy-sparsely-bundled-windows-store-for-business-apps---1222672---"></a>同步和部署稀疏捆绑的适用于企业的 Windows Store 应用 <!--1222672 -->
从适用于企业的 Windows Store 购买的脱机应用将同步至 Intune 门户。 然后，可以将这些应用部署到设备组或用户组。 脱机应用由 Intune 安装，而不是由应用商店安装。

### <a name="reset-passwords-for-android-o-devices----1238299---"></a>重置 Android O 设备的密码 <!-- 1238299 -->
可以重置已注册的 Android O 设备的密码。 将“重置密码”请求发送到 Android O 设备时，它将针对当前用户设置新的设备解锁密码或托管的配置文件质询。 密码或质询是根据设备拥有配置文件所有者还是设备所有者发送的，并且会立即生效。

### <a name="local-device-security-option-settings----1251887---"></a>本地设备安全选项设置 <!-- 1251887 -->
可以使用新的“本地设备安全选项”设置在 Windows 10 设备上启用安全设置。 创建 Windows 10 设备配置策略时，可以在终结点保护类别中查找这些设置。

### <a name="new-printer-settings-for-education-profiles----1308900---"></a>教育配置文件的新打印机设置 <!-- 1308900 -->

对于教育配置文件，新的设置将提供在“打印机”类别下：“打印机”、“默认打印机”、“添加新的打印机”。 

### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>设备限制的新隐私设置 <!--1308926 -->

将为设备提供两个新的隐私设置：

- **发布用户活动**：将此设置为“阻止”以阻止任务切换程序中最近使用资源的共享体验和发现。

- **仅限本地活动**：将此设置为“阻止”以仅基于本地活动阻止任务切换程序中最近使用资源的共享体验和发现。

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>对使用设备注册管理器的注册的 macOS 公司门户支持 <!-- 1352411 -->

用户将能够在注册 macOS 公司门户时使用设备注册管理器。

#### <a name="new-settings-for-the-edge-browser---1469166---"></a>Microsoft Edge 浏览器的新设置 <!--1469166 -->

将为具有 Microsoft Edge 浏览器的设备提供两个新的设置：“到收藏夹文件的路径”和“对收藏夹的更改”。 

### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Windows 搜索结果中的 Windows 信息保护 (WIP) 加密数据 <!-- 1469193 -->

借助 Windows 信息保护 (WIP) 策略中的新设置，可以控制是否在 Windows 搜索结果中添加 WIP 加密数据。

### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>对 macOS 的业务线 (LOB) 应用支持 <!-- 1473977 -->
Intune 将提供安装 macOS LOB 应用的功能。 LOB 应用是在其中提供安装文件并使用 Intune 在设备上安装此应用的应用。 作为 macOS LOB 应用支持的一部分，必须使用 Microsoft Intune App Wrapping Tool for macOS 预处理 macOS 业务线 (LOB) 应用。

### <a name="configure-resource-account-settings-for-surface-hubs----1475674---"></a>为 Surface Hub 配置资源帐户设置 <!-- 1475674 -->

可以为 Surface Hub 远程配置资源帐户设置。

资源帐户由 Surface Hub 用于对 Skype/Exchange 进行身份验证，以便它可以加入会议。 需要创建一个唯一的资源帐户，以使 Surface Hub 可以作为会议室出现在会议中。 例如“会议室 B41/6233”等资源帐户。

> [!NOTE]
> - 如果将字段留空，则将替代之前在设备上配置的特性。
>
> - 资源帐户属性可以在 Surface Hub 上动态变化。 例如，在启用密码轮转的情况下。 所以，Azure 控制台中的值可能需要一些时间才能反映设备上的实际情况。 
>
>   若要了解 Surface Hub 上当前配置的内容，可以将资源帐户信息包括在硬件清单中（已有 7 天的间隔时间）或者作为只读属性包括。 若要在远程操作发生后增强准确性，可以在运行操作以更新 Surface Hub 上的帐户/参数后立即获取参数的状态。

### <a name="ios-app-provisioning-configuration----1581650---"></a>iOS 应用预配配置 <!-- 1581650 -->
可以分配 iOS 应用预配配置文件以通过包括或排除安全组来防止应用过期。

### <a name="new-windows-defender-exploit-guard-settings----631893---"></a>新 Windows Defender 攻击防护设置 <!-- 631893 -->

将提供六个新的“攻击面减少”设置和扩展的“受控文件夹访问权限: 文件夹保护”功能。 这些设置可以在 Device configuration\Profiles\
Create profile\Endpoint protection\Windows Defender Exploit Guard 中找到。

#### <a name="attack-surface-reduction"></a>攻击面减少

|设置名  |设置选项  |描述  |
|---------|---------|---------|
|高级勒索软件防护|启用、审核、未配置|使用激进的勒索软件防护。|
|标记从 Windows 本地安全机构子系统窃取的凭据|启用、审核、未配置|标记从 Windows 本地安全机构子系统 (lsass.exe) 窃取的凭据。|
|来自 PSExec 和 WMI 命令的进程创建|阻止、审核、未配置|阻止来自 PSExec 和 WMI 命令的进程创建。|
|从 USB 运行的不受信任和未签名的进程|阻止、审核、未配置|阻止从 USB 运行的不受信任和未签名的进程。|
|不符合普及程度、年龄或信任列表条件的可执行文件|阻止、审核、未配置|阻止可执行文件的运行，除非这些文件符合普及程度、年龄或信任列表条件。|

#### <a name="controlled-folder-access"></a>受控文件夹访问权限

|设置名  |设置选项  |描述  |
|---------|---------|---------|
|文件夹保护（已实现）|未配置、启用、仅审核（已实现）<br><br> **新建**<br>阻止磁盘修改、审核磁盘修改|
阻止不友好应用对文件和文件夹进行未经授权的更改。<br><br>**启用**：阻止不受信任的应用修改或删除受保护文件夹中的文件，以及阻止写入到磁盘扇区。<br><br>
**仅阻止磁盘修改**：<br>阻止不受信任的应用写入到磁盘扇区。 不受信任的应用仍可以修改或删除受保护文件夹中的文件。|

### <a name="new-windows-defender-application-guard-settings----1631890---"></a>新 Windows Defender 应用程序防护设置 <!-- 1631890 -->

- **启用图形加速**

管理员将可以为 Windows Defender 应用程序防护启用虚拟图形处理器。 此设置使 CPU 可以将图形呈现卸载到 vGPU。 这可以提升使用图形密集型网站或在容器中观看视频时的性能。

- **SaveFilestoHost**

管理员将可以使文件从在容器中运行的 Microsoft Edge 传递到主机文件系统。 打开此选项将使用户可以从容器中的 Microsoft Edge 将文件下载到主机文件系统。

### <a name="see-enrollment-restrictions-per-user----1634444---"></a>请参阅每个用户的注册限制 <!-- 1634444 -->
在疑难解答边栏选项卡上，可以看到对每个用户生效的注册限制。

### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>配置自我更新的移动 MSI 应用 <!-- 1740840 -->
可以配置已知的自我更新的移动 MSI 应用以忽略版本检查过程。 此功能有助于避免出现争用条件。 例如，在应用是由应用开发人员自动更新并且也由 Intune 更新时，可能会出现这种情况。 两者都可能在 Windows 客户端上尝试强制执行一个应用版本，这可能会产生冲突。

### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies---1704133---"></a>对适用于 Windows 10 及更高版本符合性策略的系统安全设置的添加<!--1704133 -->

将提供对 Windows 10 符合性设置的添加，包括需要防火墙和 Windows Defender 防病毒。

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>根据 Android Enterprise 组包括和排除应用分配 <!-- 1813081 -->
在应用分配期间以及选择分配类型后，Android Enterprise（以前称为 Android for Work）将支持排除功能。


### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Intune 中支持的应用许可证的相关集 <!-- 1864117 -->
Azure 门户中的 Intune 将支持应用许可证的相关集，以作为 UI 中的单个应用项。 此外，任何从适用于企业的 Microsoft Store 同步的脱机许可的应用都将合并到单个应用条目中，并且各个包中的任何部署详细信息都将迁移到单个条目中。 若要在 Azure 门户中查看应用许可证的相关集，请从“移动应用”边栏选项卡中选择“应用许可证”。

<!-- the following are present prior to 1802 -->

### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625---"></a>新增了 Apple 批量注册所需的用户身份验证选项 <!-- 747625 -->
对于以下注册方法，Intune 将支持使用“公司门户”应用验证设备：

- Apple 设备注册计划
- Apple School Manager
- Apple Configurator 注册

使用“公司门户”选项时，可以强制执行 Azure Active Directory 多重身份验证，而不会屏蔽这些注册方法。

使用“公司门户”选项时，Intune 会跳过 iOS 设置助理中用于用户关联注册的用户身份验证。 也就是说，设备最初注册为无用户设备，因此不会接收用户组的配置或策略， 只会接收设备组的配置和策略。 不过，Intune 会在设备上自动安装“公司门户”应用。 首个启动并登录“公司门户”应用的用户将与 Intune 中的设备相关联。 此时，用户将会接收用户组的配置和策略。 只有重新注册，才能更改用户关联。

### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Intune 支持多个 Apple DEP/Apple School Manager 帐户 <!-- 747685 -->
Intune 将支持最多通过 100 个不同的 Apple 设备注册计划 (DEP) 或 Apple School Manager 帐户注册设备。 可以单独管理注册配置文件和设备的每个已上传令牌。 可以根据已上传的 DEP/ School Manager 令牌自动分配不同的注册配置文件。 如果上传了多个 School Manager 令牌，一次只能与 Microsoft 学校数据同步共享一个令牌。

迁移后，通过 Graph 管理 Apple DEP 或 ASM 的 beta 版本 Graph API 和已发布脚本将不再有效。 新的 beta 版本 Graph API 正在进行开发，将在迁移后发布。

### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>将符合性策略定目标到设备组中的设备 <!--1307012 -->

将可以把符合性策略定目标到用户组中的用户。 将可以把符合性策略定目标到设备组中的设备。

### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Windows 搜索结果中的 Windows 信息保护 (WIP) 加密数据 <!-- 1469193 -->

借助 Windows 信息保护 (WIP) 策略中的新设置，可以控制是否在 Windows 搜索结果中添加 WIP 加密数据。

### <a name="remote-printing-over-a-secure-network----1709994----"></a>通过安全网络远程打印 <!-- 1709994  -->
使用 PrinterOn 的无线移动打印解决方案，用户将可以随时随地通过安全网络进行远程打印。 PrinterOn 将集成适用于 iOS 和 Android 的 Intune APP SDK。 将可以通过管理控制台中的 Intune“应用保护策略”边栏选项卡，将应用保护策略定目标到此应用。 最终用户将能够通过 Play 商店或 iTunes 下载“PrinterOn for Microsoft”应用，以便在 Intune 生态系统内使用。



### <a name="microsoft-graph-api-for-intune---general-availability-----1833289---"></a>适用于 Intune 的 Microsoft Graph API - 正式版本 <!-- 1833289 -->
借助 Microsoft Graph 中的 Intune API，将可以编程方式访问数据和方法，从而自动执行 Intune 服务的管理操作。  通过这些 API 的正式版本，客户、合作伙伴和开发人员将能够利用这些 API 与内部或商业解决方案集成，这些解决方案需要 Intune 支持或其他通过 Microsoft Graph 提供的 Microsoft 服务支持，或与之相关。

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>应用保护策略<!-- 679615 -->
Intune 应用保护策略将提供创建默认全局策略的功能，以便快速对整个租户中所有用户启用保护。

### <a name="new-ios-device-action------1244701---"></a>新的 iOS 设备操作<!-- 1244701 -->
你可以关闭 iOS 10.3 监督的设备。 此操作会立即关闭设备，而不会向最终用户发出警告。 当你在“设备”工作负载中选择设备时，可以在设备属性中找到“关闭（仅监督）”操作。

### <a name="intune-provides-the-account-move-operation-----1573558-1579830---"></a>Intune 提供“帐户移动”操作 <!-- 1573558, 1579830 -->
“帐户移动”将租户从一个 Azure 扩展单元 (ASU) 迁移到另一个。 “帐户移动”可用于两种由客户启动的情景，当你调用请求它的 Intune 支持团队时，也可以是 Microsoft 驱动的情景，其中 Microsoft 需要对后端服务进行调整。 在“帐户移动”期间，租户进入只读模式 (ROM)。 在 ROM 期间，注册、重命名设备、更新符合性状态等服务操作将失败。

对于某个应用被分配到多个组（具有不同应用意向）的情况，这项更改有助于避免混淆。

如果希望在 11 月服务发布前，在信息工作者门户和公司门户中使用应用，你有两个选择：

1. 删除组的“不适用”分配。
2. 创建一个新组，该组不包括已分配“必需和可用”意向的成员，然后将该组分配为“不适用”。

有关详细信息，请参阅[如何使用 Microsoft Intune 将应用分配到组](apps-deploy.md)。

> [!Note]
> 发布后，无法在 Intune 经典控制台中查看或修改移动设备管理 (MDM) 应用分配。 但是，可使用 Azure 控制台或 Intune 图形 API 分配应用。

### <a name="configure-an-ios-app-pin----1586774---"></a>配置 iOS 应用 PIN <!-- 1586774 -->
很快，便能要求目标 iOS 应用使用 PIN。 几天后，还可通过 Azure 门户配置 PIN 需求和到期日期。 需要时，用户必须设置并使用新的 PIN 才有权访问 iOS 应用。 只有使用 Intune App SDK 启用应用保护的 iOS 应用才支持此功能。

### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866--"></a>iOS 版公司门户应用的用户体验更新<!--1412866-->

我们将向 iOS 版公司门户应用发布用户体验主要更新。 此更新具有经过完全重新设计的视觉效果，包括现代化的外观和经提升的可用性和可访问性感受。 iOS 公司门户当前的所有功能都将保留。

我们将通过 Apple TestFlight 计划推出更新版 iOS 公司门户应用的预发布版本，用户可以使用并提供反馈。 若想参与 TestFlight，请在 https://aka.ms/intune_ios_cp_testflight 注册。 

![新 iOS 公司门户应用的预告图像](./media/ios-cp-app-redesign-1801-teaser.png)

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory 网站可能需要 Intune Managed Browser 应用，并且支持 Managed Browser（公共预览版）的单一登录<!-- 710595 -->   
利用 Azure Active Directory (Azure AD)，可在移动设备上将对网站的访问限于 Intune Managed Browser 应用。 在 Managed Browser 中，网站数据可保持安全并且独立于最终用户的个人数据。 此外，Managed Browser 支持受 Azure AD 保护的站点的单一登录功能。 通过登录 Managed Browser，或在设备上将 Managed Browser 与由 Intune 管理的其他应用配合使用，用户无需输入凭据，Managed Browser 即可访问受 Azure AD 保护的公司站点。 此功能适用于 Outlook Web Access (OWA) 和 SharePoint Online 等站点，以及通过 Azure 应用代理访问的 Intranet 资源等其他公司站点。

<!-- the following are present prior to 1709 -->
### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Intune 应用保护和 Citrix MDX 开发工具 <!-- 709185 -->
可以同时使用 Citrix XenMobile MDX 和 Microsoft Intune 来管理设备和应用。 通过使用此方法，可在使用 Citrix mVPN 技术的同时通过 Intune 应用保护策略管理应用。

能够查找包含适用于iOS 和 Android 的 App Wrapping Tool 和 Intune App SDK 的代码存储库，同时还能集成 Citrix MDX mVPN 技术。

<!-- the following are present prior to 1711 -->

### <a name="redirecting-macos-users-to-the-new-company-portal-app---1380728--"></a>将 macOS 用户重定向到新公司门户应用 <!--1380728-->   
当最终用户登录公司门户网站注册其 macOS 设备时，系统会将其定向到下载 macOS 版新公司门户应用的页面，以便完成此过程。 使用 OS X El Capitan 10.11 或更高版本的 macOS 设备会出现这种情况。 

<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>iOS 和 Android 的 Intune Managed Browser 支持<!-- 1374196 -->
自 2017 年 10 月起，Android 版 Intune Managed Browser 应用将仅支持运行 Android 4.4 及更高版本的设备。 iOS 上的 Intune Managed Browser 应用将仅支持运行 iOS 9.0 及更高版本的设备。 早期版本的 Android 和 iOS 将能够继续使用 Managed Browser，但不能安装新版本的应用，并且可能无法访问所有应用功能。 建议将这些设备更新为受支持的操作系统版本。

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>改进了用户达到允许注册的最大设备数时提示的错误消息 <!-- 1270370 -->
使用 Android 设备的最终用户将不再看到通用错误消息，而将看到下面可操作的友好错误消息：“注册设备数已达到 IT 管理员允许的数量上限。请删除已注册的设备，或者向 IT 管理员寻求帮助。”



## <a name="notices"></a>通知

此时没有任何活动通知。



### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。


