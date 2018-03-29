---
title: iOS 策略设置
description: 创建策略，该策略控制通过 Intune 管理的 iOS 设备上的设置及功能。
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 11/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ab46be6c-ab73-4c99-8492-66d1dd418293
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ff426feff58de8b06fed7be9a0e6a52e9cc40ae3
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="ios-policy-settings-in-microsoft-intune"></a>Microsoft Intune 中的 iOS 策略设置

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune 提供了一系列可在 iOS 设备上进行配置的内置常规设置。 此外，还可使用 Apple Configurator 工具创建 Intune 未提供的自定义设置。

## <a name="general-configuration-policy-settings"></a>常规配置策略设置

使用 Microsoft Intune 的“iOS 常规配置策略”为以下对象配置设置：

-   “一般设备和安全设置”。 从预定义设置列表中进行选择，此列表让你可以控制设备上的一系列功能。

-   “展台模式”。 锁定设备为只允许某些功能运行。 例如，你可以让设备只运行一个指定的托管应用，也可以禁用设备上的音量按钮。 这些设置可用于设备的演示模型，也可用于专门执行一个功能的设备（如销售点设备）。

-   “相容和不相容的应用”。 指定公司中相容和不相容的应用的列表。 在 Android 和 iOS 设备上，“不相容应用报告”可用于查看你在列表中指定的应用对于用户已经安装的应用的相容性（但不能实际阻止应用的安装）。

> [!TIP]
> 你可以为用户配置条款和条件，确保他们确认其设备上的应用（包括个人应用）将会受到评估，不相容的应用将被阻止或报告为不相容。 用户必须接受这些条款和条件，然后才能注册其设备并使用公司门户获取应用。 有关使用条款和条件的详细信息，请参阅 [Microsoft Intune 中的条款和条件策略设置](terms-and-condition-policy-settings-in-microsoft-intune.md)。

如果你寻找的设置没有在此主题中出现，你可能可以使用 iOS 自定义策略创建它，通过该策略你可以使用 [Apple Configurator 工具](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12)导入你创建的设置。 有关详细信息，请参阅本主题后面的“自定义策略设置”。

### <a name="security-settings"></a>安全设置
所有设置均适用于 iOS 8.0 及更高版本。

|设置名|详细信息|
|----------------|-------|
|**需要密码才可解锁移动设备**|指定用户是否必须输入密码来访问其设备。|
|**所需的密码类型**|指定需要的密码类型，例如仅限数字或字母数字。|
|**密码中所需的复杂字符数**|指定密码中必须包括的符号字符（如**#**或**@**）数。|
|**最短密码长度**|指定密码中所需的最少字符数。|
|**允许简单密码**|允许简单密码，如 **0000** 和 **1234**。|
|**擦除设备前允许的重复登录失败次数**|指定此设置擦除设备前的失败登录尝试次数。|
|**需要提供密码之前处于非活动状态的分钟数**<sup>1</sup>|指定用户必须重新输入密码前设备可以保持空闲状态的时间。|
|**密码过期（天数）**|指定必须更改设备密码前的天数。|
|**记住密码历史**|指定用户是否可以使用以前用过的密码。|
|**“记住密码历史记录”** – **“防止重用以前的密码”**|指定设备记住的以前用过的密码数目。|
|**屏幕关闭前处于非活动状态的分钟数**<sup>1</sup>|指定设备显示屏关闭之前的分钟数。|
|**允许指纹解锁**|允许使用指纹解锁设备。|
<sup>1</sup>对于 iOS 设备，配置“屏幕关闭前处于非活动状态的分钟数”和“需要提供密码之前处于非活动状态的分钟数”设置时，它们会按顺序应用。 例如，如果你设置的两个设置的值均为“5”分钟，屏幕在 5 分钟后将自动关闭，然后再过 5 分钟后该设备将锁定。 但是，如果用户手动关闭屏幕，第二个设置将立即应用。 在相同的示例中，用户关闭屏幕后，该设备将在 5 分钟后锁定。

### <a name="system-settings"></a>系统设置
所有设置均适用于 iOS 8.0 及更高版本。

