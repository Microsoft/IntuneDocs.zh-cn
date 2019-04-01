---
ms.openlocfilehash: dc86f2c22410236368753acd4dd3b66698037241
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57736853"
---

这些注意事项提供重要信息可以帮助您准备将来的 Intune 更改和功能。 

### <a name="change-in-enrollment-workflow-with-intune-company-portal-on-corporate-ios-devices-authenticating-with-setup-assistant----1927359---"></a>使用设置助理进行身份验证的企业的 iOS 设备上通过 Intune 公司门户注册工作流中更改 <!-- 1927359 -->
没有用于注册 iOS 设备，通过 Apple 的企业设备注册方法-Apple Configurator、 Apple 业务经理、 Apple School Manager 或 Apple 设备注册计划 (DEP)，其中一个工作流中即将发生的更改时使用安装程序身份验证的助手。 此更改仅适用于具有用户关联注册的设备。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
此更改于~~三月~~四月推出时，将更新 Azure 门户中的 Intune 注册配置文件，以便你可以指定设备的身份验证方式以及是否收到公司门户应用。 将改进的工作流以通过上面列出的方法来注册 iOS 设备。 注意：

- 当注册新设备，以及使用设置助理进行身份验证，您可以选择要自动部署的公司门户应用。 最终用户将无法再看到"标识设备"屏幕和注册流程中的"确认你的设备"屏幕。  
- 注册的设备上已通过设置助理通过 Apple 的企业设备注册方法之一，则必须采取措施，如果你想要启用条件性访问。 您必须使用特定 xml 推送到这些设备在公司门户中配置的应用配置策略。 若要执行此操作的方向是中的其他信息链接上的博客文章。 如果您选择将在公司门户推送以这种方式，最终用户将无法再看到"标识设备"屏幕和注册流程中的"确认你的设备"屏幕。 
- 此更改推出后，如果你尚未部署公司门户中使用后上面提到的应用程序配置文件和最终用户下载公司门户应用从应用存储，他们将可以登录，但它们是否会收到一条错误消息。 它们将无法使用应用的条件性访问。 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要针对此更改做什么准备？
如果你打算使用修改的工作流，你需要更新你的最终用户指南，以指示：

- 最终用户将无法再看到注册流程中所述的两个屏幕。 
- 他们需要登录到公司门户时就会自动部署并不从应用商店下载它。 

您可以选择立即创建应用配置策略，如果需要以为此更改做好准备。 当推出此新的工作流时，你将看到在控制台中的已更新的注册配置文件。 我们还将通知你通过消息中心此推出。 在此之后，你将需要采取的措施，以便最终用户可以通过 DEP 注册通过使用设置助理进行身份验证，并且你可以为条件性访问使用公司门户。

请参阅我们的支持的博客文章有关此更改的更多详细信息的其他信息链接。

