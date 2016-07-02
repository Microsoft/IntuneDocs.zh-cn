---
title: "早期发行版本 | Microsoft Intune"
description: 
keywords: 
author: Lindavr
manager: jeffgilb
ms.date: 06/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: noindex,nofollow
ms.reviewer: mamoriss
ms.suite: ems
ms.sourcegitcommit: 3080d23f464e96315ed9e5fd59774ba9f1b2dd86
ms.openlocfilehash: 65d582958d77150091880cce72e079b87308209f


---

# 早期 Intune 发行版本
## 2016 年 5 月

所有这些功能也受混合部署 (Configuration Manager with Intune) 支持。 有关新的混合功能的详细信息，请查看[混合新增功能](https://technet.microsoft.com/en-us/library/mt718155.aspx)页。

### 文档
欢迎使用 [docs.microsoft.com](https://docs.microsoft.com/en-us/intune) 预览版本！
这是一个全新的新式内容平台，旨在使作为我们客户的你能更容易地理解和使用 Intune。
若要了解所有新增功能，请参阅 [Introducing docs.microsoft.com](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/)（docs.microsoft.com 简介）

### Intune 服务运行状况
Intune 服务运行状态信息已随同其他 Microsoft 服务一起移到一个中心位置。 现在你可在**服务运行状态**下的 [Office 365 管理门户](https://portal.office.com/Admin/Default.aspx)中找到此信息。
有关详细信息，请参阅[此博客文章](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/)。


### 应用管理
- **MAM SDK：支持 PIN 长度配置。** 你将能够指定类似于设备 PIN 的 MAM 应用的 PIN 的长度。 这将要求最终用户符合你设置的新限制。 他们将看到一个稍经修改的 PIN 屏幕来解释较长输入。 有关详细信息，请参阅[适用于 Android 的 MAM 策略设置](/intune/deploy-use/android-mam-policy-settings)以及[适用于 iOS 的 MAM 策略设置](/intune/deploy-use/ios-mam-policy-settings)。

- **Skype for Business iOS 版和 Android 版。** 你现在可以通过 [MAM 以 Skype for Business 为目标，而不需要注册策略](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)。 用户登录后，将应用 MAM 策略。

- **可通过 MAM 策略管理的新应用。** 适用于 Android 的 Microsoft Word、Excel 和 PowerPoint 应用现在可与未向 Intune 注册的设备上的 MAM 策略相关联。 有关支持的应用的完整列表，请转到 [Microsoft Intune application partners](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)（Microsoft Intune 应用程序合作伙伴）页上的 Microsoft Intune mobile application gallery（Microsoft Intune 移动应用程序库）。


### 公司门户更新

#### Android 公司门户应用
- **最终用户 toast 通知**：当最终用户从公司门户注册设备或删除设备时，现在他们将会看到来自 Andoid 公司门户应用的 toast 通知。

- **对 Android 公司门户应用中设备注册管理器帐户的更改。** 若要提高性能和可扩展性，Intune 不再在 Android 公司门户应用的“我的设备”窗格中显示所有设备注册管理器 (DEM) 设备。 仅显示运行该应用的本地设备，且仅限该设备通过公司门户应用注册的情况下。 DEM 用户可能会在本地设备上执行操作，但只能从 Intune 管理员控制台远程管理其他已注册设备。

#### 公司门户网站
- **公司门户网站：设备标识横幅将向最终用户提供详细信息。** 最终用户现在能够更轻松地标识他们在使用公司门户网站时所选的设备。 如果选择了错误的设备，他们将能够通过点击主页标题栏中的**点击此处**链接选择正确的设备。

## 即将推出
- **消息中心 UI 载入**。 作为 Intune 迁移到 [Office 365 管理门户](https://portal.office.com/)的一部分，我们将开始利用其消息中心以沟通新功能和其他通知。 另外，通过安装随附的 Office 365 管理员移动应用，可在移动电话上收到通知，并轻松地将任何消息转发到用户或分发别名。
我们将开始通过五月发行版本使用消息中心，以在更新完成时通知你，并且将包括有关新的和改进的 Intune 功能的信息。 现在可以通过登录到 [Office 365 管理门户](https://portal.office.com/)，然后选择左导航窗格中的“消息中心”选项来查看消息中心。

- **对设备注册管理器帐户的更改**。 为了提高性能和可扩展性，Intune 不再在 iOS 公司门户应用的**我的设备**窗格中显示**所有**设备注册管理器 (DEM) 设备。 仅显示运行该应用的本地设备，且仅限该设备通过公司门户应用注册的情况下。 DEM 用户可能会在本地设备上执行操作，但只能从 Intune 管理员控制台远程管理其他已注册设备。 此外，Intune 将不支持通过 Apple 设备注册计划或 Apple 配置器工具使用 DEM 帐户。 这两种注册方法已支持共享的 iOS 设备的无用户注册。 当共享设备的无用户注册不可用时，仅使用 DEM 帐户。

### 云路线图
通过[云平台路线图](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)实时了解 Intune 即将推出的开发内容。

### 服务弃用
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


## 2016 年 4 月
所有这些功能也支持混合客户（与 Intune 集成的 Configuration Manager）。
### 应用管理
- **MAM 用户合规性。**
现在，你可以查看 Azure Active Directory (AAD) 租户中的任何用户的应用程序管理策略的[状态](monitor-mobile-app-management-policies-with-Microsoft-Intune.md)。 这包括：
   - 设备
   - 在设备上的应用

   状态值：

   **已签入**：指示该策略已部署到用户，以及应用已用在工作环境中且已成功接收到该策略。

    **未签入**：指示策略已部署到用户，但应用从那时起尚未在工作环境中使用。


- **防止 Outlook 联系人同步的 MAM 控件 (Android)。**
适用于[移动应用程序管理](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)而无需注册设备的新设置。 此设置可以防止应用程序将联系人同步到 Android 设备的本机通讯簿。 启用此设置后，目标应用程序将不能再将联系人保存到本机通讯簿。 禁用此设置后，目标应用程序将能够将联系人保存到本机通讯簿。 [远程擦除设备或应用](wipe-managed-company-app-data-with-Microsoft-Intune.md)后，将删除已保存到本机通讯簿的所有联系人。 最初，Android 设备上的 Outlook 应用程序支持此新设置。

### 设备管理
- **公司拥有的设备的电话号码标识。** 例如，当运行移动设备清单报表时，现在使用其完整的电话号码标识归类为“企业”的手机。 BYOD 电话号码将继续使用 **** 屏蔽，仅显示最后 4 位数字。


### 公司门户更新
**Android 公司门户应用**未在 Intune 注册其设备和未安装正确证书的用户将不能登录到 Android 公司门户应用，并且会看到以下消息：“无法登录，因为设备缺少必需的证书”。 该消息包含“如何解决此问题”的链接，用户可以点击以查看关于安装证书的说明。 若要查看最终用户解决此问题的步骤，请参阅[设备缺少必需的证书](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing)。

**iOS 公司门户应用**已添加“下拉刷新”操作支持以刷新主页上的内容，其中包括列出的应用、设备以及 IT 联络信息。 “下列刷新”操作不会检查合规性或策略信息，这可以通过选择当前设备的磁贴，然后点击“同步”按钮来实现。

**Windows 10 移动版和 Windows Phone 8.1 公司门户应用**当最终用户安装业务线应用时，他们现在将了解到改进后的应用安装体验。 如果应用安装要花很长时间，用户可以手动同步设备以强制继续同步过程。 若要查看最终用户说明，请参阅[手动同步设备以加速应用安装](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually)。

**公司门户网站**当 Windows 10 移动版和 Windows Phone 8.1 用户正在安装业务线应用时，现在他们将看到以下新状态，向他们提供有关安装状态的详细信息：

* **等待设备进行同步** – 用户已点击“安装”，并且设备现在尝试与 Intune 基础结构进行同步。 必须先同步，然后才能完成安装。 “正在等待设备进行同步”消息也是一个链接，用户可以点击以查看[说明](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually)，了解如果同步过程需要很长时间或已停止，如何手动将设备与 Intune 同步。
* **正在下载** – 正在处理用户的下载请求，且设备正在下载并安装应用。

添加这些状态之前，如果应用安装需要很长时间，用户将感到困惑，因为他们只能看到“正在安装”状态，而这可能会在屏幕上保持数个小时。 添加新的状态意味着，现在用户可以点击“正在等待设备进行同步”链接，并按照说明进行操作以强制继续同步过程，而不是呼叫支持部门。


## 2016 年 3 月
### 自 2016 年 3 月 29 日起新增的功能
除了更新到 Windows 10 常规配置策略之外，2016 年 3 月 29 日发布的所有功能还支持混合客户（与 Intune 集成的 Configuration Manager）。 即将推出对 Windows 10 常规配置策略更新的混合支持。 请注意，其中某些功能可能需要使用 Configuration Manager 的最新版本。

### 应用管理
- **防止 Outlook 联系人同步的 MAM 控件 (iOS)。** 适用于移动应用程序管理而无需注册设备的新设置。 此设置可以防止应用程序将联系人同步到 iOS 设备的本机通讯簿。 启用此设置后，应用将不再能够将联系人保存到本机通讯簿。 禁用此设置后，应用就可以将联系人保存到本机通讯簿。 选择性擦除设备时，将删除已保存到本机通讯簿的所有联系人。 iOS 设备上的 Outlook 应用程序支持此新设置。 有关此设置和其他设置的详细信息，请参阅[创建和部署 MAM 策略](https://technet.microsoft.com/en-us/library/dn292747.aspx)。

### 访问控制
- **Skype for Business Online 支持条件性访问。** 可以为 Skype for Business Online 设置条件性访问策略，使仅托管且合规的 iOS 和 Android 设备可对其进行访问。 系统将提示尝试登录到 iOS 和 Android 设备上的 Skype for Business 移动应用的最终用户注册 Intune 并在登录完成前修复任何非合规性问题。 有关详细信息，请参阅[管理对 Skype for Business Online 的访问权限](https://technet.microsoft.com/en-us/library/mt695297.aspx)。

### 设备管理
- **适用于 iOS 9.3 的 Intune 支持。** 3 月 21 日星期一，Apple 宣布推出 iOS 9.3。 我们致力于确保 Microsoft Intune 与 Apple 最新版本的移动操作系统兼容，并且[我们很高兴地宣布 Intune 支持管理 iOS 9.3 设备](https://blogs.technet.microsoft.com/microsoftintune/2016/03/23/microsoft-intune-provides-support-for-ios-9-3/)。

  在用户将设备升级到 iOS 9.3 时，当前可用于管理 iOS 设备的所有现有 Intune 功能都将继续无缝工作。 此外，iOS 9.3 现在也支持混合客户（与 Intune 集成的 Configuration Manager）。

- **Windows 10 常规配置策略现包含用于管理已注册 Windows 10 电脑上的 Windows Defender 的设置。** 有关详细信息，请参阅 [Microsoft Intune 中的 Windows 10 配置策略设置](https://technet.microsoft.com/en-us/library/mt404697.aspx)。


### 公司门户

- **Windows 应用包可以直接从公司门户网站安装。** 使用 Windows 8、Windows 8.1 和 Windows RT 电脑的用户现可直接从公司门户网站安装 Windows 应用包（扩展名为.appx）。 以前，用户必须在设备上部署或安装公司门户应用才能安装应用。

- **用户可以从公司门户网站远程锁定其设备。** 公司门户网站新增了远程锁定选项，让用户在设备丢失或被盗时可以从门户网站远程锁定其设备。 请参阅[最终用户说明](https://technet.microsoft.com/library/mt590895.aspx/?wt.mc_id=ui#BKMK_iwp_remote_lock)。 下表列出了适用于独立 Intune 和带 Configuration Manager 的 Intune 的远程锁定平台支持。

|平台 | 支持详细信息|
|---------|----------------|
|Android |支持|
|iOS |支持|
|Windows 10 移动版 |仅在手机设置了密码时支持|
|Windows 10 桌面版 |不支持|
|Windows Phone 8.1 |仅在手机设置了密码时支持|
|Windows Phone 8。0 |不支持|
|电脑（Windows 8.0 及更早版本） |不支持|
|电脑 (Windows 8.1) |不支持|

### 自 2016 年 3 月 10 日起新增的功能

### 应用管理

- **利用在第三方 MDM 解决方案中注册的设备的 iOS“Open in”管理**可通过第三方移动设备管理 (MDM) 供应商利用 iOS“Open-In”管理功能。 可以在配置文件设置中设置限制，并使用[管理 iOS 应用之间的数据传输](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)部署应用。

     此方法有两个主要优点：

     1. 用户必须先使用工作帐户登录才能从云服务或其他应用中访问任何公司数据。 这可确保访问数据时移动应用管理 (MAM) 策略已到位。

     2. 通过第三方 MDM 解决方案部署的托管电子邮件配置文件和其他托管应用可以与具有 Intune MAM 策略的应用共享文件和数据。

- **使用未在 Intune 中注册的设备的 MAM 策略管理 Microsoft Outlook 应用**现在你可以使用 Intune 移动应用程序管理策略管理未在 Intune 中注册的设备上的 Microsoft Outlook 应用。 具有 MAM 功能的已更新 Microsoft Outlook 应用适用于 [iOS](https://itunes.apple.com/us/app/microsoft-outlook-email-calendar/id951937596?mt=8) 和 [Android](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook) 设备。 使用[创建和部署移动应用管理策略](https://technet.microsoft.com/library/mt627829.aspx)主题中的说明来创建 MAM 策略。  


- **移动应用配置策略使你能更灵活地为 iOS 应用指定用户详细信息**你可以提供打开 iOS 应用时可能需要的用户设置。 例如，你可以提供网络端口或用户名。 有关详细信息，请参阅[使用 Microsoft Intune 中的移动应用配置策略配置 iOS 应用](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md)。


- **将适用于 Microsoft Intune 的 Adobe Reader 部署到企业中 Intune 托管的 iOS 设备**现在可以使用 Intune 移动应用程序管理策略在已注册的设备上对适用于 iOS 的 Adobe Reader 应用进行管理。

- **确保部署的 Web 剪辑在托管浏览器中打开**可以部署仅可在 iOS 和 Android 设备上使用托管浏览器打开的目标 Web 剪辑。 例如，你通过公司门户将链接部署到企业资源，当用户导航到该链接时，他们便可直接打开到在其中能受到 MAM 策略保护的托管浏览器中。 有关详细信息，请参阅[部署应用](deploy-apps.md)。


- **从 Intune 管理员控制台为 Windows 10 设备查找、管理和分配适用于企业的 Windows 应用商店应用**Intune 支持适用于企业的 Windows 应用商店，可帮助查找、管理和分配应用到你正在管理的 Windows 10 设备。 适用于企业的 Windows 应用商店可用于管理从 Intune 管理员控制台（管理其他应用时所用的同一控制台）部署和监视这些应用的进程。 具体来说，适用于企业的 Windows 应用商店管理“在线授权应用”的内容和授权。 有关详细信息，请参阅[管理从适用于企业的 Windows 应用商店购买的应用](manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune.md)。


### 设备管理
- **针对 iOS 设备的 PFX 证书分发**Intune 管理员可以为 iOS 设备上的 Wi-Fi、电子邮件和 VPN 身份验证创建和部署 iOS PFX 证书。 此功能已可用于 Android 和 Windows 10 设备。 有关详细信息，请参阅[启用对使用证书配置文件的公司资源的访问](secure-resource-access-with-certificate-profiles.md)。


- **将应用和策略应用到基于用户类别选择的不同设备组** Intune 管理员现在可以定义自定义设备类别，以让用户在注册过程中从中进行选择。 例如，管理员可能想要用户指定是否要注册用于“收银机”或“送货车”或“库存间”的设备。 所选类别将使该设备成为 Intune 设备组的成员，这可用于将不同的应用和策略部署到已注册的设备。 有关详细信息，请参阅[使用设备组映射对设备进行分类](categorize-devices-with-device-group-mapping-in-microsoft-intune.md)。

### Microsoft 公司门户的更改和更新
此版本已针对公司门户进行了如下更改：

**Android 公司门户应用**

* 当你的用户发布一个由移动应用程序管理 (MAM) 管理的应用时，他们将看到一条消息，通知他们该应用由他们的公司管理。 用户现在可以点击“了解详细信息”链接以在此处获取有关“托管应用”意义的[详细信息](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_use_mgd_apps)。 他们还可以点击“不再显示”以便他们启动应用时不再显示该消息。
* 添加了新屏幕以指导用户完成注册过程，并提供有关用户应该注册的原因和 IT 管理员能够和不能够在他们的已注册设备上看到的内容的详细信息。 请参阅[注册说明](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc)以获取详细信息。
* 注册错误消息现在会显示在公司门户应用中。 以前，这些消息显示在公司门户网站上。 进行此更改意味着所有的错误消息现在只显示在一个位置而不是两个不同的位置。


**iOS 公司门户应用**
* 当你的用户发布一个由移动应用程序管理 (MAM) 管理的应用时，他们将看到一条消息，通知他们该应用由他们的公司管理。 用户现在可以点击“了解详细信息”链接以在此处获取有关“托管应用”意义的[详细信息](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_use_mgd_apps)。 他们还可以点击“不再显示”以便他们启动应用时不再显示该消息。
* 添加了新屏幕以指导用户完成注册过程，并提供有关用户应该注册的原因和 IT 管理员能够和不能够在他们的已注册设备上看到的内容的详细信息。 请参阅[注册说明](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device)以获取详细信息。
* 注册错误消息现在会显示在公司门户应用中。 以前，这些消息显示在公司门户网站上。 进行此更改意味着所有的错误消息现在只显示在一个位置而不是两个不同的位置。




## 2016 年 2 月
### Microsoft 公司门户的更改和更新

此版本已针对公司门户进行了如下更改：

#### Android 公司门户应用
- 添加了新屏幕以指导用户完成注册过程，并提供有关用户应该注册的原因和 IT 管理员能够和不能够在他们的已注册设备上看到的内容的详细信息。 请参阅[注册说明](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc)以获取详细信息。
- 注册错误消息现在会显示在公司门户应用中。 以前，这些消息显示在公司门户网站上。 进行此更改意味着所有的错误消息现在只显示在一个位置而不是两个不同的位置。

#### iOS 公司门户应用
 - 添加了新屏幕以指导用户完成注册过程，并提供有关用户应该注册的原因和 IT 管理员能够和不能够在他们的已注册设备上看到的内容的详细信息。 请参阅[注册说明](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device)以获取详细信息。

 - 注册错误消息现在会显示在公司门户应用中。 以前，这些消息显示在公司门户网站上。 进行此更改意味着所有的错误消息现在只显示在一个位置而不是两个不同的位置。


## 2016 年 1 月

### 利用 Windows 10 功能
* **运行状况证明服务的条件性访问** Intune 管理员现在可以在 Intune 管理控制台中查看 Windows 10 设备运行状况证明的状态。 设备运行状况证明让管理员能够确保客户端计算机具有可信 BIOS、TPM 和启动软件配置。 为了支持设备运行状况证明，客户端设备必须运行 Windows 10 并启用 TPM 2。 设备运行状况证明显示为以下各项启用的设备数：
    * 开机初期启动的反恶意软件
    * BitLocker
    * 安全启动
    * 代码完整性

    阅读 [Microsoft Intune 的设备合规性策略简介](introduction-to-device-compliance-policies-in-microsoft-intune.md)以获取有关设备运行状况设置、收集的数据点和运行状况证明报告的详细信息。 [HAS 服务详细信息](https://msdn.microsoft.com/en-us/library/dn934876.aspx)深入解释了该服务。

* **Windows 10 Passport for Work 策略和证书管理**利用 Intune，可以[与 Microsoft Passport for Work 集成](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md)，这是使用 Active Directory 或 Azure Active Directory 帐户替代密码、智能卡或虚拟智能卡的一种适用于 Windows 10 的替代登录方法。 通过 Passport，你可以使用用户手势取代密码进行登录。 用户手势可以是简单 PIN、Windows Hello 等生物识别身份验证或指纹读取器等外部设备。

* **特定应用的 VPN**你可以选择通过 VPN 自动连接到企业网络的应用。 设置 VPN 配置文件时创建应用列表，如“通过 Microsoft Intune 使用 VPN 配置文件帮助用户连接到其工作”中所述。

* **Windows 10 完全擦除支持**你现在可以发起通过 Intune 管理控制台已在 Intune 中注册的 Windows 10 桌面设备的远程完全擦除。 Windows 10 完全擦除会对设备进行出厂重置。


### Apple 批量采购计划 (VPP) 更新
Intune 现在可以帮助你[管理通过适用于企业的 Apple 批量采购计划 (VPP) 购买的应用](manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune.md)。 这包括同步 Apple 和 Intune 之间的许可证信息，和跟踪你已部署的每个应用的副本数量。

### 使用 IMEI 号码识别企业拥有的设备
现在可以对具有 IMEI 号码的移动设备平台[导入国际移动设备标识 (IMEI) 号码](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)，以帮助识别企业拥有的移动设备。 在 Intune 中注册后，带有导入的 IMEI 号码的设备就会被标记为“企业”，这些设备可用于应用与应用到个人拥有设备的策略不同的策略。

### 更多应用现在与 Intune MAM 策略相兼容
来自 Microsoft 合作伙伴的其他应用现在与 Intune 移动应用程序管理 (MAM) 策略（针对由 Intune 管理的设备）兼容：
* Box for EMM（来自 Box Inc）- 仅限 iOS
* Adobe Reader（来自 Adobe）- 仅限 Android
* Foxit PDF Reader（来自 Foxit Corporation）- iOS 和 Android


### 于 1 月结束 IE9 支持
从 2016 年 2 月开始，将不再支持 Internet Explorer 9 作为用于访问 Microsoft Intune 公司门户网站、Intune 帐户门户和 Intune 管理控制台的官方浏览器。 你将需要迁移到 Internet Explorer 10 或更高版本。

## 2015 年 12 月
### Microsoft 公司门户的更改和更新
此版本已针对公司门户进行了如下更改：

**Android 公司门户应用**

为了符合 Google 新要求，已进行以下更改。 在 Android 6.0 及更高版本的设备上，将向用户显示两条新消息：
* “是否允许公司门户发起和管理电话呼叫?”
* 是否允许公司门户访问你设备上的照片、媒体和文件？

有关这两条消息的详细信息，请参阅下表。



消息文本  |“是否允许公司门户发起和管理电话呼叫?”  
---------|---------
消息含义     |  使用户的设备电话号码和 IMEI 能够被发送到 Intune 服务并显示在“硬件”页的管理控制台中。   </br></br>**注意：公司门户应用绝不会发起或管理电话呼叫！** 消息文本由 Google 管控，不可更改。 </br></br>要查看“硬件”页，请转到“组” > “所有移动设备” > “设备”。 选择用户的设备，然后转到**查看属性** > **硬件**。    
何处以及何时显示消息  | 用户首次登录到公司门户应用开始注册设备时将显示该消息。|         
如果用户允许访问将出现的情况  |  设备电话号码和 IMEI 将显示在管理控制台的“硬件”页上。 |         
如果用户拒绝访问将出现的情况     | 用户可以继续使用公司门户应用并注册设备，但在管理控制台的“硬件”页上他们的设备电话号码和 IMEI 将为空。       </br></br> 拒绝访问后，用户第二次登录到公司门户应用时，该消息将显示“不再询问”复选框，勾选该框将不再显示该消息。</br></br>如果用户先允许访问，但稍后又拒绝访问，则在注册后用户下一次登录到公司门户应用时仍将显示该消息。</br></br>如果用户稍后决定允许访问，可转到“设置” > “应用” > “公司门户” > “权限” > “电话”，然后开启权限。
更多信息     |  适用于用户：[登录到公司门户](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_signin_cp)  </br></br>适用于 IT 专业人士：此表中的信息也位于[帮助用户了解公司门户应用消息](https://technet.microsoft.com/library/dn948527.aspx#BKMK_help_users_understd_msgs)中   

消息文本  |是否允许公司门户访问你设备上的照片、媒体和文件？  
---------|---------
消息含义     |  使设备能够向设备 SD 卡写入数据日志，从而可通过 USB 连接线移动日志。   </br></br>**注意：公司门户应用绝不会访问用户的照片、媒体和文件！** 消息文本由 Google 管控，不可更改。     
何处以及何时显示消息  | 用户点击“发送数据”以向 IT 管理员发送数据日志时将显示该消息。|         
如果用户允许访问将出现的情况  |  日志将被复制到 SD 卡。 |         
如果用户拒绝访问将出现的情况     | 他们仍可发送数据日志，但不会向设备 SD 卡复制日志。       </br></br> 拒绝访问后，用户第二次登录到公司门户应用时，该消息将显示“不再询问”复选框，勾选该框将不再显示该消息。</br></br>如果用户先允许访问，但稍后又拒绝访问，则当用户下一次尝试发送日志时，仍将显示该消息。</br></br>如果用户稍后决定允许访问，可转到“设置” > “应用” > “公司门户” > “权限” > “存储”，然后开启权限。
更多信息     |  适用于用户：[使用电子邮件将诊断数据日志发送给 IT 管理员](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_send_diag_logs)  </br></br>适用于 IT 专业人士：此表中的信息也位于[帮助用户了解公司门户应用消息](https://technet.microsoft.com/library/dn948527.aspx#BKMK_help_users_understd_msgs)中   


**iOS 公司门户应用**
* 用户现在可以使用 Microsoft Outlook 或其他邮件应用向 IT 管理员发送诊断日志。 以前，只能使用本机应用。
* 已改进了对 Apple 的设备注册程序 (DEP) 和公司注册的设备的支持。 有关详细信息，请参阅[尝试注册时会要求你对设备进行识别](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_id_your_device)。
* 在用户的已注册设备列表中，现将于用户当前正在使用的设备旁显示一个绿色复选标记。 在添加此复选标记前，用户无法辨别自己正在使用的是哪一个已注册设备。

**Windows 公司门户应用**

Microsoft 会自动收集有关性能和公司门户使用情况的匿名数据以改进 Microsoft 产品和服务。 最终用户可以使用设备上的“数据使用情况”设置关闭数据收集，但管理员无法控制数据收集，且无法更改最终用户对此设置的选择。



## 2015 年 11 月
### 应用管理
Intune 支持移动应用程序管理 (MAM) 策略，有助于防止企业数据泄漏到使用者应用或服务。 过去，这些策略仅能在对移动设备管理 (MDM) 也在 Intune 中进行了注册的设备上运行的移动应用上执行。

通过本月的更新，Intune 将其 MAM 功能扩展到设备的新类。 除了注册到 Intune 的设备，你现在还可以在以下设备上执行 MAM 策略：
* 由任何其他设备管理 (MDM) 解决方案管理的设备
* 未注册到任何设备管理系统的设备，通常为自带办公 (BYO) 设备

你可以在以下博客文章中查找有关这些新 MAM 功能的更多信息：
* [增强托管移动生产力](http://blogs.technet.com/b/microsoftintune/archive/2015/11/17/enhancing-managed-mobile-productivity.aspx)
* [宣布新的 Microsoft 企业移动功能](http://blogs.technet.com/b/microsoftintune/archive/2015/11/17/enhancing-managed-mobile-productivity.aspx)

此外，下面是关于 Intune 的 MAM 功能的一些重点和其他信息：
* 企业数据在为 Intune 启用的应用内独立于使用者数据，这些应用包括 Office Mobile 应用、采用 Intune SDK 的第三方应用或由 Intune 包装的业务线应用。
* 可以在公司应用之间共享（**剪切/辅助/粘贴**）公司数据，同时防止公司数据共享到个人应用。 阅读 [MAM 策略如何保护应用数据](https://technet.microsoft.com/library/mt627825.aspx)以获取更多详细信息。 此示例方案，即[对工作和个人任务使用 Microsoft Word 应用](https://technet.microsoft.com/library/mt627827.aspx)，显示了如何防止公司数据共享到个人应用。
* 关键数据丢失防护策略，如 Per-App PIN、另存为控件和应用之间的托管数据共享。 阅读[使用 Microsoft Intune 创建和部署移动应用管理策略](https://technet.microsoft.com/library/mt627829.aspx)以查看所有策略的列表。
* Word、Excel、PowerPoint、Outlook、OneNote 和 OneDrive for Business 全部具有这些新功能且能够在有或者没有设备注册的情况下进行管理。 数据丢失保护功能本机内置于 Apple 应用商店或 Google Play 应用商店中的标准 Office 应用中，且不需要应用包装或旁加载。
* 若要了解如何入门，请参阅 [Azure 门户中的移动应用管理策略入门](https://technet.microsoft.com/library/mt627830.aspx)。 若要了解如何配置和部署移动应用管理策略，请参阅[使用 Microsoft Intune 创建和部署移动应用管理策略](https://technet.microsoft.com/library/mt627829.aspx)。
* 当最终用户使用他们的企业凭据对应用进行身份验证时，数据丢失防护功能会自动进行设置。 [与 Microsoft Intune 移动应用管理策略相关联的应用的最终用户体验](https://technet.microsoft.com/library/mt627827.aspx)主题有一些针对在 iOS 和 Android 设备上访问 OneDrive 的示例方案。
* 可在 iOS 和 Android 设备上运行。

[可配合 Microsoft Intune 移动应用程序管理策略使用的 Microsoft 应用](https://technet.microsoft.com/library/dn708489.aspx)的列表已经更新，它将显示最新的应用。

### 设备管理
 **Mac OS X 设备管理**使用 Intune，现在可以注册和管理 Mac OS X 设备。 你可以使用你的 Mac OS X 设备进行以下操作：
* 注册设备以使设备由 Intune 管理。 请参阅[使用 Microsoft Intune 设置 iOS 和 Mac 管理](https://technet.microsoft.com/library/dn408185.aspx)。
* 具有常规配置策略的控制设备设置。 请参阅 [Microsoft Intune 中的 Mac OS X 配置策略设置](https://technet.microsoft.com/library/mt627823.aspx)。
* 使用 Apple Configurator 部署你创建的 Mac OS X 设置。 请参阅 [Microsoft Intune 中的 Mac OS X 自定义策略设置](https://technet.microsoft.com/library/mt627820.aspx)。
* 从 Mac OS X 设备收集硬件和软件清单。 请参阅[通过 Microsoft Intune 中清单了解你的设备](https://technet.microsoft.com/library/jj733634.aspx)。
* 运行显示关于你管理的 Mac OS X 设备的详细信息的新报表。 请参阅[通过使用报表了解 Microsoft Intune 操作](https://technet.microsoft.com/library/dn646977.aspx)。

**Windows 10 设备的新 Edge 浏览器设置**已经将新的设置添加到 Windows 10 常规配置策略中，能让你对 Microsoft Edge 浏览器的设置和功能进行管理。 请参阅 [Microsoft Intune 中的 Windows 10 配置策略设置](https://technet.microsoft.com/library/mt404697.aspx)。

**电子邮件配置文件**已为 Windows 10 桌面和 Windows 10 移动设备添加了新的电子邮件配置文件策略。 请参阅[使用 Microsoft Intune 策略管理设备上的设置和功能](https://technet.microsoft.com/library/dn646984.aspx)。

**新的合规性策略设置**已经将以下新的安全和系统策略设置添加到合规性策略列表中：
* 要确保访问公司资源的 Windows 8.1 或更高版本的设备安装有最新的更新，请使用“需要自动更新”设置。 你还可以指定要自动进行安装的更新类型 -- 安装所有标记为重要的更新，或安装所有标记为重要或推荐的更新。 有关合规性策略的完整列表，请参阅[为 Microsoft Intune 管理设备合规性策略](https://technet.microsoft.com/library/dn705843.aspx)。
* 新的“当设备从空闲状态返回时需要密码”设置与现有的“需要提供密码之前处于非活动状态的分钟数”设置的结合允许你创建需要最终用户输入密码以使用已经处于非活动状态一定时间的设备的合规性设置。

**新的条件性访问策略选项**可以将条件性访问策略以新的或现有的条件性访问策略应用到**所有用户**。 将要求已对 Intune 和 Office 365 授权的所有用户注册他们的设备，且如果设备平台不受 Intune 支持，那么将阻止使用[基于 Active Directory 身份验证的登录（新式验证）](https://blogs.office.com/2014/11/12/office-2013-updated-authentication-enabling-multi-factor-authentication-saml-identity-providers/)的客户端应用程序的访问。

你还可以指定将条件性访问策略应用到“所有平台”。  使用[基于 Active Directory 身份验证的登录（新式验证）](https://blogs.office.com/2014/11/12/office-2013-updated-authentication-enabling-multi-factor-authentication-saml-identity-providers/)的任何客户端应用程序都服从条件性访问策略，并且如果 Intune 不支持该平台，则它将被阻止。

### Microsoft 公司门户的更改和更新
此版本已针对公司门户应用进行了如下更改：

* **Android**：已在 Android 公司门户应用中添加了“欢迎”屏幕，以帮助用户理解公司门户应用的用途。 此屏幕的目的是为了减少其公司不是 Intune 订阅人的用户对该应用的下载。

* **iOS**：Intune 现在支持通过使用[公司门户网站](https://portal.manage.microsoft.com)注册 Mac OS X 设备。 有关说明，请参阅[在 Intune 中注册 Mac OS X 设备](https://technet.microsoft.com/library/mt598622.aspx)。

* **公司门户网站**：在 Intune 中注册了设备的用户现在可以通过使用公司门户网站上的“重置密码”选项重置密码。 以前，只有 IT 管理员才可以重置用户的密码。 Windows 8.1 和 Windows RT 设备上不支持“重置密码”选项，且仅当在移动设备管理 (MDM) 中或配有 Exchange ActiveSync 的 MDM 中注册设备时，才会显示该选项。 有关用户说明，请参阅[重置密码](https://technet.microsoft.com/library/mt590895.aspx)。

### 对全局管理员授权的更改
在 10 月，我们分享了全局管理员（也被称为租户管理员）能够继续在没有单独的 Intune 或企业移动性套件 (EMS) 许可证的情况下进行日常的管理任务。 但是，如果全局管理员想要使用服务（例如注册他们自己的设备、企业设备，或使用 Intune 公司门户），与任何其他用户一样，他们需要 Intune 或 EMS 许可证。 以下是一些其他的详细信息。
* 最终用户在 Intune 公司门户中可以：
    * 注册其设备
    * 查看其设备的状态
    * 下载全局管理员部署到组织的软件
    * 查找由全局管理员发布的有关如何联系其 IT 部门的链接

    [了解公司门户](https://technet.microsoft.com/library/dn646966.aspx#BKMK_CompanyPortal)和有关[如何自定义公司门户的方法](https://technet.microsoft.com/library/dn646983.aspx#BKMK_ConfigureCompanyPortal)。
* 以组织名义注册购买 Intune 或 EMS 的人员自动成为其租户中的第一个全局管理员。 今年秋天，Intune 开始将 Intune 或 EMS 许可证自动分配给第一个全局管理员，作为迁移到 [Office 365 门户](http://portal.office.com/)及停用 [Intune 帐户门户](http://account.manage.microsoft.com/)的一部分。 添加的任何其他全局管理员能够继续在没有单独的 Intune 或 EMS 许可证的情况下进行日常的管理。 以最终用户的身份操作并注册他们自己的（或企业的）设备或从公司门户下载软件会触发对许可证的需求，如同任何其他用户一样。
* 此更改将分阶段进行，并将在 2016 年 1 月开始。
* 对于 Microsoft 合作伙伴，此更改不应影响你以客户名义管理服务的能力。 对于最终用户的任务，用户将需要拥有一个 Intune 或 EMS 许可证以便注册设备并从公司门户访问或下载软件。

如果有关于此更改的任何问题，请随时联系你的 Intune 支持团队：
* [Microsoft Intune 支持渠道](https://technet.microsoft.com/library/jj839713.aspx)
* [社区支持](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)

对于常规 Microsoft Intune 反馈，包括提出设计更改请求 (DCRs) 或 bug，请访问 [Intune 用户之声](https://microsoftintune.uservoice.com/)。


### Intune 文档新内容 - 2015 年 11 月
**新内容**
* [Microsoft Intune 中的 Mac OS X 配置策略设置](https://technet.microsoft.com/library/mt627823.aspx)：如何控制 Mac OS X 设备的设备设置和功能。
* [Microsoft Intune 中的 Mac OS X 自定义策略设置](https://technet.microsoft.com/library/mt627820.aspx)：如何部署你使用 Apple Configurator 工具创建的 Mac OS X 设备设置。
* [使用 Microsoft Intune 配置数据丢失预防应用策略](https://technet.microsoft.com/library/mt627825.aspx)：包含关于移动应用管理策略支持的方案和策略保护数据的工作原理的信息。
* [Azure 门户中的移动应用程序管理策略入门](https://technet.microsoft.com/library/mt627830.aspx)：开始使用移动应用管理策略的 Azure 预览版门户所需的内容。
* [使用 Microsoft Intune 创建和部署移动应用程序管理策略](https://technet.microsoft.com/library/mt627829.aspx)：包含如何在 Azure 预览版门户中创建移动应用管理策略的分步演练。
* [使用 Microsoft Intune 监视移动应用管理策略](https://technet.microsoft.com/library/mt627824.aspx)：关于如何使用 Azure 预览版门户监视移动应用管理策略的信息。
* [Microsoft Intune 移动应用管理策略和 iOS Open In](https://technet.microsoft.com/library/mt627821.aspx)：关于移动应用管理策略如何与 iOS Open In 功能协作的信息。
* [Microsoft Intune 移动应用管理策略关联的应用的最终用户体验](https://technet.microsoft.com/library/mt627827.aspx)：使用与移动应用管理策略关联的应用时，最终用户体验的内容。
* [使用 Microsoft Intune 擦除托管公司应用数据](https://technet.microsoft.com/library/mt627826.aspx)：如何删除公司应用数据。

**已更新的内容**
* [Microsoft Intune 中的 Windows 10 配置策略设置](https://technet.microsoft.com/library/mt404697.aspx)：添加了新的 Edge 浏览器设置。
* [使用 Microsoft Intune 设置 iOS 和 Mac 管理](http://technet.microsoft.com/library/dn408185.aspx)：添加了关于如何注册 Mac OS X 设备的信息。
* [ Microsoft Intune 中的清单了解你的设备](https://technet.microsoft.com/library/jj733634.aspx)：添加了关于从 Mac OS X 设备收集到的清单的信息。 此外，也通过所有设备平台的最新信息更新了主题。
* [通过使用报表了解 Microsoft Intune 操作](https://technet.microsoft.com/library/dn646977.aspx)：添加了关于用于显示有关你管理的 Mac OS X 设备的信息的两个新报表的信息。
* [为 Microsoft Intune 管理设备合规性策略](https://technet.microsoft.com/library/dn705843.aspx)：添加了关于当设备从空闲状态返回时，需要自动更新和需要密码的新合规性策略的信息。
* [使用 Microsoft Intune 管理电子邮件访问](https://technet.microsoft.com/library/dn705841.aspx)：添加了关于将条件性访问策略应用到所有平台和所有用户的能力的信息。
* [使用 Microsoft Intune 管理 SharePoint Online 访问](https://technet.microsoft.com/library/dn705844.aspx)：添加了关于将条件性访问策略应用到所有平台和所有用户的能力的信息。

## 2015 年 10 月

### Exchange 内部部署条件访问更新
**现在你可以允许在 Intune 中已注册的兼容设备在全局 Exchange 规则被设置为阻止或隔离时访问 Exchange Active Sync 电子邮件** 到目前为止，要在已注册的和兼容的设备上允许电子邮件访问，你必须将默认全局 Exchange 规则设置为“允许”。

有此服务更新后，此设置不再是条件访问的必要设置。 如果 Exchange 环境要求将默认全局规则设置为“阻止/隔离”，只需选中 Exchange 本地条件访问策略页中的“默认规则覆盖”复选框。 [使用 Microsoft Intune 管理电子邮件访问](https://technet.microsoft.com/library/dn705841.aspx)主题提供了有关规则和生成的最终用户通知的更多详细信息。

**全新一键式隔离体验** 我们简化了隔离电子邮件体验，以允许一键注册。 利用此服务更新，最终用户只需单击隔离电子邮件中的单个链接，就可完成公司门户应用中的注册过程。
### 移动设备和应用管理更新
**Android** 如博客文章 [Microsoft Intune 为 Android Marshmallow 提供 0 天支持](http://blogs.technet.com/b/microsoftintune/archive/2015/10/09/microsoft-intune-to-provide-day-0-support-for-android-marshmallow.aspx)中所述，所有 Intune 管理功能现在均支持 Android 6.0 (Marshmallow)

**iOS** 再也不能对运行早于 iOS 7.1 的版本的 iOS 设备创建新的应用部署。 对运行早于 iOS 7.1 的版本的设备的所有现有应用部署将继续工作，并由 Intune 管理。

**Windows 10** Intune 现在支持使用 **Windows 应用包**软件安装程序类型部署 Windows 10 通用应用。 有关详细信息和要求，请参阅[开始在 Microsoft Intune 中部署应用](http://technet.microsoft.com/en-US/library/dn646955.aspx)。


### Microsoft 公司门户应用的更改和更新
此版本已针对公司门户应用进行了如下更改：**iOS** 已向公司门户应用添加新按钮，方便用户向其 IT 管理员发送诊断日志：

|按钮名称|显示位置|
|------------|---------------|
|报告|错误警报消息|
|发送诊断报告|公司门户应用的“关于”屏幕|


>[!div class="step-by-step"]

>[&larr; **Intune 中的新增功能**](whats-new-in-microsoft-intune.md)    



<!--HONumber=Jun16_HO3-->


