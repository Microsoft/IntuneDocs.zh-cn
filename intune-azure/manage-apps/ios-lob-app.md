---
title: "如何将 iOS 业务线应用添加到 Intune | Intune Azure 预览版 | Microsoft Docs"
description: "Intune Azure 预览版：了解如何将 iOS 业务线应用添加到 Intune。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 099101e8-4b22-40ac-ba19-82ba5c71944c
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 6d41adabfab178daa7f6fce3d86bc8216bf4ab29
ms.lasthandoff: 02/16/2017

---

# <a name="how-to-add-ios-line-of-business-lob-apps-to-microsoft-intune"></a>如何将 iOS 业务线 (LOB) 应用添加到 Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


## <a name="step-1---specify-the-software-setup-file"></a>步骤 1 - 指定软件安装程序文件

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在 Intune 边栏选项卡上，选择“管理应用”。
4. 在“移动应用”工作负荷中，选择“管理”>“应用”。
5. 在应用列表的上方，选择“添加”。
6. 在“添加应用”边栏选项卡中，选择“软件安装程序文件”。
7. 在“选择安装程序文件”边栏选项卡中，单击“浏览”按钮并浏览到 iOS 应用安装程序文件（扩展名为 .ipa），然后单击“确定”。

## <a name="step-2---configure-app-information"></a>步骤 2 - 配置应用信息

1. 在“编辑应用”边栏选项卡中，配置以下信息。 完成后，单击“添加”。 根据所选择的应用，此边栏选项卡中的某些值可能已自动填充：
    - **应用名称** - 输入应用的名称，该名称将显示在公司门户中。 请确保使用的所有应用名称都是唯一的。 如果同一应用名称存在两次，则在公司门户中将仅向用户显示其中一个应用。
    - **应用描述** - 为应用输入描述。 这将在公司门户中向用户显示。
    - **发行者** — 输入应用的发行者名称。
    - **适用设备类型** - 选择此应用是否可以安装在 iPad、iPhone 或兼容的 iPod 上。
    - **最低操作系统** - 从列表中选择可安装应用的最低操作系统版本。 如果将应用分配到具有较低操作系统的设备，则不会安装该应用。
    - **类别**（可选）- 选择一个或多个内置应用类别或你创建的类别。 这可让用户在浏览公司门户时更轻松地查找应用。
    - **在公司门户中将此应用显示为特色应用** - 当用户浏览应用时，在公司门户的主页上突出显示此应用。
    - **信息 URL** -（可选）输入包含此应用相关信息的网站 URL。 将在公司门户中向用户显示该 URL。
    - **隐私 URL** -（可选）输入包含此应用相关隐私信息的网站 URL。 将在公司门户中向用户显示该 URL。
    - **开发者** -（可选）输入应用开发者的名称。
    - **所有者** -（可选）输入此应用的所有者的名称，例如，**HR 部门**。
    - **说明** - 输入要与此应用关联的任何备注。
    - **上传图标** - 上传将与应用关联的图标。 用户浏览公司门户时，此图标将与应用一同显示。
2. 完成后，在“添加应用”边栏选项卡上，选择“保存”。

创建的应用将显示在应用列表中，可在该列表中将其分配到所选择的组。 如需帮助，请参阅[如何将应用分配到组](/intune-azure/manage-apps/deploy-apps)。
