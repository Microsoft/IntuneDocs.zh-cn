---
title: "Intune 测试和验证"
description: "本文为你提供在环境中测试和验证 Intune 仅云解决方案时需考虑的所有详细信息。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4f82ee0c-4bd6-4623-9b10-9249d316ccf5
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 4ea2974c4724564cd8f9972fdb238b06d1b100e6
ms.contentlocale: zh-cn
ms.lasthandoff: 06/08/2017


---

# <a name="intune-testing-and-validation"></a>Intune 测试和验证

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

测试阶段应在实现阶段过程中和之后进行，你需要有测试帐户、组以及用于测试之前确定的所有必要 IT（管理员）和最终用户（用例）场景的设备。

建议将 IT 支持/支持人员纳入测试阶段，以便创建支持文档，且 IT 支持/支持人员适应支持该产品。 如果组件或场景在该用例的基础上不起作用，请确保记录必需的更改并附上进行更改的原因。

## <a name="before-you-begin"></a>在开始之前

建议记录以下内容：

-   **测试条件：**确定针对其进行测量的基准。

-   **设计组件：**必须至少存在于 1 个测试条件。

如果设计组件未至少存在于 1 个符合要求或场景的测试条件中，请考虑该设计组件是否必需。 此外，请确保具备以下项：

-   **帐户：**测试中使用的帐户应为许可 EMS 和 Office 365 测试所有用例场景的测试帐户。

-   **设备：**此时使用的设备应为测试设备，这些设备可能会被清除或重置为出厂默认值。

-   **集成组件：**如果需要，应安装和配置所有集成组件（证书连接器、适用于托管 Exchange 的 Intune 服务间连接器和 Intune 本地 Exchange Connector）。

可能需要进行设计更改以适应无法预料的困难。 此外，应完整记录所有设计更改，并随附每项更改的原因。 以下示例演示了可能的更改：

-   你可能会意识到你不满足网络设备注册服务 (NDES) 的要求，并且还了解到在没有 NDES 实现的情况下，可使用满足相同要求的根 CA 来配置 VPN 和 Wi-Fi 配置文件。

在测试和验证过程中，你可能会遇到需要技术指导或专门的故障排除的挑战或问题。 建议通过 Microsoft 支持渠道寻求帮助。

-   [了解如何获得 Intune 支持](/intune-classic/troubleshoot/how-to-get-support-for-microsoft-intune)

-   [Microsoft Intune 常规疑难解答提示](/intune-classic/troubleshoot/general-troubleshooting-tips-for-microsoft-intune).

-   [了解如何获取对 Microsoft Intune 的支持。](/intune-classic/troubleshoot/how-to-get-support-for-microsoft-intune)

-   [联系 Microsoft Intune 的辅助电话支持](/intune-classic/troubleshoot/contact-assisted-phone-support-for-microsoft-intune)

## <a name="functional-validation-testing"></a>功能验证测试

功能验证包括测试每个组件和配置，以确定其是否正常工作。 请查看下表中的验证测试示例。

![第 9 节表 1](./media/section-9-image-1-table.PNG)

## <a name="use-case-validation-testing"></a>用例验证测试

应执行用例验证测试，验证场景是否完整且实用。 存在两种类型的用例场景 - IT 管理员和最终用户。

### <a name="it-admin"></a>IT 管理员

应执行 IT 管理员验证测试，验证在设备上执行的操作或用户功能是否正确。 请查看下面的 IT 管理端到端验证场景示例。

![第 9 节表 2](./media/section-9-image-2-table.PNG)

### <a name="end-user"></a>最终用户

应执行最终用户提供验证测试，验证最终用户体验在所有用户通信中是否按预期正确显示。 请务必验证最终用户体验是否正确，因为验证失败可能会导致采用率较低，而支持人员呼叫量较高。

![第 9 节表 3](./media/section-9-image-3-table.PNG)

## <a name="next-steps"></a>后续步骤

现在，已测试并验证 Intune 功能和用例场景，可开始推出 Intune 生产。 请参阅[其他资源](planning-guide-resources.md)了解详细信息。

