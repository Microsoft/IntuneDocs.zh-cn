---
title: 使用 Microsoft Intune 部署 Windows 10 应用
titleSuffix: ''
description: 了解 Microsoft Intune 提供的 Windows 10 应用部署方案。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: abebfb5e-054b-435a-903d-d1c31767bcf2
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b7772a7476f197f455191debf8e252ba83e06f49
ms.sourcegitcommit: 60ed93682a21860e9d99ba1592ede120477f2b4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2019
ms.locfileid: "72379763"
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

## <a name="windows-10-lob-apps"></a>Windows 10 LOB 应用

可以对 Windows 10 LOB 应用签名，并将它们上传到 Intune 管理控制台。 其中包括通用 Windows 平台 (UWP) 应用和 Windows 应用包 (AppX) 等新式应用，以及简单的 Microsoft Installer 包文件 (MSI) 等 Win 32 应用。 管理员必须手动上传和部署 LOB 应用的更新。 将自动在已安装此应用的用户设备上安装这些更新。 无需用户干预，用户无法控制这些更新。 

## <a name="microsoft-store-for-business-apps"></a>适用于企业的 Microsoft 应用商店应用

适用于企业的 Microsoft Store 应用是从适用于企业的 Microsoft Store 管理门户购买的新式应用。 然后会将它们同步到 Microsoft Intune 进行管理。 这些应用可以在线获得许可或离线获得许可。 Microsoft Store 直接管理更新，管理员无需执行其他操作。管理员还可以使用自定义统一资源标识符 (URI) 阻止对特定应用的更新。 有关详细信息，请参阅 [Enterprise 应用管理 - 防止应用自动更新](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management#prevent-app-from-automatic-updates)。 用户还可以禁用设备上所有适用于企业的 Microsoft Store 应用的更新。 

### <a name="categorize-microsoft-store-for-business-apps"></a>为适用于企业的 Microsoft Store 应用分类 
为适用于企业的 Microsoft Store 应用分类： 

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“客户端应用”   > “应用”  。 选择适用于企业的 Microsoft Store 应用。 然后选择“应用信息”   > “类别”。  
3. 选择类别。

## <a name="install-apps-on-windows-10-devices"></a>在 Windows 10 设备上安装应用
根据应用类型，可以通过以下两种方式之一在 Windows 10 设备上安装应用：

- **用户上下文**：如果应用已在用户上下文中部署，托管应用就会在相应用户登录设备时在设备上为用户安装。 请注意，在用户登录到设备之前，应用安装将不会成功。 
  - 新式业务线应用和适用于企业的 Microsoft Store 应用（在线和离线）可以部署在用户上下文中。 这些应用支持“必需”和“可用”意图。
  - 构建为“用户模式”或“双模式”的 Win32 应用可以部署在用户上下文中，并且支持“必需”和“可用”意图。 
- **设备上下文**：如果应用已在设备上下文中部署，Intune 会将托管应用直接安装到设备中。
  - 只有新式业务线应用和脱机许可的适用于企业的 Microsoft Store 应用，才能在设备上下文中部署。 这些应用仅支持“必需”意图。
  - 构建为“计算机模式”或“双模式”的 Win32 应用可以部署在设备上下文中，并且仅支持“必需”意图。

> [!NOTE]
> 对于构建为“双模式”应用的 Win32 应用，管理员必须选择该应用充当与该实例关联的所有分配的“用户模式”还是“计算机模式”应用。 无法更改每个分配的部署上下文。  

在设备上下文中部署应用时，只有针对支持设备上下文的设备，安装才会成功。 此外，在设备上下文中部署还支持以下条件：
- 若在设备上下文中部署应用并且针对用户，安装将失败。 管理控制台将显示以下状态和错误：
  - 状态:失败。
  - 错误：用户无法成为“设备上下文”安装的目标。
- 若在设备上下文中部署应用，但针对不支持设备上下文的设备，安装将失败。 管理控制台将显示以下状态和错误：
  - 状态:失败。
  - 错误：此平台不支持设备上下文安装。 

> [!Note]
> 使用特定部署保存应用分配后，无法为该分配更改上下文，新式应用除外。 对于新式应用，可以将上下文从用户上下文更改为设备上下文。 

若对单个用户或设备的策略存在冲突，则应用以下优先级：
- 设备上下文策略的优先级高于用户上下文策略。 
- 安装策略的优先级高于卸载策略。

有关详细信息，请参阅[在 Microsoft Intune 中包括和排除应用分配](apps-inc-exl-assignments.md)。 有关 Intune 中应用类型的详细信息，请参阅[向 Microsoft Intune 添加应用](apps-add.md)。

## <a name="next-steps"></a>后续步骤

- [使用 Microsoft Intune 将应用分配到组](apps-deploy.md)
- [如何监视应用](apps-monitor.md)
