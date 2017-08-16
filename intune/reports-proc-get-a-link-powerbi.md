---
title: "使用 Power BI 连接到数据仓库 | Microsoft Docs"
description: "可下载一个文件与 Microsoft Power BI 结合使用，从而为 Intune 租户加载动态生成的交互式报表。"
keywords: "Intune 数据仓库"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5E5A35D3-88F8-441B-8A0B-C5D7A1E5137B
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b70bf3410e20dd792c0fcff050292ddea714d63e
ms.sourcegitcommit: 99ffed621855357de427d6fdf7b70d4e543197e9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2017
---
# <a name="connect-to-the-data-warehouse-with-power-bi"></a>使用 Power BI 连接到数据仓库

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

可下载一个文件与 Microsoft Power BI 结合使用，从而为 Intune 租户加载动态生成的交互式报表。 数据仓库 Power BI 文件 (pbix) 包含租户连接设置及以下示例报表和图表：  

  -  设备
  -  注册
  -  应用保护策略
  -  合规性策略
  -  设备配置文件
  -  软件更新
  -  设备清单日志

还有十分有用的有关注册、符合性、设备配置文件和软件更新的趋势。 示例图表和报表向画布应用便于用户使用的筛选器。 若要使用高级筛选器，请查看 Power BI Desktop 中的“筛选器”窗格。 

以下步骤介绍如何下载 Power BI 文件以及如何配合使用 Power BI 和 OData 链接。

## <a name="install-power-bi"></a>安装 Power BI

安装最新版本的 Power BI Desktop。 可从 [PowerBI.microsoft.com](https://powerbi.microsoft.com/en-us/desktop) 下载 Power BI Desktop 

## <a name="load-the-data-and-reports-using-the-power-bi-file-pbix"></a>使用 Power BI 文件 (pbix) 加载数据和报表

Power BI 文件 (pbix) 包含租户连接信息和一组基于数据仓库数据模型的预置报表。 在 Power BI Desktop 中打开文件并登录 Azure AD。 报表从 Intune 租户加载数据。

> [!Important]  
> 每个 Power BI 文件 (pbix) 可能会因租户位置而有所不同。 如果要管理多个 Intune 租户，请在登录该租户时，确保使用从 Azure 门户下载的文件。  

1.  登录 Azure 门户，选择“监视 + 管理” > “Intune”。 还可搜索 Intune 资源。  
2.  打开“Microsoft Intune 数据仓库 API (预览)”边栏选项卡。
3.  单击“下载 PowerBI 文件”。 扩展名为 (Pbix) 的文件将下载到指定位置。
4.  使用 Power BI 打开文件。 此时会加载“Intune 数据仓库报表”，但这可能需要一些时间，因为报表要获取租户数据。
5.  单击“刷新”，加载租户数据并查看报表。
6.  如果 Power BI 尚未对 Azure Active Directory 凭据进行身份验证，则 Power BI 会提示用户提供凭据。 选择凭据时，请选择“组织帐户”作为身份验证方法。

## <a name="load-the-data-in-power-bi-using-the-odata-link"></a>使用 OData 链接加载 Power BI 中的数据

借助经 Azure AD 身份验证的客户端，OData URL 可连接到数据仓库 API 中的 RESTful 终结点，该终结点向报告客户端公开数据模型。 按以下说明使用 Power BI Desktop 连接并创建自己的报表。 无需局限于 Power BI Desktop，可将自己最喜爱的分析工具与 OData URL 配合使用，前提是客户端支持 OAUTH2.0 身份验证和 OData v4.0 标准。

1.  在报表边栏选项卡中检索 **OData URL**，例如 `https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=beta`。
2.  打开 Power BI Desktop。
3.  选择“开始” > “获取数据”。 选择“OData 源”。
4.  选择“基本”。
5.  在 URL 框中键入或粘贴 OData URL。
6.  单击" **确定**"。
7.  如果尚未从 Power BI 桌面客户端为租户进行 Azure AD 身份验证，请键入凭据。  
    a.  选择“组织帐户”。  
    b。  键入用户名和密码。  
    c.  单击“登录”。  
    d.  单击“连接” 。  
8.  单击“加载”。

## <a name="next-steps"></a>后续步骤

可获取环境相关问题的答案，例如在上周白天注册的设备数。 可借助一些报表来获取有关 Intune 租户和客户总体的见解，这些报表使用从 Azure 中边栏选项卡检索的 Intune 数据仓库 Power BI 文件 (pbix)。 同时，Intune 还提供其他许多扩展或重用数据的方法。 可使用 Power BI 和 Intune 数据仓库 API 执行的操作还有许多，例如：

<!-- -  You can use Power BI Desktop to create additional report types with your data. For example, you could create a custom chart representing the ratio of device manufactures in your enterprise. For more information about creating custom reports with Power BI and the Intune Data Warehouse, see `BLOG POST ON POWER BI`. -->
 -  已整理租户数据，便于用户从数据中获取见解。 有关数据组织方式的详细信息，请参阅[数据仓库数据模型](reports-ref-data-model.md)。 
<!-- -  You can also access the data from a RESTful interface and incorporate the data into your own app. For more information, see [Get data from the Data Warehouse API with a REST client](reports-proc-data-rest.md). -->