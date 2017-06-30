---
title: "Microsoft Intune 服务说明"
description: "Intune 是一项基于云的服务，有助于管理 Windows、iOS、Mac OS X、Android 和 Windows Mobile 设备。"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 06/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 40fa5a2e-6c0f-4150-9740-d5ddc0cdbda0
ms.reviewer: cacamp
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 73b43084c28436cb8a7e866dcee2d52694c60f5c
ms.openlocfilehash: 830a23e63536829f3905ff291bff25e0890457e8
ms.contentlocale: zh-cn
ms.lasthandoff: 06/16/2017


---

# <a name="microsoft-intune-service-description"></a>Microsoft Intune 服务说明

[!INCLUDE[both-portal](./includes/note-for-both-portals.md)]

Microsoft Intune 是一项基于云的服务，有助于管理运行 Windows、Mac OS X、iOS、Android 或 Windows Mobile 的设备。 Intune 还有助于保护公司的应用程序和数据。 可以单独使用 Intune，也可以将它与 System Center Configuration Manager 集成，以扩展管理能力。

Microsoft 为合格的计划中的合格服务提供了 Intune 载入权益。 载入权益允许你与 Microsoft 专家远程合作，以便使你的 Intune 环境可供使用。 有关载入权益的详细信息，请参阅 [Microsoft Intune 载入权益说明](http://go.microsoft.com/fwlink/?LinkId=619281)。

可以通过包含 100 个用户许可证的 30 天免费试用版开始使用 Intune。 若要开始免费试用，[请转到 Intune 注册页面](https://www.microsoft.com/server-cloud/products/microsoft-intune/)。 如果组织有企业协议或等效的批量许可协议，请与 Microsoft 代表联系以设置免费试用版。

> [!NOTE]
> 如果你的组织已有 Microsoft Online Services 工作或学校帐户，并且你有可能会在试用期结束后继续在生产中使用此 Intune 订阅，请选择该页上的“登录”选项，并使用组织的全局管理员帐户进行身份验证。 此操作可确保你的 Intune 试用版链接到你现有工作或学校帐户。

有关可在移动设备上配置的设置列表，请参阅：

-   [Microsoft Intune 的已注册设备管理功能](introduction-intune.md)

-   [使用 System Center Configuration Manager 和 Microsoft Intune 的混合移动设备管理 (MDM)](/sccm/mdm/understand/hybrid-mobile-device-management)

有关 System Center Configuration Manager 的详细信息，请参阅 [System Center Configuration Manager 文档](/sccm/index)。

## <a name="learn-how-intune-service-updates-affect-you"></a>了解 Intune 服务更新对你的影响

由于 Intune 是一项联机服务并且 MDM 生态系统会随着移动设备操作系统和移动应用发布频繁更改，因此，Microsoft 将会定期更新 Intune。

使用本文中的信息可帮助你了解这些服务更新的频率，以及我们在更新可能影响你使用该服务时提前向你发送的通知。

有三种方式可了解有关 Intune 服务中的更改内容：

- 第一种方式是查看 [Microsoft Intune 新增功能](whats-new.md)。 此列表会随每月服务更新，以及每周发布公司门户应用等应用时更新。 

- 第二种方式是重要的服务更新也将会在 [Office 365 管理门户](https://portal.office.com/Admin/Default.aspx)消息中心传达给你。 如果安装了配套 [Office 365 管理移动应用](https://support.office.com/article/Office-365-Admin-Mobile-App-e16f6421-2a1a-4142-bf9d-9846600a060a)，就可以在你的移动设备上接收通知。 可在[此处](https://support.office.com/en-US/client/results?Shownav=true&lcid=1033&ns=O365ENTADMIN&version=15&omkt=en-US&ver=15&HelpID=O365E_MCManageUpdates)查找有关 Office 365 消息中心内部工作方式的详细信息。 
    
    以下为某些有帮助的提示： 

    - Office 365 消息中心中的消息是有针对性的。 这意味着，如果你的公司不具有适用于 EDU 产品/服务的 Intune，我们不会向你发送有关适用于 EDU 的 Intune 消息。 

    - 消息过期。 例如，您的服务已更新的通知与“新增功能”页面的链接可能会在下一个服务更新通知之前过期。 否则，你可能会积压大量不再相关的消息。

    - Office 365 管理移动应用允许你搜索所有消息，并且，如果你想要与组织中的同事分享，还可转发通知。

    - 在编辑消息中心首选项下方，我们最终将切换为 **Intune**，因此，你会看到这些发布到 Intune 订阅上的消息。 如果你看到的是 Office 365 的移动设备管理，而不是 Intune 的，那么你看到的是不同的服务。

- 第三种方式是我们使用两个博客来分享 EMS 消息和 Intune 支持的最佳做法： 
    
    - [企业移动性 + 安全博客](https://blogs.technet.microsoft.com/enterprisemobility/) 

    - [Intune 支持博客](https://blogs.technet.microsoft.com/intunesupport/) 

>[!Note]
>你可以在 [Office 365 管理门户](https://portal.office.com/Admin/Default.aspx)中监视 Intune 服务运行状况。 在左侧窗格中选择**服务运行状况**。 你还可以使用 [Office 365 管理移动应用](https://support.office.com/article/Office-365-Admin-Mobile-App-e16f6421-2a1a-4142-bf9d-9846600a060a)查看服务运行状况。

## <a name="types-of-notices-microsoft-provides-about-the-intune-service"></a>Microsoft 提供有关 Intune 服务的通知类型

为了帮助你对服务更改做好计划，我们将根据更改产生的影响，至少在服务变更前的 7-90 天通知你。 这些更改可能包括任何以下类型的更改：

- 对你可能想要与支持人员或最终用户分享的最终用户体验的更改。 对此类更改，我们通常在 7-30 天前通知并将它们记录在 [Intune 应用 UI 中的新增功能](whats-new-app-ui.md)。 对于拼写错误的更改，我们通常不会在文档中标注。 但是，在 UI 中最终用户注册体验的任何一项更改都是非常重要的，因此，我们将会向 Office 365 消息中心的客户发送消息，并链接到 Intune App UI 中的“新增功能”部分，以便客户收到具体变更的通知，并在生产中推出更改之前有时间评估和更新最终用户的指南。

- 需要你采取操作的更改称为“计划更改”，通常会提前大约 30 天通知。 在 Office 365 消息中心，该“类别”会特别提及“计划更改”，而且，如果我们有在生产中推出更改的确切日期，我们还会加入“采取行动”日期，让你看到更改队列和解释标记。

- 对于大多数弃用功能，我们通常会提前 90 天发出弃用通知。 例如，如果我们不再支持特定版本的 IE，我们会计划提前 90 天发送通知。 但是，当另一家公司宣布弃用时，弃用通知将变得比较复杂。 例如，某一浏览器公司发出通知，他们将不再支持最新版本的 Silverlight，在这种情况下，我们会让客户知道我们即将停止对此浏览器的支持，但给客户通知的提前时间可能少于 90 天。

- 如果要停用 Intune 服务，我们将提前 12 个月通知你。

最后，对于需要采取任何事后操作让你的服务恢复正常，或根据客户反馈我们认为可能会带来巨大破坏的重大更改，在这种极少数的情况下，我们将根据 [Office 365 通信首选项](https://support.office.com/en-us/article/Change-your-contact-preferences-for-communications-from-Microsoft-6f70de1b-a64d-4498-bfbd-be8c83a9c0fc?ui=en-US&rs=en-US&ad=US)的设置方式，以及你是否拥有有效的（工作邮箱优先）电子邮件地址，向服务管理员发送电子邮件。  


## <a name="choose-the-management-solution-thats-right-for-you"></a>选择适合你的管理解决方案
可以通过多种方式设置 Intune 来管理和帮助保护公司的移动设备和计算机（本文中称为“设备”）。

- **Intune 独立配置。** 使用 Intune 中基于 Web 的管理控制台来管理组织中的设备。 可以在没有任何本地 IT 基础结构的情况下使用 Intune。 如果将 Intune 与 Active Directory 域服务一起使用，则可以将使用域服务管理的域用户帐户用于 Intune。

- **Intune 与 System Center Configuration Manager。** 使用 Configuration Manager 管理控制台来管理企业中的计算机和移动设备。 此配置有助于通过单一控制台（Configuration Manager 管理控制台）管理组织的所有设备。 Configuration Manager 支持大量的移动设备、服务器和计算机。 有关 Configuration Manager 的详细信息，请参阅[使用 System Center Configuration Manager 和 Microsoft Intune 的混合移动设备管理 (MDM)](/sccm/mdm/understand/hybrid-mobile-device-management)。 有关确定哪种方法最适合你的更多帮助，请参阅[在 Microsoft Intune 独立版和带 Configuration Manager 的混合移动设备管理之间选择](/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)。


## <a name="learn-more-about-intune"></a>了解有关 Intune 的详细信息
使用以下资源可了解有关 Intune 的详细信息：

- [Microsoft Intune 信任中心](https://www.microsoft.com/server-cloud/products/intune-trust-center/)提供了有关 Intune 的安全性、隐私和合规性实践的信息，并介绍了 Intune 的一些证书。

- [Microsoft Intune 的已注册设备管理功能](introduction-intune.md)

### <a name="see-also"></a>另请参阅
[Microsoft Intune](index.md)
[System Center 2012 Configuration Manager 的文档库](https://technet.microsoft.com/library/gg682041.aspx)

[Microsoft Intune 新增功能](whats-new.md)