|设置名|详细信息|
|----------------|-------|
|**允许屏幕截图**|允许用户以图像形式捕获屏幕内容。|
|**允许在锁定屏幕中使用控制中心**|允许用户在设备锁定时访问控制中心应用。|
|**允许在锁定屏幕中使用通知视图**|允许用户不解锁设备而访问通知视图。|
|**允许在锁定屏幕中使用今日视图**|允许用户在设备锁定时查看通知。|
|**允许使用不受信任的 TLS 证书**|允许设备使用不受信任的传输层安全性证书。|
|**允许提交诊断数据**|允许或阻止设备将诊断数据提交到 Apple。|
|**允许在锁定时使用 passbook**|允许用户在设备锁定时访问 Passbook 应用。|

### <a name="cloud-settings-for-documents-and-data"></a>文档和数据的云设置
所有设置均适用于 iOS 8.0 及更高版本。

|设置名|详细信息|
|----------------|-------|
|**允许备份到 iCloud**|允许用户将设备备份到 iCloud。|
|**允许将文档与 iCloud 同步**|允许将文档和键值同步到 iCloud 存储空间。|
|**允许将照片流与 iCloud 同步**|允许用户在其设备上启用“我的照片流”，该操作可将照片同步到 iCloud 并在所有用户设备上使用。|
|**需要加密的备份**|需要将任何设备备份进行加密。|
|**允许托管应用将数据同步到 iCloud**|允许你使用 Intune 管理的应用将数据同步到用户的 iCloud 帐户。|
|**允许 Handoff 在另一台设备上继续活动**|允许用户继续在其他 iOS 或 Mac OS X 设备上的 iOS 设备上启动的工作。|
|**允许 iCloud 照片共享**|将其设置为“否”以在设备上禁用“iCloud 照片共享”。|
|**允许 iCloud 照片库**|如果设置为“否”，则会禁用可供用户在云中存储照片和视频的 iCloud 照片库。   如果将其设置为“否”，则从设备中删除尚未从 iCloud 照片库完全下载到设备的所有照片。|

### <a name="application-settings-for-the-browser"></a>浏览器的应用程序设置
所有设置均适用于 iOS 8.0 及更高版本。

|设置名|详细信息|
|----------------|-------|
|**允许使用 Safari**|指定是否可以在设备上使用 Safari 浏览器。|
|**允许自动填充**|允许用户更改浏览器中的自动完成设置。|
|**允许使用弹出窗口阻止程序**|启用或禁用浏览器弹出窗口阻止程序。|
|**允许使用 Cookie**|允许浏览器使用 Cookie。|
|**允许使用 Java 脚本**|允许在浏览器中运行 Java 脚本。|
|**允许使用欺诈警告**|允许在浏览器中使用欺诈警告。|

### <a name="application-settings-for-apps"></a>应用的应用程序设置
所有设置均适用于 iOS 8.0 及更高版本。

|设置名|详细信息|
|----------------|-------|
|**允许安装应用**|允许设备访问应用商店和安装应用。|
|**需要提供密码来访问应用程序商店**|要求用户输入密码后才能访问应用商店。|
|**允许应用内购买**|允许在运行的应用中产生应用商店购买行为。|
|**允许在其他非托管应用中使用托管文档**|允许在任何应用中查看公司文档。<br>**示例：**你想要防止用户将文件从 OneDrive 应用保存到 Dropbox。 将此设置配置为“否”。 设备收到策略后（例如在重启后），将不再允许保存。|
|**允许在其他托管应用中使用非托管文档**|允许在公司托管的应用中查看任何文档。|
|**允许视频会议**|允许在设备上使用视频会议应用，如 FaceTime。|
|**允许用户信任新的企业应用的作者**|允许用户选择信任未从应用商店下载的应用。|


### <a name="application-settings-for-games"></a>游戏的应用程序设置
所有设置均适用于 iOS 8.0 及更高版本。

|设置名|详细信息|
|----------------|-------|
|**允许添加游戏中心好友**|允许用户在游戏中心添加好友。|
|**允许多玩家游戏**|允许用户在设备上玩多玩家游戏。|

### <a name="application-settings-for-media-content"></a>媒体内容的应用程序设置
所有设置均适用于 iOS 8.0 及更高版本。

|设置名|详细信息|
|----------------|-------|
|**分级区域**|选择区域，然后选择用户可以下载**电影**、**电视节目**和**应用**的最大分级。|
|**允许媒体存储中有成人内容**|允许设备访问存储中认定为成人的内容。|
|**允许用户从标记为“Erotica”的 iBook 商店下载内容**|允许用户下载“成人作品”类别的书籍。|


