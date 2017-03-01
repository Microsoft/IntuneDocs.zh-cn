---
title: "新增功能 | Microsoft Docs"
description: "了解 Microsoft Intune 当月新增的功能和过去的版本"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/17/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: cb1679deda0ba325ee3bd7288713f12317489006
ms.openlocfilehash: 37d44dc2752815ef7abf47e5d4a658a126892a86
ms.lasthandoff: 02/18/2017


---
# <a name="whats-new-in-microsoft-intune---february-2017"></a>Microsoft Intune 新增功能 - 2017 年 2 月
了解此版本 Microsoft Intune 中的新增功能。 你还可以发现需要计划的即将发生的更改，以及有关过去版本的信息。

> [!Note]
> 所有这些功能最终将支持混合客户部署（带 Intune 的 Configuration Manager）。 有关新的混合功能的详细信息，请查看[混合新增功能页](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。

## <a name="new-capabilities"></a>新功能

### <a name="modernizing-the-company-portal-website---753980--"></a>公司门户网站现代化<!--753980-->
公司门户网站将支持面向不具有托管设备的用户的应用。 此网站将使用新的撞色配色方案、动态图和“汉堡菜单”（![汉堡菜单的小图，该图片现已添加到公司门户网站左上角](./media/CP_hamburger_menu.png)，它包括了支持人员详细联系信息和现有托管设备的信息），这与 Microsoft 其他产品和服务保持一致。 将重新排列登录页，强调可供用户使用的应用，登录页上具有针对特色应用和最近更新应用的传送。 可在 [UI 更新页](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui)上查看提供的最初和最后的图像。

### <a name="new-guided-experience-for-windows-10-company-portal---713927--"></a>Windows 10 公司门户新的引导式体验<!--713927-->
从 3 月开始，适用于 Windows 10 的公司门户将为尚未被标识或注册的设备提供引导式的 Intune 演练体验。 新体验根据用户的 Windows 10 版本提供分步说明，引导用户执行 AAD 注册（用于条件访问功能的标识）和 MDM 注册（用于设备管理功能）。 引导式体验将可从公司门户主页访问，并且是可选的；如果用户未完成注册，仍然可以继续使用该应用，但有些功能可能会受到限制。

## <a name="notices"></a>通知

### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>iOS 设备的组迁移将不需要对组或策略进行任何更新<!--898837-->
对于所有由公司设备注册配置文件预分配的 Intune 设备组，在迁移到 Azure Active Directory 设备组期间，都将根据公司设备注册配置文件的名称在 AAD 中创建相应的动态设备组。 这样可以确保设备在注册时自动进行分组，并接收与原始 Intune 组相同的策略和应用。

租户进入分组和设定目标的迁移阶段时，Intune 将自动创建一个动态 AAD 组，该组与公司设备注册配置文件面向的 Intune 组相对应。 Intune 管理员删除目标 Intune 组时，相应的动态 AAD 组不会被删除。 组成员和动态查询将被清除，但该组本身将继续保留，直到 IT 管理员通过 AAD 门户将其删除。

同样，如果 IT 管理员更改了公司设备注册配置文件面向的 Intune 组，Intune 将创建新的动态组来反映新的配置文件分配，但不会删除为旧分配创建的动态组。

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>默认通过 Windows 设置管理 Windows 桌面设备<!--663050-->
用于注册 Windows 10 桌面版的默认行为发生了变化。 新的注册将遵循典型 MDM 代理注册流程，而非通过电脑代理进行。 公司门户网站将为 Windows 10 桌面用户提供注册说明，指导他们完成将 Windows 10 桌面计算机添加为移动设备的过程。 这不会影响当前已注册的电脑，[如果愿意](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune)，组织仍可使用电脑代理来管理 Windows 10 桌面。

### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>改进对选择性擦除的移动应用管理支持<!--581242-->
如果由于“擦除应用数据前的脱机时间间隔”策略导致自动删除了工作或学校数据，则将为最终用户提供有关如何重新获得这些数据的访问权限的其他指导。<!--, or the removal of the Intune Company Portal on Android.-->

### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>iOS 版公司门户链接在应用内打开<!--665954-->
iOS 版公司门户应用内的链接（包括文档和应用链接）将通过 Safari 的应用内视图直接在公司门户应用中打开。 此更新将与&1; 月的服务更新分开提供。

### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Windows 设备的新 MDM 服务器地址<!--893007-->
Windows 和 Windows Phone 用户如果输入 __manage.microsoft.com__ 作为 MDM 服务器地址（出现提示时），尝试注册设备时将失败。 MDM 服务器地址已从 __manage.microsoft.com__ 更改为 __enrollment.manage.microsoft.com__。 通知用户在注册 Windows 和/或 Windows Phone 时，如果出现提示，请使用 __enrollment.manage.microsoft.com__ 作为 MDM 服务器地址。 无需更改 CNAME 设置。 有关此更改的详细信息，请访问[aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange)。

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Android 适用的公司门户应用的最新用户体验<!--621622-->
从&3; 月开始，Android 适用的公司门户应用将按照[材料设计指南](https://material.io/guidelines/material-design/introduction.html)来打造更具现代感的外观。 这将改善以下用户体验：

* __颜色__：可以根据自定义调色板对选项卡标头着色。
* __界面__：“应用”选项卡上已更新了“特色应用”和“所有应用”按钮。 “搜索”按钮现在是浮动的操作按钮。
* __导航__：“所有应用”以选项卡形式呈现出“特色”、“所有”和“分类”视图，便于导航。
* __服务__：“我的设备”和“联系 IT”选项卡提高了可读性。

可在 [UI 更新页](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui)上查看最初和最后的图像。

### <a name="associate-multiple-management-tools-with-the-windows-store-for-business---926135--"></a>将多个管理工具与适用于企业的 Windows 应用商店关联<!--926135-->
使用多个管理工具部署适用于企业的 Windows 应用商店时，以前只能将一个管理工具与适用于企业的 Windows 应用商店相关联。 现在可以将多个管理工具与应用商店相关联，例如 Intune 和 Configuration Manager。 有关详细信息，请参阅[使用 Microsoft Intune 管理从适用于企业的 Windows 应用商店中购买的应用](https://docs.microsoft.com/en-us/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune#associate-your-windows-store-for-business-account-with-intune)。

## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Azure 上的 Intune 管理体验公开预览版的新增功能<!--736542-->

在 2017 年初，我们会将完整管理体验迁移到 Azure 上，以便能够在可使用图形 API 进行扩展的新式服务平台上对核心 EMS 工作流进行强大且集成的管理。

新的试用租户将于本月开始在 Azure 门户中看到新管理体验的公开预览版。 在预览状态下，将以迭代方式交付现有 Intune 控制台的功能和奇偶校验。

Azure 门户中的管理体验将使用已公布的新分组和定向功能；当现有租户迁移到新的分组体验时，也会将你迁移，以预览租户上的新管理体验。 在此期间，如果想要在租户迁移之前测试或查看任何新功能，请注册新的 Intune 试用帐户或查阅[新文档](https://docs.microsoft.com/intune-azure/introduction/whats-new)。

如果对租户迁移的时间表有任何疑问，请通过 [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com) 联系我们的迁移团队。

在[此处](https://docs.microsoft.com/intune-azure/introduction/whats-new)可找到 Azure 中 Intune 预览版的新增功能。

### <a name="see-also"></a>另请参阅
* [Microsoft Intune 博客](http://go.microsoft.com/fwlink/?LinkID=273882)
* [云平台路线图](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Azure 预览版的新增功能](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [What's new in the Company Portal UI](https://docs.microsoft.com/intune/whats-new/whats-new-in-company-portal-ui)（公司门户 UI 新增功能）
* [新增功能存档](whats-new-archive.md)

