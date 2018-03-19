---
title: "如何将 Web 应用添加到 Microsoft Intune"
titleSuffix: 
description: "了解如何将 Web 应用添加到 Microsoft Intune。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ecb44f8b98501f6c82f91994cd8a06b8177208d7
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-web-apps-to-microsoft-intune"></a>如何将 Web 应用添加到 Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune 支持包括 Web 应用在内的各种应用类型。 Web 应用是客户端-服务器应用程序。 服务器提供 Web 应用，其中包括 UI、内容和功能。 此外，新式 Web 托管平台通常会提供安全性、负载均衡和其他优势。 Web 应用是单独在 Web 上进行维护的。 可以使用 Microsoft Intune 指向此应用类型。 还可以分配哪组用户可以访问此应用。 

必须先向 Intune 添加应用，然后才能为用户管理和分配此应用。 Intune 在用户的设备主屏幕上创建一个转至 Web 应用的快捷方式。

> [!Note]
> Android for Work 设备和 macOS 上不支持 Web 应用。

若要在 Intune 中将应用添加为 Web 应用的快捷方式，请完成以下步骤：

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 在“Microsoft Intune”窗格上，选择“移动应用”。
4. 在“移动应用”窗格上，选择“应用”。
5. 在应用列表上方，选择“添加”。 随即将显示“添加应用”窗格。
6. 在“添加应用”窗格中，从“应用类型”下拉列表中选择“Web 链接”类型。
7. 选择“配置”选项以显示“应用信息”窗格。
8. 在“应用信息”窗格中，添加以下信息：
    - **名称** - 输入要在“公司门户”中显示的应用名称。
    - **描述** — 为应用输入描述。 这就是在“公司门户”中向最终用户显示的名称。
    - **发行者** - 输入应用的发行者名称。
    - **应用 URL** - 输入可托管要分配的应用的网站 URL。
    - **类别（可选）**- 选择一个或多个内置应用类别或你创建的类别。 此选择可方便用户在浏览“公司门户”时更轻松地查找应用。
    - **在公司门户中将此应用显示为特色应用** - 当用户浏览应用时，在公司门户的主页上突出显示此应用。
    - **需要托管浏览器才能打开此链接** - 用户只能在 Intune 托管浏览器中打开向其分配的网站或 Web 应用链接。 必须在用户的设备上安装此浏览器。
    - **徽标**- 上传与应用关联的徽标。 这就是在用户浏览“公司门户”时与应用一同显示的徽标。
9. 完成后，在“添加信息”窗格上选择“确定”。
10. 然后，从“添加应用”窗格中选择“添加”。

> [!Note]
> 用户需要将 Intune 小组件添加到他们的主屏幕，显示已分配到 Android 设备的 Web 应用。

## <a name="next-steps"></a>后续步骤

- 此时，已创建的应用显示在应用列表中，可供分配到选定组。 如需帮助，请参阅[如何将应用分配到组](apps-deploy.md)。