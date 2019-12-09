---
title: 将 Windows Phone 业务线应用添加到 Microsoft Intune
titleSuffix: ''
description: 了解如何使用 Microsoft Intune 添加 Windows Phone 业务线 (LOB) 应用。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a097b7b2-d01d-454b-954c-da4f3cd0ae86
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dd8025c18ef10580eb16883727bf08a316989d2e
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563531"
---
# <a name="add-a-windows-phone-line-of-business-app-to-microsoft-intune"></a>将 Windows Phone 业务线应用添加到 Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

使用本文中提供的信息将 Windows Phone 业务线 (LOB) 应用添加到 Microsoft Intune。 LOB 应用是从应用安装文件添加到 Intune 的应用。 此类应用通常在内部编写。 Intune 在用户设备上安装 LOB 应用。 

## <a name="step-1-specify-the-software-setup-file"></a>步骤 1：指定软件安装程序文件

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“应用”   > “所有应用”   > “添加”  。
3. 在“添加应用”  窗格中，选择“业务线应用”  作为“应用类型”  。

## <a name="step-2-configure-the-app-package-file"></a>步骤 2：配置应用包文件

1. 在“添加应用”  窗格中，选择“应用包文件”  。
2. 在“应用包文件”  窗格中，选择“浏览”按钮。 然后选择扩展名为 .xap  的 Windows Phone 安装文件。
3. 完成后，选择“确定”  。


## <a name="step-3-configure-app-information"></a>步骤 3：配置应用信息

1. 在“添加应用”  窗格中，选择“应用信息”  。
2. 在“应用信息”  窗格中，配置应用信息。 此窗格中的某些值可能已自动填充，具体取决于所选应用。
    - **名称**：输入显示在公司门户中的应用的名称。 请确保使用的所有应用名称都是唯一的。 如果同一应用名称存在两次，则公司门户中仅显示其中一个应用。
    - **说明**：输入应用的描述。 描述显示在公司门户中。
    - **发布者**：输入应用发布者的名称。
    - **类别**：选择一个或多个内置应用类别，或选择你创建的类别。 “类别”可让用户在浏览公司门户时更轻松地查找应用。
    - **在公司门户中将此应用显示为特色应用**：当用户浏览应用时，在公司门户的主页上突出显示应用。
    - **信息 URL**：（可选）输入包含此应用相关信息的网站的 URL。 此 URL 显示在公司门户中。
    - **隐私 URL**：（可选）输入包含此应用相关隐私信息的网站的 URL。 此 URL 显示在公司门户中。
    - **开发者**：（可选）输入应用开发者的名称。
    - **所有者**：（可选）输入此应用的所有者的名称。 例如，“HR 部门”  。
    - **备注**：输入想与此应用关联的任何备注。
    - **徽标**：上传与应用关联的图标。 用户浏览公司门户时，此图标将与应用一同显示。
3. 完成后，选择“确定”  。

## <a name="step-4-finish-up"></a>步骤 4：完成

1. 在“添加应用”  窗格中，验证是否已正确地配置了信息。
2. 选择“添加”  将应用上传到 Intune。

## <a name="next-steps"></a>后续步骤

- 你创建的应用显示在应用列表中。 现在，可将其分配到所选组。 如需帮助，请参阅[如何将应用分配到组](apps-deploy.md)。

- 详细了解可用于监视应用的属性和分配的方法。 请参阅[如何监视应用信息和分配](apps-monitor.md)。

- 详细了解 Intune 中应用的上下文。 请参阅[设备和应用生命周期概述](../fundamentals/device-lifecycle.md)。
