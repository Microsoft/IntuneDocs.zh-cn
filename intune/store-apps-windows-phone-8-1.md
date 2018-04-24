---
title: 如何将 Windows Phone 8.1 应用商店应用添加到 Microsoft Intune
titleSuffix: ''
description: 了解如何将 Windows Phone 8.1 应用商店应用添加到 Microsoft Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4a95e575-2c63-4bfc-b9c4-f0a132eef618
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 772257369368783a02a826cddc323960fea436b9
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-windows-phone-81-store-apps-to-microsoft-intune"></a>如何将 Windows Phone 8.1 应用商店应用添加到 Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

将应用分配给一个设备或一组用户之前，必须先将应用添加到 Microsoft Intune。 可按以下步骤，通过 Azure 门户将 Windows Phone 8.1 应用商店应用添加到 Intune。

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 在“Intune”窗格中，选择“移动应用”。
4. 在“移动应用”工作负荷中，选择“管理” > “应用”。
5. 在应用列表的上方，选择“添加”。
6. 在“添加应用”窗格中，选择“Windows Phone 8.1”的“应用类型”，并选择“应用信息”。
7. 在“应用信息”窗格中，配置以下信息。 完成后，单击“确定”。 此窗格中的某些值可能已自动填充（具体取决于所选应用）：
    - **名称** — 输入应用的名称，该名称将显示在公司门户中。 请确保使用的所有应用名称都是唯一的。 如果同一应用名称存在两次，则在公司门户中将仅向用户显示其中一个应用。
    - **描述** — 为应用输入描述。 这将在公司门户中向用户显示。
    - **发行者** — 输入应用的发行者名称。
    - **应用商店 URL** - 输入要创建的应用的应用商店 URL。
    - **类别（可选）**- 选择一个或多个内置应用类别或你创建的类别。 这可让用户在浏览公司门户时更轻松地查找应用。
    - **在公司门户中将此应用显示为特色应用** - 当用户浏览应用时，在公司门户的主页上突出显示此应用。
    - **信息 URL** -（可选）输入包含此应用相关信息的网站 URL。 将在公司门户中向用户显示该 URL。
    - **隐私 URL** -（可选）输入包含此应用相关隐私信息的网站 URL。 将在公司门户中向用户显示该 URL。
    - **开发者** -（可选）输入应用开发者的名称。
    - **所有者** -（可选）输入此应用的所有者的名称，例如，**HR 部门**。
    - **说明** - 输入要与此应用关联的任何备注。
    - **徽标** - 上载将与应用关联的图标。 用户浏览公司门户时，此图标将与应用一同显示。
8. 完成后，在“添加应用”窗格中，选择“添加”。

创建的应用将显示在应用列表中，可在该列表中将其分配到所选择的组。 如需帮助，请参阅[如何将应用分配到组](apps-deploy.md)。

## <a name="next-steps"></a>后续步骤

- [如何将应用分配到组](apps-deploy.md)