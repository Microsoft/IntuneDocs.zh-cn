---
title: 包含文件
description: 包含文件
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 073115d33f9a4f22fe3706ef15860c2a8d8a68ee
ms.sourcegitcommit: 69aaf89140f82f344404e75a69dc59d8a1585b10
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675487"
---
这些注意事项提供重要信息可以帮助您准备将来的 Intune 更改和功能。 

### <a name="change-in-enrollment-workflow-with-intune-company-portal-on-corporate-ios-devices-authenticating-with-setup-assistant----1927359---"></a>使用设置助理进行身份验证的企业的 iOS 设备上通过 Intune 公司门户注册工作流中更改 <!-- 1927359 -->
没有用于注册 iOS 设备，通过 Apple 的企业设备注册方法-Apple Configurator、 Apple 业务经理、 Apple School Manager 或 Apple 设备注册计划 (DEP)，其中一个工作流中即将发生的更改时使用安装程序身份验证的助手。 此更改仅适用于具有用户关联注册的设备。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
此更改于~~三月~~四月推出时，将更新 Azure 门户中的 Intune 注册配置文件，以便你可以指定设备的身份验证方式以及是否收到公司门户应用。 将改进的工作流以通过上面列出的方法来注册 iOS 设备。 

- 当注册新设备，以及使用设置助理进行身份验证，您可以选择要自动部署的公司门户应用。 最终用户将无法再看到"标识设备"屏幕和注册流程中的"确认你的设备"屏幕。  
- 注册的设备上已通过设置助理通过 Apple 的企业设备注册方法之一，则必须采取措施，如果你想要启用条件性访问。 您必须使用特定 xml 推送到这些设备在公司门户中配置的应用配置策略。 若要执行此操作的方向是中的其他信息链接上的博客文章。 如果您选择将在公司门户推送以这种方式，最终用户将无法再看到"标识设备"屏幕和注册流程中的"确认你的设备"屏幕。 
- 此更改推出后，如果你尚未部署公司门户中使用后上面提到的应用程序配置文件和最终用户下载公司门户应用从应用存储，他们可以登录，但它们是否会收到一条错误消息。 它们将无法使用应用的条件性访问。 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
如果你打算使用修改的工作流，你需要更新你的最终用户指南，以指示：

- 最终用户将无法再看到注册流程中所述的两个屏幕。 
- 他们需要登录到公司门户时就会自动部署并不从应用商店下载它。 

您可以选择立即创建应用配置策略，如果需要以为此更改做好准备。 当推出此新的工作流时，你将看到在控制台中的已更新的注册配置文件。 我们还将通知你通过消息中心此推出。 在此之后，你将需要采取的措施，以便最终用户可以通过 DEP 注册通过使用设置助理进行身份验证，并且你可以为条件性访问使用公司门户。

请参阅我们的支持的博客文章有关此更改的更多详细信息的其他信息链接。

