---
title: "如何将应用分配到组 | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Intune Azure 预览版：将应用添加到 Intune 后，需要将其分配给用户或设备组。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: 21ccb23023e9cb4f4b827887f8191ea73474c5de
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---

# <a name="how-to-assign-apps-to-groups-with-microsoft-intune"></a>如何使用 Microsoft Intune 将应用分配到组

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

将应用添加到 Intune 后，需要将其交给用户和设备。 通过分配执行此操作。

可以将应用分配到 Intune 托管或非 Intune 托管设备。 使用下表帮助了解用于将应用分配到用户和设备的各种选项：

||||
|-|-|-|-|
|&nbsp;|已注册到 Intune 的设备|未注册到 Intune 的设备|
|分配到用户|是|是|
|分配到设备|是|否|
|分配包装的应用或整合 Intune SDK 的应用（适用于应用保护策略）|是|是|
|将应用分配为“可用”|是|是|
|将应用分配为“必需”|是|否|
|卸载应用|是|否|
|最终用户从公司门户应用安装可用的应用|是|否|
|最终用户从基于 Web 的公司门户安装可用的应用|是|是|

> [!NOTE]
> 目前，可将（业务线和应用商店购买的）iOS 和 Android 应用分配到未注册到 Intune 的设备。

## <a name="changes-to-how-you-assign-apps-to-groups-in-the-intune-preview"></a>更改如何在 Intune 预览版将应用分配到组

在 Intune Azure 预览版中，无法再使用 Intune 组来分配应用；现在需使用 Azure Active Directory (Azure AD) 安全组。 因此，需要了解应用分配的工作方式的变化，特别是已将应用分配到 Intune 子组时。
最需要注意的是，Azure AD 中不存在子组的概念。 但是，有些组可能包含相同的成员。 在这种情况下，经典 Intune 和 Intune Azure 预览版之间的行为是不同的。 下表对这一情况进行了说明：

||||||
|-|-|-|-|-|
|**Intune 经典版（租户迁移前）**|-|**Intune Azure（完成租户迁移后）**|-|**详细信息**|
|**父组分配意图**|**子组分配意图**|**先前父组和子组常见成员产生的分配意图**|**父组成员产生的分配意图操作**|-|    
|可用|必需|必需和可用|可用|必需和可用表示作为必需进行分配的应用也可显示在公司门户应用中。
|不适用|可用|不适用|不适用|解决方法：从 Intune 父组删除“不适用”分配意图。
|必需|可用|必需和可用|必需|-|
|必需和可用<sup>1</sup>|可用|必需和可用|必需和可用|-|    
|必需|不适用|必需|必需|-|    
|必需和可用|不适用|必需和可用|必需和可用|-|    
|必需|“卸载”|必需|必需|-|    
|必需和可用|“卸载”|必需和可用|必需和可用|-|
<sup>1</sup> 仅针对托管 iOS 应用商店应用：将这些应用添加到 Intune 并将其分配为“必需”时，将自动使用“必需”和“可用”意图进行创建。

可采用以下操作，避免分配冲突：

1.    如果先前已将应用分配到了相关 Intune 父组和子组，请考虑在开始迁移租户前删除这些分配。
2.    从父组删除子组，并创建包含旧子组成员的新组。 然后可向此组创建新应用分配。
注意：如果上一个父组为“所有用户”，则需要创建一个不包含子组成员的新动态组。
必须在用户和设备组的 [Azure 门户](https://portal.azure.com/)中更改组。 [经典 Azure 门户](https://manage.windowsazure.com/)只允许更改用户组。


## <a name="how-to-assign-an-app"></a>如何分配应用

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“移动应用”。
1. 在“移动应用”工作负荷中，选择“管理” > “应用”。
2. 在“应用列表”边栏选项卡中，单击要分配的应用。
3. 在“<应用名称> - 概述”边栏选项卡上，选择“管理” > “分配”。
4. 选择“选择组”，然后在“选择组”边栏选项卡上，选择要将应用分配到的 Azure AD 组。
5. 对于选择的每个应用，从以下各项选择应用的“分配类型”：
    - **可用** - 用户从公司门户应用或网站安装应用。
    - **不适用** - 未在公司门户安装或显示该应用。
    - **必需** - 应用安装在所选组中的设备上。
    - **卸载** - 已从所选组中设备上卸载应用。
    - **注册与否都可用** - 可将此应用分配到未将其设备注册到 Intune 的用户组。 参见上表以获取帮助。
6. 完成后，选择“保存”。

应用现已分配给所选组。

有关帮助监视应用分配的信息，请参阅[如何监视应用](monitor-apps.md)。

