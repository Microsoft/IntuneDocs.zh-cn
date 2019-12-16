---
title: 教程 - 在 Microsoft 终结点管理器中演练 Intune
titleSuffix: Microsoft Intune
description: 在本教程中，你将在 Microsoft 终结点管理器管理中心中浏览 Microsoft Intune，以更好地了解如何完成任务。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/06/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to learn where to find the different features in Intune from the Microsoft Endpoint Manager admin center.
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 267f09c3dc16aab10fbe64f0e8662ee6f7c7ffa0
ms.sourcegitcommit: ec69e7ccc6e6183862a48c1b03ca6a3bf573f354
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/07/2019
ms.locfileid: "74907987"
---
# <a name="tutorial-walkthrough-intune-in-microsoft-endpoint-manager"></a>教程：Microsoft 终结点管理器中的 Intune 演练

[Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure) 包含 100 多项服务，可以帮助你处理各种云计算方案和可能性。 Microsoft Intune 是 Azure 中可用的多种服务之一。 Intune 可帮助你确保公司的设备、应用和数据符合公司的安全要求。 你可以控制设置需要检查哪些需求以及在不满足这些需求时会发生什么情况。 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)可用于查找 Microsoft Intune 服务和其他与设备管理相关的设置。 了解 Intune 中可用的功能将帮助你完成各种移动设备管理 (MDM) 和移动应用管理 (MAM) 任务。

> [!NOTE]
> Microsoft 终结点管理器是用于管理所有终结点的单个集成式终结点管理平台。 此 Microsoft 终结点管理器管理中心集成了 ConfigMgr 和 Microsoft Intune。

在本教程中，你将：
> [!div class="checklist"]
> * 浏览 Microsoft 终结点管理器管理中心
> * 自定义 Microsoft 终结点管理器管理中心的视图

如果没有 Intune 订阅，请[注册免费试用帐户](free-trial-sign-up.md)。

## <a name="prerequisites"></a>必备条件
在设置 Microsoft Intune 之前，请查看以下要求：

