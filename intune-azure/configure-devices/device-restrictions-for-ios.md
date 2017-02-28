---
title: "适用于 iOS 的 Intune 设备限制设置 |Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：了解可用来控制 iOS 设备上的设备设置和功能的 Intune 设置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 73590192-54ca-4833-9f1d-83e1b654399f
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 2b8bf6d3944f9968d0f4020fbb5c57ef8180062c
ms.lasthandoff: 02/16/2017


---

# <a name="ios-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune 中的 iOS 设备限制设置

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>常规
-     **相机** - 选择是否可以使用设备上的相机。     
-     **诊断数据提交** - 允许或阻止设备将诊断数据提交到 Apple。
-     **FaceTime** -允许在设备上使用 FaceTime 应用。
-     **屏幕捕获** - 允许用户以图像形式捕获屏幕内容。
-     **Siri** - 允许在设备上使用 Siri 语音助手。
    -     **在设备锁定时使用 Siri** - 允许在设备锁定时使用 Siri 语音助手。
    -     **Siri 猥亵语言筛选器（仅限被监督的设备）** - 防止 Siri 听写或说出猥亵语言。
    -     **Siri 从 Internet 查询用户生成的内容（仅限被监督的设备）** - 允许 Siri 访问网站以回答问题。
-     **不受信任的 TLS 证书** - 允许设备使用不受信任的传输层安全性证书。
-     **在设备锁定时访问控制中心** - 允许用户在设备锁定时访问控制中心应用。
-     **在设备锁定时查看通知** - 允许用户在不解锁设备的情况下访问通知视图。
-     **在设备锁定时使用 Passbook** - 允许用户在设备锁定时访问 Passbook 应用。
-     **在设备锁定时查看“今日”视图** - 允许用户在设备锁定时查看“今日”视图。
-     **企业应用信任** - 允许用户选择信任不是从应用商店下载的应用。
-     **AirDrop（仅限被监督的设备）** - 允许使用 AirDrop 功能与附近的设备相互传输内容。
-     **Spotlight 搜索从 Internet 返回结果（仅限被监督的设备）** - 允许 Spotlight 搜索连接到 Internet 以提供进一步结果。
-     **单词定义查找（仅限被监督的设备）** - 允许可突出显示某个字词并查找其定义的 iOS 功能。
-     **预测键盘（仅限被监督的设备）** - 允许使用预测键盘，它会建议用户可能想要使用的字词。
-     **自动更正（仅限被监督的设备）** - 让设备自动更正拼写错误的词。
-     **键盘拼写检查（仅限被监督的设备）** - 允许设备拼写检查程序。
-     **键盘快捷方式（仅限被监督的设备）** - 允许使用键盘快捷方式。
-     **已配对的 Apple Watch 的手腕检测** - 启用后，Apple Watch 在未穿戴时不会显示通知。
- **需要 AirPlay 传出请求配对密码** - 当用户使用 AirPlay 将内容流式传输到其他 Apple 设备时，需要提供配对密码。
- **帐户修改（仅限被监督的设备）** - 允许用户更改帐户设置，如电子邮件配置。
- **Apple Watch 配对（仅限被监督的设备）** - 允许设备与 Apple Watch 配对。
- **蓝牙修改（仅限被监督的设备）** - 阻止最终用户更改设备上的蓝牙设置。
- **通过 Classroom 应用观测远程屏幕（仅限被监督的设备）** - 允许或阻止 Classroom 应用观测远程设备上的屏幕。
- **启用设备设置中的限制（仅限被监督的设备）** - 允许用户在设备上配置设备限制（家长控制）。
- **使用设备上的擦除所有内容和设置选项（仅限被监督的设备）** - 允许用户使用设备上的擦除所有内容和设置的选项。
- **设备名称修改（仅限被监督的设备）** - 允许用户更改设备的名称。
- **修改诊断提交设置（仅限被监督的设备）** - 允许或阻止设备将诊断数据提交到 Apple。
- **通过主机配对来控制 iOS 设备可与之配对的设备（仅限被监督的设备）** - 允许主机配对，以使管理员能够控制 iOS 设备可与之配对的设备。
- **修改通知设置（仅限被监督的设备）** - 允许用户更改设备通知设置。
- **修改密码（仅限被监督的设备）** - 允许添加、更改或删除设备密码。
- **修改墙纸（仅限被监督的设备）** - 允许用户更改设备墙纸。
- **修改企业应用信任设置（仅限被监督的设备）** - 允许用户选择信任不是从应用商店下载的应用。
- **从 App Store 安装应用（仅限被监督的设备）** - 允许设备访问 App Store 并安装应用。
- **更改“查找朋友”应用设置（仅限被监督的设备）** - 允许用户更改“查找朋友”应用的设置。
- **iBooks 商店（仅限被监督的设备）** - 允许用户从 iBooks 商店浏览和购买书籍。
- **设备上的“邮件”应用（仅限被监督的设备）** - 允许使用“邮件”应用发送和阅读文本信息。
- **播客（仅限被监督的设备）** - 允许使用“播客”应用。
- **音乐服务（仅限被监督的设备）** - 允许使用 Apple 音乐应用。
- **iTunes Radio 服务（仅限被监督的设备）** - 允许使用 iTunes Radio 应用。
- **Apple 新闻（仅限被监督的设备）** - 允许使用 Apple 新闻应用。
- **配置描述文件更改** - 允许用户安装配置描述文件。

