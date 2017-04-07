---
title: "迁移到 Azure Active Directory 组 | Microsoft Docs"
description: "如何将组从 Intune 迁移到 Azure AD"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angerobe
ms.date: 12/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 03b69afa-3548-4033-9039-191528f3fd99
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 911d2887791cf16d4290c3ac5189aa44086f4603
ms.openlocfilehash: d3b4b823683196148d4fb8aa296b59c9c712e99f
ms.lasthandoff: 03/11/2017


---

# <a name="a-new-way-of-using-groups-in-intune"></a>Intune 中一种使用组的新方法

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

我们已得到了你的反馈，将对在 Microsoft Intune 中处理组的工作方式进行某些更改。
我们正在将我们所有的客户 Intune 组迁移到 Azure Active Directory 安全组。

为你带来的好处是，现在你可在你所有的企业移动性 + 安全性应用和 Azure AD 应用中使用相同的组体验。 此外，还能够使用 PowerShell 和 Graph API 来扩展和自定义此新功能。

Azure AD 安全组支持将所有类型的 Intune 部署到用户和设备。 此外，还可使用基于所提供的属性自动更新的 Azure AD 动态组。 例如，可创建一组运行 iOS 9 的设备。 每当注册运行 iOS 9 的新设备时，该设备都将自动添加到动态组。

## <a name="when-is-this-happening"></a>何时发生这种情况？

可立即进行迁移过程。 迁移前，你将收到通知。
如果你已迁移，则尝试从经典 Intune 控制台访问组时，会看到以下类似消息：

![显示组已被迁移的消息。](http://i.imgur.com/72KRaXj.png)

## <a name="what-wont-be-available"></a>哪些功能将不可用？

Intune 组某些现有功能在 Azure AD 中不可用：

- 将不迁移“未分组用户”和“未分组设备”Intune 组。
- Intune 中当前存在的用于从某个组中**排除特定成员**的选项不存在于 Azure 门户中。 但是，可使用具有高级规则的 Azure AD 安全组复制此行为。 例如，可使用以下高级规则，在安全组中创建包含“销售”部门所有成员的高级规则，但不包含职位中含有“助手”一词的成员：`(user.department -eq "Sales") -and -not (user.jobTitle -contains "Assistant")`。
- 内置于 Intune 控制台中的“所有 Exchange ActiveSync 托管设备”组将不会迁移到 Azure AD。 但仍可从 Azure 门户访问 EAS 托管设备的相关信息。
- 将不能在经典 Intune 控制台中按组筛选报表。
<!--- - Custom group targeting of notification rules will not be available. ROB I took this out as I couldn't replicate the behavior. --->

## <a name="how-to-get-ready"></a>如何做好准备

- 阅读以下 Azure AD 主题，了解 Azure AD 安全组及其工作原理：
    -  [使用 Azure Active Directory 组管理对资源的访问](https://azure.microsoft.com/en-us/documentation/articles/active-directory-manage-groups/)。
    -  [在 Azure Active Directory 中管理组](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-manage-groups/)。
    -  [使用属性创建高级规则](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/)。
- 请考虑删除迁移前不再使用的任何 Intune 组。
-  确保将任何需要创建组的管理员添加到 **Intune 服务管理员** Azure AD 角色。 请注意，Azure AD 服务管理员角色没有**管理组**权限。
-  如果使用含“排除特定成员”选项的组，请考虑你是否可重新设计这些组，而不需排除项，或是否可在 Azure AD 查询中使用高级规则以达到相同的结果。


## <a name="what-happens-to-intune-groups"></a>Intune 组会出现什么情况？

| Intune 中的组|Azure AD 中的组|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|静态用户组|静态 Azure AD 安全组|
|动态用户组|具有 Azure AD 安全组层次结构的静态 Azure AD 安全组|
|静态设备组|静态 Azure AD 安全组|
|动态设备组|动态 Azure AD 安全组|
|含有 include 条件的组|静态 Azure AD 安全组，包含 Intune 中 include 条件允许的任意静态/动态成员。|
|含有 exclude 条件的组|不迁移|
|内置组：“所有用户”、“未分组用户”、“所有设备”、“未分组设备”、“所有计算机”、“所有移动设备”、“所有 MDM 托管设备”和“所有 EAS 托管设备”|Azure AD 安全组。|

在 Intune 中，所有组都必须具有父组。 组只能包含来自其父组的成员。 在 Azure AD 中，子组可包含父组不具有的成员。

属性是指可用于定义组的设备属性。 下表描述如何将这些条件迁移到 Azure AD 安全组。

| Intune 中的属性|Azure AD 中的属性|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|设备组的组织单位 (OU) 属性|动态组的 OU 属性。|
|设备组的域名属性|动态组的域名属性。|
|作为用户组属性的安全组|在 Azure AD 动态查询中组不能作为属性。 动态组只能包含用户或设备特定的属性。|
|用户组的管理器属性|动态组中管理器属性的高级规则|
|父用户组中的所有用户|包含该组（作为成员）的静态组|
|父设备组中的所有移动设备|包含该组（作为成员）的静态组|
|由 Intune 托管的所有移动设备|动态组值为“MDM”的管理类型属性|
|静态组内的嵌套组 |静态组内的嵌套组|
|动态组内的嵌套组|含有一级嵌套的动态组|

## <a name="what-happens-to-policies-and-apps-youve-already-deployed"></a>已部署的策略和应用会出现什么情况？

像之前一样，策略和应用仍会部署到组。 但现在将从 Azure 门户，而非经典 Intune 控制台来管理这些组。
 

