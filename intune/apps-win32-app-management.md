---
title: 向 Microsoft Intune 添加并分配 Win32 应用
titleSuffix: ''
description: 了解如何通过 Microsoft Intune 添加、分配和管理 Win32 应用。 本主题概述了 Intune Win32 应用交付和管理功能，以及 Win32 应用疑难解答信息。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 06/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: efdc196b-38f3-4678-ae16-cdec4303f8d2
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d8c4813d94a269ed6b8f944585814b54f36fef8c
ms.sourcegitcommit: 6e07c35145f70b008cf170bae57143248a275b67
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66804697"
---
# <a name="intune-standalone---win32-app-management"></a>Intune 独立版 - Win32 应用管理

[Intune 独立版](mdm-authority-set.md)现拥有更强大的 Win32 应用管理功能。 虽然云连接的客户可以使用 Configuration Manager 进行 Win32 应用管理，但只使用 Intune 的客户将拥有更强大的 Win32 业务线 (LOB) 应用管理功能。 本主题概述了 Intune Win32 应用管理功能和疑难解答信息。

> [!NOTE]
> 此应用管理功能支持适用于 Windows 应用程序的 32 位和 64 位操作系统体系结构。

## <a name="prerequisites"></a>必备条件

要使用 Win32 应用管理，请确保满足以下条件：

- Windows 10 版本 1607 或更高版本（企业版、专业版和教育版）
- Windows 10 客户端需要： 
    - 设备必须加入 Azure AD 并进行自动注册。 Intune 管理扩展支持已加入 Azure AD、已加入混合域和已注册组策略的设备。 
    > [!NOTE]
    > 对于已注册组策略的情况，最终用户使用本地用户帐户将 Windows 10 设备加入 AAD。 用户必须使用其 AAD 用户帐户登录设备并注册 Intune。 如果 PowerShell 脚本或 Win32 应用以用户或设备为目标，Intune 将在设备上安装 Intune 管理扩展。
- Windows 应用程序大小的上限为每个应用 8 GB。

## <a name="prepare-the-win32-app-content-for-upload"></a>准备 Win32 应用内容以进行上传

