---
title: "迁移到 Azure Active Directory 组 | Microsoft Intune"
description: "如何将组从 Intune 迁移到 Azure AD"
keywords: 
author: Mtillman
ms.author: mtillman
manager: angerobe
ms.date: 10/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 03b69afa-3548-4033-9039-191528f3fd99
translationtype: Human Translation
ms.sourcegitcommit: 17b957cc2baedddfc53bfdf7b875e4ecb28b8517
ms.openlocfilehash: e14bbadc4293b7b963197b35704a7170e4fc29e8


---

## <a name="the-new-admin-experience-for-groups"></a>新的组管理员体验
    
基于你对跨企业移动性和安全性具有一个分组和定位体验的反馈，我们会将 Intune 组转换为基于 Azure Active Directory 的安全组。 这将跨 Intune 和 Azure Active Directory (Azure AD) 统一组管理。 此新体验将使你无需在服务间复制组，并可使用 PowerShell 和 Graph 提供可扩展性。 

### <a name="how-and-when-will-i-migrate-to-the-new-groups-experience"></a>我将什么时候以何种方式迁移到新的组体验？
当前客户将经过一段时间完成迁移（在不早于 2016 年 12 月的时间开始）。 组迁移前，你将收到一条通知。 如果有任何关于迁移的问题，请发送电子邮件到 [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com) 与我们的迁移团队联系。

### <a name="what-new-features-will-be-available-to-me"></a>将为我提供哪些新功能？
下面是将引入的新功能： 
 
-    在 Intune 中，所有类型的部署都将支持 Azure AD 安全组。 
-    Azure AD 安全组将支持对设备和用户进行分组。
-    Azure AD 安全组将支持具有 Intune 设备属性的动态组。 例如，你将能够基于平台（如 iOS）对设备进行动态分组。 这样一来，当新的 iOS 设备在组织中注册时，它将被自动添加到 iOS 动态设备组中。
-    跨 Azure AD 和 Intune 的组管理的共享管理员体验。
- Intune 服务管理员角色将被添加到 Azure AD 以允许 Intune 中的服务管理员在 Azure AD 中执行组管理任务。

 
### <a name="what-intune-functionality-wont-be-available"></a>哪种 Intune 功能将不可用？
虽然组体验将改进，但迁移后，有些 Intune 功能将不可用。

#### <a name="group-management-functionality"></a>组管理功能

-   创建新组时，你将不能排除成员或组。 但是，Azure AD 动态组将允许你使用属性创建高级规则，基于条件排除成员。 例如，可在安全组中创建包含销售部门所有成员的高级规则，但不包含职位中含有“助手”一词的成员，此高级规则为：`(user.department -eq "Sales") -and -not (user.jobTitle -contains "Assistant")`。 有关详细信息，请参阅[使用属性创建高级规则](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/)。
-   将不支持“未分组的用户”和“未分组的设备”组。 不会迁移这些组。

#### <a name="group-dependent-functionality"></a>组的依赖功能

-   服务管理员角色将不会有“管理组”权限。
-   你将不能对 Exchange ActiveSync 设备进行分组。  你的“所有 EAS 托管设备” 组将从组转换为报告视图。
-  利用报表中的组进行透视将不可用。
-  通知规则的自定义组目标将不可用。

### <a name="what-should-i-do-to-prepare-for-this-change"></a>我应该针对此更改做什么准备？
 以下建议将使你的转换更容易：
 
- 迁移前清除任何不想要或不需要的 Intune 组。
- 评估组内排除的使用情况，考虑如何重新设计组，而无需再用到排除或使用高级规则达到相同的目的。
-  如果你有不具有在 Azure AD 中创建组的权限的管理员，请让你的 Azure AD 管理员将其添加到 **Intune 服务管理员** Azure AD 角色。

