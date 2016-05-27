---
# required metadata

title: 规划用户和设备组 | Microsoft Intune
description:
keywords:
author: SanchuSa
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f11bb256-1094-4f7e-b826-1314c57f3356

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 规划用户和设备组
Intune 中的组使你能够非常灵活地管理设备和用户。 你可以根据以下条件设置适合你组织需求的组：

- 地理位置
- department
- 硬件特征
- 操作系统
- 设备是用户拥有还是公司拥有


## Intune 组如何工作


Intune 管理控制台中“组”节点的默认视图是：

![Intune 控制台中“组”节点的默认视图的屏幕截图](/intune/media/Group-planning/Intune_Planning_Groups_Default_small.png)

策略将部署到组上，因此组层次结构是关键的设计注意事项之一。 重要的是要知道，一旦创建组之后，就不能再更改此组的父组，所以组的设计从你开始使用 Intune 服务那一刻起就至关重要。 此处介绍了一些设计基于组织需求的组层次结构的建议做法。

## 组成员资格规则

1. 组可以包含用户或设备，但不能同时包含两者。

    * **设备组：** 此组包括计算机和移动设备。 必须先注册计算机，然后才能将其添加到组中。 必须将你的环境配置为支持移动设备，并且设备必须已注册或通过 Exchange ActiveSync 发现，然后你才能将移动设备添加到组中。

    * **用户组：** 一个组可包含安全组中的用户，这些安全组是从 Active Directory 中同步的组。 如果不使用 Active Directory 同步，你可以手动创建这些组。

2. 设备或用户可以属于多个组。

3. 一个组可以根据下列成员资格规则包括和排除成员：

    * **条件成员资格：**这些是 Intune 运行来包括或排除成员的动态规则。 这些条件使用从本地 Active Directory (AD) 同步的**安全组**和其他信息。 当安全组或数据更改时，组成员资格可能会在你用 AD 同步时更改。

    * **直属成员资格：** 这些是用于显式添加或排除成员的静态规则。 成员资格列表是静态的。

4. 虽然 Active Directory 域服务 (AD DS) 不是创建包括用户或计算机的用户组或设备组所必需的，但要使设备组包括移动设备，你的环境必须配置为支持移动设备。

    此外，必须发现设备且将其添加到 Intune。

## 组关系规则

1. 你创建的每个组都必须具有父组，并且在组创建之后你将无法更改该组的父组。

2. 当你向子组中添加用户或设备时：

    * 子组始终是父组的子集。

    * 你添加到子组的新成员会自动添加到该组的父组。

    * 如果某个成员已从父组中排除，则无法将该成员添加到子组。

3. 父组的成员资格定义子组的可用成员资格。

4. 如果删除父组，则所有子组也将被删除。

5. 你可以将内容和策略部署到父组，同时排除部署到子组。

6. 可以将特定用户或设备添加到不是父组成员的子组。 如果这样做，则会将新组成员添加到父组。

    但是，你无法将已从父组中排除的成员添加到子组。

7. 组成员资格是递归的。 例如：

    * **Pat** 是“便携式计算机用户”  安全组的唯一成员。

    * “便携式计算机用户”  组是“已批准用户”  安全组的成员。

    * 在 Intune 中创建一个组，该组使用包括**已批准用户**组的成员的动态成员资格查询。 结果是，Intune 用户组包括 **Pat**

> [!TIP]
> 在创建组时，考虑将如何应用策略。 例如，你可能有特定于设备操作系统的策略，特定于组织中不同角色的策略，或特定于已在 Active Directory 中定义的组织单位的策略。 有观点认为具有特定于 iOS、Android 和 Windows，以及每个组织角色的用户组的设备组非常有用。

<!--- should we just link to a policies topic at this point and remove this? Ask Rob
 You'll probably want to create a default policy that applies to all groups and devices, to establish the basic compliance requirements of your company. Then create more specific policies for the broadest categories of users and devices, for example, email policies for each of the device operating systems.

 Be careful naming your policies so that you can easily identify them later. For example, a good, descriptive policy name is **WP Email Policy for Entire Company**.

 Each time you create a restrictive policy you'll want to communicate it to your users, so after you create the more general groups and policies pay attention to how you create smaller groups so that you can reduce unnecessary communication.--->

## 内置组
Intune 提供九个无法编辑或删除的内置组： <!--maybe a screen shot would be best?-->

-   **所有用户**
    -   取消组合的用户
-   **所有设备**
    -   所有计算机
    -   所有移动设备
        -   所有直接管理的设备
        -   所有 Exchange ActiveSync 管理的设备
    -   所有企业所拥有的设备
    -   取消组合的设备

> [!NOTE]
> 让你的座右铭成为：*简单为美*。 如果你的组织没有特定的需求（例如下面所述的需求），那么从长远来看，保持简单并采用默认组结构和策略将使服务更易于管理。 如果可能的话，平等对待你的用户，几乎不通过组来做任何区分，这样维护将更加简单，也会使得要维护的策略更少。


### 组织中的所有用户和设备
为组织中的所有用户和设备定义一个父组，因为你很可能会有将应用于所有用户和设备的策略。 为此，你可以使用 Intune 中默认的**所有用户**和**所有设备**组。 按特定条件组织设备的子组，如自带设备办公 (BYOD) 的组和企业拥有设备的组 (CO)，可以是**所有用户**和**所有设备**父组的子组。

## 为你的组织自定义组

