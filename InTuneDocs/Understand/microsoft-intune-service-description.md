---
title: "服务说明 | Microsoft Intune"
description: "Intune 是一项基于云的服务，可帮助你管理 Windows 电脑以及 iOS、Mac OS X、Android 和 Windows 移动设备。"
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 40fa5a2e-6c0f-4150-9740-d5ddc0cdbda0
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c1e215320168c659d5f838355f6350111d6979b0
ms.openlocfilehash: 98a5013ef42732e6a1a541e128986bedbb004611


---

# Microsoft Intune 服务说明

Microsoft Intune 是一项基于云的服务，可帮助你管理 Windows 电脑以及 iOS、Mac OS X、Android 和 Windows 移动设备。 Intune 还有助于保护公司的应用程序和数据。 你可以单独使用 Intune，也可以将它与 System Center 2012 R2 Configuration Manager 集成，以扩展管理能力。

Microsoft 为合格的计划中的合格服务提供了 Intune 载入权益。 载入权益允许你与 Microsoft 专家远程合作，以便使你的 Intune 环境可供使用。 有关详细信息，请参阅[Microsoft Intune 载入权益说明](http://go.microsoft.com/fwlink/?LinkId=619281)。

你可以使用具有 100 个用户许可证的 30 天免费试用版的 Intune。 若要开始免费试用，[请单击此处访问 Intune 注册页面](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/)。 如果你的组织有企业协议或等效的批量许可协议，请与 Microsoft 代表联系以设置免费试用版。

> [!NOTE]
> 如果你的组织已有 Microsoft Online Services 工作或学校帐户，并且你有可能会在试用期结束后继续在生产中使用此 Intune 订阅，则应单击该页上的“登录”选项，并使用组织的全局管理员帐户进行身份验证。 此操作将确保你的 Intune 试用版链接到你的现有工作或学校帐户。

如需可以在移动设备上配置的设置的列表，请参阅：

-   [Microsoft Intune 中的移动设备管理功能](/intune/get-started/mobile-device-management-capabilities-in-microsoft-intune)

-   [Configuration Manager 中移动设备的常规设置](https://technet.microsoft.com/library/dn376523.aspx)

有关 System Center 2012 R2 Configuration Manager 的信息，请参阅 [System Center 2012 Configuration Manager 的文档库](https://technet.microsoft.com/library/gg682041.aspx)。

## 了解 Intune 服务更新对你的影响
由于 Intune 是一项在线服务，因此，Microsoft 可以定期对其更新。

使用本主题中的信息可帮助你了解这些服务更新的频率，以及我们在更新可能影响你使用该服务时提前向你发送的通知。

若要了解有关 Intune 服务的更改信息，请参阅 [What's new in Microsoft Intune（Microsoft Intune 新增功能）](/intune/deploy-use/Whats-new-in-microsoft-intune.md)。 [Microsoft Intune 博客](http://blogs.technet.com/b/microsoftintune/)也讨论了该服务中的更改信息，并为你能够最大程度从 Intune 中获益提供了有用的提示。

重要的服务更新将也会在 [Office 365 管理门户](https://portal.office.com/Admin/Default.aspx)消息中心传达给你。 如果安装了配套 [Office 365 管理移动应用](https://support.office.com/article/Office-365-Admin-Mobile-App-e16f6421-2a1a-4142-bf9d-9846600a060a)，就可以在你的移动设备上接收通知。

> [!NOTE]
> 你可以在 [Office 365 管理门户](https://portal.office.com/Admin/Default.aspx)中监视 Intune 服务运行状况。 在左侧窗格中选择**服务运行状况**。  

以下是 Microsoft 提供的有关 Intune 服务的通知类型：
-   为了帮助你对服务更改做好计划，我们将根据此更改的影响，至少在服务升级前 30-90 天通知你。 将使用诸如公告板警报之类的产品内传达通道进行传达。 这些更改可能包括：
* 可能具有合规性或法规影响的更新
* 用户体验、用户界面和工作流的变化
* 新的或已更改的 API — 通知你需要进行测试，以确保自定义应用的后向兼容性
* 系统需求的变化，例如，所需的最低浏览器版本
* 任何需要你采取操作以启用功能或避免服务中断功能的更新。
-   Microsoft 在我们的每月服务更新中提供了有关新特征、新功能和对现有功能的改进的信息。 通常情况下，Microsoft 会在每个月的中旬左右汇总服务更新。 [Microsoft Intune 新增功能](/intune/deploy-use/whats-new-in-microsoft-intune)中描述了相关更新。
-   如果要停用 Intune 服务，我们将提前 12 个月通知你。

## 选择适合你的管理解决方案
可以通过多种方式配置 Intune 来管理和帮助保护公司的移动设备和计算机（在本文档中称为“设备”）。

-   **Intune 独立配置。** 使用 Intune 中基于 Web 的管理控制台来管理组织中的设备。 可以在没有任何本地 IT 基础结构的情况下使用 Intune，但如果你将 Intune 与 Active Directory 域服务一起使用，则可以将使用域服务管理的域用户帐户用于 Intune。

-   **Intune 与 System Center Configuration Manager 的集成** 使用 Configuration Manager 管理控制台来管理企业中的计算机和移动设备。 此配置可帮助你通过单一控制台（Configuration Manager 管理控制台）管理组织的所有设备。 Configuration Manager 支持大量的移动设备、服务器和计算机。 有关详细信息，请参阅 [System Center 2012 Configuration Manager 的文档库](https://technet.microsoft.com/library/gg682041.aspx)中的[如何使用 Configuration Manager 和 Microsoft Intune 管理移动设备](http://go.microsoft.com/fwlink/?LinkID=271118)。  有关确定哪种方法最适合你的更多帮助，请参阅[在 Microsoft Intune 独立版和带 Configuration Manager 的混合移动设备管理之间选择](https://technet.microsoft.com/en-us/library/mt706478.aspx)。


## 了解有关 Intune 的详细信息
使用以下资源可了解有关 Intune 的详细信息：

-   [Microsoft Intune 信任中心](http://www.microsoft.com/en-us/server-cloud/products/intune-trust-center/)提供了有关 Intune 的安全性、隐私和合规性实践的信息，并介绍了 Intune 的一些证书。

-   [Microsoft Intune 中的移动设备管理功能](/intune/understand-explore/mobile-device-management-capabilities-in-microsoft-intune)

### 另请参阅
[Microsoft Intune](https://docs.microsoft.com/intune/)
[System Center 2012 Configuration Manager 的文档库](https://technet.microsoft.com/library/gg682041.aspx)

[Microsoft Intune 新增功能](/intune/deploy-use/whats-new-in-microsoft-intune)



<!--HONumber=Jul16_HO3-->