还可了解有关 Azure AD 安全组的详细信息：
-  有关概述，请参阅[使用 Azure Active Directory 组管理对资源的访问](https://azure.microsoft.com/en-us/documentation/articles/active-directory-manage-groups/)。
-  有关如何创建和管理 Azure AD 组的信息，请参阅[管理 Azure Active Directory 中的组](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-manage-groups/)。
-  有关安全组的高级规则的详细信息，请参阅[使用属性创建高级规则](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/)。

> [!NOTE]
你可能注意到，Azure AD 安全组文档中未讨论为设备创建组。 在 Intune 组迁移开始之前，Azure AD 中会启用该功能。

## <a name="migration-details"></a>迁移详细信息
以下是如何将 Intune 组迁移到 Azure AD 安全组的详细信息。

### <a name="migration-of-existing-groups"></a>迁移现有组

| Intune 组将成为...|...Azure AD 安全组|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Intune 策略针对的静态用户组|包含相同用户的静态 Azure AD 安全组|
|Intune 策略针对的动态用户组|具有 Azure AD 安全组层次结构的静态 Azure AD 安全组|
|Intune 策略针对的静态设备组|含有设备的静态 Azure AD 安全组|
|含有设备属性，Intune 策略针对的动态设备组|含有设备属性的动态 Azure AD 安全组|
|含有 include 条件的组|一个单独的静态 Azure AD 安全组将包含一个组和 include 条件允许的 Intune 中的任意静态/动态成员|
|含有 exclude 条件的组|...不会被迁移。 在 Azure AD 中创建静态组时不支持 exclude 条件。 在 Azure AD 中创建动态组时可使用 exclude 条件。|
|Intune 策略中使用的默认组：“所有用户”、“未分组用户”、“所有设备”、“未分组设备”、“所有计算机”、“所有移动设备”、“所有 MDM 托管设备”和“所有 EAS 托管设备”  |Azure AD 安全组。 使用动态组时，用户需按需创建未使用的默认组。|

### <a name="changes-in-hierarchical-views"></a>分层视图中的变更
Intune 中的 Intune 父子关系内的组分层视图为超集子集关系，而在 Azure AD 中却并非如此。 子级中可包含父级中没有的成员。 在 Azure AD 中，组本质上是可以循环的 - 父组可以是子组的子级。

### <a name="attribute-conversion-during-migration"></a>迁移期间的属性转换
属性是指可用于定义组的设备属性。 下表描述如何将这些条件迁移到 Azure AD 安全组。

| Intune 属性|Azure AD 属性|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|设备组的组织单位 (OU) 属性|动态组的 OU 属性。 将属性值添加为一个租户组件进行查看，使与每个租户相关的管理员能够使用该属性值。|
|设备组的域名属性|动态组的域名属性。 将属性值添加为一个租户组件进行查看，使与每个租户相关的管理员能够使用该属性值|
|作为用户组属性的安全组|在 Azure AD 动态查询中组不能作为属性。 动态组只能包含用户或设备特定的属性。|
|用户组的管理器属性|动态组中管理器属性的高级规则|
|父用户组中的所有用户|包含该组（作为成员）的静态组|
|父设备组中的所有移动设备|包含该组（作为成员）的静态组|
|由 Microsoft Intune 直接管理托管的所有移动设备|动态组值为“MDM”的管理类型属性|
|由 EAS 托管的所有移动设备|无法在 Azure AD 中对 EAS 设备分组。 你的“所有 EAS 托管设备” 组将从组转换为报告视图。|
|静态组内的嵌套组 |静态组内的嵌套组|
|动态组内的嵌套组|含有一级嵌套的动态组|


## <a name="migration-of-policies"></a>策略迁移
进行组迁移的同时，将继续在 Intune 控制台中管理策略。 Intune 控制台中具有指向 Azure 管理控制台的链接，你可以在 Azure 管理控制台中管理组。 将持续部署策略到已迁移的与旧 Intune 组平行的 Azure AD 安全组。

Intune 的所有功能都迁移到 Azure 管理门户后（大约在 2017 年第一季度），就可以在该门户上管理策略和组。

     
### <a name="see-also"></a>另请参阅
[使用 Azure Active Directory 组管理对资源的访问](https://azure.microsoft.com/en-us/documentation/articles/active-directory-manage-groups/)

[在 Azure Active Directory 中管理组](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-manage-groups/)

[使用属性创建高级规则](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/)



<!--HONumber=Nov16_HO1-->


