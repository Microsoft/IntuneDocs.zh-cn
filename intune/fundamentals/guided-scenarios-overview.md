---
title: 指导方案概述
titleSuffix: Microsoft Intune
description: 了解 Microsoft 365 设备管理门户中可用的 Intune 引导式方案。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b833e5265387637a35bfcdf79f4ae5f37558de61
ms.sourcegitcommit: 637375a390b6e34f9c4415c77b99fe2980bbf554
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2020
ms.locfileid: "75839139"
---
# <a name="intune-guided-scenarios-overview"></a>Intune 引导式方案概述 

引导式方案是围绕一个端到端用例而定制的一系列步骤。 常见方案基于管理员、用户或设备在组织中扮演的角色。 这些角色通常需要精心设计的配置文件、设置、应用程序和安全控件的集合，以提供最佳的用户体验和安全性。    

如果不熟悉实现特定 Intune 方案所需的所有步骤和资源则可以使用引导式方案作为起点。 引导式方案将自动组合策略、应用、分配和其他管理配置。 此外，引导式方案可能会故意省略某些不适用或不常用于给定方案的选项。 

引导式方案与 Intune 的不是常规工作流以外的管理空间。 这些工作流旨在与 Intune 现有的配置文件、应用和策略工作流一起使用。 完成引导式方案后，该方案的所有未来管理都必须在策略、应用和配置文件的现有菜单中进行。 引导式方案不会保存“引导式方案”资源类型或跟踪将来对资源的更改。 由引导式方案创建的每个资源都将出现在其各自的工作负荷中。 所有选项，甚至在引导式方案中省略的选项，都可在现有菜单中编辑。  

## <a name="types-of-guided-scenarios"></a>引导式方案类型 

为了简单起见，所有引导式方案都省略了复杂的作用域功能，例如作用域标记、排除组和虚拟组分配。 引导式方案创建的所有资源都将继承完成方案的管理员的每个作用域标记。 某些方案为公共设置提供了一定程度的定制，以覆盖密切相关的场景。 在这些方案中，支持仅包含组的组分配。 对于其他引导式方案，整个方案通过无自定义来保证一致的体验，并自动生成一个新组来接收所有分配。 一旦引导式方案完成，你就可以自由地通过现有的策略、应用和配置文件工作负荷直接使用更复杂的任务。  

以下方案提供引导： 
- 部署 Microsoft Edge for Mobile 
- 试用云管理 PC
- 保护 Microsoft Edge for Mobile 

## <a name="guided-scenario-functionality"></a>引导式方案功能 

引导式方案提供了特定的功能。 以下详细信息有助于解释在遵循引导式方案时可以和不能执行的操作。

### <a name="launching"></a>启动  

可从“[设备管理门户](https://devicemanagement.microsoft.com)” > “疑难解答 + 支持” > “引导式方案”访问所有引导式方案    。 

引导式方案将首先介绍方案的目的和完成设置所需的任何先决条件。 此时，将检查你的管理权限，以验证你是否具有完成此方案所需的所有权限。  

所有先决条件检查通过后，方案将提供适当的自定义设置。 引导式方案的目标是只需要输入最少的设置，并隐藏不常用或高级设置，直到需要它们或有特殊情况时才显示出来。 每个引导式方案都链接到提供更多详细信息的文档。 

在输入所有强制设置之后，引导式方案将显示输入的设置和方案所需的资源的摘要。 此时，除非明确指出，否则不会保存任何内容。

下一步是部署方案。 部署方案将创建和保存所有必要的资源和选择的设置。 完成部署所需的时间因方案而异。 部署完成后，引导式方案将显示已创建资源的列表，其中包含指向每个资源的管理视图、资源的正常工作负荷和文档的链接。 

> [!IMPORTANT]
> 在引导式方案结束时显示的列表不会保存，只在引导式方案打开时可见。  
如果部署该方案时出错，将还原所有更改。 

### <a name="editing"></a>编辑 

引导式方案不能用于编辑现有资源。 创建之后，必须使用现有的工作负荷编辑所有资源、组和分配。

### <a name="monitoring"></a>监视 

引导式方案不能用于监视初始创建过程之外的现有资源。 创建之后，必须使用现有的工作负荷监视所有资源、组和分配。 

### <a name="retiring"></a>停用 

除了在初始部署过程中出现错误时进行自动清理之外，引导式方案不能用于停用现有资源。 创建之后，必须使用现有的工作负荷停用所有资源、组和分配。 

### <a name="updating"></a>更新

随着技术的发展，Intune 可能会不时地更新引导式方案，以改进用户体验、安全性或方案的其他方面。 此更新只会影响引导式方案进行的新部署。 Intune 不会更新引导式方案之前生成的现有资源以匹配新的最佳做法或建议。  

## <a name="next-steps"></a>后续步骤

若要快速开始正常使用 Microsoft Intune，请逐步完成 Intune 引导式方案。 如果你还不熟悉 Intune，请按照[免费试用版快速入门](free-trial-sign-up.md)来设置 Intune 租户。
