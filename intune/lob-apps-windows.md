---
title: "如何将 Windows 业务线应用添加到 Intune"
titlesuffix: Azure portal
description: "了解如何将 Windows 业务线应用添加到 Intune。"
keywords: 
author: Erikre
ms.author: erikre
manager: angrobe
ms.date: 10/3/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 256cf22c0a1d061b76c9f7d93a8472e3579d496a
ms.sourcegitcommit: 833b1921ced35be140f0107d0b4205ecacd2753b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2018
---
# <a name="how-to-add-windows-line-of-business-lob-apps-to-microsoft-intune"></a>如何将 Windows 业务线 (LOB) 应用添加到 Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


## <a name="step-1---specify-the-software-setup-file"></a>步骤 1 - 指定软件安装程序文件

1. 登录到 Azure 门户。
2. 选择“更多服务” > “监视 + 管理” + “Intune”。
3. 在“Intune”边栏选项卡上，选择“管理应用”。
4. 在“移动应用”工作负荷中，选择“管理” > “应用”。
5. 在应用列表的上方，选择“添加”。
6. 在“添加应用”边栏选项卡中，选择“业务线应用”。

## <a name="step-2---configure-the-app-package-file"></a>步骤 2 - 配置应用包文件

1. 在“添加应用”边栏选项卡上，选择“应用包”文件。
2. 在“应用包”文件边栏选项卡，选择浏览按钮，然后选择扩展名为 .msi、.appx 或 .appxbundle 的 Windows 安装文件。
3. 完成后，请选择“确定”。


## <a name="step-3---configure-app-information"></a>步骤 3 - 配置应用信息

1. 在“添加应用”边栏选项卡上，选择“应用包”文件。
2. 在“应用信息”边栏选项卡，配置下列信息（此边栏选项卡中的某些值可能会自动填充）：
    - 名称 - 输入应用的名称，该名称将显示在公司门户中。 请确保使用的所有应用名称都是唯一的。 如果同一应用名称存在两次，则在公司门户中将仅向用户显示其中一个应用。
    - **描述** — 为应用输入描述。 在公司门户中向用户显示该描述。
    - **发行者** — 输入应用的发行者名称。
    - **类别** - 选择一个或多个内置应用类别或你创建的类别。 对应用分类可让用户在浏览公司门户时更轻松地查找应用。
    - **在公司门户中将此应用显示为特色应用** - 当用户浏览应用时，在公司门户的主页上突出显示此应用。
    - 信息 URL -（可选）输入包含此应用相关信息的网站 URL。 在公司门户中向用户显示该 URL。
    - 隐私 URL -（可选）输入包含此应用相关隐私信息的网站 URL。 在公司门户中向用户显示该 URL。
    - 命令行参数 -（可选）输入要在 .msi 文件运行时应用到该文件的任意命令行参数，例如 /q。
    - **开发者** -（可选）输入应用开发者的名称。
    - **所有者** -（可选）输入此应用的所有者的名称，例如，**HR 部门**。
    - **说明** - 输入要与此应用关联的任何备注。
    - 徽标 - 上传与应用关联的图标。 用户浏览公司门户时，此图标将与应用一同显示。
3. 完成后，请选择“确定”。

## <a name="step-4---finish-up"></a>步骤 4 - 完成

1. 在“添加应用”边栏选项卡上，验证配置的应用信息是否正确。
2. 选择“添加”将应用上传到 Intune。

## <a name="step-5---update-a-line-of-business-app"></a>步骤 5 - 更新业务线应用

[!INCLUDE[shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

## <a name="next-steps"></a>后续步骤

创建的应用将显示在应用列表中。 现在，可将其分配到所选组。 如需帮助，请参阅[如何将应用分配到组](apps-deploy.md)。

详细了解可用于监视应用的属性和分配的方法。 有关详细信息，请参阅[如何监视应用信息和分配](apps-monitor.md)。

详细了解 Intune 中应用的上下文。 有关详细信息，请参阅[设备和应用生命周期概述](introduction-device-app-lifecycles.md)