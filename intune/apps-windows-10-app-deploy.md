---
title: 使用 Microsoft Intune 部署 Windows 10 应用
titlesuffix: ''
description: 了解 Microsoft Intune 提供的 Windows 10 应用方案。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/31/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: abebfb5e-054b-435a-903d-d1c31767bcf2
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7508f2c2eca06ceacf203103ab2cad53abc39a65
ms.sourcegitcommit: 2d1e89fa5fa721e79648e41fde147a035e7b047d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2018
ms.locfileid: "43347426"
---
# <a name="windows-10-app-deployment-using-microsoft-intune"></a>使用 Microsoft Intune 部署 Windows 10 应用 

Microsoft Intune 当前支持 Windows 10 设备上的各种应用类型和部署方案。 向 Intune 添加应用后，可将应用分配给用户和设备。 以下信息提供了与支持的 Windows 10 方案相关的详细信息。 此外，以下信息还提供了在将应用部署到 Windows 时要注意的关键详细信息。 

业务线 (LOB) 应用和适用于企业的 Microsoft Store 应用是 Windows 10 设备支持的应用类型。

> [!Note]
> 在设备上下文中部署应用所需的最低版本的 Windows 10 更新是 [2018 年 5 月 23 日 - KB4100403（OS 内部版本 17134.81）](https://support.microsoft.com/en-us/help/4100403/windows-10-update-kb4100403)。

## <a name="windows-10-line-of-business-apps"></a>Windows 10 业务线应用

Windows 10 LOB 应用已签名并上传到 Intune 管理控制台，并且可以包括通用 Windows 平台 (UWP) 应用和 Windows 应用包 (AppX) 等现代应用，以及简单的 Microsoft Installer 包文件 (MSI) 等 Win 32 应用。 每次必须由管理员手动上传和部署 LOB 应用的更新。部署的更新将自动安装在已安装应用且无需用户干预的最终用户设备上。 用户无法控制更新。 

## <a name="microsoft-store-for-business-apps"></a>适用于企业的 Microsoft 应用商店应用

适用于企业的 Microsoft Store 应用是从适用于企业的 Microsoft Store 管理门户购买的现代应用，然后同步到 Microsoft Intune 进行管理。 这些应用可以在线获得许可或离线获得许可。 适用于企业的 Microsoft Store 应用的更新由 Microsoft Store 直接管理，管理员无需执行其他操作。管理员还可以使用自定义统一资源标识符 (URI) 阻止对特定应用的更新。 有关详细信息，请参阅 [Enterprise 应用管理 - 防止应用自动更新](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management#prevent-app-from-automatic-updates)。 在设备上，最终用户还可以禁用设备上所有适用于企业的 Microsoft Store 应用的更新。 

## <a name="installing-apps-on-windows-10-devices"></a>在 Windows 10 设备上安装应用
根据应用类型，可以通过以下两种方式在 Windows 10 设备上安装应用：

- 用户上下文：在用户上下文中部署应用时，当用户登录设备时，将在该设备上为该用户安装托管应用。 请注意，在用户登录到设备之前，应用安装将不会成功。 
    - 现代业务线应用和适用于企业的 Microsoft Store 应用（在线和离线）可以部署在用户上下文中，并且支持“必需”和“可用”意图。
- 设备上下文：在设备上下文中部署应用时，Intune 会将托管应用直接安装到设备中。
    - 只有现代业务线应用和在线许可的适用于企业的 Microsoft Store 应用才能在设备上下文中部署，并且仅支持“必需”意图。

> [!Note]
> Windows 10 设备尚不支持在设备上下文中通过 MDM 部署 MSI。

在设备上下文中部署应用时，只有针对支持设备上下文的设备，安装才会成功。 此外，在设备上下文中部署还支持以下条件：
- 如果应用部署在设备上下文中并针对用户，则安装会失败，并在管理控制台中显示以下状态和错误：
    - 状态：失败。
    - 错误：无法针对用户进行设备上下文安装。
- 如果应用部署在设备上下文中但针对的是不支持设备上下文的设备，则安装会失败，并在管理控制台中显示以下状态和错误：
    - 状态：失败。
    - 错误：此平台不支持设备上下文安装。 

> [!Note]
> 使用特定部署保存应用分配后，无法为该分配更改上下文，现代应用除外。 针对现代应用的情况，可以将上下文从用户上下文更改为设备上下文。 

如果单个用户/设备上的策略存在冲突，则以下策略优先级将用于确定最终策略：
- 设备上下文策略的优先级高于用户上下文策略。 
- 安装策略的优先级高于卸载策略。

有关使用 Microsoft Intune 分配应用的详细信息，请参阅[使用 Microsoft Intune 将应用分配到组](apps-deploy.md)以及[在 Microsoft Intune 中包括和排除应用分配](apps-inc-exl-assignments.md)。 有关 Intune 中应用类型的详细信息，请参阅[向 Microsoft Intune 添加应用](apps-add.md)。

## <a name="next-steps"></a>后续步骤

- 要了解有关将应用分配到组的详细信息，请参阅[使用 Microsoft Intune 将应用分配到组](apps-deploy.md)。
- 要了解有关监视应用分配的详细信息，请参阅[如何监视应用](apps-monitor.md)。
