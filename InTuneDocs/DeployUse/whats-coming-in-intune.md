---
# required metadata

title: 即将推出的功能 | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 05/17/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d

# optional metadata

ROBOTS: noindex,nofollow
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune 即将推出的功能
此信息在非常有限的情况下依据保密协议 (NDA) 提供，并不断变化。 此处列出的某些功能有无法按期发布的风险并可能推迟到以后的版本。 正在以试验模式（外部测试）测试其他功能，以确保它们可立即供客户使用。 如果有任何问题或顾虑，请联系 Intune/PM 好友。

本页将定期更新。 回来查看即将推出的更新。

下面的更改依据 Intune 开发。 所有这些功能还将支持混合客户部署（通过 Intune 使用 Configuration Manager）。 有关新的混合功能的详细信息，请查看[混合新增功能页](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx)。

## Intune 通信
- **Intune 服务运行状况信息。** Intune 服务运行状态信息已被移动到包含其他 Microsoft 服务的一个中心位置。 现在你可以在服务运行状态下[ Office 365 管理门户](https://portal.office.com/Admin/Default.aspx)中找到此信息。 有关详细信息，请参阅[此博客文章](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/)。

- **消息中心 UI 载入。** 作为 Intune 迁移到 [Office 365 管理门户](https://portal.office.com/)的一部分，我们将开始利用其消息中心以沟通新功能和其他通知。 另外，通过安装随附的 Office 365 管理员移动应用，可在移动电话上收到通知，并轻松地将任何消息转发到用户或分发别名。
我们将开始通过五月发行版本使用消息中心，以在更新完成时通知你，并且将包括有关新的和改进的 Intune 功能的信息。 现在可以通过登录到 [Office 365 管理门户](https://portal.office.com/)，然后选择左导航窗格中的**消息中心**选项来查看消息中心。

## 应用管理
- **可通过 MAM 策略管理的新应用。** 适用于 Android 的 Microsoft Word、Excel 和 PowerPoint 应用现在可与未向 Intune 注册的设备上的 MAM 策略相关联。 若要获取支持的应用的完整列表，请转到 [Microsoft Intune application partners](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)（Microsoft Intune 应用程序合作伙伴）页上的 Microsoft Intune mobile application gallery（Microsoft Intune 移动应用程序库）。


- **浏览器的条件性访问。** 可以为 Exchange Online 和 SharePoint Online 设置条件性访问策略，以便仅允许托管且合规的 iOS 和 Android 设备对其进行访问。 尝试通过 iOS 和 Android 设备登录到 Outlook Web Access (OWA) 和 SharePoint 站点的最终用户，系统将提示通过 Intune 注册其设备以及在完成登录前解决任何非合规性问题。
<!---TFS 1175844--->

- **MAM SDK：支持 PIN 长度配置。** 你将能够指定类似于设备 PIN 的 MAM 应用的 PIN 的长度。 这将要求最终用户符合你设置的新限制。 他们将看到一个稍经修改的 PIN 屏幕来解释较长输入。
<!--- TFS 1104753--->

- **Skype for Business for Android。** Intune 管理员现在可以通过 MAM 以 Skype for Business 为目标，而不需要注册策略。  他们的用户登录后，将应用 MAM 策略。
<!--- TFS item 1248444 --->

- **Skype for Business for iOS。** Intune 管理员现在可以通过 MAM 以 Skype for Business 为目标，而不需要注册策略。  他们的用户登录后，将应用 MAM 策略。
<!--- TFS item 1248443 --->

### Xamarin 支持
Microsoft Intune 应用 SDK 现在支持这些方案中的 Xamarin 应用：

- 使用 Intune SDK 编写新应用，或修改现有的业务线应用。 你可以在 [Microsoft Intune Github](https://github.com/msintuneappsdk) 页获取插件。
- 使用 Intune App Wrapping Tool 添加对现有业务线应用的 MAM 支持

有关选择要使用的方法的帮助信息，请参阅 [Decide how to prepare apps for mobile application management with Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)（决定如何使用 Microsoft Intune 为移动应用程序管理准备应用）。
<!--- TFS 1061478 & TFS 1152340--->


## 设备管理
- **Windows 电脑的远程协助会话。** 用于 Windows 桌面代理托管的电脑的 TeamViewer 集成将允许你使用支持最终用户支持人员部门的 Windows 桌面代理托管的电脑建立远程协助会话。 这包括 Windows 7、Windows 8、Windows 8.1 和 Windows 10。
<!--- TFS 1284856--->



## Company Portal

- **最终用户 toast 通知。** 当最终用户从公司门户注册设备或删除设备时，现在他们将会看到来自 Andoid 公司门户应用的 toast 通知。
- **设备标识横幅将向最终用户提供详细信息。** 最终用户将能够轻松地标识他们在使用公司门户网站时所选的设备。 如果选择了错误的设备，他们将能够通过点击主页标题栏中的“点击此处”链接选择正确的设备。
<!--- TFS 1231157--->

- **对 Android 公司门户应用中设备注册管理器帐户的更改。** 若要提高性能和可扩展性，Intune 将不再在 Android 公司门户应用的**我的设备**窗格中显示所有设备注册管理器 (DEM) 设备。 将仅显示运行该应用的本地设备，且仅限该设备通过公司门户应用注册的情况下。 DEM 用户可能会在本地设备上执行操作，但将只能从 Intune 管理员控制台远程管理其他已注册设备。

- **对 iOS 公司门户应用中设备注册管理器帐户的更改。** 若要提高性能和可扩展性，Intune 不再在 iOS 公司门户应用的“我的设备”窗格中显示所有设备注册管理器 (DEM) 设备。 仅显示运行该应用的本地设备，且仅限该设备通过公司门户应用注册的情况下。 DEM 用户可能会在本地设备上执行操作，但只能从 Intune 管理员控制台远程管理其他已注册设备。  此外，Intune 将不支持通过 Apple 设备注册计划或 Apple 配置器工具使用 DEM 帐户。 这两种注册方法已支持共享的 iOS 设备的无用户注册。  当共享设备的无用户注册不可用时，仅使用 DEM 帐户。



## 服务弃用
**通知规则删除的自定义组目标。**
Intune 通知规则定义将从 Intune 向其发送电子邮件警报的人员。 当前，你可将通知规则配置为向你创建的 Intune 设备组中的设备所有用户发送电子邮件 约从 2016 年 6 月 1 日起，将不再支持目标用户创建组。

当前，若要为从 Microsoft Intune 管理控制台创建的组指定通知规则，应采用以下步骤：

在**管理员**工作区，单击**通知规则** > **创建新规则**

在创建通知规则向导的步骤二中，选择此规则所针对的设备组。 将从 Intune 控制台中删除“选择设备组”这一步骤。

此更改的初步时间线如下：
- 2016 年 6 月，新租户将看不到创建通知规则向导的步骤二。 正在退出的租户不受影响。
- 2016 年 8 月左右，某些正在退出的租户将看不到向导中的“选择设备组”。
- 2016 年 10 月左右，我们期望所有租户将不会看到向导中的“选择设备组”。

<!---   TFS 1278864--->
**iOS 公司门户应用的支持更改。**
未来数月中，Microsoft Intune 公司门户应用 iOS 版将会更新，更新后仅支持运行 iOS 8.0 或更高版本的设备。 用户将无法注册运行 iOS 8.0 以下版本的新设备。 已注册的运行 iOS 8.0 以下版本的设备将继续受管理，且在有限时间内，能够继续使用公司门户应用。 但是，只有 iOS 8.0 或更高版本的设备才能访问最新版本的公司门户应用。 我们鼓励你通知用户更新到 iOS 8.0 或更高版本以充分利用 Intune 的新功能。  

- **Intune 查看器应用。** 随着新的 RMS 共享应用的发布，我们将从 2016 年 8 月起删除以下 Intune 查看器应用：
    - Intune AV 查看器
    - Intune PDF 查看器
    - Google Play 中适用于 Android 的 Intune 图片查看器

  建议使用适用于 Android 的 Rights Management 应用（RMS 共享）而不是使用 Intune 查看器应用，前者只需部署一个应用而不是三个单独的应用便可安全地查看 Android 设备上的公司文件。 了解有关 RMS 共享应用（具有指向文档的链接）的详细信息。






### 另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new-in-microsoft-intune.md)。


<!--HONumber=May16_HO5-->


