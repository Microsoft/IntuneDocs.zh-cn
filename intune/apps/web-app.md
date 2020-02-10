---
title: 将 Web 应用添加到 Microsoft Intune
titleSuffix: ''
description: 了解如何将 Web 应用（客户端服务器应用程序）添加到 Microsoft Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 90cdff66d32ac5edb3b1867a545f2c9627ccfe39
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754773"
---
# <a name="add-web-apps-to-microsoft-intune"></a>将 Web 应用添加到 Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune 支持包括 Web 应用在内的各种应用类型。 Web 应用是客户端-服务器应用程序。 服务器提供 Web 应用，其中包括 UI、内容和功能。 此外，新式 Web 托管平台通常会提供安全性、负载均衡和其他优势。 Web 应用是单独在 Web 上进行维护的。 可以使用 Microsoft Intune 指向此应用类型。 还可分配可以访问此应用的用户组。 

必须先向 Intune 添加应用，然后才能为用户管理和分配此应用。 

Intune 在用户的设备上创建一个转至 Web 应用的快捷方式。 对于 iOS 设备，转至 Web 应用的快捷方式将添加到主屏幕。 对于 Android 设备管理设备，转至 Web 应用的快捷方式将添加到 Intune 公司门户小组件，用户必须手动固定该小组件。 对于 Windows 设备，转至 Web 应用的快捷方式将放置在“开始”菜单上。

> [!Note]
> 若要启动 Web 应用，必须在用户的设备上安装浏览器。 

> [!Note]
> 对于 Android Enterprise 设备，请参阅[托管的 Google Play Web 链接](apps-add-android-for-work.md#managed-google-play-web-links)

## <a name="add-a-web-app-to-intune"></a>将 Web 应用添加到 Intune
若要在 Intune 中将应用添加为 Web 应用的快捷方式，请执行以下步骤：

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“应用”   > “所有应用”   > “添加”  。
3. 在“选择应用类型”  窗格中的可用“其他”  类型下，选择“Web 链接”  。
4. 单击“选择”  。 将显示“添加应用”  步骤。
5. 在“应用信息”页上，添加以下信息  ：
    - **名称**：输入要在公司门户中显示的应用名称。 

        > [!NOTE]
        > 如果在部署并安装应用后通过 Intune Azure 门户更改应用的名称，则将无法再使用命令来定位应用。

    - **描述**：输入应用的描述。 在公司门户中向用户显示该描述。
    - **发布者**：输入此应用发布者的名称。
    - **应用 URL**：输入托管要分配的应用的网站 URL。
    - **类别**：（可选）选择一个或多个内置应用类别或所创建的类别。 此操作可让用户在浏览公司门户时更轻松地查找应用。
    - **在公司门户中将此应用显示为特色应用**：当用户浏览应用时，选择此选项以在公司门户的主页上突出显示应用套件。
    - **需要 Managed Browser 才能打开此链接**：选择此选项，向你的用户分配能在 Intune Managed Browser 中打开网站或 Web 应用的链接。 必须在用户的设备上安装此浏览器。
    - **徽标**：上载将与应用关联的图标。 用户浏览公司门户时，此图标将与应用一同显示。
6. 单击“下一步”  以显示“作用域标记”  页面。
7. 单击“选择作用域标记”  可以选择为应用添加作用域标记。 有关详细信息，请参阅[对分布式 IT 使用基于角色的访问控制 (RBAC) 和作用域标记](~/fundamentals/scope-tags.md)。
8. 单击“下一步”以显示“分配”页面   。
9. 为应用选择组分配。 有关详细信息，请参阅[添加用于组织用户和设备的组](~/fundamentals/groups-add.md)。 
10. 单击“下一步”  以显示“查看 + 创建”页  。 查看为应用输入的值和设置。
11. 完成后，单击“创建”  将应用添加到 Intune。

    随即显示创建的应用的“概述”  边栏选项卡。

> [!Note]
> 目前，将 Intune Web 应用部署到 iOS 设备的操作与管理配置文件相关联，无法手动删除。 可以在 Intune 门户中将部署类型更改为“卸载”  ，此时可以自动删除 Web 应用。 但是，如果在将应用分配意图更改为“卸载”  之前删除部署，Web 应用将永久保留在设备上，直到设备从 Intune 取消注册。

最终用户可以通过选择 Web 应用，然后选择“在浏览器中打开”  ，直接从 Windows 公司门户应用启动 Web 应用。 已发布的 Web URL 直接在 Web 浏览器中打开。 

## <a name="next-steps"></a>后续步骤

此时，已创建的应用显示在应用列表中，可在此列表中将其分配到选择的组。 如需帮助，请参阅[将应用分配到组](apps-deploy.md)。 