### BYOD 和企业拥有的设备
如果你的组织允许员工使用他们自己的设备办公 (BYOD)、提供公司拥有的设备 (CO) 或两者的结合，我们建议你以这两种类别的设备为基础来应用策略。

若是在 BYOD 或两者结合的情况下，请注意规划不侵犯本地隐私规则的策略。 为所有将自带设备办公的用户创建父组。 然后可以将该组用于应用适用于此类别中所有用户的策略。

![创建 BYOD 父组的屏幕截图](/intune/media/Group-planning/Intune_Planning_Groups_BYOD_small.png)

同样，你可以为组织中的 CO 用户创建组：

![BYOD 和 CO 兄弟用户组的屏幕截图](/intune/media/Group-planning/Intune_Planning_Groups_BYOD_Hierachy_View_small.png)

<!---START HERE--->

### 针对地理区域的组
如果你的组织需要针对特定区域的策略，你可以创建基于地理区域的组。 你可以把它们建立在你可能已在 Active Directory (AD) 中创建的区域组的基础上，然后将它们同步到 Azure AD。 还可以直接在 Azure AD 中创建它们。

这些屏幕截图显示如何基于从本地 AD 同步的组创建 Intune 组。 此示例假定你已有一个**美国用户组**的 AD 安全组

1. 首先，提供常规信息。

    ![“编辑组”区域的屏幕快照](/intune/media/PlanDesign/Group-planning/Intune_Planning_Groups_AD_General_small.png)

在成员资格条件下，选择从 AD 同步的**美国用户组**作为在成员资格规则下使用的安全组。

![“编辑组”对话框](/intune/media/Intune_Planning_Groups_AD_Criteria_small.png)

查看然后选择**完成**以完成创建组。

![“编辑组”对话框](/intune/media/Intune_Planning_Groups_AD_Summary_small.png)

在我们的示例中，我们还创建了中东和亚洲组 (MEA)。

> 如果组成员身份不是基于安全组成员资格填充，请检查是否已将 Intune 许可证分配给这些成员。

### 针对特定硬件的组
如果你的组织要求应用于特定硬件类型的策略，你可以创建基于此要求的组。 你可以把它们建立在你已在本地 AD 中创建的特定组的基础上，然后将它们同步到 Azure AD。 还可以直接在 Azure AD 中创建它们。 在此示例中，我们使用“美国用户组”作为“笔记本电脑用户”组的父组。

![“选择安全组”对话框](/intune/media/Intune_Planning_Groups_Laptop_small.png)

此时，组层次结构应显示如下。 如你所见，现在 Intune 组“笔记本电脑用户”内有了成员。 任何应用到此组的策略现在将被应用到来自美国地区的 BYOD 笔记本电脑用户。

![笔记本电脑用户组的显示](/intune/media/Group-planning/Intune_Planning_Groups_Laptop_Hierarchy_small.png)

### 针对特定操作系统的组
如果你的组织要求应用于特定操作系统（如 Android、iOS 或 Windows）的策略，你可以创建基于此要求的组。 正如前例中一样，你可以把它们建立在你已在本地 AD 中创建的特定于操作系统的组的基础上，然后将它们同步到 Azure AD。 也可以在 Azure AD 中直接创建它们。

按照前面示例中的相同方法，我们可以使用特定的操作系统平台 <!--devices?--> 创建基于用户的组。

> 如果有用户使用多个移动平台/操作系统且你没有自动将用户分类为 Android 用户、iOS 用户或 Windows 用户的方法，那么请考虑在设备级别应用策略，这将让你在应用特定操作系统策略时有更好的灵活性。
>
> 不能基于设备的操作系统动态预配组。 使用 AD 或 AAD 安全组执行此操作。

![笔记本电脑用户组的显示](/intune/media/Intune_Planning_Groups_OS_Hierachy_small.png)

一旦你的所有用户组都基于这些组织需求填充后，组层次结构应该如此处所示：

![组层次结构视图](/intune/media/Intune_Planning_Groups_Midpoint_Hierachy_small.png)

此层次结构可用来适当地应用组织的策略。

### 设备组
如下所示，你还可以对设备创建相似的组，首先以一个针对 BYOD 方案、包括所有员工拥有设备的广泛组为例：

![“创建组”对话框](/intune/media/Intune_Planning_Groups_Device_General_small.png)

确保选择“所有设备（计算机和移动）”以使组包括所有 BYO 设备：

![“定义成员资格条件”页](/intune/media/Intune_Planning_Groups_Device_Criteria_small.png)

查看并选择“完成”以创建 BYOD 组。

![“创建组”对话框](/intune/media/Intune_Planning_Groups_Device_Summary_small.png)

继续创建设备组，直到你的设备组层次结构与用户组层次结构相似。 然后 Intune 控制台中的组节点应与此相似：

![Intune 组层次结构视图](/intune/media/Intune_Groups_Hierarchy_Final_Small.png)

## 组层次结构和命名约定
为了使策略管理更轻松，我们建议你根据用途、平台和其应用到的范围来命名每个策略。 此命名标准应遵循你在准备应用策略时创建的组结构。

例如，对于在美国地区级别应用到所有企业、Android、移动设备的 Android 策略，该策略可命名为

![CO_US_Mob_Android_General](/intune/media/Intune_planning_policy_android_small.png)

创建适用于 Android 的策略

![通过这种方式命名策略，你可以从控制台的策略节点快速识别策略和它们的预期用途和范围，如下所示：](/intune/media/Intune_planning_policy_view_small.png)

## Intune 策略列表
[后续步骤](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)


<!--HONumber=May16_HO2-->


