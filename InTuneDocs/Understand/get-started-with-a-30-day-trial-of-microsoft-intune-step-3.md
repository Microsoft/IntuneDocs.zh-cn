---
# required metadata

title: 创建用于组织评估订阅用户和设备的组 | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 7162cad3-5c14-43f3-a760-833ffd7786b1

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 创建用于组织评估订阅用户和设备的组
Intune 中的组使你能非常灵活地管理设备和用户。 你可以将组设置为适应组织需要（例如，按地理位置、部门或硬件特性）并将其广泛用于执行各种管理任务，上至为一组用户设置策略，下至将应用程序部署到一组设备。

## 创建设备组
使用设备组来部署软件和更新，并配置 Microsoft Intune 代理设置和 Windows 防火墙设置策略。 例如，使用以下步骤设置“我的试用设备”组：

1.  在 [Intune 管理控制台](https://manage.microsoft.com/)中，依次选择“组” &gt; “概述” &gt; “创建组”

2.  对于“组名称”，输入“我的试用设备”，并从父组列表中选择“所有设备”，然后选择“下一步”

3.  在 **“定义成员资格条件”** 页上，选择 **“所有设备”** 以指示该组包括移动设备和计算机。

4.  在“定义直属成员资格”页上，选择“下一步”。 如果之前创建了未包括所有设备的组，并且希望向新组中添加特定设备，则可在此处执行该操作。

5.  在“摘要”页上，查看将采取的操作，然后选择“完成”

在“所有设备”  下的“组”  工作区中的“组” 列表中，可找到新建的组。 你还可以从此处编辑或删除组。

## 创建用户组
使用用户组来部署软件和设备策略。 例如，使用以下步骤设置“我的试用用户”组：

1.  在 [Intune 管理控制台](https://manage.microsoft.com/)中，依次选择“组” &gt; “概述” &gt; “创建组”

2.  对于“组名称”，输入“我的试用用户”，并从父组列表中选择“所有用户”，然后选择“下一步”

3.  在“定义成员资格条件”页上，将“组成员资格开始为”设置为“父组中的所有用户”

4.  在“从这些安全组中排除成员”旁边，选择“浏览”，然后选择“公司管理员”。 通过这种排除方式，你便能在不影响“公司管理员”帐户（也称为租户管理员）的情况下管理“我的试用用户”组。

5.  在“定义直属成员资格”页上，选择“下一步”。 由于你希望“我的试用用户”组包括除“公司管理员”之外的所有用户，因此无需在此处执行任何操作。

6.  在“摘要”页上，查看将采取的操作，然后选择“完成”

在“所有用户”  下的“组”  工作区中的“组” 列表中，可找到新建的组。 你还可以从此处编辑或删除组。

若要了解有关使用组的详细信息，请参阅[通过 Microsoft Intune 使用组来管理用户和设备](/Intune/Deploy-Use/use-groups-to-manage-users-and-devices-with-microsoft-intune)

### 后续步骤
祝贺你！ 你刚完成了“Microsoft Intune 评估”演练的步骤 3。

>[!div class="step-by-step"]

>[&larr; **添加用户**](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-2.md)     [**创建策略** &larr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-4.md)  


<!--HONumber=May16_HO2-->


