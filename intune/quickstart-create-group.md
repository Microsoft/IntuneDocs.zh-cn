---
title: 快速入门 - 创建组以管理用户
titlesuffix: Microsoft Intune
description: 在本快速入门中，你将使用 Microsoft Intune 基于现有用户创建组。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/21/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 723f4b4e-3090-4811-84ff-6af652abea5a
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3a4468f2e6919349095d934790740afc8c347282
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581541"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>快速入门：创建组以管理用户

在本快速入门中，你将使用 Intune 基于现有用户创建组。 使用组来管理用户并控制员工对公司资源的访问。 这些资源可以是公司 Intranet 的一部分，也可以是外部资源，例如 SharePoint 网站、SaaS 应用或 Web 应用。

如果没有 Intune 订阅，请[注册免费试用帐户](free-trial-sign-up.md)。

>[!NOTE]
>为方便起见，Intune 在具有内置优化的控制台中提供了预先创建的“所有用户”和“所有设备”组。

## <a name="prerequisites"></a>必备条件

- 要完成本快速入门，必须先[创建用户](quickstart-create-user.md)。

## <a name="sign-in-to-intune"></a>登录到 Intune

以全局管理员或 Intune 服务管理员身份登录 [Intune](https://aka.ms/intuneportal)。 通过选择“所有服务” > “Intune”，在 Azure 门户中查找 Intune。 Intune 位于“监视 + 管理”部分中。

## <a name="create-a-group"></a>创建组
1. 打开“Microsoft Intune”窗格后，选择“组” > “新建组”。
2. 在“组”窗格中，选择“组类型” > “安全性”。
3. 将“名称”设置为"Contoso 测试人员"，并为组添加“说明”。
4. 将“成员身份类型”设置为“已分配”。 
5. 单击“成员”，然后从现有列表中为该组选择“成员”。

    ![在 Microsoft Intune 中创建组的屏幕截图](./media/quickstart-use-groups-01.png)

6. 单击“选择”。
7. 单击“创建”。

如果已成功创建组，则该组将显示在“所有组”的列表中。 

## <a name="next-steps"></a>后续步骤

在本快速入门中，你使用 Intune 基于现有用户创建了组。

> [!div class="nextstepaction"]
> [创建设备合规性策略](quickstart-create-policy.md)
