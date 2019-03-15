---
title: 教程 - Azure 门户中的 Intune 演练
titleSuffix: Microsoft Intune
description: 在本教程中，将浏览 Microsoft Intune 以更好地了解如何完成任务。
keywords: ''
author: ErikRe
ms.author: erikre
manager: dougeby
ms.date: 01/31/2019
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e892d8a3-7f74-498c-98d5-e968a8fbb049
Customer intent: As an Intune admin, I want to learn where to find the different features in Intune.
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c733dbbf992ae10e14ba711b34e621d3f0fb3da8
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57395267"
---
# <a name="tutorial-walkthrough-of-microsoft-intune-in-the-azure-portal"></a>教程：Azure 门户中的 Microsoft Intune 演练

[Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure) 包含 100 多项服务，可以帮助你处理各种云计算方案和可能性。 Microsoft Intune 是 Azure 中可用的多种服务之一。 Intune 可帮助你确保公司的设备、应用和数据符合公司的安全要求。 你可以控制设置需要检查哪些需求以及在不满足这些需求时会发生什么情况。 可在 [Azure 门户](https://portal.azure.com)中找到 Microsoft Intune 服务。 了解 Intune 中可用的功能将帮助你完成各种移动设备管理 (MDM) 和移动应用管理 (MAM) 任务。

在本教程中，您将：
> [!div class="checklist"]
> * 了解 Microsoft Intune
> * 配置 Azure 门户

如果没有 Intune 订阅，请[注册免费试用帐户](free-trial-sign-up.md)。

## <a name="prerequisites"></a>必备条件
在设置 Microsoft Intune 之前，请查看以下要求：

   - [支持的操作系统和浏览器](supported-devices-browsers.md) 
   - [网络配置要求和带宽](network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>注册 Microsoft Intune 免费试用版

可以免费试用 Intune 30 天。 如果已有工作或学校帐户，请使用该帐户进行“登录”，并将 Intune 添加到订阅中。 否则，也可通过注册[创建免费试用帐户](free-trial-sign-up.md)，以便为组织使用 Intune。

> [!IMPORTANT]
> 注册新帐户后，不能合并现有的工作或学校帐户。

## <a name="tour-microsoft-intune"></a>了解 Microsoft Intune

请按照以下步骤更好地了解 Azure 门户中的 Intune。 完成导览后，将对 Intune 的一些主要区域有更好的理解。

1. 打开浏览器并登录 [Intune 门户](https://aka.ms/intuneportal)。 如果你是 Intune 的新用户，请使用免费试用订阅。

    ![Microsoft Intune 门户的屏幕截图](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-01.png)

    当在 Azure 中打开 Intune 或任何其他服务时，服务将显示在一个窗格中。 可以在 Intune 中使用的一些首批工作负载包括“设备”、“客户端应用”、“用户”和“组”。 工作负载只是服务的子区域。 选择工作负载时，会以整页形式打开该窗格。 其他窗格在打开时从窗格右侧滑出，然后关闭以显示上一个窗格。 窗格也称为边栏选项卡。 

    默认情况下，当打开 Intune 时，将看到“概述”窗格。 此窗格提供设备分配和符合性状态的整体视觉效果快照，以及应用安装状态。

2. 从 [Intune](https://aka.ms/intuneportal) 中，选择“设备注册”以显示有关 Intune 租户中已注册设备的详细信息。 如果从新的 Intune 租户开始，尚不具备任何已注册的设备。 

    ![设备注册窗格的屏幕截图](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-02.png)
    
    Intune 可让你管理员工的设备和应用，包括他们访问公司数据的方式。 要使用此移动设备管理 (MDM) 设备，必须先在 Intune 中注册设备。 设备注册后，系统会向其颁发 MDM 证书。 此证书可用于与 Intune 服务进行通信。 

    在 Intune 中注册工作人员设备的方法有多种。 每种方法取决于设备的所有权（个人或公司）、设备类型（iOS、Windows、Android）和管理需求（重置、关联、锁定）。 但是，在可以启用设备注册之前，必须设置 Intune 基础结构。 具体而言，设备注册需要用户[设置 MDM 机构](mdm-authority-set.md)。 有关准备好 Intune 环境（租户）的更多信息，请参阅[设置 Intune](setup-steps.md)。 准备好 Intune 租户后，即可注册设备。 有关设备注册的详细信息，请参阅[什么是设备注册？](device-enrollment.md)

3. 从 [Intune](https://aka.ms/intuneportal) 中，选择“设备符合性”以显示有关由 Intune 管理的设备符合性的详细信息。 你将看到类似于下图的详细信息。

    ![设备符合性窗格的屏幕截图](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-03.png)
    
    符合性要求实质上是一系列规则，例如要求设备 PIN 或要求设备加密。 设备符合性策略定义设备必须遵从的规则和设置，以便设备被视为符合。 若要使用设备符合性，必须具有：
    - Intune 和 Azure Active Directory (Azure AD) Premium 订阅
    - 运行受支持平台的设备
    - 须在 Intune 中注册的设备
    - 注册到一个用户或没有主要用户的设备。
    
    有关详细信息，请参阅 [Intune 中的设备符合性策略入门](device-compliance-get-started.md)。

4. 从 [Intune](https://aka.ms/intuneportal) 中，选择“设备配置”以显示有关 Intune 中设备配置文件的详细信息。 

    ![设备配置窗格的屏幕截图](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-04.png)
    
    Intune 提供可在组织内的不同设备上启用或禁用的设置和功能。 这些设置和功能将添加“配置文件”。 你可以为不同的设备和不同的平台创建配置文件，包括 iOS、Android 和 Windows。 然后，可以使用 Intune 将配置文件应用于组织中的设备。   

    有关设备配置的详细信息，请参阅[对 Microsoft Intune 中使用设备配置文件的设备应用功能设置](device-profiles.md)。

5. 从 [Intune](https://aka.ms/intuneportal) 中，选择“设备”以显示有关 Intune 租户中已注册设备的详细信息。 如果开始注册一个新的 Intune，尚不具备任何已注册的设备。 

    ![设备注册窗格的屏幕截图](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-05.png)
    
    “设备”窗格提供有关租户已注册设备的详细信息。 可以单击“所有设备”以显示 Intune 租户的设备列表。 

6. 从 [Intune](https://aka.ms/intuneportal) 中，选择“客户端应用”以显示应用安装状态。

    ![客户端应用窗格的屏幕截图](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-06.png)
    
    IT 管理员可以使用 Microsoft Intune 来管理公司员工使用的客户端应用。 除了此功能外，还可管理设备和保护数据。 管理员的首要任务之一是，确保最终用户能够访问他们在执行工作时所需的应用。 此外，还建议分配和管理未向 Intune 注册的设备上的应用。 Intune 提供各种功能，用于在所需的设备上获取需要的应用。 有关添加和分配应用的详细信息，请参阅[将应用添加到 Microsoft Intune](apps-add.md) 和[将应用分配给具有 Microsoft Intune 的组](apps-deploy.md)。

7. 从 [Intune](https://aka.ms/intuneportal) 中，选择“条件访问”以显示有关访问策略的详细信息。

    ![条件访问窗格的屏幕截图](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-07.png)

    条件访问是指控制允许连接到电子邮件和公司资源的设备和应用的方式。 若要了解基于设备和基于应用的条件访问，并查找通过 Intune 使用条件访问的常见方案，请参阅[什么是条件访问？](conditional-access.md)

8. 从 [Intune](https://aka.ms/intuneportal) 中，选择“用户”以显示有关在 Intune 中包含的用户的详细信息。 这些用户是公司的员工。 
 
    ![用户窗格的屏幕截图](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-08.png)

    你可以将用户直接添加到 Intune，也可以从本地 Active Directory 同步用户。 添加后，用户可注册设备并访问公司资源。 还可以为用户授予访问 Intune 的其他权限。 有关详细信息，请参阅[添加用户并授予对 Intune 的管理权限](users-add.md)。

9. 从 [Intune](https://aka.ms/intuneportal) 中，选择“组”以显示有关 Intune 中包含的 Azure Active Directory (Azure AD) 组的详细信息。 作为 Intune 管理员，可以使用组来管理设备和用户。 

    ![“组”窗格的屏幕截图](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-09.png)

    你可以设置适合你组织需求的组。 创建组，以便按地理位置、部门或硬件特性来组织用户或设备。 使用组来管理大规模的任务。 例如，可设置用于大量用户的策略，或向一组设备部署应用。 有关组的详细信息，请参阅[添加用于组织用户和设备的组](groups-add.md)。

10. 从 [Intune](https://aka.ms/intuneportal) 中，选择“帮助和支持”以请求帮助。 作为 IT 管理员，你可以使用“帮助和支持”选项来搜索和查看解决方案，以及为 Intune 提交在线支持工单。 

    ![“帮助和支持”窗格的屏幕截图](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-10.png)

    若要创建支持工单，必须将帐户指定为 Azure Active Directory 中的管理员角色。 管理员角色包括“Intune 管理员”、“全局管理员”和“服务管理员”。 有关详细信息，请参阅[如何获取对 Microsoft Intune 的支持](get-support.md)。

11. 从 [Intune](https://aka.ms/intuneportal) 中，选择“租户状态”以显示有关 Intune 租户的详细信息。

    ![“租户状态”窗格的屏幕截图](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-11.png)

    租户状态详细信息包括连接器状态、Intune 服务运行状况和 Intune 新闻。 如果租户或 Intune 本身存在任何问题，可在“租户状态”窗格中找到详细信息。 有关详细信息，请参阅 [Intune 租户状态](tenant-status.md)。

12. 从 [Intune](https://aka.ms/intuneportal) 中，选择“疑难解答”，以获取有关疑难解答提示、请求支持或检查 Intune 状态的快捷方式。 此信息特定于所选定的 Intune 用户。

    ![“疑难解答”窗格的屏幕截图](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-12.png)

有关 Intune 内部故障排除的详细信息，请参阅[使用疑难解答门户帮助公司的用户](help-desk-operators.md)。

## <a name="configure-the-azure-portal"></a>配置 Azure 门户

可使用 Azure 自定义和配置门户的视图。

### <a name="change-the-sidebar"></a>更改边栏

Azure 门户左侧的边栏以列表形式显示了所有可用的 Azure 服务。 用户可更改此详细列表的默认视图，以便始终能够看见最重要的服务。 以下信息将使用 Intune 作为服务示例，并将其添加到列表顶部。

![用户在“更多服务”列表中搜索 Microsoft Intune。](./media/azure-add-intune1.png)

1. 从页面左侧的边栏中选择“所有服务”。
2. 在筛选框中搜索“Intune”。
3. 选择星形图标，将 Intune 添加到收藏的服务列表的底部。
4. 将鼠标悬停在 Intune 服务上方。 使用服务名称右侧竖向排列的三个点选择并拖动 Intune。

### <a name="change-the-dashboard"></a>更改仪表板

默认登录页面为仪表板。 用户可以在此页中自定义磁贴，使其显示与用户最相关的信息。

![常规新仪表板的图像。 图像左侧显示了包含所有服务的边栏，中间是主仪表板。 仪表板修改按钮排列在顶部，其他区域分布有可用于访问所有资源、快速入门教程、服务运行状况以及 Azure Marketplace 的磁贴。](./media/azure-default-dashboard.png)

若要修改当前仪表板，可选择“编辑仪表板”按钮。 如果不想更改默认的仪表板，还可以“新建仪表板”。 创建新仪表板时会得到一个带有“磁贴库”的空白专用仪表板，通过它可以添加或重新排列磁贴。 可按磁贴的“常规”类别和“类型”，通过“搜索”、“资源组”或“标记”来查找磁贴。

也可以选择省略号按钮，然后选择“固定到仪表板”将磁贴直接添加到仪表板。

![Intune 中“用户和组”>“所有组”位置的详细信息图，图中组的最右侧显示了“固定到仪表板”选项。](./media/azure-pin-to-dashboard.png)

将组和用户等更多内容添加到 Intune 后，此功能相关性会更高。

## <a name="next-steps"></a>后续步骤

若要在 Microsoft Intune 上快速运行，请先通过设置免费的 Intune 帐户逐步完成 Intune 快速入门。

> [!div class="nextstepaction"]
> [快速入门：免费试用 Microsoft Intune](free-trial-sign-up.md)


