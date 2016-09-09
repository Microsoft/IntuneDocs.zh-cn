---
title: "创建用于组织用户和设备的组 | Microsoft Intune"
description: "说明如何为你的 Intune 订阅创建用户和组"
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5fdf98c8-fe67-4d7a-9837-ed1234348014
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0c1e08cc49d75303f6793894e3c8a040f6e7a8b1
ms.openlocfilehash: 3b2f896ea6c3e66924dbd8b35fcddcccd0b65ca6


---


# 创建用于组织用户和设备的组
Intune 中的组使你能非常灵活地管理设备和用户。 你可以将组设置为适应组织需要（例如，按地理位置、部门或硬件特性）并将其用于执行各种管理任务，上至为一组用户部署策略，下至将应用程序部署到一组设备。

设备和用户均在 Intune 管理控制台的“组”工作区中创建。

![管理员控制台组工作区](./media/groups.png)


> [!TIP]
> 若要了解有关使用组的详细信息，请参阅[通过 Microsoft Intune 使用组来管理用户和设备](/intune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune)。


## 创建设备组
使用设备组来部署应用和更新，并配置其他功能。 例如，使用以下步骤设置“我的设备”组：

1.  在 [Intune 管理控制台](https://manage.microsoft.com/)中，依次选择“组” > “概述” > “创建组”。

2.  对于“组名称”，键入“我的设备”，并从父组列表中选择“所有设备”，然后选择“下一步”。

3.  在 **“定义成员资格条件”** 页上，选择 **“所有设备”** 以指示该组包括移动设备和计算机。

4.  在“定义直属成员资格”页上，选择“下一步”。 如果之前创建了未包括所有设备的组，并且希望向新组中添加特定设备，则可在此处执行该操作。

5.  在“摘要”页上，查看将采取的操作，然后选择“完成”。

在“所有设备”下的“组”工作区中的“组”列表中，可找到新建的组。 你还可以从此处编辑或删除组。

## 创建用户组
使用用户组来部署软件和设备策略。 例如，使用以下步骤设置“Intune 用户”组：

1.  在 [Intune 管理控制台](https://manage.microsoft.com/)中，依次选择“组” > “概述” > “创建组”。

2.  对于“组名称”，键入“Intune 用户”，并从父组列表中选择“所有用户”，然后选择“下一步”。

3.  在 **“定义成员资格条件”** 页上，将 **“组成员资格开始为”** 设置为 **“父组中的所有用户”**。

4.  在“从这些安全组中排除成员”旁边，选择“浏览”，然后选择“公司管理员”。 通过这种排除方式，可让你在不影响“公司管理员”帐户（也称为租户管理员）的情况下管理“Intune 用户”组。

5.  在“定义直属成员资格”页上，选择“下一步”。 由于你希望“Intune 用户”组包括除“公司管理员”之外的所有用户，因此无需在此处执行任何操作。

6.  在“摘要”页上，查看将采取的操作，然后选择“完成”。

在“所有用户”下的“组”工作区中的“组”列表中，可找到新建的组。 你还可以从此处编辑或删除组。



### 后续步骤
祝贺你！ 你刚刚完成了 *Intune 快速入门指南*的步骤 5。

>[!div class="step-by-step"]

>[&larr;**管理 Intune 许可证**](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)       [**创建策略和应用**&rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-6.md)  



<!--HONumber=Aug16_HO5-->


