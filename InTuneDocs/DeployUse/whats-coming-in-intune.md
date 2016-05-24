---
# required metadata

title: 即将推出的功能 | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 05/03/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d

# optional metadata

#ROBOTS:
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

下面的更改依据 Intune 开发。 所有这些功能还将支持混合客户部署（通过 Intune 使用 Configuration Manager）。 有关新的混合功能的详细信息，请查看[混合新增功能页](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).

## 消息中心载入
作为 Intune 迁移到 [Office 365 管理门户](https://portal.office.com/)的一部分，我们将开始利用其消息中心以沟通新功能和其他通知。  另外，通过安装随附的 Office 365 管理员移动应用，可在移动电话上收到通知，并轻松地将任何消息转发到用户或分发别名。<br>  
我们将开始通过五月发行版本使用消息中心，以在更新完成时通知你，并且将包括有关新的和改进的 Intune 功能的信息。  现在通过登录到 [Office 365 管理门户](https://portal.office.com/)，然后选择左导航窗格中的“消息中心”选项来查看消息中心。
<!---TFS 1242782--->


## 应用管理
- **浏览器的条件性访问。** 可以为 Exchange Online 和 SharePoint Online 设置条件性访问策略，以便仅允许托管且合规的 iOS 和 Android 设备对其进行访问。 尝试通过 iOS 和 Android 设备登录到 Outlook Web Access (OWA) 和 SharePoint 站点的最终用户，系统将提示通过 Intune 注册其设备以及在完成登录前解决任何非合规性问题。
<!---TFS 1175844--->

- **MAM SDK：支持 PIN 长度配置。** 你将能够指定类似于设备 PIN 的 MAM 应用的 PIN 的长度。 这将要求最终用户符合你设置的新限制。 他们将看到一个稍经修改的 PIN 屏幕来解释较长输入。
<!--- TFS 1104753--->

- **防止 Outlook 联系人同步的 MAM 控件 (iOS)。** 适用于移动应用程序管理而无需注册设备的新设置。 此设置使 Intune 管理员防止应用程序将联系人同步到 iOS 设备的本机通讯簿。 启用此设置后，应用将不再能够将联系人保存到本机通讯簿。 禁用此设置后，应用就可以将联系人保存到本机通讯簿。 Intune 管理员选择性擦除设备时，将删除已保存到本机通讯簿的所有联系人。 iOS 设备上的 Outlook 应用程序现在支持此新设置。
<!---TFS item 1276166--->

- **Skype for business for Android。** Intune 管理员现在可以通过 MAM 以 Skype for Business 为目标，而不需要注册策略。  他们的用户登录后，将应用 MAM 策略。
<!--- TFS item 1248444 --->

- **Skype for business for iOS。** Intune 管理员现在可以通过 MAM 以 Skype for Business 为目标，而不需要注册策略。  他们的用户登录后，将应用 MAM 策略。
<!--- TFS item 1248443 --->

### Xamarin 支持
Microsoft Intune 应用 SDK 现在支持这些方案中的 Xamarin 应用：

- 使用 Intune SDK 编写新应用，或修改现有的业务线应用。 你可以在 [Microsoft Intune Github](https://github.com/msintuneappsdk) 页获取插件。
- 使用 Intune App Wrapping Tool 添加对现有业务线应用的 MAM 支持

有关帮助选择要使用的方法，请参阅[决定如何使用 Microsoft Intune 为移动应用程序管理准备应用](https://docs.microsoft.com/en-us/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune).
<!--- TFS 1061478 & TFS 1152340--->


## 设备管理
- **Windows 电脑的远程协助会话。** 用于 Windows 桌面代理托管的电脑的 TeamViewer 集成将允许你使用支持最终用户支持人员部门的 Windows 桌面代理托管的电脑建立远程协助会话。 这包括 Windows 7、Windows 8、Windows 8.1 和 Windows 10。
<!--- TFS 1284856--->


<!--- TFS item 1274326 --->

## 访问控制
* **Skype for Business Online 支持条件性访问。** Intune 管理员将能够为 Skype for Business Online 设置条件性访问策略，以便仅允许托管且合规的 iOS 和 Android 设备对其进行访问。 系统将提示尝试登录到 iOS 和 Android 设备上的 Skype for Business 移动应用的最终用户注册 Intune 并在登录完成前修复任何非合规性问题。
<!---TFS item 1254499--->

## Company Portal
* **设备标识横幅将向最终用户提供详细信息。** 最终用户将能够轻松地标识他们在使用公司门户网站时所选的设备。 如果选择了错误的设备，他们将能够通过点击主页标题栏中的“点击此处”链接选择正确的设备。
<!--- TFS 1231157--->

* **可直接从公司门户获取 Windows 应用包**：使用 Windows 8、Windows 8.1 和 Windows RT 电脑的用户现在可以直接从公司门户网站安装 Windows 应用包（扩展名为.appx）。 以前，Intune 管理员必须在设备上部署或安装公司门户应用才能安装应用。
<!--- TFS item 1082481 --->

* **用户可以从公司门户远程锁定其设备**公司门户网站新增了远程锁定选项，这让最终用户在设备丢失或被盗时可以从门户网站远程锁定其设备。 下表列出了适用于 Intune 和带 Configuration Manager 的 Intune 的远程锁定平台支持。
<!--- TFS item 1195661 --->

|平台  |支持详细信息|
|---------|---------|
|iOS | 支持|
|Android | 支持|
|Windows Phone 8.1 | 支持|
|Windows 10 移动版 | 仅在手机设置了密码时支持|
|电脑（Windows 8.0 及更早版本） | 不支持|
|电脑 (Windows 8.1) | 不支持|
|Windows Phone 8。0 | 不支持|
|Windows 10 桌面版 | 不支持|

## 服务弃用
* **通知规则删除的自定义组目标。** 将在 2016 年 6 月初推出，你此后就不能再使用创建通知规则向导来找到具有通知规则的用户创建的组。

    现在，若要 Microsoft Intune 管理控制台找到用户创建的组，你可以依次选择“管理员” > “通知规则” > “创建新规则”。 在创建通知规则向导的步骤二中，必须选择此规则所针对的设备组。 已从 Intune 控制台弃用此步骤：**选择设备组**。

    6 月的 Intune 1606 版本后，将不再支持**选择设备组**。 但是，直到 2016 年 8 月，你仍然可以看到此选项。 8 月之后，我们将在两个月内的将我们的租户分阶段过渡到新体验。 到 2016 年 10 月底，所有现有客户都应转换到新体验。 迁移到新体验后，将不会再提供在特定组定位通知规则的选项。
<!---   TFS 1278864--->







### 另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new-in-microsoft-intune.md)。


<!--HONumber=May16_HO1-->