#### <a name="additional-information"></a>其他信息 
[https://aka.ms/enrollment_setup_assistant](https://aka.ms/enrollment_setup_assistant)

### <a name="plan-for-change-user-experience-update-to-intune-company-portal-app-for-ios"></a>更改计划：适用于 iOS 的 Intune 公司门户应用的用户体验更新
我们很高兴与大家分享，Intune 将很快发布 iOS 公司门户应用的主要用户体验更新。 此次更新将提供对主页的视觉对象重新设计，其中包含高级筛选器和对应用和书籍更快速的访问。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
在维护当前 iOS 公司门户功能的同时，该用户体验更新还提供以下内容：
- 具有本机 iOS 外观和体验的主页 
- 内容列表和搜索的筛选功能，包括按内容类型（应用或电子书）和可用性（需要设备管理或无需注册即可使用）进行筛选的功能
- 电子书搜索功能
- 应用和电子书的搜索历史记录

如果你参与了 AppleTestFlight 计划，Inune 的更新的 iOS 公司门户应用的预发行版本可用时，你将收到通知。 如果你未参与 Apple TestFlight 计划，现在注册还为时不晚。 注册后，即可在更新的公司门户应用向最终用户推出前使用它。 此外可以提供直接与 Intune 团队的反馈。  

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我能够针对此更改做什么准备？
无需执行任何操作；这些更改将在即将发布的 iOS CP 应用版本中发布。 

#### <a name="additional-information"></a>其他信息
[https://aka.ms/cp_update_iOS](https://aka.ms/cp_update_iOS)

### <a name="check-your-delay-visibility-of-software-updates-setting-in-intune"></a>检查你在 Intune 中的"延迟的软件更新的可见性"设置 

我们在我们已在控制台中四处移动几个设置的 MC171466 中共享。 使用 Intune 的年 3 月更新，我们完全将从 iOS 更新策略边栏选项卡中删除"延迟可见性的软件更新"设置。 这不会更改计划的软件更新将应用的方式，但它可能会影响最终用户多长时间延迟更新的可见性。 您可能需要采取措施年 3 月结束之前，如果您使用此设置。 

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
年 2 月 Intune 服务更新后，您会发现设置出现在控制台中，在 iOS 中的设备限制配置文件中更新的软件更新边栏选项卡中的策略。 当您看到此更改反映在控制台中时，下面是你可能需要执行操作。

- 有关适用于 iOS 的现有更新策略： 如果您有自定义配置此设置为默认值以外的任何 30 天和希望你继续应用年 3 月结束后，延迟可见性设置的现有配置，必须创建一个新iOS 设备限制配置文件。 在这里，延迟可见性设置将需要具有相同的值如下所示将现有 iOS 更新策略，并以相同的组为目标。 年 3 月服务更新后，你将不再能够编辑现有 iOS 更新策略中此设置的值，因为它将不再显示在此边栏选项卡。 将改为新的配置文件中配置此设置。
  如果可以延迟的天数内的值在自定义配置的设置的值，延迟可见性设置将不起作用，这两个位置中不匹配的可见性和最终用户将会看到更新其设备上立即可用。 由于软件更新策略边栏选项卡中的其他设置通过在控制台中的此设置总是采用优先级可能对于大多数客户的影响最小。
- 适用于 iOS 的新更新策略： 如果尝试在 Intune 年 2 月服务更新后的软件更新边栏选项卡中创建新的策略，你将看到此设置，处于灰显状态。你将看到在控制台中将你重定向到设备的配置边栏选项卡如果你想要延迟更新的可见性说明。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我能够针对此更改做什么准备？
不需要采取措施，如果不使用此设置或不想要让最终用户延迟软件更新的可见性。

如果你想要延迟更新的可见性，开始在设备限制下的设备配置边栏选项卡中的新配置文件中配置该设置 > 常规。 如果你有此设置自定义配置在现有 iOS 更新策略、 创建新的等效设备限制配置文件具有相同的值为"days"延迟到用户的更新的可见性、 年 2 月更新，并在年 3 月之前更新后推出。 

您可能想要更新您的 IT 专业人员指南，并通知支持人员联系。

请参阅我们的支持博客文章在其他信息，有关如何配置此设置的详细信息。

#### <a name="additional-information"></a>其他信息 
[https://aka.ms/Delay_visibility_setting_iOS](https://aka.ms/Delay_visibility_setting_iOS)

### <a name="plan-for-change-upcoming-fix-for-windows-10-email-profiles-in-intune---3904031--"></a>更改计划： 在 Intune 中的 Windows 10 电子邮件配置文件即将修复 <!--3904031-->
我们正在更新 Intune 写入电子邮件配置文件适用于 Windows 10 中年 4 月到 Intune 服务以修复 bug 还可以确保电子邮件配置文件继续工作在将来版本的 Windows 10 更新的方式。 没有需要执行此修补程序部署后操作。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
此更改会影响您，如果你使用与 Windows 10 电子邮件配置文件
- Windows 10 台式机上的本机邮件客户端或
- 在 Windows 10 移动版 Outlook 电子邮件客户端

这会影响这两个 Intune 独立版和混合移动设备管理 (MDM) 客户。

年 4 月更新推出后，你将需要重新创建这些配置文件在 Intune 控制台中 （在 Configuration Manager 管理员控制台中如果你使用混合 MDM）。

如果不采取措施，下面是你将看到的针对年 4 月更新之前创建的配置文件：

- 现有的电子邮件配置文件将显示在 Intune 控制台或 Configuration Manager 管理控制台中的错误状态，但最终用户将仍然可以访问电子邮件。 但是，后续的 Windows 更新推出后，这些配置文件不起作用。 这些配置文件的目标设备上的最终用户将无法访问的电子邮件。
- 对编辑这些配置文件后年 4 月将不会反映在目标设备。
- 选择性擦除将不适用于删除这些配置文件，即使在 4 月推出修补程序。

如果你采取措施，并重新创建电子邮件配置文件，最终用户将需要经过类似的步骤，第一次部署电子邮件配置文件时。 将阻止其电子邮件同步直到他们接受应用新配置文件的更新。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
需要解决方法使用年 4 月更新推出后才执行操作。 我们将与你联系通过消息中心时此更改投入，以便你可以开始重新创建在 Intune 中的配置文件。

如果在 Intune 中使用 Windows 10 电子邮件配置文件，将需要执行以下步骤：

1. 捕获现有 Win 10 配置文件设置
2. 取消分配和/或删除现有的配置文件
3. 创建新的配置文件使用捕获的设置，并将新的配置文件分配到同一个组

您可能需要通知最终用户，并让支持人员知道此发生了更改。 请参阅有关错误详细信息和说明用于重新创建这些配置文件上的其他信息的支持博客文章。

#### <a name="additional-information"></a>其他信息
https://aka.ms/Win10EmailProfiles

