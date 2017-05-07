---
title: "早期版本 | Microsoft Docs"
description: 
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 04/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: 31f984fabd2373d242e5e3399bd0c82fbaf53070
ms.lasthandoff: 04/19/2017


---


# <a name="the-early-edition-for-microsoft-intune---april-2017"></a>Microsoft Intune 的早期版本 - 2017 年 4 月

**早期版本**提供了一份即将发布的 Microsoft Intune 版本中将出现的功能的列表。 此信息在非常有限的情况下依据保密协议 (NDA) 提供，并不断变化。 此处列出的某些功能有无法按期发布的风险并可能推迟到以后的版本。 正在以试验模式（外部测试）测试其他功能，以确保它们可立即供客户使用。 如果有任何问题或顾虑，请联系 Intune/PM 好友。

本页将定期更新。 返回查看其他更新。

> [!Note]
> 下面的更改依据 Intune 开发。 所有这些功能最终将支持混合客户部署（带 Intune 的 Configuration Manager）。 有关新的混合功能的详细信息，请查看[混合新增功能页](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。

## <a name="new-capabilities"></a>新功能

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>改进 Windows 10 公司门户应用的应用安装状态 <!--676495-->

Windows 10 公司门户应用现在将为从公司门户开始的所有新式应用安装提供应用安装进度条。

### <a name="improved-status-messaging-in-the-company-portal-app-for-ios---744866--"></a>改进了适用于 iOS 的公司门户应用的状态消息传送 <!--744866-->

现在将在适用于 iOS 的公司门户应用中显示更具体的新错误消息，以提供有关设备状态的更多可访问信息。 这些错误情况以前包含在标题为“公司门户暂时不可用”的常规错误消息中。 此外，如果用户在没有 Internet 连接的情况下在 iOS 上启动公司门户，他们现在将在主页上看到显示“无Internet 连接”的持续状态栏。

### <a name="myapps-available-for-managed-browser---822308-822303--"></a>MyApps 可用于托管浏览器 <!--822308, 822303-->

Microsoft MyApps 现在在托管浏览器中具有更好的支持。 面向管理的托管浏览器用户将直接转到 MyApps 服务，他们可在此处访问管理员预配的 SaaS 应用。 面向 Intune 管理的用户将能够继续从内置托管浏览器书签访问 MyApps。

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>托管浏览器和公司门户的新图标 <!--918433, 918431-->

托管浏览器正在接收 Android 和 iOS 版本应用的更新图标。 新图标将包含更新的 Intune 徽章，使其与企业移动性 + 安全性 (EM+S) 中的其他应用更加一致。 你可以在 [Intune 应用 UI 页面中的新增内容](whats-new-in-intune-app-ui.md)上查看 Managed Browser 的新图标。

公司门户还正在接收 Android、iOS 和 Windows 版本应用的更新图标，以提高与 EM + S 中其他应用的一致性。 这些图标将在 4 月至 5 月下旬逐渐发布。

### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>从适用于 iOS 的企业门户到 Outlook for iOS 的单一登录支持 <!--834012-->

如果用户在同一设备上使用同一帐户登录到适用于 iOS 的公司门户应用，则不再需要登录 Outlook 应用。 用户启动 Outlook 应用时，他们将能够选择自己的帐户并自动登录。 我们也正在致力于为其他 Microsoft 应用添加此功能。

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Android 公司门户中的登录进度指示器 <!--953374-->

用户启动或恢复应用时，Android 公司门户应用的更新会显示进度指示器。 该指示器将依次显示新的状态，从“正在连接...”开始，然后“正在登录...”，最后“正在检查安全性要求...”，完成后即允许用户访问该应用。 你可以在 [Intune 应用 UI 页面中的新增内容](whats-new-in-intune-app-ui.md)上查看适用于 Android 的公司门户应用的新屏幕。


## <a name="notices"></a>通知

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 将要求更新应用传输安全<!--748318-->

自 2017 年春季开始，Apple 宣布他们将强制对应用程序传输安全 (ATS) 实施特定要求。 使用 ATS 对所有通过 HTTPS 的应用通信实施更严格的安全措施。 此更改会影响使用 iOS 公司门户应用的 Intune 客户。 请查看 [Intune 支持博客](https://aka.ms/compportalats)，了解更多详细信息。

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接访问 Apple 注册方案<!--951869-->

对于在 2017 年 1 月之后创建的 Intune 帐户，Intune 支持在 Azure 预览门户中使用注册设备工作负荷直接访问 Apple 注册方案。 以前，仅能通过经典 Intune 门户中的链接访问 Apple 注册预览版。 2017 年 1 月之前创建的 Intune 帐户需要进行一次性迁移，然后才能使用 Azure 中的这些功能。 迁移的计划目前尚未公布，但详细信息将尽快发布。 强烈建议创建一个试用帐户，在现有帐户无法访问预览版时测试新体验。

### <a name="whats-coming-for-appx-in-intune-on-azure----1000270---"></a>Azure 上 Intune 的 Appx 的新增功能 <!-- 1000270 -->

在迁移到 Azure 上的 Intune 的过程中，我们做出了 3 个 appx 更改：

1. 在仅能部署到 MDM 注册的设备的经典 Intune 控制台中添加新的 appx 应用类型。
2. 重用现有的 appx 应用类型，以仅面向通过 Intune PC 代理托管的 PC。
3. 通过迁移将所有现有的 appxs 转换为 MDM appx。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？

这不会影响通过 Intune PC 代理管理的设备的任何现有部署。 但是，迁移后将无法将这些已迁移的 appx 部署到由先前未面向的 Intune PC 代理托管的任何新设备。

#### <a name="what-action-do-i-need-to-take"></a>我需要执行什么操作

迁移后，如果要进行新的 PC 部署，则需要将 appx 作为电脑 appx 再次上传。 若要了解详细信息，请参阅 [Intune 支持团队博客上的 ](https://aka.ms/appxchange)Azure 上 Intune 中的 Appx 更改。  


## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Azure 上新的 Intune 管理体验公开预览版<!--736542-->

在 2017 年初，我们会将完整管理体验迁移到 Azure 上，以便能够在可使用图形 API 进行扩展的新式服务平台上对核心 EMS 工作流进行强大且集成的管理。

新的试用租户将于本月开始在 Azure 门户中看到新管理体验的公开预览版。 在预览状态下，将以迭代方式交付现有 Intune 控制台的功能和奇偶校验。

Azure 门户中的管理体验将使用已公布的新分组和定向功能；当现有租户迁移到新的分组体验时，也会将你迁移，以预览租户上的新管理体验。 在此期间，如果想要在租户迁移之前测试或查看任何新功能，请注册新的 Intune 试用帐户或查阅[新文档](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune)。

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>支持 Android 应用的托管配置选项 <!-- 621621 -->

Play Store 中支持托管配置选项的 Android 应用可以由 Intune 进行配置。  通过此功能，IT 可查看应用支持的配置值列表，并提供优质的引导式 UI，以便配置这些值。

### <a name="remote-assistance-for-android-devices----675418---"></a>Android 设备的远程协助 <!-- 675418 -->

Intune 将使用 [TeamViewer](https://www.teamviewer.com) 软件（单独购买）使运行 Android 设备的用户获得远程协助。

### <a name="new-android-policy-for-complex-pins----722069---"></a>复杂 PIN 的新 Android 策略 <!-- 722069 -->

可以在运行 Android 5.0 及更高版本的设备的 Android 设备配置文件中设置数字复杂度所需的密码类型。  使用此设置可防止设备用户创建包含重复或连续数字（如 1111 或 1234）的 PIN。

### <a name="additional-support-for-android-for-work-devices"></a>对 Android for Work 设备的其他支持

- **管理密码及工作配置文件设置** <!-- 612808 -->

  我们添加了一个新的 Android for Work 设备限制策略，可让你在管理的 Android for Work 设备上管理密码和工作配置文件设置。

- **允许在工作和个人配置文件之间共享数据** <!-- 1045102 -->

  我们已在 Android for Work 设备限制配置文件中更新了**工作和个人配置文件之间的数据共享**设置，可以帮助你配置工作和个人配置文件之间的数据共享。

- **限制工作和个人配置文件之间的复制和粘贴** <!-- 1046094 -->

  使用 Intune 管理 Android for Work 设备时，允许在工作和个人应用之间进行复制和粘贴操作。 我们现在添加了适用于 Android for Work 设备的自定义设备配置文件，以用于限制是否允许在工作和个人应用之间进行复制和粘贴操作。

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>将 LOB 应用分配到 iOS 和 Android 设备 <!-- 1057568 -->

可以为用户或设备分配适用于 iOS（.ipa 文件）和 Android（.apk 文件）的业务线应用。

###  <a name="new-policies-for-ios-devices----723774-723815-723826-723830-723832---"></a>适用于 iOS 设备的新策略 <!-- 723774, 723815, 723826, 723830, 723832 -->

- **主屏幕上的应用** - 你可以使用设备策略控制用户在其 iOS 设备的主屏幕上看到的应用。 此策略将更改主屏幕的布局，但不会部署指定的任何未安装的应用。

- **与 AirPrint 设备的连接** - 可以使用 Intune 设备策略控制 iOS 设备的最终用户可以连接的 AirPrint 设备（网络打印机）。

- **与 AirPlay 设备的连接** - 可以使用 Intune 设备策略控制 iOS 设备的最终用户可以连接的 AirPlay 设备（如 Apple TV）。

- **自定义锁屏界面消息** - 可以配置用户将在其 iOS 设备的锁屏界面上看到的自定义消息（替换默认的锁屏界面消息）。

- **Web 内容筛选器** - 可以使用以下两种方法之一控制 iOS 设备的用户可以访问的网站：

  - 使用 Apple 内置的 Web 内容筛选器添加允许和阻止的 URL。
  - 只允许 Safari 浏览器访问指定的网站。 将在 Safari 中为你指定的每个站点创建书签。


### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>限制 iOS 应用的推送通知 <!-- 723767 -->

在 Intune 设备限制配置文件中，可以为 iOS 设备配置以下通知设置：

- 完全打开或关闭指定应用的通知。
- 在通知中心中打开或关闭指定应用的通知。
- 指定警报类型：“无”、“横幅”或“提醒”。
- 指定是否允许此应用的徽章。
- 指定是否允许通知声音。

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>配置 iOS 应用以单一应用模式自主运行 <!-- 737837 -->

可以使用 Intune 设备配置文件配置 iOS 设备，以自主单一应用模式运行指定应用。 配置此模式并运行应用时，将锁定设备，因此该设备只能运行该应用。 举个例子，当你配置一个允许用户在设备上进行测试的应用时就是如此。 应用的操作完成或删除此策略时，设备将恢复正常状态。

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>为 iOS 设备上的电子邮件和 web 浏览配置受信任的域 <!-- 723765 -->

可以从 iOS 设备限制配置文件配置以下域设置：

- **未标记的电子邮件域** - 用户发送或接收的电子邮件如果不匹配在此处指定的域，将标记为不受信任。

- **托管的 Web 域** - 从此处指定的 URL 下载的文档将被视为托管(仅限 Safari)。  

- **Safari 密码自动填充域** - 用户只能在 Safari 中保存与你在此处指定的模式相匹配的 URL 的密码。 若要使用此设置，设备必须处于监督模式，不配置为用于多个用户。 （iOS 9.3 及更高版本）


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>iOS 公司门户中可用的 VPP 应用 <!-- 748782 -->

可以将 iOS 批量购买的 (VPP) 应用作为**可用**安装分配给最终用户。 最终用户需要具有 Apple Store 帐户才能安装该应用。

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>同步 Apple VPP 应用商店的电子书 <!-- 800878 -->

可以与 Intune 同步从 Apple 批量采购计划应用商店购买的书，并将其分配给用户。

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Samsung KNOX 标准版设备的多用户管理 <!-- 971988 -->

现在，运行 Samsung KNOX 标准版的设备支持 Intune 进行多用户管理。 这意味着最终用户可以使用其 Azure Active Directory 凭据登录和注销设备，并且无论是否正在使用，都会集中管理设备。  当最终用户登录时，他们可以访问应用，还可以获得已应用的任何策略。 用户注销时，会清除所有应用数据。

### <a name="additional-windows-device-restriction-settings----818566---"></a>其他 Windows 设备限制设置 <!-- 818566 -->

我们添加了其他 Windows 设备限制设置的支持，如其他 Microsoft Edge 浏览器支持、设备锁屏界面自定义、开始菜单自定义、Windows 聚焦搜索集壁纸和代理设置。

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Windows 10 创意者更新的多用户支持 <!-- 822547 -->

我们为运行 Windows 10 创意者更新的设备和加入 Azure Active Directory 域的设备添加了对多用户管理的支持。 这意味着当不同的标准用户使用其 Azure AD 凭据登录设备时，他们将收到分配给其用户名的所有应用和策略。 用户当前无法将公司门户用于自助服务方案，如安装应用。

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Windows 10 电脑的 Fresh Start <!-- 1004830 -->

在此版本中，我们为 Windows 10 电脑添加了新的 Fresh Start 设备操作。  发出此操作时，电脑上安装的任何应用都将被删除，而且电脑会自动更新到最新版本的 Windows。 这可用于删除新电脑通常附带的预先安装的 OEM 应用。 发出此设备操作时可以配置是否保留用户数据。

### <a name="additional-windows-10-upgrade-paths----903672---"></a>Windows 10 其他升级途径<!-- 903672 -->

现可创建版本升级策略，将设备升级到以下的其他 Windows 10 版本：

- Windows 10 专业版
- Windows 10 专业版 N
- Windows 10 专业教育版
- Windows 10 专业教育版 N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>批量注册 Windows 10 设备 <!-- 747607 -->

可以使用 Windows 配置设计器 (WCD) 将运行 Windows 10 创意者更新的大量设备加入到 Azure Active Directory 和 Intune。 若要为你的 Azure AD 租户启用自动 MDM 注册，请创建一个预配包，该预配包将使用 Windows 配置设计器将设备加入到 Azure AD 租户，并将程序包应用到你想要批量注册和管理的公司所有的设备。 将程序包应用到设备后，设备将加入 Azure AD 并注册 Intune，以供 Azure AD 用户登录。  Azure AD 用户是这些设备上的标准用户并接收分配的策略和必需的应用。 目前不支持自助服务和公司门户方案。

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----58112-736644---"></a>PIN 和托管存储位置的新 MAM 设置 <!-- 58112, 736644 -->

这两个新的应用设置可用于帮助你处理移动应用程序管理 (MAM) 方案：

- **托管设备 PIN 时禁用应用 PIN** - 检测注册设备上是否存在设备 PIN，如果是，则忽略应用保护策略触发的应用 PIN。 此设置允许减少用户在注册设备上打开已启用 MAM 的应用程序时所看到的 PIN 提示次数。 此功能适用于 Android 和 iOS。

- **选择可将公司数据保存到其中的存储服务** - 允许你指定可将公司数据保存到哪些存储位置。 用户可以保存到所选存储位置服务，这意味着将阻止所有未列出的其他存储位置服务。

  支持的存储位置服务列表：

  - OneDrive
  - Business SharePoint Online
  - 本地存储


### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new-in-microsoft-intune.md)。

