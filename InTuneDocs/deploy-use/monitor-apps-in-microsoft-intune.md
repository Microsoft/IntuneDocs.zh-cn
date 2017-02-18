---
title: "监视应用部署 | Microsoft Docs"
description: "了解如何监视使用 Intune 部署的应用。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5daad56d-71c8-455b-8a55-f8b33e279a8a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: ee0d10f9b86b1122d0f16568b71b087c341e88df


---


# <a name="monitor-app-deployments-in-microsoft-intune"></a>监视 Microsoft Intune 中的应用部署 | Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="monitor-an-app-deployment"></a>监视应用部署
你可以查看你管理的应用，以及 Intune 管理控制台中任何部署的状态。 <!---App status is displayed in real-time. You don't have to wait for the device to check-in before you can see this.--->

### <a name="to-view-apps-that-you-manage-and-their-status"></a>查看你管理的应用及其状态
在“应用”工作区中，选择“应用”节点，然后选择“应用”。

此时将显示你管理的应用的列表。 你可以选择任意应用，以在控制台窗口的下部窗格中查看安装状态。 选择此状态可查看更多详细信息。 例如，如果状态显示“1 名用户已可用此软件”，你可以选择该消息来查看该用户的姓名。

> [!TIP]
> 可以使用“筛选器”下拉列表以仅显示满足指定条件的应用，如未能安装的应用或已成功部署的应用。
>
> ![应用筛选器示例](./media/app-filters.png)

此外，“仪表板”工作区会显示应用状态概述。 如果单击概述中的任意位置，则将转到应用列表。

## <a name="to-view-more-detailed-information-about-an-app"></a>查看有关应用的更多详细信息
在应用列表中，选择任意应用，然后选择“查看属性”。

在应用的“软件属性”页上，选择以下任一选项卡：“常规”— 显示关于应用及其安装状态的常规信息，“设备”— 显示成功安装了应用的目标部署的设备，“用户”— 显示其设备成功安装了应用的目标部署的用户。

如前所述，你可以使用“筛选器”下拉列表来配置每个选项卡上显示的值。



<!--HONumber=Dec16_HO2-->


