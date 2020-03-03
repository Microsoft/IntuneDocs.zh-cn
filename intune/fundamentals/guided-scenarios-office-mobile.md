---
title: 引导式方案 - 保护 Microsoft Office 移动应用
titleSuffix: Microsoft Intune
description: 在 Microsoft 365 设备管理门户中了解关于部署保护 Microsoft Office 移动应用的引导式方案。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/06/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0232855773626693d848f77e561c51d281739215
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514602"
---
# <a name="guided-scenario---secure-microsoft-office-mobile-apps"></a>引导式方案 - 保护 Microsoft Office 移动应用 

通过在设备管理门户中执行此引导式方案，你可以在 iOS/iPadOS 和 Android 相关设备上启用基本的 Intune 应用保护。

启用的应用保护将强制执行以下操作： 
- 加密工作文件。
- 需要 PIN 才能访问工作文件。
- 尝试失败五次后，要求重置 PIN。
- 阻止在 iTunes、iCloud 或 Android 备份服务中备份工作文件。  
- 要求只能将工作文件保存到 OneDrive 或 SharePoint。
- 阻止受保护的应用在已越狱或取得 root 权限的设备上加载工作文件。
- 如果设备已离线 720 分钟，则阻止访问工作文件。
- 如果设备已离线 90 天，则删除工作文件。 

## <a name="background"></a>背景

Office 移动应用以及 Microsoft Edge for Mobile 都支持双重标识。 使用双重标识，应用可以将工作文件与个人文件分开管理。 

![公司数据与个人数据的图像](./media/guided-scenarios-office-mobile/guided-scenarios-office-mobile-01.png)

[Intune 应用保护策略](~/apps/app-protection-policy.md)可帮助保护在 Intune 中注册的设备上的工作文件。 另外，应用保护策略还可用在没有注册 Intune 进行管理的员工自有设备上。 在这种情况下，即使你的公司不管理该设备，仍需要确保工作文件和资源受到保护。

你可以使用应用保护策略来防止用户将工作文件保存在不受保护的位置。 还可限制将数据移动到不受应用保护策略保护的其他应用。 应用保护策略设置包括：
- 数据重定位策略，例如“保存原始数据副本”  和“限制剪切、复制和粘贴”  。
- 访问策略设置，要求使用简单的 PIN 进行访问，阻止在已越狱或取得 root 权限的设备上运行受管理的应用。

通过确保仅支持 Intune 应用保护策略的客户端应用可以访问 Exchange Online 和其他 Office 365 服务，基于应用的条件访问和客户端应用管理增加了一个安全层。

仅允许 Microsoft Outlook 应用访问 Exchange Online 时，可阻止 iOS/iPadOS 和 Android 上的内置邮件应用。 此外，你还可以阻止未执行 Intune 应用保护策略的应用访问 SharePoint Online。

在此示例中，管理员将应用保护策略应用到 Outlook 应用，然后应用条件访问规则，将 Outlook 应用添加到可在访问企业电子邮件时使用的已批准的应用列表。

![Outlook 应用条件访问流](./media/guided-scenarios-office-mobile/guided-scenarios-office-mobile-02.png)

## <a name="prerequisites"></a>必备条件

你将需要具有以下 Intune 管理员权限：

   - 托管应用读取、创建、删除和分配权限
   - 策略集读取、创建和分配权限
   - 组织读取权限

## <a name="step-1---introduction"></a>步骤 1 - 简介

按照“Intune 应用保护”引导式方案进行操作，可以防止数据在组织外部共享或泄漏  。 

已分配的 iOS/iPadOS 和 Android 用户每次打开 Office 应用时都必须输入 PIN。 5 次输入 PIN 尝试失败后，用户必须重置其 PIN。 如果已要求使用设备 PIN，则用户不会受到影响。

### <a name="what-you-will-need-to-continue"></a>需要继续执行的操作

