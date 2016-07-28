---
title: "即将推出的功能 | Microsoft Intune"
description: 
keywords: 
author: Lindavr
manager: jeffgilb
ms.date: 07/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 35ee5d0c8898c95898c0527a623cf13c454387f2
ms.openlocfilehash: 831cec6cd0e02a94c1a3f67d4adf5a5dcbb01449


---

# Microsoft Intune 中即将推出的功能 - 7 月
此信息在非常有限的情况下依据保密协议 (NDA) 提供，并不断变化。 此处列出的某些功能有无法按期发布的风险并可能推迟到以后的版本。 正在以试验模式（外部测试）测试其他功能，以确保它们可立即供客户使用。 如果有任何问题或顾虑，请联系 Intune/PM 好友。

本页将定期更新。 回来查看即将推出的更新。

下面的更改依据 Intune 开发。 所有这些功能最终将支持混合客户部署（带 Intune 的 Configuration Manager）。 有关新的混合功能的详细信息，请查看[混合新增功能页](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx)。


## 应用管理
### 改善应用预配配置文件更新体验
Apple iOS 业务线移动应用附带预配配置文件和证书签名的代码。 当应用在 iOS 设备上运行时，iOS 会确认 iOS 应用的完整性，并强制实施由预配配置文件定义的策略。

用于签署应用的企业签名证书通常持续 3 年。 但是，预配配置文件将在 1 年后过期。 利用此更新，Intune 将为你提供一些工具，用于主动地将新预配配置文件策略部署到安装了即将到期的应用而证书仍有效的设备。
<!--- TFS 1280247--->

### Xamarin 支持
Microsoft Intune 应用 SDK 将在这些方案中支持 Xamarin 应用：

