---
title: 如何将 iOS 业务线应用添加到 Microsoft Intune
titlesuffix: ''
description: 了解如何将 macOS 业务线 (LOB) 应用添加到 Microsoft Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ef8008ac-8b85-4bfc-86ac-1f9fcbd3db76
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dbd4be551365c1dd65aea8e9270df5f6b6263f89
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-add-macos-line-of-business-lob-apps-to-microsoft-intune"></a>如何将 macOS 业务线 (LOB) 应用添加到 Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文中提供的信息可帮助你将 macOS 业务线应用添加到 Microsoft Intune。 必须先下载一个外部工具来预处理 .pkg 文件，然后才能将业务线文件上载到 Microsoft Intune。 .pkg 文件的预处理必须在 macOS 设备上进行。

>[!NOTE]
>尽管 macOS 设备用户可删除部分内置 macOS 应用（如“股市”和“地图”），但无法使用 Intune 重新部署这些应用。 如果最终用户删除这些应用，则必须前往 App Store，并手动重新安装它们。
>
>仅 .pkg 文件可用于将 macOS LOB 应用上传到 Microsoft Intune。 

## <a name="step-1---pre-process-your-software-setup-file"></a>第 1 步 - 预处理软件安装程序文件

使用 Intune App Wrapping Tool for Mac，可以让 Microsoft Intune 管理 Mac 应用。

1. 下载并运行 [Intune App Wrapping Tool for Mac](https://github.com/msintuneappsdk/intune-app-wrapping-tool-mac)。

    > [!NOTE]
    > Intune App Wrapping Tool for Mac 必须在 macOS 计算机上运行。

2. 使用 Intune App Wrapping Tool for Mac 内的 `IntuneAppUtil` 命令，从 .intunemac 文件中包装 .pkg LOB 应用文件。<br>

    用于 Microsoft Intune App Wrapping Tool for macOS 的简单命令：
    
    - `IntuneAppUtil -h`<br>
    该命令将显示工具的使用信息。
    
    - `IntuneAppUtil -c <source_file> -o <output_file> [-v]`<br>
    该命令将 .pkg  LOB 应用文件包装为 .intunemac 文件。
    
    - `IntuneAppUtil -r <filename.intunemac> [-v]`<br>
    该命令将为创建的 .intunemac 文件提取检测到的参数和版本。

## <a name="step-2---specify-the-software-setup-file"></a>第 2 步 - 指定软件安装程序文件

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 在“Intune”窗格中，选择“移动应用”。
4. 在“移动应用”工作负荷中，选择“管理” > “应用”。
5. 在应用列表的上方，选择“添加”。
6. 在“添加应用”窗格中，选择“业务线应用”。

## <a name="step-3---configure-the-app-package-file"></a>第 3 步 - 配置应用包文件

1. 在“添加应用”窗格中，选择“应用包文件”。
2. 在“应用包文件”窗格中，选择“浏览”按钮，然后选择扩展名为 .intunemac 的 macOS 安装文件。
3. 完成后，请选择“确定”。


## <a name="step-4---configure-app-information"></a>第 4 步 - 配置应用信息

1. 在“添加应用”窗格中，选择“应用信息”。
2. 在“应用信息”窗格中，添加应用的详细信息。 此窗格中的某些值可能已自动填充（具体取决于所选应用）：
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

## <a name="step-5---finish-up"></a>第 5 步 - 完成

1. 在“添加应用”窗格上，确认应用的详细信息是正确的。
2. 选择“添加”将应用上传到 Intune。

创建的应用显示在应用列表中，可在该列表中将其分配到选择的组。 如需帮助，请参阅[如何将应用分配到组](apps-deploy.md)。

> [!NOTE]
> 如果 .pkg 文件包含多个应用或应用安装程序，则 Microsoft Intune 将仅在设备上检测到所有安装的应用后报告应用已成功安装。

## <a name="step-6---update-a-line-of-business-app"></a>第 6 步 - 更新业务线应用

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

> [!NOTE]
> 为了让 Intune 服务成功地将新的 .pkg 文件部署到设备上，必须在 .pkg 包的 packageinfo 文件中递增包的 `version` 和 `CFBundleVersion` 字符串。

## <a name="next-steps"></a>后续步骤

- 创建的应用将显示在应用列表中。 现在，可将其分配到所选组。 如需帮助，请参阅[如何将应用分配到组](apps-deploy.md)。

- 详细了解可用于监视应用的属性和分配的方法。 有关详细信息，请参阅[如何监视应用信息和分配](apps-monitor.md)。

- 详细了解 Intune 中应用的上下文。 有关详细信息，请参阅[设备和应用生命周期概述](introduction-device-app-lifecycles.md)
