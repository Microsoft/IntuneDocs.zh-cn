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


## 应用管理
- **对 Windows 10 企业数据策略的更改。** 由于 Windows 10 企业数据策略中的应用策略改进功能，当你保存已配置应用规则（原来受保护的应用）的策略时，将丢失你所配置的所有现有规则。 若要继续，你将需要重新配置这些应用规则。

- **浏览器的条件性访问。** 可以为 Exchange Online 和 SharePoint Online 设置条件性访问策略，以便仅允许托管且合规的 iOS 和 Android 设备对其进行访问。 尝试通过 iOS 和 Android 设备登录到 Outlook Web Access (OWA) 和 SharePoint 站点的最终用户，系统将提示通过 Intune 注册其设备以及在完成登录前解决任何非合规性问题。
<!---TFS 1175844--->

- **Dynamics CRM Online 支持条件性访问。** 客户将能够为 Dynamics CRM Online 设置条件访问策略，以便仅允许托管且合规的 iOS 和 Android 设备对其进行访问。 系统将提示尝试登录到 iOS 和 Android 设备上的 Dynamics CRM 移动应用的最终用户注册 Intune 并在登录完成前修正任何非合规性问题。
<!---TFS1295358--->

### Xamarin 支持
Microsoft Intune 应用 SDK 现在支持这些方案中的 Xamarin 应用：

- 使用 Intune SDK 编写新应用，或修改现有的业务线应用。 你可以在 [Microsoft Intune Github](https://github.com/msintuneappsdk) 页获取插件。
- 使用 Intune App Wrapping Tool 添加对现有业务线应用的 MAM 支持

有关选择要使用的方法的帮助信息，请参阅 [Decide how to prepare apps for mobile application management with Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)（决定如何使用 Microsoft Intune 为移动应用程序管理准备应用）。
<!--- TFS 1061478 & TFS 1152340--->


## Company Portal
**对 iOS 公司门户应用中设备注册管理器帐户的更改。** 为了提高性能和可扩展性，Intune 不再在 iOS 公司门户应用的“我的设备”窗格中显示所有设备注册管理器 (DEM) 设备。 仅显示运行该应用的本地设备，且仅限该设备通过公司门户应用注册的情况下。 DEM 用户可能会在本地设备上执行操作，但只能从 Intune 管理员控制台远程管理其他已注册设备。  此外，Intune 将不支持通过 Apple 设备注册计划或 Apple 配置器工具使用 DEM 帐户。 这两种注册方法已支持共享的 iOS 设备的无用户注册。  当共享设备的无用户注册不可用时，仅使用 DEM 帐户。
<!---TFS 1233681--->

## 服务弃用
**适用于 Windows 8 和 Windows Phone 8 的公司门户应用将从 2016 年 9 月起弃用。** 从 2016 年 9 月开始，Microsoft Intune 将结束为适用于 Windows Phone 8 和 Windows 8 平台的 Microsoft Intune 公司门户应用提供支持。 将设备更新到 Windows 8.1 和 Windows Phone 8.1，并使用相应的 Windows 8.1 和 Windows Phone 8.1 公司门户应用继续向这些设备分发应用。
<!---TFS 1255391--->

**通知规则删除的自定义组目标。**
Intune 通知规则定义将从 Intune 向其发送电子邮件警报的人员。 当前，你可将通知规则配置为向你创建的 Intune 设备组中的设备所有用户发送电子邮件。 约从 2016 年 6 月 1 日起，已不再支持目标用户创建组。

此更改的初步时间线如下：
- 2016 年 6 月，新租户将看不到创建通知规则向导的步骤二。 正在退出的租户不受影响。
- 2016 年 8 月左右，某些正在退出的租户将看不到向导中的“选择设备组”。
- 2016 年 10 月左右，我们期望所有租户将不会看到向导中的“选择设备组”。

<!---   TFS 1278864--->
**iOS 公司门户应用的支持更改。**
用户必须更新到最新的 iOS 公司门户应用。 在未来几个月，要求适用于 iOS 的 Microsoft Intune 公司门户应用的所有用户都使用最新版本。 新用户将只能够下载最新版本，而当前用户必须更新到最新版本。 最新版本需要 iOS 8.0 或更高版本，因此运行较旧的 iOS 版本的设备将无法使用公司门户或者进行注册，直到将其设备更新为 iOS 8.0 或更高版本，并且将公司门户应用更新到最新版本。 运行 iOS 8.0 以下版本的已注册设备将继续受管理，并将列在 Intune 管理员控制台中。  

**Intune 查看器应用。** 随着新的 RMS 共享应用的发布，我们将从 2016 年 8 月起删除以下 Intune 查看器应用：
- Intune AV 查看器
- Intune PDF 查看器
- Google Play 中适用于 Android 的 Intune 图像查看器

建议使用适用于 Android 的 Rights Management 应用（RMS 共享）而不是使用 Intune 查看器应用，前者只需部署一个应用而不是三个单独的应用便可安全地查看 Android 设备上的公司文件。 了解有关 RMS 共享应用（具有指向文档的链接）的详细信息。


### 另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new-in-microsoft-intune.md)。


<!--HONumber=Jun16_HO2-->


