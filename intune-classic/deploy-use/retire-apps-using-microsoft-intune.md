---
title: "停用应用 | Microsoft Docs"
description: "了解如何使用 Intune 停用或卸载应用。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6fbf0805-1144-4e08-bafd-4f181d932bf2
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 670e108fc4f672b4900f7cfb4e0127e16a377fa7
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017


---

# <a name="retire-apps-using-microsoft-intune"></a>使用 Microsoft Intune 停用应用

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

若要停用应用，只需卸载它。 使用 Intune 部署和管理应用时，在移动设备和 Windows PC 上卸载应用的过程是相同的。 该应用必须支持卸载过程，才能确保此过程成功。

## <a name="uninstall-an-app"></a>卸载应用

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，选择“应用”&gt;“应用”。

2.  选择你要卸载的应用（之前已部署的应用），然后选择“管理部署”。

3.  在“部署操作”  页上，从“批准”  列中选择“卸载”  ：

当设备或计算机下一步检查应用时，该应用将被卸载。

### <a name="see-also"></a>另请参阅
[在 Microsoft Intune 中添加应用](add-apps.md)

