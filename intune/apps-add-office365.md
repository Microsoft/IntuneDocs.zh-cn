---
title: "使用 Microsoft Intune 将 Office 365 应用安装到设备"
titlesuffix: 
description: "了解如何使用 Microsoft Intune 更轻松地在 Windows 10 设备上安装 Office 365 应用。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 076d228f3b18416e4ecb8fd1b3543a58d037e386
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-assign-office-365-apps-to-windows-10-devices-with-microsoft-intune"></a>如何使用 Microsoft Intune 将 Office 365 应用分配到 Windows 10 设备

此应用类型使用户可以轻松地将 Office 365 应用分配到所管理的运行 Windows 10 的设备。 还可以安装适用于 Microsoft Project Online 桌面客户端的应用和 Microsoft Visio Pro for Office 365，前提是拥有它们的许可证。 所需的应用将显示为 Intune 控制台的应用列表中的单一条目。


## <a name="before-you-start"></a>开始之前

>[!IMPORTANT]
>仅当设备上未安装其他版本的 Microsoft Office 时，才支持此安装 Office 的方法。

- 部署这些应用的设备必须运行 Windows 10 创意者更新或更高版本。
- Intune 仅支持从 Office 365 套件添加 Office 应用。
- 当 Intune 安装应用套件时，如果任何 Office 应用处于打开状态，安装可能会失败，并且最终用户可能会丢失未保存文件中的数据。
- Windows 10S、Windows 家庭版、Windows 团队、Windows Holographic 和 Windows Holographic for Business 设备上不支持此安装方法。
- 在已使用 Intune 部署 Office 365 应用的设备上，Intune 不支持安装 Microsoft Store 中的 Office 365 桌面应用（称为 Office Centennial 应用）。 如果安装此配置，可能会导致数据丢失或损坏。
- 多个必需或可用的应用分配不会累加。 后面的应用分配会覆盖之前存在的已安装应用分配。 例如，如果第一组 Office 应用包含 Word，而后面的应用不包含，则 Word 会被卸载。 这不适用于任何 Visio 或 Project 应用程序。


## <a name="get-started"></a>入门

