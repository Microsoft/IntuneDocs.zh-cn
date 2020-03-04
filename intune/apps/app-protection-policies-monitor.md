---
title: 如何监视应用保护策略
titleSuffix: Microsoft Intune
description: 本主题介绍如何在 Intune 中监视应用保护策略。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/28/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 152edba9ba6821cc17960bfbbaef248459d12ac0
ms.sourcegitcommit: 9ee2401a2f01373a962749b0728c22385dbcba6d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181835"
---
# <a name="how-to-monitor-app-protection-policies"></a>如何监视应用保护策略
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

将应用保护策略应用到用户后，可在 [Azure 门户](https://portal.azure.com)的 Intune 应用保护窗格中监视策略的状态。 此外，可找到的信息包括受应用保护策略影响的用户、策略符合性状态和用户可能遇到的任何问题。

可在三个不同的位置监视应用保护策略：
- 摘要视图
- 详细视图
- 报表视图

应用保护数据的保持期为 90 天。 在过去 90 天内签入到 Intune 服务的任何应用实例都将包含在“应用保护状态”报表中。 应用实例  是唯一的用户 + 应用 + 设备。 

> [!NOTE]
> 有关详细信息，请参阅[如何创建和分配应用保护策略](app-protection-policies.md)。

## <a name="summary-view"></a>摘要视图

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
3. 选择“应用”   > “监视”   > “应用保护状态”  。

   ![Intune 移动应用管理窗格的“摘要”磁贴的屏幕截图](./media/app-protection-policies-monitor/app-protection-user-status-summary.png)

- **分配的用户**：贵公司中使用与工作环境中策略相关的应用且受保护和获许可的分配用户，以及未受保护和未获得许可的分配用户的总数。
- **已标记用户**：遇到设备问题的用户数。 将已越狱 (iOS/iPadOS) 和取得 root (Android) 权限的设备报告在“已标记用户”下  。 此外，在此处报告具有由 Google SafetyNet 设备证明检查（如果 IT 管理员已启用）标记的设备的用户。 
- **使用潜在有害应用的用户**：Android 设备上可能存在 Google Play Protect 检测到的有害应用的用户数。 
- “iOS 用户状态”和“Android 用户状态”   ：已在相关平台的工作环境中使用某应用且已分配到策略的用户数。 此信息显示策略托管的用户数量，以及正在工作环境中使用任何策略均不以其为目标的应用的用户数。 可以考虑将这些用户添加到策略。
- **受保护的热门 iOS/iPadOS 应用**和**受保护的热门 Android 应用**：根据最常用的 iOS/iPadOS 和 Android 应用，此信息显示平台保护和未保护的应用数。
- **未注册的热门已配置 iOS/iPadOS 应用**和**未注册的热门已配置 Android 应用**：根据未注册设备的最常用的 iOS/iPadOS 和 Android 应用，此信息显示平台已配置的应用数（例如使用应用配置策略）。

    > [!NOTE]
    > 如果每个平台有多个策略且已至少为某个用户分配了一个策略，则该用户被视为由策略管理。

## <a name="detailed-view"></a>详细视图
可以通过选择“已标记用户”  磁贴和“使用潜在有害应用的用户”  磁贴转到摘要的详细视图。

### <a name="flagged-users"></a>已标记用户
详细视图显示错误消息、错误发生时访问的应用、受影响的设备操作系统平台和时间戳。 此错误通常适用于已越狱 (iOS/iPadOS) 或获得 root 权限 (Android) 的设备。 此外，在此处报告具有由“SafetyNet 设备证明”条件启动检查标记的设备的用户，原因是“由 Google 报告”。 对于要从报表中删除的用户，设备本身的状态需要进行更改，这会在需要报告正面结果的下一次 root 权限检测检查（或越狱检查/SafetyNet 检查）后发生。 如果设备已真正修正，则会在重新加载窗格时刷新“已标记用户”报表。

### <a name="users-with-potentially-harmful-apps"></a>使用潜在有害应用的用户
在此处报告具有由“要求对应用进行威胁扫描”条件启动检查标记的设备的用户，威胁类别是“由 Google 报告”  。 如果此报表中列出了通过 Intune 部署的应用，请与应用开发人员联系，或删除要分配给用户的应用。 详细视图显示：

- **用户**：用户的名称。
- **应用包 ID**：Android OS 使用此方式对应用进行唯一的确定。
- **应用是否已启用 MAM**：是否正在通过 Microsoft Intune 部署应用。 
- **威胁类别**：此应用所属于的 Google 确定的威胁类别。 
- **电子邮件**：用户的电子邮件。
- **设备名**：与用户帐户关联的任意设备的名称。
- **时间戳**：此为 Google 上次与 Microsoft Intune 进行潜在有害应用同步的日期。

## <a name="reporting-view"></a>报表视图

可以在“应用保护状态”窗格顶部找到相同报表  。 若要查看这些报表，请选择“应用” > “应用保护状态” > “报表”    。 “报表”窗格根据用户和应用提供多个报表，包括以下内容  ：

### <a name="user-report"></a>用户报表
可搜索单个用户并查看该用户的合规性状态。 “应用报告”  窗格显示已选择用户的以下信息：
- **图标**：显示应用状态是否是最新的。
- **应用名称**：应用的名称。
- **设备名**：与用户帐户关联的设备。
- **设备类型**：设备所运行的设备或操作系统的类型。
- **策略**：与应用关联的策略。
- **状态**：
  - **已签入**：策略已部署到用户，且应用在工作环境中至少使用了一次。
  - **未签入**：策略已部署到用户，但应用从部署策略起尚未在工作环境中使用。
- **上次同步时间**：应用上次与 Intune 同步的时间。 

>[!NOTE]
> “上次同步时间”列在控制台内“用户状态”报表和“应用保护策略”[可导出的 .csv 报表](https://docs.microsoft.com/intune/app-protection-policies-monitor#export-app-protection-activities)中表示相同的值  。 差别在于两个报表中的值之间的同步存在较小延迟。 
>
> “上次同步时间”中引用的时间是 Intune 最后一次看到应用实例的时间。 当用户启动应用时，该应用可能会在启动期间通知 Intune 应用保护服务，具体取决于上次签入的时间。 请参阅[应用保护策略签入的重试间隔时间](~/apps/app-protection-policy-delivery.md)。 如果用户在上次签入时间间隔（活动使用时间通常为 30 分钟）内未使用该特定应用，并且他们启动了应用，那么：
>
> - 应用保护策略可导出的 .csv 报表会在 1 分钟（最小值）到 30 分钟（最大值）之间获得最新时间。
> - 用户状态报表会立即获得最新时间。
>
> 例如，假设有一个获许可的目标用户在中午 12:00 启动受保护的应用：
> - 如果这是首次登录，则表示用户已在之前注销，并且没有向 Intune 注册应用实例。 用户登录后，用户将获得新的应用实例注册，并且可以立即签入（未来签入的时间延迟与前面列出的时间延迟相同）。 因此，上次同步时间将在“用户状态”报表中报告为中午 12:00，并在“应用保护策略”报表中报告为中午 12:01（或最迟为中午 12:30）。 
> - 如果用户只是启动应用，则“上次同步时间”的报告时间取决于用户上次签入的时间。

若要查看用户的报告，请按照这些步骤进行操作：

1. 若要选择用户，请选择“用户状态”摘要磁贴  。

    ![Intune 移动应用管理的“摘要”磁贴的屏幕截图](./media/app-protection-policies-monitor/MAM-reporting-6.png)

2. 在“应用报表”  窗格中，选择“选择用户”  以搜索 Azure Active Directory 用户。

    ![“应用报告”窗格上的“选择用户”选项的屏幕截图](./media/app-protection-policies-monitor/MAM-reporting-2.png)

3. 从列表中选择一个用户。 可以看到该用户符合性状态的详细信息。

>[!NOTE]
> 如果搜索的用户没有部署 MAM 策略，你将看到一条消息，告知你用户不是任何 MAM 策略的目标对象。

### <a name="app-report"></a>应用报表
可以按平台和应用搜索，然后此报表会提供生成报表前可选择的两种不同应用保护状态。 状态可以是“受保护”，也可以是“不受保护”   。

  - 托管 MAM 活动的用户状态（受保护  ）：此报表概述了每个用户的每个托管 MAM 应用的活动。 它为每个用户显示了 MAM 策略所针对的所有应用，以及使用 MAM 策略签入的每个应用的状态。 此报表还包括 MAM 策略所针对但从未签入的每个应用的状态。
  - 非托管 MAM 活动的用户状态（不受保护  ）：此报表概述了每个用户目前已启用 MAM 的非托管应用的活动。 出现这种情况的原因可能是：
    - 用户正在使用这些应用，或者这些应用是 MAM 策略目前未针对的应用。
    - 已签入所有应用，但应用还未获取任何 MAM 策略。

    ![用户“应用报告”窗格的屏幕截图，其中包含三个应用的详细信息](./media/app-protection-policies-monitor/MAM-reporting-4.png)

### <a name="user-configuration-report"></a>**用户配置报表**
根据所选用户，此报表提供了有关用户已收到的任何应用配置的详细信息。

### <a name="app-configuration-report"></a>**应用配置报表**
根据所选平台和应用，此报表提供了有关哪些用户已收到所选应用的配置的详细信息。

### <a name="app-learning-report-for-windows-information-protection"></a>Windows 信息保护的应用学习报告
此报表显示哪些应用正在试图违反策略。

### <a name="website-learning-for-windows-information-protection"></a>Windows 信息保护的网站学习
此报表显示哪些网站正在试图违反策略。

## <a name="export-app-protection-activities"></a>导出应用保护活动
可以将所有应用保护策略活动导出到单个 .csv 文件。 这可帮助分析用户报告的所有应用保护状态。 **应用保护 .csv 文件显示的内容**：
- **用户**：用户的名称。
- **电子邮件**：用户的电子邮件。
- **应用**：应用的名称。
- **应用版本**：应用版本。
- **设备名**：与用户帐户关联的任意设备的名称。
- **设备制造商**：这会列出设备的制造商（仅 Android）。 
- **设备型号**：这会列出设备的制造商（仅 Android）。 
- **Android 修补程序版本**：最新的 Android 安全修补程序的日期。
- **AAD 设备 ID**：若设备已加入 AAD，将填充此列。
- **MDM 设备 ID**：若设备已注册 Microsoft Intune MDM，将填充此列。
- **平台**：操作系统。
- **平台版本**：操作系统版本。
- **管理类型**：设备管理类型。 例如，Android Enterprise、未经管理或 MDM。  
- **应用保护状态**：未受保护或受保护。
- **策略**：与应用关联的应用保护策略。
- **上次同步时间**：应用上次与 Microsoft Intune 同步的时间。 
- **符合性状态**：用户设备上的应用是否符合任何基于应用的条件访问策略。  

按照以下步骤生成应用保护 .csv 文件或应用程序配置 .csv 文件：

1. 在“Intune 移动应用程序管理”窗格中，选择“应用保护报表”  。

    ![应用保护下载链接的屏幕截图](./media/app-protection-policies-monitor/app-protection-report-csv-2.png)

2. 选择“是”  以保存报表，然后选择“另存为”  。 选择要保存报表的文件夹。

    ![“保存报表”确认框的屏幕截图](./media/app-protection-policies-monitor/app-protection-report-csv-1.png)
   
> [!NOTE]
> Intune 提供其他设备报告字段，包括应用注册 ID、Android 制造商、模型和安全修补程序版本以及 iOS/iPadOS 型号。 在 Intune 中，通过选择“应用” > “应用保护状态” > “应用保护报告: iOS/iPadOS、Android”来访问这些字段    。 此外，这些参数将帮助你配置设备制造商“允许”列表 (Android)、设备型号的“允许”列表（Android 和 iOS/iPadOS）和最低 Android 安全修补程序版本设置    。   
 
## <a name="see-also"></a>另请参阅
- [管理 iOS/iPadOS 应用之间的数据传输](data-transfer-between-apps-manage-ios.md)
- [Android 应用由应用保护策略托管时会出现的情况](../fundamentals/end-user-mam-apps-android.md)
- [iOS/iPadOS 应用由应用保护策略托管时会出现的情况](../fundamentals/end-user-mam-apps-ios.md)
