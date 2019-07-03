---
title: 在 Intune 迁移过程中配置设备和应用符合性
titleSuffix: Microsoft Intune
description: 本文提供在 Microsoft Intune 迁移过程中配置设备符合性和应用管理策略的必要步骤。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0062d08e-e5b3-4f73-8b64-5ad95adbe945
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9a5f28f01d0c8be6692deaf27391e52619fcdcab
ms.sourcegitcommit: 84c79ceea27f7411528defc5ee8ba35ae2bf473c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67512267"
---
# <a name="configure-device-compliance-and-app-management-policies-when-migrating-to-microsoft-intune"></a>在迁移到 Microsoft Intune 时，配置设备符合性和应用管理策略

迁移到 Intune 时的主要目标是在 Intune 中注册所有设备，并使设备符合其策略。 设备策略不仅可以帮助你管理公司拥有的单用户设备，而且还可以帮助管理个人 (BYOD) 和共享设备，例如，展台、销售终端系统机器、教室内由多名学生共享的平板电脑，或者无用户设备（仅限 iOS）。

每个设备平台可能会提供不同的设置，但 Intune 设备策略通过提供以下移动设备管理功能用于每个设备平台：

-   控制每个用户注册的设备数。

-   管理设备设置（如设备级别的加密、密码长度、照相机使用情况）。

-   提供应用、电子邮件配置文件、VPN 配置文件等。

-   评估安全符合性策略的设备级条件。

> [!IMPORTANT]
> 设备管理策略不直接分配给单个设备或用户，而是分配给用户组。 策略可能直接应用到用户组，从而应用到用户设备，策略也可能应用到设备组，并因此应用到组成员。

## <a name="task-list-for-device-compliance-policies"></a>设备符合性策略的任务列表

### <a name="task-1-add-device-groups-optional"></a>任务 1：添加设备组（可选）

如果需要执行基于设备标识而不是用户标识的管理任务，此时可以创建设备组。

设备组可用于管理无专用用户的设备，例如展台设备、由轮班工作人员共享的设备或分配给特定位置的设备。

通过在设备注册前配置设备组，可以利用设备类别在注册时自动将设备加入组。 然后设备将自动接收其所在组的设备策略。 [组入门](groups-get-started.md)。

### <a name="task-2-use-resource-access-profiles-wi-fi-vpn-and-email-certificates"></a>任务 2：使用资源访问配置文件（Wi-Fi、VPN 和电子邮件证书）

资源访问配置文件提供注册设备的证书和访问配置。 如果使用基于证书的身份验证，请[配置证书](certificates-configure.md)。

### <a name="task-3-create-and-deploy-device-configuration-profiles"></a>任务 3：创建和部署设备配置配置文件

需要创建设备配置的配置文件以强制实施设备级设置，例如：禁用照相机、应用商店、配置单应用模式、主屏幕等等。 了解[设备配置文件](device-profiles.md)。

#### <a name="directly-import-ios-configuration-profiles-optional"></a>直接导入 iOS 配置的配置文件（可选）

-   **Apple Configurator iOS 配置文件（iOS 7.1 及更高版本）：** 如果现有 MDM 解决方案使用 Apple Configurator 配置文件（.mobileconfig 文件），Intune 可以直接导入它们作为自定义配置策略。

-   **iOS 移动应用配置策略：** 如果现有 MDM 解决方案使用 iOS 移动应用配置策略，Intune 可以直接导入它们，前提是它们符合 Apple 针对属性列表指定的 XML 格式。

- 了解如何添加适用于 [iOS](custom-settings-ios.md) 的自定义策略。

### <a name="task-4-create-and-deploy-device-compliance-policies-optional"></a>任务 4：创建和部署设备符合性策略（可选）

设备符合性策略评估以安全为目标的设置，并提供显示设备是否符合企业标准的报告。 此类设置包括：

-   PIN 长度

-   越狱状态

-   OS 版本

请参阅有关设备符合性设置的其他资源：

-   了解[设备符合性策略](device-compliance.md)。

-   了解[如何创建设备符合性策略](device-compliance-get-started.md)。

### <a name="task-5-publish-and-deploy-apps"></a>任务 5：发布和部署应用

使用 Intune MDM 时，可以通过要求其自动安装，或使它们在公司门户中可用的方式来提供应用。

-   [如何添加应用](apps-add.md)。

-   [如何部署应用](apps-deploy.md)。

### <a name="task-6-enable-device-enrollment"></a>任务 6：启用设备注册

要管理设备，则必须注册设备。 了解[如何准备注册公司所有的设备和用户的个人设备](device-enrollment.md)。

## <a name="next-steps"></a>后续步骤

[配置应用保护策略（可选）](migration-guide-app-protection-policies.md)。
