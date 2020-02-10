---
title: 使用 Microsoft Intune 将 Office 365 应用添加到 Windows 10 设备
titleSuffix: ''
description: 了解如何使用 Microsoft Intune 在 Windows 10 设备上安装 Office 365 应用。
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
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86d02ae1277ff2fd6dfce9bf206628f5dc1c2a84
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755304"
---
# <a name="add-office-365-apps-to-windows-10-devices-with-microsoft-intune"></a>使用 Microsoft Intune 将 Office 365 应用添加到 Windows 10 设备

必须首先将应用添加到 Intune 中，才可以分配、监视、配置或保护它们。 其中一个可用的[应用类型](apps-add.md#app-types-in-microsoft-intune)是适用于 Windows 10 的 Office 365 应用。 通过在 Intune 中选择此应用类型，可以将 Office 365 应用分配并安装到所管理的运行 Windows 10 的设备。 还可以分配和安装适用于 Microsoft Project Online 桌面客户端和 Microsoft Visio Online 计划 2 的应用，前提是拥有它们的许可证。 可用的 Office 365 应用将显示为 Azure 内 Intune 控制台中应用列表中的一个条目。

> [!NOTE]
> 必须使用 Office 365 专业增强版许可证来激活通过 Microsoft Intune 部署的 Office 365 专业增强版应用。 Intune 目前不支持 Office 365 商业版。

## <a name="before-you-start"></a>开始之前

> [!IMPORTANT]
> 如果最终用户设备上有 .msi Office 应用，则必须使用“删除 MSI”  功能来安全地卸载这些应用。 否则，Intune 提供的 Office 365 应用将无法安装。

- 部署这些应用的设备必须运行 Windows 10 创意者更新或更高版本。
- Intune 仅支持添加来自 Office 365 套件的 Office 应用。
- 当 Intune 安装应用套件时，如果任何 Office 应用处于打开状态，安装可能会失败，并且用户可能会丢失未保存文件中的数据。
- Windows 家庭版、Windows 团队版、Windows 全息版或 Windows Holographic for Business 设备不支持这种安装方法。
- 在已使用 Intune 部署 Office 365 应用的设备上，Intune 不支持安装 Microsoft Store 中的 Office 365 桌面应用（称为 Office Centennial 应用）。 如果安装此配置，可能会导致数据丢失或损坏。
- 多个必需或可用的应用分配不会累加。 后面的应用分配会覆盖之前存在的已安装应用分配。 例如，如果第一组 Office 应用包含 Word，而后面的应用不包含，则 Word 会被卸载。 该条件不适用于任何 Visio 或 Project 应用程序。
- 当前不支持多个 Office 365 部署。 只会向设备提供一个部署
- **Office 版本** - 选择要分配 32 位还是 64 位版本的 Office。 可以在 32 位和 64 位设备上安装 32 位版本，但只能在 64 位设备上安装 64 位版本。
- **从最终用户设备中删除 MSI** - 选择是否要从最终用户设备中删除预先存在的 Office .MSI 应用。 如果最终用户设备上存在预先存在的 .MSI 应用，安装不会成功。 要卸载的应用不仅限于在“配置应用套件”中选择安装的应用，因为它会从最终用户设备中删除所有 Office (MSI) 应用  。 有关详细信息，请参阅[升级到 Office 365 专业增强版后删除现有的 Office MSI 版本](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version)。 Intune 在最终用户计算机上重新安装 Office 时，最终用户将自动获得与以前安装的 .MSI Office 相同的语言包。

## <a name="select-the-office-365-suite-app-type"></a>选择 Office 365 套件应用类型

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“应用”   > “所有应用”   > “添加”  。
3. 在“选择应用类型”  窗格的“Office 365 套件”  部分中选择“Windows 10”  。
4. 单击“选择”  。 将显示“添加 Office 365 套件”  步骤。


## <a name="step-1---app-suite-information"></a>步骤 1 - 应用套件信息

在此步骤中，提供有关该应用套件的信息。 此信息有助于在 Intune 中识别应用套件，也有助于用户在公司门户中找到应用套件。

1. 在“应用套件信息”  页中，可以确认或修改默认值：
    - **套件名称**：输入应用套件的名称，该名称将显示在公司门户中。 请确保使用的所有套件名称都是唯一的。 如果同一应用套件名称存在两次，则在公司门户中将仅向用户显示其中一个应用。
    - **套件描述**：输入应用套件的描述。 例如，可以列出已选择要包括的应用。
    - **发布者**：Microsoft 显示为发布者。
    - **类别**：（可选）选择一个或多个内置应用类别或所创建的类别。 该设置可让用户在浏览公司门户时更轻松地查找应用套件。
    - **在公司门户中将此应用显示为特色应用**：当用户浏览应用时，选择此选项以在公司门户的主页上突出显示应用套件。
    - **信息 URL**：（可选）输入包含此应用相关信息的网站的 URL。 在公司门户中向用户显示该 URL。
    - **隐私 URL**：（可选）输入包含此应用相关隐私信息的网站的 URL。 在公司门户中向用户显示该 URL。
    - **开发者**：Microsoft 显示为开发者。
    - **所有者**：Microsoft 显示为所有者。
    - **备注**：输入想与此应用关联的任何备注。
    - **徽标**：用户浏览公司门户时，Office 365 徽标与应用一同显示。
2. 单击“下一步”  以显示“配置应用套件”  页。

## <a name="step-2---option-1-configure-app-suite-using-the-configuration-designer"></a>步骤 2 -（选项 1  ）使用配置设计器配置应用套件 

可以选择一种方法来配置应用设置，方法是选择“配置设置格式”  。 设置格式选项包括：
- 配置设计器
- 输入 XML 数据

选择“配置设计器”  后，“添加应用”  窗格会发生变化，会新增三个设置区域：
- 配置应用套件
- 应用套件信息
- 属性

<img alt="Add Office 365 - Configuration designer" src="./media/apps-add-office365/apps-add-office365-02.png" width="700">

1. 在“配置应用套件”  页上，选择“配置设计器”  。
   - **选择 Office 应用**：通过在下拉列表中选择应用，选择要分配到设备的标准 Office 应用。
   - **选择其他 Office 应用(需要许可证)** ：通过在下拉列表中选择应用，选择要分配到设备以及有相应许可证的其他 Office 应用。 这些应用包括许可的应用，如 Microsoft Project Online 桌面客户端和 Microsoft Visio Online 计划 2。
   - **体系结构**：选择要分配 32 位  还是 64 位  版本的 Office ProPlus。 可以在 32 位和 64 位设备上安装 32 位版本，但只能在 64 位设备上安装 64 位版本。
    - **更新通道**：选择在设备上更新 Office 的方式。 有关不同更新通道的信息，请参阅 [Office 365 专业增强版的更新通道概述](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)。 选择：
        - **每月**
        - **每月（定向）**
        - **半年**
        - **半年（定向）**

        选择通道后，可以选择以下项：
        - **删除其他版本**：选择“是”  从用户设备中删除其他版本的 Office (MSI)。 如果要从最终用户设备中删除预先存在的 Office .MSI 应用，请选择此选项。 如果最终用户设备上存在预先存在的 .MSI 应用，安装不会成功。 要卸载的应用不仅限于在“配置应用套件”中选择安装的应用，因为它会从最终用户设备中删除所有 Office (MSI) 应用  。 有关详细信息，请参阅[升级到 Office 365 专业增强版后删除现有的 Office MSI 版本](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version)。 Intune 在最终用户计算机上重新安装 Office 时，最终用户将自动获得与以前安装的 .MSI Office 相同的语言包。 
        - **要安装的版本**：选择应安装的 Office 版本。
        - **特定版本**：如果在上述设置中选择“特定版本”  作为要安装的版本  ，则可以选择为最终用户设备上的选定通道安装特定版本的 Office。 
            
            可用版本会随时间发生变化。 因此，在创建新部署时，可用版本可能为更新的版本，而不再提供某些较旧版本。 当前部署会继续部署旧版本，但版本列表会持续按通道更新。
            
            对于更新其固定版本和部署为可用的设备，如果设备在发生设备签入前已安装以前版本，报告状态将显示为“已安装”。 发生设备签入时，状态将暂时更改为“未知”，但不会向用户显示该状态。 当用户开始安装最新可用版本时，用户将看到状态更改为“已安装”。
            
            有关详细信息，请参阅 [Office 365 专业增强版的更新频道概述](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)。
    - **使用共享的计算机激活**：当多个用户共享一台计算机时选择该选项。 有关详细信息，请参阅 [Office 365 的共享计算机激活概述](https://docs.microsoft.com/DeployOffice/overview-of-shared-computer-activation-for-office-365-proplus)。
    - **自动接受应用最终用户许可协议**：如果不需要最终用户接受许可协议，请选择此选项。 Intune 随后会自动接受该协议。
    - **语言**：Office 会自动以随 Windows 安装在最终用户设备上的任何受支持的语言进行安装。 如果想要使用应用套件安装其他语言，请选择此选项。 <p></p>
        可以为通过 Intune 管理的 Office 365 专业增强版应用部署其他语言。 可用语言列表包括语言包的“类型”（核心、部分和校对）  。 在 Azure 门户中，选择“Microsoft Intune” > “应用” > “所有应用” > “添加”     。 在“添加应用”窗格的“应用类型”列表中，选择“Office 365 套件”下的“Windows 10”     。 在“应用套件设置”窗格中选择“语言”   。 有关其他信息，请参阅 [Office 365 专业增强版中的语言部署概述](https://docs.microsoft.com/deployoffice/overview-of-deploying-languages-in-office-365-proplus)。
2. 单击“下一步”  以显示“作用域标记”  页面。

## <a name="step-2---option-2-configure-app-suite-using-xml-data"></a>步骤 2 -（选项 2  ）使用 XML 数据配置应用套件 

如果在“配置应用套件”  页上的“设置格式”  下拉框下选择了“输入 XML 数据”  选项，则可以使用自定义配置文件来配置 Office 应用套件。

![添加 Office 365 配置设计器](./media/apps-add-office365/apps-add-office365-01.png)

1. 添加了配置 XML。
2. 单击“下一步”  以显示“作用域标记”  页面。

有关输入 XML 数据的详细信息，请参阅 [Office 部署工具的配置选项](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool)。

## <a name="step-3---select-scope-tags-optional"></a>步骤 3 - 选择作用域标记（可选）
可以使用作用域标记来确定谁可以在 Intune 中查看客户端应用信息。 若要详细了解作用域标记，请参阅[将基于角色的访问控制和作用域标记用于分布式 IT](../fundamentals/scope-tags.md)。

1. 单击“选择作用域标记”  可以选择为应用套件添加作用域标记。 
2. 单击“下一步”以显示“分配”页面   。

## <a name="step-4---assignments"></a>步骤 4 - 分配

1. 为应用套件选择“必需”  、“适用于已注册的设备”  或“卸载”  组分配。 有关详细信息，请参阅[添加用于组织用户和设备的组](~/fundamentals/groups-add.md)和[使用 Microsoft Intune 将应用分配到组](apps-deploy.md)。
2. 单击“下一步”  以显示“查看 + 创建”页  。 

## <a name="step-5---review--create"></a>步骤 5 - 查看 + 创建

1. 查看为应用套件输入的值和设置。
2. 完成后，单击“创建”  将应用添加到 Intune。

    随即显示创建的 Office 365 Window 10 应用套件的“概述”  边栏选项卡。

## <a name="deployment-details"></a>部署详细信息

通过 [Office 配置服务提供程序 (CSP)](https://docs.microsoft.com/windows/client-management/mdm/office-csp) 将 Intune 中的部署策略分配给目标计算机后，最终设备将从 officecdn.microsoft.com 位置自动下载安装包  。 你将看到两个目录显示在“Program Files”目录中  ：

![Program Files 目录中的 Office 安装包](./media/apps-add-office365/office-folder.png)

在“Microsoft Office”  目录下，将创建存储安装文件的新文件夹：

![Microsoft Office 目录下新建的文件夹](./media/apps-add-office365/created-folder.png)

在“Microsoft Office 15”  目录下，将存储 Office 即点即用安装启动器文件。 如果需要分配类型，则将自动启动安装：

![单击以运行安装启动器文件](./media/apps-add-office365/clicktorun-files.png)

如果将 O365 套件的分配配置为“必需”，则安装将处于静默模式。 安装成功后，将删除已下载的安装文件。 如果将分配配置为“可用”  ，则 Office 应用程序将显示在公司门户应用程序中，以便最终用户能够手动触发安装。

## <a name="troubleshooting"></a>疑难解答
Intune 使用 [Office 部署工具](https://docs.microsoft.com/DeployOffice/overview-of-the-office-2016-deployment-tool)下载 Office 365 专业增强版并使用 [Office 365 CDN](https://docs.microsoft.com/office365/enterprise/content-delivery-networks) 将其部署到客户端计算机。 参考[管理 Office 365 终结点](https://docs.microsoft.com/office365/enterprise/managing-office-365-endpoints)中所述的最佳做法，确保网络配置允许客户端直接访问 CDN（而不是通过中心代理路由 CDN 流量）以避免引入不必要的延迟。

如果遇到安装或运行时问题，请在目标设备上运行 [Microsoft Office 365 支持和恢复助手](https://diagnostics.office.com)。

### <a name="additional-troubleshooting-details"></a>其他疑难解答详细信息

无法将 O365 应用安装到设备时，必须确定问题是与 Intune 相关还是与 OS/Office 相关。 如果你可以看到两个文件夹“Microsoft Office”和“Microsoft Office 15”显示在设备的“Program Files”目录中，则可以确认 Intune 已成功启动部署    。 如果看不到两个文件夹显示在“Program Files”下，则应确认以下情况  ：

- 设备已在 Microsoft Intune 中正确注册。 
- 设备上有活动的网络连接。 如果设备处于飞行模式、处于关闭状态，或位于无服务的位置，则在建立网络连接之前不会应用此策略。
- 同时满足 Intune 和 Office 365 网络要求，并且可以根据以下文章访问相关的 IP 范围：

  - [Intune 网络配置要求和带宽](https://docs.microsoft.com/intune/network-bandwidth-use)
  - [Office 365 URL 和 IP 地址范围](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)

- 已为 O365 应用套件分配了正确的组。 

此外，还会监视目录 C:\Program Files\Microsoft Office\Updates\Download 的大小  。 从 Intune 云下载的安装包将存储在此位置。 如果大小不增加或仅缓慢增加，则建议仔细检查网络连接和带宽。

可以得出 Intune 和网络基础结构按预期方式工作的结论后，应从 OS 的角度进一步分析问题。 考虑以下情况：

- 目标设备必须在 Windows 10 创意者更新或更高版本上运行。
- Intune 部署应用程序时，未打开任何现有 Office 应用。
- 已正确从设备中删除 Office 的现有 MSI 版本。 Intune 利用与 Office MSI 不兼容的 Office 即点即用。 本文档进一步介绍了此行为：<br>
  [不支持在同一台计算机上随即点即用和 Windows Installer 一起安装的 Office](https://support.office.com/article/office-installed-with-click-to-run-and-windows-installer-on-same-computer-isn-t-supported-30775ef4-fa77-4f47-98fb-c5826a6926cd)
- 登录用户应拥有在设备上安装应用程序的权限。
- 根据 Windows 事件查看器日志“Windows 日志”   -> “应用程序”  确认没有问题。
- 在安装过程中捕获 Office 安装详细日志。 为此，请执行以下步骤：<br>
    1. 在目标计算机上为 Office 安装激活详细日志记录。 为此，请运行以下命令以修改注册表：<br>
        `reg add HKLM\SOFTWARE\Microsoft\ClickToRun\OverRide /v LogLevel /t REG_DWORD /d 3`<br>
    2. 将 Office 365 套件再次部署到目标设备。<br>
    3. 等待大约 15 到 20 分钟，然后跳到“%temp%”文件夹和“%windir%\temp”文件夹，按“修改日期”排序    ，选取根据重现时间修改的“{Machine Name}-{TimeStamp}.log”文件  。<br>
    4. 运行以下命令以禁用详细日志：<br>
        `reg delete HKLM\SOFTWARE\Microsoft\ClickToRun\OverRide /v LogLevel /f`<br>
        详细日志可以提供有关安装过程的详细信息。

## <a name="errors-during-installation-of-the-app-suite"></a>在安装应用套件期间出错

有关如何查看详细安装日志的信息，请参阅[如何启用 Office 365 专业增强版 ULS 日志记录](/office/troubleshoot/diagnostic-logs/how-to-enable-office-365-proplus-uls-logging)。

下表列出了用户可能会遇到的常见错误代码及其含义。

### <a name="status-for-office-csp"></a>Office CSP 的状态

| 状态 | 阶段 | 说明 |
|--------------------------------------------------|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1460 (ERROR_TIMEOUT) | 下载 | 下载 Office 部署工具失败 |
| 13 (ERROR_INVALID_DATA) | - | 无法验证下载的 Office 部署工具的签名 |
| 来自 CertVerifyCertificateChainPolicy 的错误代码 | - | 下载的 Office 部署工具的证书检查失败 |
| 997 | WIP | 安装 |
| 0 | 安装后 | 安装成功 |
| 1603 (ERROR_INSTALL_FAILURE) | - | 任何先决条件检查失败，如：SxS（尝试在安装 2016 MSI 时安装）版本与其他版本不匹配 |
| 0x8000ffff (E_UNEXPECTED) | - | 尝试在计算机上没有即点即用 Office 时卸载 |
| 17002 | - | 未能完成方案（安装）。 可能的原因：用户取消了安装；另一个安装取消了安装；安装期间磁盘空间不足；语言 ID 未知 |
| 17004 | - | 未知 SKU |


### <a name="office-deployment-tool-error-codes"></a>Office 部署工具错误代码

| 方案 | 返回代码 | UI | 备注 |
|------------------------------------------------------------------------------------------------------------------|---------------------------------------|----------------------------------------------------|------------------------------------|
| 没有可用的即点即用安装时卸载工作量 | -2147418113、0x8000ffff 或 2147549183 | 错误代码：30088-1008 错误代码：30125-1011 (404) | Office 部署工具 |
| 安装 MSI 版本时安装 | 1603 | - | Office 部署工具 |
| 用户或另一个安装取消了安装 | 17002 | - | 即点即用 |
| 尝试在安装了 32 位的设备上安装 64 位。 | 1603 | - | Office 部署工具返回代码 |
| 尝试安装未知的 SKU（不是 Office CSP 的合法用例，因为我们只应传入有效的 SKU） | 17004 | - | 即点即用 |
| 空间不足 | 17002 | - | 即点即用 |
| 即点即用客户端无法启动（意外） | 17000 | - | 即点即用 |
| 即点即用客户端无法将方案加入队列（意外） | 17001 | - | 即点即用 |

## <a name="next-steps"></a>后续步骤

- 若要将应用套件分配给其他组，请参阅[将应用分配给组](/intune-azure/manage-apps/deploy-apps)。
