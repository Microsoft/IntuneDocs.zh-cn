---
title: "Intune 数据库仓库 API | Microsoft Docs"
description: "可使用该 API 生成报表，获取有关企业移动环境的见解。"
keywords: "Intune 数据仓库"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 701D6CE9-43F6-4A29-8E84-E2B59931C635
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5f03fd3a1557ef5d013fe695016ed0e3b119ee62
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2017
---
#  <a name="intune-data-warehouse-api"></a>Intune 数据仓库 API

通过 Intune 数据仓库 API 可访问机器可读格式的 Intune 数据，将其用于最喜欢的分析工具。 可使用该 API 生成报表，获取有关企业移动环境的见解。 API 使用 OData 协议，该协议遵循以下内容的标准模式：

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
> 可使用 beta 版本，试用数据仓库的最新功能。 若要使用 beta 版本，URL 中必须包含查询参数 `api-version=beta`。 在功能正式推出为支持的服务前，可通过 beta 版本使用供这些服务。 随着 Intune 不断添加新功能，beta 版本可能会更改行为和数据协定。 任何依赖于 beta 版本的自定义代码或报告工具都可能会中断正在进行的更新。 <!--If you experience problems with the beta service, follow [link to feedback process]() to report the issue or provide feedback.-->

<!-- ## OData custom client

You can access the Intune Data Warehouse data model through RESTful endpoints. To gain access to your data, your client must authorize with Microsoft Azure Active Directory (Azure AD) using OAuth 2.0. You first set up a web app and a client app in Azure, grant permissions to the client. Your local client will get authorization, can then communicate with the Data Warehouse endpoints.

For more information, see [Get data from the Data Warehouse API with a REST client](Get-data-REST.md) -->

## <a name="interacting-with-the-api"></a>与 API 交互

API 需要 Azure AD 的授权。 Azure AD 使用 OAuth 2.0。 一旦获得授权，即可通过使用 HTTP GET 谓词并联系公开的实体集合从 API 获取数据。 有关详细信息，请参阅：

 -  [授权](reports-api-url.md)
 -  [API URL 结构](reports-api-url.md)

## <a name="intune-data-warehouse-data-model"></a>Intune 数据库仓库数据模型

OData 定义抽象的数据模型和协议，允许任何客户端访问任何数据源公开的信息。 数据模型文档主题对 Intune 数据仓库数据模型中的命名空间、实体和返回对象进行了解释。 有关详细信息，请参阅[数据仓库服务数据模型](reports-ref-data-model.md)。

## <a name="for-more-information"></a>更多相关信息

[Azure AD 的身份验证方案](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios)  
[odata.org](http://www.odata.org)  
[OData 4.0 版](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html)  
