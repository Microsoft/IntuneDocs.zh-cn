---
title: Microsoft Intune 中适用于企业的 Windows 更新设置 - Azure | Microsoft Docs
description: 可以使用 Intune 部署的适用于 Windows 10 设备的 WUfB 设置。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: e44f9d0848d449ef9131c76784ca8c7244b7c223
ms.sourcegitcommit: b78793ccbef2a644a759ca3110ea73e7ed6ceb8f
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 08/16/2019
ms.locfileid: "69550110"
---
# <a name="windows-update-settings-for-intune"></a>Intune 中的 Windows 更新设置  

查看可以通过 Microsoft Intune [配置和管理](windows-update-for-business-configure.md)的 Windows 10 更新设置。  

在 Intune 中配置适用于 Windows 10 更新通道的设置时，将配置 Windows 更新设置。 如果 Windows 更新设置具有 Windows 10 版本依赖关系，则在设置详细信息中会记录版本依赖关系。  

## <a name="update-settings"></a>更新设置  

更新设置可控制设备将要下载的位和时间。 有关每个设置的行为的详细信息，请参阅 Windows 参考文档。  

- 服务频道   
  **默认值**：半年频道  
  Windows 更新 CSP: [Update/BranchReadinessLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-branchreadinesslevel)  

  设置设备从中接收 Windows 更新的频道（分支）。 在交付更新前，不同的频道可以使用不同的延迟期。  

  例如，半年频道  具有六个月的延迟期。 如果使用此频道而没有此设置主体的任何其他延迟，则设备将在更新发布后的六个月安装该更新。  

  支持的更新频道：  

  - 半年频道  
  - 半年频道(定向)  
  - Windows 预览体验计划 - 快  
  - Windows 预览体验计划 - 慢  
  - 发布 Windows 预览体验计划  

  如果选择预览体验计划频道，则 Intune 将自动配置 Windows 更新设置 [Update/ManagePreviewBuilds](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-managepreviewbuilds)，以便此预览体验计划正常运行。  


  > [!IMPORTANT]  
  > 从 Windows 版本 1903 开始，停用半年频道(定向)  (SAC-T)。 通过这一更改，SAC-T 与半年频道  合并。 若要详细了解这一更改及其对适用于企业的 Windows 更新所产生的影响，请参阅 Windows IT 专业人员博客文章[适用于企业的 Windows 更新和 SAC-T 的停用](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/Windows-Update-for-Business-and-the-retirement-of-SAC-T/ba-p/339523)。  
 
- Microsoft 产品更新   
  **默认值**：允许  
  Windows 更新 CSP: [Update/AllowMUUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowmuupdateservice)

  - **允许**-选择 "*允许*" 以扫描 Microsoft 更新中的应用更新。  
  - **块**-选择 "阻止" 以阻止扫描应用更新。  

- **Windows 驱动程序**  
  **默认值**：允许  
  Windows 更新 CSP: [Update/ExcludeWUDriversInQualityUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-excludewudriversinqualityupdate)  

  - **允许**-选择 "*允许*在更新过程中包含 Windows 更新驱动程序"。  
  - **块**选择阻止扫描驱动程序。  

- **质量更新延迟期(天)**  
  **默认值**：0  
  Windows 更新 CSP: [Update/DeferQualityUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferqualityupdatesperiodindays)  

  指定质量更新延迟的天数（从 0 到 30）。 此期限是属于所选的服务频道的任何延迟期以外的期限。 延迟期在设备收到策略时开始。  

  质量更新通常是对现有 Windows 功能的修复和改进。  

- **功能更新延迟期(天)**  
  **默认值**：0  
  Windows 更新 CSP: [Update/PauseFeatureUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferfeatureupdatesperiodindays)  

  指定功能更新延迟天数。 此期限是属于所选的服务频道的任何延迟期以外的期限。 延迟期在设备收到策略时开始。  

  支持的延迟期：  

  - *Windows 版本1709及更高版本*-0 到365天  
  - *Windows 版本 1703* - 0 至 180 天  

  功能更新通常是 Windows 的新功能。  

- **设置功能更新卸载期(2 到 60 天)**  
  **默认值**：10  
  Windows 更新 CSP: [Update/ConfigureFeatureUpdateUninstallPeriod](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configurefeatureupdateuninstallperiod)  

  配置无法卸载功能更新的时间。  

  当此期限到期后，会从设备中删除之前的更新位，并且无法再将其卸载到以前的更新版本。  

  例如，功能更新卸载期为 20 天的更新通道。 在 25 天后，你决定回滚到最新的功能更新并使用“卸载”选项。  在 20 天以前安装了功能更新的设备无法卸载更新，因为它们已删除了作为维护一部分的必需的位。 但是，在 19 天以前仅安装了功能更新的设备可以卸载更新（如果它们在超过 20 天的卸载期前成功签入以接收卸载命令）。  

## <a name="user-experience-settings"></a>用户体验设置  

用户体验设置控制设备重启和提醒的最终用户体验。 有关每个设置的行为的详细信息，请参阅 Windows 更新 CSP 文档。  

