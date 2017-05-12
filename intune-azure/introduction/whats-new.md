---
title: "Microsoft Intune 预览版新增功能"
titleSuffix: Intune Azure preview
description: "了解 Intune Azure 预览版新增功能"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 04/29/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: f209429bbafe50530e90bbaf133f780f448a8c57
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---

# <a name="whats-new-in-the-microsoft-intune-preview"></a>Microsoft Intune 预览版新增功能

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

随着公共预览版的不断改进，添加了更多功能，以下是相关介绍。

> [!Note]
> 此页上提供了针对 Azure 门户预览列出的更改。 但是，鉴于 Intune 服务的更新方式，所做的更改可能无法立即使用。  在新门户功能可用之前，必须按顺序更新服务的多个组件。 在本月晚些时候推出时查找这些更改。

## <a name="april-2017"></a>2017 年 4 月

### <a name="support-for-managing-the-apple-classroom-app"></a>支持管理 Apple Classroom 应用

现在可以在 iPad 设备上管理 iOS Classroom 应用。 使用正确的班级和学生数据设置教师 iPad 上的 Classroom 应用，然后配置已注册到某个班级的学生 iPad，方便使用此应用进行控制。
有关详细信息，请参阅[配置 iOS 教育设置](../configure-devices/how-to-configure-ios-edu-settings.md)。

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>支持 Android 应用的托管配置选项 <!-- 621621 -->

Play Store 中支持托管配置选项的 Android 应用现在可以由 Intune 进行配置。  通过此功能，IT 可查看应用支持的配置值列表，并提供优质的引导式 UI，以便配置这些值。

### <a name="new-android-policy-for-complex-pins----722069---"></a>复杂 PIN 的新 Android 策略 <!-- 722069 -->

