---
title: "旧版 | Microsoft Docs"
description: 
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 04/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 5f172290d493717308446c4f9e2313a03ba8f3aa
ms.openlocfilehash: d7f25657fc7cfb9298809f76f198810718e58c39
ms.contentlocale: zh-cn
ms.lasthandoff: 04/27/2017


---


# <a name="the-early-edition-for-microsoft-intune---april-2017"></a>旧版 Microsoft Intune - 2017 年 4 月

**旧版**列出了即将发布的 Microsoft Intune 版本中将推出的功能。 此信息是根据保密协议提供，具有极为严格的条件限制，可能会发生变更。 本文中列出的一些功能面临着无法按期发布的风险，可能会推迟到今后推出的版本中发布。 其他功能正在接受试点测试（外部测试），以确保它们可供客户使用。 若有任何问题或疑问，请与你的 Intune/PM 合作者联系。

此页会定期进行更新。 请保持关注，看看是否有其他更新。

> [!Note]
> 下面的 Intune 更改仍处于开发阶段。 混合客户部署（含 Intune 的 Configuration Manager）最终将会支持所有这些功能。 若要详细了解新增的混合功能，请参阅[混合版本中的新增功能](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)页。

## <a name="new-capabilities"></a>新功能

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>改进了 Windows 10 公司门户应用的应用安装状态 <!--676495-->

现在，在 Windows 10 公司门户应用中开始安装所有新式应用时，都可以看到应用安装进度栏。 有关 Windows 10 公司门户应用的新状态消息，可以参阅 [Intune 应用 UI 页中的新增功能](whats-new-in-intune-app-ui.md)。

### <a name="improved-status-messaging-in-the-company-portal-app-for-ios---744866--"></a>改进了 iOS 公司门户应用中的状态消息 <!--744866-->

iOS 公司门户应用中现在将显示更具体的新错误消息，以提供有关设备动态的更多可访问信息。 这些错误之前包含在标题为“公司门户暂时不可用”的常规错误消息中。 此外，如果用户在未连接到 Internet 的情况下在 iOS 上启动公司门户，主页现在会一直显示“未连接到 Internet”状态栏。

### <a name="myapps-available-for-managed-browser---822308-822303--"></a>适用于 Managed Browser 的 MyApps <!--822308, 822303-->

现在 Microsoft MyApps 改进了 Managed Browser 内部的支持。 不作为管理目标的 Managed Browser 用户将直接转至 MyApps 服务，这些用户可以在其中访问管理员预配的 SaaS 应用。 作为 Intune 管理目标的用户将可以继续从内置 Managed Browser 书签访问 MyApps。

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Managed Browser 和公司门户的新图标 <!--918433, 918431-->

Managed Browser 将获得该应用的 Android 和 iOS 版的更新图标。 新图标将包含更新的 Intune 徽章，使其与企业移动性 + 安全性 (EM+S) 中的其他应用更为一致。 可以在 [Intune 应用 UI 页中的新增功能](whats-new-in-intune-app-ui.md)中查看 Managed Browser 的新图标。

公司门户还将获得该应用的 Android、iOS 和 Windows 版的更新图标，以改进与 EM+S 中的其他应用的一致性。 这些图标将于四月至五月底逐步在平台上发布。

### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>支持从 iOS 公司门户单一登录 Outlook for iOS <!--834012-->

如果用户使用相同帐户在同一设备上登录 iOS 公司门户应用，再也不用登录 Outlook 应用了。 启动 Outlook 应用后，可以选择自己的帐户并自动登录。 我们还在不断努力，以便为其他 Microsoft 应用添加此功能。

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Android 公司门户中的登录进度指示器 <!--953374-->

用户启动或重启应用时，Android 公司门户应用的更新程序将显示登录进度指示器。 允许用户访问应用前，指示器将经历以下新状态：开始是“正在连接...”，然后是“正在登录...”，接下来是“正在查看安全要求...”。 可以在 [Intune 应用 UI 页中的新增功能](whats-new-in-intune-app-ui.md)中查看适用于 Android 的公司门户应用的新屏幕。