### <a name="device-capabilities-settings-for-hardware"></a>硬件的设备性能设置
所有设置均适用于 iOS 8.0 及更高版本。

|设置名|详细信息|
|----------------|-------|
|**允许照相机**|指定是否可以使用设备上的照相机。|
|**强制已配对的 Apple Watch 使用手腕检测**|启用后，Apple Watch 在未穿戴时不会显示通知。|
|**要求提供配对密码来传出 AirPlay 请求**|当用户使用 AirPlay 将内容流式传输到其他 Apple 设备时，需要配对密码。|

### <a name="device-capabilities-settings-for-cellular"></a>手机网络的设备性能设置
所有设置均适用于 iOS 8.0 及更高版本。

|设置名|详细信息|
|----------------|-------|
|**允许语音漫游**|当设备在移动电话网络中时允许语音漫游。|
|**允许数据漫游**|当设备在移动电话网络中时允许数据漫游。|
|**允许漫游时进行全局后台获取**|允许当设备在移动电话网络漫游时提取数据，例如电子邮件。|

### <a name="device-capabilities-settings-for-features"></a>功能的设备性能设置
所有设置均适用于 iOS 8.0 及更高版本。

|设置名|详细信息|
|----------------|-------|
|**允许使用 Siri**|允许在设备上使用 Siri 语音助手。|
|**允许在设备锁定时使用 Siri**|允许在设备锁定时使用 Siri 语音助手。|
|**允许语音拨号**|允许在设备上使用语音拨号功能。|
|**不允许托管应用使用 Airdrop**|停止托管的应用能够通过 。|


### <a name="settings-for-compliant-and-noncompliant-apps"></a>相容和不相容应用的设置
在“相容和不相容应用”列表中，使用以下信息指定相容或不相容应用列表。

> [!NOTE]
> 单个策略只能包含一个相容应用列表或一个不相容应用列表。 不能在同一策略中同时指定两个列表。

|设置名|详细信息|
|----------------|--------------------|
|**用户安装列出的应用时报告不相容情况**|列出用户不得安装和运行的应用（未由 Intune 托管）。|
|**用户安装未列出的应用时报告不合规性**|列出允许用户安装的应用。 为了保持相容状态，用户不得安装未列出的应用。 自动允许由 Intune 托管的应用。|
|**添加**|将应用添加到选定的列表。 在应用商店中指定你选择的名称（可选择使用应用发布者）和应用的 URL。 若要获取更多帮助，请参阅本主题后面的“如何指定应用商店的 URL”。|
|**导入应用**|导入你已在逗号分隔值文件中指定的应用列表。 在文件中使用此格式：应用程序名称、发布者和应用 URL。|
|**编辑**|编辑选定应用的名称、发布者和 URL。|
|**删除**|从列表中删除选定的应用。|

必须将包含合规和不合规应用设置的策略部署到用户组。

### <a name="kiosk-mode-settings"></a>展台模式设置