- [支持的操作系统和浏览器](../supported-devices-browsers.md) 
- [网络配置要求和带宽](../network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>注册 Microsoft Intune 免费试用版

可以免费试用 Intune 30 天。 如果已有工作或学校帐户，请使用该帐户进行“登录”，并将 Intune 添加到订阅中  。 否则，也可通过注册[创建免费试用帐户](free-trial-sign-up.md)，以便为组织使用 Intune。

> [!IMPORTANT]
> 注册新帐户后，不能合并现有的工作或学校帐户。

## <a name="tour-microsoft-intune-in-the-microsoft-endpoint-manager-admin-center"></a>在 Microsoft 终结点管理器管理中心浏览 Microsoft Intune

请按照以下步骤操作，以通过 Microsoft 终结点管理器管理中心更好地了解 Intune。 完成导览后，将对 Intune 的一些主要区域有更好的理解。

1. 打开浏览器并登录 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。 如果你是 Intune 的新用户，请使用免费试用订阅。

    ![Microsoft 终结点管理器管理中心的屏幕截图 - 主页](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-01.png)

    当在 Azure 中打开 Microsoft 终结点管理器或任何其他服务时，服务将显示在一个窗格中。 可以在 Intune 中使用的部分首批工作负载包括“设备”、“应用”、“用户”和“组”     。 工作负载只是服务的子区域。 选择工作负载时，会以整页形式打开该窗格。 其他窗格在打开时从窗格右侧滑出，然后关闭以显示上一个窗格。 

    默认情况下，打开 Microsoft 终结点管理器时，你将看到“主页”窗格  。 此窗格提供了租户状态和合规性状态的整体视觉对象快照，以及其他有用的相关链接。

2. 从导航窗格中，选择“仪表板”以显示有关 Intune 租户中的设备和客户端应用的总体详细信息  。 如果从新的 Intune 租户开始，尚不具备任何已注册的设备。 

    ![Microsoft 终结点管理器管理中心的屏幕截图 - 仪表板](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-02.png)
    
    Intune 可让你管理员工的设备和应用，包括他们访问公司数据的方式。 要使用此移动设备管理 (MDM) 设备，必须先在 Intune 中注册设备。 设备注册后，系统会向其颁发 MDM 证书。 此证书可用于与 Intune 服务进行通信。 

    在 Intune 中注册工作人员设备的方法有多种。 每种方法取决于设备的所有权（个人或公司）、设备类型（iOS、Windows、Android）和管理需求（重置、关联、锁定）。 但是，在可以启用设备注册之前，必须设置 Intune 基础结构。 具体而言，设备注册需要用户[设置 MDM 机构](mdm-authority-set.md)。 有关准备好 Intune 环境（租户）的更多信息，请参阅[设置 Intune](setup-steps.md)。 准备好 Intune 租户后，即可注册设备。 有关设备注册的详细信息，请参阅[什么是设备注册？](../enrollment/device-enrollment.md)

3. 从导航窗格中，选择“设备”以显示有关 Intune 租户中的注册设备的详细信息  。 

    > [!TIP]
    > 如果你以前在 Azure 门户中使用过 Intune，则可以通过登录 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 并选择“设备”来找到 Azure 门户中的上述详细信息  。

    “设备 - 概述”窗格中提供了几个选项卡，可用于查看以下状态和警报的摘要  ：
    - **注册状态** - 按平台查看在 Intune 中注册的设备和注册失败的详细信息。
    - **注册警报** - 按平台了解未分配设备的更多详细信息。 
    - **合规性状态** - 按设备、策略、设置、威胁和保护查看合规性状态。 此外，此窗格还提供了一系列没有合规性策略的设备。
    - **配置状态** - 查看设备配置文件的配置状态和配置文件部署，以及 
    - **软件更新状态** - 查看所有设备和所有用户的部署状态的视觉对象。

    ![Microsoft 终结点管理器管理中心的屏幕截图 - 设备](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-03.png)

4. 从“设备 - 概述”中，选择“合规性策略”以显示有关由 Intune 管理的设备的合规性的详细信息   。 你将看到类似于下图的详细信息。

    ![Microsoft 终结点管理器管理中心的屏幕截图 - 合规性策略](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-04.png)
    
    > [!TIP]
    > 如果你以前在 Azure 门户中使用过 Intune，则可以通过登录 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 并选择“设备合规性”来找到 Azure 门户中的上述详细信息  。

    符合性要求实质上是一系列规则，例如要求设备 PIN 或要求设备加密。 设备符合性策略定义设备必须遵从的规则和设置，以便设备被视为符合。 若要使用设备符合性，必须具有：
    - Intune 和 Azure Active Directory (Azure AD) Premium 订阅
    - 运行受支持平台的设备
    - 须在 Intune 中注册的设备
    - 注册到一个用户或没有主要用户的设备。
    
    有关详细信息，请参阅 [Intune 中的设备符合性策略入门](../protect/device-compliance-get-started.md)。

5. 从“设备 - 概述”窗格”中，选择“条件访问”以显示有关访问策略的详细信息   。

    ![Microsoft 终结点管理器管理中心的屏幕截图 - 条件访问](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-05.png)

    > [!TIP]
    > 如果你以前在 Azure 门户中使用过 Intune，则可以通过登录 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 并选择“条件访问”来找到 Azure 门户中的上述详细信息  。

    条件访问是指控制允许连接到电子邮件和公司资源的设备和应用的方式。 若要了解基于设备和基于应用的条件访问，并查找使用 Intune 条件访问的常见方案，请参阅[什么是条件访问？](../protect/conditional-access.md)

6. 从导航窗格中，选择“设备” > “配置文件”以显示有关 Intune 中的设备配置文件的详细信息   。

    ![Microsoft 终结点管理器管理中心的屏幕截图 - 配置文件](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-06.png)
    
    > [!TIP]
    > 如果你以前在 Azure 门户中使用过 Intune，则可以通过登录 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 并选择“设备配置”来找到 Azure 门户中的上述详细信息  。

    Intune 提供可在组织内的不同设备上启用或禁用的设置和功能。 这些设置和功能将添加到“配置文件”。 你可以为不同的设备和不同的平台（包括 iOS、Android、macOS 和 Windows）创建配置文件。 然后，可以使用 Intune 将配置文件应用于组织中的设备。   

    有关设备配置的详细信息，请参阅[对 Microsoft Intune 中使用设备配置文件的设备应用功能设置](../configuration/device-profiles.md)。

7. 从导航窗格中，选择“设备” > “所有设备”以显示有关 Intune 租户的注册设备的详细信息   。 如果开始注册一个新的 Intune，尚不具备任何已注册的设备。

    ![Microsoft 终结点管理器管理中心的屏幕截图 - 所有设备](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-07.png)

    此设备列表显示了有关合规性、OS 版本和上次签入日期的关键详细信息。

    > [!TIP]
    > 如果你以前在 Azure 门户中使用过 Intune，则可以通过登录 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 并选择“设备” > “所有设备”来找到 Azure 门户中的上述详细信息   。
 
8. 从导航窗格中，选择“应用”以显示应用状态概览  。 此窗格根据以下选项卡提供应用的安装状态：

    > [!TIP]
    > 如果你以前在 Azure 门户中使用过 Intune，则可以通过登录 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 并选择“客户端应用”来找到 Azure 门户中的上述详细信息  。

    “设备 - 概述”窗格中提供了两个选项卡，可用于查看以下状态的摘要  ：
    - 安装状态 - 按设备查看最常见的安装失败，以及发生安装失败的应用  。  
    - 应用保护策略状态 - 了解有关为应用保护策略分配的用户以及标记用户的详细信息  。

    ![Microsoft 终结点管理器管理中心的屏幕截图 - 应用](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-08.png)

    IT 管理员可以使用 Microsoft Intune 来管理公司员工使用的客户端应用。 除了此功能外，还可管理设备和保护数据。 管理员的首要任务之一是，确保最终用户能够访问他们在执行工作时所需的应用。 此外，还建议分配和管理未向 Intune 注册的设备上的应用。 Intune 提供各种功能，用于在所需的设备上获取需要的应用。 

    > [!NOTE]
    > “应用 - 概述”窗格还提供了租户状态和帐户详细信息  。

    有关添加和分配应用的详细信息，请参阅[将应用添加到 Microsoft Intune](../apps/apps-add.md) 和[将应用分配给具有 Microsoft Intune 的组](../apps/apps-deploy.md)。

9. 从“应用-概述”窗格中，选择“所有应用”以查看添加到 Intune 的一系列应用   。

    > [!TIP]
    > 如果你以前在 Azure 门户中使用过 Intune，则可以通过登录 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 并选择“客户端应用” > “应用”来找到 Azure 门户中的上述详细信息   。

    可以根据平台将各种不同类型的应用添加到 Intune。 添加应用后即可将其分配给用户组。 

    ![Microsoft 终结点管理器管理中心的屏幕截图 - 所有应用](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-09.png)

    有关详细信息，请参阅[将应用添加到 Microsoft Intune](~/apps/apps-add.md)。 

10. 从导航窗格中，选择“用户”以显示有关包含在 Intune 中的用户的详细信息  。 这些用户是公司的员工。

    ![Microsoft 终结点管理器管理中心的屏幕截图 - 用户](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-10.png)

    > [!TIP]
    > 如果你以前在 Azure 门户中使用过 Intune，则可以通过登录 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 并选择“用户”来找到 Azure 门户中的上述详细信息  。

    你可以将用户直接添加到 Intune，也可以从本地 Active Directory 同步用户。 添加后，用户可注册设备并访问公司资源。 还可以为用户授予访问 Intune 的其他权限。 有关详细信息，请参阅[添加用户并授予对 Intune 的管理权限](users-add.md)。

11. 从导航窗格中，选择“组”以显示有关 Intune 中包含的 Azure Active Directory (Azure AD) 组的详细信息  。 作为 Intune 管理员，可以使用组来管理设备和用户。

    ![Microsoft 终结点管理器管理中心的屏幕截图 - 组](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-11.png)

    > [!TIP]
    > 如果你以前在 Azure 门户中使用过 Intune，则可以通过登录 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 并选择“组”来找到 Azure 门户中的上述详细信息  。

    你可以设置适合你组织需求的组。 创建组，以便按地理位置、部门或硬件特性来组织用户或设备。 使用组来管理大规模的任务。 例如，可设置用于大量用户的策略，或向一组设备部署应用。 有关组的详细信息，请参阅[添加用于组织用户和设备的组](../groups-add.md)。

12. 从导航窗格中，选择“租户管理”以显示有关 Intune 租户的详细信息  。

    > [!TIP]
    > 如果你以前在 Azure 门户中使用过 Intune，则可以通过登录 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 并选择“租户状态”来找到 Azure 门户中的上述详细信息  。

    “租户管理员 - 租户状态”窗格提供了“租户详细信息”、“连接器状态”和“服务运行状况仪表板”的选项卡     。 如果租户或 Intune 本身存在任何问题，你将在此窗格中找到可用的详细信息。 

    ![Microsoft 终结点管理器管理中心的屏幕截图 - 租户状态](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-12.png)

    有关详细信息，请参阅 [Intune 租户状态](../tenant-status.md)。

13. 从导航窗格中，选择“故障排除 + 支持” > “故障排除”以检查特定用户的状态详细信息   。 

    > [!TIP]
    > 如果你以前在 Azure 门户中使用过 Intune，则可以通过登录 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 并选择“故障排除”来找到 Azure 门户中的上述详细信息  。

    从“分配”下拉列表中，可以选择查看客户端应用、策略、更新通道和注册限制的目标分配  。 此外，此窗格还提供了特定用户的设备详细信息、应用保护状态和注册失败信息。

    ![Microsoft 终结点管理器管理中心的屏幕截图 - 故障排除](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-13.png)

    有关 Intune 内部故障排除的详细信息，请参阅[使用疑难解答门户帮助公司的用户](../help-desk-operators.md)。

14. 从导航窗格中，选择“故障排除 + 支持” > 帮助和支持”以请求帮助   。 

    > [!TIP]
    > 如果你以前在 Azure 门户中使用过 Intune，则可以通过登录 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 并选择“帮助和支持”来找到 Azure 门户中的上述详细信息  。

    作为 IT 管理员，你可以使用“帮助和支持”选项来搜索和查看解决方案，以及为 Intune 提交在线支持工单  。 

    ![Microsoft 终结点管理器管理中心的屏幕截图 - 帮助和支持](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-14.png)

    若要创建支持工单，必须将帐户指定为 Azure Active Directory 中的管理员角色。 管理员角色包括“Intune 管理员”、“全局管理员”和“服务管理员”    。 

    有关详细信息，请参阅[如何获取对 Microsoft Intune 的支持](../get-support.md)。

15. 从导航窗格中，选择“故障排除 + 支持” > “引导式方案”以显示可用的 Intune 引导式方案   。 

    引导式方案是围绕一个端到端用例而定制的一系列步骤。 常见方案基于管理员、用户或设备在组织中扮演的角色。 这些角色通常需要精心设计的配置文件、设置、应用程序和安全控件的集合，以提供最佳的用户体验和安全性。

    如果不熟悉实现特定 Intune 方案所需的所有步骤和资源则可以使用引导式方案作为起点。 

    ![Microsoft 终结点管理器管理中心的屏幕截图 - 引导式方案](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-15.png)

    有关引导式方案的详细信息，请参阅[引导式方案概述](~/fundamentals/guided-scenarios-overview.md)。

## <a name="configure-the-microsoft-endpoint-manager-admin-center"></a>配置 Microsoft 终结点管理器管理中心

可使用 Azure 自定义和配置门户的视图。

### <a name="change-the-dashboard"></a>更改仪表板

“仪表板”用于显示有关 Intune 租户中的设备和客户端应用的总体详细信息  。 通过仪表板可以在 Microsoft 终结点管理器管理中心创建集中且整齐的视图。 使用仪表板作为工作区，可在其中快速启动用于日常操作的任务以及监视资源。 例如，根据项目、任务或用户角色生成自定义仪表板。 Microsoft 终结点管理器管理中心提供了一个默认的仪表板，你可以使用它开始操作。 你可以编辑默认仪表板、创建和自定义其他仪表板，以及发布和共享仪表板，以使其可供其他用户使用。 

   ![Microsoft 终结点管理器管理中心的屏幕截图 - 仪表板](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-16.png)

若要修改当前仪表板，请选择“编辑”  。 如果不想更改默认的仪表板，还可以“新建仪表板”  。 创建新仪表板时会得到一个带有“磁贴库”的空白专用仪表板，通过它可以添加或重新排列磁贴  。 可以按类别或资源类型查找磁贴。 也可以搜索特定的磁贴。 选择“我的仪表板”，选择任何现有的自定义仪表板  。

### <a name="change-the-portal-settings"></a>更改门户设置

可以通过选择默认视图、主题、凭据超时期限以及语言与区域设置来自定义 Microsoft 终结点管理器管理中心。

   <img alt="Screenshot of the Microsoft Endpoint Manager admin center - Portal settings" src="./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-17.png" width="250">

## <a name="next-steps"></a>后续步骤

若要在 Microsoft Intune 上快速运行，请先通过设置免费的 Intune 帐户逐步完成 Intune 快速入门。

> [!div class="nextstepaction"]
> [快速入门：免费试用 Microsoft Intune](free-trial-sign-up.md)
