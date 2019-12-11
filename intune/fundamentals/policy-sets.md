---
title: 策略集
titleSuffix: Microsoft Intune
description: 使用策略集对 Microsoft Intune 中的管理对象集合进行分组。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e539f44fc9c9b4e7382368c0f3ad9f79bb1c98b1
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72585652"
---
# <a name="use-policy-sets-to-group-collections-of-management-objects"></a>使用策略集对管理对象集合进行分组

策略集允许创建对现有管理实体的一系列引用，这些实体需要作为单个概念单元进行标识、定位和监视。 策略集是你创建的应用、策略和其他管理对象的可分配集合。 创建策略集使你能够同时选择许多不同的对象，并从单个位置分配它们。 随着组织变动，可以重新访问策略集，添加或删除其对象和分配。 可以使用策略集来关联和分配单个包中的现有对象，如应用、策略和 VPN。 

> [!IMPORTANT]
> 与策略集相关的已知问题列表见[策略集已知问题](~/fundamentals/policy-sets.md#policy-sets-known-issues)。

策略集不会替换现有的概念或对象。 你可以继续分配各个对象，也可以将各个对象作为策略集的一部分进行引用。 因此，对各对象的任何更改都将反映在策略集中。 

可使用策略集执行以下操作：

- 组合需要一起分配的对象
- 在所有受管理设备上分配组织的最低配置要求
- 将常用或相关应用分配到所有用户

可以在策略集中包含以下管理对象：
- 应用
- 应用配置策略
- 应用保护策略
- 设备配置文件
- 设备合规性策略
- 设备类型限制
- Windows Autopilot 部署配置文件
- 注册状态页

创建策略集时，将创建单个分配单元，并管理不同对象之间的关联。 策略集将是对其外部对象的引用。 所包含对象中的任何更改也将影响策略集。 创建策略集后，可以重复查看和编辑其对象和分配。 

> [!NOTE]
> 策略集支持 Windows、Android、macOS 和 iOS 设置，并且可跨平台进行分配。

## <a name="how-to-create-a-policy-set"></a>如何创建策略集

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 在“Intune”边栏选项卡上，选择“策略集” > “策略集” > “创建”     。
3. 在“基本信息”页上，添加以下值  ：
    - **策略集名称** - 提供此策略集的名称。
    - **说明** -（可选）提供策略集的说明。
   <p>
   <img alt="Create policy set - Basics" src="~/fundamentals/media/policy-sets/policy-sets-01.png">

4. 单击“下一步:  应用程序管理”。<br>
   在“应用程序管理”页面，可以选择[添加应用](~/apps/apps-add.md)、[应用配置策略](~/apps/app-configuration-policies-overview.md)和[应用保护策略](~/apps/app-protection-policy.md)到策略集  。 有关应用管理的信息，请参阅[什么是 Microsoft Intune 应用管理？](~/apps/app-management.md)。 
5. 单击“下一步:  设备管理”。<br>
   通过“设备管理”页面，可以将设备管理对象添加到策略集，例如[设备配置文件](~/configuration/device-profiles.md)和[设备符合性策略](~/protect/device-compliance-get-started.md)  。 请确保包含所有关联的对象，例如其他策略、证书和安全基线配置文件。
6. 单击“下一步:  设备注册”。<br>
   通过“设备注册”页面，可以将设备注册对象添加到策略集，例如[设备类型限制](~/enrollment/enrollment-restrictions-set.md)、[Windows Autopilot 部署配置文件](~/enrollment/enrollment-autopilot.md)和[注册状态页配置文件](~/enrollment/windows-enrollment-status.md)  。
7. 单击“下一步:  分配”。<br>
   通过“分配”页面，可以将策略集分配到用户和设备  。 值得注意的是，无论设备是否由 Intune 管理，都可以将策略集分配到设备。
8. 单击“**下一步:查看 + 创建**”以查看你为配置文件输入的值。
9. 完成后，单击“创建”以在 Intune 中创建策略集  。 

## <a name="policy-sets-known-issues"></a>策略设置已知问题

策略集是 1910 版本的新增内容，存在以下已知问题。

- 创建策略集时，如果作用域管理员尝试在未选择任何作用域标记的情况下创建策略集，则在到达“查看 + 创建”页面时，验证将失败，并在状态栏上显示错误  。 管理员必须在过程中切换到其他页面，然后返回“查看 + 创建”页面  。 这将启用“创建”选项  。  
 
- 策略集当前支持以下应用类型：
    - iOS 应用商店应用
    - iOS 业务线应用
    - 托管 iOS 业务线应用
    - Android 应用商店应用
    - Android 业务线应用
    - 托管 Android 业务线应用
    - Office 365 专业增强版套件 (Windows 10)
    - Web 链接
    - 内置的 iOS 应用
    - 内置的 Android 应用

- 不支持将“所有用户”的策略集分配设置为“Autopilot 配置文件”   。

- 策略集具有以下注册限制和注册状态页 (ESP) 问题：
    - 限制和 ESP 不支持虚拟组分配。
    - 限制和 ESP 不严格支持排除组分配。 
    - 限制和 ESP 使用基于优先级的冲突解决。 如果限制和 ESP 也是更高优先级限制和 ESP 的目标，则限制和 ESP 可能不会应用于与策略集的其余有效负载相同的用户。
    - 无法将默认限制和 ESP 添加到策略集。

- 支持策略集的 MAM 策略类型包括： 
    - MAM WIP (Windows) MDM 目标托管应用保护 
    - MAM iOS 目标托管应用保护
    - MAM Android 目标托管应用保护
    - MAM iOS 目标托管应用配置
    - MAM Android 目标托管应用配置

- 不支持策略集的 MAM 策略类型包括： 
    - MAM WIP (Windows) 目标托管应用保护

- MAM 将策略集分配作为以下策略类型的直接分配进行处理：
    - MAM iOS 目标托管应用保护
    - MAM Android 目标托管应用保护
    - MAM iOS 目标托管应用配置
    - MAM Android 目标托管应用配置

    如果将策略添加到部署到组的策略集中，则该组将显示为在工作负荷中直接分配，而不是“通过策略集分配”。 因此，MAM 不处理来自策略集的组分配删除。

- 对于任何策略类型，MAM 不支持部署到“所有用户”和“所有设备”虚拟组   。

## <a name="next-steps"></a>后续步骤

- [在 Microsoft Intune 中注册设备](~/enrollment/index.yml)