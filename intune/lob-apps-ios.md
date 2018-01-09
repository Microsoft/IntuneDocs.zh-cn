---
title: "如何将 iOS 业务线应用添加到 Intune"
titlesuffix: Azure portal
description: "了解如何将 iOS 业务线应用添加到 Intune。"
keywords: 
author: Erikre
ms.author: erikre
manager: angrobe
ms.date: 10/3/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 099101e8-4b22-40ac-ba19-82ba5c71944c
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 20a044ea6b517279a2546f62d05cc79e09dcdc5f
ms.sourcegitcommit: 833b1921ced35be140f0107d0b4205ecacd2753b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2018
---
# <a name="how-to-add-ios-line-of-business-lob-apps-to-microsoft-intune"></a>如何将 iOS 业务线 (LOB) 应用添加到 Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

本主题提供的信息有助于向 Intune 添加 iOS 业务线应用。

>[!NOTE]
>尽管 iOS 设备用户可删除部分内置 iOS 应用（如 Stocks 和地图），但无法使用 Intune 重新部署这些应用。 如果最终用户删除这些应用，则必须前往 App Store，并手动重新安装它们。

## <a name="step-1---specify-the-software-setup-file"></a>步骤 1 - 指定软件安装程序文件

1. 登录到 Azure 门户。
2. 选择“更多服务” > “监视 + 管理” + “Intune”。
3. 在“Intune”边栏选项卡上，选择“管理应用”。
4. 在“移动应用”工作负荷中，选择“管理” > “应用”。
5. 在应用列表的上方，选择“添加”。
6. 在“添加应用”边栏选项卡中，选择“业务线应用”。

## <a name="step-2---configure-the-app-package-file"></a>步骤 2 - 配置应用包文件

1. 在“添加应用”边栏选项卡上，选择“应用包”文件。
2. 在“应用包”文件边栏选项卡，选择浏览按钮，然后选择扩展名为 **.ipa** 的 iOS 安装文件。
3. 完成后，请选择“确定”。


## <a name="step-3---configure-app-information"></a>步骤 3 - 配置应用信息

1. 在“添加应用”边栏选项卡上，选择“应用包”文件。
2. 在“应用信息”边栏选项卡上，添加应用的详细信息。 根据所选择的应用，此边栏选项卡中的某些值可能已自动填充：
    - 名称 - 输入要在公司门户中显示的应用名称。 请确保使用的所有应用名称都是唯一的。 如果同一应用名称存在两次，则在公司门户中将仅向用户显示其中一个应用。
    - 说明 - 输入要在公司门户中向用户显示的应用说明。
    - **发行者** — 输入应用的发行者名称。
    - **最低操作系统** - 从列表中选择可安装应用的最低操作系统版本。 如果将应用分配到具有较低操作系统的设备，则不会安装该应用。
    - **类别** - 选择一个或多个内置应用类别或你创建的类别。 这样，可让用户在浏览公司门户时更轻松地查找应用。
    - **在公司门户中将此应用显示为特色应用** - 当用户浏览应用时，在公司门户的主页上突出显示此应用。
    - **信息 URL** -（可选）输入包含此应用相关信息的网站 URL。 在公司门户中向用户显示该 URL。
    - **隐私 URL** -（可选）输入包含此应用相关隐私信息的网站 URL。 在公司门户中向用户显示该 URL。
    - **开发者** -（可选）输入应用开发者的名称。
    - **所有者** -（可选）输入此应用的所有者的名称，例如，**HR 部门**。
    - **说明** - 输入要与此应用关联的任何备注。
    - 徽标 - 上传与应用关联的图标。 用户浏览公司门户时，此图标与应用一同显示。
3. 完成后，请选择“确定”。

## <a name="step-4---finish-up"></a>步骤 4 - 完成

1. 在“添加应用”边栏选项卡上，确认应用的详细信息正确。
2. 选择“添加”将应用上传到 Intune。

创建的应用显示在应用列表中，可在该列表中将其分配到选择的组。 如需帮助，请参阅[如何将应用分配到组](apps-deploy.md)。

## <a name="step-5---update-a-line-of-business-app"></a>步骤 5 - 更新业务线应用

[!INCLUDE[shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]注意：为了让 Intune 服务成功地将新的 IPA 文件部署到设备上，你必须在 IPA 包的 Info.plist 文件中递增 CFBundleVersion 字符串。

## <a name="next-steps"></a>后续步骤

创建的应用将显示在应用列表中。 现在，可将其分配到所选组。 如需帮助，请参阅[如何将应用分配到组](apps-deploy.md)。

详细了解可用于监视应用的属性和分配的方法。 有关详细信息，请参阅[如何监视应用信息和分配](apps-monitor.md)。

详细了解 Intune 中应用的上下文。 有关详细信息，请参阅[设备和应用生命周期概述](introduction-device-app-lifecycles.md)