1.  登录到 [Azure 门户](https://portal.azure.com)。
2.  选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分。
3.  在 Intune 边栏选项卡上，选择“移动应用”。
4.  在“移动应用”工作负载中，选择“管理”部分中的“应用”。
5.  在应用列表的上方，选择“添加”。
6.  在“添加应用”边栏选项卡的“应用类型”列表中，选择“Office 365 套件”下的“Windows 10”。
    现在，你便可以配置应用套件。

## <a name="configure-the-app-suite"></a>配置应用套件

在此步骤中，选择想要分配到设备的 Office 应用。

1.  在“添加应用”边栏选项卡上，选择“配置应用套件”。
2.  在“配置应用套件”边栏选项卡上，选择想要分配到设备的标准 Office 应用。 此外，还可以安装适用于 Microsoft Project Online 桌面客户端的应用和 Microsoft Visio Pro for Office 365，前提是拥有它们的许可证。
3.  完成后，请单击“确定”。

>[!IMPORTANT]
> 创建应用套件后，无法编辑其属性。 若要配置不同的属性，请删除该应用套件并创建一个新的应用套件。

## <a name="configure-app-information"></a>配置应用信息

在此步骤中，须提供有关该应用套件的信息。 此信息有助于在 Intune 中识别应用套件，也有助于用户在公司门户应用中找到它。

1.  在“添加应用”边栏选项卡上，选择“应用套件信息”。
2.  在“应用套件信息”边栏选项卡上，指定以下信息：
    - **套件名称** - 输入应用套件的名称，该名称将显示在公司门户中。 请确保使用的所有套件名称都是唯一的。 如果同一应用套件名称存在两次，则在公司门户中将仅向用户显示其中一个应用。
    - **套件描述** - 为应用套件输入描述。 例如，可以列出已选择要包括的应用。
    - **发行者** — 输入应用的发行者名称。
    - **类别** -（可选）选择一个或多个内置应用类别或所创建的类别。 这样，可让用户在浏览公司门户时更轻松地查找应用套件。
    - **在公司门户中将此应用显示为特色应用** - 当用户浏览应用时，在公司门户的主页上突出显示此应用套件。
    - **信息 URL** -（可选）输入包含此应用相关信息的网站 URL。 在公司门户中向用户显示该 URL。
    - **隐私 URL** -（可选）输入包含此应用相关隐私信息的网站 URL。 在公司门户中向用户显示该 URL。
    - **开发者** -（可选）输入应用开发者的名称。
    - **所有者** -（可选）输入此应用的所有者的名称，例如，**HR 部门**。
    - **说明** - 输入要与此应用关联的任何备注。
    -  - 上传用户浏览公司门户时，与应用一同显示的图标。
3.  完成后，请单击“确定”。

## <a name="configure-app-settings"></a>配置应用设置

在此步骤中，配置应用套件的安装选项。 这些设置适用于添加到该套件的所有应用。

1.  在“添加应用”边栏选项卡上，选择“应用套件设置”。
2.  在“应用套件设置”边栏选项卡上，指定以下信息：
    - **Office 版本** - 选择是否想要分配 32 位或 64 位版本的 Office。 可以在 32 位和 64 位设备上安装 32 位版本，但只能在 64 位设备上安装 64 位版本。
    - **更新频道** - 选择在设备上更新 Office 的方式。 有关不同更新通道的信息，请参阅 [Office 365 专业增强版的更新通道概述](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)。 选择：
        - **每月**
        - **每月（定向）**
        - **半年**
        - **半年（定向）**
    - **自动接受应用最终用户许可协议** - 如果不需要最终用户接受许可协议，请选择此选项。 Intune 随后会自动接受该协议。
    - **使用共享计算机激活** - 当多个用户共享一台计算机时，使用共享计算机激活。 有关详细信息，请参阅 Office 365 的共享计算机激活概述。
    - **语言** - Office 会自动以随 Windows 安装在最终用户设备上的任何受支持的语言进行安装。 如果想要使用应用套件安装其他语言，请选择此选项。

>[!IMPORTANT]
> 创建应用套件后，无法编辑其属性。 若要配置不同的属性，请删除该应用套件并创建一个新的应用套件。

## <a name="finish-up"></a>完成

完成后，在“添加应用”边栏选项卡上，选择“添加”。 创建的应用将显示在应用列表中。

## <a name="error-codes-when-installing-the-app-suite"></a>安装应用套件时的错误代码

下表列出了用户可能会遇到的常见错误代码及其含义。

### <a name="status-for-office-csp"></a>Office CSP 的状态：

||||
|-|-|-|
|状态|阶段|描述|
|1460 (ERROR_TIMEOUT)|下载|下载 Office 部署工具失败|    
|13 (ERROR_INVALID_DATA)|-|无法验证下载的 Office 部署工具的签名|
|来自 CertVerifyCertificateChainPolicy 的错误代码|-|下载的 Office 部署工具的证书检查失败|    
|997|WIP|安装|
|0|安装后|安装成功|    
|1603 (ERROR_INSTALL_FAILURE)|-|任何先决条件检查失败，如：<br>- SxS（尝试在安装 2016 MSI 时安装）<br>- 版本不匹配<br>- 等等。|     
|0x8000ffff (E_UNEXPECTED)|-|尝试在计算机上没有即点即用 Office 时卸载。|    
|17002|-|未能完成方案（安装）。 可能的原因：<br>- 用户取消了安装<br>- 另一个安装取消了安装<br>- 安装期间磁盘空间不足<br>- 未知语言 ID|
|17004|-|未知 SKU|   


### <a name="office-deployment-tool-error-codes"></a>Office 部署工具错误代码

|||||
|-|-|-|-|
|方案|返回代码|UI|备注|
|没有可用的即点即用安装时卸载工作量|-2147418113、0x8000ffff 或 2147549183|错误代码：30088-1008<br>错误代码：30125-1011 (404)|Office 部署工具|
|安装 MSI 版本时安装|1603|-|Office 部署工具|
|用户或另一个安装取消了安装|17002|-|即点即用|
|尝试在安装了 32 位的设备上安装 64 位。|1603|-|Office 部署工具返回代码|
|尝试安装未知的 SKU（不是 Office CSP 的合法用例，因为我们只应传入有效的 SKU）|17004|-|即点即用|
|空间不足|17002|-|即点即用|
|即点即用客户端无法启动（意外）|17000|-|即点即用|
|即点即用客户端无法将方案加入队列（意外）|17001|-|即点即用|

## <a name="next-steps"></a>后续步骤

- 现在可以分配所选的应用组，请参阅[如何将应用分配到组](/intune-azure/manage-apps/deploy-apps)。
