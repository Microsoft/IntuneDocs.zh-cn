---
title: 快速入门 - 创建组以管理用户
titleSuffix: Microsoft Intune
description: 在本快速入门中，你将使用 Microsoft Intune 基于现有用户创建组。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 723f4b4e-3090-4811-84ff-6af652abea5a
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ccf0f06993ef0edf06ca60ba4de7973ed878441a
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71727098"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>快速入门：创建组以管理用户

在本快速入门中，你将使用 Intune 基于现有用户创建组。 使用组来管理用户并控制员工对公司资源的访问。 这些资源可以是公司 Intranet 的一部分，也可以是外部资源，例如 SharePoint 网站、SaaS 应用或 Web 应用。

如果没有 Intune 订阅，请[注册免费试用帐户](free-trial-sign-up.md)。

>[!NOTE]
>为方便起见，Intune 在具有内置优化的控制台中提供了预先创建的“所有用户”和“所有设备”组   。

## <a name="prerequisites"></a>必备条件

- 要完成本快速入门，必须先[创建用户](quickstart-create-user.md)。

## <a name="sign-in-to-intune"></a>登录到 Intune

以[全局管理员或 Intune 服务管理员身份](users-add.md#types-of-administrators)登录 [Intune 门户](https://aka.ms/intuneportal)。 如果已创建 Intune 试用版订阅，则用于创建订阅的帐户就是全局管理员。

## <a name="create-a-group"></a>创建组

你需要创建一个组以便稍后在本快速入门系列中使用。 若要创建组，请执行以下操作：

1. 打开“Microsoft Intune”窗格后，选择“组” > “新建组”    。
2. 在“组类型”下拉列表中，选择“安全”   。
3. 在“组名称”  字段中，输入新组的名称（例如，Contoso 测试人员  ）。
4. 添加对该组的描述  。
5. 将“成员身份类型”设置为“已分配”   。 
6. 单击“成员”，然后从列表中为该组选择一个或多个成员  。

    ![在 Microsoft Intune 中创建组的屏幕截图](./media/quickstart-create-group/quickstart-use-groups-01.png)

7. 单击“选择” > “创建”   。

已成功创建组后，该组将显示在“所有组”列表中  。 

## <a name="next-steps"></a>后续步骤

在本快速入门中，你使用 Intune 基于现有用户创建了组。 有关将组添加到 Intune 的详细信息，请参阅[添加用于组织用户和设备的组](../groups-add.md)。

要完成这一系列的 Intune 快速入门，请继续学习下一篇快速入门。

> [!div class="nextstepaction"]
> [快速入门：设置适用于 Windows 10 设备的自动注册](../enrollment/quickstart-setup-auto-enrollment.md)
