---
title: "在 Intune 迁移过程中配置设备符合性和应用管理策略 | Microsoft Docs"
description: "本文主旨是在 Intune 迁移过程中提供配置设备符合性和应用管理策略的必要步骤。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0062d08e-e5b3-4f73-8b64-5ad95adbe945
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab5aa4e12d951d818c5afb4e1ac5e866b05733fb
ms.openlocfilehash: 5904b117ccab9046d2afde4a761b4724431a6302
ms.lasthandoff: 03/27/2017


---

# <a name="phase-1-configure-device-compliance-and-app-management-policies"></a>阶段 1：配置设备符合性和应用管理策略

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

迁移到 Intune 时的主要目标是注册所有设备，并使设备符合其策略。 设备策略不仅可以帮助你管理公司所有的单用户设备，而且还可以帮助管理个人 (BYOD) 和共享设备，例如，展台、销售终端系统机器、教室内由多名学生共享的平板电脑，或者无用户设备（仅限 iOS）。

每个设备平台可能会提供不同的设置，但 Intune 设备策略通过提供以下移动设备管理功能用于每个设备平台：

-   控制每个用户注册的设备数。

-   管理设备设置（如设备级别的加密、密码长度、照相机使用情况）。

-   提供应用、电子邮件配置文件、VPN 配置文件等等。

-   评估安全符合性策略的设备级条件。

> [!IMPORTANT]
> 设备管理策略不直接分配给单个设备或用户，而是分配给用户组。 策略可能直接应用到用户组，从而应用到用户设备，或者策略可能应用到设备组，并因此应用到组成员。

## <a name="task-list-for-device-compliance-policies"></a>设备符合性策略的任务列表

### <a name="task-1-add-device-groups-optional"></a>任务 1：添加设备组（可选）

通过 [Intune 经典门户](https://manage.microsoft.com/)在需要执行基于设备标识而不是用户标识的各种管理任务时，能够创建设备组。

设备组可用于管理无专用用户的设备，例如展台设备或由轮班工作人员共享的或分配给特定位置的设备。

通过在设备注册前配置设备组，你可以利用设备类别在注册时自动分组设备，以自动接收组的设备策略。

-   了解[如何添加设备组](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)。

-   了解[如何配置设备类别](https://docs.microsoft.com/intune/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune)。

### <a name="task-2-use-resource-access-profiles-wi-fi-vpn-and-email-certificates"></a>任务 2：使用资源访问配置文件（Wi-Fi、VPN 和电子邮件证书）

资源访问配置文件设置证书以及对注册设备的访问权限配置。

如前面的“评估 MDM 要求”部分所述，如果使用基于证书的身份验证，则需要具有[PKI 基础结构](https://docs.microsoft.com/intune/deploy-use/secure-resource-access-with-certificate-profiles)来部署 VPN、Wi-fi、和电子邮件证书。

#### <a name="direct-import-of-resource-access-profiles-optional"></a>直接导入资源访问配置文件（可选）

如果现有的 MDM 解决方案提供一种机制以 XML 格式导出电子邮件、Wi-fi 和 VPN 配置文件，则可以利用 XML 文件并只需通过使用 OMA-URI 将其导入 Intune，创建适用于 iOS、Android 和 Windows 设备的自定义配置文件。

-   了解如何添加适用于 [iOS](https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune)、[Android](https://docs.microsoft.com/intune/deploy-use/android-policy-settings-in-microsoft-intune) 和 [Windows](https://docs.microsoft.com/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune) 设备的自定义策略。

### <a name="task-3-create-and-deploy-device-configuration-profiles"></a>任务 3：创建和部署设备配置文件

需要创建设备配置文件以强制实施设备级设置，例如：禁用相机、应用商店、配置单应用模式、主屏幕等等。

- 了解[设备配置描述文件](https://docs.microsoft.com/intune-azure/configure-devices/how-to-create-device-profiles)。

####  <a name="direct-import-of-ios-configuration-profiles-optional"></a>直接导入 iOS 配置描述文件（可选）

-   **Apple 配置器 iOS 配置文件（iOS 7.1 及更高版本）：**如果你现有的 MDM 解决方案使用 Apple配置器配置文件（.mobileconfig 文件），Intune 可以直接导入它们作为自定义配置策略。

-   **iOS 移动应用程序配置策略：**如果你现有的 MDM 解决方案使用 iOS 移动应用程序配置策略，Intune 可以直接将其导入，前提是它们符合 Apple 针对属性列表指定的 XML 格式。

- 了解如何添加适用于 [iOS](https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune#custom-policy-settings) 的自定义策略

### <a name="task-4-create-and-deploy-device-compliance-policies-optional"></a>任务 4：创建和部署设备符合性策略（可选）

设备符合性策略评估以安全为目标的设置，并提供显示设备是否符合企业标准的报告。 设备符合性策略评估以安全为目标的因素，如：

-   PIN 长度

-   越狱状态

-   操作系统版本

请参阅有关设备符合性设置的其他资源：

-   了解[设备符合性策略](https://docs.microsoft.com/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune)。

-   了解[如何创建设备符合性策略](https://docs.microsoft.com/intune/deploy-use/create-a-device-compliance-policy-in-microsoft-intune)。

### <a name="task-5-publish-and-deploy-apps"></a>任务 5：发布和部署应用

在使用 Intune MDM 时，可以通过要求其自动安装，或使它们在公司门户中可用的方式来设置应用。

-   了解[如何添加应用](https://docs.microsoft.com/intune/deploy-use/add-apps)。

-   了解[如何部署应用](https://docs.microsoft.com/intune/deploy-use/deploy-apps)。

### <a name="task-6-enable-device-enrollment"></a>任务 6：启用设备注册

注册通过在设备上设置控制来建立管理。

-   了解[如何准备注册公司所有的设备和用户的个人设备](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune)。

-   了解[如何注册公司所有的设备](https://docs.microsoft.com/intune/deploy-use/manage-corporate-owned-devices)。

如果你需要注册共享设备或无用户设备，可以使用[设备注册管理器 (DEM) 帐户](https://docs.microsoft.com/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)。

## <a name="next-steps"></a>后续步骤 

[阶段 1：配置应用保护策略（可选）](https://docs.microsoft.com/intune/plan-design/migration-phase1-configure-app-protection-policies)

