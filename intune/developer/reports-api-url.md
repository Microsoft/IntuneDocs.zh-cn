---
title: Intune 数据仓库 API 终结点
titleSuffix: Microsoft Intune
description: 此参考主题介绍 Microsoft Intune 数据仓库 API URL 结构。 提供了筛选器示例。
keywords: Intune 数据仓库
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/03/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A7A174EC-109D-4BB8-B460-F53AA2D033E6
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: e19cc606792c59d2f5676aeca41d862308f1ab32
ms.sourcegitcommit: 8d7406b75ef0d75cc2ed03b1a5e5f74ff10b98c0
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2020
ms.locfileid: "75654135"
---
# <a name="intune-data-warehouse-api-endpoint"></a>Intune 数据仓库 API 终结点

可将 Intune 数据仓库 API 与具有基于特定角色的访问控制和 Azure AD 凭据的帐户配合使用。 然后，使用 OAuth 2.0 向 REST 客户端授予 Azure AD 权限。 最后会形成一个有意义的可调用数据仓库资源的 URL。

[!INCLUDE [reports-credential-reqs](../includes/reports-credential-reqs.md)]

## <a name="authorization"></a>授权

Azure Active Directory (Azure AD) 使用 OAuth 2.0 使你能够在你的  Azure  AD  租户中授予对  Web  应用程序和  Web  API  的访问权限。 本指南介绍如何在不使用任何开源库的情况下发送和接收 HTTP 消息（无语言限制）。 OAuth 2.0 规范的[第 4.1 节](https://tools.ietf.org/html/rfc6749#section-4.1)介绍了 OAuth 2.0 授权代码流。

有关详细信息，请参阅[授权使用 OAuth 2.0 和 Azure Active Directory 访问 Web 应用程序](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code)。

## <a name="api-url-structure"></a>API URL 结构

数据仓库 API 终结点读取每个集的实体。 API 支持 **GET** HTTP 谓词和查询选项的子集。

Intune 的 URL 使用以下格式：  
`https://fef.{location}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{entity-collection}?api-version={api-version}`

> [!NOTE]
> 根据下表中提供的详细信息，替换上述 URL 中的 `{location}`、`{entity-collection}` 和 `{api-version}`。

该 URL 包含以下元素：

| 元素 | 示例 | 说明 |
|-------------------|------------|--------------------------------------------------------------------------------------------------------------------|
| 位置 | msua06 | 可通过查看 Azure 门户中的数据仓库 API 边栏选项卡获取基 URL。 |
| 实体集合 | devicePropertyHistories | OData 实体集合的名称。 有关数据模型中集合和实体的详细信息，请参阅[数据模型](reports-ref-data-model.md)。 |
| api-version | beta | 版本是指要访问的 API 版本。 有关详细信息，请参阅[版本](reports-api-url.md#api-version-information)。 |
| maxhistorydays | 7 | （可选）要检索的历史记录的最大天数。 此参数可提供给任何集合，但仅对键属性中包含 `dateKey` 的集合生效。 有关详细信息，请参阅 [DateKey 范围筛选器](reports-api-url.md#datekey-range-filters)。 |

## <a name="api-version-information"></a>API 版本信息

现在可以通过设置查询参数  `api-version=v1.0` 来使用 v1.0 版的 Intune 数据仓库。 数据仓库中集合的更新本质上是附加更新，不会破坏现有方案。

可通过使用 beta 版本，试用数据仓库的最新功能。 若要使用 beta 版本，URL 中必须包含查询参数  `api-version=beta`。 Beta 版本会提供尚未正式作为支持服务推出的功能。 随着 Intune 不断添加新功能，beta 版本可能会更改行为和数据协定。 任何依赖于 beta 版本的自定义代码或报告工具都可能会因不断推出的更新而临时中断运行。

## <a name="odata-query-options"></a>OData 查询选项

当前版本支持以下 OData 查询参数：`$filter`、`$select`、`$skip,` 和 `$top`。 在 `$filter` 中，当列适用时，可能仅支持 `DateKey` 或 `RowLastModifiedDateTimeUTC`，其他属性将触发错误请求。

## <a name="datekey-range-filters"></a>DateKey 范围筛选器

`DateKey` 范围筛选器可用于限制键属性为 `dateKey` 的某些集合可下载的数据量。 通过提供以下 `$filter` 查询参数，`DateKey` 筛选器可用于优化服务性能：

1. `$filter` 中的 `DateKey` 可单独支持 `lt/le/eq/ge/gt` 运算符并可与逻辑运算符 `and` 结合使用，将它们映射到开始日期和/或结束日期。
2. `maxhistorydays` 作为自定义查询选项提供。<br>

## <a name="filter-examples"></a>筛选器示例

> [!NOTE]
> 筛选器示例假定现在是 2019/2/21。

|                             筛选器                             |           性能优化           |                                          说明                                          |
|:--------------------------------------------------------------:|:--------------------------------------------:|:---------------------------------------------------------------------------------------------:|
|    `maxhistorydays=7`                                            |    完整                                      |    返回 `DateKey` 介于 20180214 至 20180221 的数据。                                     |
|    `$filter=DateKey eq 20180214`                                 |    完整                                      |    返回 `DateKey` 等于 20180214 的数据。                                                    |
|    `$filter=DateKey ge 20180214 and DateKey lt 20180221`         |    完整                                      |    返回 `DateKey` 介于 20180214 至 20180220 的数据。                                     |
|    `maxhistorydays=7&$filter=DateKey eq 20180214`                |    完整                                      |    返回 `DateKey` 等于 20180214 的数据。 已忽略 `maxhistorydays`。                            |
|    `$filter=RowLastModifiedDateTimeUTC ge 2018-02-21T23:18:51.3277273Z`                                |    完整                                       |    返回 `RowLastModifiedDateTimeUTC` 数据大于或等于 `2018-02-21T23:18:51.3277273Z`                             |
