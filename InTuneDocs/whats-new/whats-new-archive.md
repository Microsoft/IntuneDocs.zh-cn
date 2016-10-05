---
title: "新增功能存档 | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ecf43b38e9593375981770583220d4ce2dfd709f
ms.openlocfilehash: 8b0f393da727b433a926e780d6de42cf7b4c6034


---
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



## 2015 年 9 月
### 移动设备和应用管理更新
**所有 Intune iOS 管理功能现在均支持 iOS 9**有关 iOS 9 管理功能的详细信息，请参阅[此博客文章](http://blogs.technet.com/b/microsoftintune/archive/2015/09/09/day-zero-support-for-ios-9-with-intune.aspx)。

**适用于 iOS 的新移动应用配置策略**使用新的移动应用配置策略来自动提供 iOS 应用运行时可能需要的设置。 例如，你可以提供网络端口或用户名。 有关详细信息，请参阅[使用 Microsoft Intune 中的移动应用配置策略配置应用](https://technet.microsoft.com/library/mt481447.aspx)。

**为 iOS 9 用户简化应用管理**
在此版本中，你可以为 iOS 9 用户将已部署的应用交由 Intune 管理。 对于 iOS 的早期版本，在部署应用时，即使已在一个设备上安装了非托管版本的该应用，你仍须让用户手动卸载该应用后，Intune 才能安装托管应用。

 但从这个版本的 Intune 开始，你现在可以提示 iOS 9 设备的用户允许 Intune 接管该应用的管理并应用任何相关的移动应用程序管理策略。

 **Windows 10 管理** 使用新的 [Windows 10 常规配置策略](https://technet.microsoft.com/library/mt404697.aspx)为运行 Windows 10 和 Windows 10 移动版的已注册设备配置密码、设备、浏览器和其他设置。

 **创建应用并将其部署到已注册的 Windows 10 设备**新的软件安装程序类型，通过 MDM 的 Windows Installer (&#42;.msi)，允许你创建 Windows Installer 应用，并将其部署到运行 Windows 10 的已注册设备中。 有关详细信息，请参阅[开始在 Microsoft Intune 中部署应用](https://technet.microsoft.com/library/dn646955.aspx)。

### Microsoft 公司门户应用的更改和更新
此版本已针对公司门户应用进行了如下更改：

**iOS**
* Microsoft 会自动收集有关性能和公司门户使用情况的匿名数据以改进 Microsoft 产品和服务。 最终用户可以使用设备上的“数据使用情况”设置关闭数据收集，但管理员无法控制数据收集，并且无法更改最终用户对此设置的选择。
* iPhone 6 和 iPhone 6 Plus 上支持全屏分辨率
* 修复 bug 以提高安全性

### Intune 文档新增内容 — 2015 年 9 月
**新主题**

|Name|详细信息|
|----|--------|
|[Microsoft Intune 中的 Windows 10 配置策略设置](https://technet.microsoft.com/library/mt404697.aspx)|这是一个新的配置策略，允许你管理运行 Windows 10 和 Windows 10 移动版的设备上的设置和功能。
| [使用 Microsoft Intune 中的移动应用配置策略配置应用](https://technet.microsoft.com/library/mt481447.aspx)|这是一种新的策略类型，允许你自动提供用户运行 iOS 应用时可能需要的设置。 |

**更新的主题**

|Name|详细信息|
|----|-------|
|[通过 Microsoft Intune 使用策略来管理计算机和移动设备](https://technet.microsoft.com/library/dn743712.aspx)|已更新为包含帮助你了解和创建策略的最新信息。|

## 2015 年 8 月
### 移动设备和应用管理更新
* Intune 注册和公司访问的“条款和条件”[现在使用策略进行管理](https://technet.microsoft.com/library/mt405893.aspx)。 可以指定不同的条款和条件来满足特定用户组的要求。 例如，你可以将条款和条件以不同语言部署到按地理位置定义的用户组。 还可以 [编辑你的条款和条件](https://technet.microsoft.com/library/mt405893.aspx#BKMK_TCVers) 并指定是否递增版本号，这要求用户在使用公司门户前首先需同意新的条款和条件。
* “已重命名多个 Intune 策略” 以增强跨产品一致性和方便轻松查找。 有关所有可用的 Intune 策略列表，请参阅[通过 Microsoft Intune 使用策略来管理计算机和移动设备](https://technet.microsoft.com/library/dn743712.aspx)。
* “PKCS #12 (.PFX) 证书配置文件”可以用于 Android 4.0 或更高版本，以及 Windows 10（桌面版和移动版）和更高版本。 使用 .PFX 不需要 NDES 服务器。 在[通过 Microsoft Intune 使用证书配置文件启用对公司资源的访问](http://technet.microsoft.com/library/dn818904.aspx)中了解如何使用 .PFX 证书配置文件
* 如[通过 Microsoft Intune 使用 VPN 配置文件帮助用户连接到其工作](https://technet.microsoft.com/library/dn818905.aspx)中所述，**Windows 10 桌面版和移动版的企业边界设置**启用了粒度 VPN 设置
* **适用于 Android 的 OneDrive 应用现支持多身份**。 在 [可以管理的 Microsoft 应用程序列表](https://technet.microsoft.com/library/dn708489.aspx)中描述了对移动应用管理策略的此项和其他更新。
* **绕过 iOS 激活锁定**。 如果公司拥有的 iOS 设备受激活锁定保护，则必须先输入用户的 Apple ID 和密码，才能擦除或重新激活该设备。 当用户在不关闭激活锁定的情况下离开公司，然后返回使用公司拥有的设备时，则将面临一项巨大的挑战。 若要帮助解决此问题，可以使用 [Intune 绕过激活锁定](https://technet.microsoft.com/library/mt414176.aspx)

### PC 的条件性访问
现在，你可以配置 PC 的条件访问策略。 这将允许 Office 桌面应用访问 Exchange Online 和 SharePoint Online 服务。
若要启用 PC 的条件性访问策略，此 PC 必须已加入域或必须合规。
* 有关启用电脑的条件性访问的要求的完整列表，请参阅[使用 Microsoft Intune 管理对电子邮件和 SharePoint 的访问](http://technet.microsoft.com/library/dn818907).aspx) 中的**入门**部分。
* 请参阅[使用 Microsoft Intune 管理电子邮件访问](https://technet.microsoft.com/library/dn705841.aspx)，了解可设置为启用电子邮件访问的条件性访问的选项。
* 请参阅[使用 Microsoft Intune 管理 SharePoint Online 访问](https://technet.microsoft.com/library/dn705844.aspx)，了解可设置为启用 SharePoint Online 的条件性访问的选项。

### Microsoft 公司门户应用的更改和更新
此版本已针对公司门户应用进行了如下更改：

**Android**

如果用户尚未注册其设备以进行管理，则该用户现将在登录后看到设备注册说明。

### Intune 文档新增内容 - 2015 年 8 月
**新主题**

|标题|详细信息|
|-----|-------|
|[通过 Microsoft Intune 的绕过激活锁定帮助保护 iOS 设备](https://technet.microsoft.com/library/mt414176.aspx)|了解有关在用户离开公司并返还已锁定设备时如何使用 Intune 绕过 iOS 激活锁定的信息。|

**更新的主题**

|标题|详细信息|
|-----|-------|
|[可配合 Microsoft Intune 移动应用程序管理策略使用的 Microsoft 应用](https://technet.microsoft.com/library/dn708489.aspx)|更新了有关可使用移动应用程序管理策略管理的应用的最新信息。
|[通过 Microsoft Intune 使用策略来管理计算机和移动设备](http://technet.microsoft.com/library/dn743712.aspx)|更新了 Intune 新增的最新策略。|
<!---
## July 2015
July updates for Intune are limited to behind-the-scenes enhancements that allow us to continue providing you with a high-quality service experience. New features are not included in this service update.

### Intune Onboarding benefit
Microsoft offers the Intune Onboarding benefit for eligible plans. The Onboarding benefit lets you work remotely with Microsoft specialists to get your Intune environment ready for use. For more information, see [Microsoft Intune Onboarding benefit description](https://technet.microsoft.com/library/mt228266.aspx)
### Changes and updates to Microsoft Company Portal apps
The following changes have been made to the company portal apps in this release.

**Android**

Microsoft automatically collects anonymous data about the performance and use of the company portal to improve Microsoft products and services. End users can turn off data collection by using the Usage Data setting on their device, but administrators have no control over the data collection and cannot change the end user’s selection for this setting.--->



<!--HONumber=Sep16_HO5-->