|设置名|详细信息|
|----------------|--------------------|
|**选择当设备处于展台模式时允许运行的托管应用**|选择“浏览”，然后指定当设备处于展台模式时允许运行的托管应用或来自商店的应用。 不允许在设备上运行其他应用。 若要获取更多帮助，请参阅本主题后面的“如何指定应用商店的 URL”。|
|**允许触摸**|启用或禁用设备上的触摸屏。|
|**允许屏幕旋转**|启用或禁用在用户旋转设备时更改屏幕方向。|
|**允许使用音量按钮**|启用或禁用设备上的音量按钮。|
|**允许使用响铃开关**|启用或禁用设备上的响铃（静音）开关。|
|**允许使用屏幕睡眠唤醒按钮**|启用或禁用设备上的屏幕睡眠唤醒按钮。|
|**允许自动锁定**|启用或禁用设备的自动锁定。|
|**启用单声道音频**|启用或禁用“单声道音频”辅助功能设置。|
|**启用语音朗读**|启用或禁用“VoiceOver”辅助功能设置，它能朗读设备上显示的文本。|
|**启用语音朗读调整**|启用或禁用语音朗读调整，它允许用户调整 VoiceOver 功能（例如，屏幕上文本的朗读速度）。|
|**启用缩放**|启用或禁用“缩放”辅助功能设置，它允许用户通过触摸来缩放设备显示。|
|**启用缩放调整**|启用或禁用缩放调整，它允许用户调整缩放功能。|
|**启用反转颜色**|启用或禁用“反转颜色”辅助功能设置，它可调整显示效果以帮助有视觉障碍的用户。|
|**启用反转颜色调整**|启用或禁用反色调整，它允许用户调整反转颜色功能。|
|**启用辅助触摸**|启用或禁用“辅助触摸”辅助功能设置，它可帮助用户执行可能难以执行的屏幕手势。|
|**启用辅助触摸调整**|启用或禁用辅助触摸调节，它允许用户调节辅助触摸功能。|
|**启用朗读选项**|启用或禁用“朗读所选项”辅助功能设置，它可朗读用户选择的文本。|
> [!NOTE]
> 以下说明适用于 iOS 设备的展台模式设置：
>
> -   必须使用 [Apple 配置器工具](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12)或 [Apple 设备注册程序](ios-device-enrollment-program-in-microsoft-intune.md)将设备置于监管模式后才能为 iOS 设备配置展台模式。 有关 Apple Configurator 工具的详细信息，请参阅 Apple 文档。
> -   如果在部署配置策略之后安装指定的 iOS 应用，则设备将在重启后才会进入展台模式。

### <a name="reference-information-for-compliant-and-noncompliant-apps"></a>相容和不相容应用的参考信息

使用“不相容应用报告”查看允许和阻止的应用的相容性。

##### <a name="to-run-the-noncompliant-apps-report"></a>运行不相容应用报告

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，选择“报告”&gt;“不合规应用报告”。

2.  选择你想要检查的设备组，选择要检查相容应用还是不相容应用，或是同时检查两者，然后选择“查看报告”。

#### <a name="how-to-specify-urls-to-app-stores"></a>如何指定应用商店的 URL
要在相容和不相容应用列表中或在“选择一个在设备处于展台模式时能够运行的托管应用”选项(仅限 iOS)中指定一个应用 URL，请使用以下格式:

1. 使用搜索引擎，查找你想在 iTunes 应用商店中使用的应用并打开该应用的页面。

2. 复制页面的 URL，并使用此 URL 配置的符合或不符合要求的应用列表或你想要在展台模式下运行的应用。

“示例：” 搜索“” 。 将要使用的 URL 为 https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8。

> [!NOTE]
> 你还可以使用 iTunes 软件查找应用程序，然后使用“复制链接”  命令获取应用的 URL。

### <a name="enrollment-settings"></a>注册设置
所有设置均适用于 iOS 8.0 及更高版本。

|设置名|详细信息|
|----------------|--------------------|
|**设备处于监督模式时允许激活锁定**|在已监督的 iOS 设备上启用激活锁定。|

### <a name="supervised-mode-settings"></a>监督模式设置
可以在运行 iOS 8.0 及更高版本的处于监督模式的设备上配置以下设置。

### <a name="supervised-mode-settings-for-device-restrictions"></a>设备限制的监督模式设置

|设置名|详细信息|
|----------------|--------------------|
|**允许帐户修改**|允许用户更改电子邮件配置等帐户设置。|
|**允许对应用的移动电话网络数据使用设置进行更改**|允许用户控制允许哪些应用使用移动电话网络数据。|
|**允许擦除设备上的所有内容和设置选项**|允许用户使用擦除设备上的所有内容和设置的选项。|
|**允许用户在设备设置中启用限制**|允许用户在设备上配置设备限制（家长控制）。|
|**允许主机配对控制 iOS 设备可与之配对的设备**|允许主机配对，以使管理员能够控制 iOS 设备可与之配对的设备。|
|**允许用户安装配置文件和证书**|允许用户安装配置配置文件和证书。|
|**允许修改设备名称**|允许用户更改设备的名称。|
|**允许修改密码**|允许添加、更改或删除设备密码。|
|**允许 Apple Watch 配对**|允许设备与 Apple Watch 配对。|
|**允许修改通知设置**|允许用户更改设备通知设置。|
|**允许修改壁纸**|允许用户更改设备墙纸。|

### <a name="supervised-mode-settings-for-feature-restrictions"></a>功能限制的监督模式设置

