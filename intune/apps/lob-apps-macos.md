---
title: 如何将 iOS 业务线应用添加到 Microsoft Intune
titleSuffix: ''
description: 了解如何将 macOS 业务线 (LOB) 应用添加到 Microsoft Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ef8008ac-8b85-4bfc-86ac-1f9fcbd3db76
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c7aa6af751e5ab3e1e3cdff6b1d2e3d6693f65df
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755164"
---
# <a name="how-to-add-macos-line-of-business-lob-apps-to-microsoft-intune"></a>如何将 macOS 业务线 (LOB) 应用添加到 Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

本文中提供的信息可帮助你将 macOS 业务线应用添加到 Microsoft Intune。 必须先下载一个外部工具来预处理 .pkg  文件，然后才能将业务线文件上载到 Microsoft Intune。 .pkg  文件的预处理必须在 macOS 设备上进行。

> [!NOTE]
> 从 macOS Catalina 10.15 发布开始，在将应用添加到 Intune 之前，请检查以确保 macOS LOB 应用已经过公证。 如果 LOB 应用的开发人员未公证其应用，应用将无法在用户的 macOS 设备上运行。 有关如何检查应用是否已公证的详细信息，请访问[公证 macOS 应用以便为 macOS Catalina 做准备](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Notarizing-your-macOS-apps-to-prepare-for-macOS/ba-p/808579)。

> [!NOTE]
> 尽管 macOS 设备用户可删除部分内置 macOS 应用（如“股市”和“地图”），但无法使用 Intune 重新部署这些应用。 如果最终用户删除这些应用，则必须前往 App Store，并手动重新安装它们。

## <a name="before-your-start"></a>准备工作

必须先下载外部工具，将下载的工具标记为可执行文件，并使用此工具预处理 .pkg  文件，然后才能将业务线文件上传到 Microsoft Intune。 .pkg  文件的预处理必须在 macOS 设备上进行。 使用 Intune App Wrapping Tool for Mac，可以让 Microsoft Intune 管理 Mac 应用。

> [!IMPORTANT]
> 必须使用从 Apple 开发人员帐户获取的“开发人员 ID 安装程序”证书对 .pkg  文件进行签名。 仅  .pkg 文件可用于将 macOS LOB 应用上传到 Microsoft Intune。 不支持转换其他格式（例如从 .dmg 转换到 .pkg）   。
>

