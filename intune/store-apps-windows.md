---
title: "如何将 Windows 应用商店应用添加到 Microsoft Intune"
titleSuffix: 
description: "了解如何将 Windows 应用商店应用添加到 Microsoft Intune。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 07241b6d-86d8-4abb-83a2-3fc5feae5788
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2e2280ad72bbd353d80af316cde436e8ffc79d1f
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-windows-store-apps-to-microsoft-intune"></a>如何将 Windows 应用商店应用添加到 Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

必须首先将应用添加到 Intune 中，才可以分配、监视、配置或保护它们。 通过以下步骤，可以将 Windows 商店应用添加到 Microsoft Intune。

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分。
3. 在 Intune 窗格中，选择“移动应用”。
4. 在“移动应用”工作负荷中，选择“管理” > “应用”。
5. 在应用列表的上方，选择“添加”。
6. 在“添加应用”窗格中，选择“Windows”作为“应用类型”，并选择“应用信息”。
7. 在“应用信息”窗格中，配置以下信息。 完成后，单击“确定”。 此窗格中的某些值可能已自动填充（具体取决于所选应用）：
    - **名称** — 输入应用的名称，该名称将显示在公司门户中。 请确保使用的所有应用名称都是唯一的。 如果同一应用名称存在两次，则在公司门户中将仅向用户显示其中一个应用。
    - 说明 - 输入要在公司门户中向用户显示的应用说明。
    - **发行者** — 输入应用的发行者名称。
    - **应用商店 URL** - 输入要创建的应用的应用商店 URL。
    - **类别(可选)** - 选择一个或多个内置应用类别或你创建的类别，使用户在浏览公司门户时可以更轻松地查找应用。
    - **在公司门户中将此应用显示为特色应用** - 当用户浏览应用时，在公司门户的主页上突出显示此应用。
    - **信息 URL** -（可选）输入包含此应用相关信息的网站 URL。 将在公司门户中向用户显示该 URL。
    - **隐私 URL** -（可选）输入包含此应用相关隐私信息的网站 URL。 将在公司门户中向用户显示该 URL。
    - **开发者** -（可选）输入应用开发者的名称。
    - **所有者** -（可选）输入此应用的所有者的名称，例如，**HR 部门**。
    - **说明** - 输入要与此应用关联的任何备注。
    - **徽标** - 上传与应用关联的图标。 用户浏览公司门户时，此图标将与应用一同显示。
8. 完成后，在“添加应用”窗格中，选择“添加”。

创建的应用将显示在应用列表中，可在该列表中将其分配到所选择的组。 

## <a name="next-steps"></a>后续步骤

- [如何将应用分配到组](apps-deploy.md)