|设置名|详细信息|
|----------------|--------------------|
|**允许 AirDrop**|允许使用 AirDrop 功能，以与附近的设备相互传输内容。|
|**允许 Siri 从 Internet 查询用户生成的内容**|允许 Siri 访问网站以回答问题。|
|**使用 Siri 猥亵语言筛选器**|阻止 Siri 讲述猥亵语言。|
|**允许 Spotlight 搜索从 Internet 返回结果**|允许 Spotlight 搜索连接到 Internet 以提供更多的结果。|
|**允许查找单词定义**|允许使用 iOS 功能，该功能允许你突出显示一个词语并查找其定义。|
|**允许使用预测键盘**|允许使用建议用户可能所需单词的输入预测。|
|**允许自动更正**|让设备自动更正拼写错误的词。|
|**允许键盘拼写检查**|允许设备拼写检查程序。|
|**允许键盘快捷方式**|允许使用键盘快捷方式。|

### <a name="supervised-mode-settings-for-app-restrictions"></a>应用限制的监督模式设置

|设置名|详细信息|
|----------------|--------------------|
|**允许修改企业应用的信任设置**|让用户更改企业应用的信任设置。|
|**仅允许使用 Apple 配置和 iTune 来安装应用**|从设备主屏幕启用或禁用 App Store。 用户仍然可以使用 iTunes 或 Apple Configurator 工具来安装和更新应用。|
|**允许自动下载应用**|允许在其他设备上购买的应用自动下载到此设备。 此设置不会影响应用更新。|
|**允许对“查找我的好友”应用设置进行更改**|允许用户更改“查找我的好友”应用的设置。|
|**允许访问 iBooks 商店**|允许用户从 iBooks 商店浏览和购买书籍。|
|**允许在设备上使用“邮件”应用**|允许使用“邮件”应用发送短信。|
|**允许使用播客**|允许使用播客应用。|
|**允许使用音乐服务**|允许使用 Apple 音乐应用。|
|**允许 iTunes Radio 服务**|允许使用 iTunes Radio 应用。|
|**允许 Apple 新闻**|允许使用 Apple 新闻应用。|
|**允许游戏中心**|允许使用 Game Center 应用。|


### <a name="show-or-hide-apps"></a>显示或隐藏应用

使用“隐藏和显示应用列表”在运行 iOS 9.3 或更高版本的已监督设备上控制以下方面：

- 指定对用户隐藏的应用列表。 用户无法查看，或启动这些应用。
- 指定用户可以查看和启动的应用列表。 无法查看或启动其他应用。


#### <a name="how-to-create-a-hidden-or-shown-app-list"></a>如何创建隐藏或显示的应用列表

指定以下设置：

|设置名|详细信息|
|-|-|
|**隐藏和显示的应用列表**|如果想要创建的隐藏或显示的应用列表，请启用此设置。|
|**向用户隐藏列出的应用**|如果想要创建向用户隐藏的应用列表，请选择此选项。<br>创建这种列表类型时，除了 iOS **设置**和**电话**（适用于 iPhone）应用外，其他的所有应用都处于隐藏状态。|
|**仅向用户显示列出的应用**|如果想要创建向用户显示的应用列表，请选择此选项。<br>创建这种列表类型时，除了 iOS **设置**和 **电话**（适用于 iPhone）应用外，其他的所有应用都处于隐藏状态。<br>此外，必须将公司门户和任何已部署且使用 Intune 管理的应用添加到列表。|
|**添加**|将应用添加到选定的列表。<br>对于隐藏列表，必须为要隐藏的每个应用指定**名称**、**发布者**和**应用 URL 或捆绑 ID**。<br>对于显示的列表中，可以**选择托管应用**，它为你提供要从中选择使用 Intune 托管的应用列表，或选择应用商店应用，此后必须为要显示的每个应用指定**名称**、**发布者**和**应用 URL 或捆绑 ID**。|
|**导入应用**|导入你已在逗号分隔值文件中指定的应用列表。 在文件中使用格式、应用程序名称、发布者和应用 URL。|
|**编辑**|允许你编辑选定应用的名称、发布者和 URL。|
|**删除**|从列表中删除选定的应用。|

#### <a name="app-information-for-built-in-ios-apps"></a>内置 iOS 应用的应用信息

