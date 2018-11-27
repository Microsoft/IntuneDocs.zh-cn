---
title: Intune 数据库仓库 API
titlesuffix: Microsoft Intune
description: 可使用 Intune 数据仓库 API 生成报表，获取有关企业移动环境的见解。
keywords: Intune 数据仓库
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 701D6CE9-43F6-4A29-8E84-E2B59931C635
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: b08746965c23c8d247a53bcd0b0844a24581b4e6
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179065"
---
#  <a name="intune-data-warehouse-api"></a>Intune 数据仓库 API

通过 Intune 数据仓库 API 可访问机器可读格式的 Intune 数据，以便在最喜欢的分析工具中使用它。 可使用该 API 生成报表，获取有关企业移动环境的见解。 API 使用 OData 协议，该协议遵循以下内容的标准模式：

  -   请求和响应标头
  -   状态代码
  -   HTTP 方法
  -   URL 约定
  -   媒体类型
  -   负载格式
  -   查询选项

OData (Open Data Protocol) 是结构化信息标准促进组织 (OASIS) 的一个标准，用于定义构建和使用 RESTful API 的最佳实践。 Intune 数据仓库使用 OData 4.0。

本参考部分概述了 Intune 数据仓库数据模型的终结点、支持的 HTTP 方法、返回负载格式和文档。

> [!Important]  
> 可使用 beta 版本，试用数据仓库的最新功能。 若要使用 beta 版本，URL 中必须包含查询参数 `api-version=beta`。 Beta 版本会提供尚未正式推出为支持服务的功能。 随着 Intune 不断添加新功能，beta 版本可能会更改行为和数据协定。 任何依赖于 beta 版本的自定义代码或报告工具都可能会因不断推出的更新而临时中断运行。 <!--If you experience problems with the beta service, follow [link to feedback process]() to report the issue or provide feedback.-->

## <a name="odata-custom-client"></a>OData 自定义客户端

可以通过 RESTful 终结点访问 Intune 数据仓库数据模型。 客户端必须使用 OAuth 2.0 获得 Azure Active Directory (Azure AD) 授权后才能访问数据。 首先在 Azure 中设置 Web 应用和客户端应用，向客户端授权。 本地客户端获得授权后便可与数据仓库终结点进行通信。

有关详细信息，请参阅[使用 REST 客户端从数据仓库 API 获取数据](reports-proc-data-rest.md)

> [!Note]  
> 可访问 GitHub 上的 [Github Intune 数据仓库存储库](https://github.com/Microsoft/Intune-Data-Warehouse)以获取代码示例。

## <a name="interacting-with-the-api"></a>与 API 交互

API 需要 Azure AD 的授权。 Azure AD 使用 OAuth 2.0。 一旦获得授权，即可通过使用 HTTP GET 谓词并联系公开的实体集合从 API 获取数据。 有关详细信息，请参阅：

 -  [授权](reports-api-url.md)
 -  [API URL 结构](reports-api-url.md)

## <a name="intune-data-warehouse-data-model"></a>Intune 数据库仓库数据模型

OData 定义抽象的数据模型和协议，允许任何客户端访问任何数据源公开的信息。 数据模型文档主题对 Intune 数据仓库数据模型中的命名空间、实体和返回对象进行了解释。 有关详细信息，请参阅[数据仓库服务数据模型](reports-ref-data-model.md)。

## <a name="next-steps"></a>后续步骤

有关使用 Azure AD 的详细信息，请参阅 [Azure AD 的身份验证方案](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios)。

在 [odata.org](http://www.odata.org) 上查找 OData 资源。
  
在 [OData 版本 4.0] (http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html)) 处查看 OData 4.0 标准版  
