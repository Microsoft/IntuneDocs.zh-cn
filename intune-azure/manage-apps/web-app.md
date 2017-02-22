---
title: "如何将 Web 应用添加到 Intune | Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：了解如何将 Web 应用添加到 Intune。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/11/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4188957e263717d416853f308a50e3dbd7a9244a
ms.openlocfilehash: 4f8af0008300550d284957c1002be779e0e53f79

---

# <a name="how-to-add-web-apps-to-intune"></a>如何将 Web 应用添加到 Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“管理应用”。
4. 在“移动应用”工作负荷中，选择“管理” > “应用”。
5. 在应用列表的上方，选择“添加”。
6. 在“添加应用”边栏选项卡中，选择“应用信息”。
7. 在“编辑应用”边栏选项卡中，配置以下信息。 完成后，单击“添加”：
    - **应用 URL** - 输入承载想要部署的应用的网站 URL。
    - **应用名称** - 输入应用的名称，该名称将显示在公司门户中。
    - **应用描述** - 为应用输入描述。 该描述将在公司门户中向最终用户显示。
    - **发行者** - 输入应用的发行者名称。
    - **类别（可选）**- 选择一个或多个内置应用类别或你创建的类别。 这可让用户在浏览公司门户时更轻松地查找应用。
    - **在公司门户中将此应用显示为特色应用** - 当用户浏览应用时，在公司门户的主页上突出显示此应用。
    - **需要使用 Managed Browser 打开此链接** - 向用户部署网站或 Web 应用的链接时，用户将只能在 Intune Managed Browser 中打开此链接。 必须在用户的设备上安装此浏览器。
    - **上传图标** - 上传将与应用关联的图标。 用户浏览公司门户时，此图标将与应用一同显示。
8. 完成后，在“添加应用”边栏选项卡上，选择“保存”。

创建的应用将显示在应用列表中，可在该列表中将其分配到所选择的组。 如需帮助，请参阅[如何将应用分配到组](/intune-azure/manage-apps/deploy-apps)。


<!--HONumber=Feb17_HO1-->


