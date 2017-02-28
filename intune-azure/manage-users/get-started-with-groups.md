---
title: "Intune Azure 门户预览版中的组入门 | Microsoft Docs"
description: "了解 Intune Azure 门户预览版中的组的新增功能"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angerobe
ms.date: 01/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 323f384d-8a76-4adc-999b-e508d641bfa1
translationtype: Human Translation
ms.sourcegitcommit: 00e9dfd165a449182c5b937372db7085c981c68f
ms.openlocfilehash: 9386002cf5ab8bc9dac66646a7de3b00b54b1b72
ms.lasthandoff: 02/14/2017


---

# <a name="get-started-with-groups"></a>组入门

[!INCLUDE[azure preview](../includes/azure_preview.md)]

根据你的反馈，我们对 Microsoft Intune 中组的使用方法进行了某些更改。
如果你从 Azure 门户使用 Intune，Intune 组已迁移到 Azure Active Directory 安全组。

为你带来的好处是，现在可在你所有的企业移动性 + 安全性应用和 Azure AD 应用中使用相同的组体验。 此外，还能够使用 PowerShell 和 Graph API 来扩展和自定义此新功能。

Azure AD 安全组支持将所有类型的 Intune 部署到用户和设备。 此外，还可使用基于所提供的属性自动更新的 Azure AD 动态组。 例如，可创建一组运行 iOS 9 的设备。 每当运行 iOS 9 的设备注册时，该设备将自动显示动态组。

## <a name="what-is-not-available"></a>什么功能不可用？

你可能使用过的某些 Intune 组功能在 Azure AD 中不可用：

- “未分组用户”和“未分组设备”Intune 组将不再可用。
- Azure 门户中不存在从某个组中“排除特定成员”的选项。 但是，可使用具有高级规则的 Azure AD 安全组复制此行为。 例如，若要在安全组中创建包含销售部门所有成员的高级规则，但排除职位中含有“助手”一词的成员，可使用此高级规则：

  `(user.department -eq "Sales") -and -not (user.jobTitle -contains "Assistant")`。
- Intune 控制台中的“所有 Exchange ActiveSync 托管设备”组未迁移到 Azure AD。 但仍可从 Azure 门户访问 EAS 托管设备的相关信息。

## <a name="how-to-get-started"></a>如何开始？

- 阅读以下主题，了解 Azure AD 安全组及其工作原理：
    -  [使用 Azure Active Directory 组管理对资源的访问](https://azure.microsoft.com/en-us/documentation/articles/active-directory-manage-groups/)。
    -  [在 Azure Active Directory 中管理组](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-manage-groups/)。
    -  [使用属性创建高级规则](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/)。
-  确保将需要创建组的管理员添加到 **Intune 服务管理员** Azure AD 角色。 Azure AD 服务管理员角色没有**管理组**权限。
-  如果 Intune 组使用“排除特定成员”选项，需确定是否可在不排除项的情况下重新设计这些组，或是否需要高级规则以满足业务需求。


## <a name="what-happened-to-intune-groups"></a>Intune 组出现了什么情况？
组从经典 Intune 门户迁移到 Azure 门户中的 Intune 时，将应用以下规则：

| Intune 中的组|Azure AD 中的组|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|静态用户组|静态 Azure AD 安全组|
|动态用户组|具有 Azure AD 安全组层次结构的静态 Azure AD 安全组|
|静态设备组|静态 Azure AD 安全组|
|动态设备组|动态 Azure AD 安全组|
|含有 include 条件的组|静态 Azure AD 安全组，包含 Intune 中 include 条件允许的任意静态/动态成员|
|含有 exclude 条件的组|不迁移|
|内置组：<br>- **所有用户**<br>- **取消组合的用户**<br>- **所有设备**<br>- **取消组合的设备**<br>- **所有计算机**<br>- **所有移动设备**<br>- **所有 MDM 托管设备**<br>- **所有 EAS 托管设备**|Azure AD 安全组|

## <a name="group-hierarchy"></a>组层次结构

在经典 Intune 控制台中，所有组都有一个父组。 组只能包含其父组的成员。 在 Azure AD 中，子组可包含父组中没有的成员。

## <a name="group-attributes"></a>组属性
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

## <a name="what-happens-to-policies-and-apps-you-previously-deployed"></a>以前部署的策略和应用会出现什么情况？

像之前一样，策略和应用仍会部署到组。 但现在将从 Azure 门户，而非经典 Intune 控制台来管理这些组。