1. 下载 [Intune App Wrapping Tool for Mac](https://github.com/msintuneappsdk/intune-app-wrapping-tool-mac)。

    > [!NOTE]
    > Intune App Wrapping Tool for Mac  必须在 macOS 计算机上运行。 

2. 将下载的工具标记为可执行文件：
   - 启动终端应用。
   - 将目录更改为 `IntuneAppUtil` 所在的位置。
   - 运行以下命令以使工具成为可执行文件：<br> 
       `chmod +x IntuneAppUtil`

3. 使用 Intune App Wrapping Tool for Mac 内的 `IntuneAppUtil` 命令  ，从 .intunemac 文件中包装  .pkg LOB 应用文件  。<br>

    用于 Microsoft Intune App Wrapping Tool for macOS 的简单命令：
    > [!IMPORTANT]
    > 在运行 `IntuneAppUtil` 命令之前，请确保参数 `<source_file>` 不包含空格。

    - `IntuneAppUtil -h`<br>
    该命令将显示工具的使用信息。
    
    - `IntuneAppUtil -c <source_file> -o <output_file> [-v]`<br>
    该命令将 .pkg  LOB 应用文件包装为  .intunemac 文件。
    
    - `IntuneAppUtil -r <filename.intunemac> [-v]`<br>
    该命令将为创建的 .intunemac  文件提取检测到的参数和版本。

## <a name="select-the-app-type"></a>选择应用类型

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“应用”   > “所有应用”   > “添加”  。
3. 在“选择应用类型”  窗格中的“其他”  应用类型下，选择“业务线应用”  。
4. 单击“选择”  。 将显示“添加应用”  步骤。

## <a name="step-1---app-information"></a>步骤 1 - 应用信息

### <a name="select-the-app-package-file"></a>选择应用包文件

1. 在“添加应用”  窗格中，单击“选择应用包文件”  。 
2. 在“应用包文件”  窗格中，选择“浏览”按钮。 然后选择扩展名为 .intunemac 的 macOS 安装文件  。
   将显示应用详细信息。
3. 完成后，在“应用包文件”  窗格中选择“确定”  以添加应用。

### <a name="set-app-information"></a>设置应用信息

1. 在“应用信息”  页中，添加应用的详细信息。 此窗格中的某些值可能已自动填充，具体取决于所选应用。
    - **名称**：输入显示在公司门户中的应用的名称。 请确保使用的所有应用名称都是唯一的。 如果同一应用名称存在两次，则公司门户中仅显示其中一个应用。
    - **描述**：输入应用的说明。 描述显示在公司门户中。
    - **发布者**：输入应用发布者的名称。
    - **最低操作系统**：从列表中选择可安装应用的最低操作系统版本。 如果将应用分配到具有较低操作系统的设备，则不会安装该应用。
    - **类别**：选择一个或多个内置应用类别，或选择你创建的类别。 “类别”可让用户在浏览公司门户时更轻松地查找应用。
    - **在公司门户中将此应用显示为特色应用**：当用户浏览应用时，在公司门户的主页上突出显示应用。
    - **信息 URL**：（可选）输入包含此应用相关信息的网站的 URL。 此 URL 显示在公司门户中。
    - **隐私 URL**：（可选）输入包含此应用相关隐私信息的网站的 URL。 此 URL 显示在公司门户中。
    - **开发者**：（可选）输入应用开发者的名称。
    - **所有者**：（可选）输入此应用的所有者的名称。 例如，“HR 部门”  。
    - **备注**：输入想与此应用关联的任何备注。
    - **徽标**：上传与应用关联的图标。 用户浏览公司门户时，此图标将与应用一同显示。
2. 单击“下一步”  以显示“作用域标记”  页面。

## <a name="step-2---select-scope-tags-optional"></a>步骤 2 - 选择作用域标记（可选）
可以使用作用域标记来确定谁可以在 Intune 中查看客户端应用信息。 若要详细了解作用域标记，请参阅[将基于角色的访问控制和作用域标记用于分布式 IT](../fundamentals/scope-tags.md)。

1. 单击“选择作用域标记”  可以选择为应用添加作用域标记。 
2. 单击“下一步”以显示“分配”页面   。

## <a name="step-3---assignments"></a>步骤 3 - 分配

1. 为应用选择“必需”  、“适用于已注册的设备”  或“卸载”  组分配。 有关详细信息，请参阅[添加用于组织用户和设备的组](~/fundamentals/groups-add.md)和[使用 Microsoft Intune 将应用分配到组](apps-deploy.md)。
2. 单击“下一步”  以显示“查看 + 创建”页  。 

## <a name="step-4---review--create"></a>步骤 4 - 查看 + 创建

1. 查看为应用输入的值和设置。
2. 完成后，单击“创建”  将应用添加到 Intune。

    将显示业务线应用的“概述”  边栏选项卡。

创建的应用显示在应用列表中，可在该列表中将其分配到选择的组。 如需帮助，请参阅[如何将应用分配到组](apps-deploy.md)。

> [!NOTE]
> 如果 .pkg  文件包含多个应用或应用安装程序，则 Microsoft Intune 将仅在设备上检测到所有安装的应用后  报告应用已成功安装。

## <a name="update-a-line-of-business-app"></a>更新业务线应用

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

> [!NOTE]
> 为了让 Intune 服务成功地将新的 .pkg  文件部署到设备上，必须在 .pkg 包的 packageinfo 文件中递增包的 `version` 和 `CFBundleVersion` 字符串   。

## <a name="next-steps"></a>后续步骤

- 创建的应用将显示在应用列表中。 现在，可将其分配到所选组。 如需帮助，请参阅[如何将应用分配到组](apps-deploy.md)。

- 详细了解可用于监视应用的属性和分配的方法。 有关详细信息，请参阅[如何监视应用信息和分配](apps-monitor.md)。

- 详细了解 Intune 中应用的上下文。 有关详细信息，请参阅[设备和应用生命周期概述](../fundamentals/device-lifecycle.md)