## <a name="password"></a>Password
-     **需要密码** - 需要最终用户输入密码才能访问设备。
-     **简单密码** - 允许 0000 和 1234 等简单密码。
-     **所需的密码类型** - 指定需要的密码类型，例如仅限数字或字母数字。
-     **密码中的非字母数字字符数** - 指定密码中必须包含的符号字符（如 **#** 或 **@**）数。
-     **最短密码长度** - 指定密码中所需的最少字符数。
-     **擦除设备前的登录失败次数** - 指定此设置擦除设备前的失败登录尝试次数。
-     **屏幕锁定后要求提供密码前的最大分钟数**<sup>1</sup> - 指定用户必须重新输入密码前设备可以保持空闲状态的时间。
-     **屏幕锁定前的非活动状态最大分钟数**<sup>1</sup> - 指定设备显示屏关闭之前的分钟数。
-     **密码过期（天数）** - 指定必须更改设备密码前的天数。
-     **防止重用以前的密码** - 指定设备记住的以前用过的密码数目。
-     **指纹解锁** - 允许使用指纹解锁兼容的设备。

<sup>1</sup>配置设置“屏幕锁定前的非活动状态最大分钟数”和“屏幕锁定后要求提供密码前的最大分钟数”时，它们会依次应用。 例如，如果你设置的两个设置的值均为“5”  分钟，屏幕在 5 分钟后将自动关闭，然后再过 5 分钟后该设备将锁定。 但是，如果用户手动关闭屏幕，第二个设置将立即应用。 在相同的示例中，用户关闭屏幕后，该设备将在 5 分钟后锁定。

## <a name="app-store-doc-viewing-gaming"></a>App Store、文档查看和游戏


-   **App Store（仅限被监督的设备）** - 阻止访问受监督设备上的 App Store。
-     **输入密码以访问 App Store** - 要求用户输入密码后才能访问 App Store。
-     **应用内购买** - 允许在运行的应用中产生应用商店购买行为。
-     **自动应用下载（仅限被监督的设备）** -
-     **成人 iTunes 音乐、播客或新闻内容（仅限被监督的设备）** - 允许设备访问商店中的成人内容。
-     **从 iBook 商店下载标记为“成人作品”的内容** - 允许用户下载类别为“成人作品”的书籍。
-     **在非托管应用中查看公司文档** - 允许在任何应用中查看公司文档。<br>**示例：**你想要防止用户将文件从 OneDrive 应用保存到 Dropbox。 将此设置配置为“否”。 设备收到策略后（例如在重启后），将不再允许保存。
-     **在公司应用中查看非公司文档** - 允许在公司托管的应用中查看任何文档。
-     **将 AirDrop 视为非托管目标** - 阻止托管应用通过 Airdrop 发送数据。 。
-     **添加 Game Center 好友（仅限被监督的设备）** - 允许用户在 Game Center 中添加好友。
-     **Game Center（仅限被监督的设备）** - 阻止或启用 Game Center 应用。
-     **多玩家游戏（仅限被监督的设备）** - 允许用户在设备上玩多玩家游戏。
-     **分级区域** - 选择要为其配置允许的下载的分级区域，然后为**电影**和**电视节目**选择允许的分级。
-     **应用** - 选择用户可下载允许年龄分级的应用，或者可以选择“允许所有应用”。

## <a name="restricted-apps"></a>受限制的应用

在受限制的应用列表中，可以配置以下列表之一：

**禁止的应用**列表 - 列出用户不得安装和运行的应用（未由 Intune 托管）。
**批准的应用**列表 - 列出允许用户安装的应用。 为了保持相容状态，用户不得安装未列出的应用。 自动允许由 Intune 托管的应用。

若要配置列表，请单击“添加”，然后指定所选应用的名称、应用发布者（可选）和该应用在应用商店中的 URL。

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>如何指定应用商店中应用的 URL

