---
title: 使用 Intune 数据仓库
titleSuffix: Microsoft Intune
description: 使用 Intune 数据仓库生成报表，获取有关企业移动环境的见解。
keywords: Intune 数据仓库
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 57019B11-DF9B-4D8A-95FE-254C75398DDE
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: f382ce35d1d13a59f1aa5ca6a904c0c9babff8c1
ms.sourcegitcommit: 7cc45ef52dda08479bc6bdff7d11d2f6c0e7b93b
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 12/06/2019
ms.locfileid: "74899338"
---
# <a name="use-the-microsoft-intune-data-warehouse"></a>使用 Microsoft Intune 数据仓库

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

使用 Intune 数据仓库生成报表，获取有关企业移动环境的见解。 例如，一些报表包括：
- 用户注册 Intune 的趋势，可帮助优化许可证购买
- 应用和操作系统版本细目，可供查看移动设备的状态
- 注册和设备符合性趋势，有助于顺利推出策略更新

## <a name="data-warehouse-benefits"></a>数据仓库优势

相比 Azure 门户，通过数据仓库可访问更多有关移动环境的信息。 借助 Intune 数据仓库可访问：

- Intune 历史数据
- 每日刷新的数据
- 一个使用 OData 标准的数据模型

> [!Note]
> 如果将共同管理的移动设备管理 (MDM) 与 System Center Configuration Manager 和 Microsoft Intune 配合使用，则需要从 Configuration Manager 检索数据。 Intune 数据仓库仅包含 Intune 数据。 可将 Configuration Manager Power BI 仪表板用于自定义报表。 有关详细信息，请参阅 [Announcing the Power BI solution template for System Center Configuration Manager]( https://powerbi.microsoft.com/blog/sccm-solution-template)（宣布推出适用于 System Center Configuration Manager 的 Power BI 解决方案模板）和[适用于 Dynamics 365 的 Power BI 内容](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/analytics/power-bi-home-page)。

> [!Important]  
> 现在可以通过设置查询参数  `api-version=v1.0` 来使用 v1.0 版的 Intune 数据仓库。 数据仓库中集合的更新本质上是附加更新，不会破坏现有方案。<br><br>
> 可通过使用 beta 版本，试用数据仓库的最新功能。 若要使用 beta 版本，URL 中必须包含查询参数  `api-version=beta`。 Beta 版本会提供尚未正式作为支持服务推出的功能。 随着 Intune 不断添加新功能，beta 版本可能会更改行为和数据协定。 任何依赖于 beta 版本的自定义代码或报告工具都可能会因不断推出的更新而临时中断运行。

## <a name="next-steps"></a>后续步骤

- 获取链接并使用 Power BI 来获取见解。 有关说明，请参阅[使用 Power BI 连接到 Intune 数据仓库](reports-proc-get-a-link-powerbi.md)。
- 通过链接，使用 Power BI 创建自定义报表。 有关说明，请参阅[使用 Power BI 从 OData 数据源创建报表](reports-proc-create-with-odata.md)。
- 有关 Intune 数据仓库 API、数据模型及实体间关系的详细信息，<!-- , and an example of creating a custom client to retrieve data,--> 请参阅 [Intune 数据仓库 API](reports-nav-intune-data-warehouse.md)。
