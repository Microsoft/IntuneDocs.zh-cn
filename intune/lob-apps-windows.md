---
title: 将 Windows 业务线应用添加到 Microsoft Intune
titlesuffix: ''
description: 了解如何使用 Microsoft Intune 添加 Windows 业务线 (LOB) 应用。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 96b1bc23189faaad8aa8dd279352ef74c0b36e4b
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55845425"
---
# <a name="add-a-windows-line-of-business-app-to-microsoft-intune"></a>将 Windows 业务线应用添加到 Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

业务线 (LOB) 应用是从应用安装文件添加的应用。 此类应用通常在内部编写。 以下步骤提供指导，以帮助将 Windows LOB 应用添加到 Microsoft Intune。

## <a name="step-1-specify-the-software-setup-file"></a>步骤 1：指定软件安装程序文件

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 在“Intune”窗格中，选择“客户端应用”。
4. 在“客户端应用”工作负载中，选择“管理” > “应用”。
5. 在应用列表上方，选择“添加”。
6. 在“添加应用”窗格中，选择“业务线应用”。

## <a name="step-2-configure-the-app-package-file"></a>步骤 2：配置应用包文件

1. 在“添加应用”窗格中，选择“应用包文件”。
2. 在“应用包文件”窗格中，选择“浏览”按钮。 然后选择带扩展名“.msi”、“.appx”，或“.appxbundle”的 Windows 安装文件。

    > [!NOTE]
    > Windows 应用的文件扩展名包括 .msi、.appx、.appxbundle、.msix 和 .msixbundle。  

1. 完成后，选择“确定”。


## <a name="step-3-configure-app-information"></a>步骤 3：配置应用信息

1. 在“添加应用”窗格中，选择“应用信息”。
2. 在“应用信息”窗格中，配置以下信息。 此窗格中的某些值可能已自动填充。
    - **名称**：输入显示在公司门户中的应用的名称。 请确保使用的所有应用名称都是唯一的。 如果同一应用名称存在两次，则公司门户中仅显示其中一个应用。
    - **说明**：输入应用的描述。 描述显示在公司门户中。
    - **发布者**：输入应用发布者的名称。
    - **忽略应用版本**：如果应用开发人员自动更新应用，则设置为“是”。 此选项仅适用于移动 .msi 应用。
    - **类别**：选择一个或多个内置应用类别，或选择你创建的类别。 “类别”可让用户在浏览公司门户时更轻松地查找应用。
    - **在公司门户中将此应用显示为特色应用**：当用户浏览应用时，在公司门户的主页上突出显示应用。
    - **信息 URL**：（可选）输入包含此应用相关信息的网站的 URL。 此 URL 显示在公司门户中。
    - **隐私 URL**：（可选）输入包含此应用相关隐私信息的网站的 URL。 此 URL 显示在公司门户中。
    - **命令行参数**：（可选）输入要在 .msi 文件运行时应用到该文件的任意命令行参数。 例如 /q。
    - **开发者**：（可选）输入应用开发者的名称。
    - **所有者**：（可选）输入此应用的所有者的名称。 例如，“HR 部门”。
    - **备注**：输入想与此应用关联的任何备注。
    - **徽标**：上传与应用关联的图标。 用户浏览公司门户时，该图标将与应用一同显示。
3. 完成后，选择“确定”。

## <a name="step-4-finish-up"></a>步骤 4：完成

1. 在“添加应用”窗格中，验证是否已正确配置应用信息。
2. 选择“添加”将应用上传到 Intune。

## <a name="step-5-update-a-line-of-business-app"></a>步骤 5：更新业务线应用

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

## <a name="configure-a-self-updating-mobile-msi-app-to-ignore-the-version-check-process"></a>配置自我更新的移动 MSI 应用以忽略版本检查过程

可以配置已知的自我更新移动 MSI 应用以忽略版本检查过程。 

某些基于 MSI 安装程序的应用会由应用开发者自动更新。 对于这些自动更新的 MSI 应用，可以在“应用信息”窗格中配置“忽略应用版本”设置。 当此设置切换为“是”时，Microsoft Intune 将不会强制执行在 Windows 客户端上安装的应用版本。 

此功能有助于避免出现争用条件。 例如，当应用开发者自动更新应用并通过 Intune 更新时，就会出现争用条件。 两者都可能在 Windows 客户端上尝试强制执行一个应用版本，进而引发冲突。

## <a name="next-steps"></a>后续步骤

- 你创建的应用显示在应用列表中。 现在，可将其分配到所选组。 如需帮助，请参阅[如何将应用分配到组](apps-deploy.md)。

- 详细了解可用于监视应用的属性和分配的方法。 请参阅[如何监视应用信息和分配](apps-monitor.md)。

- 详细了解 Intune 中应用的上下文。 请参阅[设备和应用生命周期概述](introduction-device-app-lifecycles.md)。
