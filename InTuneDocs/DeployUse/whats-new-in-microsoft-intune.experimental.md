---
# required metadata

experiment_id: lindavr-abtest-20160527
title: 新增功能 | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune 新增功能
## 2016 年 6 月

### 公司门户更新

#### iOS 公司门户应用

- 当最终用户安装业务线应用时，现在它们将看到改进的应用安装体验。 如果应用安装要花很长时间，用户可以手动同步设备以强制继续同步过程。 若要查看最终用户说明，请参阅[手动同步 iOS 设备](/Intune/EndUser/sync-your-device-manually-ios.md)。

- 适用于 iOS 的 Microsoft Intune 公司门户应用已更新，可支持 iOS 8.0 和更高版本。 此更新意味着，仅当设备正在运行 iOS 8.0 或更高版本时，最终用户才可在 Intune 中安装公司门户应用并注册新设备。 如果用户已注册运行不受支持的 iOS 版本的设备，则这些用户可以继续使用其设备上的公司门户应用。

## 2016 年 5 月


所有这些功能也受混合部署 (Configuration Manager with Intune) 支持。 有关新的混合功能的详细信息，请查看[混合新增功能](https://technet.microsoft.com/en-us/library/mt718155.aspx)页。

### 文档

欢迎使用 [docs.microsoft.com](https://docs.microsoft.com/en-us/intune) 预览版本！
这是一个全新的新式内容平台，旨在使作为我们客户的你能更容易地理解和使用 Intune。
若要了解所有最新功能，请参阅 [Introducing docs.microsoft.com](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/)（docs.microsoft.com 简介）

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
-
#### 公司门户网站

**公司门户网站：设备标识横幅将向最终用户提供详细信息。** 最终用户现在能够更轻松地标识他们在使用公司门户网站时所选的设备。 如果选择了错误的设备，他们将能够通过点击主页标题栏中的**点击此处**链接选择正确的设备。


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

    在**管理员**工作区，单击**通知规则** > **创建新规则**

    在创建通知规则向导的步骤二中，选择此规则所针对的设备组。 将从 Intune 控制台中删除“选择设备组”这一步骤。

    此更改的初步时间线如下：
    - 2016 年 6 月，新租户将看不到创建通知规则向导的步骤二。 正在退出的租户不受影响。
    - 2016 年 8 月左右，某些正在退出的租户将看不到向导中的“选择设备组”。
    - 2016 年 10 月左右，我们期望所有租户将不会看到向导中的“选择设备组”。


- **iOS 公司门户应用的支持更改**。 未来数月中，Microsoft Intune 公司门户应用 iOS 版将会更新，更新后仅支持运行 iOS 8.0 或更高版本的设备。 用户将无法注册运行 iOS 8.0 以下版本的新设备。 已注册的运行 iOS 8.0 以下版本的设备将继续受管理，且在有限时间内，能够继续使用公司门户应用。 但是，只有 iOS 8.0 或更高版本的设备才能访问最新版本的公司门户应用。 我们鼓励你通知用户更新到 iOS 8.0 或更高版本以充分利用 Intune 的新功能。



## 早期 Intune 发行版本
如果想要查看在过去六个月内发布在 Intune 中的内容，它们已在[早期 Intune 发行版本](previous-intune-releases.md)文章中列出。
> [!div class="op_single_selector"]
- [2016 年 4 月](previous-intune-releases.md)
- [2016 年 3 月](previous-intune-releases.md)
- [2016 年 2 月](previous-intune-releases.md)
- [2016 年 1 月](previous-intune-releases.md)
- [2015 年 12 月](previous-intune-releases.md)
- [2015 年 11 月](previous-intune-releases.md)




### 另请参阅
* [Microsoft Intune 博客](http://go.microsoft.com/fwlink/?LinkID=273882)
* [云平台路线图](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)


<!--HONumber=Jun16_HO2-->


