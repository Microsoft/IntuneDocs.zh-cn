---
title: 快速入门 - 创建和分配应用保护策略
titleSuffix: Microsoft Intune
description: 本快速入门使用 Microsoft Intune 来创建和分配应用保护策略。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/26/2019
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2586fce0-5dca-4686-b9c4-791778838401
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5d7e63542563425606cf1f9a8509a7bf0c09b9a9
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61511228"
---
# <a name="quickstart-create-and-assign-an-app-protection-policy"></a>快速入门：创建和分配应用保护策略

本快速入门使用 Intune 以创建应用保护策略并将其分配给最终用户设备上的客户端应用。 Intune 使用应用保护策略来确认应用是否满足组织的数据保护要求。

如果没有 Intune 订阅，请[注册免费试用帐户](free-trial-sign-up.md)。

## <a name="prerequisites"></a>必备条件

- 要完成本快速入门，必须[创建用户](quickstart-create-user.md)、[创建组](quickstart-create-group.md)、[注册设备](quickstart-setup-auto-enrollment.md)以及[添加和分配应用](quickstart-add-assign-app.md)。

## <a name="sign-in-to-intune"></a>登录到 Intune

以[全局管理员或 Intune 服务管理员身份](users-add.md#types-of-administrators)登录 [Intune](https://aka.ms/intuneportal)。 如果已创建 Intune 试用版订阅，则用于创建订阅的帐户就是全局管理员。

## <a name="create-an-app-protection-policy"></a>创建应用保护策略

可使用以下步骤创建应用保护策略：

1. 在 [Intune](https://aka.ms/intuneportal) 中，选择“客户端应用” > “应用保护策略” > “创建策略”。 
2. 输入以下详细信息： 

    - **名称**：Windows 10 内容保护
    - **说明**：与此策略相关联的用户将无法在设备上的指定应用与其他非托管应用之间剪切、复制或粘贴任何内容。
    - **平台**：*Windows 10*
    - **注册状态**：需要注册

3. 选择“受保护的应用”以选择必须遵守此策略的应用。
4. 单击“添加应用”。
5. 在“推荐的应用”下，选择“Word Mobile”。
5. 单击“确定” > “确定”。 
6. 选择“所需的设置”以配置应用。
7. 单击“允许覆盖”以设置 Windows 信息保护模式。 选择此选项将阻止企业数据离开受保护的应用。
8. 单击“确定” > “创建”。

现在将在 Intune 中看到应用保护策略。

### <a name="assign-the-app-protection-policy"></a>分配应用保护策略

在 Intune 中创建应用保护策略后，可将其分配给组。 

可使用以下步骤分配应用保护策略：

1.  在 [Intune](https://aka.ms/intuneportal) 中，选择“Intune” > “客户端应用” > “应用保护策略”。 
2.  选择先前创建的应用保护策略。 在本快速入门中，策略是“Windows 10 内容保护”。
3.  选择“分配”。
4.  单击“包括”选项卡上的“选择要包括的组”。
5.  选择“Contoso 测试人员”作为要包括的组。
6.  单击“选择” > “保存”。 

现已分配应用保护策略。

> [!NOTE]
> 应用保护策略只能应用于包含用户的组，而不能应用于包含设备的组。

## <a name="next-steps"></a>后续步骤

在本快速入门中，你已创建并分配了应用保护策略。 分配了此策略的应用用户将无法在设备上的指定应用与其他非托管应用之间剪切、复制或粘贴任何内容。 此类保护有助于保护组织的数据。 有关 Intune 中应用保护策略的详细信息，请参阅[什么是应用保护策略？](app-protection-policy.md)

要完成这一系列的 Intune 快速入门，请继续学习下一篇快速入门。

> [!div class="nextstepaction"]
> [快速入门：创建并分配自定义角色](quickstart-create-custom-role.md)