#### <a name="additional-information"></a>其他信息 
[https://aka.ms/enrollment_setup_assistant](https://aka.ms/enrollment_setup_assistant)


### <a name="company-portal-changes-for-ios-122-enrollment-in-intune"></a>在 Intune 中的 iOS 12.2 注册的公司门户更改
我们在 MC172534 中分享了 Apple 已宣布与注册到移动设备管理 (MDM) 服务的 iOS 设备相关的一些更改。 将可能在 iOS 中 2019 年 3 月的版本，以及所有将来的 iOS 版本中看到更改。 我们将一些更新以反映 Apple 的更改在公司门户中。 
 
#### <a name="how-does-this-affect-me"></a>这对我有何影响？
如果您的最终用户将设备升级到 iOS 12.2 及更高版本，知道没有修改的工作流，并且它们必须采取其他步骤完成注册到 Intune。 年 3 月更新后到 Intune，下面是它们将如何-  

- 开始注册过程中若要下载管理配置文件的公司门户应用
- 转到设置 > 常规 > 配置文件并查找红色的锁屏提醒通知
- 选择正确的配置文件，然后通过单击进行安装
- 返回到公司门户中完成注册

单击注册流程的详细信息的其他信息。

不应影响除非它们取消注册并需要重新注册，设备已注册并升级到 iOS 12.2 及更高版本。 运行 iOS 12.1 或更早版本的设备上的注册体验将不会随着 Apple 新版本的发布而更改。 通过一项或 Apple 的企业注册方法 （设备注册计划、 Apple School Manager 或 Apple 业务经理） 注册的设备不会受到影响。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我能够针对此更改做什么准备？
应计划升级文档和最终用户指南。 你可能还想让帮助台了解这些更改。 我们将向您通过我们新增功能页时此更改会实时通知。 

如果你想要充分利用我们将引入的公司门户更改，要求最终用户后三月版更新到 Intune 服务时，将其设备更新到新的 iOS 版本公司门户应用程序版本 3.9.0。 将释放。

单击带预览的公司门户更改的屏幕截图的支持博客文章的其他信息。

其他信息 [https://aka.ms/CP_changes_iOS12](https://aka.ms/CP_changes_iOS12)

### <a name="plan-for-change-workflow-changes-for-ios-12-enrollment-in-intune"></a>更改计划： iOS 12 注册在 Intune 中的工作流更改
Apple 已宣布与注册移动设备管理 (MDM) 服务的 iOS 设备相关的一些更改。 此更改可能会在 iOS 的 2019 年春季版本以及未来所有 iOS 版本中出现。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
如果最终用户在春季将其设备升级为新版本 iOS 12，请牢记工作流已修改，他们需要采取额外步骤来完成到 Intune 的注册。 Apple 引入了这些更改，最终用户将有到：

- 开始注册过程中若要下载管理配置文件的公司门户应用
- 转到设置 > 常规 > 配置文件
- 选择正确的配置文件，然后通过单击进行安装
- 返回到公司门户中完成注册 

除非设备未注册且需要新注册，否则已经注册并升级到 iOS 新版本的设备不会受到影响。

运行 iOS 12.1 或更早版本的设备上的注册体验将不会随着 Apple 新版本的发布而更改。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我能够针对此更改做什么准备？
应计划升级文档和最终用户指南。 你可能还想让帮助台了解这些更改。 此更改生效时，我们将通过消息中心和“新增功能”进行通知。

#### <a name="additional-information"></a>其他信息
[支持与屏幕截图和视频的预期的注册流程的博客文章](https://aka.ms/iOS_enrollment_changes)。

### <a name="plan-for-change-user-experience-update-to-intune-company-portal-app-for-ios"></a>更改计划：适用于 iOS 的 Intune 公司门户应用的用户体验更新
我们很高兴与大家分享，Intune 将很快发布 iOS 公司门户应用的主要用户体验更新。 此次更新将提供对主页的视觉对象重新设计，其中包含高级筛选器和对应用和书籍更快速的访问。

#### <a name="how-does-this-affect-me"></a>这对我有何影响？
在维护当前 iOS 公司门户功能的同时，该用户体验更新还提供以下内容：
- 具有本机 iOS 外观和体验的主页 
- 内容列表和搜索的筛选功能，包括按内容类型（应用或电子书）和可用性（需要设备管理或无需注册即可使用）进行筛选的功能
- 电子书搜索功能
- 应用和电子书的搜索历史记录

如果你参与了 AppleTestFlight 计划，Inune 的更新的 iOS 公司门户应用的预发行版本可用时，你将收到通知。 如果你未参与 Apple TestFlight 计划，现在注册还为时不晚。 注册后，即可在更新的公司门户应用向最终用户推出前使用它。 您可以还将提供直接与 Intune 团队的反馈。  

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我能够针对此更改做什么准备？
无需执行任何操作；这些更改将在即将发布的 iOS CP 应用版本中发布。 

#### <a name="additional-information"></a>其他信息
[https://aka.ms/cp_update_iOS](https://aka.ms/cp_update_iOS)


### <a name="reminder-removal-of-existing-exchange-online-to-intune-connectors----3105122---"></a>提醒： 删除的现有 Exchange Online 与 Intune 连接器 <!-- 3105122 -->
在 MC165575，我们共享，我们将删除 Exchange Online 到 Intune 服务到服务的连接器功能在将来的更新。 使用 Intune 服务的年 2 月更新，我们将禁用按钮以设置新的连接器。 我们计划在 2019 年 3 月中删除所有现有 Exchange Online 与 Intune 连接器。
 
#### <a name="how-does-this-affect-me"></a>这对我有何影响？
你将收到此消息，因为我们的记录表明，你可能正在你的环境中使用“服务间”连接器功能。 “服务间”连接器支持对适用于 Exchange Online 的 Exchange Active Sync Only 设备进行 Intune 管理，但不支持本地基础结构。 此连接器因其在控制台中的显示方式，似乎是条件访问 (CA) 必需的连接器，但在实际情况下，它不是 CA 必需的。 你可能已使用此连接器应用条件性访问之前，了解 Exchange Online 的使用情况。 Microsoft 365 管理中心内已提供此信息。 在这里，您会发现在 7 和 180 天内用于 Exchange Online 包括的应用类型提供了使用情况报告。 有关详细信息请参阅[Office 365 管理中心-电子邮件应用使用情况报表](https://docs.microsoft.com/office365/admin/activity-reports/email-apps-usage?view=o365-worldwide)。  
 
如果在你的环境中使用此连接器，二月禁用连接器之后将无法在 Intune 中监视或擦除 Exchange Active Sync Only 设备。 在此更改期间预期对最终用户没有任何影响。
 
#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我能够针对此更改做什么准备？
如果要设置“服务间”连接器和 Exchange Active Sync Only 设备，请切换到管理设备的其他方法。 你有下列选择：

- 在移动设备管理 (MDM) 中注册设备 
- 使用 Intune 应用保护策略管理设备 
- 使用[此处](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online)文档中所述的 Exchange 控件 

#### <a name="additional-information"></a>其他信息  
https://docs.microsoft.com/intune/exchange-service-connector-configure




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
