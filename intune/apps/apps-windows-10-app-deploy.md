---
title: 使用 Microsoft Intune 部署 Windows 10 应用
titleSuffix: ''
description: 了解 Microsoft Intune 提供的 Windows 10 应用部署方案。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/30/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: abebfb5e-054b-435a-903d-d1c31767bcf2
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fa4510b95e1e84d9f94158833dac555daa33c690
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912550"
---
# <a name="windows-10-app-deployment-by-using-microsoft-intune"></a>使用 Microsoft Intune 部署 Windows 10 应用 

Microsoft Intune 支持 Windows 10 设备上的各种应用类型和部署方案。 向 Intune 添加应用后，可将应用分配给用户和设备。 本文详细说明了支持的 Windows 10 方案，并且还介绍了将应用部署到 Windows 时要注意的重要细节。 

业务线 (LOB) 应用和适用于企业的 Microsoft Store 应用是 Windows 10 设备支持的应用类型。 Windows 应用的文件扩展名包括 .msi、.appx 和 .appxbundle。  

> [!Note]
> 至少要满足以下条件才可部署新式应用：
> - 对于 Windows 10 1803，[2018 年 5 月 23 日 - KB4100403（操作系统内部版本 17134.81）](https://support.microsoft.com/help/4100403/windows-10-update-kb4100403)。
> - 对于 Windows 10 1709，[2018 年 6 月 21 日 - KB4284822（操作系统内部版本 16299.522）](https://support.microsoft.com/help/4284822)。
>
> 如果未关联主要用户，只有 Windows 10 1803 及更高版本支持安装应用。
>
> 在运行 Windows 10 家庭版的设备上不支持 LOB 应用部署。

## <a name="supported-windows-10-app-types"></a>支持的 Windows 10 应用类型

支持的特定应用类型取决于用户运行的 Windows 10 版本。 下表提供了应用类型和 Windows 10 支持。

| 应用类型 | 主页 | Pro | Microsoft Store | 企业 | 教育水平 | S 模式 | Hololense | SurfaceHub | WCOS | 移动电话 |
|----------------|------|-----|----------|------------|-----------|--------|-----------|------------|------|--------|
|  .MSI | 否 | 是 | 是 | 是 | 是 | 否 | 否 | 否 | 否 | 否 |
| .IntuneWin | 否 | 是 | 是 | 是 | 是 | 19H2+ | 否 | 否 | 否 | 否 |
| Office C2R | 否 | 是 | 是 | 是 | 是 | 否 | 否 | 否 | 否 | 否 |
| LOB：APPX/MSIX | 是 | 是 | 是 | 是 | 是 | 是 | 是 | 是 | 是 | 是 |
| MSFB 脱机 | 是 | 是 | 是 | 是 | 是 | 是 | 是 | 是 | 是 | 是 |
| MSFB 在线 | 是 | 是 | 是 | 是 | 是 | 是 | RS4+ | 是 | 是 | 是 |
| Web 应用 | 是 | 是 | 是 | 是 | 是 | 是 | 是<sup>1 | 是<sup>1 | 是 | 是 |
| 商店链接 | 是 | 是 | 是 | 是 | 是 | 是 | 是 | 是 | 是 | 是 |

<sup>1</sup> 仅从公司门户启动。

> [!NOTE]
> 所有 Windows 应用类型都需要注册。

## <a name="windows-10-lob-apps"></a>Windows 10 LOB 应用

可以对 Windows 10 LOB 应用签名，并将它们上传到 Intune 管理控制台。 其中包括通用 Windows 平台 (UWP) 应用和 Windows 应用包 (AppX) 等新式应用，以及简单的 Microsoft Installer 包文件 (MSI) 等 Win 32 应用。 管理员必须手动上传和部署 LOB 应用的更新。 将自动在已安装此应用的用户设备上安装这些更新。 无需用户干预，用户无法控制这些更新。 

## <a name="microsoft-store-for-business-apps"></a>适用于企业的 Microsoft Store 应用

适用于企业的 Microsoft Store 应用是从适用于企业的 Microsoft Store 管理门户购买的新式应用。 然后会将它们同步到 Microsoft Intune 进行管理。 这些应用可以在线获得许可或离线获得许可。 Microsoft Store 直接管理更新，管理员无需执行其他操作。管理员还可以使用自定义统一资源标识符 (URI) 阻止对特定应用的更新。 有关详细信息，请参阅 [Enterprise 应用管理 - 防止应用自动更新](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management#prevent-app-from-automatic-updates)。 用户还可以禁用设备上所有适用于企业的 Microsoft Store 应用的更新。 

### <a name="categorize-microsoft-store-for-business-apps"></a>为适用于企业的 Microsoft Store 应用分类 
为适用于企业的 Microsoft Store 应用分类： 

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 选择“应用”   > “所有应用”  。 
3. 选择适用于企业的 Microsoft Store 应用。 然后选择“属性”   > “应用信息”   > “类别”  。 
4. 选择类别。

## <a name="install-apps-on-windows-10-devices"></a>在 Windows 10 设备上安装应用
根据应用类型，可以通过以下两种方式之一在 Windows 10 设备上安装应用：

- **用户上下文**：如果应用已在用户上下文中部署，托管应用就会在相应用户登录设备时在设备上为用户安装。 请注意，在用户登录到设备之前，应用安装将不会成功。 
  - 新式 LOB 应用和适用于企业的 Microsoft Store 应用（在线和离线）可以部署在用户上下文中。 这些应用支持“必需”和“可用”意图。
  - 构建为“用户模式”或“双模式”的 Win32 应用可以部署在用户上下文中，并且支持“必需”和“可用”意图。 
- **设备上下文**：如果应用已在设备上下文中部署，Intune 会将托管应用直接安装到设备中。
  - 只有新式 LOB 应用和脱机许可的适用于企业的 Microsoft Store 应用，才能在设备上下文中部署。 这些应用仅支持“必需”意图。
  - 构建为“计算机模式”或“双模式”的 Win32 应用可以部署在设备上下文中，并且仅支持“必需”意图。

> [!NOTE]
> 对于构建为“双模式”应用的 Win32 应用，管理员必须选择该应用充当与该实例关联的所有分配的“用户模式”还是“计算机模式”应用。 无法更改每个分配的部署上下文。  

只有在设备和 Intune 应用类型支持的情况下，才能在设备上下文中安装应用。 可以在设备上下文中安装以下应用类型，并将这些应用分配给设备组：

- Win32 应用
- 获得许可的适用于企业的 Microsoft Store 脱机应用
- LOB 应用（MSI、APPX 和 MSIX）
- Office 365 专业增强版

已在设备上下文中选择要安装的 Windows LOB 应用（特别是 APPX 和 MSIX）和适用于企业的 Microsoft Store 应用（脱机应用）必须分配给设备组。 如果在用户上下文中部署了其中一个应用，安装将失败。 管理控制台将显示以下状态和错误：
  - 状态：失败。
  - 错误：用户无法成为“设备上下文”安装的目标。

> [!IMPORTANT]
> 与 Autopilot 白色手套预配方案结合使用时，在设备上下文中部署的 LOB 应用和适用于企业的 Microsoft Store 应用不需要面向设备组。 有关详细信息，请参阅 [Windows Autopilot 白色手套部署](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove)。

> [!Note]
> 使用特定部署保存应用分配后，无法为该分配更改上下文，新式应用除外。 对于新式应用，可以将上下文从用户上下文更改为设备上下文。 

若对单个用户或设备的策略存在冲突，则应用以下优先级：
- 设备上下文策略的优先级高于用户上下文策略。 
- 安装策略的优先级高于卸载策略。

有关详细信息，请参阅[在 Microsoft Intune 中包括和排除应用分配](apps-inc-exl-assignments.md)。 有关 Intune 中应用类型的详细信息，请参阅[向 Microsoft Intune 添加应用](apps-add.md)。

## <a name="next-steps"></a>后续步骤

- [使用 Microsoft Intune 将应用分配到组](apps-deploy.md)
- [如何监视应用](apps-monitor.md)