- 自动更新行为   
  **默认值**：在维护时间自动安装  
  Windows 更新 CSP: [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

  选择自动更新的安装方式，如有必要，选择重启设备的时间。  

  支持的选项：  

  - **通知下载** - 在下载更新前通知用户。 用户选择下载和安装更新。  

  - **在维护期自动安装** - 自动下载更新，然后在设备未使用或在电池电源上运行时的自动维护期间安装。 当需要重启时，系统将连续七天提示用户重启，在这之后将强制重启。  

    此选项可在更新安装后自动重启设备。 使用“活动时间”  设置来定义阻止自动重启的时间段：  

    - **活动时间开始** - 指定由于更新安装所导致的取消重启的开始时间。  
      **默认**：上午 8 点  
      Windows 更新 CSP: [Update/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
  
    - **活动时间结束** - 指定由于更新安装所导致的取消重启的结束时间。  
      **默认值**：下午 5 点  
      Windows 更新 CSP: [Update/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  

  - **在维护期自动安装和重启** – 自动下载更新，然后在设备未使用或在电池电源上运行时的自动维护期间安装。 需要重启时，设备将在未使用时重启。 （这是非托管设备的默认设置。）  

    此选项可在更新安装后自动重启设备。 在 Windows 更新设置中未说明“活动时间”设置的使用，但 Intune 使用此设置来定义阻止自动重启的时间段  ：  

    - **活动时间开始** - 指定由于更新安装所导致的取消重启的开始时间。  
      **默认**：上午 8 点  
      Windows 更新 CSP: [Update/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
  
    - **活动时间结束** - 指定由于更新安装所导致的取消重启的结束时间。  
      **默认值**：下午 5 点  
      Windows 更新 CSP: [Update/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  

  - **在计划时间自动安装和重启** - 指定安装日期和时间。 如果未指定，则安装程序将在每天凌晨 3 点运行，随后进行 15 分钟倒计时以执行重启。 登录的用户可以延迟倒计时和重启。   
  Windows 更新 CSP: [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

    此选项支持其他设置。  

    - **自动行为频率** - 使用此设置计划安装更新的时间，包括星期、天和时间。  
      **默认值**：每周

    - **计划安装日期** - 指定要在星期几安装更新。  
      **默认值**：任意一天  

    - **计划安装时间** - 指定要在一天中安装更新的时间。  
      **默认值**：上午 3 点  

  - **无需最终用户控制即可自动安装并重启** - 自动下载更新，然后在设备未使用或在电池电源上运行时的自动维护期间安装。 需要重启时，设备将在未使用时重启。 此选项将最终用户控制窗格设置为只读。  

  - **重置为默认值** - 在运行“2018 年 10 月”更新或更高版本更新的 Windows 10 计算机上还原原始的自动更新设置。  


- **重启检查**  
  **默认值**：允许  
  Windows 更新 CSP: [Update/SetEDURestart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setedurestart)  

  要在重启设备时跳过这些检查，请选择“跳过”  。 
  
  此设置具有不同的结果，具体取决于 Windows 的设备版本：  
 
  - *Windows 版本 1703 和更早版本* - 重启设备时，会出现一些检查项，包括检查活跃用户、电池剩余电量和正在运行的游戏等。  
  
  - *Windows 版本 1709 及更高版本* - 在活动时间，不为更新运行以下进程：扫描、下载、安装和重启。 在活动时间后，只要通过电池和电源检查，更新进程就会运行并可将设备从睡眠状态唤醒、扫描、下载、安装和重启设备。 

- **阻止用户暂停 Windows 更新**  
  **默认值**：允许  
  Windows 更新 CSP: [Update/SetDisablePauseUXAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisablepauseuxaccess)  

  - **允许**-允许设备用户暂停更新的安装。  
  - **阻止**-防止设备用户暂停更新的安装。  

- **阻止用户扫描 Windows 更新**  
  **默认值**：允许  
  Windows 更新 CSP: [Update/SetDisableUXWUAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisableuxwuaccess) 

  - **允许**-允许设备用户使用 Windows 更新扫描查找并下载更新并安装功能。
  - **阻止**-防止设备用户访问 Windows 更新扫描、下载更新和安装功能。  

- **需要用户批准才能在工作时间之外重启**  
  **默认值**：未配置  
  Windows 更新 CSP: [Update/AutoRestartRequiredNotificationDismissal](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-autorestartrequirednotificationdismissal)
  
  - 未配置   
  - **必需** - 要求用户批准在工作时间以外进行设备重启。  
   
- **通过可消除的提醒提前提醒用户需要自动重启(小时)**  
  **默认值**：4  
  Windows 更新 CSP: [Update/ScheduleRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-schedulerestartwarning)  

  指定在自动重启前提前多久向设备用户显示有关该重启的可消除通知。 支持值 2  、4  、8  、12  或 24  小时。  
  
  清除默认值时, 此设置将变为 "*未配置*"。  

- **通过永久提醒提前提醒用户需要自动重启(分钟)**  
  **默认值**：15  
  Windows 更新 CSP: [Update/ScheduleImminentRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduleimminentrestartwarning)  

  指定自动重启前提前多久向设备用户显示有关该重启的不可消除的警告。 支持值 15  、30  或 60  分钟。  

  清除默认值时, 此设置将变为 "*未配置*"。  

- **更改更新通知级别**  
  **默认**：使用默认 Windows 更新通知  
  Windows 更新 CSP: [Update/UpdateNotificationLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updatenotificationlevel)
  
  指定用户可见的 Windows 更新通知级别。 此设置不控制下载和安装更新的方式和时间。  

  支持的选项：
  - 未配置 
  - **使用默认 Windows 更新通知**
  - **关闭所有通知, 不包括重新启动警告**
  - **关闭所有通知, 包括重新启动警告**  

- **允许用户重启(预定重启)**  
  **默认值**：未配置  
  > [!IMPORTANT]  
  > 不再建议使用*预定重新启动*设置。 相反, 请使用新的*截止时间*设置, 该设置取代了*预定的重新启动*设置。 Intune 将在将来的更新中[弃用对*预定重启*设置的支持](whats-new.md#plan-for-change-new-windows-updates-settings-in-intune-)。

  Windows 10 版本1803及更高版本支持预定重启。 

  > [!NOTE]  
  > Windows 10 版本 1809 引入了其他重启提醒期设置，可向功能和质量更新应用单独的设置。 但是，由 Intune 管理的设置不会单独应用于不同的更新类型。 相反，Intune 向功能和质量更新应用相同的值。  
  
  - 未配置   
  - **必需** - 当设置为“必需”  时，将为 Windows 10 更新启用预定重启选项。 这些设置预定设备用户，以帮助管理在安装需要重启的更新后重启设备的时间。  

  有关此选项的详细信息，请参阅 Windows 10 文档中的[重启提醒期](https://docs.microsoft.com/windows/deployment/update/waas-restart#engaged-restart)以部署更新。  

  以下设置用于控制何时进行重启提醒期操作。  

  - **在自动重启后将用户转换为重启提醒期(天)**  
    **默认值**: 未配置 Windows 更新 CSP: [Update/EngagedRestartTransitionSchedule](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestarttransitionschedule)  
    
    指定更新安装后多久设备才执行预定重启行为（2 到 30 天）   。 在配置的天数后，用户将收到重启设备的提示。  

  - **推迟重启提醒期提醒(天)**  
    **默认值**：未配置    
    Windows 更新 CSP: [Update/EngagedRestartSnoozeSchedule](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestartsnoozeschedule)  
    
    指定一个介于**1**和**3**之间的值, 用于暂停重启提示符的时间长度。  推迟期限过后，将再次提供重启提示。 在到达安装截止时间前，用户可以继续推迟提醒。  

  - **设置等待重启的截止时间(天)**  
    **默认值**：未配置  
    Windows 更新 CSP: [Update/EngagedRestartDeadline](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestartdeadline)  
  
    指定在设备强制实施所需的重启前，开始执行预定重启行为后要等待的最大天数（2 到 30 天）   。 此重启将提示用户保存其工作。

- **使用截止时间设置**  
  **默认值**：未配置  
  > [!IMPORTANT]  
  > 从 Intune 的8月更新版开始, 我们建议使用以下用于替代预定重启设置的截止时间设置。 Intune 将在 Intune 的将来更新中[弃用对*预定重启*设置的支持](whats-new.md#plan-for-change-new-windows-updates-settings-in-intune-)。  

  允许用户使用截止时间设置。  

  - 未配置 
  - **允许**

  如果设置为 "*允许*", 则可以为截止时间配置以下设置:

  - **功能更新截止时间**  
    **默认值**：7  
    Windows 更新 CSP: [Update/ConfigureDeadlineForFeatureUpdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforfeatureupdates)  

    指定用户在其设备上自动安装功能更新前的天数 (2-30)。

  - **质量更新截止时间**  
    **默认值**：7  
    Windows 更新 CSP: [Update/ConfigureDeadlineForQualityUpdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforqualityupdates)

    指定用户在其设备上自动安装质量更新前的天数 (2-30)。

  - **宽限期**  
    **默认值**: 2 Windows 更新 CSP: [Update/ConfigureDeadlineGracePeriod]( https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlinegraceperiod)

    指定截止时间晚到截止时间的最小天数 (0-7)。

  - **截止时间之前自动重启**  
    **默认值**: 是 Windows 更新 CSP: [Update/ConfigureDeadlineNoAutoReboot](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlinenoautoreboot)

    指定设备是否应在截止时间之前自动重新启动。
    - **是**
    - **否**




### <a name="delivery-optimization-download-mode"></a>传递优化下载模式  

传递优化不再作为“软件更新”下的“Windows 10 更新圈”的一部分进行配置。 现在，传递优化通过设备配置进行设置。 但是，以前的配置在控制台中仍然可用。 可以通过将以前的配置编辑为“未配置”来删除这些配置，否则便无法对其进行修改  。 

为避免新旧策略之间的冲突，请参阅[从现有更新圈移动到传递优化](delivery-optimization-windows.md#move-existing-update-rings-to-delivery-optimization)，然后将设置移动到传递优化配置文件。
