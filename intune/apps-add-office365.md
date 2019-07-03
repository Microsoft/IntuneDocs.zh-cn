---
title: 使用 Microsoft Intune 将 Office 365 应用分配到 Windows 10 设备
titleSuffix: ''
description: 了解如何使用 Microsoft Intune 在 Windows 10 设备上安装 Office 365 应用。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 095c2ee0aba0680de0c5fc55c1406dba41111b92
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67527442"
---
# <a name="assign-office-365-apps-to-windows-10-devices-with-microsoft-intune"></a>使用 Microsoft Intune 将 Office 365 应用分配到 Windows 10 设备

必须首先将应用添加到 Intune 中，才可以分配、监视、配置或保护它们。 其中一个可用的[应用类型](apps-add.md#app-types-in-microsoft-intune)是适用于 Windows 10 的 Office 365 应用。 通过在 Intune 中选择此应用类型，可以将 Office 365 应用分配并安装到所管理的运行 Windows 10 的设备。 还可以分配和安装适用于 Microsoft Project Online 桌面客户端和 Microsoft Visio Online 计划 2 的应用，前提是拥有它们的许可证。 可用的 Office 365 应用将显示为 Azure 内 Intune 控制台中应用列表中的一个条目。

> [!NOTE]
> 必须使用 Office 365 专业增强版许可证来激活通过 Microsoft Intune 部署的 Office 365 专业增强版应用。 Intune 目前不支持 Office 365 商业版。

## <a name="before-you-start"></a>开始之前

> [!IMPORTANT]
> 如果最终用户设备上有 .msi Office 应用，则必须使用“删除 MSI”  功能来安全地卸载这些应用。 否则，Intune 提供的 Office 365 应用将无法安装。

- 部署这些应用的设备必须运行 Windows 10 创意者更新或更高版本。
- Intune 仅支持添加来自 Office 365 套件的 Office 应用。
- 当 Intune 安装应用套件时，如果任何 Office 应用处于打开状态，安装可能会失败，并且用户可能会丢失未保存文件中的数据。
- Windows 10 S、Windows 家庭版、Windows 团队、Windows Holographic 或 Windows Holographic for Business 设备上不支持此安装方法。
- 在已使用 Intune 部署 Office 365 应用的设备上，Intune 不支持安装 Microsoft Store 中的 Office 365 桌面应用（称为 Office Centennial 应用）。 如果安装此配置，可能会导致数据丢失或损坏。
- 多个必需或可用的应用分配不会累加。 后面的应用分配会覆盖之前存在的已安装应用分配。 例如，如果第一组 Office 应用包含 Word，而后面的应用不包含，则 Word 会被卸载。 该条件不适用于任何 Visio 或 Project 应用程序。
- **Office 版本** - 选择要分配 32 位还是 64 位版本的 Office。 可以在 32 位和 64 位设备上安装 32 位版本，但只能在 64 位设备上安装 64 位版本。
- **从最终用户设备中删除 MSI** - 选择是否要从最终用户设备中删除预先存在的 Office .MSI 应用。 如果最终用户设备上存在预先存在的 .MSI 应用，安装不会成功。 要卸载的应用不仅限于在“配置应用套件”中选择安装的应用，因为它会从最终用户设备中删除所有 Office (MSI) 应用  。 有关详细信息，请参阅[升级到 Office 365 专业增强版后删除现有的 Office MSI 版本](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version)。 Intune 在最终用户计算机上重新安装 Office 时，最终用户将自动获得与以前安装的 .MSI Office 相同的语言包。

## <a name="get-started"></a>入门

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在“Intune”窗格中，选择“客户端应用”   。
4. 在“客户端应用”工作负载窗格的“管理”下，选择“应用”    。
5. 选择“添加”  。
6. 在“添加应用”窗格中，请在“应用类型”列表中的“Office 365 套件”下选择“Windows 10”     。

## <a name="select-settings-format"></a>选择设置格式

可通过选择“设置格式”来选择配置应用设置的方法  。 设置格式选项包括：
- 配置设计器
- 输入 XML 数据

选择“配置设计器”后，“添加应用”边栏选项卡会发生变化，会新增两个设置选项   ：
- 配置应用套件
- 应用套件设置

<img alt="Add Office 365 - Configuration designer" src="./media/apps-add-office365/apps-add-office365-02.png" width="700">

选择“输入 XML 数据”后，“添加应用”边栏选项卡会显示“输入 XML 数据”选项    。 选择此选项以显示“配置文件”边栏选项卡  。 

![添加 Office 365 配置设计器](./media/apps-add-office365/apps-add-office365-01.png)
    
有关“输入 XML 数据”选项的详细信息，请参阅下方的[输入 XML 数据](apps-add-office365.md#enter-xml-format)  。

## <a name="configure-app-suite-information"></a>配置应用套件信息

在此步骤中，提供有关该应用套件的信息。 此信息有助于在 Intune 中识别应用套件，也有助于用户在公司门户中找到应用套件。

1. 在“添加应用”  窗格中，选择“应用套件信息”  。
2. 在  “应用套件信息”窗格中，请执行以下操作：
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
3. 选择“确定”  。

## <a name="configure-app-suite"></a>配置应用套件

如果选择“设置格式”下拉框下方的“配置设计器”选项，将看到“添加应用”边栏选项卡中的“配置应用套件”选项     。 选择想要分配到设备的 Office 应用。

1. 在“添加应用”  窗格中，选择“配置应用套件”  。
2. 在“配置应用套件”  窗格中，选择想要分配到设备的标准 Office 应用。  
    此外，还可以安装适用于 Microsoft Project Online 桌面客户端和 Microsoft Visio Online 计划 2 的应用，前提是拥有它们的许可证。
3. 选择“确定”  。

## <a name="configure-app-suite-settings"></a>配置应用套件设置

如果选择“设置格式”下拉框下方的“配置设计器”选项，将看到“添加应用”边栏选项卡中的“应用套件设置”选项     。 在此步骤中，配置应用套件的安装选项。 这些设置适用于添加到该套件的所有应用。

1. 在“添加应用”  窗格中，选择“应用套件设置”  。
2. 在  “应用套件设置”窗格中，请执行以下操作：
    - **Office 版本**：选择要分配 32 位还是 64 位版本的 Office。 可以在 32 位和 64 位设备上安装 32 位版本，但只能在 64 位设备上安装 64 位版本。
    - **更新通道**：选择在设备上更新 Office 的方式。 有关不同更新通道的信息，请参阅 [Office 365 专业增强版的更新通道概述](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)。 选择：
        - **每月**
        - **每月（定向）**
        - **半年**
        - **半年（定向）**

        选择通道后，可选择“特定”，在最终用户设备上为所选通道安装特定的 Office 版本  。 然后，选择要使用的特定版本的 Office  。
        
        可用版本会随时间发生变化。 因此，在创建新部署时，可用版本可能为更新的版本，而不再提供某些较旧版本。 当前部署会继续部署旧版本，但版本列表会持续按通道更新。
        
        对于更新其固定版本和部署为可用的设备，如果设备在发生设备签入前已安装以前版本，报告状态将显示为“已安装”。 发生设备签入时，状态将暂时更改为“未知”，但不会向用户显示该状态。 当用户开始安装最新可用版本时，用户将看到状态更改为“已安装”。
        
        有关详细信息，请参阅 [Office 365 专业增强版的更新频道概述](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)。

    - **从最终用户设备中删除 MSI** - 选择是否要从最终用户设备中删除预先存在的 Office .MSI 应用。 如果最终用户设备上存在预先存在的 .MSI 应用，安装不会成功。 要卸载的应用不仅限于在“配置应用套件”中选择安装的应用，因为它会从最终用户设备中删除所有 Office (MSI) 应用  。 有关详细信息，请参阅[升级到 Office 365 专业增强版后删除现有的 Office MSI 版本](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version)。 Intune 在最终用户计算机上重新安装 Office 时，最终用户将自动获得与以前安装的 .MSI Office 相同的语言包。 
    - **自动接受应用最终用户许可协议**：如果不需要最终用户接受许可协议，请选择此选项。 Intune 随后会自动接受该协议。
    - **使用共享的计算机激活**：当多个用户共享一台计算机时选择该选项。 有关详细信息，请参阅 [Office 365 的共享计算机激活概述](https://docs.microsoft.com/DeployOffice/overview-of-shared-computer-activation-for-office-365-proplus)。
    - **语言**：Office 会自动以随 Windows 安装在最终用户设备上的任何受支持的语言进行安装。 如果想要使用应用套件安装其他语言，请选择此选项。 <p></p>
    可以为通过 Intune 管理的 Office 365 专业增强版应用部署其他语言。 可用语言列表包括语言包的“类型”（核心、部分和校对）  。 在 Azure 门户中，选择“Microsoft Intune” > “客户端应用” > “应用” > “添加”     。 在“添加应用”边栏选项卡的“应用类型”列表中，选择“Office 365 套件”下的“Windows 10”     。 在“应用套件设置”边栏选项卡中选择“语言”   。 有关其他信息，请参阅 [Office 365 专业增强版中的语言部署概述](https://docs.microsoft.com/deployoffice/overview-of-deploying-languages-in-office-365-proplus)。

## <a name="select-scope-tags-optional"></a>选择作用域标记（可选）。
可以使用作用域标记来确定谁可以在 Intune 中查看客户端应用信息。 若要详细了解作用域标记，请参阅[将基于角色的访问控制和作用域标记用于分布式 IT](scope-tags.md)。

1. 选择“作用域(标记)”   >   “添加”。
2. 使用“选择”  框搜索作用域标记。
3. 选中要分配到此应用的作用域标记旁边的复选框。
4. 选择“选择” > “确定”   。

## <a name="enter-xml-format"></a>输入 XML 格式

如果选择“设置格式”下拉框下方的“输入 XML 数据”选项，将看到“添加应用”边栏选项卡中的“输入 XML 格式”选项     。 有关详细信息，请参阅 [Office 部署工具的配置选项](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool)。

## <a name="finish-up"></a>完成

完成后，在“添加应用”  窗格中，选择“添加”  。 创建的应用将显示在应用列表中。

## <a name="errors-during-installation-of-the-app-suite"></a>在安装应用套件期间出错

下表列出了用户可能会遇到的常见错误代码及其含义。

### <a name="status-for-office-csp"></a>Office CSP 的状态

| 状态 | 阶段 | 描述 |
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

- 要将应用分配给所选的组，请参阅[将应用分配给组](/intune-azure/manage-apps/deploy-apps)。
