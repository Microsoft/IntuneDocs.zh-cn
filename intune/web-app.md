---
title: "如何将 Web 应用添加到 Intune"
titleSuffix: Azure portal
description: "了解如何将 Web 应用添加到 Intune。"
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 12/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6da1441b16a43b5e22bedd9e87970f3388b11b9e
ms.sourcegitcommit: a3a744ea55f38a360ca9f788c77a5b3018d1add5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/30/2017
---
# <a name="how-to-add-web-apps-to-microsoft-intune"></a>如何将 Web 应用添加到 Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

必须先向 Intune 添加应用，然后才能为用户管理和分配此应用。 Intune 支持包括 Web 应用在内的各种应用类型。

> [!Note]
> Android for Work 设备不支持 Web 应用。

若要在 Intune 中将应用添加为 Web 应用的快捷方式，请完成以下步骤：

1. 登录 Azure 门户。
2. 使用“更多资源”搜索并选择“Intune”。
3. 在“Microsoft Intune”边栏选项卡上，选择“移动应用”。
4. 在“移动应用”边栏选项卡上，选择“应用”。
5. 在应用列表上方，选择“添加”。 此时，“添加应用”边栏选项卡显示。
6. 在“添加应用” 边栏选项卡中，从“应用类型”下拉列表中选择“Web 应用”类型。
7. 选择“配置”选项，调出“应用信息”边栏选项卡。
8. 在“应用信息”边栏选项卡中，添加以下信息：
    - **名称** - 输入要在“公司门户”中显示的应用名称。
    - **描述** — 为应用输入描述。 这就是在“公司门户”中向最终用户显示的名称。
    - **发行者** - 输入应用的发行者名称。
    - **应用 URL** - 输入可托管要分配的应用的网站 URL。
    - **类别（可选）**- 选择一个或多个内置应用类别或你创建的类别。 此选择可方便用户在浏览“公司门户”时更轻松地查找应用。
    - **在公司门户中将此应用显示为特色应用** - 当用户浏览应用时，在公司门户的主页上突出显示此应用。
    - **需要托管浏览器才能打开此链接** - 用户只能在 Intune 托管浏览器中打开向其分配的网站或 Web 应用链接。 必须在用户的设备上安装此浏览器。
    - **徽标**- 上传与应用关联的徽标。 这就是在用户浏览“公司门户”时与应用一同显示的徽标。
9. 完成后，选择“添加信息”边栏选项卡上的“确定”。
10. 然后，选择“添加应用”边栏选项卡中的“添加”。

此时，已创建的应用显示在应用列表中，可供分配到选定组。 如需帮助，请参阅[如何将应用分配到组](apps-deploy.md)。