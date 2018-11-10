---
title: 将 Microsoft Store 应用添加到 Microsoft Intune
titleSuffix: ''
description: 了解如何将 Microsoft Store (Windows Store) 应用添加到 Microsoft Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 07241b6d-86d8-4abb-83a2-3fc5feae5788
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: da10455cd6dc3cfbda23726832c539c206aea18c
ms.sourcegitcommit: 814d1d473de2de2e735efab826b1091de2b093f5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2018
ms.locfileid: "51025145"
---
# <a name="add-microsoft-store-apps-to-microsoft-intune"></a>将 Microsoft Store 应用添加到 Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

必须首先将应用添加到 Intune 中，才可以分配、监视、配置或保护它们。 

## <a name="add-an-app-to-intune"></a>将应用添加到 Intune
通过执行以下操作可将 Microsoft Store 应用添加到 Intune：

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。  
    Intune 位于“监视 + 管理”部分中。
3. 在“Intune”窗格中，选择“客户端应用”。
4. 在“客户端应用”工作负载窗格的“管理”下，选择“应用”。
5. 在“应用”窗格中，选择“添加”。
6. 在“添加应用”窗格中，选择“Windows ”的“应用类型”，然后选择“应用信息”。
7. 在“应用信息”窗格中，添加应用信息。 此窗格中的某些值可能已自动填充（具体取决于所选应用）：
    - **名称**：输入要在公司门户中显示的应用名称。 请确保使用唯一的应用名称。 如果应用名称重复，则在公司门户中仅向用户显示一个名称。
    - 描述：为应用输入描述。 在公司门户中向用户显示该描述。
    - 发布者：输入应用的发布者名称。
    - **应用商店 URL**：键入要创建的应用的应用商店 URL。
    - **类别**（可选）：选择一个或多个内置应用类别或你创建的类别。 此操作可让用户在浏览公司门户时更轻松地查找应用。
    - 在“公司门户”中将此显示为特别推荐的应用：选择此选项可在用户浏览应用时，在“公司门户”的主页上突出显示应用套件。
    - 信息 URL：（可选）输入包含此应用相关信息的网站 URL。 在公司门户中向用户显示该 URL。
    - 隐私 URL：（可选）输入包含此应用相关隐私信息的网站 URL。 在公司门户中向用户显示该 URL。
    - 开发人员：（可选）输入应用开发人员的名称。
    - 所有者：（可选）输入此应用的所有者的名称（例如，HR 部门）。
    - 备注：（可选）输入要与此应用关联的任何备注。
    - **徽标**（可选）：上传将与应用关联的图标。 用户浏览公司门户时，此图标将与应用一同显示。
8. 选择“确定”。
9. 选择“添加”。

此时，已创建的应用显示在应用列表中，可在此列表中将其分配到选择的组。 Microsoft Store 应用仅分配到分配类型为“适用于已注册设备”的组（用户从公司门户应用或网站安装应用）。

## <a name="next-steps"></a>后续步骤
- [将应用分配给组](apps-deploy.md)
