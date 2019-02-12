---
title: 使用 Microsoft Intune 中的作用域标记来筛选策略 - Azure | Microsoft Docs
description: 使用作用域标记将配置文件筛选到特定角色。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9441f1c69e3d445d6174521ad2c9ef5c7a6db2be
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55835531"
---
# <a name="use-scope-tags-to-filter-policies"></a>使用作用域标记筛选策略

通过作用域标记，可筛选你创建的含自定义标记的策略。 可以将作用域标记应用到角色和应用。

例如，创建名为“工程部门”的作用域标记，并将其分配给与工程部门相关的配置文件。 将该相同标记分配给“工程管理员”角色。 他们将只能看到含“工程部门”标记的策略。

## <a name="to-create-a-scope-tag"></a>创建作用域标记

选择“角色” > “作用域(标记)” > “创建”。

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>将作用域标记添加到配置文件

选择“设备配置” > “配置文件”> 选择配置文件 >“属性” > “作用域(标记)”。

## <a name="to-assign-a-scope-tag-to-a-role"></a>向角色分配作用域标记

选择“角色” > “所有角色” > “策略和配置文件管理器” > “分配” > “作用域(标记)”。

## <a name="to-assign-a-scope-tag-to-an-app"></a>向应用分配作用域标记

选择“客户端应用” > “应用”> 选择应用 >“属性” > “作用域(标记)” > “添加”> 选择标记 >“选择” > “确定” > “保存”。


## <a name="next-steps"></a>后续步骤

管理[角色](role-based-access-control.md)和[配置文件](device-profile-assign.md)。

