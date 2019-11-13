---
title: 验证应用保护策略设置
titleSuffix: Microsoft Intune
description: 了解如何在 Microsoft Intune 中测试应用保护策略是否已正确设置并正常运行。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/06/2019
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.topic: conceptual
ms.technology: ''
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0b9dda9a1aa1e81b46533c1c15d996807984193d
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "73712950"
---
# <a name="how-to-validate-your-app-protection-policy-setup-in-microsoft-intune"></a>如何在 Microsoft Intune 中验证应用保护策略设置

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

验证应用保护策略是否已正确设置并运行。 本指南适用于 Azure 门户中的应用保护策略。

## <a name="checking-for-symptoms"></a>检查症状
由于应用保护是数据保护工具，因此用户不太可能报告问题。 如果应用保护配置出现问题，用户将具有不受限制的访问权限，就如同没有应用保护一样，并且不会知道出现了问题。 因此，建议让一小组可专门测试应用保护限制的用户试验应用保护策略来验证应用保护配置。

## <a name="what-to-check"></a>要检查的内容

如果测试显示应用保护策略行为与预期不符，请检查以下项：

- 用户是否已获得应用保护授权？
- 用户是否已获得 O365 授权？
- 每个用户的应用保护应用的状态是否与预期相符。 可能的应用状态为“**已签入**”和“**未签入**”。

### <a name="user-app-protection-status"></a>用户应用保护状态
1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 选择  “客户端应用” >    “应用保护状态”，然后选择  “分配的用户”磁贴。 
4. 在  “应用报告”页上，选择  “选择用户”以显示用户和组的列表。 
5. 从列表中搜索并选择一个用户，然后选择“选择用户”  。 在“应用报告”窗格顶部，可以看到用户是否已获得应用保护授权  。 还可以看到该用户是否已获得 O365 授权，以及该用户所有设备的应用状态。

## <a name="what-to-do"></a>要执行的操作
下面是要根据用户状态采取的操作：

- 如果用户未获得应用保护授权，请为用户分配 [Intune 许可证](../fundamentals/licenses.md)。
- 如果用户未获得 O365 授权，请为用户获取[许可证](../fundamentals/licenses.md)。
- 如果用户的某个应用被列为“未签入”  ，请检查是否已为该应用正确配置[应用保护策略](app-protection-policies-validate.md)。
- 确保这些条件适用于要应用[应用保护策略](app-protection-policies-monitor.md)的所有用户。

## <a name="see-also"></a>另请参阅

- [什么是 Intune 应用保护策略？](app-protection-policies.md)
- [包括 Intune 的许可证](../fundamentals/licenses.md)
- [向用户分配许可证，以便他们能够在 Intune 中注册设备](../fundamentals/licenses-assign.md)
- [如何验证应用保护策略设置](app-protection-policies-validate.md)
- [如何监视应用保护策略](app-protection-policies-monitor.md)