使用 [Microsoft Win32 内容准备工具](https://go.microsoft.com/fwlink/?linkid=2065730)预处理 Windows 经典 (Win32) 应用。 该工具将应用程序安装文件转换为 .intunewin 格式。 该工具还检测 Intune 所需的某些属性，以确定应用程序安装状态。 在应用安装程序文件夹上使用此工具后，你将能够在 Intune 控制台中创建 Win32 应用。

> [!IMPORTANT]
> [Microsoft Win32 内容准备工具](https://go.microsoft.com/fwlink/?linkid=2065730)在创建 .intunewin 文件时压缩所有文件和子文件夹。 确保将 Microsoft Win32 内容准备工具与安装程序文件和文件夹分开，这样就不会在 .intunewin 文件中包含该工具或其他不必要的文件和文件夹。

可从 GitHub 以 zip 文件形式下载 [Microsoft Win32 内容准备工具](https://go.microsoft.com/fwlink/?linkid=2065730)。 压缩文件包含名为 Microsoft-Win32-Content-Prep-Tool-master 的文件夹。 该文件夹包含准备工具、许可证、自述文件和发行说明。 

### <a name="process-flow-to-create-intunewin-file"></a>.intunewin 文件的创建流程

   ![.intunewin 文件的创建流程](./media/prepare-win32-app.svg)

### <a name="run-the-microsoft-win32-content-prep-tool"></a>运行 Microsoft Win32 内容准备工具

如果在没有参数的情况下通过命令窗口运行 `IntuneWinAppUtil.exe`，该工具将指导你逐步输入所需参数。 或者，可以根据以下可用命令行参数向命令添加参数。

### <a name="available-command-line-parameters"></a>可用的命令行参数 

|    **命令行参数**    |    **描述**    |
|:------------------------------:|:----------------------------------------------------------:|
|    `-h`     |    帮助    |
|    `-c <setup_folder>`     |    所有安装程序文件的文件夹。 此文件夹中的所有文件将压缩为 .intunewin 文件。    |
|   ` -s <setup_file>`     |    安装程序文件（如 setup.exe 或 setup.msi）。    |
|    `-o <output_folder>`     |    生成的 .intunewin 文件的输出文件夹。    |
|    `-q`       |    安静模式    |

### <a name="example-commands"></a>示例命令

|    **示例命令**    |    **描述**    |
|:-----------------------------------------------------------------------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|    `IntuneWinAppUtil -h`    |    该命令将显示工具的使用信息。    |
|    `IntuneWinAppUtil -c c:\testapp\v1.0 -s c:\testapp\v1.0\setup.exe -o c:\testappoutput\v1.0 -q`    |    此命令将从指定的源文件夹和安装文件生成 `.intunewin` 文件。 对于 MSI 安装文件，此工具将检索 Intune 所需的信息。 如果指定了 `-q`，则命令将以安静模式运行；如果输出文件已存在，则将覆盖该命令。 此外，如果输出文件夹不存在，将自动创建该文件夹。    |

生成 .intunewin 文件时，将需要引用的任何文件置于安装程序文件夹的子文件夹中。 然后，使用相对路径引用所需的特定文件。 例如：

安装程序源文件夹：c:\testapp\v1.0<br>
许可证文件：c:\testapp\v1.0\licenses\license.txt

通过使用相对路径 licenses\license.txt 引用 license.txt 文件。

## <a name="create-assign-and-monitor-a-win32-app"></a>创建、分配和监视 Win32 应用

与业务线 (LOB) 应用一样，可以向 Microsoft Intune 添加 Win32 应用。 此类应用通常由内部或第三方编写。 

### <a name="process-flow-to-add-a-win32-app-to-intune"></a>将 Win32 应用添加到 Intune 的流程

   ![将 Win32 应用添加到 Intune 的流程](./media/add-win32-app.svg)

### <a name="add-a-win32-app-to-intune"></a>将 Win32 应用添加到 Intune

以下步骤提供指导，以帮助将 Windows 应用添加到 Intune。

### <a name="step-1-specify-the-software-setup-file"></a>步骤 1：指定软件安装程序文件

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3.  在“Intune”窗格中，选择“客户端应用” > “应用” > “添加”。
4.  在“添加”应用窗格中，从提供的下拉列表中选择“Windows 应用(Win32)”。

    ![添加应用边栏选项卡 - 添加类型下拉列表框的屏幕截图](./media/apps-win32-app-01.png)

### <a name="step-2-upload-the-app-package-file"></a>步骤 2：上传应用包文件

1.  在“添加应用”窗格中，选择“应用包文件”以选择一个文件。 随即显示“应用包文件”窗格。

    ![应用包文件边栏选项卡的屏幕截图](./media/apps-win32-app-02.png)

2.  在“应用包文件”窗格中，选择“浏览”按钮。 然后选择扩展名为 .intunewin 的 Windows 安装文件。

    > [!IMPORTANT]
    > 请确保使用最新版本的 Microsoft Win32 内容准备工具。 如果不使用最新版本，你将看到一条警告，指示该应用是使用旧版本的 Microsoft Win32 内容准备工具打包的。 

3.  完成后，选择“确定”。

### <a name="step-3-configure-app-information"></a>步骤 3：配置应用信息

1.  在“添加应用”窗格中，选择“应用信息”以配置应用。
2.  在“应用信息”窗格中，配置以下信息。 此窗格中的某些值可能已自动填充。
    - **名称**：输入显示在公司门户中的应用的名称。 如果同一应用名称存在两次，则每个应用都将显示在公司门户中。
    - **说明**：输入应用的描述。 描述显示在公司门户中。
    - **发布者**：输入应用发布者的名称。
    - **类别**：选择一个或多个内置应用类别，或选择你创建的类别。 “类别”可让用户在浏览公司门户时更轻松地查找应用。
    - **在公司门户中将此应用显示为特色应用**：当用户浏览应用时，在公司门户的主页上突出显示应用。
    - **信息 URL**：（可选）输入包含此应用相关信息的网站的 URL。 此 URL 显示在公司门户中。
    - **隐私 URL**：（可选）输入包含此应用相关隐私信息的网站的 URL。 此 URL 显示在公司门户中。
    - **开发者**：（可选）输入应用开发者的名称。
    - **所有者**：（可选）输入此应用的所有者的名称。 例如，“HR 部门”。
    - **备注**：输入想与此应用关联的任何备注。
    - **徽标**：上传与应用关联的图标。 用户浏览公司门户时，该图标将与应用一同显示。
3.  完成后，选择“确定”。

### <a name="step-4-configure-app-installation-details"></a>步骤 4：配置应用的安装详细信息
1.  在“添加应用”窗格中，选择“程序”以配置应用的安装和删除命令。
2.  添加用于安装应用的完整安装命令行。 

    例如，如果应用文件名为“MyApp123”，请添加以下内容：<br>
    `msiexec /p “MyApp123.msp”`<p>
    此外，如果应用程序为 `ApplicationName.exe`，命令将为应用程序名称，后跟程序包支持的命令参数（开关）。 <br>例如：<br>
    `ApplicationName.exe /quiet`<br>
    在上述命令中，`ApplicationName.exe` 程序包支持 `/quiet` 命令参数。<p> 如需获取应用程序包支持的特定参数，请联系应用程序供应商。

3.  添加根据应用的 GUID 卸载应用的完整卸载命令行。 

    例如：`msiexec /x “{12345A67-89B0-1234-5678-000001000000}”`

    > [!NOTE]
    > 可以将 Win32 应用配置为在“用户”或“系统”上下文中安装。 “用户”上下文表示仅指定用户。 “系统”上下文表示 Windows 10 设备的所有用户。
    >
    > 最终用户无需登录设备即可安装 Win32 应用。
    > 
    > 将应用设置为在用户上下文中安装且设备上的最终用户具有管理员权限时，将在管理员权限下执行 Win32 应用安装和卸载（默认情况）。

4.  完成后，选择“确定”。

### <a name="step-5-configure-app-requirements"></a>步骤 5：配置应用要求

1.  在“添加应用”窗格中，选择“要求”以配置设备在安装应用之前必须满足的要求。
2.  在“添加要求规则”窗格中，配置以下信息。 此窗格中的某些值可能已自动填充。
    - **操作系统体系结构**：选择安装应用所需的体系结构。
    - **最低操作系统**：选择安装应用所需的最低操作系统。
    - **所需的磁盘空间(MB)**：添加系统驱动器上安装应用所需的可用磁盘空间（可选）。
    - **所需的物理内存(MB)**：添加安装应用所需的物理内存 (RAM)（可选）。
    - **所需的逻辑处理器的最小数**：添加安装应用所需的最小逻辑处理器数（可选）。
    - **所需的最低 CPU 速度 (MHz)**：添加安装应用所需的最低 CPU 速度（可选）。

3. 单击“添加”以显示“添加要求规则”边栏选项卡，并配置其他要求规则。 选择“要求类型”，以选择将用于确定如何验证要求的规则类型。 要求规则可以基于文件系统信息、注册表值和 PowerShell 脚本。 
    - **文件**：选择“文件”作为“要求类型”时，要求规则必须检测文件或文件夹、日期、版本或大小。 
        - **路径** - 包含要检测的文件或文件夹的文件夹完整路径。
        - **文件或文件夹** - 要检测的文件或文件夹。
        - **属性** - 选择用于验证应用是否存在的规则类型。
        - **与 64 位客户端上的 32 位应用程序相关联** - 选择“是”以展开 64 位客户端上的 32 位上下文中的任何路径环境变量。 选择“否”（默认值），展开 64 位客户端上的 64 位上下文中的任何路径变量。 32 位客户端将始终使用 32 位上下文。
    - **注册表**：选择“注册表”作为“要求类型”时，要求规则必须根据值、字符串、整数或版本检测注册表设置。
        - **密钥路径** - 包含要检测的值的注册表项的完整路径。
        - **值名称** - 要检测的注册表值的名称。 如果此值为空，则将对密钥进行检测。 如果检测方法不是文件或文件夹存在，则密钥的（默认）值将用作检测值。
        - **注册表项要求** – 选择用于确定如何验证要求规则的注册表项比较的类型。
        - **与 64 位客户端上的 32 位应用相关联** -选择“是”，搜索 64 位客户端上的 32 位注册表。 选择“否”（默认值），搜索 64 位客户端上的 64 位注册表。 32 位客户端将始终搜索 32 位注册表。
    - **脚本**：如果在 Intune 控制台中无法根据提供给你的文件、注册表或其他任何方法创建要求规则，请选择“脚本”作为“要求类型”。
        - **脚本文件** – 对于基于 PowerShell 脚本的要求规则，如果存在代码为 0，则将更详细地检测 STDOUT。 例如，在整数值为 1 时，可以检测 STDOUT。
        - **在 64 位客户端上以 32 位进程形式运行脚本** - 选择“是”，在 64 位客户端上以 32 位进程运行脚本。 选择“否”（默认值），在 64 位客户端上以 64 位进程运行该脚本。 32 位客户端在 32 位进程中运行该脚本。
        - **使用登录凭据运行此脚本**：选择“是”，使用登录设备凭据运行脚本**。
        - **强制执行脚本签名检查** - 选择“是”，验证脚本已由受信任的发布者签名，这将允许脚本在没有显示警告或提示的情况下运行。 该脚本将运行畅通。 选择“否”（默认值），运行无需签名验证的最终用户确认脚本。
        - **选择输出数据类型**：选择确定要求规则是否匹配时所用的数据类型。
4.  完成后，选择“确定”。

### <a name="step-6-configure-app-detection-rules"></a>步骤 6：配置应用检测规则

1.  在“添加应用”窗格中，选择“检测规则”以配置检测应用状态的规则。
2.  在“规则格式”字段中，选择检测应用存在性的方式。 可选择手动配置检测规则，或使用自定义脚本检测应用是否存在。 必须至少选择一个检测规则。 

    > [!NOTE]
    > 在“检测规则”窗格中，可选择添加多个规则。 必须满足“所有”规则的条件才能检测应用。

    - **手动配置检测规则** - 可选择以下某个规则类型：
        1.  **MSI** - 基于 MSI 版本检查进行验证。 此选项只能添加一次。 选择此规则类型时，你有两个设置：
            - **MSI 产品代码** - 为应用添加有效的 MSI 产品代码。
            - **MSI 产品版本检查** - 选择“是”，以验证除 MSI 产品代码外的 MSI 产品版本。
        2.  **文件** - 基于文件或文件夹检测、日期、版本或大小进行验证。
            - **路径** - 包含要检测的文件或文件夹的文件夹完整路径。
            - **文件或文件夹** - 要检测的文件或文件夹。
            - **检测方法** - 选择用于验证应用存在的检测方法类型。
            - **与 64 位客户端上的 32 位应用程序相关联** - 选择“是”以展开 64 位客户端上的 32 位上下文中的任何路径环境变量。 选择“否”（默认值），展开 64 位客户端上的 64 位上下文中的任何路径变量。 32 位客户端将始终使用 32 位上下文。
            
            **基于文件的检测示例**
            1.  检查文件是否存在。
         
                ![检测规则窗格的屏幕截图 - 文件存在](./media/apps-win32-app-03.png)
        
            2.  检查文件夹是否存在。
         
                ![检测规则窗格的屏幕截图 - 文件夹存在](./media/apps-win32-app-04.png)
        
        3. **注册表** - 基于值、字符串、整数或版本进行验证。
            - **密钥路径** - 包含要检测的值的注册表项的完整路径。
            - **值名称** - 要检测的注册表值的名称。 如果此值为空，则将对密钥进行检测。 如果检测方法不是文件或文件夹存在，则密钥的（默认）值将用作检测值。
            - **检测方法** - 选择用于验证应用存在的检测方法类型。
            - **与 64 位客户端上的 32 位应用相关联** -选择“是”，搜索 64 位客户端上的 32 位注册表。 选择“否”（默认值），搜索 64 位客户端上的 64 位注册表。 32 位客户端将始终搜索 32 位注册表。
            
            **基于注册表的检测示例**
            1.  检查注册表项是否存在。
            
                ![检测规则窗格的屏幕截图 - 注册表项存在](./media/apps-win32-app-05.png)    
            
            2.  检查是否存在注册表值。
        
                ![检测规则窗格的屏幕截图 - 注册表值存在](./media/apps-win32-app-06.png)    
        
            3.  检查注册表值字符串是否相等。
        
                ![检测规则窗格的屏幕截图 - 注册表值字符串相等](./media/apps-win32-app-07.png)    
     
    - **使用自定义检测脚本** - 指定将用于检测此应用的 PowerShell 脚本。 
    
        1.  **脚本文件** - 选择将检测客户端上的应用存在的 PowerShell 脚本。 该脚本返回 0 值退出代码时以及将字符串值写入 STDOUT 时，都将检测该应用。

        2.  **在 64 位客户端上以 32 位进程形式运行脚本** - 选择“是”，在 64 位客户端上以 32 位进程运行脚本。 选择“否”（默认值），在 64 位客户端上以 64 位进程运行该脚本。 32 位客户端在 32 位进程中运行该脚本。

        3.  **强制执行脚本签名检查** - 选择“是”，验证脚本已由受信任的发布者签名，这将允许脚本在没有显示警告或提示的情况下运行。 该脚本将运行畅通。 选择“否”（默认值），运行无需签名验证的最终用户确认脚本。
    
            Intune 代理检查脚本的结果。 读取脚本写入到标准输出 (STDOUT) 流、标准错误 (STDERR) 流和退出代码的值。 如果脚本以非零值退出，则脚本失败，并且应用程序检测状态为“未安装”。 如果退出代码为零，并且 STDOUT 具有数据，则应用程序检测状态为“已安装”。 

            > [!NOTE]
            > Microsoft 建议将你的脚本编码为 UTF-8。 脚本以 0 值退出时，脚本执行成功。 第二个输出通道表示检测到应用 - STDOUT 数据表明该应用已在客户端上找到。 我们不会从 STDOUT 中查找特定的字符串。

        4.  添加应用规则后，请选择“添加” > “确定”。

### <a name="step-7-configure-app-return-codes"></a>步骤 7：配置应用返回代码

1.  在“添加应用”窗格中，选择“返回代码”以添加用于指定应用安装重试行为或安装后行为的返回代码。 在创建应用期间默认添加返回代码条目。 但是，可以添加其他返回代码，或更改现有的返回代码。 
2.  在“返回代码”窗格中，添加其他返回代码，或修改现有的返回代码。
    - **失败** - 表示应用安装失败的返回值。
    - **硬重启** - 硬新启返回代码不允许在未重启的情况下在客户端上安装下一个 Win32 应用。 
    - **软重启** - 软重启返回代码允许安装下一个 Win32 应用程序而无需重启客户端。 重启对于完成当前应用安装操作是必要的。
    - **重试** - 重试返回代码代理将尝试三次安装应用。 每次尝试都将等待 5 分钟。 
    - **成功** - 表示应用已成功安装的返回值。
3.  添加或修改返回代码列表后，请选择“确定”。

### <a name="step-8-add-the-app"></a>步骤 8：添加应用

1.  在“添加应用”窗格中，验证是否已正确配置应用信息。
2.  选择“添加”将应用上传到 Intune。

### <a name="step-9-assign-the-app"></a>步骤 9：分配应用

1.  在“应用”窗格中，选择“分配”。
2.  选择“添加组”以打开与该应用相关的“添加组”窗格。
3.  对于特定应用，请选择“分配类型”：
    - **适用于已注册的设备**：用户从公司门户应用或公司门户网站安装应用。
    - **必需**：应用安装在所选组中的设备上。
    - **卸载**：已从所选组中设备上卸载应用。
4.  选择“包括的组”并分配将使用此应用的组。
5.  在“分配”窗格中选择“确定”，完成包括的组选择。
6.  如果想排除受此应用分配影响的任何用户组，请选择“排除组”。
7.  在“添加组”窗格中，选择“确定”。
8.  在应用的“分配”窗格中，选择“保存”。

此时已完成将 Win32 应用添加到 Intune 的步骤。 有关应用分配和监视的详细信息，请参阅[使用 Microsoft Intune 将应用分配到组](https://docs.microsoft.com/intune/apps-deploy)和[使用 Microsoft Intune 监视应用信息和分配](https://docs.microsoft.com/intune/apps-monitor)。

## <a name="app-dependencies"></a>应用依赖项

应用依赖项是在能够安装 Win32 应用前必须安装的应用程序。 可以要求将其他应用作为依赖项安装。 具体来说，设备必须先安装相关应用，再安装 Win32 应用。 最多有 100 个依赖项，其中包括任何已包含的依赖项，以及应用本身的依赖项。 仅在向 Intune 添加并上传 Win32 应用之后，才可以添加 Win32 应用依赖项。 添加 Win32 应用之后，Win32 应用的边栏选项卡上将显示“依赖项”选项。 

添加应用依赖项时，可以根据应用名称和发布者进行搜索。 此外，还可根据应用名称和发布者对已添加的依赖项进行排序。 在已添加的应用依赖项列表中无法选中之前添加的应用依赖项。 

可以选择是否自动安装每个相关应用。 每个依赖项的“自动安装”选项默认设置为“是”。 即使相关应用的目标不是用户或设备，Intune 也将通过自动安装相关应用，在设备上安装满足依赖关系的应用，然后安装 Win32 应用。 务必注意，依赖项可具有递归子依赖项，并且将先安装每个子依赖项，然后安装主依赖项。 此外，依赖项的安装不遵循给定依赖项级别的安装顺序。

要向 Win32 应用添加应用依赖项，请按以下步骤操作：

1. 在 Intune 中，选择“客户端应用” > “应用”，查看已添加客户端应用的列表。 
2. 选择已添加的“Windows 应用(Win32)”应用。 
3. 选择“依赖项”，添加在安装 Win32 应用之前必须安装的相关应用。 
4. 单击“添加”添加应用依赖项。
5. 添加相关应用之后，单击“选择”。
6. 通过在“自动安装”下选择“是”或“否”，选择是否自动安装相关应用。
7. 单击 **“保存”**。

最终用户将看到 Windows Toast 通知，其中指出了在 Win32 应用安装过程中下载和安装的相关应用。 此外，如果未安装相关应用，最终用户通常会看到下列其中一条通知：
- 1 个或多个相关应用无法安装
- 1 个或多个相关应用要求不满足
- 1 个或多个相关应用等待设备重启

如果不选择“自动安装”依赖项，将不会尝试安装 Win32 应用。 此外，应用报告将显示标记为 `failed` 的依赖项，并提供失败原因。 可以单击 Win 32 应用[安装详细信息](troubleshoot-app-install.md#win32-app-installation-troubleshooting)中提供的失败消息（或警告），查看依赖项安装失败的信息。 

每个依赖项将遵循 Intune Win32 应用重试逻辑（等待 5 分钟后尝试安装 3 次）和全局重新评估计划。 此外，依赖项仅在设备上安装 Win32 应用时适用。 依赖项在卸载 Win32 应用时不适用。 要删除依赖项，必须单击依赖项列表行末的相关应用左侧的椭圆形（三个点）。 

## <a name="delivery-optimization"></a>传递优化

Windows 10 1709 及更高版本的客户端将在 Windows 10 客户端上使用传递优化组件下载 Intune Win32 应用内容。 传递优化提供了在默认情况下处于打开状态的对等功能。 传递优化可通过组策略和 Intune 设备配置进行配置。 有关详细信息，请参阅[适用于 Windows 10 的传递优化](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization)。 

## <a name="install-required-and-available-apps-on-devices"></a>在设备上安装必需和可用应用

最终用户将看到必需和可用应用安装的 Windows Toast 通知。 下图显示了在设备重启之前应用安装还未完成的 toast 通知示例。 

![应用安装的 Windows toast 通知的屏幕截图](./media/apps-win32-app-08.png)    

下图会通知最终用户，正在对设备进行应用更改。

![通知用户正在进行应用更改的屏幕截图](./media/apps-win32-app-09.png)    

## <a name="toast-notifications-for-win32-apps"></a>Win32 应用的 Toast 通知 
如需要，可以隐藏每个应用分配的最终用户 Toast 通知。 在 Intune 中，依次选择“客户端应用” > “应用”> 应用 >“分配” > “包括组”。 

> [!NOTE]
> 在未注册设备上不会卸载已安装 Intune 管理扩展的 Win32 应用。 管理员可利用分配排除避免向 BYOD 设备提供 Win32 应用。

## <a name="troubleshoot-win32-app-issues"></a>Win32 应用问题的疑难解答
客户端计算机上的代理日志通常位于 `C:\ProgramData\Microsoft\IntuneManagementExtension\Logs`。 可利用 `CMTrace.exe` 查看这些日志文件。 从 [Configuration Manager 客户端工具](https://docs.microsoft.com/sccm/core/support/tools)可以下载 CMTrace.exe。 

![客户端计算机上代理日志的屏幕截图](./media/apps-win32-app-10.png)    

> [!IMPORTANT]
> 为了能够正确安装和执行 LOB Win32 应用，反恶意软件设置应不扫描以下目录：<p>
> **在 X64 客户端计算机上**：<br>
> C:\Program Files (x86)\Microsoft Intune Management Extension\Content<br>
> C:\windows\IMECache
>  
> **在 X86 客户端计算机上**：<br>
> C:\Program Files\Microsoft Intune Management Extension\Content<br>
> C:\windows\IMECache

### <a name="detecting-the-win32-app-file-version-using-powershell"></a>检测使用 PowerShell 的 Win32 应用文件版本

如果难以检测到 Win32 应用文件版本，请考虑使用或修改以下 PowerShell 命令：

``` PowerShell

$FileVersion = [System.Diagnostics.FileVersionInfo]::GetVersionInfo("<path to binary file>").FileVersion
#The below line trims the spaces before and after the version name
$FileVersion = $FileVersion.Trim();
if ("<file version of successfully detected file>" -eq $FileVersion)
{
#Write the version to STDOUT by default
$FileVersion
exit 0
}
else
{
#Exit with non-zero failure code
exit 1
}

```
在以上 PowerShell 命令中，使用 Win32 应用文件的路径替换 `<path to binary file>` 字符串。 示例路径类似于以下内容：<br>
`C:\Program Files (x86)\Microsoft SQL Server Management Studio 18\Common7\IDE\ssms.exe`

另外，使用需要检测的文件版本替换 `<file version of successfully detected file>` 字符串。 示例文件版本字符串类似于以下内容：<br>
`2019.0150.18118.00 ((SSMS_Rel).190420-0019)`

如果需要获取 Win32 应用的版本信息，可使用以下 PowerShell 命令：

``` PowerShell

[System.Diagnostics.FileVersionInfo]::GetVersionInfo("<path to binary file>").FileVersion

```

在以上 PowerShell 命令中，使用文件路径替换 `<path to binary file>`。

### <a name="additional-troubleshooting-areas-to-consider"></a>需要考虑的其他故障排除方面
- 检查目标以确保设备上已安装代理 - 面向组的 Win32 应用或 PowerShell 脚本将为安全组创建代理安装策略。
- 检查 OS 版本 - Windows 10 1607 及更高版本。  
- 检查 Windows 10 SKU - Windows 10 S 或以 S 模式运行的 Windows 版本不支持 MSI 安装。

有关对 Win32 应用进行故障排除的更多信息，请参阅 [Win32 应用安装故障排除](troubleshoot-app-install.md#win32-app-installation-troubleshooting)。

## <a name="next-steps"></a>后续步骤

- 有关向 Intune 添加应用的详细信息，请参阅[向 Microsoft Intune 添加应用](apps-add.md)。
