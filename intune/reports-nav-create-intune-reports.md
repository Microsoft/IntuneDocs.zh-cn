---
title: "使用 Intune 数据仓库 | Microsoft Docs"
description: "使用 Intune 数据仓库生成报表，获取有关企业移动环境的见解。"
keywords: "Intune 数据仓库"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 57019B11-DF9B-4D8A-95FE-254C75398DDE
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: db6661dd92b890d711f655a60eb883b417a30d8a
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2017
---
# <a name="use-the-intune-data-warehouse"></a>使用 Intune 数据仓库

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

使用 Intune 数据仓库生成报表，获取有关企业移动环境的见解。 例如，一些报表包括：
-   用户注册 Intune 的趋势，可帮助优化许可证购买
-   应用和操作系统版本细目，可供查看移动设备的状态
-   注册和设备符合性趋势，有助于顺利推出策略更新

相比 Azure 门户，通过数据仓库可访问更多有关移动环境的信息。 借助 Intune 数据仓库可访问：

  -  Intune 历史数据
  -  每日刷新的数据
  -  一个使用 OData 标准的数据模型

> [!Important]  
> 可通过使用 beta 版本，试用数据仓库的最新功能。 若要使用 beta 版本，URL 中必须包含查询参数 `api-version=beta`。 Beta 版本会提供尚未正式推出为支持服务的功能。 随着 Intune 不断添加新功能，beta 版本可能会更改行为和数据协定。 任何依赖于 beta 版本的自定义代码或报告工具都可能会因不断推出的更新而临时中断运行。 <!-- If you experience problems with the beta service, follow [link to feedback process]() to report the issue or provide feedback.-->

**后续步骤**

- 获取链接并使用 Power BI 来获取见解。 有关说明，请参阅[使用 Power BI 连接到 Intune 数据仓库](reports-proc-get-a-link-powerbi.md)。
- 有关 Intune 数据仓库 API、数据模型及实体间关系的详细信息<!-- , and an example of creating a custom client to retrieve data,-->，请参阅 [Intune 数据仓库 API](reports-nav-intune-date-warehouse.md)。