- 使用 Intune SDK 编写新应用，或修改现有的业务线应用。 你将在 [Microsoft Intune Github](https://github.com/msintuneappsdk) 页获取插件。
- 使用 Intune App Wrapping Tool 添加对现有业务线应用的 MAM 支持

有关选择要使用的方法的帮助信息，请参阅 [Decide how to prepare apps for mobile application management with Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)（决定如何使用 Microsoft Intune 为移动应用程序管理准备应用）。

<!--- TFS 1061478 & TFS 1152340--->

## 设备管理
### 提高了设备注册限制
Intune 会将每个用户的设备的最大可配置设备注册限制从 5 提高到 15。
<!---TFS 1289896 --->

## 组管理
### Intune 组将于 2016 年 8 月初过渡到 Azure Active Directory 组
Intune 正在创建将 Azure Active Directory (AAD) 安全组用作 Intune 中的用户和设备组的新组管理体验。 **当我们介绍新的基于 Azure 的 Intune 管理门户时**，这些组将用于所有组管理、策略部署和配置文件部署。

此新体验将会使你无需在服务之间重复组，**允许你访问某些新的 Azure Active Directory Premium (AADP) 组功能**，并提供使用 PowerShell 和图表的可扩展性。 这还将跨企业移动性管理统一组管理体验。

若要启用移动到安全组，**当前管理控制台**中的体验将进行一些修改。 **这些更改和 AAD 安全组的使用情况将记录在 Intune 文档中**。

Intune 的新客户将看到**当前租户执行操作之前的一些安全组更改**。

除了组管理中的更改，**还将弃用以下功能**：
- 在创建新组的过程中排除成员或组
- 服务管理员角色中的“管理组”
- 对通知规则的基于组的自定义警报
- 利用报表中的组进行透视


## Company Portal

### 向 Android 公司门户添加“通知”
我们即将于 8 月发布 Android 公司门户的更新，这将在主页上引入一个新的“**通知**”图标。 点击此图标将访问“**通知**”页，该页将向你的最终用户显示在公司门户应用中需要注意的所有项，例如，设备非合规性、注册更新和注册激活。 如果还使用 iOS 公司门户应用，你将已看到通知体验。 通过引入“**通知**”页，只要设备已经注册，每次启动或恢复 Android 公司门户时，你将不会看到“**公司访问设置**”页。 我们听说你们中的许多人都已创建最终用户指南，而且非常感谢你们在指南/屏幕快照可能需要更新时提前通知我们。 请更新你的文档，以反映体验中即将发生的更改。 有关更新的屏幕快照，请访问：https://aka.ms/androidcpupdate。  

### 帮助用户解决工作区加入失败时的注册问题
使用条件访问时，Windows 8.1、Windows 10 桌面版和 Windows 10 移动版的注册步骤已针对体验工作区加入 (WPJ) 失败的最终用户在公司门户网站中进行了简化。 以前，当最终用户尝试注册并执行 WPJ，而且注册已成功，但 WPJ 失败时，已注册的设备将不出现在用户标识的设备列表中，因而使用户感到困惑。 用户现在将看到单独的“设备注册”和“工作区加入”步骤，从而在 WPJ 失败后更易于看到设备的状态以及完成此过程。 执行单独的步骤还可以简化 IT 管理员排除故障的过程。

### 对 iOS 公司门户应用中设备注册管理器帐户的更改
若要提高性能和可扩展性，Intune 将不再在 iOS 公司门户应用的“我的设备”窗格中显示所有设备注册管理器 (DEM) 设备。 将仅显示运行该应用的本地设备，且仅限该设备通过公司门户应用注册的情况下。 DEM 用户可能会在本地设备上执行操作，但只能从 Intune 管理员控制台远程管理其他已注册设备。  此外，Intune 将不支持通过 Apple 设备注册计划或 Apple 配置器工具使用 DEM 帐户。 这两种注册方法已支持共享的 iOS 设备的无用户注册。 当共享设备的无用户注册不可用时，仅使用 DEM 帐户。
<!---TFS 1233681--->
### 限制旁加载应用安装到注册的 Android 设备
Android 设备不能再通过公司门户网站安装应用程序，除非使用适用于 Android 的 Intune 公司门户应用已在 Intune 中注册设备。 
<!---TFS 1299082--->

## 服务弃用
**适用于 Windows 8 和 Windows Phone 8 的公司门户应用将从 2016 年 9 月起弃用。** 从 2016 年 9 月开始，Microsoft Intune 将结束为适用于 Windows Phone 8 和 Windows 8 平台的 Microsoft Intune 公司门户应用提供支持。 将设备更新到 Windows 8.1 和 Windows Phone 8.1，并使用相应的 Windows 8.1 和 Windows Phone 8.1 公司门户应用继续向这些设备分发应用。
<!---TFS 1255391--->

**通知规则删除的自定义组目标。**
Intune 通知规则定义将从 Intune 向其发送电子邮件警报的人员。 当前，你可将通知规则配置为向你创建的 Intune 设备组中的设备所有用户发送电子邮件。 约从 2016 年 6 月 1 日起，已不再支持目标用户创建组。

此更改的初步时间线如下：
- 2016 年 8 月，新租户将看不到创建通知规则向导的步骤二。 现有的租户不受影响。
- 2016 年 9 月左右，某些现有租户将看不到向导中的“选择设备组”。
- 2016 年 11 月左右，我们期望所有租户将不会看到向导中的“选择设备组”。

<!---   TFS 1278864--->

**iOS 公司门户应用的支持更改。**
在 7 月，要求适用于 iOS 的 Microsoft Intune 公司门户应用的所有用户都使用最新版本。 新用户将只能够下载最新版本，而当前用户必须更新到最新版本。 最新版本需要 iOS 8.0 或更高版本，因此运行较旧的 iOS 版本的设备将无法使用公司门户或者进行注册，直到将其设备更新为 iOS 8.0 或更高版本，并且将公司门户应用更新到最新版本。 运行 iOS 8.0 以下版本的已注册设备将继续受管理，并将列在 Intune 管理员控制台中。  

**Intune 查看器应用。** 随着新的 RMS 共享应用的发布，我们将从 2016 年 8 月起删除以下 Intune 查看器应用：
- Intune AV 查看器
- Intune PDF 查看器
- Google Play 中适用于 Android 的 Intune 图像查看器

建议使用适用于 Android 的 Rights Management 应用（RMS 共享）而不是使用 Intune 查看器应用，前者只需部署一个应用而不是三个单独的应用便可安全地查看 Android 设备上的公司文件。 了解有关 RMS 共享应用（具有指向文档的链接）的详细信息。



### 另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new-in-microsoft-intune.md)。



<!--HONumber=Jul16_HO3-->