若要在应用列表中指定应用 URL，请使用以下格式：

使用搜索引擎，查找你想在 iTunes 应用商店中使用的应用并打开该应用的页面。
复制页面的 URL，并使用此 URL 配置允许或禁止应用列表或你想要在展台模式下运行的应用。
必须将包含受限制的应用设置的设备配置文件部署到用户组。

示例：搜索 Microsoft Word for iPad。 你将使用的 URL 是 https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8。

> [!Note]
> 你还可以使用 iTunes 软件查找应用程序，然后使用“复制链接”  命令获取应用的 URL。



### <a name="additional-options"></a>其他选项

还可以单击“导入”，填充 csv 文件中的列表（格式为 <*应用 URL*>,<*应用名称*>,<*应用发布者*>），或单击“导出”，创建包含受限制应用列表内容且格式相同的 csv 文件。

## <a name="show-or-hide-apps"></a>显示或隐藏应用

在“显示或隐藏应用”列表中，可以配置以下列表之一（需要运行 iOS 9.3 或更高版本的受监控设备）。

**隐藏应用**列表 - 指定对用户隐藏的应用列表。 用户无法查看，或启动这些应用。
**可见应用**列表 - 指定用户可以查看和启动的应用的列表。 无法查看或启动其他应用。

若要配置列表，请单击“添加”，然后指定所选应用的名称、应用发布者（可选）和该应用在应用商店中的 URL。

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>如何指定应用商店中应用的 URL

若要在应用列表中指定应用 URL，请使用以下格式：

使用搜索引擎，查找你想在 iTunes 应用商店中使用的应用并打开该应用的页面。
复制页面的 URL，并使用此 URL 配置允许或禁止应用列表或你想要在展台模式下运行的应用。

示例：搜索 Microsoft Word for iPad。 你将使用的 URL 是 https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8。

> [!Note]
> 你还可以使用 iTunes 软件查找应用程序，然后使用“复制链接”  命令获取应用的 URL。

### <a name="additional-options"></a>其他选项

还可以单击“导入”，填充 csv 文件中的列表（格式为 <*应用 URL*>,<*应用名称*>,<*应用发布者*>），或单击“导出”，创建包含隐藏或可见应用列表内容且格式相同的 csv 文件。

### <a name="app-information-for-built-in-ios-apps"></a>内置 iOS 应用的应用信息
使用此列表中的信息识别想要显示或隐藏的内置 iOS 应用的名称、发布者和捆绑 ID。 如果想要显示或隐藏列表中的所有应用，可以将下面的数据复制到扩展名为 **.csv** 的文本文件中，然后使用“导入”选项同时导入所有应用。


    App Store,Apple,com.apple.AppStore
    Calculator,Apple,com.apple.calculator
    Calendar,Apple,com.apple.mobilecal
    Camera,Apple,com.apple.camera
    Clock,Apple,com.apple.mobiletimer
    Compass,Apple,com.apple.compass
    Contacts,Apple,com.apple.MobileAddressBook
    FaceTime,Apple,com.apple.facetime
    Find Friends,Apple,com.apple.mobileme.fmf1
    Find iPhone,Apple,com.apple.mobileme.fmip1
    Game Center,Apple,com.apple.gamecenter
    GarageBand,Apple,com.apple.mobilegarageband
    Health,Apple,com.apple.Health
    iBooks,Apple,com.apple.iBooks
    iTunes Store,Apple,com.apple.MobileStore
    iTunes U,Apple,com.apple.itunesu
    Keynote,Apple,com.apple.Keynote
    Mail,Apple,com.apple.mobilemail
    Maps,Apple,com.apple.Maps
    Messages,Apple,com.apple.MobileSMS
    Music,Apple,com.apple.Music
    News,Apple,com.apple.news
    Notes,Apple,com.apple.mobilenotes
    Numbers,Apple,com.apple.Numbers
    Pages,Apple,com.apple.Pages
    Photo Booth,Apple,com.apple.Photo-Booth
    Photos,Apple,com.apple.mobileslideshow
    Podcasts,Apple,com.apple.podcasts
    Reminders,Apple,com.apple.reminders
    Safari,Apple,com.apple.mobilesafari
    Settings,Apple,com.apple.Preferences
    Stocks,Apple,com.apple.stocks
    Tips,Apple,com.apple.tips
    Videos,Apple,com.apple.videos
    VoiceMemos,Apple,com.apple.VoiceMemos
    Wallet,Apple,com.apple.Passbook
    Watch,Apple,com.apple.Bridge
    Weather,Apple,com.apple.weather





