---
title: "如何将应用分配到组 | Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：将应用添加到 Intune 后，需要将其分配给用户或设备组。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 638ad0d87c19c9e40e96b42d18e5c4342f40a156
ms.lasthandoff: 02/16/2017

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
|卸载应用|是|是|
|最终用户从公司门户应用安装可用的应用|是|否|
|最终用户从基于 Web 的公司门户安装可用的应用|是|是|

> [!NOTE]
> 目前，可将（业务线和应用商店购买的）iOS 和 Android 应用分配到未注册到 Intune 的设备。

## <a name="how-to-assign-an-app"></a>如何分配应用

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“管理应用”。
1. 在“管理应用”工作负荷中，选择“管理” > “应用”。
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

