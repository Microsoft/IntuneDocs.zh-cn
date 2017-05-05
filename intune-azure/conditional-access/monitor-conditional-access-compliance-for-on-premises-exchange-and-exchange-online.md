---
title: "监视本地 Exchange 和 Exchange Online 的条件访问符合性"
titleSuffix: Intune Azure preview
description: "通过 Intune Azure 门户监视本地 Exchange 和 Exchange Online 的条件访问符合性"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 04/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5712682d-285b-43fd-9978-3dcfd95ec5f9
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: c8715f96f532ee6bacda231e1147d03226ecbb48
ms.openlocfilehash: 9d5521de8709bf232dedfeeb1874f8db1898f2d0
ms.lasthandoff: 04/26/2017


---

# <a name="monitor-conditional-access-compliance-for-on-premises-exchange-and-exchange-online-in-intune-azure-preview"></a>在 Intune Azure 预览版中监视本地 Exchange 和 Exchange Online 的条件访问符合性

从 Intune 1704 版本开始，管理员可以查看与 Exchange ActiveSync 设备记录（通过本地 Exchange Connector 或 Intune 服务到服务连接器（Exchange Online 连接器）与 Intune 同步）相关的报告信息。 条件访问符合性报告将提供具有不同同步状态的设备摘要：

-   **允许**

-   **阻止**

-   **隔离**

## <a name="to-monitor-conditional-access-compliance"></a>监视条件访问符合性

1.  转到 [Azure 门户](https://portal.azure.com/)，然后使用 Intune 凭据登录。

2.  成功登录后，会看到“Azure 仪表板”。

3.  从左侧菜单中选择“**更多服务**”，然后在文本框筛选器中键入 **Intune**。

4.  选择“Intune”，将看到“Intune 仪表板”。

5.  选择“条件访问”，然后选择“概述”。

6.  选择图表上的三个区域（“阻止”、“隔离”或“允许”）之一，查看条件访问符合性报告。

    ![条件访问仪表板](../media/CA-reporting-intune-1.png)

选择三个区域之一后，可以看到有关已允许、阻止或隔离的设备的详细信息。

还可以进一步查看特定设备来了解更多详细信息。 例如，下图中所选定的设备被阻止。 可以通过 Intune 从条件访问符合性报告边栏选项卡删除公司数据。

![条件访问设备详细信息报告](../media/CA-reporting-intune-3.png)

在设备详细信息边栏选项卡上，可以看到更多信息：

-   **概述：**可以看到设备属性，例如：操作系统版本、设备型号、所有权、序列号、设备制造商、电话号码和上次审查设备的时间。

-   **属性：**可以设置设备所有权（个人或公司）。

-   **硬件：**提供在“概述”上看到的信息及存储详细信息（总空间和可用空间）、系统封闭、网络详细信息、网络服务及其他条件访问阻止详细信息。

-   **已发现的应用：**显示设备上已安装的所有应用程序。 还可以将已安装的应用列表导出为 .CSV 格式。

-   **符合性：**显示所有设备符合性策略详细信息。

-   **设备配置：**显示所有设备配置详细信息。

-   **Exchange 访问：**应用条件访问策略后，可以在此处了解设备状态的详细信息。

