---
title: 如何监视应用保护策略
titleSuffix: Microsoft Intune
description: 本主题介绍如何在 Intune 中监视移动应用管理策略的符合性状态。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/20/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2d8c34f1947a0abaa4cdf0bbcd65dcf31e4c11ff
ms.sourcegitcommit: 93286c22426dcb59191a99e3cf2af4ff6ff16522
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2019
ms.locfileid: "59566784"
---
# <a name="how-to-monitor-app-protection-policies"></a>如何监视应用保护策略
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

将移动应用管理 (MAM) 策略应用到用户后，可在 [Azure 门户](https://portal.azure.com)的 Intune 应用保护窗格中监视策略的符合性状态。 此外，可找到的信息包括受 MAM 策略影响的用户、MAM 策略符合性状态和用户可能遇到的任何问题。

可在 3 个不同的位置监视 MAM 策略的符合性状态：
-   摘要视图
-   详细视图
-   报表视图

> [!NOTE]
> 有关创建应用保护策略的信息，请参阅[如何创建和分配应用保护策略](app-protection-policies.md)。

## <a name="summary-view"></a>摘要视图

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 在“Intune”窗格中，选择“客户端应用”。
4. 在“客户端应用”工作负荷中，选择“监视”部分的“应用保护状态”，查看摘要视图：

![“Intune 移动应用程序管理”窗格上的“摘要”磁贴](./media/app-protection-user-status-summary.png)

- **分配的用户**：贵公司中使用与工作环境中策略相关的应用且受保护和获许可的分配用户，以及未受保护和未获得许可的分配用户的总数。
- **已标记用户**：遇到问题的用户数。 将已越狱 (iOS) 和取得 root 权限的设备报告在“已标记用户”下。 在此处报告具有由 Google SafetyNet 设备证明检查（如果 IT 管理员已启用）标记的设备的用户。 
- “iOS 用户状态”和“Android 用户状态”：已在相关平台的工作环境中使用某应用且已分配到策略的用户数。 此信息显示策略托管的用户数量，以及正在工作环境中使用任何策略均不以其为目标的应用的用户数。 可以考虑将这些用户添加到策略。
- **受保护的热门 iOS 应用**：根据最常用的 iOS 应用，此信息显示受保护和未受保护的 iOS 应用数。
- **受保护的热门 Android 应用**：根据最常用的 Android 应用，此信息显示受保护和未受保护的 Android 应用数。
- **未注册的热门已配置 iOS 应用**：根据未注册设备的最常用的 iOS 应用，此信息显示已配置的 iOS 应用数。
- **未注册的热门已配置 Android 应用**：根据未注册设备的最常用的 Android 应用，此信息显示已配置的 Android 应用数。

    > [!NOTE]
    > 如果每个平台有多个策略且已至少为某个用户分配了一个策略，则该用户被视为由策略管理。

## <a name="detailed-view"></a>详细视图
可以通过选择“用户状态”磁贴（基于设备操作系统平台）和“已标记用户”磁贴转到摘要的详细视图。

### <a name="user-status"></a>用户状态
可搜索单个用户并查看该用户的合规性状态。 “应用报告”窗格显示已选择用户的以下信息：
- **图标**：显示应用状态是否是最新的。
- **应用名称**：应用的名称。
- **设备名**：与用户帐户关联的设备。
- **设备类型**：设备所运行的设备或操作系统的类型。
- **策略**：与应用关联的策略。
- **状态**：
  - **已签入**：策略已部署到用户，且应用在工作环境中至少使用了一次。
  - **未签入**：策略已部署到用户，但应用从部署策略起尚未在工作环境中使用。
- **上次同步时间**：上次同步设备的时间。

>[!NOTE]
> 如果搜索的用户没有部署 MAM 策略，你将看到一条消息，告知你用户不是任何 MAM 策略的目标对象。

若要查看用户的报告，请按照这些步骤进行操作：

1.  若要选择用户，请选择“用户状态”摘要磁贴。

    ![Intune 移动应用管理的“摘要”磁贴的屏幕截图](./media/MAM-reporting-6.png)

2. 在打开的“应用报表”窗格中，选择“选择用户”以搜索 Azure Active Directory 用户。

    ![“应用报告”窗格上的“选择用户”选项的屏幕截图](./media/MAM-reporting-2.png)

3. 从列表中选择一个用户。 可以看到该用户符合性状态的详细信息。

### <a name="flagged-users"></a>已标记用户
详细视图显示错误消息、错误发生时访问的应用、受影响的设备操作系统平台和时间戳。 在此处报告具有由 Google SafetyNet 设备证明检查标记的设备的用户，原因是“由 Google 报告”。

## <a name="reporting-view"></a>报表视图

可以在“应用保护状态”边栏选项卡顶部找到相同报表。

> [!NOTE]
> Intune 提供其他设备报告字段，包括 Android 注册 ID、Android 制造商、模型和安全修补程序版本以及 iOS 型号。 在 Intune 中，通过选择“客户端应用” > “应用保护状态”并选择“应用保护报告: iOS、Android”来获取这些字段。 此外，这些参数将帮助你配置设备制造商“允许”列表 (Android)、设备型号的“允许”列表（Android 和 iOS）和最低 Android 安全修补程序版本设置。 

其他报表也可以帮助了解 MAM 策略符合性状态。 若要查看这些报表，请选择“客户端应用” > “应用保护状态” > “报表”。 

“报表”边栏选项卡根据用户和应用提供多个报表，包括以下内容：


- **用户报表**：此报表概述了可在以上[详细视图](app-protection-policies-monitor.md#detailed-view)部分下的“用户状态”报表中找到的相同信息。

- **应用报表**：除了选择平台和应用之外，此报表还提供了生成报表前可选择的两种不同应用保护状态。 状态可以是“受保护”，也可以是“不受保护”。

    -   托管 MAM 活动的用户状态（受保护）：此报表概述了每个用户的每个托管 MAM 应用的活动。 它显示了每个用户的 MAM 策略所面向的所有应用，并通过 MAM 策略将每个应用的状态细分为“已签入”，或者显示以 MAM 策略为目标但应用从未签入的应用。
    -   非托管 MAM 活动的用户状态（不受保护）：此报表概述了每个用户目前已启用 MAM 的非托管应用的活动。 发生这种情况的原因如下：
        -   用户正在使用这些应用，或者这些应用是 MAM 策略目前未针对的应用。
        -   已签入所有应用，但应用还未获取任何 MAM 策略。

        ![用户“应用报告”边栏选项卡的屏幕截图，其中包含 3 个应用的详细信息](./media/MAM-reporting-4.png)

- **用户配置报表**：根据所选用户，此报表提供了有关用户已收到的任何应用配置的详细信息。
- **应用配置报表**：根据所选平台和应用，此报表提供了有关哪些用户已收到所选应用的配置的详细信息。
- **Windows 信息保护的应用学习报告**：此报表显示哪些应用正在试图违反策略。
- **Windows 信息保护的网站学习**：此报表显示哪些网站正在试图违反策略。

## <a name="table-grouping"></a>表格分组

显示“应用保护用户报表”数据后，可按照以下方式聚合数据：

- **验证结果：** 数据显示为按应用保护状态分组，可能是失败、警告或成功。
- **应用名称：** 数据显示为按应用（实际应用名称）分组，有失败、警告或成功。

## <a name="export-app-protection-activities-to-csv"></a>将应用保护活动导出到 CSV

可以将所有应用保护策略活动导出到单个 .csv 文件。 这可帮助分析用户报告的所有应用保护状态。

按照下列步骤进行操作可生成应用保护报表：

1. 在“Intune 移动应用程序管理”窗格中，选择“应用保护报表”。

    ![应用保护下载链接的屏幕截图](./media/app-protection-report-csv-2.png)

2. 选择“是”以保存报表，然后选择“另存为”，并选择要在其中保存报表的文件夹。

    ![“保存报表”确认框的屏幕截图](./media/app-protection-report-csv-1.png)

## <a name="see-also"></a>另请参阅
- [管理 iOS 应用之间的数据传输](data-transfer-between-apps-manage-ios.md)
- [Android 应用由应用保护策略托管时会出现的情况](app-protection-enabled-apps-android.md)
- [iOS 应用由应用保护策略托管时会出现的情况](app-protection-enabled-apps-ios.md)