我们会询问你用户需要哪些应用，以及访问这些应用需要哪些权限。 请确保你可以使用以下信息：
- 已批准公司使用的 Office 应用列表。
- 在非托管设备上启动已批准应用的任何 PIN 要求。

## <a name="step-2---basics"></a>步骤 2 - 基础知识

在此步骤中，必须为新的应用保护策略输入“前缀”和“说明”   。 添加“前缀”时，将更新与引导式方案创建的资源相关的详细信息  。 以后如果需要更改分配和配置，可以通过这些详细信息轻松找到策略。 

> [!TIP]
> 请考虑记下将要创建的资源，以便以后可以参考这些资源。

## <a name="step-3---apps"></a>步骤 3 - 应用

为了帮助你入门，此引导式方案预先选择以下要在 iOS/iPadOS 和 Android 设备上保护的移动应用：
- Microsoft Excel 
- Microsoft Word 
- Microsoft Teams 
- Microsoft Edge 
- Microsoft PowerPoint 
- Microsoft Outlook 
- Microsoft OneDrive 

此引导式方案还将配置这些应用，使其在 Microsoft Edge 中打开网页链接，以确保在受保护的浏览器中打开工作网站。

修改要保护的策略托管应用的列表。 添加或删除此列表中的应用。 

选择应用后，单击“下一步”  。

## <a name="step-4---configuration"></a>步骤 4 - 配置

在此步骤中，必须配置在这些应用中访问和共享公司文件和电子邮件的相关要求。 默认情况下，用户可以将数据保存到组织的 OneDrive 和 SharePoint 帐户。

| 设置 | 说明 | 默认值 |
|---------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| PIN 类型 | 数值 PIN 由所有数字组成。 密码由字母数字字符和特殊字符组成。  在 iOS/iPadOS 上，若要配置“密码”类型，应用必须安装 Intune SDK 版本 7.1.12 或更高版本。 数值类型没有任何 Intune SDK 版本限制。 | 数字 |
| 选择最小 PIN 长度 | 指定 PIN 序列必须包含的最小位数。 | 6 |
| 在（非活动状态的分钟数）后重新检查访问要求 | 如果策略托管的应用处于非活动状态的时间超过指定的非活动分钟数，将在启动应用后提示重新检查访问要求 （即 PIN、条件启动设置）。 | 30 |
| 打印组织数据 | 如果阻止，则应用无法打印受保护的数据。 | 阻止 |
| 在非托管的浏览器中打开策略托管的应用链接 | 如果阻止，则必须通过托管浏览器打开策略托管的应用链接。 | 阻止 |
| 将数据复制到非托管应用 | 如果阻止，托管数据将保留在托管应用中。 | Allow |

## <a name="step-5---assignments"></a>步骤 5 - 分配

在此步骤中，你可以选择要包含的用户组，以确保他们能够访问你的公司数据。 应用保护是分配到用户的，而不是分配到设备的，因此无论使用哪种设备及其注册状态如何，公司数据都是安全的。

未分配到应用保护策略和条件访问设置的用户，可以在其移动设备上将其公司配置文件中的数据保存到个人应用和非托管本地存储。 他们还可以通过个人应用连接到企业数据服务（例如 Microsoft Exchange）。

## <a name="step-6---review--create"></a>步骤 6 - 查看 + 创建

通过最后一个步骤可以查看配置的设置摘要。 查看你的选择后，请单击“创建”以完成引导式方案  。 引导式方案完成后，系统将显示一个资源表。 可以稍后编辑这些资源，但退出“摘要”视图后，该表将不会保存。

> [!IMPORTANT]
> 引导式方案完成后，系统将显示摘要。 可以稍后修改摘要中列出的资源，但是将不会保存显示这些资源的表。
## <a name="next-steps"></a>后续步骤

- 通过为用户分配基于应用的条件访问策略，以防止云服务将工作文件发送到不受保护的应用，从而增强工作文件的安全性。 有关详细信息，请参阅[使用 Intune 设置基于应用的条件访问策略](~/protect/app-based-conditional-access-intune-create.md)。

