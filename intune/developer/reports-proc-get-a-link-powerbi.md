---
title: 使用 Power BI 连接到数据仓库
titleSuffix: Microsoft Intune
description: 可下载一个文件与 Microsoft Power BI 结合使用，从而为 Microsoft Intune 租户加载动态生成的交互式报表。
keywords: Intune 数据仓库
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/14/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 5E5A35D3-88F8-441B-8A0B-C5D7A1E5137B
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5ee5cdb6bbdcce229fbc217726a1ee118f77beff
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71733408"
---
# <a name="connect-to-the-data-warehouse-with-power-bi"></a>使用 Power BI 连接到数据仓库

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

可使用 Power BI 符合性应用为 Intune 租户加载交互式动态生成的报告。 此外，可使用 OData 链接在 Power BI 中加载租户数据。 Intune 为你的租户提供连接设置，使你可以查看与以下内容相关的示例报表和图表：  

- 设备
- 注册
- 应用保护策略
- 合规性策略
- 设备配置文件
- 软件更新
- 设备清单日志

还有十分有用的有关注册、符合性、设备配置文件和软件更新的趋势。 示例图表和报表向画布应用便于用户使用的筛选器。 若要使用高级筛选器，请查看 Power BI Desktop 中的“筛选器”窗格  。

以下步骤介绍如何下载 Power BI 文件以及如何配合使用 Power BI 和 OData 链接。

[!INCLUDE [reports-credential-reqs](../includes/reports-credential-reqs.md)]

## <a name="install-power-bi"></a>安装 Power BI

安装最新版本的 [Power BI Desktop](https://aka.ms/intune/datawarehouseapi/installpowerbi)。 有关详细信息，请参阅 [Power BI Desktop](https://powerbi.microsoft.com/desktop)

## <a name="load-the-data-and-reports-using-the-power-bi-intune-compliance-data-warehouse-app"></a>使用 Power BI Intune 符合性数据仓库应用加载数据和报表

Power BI [Intune 符合性（数据仓库）](https://aka.ms/intune/datawarehouseapi/getpowerbiapp)应用包含租户信息和一组基于数据仓库数据模型的预置报表。

1. 导航到 [Intune 符合性（数据仓库）](https://aka.ms/intune/datawarehouseapi/getpowerbiapp)应用的“AppSource”页  以开始安装过程。
2. 单击 "**立即获取**" 按钮，然后单击 "**继续**"。
3. 系统提示安装 Power BI 应用时，单击 "**安装**"。
4. 安装完成后，单击 " **Intune 相容性（数据仓库）** 应用" 磁贴。
5. 单击“连接”按钮  。 随即显示“连接到 Intune 符合性(数据仓库)”对话框  。
6. 单击“登录”按钮  。
7. 使用用户帐户登录，此帐户具有你要查看报表的租户的 Intune 数据仓库访问权限。
8. 若要查看包含的仪表板，请单击 "**仪表板**" 选项卡，然后单击 "**合规性概述**" 仪表板。
9. 若要查看所有可用的报表，请单击 "**报表**" 选项卡，然后单击 "**符合性 1.0**版" 报表。 单击底部的选项卡，浏览报表页。
10. 若要稍后轻松导航回到这些报表，请单击“符合性 V1.0”报表旁边的星标  。 这会将报告添加到 Power BI 收藏夹中。

或者，从 Intune 门户安装应用：

1. 登录 Azure 门户，选择“监视 + 管理” > “Intune”   。 还可为 Intune 搜索资源。
2. 打开“设置 Intune 数据仓库”边栏选项卡  。
3. 选择“获取 Power BI 应用”以访问和共享浏览器中为租户预创建的 Power BI 报表  。
4. 请按照上述步骤 2-10 操作。

## <a name="load-the-data-in-power-bi-using-the-odata-link"></a>使用 OData 链接加载 Power BI 中的数据

借助经 Azure AD 身份验证的客户端，OData URL 可连接到数据仓库 API 中的 RESTful 终结点，该终结点向报告客户端公开数据模型。 按以下说明使用 Power BI Desktop 连接并创建自己的报表。 无需局限于 Power BI Desktop，可将自己最喜爱的分析工具与 OData URL 配合使用，前提是客户端支持 OAUTH2.0 身份验证和 OData v4.0 标准。

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 单击 "概述" 边栏选项卡右侧的 "**其他任务**" 部分下的 "**设置 Intune 数据仓库**"。 将显示 " **Intune 数据仓库**" 边栏选项卡。
3. 在报表边栏选项卡中检索自定义源 URL，例如：`https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=v1.0`
4. 打开 Power BI Desktop  。
5. 选择“开始” > “获取数据”   。 选择“OData 源”  。
6. 选择“基本”  。
7. 在 URL 框中键入或粘贴 OData URL  。
8. 选择“确定”  。
9. 如果尚未从 Power BI 桌面客户端为租户进行 Azure AD 身份验证，请键入凭据。 必须使用 OAuth 2.0 获得 Azure Active Directory (Azure AD) 授权后才能访问数据。  
    1. 选择“组织帐户”  。  
    2. 键入用户名和密码。  
    3. 选择“登录”  。  
    4. 选择“**连接**”。  
10. 选择“加载”  。

## <a name="next-steps"></a>后续步骤

可获取环境相关问题的答案，例如在上周白天注册的设备数。 可使用从 Azure 边栏选项卡中检索的 Intune 数据仓库 Power BI 报表来获取有关 Intune 租户和客户端总体的见解。 同时，Intune 还提供其他许多扩展或重用数据的方法。 Power BI 和 Intune 数据仓库 API 提供其他功能，例如：

<!-- - You can use Power BI Desktop to create additional report types with your data. For example, you could create a custom chart representing the ratio of device manufactures in your enterprise. For more information about creating custom reports with Power BI and the Intune Data Warehouse, see `BLOG POST ON POWER BI`. -->
- 已整理租户数据，便于用户从数据中获取见解。 有关数据组织方式的详细信息，请参阅[数据仓库数据模型](reports-ref-data-model.md)。
- 还可以从 RESTful 接口访问数据，并将数据整合到自己的应用中。 有关详细信息，请参阅[使用 REST 客户端从数据仓库 API 获取数据](../reports-proc-data-rest.md)。
