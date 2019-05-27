---
title: 开发过程中 - Microsoft Intune
titleSuffix: ''
description: 开发过程中的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ca66a2fa331fe4dcc30c32d369db32a57ba9999c
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2019
ms.locfileid: "66047318"
---
# <a name="in-development-for-microsoft-intune---may-2019"></a>Microsoft Intune 开发过程中的功能 - 2019 年 5 月

为了辅助就绪性和计划，此页面列出了正在开发但尚未发布的 Intune UI 更新和功能。 此外：

- 如果我们预计你需要在更改之前采取措施，我们将发布补充性的 Office 消息中心文章。
- 当某个功能在生产环境中推出时（无论是预览功能还是正式发布的功能），功能描述都将从此页移至[新增功能页](whats-new.md)。
- 此页和[新增功能页](whats-new.md)会定期更新。 返回查看其他更新。
- 有关策略性可交付内容和时间线，请参阅 [M365 路线图](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)。

> [!Note]
> 这些项目反映了 Microsoft 目前对将来版本中 Intune 功能的期望。 日期和各项功能可能会更改。 并非所有开发中的项目在此页上都有功能描述。

**RSS 源**：通过将以下 URL 复制并粘贴到源阅读器中，可以在页面更新时收到通知：`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure 门户中的 Intune


<!-- 1905 start-->


### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>关键字搜索的基线支持  <!-- 3082036         -->
创建或编辑安全基线配置文件时，即将能够使用搜索功能来筛选控制台中显示的设置。   

### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>使用图形 API 批量重置和擦除设备 <!-- 3295288 -->
用户能够使用图形 API 批量重置和擦除多达 100 台设备。

<!-- 1904 start-->

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>设备用户可以查看他们已安装或尝试安装的所有托管应用 <!-- 2352913 -->
Company Portal for Windows 将列出用户设备上安装的所有要求的和可用的托管应用。 用户将能够查看已尝试和待处理的应用安装及其当前状态。 如果组织未提供所需或可用的应用，则用户将看到一条消息，说明尚未安装任何公司应用。 用户还可以按安装状态对其应用进行排序或筛选。

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>在创建 Windows 10 设备配置配置文件时使用“适用性规则” <!-- 2549910 -->
创建 Windows 10 设备配置配置文件（“设备配置” > “配置文件” > “创建配置文件” > 适用于平台的“Windows 10”）。 你将能够创建“适用性规则”，使配置文件仅应用于特定版本。 例如，创建一个启用某些 BitLocker 设置的配置文件。 添加配置文件后，请使用适用性规则，使配置文件仅适用于运行 Windows 10 企业版的设备。

适用于： 
- Windows 10 及更高版本



## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>另请参阅
有关最近开发的详细信息，请参阅 [Microsoft Intune 中的新增功能](whats-new.md)。


