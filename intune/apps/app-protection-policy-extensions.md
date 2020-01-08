---
title: 用于扩展的应用保护策略
titleSuffix: Microsoft Intune
description: 本主题介绍了用于扩展的应用保护策略 (APP)。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/06/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1ff4fcd7d1b2115c4fbe0bc00759ef3d60482904
ms.sourcegitcommit: a66b5916eaab9cb537e483064efc584a6a63a390
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75692106"
---
# <a name="protecting-application-extensions"></a>保护应用扩展

本文介绍了 Microsoft Intune 中用于扩展的应用保护策略。

## <a name="add-ins-for-outlook-app"></a>Outlook 应用的加载项

使用 Outlook 加载项，可以将热门应用与电子邮件客户端集成。 Outlook 加载项适用于 Web、Windows、Mac 以及 Android 和 iOS 版 Outlook。 Intune APP SDK 和 Intune 应用保护策略不支持管理 Outlook 加载项，但可使用其他方法来限制使用加载项。 由于加载项是通过 Microsoft Exchange 管理的，所以用户能够在 Outlook 和非托管加载项应用程序之间共享数据和邮件，除非用户的 Exchange 关闭了加载项。

如果要阻止最终用户访问和安装 Outlook 加载项（这会影响所有 Outlook 客户端），请确保在 Exchange 管理中心中对角色进行以下更改：

- 若要防止用户安装 Office 应用商店加载项，请从中删除“我的市场”角色。
- 若要防止用户侧向加载加载项，请从中删除“我的自定义应用”角色。
- 若要防止用户安装所有加载项，请从中删除“我的自定义应用”和“我的市场”角色。

这些说明适用于跨 Web、Windows、Mac 和移动版 Outlook 的 Office 365、Exchange 2016、Exchange 2013。

- 详细了解 [Outlook 的加载项](https://technet.microsoft.com/library/jj943753(v=exchg.150).aspx)。
- 详细了解[如何指定可安装和管理 Outlook 应用的加载项的管理员和用户](https://technet.microsoft.com/library/jj943754(v=exchg.150).aspx)。

## <a name="linkedin-account-connections-for-microsoft-apps"></a>Microsoft 应用的 LinkedIn 帐户连接

LinkedIn 帐户连接允许用户在某些 Microsoft 应用中查看公开的 LinkedIn 档案信息。 默认情况下，用户可选择连接其 LinkedIn 和 Microsoft 工作或学校帐户，以查看其他 LinkedIn 档案信息。 

> [!NOTE]
> 美国政府客户以及在澳大利亚、加拿大、中国、法国、德国、印度、韩国、英国、日本和南非托管 Exchange Online 邮箱的组织目前无法使用 LinkedIn 集成功能。

Intune SDK 和 Intune 应用保护策略不包括对管理领英帐户连接的支持，但可使用其他方法来对其进行管理。 可为整个组织禁用 LinkedIn 帐户连接，也可为组织中的所选用户组启用 LinkedIn 帐户连接。 这些设置会影响所有平台（Web、移动和桌面）上 Office 365 应用之间的 LinkedIn 连接。 你可以：

- 在 Azure 门户中启用或禁用租户的 LinkedIn 帐户连接。 
- 使用组策略为组织的 Office 2016 应用启用或禁用 LinkedIn 帐户连接。

如果为租户启用了 LinkedIn 集成，则当组织中的用户连接其 LinkedIn 和 Microsoft 工作或学校帐户时，他们有两种选项： 

- 他们可授权在两个帐户之间共享数据。 这意味着，他们允许其 LinkedIn 帐户与其 Microsoft 工作或学校帐户彼此共享数据。 与 LinkedIn 共享的数据退出联机服务。 
- 他们仅允许从 LinkedIn 帐户向 Microsoft 工作和学校帐户共享数据

如果用户同意在帐户之间共享数据，与 Office 加载项一样，LinkedIn 集成使用现有的 Microsoft Graph API。 LinkedIn 集成仅使用 Office 加载项可用的 API 子集，并支持各种排除项。


|Microsoft Graph 权限  |说明  |
|---------|---------|
|[人员](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#people-permissions)的读取权限     |允许该应用读取与已登录用户相关的评分列表。 该列表可包括本地联系人、社交网络或组织目录中的联系人以及最近通信（如电子邮件和 Skype）中的联系人。         |
|[日历](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#calendars-permissions)的读取权限     |允许该应用读取用户日历中的事件。 包括已登录用户日历中的会议、其时间、地点和与会者。         |
|[用户配置文件](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#user-permissions)的读取权限     |允许用户登录到应用，并允许应用读取已登录用户的个人资料。 它还允许应用读取已登录用户的基本公司信息。         |
|订阅     |此作用域不可用且尚未使用。 它包括用户组织向 Microsoft 应用和服务（如 Office 365）提供的订阅。         |
|见解     |此作用域不可用且尚未使用。 它包括基于 Microsoft 服务的使用与已登录用户帐户相关的权益。         |

### <a name="learn-more"></a>了解详细信息

- 了解 [Microsoft 应用中的 LinkedIn 信息和功能](https://go.microsoft.com/fwlink/?linkid=850740)。
- 在 [Office 365 产品指南页](https://products.office.com/en-US/business/office-365-roadmap?filters=%26freeformsearch=linkedin#abc)了解 LinkedIn 帐户连接版本。 
- 了解[配置 LinkedIn 帐户连接](https://docs.microsoft.com/azure/active-directory/linkedin-integration)。
- 有关用户的 LinkedIn 和 Microsoft 工作或学校帐户之间共享的数据的详细信息，请参阅[工作或学校的 Microsoft 应用程序中的 LinkedIn](https://www.linkedin.com/help/linkedin/answer/84077)。

