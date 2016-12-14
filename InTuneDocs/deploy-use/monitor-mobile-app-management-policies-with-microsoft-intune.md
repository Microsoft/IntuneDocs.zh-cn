---
title: "使用 Microsoft Intune 监视 MAM 策略| Microsoft Intune"
description: "查看有多少用户拥有策略，并深入了解获取详细信息。"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d3aa6c74-6b5d-4b50-aa66-a040ec44393e
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: 487fe778bae73c2ac5564f90c21328932060f576


---

# <a name="monitor-mobile-app-management-policies-with-microsoft-intune"></a>使用 Microsoft Intune 监视移动应用管理策略
设置移动应用管理 (MAM) 策略并将其应用到用户后，可在 [Azure 门户](https://portal.azure.com)上监视合规性状态。 Azure 门户包括有关受策略影响的用户、合规性状态和任何用户可能遭遇的问题的信息。
## <a name="summary-view"></a>摘要视图
可在“Intune 移动应用程序管理”边栏选项卡上查看合规性状态的摘要：


![“Intune 移动应用程序管理”边栏选项卡上的“摘要”磁贴。](../media/mam-azure-portal-user-status-summary.png)

-   **用户**：公司中正在使用与该策略相关联的应用的用户总数。

-   **由策略管理**：在工作环境中至少使用过其中一种应用的用户数量。

-   **无策略**：正在使用与该策略相关联的应用，但却不是策略的目标用户的数量。 可以考虑将这些用户添加到策略。

- **已标记用户**：遇到问题的用户数量。 目前仅将具有已越狱设备的用户报告在“已标记用户”下。


## <a name="detailed-view"></a>详细视图
可以通过选择“用户状态”磁贴和“已标记用户”磁贴转到摘要的详细视图。

### <a name="user-status"></a>用户状态
可搜索单个用户并查看该用户的合规性状态。 “应用报告”边栏选项卡显示已选择用户的以下信息：
- 与用户帐户关联的设备

- 设备上具有 MAM 策略的应用

- 状态:

  - **已签入**：策略已部署到用户，且应用在工作环境中至少使用了一次。

  - **未签入**：策略已部署到用户，但应用从那时起尚未在工作环境中使用。

>[!NOTE]
> 如果你搜索的用户没有部署 MAM 策略，你将看到一条消息，告知你用户不面向任何应用策略。

若要查看用户的报告，请按照这些步骤进行操作：

1.  要选择用户，单击“摘要”磁贴或在“设置”边栏选项卡上选择“应用报告(按用户)”选项：

    ![“设置”边栏选项卡上的“应用报告”选项](../media/mam-azure-portal-app-reporting-by-user-settings-blade.png)

2. 在打开的“应用报表”边栏选项卡上，选择“选择用户”以搜索 Azure Active Directory 用户。

    ![“应用报告”边栏选项卡上的“选择用户”选项](../media/mam-azure-portal-app-reporting-select-user.png)

3. 从列表中选择一个用户。 可以看到该用户合规性状态的详细信息。

    ![应用报告详细信息](../media/mam-azure-portal-app-reporting-by-user.png)

### <a name="flagged-users"></a>已标记用户
详细视图显示错误消息、错误发生时访问的应用、设备的平台和时间戳。  

### <a name="see-also"></a>另请参阅
[管理 iOS 应用之间的数据传输](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)

* [Android 应用由 MAM 策略托管时会出现的情况](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
* [iOS 应用由 MAM 策略托管时会出现的情况](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