现在可以在运行 Android 5.0 及更高版本的设备的 Android 设备配置文件中设置数字复杂度的必需[密码](../configure-devices/device-restrictions-for-android.md#password)类型。  使用此设置可防止设备用户创建包含重复或连续数字（如 1111 或 1234）的 PIN。

### <a name="additional-support-for-android-for-work-devices"></a>对 Android for Work 设备的其他支持

- **管理密码及工作配置文件设置** <!-- 612808 -->

  通过新的 Android for Work 设备限制策略，现在可让你在管理的 Android for Work 设备上管理密码和工作配置文件设置。

- **允许在工作和个人配置文件之间共享数据** <!-- 1045102 -->

此 Android for Work 设备限制配置文件现在具有新的选项来帮助你配置工作和个人配置文件之间共享的数据。

- **限制工作和个人配置文件之间的复制和粘贴** <!-- 1046094 -->

  借助适用于 Android for Work 设备的新的自定义设备配置文件，现在可以限制是否允许在工作和个人应用之间进行复制和粘贴操作。

有关详细信息，请参阅 [Android for Work 的设备限制](../configure-devices/device-restrictions-for-afw.md)。

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>将 LOB 应用分配到 iOS 和 Android 设备 <!-- 1057568 -->

现在可以为用户或设备分配适用于 [iOS](../manage-apps/ios-lob-app.md)（.ipa 文件）和 [Android](../manage-apps/android-lob-app.md)（.apk 文件）的业务线 (LOB) 应用。

###  <a name="new-device-policies-for-ios----723774-723815-723826-723830---"></a>适用于 iOS 的新设备策略<!-- 723774, 723815, 723826, 723830 -->

- **主屏幕上的应用** - 控制用户在[其 iOS 设备的主屏幕](../configure-devices/home-screen-settings-for-ios.md)上看到的应用。 此策略将更改主屏幕的布局，但不会部署指定的任何未安装的应用。

- **与 AirPrint 设备的连接** - 控制 iOS 设备的最终用户可以连接到的 [AirPrint 设备](../configure-devices/air-print-settings-for-ios-and-macos.md)（网络打印机）。

- **与 AirPlay 设备的连接** - 控制 iOS 设备的最终用户可以连接到的 [AirPlay 设备](../configure-devices/airplay-settings-for-ios-devices.md)（如 Apple TV）。

- **自定义锁屏界面消息** - 配置用户将在其 iOS 设备的锁屏界面上看到的自定义消息（替换默认的锁屏界面消息）。 有关详细信息，请参阅[可用的设备操作](../manage-devices/what-is.md#available-device-actions)


### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>限制 iOS 应用的推送通知 <!-- 723767 -->

在 Intune 设备限制配置文件中，现在可以为 iOS 设备配置以下[通知设置](../configure-devices/app-notification-settings-for-ios.md)：

- 完全打开或关闭指定应用的通知。
- 在通知中心中打开或关闭指定应用的通知。
- 指定警报类型：“无”、“横幅”或“提醒”。
- 指定是否允许此应用的徽章。
- 指定是否允许通知声音。

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>配置 iOS 应用以单一应用模式自主运行 <!-- 737837 -->

可以使用 Intune 设备配置文件配置 iOS 设备，以[自主单一应用模式](../configure-devices/device-restrictions-for-ios.md#autonomous-single-app-mode-supervised-only)运行指定应用。 配置此模式并运行应用时，将锁定设备，因此该设备只能运行该应用。 举个例子，当你配置一个允许用户在设备上进行测试的应用时就是如此。 应用的操作完成或删除此策略时，设备将恢复正常状态。

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>为 iOS 设备上的电子邮件和 web 浏览配置受信任的域 <!-- 723765 -->

现在可以从 iOS 设备限制配置文件配置以下[域设置](../configure-devices/device-restrictions-for-ios.md#domains)：

- **未标记的电子邮件域** - 用户发送或接收的电子邮件如果不匹配在此处指定的域，将标记为不受信任。

- **托管的 Web 域** - 从此处指定的 URL 下载的文档将被视为托管(仅限 Safari)。  

- **Safari 密码自动填充域** - 用户只能在 Safari 中保存与你在此处指定的模式相匹配的 URL 的密码。 若要使用此设置，设备必须处于监督模式，不配置为用于多个用户。 （iOS 9.3 及更高版本）


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>iOS 公司门户中可用的 VPP 应用 <!-- 748782 -->

现在可以将 iOS 批量购买的 (VPP) 应用作为**可用**安装分配给最终用户。 最终用户需要具有 Apple Store 帐户才能安装该应用。

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>同步 Apple VPP 应用商店的电子书 <!-- 800878 -->

现在可以与 Intune [同步从 Apple 批量采购计划应用商店购买的书](../manage-apps/ios-vpp-apps.md)，并将其分配给用户。

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Samsung KNOX 标准版设备的多用户管理 <!-- 971988 -->

现在，运行 Samsung KNOX 标准版的设备支持 Intune 进行[多用户管理](../enroll-devices/enroll-android-and-knox-standard-devices.md)。 这意味着最终用户可以使用其 Azure Active Directory 凭据登录和注销设备，并且无论是否正在使用，都会集中管理设备。  当最终用户登录时，他们可以访问应用，还可以获得已应用的任何策略。 用户注销时，会清除所有应用数据。

### <a name="additional-windows-device-restriction-settings----818566---"></a>其他 Windows 设备限制设置 <!-- 818566 -->

我们添加了对其他 [Windows 设备限制设置](../configure-devices/device-restrictions-for-windows-10.md)的支持，如其他 Microsoft Edge 浏览器支持、设备锁屏界面自定义、开始菜单自定义、Windows 聚焦搜索集壁纸和代理设置。

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Windows 10 创意者更新的多用户支持 <!-- 822547 -->

我们为运行 Windows 10 创意者更新的设备和加入 Azure Active Directory 域的设备添加了对[多用户管理](../enroll-devices/enroll-windows-devices.md)的支持。 这意味着当不同的标准用户使用其 Azure AD 凭据登录设备时，他们将收到分配给其用户名的所有应用和策略。 用户当前无法将公司门户用于自助服务方案，如安装应用。

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Windows 10 电脑的 Fresh Start <!-- 1004830 -->

现在提供 Windows 10 电脑的全新 [Fresh Start 设备操作](../manage-devices/what-is.md#available-device-actions)。  发出此操作时，电脑上安装的任何应用都将被删除，而且电脑会自动更新到最新版本的 Windows。 这可用于删除新电脑通常附带的预先安装的 OEM 应用。 发出此设备操作时可以配置是否保留用户数据。

### <a name="additional-windows-10-upgrade-paths----903672---"></a>Windows 10 其他升级途径<!-- 903672 -->

现可创建[版本升级策略](../configure-devices/how-to-configure-windows-10-edition-upgrade.md)，将设备升级到以下的其他 Windows 10 版本：

- Windows 10 专业版
- Windows 10 专业版 N
- Windows 10 专业教育版
- Windows 10 专业教育版 N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>批量注册 Windows 10 设备 <!-- 747607 -->

现在可以使用 Windows 配置设计器 (WCD) 将运行 Windows 10 创意者更新的大量设备加入到 Azure Active Directory 和 Intune。 若要启用 Azure AD 租户的[批量 MDM 注册](../enroll-devices/bulk-enroll-windows.md)，请使用 Windows 配置设计器创建将设备加入你的 Azure AD 租户的预配程序包，并将程序包应用到你想要批量注册和管理的公司所有的设备。 将程序包应用到设备后，设备将加入 Azure AD 并注册 Intune，以供 Azure AD 用户登录。  Azure AD 用户是这些设备上的标准用户并接收分配的策略和必需的应用。 目前不支持自助服务和公司门户方案。

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----581122-736644---"></a>PIN 和托管存储位置的新 MAM 设置 <!-- 581122, 736644 -->

现在这两个新的应用设置可用于帮助你处理移动应用程序管理 (MAM) 方案：

- **托管设备 PIN 时禁用应用 PIN** - 检测注册设备上是否存在设备 PIN，如果是，则忽略应用保护策略触发的应用 PIN。 此设置允许减少用户在注册设备上打开已启用 MAM 的应用程序时所看到的 PIN 提示次数。 此功能适用于 Android 和 iOS。

- **选择可将公司数据保存到其中的存储服务** - 允许你指定可将公司数据保存到哪些存储位置。 用户可以保存到所选存储位置服务，这意味着将阻止所有未列出的其他存储位置服务。

  支持的存储位置服务列表：

  - OneDrive
  - Business SharePoint Online
  - 本地存储

### <a name="help-desk-troubleshooting-portal----907448---"></a>支持人员疑难解答门户<!-- 907448 -->

新的[疑难解答门户](../manage-users/help-desk.md)允许技术支持人员和 Intune 管理员查看用户及其设备，并执行任务以解决 Intune 技术问题。

## <a name="march-2017"></a>2017 年 3 月

### <a name="support-for-ios-lost-mode---431695--"></a>对 iOS 丢失模式的支持<!--431695-->

对于 iOS 9.3 和更高版本设备，Intune 增加了对**丢失模式**的支持。 现在可以锁定设备以防止所有使用并显示设备锁定屏幕的消息和联系人电话号码。

最终用户将无法解锁设备，直到管理员禁用丢失模式。 启用丢失模式后，可以使用“查找设备”操作在 Intune 控制台中的地图上显示该设备的地理位置。

此设备必须是处于监督模式下通过 EDP 注册的公司所有的 iOS 设备。

有关详细信息，请参阅[什么是 Microsoft Intune 设备管理](../manage-devices/what-is.md)？

### <a name="improvements-to-device-actions-report---677150--"></a>改进设备操作报告<!--677150-->

改进了设备操作报告，进而改善了性能。 此外，现可按状态筛选报告。 例如，可筛选报告以仅显示“已完成”的设备操作。

### <a name="actions-for-non-compliance---730266--"></a>针对不合规的操作<!--730266-->

“针对不合规的操作”是合规性策略的新功能，允许在不合规的设备上执行操作。 可指定单个或多个操作，并指定这些操作必然会发生的时间段。 例如，可在设备变为不合规后，立即通过电子邮件通知该不合规设备的用户，或可在 3 天宽限期后，通过条件性访问阻止不合规设备访问公司资源。

### <a name="custom-app-categories---748805--"></a>自定义应用类别<!--748805-->

现可以为添加到 Intune 的应用创建、编辑和分配类别。 目前，只能以英文指定类别。
请参阅[如何将应用添加到 Intune](../manage-apps/add-apps.md)。

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>将 LOB 应用分配给未注册设备的用户<!--748823-->

现在，无论用户的设备是否已注册 Intune，都可以从应用商店向用户分配业务线应用。 如果用户设备未注册 Intune，他们必须转到公司门户网站（而非公司门户应用）安装它。

### <a name="new-compliance-reports---846671--"></a>新符合性报告<!--846671-->

现可通过符合性报告了解设备在公司中的符合性状态，以便快速解决用户遇到的与符合性相关的问题。 可查看以下相关信息

- 设备的总体符合性状态
- 单个设置的符合性状态
- 单个策略的符合性状态

还可使用这些报告向下钻取各个设备，查看影响该设备的特定设置和策略。

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接访问 Apple 注册方案<!--951869-->

对于在 2017 年 1 月之后创建的 Intune 帐户，Intune 支持在 Azure 预览门户中使用注册设备工作负荷直接访问 Apple 注册方案。 以前，仅能通过经典 Intune 门户中的链接访问 Apple 注册预览版。 2017 年 1 月之前创建的 Intune 帐户需要进行一次性迁移，然后才能使用 Azure 中的这些功能。 迁移的计划目前尚未公布，但详细信息将尽快发布。 强烈建议创建一个试用帐户，在现有帐户无法访问预览版时测试新体验。


## <a name="february-2017"></a>2017 年 2 月

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>限制移动设备注册的功能<!--747600, 795782-->
Intune 新增了注册限制，可控制允许注册的移动设备平台。 Intune 将移动设备平台分为 iOS、macOS，Android、Windows 和 Windows Mobile。

* 限制移动设备注册不会限制电脑客户端注册。  
* 阻止个人自有设备的注册有一个附加选项，该选项仅适用于 iOS 和 Android。

Intune 将所有新设备都标记为个人所有，除非 IT 管理员将设备标记为公司所有，如[本文](https://docs.microsoft.com/intune/deploy-use/manage-corporate-owned-devices)所述。

### <a name="view-all-actions-on-managed-devices---677150--"></a>查看托管设备上的所有操作<!--677150-->
新添加的__设备操作__报表显示了在设备上执行远程操作（如出厂重置）的操作者，还额外显示了该操作的状态。 请参阅 [What is device management?](https://docs.microsoft.com../manage-devices/what-is.md)（什么是设备管理？）。

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>非托管设备可访问已分配的应用<!--664691-->
公司门户网站上的设计更改之一是，iOS 和 Android 用户能够在其非托管设备上安装分配到的“可用且无需注册”设备。 用户可使用其 Intune 凭据登录到公司门户网站，并查看分配到的应用列表。 “可用且无需注册”应用的应用包可通过公司门户网站进行下载。 需要注册才能安装的应用不受此更改影响，如果用户想安装这类应用，则会提示用户注册其设备。

### <a name="custom-app-categories---748805--"></a>自定义应用类别<!--748805-->
现可以为添加到 Intune 的应用创建、编辑和分配类别。 目前，只能以英文指定类别。
请参阅[如何将应用添加到 Intune](../manage-apps/add-apps.md)。

### <a name="display-device-categories---814654--"></a>显示设备类别<!--814654-->
现在可以将设备类别作为设备列表中的一列进行查看。 并且还可以在设备属性边栏选项卡的属性部分编辑该类别。 请参阅[如何将应用添加到 Intune](../manage-apps/add-apps.md)。

### <a name="configure-windows-update-for-business-settings---776716--"></a>配置 Windows Update for Business 设置<!--776716-->

Windows 即服务是为 Windows 10 提供更新的新方式。 从 Windows 10 开始，任何新的功能更新和质量更新都将包含所有此前更新的内容。 这意味着，只要安装了最新更新，你的 Windows 10 设备将完全保持最新状态。 与以前版本的 Windows 不同的是，现在必须安装完整的更新，而不是部分更新。

借助 Windows Update for Business 可以简化更新管理体验，不需要批准设备组的单个更新。 通过配置更新推出策略仍可以管理环境中的风险，并且 Windows 更新将确保在适当的时间安装更新。 Microsoft Intune 提供在设备上配置更新设置的功能，使你能够延迟更新安装。 Intune 不会存储更新，仅存储更新策略分配。 设备直接访问 Windows 更新以进行更新。使用 Intune 来配置和管理 **Windows 10 更新通道**。 更新通道包含一组设置，可配置何时以及如何安装 Windows 10 更新。 有关详细信息，请参阅[配置 Windows Update for Business 设置](../configure-devices/how-to-configure-windows-update-for-business.md)。

## <a name="january-2017"></a>2017 年 1 月

### <a name="assign-line-of-business-apps-whether-or-not-devices-are-enrolled---748823--"></a>分配业务线应用（无论设备是否注册）<!--748823-->
现在，无论用户的设备是否已注册 Intune，都可以从应用商店向用户分配业务线和应用。 如果用户设备未注册 Intune，他们必须转到公司门户网站（而非公司门户应用）安装它。 请参阅[什么是应用管理](../manage-apps/what-is-app-management.md)。

### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them"></a>解决 iOS 设备处于非活动状态，或管理控制台不能与其通信的问题
如果用户的设备失去与 Intune 的联系，可向其提供新的故障排除步骤，帮助他们重新获得公司资源的访问权限。 请参阅[设备处于非活动状态，或管理控制台不能与其通信](../enroll-devices/troubleshoot-device-enrollment.md#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them)。

## <a name="december-2016-initial-release"></a>2016 年 12 月（初始版本）

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Azure 门户公开预览版中的电信费用管理集成<!--747605-->
现在，我们将开始在 Azure 门户中预览与第三方电信费用管理 (TEM) 服务的集成。 可以使用 Intune 强制实施对国内和漫游数据使用的限制。 我们将使用 [Saaswedo](http://www.saaswedo.com) 开始这些集成。 若要在试用租户中启用此功能，请[联系 Microsoft 支持](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)。

- 将应用从应用商店部署到 iOS、Android 和 Windows 设备并对其进行管理
- 将业务线 (LOB) 应用部署到 iOS、Android 和 Windows 设备并对其进行管理
- 将批量购买应用部署到 iOS 和 Windows 设备并对其进行管理
- 部署和管理适用于 Android、iOS 和 Windows 设备的 Web 应用
- iOS 托管应用配置描述文件
- 配置应用保护策略，并将业务线应用部署到未向 Intune 注册的设备
- VPN 配置文件、每个应用 VPN、Wi-Fi、电子邮件和证书配置文件
- 相容性策略
- Azure AD 的条件性访问
- 本地 Exchange 的条件性访问
- 设备注册
- 基于角色的访问控制

## <a name="deprecated-features-in-the-azure-portal"></a>Azure 门户中的弃用功能

### <a name="support-for-row-by-row-review-of-hardware-identifiers"></a>支持逐行查看硬件标识符
对于 IMEI 号码和 Apple 序列号，Azure 门户不支持逐行查看硬件标识符。 在经典 Intune 控制台中，可以从逗号分隔值 (.csv) 文件导入详细信息，然后覆盖单个硬件标识符的现有详细信息。 Azure 门户提供一种单一、简化的选项，此选项可自动覆盖所有硬件标识符的详细信息，或忽略现有标识符的新详细信息。

#### <a name="how-this-affects-you"></a>此更改的影响
在 Azure 门户中，你将无法逐行决定要更新哪些国际移动设备标识 (IMEI) 设备。 经典 Intune 控制台将继续支持此功能。

#### <a name="how-to-get-ready-for-this-change"></a>如何针对此更改做好准备
我们提前提供此信息，如果此更改将对你产生影响，你可以提醒支持管理员注意。 预计在 2017 年上半年向 Azure 门户迁移时将继续使用此更改。


### <a name="support-for-default-corporate-device-enrollment-profiles-in-apple-dep"></a>支持 Apple DEP 中默认的企业设备注册配置文件
Azure 门户不支持 Apple 设备注册计划 (DEP) 设备序列号的“默认”公司设备注册配置文件。 经典 Intune 控制台中提供的此功能将停用，以防止无意中分配配置文件。 在 Azure 门户中，从 Apple DEP 帐户同步的序列号最初将不会分配公司设备注册配置文件。

#### <a name="how-this-affects-you"></a>此更改的影响
在 Azure 门户中，你将无法跨所有 Apple 设备设置默认配置文件策略。 经典 Intune 控制台将继续支持此功能。

#### <a name="how-to-get-ready-for-this-change"></a>如何针对此更改做好准备
我们提前提供此信息，如果此更改将对你产生影响，你可以提醒支持管理员注意。 预计在 2017 年上半年向 Azure 门户迁移时将继续使用此更改。

