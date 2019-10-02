---
title: 使用 Microsoft Intune 管理操作系统版本
titleSuffix: Microsoft Intune
description: 了解如何使用 Microsoft Intune 跨平台管理操作系统版本。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 361ef17b-1ee0-4879-b7b1-d678b0787f5a
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3be329e5b84f307c2683bc3799ff9cd6deafe729
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726006"
---
# <a name="manage-operating-system-versions-with-intune"></a>使用 Intune 管理操作系统版本
在新式移动和桌面平台上，主要更新、修补程序和新版本的发布速度很快。 你在 Windows 上具有完全管理更新和修补程序的控制权限，但在 iOS 和 Android 等平台上，最终用户也需参与此过程。  Microsoft Intune 可帮助构建跨不同平台的操作系统版本管理。

Intune 能解决的常见方案包括： 
- 判断最终用户设备上采用的操作系统版本
- 在验证新的操作系统发布时，控制对设备上组织数据的访问
- 鼓励/要求最终用户升级到经组织批准的最新操作系统版本
- 管理组织范围内新操作系统版本的推出
  
## <a name="operating-system-version-control-using-intune-mobile-device-management-mdm-enrollment-restrictions"></a>使用 Intune 移动设备管理 (MDM) 注册限制的操作系统版本控制
Intune MDM 注册限制让你可以定义客户端设备要求，然后再允许设备注册。 其目的是要求最终用户在获得访问组织资源的权限之前，仅注册符合的设备。 设备要求包括受支持的平台上所允许的最低和最高操作系统版本。

![平台配置限制边栏选项卡](./media/manage-os-versions/os-version-platform-configurations.png)

### <a name="in-practice"></a>具体实践

组织使用设备类型限制来控制对组织资源的访问，其设置如下所示：

1. 使用最低操作系统版本，确保最终用户处于组织中当前和受支持的平台上。
2. 不指定最高操作系统（无限制），或将其设置为组织中最新验证的版本，以便为新操作系统发布的内部测试留出时间。

有关详细信息，请参阅[设置设备类型限制](../enrollment/enrollment-restrictions-set.md#create-a-device-type-restriction)。

## <a name="operating-system-version-reporting-and-compliance-with-intune-mdm-device-compliance-policies"></a>操作系统版本报告和对 Intune MDM 设备符合性策略的符合性

Intune MDM 设备符合性策略提供以下工具：

- 指定符合性规则
- 通过报告查看符合性状态
- 通过设备隔离和条件访问处理不符合性

与注册限制类似，设备符合性策略同时包含最低和最高操作系统版本。 策略还具有符合性时间线，以向你的用户提供用于获得符合性的宽限期。 设备符合性策略可确保所注册的最终用户设备符合组织策略。

![设备符合性 - 针对不符合设备的操作](./media/manage-os-versions/os-version-actions-noncompliance.png)

### <a name="in-practice"></a>具体实践
对于相同的方案，组织正使用与注册限制一致的设备符合性策略。 这些策略确保用户处于组织中已验证的当前操作系统版本。 当最终用户设备不符合时，可通过条件访问阻止其对组织资源的访问，直至最终用户处于受组织支持的操作系统范围内。 将不符合状态通知给最终用户，并为其提供重获访问权限的步骤。   

有关详细信息，请参阅[设备符合性入门](../protect/device-compliance-get-started.md)。
 
## <a name="operating-system-version-controls-using-intune-app-protection-policies"></a>使用 Intune 应用保护策略的操作系统版本控制    
使用 Intune 应用保护策略和移动应用程序管理 (MAM) 访问设置，可在应用层级指定最低操作系统版本。 如此一来便可通知、鼓励或要求最终用户将操作系统更新至指定的最低版本。
 
有两种不同选项： 
- **警告** - 如果最终用户打开具有应用程序保护策略的应用，或对于具有 MAM 访问设置的设备，其操作系统版本低于指定版本，则“警告”将通知最终用户需进行升级。 允许访问应用和组织数据。
  ![Android 更新警告对话框示意图](./media/manage-os-versions/os-version-update-warning.png) 

- **阻止** - 如果最终用户打开具有应用程序保护策略的应用，或对于具有 MAM 访问设置的设备，其操作系统版本低于指定版本，则“阻止”将通知最终用户必须进行升级。 不允许访问应用和组织数据。
  ![已阻止应用访问对话框示意图](./media/manage-os-versions/os-version-access-blocked.png)

### <a name="in-practice"></a>具体实践
当前，在打开或恢复应用时，组织通过使用应用保护策略设置提醒最终用户需确保其应用处于最新版本。 例如这个示例配置：如果版本为最新版本减一，则将警告最终用户；如果版本为最新版本减二，则将阻止最终用户。
 
有关详细信息，请参阅[如何创建和分配应用保护策略](../apps/app-protection-policies.md)。

## <a name="managing-a-new-operating-system-version-rollout"></a>管理新操作系统版本的推出
可使用本文所述 Intune 功能，在自定义的时间线内将组织移至新操作系统版本。 以下是关于某个示例部署模型的步骤说明，该示例在七天内将用户从操作系统 v1 移至操作系统 v2。
- **步骤 1**：使用注册限制将操作系统 v2 作为注册设备的最低版本。 此操作确保新的最终用户设备在注册时满足符合性。
- **步骤 2a**：使用 Intune 应用保护策略，在应用打开或恢复时，警告用户他们需要操作系统 v2。
- 步骤 2b  。 使用设备符合性策略，将操作系统 v2 作为使设备获得符合性的最低版本。 使用针对不符合性的操作，允许七天的宽限期，并向最终用户发送包含时间线和要求的电子邮件通知  。
  - 这些策略将通过电子邮件或 Intune 公司门户，以及在打开启用了应用保护策略的应用时，告知最终用户现有设备需要更新。
  - 可运行符合性报告来标识不符合的用户。 
- **步骤 3a**：使用 Intune 应用保护策略，在设备未运行操作系统 v2 的情况下，当应用打开或恢复时阻止用户。
- **步骤 3b**：使用设备符合性策略，将操作系统 v2 作为使设备获得符合性的最低版本。
  - 这些策略要求更新设备，以便继续访问组织数据。 当与设备条件访问配合使用时，受保护的服务将被阻止。 启用了应用保护策略的应用在打开时或访问组织数据时将被阻止。

## <a name="next-steps"></a>后续步骤

使用以下资源在组织中管理操作系统版本：

- [设置设备类型限制](../enrollment/enrollment-restrictions-set.md#create-a-device-type-restriction)
- [设备符合性入门](../protect/device-compliance-get-started.md)
- [如何创建和分配应用保护策略](../apps/app-protection-policies.md)
