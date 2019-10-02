---
title: Intune 测试和验证
titleSuffix: Microsoft Intune
description: 如何在环境中测试和验证 Intune 仅限云解决方案。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 3/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4f82ee0c-4bd6-4623-9b10-9249d316ccf5
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6fe203de969f848da92fecfc00787e905d0a946d
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71727189"
---
# <a name="intune-testing-and-validation"></a>Intune 测试和验证

在测试 Microsoft Intune 的实现时，请考虑功能验证和用例验证。 功能验证包括测试每个组件和配置，以确定其是否正常工作。 用例验证需要测试来验证涉及一系列任务的方案是否按预期工作。 

建议将 IT 支持和支持人员纳入测试阶段，以便创建支持文档，且 IT 支持和支持人员能够轻松提供对该产品的支持。 如果组件或场景在该用例的基础上不起作用，请确保记录必需的更改并附上进行更改的原因。

## <a name="before-you-begin"></a>在开始之前

建议记录以下内容：

- **测试条件：** 确定度量依据基准。

- **设计组件：** 至少必须符合 1 个测试条件。

如果设计组件未存在于至少 1 个符合要求或场景的测试条件中，请考虑该设计组件是否必需。 此外，请确保具备以下项：

- **帐户：** 应获得 EMS 和 Office 365 许可且可用于测试所有用例方案的测试帐户。

- **设备：** 可擦除或重置为出厂默认设置的测试设备。

- **集成组件：** 必要时，应安装和配置所有集成组件（证书连接器和 Intune Exchange 本地连接器）。

可能需要进行设计更改以适应无法预料的困难。 此外，应完整记录所有设计更改，并随附每项更改的原因。 以下示例演示了可能的更改：

<blockquote>你意识到自己不满足网络设备注册服务 (NDES) 的要求，还了解到在没有 NDES 实现的情况下，可使用满足相同要求的根 CA 来配置 VPN 和 Wi-Fi 配置文件。</blockquote>

在测试和验证过程中，可能会遇到需要技术指导或专项疑难解答的挑战或问题。 建议通过 Microsoft 支持渠道寻求帮助。

- [了解如何获得 Intune 支持](../get-support.md)

- [联系 Microsoft Intune 的辅助电话支持](../get-support.md)

## <a name="functional-validation-testing"></a>功能验证测试

功能验证包括测试每个组件和配置，以确定其是否正常工作。 请查看下表中的验证测试示例。

![第 9 节表 1](./media/planning-guide-test-validation/section-9-image-1-table.PNG)

## <a name="use-case-validation-testing"></a>用例验证测试

执行用例验证测试，验证场景是否完整且实用。 有以下两种类型的用例方案：IT 管理员和最终用户。

### <a name="it-admin"></a>IT 管理员

执行 IT 管理员验证测试，验证在设备上执行的操作或用户功能是否正确。 请查看下面的 IT 管理员端到端验证场景示例。

![第 9 节表 2](./media/planning-guide-test-validation/section-9-image-2-table.PNG)

### <a name="end-user"></a>最终用户

执行最终用户提供验证测试，验证最终用户体验在所有用户通信中是否按预期正确显示。 请务必验证最终用户体验是否正确。 如果不进行验证，可能导致低采用率，并加重支持人员的工作负担。

![第 9 节表 3](./media/planning-guide-test-validation/section-9-image-3-table.PNG)

## <a name="next-steps"></a>后续步骤

现在，已测试并验证 Intune 功能和用例场景，可开始[推出 Intune 生产](../planning-guide-rollout-plan.md)。

请参阅[其他资源](../planning-guide-resources.md)，获取更多计划模板和相关信息。