## <a name="notices"></a>通知

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 要求针对应用传输安全进行更新 <!--748318-->

自 2017 年春季起，Apple 宣布将强制实施应用传输安全 (ATS) 特定要求。 ATS 用于对所有通过 HTTPS 的应用通信强制实施更严格的安全措施。 此更改会影响使用 iOS 公司门户应用的 Intune 客户。 请参阅 [Intune 支持博客](https://aka.ms/compportalats)，了解更多详情。

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接访问 Apple 注册方案 <!--951869-->

对于 2017 年 1 月之后创建的 Intune 帐户，Intune 允许在 Azure 预览门户中使用“注册设备”工作负载直接访问 Apple 注册方案。 以前，Apple 注册预览只能通过经典 Intune 门户中的链接进行访问。 在 2017 年 1 月之前创建的 Intune 帐户必须先进行一次性迁移，然后才能在 Azure 中使用这些功能。 虽然迁移时间表尚未宣布，但会尽快发布详细信息。 如果现有帐户无法访问注册预览，强烈建议创建试用帐户来测试新体验。

### <a name="whats-coming-for-appx-in-intune-on-azure----1000270---"></a>Azure 上的 Intune 中即将推出的 Appx 新功能 <!-- 1000270 -->

在迁移到 Azure 上的 Intune 期间，我们在执行三项 appx 更改：

1. 在经典 Intune 控制台中添加新的 appx 应用类型，这种类型只能部署到已注册 MDM 的设备。
2. 重新利用现有的 appx 应用类型，使其仅定位通过 Intune PC 代理管理的 PC。
3. 通过迁移将现有全部 appx 转换成 MDM appx。

#### <a name="how-does-this-affect-me"></a>这会对我产生哪些影响？

这不会影响通过 Intune PC 代理管理的设备中的任何现有部署。 不过，迁移后，将无法把已迁移的 appx 部署到任何通过 Intune PC 代理管理且以前未定位的新设备。

#### <a name="what-action-do-i-need-to-take"></a>我需要采取哪些措施

迁移后，如果要进行新的 PC 部署，则需要再次将 appx 重新上载为 PC appx。 若要了解详细信息，请参阅 Intune 支持团队博客上的 [Azure 上的 Intune 中推出的 Appx 更改](https://aka.ms/appxchange)。  


## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Azure 上新 Intune 管理体验的公开预览版 <!--736542-->

在 2017 年年初，我们将会把管理体验完全迁移到 Azure 上，以便能够在可使用 Graph API 进行扩展的新式服务平台上对核心 EMS 工作流进行强大的集成式管理。

从本月开始，新建的试用租户将可以在 Azure 门户中看到新管理体验的公开预览版。 在预览状态下，将以循环访问方式交付功能，以及与现有 Intune 控制台等同的体验。

对于 Azure 门户中的管理体验，将使用已宣布的新分组和定位功能；将现有租户迁移为采用新的分组体验时，也会迁移为在租户上预览新管理体验。 与此同时，如果要在租户迁移完成之前测试或查看任何新功能，请注册新的 Intune 试用帐户或参阅[新文档](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune)。

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>支持 Android 应用的受管理配置选项 <!-- 621621 -->

Intune 可以配置 Play 商店中支持受管理配置选项的 Android 应用。  使用此功能，IT 人员可以查看应用支持的配置值列表，并能通过引导式优质 UI 配置这些值。

### <a name="remote-assistance-for-android-devices----675418---"></a>Android 设备远程协助 <!-- 675418 -->

Intune 使用 [TeamViewer](https://www.teamviewer.com) 软件（单独购买），以便你可以向运行 Android 设备的用户提供远程协助。

### <a name="new-android-policy-for-complex-pins----722069---"></a>设置复杂 PIN 的新 Android 策略 <!-- 722069 -->

对于运行 Android 5.0 及更高版本的设备，可以在 Android 设备配置文件中设置所需的复杂数字类型密码。  使用此设置可防止设备用户创建包含重复或连续数字（如 1111 或 1234）的 PIN。

### <a name="additional-support-for-android-for-work-devices"></a>针对 Android for Work 设备提供的其他支持

- **管理密码和工作配置文件设置** <!-- 612808 -->

  我们新增了一项 Android for Work 设备限制策略，以便你可以在管理的 Android for Work 设备上管理密码和工作配置文件设置。

- **允许在工作和个人配置文件之间共享数据** <!-- 1045102 -->

  我们已更新 Android for Work 设备限制配置文件中的**工作和个人配置文件之间的数据共享**设置，在其中添加了有助于配置工作和个人配置文件之间的数据共享的新选项。

- **限制在工作和个人配置文件之间执行复制和粘贴操作** <!-- 1046094 -->

  使用 Intune 管理 Android for Work 设备时，允许在工作和个人应用之间执行复制和粘贴操作。 我们现在为 Android for Work 设备添加了自定义设备配置文件，以便你可以限制是否允许在工作和个人应用之间执行复制和粘贴操作。

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>将 LOB 应用分配给 iOS 和 Android 设备 <!-- 1057568 -->

可以向用户或设备分配 iOS 业务线应用（.ipa 文件）和 Android 业务线应用（.apk 文件）。

###  <a name="new-policies-for-ios-devices----723774-723815-723826-723830-723832---"></a>适用于 iOS 设备的新策略 <!-- 723774, 723815, 723826, 723830, 723832 -->

- **主屏幕上的应用** - 可以使用设备策略来控制用户可以在其 iOS 设备主屏幕上看到的应用。 此策略可更改主屏幕的布局，但不会部署你指定的任何尚未安装的应用。

- **连接 AirPrint 设备** - 可以使用 Intune 设备策略来控制 iOS 设备最终用户可以连接的 AirPrint 设备（网络打印机）。

- **连接 AirPlay 设备** - 可以使用 Intune 设备策略来控制 iOS 设备最终用户可以连接的 AirPlay 设备（如 Apple TV）。

- **自定义锁屏界面消息** - 可以配置用户将在其 iOS 设备锁屏界面上看到的自定义消息（替换默认的锁屏界面消息）。

- **Web 内容筛选器** - 可以使用以下两种方法之一来控制 iOS 设备用户可以访问的网站：

  - 使用 Apple 内置的 Web 内容筛选器添加允许和阻止的 URL。
  - 仅允许 Safari 浏览器访问指定网站。 将会在 Safari 中创建你指定的每个网站的书签。


### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>限制 iOS 应用的推送通知 <!-- 723767 -->

在 Intune 设备限制配置文件中，可以为 iOS 设备配置以下通知设置：

- 为指定应用完全启用或禁用通知。
- 在通知中心为指定应用启用或禁用通知。
- 指定警报类型（“无”、“横幅”或“模式警报”）。
- 指定是否允许对此应用使用锁屏提醒。
- 指定是否允许使用通知声音。

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>将 iOS 应用配置为在自治单应用模式下运行 <!-- 737837 -->

可以使用 Intune 设备配置文件将 iOS 设备配置为在自治单应用模式下运行指定应用。 如果配置此模式，那么在运行应用时，设备会被锁定，以便只运行相应应用。 例如，将应用配置为允许用户在设备上参加测验。 当应用的操作完成或你删除此策略时，设备便会恢复常规状态。

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>配置受信任的域以便在 iOS 设备上浏览电子邮件和网页 <!-- 723765 -->

可以使用 iOS 设备限制配置文件配置以下域设置：

- **未标记的电子邮件域** - 如果用户发送或接收的电子邮件与你在此处指定的域不一致，则会被标记为不受信任。

- **托管的 Web 域** - 从你在此处指定的 URL 下载的文档将被视为托管（仅限 Safari）。  

- **Safari 密码自动填充域** - 用户只能在 Safari 中与你在这里指定的模式匹配的 URL 处保存密码。 设备必须处于受监督模式，且未配置为供多个用户使用，才能使用此设置。 (iOS 9.3+)


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>可以在 iOS 公司门户中安装 VPP 应用 <!-- 748782 -->

可以将 iOS Volume Purchase Program (VPP) 应用分配为最终用户“可用”安装项。 最终用户必须拥有 Apple Store 帐户，才能安装此类应用。

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>同步从 Apple VPP 商店购买的电子图书 <!-- 800878 -->

可以使用 Intune 同步从 Apple Volume Purchase Program 商店购买的电子图书，然后将其分配给用户。

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Samsung KNOX Standard 设备的多用户管理 <!-- 971988 -->

现在，支持使用 Intune 对运行 Samsung KNOX Standard 的设备进行多用户管理。 也就是说，最终用户可以使用其 Azure Active Directory 凭据登录和注销设备，并且设备可供集中管理，无论其是不是在被使用。  登录后，最终用户不仅可以访问应用，还可以获取向其应用的所有策略。 用户注销后，所有应用数据都会被清除。

### <a name="additional-windows-device-restriction-settings----818566---"></a>其他 Windows 设备限制设置 <!-- 818566 -->

我们现已开始支持其他 Windows 设备限制设置，如额外的 Edge 浏览器支持、设备锁屏界面自定义、开始菜单自定义、Windows Spotlight 搜索集壁纸和代理设置。

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Windows 10 创意者更新的多用户支持 <!-- 822547 -->

我们现已开始支持对运行 Windows 10 创意者更新且已加入 Azure Active Directory 域的设备进行多用户管理。 也就是说，当多个标准用户使用其 Azure AD 凭据登录设备时，他们将收到分配给其用户名的所有应用和策略。 用户暂无法使用公司门户执行自助式操作，如安装应用。

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Windows 10 PC 的从头开始选项 <!-- 1004830 -->

在此版本中，我们为 Windows 10 PC 添加了从头开始的设备操作。  发出此操作后，将会删除 PC 上安装的任何应用，并且 PC 会自动更新到最新版本的 Windows。 这可用于删除新 PC 通常随附的预安装 OEM 应用。 可以配置是否在发出此设备操作时保留用户数据。

### <a name="additional-windows-10-upgrade-paths----903672---"></a>其他 Windows 10 升级路径 <!-- 903672 -->

现在可以创建版本升级策略，将设备升级到以下其他 Windows 10 版本：

- Windows 10 专业版
- Windows 10 专业版 N
- Windows 10 专业教育版
- Windows 10 专业教育版 N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>批量注册 Windows 10 设备 <!-- 747607 -->

可以使用 Windows 配置设计器 (WCD)，将运行 Windows 10 创意者更新的大量设备加入 Azure Active Directory 和 Intune。 若要为 Azure AD 租户启用自动 MDM 注册，请创建一个预配包，以使用 Windows 配置设计器将设备加入 Azure AD 租户，然后将预配包应用到要批量注册并管理的企业拥有的设备。 将预配包应用到设备后，它们便会加入 Azure AD、注册使用 Intune，然后即可供 Azure AD 用户登录。  Azure AD 用户是这些设备上的标准用户，可接收分配的策略和所需的应用。 暂不支持执行自助式操作和使用公司门户。

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----58112-736644---"></a>有关 PIN 和托管存储位置的新 MAM 设置 <!-- 58112, 736644 -->

新增了两项有助于进行移动应用管理 (MAM) 的应用设置：

- **托管设备 PIN 时，禁用应用 PIN** - 检测已注册设备上是否有设备 PIN；如果有，将绕过应用保护策略触发的应用 PIN。 此设置有助于减少向在已注册设备上打开启用了 MAM 的应用的用户显示的 PIN 提示次数。 此功能适用于 Android 和 iOS。

- **选择可以在其中保存企业数据的存储服务** - 允许指定用于保存企业数据的存储位置。 用户可以将数据保存到选定存储位置服务。也就是说，未列出的其他所有存储位置服务将被屏蔽。

  支持的存储位置服务列表：

  - OneDrive
  - Business SharePoint Online
  - 本地存储


### <a name="see-also"></a>另请参阅
若要详细了解最近的开发情况，请参阅 [Microsoft Intune 中的新增功能](whats-new-in-microsoft-intune.md)。

