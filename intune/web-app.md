---
title: "如何将 Web 应用添加到 Intune"
titleSuffix: Intune on Azure
description: "了解如何将 Web 应用添加到 Intune。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 476e547f2ee21119443b08db0984f66844f701d3
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-add-web-apps-to-microsoft-intune"></a>如何将 Web 应用添加到 Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“管理应用”。
4. 在“移动应用”工作负荷中，选择“管理” > “应用”。
5. 在应用列表的上方，选择“添加”。
6. 在“添加应用”边栏选项卡中，选择“应用信息”。
7. 在“编辑应用”边栏选项卡中，配置以下信息。 完成后，单击“添加”：
    - **应用 URL** - 输入可托管要分配的应用的网站 URL。
    - **应用名称** - 输入应用的名称，该名称将显示在公司门户中。
    - **应用描述** - 为应用输入描述。 该描述将在公司门户中向最终用户显示。
    - **发行者** - 输入应用的发行者名称。
    - **类别（可选）**- 选择一个或多个内置应用类别或你创建的类别。 这可让用户在浏览公司门户时更轻松地查找应用。
    - **在公司门户中将此应用显示为特色应用** - 当用户浏览应用时，在公司门户的主页上突出显示此应用。
    - **需要使用 Managed Browser 打开此链接** - 向用户分配网站或 Web 应用的链接时，用户将只能在 Intune Managed Browser 中打开此链接。 必须在用户的设备上安装此浏览器。
    - **上传图标** - 上传将与应用关联的图标。 用户浏览公司门户时，此图标将与应用一同显示。
8. 完成后，在“添加应用”边栏选项卡上，选择“保存”。

创建的应用将显示在应用列表中，可在该列表中将其分配到所选择的组。 如需帮助，请参阅[如何将应用分配到组](apps-deploy.md)。