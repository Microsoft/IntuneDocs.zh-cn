---
title: "早期发行版本 | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: noindex,nofollow
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: fd1e154aed6b2afecb7a7b24b927f7a5f92acba9
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="previous-intune-releases"></a>早期 Intune 发行版本

此页是 [Microsoft Intune 的新增功能](whats-new-in-microsoft-intune.md)中的声明列表。

[!INCLUDE[wit_nextref](../includes/whats-new-last-six-months.md)]

## <a name="july-2016"></a>2016 年 7 月

### <a name="app-management"></a>应用管理

__改善应用预配配置文件更新体验__ Apple iOS 业务线移动应用附带预配配置文件和证书签名的代码。 当应用在 iOS 设备上运行时，iOS 会确认 iOS 应用的完整性，并强制实施由预配配置文件定义的策略。

用于签署应用的企业签名证书通常持续 3 年。 但是，预配配置文件将在 1 年后过期。 利用此更新，Intune 会为你提供一些工具，用于主动地将新预配配置文件策略部署到安装了即将到期的应用而证书仍有效的设备。 有关详细信息，请参阅[使用 iOS 移动预配配置文件策略以保持你的业务线应用最新](/intune-classic/deploy-use/ios-mobile-app-provisioning-profiles)。
<!--- TFS 1280247--->

