---
title: "早期版本 | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 68c7a23dc8769330c14f74e6aebb07eeb188a991
ms.openlocfilehash: 4bc9a2799bcce035c6847b7b2884ee24160426da


---


# <a name="the-early-edition-for-microsoft-intune---february-2017"></a>Microsoft Intune 的早期版本 - 2017 年 2 月

**早期版本**提供了一份即将发布的 Microsoft Intune 版本中将出现的功能的列表。 此信息在非常有限的情况下依据保密协议 (NDA) 提供，并不断变化。 此处列出的某些功能有无法按期发布的风险并可能推迟到以后的版本。 正在以试验模式（外部测试）测试其他功能，以确保它们可立即供客户使用。 如果有任何问题或顾虑，请联系 Intune/PM 好友。

本页将定期更新。 返回查看其他更新。

> [!Note]
> 下面的更改依据 Intune 开发。 所有这些功能最终将支持混合客户部署（带 Intune 的 Configuration Manager）。 有关新的混合功能的详细信息，请查看[混合新增功能页](https://docs.microsoft.com/en-us/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。

## <a name="new-capabilities"></a>新功能

### <a name="modernizing-the-company-portal-website---753980--"></a>公司门户网站现代化<!--753980-->
公司门户网站将支持面向不具有托管设备的用户的应用。 此网站将使用新的撞色配色方案、动态图和“汉堡菜单”（![汉堡菜单的小图，该图片现已添加到公司门户网站左上角](./media/CP_hamburger_menu.png)，它包括了支持人员详细联系信息和现有托管设备的信息），这与 Microsoft 其他产品和服务保持一致。 将重新排列登录页，强调可供用户使用的应用，登录页上具有针对特色应用和最近更新应用的传送。 可在 [UI 更新页](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui)上查看提供的最初和最后的图像。

### <a name="new-guided-experience-for-windows-10-company-portal---713927--"></a>Windows 10 公司门户新的引导式体验<!--713927-->
从 3 月开始，适用于 Windows 10 的公司门户将为尚未被标识或注册的设备提供引导式的 Intune 演练体验。 新体验根据用户的 Windows 10 版本提供分步说明，引导用户执行 AAD 注册（用于条件访问功能的标识）和 MDM 注册（用于设备管理功能）。 引导式体验将可从公司门户主页访问，并且是可选的；如果用户未完成注册，仍然可以继续使用该应用，但有些功能可能会受到限制。

###

## <a name="notices"></a>通知

### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>iOS 设备的组迁移将不需要对组或策略进行任何更新<!--898837-->
对于所有由公司设备注册配置文件预分配的 Intune 设备组，在迁移到 Azure Active Directory 设备组期间，都将根据公司设备注册配置文件的名称在 AAD 中创建相应的动态设备组。 这样可以确保设备在注册时自动进行分组并收到与原始 Intune 组相同的策略和应用。

租户进入分组和设定目标的迁移阶段时，Intune 将自动创建一个动态 AAD 组，该组与公司设备注册配置文件面向的 Intune 组相对应。 Intune 管理员删除目标 Intune 组时，相应的动态 AAD 组不会被删除。 组成员和动态查询将被清除，但该组本身将继续保留，直到 IT 管理员通过 AAD 门户将其删除。

同样，如果 IT 管理员更改了公司设备注册配置文件面向的 Intune 组，Intune 将创建新的动态组来反映新的配置文件分配，但不会删除为旧分配创建的动态组。

### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Windows 设备的新 MDM 服务器地址<!--893007-->
Windows 和 Windows Phone 用户如果输入 __manage.microsoft.com__ 作为 MDM 服务器地址（出现提示时），尝试注册设备时将失败。 MDM 服务器地址已从 __manage.microsoft.com__ 更改为 __enrollment.manage.microsoft.com__。 通知用户在注册 Windows 和/或 Windows Phone 时，如果出现提示，请使用 __enrollment.manage.microsoft.com__ 作为 MDM 服务器地址。 此更新需要把在 DNS 中将 __EnterpriseEnrollment.contoso.com__ 重定向到 __manage.microsoft.com__ 的所有 CNAME 替换为在 DNS 中将 __EnterpriseEnrollment.contoso.com__ 重定向到 __EnterpriseEnrollment-s.manage.microsoft.com__ 的 CNAME。 有关此更改的详细信息，请访问[aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange)。

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Android 适用的公司门户应用的最新用户体验<!--621622-->
从&3; 月开始，Android 适用的公司门户应用将按照[材料设计指南](https://material.io/guidelines/material-design/introduction.html)来打造更具现代感的外观。 这将改善以下用户体验：

* __颜色__：可以根据自定义调色板对选项卡标头着色。
* __界面__：“应用”选项卡上已更新了“特色应用”和“所有应用”按钮。 “搜索”按钮现在是浮动的操作按钮。
* __导航__：“所有应用”以选项卡形式呈现出“特色”、“所有”和“分类”视图，便于导航。
* __服务__：“我的设备”和“联系 IT”选项卡提高了可读性。

可在 [UI 更新页](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui)上查看最初和最后的图像。

### <a name="associate-multiple-management-tools-with-the-windows-store-for-business---926135--"></a>将多个管理工具与适用于企业的 Windows 应用商店关联<!--926135-->
使用多个管理工具部署适用于企业的 Windows 应用商店时，以前只能将一个管理工具与适用于企业的 Windows 应用商店相关联。 现在可以将多个管理工具与应用商店相关联，例如 Intune 和 Configuration Manager。 有关详细信息，请参阅[使用 Microsoft Intune 管理从适用于企业的 Windows 应用商店中购买的应用](https://docs.microsoft.com/en-us/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune#associate-your-windows-store-for-business-account-with-intune)。

## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Azure 上新的 Intune 管理体验公开预览版<!--736542-->

在 2017 年初，我们会将完整管理体验迁移到 Azure 上，以便能够在可使用图形 API 进行扩展的新式服务平台上对核心 EMS 工作流进行强大且集成的管理。

新的试用租户将于本月开始在 Azure 门户中看到新管理体验的公开预览版。 在预览状态下，将以迭代方式交付现有 Intune 控制台的功能和奇偶校验。

Azure 门户中的管理体验将使用已公布的新分组和定向功能；当现有租户迁移到新的分组体验时，也会将你迁移，以预览租户上的新管理体验。 在此期间，如果想要在租户迁移之前测试或查看任何新功能，请注册新的 Intune 试用帐户或查阅[新文档](https://docs.microsoft.com/en-us/intune-azure/introduction/what-is-microsoft-intune)。

如果对租户迁移的时间表有任何疑问，请通过 [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com) 联系我们的迁移团队。

### <a name="february-2017"></a>2017 年 2 月

#### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>限制移动设备注册的功能<!--747600, 795782-->
Intune 新增了注册限制，可控制允许注册的移动设备平台。 Intune 将移动设备平台分为 iOS、macOS，Android、Windows 和 Windows Mobile。

* 限制移动设备注册不会限制电脑客户端注册。  
* 阻止个人自有设备的注册有一个附加选项，该选项仅适用于 iOS 和 Android。

Intune 将所有新设备都标记为个人所有，除非 IT 管理员将设备标记为公司所有，如[本文](https://docs.microsoft.com/en-us/intune/deploy-use/manage-corporate-owned-devices)所述。

#### <a name="view-all-actions-on-managed-devices---677150--"></a>查看托管设备上的所有操作<!--677150-->
新添加的__设备操作__报表显示了在设备上执行远程操作（如出厂重置）的操作者，还额外显示了该操作的状态。

#### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>非托管设备可访问已分配的应用<!--664691-->
公司门户网站上的设计更改之一是，iOS 和 Android 用户能够在其非托管设备上安装分配到的“可用且无需注册”设备。 用户可使用其 Intune 凭据登录到公司门户网站，并查看分配到的应用列表。 “可用且无需注册”应用的应用包可通过公司门户网站进行下载。 需要注册才能安装的应用不受此更改影响，如果用户想安装这类应用，则会提示用户注册其设备。

#### <a name="custom-app-categories---748805--"></a>自定义应用类别<!--748805-->
现可以为添加到 Intune 的应用创建、编辑和分配类别。 目前，只能以英文指定类别。
请参阅[如何将应用添加到 Intune](/intune-azure/manage-apps/add-apps)。

#### <a name="display-device-categories---814654--"></a>显示设备类别<!--814654-->
现在可以将设备类别作为设备列表中的一列进行查看。 并且还可以在设备属性边栏选项卡的属性部分编辑该类别。

### <a name="january-2017"></a>2017 年 1 月

#### <a name="custom-app-categories---748805--"></a>自定义应用类别<!--748805-->
现可以为添加到 Intune 的应用创建、编辑和分配类别。 目前，只能以英文指定类别。

#### <a name="assign-line-of-business-apps-whether-or-not-devices-are-enrolled---748803--"></a>分配业务线应用（无论设备是否注册）<!--748803-->
现在，无论用户的设备是否已注册 Intune，都可以从应用商店向用户分配业务线和应用。 如果用户设备未注册 Intune，他们必须转到公司门户网站（而非公司门户应用）安装它。

### <a name="december-2016"></a>2016 年 12 月

#### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Azure 门户公开预览版中的电信费用管理集成<!--747605-->
现在，我们将开始在 Azure 门户中预览与第三方电信费用管理 (TEM) 服务的集成。 可以使用 Intune 强制实施对国内和漫游数据使用的限制。 我们将使用 [Saaswedo](http://www.saaswedo.com) 开始这些集成。 若要在试用租户中启用此功能，请[联系 Microsoft 支持](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)。

### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new-in-microsoft-intune.md)。



<!--HONumber=Feb17_HO2-->


