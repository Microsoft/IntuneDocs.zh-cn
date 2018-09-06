---
title: 将 Web 应用添加到 Microsoft Intune
titleSuffix: ''
description: 了解如何将 Web 应用添加到 Microsoft Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 26117a07e0769033dda573882c3853eb0e3921ff
ms.sourcegitcommit: 0ac196d1d06f4f52f01610eb26060419d248168b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2018
ms.locfileid: "40251593"
---
# <a name="add-web-apps-to-microsoft-intune"></a>将 Web 应用添加到 Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 支持包括 Web 应用在内的各种应用类型。 Web 应用是客户端-服务器应用程序。 服务器提供 Web 应用，其中包括 UI、内容和功能。 此外，新式 Web 托管平台通常会提供安全性、负载均衡和其他优势。 Web 应用是单独在 Web 上进行维护的。 可以使用 Microsoft Intune 指向此应用类型。 还可分配可以访问此应用的用户组。 

必须先向 Intune 添加应用，然后才能为用户管理和分配此应用。 Intune 在用户的设备主屏幕上创建一个转至 Web 应用的快捷方式。

> [!Note]
> Android 工作配置文件设备和 macOS 上不支持 Web 应用。

## <a name="add-a-web-app-to-intune"></a>将 Web 应用添加到 Intune
若要在 Intune 中将应用添加为 Web 应用的快捷方式，请执行以下步骤：

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。  
    Intune 位于“监视 + 管理”部分中。
3. 在“Intune”窗格中，选择“移动应用”。
4. 在“移动应用”工作负载窗格的“管理”下，选择“应用”。
5. 在“应用”窗格中，选择“添加”。
6. 在“添加应用”窗格的“应用类型”下拉列表中选择“Web 链接”类型。
7. 选择“配置”。
8. 在“应用信息”窗格中，添加以下信息：
    - 名称 - 输入要在公司门户中显示的应用名称。 
    
        > [!NOTE]
        > 如果在部署并安装应用后通过 Intune Azure 门户更改应用的名称，则将无法再使用命令来定位应用。
    
    - 描述：为应用输入描述。 在公司门户中向用户显示该描述。
    - **发布者**：输入应用的发布者名称。
    - **应用 URL**：输入托管要分配的应用的网站 URL。
    - **类别**（可选）：选择一个或多个内置应用类别或你创建的类别。 此操作可让用户在浏览公司门户时更轻松地查找应用。
    - 在“公司门户”中将此显示为特别推荐的应用：选择此选项可在用户浏览应用时，在“公司门户”的主页上突出显示应用套件。
    - **需要 Managed Browser 才能打开此链接**：选择此选项，向你的用户分配能在 Intune Managed Browser 中打开网站或 Web 应用的链接。 必须在用户的设备上安装此浏览器。
    - **徽标**：上传将与应用关联的图标。 用户浏览公司门户时，此图标将与应用一同显示。
9. 选择“确定”。
10. 在“添加应用”窗格中，选择“添加”。

> [!Note]
> 用户必须将 Intune 小组件添加到他们的主屏幕，显示已分配到 Android 设备的 Web 应用。

## <a name="next-steps"></a>后续步骤

此时，已创建的应用显示在应用列表中，可在此列表中将其分配到选择的组。 如需帮助，请参阅[将应用分配到组](apps-deploy.md)。 