## <a name="cellular"></a>移动电话
-     **数据漫游** - 当设备在手机网络中时允许数据漫游。
-     **漫游时进行全局后台提取** - 允许当设备在手机网络漫游时提取数据，例如电子邮件。
-     **语音拨号** - 允许在设备上使用语音拨号功能。
-     **语音漫游** - 当设备在手机网络中时允许语音漫游。
-     **更改应用的移动电话数据使用情况设置（仅限被监督的设备）** - 允许用户控制允许哪些应用使用手机数据。

## <a name="cloud-and-storage"></a>云和存储
-     **备份到 iCloud** - 允许用户将设备备份到 iCloud。
-     **将文档同步到 iCloud（仅限被监督的设备）** - 允许将文档和键值同步到 iCloud 存储空间。
-     **将照片流同步到 iCloud** - 允许用户在其设备上启用“我的照片流”，该操作可将照片同步到 iCloud 并在所有用户设备上可用。
-     **加密的备份** - 需要将任何设备备份进行加密。
-     **iCloud 照片库** - 如果设置为“否”，则会禁用可供用户在云中存储照片和视频的 iCloud 照片库。    如果将其设置为“否”，则从设备中删除尚未从 iCloud 照片库完全下载到设备的所有照片。
-     **通过托管的应用同步到云** - 允许通过 Intune 管理的应用将数据同步到用户的 iCloud 帐户。
-     **共享照片流** - 将其设置为“否”以在设备上禁用“iCloud 照片共享”。
-     **活动延续** - 允许用户在其他 iOS 或 Mac OS X 设备上继续进行在某台 iOS 设备上开始的工作（切换）。

## <a name="kiosk"></a>Kiosk
-     **激活锁** - 在受监管的 iOS 设备上启用激活锁。
-     **在展台模式下运行的应用** - 选择“托管应用”以选择已添加到 Intune 的应用，或选择“应用商店应用”以指定应用商店中应用的 URL。 不允许在设备上运行其他应用。 若要获取更多帮助，请参阅本主题后面的“如何指定应用商店的 URL”。
-     **辅助触摸** - 启用或禁用“辅助触摸”辅助功能设置，它可帮助用户执行可能难以执行的屏幕手势。
-     **反转颜色** - 启用或禁用“反转颜色”辅助功能设置，它可调整显示效果以帮助有视觉障碍的用户。
-     **单声道音频** - 启用或禁用“单声道音频”辅助功能设置。
-     **VoiceOver** - 启用或禁用“VoiceOver”辅助功能设置，它能朗读设备上显示的文本。
-     **缩放** - 启用或禁用“缩放”辅助功能设置，它允许用户通过触摸来缩放设备显示。
-     **自动锁定** - 启用或禁用设备的自动锁定。
-     **响铃开关** - 启用或禁用设备上的响铃（静音）开关。
-     **屏幕旋转** - 启用或禁用在用户旋转设备时更改屏幕方向。
-     **屏幕睡眠按钮** - 启用或禁用设备上的屏幕睡眠唤醒按钮。
-     **触控** - 启用或禁用设备上的触摸屏。
-     **音量按钮** - 启用或禁用设备上的音量按钮。
-     **辅助触控** - 启用或禁用辅助触摸调节，它允许用户调节辅助触摸功能。
-     **反转颜色控制** - 启用或禁用反色调整，它允许用户调整反转颜色功能。
-     **朗读所选文本** - 启用或禁用“朗读所选项”辅助功能设置，它可朗读用户选择的文本。
-     **VoiceOver 控制** - 启用或禁用语音朗读调整，它允许用户调整 VoiceOver 功能（例如，屏幕上文本的朗读速度）。
-     **缩放控制** - 启用或禁用缩放调整，它允许用户调整缩放功能。

>[!NOTE]
> 必须使用 Apple Configurator 工具或 Apple 设备注册程序将设备置于监督模式后才能为 iOS 设备配置展台模式。 有关 Apple Configurator 工具的详细信息，请参阅 Apple 文档。
>如果在部署配置策略之后安装指定的 iOS 应用，则设备将在重启后才会进入展台模式。

## <a name="safari"></a>Safari
-     **Safari（仅限被监督的设备）** - 指定是否可以在设备上使用 Safari 浏览器。
-     **自动填充** - 允许用户更改浏览器中的自动完成设置。
-     **Cookie** - 允许浏览器使用 Cookie。
-     **JavaScript** - 允许在浏览器中运行 Java 脚本。
-     **欺诈警告** - 允许在浏览器中使用欺诈警告。
-     **弹出窗口** - 启用或禁用浏览器弹出窗口阻止程序。