使用此列表中的信息识别想要显示或隐藏的内置 iOS 应用的名称、发布者和捆绑 ID。 如果想要显示或隐藏列表中的所有应用，可以将下面的数据复制到扩展名为 **.csv** 的文本文件中，然后使用“导入应用”选项同时导入所有应用。

```
,com.apple.AppStore,App Store,Apple
,com.apple.calculator,Calculator,Apple
,com.apple.mobilecal,Calendar,Apple
,com.apple.camera,Camera,Apple
,com.apple.mobiletimer,Clock,Apple
,com.apple.compass,Compass,Apple
,com.apple.MobileAddressBook,Contacts,Apple
,com.apple.facetime,FaceTime,Apple
,com.apple.mobileme.fmf1,Find Friends,Apple
,com.apple.mobileme.fmip1,Find iPhone,Apple
,com.apple.gamecenter,Game Center,Apple
,com.apple.mobilegarageband,GarageBand,Apple
,com.apple.Health,Health,Apple
,com.apple.iBooks,iBooks,Apple
,com.apple.MobileStore,iTunes Store,Apple
,com.apple.itunesu,iTunes U,Apple
,com.apple.Keynote,Keynote,Apple
,com.apple.mobilemail,Mail,Apple
,com.apple.MapsMaps,Apple
,com.apple.MobileSMS,Messages,Apple
,com.apple.Music,Music,Apple
,com.apple.news,News,Apple
,com.apple.mobilenotes,Notes,Apple
,com.apple.Numbers,Numbers,Apple
,com.apple.Pages,Pages,Apple
,com.apple.Photo-Booth,Photo Booth,Apple
,com.apple.mobileslideshow,Photos,Apple
,com.apple.podcasts,Podcasts,Apple
,com.apple.reminders,Reminders,Apple
,com.apple.MobileSafari,Safari,Apple
,com.apple.Preferences,Settings,Apple
,com.apple.stocks,Stocks,Apple
,com.apple.tips,Tips,Apple
,com.apple.videos,Videos,Apple
,com.apple.VoiceMemos,VoiceMemos,Apple
,com.apple.Passbook,Wallet,Apple
,com.apple.Bridge,Watch,Apple
,com.apple.weather,Weather,Apple


```




## <a name="custom-policy-settings"></a>自定义策略设置

使用 Microsoft Intune 的“iOS 自定义策略”将使用 [Apple Configurator 工具](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12)创建的设置部署到 iOS 设备。 使用此工具可以创建控制这些设备的操作的许多设置，并将其导出到配置的配置文件中。 然后可将此配置文件导入到 Intune iOS 自定义策略并将这些设置部署到组织中的用户和设备。

此功能允许你部署不能与 Intune 常规配置策略一起配置的 iOS 设置。

### <a name="prerequisites"></a>先决条件
在开始之前，必须已安装了 Apple Configurator并创建了包含需部署到用户或设备的设置的配置文件。 可从 [Mac 应用商店](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12)下载和了解 Apple Configurator。

> [!NOTE]
> Intune 不会报告 iOS 自定义策略中各个设置的合规性。 但会报告策略的总体合规性。

### <a name="general-settings"></a>常规设置

|设置名|详细信息|
    |----------------|--------------------|
    |**Name**|输入 iOS 自定义策略的唯一名称，以帮助你在 Intune 控制台中识别它。|
    |**描述**|提供对 iOS 自定义策略的概述以及可帮助你查找它的其他相关信息。|

### <a name="custom-settings"></a>自定义设置

|设置名|详细信息|
    |----------------|--------------------|
|**自定义配置的配置文件名称（对用户显示）**|提供策略的名称，该名称将显示在设备上以及 Intune 策略报告中。|
|**配置的配置文件**|选择“导入”，然后浏览到使用 Apple Configurator 创建的配置文件。 **注意：**确保从 Apple Configurator 工具导出的设置在要部署 iOS 自定义策略的设备上与 iOS 版本兼容。 有关如何解析不兼容的设置的信息，可搜索 [Apple 开发人员](https://developer.apple.com/)网站上的“配置描述文件参考”和“移动设备管理协议参考”。|
    |**配置的配置文件详细信息**|显示导入的配置文件的 XML 代码。|

### <a name="see-also"></a>另请参阅
[使用 Microsoft Intune 策略管理设备上的设置和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
