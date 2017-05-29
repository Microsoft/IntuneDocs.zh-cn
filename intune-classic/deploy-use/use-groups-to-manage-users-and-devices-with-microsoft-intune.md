---
title: "使用组来管理用户和设备 | Microsoft Docs"
description: "使用“组”工作区创建和管理组。"
keywords: 
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: eb9b01ce-9b9b-4c2a-bf99-3879c0bdaba5
ms.reviewer: lpatha
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 095b8db0cb5097edca98d138edccafbe8e55b9ba
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---
# <a name="use-groups-to-manage-users-and-devices-in-microsoft-intune"></a>在 Microsoft Intune 中使用组来管理用户和设备

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本主题介绍如何在 Intune 中创建组。 其中还提供了有关在未来数月将如何更改组的管理的信息。 

>[!IMPORTANT]
>
>在 Intune 门户中打开“组”工作区时，若显示 Azure Active Directory (Azure AD) 门户的链接，则表明你正在使用新的 Azure AD 安全组方法在 Intune 中进行组管理，如[将组迁移到 Azure Active Directory](migrating-groups-to-azure-active-directory.md) 中所述。 单击 Azure AD 门户链接以创建并管理组。
>
>![Azure 组管理链接的屏幕截图](../media/groups-link-azure.png) 
>
>若未显示 Azure AD 门户链接，则表明正在使用当前组管理方法，如[使用 Microsoft Intune 创建组以管理用户和设备](#Create-groups-to-manage-users-and-devices-with-Microsoft-Intune)中所述。

本主题介绍如何在 Intune 管理控制台中创建 Intune 组。

可在 Microsoft Intune 管理控制台中的“组”工作区创建和管理组。 “组概述”页显示了状态摘要，可帮助你确定需要关注的问题并划分其优先级。 状态摘要包含以下方面：

-   警报
-   软件更新
-   Endpoint Protection
-   策略
-   软件管理

你的组层次结构也会显示状态摘要，帮助你确定和解决所选组的相关成员问题。

## <a name="create-groups"></a>创建组

> [!TIP]
> 在创建组时，请考虑将如何应用策略。 例如，你可能有特定于设备操作系统的策略、特定于组织中不同角色的策略或特定于已在 Active Directory 中定义的组织单位的策略。 分别设置 iOS、Android 和 Windows 设备组，并为每个组织角色分别设置用户组，可能会很有用。
>
> 还可创建适用于所有组和设备的默认策略，以建立组织的基本合规性要求。 然后，可针对范围最广泛的用户和设备创建更具体的策略。 例如，可为每个设备操作系统创建电子邮件策略。
>
> 请注意为策略命名，以便稍后可以轻松识别。 例如，一个好的描述性策略名称是**“整个公司的 WP 电子邮件策略”**。
>
> 每次创建严格策略时，请将其传达给用户。 在创建更多常规组和策略后，请关注如何创建更小的组，以便减少不必要的通信。

## <a name="to-create-a-device-group"></a>创建设备组

1.  在 Intune 管理员控制台中，依次选择“组”&gt;“概述”&gt;“创建组”。

2.  输入组名称和描述（可选），然后选择一个设备组作为父组。 选择**下一步**。

3.  在“定义成员资格条件”页上，选择组内要包含的设备类型。 根据要包含的设备类型，可选择其他组配置：

    -   **计算机**。 选择是否添加父组中的所有成员；想添加或排除的组织单元和域。 可从清单中获取计算机的组织单位和域信息。

    -   **移动设备**。 指定是否要包含 Intune 管理的移动设备、Exchange ActiveSync 管理的移动设备，还是包含两者。

    -   **所有设备**。 该选项可添加符合条件的所有设备。

4.  在“定义直属成员资格”页上，选择“浏览”，选择要包含或排除的单独设备。 如果选择的设备不在指定的父组中，Intune 会将其自动添加到父组。

5.  在“摘要”页上，查看所做的选择，然后选择“完成”。

在“父组”下的“组”工作区中的“组”列表中，可找到新建的组。 还可以从此处编辑或删除组。

## <a name="to-create-a-user-group"></a>创建用户组

1.  在 Intune 管理员控制台中，依次选择“组”&gt;“概述”&gt;“创建组”。

2.  输入组名称和描述（可选），然后选择一个用户组作为父组。 选择**下一步**。

3.  在“定义成员资格条件”页上，选择是包括父组的所有成员还是从一个空组开始。 然后，可以根据你在 [Office 365 管理中心](http://go.microsoft.com/fwlink/?LinkId=698854)手动配置的或从 Active Directory 同步的用户安全组包括或排除成员。 如果安全组的成员资格更改，则基于该安全组的用户组的成员资格也可能更改。

    > [!IMPORTANT]
    > 目前，如果你的组包括特定安全组或管理员组中的成员，同时排除某些组中的成员将删除最初包括的成员。 若要创建既有包含成员又有排除成员的组，建议先创建具有包含成员的父组。 然后为该父组创建子组。 在新建子组中，列出排除成员。 然后，使用该子组管理 Intune 策略、配置文件和应用分发。

    > [!NOTE]
    > 在 Azure 门户中，可基于用户的直接管理员创建组。 此类组为动态组，当向 Azure Active Directory 中的管理者团队添加或从中删除员工时，该组将随之变化。 在**将组配置为“管理员”组**部分，[使用属性创建高级规则](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/)介绍了如何基于管理员名称创建 Azure 组。

4.  在“定义直属成员资格”页上，选择“浏览”，选择要包含或排除的单独用户。 如果选择的用户不在指定的父组中，这些设备将自动添加到父组。 “手动添加用户”选项位于“选择成员”对话框的底部。 如果你想要添加尚无已注册设备的用户，可使用此选项。

5.  在“摘要”页上，查看所做的选择，然后选择“完成”。

在“父组”下的“组”工作区中的“组”列表中，可找到新建的组。 还可以从此处编辑或删除组。

> [!TIP]
> 安全组是用于填充用户组的绝佳资源。 由于安全组定义谁有权访问哪些资源，因此可顺利地转换到 Intune 用户组。 从 Active Directory 同步到 Azure Active Directory 的安全组，或者在 Azure Active Directory 中通过 Office 365 管理中心或 Azure 门户直接创建的安全组，都可用于在 Intune 中创建用户组。

## <a name="filter-admin-views-by-role"></a>按角色筛选管理员视图
在已筛选的组视图中，可以管理员角色为基础，定制 IT 管理员可查看的内容。 还可以限制每个 IT 管理员可以管理的组。 在以下情况下有用：

-   希望 IT 管理员仅能够将项目部署到特定用户和设备
-   希望 IT 管理员只能查看与该管理员相关的组

在 Intune 管理控制台中，可为服务管理员配置已筛选的组视图。 有关详细信息，请参阅[使用 Microsoft Intune 前须知](/intune-classic/get-started/what-to-know-before-you-start-microsoft-intune)。

为服务管理员部署设置已筛选的组后，该管理员在部署软件/策略或运行报表时只能查看和选择指定的组。 该管理员还无法在管理控制台的以下页面上查看状态信息：

-   **系统概述**
-   **组概述**
-   **Endpoint Protection 概述**
-   **警报概述**
-   **软件概述**
-   **策略概述**

### <a name="to-create-a-filtered-group-view"></a>创建已筛选组视图

1.  在 Intune 管理控制台中，依次选择“管理员”&gt;“管理员管理”&gt;“服务管理员”。

2.  选择要为其创建已筛选组视图的管理员，然后选择“管理组”。

3.  在“选择将对此服务管理员可见的组”对话框中，添加服务管理员将能够访问的组，然后选择“确定”。

设置已筛选组视图后，IT 管理员就只能够查看和选择选定的组。

## <a name="manage-your-groups"></a>管理组
创建组后，可继续根据组织的需求对其进行管理。

可以编辑组，更改它的名称或说明或是属于该组的成员。

你可以删除不再能够满足组织需求的组。 删除组的不会删除属于该组的用户。

## <a name="next-steps"></a>后续步骤
设置组和策略后，查看“预期值”和“状态”检查设计的实际含义。

### <a name="to-check-your-design"></a>检查你的设计

1. 从一个设备组中选择任何设备，并浏览页面顶部的信息类别。
2. 选择“策略”。 你将看到的内容类似于此屏幕截图中的 Android 设备的策略设置。

![Android 设置策略示例](../media/Intune-Device-Policy-v.2.jpg)

每个策略都有 **“预期值”** 和 **“状态”**。 预期值是指在分配策略时想要获得的值。 状态是指综合考虑应用于设备的所有策略，以及硬件和操作系统的限制及要求时，获得的内容。 在此屏幕截图中可以看到两个清晰的示例：

-   **“允许简单密码”** 设置为 **“是”**（如 **“预期值”** 列中所示），但其 **“状态”** 为 **“不适用”**。 这是因为 Android 设备不支持简单密码。
-   同样，扩展的策略项 **iOS 设备的电子邮件设置**不适用于此设备，因为这是 Android 设备。

> [!NOTE]
> 请记住，当具有不同限制级别的两个策略应用于同一个设备或用户时，实际会使用限制更严格的策略。