__用于 Intune 应用的 SDK Xamarin 已推出__ Intune App SDK Xamarin 组件允许在使用 Xamarin 生成的移动 iOS 和 Android 应用中启用 Intune 移动应用管理功能。 你可以在 [Xamarin 应用商店](https://components.xamarin.com/view/Microsoft.Intune.MAM)中或在 [Microsoft Intune Github 页面](https://github.com/msintuneappsdk)上找到该组件。
<!--- TFS 1061478 --->

### <a name="device-management"></a>设备管理
__提高了设备注册限制__ Intune 将每个用户的最大可配置设备注册限制从 5 提高到了 15。
<!---TFS 1289896 --->

运行 Intune 客户端软件的 Windows 电脑的 TeamViewer 集成____
[TeamViewer](/intune-classic/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client)。
<!---TFS 1284856--->

### <a name="company-portal-updates"></a>公司门户更新

__公司门户网站__
- **改善了注册 Windows 设备时的最终用户体验**<br/>
使用条件访问时，Windows 8.1、Windows 10 桌面版和 Windows 10 移动版的注册步骤已在公司门户网站中阐明。 用户现在将看到单独的“设备注册”和“工作区加入”步骤，从而在他们遇到工作区加入 (WPJ) 失败时更易于看到设备的状态以及完成此过程。 执行单独的步骤还可以简化 IT 管理员排除故障的过程。 以前，当最终用户尝试注册并且 WPJ 除外的所有注册步骤都成功时，已注册的设备将不出现在用户要标识的设备列表中，因而使用户感到困惑。

__Android__
- **Android 公司门户应用**<br/>
如果 Android 最终用户看到一条错误消息指出其设备缺少所需的证书，用户可以点击“如何解决此问题”按钮了解相应解决[步骤](/intune-classic/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues)，这些步骤中包含 IT 管理员可用于修复证书问题的步骤。

- **限制旁加载的应用安装到注册的设备**<br/>
Android 设备不能再通过公司门户网站安装应用程序，除非使用适用于 Android 的 Intune 公司门户应用已在 Intune 中注册设备。
<!---TFS 1299082--->

__iOS__
- **对 iOS 公司门户应用中设备注册管理器帐户的更改**<br/>
若要提高性能和可扩展性，Intune 不再在 iOS 公司门户应用的“**我的设备**”窗格中显示所有设备注册管理器 (DEM) 设备。 仅显示运行该应用的本地设备，且仅限该设备通过公司门户应用注册的情况下。

DEM 用户可能会在本地设备上执行操作，但只能从 Intune 管理员控制台远程管理其他已注册设备。 此外，Intune 将不支持通过 Apple 设备注册计划或 Apple 配置器工具使用 DEM 帐户。 这两种注册方法已支持共享的 iOS 设备的无用户注册。

当共享设备的无用户注册不可用时，仅使用 DEM 帐户。 有关详细信息，请参阅[使用 Microsoft Intune 中的“设备注册管理器”注册企业自有设备](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)。
<!---TFS 1233681--->

### <a name="change-of-names-for-windows-features"></a>对 Windows 功能名称的更改
- [Microsoft Passport for Windows](/intune-classic/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune) 现在称为 **Windows Hello 企业版**。
- [企业数据保护](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune)现在称为 **Windows 信息保护**。


## <a name="june-2016"></a>2016 年 6 月
### <a name="intune-service-health"></a>Intune 服务运行状况
Intune 服务运行状态信息已随同其他 Microsoft 服务一起移到一个中心位置。 现在，你可在服务运行状态下的 Office 365 管理门户中找到此信息。 有关详细信息，请参阅[此博客文章](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/)。

### <a name="app-management"></a>应用管理
- **增强的 Windows 10 企业数据策略配置体验。** 我们围绕创建应用规则、指定网络边界定义和其他企业数据保护设置增强了 Windows 10 企业数据保护策略配置体验。 若要了解详细信息，请参阅 [Create an enterprise data protection (EDP) policy using Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune)（使用 Microsoft Intune 创建企业数据保护 (EDP) 策略）。


### <a name="device-management"></a>设备管理
- **Windows Defender 策略设置，可以避免可能不需要的应用。** 名为“**可能不需要的应用程序检测**”的新 Windows Defender 设置已被添加到 Windows 10 桌面版和移动版的常规配置。 你可以使用此设置以防止已注册的 Windows 台式计算机运行被 Windows Defender 分类为可能不需要的软件。 你可以防止这些应用程序运行，或使用审核模式在安装了不需要的应用程序时进行报告。 有关详细信息，请参阅 [Microsoft Intune 中的 Windows 10 策略设置](/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune)。
<!---TFS 1244478--->

### <a name="conditional-access"></a>条件性访问
- **Intune 的 Cisco ISE 网络访问控制策略。**  使用 Cisco 标识服务引擎 (ISE) 2.1 并使用 Microsoft Intune 的客户可以在 ISE 中设置网络访问控制策略。

    此策略下，需要使用 WiFi 或 VPN 连接到网络的设备必须在符合以下条件后才被允许访问：

    * 必须由 Intune 进行管理
    * 必须符合任何已部署的 Intune 合规性策略

 非合规设备的最终用户将被提示注册和修正任何合规性问题以获取访问权限。
- **浏览器的条件性访问。** 可以为 [Exchange Online](/intune-classic/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune) 设置条件访问策略，以便仅允许通过托管且合规的 iOS 和 Android 设备上受支持的 Web 浏览器对其进行访问。 尝试通过 iOS 和 Android 设备登录到 Outlook Web Access (OWA) 和 SharePoint 站点的最终用户，系统将提示通过 Intune 注册其设备以及在完成登录前解决任何非合规性问题。
<!---TFS 1175844--->

- **Dynamics CRM Online 支持条件性访问。** 可以为 [Dynamics CRM Online](/intune-classic/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune) 设置条件访问策略，以便仅允许托管且合规的 iOS 和 Android 设备对其进行访问。 系统将提示尝试登录到 iOS 和 Android 设备上的 Dynamics CRM 移动应用的最终用户注册 Intune 并在登录完成前修正任何非合规性问题。
<!---TFS1295358--->

### <a name="intune-company-portal-updates"></a>Intune 公司门户更新

__Android 公司门户应用__

- 当 IT 管理员应用了新的“要求设备不允许安装来自未知源的应用 (Android 4.0 +)”策略时，Android 4.0 或更高版本设备的最终用户将看到消息“必须禁用来自未知来源的安装”。 用户将需要转到“设置” > “安全”，然后关闭“未知源”。 通过合规性消息中的链接，用户可获取有关该消息和为什么需要禁用该设置的详细[信息](/intune-user-help/you-are-asked-to-turn-off-unknown-sources-android)。

- 当 IT 管理员应用了新的“要求设备已启用扫描应用的安全威胁 (Android 4.0 +)”策略时，Android 4.0 或更高版本设备的最终用户将看到消息“扫描设备的安全威胁”。 用户将需要转到“设置” > “Google” > “安全”，然后打开“扫描设备的安全威胁”。 通过合规性消息中的链接，用户可获取有关该消息和为什么需要启用该设置的详细[信息](/intune-user-help/you-are-asked-to-turn-on-scan-device-for-security-threats-android)。

- 当 IT 管理员应用了新的“要求禁用 USB 调试 (Android 4.2 +)”策略时，Android 4.2 或更高版本设备的最终用户将看到消息“必须禁用 USB 调试”。 用户将需要转到“设置” > “开发人员”选项，然后关闭“USB 调试”。 通过合规性消息中的链接，用户可获取有关该消息和为什么需要禁用该设置的详细[信息](/intune-user-help/you-are-asked-to-turn-off-usb-debugging-android)。

- 当 IT 管理员应用新的“最低 Android 安全修补程序级别 (Android 6.0+)”策略时，Android 6.0 或更高版本设备用户会看到消息“此设备不符合最低 Android 安全修补程序级别”。 用户将需要安装所需的安全修补程序。 通过合规性消息中的链接，用户可获取有关如何安装所需安全修补程序并查看当前已安装的安全修补程序的[信息](/intune-user-help/you-are-asked-to-turn-on-scan-device-for-security-threats-android)。

__iOS 公司门户应用__

- 当最终用户安装业务线应用时，现在它们将看到改进的应用安装体验。 如果应用安装要花很长时间，用户可以手动同步设备以强制继续同步过程。 若要查看最终用户说明，请参阅[手动同步 iOS 设备](/intune-user-help/sync-your-device-manually-ios)。

- 适用于 iOS 的 Microsoft Intune 公司门户应用已更新，可支持 iOS 8.0 和更高版本。 此更新意味着，仅当设备正在运行 iOS 8.0 或更高版本时，最终用户才可在 Intune 中安装公司门户应用并注册新设备。 如果用户已注册运行不受支持的 iOS 版本的设备，则这些用户可以继续使用其设备上的公司门户应用。

## <a name="may-2016"></a>2016 年 5 月
所有这些功能也受混合部署 (Configuration Manager with Intune) 支持。 有关新的混合功能的详细信息，请查看[混合新增功能](https://technet.microsoft.com/library/mt718155.aspx)页。

### <a name="documentation"></a>文档
欢迎使用 [docs.microsoft.com](https://docs.microsoft.com/intune) 预览版本！
这是一个全新的新式内容平台，旨在使作为我们客户的你能更容易地理解和使用 Intune。
若要了解所有新增功能，请参阅 [Introducing docs.microsoft.com](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/)（docs.microsoft.com 简介）

### <a name="intune-service-health"></a>Intune 服务运行状况
Intune 服务运行状态信息已随同其他 Microsoft 服务一起移到一个中心位置。 现在你可在**服务运行状态**下的 [Office 365 管理门户](https://portal.office.com/Admin/Default.aspx)中找到此信息。
有关详细信息，请参阅[此博客文章](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/)。

### <a name="app-management"></a>应用管理
- **MAM SDK：支持 PIN 长度配置。** 你将能够指定类似于设备 PIN 的 MAM 应用的 PIN 的长度。 这将要求最终用户符合你设置的新限制。 他们将看到一个稍经修改的 PIN 屏幕来解释较长输入。 有关详细信息，请参阅[适用于 Android 的 MAM 策略设置](/intune-classic/deploy-use/ios-mam-policy-settings)。

- **Skype for Business iOS 版和 Android 版。** 你现在可以通过 [MAM 以 Skype for Business 为目标，而不需要注册策略](/intune-classic/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)。 用户登录后，将应用 MAM 策略。

- **可通过 MAM 策略管理的新应用。** 适用于 Android 的 Microsoft Word、Excel 和 PowerPoint 应用现在可与未向 Intune 注册的设备上的 MAM 策略相关联。 有关支持的应用的完整列表，请转到 [Microsoft Intune application partners](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx)（Microsoft Intune 应用程序合作伙伴）页上的 Microsoft Intune mobile application gallery（Microsoft Intune 移动应用程序库）。


### <a name="company-portal-updates"></a>公司门户更新

#### <a name="android-company-portal-app"></a>Android 公司门户应用
- **最终用户 toast 通知**：当最终用户从公司门户注册设备或删除设备时，现在他们将会看到来自 Andoid 公司门户应用的 toast 通知。

- **对 Android 公司门户应用中设备注册管理器帐户的更改。** 若要提高性能和可扩展性，Intune 不再在 Android 公司门户应用的“我的设备”窗格中显示所有设备注册管理器 (DEM) 设备。 仅显示运行该应用的本地设备，且仅限该设备通过公司门户应用注册的情况下。 DEM 用户可能会在本地设备上执行操作，但只能从 Intune 管理员控制台远程管理其他已注册设备。

#### <a name="company-portal-website"></a>公司门户网站
- **公司门户网站：设备标识横幅将向最终用户提供详细信息。** 最终用户现在能够更轻松地标识他们在使用公司门户网站时所选的设备。 如果选择了错误的设备，他们将能够通过点击主页标题栏中的**点击此处**链接选择正确的设备。

### <a name="service-deprecation"></a>服务弃用
- **Intune 查看器应用。** 随着新的 RMS 共享应用的发布，我们将从 2016 年 8 月起删除以下 Intune 查看器应用：
    - Intune AV 查看器
    - Intune PDF 查看器
    - Google Play 中适用于 Android 的 Intune 图像查看器

  建议使用适用于 Android 的 Rights Management 应用（RMS 共享）而不是使用 Intune 查看器应用，前者只需部署一个应用而不是三个单独的应用便可安全地查看 Android 设备上的公司文件。 了解有关 RMS 共享应用（具有指向文档的链接）的详细信息。

- **通知规则删除的自定义组目标。**
Intune 通知规则定义将从 Intune 向其发送电子邮件警报的人员。 当前，你可将通知规则配置为向你创建的 Intune 设备组中的设备所有用户发送电子邮件。 约从 2016 年 6 月 1 日起，已不再支持目标用户创建组。

    当前，若要为从 Microsoft Intune 管理控制台创建的组指定通知规则，应采用以下步骤：

    在**管理员**工作区，单击**通知规则**  >  **创建新规则**

    在创建通知规则向导的步骤二中，选择此规则所针对的设备组。 将从 Intune 控制台中删除“选择设备组”这一步骤。

    此更改的初步时间线如下：
    - 2016 年 6 月，新租户将看不到创建通知规则向导的步骤二。 正在退出的租户不受影响。
    - 2016 年 8 月左右，某些正在退出的租户将看不到向导中的“选择设备组”。
    - 2016 年 10 月左右，我们期望所有租户将不会看到向导中的“选择设备组”。


- **iOS 公司门户应用的支持更改**。 未来数月中，Microsoft Intune 公司门户应用 iOS 版将会更新，更新后仅支持运行 iOS 8.0 或更高版本的设备。 用户将无法注册运行 iOS 8.0 以下版本的新设备。 已注册的运行 iOS 8.0 以下版本的设备将继续受管理，且在有限时间内，能够继续使用公司门户应用。 但是，只有 iOS 8.0 或更高版本的设备才能访问最新版本的公司门户应用。 我们鼓励你通知用户更新到 iOS 8.0 或更高版本以充分利用 Intune 的新功能。  


## <a name="april-2016"></a>2016 年 4 月
所有这些功能也支持混合客户（与 Intune 集成的 Configuration Manager）。

### <a name="app-management"></a>应用管理
- **MAM 用户合规性。**
现在，你可以查看 Azure Active Directory (AAD) 租户中的任何用户的应用程序管理策略的[状态](/intune-classic/deploy-use/monitor-mobile-app-management-policies-with-Microsoft-Intune)。 这包括：
   - 设备
   - 在设备上的应用

   状态值：

   **已签入**：指示该策略已部署到用户，以及应用已用在工作环境中且已成功接收到该策略。

    **未签入**：指示策略已部署到用户，但应用从那时起尚未在工作环境中使用。


- **防止 Outlook 联系人同步的 MAM 控件 (Android)。**
新设置可用于[移动应用程序管理](/intune-classic/deploy-use/wipe-managed-company-app-data-with-Microsoft-Intune)，已保存至本机通讯簿的联系人将被删除。 最初，Android 设备上的 Outlook 应用程序支持此新设置。

### <a name="device-management"></a>设备管理
- **公司拥有的设备的电话号码标识。** 例如，当运行移动设备清单报表时，现在使用其完整的电话号码标识归类为“企业”的手机。 BYOD 电话号码将继续使用 **** 屏蔽，仅显示最后 4 位数字。


### <a name="company-portal-updates"></a>公司门户更新
**Android 公司门户应用**未在 Intune 注册其设备和未安装正确证书的用户将不能登录到 Android 公司门户应用，并且会看到以下消息：“无法登录，因为设备缺少必需的证书”。 该消息包含“如何解决此问题”的链接，用户可以点击以查看关于安装证书的说明。 若要查看最终用户解决此问题的步骤，请参阅[设备缺少必需的证书](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing)。

**iOS 公司门户应用**已添加“下拉刷新”操作支持以刷新主页上的内容，其中包括列出的应用、设备以及 IT 联络信息。 “下列刷新”操作不会检查合规性或策略信息，这可以通过选择当前设备的磁贴，然后点击“同步”按钮来实现。

**Windows 10 移动版和 Windows Phone 8.1 公司门户应用**当最终用户安装业务线应用时，他们现在将了解到改进后的应用安装体验。 如果应用安装要花很长时间，用户可以手动同步设备以强制继续同步过程。 若要查看最终用户说明，请参阅[手动同步设备以加速应用安装](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually)。

**公司门户网站**当 Windows 10 移动版和 Windows Phone 8.1 用户正在安装业务线应用时，现在他们将看到以下新状态，向他们提供有关安装状态的详细信息：

* **等待设备进行同步** – 用户已点击“安装”，并且设备现在尝试与 Intune 基础结构进行同步。 必须先同步，然后才能完成安装。 “正在等待设备进行同步”消息也是一个链接，用户可以点击以查看[说明](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually)，了解如果同步过程需要很长时间或已停止，如何手动将设备与 Intune 同步。
* **正在下载** – 正在处理用户的下载请求，且设备正在下载并安装应用。

添加这些状态之前，如果应用安装需要很长时间，用户将感到困惑，因为他们只能看到“正在安装”状态，而这可能会在屏幕上保持数个小时。 添加新的状态意味着，现在用户可以点击“正在等待设备进行同步”链接，并按照说明进行操作以强制继续同步过程，而不是呼叫支持部门。

>[!div class="step-by-step"]

>[&larr;**Intune 的新增功能**](whats-new-in-microsoft-intune.md)    

