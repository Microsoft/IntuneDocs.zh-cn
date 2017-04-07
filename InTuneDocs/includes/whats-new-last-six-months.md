# <a name="february-2017"></a>2017 年 2 月

## <a name="new-capabilities"></a>新功能

### <a name="modernizing-the-company-portal-website---753980--"></a>公司门户网站现代化<!--753980-->
公司门户网站将支持面向不具有托管设备的用户的应用。 此网站将使用新的撞色配色方案、动态图和“汉堡菜单”（![汉堡菜单的小图，该图片现已添加到公司门户网站左上角](/intune/whats-new/media/CP_hamburger_menu.png)，它包括了支持人员详细联系信息和现有托管设备的信息），这与 Microsoft 其他产品和服务保持一致。 将重新排列登录页，强调可供用户使用的应用，登录页上具有针对特色应用和最近更新应用的传送。 可在 [UI 更新页](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui)上查看提供的最初和最后的图像。

## <a name="notices"></a>通知

### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>iOS 设备的组迁移将不需要对组或策略进行任何更新<!--898837-->
对于所有由公司设备注册配置文件预分配的 Intune 设备组，在迁移到 Azure Active Directory 设备组期间，都将根据公司设备注册配置文件的名称在 AAD 中创建相应的动态设备组。 这样可以确保设备在注册时自动进行分组，并接收与原始 Intune 组相同的策略和应用。

租户进入分组和设定目标的迁移阶段时，Intune 将自动创建一个动态 AAD 组，该组与公司设备注册配置文件面向的 Intune 组相对应。 Intune 管理员删除目标 Intune 组时，相应的动态 AAD 组不会被删除。 组成员和动态查询将被清除，但该组本身将继续保留，直到 IT 管理员通过 AAD 门户将其删除。

同样，如果 IT 管理员更改了公司设备注册配置文件面向的 Intune 组，Intune 将创建新的动态组来反映新的配置文件分配，但不会删除为旧分配创建的动态组。

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>默认通过 Windows 设置管理 Windows 桌面设备<!--663050-->
用于注册 Windows 10 桌面版的默认行为发生了变化。 新的注册将遵循典型 MDM 代理注册流程，而非通过电脑代理进行。 公司门户网站将为 Windows 10 桌面用户提供注册说明，指导他们完成将 Windows 10 桌面计算机添加为移动设备的过程。 这不会影响当前已注册的电脑，[如果愿意](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune)，组织仍可使用电脑代理来管理 Windows 10 桌面。

### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>改进对选择性擦除的移动应用管理支持<!--581242-->
如果由于“擦除应用数据前的脱机时间间隔”策略导致自动删除了工作或学校数据，则将为最终用户提供有关如何重新获得这些数据的访问权限的其他指导。<!--, or the removal of the Intune Company Portal on Android.-->

### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>iOS 版公司门户链接在应用内打开<!--665954-->
iOS 版公司门户应用内的链接（包括文档和应用链接）将通过 Safari 的应用内视图直接在公司门户应用中打开。 此更新将与 1 月的服务更新分开提供。

### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Windows 设备的新 MDM 服务器地址<!--893007-->
Windows 和 Windows Phone 用户如果输入 __manage.microsoft.com__ 作为 MDM 服务器地址（出现提示时），尝试注册设备时将失败。 MDM 服务器地址已从 __manage.microsoft.com__ 更改为 __enrollment.manage.microsoft.com__。 通知用户在注册 Windows 和/或 Windows Phone 时，如果出现提示，请使用 __enrollment.manage.microsoft.com__ 作为 MDM 服务器地址。 无需更改 CNAME 设置。 有关此更改的详细信息，请访问[aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange)。

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Android 适用的公司门户应用的最新用户体验<!--621622-->
从 3 月开始，Android 适用的公司门户应用将按照[材料设计指南](https://material.io/guidelines/material-design/introduction.html)来打造更具现代感的外观。 这将改善以下用户体验：

* __颜色__：可以根据自定义调色板对选项卡标头着色。
* __界面__：“应用”选项卡上已更新了“特色应用”和“所有应用”按钮。 “搜索”按钮现在是浮动的操作按钮。
* __导航__：“所有应用”以选项卡形式呈现出“特色”、“所有”和“分类”视图，便于导航。
* __服务__：“我的设备”和“联系 IT”选项卡提高了可读性。

可在 [UI 更新页](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui)上查看最初和最后的图像。

### <a name="associate-multiple-management-tools-with-the-windows-store-for-business---926135--"></a>将多个管理工具与适用于企业的 Windows 应用商店关联<!--926135-->
使用多个管理工具部署适用于企业的 Windows 应用商店时，以前只能将一个管理工具与适用于企业的 Windows 应用商店相关联。 现在可以将多个管理工具与应用商店相关联，例如 Intune 和 Configuration Manager。 有关详细信息，请参阅[使用 Microsoft Intune 管理从适用于企业的 Windows 应用商店中购买的应用](https://docs.microsoft.com/en-us/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune#associate-your-windows-store-for-business-account-with-intune)。

## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Azure 上的 Intune 管理体验公开预览版的新增功能<!--736542-->

在 2017 年初，我们会将完整管理体验迁移到 Azure 上，以便能够在可使用图形 API 进行扩展的新式服务平台上对核心 EMS 工作流进行强大且集成的管理。

新的试用租户将于本月开始在 Azure 门户中看到新管理体验的公开预览版。 在预览状态下，将以迭代方式交付现有 Intune 控制台的功能和奇偶校验。

Azure 门户中的管理体验将使用已公布的新分组和定向功能；当现有租户迁移到新的分组体验时，也会将你迁移，以预览租户上的新管理体验。 在此期间，如果想要在租户迁移之前测试或查看任何新功能，请注册新的 Intune 试用帐户或查阅[新文档](https://docs.microsoft.com/intune-azure/introduction/whats-new)。

在[此处](https://docs.microsoft.com/intune-azure/introduction/whats-new)可找到 Azure 中 Intune 预览版的新增功能。

## <a name="january-2017"></a>2017 年 1 月

### <a name="new-capabilities"></a>新功能

#### <a name="in-console-reports-for-mam-without-enrollment---677961--"></a>无需注册的 MAM 控制台内报表<!--677961-->
已为已注册设备和未注册设备添加了新的应用保护报表。 详细了解如何[使用 Intune 监视移动应用管理策略](https://docs.microsoft.com/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune)。

#### <a name="android-711-support---694397--"></a>Android 7.1.1 支持<!--694397-->
Intune 现在完全支持并可管理 Android 7.1.1。

#### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them---unknown--"></a>解决 iOS 设备处于非活动状态，或管理控制台不能与其通信的问题 <!--unknown-->
如果用户的设备失去与 Intune 的联系，可向其提供新的故障排除步骤，帮助他们重新获得公司资源的访问权限。 请参阅[设备处于非活动状态，或管理控制台不能与其通信](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them)。

### <a name="notices"></a>通知

#### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>默认通过 Windows 设置管理 Windows 桌面设备<!--663050-->
用于注册 Windows 10 桌面版的默认行为发生了变化。 新的注册将遵循典型 MDM 代理注册流程，而非通过电脑代理进行。

公司门户网站将为 Windows 10 桌面用户提供注册说明，指导他们完成将 Windows 10 桌面计算机添加为移动设备的过程。 这不会影响当前已注册的电脑，[如果愿意](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune)，组织仍可使用电脑代理来管理 Windows 10 桌面。

#### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>改进对选择性擦除的移动应用管理支持<!--581242-->
如果由于“擦除应用数据前的脱机时间间隔”策略导致自动删除了工作或学校数据，则将为最终用户提供有关如何重新获得这些数据的访问权限的其他指导。<!--, or the removal of the Intune Company Portal on Android.-->

#### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>iOS 版公司门户链接在应用内打开<!--665954-->
iOS 版公司门户应用内的链接（包括文档和应用链接）将通过 Safari 的应用内视图直接在公司门户应用中打开。 此更新将与 1 月的服务更新分开提供。

#### <a name="modernizing-the-company-portal-website---753980--"></a>公司门户网站现代化<!--753980-->
从 2 月开始，公司门户网站将支持针对不具有托管设备的用户的应用。 此网站将使用新的撞色配色方案、动态图和“汉堡菜单”（即![公司门户网站汉堡菜单](/Intune/whats-new/media/CP_hamburger_menu.png)，包括支持人员详细联系信息和现有托管设备的信息），这与 Microsoft 其他产品和服务保持一致。 将重新排列登录页，强调可供用户使用的应用，登录页上具有针对特色应用和最近更新应用的传送。 可在 [Intune 应用 UI 的新增功能](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui)页面中查看更改前和更改后的图片。

#### <a name="new-documentation-for-app-protection-policies---583398--"></a>新的应用保护策略文档<!--583398-->
针对想要使用 Intune 应用包装工具或 Intune App SDK 在 iOS 和 Android 应用中启用应用保护策略（称为 MAM 策略）的管理员和应用开发人员，我们更新了相关文档。

已更新以下文章：

* [决定如何使用 Microsoft Intune 为移动应用程序管理准备应用](https://docs.microsoft.com/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)
* [使用 Intune 应用包装工具为移动应用程序管理准备 iOS 应用](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)
* [Microsoft Intune App SDK 入门](https://docs.microsoft.com/intune/develop/intune-app-sdk-get-started)
* [Intune App SDK for iOS 开发人员指南](https://docs.microsoft.com/intune/develop/intune-app-sdk-ios)

以下文章是对文档库新增的内容：

* [Intune App SDK Cordova 插件](https://docs.microsoft.com/intune/develop/intune-app-sdk-cordova)
* [Intune App SDK Xamarin 组件](https://docs.microsoft.com/intune/develop/intune-app-sdk-xamarin)

#### <a name="progress-bar-when-launching-the-company-portal-on-ios---665978--"></a>在 iOS 上启动公司门户时的进度栏<!--665978-->
IOS 版公司门户在启动屏幕上引入了一个进度栏，为用户提供所发生的加载进程的信息。 进度栏将逐步推出，以替代旋转图标。 这意味着某些用户将看到新的进度栏，而其他用户会继续看到旋转图标。

## <a name="december-2016"></a>2016 年 12 月

### <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Azure 上新的 Intune 管理体验公开预览版<!--736542-->
在 2017 年初，我们会将完整管理体验迁移到 Azure 上，以便能够在可使用图形 API 进行扩展的新式服务平台上对核心 EMS 工作流进行强大且集成的管理。 在正式发布此面向所有 Intune 租户的门户之前，我们高兴地宣布将在本月晚些时候向所选租户推出此新的管理体验的预览版。

Azure 门户中的管理体验将使用已公布的新分组和定向功能；当现有租户迁移到新的分组体验时，也会将你迁移，以预览租户上的新管理体验。 同时，在[新文档](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune)中查找应用商店提供的用于 Azure 门户中的 Microsoft Intune 的应用的更多信息。

__Azure 门户公开预览版中的电信费用管理集成__ <!--747605--> 现在，我们将开始在 Azure 门户中预览与第三方电信费用管理 (TEM) 服务的集成。 可以使用 Intune 强制实施对国内和漫游数据使用的限制。 我们将使用 [Saaswedo](http://www.saaswedo.com) 开始这些集成。 若要在试用租户中启用此功能，请[联系 Microsoft 支持](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)。

### <a name="new-capabilities"></a>新功能

__跨所有平台的多重身份验证__ <!--747590--> 现在，通过在 Azure Active Directory 中的 Microsoft Intune 注册应用程序上配置 MFA，可在所选用户组从 Azure 管理门户注册 iOS、Android、Windows 8.1+ 或 Windows Phone 8.1+ 设备时，对其强制执行多重身份验证 (MFA) 。

__能够限制移动设备注册__ <!--747596--> Intune 新增了注册限制，可控制允许注册的移动设备平台。 Intune 将移动设备平台分为 iOS、macOS，Android、Windows 和 Windows Mobile。
* 限制移动设备注册不会限制电脑客户端注册。
* 阻止个人自有设备的注册有一个附加选项，该选项仅适用于 iOS。

Intune 将所有新设备都标记为个人所有，除非 IT 管理员将设备标记为公司所有，如[本文](https://docs.microsoft.com/en-us/intune/deploy-use/manage-corporate-owned-devices)所述。

### <a name="notices"></a>通知

__注册的多重身份验证移动到 Azure 门户__ <!--VSO 750545--> 以前，管理员会进入 Intune 控制台或 Configuration Manager（2016 年 10 月之前的版本）控制台，为 Intune 注册设置 MFA。 通过此更新的功能，现在可使用 Intune凭据登录 [Microsoft Azure 门户](https://manage.windowsazure.com)，并通过 Azure AD 配置 MFA 设置。 在[此处](https://aka.ms/mfa_ad)了解详细信息。

__Android 版公司门户应用现已在中国推出__  <!--VSO 658093--> 我们将发布 Android 版公司门户应用，以供中国地区下载。 由于中国地区没有 Google Play 商店，Android 设备必须从中国的应用市场获取应用。 可在以下应用商店下载用于 Android 的公司门户应用：
* [百度](https://go.microsoft.com/fwlink/?linkid=836946)
* [华为](https://go.microsoft.com/fwlink/?linkid=836948)
* [腾讯](https://go.microsoft.com/fwlink/?linkid=836949)
* [豌豆荚](https://go.microsoft.com/fwlink/?linkid=836950)
* [小米](https://go.microsoft.com/fwlink/?linkid=836947)

Android 版公司门户应用使用 Google Play Services 与 Microsoft Intune 服务进行通信。 由于 Google Play Services 尚未在中国推出，因此执行以下任何任务最高可能需要 8 个小时才能完成。 

|Intune 管理控制台| Android 适用的 Intune 公司门户应用 |Intune 公司门户网站|   
|---|---|---|
|完全擦除| 移除远程设备| 移除设备（本地和远程）|
|“选择性擦除”| 重置设备| 重置设备|
|新的或更新的应用部署| 安装可用的业务线应用| 设备密码重置|
|远程锁定|||
|密码重置|||

### <a name="deprecations"></a>弃用功能

__Firefox 不再支持 Silverlight__ <!--VSO TBA--> Mozilla 将在 52 版 [Firefox 浏览器](https://www.mozilla.org/firefox)中移除对 Silverlight 的支持，此更新于 2017 年 3 月生效。 因此，无法使用高于 51 版的 Firefox 登录现有 Intune 控制台。 我们建议使用 Internet Explorer 10 或 11，或者 [52 版之前的 Firefox](https://ftp.mozilla.org/pub/firefox/releases/) 访问管理控制台。 Intune 向 Azure 门户的过渡允许其支持多种[新式浏览器](https://docs.microsoft.com/en-us/azure/azure-preview-portal-supported-browsers-devices)，而无需依赖于 Silverlight。

__删除 Exchange Online 移动版收件箱策略__ <!--770687--> 从 12 月开始，管理员将无法继续在 Intune 控制台中查看或配置 Exchange Online (EAS) 移动版邮箱策略。 此更改将在 12 月和 1 月向所有 Intune 租户推出。 所有现有策略将保持配置状态；若要配置新策略，请使用 Exchange 命令行管理程序。 可在[此处](https://technet.microsoft.com/en-us/library/bb123783%28v=exchg.150%29.aspx)找到详细信息。

__Android 不再支持 Intune AV 播放器、图像查看器和 PDF 查看器应用__ <!--747553--> 从 2016 年 12 月中旬起，用户将无法继续使用 Intune AV 播放器、图像查看器和 PDF 查看器应用。 这些应用已替换为 Azure 信息保护应用。 可在[此处](https://docs.microsoft.com/information-protection/rms-client/mobile-app-faq)查找有关 Azure 信息保护应用的详细信息。

## <a name="november-2016"></a>2016 年 11 月

### <a name="new-capabilities"></a>新功能

__适用于 Windows 10 设备的新 Microsoft Intune 公司门户__ Microsoft 将发布[适用于 Windows 10 设备的新 Microsoft Intune 公司门户](https://www.microsoft.com/store/apps/9wzdncrfj3pz)。 此应用利用了新 Windows 10 Universal 格式，将在应用内为用户提供更新的用户体验，且跨所有 Windows 10 设备（PC 和移动设备等）提供相同的体验，同时还将保持现有的一切功能。

新应用还允许用户们在 Windows 10 设备上利用传统平台功能，例如单一登录 (SSO) 和基于证书的身份验证。 此应用将作为对现有 Windows 8.1 公司门户和 Windows Phone 8.1 公司门户（安装自 Windows 应用商店）的升级而提供。 有关详细信息，请转到 [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp)。

> [!IMPORTANT]
> __Intune 和 Android for Work 上的更新__虽然可通过“必需”操作部署 Android for Work 应用，但如果已将 Intune 组迁移至新的 Azure AD 组体验，则只可以将应用部署为“可用”。

__Intune App SDK for Cordova 插件现在支持 MAM（无需注册设备）__应用开发人员现在可以使用 Intune App SDK for Cordova 插件启用 MAM 功能，且无需在适用于 Android 和 iOS 的基于 Cordova 的应用中注册设备。 可在[此处](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)找到 Intune App SDK for Cordova 插件。

__Intune App SDK Xamarin 组件现在支持 MAM（无需注册设备）__应用开发人员现在可以使用 Intune App SDK Xamarin 组件启用 MAM 功能，且无需在适用于 Android 和 iOS 的基于 Xamarin 的应用中注册设备。 可在[此处](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)找到 Intune App SDK Xamarin 组件。

### <a name="notices"></a>通知

__上传 Symantec 签名证书不再需要已签名的 Windows Phone 8 公司门户__上传 Symantec 签名证书不再需要已签名的 Windows Phone 8 公司门户应用。 可以独立上传该证书。

###<a name="deprecations"></a>弃用功能

__对 Windows Phone 8 公司门户的支持__将取消对 Windows Phone 8 公司门户的支持。 2016 年 10 月弃用了对 Windows Phone 8 和 WinRT 平台的支持。 2016 年 10 月弃用了对 Windows 8 公司门户的支持。

## <a name="october-2016"></a>2016 年 10 月

### <a name="conditional-access-for-mobile-application-management"></a>用于移动应用程序管理的条件访问
你将能够限制对 Exchange Online 的访问，以便访问只能来自支持 Intune 移动应用程序管理策略的应用（如 Outlook）。 [这一新功能](/intune/deploy-use/allow-policy-managed-apps-access-to-o365)与 Intune 移动应用管理 (MAM) 策略实现完美配对，因为你可以阻止对内置邮件客户端或其他未配置 Intune MAM 策略的应用的访问。 这可确保用户使用可通过 Intune MAM 进行保护的应用访问组织数据。 你可以通过 Azure 门户开始使用 Intune 移动应用管理。 在“设置”边栏选项卡中查找新的“条件访问”分区。

### <a name="conditional-access-for-windows-pcs"></a>Windows 电脑的条件访问
现在可通过 Intune 管理控制台创建条件访问策略，阻止 Windows 电脑访问 [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) 和 [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)。 还可以创建条件访问策略，阻止访问 Office 桌面和通用应用程序。

### <a name="android-for-work-support"></a>Android for Work 支持

> [!IMPORTANT]

> 虽然可通过“必需”操作部署 Android for Work 应用，但如果已将 Intune 组迁移至新的 Azure AD 组体验，则只可以将应用部署为“可用”。

目前 Intune 是 Android for Work (AfW) 计划的一部分。 从本月起到接下来的几个月，我们将提供对 AfW 功能的支持。 请注意，AfW 的可用应用部署利用新的分组和目标设定体验。 新预配的 Intune 服务帐户在 AfW 对它们可用后就可使用此功能。

[阅读 Microsoft 关于针对 Android for Work 的 Intune 支持公告](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/12/microsoft-intune-support-for-android-for-work/)。

以下 Intune 主题是新主题或使用 Android for Work 信息进行了更新：

对于 IT 专业人员：
- [设置 Android for Work](/intune/deploy-use/set-up-android-for-work)
- [使用 Intune 限制对 Exchange Online 和新版 Exchange Online Dedicated 的电子邮件访问](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
- [使用 Intune 限制对 Exchange 内部部署和旧版 Exchange Online Dedicated 的电子邮件访问](/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
- [Android for Work 合规性策略设置](/intune/deploy-use/afw-compliance-policy-settings-in-microsoft-intune)
- [如何部署 Android for Work 应用](/intune/deploy-use/android-for-work-apps)
- [使用移动应用配置策略配置 Android for Work 应用](/intune/deploy-use/afw-app-configuration-policy)
- [Android for Work 策略设置](/intune/deploy-use/android-for-work-policy-settings-in-microsoft-intune)

对于最终用户：
- [创建工作配置文件时会发生的情况](/intune/enduser/what-happens-when-you-create-a-work-profile-android)
- [创建工作配置文件并在 Intune 中注册设备](/intune/enduser/create-a-work-profile-and-enroll-your-device-in-intune-android)

### <a name="lookout-integration-to-protect-ios-devices"></a>集成 Lookout 以保护 iOS 设备
在 10 月，Microsoft 将与 Lookout 的移动威胁防护解决方案集成，以通过检测设备上的恶意软件、危险应用等来保护 iOS 移动设备。 Lookout 的解决方案有助于确定威胁级别，可对该功能进行配置。 可以在 Intune 中创建合规性策略规则，以根据 Lookout 的风险评估来确定设备合规性。 使用条件访问策略，你可以基于设备合规性状态允许或阻止访问公司资源。

将提示不合规 iOS 设备的最终用户进行注册，并要求其在设备上安装 Lookout for Work 应用，激活该应用并修正 Lookout for Work 应用程序中报告的威胁，以便获得对公司数据的访问权限。 了解如何[配置并部署 Lookout for Work 应用](/intune/deploy-use/configure-and-deploy-lookout-for-work-apps)。
<!--TFS 1319493-->

### <a name="intune-app-wrapping-tool-for-android"></a>Intune App Wrapping Tool for Android
可以利用 Intune App Wrapping Tool，使应用能够使用 Intune 移动应用程序管理 (MAM) 策略。 现在可支持 MAM 策略，且无需设备注册。

### <a name="manage-printing-from-apps-managed-using-mam-policies"></a>从使用 MAM 策略管理的应用中管理打印
现可阻止打印来自使用了 MAM 策略的应用中的公司数据。 可在 [Azure 门户](/Intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)中使用此设置，且 [iOS](/Intune/deploy-use/ios-mam-policy-settings) 和 [Android](/Intune/deploy-use/android-mam-policy-settings) 设备均支持此设置。
<!--TFS 1014328-->

### <a name="support-for-fingerprints-on-android-devices"></a>Android 设备上支持使用指纹
Android 移动应用管理 (MAM) 策略现在允许用户使用指纹（而不是键入 PIN）访问应用。 在此查看此设置和其他[适用于 Android 的移动应用管理策略设置](/Intune/deploy-use/android-mam-policy-settings)。

### <a name="notices"></a>通知

__Android Samsung KNOX 与 Intune 的兼容性__ Samsung Galaxy Ace 手机的某些型号无法作为 Samsung KNOX 设备通过 Intune 进行管理。 当你使用 Intune 注册这些设备时，它们将被视为标准 Android 设备来进行管理。

受影响的型号包括：

* SM-G313HU
* SM-G313HY
* SM-G313M
* SM-G313MY
* SM-G313U

你和最终用户无需采取进一步的操作。 有关详细信息，请访问 [Samsung KNOX](https://www.samsungknox.com) 网站。

__适用于 Windows 8 的公司门户应用已弃用；将终止对 Windows Phone 8 和 Windows RT 平台的支持__ 从 2016 年 10 月开始，Microsoft Intune 将终止对 Windows 8 公司门户的支持。 另外，Microsoft Intune 还将终止对 Windows Phone 8 和 Windows RT 平台的支持。 因此，将无法注册或更新任何 Windows Phone 8 或 Windows RT 设备。

可以继续管理已注册的 Windows Phone 8、Windows RT 和 Windows 8 设备。 将 Windows Phone 8 和 Windows 8 设备更新到 Windows 8.1 和 Windows Phone 8.1，并使用相应的 Windows 8.1 和 Windows Phone 8.1 公司门户应用在不中断的情况下继续向这些设备分发应用。

从 2016 年 11 月开始，我们将终止对 Windows Phone 8 公司门户的支持。
<!--TFS 1255391-->

### <a name="whats-coming"></a>即将推出

__可用于 Windows 10 设备的新 Microsoft Intune 公司门户__ Microsoft 将发布适用于 Windows 10 设备的新 Microsoft Intune 公司门户。 此应用利用了新 Windows 10 Universal 格式，将在应用内为用户提供更新的用户体验，且跨所有 Windows 10 设备（PC 和移动设备等）提供相同的体验，同时还将保持现有的一切功能。

新应用还允许用户们在 Windows 10 设备上利用传统平台功能，例如单一登录 (SSO) 和基于证书的身份验证。 此应用将作为对现有 Windows 8.1 公司门户和 Windows Phone 8.1 公司门户（安装自 Windows 应用商店）的升级而提供。 有关详细信息，请转到 [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp)。
<!--TFS 1016502-->

## <a name="september-2016"></a>2016 年 9 月
### <a name="new-features-announcements-and-information"></a>新增功能、公告和信息
* [Windows 条件访问](#windows-conditional-access)
* [iOS 10 支持](#ios-10-support)
* [支持 MAM，且无需进行设备注册（针对 Android 和 iOS）](#app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios)
* [Intune 组将于 9 月过渡到 Azure Active Directory](#intune-groups-begin-transitioning-to-azure-active-directory-in-september)
* [集成 Lookout 以保护 Android 设备](#lookout-integration-to-protect-android-devices)
* [Android、iOS 和 Windows 公司门户更新](#company-portal-updates)
* [Intune 术语表](#intune-glossary)
* [即将推出](#whats-coming)

### <a name="windows-conditional-access"></a>Windows 条件访问
现在可通过 Intune 管理控制台创建条件访问策略，阻止 Windows 电脑访问 Exchange Online 和 SharePoint Oline。 还可以创建条件访问策略，阻止访问 Office 桌面和通用应用程序。

### <a name="ios-10-support"></a>iOS 10 支持
现有的 Intune MDM 和 MAM 方案与 iOS 10 兼容。 有关提示，请参阅 [Intune Support Team Blog](https://blogs.technet.microsoft.com/intunesupport/2016/09/13/support-tip-intune-support-for-ios-10/)（Intune 支持团队博客）。

### <a name="app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios"></a>App Wrapping Tool 支持 MAM，且无需进行设备注册（针对 Android 和 iOS）
Intune App Wrapping Tool 是一种命令行工具，用于在适用于 iOS 和 Android 的业务线 (LOB) 应用上启用 Intune MAM。 借助该工具，能够以最简单的方法将 Intune MAM SDK 整合到应用中，以便应用可执行通过 Intune 部署的 MAM 策略。 使用 MAM 策略，可以：

1. 加密应用数据。
2. 要求信息工作者在启动应用时输入 PIN。
3. 允许应用仅将数据传输到其他托管应用。
4. 防止应用将数据备份到 Android、iTunes 和 iCloud。
5. 仅允许剪切、复制和粘贴到其他托管应用，以及剪切、复制和粘贴自其他托管应用。

已更新的 Intune App Wrapping Tool 的公共预览版现支持 MAM，且无需在 Android 和 iOS 上对内部 LOB 应用进行设备注册。 这意味着最终用户不需要让其设备注册 Intune，便可使用启用了 MAM 的 LOB 应用。

任何人都可以测试该公共预览版软件，并参阅帮助文档，该文档位于 msintuneappsdk 的 GitHub：

<p style="margin-left: 40px">http://www.github.com/msintuneappsdk/intune-app-wrapper-ios-preview

<p style="margin-left: 40px">http://www.github.com/msintuneappsdk/intune-app-wrapper-android-preview

安装和使用适用于 Android 和 iOS 预发行版的 Microsoft Intune 应用包装之前，必须：

* 查看适用于 Android 和 iOS 预发行版的 Microsoft Intune App Wrapping Tool 的 Microsoft 许可条款
* 打印并保留一份许可条款，以留作记录。 下载和使用适用于 Android 预发行版的 Microsoft Intune App Wrapping Tool 表示你同意这些许可条款。 如果不接受这些条款，请不要使用此软件。
<!---TFS 1235607--->

### <a name="intune-groups-begin-transitioning-to-azure-active-directory-in-september"></a>Intune 组将于 9 月过渡到 Azure Active Directory
某些新的 Intune 帐户将使用 Azure Active Directory 安全组，而不是 Intune 用户组。 你将知道自己使用的是安全组，因为 Intune 门户组页上会有一个定向到 Azure 管理门户的链接。

### <a name="lookout-integration-to-protect-android-devices"></a>集成 Lookout 以保护 Android 设备
Microsoft 将与 Lookout 的移动威胁防护解决方案集成，以通过检测设备上的恶意软件、危险应用等来保护 Android 移动设备。 Lookout 的解决方案有助于确定威胁级别，可对该功能进行配置。 可以在 Intune 中创建合规性策略规则，以根据 Lookout 的风险评估来确定设备合规性。 使用条件访问策略，你可以基于设备合规性状态允许或阻止访问公司资源。

将提示非合规性设备的最终用户进行注册，并要求其在 Android 设备上安装 Lookout for Work 应用程序，激活该应用并修正 Lookout for Work 应用程序中报告的威胁，以便获得访问权限。 若要了解详细信息，请参阅[根据设备、网络和应用程序风险限制访问权限](https://docs.microsoft.com/en-us/intune/deploy-use/device-threat-protection)。


### <a name="company-portal-updates"></a>公司门户更新

__Android__

<p style="margin-left: 40px">**向 Android 公司门户添加“通知”**<br/>
<p style="margin-left: 40px">已将新的“通知”图标添加到 Android 公司门户的主页上。 点击此图标将访问“通知”页，该页将向你的最终用户显示在公司门户应用中需要注意的所有项，例如，设备非合规性、注册更新和注册激活。 iOS 公司门户应用已经有此通知体验。 拥有此新的“通知”页意味着，只要设备已注册，每次启动或恢复公司门户时，你将不会看到“公司访问设置”页。 如果你创建自己的最终用户指南，可能需要更新你的文档来反映此更改。 在[此处](https://aka.ms/androidcpupdate)查看更新的屏幕截图。  

__iOS__
<p style="margin-left: 40px">**iOS 公司门户应用的支持更改**<br/>
<p style="margin-left: 40px">现要求适用于 iOS 的 Microsoft Intune 公司门户应用的所有用户都使用最新版本。 新用户只能下载最新版本，而当前用户必须更新到最新版本。 最新版本需要 iOS 8.0 或更高版本，因此运行较旧的 iOS 版本的设备将无法使用公司门户或者进行注册，直到将其设备更新为 iOS 8.0 或更高版本，并且将公司门户应用更新到最新版本。 运行 iOS 8.0 以下版本的已注册设备将继续受管理，并将列在 Intune 管理员控制台中。
<!---TFS 1283165--->

<p style="margin-left: 40px">**iOS 最终用户如何获取应用方面的改进**<br/>
<p style="margin-left: 40px">在 iOS 的公司门户应用的应用磁贴中已进行了以下更改，从一个位置（公司门户网站中）即可将用户指向其所有应用的不同视图。 Apple 限制禁止业务线和托管应用商店应用列于公司门户应用中，并要求用户访问不同视图来查找自己所有的应用。

<p style="margin-left: 40px">“公司应用”磁贴之前指向公司门户网站“全部”选项卡中的所有应用的列表，此行为将继续以同种方式运作。 磁贴名称已更改为“全部应用”。

<p style="margin-left: 40px">“其他应用”磁贴之前指向公司门户应用内部的一个视图，其中列出了 Apple 允许公司门户应用显示的所有应用。 磁贴名称已更改为“特别推荐的应用”，点击该磁贴会将用户转到公司门户网站的“特别推荐”选项卡。

<p style="margin-left: 40px">“类别”磁贴之前指向公司门户应用内部的一个视图，其中列出了应用类别。 磁贴名称未改变，但它现指向公司门户网站的“类别”选项卡。 你可以在[此处](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186)查看更新的屏幕截图。
  <!---TFS 1317133--->

<p style="margin-left: 40px">**如果 IT 专业人员为应用设置该要求，则会提示安装 iOS 托管浏览器应用**<br/>
<p style="margin-left: 40px">如果你已经将 Web Clip 配置为仅在托管的浏览器中打开，且托管浏览器未在设备上安装，则设备上的公司门户应用将提示用户安装托管浏览器后才能安装 Web Clip。
  <!---TFS 1228570--->

__Windows__
<p style="margin-left: 40px">**添加到 Windows Phone 8.1 公司门户应用的反馈按钮**<br/>
<p style="margin-left: 40px">Windows Phone 8.1 公司门户应用让最终用户能够通过使用新的“发送反馈”按钮发送有关应用的反馈。 要找到该按钮，用户需点击公司门户应用屏幕右下方的的“三个点”菜单，然后点击“发送反馈”。 收集的匿名信息反馈将帮助 Microsoft 改进用户的公司门户应用体验。
<!---TFS 1317806--->

### <a name="intune-glossarybr"></a>Intune 术语表</br>
我们在库中添加了一个新的[术语表主题](https://docs.microsoft.com/intune/understand-explore/intune-glossary)，帮助你了解 Intune 产品中使用的一些术语。

## <a name="august-2016"></a>2016 年 8 月
### <a name="app-management"></a>应用管理

__iOS 9.3 隐藏和显示的应用__ 对于运行 iOS 9.3 或更高版本的设备，可将 iOS 常规配置策略中隐藏和显示的应用列表用于：
- 指定对用户隐藏的应用列表。 用户无法查看，或启动这些应用。
- 指定用户可以查看和启动的应用列表。 无法查看或启动其他应用。

你可以指定的应用包括已部署的应用，以及内置的 iOS 应用，如“信息”和“备忘录”。 有关详细信息，请参阅 [Microsoft Intune 中的 iOS 策略设置](https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune)
<!---TFS 1279009 checked--->
__Samsung KNOX 设备允许和阻止的应用策略__ 现在可以配置适用于 Samsung KNOX 设备的自定义策略，使你能够创建以下项之一：
- 阻止在设备上运行的应用的列表。 即使安装了阻止列表中定义的应用，该应用也不能在设备上激活。
- 允许设备用户从 Google Play 商店中安装的应用的列表。 其他应用不能从应用商店安装。

仅运行 Samsung KNOX 的设备可以使用这些设置。
有关详细信息，请参阅[使用自定义策略允许和阻止适用于 Samsung KNOX 设备的应用](https://docs.microsoft.com/en-us/intune/deploy-use/custom-policy-to-allow-and-block-samsung-knox-apps)。
<!---TFS 1311629 checked --->

__与移动应用程序管理 (MAM) 策略兼容的新应用__ 无论是否已注册设备，适用于 [iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) 和 [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) 的 Yammer 应用现在都与 [Intune 移动应用程序管理 (MAM) 策略](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)兼容。

有关 MAM 兼容应用的完整列表，请参阅 [Microsoft Intune 应用程序合作伙伴](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners)站点。
<!--- TFS 1252335 & 1252336 checked--->

__Intune 查看器应用__ 随着新的 RMS 共享应用的发布，我们将从 2016 年 8 月起删除以下 Intune 查看器应用：
- Intune AV 查看器
- Intune PDF 查看器
- Google Play 中适用于 Android 的 Intune 图像查看器

建议使用[适用于 Android 的 Rights Management 应用（RMS 共享）](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app)而不是使用 Intune 查看器应用，前者只需部署一个应用而不是三个单独的应用便可安全地查看 Android 设备上的公司文件。 如果不再支持 Intune 查看器应用，则将其从 Google 应用商店中删除并且不可供将来使用。

### <a name="device-management"></a>设备管理
__Android 7.0 支持__ Intune 为移动设备即将推出的 Android 7.0 操作系统提供“day 0”支持。
<!---TFS 1262053--->
### <a name="google-removal-of-remote-passcode-reset-capability-on-android-70-devices"></a>Google 删除了 Android 7.0 设备上的远程密码重置功能
Google 正在删除 Android 7.0 设备的 IT 管理员和最终用户远程重置密码功能。 以前，IT 管理员可以远程重置用户的密码，而且最终用户可以从公司门户网站重置其密码。



### <a name="company-portal-updates"></a>公司门户更新
__公司门户网站__
- **从公司门户到 Microsoft 的反馈链接** <br/>
公司门户网站使最终用户能够点击位于页面底部的新的“反馈”链接，以便向 Microsoft 发送有关他们对站点的体验的反馈。 收集的匿名信息反馈将帮助 Microsoft 改进用户的公司门户网站体验。
<!--- TFS 1313657 checked--->

__iOS__
- **最低 iOS 托管浏览器版本已更新为 8.0**<br/>
已更新用于 iOS 的 Microsoft Intune Managed Browser 应用以支持运行 iOS 8.0 或更高版本的设备。 虽然 iOS 7.1 设备仍可使用现有的 Managed Browser 应用，但最好鼓励你的用户更新为 iOS 8.0 或更高版本，以访问和充分利用新的 Managed Browser 功能。  
<!---TFS 1313253 checked--->

### <a name="whats-coming"></a>即将推出
__Intune 组将于 2016 年 9 月过渡到 Azure Active Directory 组__ Intune 正在创建将 Azure Active Directory (AAD) 安全组用作 Intune 中的用户和设备组的新组管理体验。 **当我们介绍新的基于 Azure 的 Intune 管理门户时**，这些组将用于所有组管理、策略部署和配置文件部署。

此新体验将会使你无需在服务之间重复组，**允许你访问某些新的 Azure Active Directory Premium (AADP) 组功能**，并提供使用 PowerShell 和图表的可扩展性。 这还将跨企业移动性管理统一组管理体验。

若要启用移动到安全组，**当前管理控制台**中的体验将进行一些修改。 **这些更改和 AAD 安全组的使用情况将记录在 Intune 文档中**。

Intune 的新客户将看到**当前租户执行操作之前的一些安全组更改**。

除了组管理中的更改，**还将弃用以下功能**：
- 在创建新组的过程中排除成员或组
- “**未分组的用户**”和“**未分组的设备**”组
- 服务管理员角色中的“**管理组**”
- 对通知规则的基于组的自定义警报
- 利用报表中的组进行透视
<!--- TFS 1295329--->

__向 Android 公司门户添加“通知”__ 我们将于 9 月发布 Android 公司门户的更新，会在主页上引入一个新的“通知”图标。 点击此图标将访问“**通知**”页，该页将向你的最终用户显示在公司门户应用中需要注意的所有项，例如，设备非合规性、注册更新和注册激活。 如果还使用 iOS 公司门户应用，你将已看到通知体验。 通过引入“**通知**”页，只要设备已经注册，每次启动或恢复 Android 公司门户时，你将不会看到“**公司访问设置**”页。 我们听说你们中的许多人都已创建最终用户指南，而且非常感谢你们在指南/屏幕快照可能需要更新时提前通知我们。 请更新你的文档，以反映体验中即将发生的更改。 在此查找更新的屏幕快照：https://aka.ms/androidcpupdate。  

### <a name="service-deprecation"></a>服务弃用

- **iOS 公司门户应用的支持更改**<br/>
在 9 月，要求适用于 iOS 的 Microsoft Intune 公司门户应用的所有用户都使用最新版本。 新用户将只能够下载最新版本，而当前用户必须更新到最新版本。 最新版本需要 iOS 8.0 或更高版本，因此运行较旧的 iOS 版本的设备将无法使用公司门户或者进行注册，直到将其设备更新为 iOS 8.0 或更高版本，并且将公司门户应用更新到最新版本。 运行 iOS 8.0 以下版本的已注册设备将继续受管理，并将列在 Intune 管理员控制台中。  

- **最低 iOS 托管浏览器版本已更新为 8.0**<br/>
Intune 将于 8 月发布适用于 iOS 的更新的 Microsoft Intune 托管浏览器应用，该应用将仅支持运行 iOS 8.0 或更高版本的设备。 iOS 7.1 设备仍将能够使用现有的托管浏览器应用，请鼓励你的用户更新为 iOS 8.0 或更高版本，以访问和充分利用新的托管浏览器功能。  
<!---TFS 1313253--->

- **适用于 Windows 8 和 Windows Phone 8 的公司门户应用将从 2016 年 9 月起弃用** <br/>
从 2016 年 9 月开始，Microsoft Intune 将结束为适用于 Windows Phone 8 和 Windows 8 平台的 Microsoft Intune 公司门户应用提供支持。 将设备更新到 Windows 8.1 和 Windows Phone 8.1，并使用相应的 Windows 8.1 和 Windows Phone 8.1 公司门户应用继续向这些设备分发应用。
<!---TFS 1255391--->
