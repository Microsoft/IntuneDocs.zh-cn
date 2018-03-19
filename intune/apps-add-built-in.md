---
title: "使用 Microsoft Intune 将内置应用添加到移动设备"
titlesuffix: 
description: "了解如何使用 Intune 更轻松地在移动设备上安装内置应用。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0ec8de66-5a0f-4c8d-afbf-c2becc7d6eec
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7d90f86babc2f73acd5ccd1b454c636c6d4f79b2
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-built-in-apps-to-microsoft-intune"></a>如何将内置应用添加到 Microsoft Intune

通过使用内置的应用类型，可以轻松地将特选的托管应用（例如 Office 365 应用）分配给 iOS 和 Android 设备。 可以为此应用类型分配特定的应用，例如 Excel、OneDrive、Outlook、Skype 等。 添加应用后，可以将应用类型视为“内置 iOS 应用”或“内置 Android 应用”。 通过使用内置应用类型，可以选择将其中哪些特定应用发布给设备用户。

 在早期版本的 Intune 控制台中，Intune 提供了几个默认的托管 Office 365 应用，如 Outlook 和 OneDrive。 这些托管应用的应用类型被标记为“托管 iOS 应用商店应用”或“托管 Android 应用”。 建议使用内置应用类型，而不是“托管 iOS 应用商店”或“托管 Android 应用”。 内置应用类型在编辑和删除 office 365 应用方面提供更多灵活性。

>[!NOTE]
>删除所有分配时，也会从应用列表中删除被标记为“托管 iOS 应用商店”和“托管 Android 应用”的默认 Office 365 应用。

## <a name="add-built-in-app"></a>添加内置应用

通过以下步骤可以将内置应用添加到 Microsoft Intune 中的可用应用中。
1.  登录 Azure 门户。
2.  选择“更多服务” > “监视 + 管理” > “Intune”，以显示 Microsoft Intune 边栏选项卡。
3.  在 Intune 边栏选项卡上，选择“移动应用”。
4.  在“移动应用”边栏选项卡上，选择“管理”组中的“应用”。
5.  选择“添加”，添加新的应用。
6.  在“添加”应用边栏选项卡上，从“应用类型”列表中选择“内置应用”。
7.  单击“选择应用”，选择要包含的内置应用。
8.  在“内置”应用边栏选项卡上，选择要包含的应用。
9.  在“添加应用”边栏选项卡上，单击“添加”以包含应用。


## <a name="configure-app-information"></a>配置应用信息

可以修改有关内置应用的信息。 此信息有助于在 Intune 中识别应用，也有助于用户在公司门户应用中找到该应用。
1.  在“移动应用 - 应用”边栏选项卡上，选择想要修改的内置应用。 随即显示该内置应用的边栏选项卡。
2.  从“管理”组中选择“属性”选项。
3.  选择“配置”选项，修改该内置应用的信息。
4.  在“应用信息”边栏选项卡上可以修改以下信息：
    -   **名称** - 输入内置应用的名称，该名称将显示在公司门户中。 请确保使用的所有名称都是唯一的。 如果同一应用名称存在两次，则在公司门户中将仅向用户显示其中一个应用。
    -   **描述** — 为应用输入描述。 
    -   **发行者** — 输入应用的发行者名称。
    -   **类别** —（可选）选择一个或多个内置应用类别。 设置此选项可让用户在浏览公司门户时更轻松地查找应用。
    -   **在公司门户中将此应用显示为特色应用** - 当用户浏览应用时，在公司门户的主页上突出显示此应用。
    -   **信息 URL** -（可选）输入包含此应用相关信息的网站 URL。 在公司门户中向用户显示该 URL。
    -   **隐私 URL** -（可选）输入包含此应用相关隐私信息的网站 URL。 在公司门户中向用户显示该 URL。
    -   **开发者** -（可选）输入应用开发者的名称。
    -   **所有者** -（可选）输入此应用的所有者的名称，例如，HR 部门。
    -   **说明** - 输入要与此应用关联的任何备注。
    -   **上传图标** - 用户浏览公司门户时，上传与应用一同显示的图标。
3.  完成后，单击“应用信息”边栏选项卡上的“确定”。
4.  单击“属性”边栏选项卡上的“保存”。

## <a name="next-steps"></a>后续步骤

- 现在，可将应用分配到所选组。 如需帮助，请参阅[如何将应用分配到组](apps-deploy.md)。
